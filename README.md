# `Eras256`

I build infrastructure for the agent economy: how an AI agent pays, how
it gets checked before anyone trusts it, and how it proves what it did.
Each piece runs on the network that fits it.

| What it does for an agent | Product | Network | Status |
| --- | --- | --- | --- |
| **Pays, gets paid, keeps proof** | **[Nirium](https://nirium.xyz)**: x402 pay-gates for any API, an audit trail that pins a hash (and optionally who signed it) to IPFS, and a treasury agent that moves idle funds into tokenized CETES | Stellar | Partly on mainnet: x402 payments, the audit trail, and the treasury on a third-party DeFindex vault · Nirium's own vault contract stays on testnet until it has an external audit |
| **Finds a paid service and settles it** | **[Periplo](https://periplo.xyz)**: x402 facilitator with a Bazaar discovery catalog and an `upto` scheme on Soroban | Stellar | Testnet, with an outside seller in the catalog |
| **Checks who it's paying** | **[Vouch402](https://www.vouch402.xyz)**: pay-per-call risk data on any address, plus EAS attestations that a paid service was delivered | Base | Mainnet, full flow settled |
| **Proves who's behind it** | **[Kumply](https://kumply.xyz)**: KYC/KYB/KYA tiers as on-chain attestations, no personal data on-chain, and an L1 where validators must hold one | Avalanche | Fuji testnet (full) · mainnet read-only beta · L1 registered on Fuji, not active yet |
| **Moves company money under signed terms** | **[Contextio](https://contextio.xyz)**: treasury and payroll agent for LatAm companies, every action tied to a signed legal document (LCP) | Stellar | Testnet (full agent) · mainnet invite-only, read-only and self-custody, contracts pending audit |
| **Proves what it did** | **[Prova](https://www.theprova.xyz)**: one `attest()` call, one Ed25519-signed receipt on-chain through an Anchor program | Solana | Devnet |
| Side build | **[Votalo](https://www.votalo.xyz)**: group voting with a passkey, no wallet; every vote is an EIP-712 signature | Monad | Testnet |

Built with my cofounder **[Monserrat Mendoza](https://github.com/M0nsxx)**,
Dev Lead. She has six merged PRs in Nirium and has shipped fixes in Kumply
and Vouch402. More on [her profile](https://github.com/M0nsxx/M0nsxx).

A product only moves to a new network when there's real demand for it.
That's why Contextio's mainnet does less than its testnet, and Prova is
still on devnet.

---

## Proof, not claims

Every item links to something you can check. If it's still open or
unmerged, I say so.

- **Periplo:** I found and fixed a crash in **x402's official
  conformance suite**. Merged upstream the same week:
  [x402-foundation/x402#3228](https://github.com/x402-foundation/x402/pull/3228).
- **Nirium:** a shared facilitator was down on mainnet for **32 days**.
  After the fix I checked it with a real $0.05 payment, not just a 200
  response:
  [OpenZeppelin/relayer-plugin-x402-facilitator#47](https://github.com/OpenZeppelin/relayer-plugin-x402-facilitator/issues/47).
- **Nirium:** Trustless Work, a team we had never worked with, merged
  **4 of our PRs in one sitting** (three mine, one my cofounder's) as
  research for their agentic payments work:
  [Trustless-Work/agentic-escrow-research#1-#4](https://github.com/Trustless-Work/agentic-escrow-research/pull/1).
- **Vouch402:** I found a **security bug** in the library Vouch402 uses
  for every attestation. The maintainer fixed it:
  [eas-sdk#132](https://github.com/ethereum-attestation-service/eas-sdk/issues/132).
- **Kumply:** before turning on our Avalanche L1, I checked our validator
  manager against ava-labs' real source code and **found a bug in our
  own code**. A missing 4-byte length prefix meant the conversion ID would
  never match what the P-Chain signs. Our 27 tests missed it because the
  mock had the same mistake. Fixed and redeployed
  ([writeup](https://github.com/kumplyprotocol/Kumply/blob/main/docs/audits/avalanche-ecosystem-audit-2026-08-17.md)).
  The contracts run on C-Chain mainnet as a read-only beta, with verified
  source:
  [AttestationStore](https://snowtrace.io/address/0xa116261Ed3a848A9E1cd34923D5A0442D1455F71).
- **Prova:** I removed a dependency problem from **Anchor**, the Solana
  framework Prova is built on. Merged by the maintainer:
  [anchor#4960](https://github.com/otter-sec/anchor/pull/4960).
- **Periplo:** when I was wrong, I said so and closed my own issue.
  [OpenZeppelin/stellar-contracts#839](https://github.com/OpenZeppelin/stellar-contracts/issues/839)
  was a bug in how I built the auth entries, not in the library.
- **Nirium:** **two Stellar Community Fund Instawards**, delivered
  against real milestones. You can only get one as an active
  [Stellar Ambassador](https://stellar.gitbook.io/ambassador-program);
  that's the program's rule, not my claim.
- Every contract I ship is **non-custodial**: the user's own wallet
  signs, or a role that can't move funds by design. I never hold a key
  that can.

<details>
<summary><strong>Full receipts</strong>: every PR, issue and bounty, by project</summary>

Most of my public work is one of two things: a protocol I maintain, or a
bug I found in something I depend on, followed by a fix. When someone
else wrote the fix, I name them. The report was mine, the patch wasn't.

Periplo, Nirium and Contextio share a lot of upstream code, sometimes the
exact same bug. So each item is listed under the project it came from.

Checked against the GitHub API on **2026-10-11**. The search links at the
bottom are always more current.

### Kumply, Vouch402, Prova

**Kumply (Avalanche):** three bugs I reported in a community skills repo,
[Ayomisco/avaxskills](https://github.com/Ayomisco/avaxskills), found while
building on it:
[#2](https://github.com/Ayomisco/avaxskills/issues/2) (a skill lists CLI
commands that don't exist in `ava-labs/avalanche-cli`),
[#3](https://github.com/Ayomisco/avaxskills/issues/3) (wrong genesis key
name for `TxAllowList`) and
[#4](https://github.com/Ayomisco/avaxskills/issues/4) (an outdated wagmi
version and a deprecated hook). All three are open, and so are my fixes:
[#5](https://github.com/Ayomisco/avaxskills/pull/5),
[#6](https://github.com/Ayomisco/avaxskills/pull/6),
[#7](https://github.com/Ayomisco/avaxskills/pull/7).
I'm an official **Team1 LatAm collaborator** for the Avalanche ecosystem.
I also built
[AgentHub Protocol](https://www.npmjs.com/package/@vaiosx44/agenthub-sdk)
for Avalanche's Hack2Build: Payments x402 hackathon: x402 micropayments,
on-chain agent reputation, and integrations with Trader Joe, Benqi and
Aave V3. The SDK is on npm and the contracts are on Fuji. It hasn't been
touched since January 2026.

**Vouch402 (Base):** [base/skills#152](https://github.com/base/skills/pull/152),
an open PR to list Vouch402 in Base's community skills catalog. While
checking the tools Vouch402 depends on, I also found
[eas-sdk#132](https://github.com/ethereum-attestation-service/eas-sdk/issues/132)
(fixed) and
[foundry-rs/foundry#16209](https://github.com/foundry-rs/foundry/issues/16209)
(`cast wallet new <name>` failed with a plain account name; fixed by
[@riba2534 in #16219](https://github.com/foundry-rs/foundry/pull/16219),
closed 2026-09-09). I'm a **Based Developer Ambassador** in Base's
Discord.

**Prova (Solana):** [otter-sec/anchor#4960](https://github.com/otter-sec/anchor/pull/4960)
bumps `heck` from 0.3 to 0.5, which removes an `edition2024` dependency
that could break Anchor builds. Merged 2026-09-30 by @jamie-osec. He
merged three more of mine in October:
[#5130](https://github.com/otter-sec/anchor/pull/5130) (`NonZero*`
integers in IDL generation, 2026-10-08),
[#5131](https://github.com/otter-sec/anchor/pull/5131) (error on type
aliases with the same name but different definitions, 2026-10-07) and
[#5132](https://github.com/otter-sec/anchor/pull/5132) (`Space` for
`NonZero*` integers, 2026-10-07).

### Periplo

The full story, with transaction hashes and steps to reproduce, is in
[Periplo's README](https://github.com/Eras256/Periplo#readme).

**Merged**

| PR | Repo | Merged |
| --- | --- | --- |
| [#3228](https://github.com/x402-foundation/x402/pull/3228): scope EVM/SVM client signer derivation to the selected `--families`, fixing a crash in the official e2e conformance suite | `x402-foundation/x402` | 2026-08-31. My PR, merged by @phdargen. Closes [#3187](https://github.com/x402-foundation/x402/issues/3187), which I filed. My earlier attempt, [#3219](https://github.com/x402-foundation/x402/pull/3219), was closed in favor of this one. |
| [#103](https://github.com/stellar/stellar-dev-skill/pull/103): point `ECOSYSTEM_CARDS` `copyValue` at the raw file, not GitHub's HTML page | `stellar/stellar-dev-skill` | 2026-08-28, by @kaankacar |
| [#3306](https://github.com/x402-foundation/x402/pull/3306): a dedicated `extension_responses`/`extensionResponses` field instead of leaking `EXTENSION-RESPONSES` data through `extensions` | `x402-foundation/x402` | 2026-08-31, by @phdargen. Closes [#3270](https://github.com/x402-foundation/x402/issues/3270), which I filed. Not my code. |
| [#3336](https://github.com/x402-foundation/x402/pull/3336): include `feeBumpSigner` in the facilitator safety checks | `x402-foundation/x402` | 2026-09-03. My PR, merged by @phdargen. Closes [#3332](https://github.com/x402-foundation/x402/issues/3332), which I filed. |

**Open fix PRs**

| PR | Repo | Fixes |
| --- | --- | --- |
| [#3215](https://github.com/x402-foundation/x402/pull/3215): one wildcard pattern per namespace, not one per registration | `x402-foundation/x402` | [#3172](https://github.com/x402-foundation/x402/issues/3172) |
| [#3138](https://github.com/x402-foundation/x402/pull/3138): use the raw resource URL for opaque-origin schemes | `x402-foundation/x402` | [#3121](https://github.com/x402-foundation/x402/issues/3121) |
| [#3098](https://github.com/x402-foundation/x402/pull/3098): `upto` scheme spec for Stellar | `x402-foundation/x402` | [#3097](https://github.com/x402-foundation/x402/issues/3097) |
| [#3338](https://github.com/x402-foundation/x402/pull/3338): enforce the settlement override limit against `PaymentRequirements.amount` | `x402-foundation/x402` | [#3334](https://github.com/x402-foundation/x402/issues/3334) (closed by the maintainer 2026-09-08) |
| [#3339](https://github.com/x402-foundation/x402/pull/3339): document that `areFeesSponsored: false` isn't supported | `x402-foundation/x402` | [#3333](https://github.com/x402-foundation/x402/issues/3333) |
| [Tally#1](https://github.com/Madhav-Gupta-28/Tally/pull/1): declare `paymentFlows`/`defaultAssetTransferMethod` in an `upto` server so it works with `@x402/core` | `Madhav-Gupta-28/Tally` | - |

**Bugs I reported that got fixed**

- **[x402#3169](https://github.com/x402-foundation/x402/issues/3169):** `isValidRouteTemplate` decoded `routeTemplate` only once, so double percent-encoding got past its traversal and scheme-injection checks. Fixed by [@ygd58 in #3213](https://github.com/x402-foundation/x402/pull/3213), merged 2026-09-09.
- **[x402#3270](https://github.com/x402-foundation/x402/issues/3270):** `HTTPFacilitatorClient.settle()/verify()` decoded the `EXTENSION-RESPONSES` header and threw it away. I worked around it in Periplo the same day. The real fix was the maintainer's [#3306](https://github.com/x402-foundation/x402/pull/3306) (Python, @phdargen), which added a new field instead of reusing `extensions`, so my workaround's shape didn't make it in. My `/settle` still uses the old shape until I move it to the new field, available since `@x402/core` `2.28.0`.
- **[eas-sdk#132](https://github.com/ethereum-attestation-service/eas-sdk/issues/132):** `getUIDsFromAttestReceipt` trusted the log's `topic0` without checking who emitted it. Fixed in [eas-sdk 2.10.0](https://www.npmjs.com/package/@ethereum-attestation-service/eas-sdk/v/2.10.0), closed 2026-08-27.
- **[OpenZeppelin/stellar-contracts#839](https://github.com/OpenZeppelin/stellar-contracts/issues/839):** hit `UnreachableCodeReached` combining `Signer::Delegated` with a `CallContract` rule. My mistake: I built the auth entries wrong. Closed 2026-09-02.
- **[js-stellar-sdk#1655](https://github.com/stellar/js-stellar-sdk/issues/1655):** `needsNonInvokerSigningBy()`/`signAuthEntries()` only looked at the top level of a CAP-71 delegate credential. I sent a fix, [#1672](https://github.com/stellar/js-stellar-sdk/pull/1672), which was closed in favor of the maintainer's [#1747](https://github.com/stellar/js-stellar-sdk/pull/1747) (merged 2026-09-28).
- **[OpenZeppelin/stellar-contracts#863](https://github.com/OpenZeppelin/stellar-contracts/issues/863):** with `Signer::Delegated`, simulation never showed that the delegate had to sign. Closed by @brozorec 2026-09-02.

Still open, waiting on the maintainers: `x402-foundation/x402`
[#3121](https://github.com/x402-foundation/x402/issues/3121),
[#3148](https://github.com/x402-foundation/x402/issues/3148),
[#3333](https://github.com/x402-foundation/x402/issues/3333),
[#3341](https://github.com/x402-foundation/x402/issues/3341).

### Nirium

**In repos Nirium doesn't own**

| Item | Repo | Status |
| --- | --- | --- |
| [#96](https://github.com/stellar/stellar-dev-skill/pull/96): add Nirium to the community skills | `stellar/stellar-dev-skill` | Merged 2026-08-15 |
| [#97](https://github.com/stellar/stellar-dev-skill/pull/97): production patterns for x402 + MPP | `stellar/stellar-dev-skill` | Merged 2026-09-05 by @kaankacar, after ~16 review rounds |
| [#47](https://github.com/OpenZeppelin/relayer-plugin-x402-facilitator/issues/47): the mainnet sponsor account went silent, then a stale RPC took it down | `OpenZeppelin/relayer-plugin-x402-facilitator` | Fixed by OZ 2026-09-11; I confirmed it with a real mainnet payment |
| [#58](https://github.com/stellar/stellar-mpp-sdk/issues/58): accept an external SEP-43 signer instead of a raw secret key | `stellar/stellar-mpp-sdk` | Open |
| [#30](https://github.com/pollar-xyz/pollar-apps/pull/30): Nirium x402 adapter demo (`apps/nirium`) | `pollar-xyz/pollar-apps` | Merged 2026-08-31 by @aleregex |
| [#1](https://github.com/Trustless-Work/agentic-escrow-research/pull/1)-[#4](https://github.com/Trustless-Work/agentic-escrow-research/pull/4): milestone payouts with limited authority, treasury rebalancing, direct x402 payment, and tool-schema evidence for agents | `Trustless-Work/agentic-escrow-research` | All four merged 2026-09-21 within 27 minutes. Three are mine, #3 is Monserrat's |
| [#9](https://github.com/Trustless-Work/agentic-escrow-research/pull/9): research note on fail-closed payment and delivery checks, with two real production bugs found and fixed | `Trustless-Work/agentic-escrow-research` | Open since 2026-10-05 |
| [#69](https://github.com/stellar/stellar-mpp-sdk/pull/69): fix two mainnet SAC constants that weren't valid StrKeys | `stellar/stellar-mpp-sdk` | Merged 2026-09-09 by @jeesunikim. Closes [#68](https://github.com/stellar/stellar-mpp-sdk/issues/68) |
| [x402#3171](https://github.com/x402-foundation/x402/issues/3171): `paymentRequirementsMatchAccepted` threw when `payload.accepted` was missing | `x402-foundation/x402` | Fixed by [@JasonColapietro in #3180](https://github.com/x402-foundation/x402/pull/3180), merged 2026-08-17 |
| [#840](https://github.com/OpenZeppelin/stellar-contracts/issues/840): fee abstraction's Lazy-mode expiration check validated the wrong value | `OpenZeppelin/stellar-contracts` | Closed 2026-09-07. My fix [#844](https://github.com/OpenZeppelin/stellar-contracts/pull/844) wasn't merged; the docs follow-up [#893](https://github.com/OpenZeppelin/stellar-contracts/pull/893) is open |
| [#6](https://github.com/Trustless-Work/trustlesswork-sdk-react/issues/6): Multi-Release `trustline.address` needs the classic issuer, not the SAC id | `Trustless-Work/trustlesswork-sdk-react` | Closed 2026-09-28 |
| [#2](https://github.com/pollar-xyz/demo/issues/2): the Nirium x402 tab shows a classic Stellar payment labeled as x402 | `pollar-xyz/demo` | Open |
| [#3692](https://github.com/x402-foundation/x402/issues/3692): `@x402/stellar` pulls in an axios version with 7 high advisories | `x402-foundation/x402` | Open |

Not a bounty, a real collaboration: I opened
[issue #96](https://github.com/nirium-protocol/nirium/issues/96), and
[@CodeDeityX](https://github.com/CodeDeityX) designed and tested the fix
and built a public harness to reproduce it. It shipped as
[#98](https://github.com/nirium-protocol/nirium/pull/98): `nirium@0.16.0`
on npm has an optional `policy` hook on `initX402()`.

**GrantFox bounties** (bounties Nirium posted in its own repo,
`nirium-protocol/nirium`). As of 2026-09-05: 44 issues across three
campaigns, 42 real asks. 20 delivered in `nirium`, 2 delivered in other
projects and waiting on their review, 4 closed and recreated, 16 closed
without delivery.

<details>
<summary>Bounty details: every delivery, who opened it, and the five from my cofounder</summary>

- **2 delivered in other projects:** [#75 → Fundable-Protocol/fundable-sdk#8](https://github.com/Fundable-Protocol/fundable-sdk/pull/8) and [#76 → wejoona/api#23](https://github.com/wejoona/api/pull/23), both by **@Santia2004**, not me.
- **4 recreated** in a later campaign with the same ask: [#29→#43](https://github.com/nirium-protocol/nirium/issues/43), [#30→#44](https://github.com/nirium-protocol/nirium/issues/44), [#31→#45](https://github.com/nirium-protocol/nirium/issues/45), [#32→#46](https://github.com/nirium-protocol/nirium/issues/46).

Some of the best merged deliveries:

| Bounty issue | PR | Author |
| --- | --- | --- |
| [#39](https://github.com/nirium-protocol/nirium/issues/39): harden the Python WebSocket signals client | [#47](https://github.com/nirium-protocol/nirium/pull/47), merged | @Simultech369 (external) |
| [#51](https://github.com/nirium-protocol/nirium/issues/51): GitHub Action to verify a Nirium audit CID in CI | [#80](https://github.com/nirium-protocol/nirium/pull/80), merged | @Simultech369 (external) |
| [#65](https://github.com/nirium-protocol/nirium/issues/65): forensic export bridge for the audit trail | [#69](https://github.com/nirium-protocol/nirium/pull/69), merged | @Santia2004 (external) |

Five more are my cofounder's first shipped code for Nirium, through the
same GrantFox process:
[#50](https://github.com/nirium-protocol/nirium/issues/50) via [#58](https://github.com/nirium-protocol/nirium/pull/58),
[#37](https://github.com/nirium-protocol/nirium/issues/37) via [#59](https://github.com/nirium-protocol/nirium/pull/59),
[#45](https://github.com/nirium-protocol/nirium/issues/45) via [#61](https://github.com/nirium-protocol/nirium/pull/61),
[#38](https://github.com/nirium-protocol/nirium/issues/38) via [#60](https://github.com/nirium-protocol/nirium/pull/60)
and [#44](https://github.com/nirium-protocol/nirium/issues/44) via [#62](https://github.com/nirium-protocol/nirium/pull/62),
all by [Monserrat Mendoza](https://github.com/M0nsxx).

Not a bounty: **[#81](https://github.com/nirium-protocol/nirium/issues/81)**
was a fail-open bug in the Next.js x402 example, reported by someone
outside the team and fixed in [#84](https://github.com/nirium-protocol/nirium/pull/84).
And [nirium#108](https://github.com/nirium-protocol/nirium/pull/108),
merged 2026-10-09, stops `pay` from taking a secret key as a CLI
argument, so it no longer ends up in shell history or the process list.

</details>

### Contextio

Contextio moved to its own org: `Eras256/Contextio` now redirects to
[`contextio/Contextio`](https://github.com/contextio/Contextio). It runs
its own bounties: five open issues, none delivered yet, two with outside
PRs waiting for review. Upstream, three merged PRs added and updated its
listing on `stellar/stellar-dev-skill`
([#98](https://github.com/stellar/stellar-dev-skill/pull/98),
[#101](https://github.com/stellar/stellar-dev-skill/pull/101),
[#102](https://github.com/stellar/stellar-dev-skill/pull/102)).
No other upstream work for Contextio yet.

### Shared Stellar SDK work

Found while building the three Stellar products, not tied to one.

- **[js-stellar-sdk#1683](https://github.com/stellar/js-stellar-sdk/issues/1683):** `authorizeEntry`'s bare-signature fallback ignored `forAddress`. Closed by @Ryang-21 2026-09-24.
- **[js-stellar-sdk#1681](https://github.com/stellar/js-stellar-sdk/issues/1681):** `signAuthEntries` couldn't handle a non-master-key signer on a plain account. Fixed by @Ryang-21; I closed it 2026-09-26.
- **[js-stellar-sdk#1700](https://github.com/stellar/js-stellar-sdk/issues/1700):** `needsNonInvokerSigningBy()`/`signAuthEntries()` missed custom accounts. Closed by @Ryang-21 2026-09-25.
- **[py-stellar-base#1215](https://github.com/StellarCN/py-stellar-base/issues/1215):** signing CAP-71 delegates one after another in `authorize_entry()` silently broke an earlier signature. Closed by @overcat 2026-09-08.
- **[OpenZeppelin/stellar-contracts#865](https://github.com/OpenZeppelin/stellar-contracts/issues/865):** Protocol 28: `get_validated_context_by_id` won't compile on soroban-sdk 28.x. Closed 2026-09-26.
- **[smart-account-kit#7](https://github.com/stellar/smart-account-kit/issues/7):** the `@stellar/stellar-sdk` peer range had no upper limit, so v17 could get installed and break it. Closed by @kalepail 2026-09-08.
- **[js-stellar-sdk#1777](https://github.com/stellar/js-stellar-sdk/issues/1777):** asked for an lts-16 patch with a fixed axios. Open.
- **[stellar-docs#2811](https://github.com/stellar/stellar-docs/pull/2811):** a page on autonomous agents under contract accounts. Open PR.

### Other dependencies

- **[Creit-Tech/Stellar-Wallets-Kit#105](https://github.com/Creit-Tech/Stellar-Wallets-Kit/issues/105):** `signMessage()`'s docs say SEP-43 hex, but Freighter returns base64. Open.
- **[wevm/viem#5082](https://github.com/wevm/viem/issues/5082):** `shouldRetry` didn't retry QuickNode's `-32007` rate-limit error. My fix [#5083](https://github.com/wevm/viem/pull/5083) was merged by @jxom 2026-09-16.
- **[base/account-sdk#405](https://github.com/base/account-sdk/issues/405):** `getPaymentStatus()` gets the receipt but never returns `transactionHash`. My fix [#406](https://github.com/base/account-sdk/pull/406) is open.

### Hackathons outside the portfolio

Weekend builds, none with a public repo. Two wins were announced by the
event itself. The third only has my own tweet, so take it as that.

- **[ActivaChain](https://activachain.com):** won ETH Uruguay 2025, with
  Monserrat. [Announced](https://x.com/EthereumUruguay/status/1968785973749170227)
  by the event.
- **[CreatorChain](https://creatorchain-mx.vercel.app/):** 1st and 3rd
  place at ETH Mexico Monterrey 2025.
  [Announced](https://x.com/ethereum_mexico/status/1989005140838265067).
  Solo build.
- **[BioShield Insurance](https://bioshield-insurance.vercel.app/):** won
  the FDA Track at DeSci Builders Hackathon 2025, with Monserrat. Deployed
  on Solana, Base and Optimism. Source: [my own tweet](https://x.com/vaiossx/status/1972064428091924681).

</details>

---

## Stack

<p>
  <img src="https://img.shields.io/badge/Avalanche-E84142?style=for-the-badge&logo=data%3Aimage%2Fsvg%2Bxml%3Bbase64%2CPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI%2BPHBhdGggZmlsbD0iI2ZmZiIgZD0iTTExIDMuNSAyIDIwaDYuNmw2LTEwLjZ6Ii8%2BPHBhdGggZmlsbD0iI2ZmZiIgZD0iTTE2LjYgMTEuNiAxMiAyMGg5LjJ6Ii8%2BPC9zdmc%2B" alt="Avalanche" height="40">
  <img src="https://img.shields.io/badge/Base-0052FF?style=for-the-badge&logo=data%3Aimage%2Fsvg%2Bxml%3Bbase64%2CPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI%2BPGNpcmNsZSBjeD0iMTIiIGN5PSIxMiIgcj0iMTAiIGZpbGw9IiNmZmYiLz48cmVjdCB4PSIwIiB5PSIxMC42IiB3aWR0aD0iMTMuNSIgaGVpZ2h0PSIyLjgiIGZpbGw9IiMwMDUyRkYiLz48L3N2Zz4%3D" alt="Base" height="40">
  <img src="https://img.shields.io/badge/Monad-836EF9?style=for-the-badge&logo=data%3Aimage%2Fsvg%2Bxml%3Bbase64%2CPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI%2BPHJlY3QgeD0iNS41IiB5PSI1LjUiIHdpZHRoPSIxMyIgaGVpZ2h0PSIxMyIgcng9IjMuNSIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjZmZmIiBzdHJva2Utd2lkdGg9IjMiIHRyYW5zZm9ybT0icm90YXRlKDQ1IDEyIDEyKSIvPjwvc3ZnPg%3D%3D" alt="Monad" height="40">
  <img src="https://img.shields.io/badge/Solana-9945FF?style=for-the-badge&logo=solana&logoColor=white" alt="Solana" height="40">
  <img src="https://img.shields.io/badge/Stellar-000000?style=for-the-badge&logo=stellar&logoColor=white" alt="Stellar" height="40">
</p>
<p>
  <img src="https://img.shields.io/badge/Soroban-1F6FEB?style=for-the-badge&logo=stellar&logoColor=white" alt="Soroban" height="30">
  <img src="https://img.shields.io/badge/Anchor-1E3A8A?style=for-the-badge&logo=data%3Aimage%2Fsvg%2Bxml%3Bbase64%2CPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjZmZmIiBzdHJva2Utd2lkdGg9IjIiIHN0cm9rZS1saW5lY2FwPSJyb3VuZCI%2BPGNpcmNsZSBjeD0iMTIiIGN5PSI1IiByPSIyLjIiLz48cGF0aCBkPSJNMTIgNy4yVjIxTTcuNSAxMC41aDlNNCAxMy41YTggOCAwIDAgMCAxNiAwIi8%2BPC9zdmc%2B" alt="Anchor" height="30">
  <img src="https://img.shields.io/badge/Solidity-363636?style=for-the-badge&logo=solidity&logoColor=white" alt="Solidity" height="30">
  <img src="https://img.shields.io/badge/Rust-000000?style=for-the-badge&logo=rust&logoColor=white" alt="Rust" height="30">
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript" height="30">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python" height="30">
  <img src="https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white" alt="Next.js" height="30">
  <img src="https://img.shields.io/badge/x402-0F766E?style=for-the-badge" alt="x402" height="30">
</p>

**Protocols:** x402, MPP, SEP-41/SAC, SEP-43, SEP-53, CAP-71 delegated
auth, MCP, EAS, EIP-712, WebAuthn passkeys

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://github-stats-extended.vercel.app/api?username=Eras256&show_icons=true&show=reviews,prs_merged,prs_merged_percentage&rank_icon=percentile&theme=dark">
  <img alt="Commits, pull requests, merged PRs, reviews and issues for Eras256" src="https://github-stats-extended.vercel.app/api?username=Eras256&show_icons=true&show=reviews,prs_merged,prs_merged_percentage&rank_icon=percentile">
</picture>

---

## Check it yourself

[All my PRs](https://github.com/search?q=author%3AEras256+is%3Apr&type=pullrequests)
·
[all my issues](https://github.com/search?q=author%3AEras256+is%3Aissue&type=issues)
·
[Nirium's bounty board](https://github.com/nirium-protocol/nirium/issues?q=is%3Aissue)
·
[Contextio's open issues](https://github.com/contextio/Contextio/issues)

**Contact:** open an issue on any repo above, or
[nirium.xyz](https://nirium.xyz) · [periplo.xyz](https://periplo.xyz) ·
[vouch402.xyz](https://www.vouch402.xyz) · [kumply.xyz](https://kumply.xyz) ·
[contextio.xyz](https://contextio.xyz) · [theprova.xyz](https://www.theprova.xyz) ·
[votalo.xyz](https://www.votalo.xyz) · X:
[@vaiossx](https://x.com/vaiossx) · Discord: `vaiossx`
