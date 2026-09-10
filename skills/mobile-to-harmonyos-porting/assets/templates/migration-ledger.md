# Mobile to HarmonyOS Migration Ledger

## Boundary

| Field | Value |
| --- | --- |
| Source snapshot | |
| Target mode | Existing target / Phase 0 bootstrap |
| Target snapshot or bootstrap identity | |
| Source license / access boundary | |
| Target branch or worktree | |
| Target dirty-state disposition | |
| HarmonyOS API / device / SDK / firmware | |
| Requested page and function scope | |
| Exact UI equivalence standard | Every visible source element must match its source content, size, position, shape, style, asset, and visible state; only written, element-specific user exceptions may deviate. |

## Workspace Reconciliation

| Category | Path boundary / count / size | Decision | Evidence / exit condition |
| --- | --- | --- | --- |
| Frozen user edit | | Preserve, do not mix into migration work | |
| Recoverable source / document / input | | Explicit-path recovery commit | |
| Verified generated evidence / cache | | Narrow ignore; retain on disk | |
| Binary / media pending provenance or LFS | | `BLOCKED`, keep visible | |
| Unknown | | No stage, ignore, deletion, or migration | |

## Phase A: Page UI Matrix

| Page group | Priority | Source behavior and routes | Source UI inventory and exact comparison | HarmonyOS UI mapping | Required states | Required `DEVICE_UI` proof | Status | Next action |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | P0/P1/P2 | | text/components/icons/graphics/assets; content, size, position, shape, style, state | | loading/empty/error/permission/unavailable | final-package, element-by-element exact-match evidence | NOT TESTED/BLOCKED/PASS/FAIL | |

## Phase B: Functional Category Matrix

| ID | Priority | Category and source call chain | HarmonyOS mapping | Contract / state risks | Required proof | Status | Next action |
| --- | --- | --- | --- | --- | --- | --- | --- |
| | P0/P1/P2 | | | | CODE/LOCAL/DEVICE_REAL | NOT TESTED/BLOCKED/PASS/FAIL | |

## Slice Evidence

| Slice | Preconditions | Action | Expected user/internal/resource state | Actual result | Revision and package identity | Evidence level | Decision |
| --- | --- | --- | --- | --- | --- | --- |
| | | | | | | | |

## Open Risks

| Risk | Why it remains open | Blocker or missing evidence | Owner / next smallest action |
| --- | --- | --- | --- |
| | | | |

## Progress Snapshot

| Measure | Basis / denominator | Status | Next action |
| --- | --- | --- | --- |
| Workspace hygiene / recoverability | | | |
| Source, code, and local evidence | | | |
| End-to-end page / functional / device acceptance | | | |

