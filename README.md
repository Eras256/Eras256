# `Eras256`

I build payment and trust infrastructure for AI agents — one product per
network, each built for what that network does best, not one idea
copy-pasted five times.

| Product | What it does | Network | Status |
| --- | --- | --- | --- |
| **[Nirium](https://nirium.xyz)** | Autonomous treasury + machine-to-machine (x402/MPP) payments | Stellar | Mainnet (non-custodial roles), invite-only |
| **[Vouch402](https://www.vouch402.xyz)** | x402-metered risk checks for agents, with on-chain attestations | Base | Mainnet, full flow settled |
| **[Kumply](https://kumply.xyz)** | On-chain KYC/KYB/KYA compliance attestations | Avalanche | Fuji testnet (full) · mainnet (read-only beta) |
| **[Periplo](https://periplo.xyz)** | x402 payment facilitator + discovery catalog for agents | Stellar | Testnet |
| **[Contextio](https://contextio.xyz)** | Treasury/payroll agent for LatAm companies, bound to a signed legal-context document | Stellar | Testnet (full) · mainnet (invite-only, pre-audit) |
| **[Prova](https://www.theprova.xyz)** | Signed on-chain receipts for AI agent actions | Solana | Devnet |
| **[Votalo](https://www.votalo.xyz)** | Passkey-signed group voting, no wallet | Monad | Testnet |

Built with my cofounder, **[Monserrat Mendoza](https://github.com/M0nsxx)**
— Dev Lead, five merged PRs in Nirium plus real fixes now shipped
directly in Kumply and Vouch402 too; full detail on
[her own profile](https://github.com/M0nsxx/M0nsxx).

Each product stays on its own network until real demand says otherwise —
Contextio's mainnet is narrower than its testnet build, Prova hasn't
left devnet. That's a gate on evidence, not a roadmap slide.

---

## Proof, not claims

Everything below is a link you can check yourself. Where something's
still open or unmerged, it says so.

- Found and fixed a crash in **x402's own official conformance suite**,
  merged upstream the same week —
  [x402-foundation/x402#3228](https://github.com/x402-foundation/x402/pull/3228).
- A skill PR survived **~16 real review rounds across 21 days** before
  merging —
  [stellar/stellar-dev-skill#97](https://github.com/stellar/stellar-dev-skill/pull/97).
- Found a **security vulnerability** in the exact library Vouch402 calls
  for every attestation it emits, fixed by the maintainer —
  [eas-sdk#132](https://github.com/ethereum-attestation-service/eas-sdk/issues/132).
- A **32-day mainnet outage** on a shared facilitator got fixed; verified
  it myself with a real $0.05 payment, not a 200 response —
  [OpenZeppelin/relayer-plugin-x402-facilitator#47](https://github.com/OpenZeppelin/relayer-plugin-x402-facilitator/issues/47).
- A protocol I'd never worked at merged **4 of my PRs in one sitting**
  and thanked me by name —
  [Trustless-Work/agentic-escrow-research#1–#4](https://github.com/Trustless-Work/agentic-escrow-research/pull/1).
- When I was wrong, I said so and closed my own issue against myself —
  [OpenZeppelin/stellar-contracts#839](https://github.com/OpenZeppelin/stellar-contracts/issues/839)
  turned out to be my own construction bug, not a library gap.
- **Two Stellar Community Fund Instawards**, delivered against real
  milestones — gated on being an active
  [Stellar Ambassador](https://stellar.gitbook.io/ambassador-program), the
  program's own stated eligibility rule, not something I'm claiming on
  my own.
- Every contract I ship is **non-custodial by construction** — the
  client's own wallet signs, or a role that by contract design can't
  move funds. Never a key of mine that can.

<details>
<summary><strong>Full receipts</strong> — every PR, issue, and bounty, by project</summary>

Most of my public work is either a protocol implementation I maintain or
a bug I found in something I depend on, then a patch for it. Where a fix
landed as someone else's PR, that's named — the report was mine, not the
patch.

Three Stellar products below (Periplo, Nirium, Contextio) share real
upstream dependencies — same protocols, sometimes the literal same bug —
so each fix is attributed to the specific project it came from, not
merged into one pile.

Snapshot re-verified live against the GitHub API on **2026-10-09**; the
search links at the bottom always supersede it.

### Kumply, Vouch402, Prova — upstream contributions

**Kumply (Avalanche)** — three open bug reports against a third-party
community skills repo, [Ayomisco/avaxskills](https://github.com/Ayomisco/avaxskills),
found while building on top of it: [#2](https://github.com/Ayomisco/avaxskills/issues/2)
(a subnet-deployment skill cites CLI commands that don't exist in the real
`ava-labs/avalanche-cli`), [#3](https://github.com/Ayomisco/avaxskills/issues/3)
(a precompiles skill has the wrong genesis key name for `TxAllowList`),
[#4](https://github.com/Ayomisco/avaxskills/issues/4) (a wagmi skill cites
an outdated version and a deprecated hook). All still open. I'm an
official **Team1 LatAm collaborator** — an Avalanche-ecosystem-wide role,
not tied to a single project. Also shipped
[AgentHub Protocol](https://www.npmjs.com/package/@vaiosx44/agenthub-sdk)
for Avalanche's Hack2Build: Payments x402 hackathon — real x402
micropayment code, on-chain agent reputation, and DeFi integration code
for Trader Joe, Benqi, and Aave V3. SDK published on npm, contracts
deployed to Fuji testnet — dormant since January 2026, stated plainly
rather than presented as active.

**Vouch402 (Base)** — [base/skills#152](https://github.com/base/skills/pull/152),
an open PR adding a Vouch402 listing to Base's own community skills
catalog. Also [eas-sdk#132](https://github.com/ethereum-attestation-service/eas-sdk/issues/132)
(closed, fixed) and
[foundry-rs/foundry#16209](https://github.com/foundry-rs/foundry/issues/16209)
(`cast wallet new <name>` failed with a bare account name — closed
2026-09-09, fixed by [@riba2534 in #16219](https://github.com/foundry-rs/foundry/pull/16219)),
both found auditing tooling Vouch402 depends on. I hold the **Based
Developer Ambassador** role in Base's own Discord — real and active.

**Prova (Solana)** — [otter-sec/anchor#4960](https://github.com/otter-sec/anchor/pull/4960),
bumping `heck` 0.3 → 0.5 to drop an unbounded `edition2024` dependency
landmine in the Anchor framework Prova's on-chain program is built on —
**merged 2026-09-30** by @jamie-osec.

### Periplo — upstream contributions

Full first-hand narrative with transaction hashes and reproduction steps
lives in [`Eras256/Periplo`'s own README](https://github.com/Eras256/Periplo#readme).

**Merged**

| PR | Repo | Merged |
| --- | --- | --- |
| [#3228](https://github.com/x402-foundation/x402/pull/3228) — scope EVM/SVM client signer derivation to the selected `--families`, fixing a crash in the official e2e conformance suite | `x402-foundation/x402` | 2026-08-31 — authored by me, merged by @phdargen. Closes [#3187](https://github.com/x402-foundation/x402/issues/3187), which I also filed. An earlier attempt, [#3219](https://github.com/x402-foundation/x402/pull/3219), was closed unmerged and superseded by this one. |
| [#103](https://github.com/stellar/stellar-dev-skill/pull/103) — point `ECOSYSTEM_CARDS` `copyValue` at raw content, not GitHub's blob HTML page | `stellar/stellar-dev-skill` | 2026-08-28, by @kaankacar |
| [#3306](https://github.com/x402-foundation/x402/pull/3306) — add a dedicated `extension_responses`/`extensionResponses` field instead of leaking `EXTENSION-RESPONSES` data via the buyer-facing `extensions` field | `x402-foundation/x402` | 2026-08-31, by @phdargen. Closes [#3270](https://github.com/x402-foundation/x402/issues/3270), which I filed. Not my code — full detail below. |
| [#97](https://github.com/stellar/stellar-dev-skill/pull/97) — production patterns for x402 + MPP | `stellar/stellar-dev-skill` | 2026-09-05, by @kaankacar — this one's Nirium's, not Periplo's |

**Open fix PRs**

| PR | Repo | Fixes |
| --- | --- | --- |
| [#3215](https://github.com/x402-foundation/x402/pull/3215) — derive one wildcard pattern per namespace, not one per registration | `x402-foundation/x402` | [#3172](https://github.com/x402-foundation/x402/issues/3172) |
| [#3138](https://github.com/x402-foundation/x402/pull/3138) — use the raw resource URL as canonical for opaque-origin schemes | `x402-foundation/x402` | [#3121](https://github.com/x402-foundation/x402/issues/3121) |
| [#3098](https://github.com/x402-foundation/x402/pull/3098) — `upto` scheme implementation spec for Stellar | `x402-foundation/x402` | [#3097](https://github.com/x402-foundation/x402/issues/3097) |

**Bug reports that landed**

- **[x402#3171](https://github.com/x402-foundation/x402/issues/3171)** — `paymentRequirementsMatchAccepted` threw on a missing/null `payload.accepted`. I found and reported it; fixed by [@JasonColapietro in #3180](https://github.com/x402-foundation/x402/pull/3180), merged 2026-08-17.
- **[x402#3169](https://github.com/x402-foundation/x402/issues/3169)** — `isValidRouteTemplate`'s traversal/scheme-injection checks decoded `routeTemplate` only once, so double percent-encoding bypassed both. Filed with full repro; fixed by [@ygd58 in #3213](https://github.com/x402-foundation/x402/pull/3213), merged 2026-09-09.
- **[x402#3270](https://github.com/x402-foundation/x402/issues/3270)** — `HTTPFacilitatorClient.settle()/verify()` decoded the `EXTENSION-RESPONSES` header and discarded it. Fixed on Periplo's own side the same day; the actual upstream fix was the maintainer's own [#3306](https://github.com/x402-foundation/x402/pull/3306) (Python, @phdargen), introducing a dedicated field instead of reusing `extensions` — rejecting the shape my own workaround used. My `/settle` still uses the old shape pending a migration to the new field, now available since `@x402/core` has moved to `2.28.0`.
- **[eas-sdk#132](https://github.com/ethereum-attestation-service/eas-sdk/issues/132)** — `getUIDsFromAttestReceipt` trusted log `topic0` without checking the emitter address. Closed as completed by the maintainer 2026-08-27, fixed in [eas-sdk 2.10.0](https://www.npmjs.com/package/@ethereum-attestation-service/eas-sdk/v/2.10.0).
- **[OpenZeppelin/stellar-contracts#839](https://github.com/OpenZeppelin/stellar-contracts/issues/839)** — hit `UnreachableCodeReached` combining `Signer::Delegated` with a `CallContract` rule. Closed 2026-09-02, resolution: ours — a construction bug in how the auth entries were built, not a library gap.
- **[js-stellar-sdk#1655](https://github.com/stellar/js-stellar-sdk/issues/1655)** — `needsNonInvokerSigningBy()`/`signAuthEntries()` only see the top-level node of a CAP-71 delegate credential. Filed with my own fix, [#1672](https://github.com/stellar/js-stellar-sdk/pull/1672) (closed unmerged), superseded by the maintainer's own [#1747](https://github.com/stellar/js-stellar-sdk/pull/1747) (merged 2026-09-28).

Still open, awaiting maintainer response: `x402-foundation/x402`
[#3121](https://github.com/x402-foundation/x402/issues/3121),
[#3148](https://github.com/x402-foundation/x402/issues/3148).

### Nirium — upstream contributions and GrantFox bounty program

**Upstream, to repos Nirium doesn't own**

| Item | Repo | Status |
| --- | --- | --- |
| [#96](https://github.com/stellar/stellar-dev-skill/pull/96) — add Nirium to community skills | `stellar/stellar-dev-skill` | Merged 2026-08-15 |
| [#97](https://github.com/stellar/stellar-dev-skill/pull/97) — production patterns for x402 + MPP | `stellar/stellar-dev-skill` | Merged 2026-09-05, by @kaankacar, after ~16 real review rounds |
| [#47](https://github.com/OpenZeppelin/relayer-plugin-x402-facilitator/issues/47) — mainnet sponsor/relayer account silent, then a stale-RPC outage | `OpenZeppelin/relayer-plugin-x402-facilitator` | Resolved by OZ 2026-09-11, confirmed by me with a real mainnet payment |
| [#58](https://github.com/stellar/stellar-mpp-sdk/issues/58) — allow an external SEP-43 signer instead of a raw secret key | `stellar/stellar-mpp-sdk` | Open |
| [#30](https://github.com/pollar-xyz/pollar-apps/pull/30) — Nirium x402 adapter demo (`apps/nirium`) | `pollar-xyz/pollar-apps` | Merged 2026-08-31, by @aleregex |
| [#1](https://github.com/Trustless-Work/agentic-escrow-research/pull/1)–[#4](https://github.com/Trustless-Work/agentic-escrow-research/pull/4) — bounded-authority milestone payouts, treasury rebalance via a missing destination parameter, direct x402 payment, agent-facing tool-schema evidence | `Trustless-Work/agentic-escrow-research` | Merged 2026-09-21, all four within 27 minutes — three by me, #3 by Monserrat |
| [#9](https://github.com/Trustless-Work/agentic-escrow-research/pull/9) — research note: fail-closed payment and delivery gates, two real production bugs found and fixed | `Trustless-Work/agentic-escrow-research` | Open, filed 2026-10-05 |

A real design collaboration, not a bounty: [issue #96](https://github.com/nirium-protocol/nirium/issues/96)
(opened by me) was designed and tested by [@CodeDeityX](https://github.com/CodeDeityX),
who built the public reproducibility harness. Merged as
[#98](https://github.com/nirium-protocol/nirium/pull/98) — `nirium@0.16.0`,
now on npm, ships an optional `policy` hook on `initX402()`.

**GrantFox bounty program** (`nirium-protocol/nirium`, Nirium's own
repo — these are bounties Nirium posted). As of 2026-09-05: 44 issues
across three campaigns, 42 real bounty asks — 20 delivered inside
`nirium` itself, 2 delivered externally and awaiting that project's own
review, 4 closed and administratively recreated, 16 closed without
delivery.

<details>
<summary>Full bounty breakdown — every delivery, who opened it, and the five that are my cofounder's</summary>

- **2 delivered externally**: [#75 → Fundable-Protocol/fundable-sdk#8](https://github.com/Fundable-Protocol/fundable-sdk/pull/8) and [#76 → wejoona/api#23](https://github.com/wejoona/api/pull/23), both opened by **@Santia2004**, not by this account.
- **4 administratively recreated** under a later campaign, same ask: [#29→#43](https://github.com/nirium-protocol/nirium/issues/43), [#30→#44](https://github.com/nirium-protocol/nirium/issues/44), [#31→#45](https://github.com/nirium-protocol/nirium/issues/45), [#32→#46](https://github.com/nirium-protocol/nirium/issues/46).

A few of the stronger merged deliveries:

| Bounty issue | Delivering PR | Author |
| --- | --- | --- |
| [#39](https://github.com/nirium-protocol/nirium/issues/39) — harden the Python WebSocket signals client | [#47](https://github.com/nirium-protocol/nirium/pull/47), merged | @Simultech369 — external |
| [#51](https://github.com/nirium-protocol/nirium/issues/51) — GitHub Action to verify a Nirium audit-CID in CI | [#80](https://github.com/nirium-protocol/nirium/pull/80), merged | @Simultech369 — external |
| [#65](https://github.com/nirium-protocol/nirium/issues/65) — audit trail forensic export bridge | [#69](https://github.com/nirium-protocol/nirium/pull/69), merged | @Santia2004 — external |

Five more are my cofounder's own first shipped code for this project,
through the same GrantFox process:
[#50](https://github.com/nirium-protocol/nirium/issues/50) via [#58](https://github.com/nirium-protocol/nirium/pull/58),
[#37](https://github.com/nirium-protocol/nirium/issues/37) via [#59](https://github.com/nirium-protocol/nirium/pull/59),
[#45](https://github.com/nirium-protocol/nirium/issues/45) via [#61](https://github.com/nirium-protocol/nirium/pull/61),
[#38](https://github.com/nirium-protocol/nirium/issues/38) via [#60](https://github.com/nirium-protocol/nirium/pull/60),
and [#44](https://github.com/nirium-protocol/nirium/issues/44) via [#62](https://github.com/nirium-protocol/nirium/pull/62)
— all by [Monserrat Mendoza](https://github.com/M0nsxx).

One more worth naming because it isn't a bounty at all:
**[#81](https://github.com/nirium-protocol/nirium/issues/81)** was a real
fail-open vulnerability in the Next.js x402 example, reported by an
outside party and fixed via a merged PR, [#84](https://github.com/nirium-protocol/nirium/pull/84).
Separately, [nirium#108](https://github.com/nirium-protocol/nirium/pull/108)
(`pay` no longer accepts a secret key as a CLI argument, fixing a
shell-history/process-list leak) merged 2026-10-09.

</details>

### Contextio

Moved from a personal repo to its own org — `Eras256/Contextio` now
resolves to [`contextio/Contextio`](https://github.com/contextio/Contextio).
Runs its own bounty-style program (not GrantFox-labeled): five open
issues, none delivered yet, two with competing external PRs open and
unreviewed. Upstream, three merged PRs added/refined its community-skill
listing on `stellar/stellar-dev-skill`
([#98](https://github.com/stellar/stellar-dev-skill/pull/98),
[#101](https://github.com/stellar/stellar-dev-skill/pull/101),
[#102](https://github.com/stellar/stellar-dev-skill/pull/102)).
Beyond that, no upstream contribution from this account to any other
external repo specifically for Contextio — said plainly, not padded.

### Other dependency bug reports

- **[Creit-Tech/Stellar-Wallets-Kit#105](https://github.com/Creit-Tech/Stellar-Wallets-Kit/issues/105)** — `signMessage()`'s JSDoc says SEP-43 hex, Freighter returns base64. Open.

### Hackathons outside the portfolio

Separate weekend builds, no public repo for any of the three. Two have
the event's own announcement naming the winner; the third only has my
own tweet — disclosed as such, same standard as everywhere else here.

- **[ActivaChain](https://activachain.com)** — won ETH Uruguay 2025, with
  Monserrat. [Confirmed](https://x.com/EthereumUruguay/status/1968785973749170227)
  by the event.
- **[CreatorChain](https://creatorchain-mx.vercel.app/)** — 1st +
  3rd place at ETH Mexico Monterrey 2025. [Confirmed](https://x.com/ethereum_mexico/status/1989005140838265067).
  Solo build.
- **[BioShield Insurance](https://bioshield-insurance.vercel.app/)** — won
  the FDA Track at DeSci Builders Hackathon 2025, with Monserrat. Deployed
  across Solana, Base, and Optimism. Self-reported, [my own tweet](https://x.com/vaiossx/status/1972064428091924681)
  at the time.

</details>

---

## Stack

![Avalanche](https://img.shields.io/badge/Avalanche-E84142?style=flat-square&logo=avalanche&logoColor=white)
![Base](https://img.shields.io/badge/Base-0052FF?style=flat-square&logo=coinbase&logoColor=white)
![Stellar](https://img.shields.io/badge/Stellar-000000?style=flat-square&logo=stellar&logoColor=white)
![Soroban](https://img.shields.io/badge/Soroban-1f6feb?style=flat-square)
![Solana](https://img.shields.io/badge/Solana-9945FF?style=flat-square&logo=solana&logoColor=white)
![x402](https://img.shields.io/badge/x402-teal?style=flat-square)
![Solidity](https://img.shields.io/badge/Solidity-363636?style=flat-square&logo=solidity&logoColor=white)
![Rust](https://img.shields.io/badge/Rust-000000?style=flat-square&logo=rust&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)

**Protocols** — x402, MPP, SEP-41/SAC, SEP-43, SEP-53, CAP-71 delegated
auth, MCP, EAS

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://github-stats-extended.vercel.app/api?username=Eras256&show_icons=true&show=reviews,prs_merged,prs_merged_percentage&rank_icon=percentile&theme=dark">
  <img alt="Commits, pull requests, merged PRs, reviews and issues for Eras256" src="https://github-stats-extended.vercel.app/api?username=Eras256&show_icons=true&show=reviews,prs_merged,prs_merged_percentage&rank_icon=percentile">
</picture>

---

## Search these live yourself

[All my PRs](https://github.com/search?q=author%3AEras256+is%3Apr&type=pullrequests)
·
[all my issues](https://github.com/search?q=author%3AEras256+is%3Aissue&type=issues)
·
[Nirium's bounty board](https://github.com/nirium-protocol/nirium/issues?q=is%3Aissue)
·
[Contextio's open issues](https://github.com/contextio/Contextio/issues)

**Reach me** — open an issue on any repo above, or
[periplo.xyz](https://periplo.xyz) · [nirium.xyz](https://nirium.xyz) ·
[contextio.xyz](https://contextio.xyz) · X:
[@vaiossx](https://x.com/vaiossx) · Discord: `vaiossx`
