# Failure Modes and Stop Conditions

| Risk | Stop condition | Safe next action |
| --- | --- | --- |
| Page before function | A page needs a function that has not been verified. | Show explicit unavailable/error/loading state; complete page UI acceptance before the function category. |
| UI asset or visual drift | An asset is generated, searched, substituted, restyled, or not traceable to the source snapshot. | Stop the page group; inventory source provenance and obtain explicit user authorization before any exception. |
| Read/delete device history | Delete can occur before durable, verified application persistence. | Obtain a supported persist-then-confirm contract and test normal, timeout, disconnect, duplicate, and late-confirm paths. |
| Data semantics | Units, timestamps, time zones, day boundaries, aggregation, or source freshness are unclear. | Preserve raw provenance, map one metric at a time, and reject invented values or dates. |
| Authorization | Natural-language confirmation is ambiguous, negated, quoted, stale, or targets a broader scope than requested. | Require structured action, owner, scope, confirmation, and request generation; default to no action. |
| Cancellation | A late callback can update UI, send data, speak, delete, or clear state after cancellation. | Tie work and callbacks to a generation/session; only the current generation may settle a terminal state. |
| Release | A platform cleanup failure is overwritten by a generic success or released state. | Preserve the error terminal state and verify listener, timer, handle, and player ownership. |
| Background behavior | The upstream uses a platform capability with no documented HarmonyOS equivalent. | Describe the supported substitute and limitation; never promise parity without evidence. |
| Retry | A request may have reached a service or device but its result is unknown. | Use a supported idempotency/receipt contract or stop automatic retry. |
| Evidence drift | Source changed after build, package identity is unknown, or old evidence is reused. | Freeze revisions, verify package identity, rebuild, and rerun the relevant test. |
| Shared workspace/device | User state, dirty edits, or device ownership is unknown. | Preserve state, isolate target changes, request ownership, and pause interaction. |
| Secrets and private material | Notes, diffs, logs, or examples include credentials or identifying production data. | Redact and remove the material; use fictional inputs and describe the data type only. |

## Common Rationalizations

| Rationalization | Required response |
| --- | --- |
| "The APIs have the same name." | Trace behavior and verify the platform contract. |
| "The widget looks right, so the feature is done." | Complete the functional category separately and record its evidence level. |
| "The test suite is green." | Bind the claim to the tested revision and package; run missing evidence. |
| "We can patch the limitation in UI." | Keep the limitation visible and resolve it at the owning protocol/platform boundary. |
| "The user needs it today." | Narrow the slice; do not bypass a P0 gate. |
