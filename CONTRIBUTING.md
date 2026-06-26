
# Contributing to trustless-ai

This org exists to make one promise true: **every claim here is independently checkable from
public data, without trusting anyone.** These conventions exist to keep that promise enforceable as
the org grows.

## The membrane (the one hard rule)

**Every repo ships a `recompute` / `verify` step, documented near the top of its README.** On-chain
or off, a newcomer must be able to re-derive the repo's central claim from public data in one
command. A repo that can't be independently re-verified doesn't belong here — that boundary is what
lets the tent widen to "AI + blockchain broadly" without sliding into "anything adjacent." The name
is earned by what a stranger can re-derive.

## The repo categories — keep the split hard

| Category | Is | Is not |
|---|---|---|
| `agent-ercs` | the shared **on-chain** dependency: versioned, audited contracts you import and pin | a place for project-specific logic |
| `agent-sdk` | the shared **off-chain** verify/recompute tooling, one install, one API | a black box you have to trust |
| `agent-contracts-examples` | minimal runnable quickstarts over the two shared deps | production code |
| project repos | fast-moving, opinionated, prove the stack in prod | a source of truth other repos depend on |

**Project code never leaks back into a shared dependency.** The shared deps stay boring and audited;
project repos move fast. Both directions of that wall are load-bearing.

## The SDK is a convenience layer, never the only path

`agent-sdk` exists so verification is one import and five minutes, not a research project — that's
how more people actually run it. But packaging must never soften the promise:

1. **The zero-dependency recompute scripts stay the trust anchor and stay first-class.** The SDK is a
   thin, transparent wrapper over them, not a replacement.
2. **Every SDK README shows both paths side by side** — `verifyFullFlow()` *and* the manual,
   zero-dep recompute — so "audit the verifier itself" is the headline, not a footnote.
3. **The SDK pins an exact recompute-lib version**, so anyone can see precisely which logic their
   one-liner ran.

Convenience that you can always step underneath. Get this right and the SDK strengthens the promise
instead of diluting it.

## Reference-impl conventions

- **Clone-and-run, not just spec markdown.** Solidity ships with tests + deploy scripts; off-chain
  tools ship runnable.
- **Provider-agnostic where possible.** A contributor's live endpoint/key is fine as the default
  working example, clearly labelled as such, with the parameters to retarget it documented.
- **Losses retained.** Where a repo publishes a track record, it publishes failures too — a record
  that only shows wins isn't recomputable, it's marketing.

## Governance

Owners listed on the org. Structural decisions (new shared deps, conventions, license) are made in
the open by the group. This document and the boundary-chain map in the profile README move together
and should stay in sync with the Composition Note.
