# Giovanny Amador (`Eras256`)

Co-founder of [Nirium](https://nirium.xyz). I build payment and verification
infrastructure for AI agents: how an
agent pays for a service, how it checks who it is paying, and how it proves
what it did. Mostly TypeScript, Rust and Soroban.

Based in Mexico.

## What I'm building

**[Nirium](https://nirium.xyz):** payment, audit and execution rails on
Stellar for apps, backends and AI agents. Charge or pay per request in USDC
(x402) and leave a receipt anyone can verify, without trusting us.
Open source and non-custodial: the user's own key signs every payment.
I co-founded it with [Monserrat Mendoza](https://github.com/M0nsxx), who
co-owns and publishes all four packages, on npm and on PyPI.

- Packages: [`nirium`](https://www.npmjs.com/package/nirium) (npm and
  [PyPI](https://pypi.org/project/nirium/)),
  [`nirium-cli`](https://www.npmjs.com/package/nirium-cli),
  [`nirium-mcp`](https://www.npmjs.com/package/nirium-mcp) and
  [`nirium-pollar-adapter`](https://www.npmjs.com/package/nirium-pollar-adapter).
- Code: [nirium-protocol/nirium](https://github.com/nirium-protocol/nirium).
- Two Stellar Community Fund Instawards, both paid on-chain
  ([May](https://stellar.expert/explorer/public/tx/fd0f7469ae78b76ca5c4186cd7e1b24c081c407758a92cff3a56f376d01e91d1),
  [July](https://stellar.expert/explorer/public/tx/7784ad6eb2b27ace75ce2fe4b7290fb1b8241da425331bfbda2e939b47759b7e)).
- Every claim, with its transaction hash:
  [EVIDENCE.md](https://github.com/nirium-protocol/nirium/blob/main/EVIDENCE.md).
- Open to outside contributors: 38 pull requests from people outside the
  team merged so far, through Stellar Wave (Drips) and GrantFox
  ([live list](https://nirium.xyz/stats)).
- Teaching: with Monserrat I run [Código 402](https://nirium.xyz/blog/codigo-402-agentes-que-pagan),
  a free Spanish-language bootcamp with BAF where developers build an API
  that charges per use and an agent that pays on its own, on Stellar testnet.

## Open source, with links you can check

**29 pull requests merged into projects I don't maintain**:
[see them all](https://github.com/search?q=author%3AEras256%20is%3Apr%20is%3Amerged%20repo%3Ax402-foundation/x402%20repo%3Astellar/stellar-dev-skill%20repo%3Astellar/stellar-mpp-sdk%20repo%3Aotter-sec/anchor%20repo%3Awevm/viem%20repo%3ATrustless-Work/agentic-escrow-research%20repo%3ASorobanAgents/agentrail%20repo%3Apollar-xyz/pollar-apps&type=pullrequests).

- **x402 (the HTTP payments protocol), 6 merged:** closed a gap that let
  settlement amounts exceed their authorized cap
  ([#3338](https://github.com/x402-foundation/x402/pull/3338)), fixed
  network matching for facilitators that serve several chains
  ([#3215](https://github.com/x402-foundation/x402/pull/3215)), fixed broken
  discovery URLs for MCP tools
  ([#3138](https://github.com/x402-foundation/x402/pull/3138)), fixed a crash
  in the official e2e conformance suite
  ([#3228](https://github.com/x402-foundation/x402/pull/3228)), added a
  missing check in the Stellar facilitator safety checks
  ([#3336](https://github.com/x402-foundation/x402/pull/3336)) and documented
  an unsupported Stellar setting where it is configured
  ([#3339](https://github.com/x402-foundation/x402/pull/3339)).
- **Stellar, 9 merged:** production patterns for x402 and MPP in the official
  Stellar dev skill ([#97](https://github.com/stellar/stellar-dev-skill/pull/97),
  merged after about 16 review rounds), a correction to its own MPP
  production claim ([#150](https://github.com/stellar/stellar-dev-skill/pull/150)),
  and a fix for two invalid mainnet constants in the MPP SDK
  ([#69](https://github.com/stellar/stellar-mpp-sdk/pull/69)).
- **Anchor, 4 merged by the maintainer,** starting with
  [#4960](https://github.com/otter-sec/anchor/pull/4960), which removed a
  dependency that could break builds.
- **viem:** retry on QuickNode's rate-limit error code
  ([#5083](https://github.com/wevm/viem/pull/5083)).
- **Trustless Work, 6 merged:** use cases and research notes on agent-driven
  escrow in their
  [agentic-escrow-research](https://github.com/Trustless-Work/agentic-escrow-research) repo.
- **Pollar:** a demo app for paying x402 APIs from a Pollar social-login
  wallet ([pollar-apps#30](https://github.com/pollar-xyz/pollar-apps/pull/30)).
- **AgentRail, 2 merged:** optional public receipts for agent spends and
  proof-of-task ([#68](https://github.com/SorobanAgents/agentrail/pull/68)), and an
  opt-in `--receipt` flag in their demo ([#70](https://github.com/SorobanAgents/agentrail/pull/70)).
- **OpenZeppelin:** a shared mainnet facilitator was down for 32 days. I
  reported it and confirmed the fix with a real payment, not just a 200
  response
  ([relayer-plugin-x402-facilitator#47](https://github.com/OpenZeppelin/relayer-plugin-x402-facilitator/issues/47)).
- **Ethereum Attestation Service:** reported a security bug in
  `getUIDsFromAttestReceipt`, fixed in eas-sdk 2.10.0
  ([#132](https://github.com/ethereum-attestation-service/eas-sdk/issues/132)).

When I'm wrong, I say so: I closed my own
[OpenZeppelin/stellar-contracts#839](https://github.com/OpenZeppelin/stellar-contracts/issues/839)
after finding the bug was in how I built the auth entries, not in the
library.

Everything I ship is non-custodial: the user's own wallet signs, or a role
that can't move funds by design.

## Hackathons

Weekend builds. Two wins were announced by the
event itself and one was reported by the press. The last one only has my own
tweet, so take it as that.

- **ActivaChain:** 1st place, ETH Uruguay 2025
  hackathon, in a team of six with Monserrat; prize included the trip to Devconnect.
  [Announced](https://x.com/EthereumUruguay/status/1968730843498610713)
  by the event.
- **[CreatorChain](https://creatorchain-mx.vercel.app/):** 1st and 3rd
  place at ETH Mexico Monterrey 2025.
  [Announced](https://x.com/ethereum_mexico/status/1989005140838265067). Built with two
  other teammates.
- **Sui Loop:** 3rd place at the FinTech World Cup México 2026 national
  qualifiers, behind Linko and Network Bank.
  [Reported](https://ecosistemastartup.com/?p=69334) by the press.
- **[BioShield Insurance](https://bioshield-insurance.vercel.app/):** won
  the FDA Track at DeSci Builders Hackathon 2025, with Monserrat. Source: [my own tweet](https://x.com/vaiossx/status/1972064428091924681).

---

## Check it yourself

[All my PRs](https://github.com/search?q=author%3AEras256+is%3Apr&type=pullrequests)
·
[all my issues](https://github.com/search?q=author%3AEras256+is%3Aissue&type=issues)

**Contact:** X [@vaiossx](https://x.com/vaiossx) · Discord: `vaiossx`
