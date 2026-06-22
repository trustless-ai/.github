     The boundary-chain rows below carry the INVARIANT + repo home; exact ERC pins come from
     Merlini's Composition Note (offered as the seed for this map) so we don't misattribute numbers. -->

# onchain-ai

A neutral, open-source home for the standards, reference implementations, and live proofs at the
intersection of **AI agents and blockchain**. The defining promise: **every claim here is
independently checkable from public data — a stranger can re-derive it without trusting anyone.**

## The boundary chain

Each layer defends one invariant and hands a reference to the next. The whole chain re-verifies
from public data.

| Link | Invariant it defends | Lives in |
|---|---|---|
| **agreement** | the parties agreed to this, on these terms | project repo |
| **identity** | the agent is who it claims to be | `agent-ercs` |
| **dispatch** | the task reached the agent it was meant for | `agent-ercs` |
| **provenance** | the inputs/outputs are committed and intact | `agent-ercs` |
| **verify** | the verdict was committed, intact, by the claimed key | `agent-sdk` |
| **anchor** | the commitment existed *before* its outcome (PoW precedence) | `agent-sdk` |
| **eligibility** | the actor was permitted to act | `agent-ercs` |
| **settlement** | the outcome settled on a public, non-editable account | project repo |
| **reputation** | standing is a deterministic function of public settled outcomes | `agent-sdk` |

*(Chain order per the Composition Note; exact ERC references pinned there.)*

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
  fast-moving, opinionated implementations that prove the stack in production.

## The one rule

**Nothing goes in that a third party can't independently verify from public data.** Every repo —
on-chain or off — carries a `recompute` / `verify` step near the top of its README. The name is
earned by what a stranger can re-derive. See [CONTRIBUTING](./CONTRIBUTING.md).

## License

TBD by the group (proposed: permissive for code, CC0/MIT for specs).
