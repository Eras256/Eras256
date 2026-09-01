# `Eras256`

I build payment infrastructure on **Stellar / Soroban**: x402 and MPP
payment rails, service discovery, and non-custodial treasury automation.
This account is the personal contributor identity behind three real
projects — **Periplo**, **Nirium**, and **Contextio** — plus the upstream
fixes and bug reports that came out of building them.

Most of my public work is either a protocol implementation I maintain or a
bug I found in something I depend on and then sent a patch for. Everything
below links to the actual issue, PR, or running service — no claim here
that you can't click and check yourself. Where something is still open or
unmerged, it's marked as such, not implied to be done.

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
live 2026-08-31, still serving). Some caveats worth stating, since several
of these figures look like they disagree and don't:

- The counts above include my own repositories. The tables further down
  count only repositories I don't own, so those numbers are smaller by
  design.
- **Commits and contributions are different metrics.** The card's *Total
  Commits (last year)* counts public commits only. The number on my GitHub
  profile page is the *contribution* total, which adds pull requests,
  issues and reviews on top of commits — and private-repo activity too,
  which GitHub lets you surface as a count without exposing the
  repositories. A much larger number there is the two metrics measuring
  different things, not an error in either.
- *Contributed to (last year)* on the card is a twelve-month count over
  every contribution type. The per-project tables below are all-time and
  count only repositories where I opened a PR or an issue.
- Language shares are measured across my non-forked repositories, not
  across every commit I've pushed somewhere else.

---

## What I'm building

| Project | What it actually is |
| --- | --- |
| **[Periplo](https://github.com/Eras256/Periplo)** · [periplo.xyz](https://periplo.xyz) | An x402 payment facilitator for Stellar with a "Bazaar" discovery catalog, so an agent can find a payable service it has never seen before. Facilitator is live on `stellar:testnet` — [`GET /supported`](https://periplo-testnet.fly.dev/supported) responds without setup. Apache-2.0, TypeScript + Soroban. |
| **[Nirium](https://github.com/Eras256/Nirium)** · [nirium.xyz](https://nirium.xyz) | Autonomous treasury and machine-to-machine payments on Stellar — Soroban contracts in Rust, an x402 + MPP payment layer, and MCP integration. Non-custodial: the client's wallet signs, or a scoped `RebalanceManager` role that by contract design can't withdraw or move funds; Nirium itself never holds a key that can. Apache-2.0. |
| **[nirium-sdk](https://github.com/nirium-protocol/nirium-sdk)** | The TypeScript and Python packages plus CLI behind Nirium — x402 `pay`/`serve`, MPP session budgets, IPFS audit anchoring. Also where Nirium runs its own GrantFox bounty program (see below). Apache-2.0. |
| **[Contextio](https://github.com/contextio/Contextio)** · [contextio.xyz](https://contextio.xyz) | An AI agent that moves treasury and payroll funds for companies in Brazil, Argentina, and Colombia, binding every action to a verifiable Legal Context Protocol (LCP) document. Live on Stellar testnet (full autonomy) and mainnet (deliberately narrower: read-only data plus self-custody actions only, invitation-only while contracts await external audit). SEP-53 wallet sign-in. Originally a Stellar PULSO Hackathon submission, now aimed at the SCF Integration Track. Migrated from a personal repo to the `contextio` org. |
| **[nirium-pollar-adapter](https://github.com/nirium-protocol/nirium-pollar-adapter)** · [npm](https://www.npmjs.com/package/nirium-pollar-adapter) | Adapter that lets a wallet onboarded through the Pollar SDK pay x402 requests and anchor audit receipts. Published to npm, running against Stellar mainnet. MIT. |

---

## Periplo — upstream contributions

Snapshot below is a live re-check as of **2026-08-31**; the search links at
the bottom always supersede it. Full first-hand narrative with transaction
hashes and reproduction steps lives in
[`Eras256/Periplo`'s own README](https://github.com/Eras256/Periplo#readme).

### Merged

| PR | Repo | Merged |
| --- | --- | --- |
| [#3228](https://github.com/x402-foundation/x402/pull/3228) — scope EVM/SVM client signer derivation to the selected `--families`, fixing a crash in the official e2e conformance suite | `x402-foundation/x402` | 2026-08-31 — authored by me, merged by @phdargen. Closes [#3187](https://github.com/x402-foundation/x402/issues/3187), which I also filed. An earlier attempt, [#3219](https://github.com/x402-foundation/x402/pull/3219), was closed unmerged and superseded by this one. |
| [#103](https://github.com/stellar/stellar-dev-skill/pull/103) — point `ECOSYSTEM_CARDS` `copyValue` at raw content, not GitHub's blob HTML page | `stellar/stellar-dev-skill` | 2026-08-28, by @kaankacar |
| [#3306](https://github.com/x402-foundation/x402/pull/3306) — add a dedicated `extension_responses`/`extensionResponses` field instead of leaking `EXTENSION-RESPONSES` data via the buyer-facing `extensions` field | `x402-foundation/x402` | 2026-08-31, by @phdargen. Closes [#3270](https://github.com/x402-foundation/x402/issues/3270), which I filed. Not my code — full detail below. |

### Open fix PRs

| PR | Repo | Fixes |
| --- | --- | --- |
| [#3215](https://github.com/x402-foundation/x402/pull/3215) — derive one wildcard pattern per namespace, not one per registration | `x402-foundation/x402` | [#3172](https://github.com/x402-foundation/x402/issues/3172) |
| [#3138](https://github.com/x402-foundation/x402/pull/3138) — use the raw resource URL as canonical for opaque-origin schemes | `x402-foundation/x402` | [#3121](https://github.com/x402-foundation/x402/issues/3121) |
| [#3098](https://github.com/x402-foundation/x402/pull/3098) — `upto` scheme implementation spec for Stellar | `x402-foundation/x402` | [#3097](https://github.com/x402-foundation/x402/issues/3097) |
| [#1672](https://github.com/stellar/js-stellar-sdk/pull/1672) — walk every CAP-71 delegate node, not just the top level | `stellar/js-stellar-sdk` | [#1655](https://github.com/stellar/js-stellar-sdk/issues/1655). Blocked/mergeable pending review; nudged 2026-08-31 that this is no longer theoretical now that v17.0.0/v17.0.1 made CAP-71 v2 the default on both ends of the auth flow. |
| [#844](https://github.com/OpenZeppelin/stellar-contracts/pull/844) — drop the Lazy-mode expiration check that validates the wrong value | `OpenZeppelin/stellar-contracts` | [#840](https://github.com/OpenZeppelin/stellar-contracts/issues/840) — this one is Nirium's, not Periplo's; see the Nirium section below |
| [#97](https://github.com/stellar/stellar-dev-skill/pull/97) — production patterns for x402 + MPP | `stellar/stellar-dev-skill` | Nirium's, not Periplo's; see below |
| [#4960](https://github.com/otter-sec/anchor/pull/4960) — bump `heck` 0.3 → 0.5 to drop the unbounded edition2024 landmine | `otter-sec/anchor` | Unrelated dependency fix, not tied to either product |

### Bug reports that landed

- **[x402#3171](https://github.com/x402-foundation/x402/issues/3171)** — `paymentRequirementsMatchAccepted` threw on a missing/null `payload.accepted`. I found and reported it; the code fix was written by [@JasonColapietro](https://github.com/JasonColapietro) in [#3180](https://github.com/x402-foundation/x402/pull/3180), merged 2026-08-17. The merged patch is his work, not mine — my part was the report.
- **[x402#3270](https://github.com/x402-foundation/x402/issues/3270)** — `HTTPFacilitatorClient.settle()/verify()` decoded the `EXTENSION-RESPONSES` header and then discarded it. I fixed this on Periplo's own side the same day rather than waiting on upstream. **Closed 2026-08-31** — not the way it first looked like it would close. The actual fix was the maintainer's own separate PR, [#3306](https://github.com/x402-foundation/x402/pull/3306) (Python, @phdargen), introducing a dedicated `extension_responses`/`extensionResponses` field instead of reusing `extensions` — explicitly rejecting that shape (which my own workaround used, and so did the two community PRs this finding first prompted) as leaking a server-only sidechannel into buyer-facing data. [#3278](https://github.com/x402-foundation/x402/pull/3278) (TypeScript, @Bartok9) was revised to match before merging separately; [#3301](https://github.com/x402-foundation/x402/pull/3301) (Go, @wnjoon) and [PhilBot402/x402#4](https://github.com/PhilBot402/x402/pull/4) (Python, draft) remain open, likely needing the same adjustment. My own `/settle` still uses the old shape — migrating once `@x402/core` actually ships the new field (not yet: `latest` is still `2.24.0`, predating this fix).
- **[eas-sdk#132](https://github.com/ethereum-attestation-service/eas-sdk/issues/132)** — `getUIDsFromAttestReceipt` trusted log `topic0` without checking the emitter address. *Closed as completed.* (General dependency finding, not tied to a specific product below.)

### Still open, awaiting maintainer response

`x402-foundation/x402` — [#3121](https://github.com/x402-foundation/x402/issues/3121), [#3148](https://github.com/x402-foundation/x402/issues/3148), [#3169](https://github.com/x402-foundation/x402/issues/3169); `stellar/js-stellar-sdk` — [#1681](https://github.com/stellar/js-stellar-sdk/issues/1681), [#1683](https://github.com/stellar/js-stellar-sdk/issues/1683); `OpenZeppelin/stellar-contracts` — [#839](https://github.com/OpenZeppelin/stellar-contracts/issues/839) (CAP-71 delegated auth trap hit while building Periplo's smart-account extension).

---

## Nirium — upstream contributions and GrantFox bounty program

### Upstream, to repos Nirium doesn't own

| Item | Repo | Status |
| --- | --- | --- |
| [#96](https://github.com/stellar/stellar-dev-skill/pull/96) — add Nirium to community skills | `stellar/stellar-dev-skill` | Merged 2026-08-15 |
| [#97](https://github.com/stellar/stellar-dev-skill/pull/97) — production patterns for x402 + MPP | `stellar/stellar-dev-skill` | Open. An earlier version, [#14](https://github.com/stellar/stellar-dev-skill/pull/14), was closed unmerged and superseded by this one |
| [#844](https://github.com/OpenZeppelin/stellar-contracts/pull/844) — fix(fee-abstraction): drop Lazy-mode expiration check that validates the wrong value | `OpenZeppelin/stellar-contracts` | Open, fixes [#840](https://github.com/OpenZeppelin/stellar-contracts/issues/840). Mergeable and CI-green since Aug 24; nudged for review 2026-08-31 |
| [#47](https://github.com/OpenZeppelin/relayer-plugin-x402-facilitator/issues/47) — mainnet sponsor/relayer account silent 510+ hours | `OpenZeppelin/relayer-plugin-x402-facilitator` | Open. As of 2026-08-31 this is three independent integrators (Nirium's own fee-payer, AgentPayments.fi, and NovaCorpAI) converging on the same finding from three directions, with no OZ response yet |
| [#58](https://github.com/stellar/stellar-mpp-sdk/issues/58) — allow an external SEP-43 signer instead of a raw secret key | `stellar/stellar-mpp-sdk` | Open |
| [#30](https://github.com/pollar-xyz/pollar-apps/pull/30) — Nirium x402 adapter demo (`apps/nirium`) | `pollar-xyz/pollar-apps` | Open, awaiting Pollar's own review as of 2026-08-31 |

### GrantFox bounty program (`nirium-protocol/nirium-sdk`)

This is Nirium's own repo, so these are bounties Nirium posted, not upstream
contributions Nirium made elsewhere. Full live audit as of **2026-08-31**:
**44 issues** across three campaigns (Official Campaign, FWC26, Third
Campaign). 42 of those are real bounty asks (the other 2 are unlabeled
resource suggestions, not bounties). Of the 42 bounty asks:

- **20 delivered**, each with a merged PR inside `nirium-sdk` itself.
- **2 delivered externally**, as real PRs against the target repo, both
  still open and awaiting that project's own review: [#75 → Fundable-Protocol/fundable-sdk#8](https://github.com/Fundable-Protocol/fundable-sdk/pull/8) and [#76 → wejoona/api#23](https://github.com/wejoona/api/pull/23). Both were opened by the same bounty contributor, **@Santia2004** — not by this account.
- **4 were closed and administratively recreated** under a later campaign, same ask, new issue number: [#29→#43](https://github.com/nirium-protocol/nirium-sdk/issues/43), [#30→#44](https://github.com/nirium-protocol/nirium-sdk/issues/44), [#31→#45](https://github.com/nirium-protocol/nirium-sdk/issues/45), [#32→#46](https://github.com/nirium-protocol/nirium-sdk/issues/46).
- **16 closed without any delivery.**

A few of the stronger merged deliveries, cited by bounty issue alongside the
PR that closed it, since that's better evidence than a bare PR link:

| Bounty issue | Delivering PR |
| --- | --- |
| [#39](https://github.com/nirium-protocol/nirium-sdk/issues/39) — harden the Python WebSocket signals client | [#47](https://github.com/nirium-protocol/nirium-sdk/pull/47), merged |
| [#44](https://github.com/nirium-protocol/nirium-sdk/issues/44) — `nirium` CLI `pay`/`serve` commands | [#62](https://github.com/nirium-protocol/nirium-sdk/pull/62), merged |
| [#45](https://github.com/nirium-protocol/nirium-sdk/issues/45) — resilient reconnecting WebSocket signals client | [#61](https://github.com/nirium-protocol/nirium-sdk/pull/61), merged |
| [#51](https://github.com/nirium-protocol/nirium-sdk/issues/51) — GitHub Action to verify a Nirium audit-CID in CI | [#80](https://github.com/nirium-protocol/nirium-sdk/pull/80), merged |
| [#65](https://github.com/nirium-protocol/nirium-sdk/issues/65) — audit trail forensic export bridge | [#69](https://github.com/nirium-protocol/nirium-sdk/pull/69), merged |

One more worth naming separately because it isn't a bounty at all: **[#81](https://github.com/nirium-protocol/nirium-sdk/issues/81)** was a real fail-open vulnerability in the Next.js x402 example (any `X-PAYMENT` header granted access, valid or not), reported by an outside party and fixed the same way as everything above — a merged PR, [#84](https://github.com/nirium-protocol/nirium-sdk/pull/84).

Separately, [nirium-pollar-adapter#1](https://github.com/nirium-protocol/nirium-pollar-adapter/pull/1) (deferred wallet funding) merged 2026-08-29, and [nirium-sdk#68](https://github.com/nirium-protocol/nirium-sdk/pull/68) (restore `viem` as a direct dependency) merged 2026-08-26 — both real fixes by this account, not bounty deliveries.

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
account, none delivered yet —
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

## Other dependency bug reports

Found using these libraries for one of the three projects above, but not
clearly attributable to a single one:

- **[Creit-Tech/Stellar-Wallets-Kit#105](https://github.com/Creit-Tech/Stellar-Wallets-Kit/issues/105)** — `signMessage()`'s JSDoc says SEP-43 hex, Freighter returns base64. Open.
- **[foundry-rs/foundry#16209](https://github.com/foundry-rs/foundry/issues/16209)** — `cast wallet new <name>` still fails with a bare account name. Open.

---

## Stack

![Stellar](https://img.shields.io/badge/Stellar-000000?style=flat-square&logo=stellar&logoColor=white)
![Soroban](https://img.shields.io/badge/Soroban-1f6feb?style=flat-square)
![x402](https://img.shields.io/badge/x402-teal?style=flat-square)
![Rust](https://img.shields.io/badge/Rust-000000?style=flat-square&logo=rust&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white)

**Protocols** — x402, MPP (Charge and Channel), SEP-41 / SAC, SEP-43,
SEP-53, CAP-71 delegated auth, MCP
**Chains** — Stellar / Soroban primarily; some EVM and Solana work

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

Snapshot above is accurate as of **2026-08-31**; these always supersede it:
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
