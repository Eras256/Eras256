# `Eras256`

I build infrastructure for the agent economy — payment rails, service
discovery, identity attestations, and audit trails for autonomous agents
transacting with real money. Built with my cofounder,
**[Monserrat Mendoza](https://github.com/M0nsxx)** — product and UX across
every project below, expanding into marketing, and now shipping real code
too (see the Nirium section for two merged PRs that are hers).

Six projects, four chains, each for a specific reason:

| Project(s) | Chain | Why there |
| --- | --- | --- |
| Periplo, Nirium, Contextio | Stellar | Payments: [$0.0007667 average transaction cost](https://stellar.org/) and 24/7 settlement, cheap enough for agent-scale micropayments, plus the SCF funding program this portfolio started in |
| KUMPLY | Avalanche | Compliance for regulated institutions: purpose-built [Evergreen Subnets](https://www.avax.network/about/blog/avalanche-launches-evergreen-for-institutional-blockchain-deployments/) give KYC, permissioned validators, and controlled access — the same track that had [Progmat migrate $2B+ in security tokens](https://www.avax.network/institutions) in Feb 2026 and 29 institutions (Franklin Templeton, VanEck, WisdomTree among them) formalize the [Avalanche Payments Collective](https://www.avax.network/about/blog/avalanche-payments-collective) in Q2 2026, compliance named as one of its explicit categories |
| Vouch402 | Base | Same chain as EAS (Ethereum Attestation Service), the attestation layer it settles proof-of-fulfillment to |
| Prova | Solana | Sub-second finality, ~$0.0005 per attestation — the cost profile a high-frequency agent-receipt layer actually needs |

Each one stays where it started until real demand justifies expanding it
elsewhere. Contextio's mainnet and Prova's mainnet are both deliberately
narrower than their testnet builds for that same reason — gated on
evidence, not on a roadmap slide.

Most of my public work is either a protocol implementation I maintain or a
bug I found in something I depend on and then sent a patch for. Everything
below links to the actual issue, PR, or running service — no claim here
that you can't click and check yourself. Where something is still open or
unmerged, it's marked as such, not implied to be done.

I write it this dense on purpose. Every project below moves someone else's
funds or blocks their transaction, so I'd rather you check the receipts
than take my word for anything. If a claim here can't be clicked and
verified, it doesn't belong here.

---

## Highlights

Skip the rest if you only have 90 seconds — this is the material that
actually matters, each one a link, not a claim:

- **Found and fixed a crash in x402's own official conformance suite**,
  merged upstream the same week —
  [x402-foundation/x402#3228](https://github.com/x402-foundation/x402/pull/3228).
- **A skill PR survived ~16 real review rounds across 21 days before
  merging** —
  [stellar/stellar-dev-skill#97](https://github.com/stellar/stellar-dev-skill/pull/97) —
  because I kept addressing feedback instead of abandoning it.
- **When I was wrong, I said so and closed my own issue against myself**:
  [OpenZeppelin/stellar-contracts#839](https://github.com/OpenZeppelin/stellar-contracts/issues/839)
  turned out to be a construction bug in my own code, not a library gap —
  confirmed with the maintainer's help, not asserted.
- **KUMPLY's compliance contracts are live and verified on Avalanche**,
  Fuji testnet and mainnet C-Chain read-only beta —
  [`AttestationStore`](https://snowtrace.io/address/0xa116261Ed3a848A9E1cd34923D5A0442D1455F71)
  on Snowtrace, source at
  [kumplyprotocol/Kumply](https://github.com/kumplyprotocol/Kumply) — the
  one non-Stellar project in this profile with its own paper trail.
- **Every contract I ship is non-custodial by construction** — the
  client's own wallet signs, or a role that by contract design cannot move
  funds, never a key of mine that can. Detail and a real example under
  "How I work" below.
- **981 commits across these seven repos over 219 straight days**
  (1 Feb – 8 Sep 2026), pulled from `git log`, not typed in: 20.8% of them
  land on a weekend, 12.1% between 10pm and 6am local time. There's a real
  gap from 3am–6am — not claiming literal around-the-clock, the data just
  doesn't say that.
- **Two Stellar Community Fund Instawards, both delivered against real
  milestones**, not just awarded — the track record the rest of this
  profile's execution claims actually rest on.

---

## Activity

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://github-stats-extended.vercel.app/api?username=Eras256&show_icons=true&show=reviews,prs_merged,prs_merged_percentage&rank_icon=percentile&theme=dark">
  <img alt="Commits, pull requests, merged PRs, reviews and issues for Eras256" src="https://github-stats-extended.vercel.app/api?username=Eras256&show_icons=true&show=reviews,prs_merged,prs_merged_percentage&rank_icon=percentile">
</picture>

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://github-stats-extended.vercel.app/api/top-langs/?username=Eras256&layout=compact&langs_count=6&theme=dark">
  <img alt="Most used languages for Eras256" src="https://github-stats-extended.vercel.app/api/top-langs/?username=Eras256&layout=compact&langs_count=6">
</picture>

Both cards are rendered live from the GitHub API by
[github-stats-extended](https://github.com/stats-organization/github-stats-extended),
so the numbers move on their own rather than being typed in here (checked
live 2026-09-05, still serving). If a number here looks off against my
GitHub profile page or the tables further down, it's almost always scope,
not error: this card counts my own repos and public commits over the last
year, the profile page's contribution count adds PRs/issues/reviews and
private activity on top of that, and the per-project tables below are
all-time and repos-I-don't-own only — three different, narrower slices of
the same activity, not three inconsistent counts of the same thing.

---

## What I'm building

Periplo, Nirium, and Contextio are three separate Stellar products, not
three names for one thing — but they share real upstream dependencies
(same protocols, sometimes the literal same bug), so the contribution
tables further down attribute each fix to the specific project it came
from instead of merging them into one undifferentiated pile. If a note
says "this one's Nirium's, not Periplo's," that's the reason.

| Project | What it actually is |
| --- | --- |
| **[Periplo](https://github.com/Eras256/Periplo)** · [periplo.xyz](https://periplo.xyz) | An x402 payment facilitator for Stellar with a "Bazaar" discovery catalog, so an agent can find a payable service it has never seen before. Facilitator is live on `stellar:testnet` — [`GET /supported`](https://periplo-testnet.fly.dev/supported) responds without setup. Apache-2.0, TypeScript + Soroban. |
| **[Nirium](https://github.com/Eras256/Nirium)** · [nirium.xyz](https://nirium.xyz) | Autonomous treasury and machine-to-machine payments on Stellar — Soroban contracts in Rust, an x402 + MPP payment layer, and MCP integration. Non-custodial: the client's wallet signs, or a scoped `RebalanceManager` role that by contract design can't withdraw or move funds; Nirium itself never holds a key that can. Apache-2.0. |
| **[nirium-sdk](https://github.com/nirium-protocol/nirium-sdk)** | The TypeScript and Python packages plus CLI behind Nirium — x402 `pay`/`serve`, MPP session budgets, IPFS audit anchoring. Also where Nirium runs its own GrantFox bounty program (see below). Apache-2.0. |
| **[Contextio](https://github.com/contextio/Contextio)** · [contextio.xyz](https://contextio.xyz) | An AI agent that moves treasury and payroll funds for companies in Brazil, Argentina, and Colombia, binding every action to a verifiable Legal Context Protocol (LCP) document. Live on Stellar testnet (full autonomy) and mainnet (deliberately narrower: read-only data plus self-custody actions only, invitation-only while contracts await external audit). SEP-53 wallet sign-in. Originally a Stellar PULSO Hackathon submission, now aimed at the SCF Integration Track. Migrated from a personal repo to the `contextio` org. |
| **[nirium-pollar-adapter](https://github.com/nirium-protocol/nirium-pollar-adapter)** · [npm](https://www.npmjs.com/package/nirium-pollar-adapter) | Adapter that lets a wallet onboarded through the Pollar SDK pay x402 requests and anchor audit receipts. Published to npm, running against Stellar mainnet. MIT. |
| **[KUMPLY](https://github.com/kumplyprotocol/Kumply)** · [kumply.xyz](https://kumply.xyz) | On-chain KYC/KYB/KYA compliance attestations for Avalanche — no personal data stored on-chain, just `(tier, expiry, issuer, revocation status)`. Contracts live and verified on Fuji testnet (full read/write) and Avalanche mainnet C-Chain ([`AttestationStore`](https://snowtrace.io/address/0xa116261Ed3a848A9E1cd34923D5A0442D1455F71), read-only beta). 164 tests on every push. Apache-2.0. |
| **Vouch402** · [vouch402.xyz](https://www.vouch402.xyz) | x402-metered on-chain risk intelligence for agents on Base, with a built-in proof-of-fulfillment attestation layer. Full quote-to-attestation flow run end-to-end on **Base mainnet**, not just testnet: [settled payment](https://basescan.org/tx/0x6e44081aa3f05c73f6c9c32dc456f0231c3a690a33159765917ff096d138659c), [fulfillment attestation](https://basescan.org/tx/0xe2b5002c923bd9b49afce698f9d0f7ebef66d24f8c1eafd22c0a64e7c5f7ebb7), [EAS schema](https://base.easscan.org/schema/view/0xfbd6000caf2aaa6f7e269c74b45a0f891ddfe3381356d8ebaefc46b1a524abac). Client packages on npm: [`vouch402-sdk`](https://www.npmjs.com/package/vouch402-sdk), [`vouch402`](https://www.npmjs.com/package/vouch402) (CLI), [`vouch402-mcp-server`](https://www.npmjs.com/package/vouch402-mcp-server). Source repo is private. |
| **[Prova](https://github.com/Prova-Solana/Prova)** · [theprova.xyz](https://www.theprova.xyz) | Cryptographic, on-chain receipts for AI agent actions on Solana — one `attest()` call, one Ed25519-sealed record, verifiable without trusting the operator's own logs. **Solana devnet today**, not mainnet — stated plainly since the site's own copy could be read otherwise. SDKs (`prova-agent-sdk` etc.) published on npm at `0.1.7`. Apache-2.0. |

---

## Periplo — upstream contributions

Snapshot below is a live re-check as of **2026-09-05**; the search links at
the bottom always supersede it. Full first-hand narrative with transaction
hashes and reproduction steps lives in
[`Eras256/Periplo`'s own README](https://github.com/Eras256/Periplo#readme).

### Merged

| PR | Repo | Merged |
| --- | --- | --- |
| [#3228](https://github.com/x402-foundation/x402/pull/3228) — scope EVM/SVM client signer derivation to the selected `--families`, fixing a crash in the official e2e conformance suite | `x402-foundation/x402` | 2026-08-31 — authored by me, merged by @phdargen. Closes [#3187](https://github.com/x402-foundation/x402/issues/3187), which I also filed. An earlier attempt, [#3219](https://github.com/x402-foundation/x402/pull/3219), was closed unmerged and superseded by this one. |
| [#103](https://github.com/stellar/stellar-dev-skill/pull/103) — point `ECOSYSTEM_CARDS` `copyValue` at raw content, not GitHub's blob HTML page | `stellar/stellar-dev-skill` | 2026-08-28, by @kaankacar |
| [#3306](https://github.com/x402-foundation/x402/pull/3306) — add a dedicated `extension_responses`/`extensionResponses` field instead of leaking `EXTENSION-RESPONSES` data via the buyer-facing `extensions` field | `x402-foundation/x402` | 2026-08-31, by @phdargen. Closes [#3270](https://github.com/x402-foundation/x402/issues/3270), which I filed. Not my code — full detail below. |
| [#97](https://github.com/stellar/stellar-dev-skill/pull/97) — production patterns for x402 + MPP | `stellar/stellar-dev-skill` | 2026-09-05, by @kaankacar — this one's Nirium's, not Periplo's; see the Nirium section below |

### Open fix PRs

| PR | Repo | Fixes |
| --- | --- | --- |
| [#3215](https://github.com/x402-foundation/x402/pull/3215) — derive one wildcard pattern per namespace, not one per registration | `x402-foundation/x402` | [#3172](https://github.com/x402-foundation/x402/issues/3172) |
| [#3138](https://github.com/x402-foundation/x402/pull/3138) — use the raw resource URL as canonical for opaque-origin schemes | `x402-foundation/x402` | [#3121](https://github.com/x402-foundation/x402/issues/3121) |
| [#3098](https://github.com/x402-foundation/x402/pull/3098) — `upto` scheme implementation spec for Stellar | `x402-foundation/x402` | [#3097](https://github.com/x402-foundation/x402/issues/3097) |
| [#1672](https://github.com/stellar/js-stellar-sdk/pull/1672) — walk every CAP-71 delegate node, not just the top level | `stellar/js-stellar-sdk` | [#1655](https://github.com/stellar/js-stellar-sdk/issues/1655). Blocked/mergeable pending review; nudged 2026-08-31 that this is no longer theoretical now that v17.0.0/v17.0.1 made CAP-71 v2 the default on both ends of the auth flow. |
| [#844](https://github.com/OpenZeppelin/stellar-contracts/pull/844) — drop the Lazy-mode expiration check that validates the wrong value | `OpenZeppelin/stellar-contracts` | [#840](https://github.com/OpenZeppelin/stellar-contracts/issues/840) — this one is Nirium's, not Periplo's; see the Nirium section below. Was mergeable and CI-green since Aug 24; picked up a merge conflict since (`CONFLICTING`/`DIRTY` as of 2026-09-05) — needs a rebase, still no maintainer response to the Aug 31 nudge. |
| [#4960](https://github.com/otter-sec/anchor/pull/4960) — bump `heck` 0.3 → 0.5 to drop the unbounded edition2024 landmine | `otter-sec/anchor` | Unrelated dependency fix, not tied to either product |

### Bug reports that landed

- **[x402#3171](https://github.com/x402-foundation/x402/issues/3171)** — `paymentRequirementsMatchAccepted` threw on a missing/null `payload.accepted`. I found and reported it; the code fix was written by [@JasonColapietro](https://github.com/JasonColapietro) in [#3180](https://github.com/x402-foundation/x402/pull/3180), merged 2026-08-17. The merged patch is his work, not mine — my part was the report.
- **[x402#3270](https://github.com/x402-foundation/x402/issues/3270)** — `HTTPFacilitatorClient.settle()/verify()` decoded the `EXTENSION-RESPONSES` header and then discarded it. I fixed this on Periplo's own side the same day rather than waiting on upstream. **Closed 2026-08-31** — not the way it first looked like it would close. The actual fix was the maintainer's own separate PR, [#3306](https://github.com/x402-foundation/x402/pull/3306) (Python, @phdargen), introducing a dedicated `extension_responses`/`extensionResponses` field instead of reusing `extensions` — explicitly rejecting that shape (which my own workaround used, and so did the two community PRs this finding first prompted) as leaking a server-only sidechannel into buyer-facing data. [#3278](https://github.com/x402-foundation/x402/pull/3278) (TypeScript, @Bartok9) was revised to match before merging separately; [#3301](https://github.com/x402-foundation/x402/pull/3301) (Go, @wnjoon) and [PhilBot402/x402#4](https://github.com/PhilBot402/x402/pull/4) (Python, draft) remain open, likely needing the same adjustment. My own `/settle` still uses the old shape — migrating once `@x402/core` actually ships the new field (not yet: `latest` is still `2.24.0`, predating this fix).
- **[eas-sdk#132](https://github.com/ethereum-attestation-service/eas-sdk/issues/132)** — `getUIDsFromAttestReceipt` trusted log `topic0` without checking the emitter address, found while auditing the library Vouch402 calls for every attestation it emits. Vouch402 itself isn't affected (no resolver, no `multiAttest()` calls) — a library-level finding, not a gap in that project. *Closed as completed* by the maintainer 2026-08-27, fixed in [eas-sdk 2.10.0](https://www.npmjs.com/package/@ethereum-attestation-service/eas-sdk/v/2.10.0).
- **[OpenZeppelin/stellar-contracts#839](https://github.com/OpenZeppelin/stellar-contracts/issues/839)** — hit `UnreachableCodeReached` combining `Signer::Delegated` with a `CallContract` rule, and opened this not sure yet whether it was our construction or a real library gap. **Closed 2026-09-02, resolution: ours.** With help from the maintainer (@brozorec) clarifying `execute()`'s self-authorization is meant only for self-admin operations, hand-constructing both auth entries (the smart account's own plus the delegate's) authorizes and confirms correctly on-chain — no library fix needed, the trap was in how we were building the auth entry, not the library.

### Still open, awaiting maintainer response

`x402-foundation/x402` — [#3121](https://github.com/x402-foundation/x402/issues/3121), [#3148](https://github.com/x402-foundation/x402/issues/3148), [#3169](https://github.com/x402-foundation/x402/issues/3169); `stellar/js-stellar-sdk` — [#1681](https://github.com/stellar/js-stellar-sdk/issues/1681), [#1683](https://github.com/stellar/js-stellar-sdk/issues/1683).

---

## Nirium — upstream contributions and GrantFox bounty program

### Upstream, to repos Nirium doesn't own

| Item | Repo | Status |
| --- | --- | --- |
| [#96](https://github.com/stellar/stellar-dev-skill/pull/96) — add Nirium to community skills | `stellar/stellar-dev-skill` | Merged 2026-08-15 |
| [#97](https://github.com/stellar/stellar-dev-skill/pull/97) — production patterns for x402 + MPP | `stellar/stellar-dev-skill` | **Merged 2026-09-05**, by @kaankacar, after ~16 real review rounds across 21 days. An earlier version, [#14](https://github.com/stellar/stellar-dev-skill/pull/14), was closed unmerged and superseded by this one |
| [#844](https://github.com/OpenZeppelin/stellar-contracts/pull/844) — fix(fee-abstraction): drop Lazy-mode expiration check that validates the wrong value | `OpenZeppelin/stellar-contracts` | Open, fixes [#840](https://github.com/OpenZeppelin/stellar-contracts/issues/840). Was mergeable and CI-green since Aug 24; picked up a merge conflict since (needs a rebase, as of 2026-09-05), still no maintainer response to the Aug 31 nudge |
| [#47](https://github.com/OpenZeppelin/relayer-plugin-x402-facilitator/issues/47) — mainnet sponsor/relayer account silent 500+ hours | `OpenZeppelin/relayer-plugin-x402-facilitator` | Open. As of 2026-09-05 this is four independent integrators (Nirium's own fee-payer, AgentPayments.fi, NovaCorpAI, and Lexirieru/stellarouter) converging on the same finding from four directions, with no OZ response yet |
| [#58](https://github.com/stellar/stellar-mpp-sdk/issues/58) — allow an external SEP-43 signer instead of a raw secret key | `stellar/stellar-mpp-sdk` | Open |
| [#30](https://github.com/pollar-xyz/pollar-apps/pull/30) — Nirium x402 adapter demo (`apps/nirium`) | `pollar-xyz/pollar-apps` | **Merged 2026-08-31**, by @aleregex |

### GrantFox bounty program (`nirium-protocol/nirium-sdk`)

This is Nirium's own repo, so these are bounties Nirium posted, not upstream
contributions Nirium made elsewhere. Full live audit as of **2026-09-05**:
**44 issues** across three campaigns, 42 real bounty asks (2 unlabeled
resource suggestions aren't bounties) — 20 delivered inside `nirium-sdk`
itself, 2 delivered externally and still awaiting that project's own
review, 4 closed and administratively recreated under a later campaign,
16 closed without delivery.

<details>
<summary>Full breakdown — every delivery, who opened it, and the two that are my cofounder's</summary>

- **20 delivered**, each with a merged PR inside `nirium-sdk` itself.
- **2 delivered externally**, as real PRs against the target repo, both
  still open and awaiting that project's own review: [#75 → Fundable-Protocol/fundable-sdk#8](https://github.com/Fundable-Protocol/fundable-sdk/pull/8) and [#76 → wejoona/api#23](https://github.com/wejoona/api/pull/23). Both were opened by the same bounty contributor, **@Santia2004** — not by this account.
- **4 were closed and administratively recreated** under a later campaign, same ask, new issue number: [#29→#43](https://github.com/nirium-protocol/nirium-sdk/issues/43), [#30→#44](https://github.com/nirium-protocol/nirium-sdk/issues/44), [#31→#45](https://github.com/nirium-protocol/nirium-sdk/issues/45), [#32→#46](https://github.com/nirium-protocol/nirium-sdk/issues/46).
- **16 closed without any delivery.**

A few of the stronger merged deliveries, cited by bounty issue alongside the
PR that closed it and who actually opened that PR, since that's better
evidence than a bare link:

| Bounty issue | Delivering PR | Author |
| --- | --- | --- |
| [#39](https://github.com/nirium-protocol/nirium-sdk/issues/39) — harden the Python WebSocket signals client | [#47](https://github.com/nirium-protocol/nirium-sdk/pull/47), merged | @Simultech369 — external |
| [#51](https://github.com/nirium-protocol/nirium-sdk/issues/51) — GitHub Action to verify a Nirium audit-CID in CI | [#80](https://github.com/nirium-protocol/nirium-sdk/pull/80), merged | @Simultech369 — external |
| [#65](https://github.com/nirium-protocol/nirium-sdk/issues/65) — audit trail forensic export bridge | [#69](https://github.com/nirium-protocol/nirium-sdk/pull/69), merged | @Santia2004 — external |

Two more from that same list are worth pulling out separately rather than
folding into "external bounty deliveries," because they aren't that —
they're my cofounder's own first shipped code for this project, done
through the same GrantFox process rather than around it:
[#44](https://github.com/nirium-protocol/nirium-sdk/issues/44) (CLI
`pay`/`serve` commands) via
[#62](https://github.com/nirium-protocol/nirium-sdk/pull/62), and
[#45](https://github.com/nirium-protocol/nirium-sdk/issues/45) (resilient
reconnecting WebSocket signals client) via
[#61](https://github.com/nirium-protocol/nirium-sdk/pull/61) — both merged,
both by [Monserrat Mendoza](https://github.com/M0nsxx).

One more worth naming separately because it isn't a bounty at all: **[#81](https://github.com/nirium-protocol/nirium-sdk/issues/81)** was a real fail-open vulnerability in the Next.js x402 example (any `X-PAYMENT` header granted access, valid or not), reported by an outside party and fixed the same way as everything above — a merged PR, [#84](https://github.com/nirium-protocol/nirium-sdk/pull/84).

Separately, [nirium-pollar-adapter#1](https://github.com/nirium-protocol/nirium-pollar-adapter/pull/1) (deferred wallet funding) merged 2026-08-29, and [nirium-sdk#68](https://github.com/nirium-protocol/nirium-sdk/pull/68) (restore `viem` as a direct dependency) merged 2026-08-26 — both real fixes by this account, not bounty deliveries.

</details>

---

## Contextio

Contextio moved from a personal repo (`Eras256/Contextio`) to its own org,
`contextio` — `Eras256/Contextio` now resolves to
[`contextio/Contextio`](https://github.com/contextio/Contextio). The planner
logic behind its treasury/payroll rebalance decisions was extracted into a
separate private repo, `contextio/contextio-agent-planner`, consumed by the
main repo as a private git dependency.

**Contextio also runs a bounty-style program**, though not GrantFox-labeled
like Nirium's: five open issues in `contextio/Contextio`, all opened by this
account, none delivered yet — two already have competing external PRs
open and unreviewed.

<details>
<summary>All five issues and the two open external PRs</summary>

[#1](https://github.com/contextio/Contextio/issues/1) (Python client parity),
[#2](https://github.com/contextio/Contextio/issues/2) (Go client parity),
[#3](https://github.com/contextio/Contextio/issues/3) (standalone offline LCP
conformance verifier),
[#4](https://github.com/contextio/Contextio/issues/4) (GitHub Action to
verify a published LCP document in CI), and
[#5](https://github.com/contextio/Contextio/issues/5) (CONTRIBUTING.md).
Issue #5 already has two competing external submissions, both open and
unreviewed: [#6](https://github.com/contextio/Contextio/pull/6) by
@mayankbohara0-dev and [#7](https://github.com/contextio/Contextio/pull/7)
by @CharoenwitKunna.

</details>

**Upstream, to `stellar/stellar-dev-skill`** (not owned by Contextio): three
merged PRs adding and refining the Contextio SDK's community-skill listing —
[#98](https://github.com/stellar/stellar-dev-skill/pull/98),
[#101](https://github.com/stellar/stellar-dev-skill/pull/101), and
[#102](https://github.com/stellar/stellar-dev-skill/pull/102), all merged
2026-08-15.

**Beyond that, I found no upstream contribution from this account to any
other external repo specifically for Contextio.** Said plainly rather than
padded: Contextio's public footprint on this account is its own repo plus
that one skill listing, not a wider trail of dependency fixes the way
Periplo and Nirium have.

---

## Elsewhere — KUMPLY, Vouch402, Prova

Same standard as above, smaller footprint since these are newer:

**KUMPLY (Avalanche)** — three open bug reports against a third-party
community skills repo, [Ayomisco/avaxskills](https://github.com/Ayomisco/avaxskills),
found while building on top of it: [#2](https://github.com/Ayomisco/avaxskills/issues/2)
(a subnet-deployment skill cites CLI commands that don't exist in the real
`ava-labs/avalanche-cli`), [#3](https://github.com/Ayomisco/avaxskills/issues/3)
(a precompiles skill has the wrong genesis key name for `TxAllowList`),
[#4](https://github.com/Ayomisco/avaxskills/issues/4) (a wagmi skill cites
an outdated version and a deprecated hook). All still open.

**Vouch402 (Base)** — [base/skills#152](https://github.com/base/skills/pull/152),
an open PR adding a Vouch402 plugin listing to Base's own community skills
catalog, same genre as the `stellar-dev-skill` PRs above. Also
[eas-sdk#132](https://github.com/ethereum-attestation-service/eas-sdk/issues/132)
(closed, fixed — detail above) and
[foundry-rs/foundry#16209](https://github.com/foundry-rs/foundry/issues/16209)
(`cast wallet new <name>` still fails with a bare account name, open),
both found auditing tooling Vouch402 depends on.

**Prova (Solana)** — [otter-sec/anchor#4960](https://github.com/otter-sec/anchor/pull/4960),
an open PR bumping `heck` 0.3 → 0.5 to drop an unbounded `edition2024`
dependency landmine in the Anchor framework Prova's on-chain program is
built on. Not merged yet.

---

## Other dependency bug reports

Found using these libraries for Periplo, Nirium, or Contextio, but not
clearly attributable to a single one:

- **[Creit-Tech/Stellar-Wallets-Kit#105](https://github.com/Creit-Tech/Stellar-Wallets-Kit/issues/105)** — `signMessage()`'s JSDoc says SEP-43 hex, Freighter returns base64. Open.

---

## Stack

![Stellar](https://img.shields.io/badge/Stellar-000000?style=flat-square&logo=stellar&logoColor=white)
![Soroban](https://img.shields.io/badge/Soroban-1f6feb?style=flat-square)
![Avalanche](https://img.shields.io/badge/Avalanche-E84142?style=flat-square&logo=avalanche&logoColor=white)
![Base](https://img.shields.io/badge/Base-0052FF?style=flat-square&logo=coinbase&logoColor=white)
![Solana](https://img.shields.io/badge/Solana-9945FF?style=flat-square&logo=solana&logoColor=white)
![x402](https://img.shields.io/badge/x402-teal?style=flat-square)
![Rust](https://img.shields.io/badge/Rust-000000?style=flat-square&logo=rust&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white)
![Solidity](https://img.shields.io/badge/Solidity-363636?style=flat-square&logo=solidity&logoColor=white)

**Protocols** — x402, MPP (Charge and Channel), SEP-41 / SAC, SEP-43,
SEP-53, CAP-71 delegated auth, MCP, EAS (Ethereum Attestation Service)
**Chains** — Stellar/Soroban (Periplo, Nirium, Contextio), Avalanche
(KUMPLY), Base (Vouch402), Solana (Prova)

---

## How I work

- Small PRs, one root cause each, with the reproduction in the description.
- If I file a bug in a dependency, I try to open the fix alongside it when I
  can —
  [#3187 → #3228](https://github.com/x402-foundation/x402/pull/3228),
  [#840 → #844](https://github.com/OpenZeppelin/stellar-contracts/pull/844).
  When someone else beats me to the fix, I say so and name them —
  [#3171 → #3180 by @JasonColapietro](https://github.com/x402-foundation/x402/pull/3180),
  [#3270 → #3306 by @phdargen](https://github.com/x402-foundation/x402/pull/3306) — the maintainer's own fix, rejecting the field shape my own workaround used.
- When I'm not sure whether it's my bug or theirs, I say so in the issue
  rather than asserting a diagnosis I can't back
  ([#839](https://github.com/OpenZeppelin/stellar-contracts/issues/839) is
  an example).
- Every contract I ship is non-custodial by construction: the client signs,
  or a role that by contract design can't move funds — never a key of ours
  that can.

---

## Search these live yourself

Snapshot above is accurate as of **2026-09-05**; these always supersede it:
[all my PRs](https://github.com/search?q=author%3AEras256+is%3Apr&type=pullrequests)
·
[all my issues](https://github.com/search?q=author%3AEras256+is%3Aissue&type=issues)
·
[nirium-sdk's full bounty board](https://github.com/nirium-protocol/nirium-sdk/issues?q=is%3Aissue)
·
[Contextio's open issues](https://github.com/contextio/Contextio/issues)

---

## Reach me

Open an issue on any repo above, or start with
[periplo.xyz](https://periplo.xyz) · [nirium.xyz](https://nirium.xyz) ·
[contextio.xyz](https://contextio.xyz)
