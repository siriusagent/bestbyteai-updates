<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.019

Alpha.019 is a permission-system hotfix release. A real Sirius production
trace proved that the previous synthetic Auto gate did not represent actual
transcript/action shapes, and the Auto refactor also regressed the older
Permissive bypass contract. This release fixes both families and records the
failed assumptions instead of carrying forward the invalid certification.

## Fixed

- **Auto classifies the action Sirius is actually about to run (BUG-406).** A
  foreground request contains the candidate only; nested work contains its
  direct parent and candidate. Unrelated historical tool calls are no longer
  invented as one executable action closure.
- **Project-scoped authority reaches the classifier (BUG-406).** Runtime-issued
  workspace/project identity and candidate locus let ordinary reversible audit,
  implementation, and test work remain inside the task the user assigned.
- **Shell composition no longer looks like unknown targeting (BUG-406).**
  Pipelines, command sequences, quoted metacharacters, relative globs, sourced
  project scripts, redirections, and absolute system executables preserve
  resolvable workspace targets. Active variables and command/process/arithmetic
  substitution remain unresolved and fail closed.
- **Valid classifier JSON is not converted into an infrastructure failure.**
  Long diagnostic explanations are bounded after schema validation, preventing
  false malformed-output counts and turn-wide saturation.
- **Channel calls retain their real execution surface.** Authority projection
  and audit no longer relabel channel activity as foreground.
- **Permissive is automatic again (BUG-407).** Its pre-Auto contract is
  restored: ordinary non-bypass-immune Browser mutations, checker reviews, and
  ask rules do not open approval UI and do not call the classifier. Hard denies,
  human-required authority, bypass-immune checks, and the repeated-denial
  checkpoint remain enforced.
- **Dead permission machinery is removed.** The never-constructed shadow
  subsystem and production-only test doubles are gone; historical shadow audit
  rows remain readable.

## Verification and certification status

- The exact persisted SiriusPDF calls that exposed the production-history and
  shell-locus failures now replay against the current projection and policy.
- The Permissive regression is covered through the production Browser mutating
  checker. A rebuilt signed throwaway reran the original three-site kitchen
  prompt byte-for-byte: all 16 audited calls were mode-approved, including
  three tab mutations and one browser transaction, with zero prompts or
  denials.
- Focused permission/Browser coverage passed 253 tests; the broader affected
  suite passed 505 tests before release packaging.
- The alpha.017/alpha.018 synthetic-only Auto certificates are invalidated.
  Production-trace regression evidence is now mandatory. Alpha.019 does not
  claim a replacement statistical certificate.

## Distribution

- macOS 26 (Tahoe) or later.
- Developer ID signed and Apple notarized.
- Sparkle build 144 with the matching signed core-runtime feed.
