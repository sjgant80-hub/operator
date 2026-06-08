# OPERATOR · pro-slot interface

> The 5-phase strategy engine is intentionally swappable. Default implementations are clean, deterministic, and free. Plug in LLM cascades / ML scorers / custom frameworks · the rest of the app doesn't care.

---

## The 5 swap points

| Phase | Default | What you can replace it with |
|---|---|---|
| **1 · Diagnose** | hardcoded MECE templates · manual hypothesis entry | LLM-driven issue-tree decomposition from a free-text question |
| **2 · Research** | manual claim entry + manual verdict cycling | multi-source web-search agent + 3-vote adversarial verifier (fall-verify pattern) |
| **3 · Frame** | manual fill-in of Porter / 7S / BCG / VDT | LLM auto-fill from the research base · returns structured JSON |
| **4 · Synthesize** | manual strand notes + L/M/H risk rating | weave engine from groundlevel-sdk · re-skinned strands · contradiction detection |
| **5 · Deck** | manual Minto pyramid entry · markdown + reveal.js output | LLM auto-storyline from synthesised findings · slide outline → polished design |

---

## The contract

Each phase exposes a function on `window.OPERATOR_ENGINE`. Replace any subset.

```js
window.OPERATOR_ENGINE = {
  // L1
  async generateIssueTree(question, context) {
    // returns { root, branches: [{ text, children: [...] }] }
  },

  // L2
  async runResearch(subQuestion) {
    // returns [{ text, src, verdict: 'confirmed'|'refuted'|'pending', score }]
  },

  // L3
  async fillFramework(name, evidence) {
    // name: 'porter' | '7s' | 'bcg' | 'vdt'
    // returns the framework-shaped JSON to populate the form
  },

  // L4
  async synthesise(state) {
    // returns { strands: { CUSTOMER: { notes, risk }, ... }, contradictions: [...], risk: { label, score } }
  },

  // L5
  async buildStoryline(state) {
    // returns { governing, arguments: [{ thesis, support: [] }] }
  },
};
```

---

## What's already wired

- Engagement state in `localStorage` (key `operator.v1.current`) + history in `operator.v1.history`
- IndexedDB store `operator.v1` for Konomi keypair + κ ledger
- SHA-256 prevHash audit chain on every state-changing action (see `hashMove()`)
- Ed25519 signing via libsodium-wasm (lazy ESM from `https://esm.run/libsodium-wrappers`)
- κ-ledger entries broadcast on `BroadcastChannel('kcc-signal')` for sister-tool integration
- Tool-ready emit on `BroadcastChannel('fall-signal')` for mesh discovery
- Sample engagement loadable from the Home view (acquisition diligence)
- Markdown / reveal.js / signed-JSON-envelope output formats

---

## Recommended swap order

1. **L5 (Deck storyline)** is the highest-leverage LLM swap. A Claude/GPT/Gemini call that takes the synthesised state and produces a tight 3-argument-with-3-supports pyramid is the actual value-add over manual storyline writing.
2. **L1 (Issue tree)** is next — issue tree generation is exactly what LLMs are good at and saves 20-30 minutes per engagement.
3. **L3 (Framework auto-fill)** is third — works best when L2 has produced a rich evidence base for the LLM to draw from.
4. **L2 (Research agent)** is the deepest swap — wire up your own multi-source search + adversarial verifier (fall-substrate / fall-verify patterns work directly).
5. **L4 (Synthesise)** is the smallest gap — the existing weave-style logic does most of the lift; replace if you want a smarter contradiction detector.

---

## Konomi protocol

Engagement envelopes are Ed25519-signed against the user's local Konomi keypair. The envelope structure:

```json
{
  "envelope": {
    "kind": "operator-engagement-v1",
    "issuer": "<public-key-hex>",
    "issuedAt": "ISO timestamp",
    "engagement": {
      "id": "eng-…",
      "title": "…",
      "question": "…",
      "startedAt": "ISO",
      "finalHash": "<prevHash sha256>",
      "claimsTotal": 12,
      "claimsRefuted": 3,
      "governing": "the one-line recommendation"
    }
  },
  "signature": "<ed25519 detached signature hex>"
}
```

Client verification:
```js
const sodium = await libsodium();
const ok = sodium.crypto_sign_verify_detached(
  sodium.from_hex(envelope.signature),
  sodium.from_string(JSON.stringify(envelope.envelope)),
  sodium.from_hex(envelope.envelope.issuer)
);
```

If `ok === true`, this is THE engagement, signed by THIS consultant, at THAT time, with the listed claim counts and that specific final hash. Tamper-proof.

---

## What pro-slot doesn't change

- the UI structure
- the audit chain
- the Konomi signing
- the κ-ledger mesh emit
- localStorage / IndexedDB shape
- export formats

Drop in your engine, change nothing else.

**◊·κ=φ⁴**
