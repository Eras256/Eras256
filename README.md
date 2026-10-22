# Giovanny Amador (`Eras256`)

I build payment and verification infrastructure for AI agents: how an
agent pays for a service, how it checks who it is paying, and how it proves
what it did. Mostly TypeScript, Rust and Soroban.

Based in Mexico.

## Open source, with links you can check

- **x402 (the HTTP payments protocol):** found and fixed a crash in the
  official e2e conformance suite
  ([#3228](https://github.com/x402-foundation/x402/pull/3228), merged) and
  added a missing check in the facilitator safety checks
  ([#3336](https://github.com/x402-foundation/x402/pull/3336), merged).
  Also reported [#3270](https://github.com/x402-foundation/x402/issues/3270),
  fixed by the maintainer in #3306.
- **Stellar:** production patterns for x402 and MPP in the official Stellar
  dev skill ([#97](https://github.com/stellar/stellar-dev-skill/pull/97),
  merged after about 16 review rounds), and a fix for two invalid mainnet
  constants in the MPP SDK
  ([#69](https://github.com/stellar/stellar-mpp-sdk/pull/69), merged).
- **OpenZeppelin:** a shared mainnet facilitator was down for 32 days. I
  reported it and confirmed the fix with a real payment, not just a 200
  response
  ([relayer-plugin-x402-facilitator#47](https://github.com/OpenZeppelin/relayer-plugin-x402-facilitator/issues/47)).
- **Anchor:** four PRs merged by the maintainer, starting with
  [#4960](https://github.com/otter-sec/anchor/pull/4960), which removed a
  dependency that could break builds.
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

---

## Stack

<p>
  <img src="https://img.shields.io/badge/Avalanche-E84142?style=for-the-badge&logo=data%3Aimage%2Fsvg%2Bxml%3Bbase64%2CPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI%2BPHBhdGggZmlsbD0iI2ZmZiIgZD0iTTExIDMuNSAyIDIwaDYuNmw2LTEwLjZ6Ii8%2BPHBhdGggZmlsbD0iI2ZmZiIgZD0iTTE2LjYgMTEuNiAxMiAyMGg5LjJ6Ii8%2BPC9zdmc%2B" alt="Avalanche" height="40">
  <img src="https://img.shields.io/badge/Base-0052FF?style=for-the-badge&logo=data%3Aimage%2Fsvg%2Bxml%3Bbase64%2CPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI%2BPGNpcmNsZSBjeD0iMTIiIGN5PSIxMiIgcj0iMTAiIGZpbGw9IiNmZmYiLz48cmVjdCB4PSIwIiB5PSIxMC42IiB3aWR0aD0iMTMuNSIgaGVpZ2h0PSIyLjgiIGZpbGw9IiMwMDUyRkYiLz48L3N2Zz4%3D" alt="Base" height="40">
  <img src="https://img.shields.io/badge/Ethereum-3C3C3D?style=for-the-badge&logo=ethereum&logoColor=white" alt="Ethereum" height="40">
  <img src="https://img.shields.io/badge/Monad-836EF9?style=for-the-badge&logo=data%3Aimage%2Fsvg%2Bxml%3Bbase64%2CPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI%2BPHJlY3QgeD0iNS41IiB5PSI1LjUiIHdpZHRoPSIxMyIgaGVpZ2h0PSIxMyIgcng9IjMuNSIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjZmZmIiBzdHJva2Utd2lkdGg9IjMiIHRyYW5zZm9ybT0icm90YXRlKDQ1IDEyIDEyKSIvPjwvc3ZnPg%3D%3D" alt="Monad" height="40">
  <img src="https://img.shields.io/badge/Solana-9945FF?style=for-the-badge&logo=solana&logoColor=white" alt="Solana" height="40">
  <img src="https://img.shields.io/badge/Stellar-000000?style=for-the-badge&logo=stellar&logoColor=white" alt="Stellar" height="40">
</p>

<p><strong>Stellar</strong><br>
  <img src="https://img.shields.io/badge/Soroban-1F6FEB?style=for-the-badge&logo=stellar&logoColor=white" alt="Soroban" height="30">
  <img src="https://img.shields.io/badge/Stellar%20SDK-000000?style=for-the-badge&logo=stellar&logoColor=white" alt="Stellar SDK" height="30">
  <img src="https://img.shields.io/badge/OpenZeppelin%20Stellar-4E5EE4?style=for-the-badge&logo=openzeppelin&logoColor=white" alt="OpenZeppelin Stellar" height="30">
  <img src="https://img.shields.io/badge/Stellar%20Wallets%20Kit-000000?style=for-the-badge&logo=stellar&logoColor=white" alt="Stellar Wallets Kit" height="30">
</p>

<p><strong>EVM: Ethereum, Base, Avalanche, Monad</strong><br>
  <img src="https://img.shields.io/badge/Solidity-363636?style=for-the-badge&logo=solidity&logoColor=white" alt="Solidity" height="30">
  <img src="https://img.shields.io/badge/OpenZeppelin-4E5EE4?style=for-the-badge&logo=openzeppelin&logoColor=white" alt="OpenZeppelin" height="30">
  <img src="https://img.shields.io/badge/Hardhat-B58B00?style=for-the-badge&logo=data%3Aimage%2Fsvg%2Bxml%3Bbase64%2CPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI%2BPHBhdGggZmlsbD0iI2ZmZiIgZD0iTTQgMTVhOCA4IDAgMCAxIDE2IDB6Ii8%2BPHJlY3QgeD0iMiIgeT0iMTUiIHdpZHRoPSIyMCIgaGVpZ2h0PSIzIiByeD0iMS41IiBmaWxsPSIjZmZmIi8%2BPHJlY3QgeD0iMTEiIHk9IjUiIHdpZHRoPSIyIiBoZWlnaHQ9IjYiIGZpbGw9IiNCNThCMDAiLz48L3N2Zz4%3D" alt="Hardhat" height="30">
  <img src="https://img.shields.io/badge/Foundry-1C1C1C?style=for-the-badge" alt="Foundry" height="30">
  <img src="https://img.shields.io/badge/viem-1E1E20?style=for-the-badge" alt="viem" height="30">
  <img src="https://img.shields.io/badge/wagmi-1B1B1F?style=for-the-badge&logo=wagmi&logoColor=white" alt="wagmi" height="30">
  <img src="https://img.shields.io/badge/ethers-2535A0?style=for-the-badge&logo=ethers&logoColor=white" alt="ethers" height="30">
  <img src="https://img.shields.io/badge/EAS-3C3C3D?style=for-the-badge&logo=ethereum&logoColor=white" alt="EAS" height="30">
  <img src="https://img.shields.io/badge/Avalanche%20ICM-E84142?style=for-the-badge&logo=data%3Aimage%2Fsvg%2Bxml%3Bbase64%2CPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI%2BPHBhdGggZmlsbD0iI2ZmZiIgZD0iTTExIDMuNSAyIDIwaDYuNmw2LTEwLjZ6Ii8%2BPHBhdGggZmlsbD0iI2ZmZiIgZD0iTTE2LjYgMTEuNiAxMiAyMGg5LjJ6Ii8%2BPC9zdmc%2B" alt="Avalanche ICM" height="30">
</p>

<p><strong>Solana</strong><br>
  <img src="https://img.shields.io/badge/Anchor-1E3A8A?style=for-the-badge&logo=data%3Aimage%2Fsvg%2Bxml%3Bbase64%2CPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjZmZmIiBzdHJva2Utd2lkdGg9IjIiIHN0cm9rZS1saW5lY2FwPSJyb3VuZCI%2BPGNpcmNsZSBjeD0iMTIiIGN5PSI1IiByPSIyLjIiLz48cGF0aCBkPSJNMTIgNy4yVjIxTTcuNSAxMC41aDlNNCAxMy41YTggOCAwIDAgMCAxNiAwIi8%2BPC9zdmc%2B" alt="Anchor" height="30">
  <img src="https://img.shields.io/badge/Solana%20Kit-9945FF?style=for-the-badge&logo=solana&logoColor=white" alt="Solana Kit" height="30">
  <img src="https://img.shields.io/badge/web3.js-9945FF?style=for-the-badge&logo=solana&logoColor=white" alt="web3.js" height="30">
</p>

<p><strong>Agent payments</strong><br>
  <img src="https://img.shields.io/badge/x402-0F766E?style=for-the-badge" alt="x402" height="30">
  <img src="https://img.shields.io/badge/MPP-374151?style=for-the-badge" alt="MPP" height="30">
  <img src="https://img.shields.io/badge/MCP-000000?style=for-the-badge&logo=modelcontextprotocol&logoColor=white" alt="MCP" height="30">
  <img src="https://img.shields.io/badge/LangChain-1C3C3C?style=for-the-badge&logo=langchain&logoColor=white" alt="LangChain" height="30">
  <img src="https://img.shields.io/badge/IPFS-65C2CB?style=for-the-badge&logo=ipfs&logoColor=white" alt="IPFS" height="30">
</p>

<p><strong>3D and games</strong><br>
  <img src="https://img.shields.io/badge/Blender-E87D0D?style=for-the-badge&logo=blender&logoColor=white" alt="Blender" height="30">
  <img src="https://img.shields.io/badge/Unity-000000?style=for-the-badge&logo=unity&logoColor=white" alt="Unity" height="30">
</p>

<p><strong>Languages and apps</strong><br>
  <img src="https://img.shields.io/badge/Rust-000000?style=for-the-badge&logo=rust&logoColor=white" alt="Rust" height="30">
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript" height="30">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python" height="30">
  <img src="https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white" alt="Next.js" height="30">
  <img src="https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=white" alt="React" height="30">
  <img src="https://img.shields.io/badge/Hono-E36002?style=for-the-badge&logo=hono&logoColor=white" alt="Hono" height="30">
  <img src="https://img.shields.io/badge/Express-000000?style=for-the-badge&logo=express&logoColor=white" alt="Express" height="30">
  <img src="https://img.shields.io/badge/Supabase-3ECF8E?style=for-the-badge&logo=supabase&logoColor=white" alt="Supabase" height="30">
  <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white" alt="Docker" height="30">
  <img src="https://img.shields.io/badge/Fly.io-7B3BE2?style=for-the-badge&logo=flydotio&logoColor=white" alt="Fly.io" height="30">
  <img src="https://img.shields.io/badge/Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white" alt="Vercel" height="30">
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

**Contact:** X [@vaiossx](https://x.com/vaiossx) · Discord: `vaiossx`
