# Migration Playbook

## 0. Bootstrap a New Target Only When Needed

When no HarmonyOS project exists, create the smallest buildable target needed to establish package identity, module boundary, SDK baseline, and launch path. Record those choices and verify that the blank target builds and launches.

Phase 0 is infrastructure only: do not claim a source page or functional category has migrated, invent a design system, or use substitute UI assets. Begin Phase A only after the bootstrap identity is frozen.

## 1. Freeze the Boundary

Record source revision, target revision or bootstrap identity, dirty files, source license, build/package identity, device and OS version, SDK/firmware version, and requested scope. The source stays read-only. Use an isolated target branch or worktree when the target has user changes.

Do not begin implementation if the source revision, target state, or requested capability is ambiguous.

## 2. Reconcile a Dirty Target Worktree

A dirty target is not something to make clean by force. Before migration edits:

1. Preserve the active tree and its user-owned state. Do not use reset, clean, stash, broad staging, or broad ignore as a substitute for reconciliation.
2. Create or reuse a clean audit worktree at the exact target revision; do not inspect or build from a different snapshot and call it equivalent.
3. Classify each changed or untracked path as one of: frozen user edit; recoverable source, document, or migration input; verified generated evidence or cache; binary/media pending provenance or LFS; or unknown.
4. Recover only explicit verified source, document, and input paths in small reversible commits. For verified generated output, add only a narrow ignore rule and retain files on disk. Keep unknown and provenance-pending binary/media visible and `BLOCKED` with an owner and exit condition.
5. Record path boundary, count or size, decision, evidence, and exit condition in the ledger. If a category is still unknown, do not stage, ignore, delete, or migrate through it.

If the target is clean, record that fact and continue. A clean audit worktree proves the baseline only; it does not erase or reinterpret frozen user edits.

## 3. Phase A: Page UI Migration

Inventory source pages, routes, visual assets, navigation, typography, safe areas, loading, empty, permission, error, and disabled states. Record asset paths, hashes where practical, dimensions, source font files, and layout measurements. Group only related pages that can be accepted together.

For each page group:

1. Trace the source page and navigation call chain.
2. Inventory every visible source element: text, component, icon, graphic, image, animation, font, material, navigation affordance, and visible state.
3. Record and reproduce every visible element's content, dimensions, position, shape, asset, typography, color, spacing, layering, opacity, geometry, corner treatment, and other visible characteristics exactly. Unless the user explicitly approves a scoped exception, do not generate, search, substitute, use a native default, or creatively redesign any UI material.
4. Map the source design to HarmonyOS layers without changing its user-visible result. Render an explicit source-matched unavailable state for functions not yet migrated.
5. Compare the identified final package with the recorded source under the same comparison conditions. Any mismatch—including text, a component, icon, graphic, material, size, position, style, or visible state—is `FAIL`, not “close enough.”
6. Record `DEVICE_UI` evidence only after every recorded visible element matches. Only then may that group's functional migration begin.

If source assets are missing, access/license is unclear, or a platform constraint prevents exact rendering or interaction, stop the page group as `BLOCKED` and ask the user. A written, element-specific user exception is the only way to record a deviation. UI acceptance proves only the page group; it does not prove real data, permissions, devices, network, lifecycle, or backend behavior.

## 4. Phase B: Functional Category Migration

After its page group is accepted, migrate one category at a time:

| Category | Required review |
| --- | --- |
| Data and storage | Ownership, schemas, migration, read-back confirmation, deletion/export, corrupt or short writes. |
| Permissions | Denial, revocation, settings return, unavailable state, and no hidden fallback. |
| Networking and AI/tools | Authorization, parsing bounds, source/time semantics, cancellation, retry safety, and non-fabricated failure state. |
| Device, BLE, and vendor SDK | Permissions, ownership, protocol version, reconnect/timeout, real-device evidence, and release on destruction. |
| Background and lifecycle | Scheduling limits, foreground/background/kill recovery, power impact, and cleanup. |
| Audio, voice, and media | Accepted command versus observed state, cancellation, late events, focus, and resource release. |

Use current official HarmonyOS documentation and actual source call chains. Do not infer equivalence from similarly named APIs. If a required contract is absent, write the smallest diagnostic or test that demonstrates the gap and mark it `BLOCKED`.

## 5. Vertical Slice, Throughput, and Handoff

For one category row or cohesive row group: write normal, boundary, and failure tests first; make the smallest target-layer change; verify stale events, cancellation, timeout, retry, release, and concurrency where relevant; then bind results to source revision and final package identity.

Use inexpensive source, asset, and narrow local checks per slice. Build the final package and use Previewer after a cohesive page group or integration milestone, not after every isolated visual edit. Batch read-only source inventory and same-condition comparison work where it stays traceable, but never concurrently edit the same target path or share one live device session.

An isolated static UI candidate can establish source/resource or `CODE`/`LOCAL` evidence only. It is not final-package `DEVICE_UI`, functional, device, or page-group acceptance. For external blockers, record missing evidence, owner, and the next smallest safe action instead of repeatedly retrying the same probe.

At the end of every slice, report changed files, evidence, `NOT TESTED`/`BLOCKED` items, risk, target Git state, and the next smallest slice.

## 6. Progress Reporting

Report workspace hygiene, source/code/local evidence, and end-to-end acceptance separately. Do not roll one into another. State a percentage only when the ledger defines a weighted denominator; otherwise use evidence labels and the exact blocker.

