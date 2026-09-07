# Migration Playbook

## 0. Bootstrap a New Target Only When Needed

When no HarmonyOS project exists, create the smallest buildable target needed to establish package identity, module boundary, SDK baseline, and launch path. Record those choices and verify that the blank target builds and launches.

Phase 0 is infrastructure only: do not claim a source page or functional category has migrated, invent a design system, or use substitute UI assets. Begin Phase A only after the bootstrap identity is frozen.

## 1. Freeze the Boundary

Record source revision, target revision or bootstrap identity, dirty files, source license, build/package identity, device and OS version, SDK/firmware version, and requested scope. The source stays read-only. Use an isolated target branch or worktree when the target has user changes.

Do not begin implementation if the source revision, target state, or requested capability is ambiguous.

## 2. Phase A: Page UI Migration

Inventory source pages, routes, visual assets, navigation, typography, safe areas, loading, empty, permission, error, and disabled states. Record asset paths, hashes where practical, dimensions, source font files, and layout measurements. Group only related pages that can be accepted together.

For each page group:

1. Trace the source page and navigation call chain.
2. Verify that every image, icon, font, animation, color, geometry, and visible state comes from the source snapshot. Unless the user explicitly approves an exception, do not generate, search, substitute, or creatively redesign assets or visuals.
3. Map visible states to existing HarmonyOS layers and native layout behavior without changing the source design.
4. Render explicit unavailable state for functions not yet migrated.
5. Test navigation, return behavior, UI state, accessibility, supported layouts, source-asset provenance, and exact visual evidence on the final package.
6. Record `DEVICE_UI` evidence before allowing that group's functional migration.

If source assets are missing, access/license is unclear, or platform behavior prevents exact rendering, stop the page group as `BLOCKED` and ask the user. UI acceptance proves only the page group. It does not prove real data, permissions, devices, network, lifecycle, or backend behavior.

## 3. Phase B: Functional Category Migration

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

## 4. Vertical Slice and Handoff

For one category row or cohesive row group: write normal, boundary, and failure tests first; make the smallest target-layer change; verify stale events, cancellation, timeout, retry, release, and concurrency where relevant; then bind results to source revision and final package identity.

At the end of every slice, report changed files, evidence, `NOT TESTED`/`BLOCKED` items, risk, target Git state, and the next smallest slice.
