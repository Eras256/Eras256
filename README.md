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
