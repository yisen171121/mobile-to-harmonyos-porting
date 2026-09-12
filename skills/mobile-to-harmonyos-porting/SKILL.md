---
name: mobile-to-harmonyos-porting
description: Use when incrementally porting or updating an Android, iOS, Flutter, React Native, or shared-native mobile app into an existing or newly initialized HarmonyOS target whose source UI requires exact element-level fidelity across text, components, icons, graphics, assets, layout, and visible states.
---

# Mobile to HarmonyOS Porting

Treat a port as behavior preservation with explicit platform differences, never as source-file conversion. Keep upstream source read-only, preserve target-user changes, and stop instead of guessing at destructive or unsupported behavior. The target may already exist or begin as a minimal HarmonyOS project.

## Non-Negotiable Migration Order

0. **Target bootstrap only when absent:** create and build the smallest HarmonyOS target needed to establish its package identity, module boundary, SDK baseline, and launch path. This is not a feature or UI migration.
1. **UI first:** migrate and accept user-visible pages in small page groups before migrating their new functional behavior. For each group, confirm information hierarchy, navigation, unavailable/error/loading states, accessibility, supported layouts, and final-package UI evidence.
2. **Functions second:** after the relevant page group is accepted, migrate one functional category at a time: data/storage, permissions, networking, device/BLE, background/lifecycle, or AI/tool behavior. A UI pass is not functional evidence.
3. Do not merge unrelated page polish and functional categories into one slice. If a source feature requires its function to render safely, use explicit unavailable state until the function slice is verified.

## Accelerated Evidence-Preserving Delivery

Use this cadence after a clean buildable entry and a usable Previewer path are established; it accelerates UI work without lowering any gate.

1. For each source page, capture its source hash, assets/fonts, measurements, visible state branches, and screenshot baseline once; reuse that record for every HarmonyOS slice.
2. Migrate the real entry path in order: page UI → state → route → service. Keep `ui_baseline` for source assets and isolated hard-to-integrate visuals, never as the default acceptance path.
3. Run only the relevant static gate and smallest module build per slice. Accumulate a default batch of four UI slices (never more than five), then run the entry gate suite, one unsigned HAP build, and one fixed-environment emulator/device pass. Keep independently captured screenshot, layout, and log evidence for each page.
4. Update the ledger and acceptance board once per batch. Do not repeatedly probe Previewer without a confirmed usable control surface; batch pages under the same target identity, theme, font scale, and resolution.
5. Keep P5 data, P6 services, and P7 BLE frozen behind their evidence gates. Maintain an explicit blocker list with missing evidence, owner, and smallest safe next action; do not repeatedly probe an unmet external prerequisite.

## Parallel Worktree Delivery

Use parallel writers only through isolated worktrees at the same recorded baseline. Assign each writer a non-overlapping page group and exclusive resources; shared routes, global state, resource indexes, build configuration, device commands, and the main ledger remain owned by one integrator.

Each writer returns its changed-file list, source/evidence record, smallest gate result, and integration risk. The one integrator reviews and merges each result, runs batch/full builds and device evidence, and is the only writer of the final acceptance board. After integration and required evidence are complete, confirm every temporary worktree is merged or explicitly discarded, then remove it; never delete a worktree with unreviewed changes.

Return integration findings to the original writer for correction by default. The integrator changes code only when the defect belongs to shared integration files, or the original writer is unavailable and the fix is small with a clear boundary. Re-run the affected gate and integration verification after every correction.

## Exact UI Equivalence and Asset Provenance

Unless the user explicitly authorizes a scoped exception, every UI asset and visual decision must come from the migrated source snapshot. Do not generate, search for, purchase, substitute, reinterpret, or creatively improve UI material. Do not use “similar” system icons or platform defaults.

**Exact means element-by-element equality, not “close enough.”** All user-visible source elements—text, components, icons, graphics, images, animation assets, fonts, materials, navigation affordances, and visible states—must retain the same content, dimensions, position, shape, asset, typography, color, spacing, layering, opacity, geometry, corner treatment, and other visible characteristics in the HarmonyOS target.

Before each page group, inventory source asset paths, hashes where practical, dimensions, font files, visible states, and layout measurements. Build a source-to-target comparison record for every user-visible element and verify it on the final package under recorded comparison conditions. A native default, a hand-recreated element, an approximate layout, or any remaining size, position, text, component, icon, graphic, material, or visual-state mismatch is a failed UI comparison.

Do not mark the page group accepted or start its functional migration until every recorded visible element matches the source exactly. If an asset is absent, provenance/license is unclear, or a HarmonyOS constraint prevents exact rendering or interaction, mark the page group `BLOCKED` and ask the user. Only a written, element-specific user exception may permit a documented deviation; never invent a replacement or call a near match successful.

## First Actions

1. Freeze source and target identities: revision, branch, dirty state, build/package identity, supported devices, SDK/firmware, and available credentials. If the target is absent, complete and record the Phase 0 bootstrap before this gate. Never copy credentials into notes or output.
2. If the target is materially dirty, record its disposition and complete the dirty-target reconciliation gate before any migration edit.
3. Trace the upstream call chain for the requested page or capability; record behavior, states, errors, cancellation, cleanup, background behavior, and data ownership.
4. Build a source-to-target ledger from [the template](assets/templates/migration-ledger.md). Classify each row P0, P1, or P2 before editing.
5. Obtain current official HarmonyOS API, SDK, and protocol evidence for version-sensitive behavior. If it conflicts with source behavior, document the gap; do not imitate an API name.

## Dirty Target Reconciliation

A dirty target is an ownership and evidence issue, not an invitation to force it clean. Before migration edits, follow [the reconciliation workflow](references/migration-playbook.md#2-reconcile-a-dirty-target-worktree): preserve the active tree, inspect from a clean worktree at the exact target revision, and classify every path before deciding whether to recover, narrowly ignore, block, or leave it untouched.

Do not use reset, clean, stash, broad staging, or broad ignore as a substitute for reconciliation. Unknown paths and binary/media with unresolved provenance remain visible and `BLOCKED`.

## Gates

Do not implement or accept a capability until its source behavior, HarmonyOS implementation, and evidence agree. Label each side separately: `CODE`, `LOCAL`, `DEVICE_UI`, `DEVICE_REAL`, `PASS`, `FAIL`, `NOT TESTED`, or `BLOCKED`.

| Condition | Required decision |
| --- | --- |
| No HarmonyOS target exists | Bootstrap the smallest buildable target and record its package/module/toolchain identity. Do not migrate a source page or function as part of bootstrap. |
| A page group has missing provenance, incomplete element comparison, or any visible mismatch in text, components, icons, graphics, assets, size, position, style, or state | Mark the UI comparison `FAIL` or `BLOCKED`; do not accept the page group or start its functional migration. |
| Device data can be deleted, overwritten, sent, or charged | Require a protocol contract, confirmation boundary, idempotency/late-event plan, and destructive-flow test. Otherwise `BLOCKED`. |
| Android or iOS relies on background work, services, alarms, or lifecycle callbacks | Verify the HarmonyOS equivalent and limits. A platform constraint is not a bug to hide. |
| Tests or screenshots belong to another source snapshot or package | Do not transfer them. Rebuild, identify the package, and rerun relevant evidence. |
| Target tree is dirty or device ownership/state is unknown | Preserve active state and pause device input. Reconcile the target from a clean audit worktree at the exact revision; do not reset, clean, stash, broadly stage, broadly ignore, overwrite, send drafts, or alter user state. |
| A static candidate exists outside the final target integration | Record only source/resource or `CODE`/`LOCAL` evidence. It cannot satisfy final-package `DEVICE_UI`, functional, or real-device acceptance. |
| A hardware, service, provenance, or device blocker persists | Record the missing evidence, owner, and smallest safe exit action. Do not repeatedly probe it or convert it into a progress claim. |

Use [the playbook](references/migration-playbook.md) for phases, [evidence templates](references/evidence-templates.md) for records, and [failure modes](references/failure-modes.md) for destructive, asynchronous, or externally stateful paths.

## Example

For a wearable history page, first port and verify the list, loading, empty, permission-denied, and error states. Only then assess the history-sync category. Do not port a `read → delete` callback until HarmonyOS can prove persist-and-read-back before a batch-scoped delete confirmation. Without that contract, report `BLOCKED`.

## Red Flags

- “The API names look equivalent.”
- “The widget looks right, so the feature is done.”
- “The native font, default icon, or a few pixels of layout difference is close enough.”
- “The old test suite passed.”
- “HTTP 200 means the fact is true.”
- “Cancel only needs to hide the UI.”
- “We can fix the SDK limitation in the page.”

Each red flag returns to the ledger and the relevant gate. Do not turn an unverified claim into a success state.

