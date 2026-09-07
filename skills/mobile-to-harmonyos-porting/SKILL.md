---
name: mobile-to-harmonyos-porting
description: Use when incrementally porting or updating an Android, iOS, Flutter, React Native, or shared-native mobile app in an existing HarmonyOS app, especially where SDKs, hardware, background behavior, data deletion, or release evidence make a rewrite unsafe.
---

# Mobile to HarmonyOS Porting

Treat a port as behavior preservation with explicit platform differences, never as source-file conversion. Keep upstream source read-only, preserve target-user changes, and stop instead of guessing at destructive or unsupported behavior.

## Non-Negotiable Migration Order

1. **UI first:** migrate and accept user-visible pages in small page groups before migrating their new functional behavior. For each group, confirm information hierarchy, navigation, unavailable/error/loading states, accessibility, supported layouts, and final-package UI evidence.
2. **Functions second:** after the relevant page group is accepted, migrate one functional category at a time: data/storage, permissions, networking, device/BLE, background/lifecycle, or AI/tool behavior. A UI pass is not functional evidence.
3. Do not merge unrelated page polish and functional categories into one slice. If a source feature requires its function to render safely, use explicit unavailable state until the function slice is verified.

## UI Fidelity and Asset Provenance

Unless the user explicitly authorizes an exception, every UI asset and visual decision must come from the migrated source snapshot: images, icons, fonts, illustrations, animation assets, color, spacing, typography, geometry, navigation structure, and visible state. Do not generate, search for, purchase, substitute, reinterpret, or creatively improve UI material. Do not use “similar” system icons or platform defaults.

Before each page group, inventory source asset paths, hashes where practical, dimensions, font files, visible states, and layout measurements. Reuse or faithfully translate the source material only after confirming its license/access boundary. Do not copy those assets into this public Skill repository.

The target UI must match the source UI exactly within the recorded platform-rendering evidence. If an asset is absent, provenance/license is unclear, or a HarmonyOS platform constraint prevents an equivalent rendering or interaction, mark the page group `BLOCKED` and ask the user. Never fill the gap with an original asset or design decision.

## First Actions

1. Freeze source and target identities: revision, branch, dirty state, build/package identity, supported devices, SDK/firmware, and available credentials. Never copy credentials into notes or output.
2. Trace the upstream call chain for the requested page or capability; record behavior, states, errors, cancellation, cleanup, background behavior, and data ownership.
3. Build a source-to-target ledger from [the template](assets/templates/migration-ledger.md). Classify each row P0, P1, or P2 before editing.
4. Obtain current official HarmonyOS API, SDK, and protocol evidence for version-sensitive behavior. If it conflicts with source behavior, document the gap; do not imitate an API name.

## Gates

Do not implement or accept a capability until its source behavior, HarmonyOS implementation, and evidence agree. Label each side separately: `CODE`, `LOCAL`, `DEVICE_UI`, `DEVICE_REAL`, `PASS`, `FAIL`, `NOT TESTED`, or `BLOCKED`.

| Condition | Required decision |
| --- | --- |
| A page group lacks source-asset provenance or exact UI evidence on the final package | Do not start its new functional migration; keep unavailable behavior explicit. |
| Device data can be deleted, overwritten, sent, or charged | Require a protocol contract, confirmation boundary, idempotency/late-event plan, and destructive-flow test. Otherwise `BLOCKED`. |
| Android or iOS relies on background work, services, alarms, or lifecycle callbacks | Verify the HarmonyOS equivalent and limits. A platform constraint is not a bug to hide. |
| Tests or screenshots belong to another source snapshot or package | Do not transfer them. Rebuild, identify the package, and rerun relevant evidence. |
| Target tree is dirty or device ownership/state is unknown | Isolate work, preserve changes, and pause device input. Do not reset, overwrite, send drafts, or alter user state. |

Use [the playbook](references/migration-playbook.md) for phases, [evidence templates](references/evidence-templates.md) for records, and [failure modes](references/failure-modes.md) for destructive, asynchronous, or externally stateful paths.

## Example

For a wearable history page, first port and verify the list, loading, empty, permission-denied, and error states. Only then assess the history-sync category. Do not port a `read → delete` callback until HarmonyOS can prove persist-and-read-back before a batch-scoped delete confirmation. Without that contract, report `BLOCKED`.

## Red Flags

- “The API names look equivalent.”
- “The widget looks right, so the feature is done.”
- “The old test suite passed.”
- “HTTP 200 means the fact is true.”
- “Cancel only needs to hide the UI.”
- “We can fix the SDK limitation in the page.”

Each red flag returns to the ledger and the relevant gate. Do not turn an unverified claim into a success state.
