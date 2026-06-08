# ◊ OPERATOR · structured strategy

> A sovereign single-file management-consulting tool.
> 5-phase engagement engine · MECE issue trees · Porter / 7S / BCG / Value-Driver Tree · 7-strand synthesis · Minto-pyramid deck output · audit-chained · Konomi-signed · MIT.
> McKinsey's frameworks · without the £1M deck.

**Live:** https://sjgant80-hub.github.io/operator

```
McKinsey's IP is in every business-school textbook.
The frameworks are public · the deck is the paywall.
OPERATOR removes the paywall · structured thinking is just code.
```

---

## What it is

A turn-key strategy engagement, structured McKinsey-style, that runs in your browser. Five phases. Sample engagement preloaded. Every claim hash-chained, every deliverable Ed25519-signed against your Konomi keypair so the client can verify provenance.

### The 5-phase engine

1. **Diagnose** · MECE issue tree + hypothesis pyramid · the question before the answer · templates for acquisition, market entry, cost transformation
2. **Research** · evidence base per sub-question · adversarial verification (claims marked confirmed / refuted / pending) · killed-claims listed openly (the same honesty pattern that won attention for `nhs-reinjection`)
3. **Frame** · Porter's 5 Forces · McKinsey 7S · BCG Matrix · Value-Driver Tree · each as a structured form
4. **Synthesize** · 7-strand cross-cutting weave (CUSTOMER · CAPABILITY · CHANNEL · COST · CASH · COMPLIANCE · CULTURE) · contradiction detection · overall risk score (STRONG / MODERATE / WEAK / INADVISABLE) using the same algorithm as `groundlevel-sdk`
5. **Deck** · Minto pyramid storyline (governing thought + arguments + supports) · output as Markdown, reveal.js HTML slides, or Konomi-signed JSON envelope

---

## What makes it sovereign

- **Single HTML file.** Drop on a USB. Opens offline.
- **No accounts.** No tracking. IndexedDB + localStorage persist everything locally.
- **Ed25519 identity** via libsodium-wasm · keypair generated on first boot · never leaves the device · seed-exportable for cross-device.
- **κ-ledger** · +21 κ per completed engagement · broadcasts on `kcc-signal` for sister-tool integration · same pattern as `kard`.
- **MIT.** Fork it · rebrand it · brand it your firm's name · same engine.
- **Pro-slot architecture.** 5 swappable functions documented in [`src/pro-slot.md`](./src/pro-slot.md). Plug in your LLM for issue-tree decomposition · framework auto-fill · storyline generation · whatever.

---

## How it differs from a McKinsey engagement

| | McKinsey | OPERATOR |
|---|---|---|
| Cost | £1M-£5M+ per engagement | £0 (open source) · £12,500 productized via Upwork |
| Time | 8-12 weeks | days (with the playbook running) |
| Deliverable | 60-slide deck, faces on cover | Markdown / reveal.js / signed JSON envelope |
| Provenance | brand reputation | SHA-256 audit chain + Ed25519 signature |
| Audit trail | partner sign-off | every claim hash-chained, refuted ones listed openly |
| Frameworks | same Porter / 7S / BCG | same Porter / 7S / BCG |
| Methodology | hypothesis-driven · MECE · Minto | hypothesis-driven · MECE · Minto |
| The bit you pay for | the brand on the cover + 12 weeks of analyst labour | structured thinking · already in code |

The brand on the cover is the only piece OPERATOR cannot give you. That you build yourself, over years of receipts. The rest is structured thinking and the IP is public.

---

## Try it

```
https://sjgant80-hub.github.io/operator
```

Hit **Load sample · acquisition diligence** on the home page to see all 5 phases pre-populated with a worked example. Walk through tab by tab. Hit **Finish · +21 κ** at the end to mint a signed engagement envelope.

---

## Build a real engagement

1. **Home** → "Start a new engagement"
2. **Diagnose** · paste the business question · pick a MECE template (acquisition / market-entry / cost-transform) or build the tree manually
3. **Research** · paste each claim · cite source · mark verdict · refuted claims auto-flow to the killed-claims section
4. **Frame** · fill Porter / 7S / BCG / Value-Driver Tree as relevant (you don't need all four for every engagement)
5. **Synthesize** · write the 7-strand notes · rate each strand · click "Compute risk" to score the recommendation
6. **Deck** · write the Minto pyramid · generate Markdown for Google Slides paste-ready · or reveal.js HTML for self-contained presentation · or signed JSON envelope for cryptographic provenance
7. Click **Finish · +21 κ** · engagement gets sealed in history, audit chain final-hashed, Konomi envelope signed

---

## Sister tools in the estate

OPERATOR completes the 3-lane vision:

| Lane | Tool | Who it's for |
|---|---|---|
| **Legal** | [groundlevel](https://github.com/sjgant80-hub/groundlevel) (PWA + SDK + worker + shim + MCP + Obsidian) | the wronged citizen + the legal-tech builder + the practising solicitor |
| **Operations** | [gymops](https://github.com/sjgant80-hub/gymops) + fallinvoice/flow/crm/hire/carousel/ap + [nhs-reinjection](https://github.com/sjgant80-hub/nhs-reinjection) | the gym owner + the SME owner + the policy reformer |
| **Strategy** | **OPERATOR · this repo** | the founder facing a hard decision + the consultant who can't afford McKinsey + the board that wants a second opinion |

All three lanes share:
- Ed25519 Konomi keypair identity (libsodium-wasm)
- SHA-256 prevHash audit chain
- BroadcastChannel `fall-signal` mesh emit
- MIT licence · no backend · no telemetry · no accounts

---

## Roadmap

- **v1.0** (you're here) · PWA with all 5 phases · sample engagement · manual entry + LLM swap-slots
- **v1.1** · `operator-sdk` · pure ESM npm package · the 5-phase engine extractable for any context (same pattern as `groundlevel-sdk`)
- **v1.2** · `operator-worker` · Cloudflare Worker REST API · POST /diagnose · /research · /frame · /synthesise · /storyline
- **v1.3** · `operator-shim` · CDN drop-in `<script>` that adds an "engagement wizard" to any consulting site
- **v1.4** · `operator-mcp` · MCP stdio server · use OPERATOR from inside Claude Code / Cursor
- **v1.5** · `operator-obsidian` · Obsidian plugin · run an engagement from inside your notes vault
- **v2.0** · BYOK LLM cascade wired into all 5 phases by default · v1.0 stays as the manual-driven mode

Same playbook as GroundLevel. The PWA is the seed · the SDK/worker/shim/MCP/Obsidian ripple is the multiplier.

---

## Pricing (for productised deployments)

If you want OPERATOR to run a real engagement for you:

| SKU | What | Price |
|---|---|---|
| Strategic Diagnosis Pack | Phases 1 + 2 · MECE tree + research base + killed claims · 5 days | $3,500 |
| Full Strategic Analysis | All 5 phases · client decision-ready · 14 days | $12,500 |
| Board-Ready Deck | Full Strategic Analysis + custom reveal.js slides + signed envelope | $18,500 |

Productized listings will land on Upwork after v1.1 SDK ships · launch promo: **first 3 DMs get 50% off the Diagnosis Pack ($3,500 → $1,750)**.

---

## Caveats

- **Not financial advice.** Strategic information and analysis only. Verify before any irreversible decision.
- **v1.0 is manual-mode.** LLM auto-fill swaps in at v2.0. Today you do the thinking; OPERATOR structures it.
- **Konomi seed is your responsibility.** If you wipe browser data without exporting the seed, your identity (and signed envelope continuity) is gone.

---

## Licence

MIT · use freely · fork freely · re-skin freely.

**◊·κ=φ⁴ · structured thinking is just code · the deck is the paywall · we remove the paywall.**
