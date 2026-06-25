     The boundary-chain rows below carry the INVARIANT + repo home; exact ERC pins come from
     Merlini's Composition Note (offered as the seed for this map) so we don't misattribute numbers. -->

# onchain-ai

A neutral, open-source home for the standards, reference implementations, and live proofs at the
intersection of **AI agents and blockchain**. The defining promise: **every claim here is
independently checkable from public data — a stranger can re-derive it without trusting anyone.**

## The boundary chain

Each layer defends one invariant and hands a reference to the next. The whole chain re-verifies
from public data.

| Link | Invariant it defends | Lives in | ERC pin |
|---|---|---|---|
| **agreement** | the parties agreed to this, on these terms | project repo | ERC-8001 (Agent Coordination Framework) |
| **identity** | the agent is who it claims to be | `agent-ercs` | ERC-8004 (Trustless Agents) |
| **dispatch** | the task reached the agent it was meant for | `agent-ercs` | ERC-8301 (AgentTask) |
| **provenance** | the inputs/outputs are committed and intact | `agent-ercs` | ERC-8281 / OCP + ERC-8299 (WYRIWE) |
| **verify** | the verdict was committed, intact, by the claimed key | `agent-sdk` | ERC-8274 |
| **anchor** | the commitment existed *before* its outcome (PoW precedence) | `agent-sdk` | ERC-8263 (TruthAnchorV1) + Bitcoin OTS |
| **eligibility** | the actor was permitted to act | `agent-ercs` | ReceiptOS |
| **settlement** | the outcome settled on a public, non-editable account | project repo | ERC-8275 (settlement axis) |
| **reputation** | standing is a deterministic function of public settled outcomes | `agent-sdk` | ERC-8275 (reputation axis) |

*(Chain order + ERC pins per the [Composition Note](https://ethereum-magicians.org/t/composition-note-agent-service-consultation-flow-composing-the-agent-ercs-8004-8263-8274-8275-8281-8299-8301-informational/28833). Each pin names the spec that defends the link; some are filed PRs (8004/8001 in-repo, 8275/8299/8309 open), others pre-PR.)*

## Repos

- **[`.github`](https://github.com/onchain-ai/.github)** — this front door: boundary-chain map,
  contribution guide, community health files.
- **`agent-ercs`** — production-grade, versioned, audited ERC contracts. The shared **on-chain**
  dependency you import and pin. Think OpenZeppelin for AI-agent infrastructure.
- **`agent-sdk`** — the shared **off-chain** verify/recompute tooling. One
  `npm install @onchain-ai/agent-sdk`, one consistent API to check every layer's claims. A thin,
  transparent wrapper over zero-dependency recompute scripts that remain the trust anchor.
- **`agent-contracts-examples`** — minimal, runnable quickstarts using `agent-ercs` + `agent-sdk`.
- **Project repos** — `ccip-router`, `ConsultEscrow`, and whatever each layer author brings: the
  fast-moving, opinionated implementations that prove the stack in production. Registered:
  - **[`ccip-router`](https://github.com/trustless-ai/ccip-router)** — CCIP-Read gateway mesh (peer
    sync, signed records, on-chain attestation); reference impl of the *Gateway Mesh Sync Protocol*
    ERC. *Verify:* recompute any attestation trustlessly via the live `WyriweProofVerifier` (ERC-8274,
    Sepolia) — no node in the loop.
  - **[`hack-ens-recovery`](https://github.com/TMerlini/hack-ens-recovery)** — owner-bound, verifiable
    recovery agent: WYRIWE commit-before-outcome receipt → on-chain BIP-340 verify (no oracle) →
    owner-bound escrow with a replay nullifier. Composes 8004/8263/8274/8275/8281/8299/8301 on a real
    use case. *Verify:* `cd contracts && forge test` (incl. all 15 official BIP-340 vectors); live on
    Sepolia, full fee-release proven on-chain. `BIP340.sol` flagged pre-mainnet-audit.

## The one rule

**Nothing goes in that a third party can't independently verify from public data.** Every repo —
on-chain or off — carries a `recompute` / `verify` step near the top of its README. The name is
earned by what a stranger can re-derive. See [CONTRIBUTING](./CONTRIBUTING.md).

## License

TBD by the group (proposed: permissive for code, CC0/MIT for specs).
