# `Eras256`

I build payment infrastructure on **Stellar / Soroban**: x402 and MPP
payment rails, service discovery, and non-custodial treasury automation.

Most of my public work is either a protocol implementation I maintain or a
bug I found in something I depend on and then sent a patch for. Everything
below links to the actual issue, PR, or running service — no claim here
that you can't click and check yourself.

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
so the numbers move on their own rather than being typed in here. Some
caveats worth stating, since several of these figures look like they
disagree and don't:

- The counts above include my own repositories. The upstream table further
  down counts only repositories I don't own, so its numbers are smaller by
  design.
- **Commits and contributions are different metrics.** The card's *Total
  Commits (last year)* counts public commits only. The number on my GitHub
  profile page is the *contribution* total, which adds pull requests,
  issues and reviews on top of commits — and private-repo activity too,
  which GitHub lets you surface as a count without exposing the
  repositories. A much larger number there is the two metrics measuring
  different things, not an error in either.
- *Contributed to (last year)* on the card is a twelve-month count over
  every contribution type. The "19 repositories" in the upstream table is
  all-time and counts only repositories where I opened a PR or an issue.
  Different window, different definition.
- Language shares are measured across my non-forked repositories, not
  across every commit I've pushed somewhere else.

---

## What I'm building

| Project | What it actually is |
| --- | --- |
| **[Periplo](https://github.com/Eras256/Periplo)** · [periplo.xyz](https://periplo.xyz) | An x402 payment facilitator for Stellar with a "Bazaar" discovery catalog, so an agent can find a payable service it has never seen before. Facilitator is live on `stellar:testnet` — [`GET /supported`](https://periplo-testnet.fly.dev/supported) responds without setup. Apache-2.0, TypeScript + Soroban. |
| **[Nirium](https://github.com/Eras256/Nirium)** · [nirium.xyz](https://nirium.xyz) | Autonomous treasury and machine-to-machine payments on Stellar — Soroban contracts in Rust, an x402 payment layer, and MCP integration. Non-custodial: the client's wallet signs, the protocol never holds funds. Apache-2.0. |
| **[nirium-sdk](https://github.com/nirium-protocol/nirium-sdk)** | The TypeScript and Python packages plus CLI behind Nirium — x402 `pay`/`serve`, MPP session budgets, IPFS audit anchoring. Apache-2.0. |
| **[Contextio](https://github.com/contextio/Contextio)** · [contextio.xyz](https://contextio.xyz) | Legal Context Protocol (LCP) on Stellar — verifiable, non-custodial binding of legal context to treasury and payroll operations, with SEP-53 wallet auth. Apache-2.0. |
| **[nirium-pollar-adapter](https://github.com/nirium-protocol/nirium-pollar-adapter)** · [npm](https://www.npmjs.com/package/nirium-pollar-adapter) | Adapter that lets a wallet onboarded through the Pollar SDK pay x402 requests and anchor audit receipts. Published to npm, running against Stellar mainnet. MIT. |

---

## Upstream contributions

I use these libraries in production, so when one breaks I try to arrive
with the diff rather than just the complaint. Snapshot below is accurate
as of **2026-08-29**; the live queries at the bottom always supersede it.

### Merged

| PR | Repo | Merged |
| --- | --- | --- |
| [#103](https://github.com/stellar/stellar-dev-skill/pull/103) — point `ECOSYSTEM_CARDS` `copyValue` at raw content, not GitHub's blob HTML page | `stellar/stellar-dev-skill` | 2026-08-28 |
| [#102](https://github.com/stellar/stellar-dev-skill/pull/102) — update Contextio SDK `copyValue` to the renamed `SKILL.md` path | `stellar/stellar-dev-skill` | 2026-08-15 |
| [#101](https://github.com/stellar/stellar-dev-skill/pull/101) — reposition Contextio SDK's catalog description around LCP | `stellar/stellar-dev-skill` | 2026-08-15 |
| [#98](https://github.com/stellar/stellar-dev-skill/pull/98) — add Contextio SDK to community skills | `stellar/stellar-dev-skill` | 2026-08-15 |
| [#96](https://github.com/stellar/stellar-dev-skill/pull/96) — add Nirium to community skills | `stellar/stellar-dev-skill` | 2026-08-15 |

### Open fix PRs

| PR | Repo | Fixes |
| --- | --- | --- |
| [#3228](https://github.com/x402-foundation/x402/pull/3228) — scope EVM/SVM client signer derivation to the selected families | `x402-foundation/x402` | [#3187](https://github.com/x402-foundation/x402/issues/3187) |
| [#3215](https://github.com/x402-foundation/x402/pull/3215) — derive one wildcard pattern per namespace, not one per registration | `x402-foundation/x402` | [#3172](https://github.com/x402-foundation/x402/issues/3172) |
| [#3138](https://github.com/x402-foundation/x402/pull/3138) — use the raw resource URL as canonical for opaque-origin schemes | `x402-foundation/x402` | — |
| [#3098](https://github.com/x402-foundation/x402/pull/3098) — `upto` scheme implementation spec for Stellar | `x402-foundation/x402` | [#3097](https://github.com/x402-foundation/x402/issues/3097) |
| [#1672](https://github.com/stellar/js-stellar-sdk/pull/1672) — walk every CAP-71 delegate node, not just the top level | `stellar/js-stellar-sdk` | [#1655](https://github.com/stellar/js-stellar-sdk/issues/1655) |
| [#844](https://github.com/OpenZeppelin/stellar-contracts/pull/844) — drop the Lazy-mode expiration check that validates the wrong value | `OpenZeppelin/stellar-contracts` | [#840](https://github.com/OpenZeppelin/stellar-contracts/issues/840) |
| [#4960](https://github.com/otter-sec/anchor/pull/4960) — bump `heck` 0.3 → 0.5 to drop the unbounded edition2024 landmine | `otter-sec/anchor` | — |
| [#97](https://github.com/stellar/stellar-dev-skill/pull/97) — production patterns for x402 + MPP | `stellar/stellar-dev-skill` | — |

### Bug reports that landed

- **[eas-sdk#132](https://github.com/ethereum-attestation-service/eas-sdk/issues/132)** — `getUIDsFromAttestReceipt` trusted log `topic0` without checking the emitter address, so a malicious resolver could inject spoofed UIDs in `multiAttest()`. *Closed as completed.*
- **[x402#3171](https://github.com/x402-foundation/x402/issues/3171)** — `paymentRequirementsMatchAccepted` threw on a missing/null `payload.accepted`, leaking a raw internal error to the resource server. I found and reported it; the code fix was written by [@JasonColapietro](https://github.com/JasonColapietro) in [#3180](https://github.com/x402-foundation/x402/pull/3180) ("Fixes #3171"), merged 2026-08-17. The merged patch is his work, not mine — my part was the report.
- **[x402#3270](https://github.com/x402-foundation/x402/issues/3270)** — `HTTPFacilitatorClient.settle()/verify()` decoded the `EXTENSION-RESPONSES` header and then discarded it, so resource servers couldn't branch on extension outcomes. Picked up by another contributor as [#3278](https://github.com/x402-foundation/x402/pull/3278) ("Fixes #3270"), currently open.

### Still open

Reported and awaiting maintainer response:

- `x402-foundation/x402` — [#3121](https://github.com/x402-foundation/x402/issues/3121) (broken canonical URL for `mcp://tool/{toolName}`), [#3148](https://github.com/x402-foundation/x402/issues/3148) (`payment-error` advertised in CORS, never emitted), [#3169](https://github.com/x402-foundation/x402/issues/3169) (double percent-encoding bypasses `isValidRouteTemplate`'s traversal and scheme-injection checks)
- `stellar/js-stellar-sdk` — [#1681](https://github.com/stellar/js-stellar-sdk/issues/1681), [#1683](https://github.com/stellar/js-stellar-sdk/issues/1683) (auth-entry signing against the wrong public key)
- `OpenZeppelin/stellar-contracts` — [#839](https://github.com/OpenZeppelin/stellar-contracts/issues/839) (`__check_auth` traps on a `Signer::Delegated` + `CallContract` auth entry)
- `stellar/stellar-mpp-sdk` — [#58](https://github.com/stellar/stellar-mpp-sdk/issues/58) (allow an external SEP-43 signer instead of a raw secret key)
- `Creit-Tech/Stellar-Wallets-Kit` — [#105](https://github.com/Creit-Tech/Stellar-Wallets-Kit/issues/105) (`signMessage()` JSDoc says SEP-43 hex, Freighter returns base64)
- `foundry-rs/foundry` — [#16209](https://github.com/foundry-rs/foundry/issues/16209) (`cast wallet new <name>` still fails with a bare account name)

**Totals as of 2026-08-29** — 18 pull requests and 29 issues opened across
19 repositories I don't own, belonging to 16 different accounts; 5 PRs
merged. Not every one landed, and the closed-unmerged ones are in the
same search:
[all my PRs](https://github.com/search?q=author%3AEras256+is%3Apr&type=pullrequests)
·
[all my issues](https://github.com/search?q=author%3AEras256+is%3Aissue&type=issues)

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
- If I file a bug in a dependency, I try to open the fix alongside it —
  [#3187 → #3228](https://github.com/x402-foundation/x402/pull/3228),
  [#1655 → #1672](https://github.com/stellar/js-stellar-sdk/pull/1672),
  [#840 → #844](https://github.com/OpenZeppelin/stellar-contracts/pull/844).
- When I'm not sure whether it's my bug or theirs, I say so in the issue
  rather than asserting a diagnosis I can't back
  ([#839](https://github.com/OpenZeppelin/stellar-contracts/issues/839) is
  an example).
- Every contract I ship is non-custodial by construction: the client signs,
  the protocol never holds a key that can move funds.

---

## Reach me

Open an issue on any repo above, or start with
[periplo.xyz](https://periplo.xyz) · [nirium.xyz](https://nirium.xyz) ·
[contextio.xyz](https://contextio.xyz)
