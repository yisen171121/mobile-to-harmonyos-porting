# Evidence Templates

## Migration Ledger

Copy [the ledger template](../assets/templates/migration-ledger.md) into the target repository. Do not put secrets, personal data, raw production responses, or private source code in it.

## State and Failure Record

| Field | Record |
| --- | --- |
| Capability and scope | One page group or one functional category and its boundaries. |
| UI provenance | Source asset paths, hashes where practical, dimensions, fonts, layout measurements, and explicit user-approved exceptions. |
| Source evidence | Revision, file/function path, call-chain summary, official source/SDK/protocol reference. |
| Target mapping | Target files/layers, platform API, supported OS/device/SDK conditions. |
| States | Initial, active, success, failure, cancel, timeout, disconnect, recovery, and release states. |
| Data contract | Owner, sensitivity, write/read-back confirmation, delete/export behavior, and idempotency key or batch boundary. |
| Tests | Preconditions, action, expected state, actual state, evidence level, package identity, and result. |
| Decision | `PASS`, `FAIL`, `NOT TESTED`, or `BLOCKED`; exact missing precondition and next smallest action. |

## Acceptance Matrix

| Evidence level | It can establish | It cannot establish |
| --- | --- | --- |
| `CODE` | A reachable implementation and call chain exist. | Runtime behavior. |
| `LOCAL` | A deterministic isolated test or injected failure behaves as recorded. | Platform, real device, backend, firmware, or release behavior. |
| `DEVICE_UI` | The identified package displays and responds on the recorded device. | Real sensor/SDK/backend behavior, background durability, or every device size. |
| `DEVICE_REAL` | The recorded hardware/service behavior occurred under stated conditions. | Different firmware, accounts, networks, devices, or long-duration behavior. |

Never combine rows from different source revisions, packages, devices, or firmware versions into one `PASS` claim.
