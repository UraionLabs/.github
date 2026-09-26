# Four Fabric workflow proof notes

By Uraion Labs · 2026-09-26

**Internal engineering demonstrations, not customer outcomes.** These observations
show specific checks and decisions, not general reliability, saved labor, paid
demand or a signed beta. Operator actions were driven by our coding assistant,
including browser automation. Biological-human/founder time was not measured.
Local energy, hardware and labor cost is **unknown**, not $0. No customer material
is used.

[Watch the 97.8-second captioned workflow](https://www.uraionlabs.com/products?source=organic#demo)
· [Current product scope and limitations](https://www.uraionlabs.com/products?source=organic)

Fabric's source and engineering issues are currently private. Internal ticket,
commit and receipt identifiers below identify our records; they are **not public
or independently audited evidence**. Fabric-specific reproduction commands need
authorized source access and a configured environment. The three-file invoice
fixture can be reproduced independently with Node, without Fabric. Source-build
onboarding is subject to fit; there is no public installer or source release.

- [1. A checked maintenance change](#1-a-checked-maintenance-change)
- [2. A failed run stopped by verification](#2-a-failed-run-stopped-by-verification)
- [3. Recovery after failed checks](#3-recovery-after-failed-checks)
- [4. Three model attempts, including noncompletions](#4-three-model-attempts-including-noncompletions)

## 1. A checked maintenance change

**Starting problem.** A synthetic invoice function adds unit price and quantity
instead of multiplying them. In a new empty directory, create:

`package.json`:
```json
{"name":"invoice-maintenance-demo","private":true,"type":"module","scripts":{"build":"node --check invoice.js","lint":"node --check invoice.test.js","test":"node --test"}}
```

`invoice.js`:
```js
export function lineTotalCents(unitCents, quantity) {
  return unitCents + quantity;
}
```

`invoice.test.js`:
```js
import test from 'node:test';
import assert from 'node:assert/strict';
import { lineTotalCents } from './invoice.js';

test('three units multiply the unit price', () => {
  assert.equal(lineTotalCents(1200, 3), 3600);
});
test('zero units cost zero', () => {
  assert.equal(lineTotalCents(1200, 0), 0);
});
```

With a Node version supporting `node:test`, run `npm test`; both assertions fail
(`1203 != 3600`, `1200 != 0`). No package installation is required. Change only
the function's `+` to `*`, then run:

```sh
npm run --if-present build && npm run --if-present lint && npm test
```

Both assertions now pass. These commands reproduce the fixture's checks, **not**
an agent delivery. In the recorded Fabric workflow the local model made that
same one-line change inside an isolated Agent Workspace. Review displayed:

```diff
-  return unitCents + quantity;
+  return unitCents * quantity;
```

The primary Project was unchanged before explicit Apply and passed the same
checks afterward. Build and lint here are syntax checks, not bundling or a style
linter. Recorded receipt `verification_c829990b94084eb9` passed build/lint/test
in 123/110/161 ms. Queue `queue_34a2b338577b4346` was incorporated after review.

**Setup and interventions.** Fabric `866f6fe`, macOS Apple Silicon, Node 26.10.0,
npm 11.19.1, Ollama 0.34.4 and `qwen3.8:27b-nvfp4` (not Forge). The assistant
prepared the fixture and execution Grant, supplied the exact fix and `write_file`
tool in the prompt, inspected the diff/checks, and drove operator-only Apply.
One successful rehearsal preceded the published take. Two other recording takes
stopped on automation assertions about view hydration and queue timing; they
are not model failures or extra successful deliveries. The published take is
97.833 seconds, unsped and unspliced; native captions leave its bytes unchanged.

**Cost and limitation.** Total preparation/retry/operator time and local cost
were not measured. Video duration is not end-to-end task time. This is not
independent bug discovery, a complete invoicing implementation, a customer
acceptance result or native/clean-machine onboarding. Model reruns may differ.
Internal record: #196.

## 2. A failed run stopped by verification

**Starting problem.** An earlier real local-model run of the invoice fixture
encountered a Fabric compatibility defect: home-installed npm could not read its
own package metadata inside the macOS execution sandbox.

**Observed result.** At `b91349b`, receipt `verification_78524b6a4e6c4bb7` recorded
`ERR_INVALID_PACKAGE_CONFIG`, OS `Operation not permitted`, exit 1, in 55 ms.
The application tests never ran. No candidate from that failed verification was
incorporated. This is **not** a claim that tests caught bad invoice logic.

**Resulting fix and check.** Internal commit `70be3f5` grants read access to the
canonical npm package directory, not HOME, the installation prefix, network or
writes. A fresh local-model run then passed the default npm build/lint/test
commands in 150/115/148 ms; explicit review/incorporation and both primary
assertions followed. Source-access operators on macOS can run:

```sh
cargo test -p fabric-agent npm_package_reads_do_not_expose_the_installation_or_home -- --nocapture
```

This deterministic regression exercises real OS reads, unrelated HOME/install
canaries, symlink escapes and write denial. It failed before the repair and
passed after it. It is separate from the recorded local-model workflow; other
operating systems do not exercise this macOS-only test.

**Interventions, cost, limitation.** The coding assistant diagnosed and authored
the product fix, then reran the workflow; uraion did not author that repair.
Diagnosis/retry labor and local inference cost are unknown. The full gate passed
in 790.54 seconds; that is verification wall time, not human effort. A stopped
check is not a delivered customer result. Internal record: #258.

## 3. Recovery after failed checks

**Starting problem.** A real local-model candidate was intentionally checked
with `node --test missing.test.js`. Failure then exposed a persistence defect:
the latest task graph had not been saved on the check-failure path. Reload must
retain failure without enabling Apply.

**Resulting fix and check.** Internal commit `866f6fe` saves the current canonical
Task Graph Snapshot before the failure frame. It does not complete the task or
bypass verification. Source-access operators can run:

```sh
cargo test -p fabric-runtime coding_check_failure_preserves_graph_for_restart_and_verified_recovery -- --nocapture
```

The regression restarts the facade from the Event Log, recovers the in-progress
graph and failed receipt, refuses queue submission and preserves the primary.
A corrected candidate must pass verification before review/incorporation.

**Observed UI run.** Failed receipt `verification_920e2a272516482d` took 57 ms.
UI reload retained failure and Verify again. After the assistant corrected the
required command to npm build/lint/test, receipt `verification_c15aae8dd74d4c2e`
passed in 385 ms with two passing assertions. Reload retained Passed and Review.
The one-line invoice diff was inspected and explicitly applied as
`queue_15f8fb7af6134174`; primary checks passed afterward.

**Interventions and retries.** The model encountered three hash-edit rejections,
unavailable AST tooling and read-only command approval before using `write_file`.
The assistant intentionally misconfigured/corrected the check, authored the
Runtime fix, and drove review/apply. These attempts are not extra accepted tasks.

**Cost and limitation.** Total attempt/operator labor and local cost are unknown.
The full gate passed in 773.46 seconds. The regression covers Runtime/facade
restart; the browser observation covers UI reload. Neither proves native
clean-machine onboarding, retroactive repair of old events, or customer renewal.
Internal record: #259.

## 4. Three model attempts, including noncompletions

**Starting problem.** A real repository ticket found that CLI help omitted the
Runtime binary from its source-build command. uraion worked in a non-Git
snapshot of the actual repository, not a customer Project.

| Sequential local-model turn | Exec wall time | Model attempts | Tool calls | Result |
| --- | ---: | ---: | ---: | --- |
| `lfm2.5:latest` | 15.91 s | 2 | 1 | No bytes changed; tool-shaped prose with empty fields |
| `gemma4:e2b` | 32.14 s | 4 | 3 | No bytes changed despite a claimed README fix |
| `qwen3.8:27b-nvfp4` | 44.88 s | 4 | 3 | Correct one-line CLI help edit |
| **All turns** | **92.93 s** | **10** | **7** | **One candidate, not three completions** |

**Resulting diff and checks.** Internal commit `3ae0493` changes the displayed
`cargo build -p fabric-cli --bins` command to:

```sh
cargo build -p fabric-cli -p fabric-runtime --bins
```

That command actually built both binaries. A sibling-binary installation opened
a plain-folder Project against a fresh Runtime without a Runtime-path override.
Receipt `verification_f5255801ddfb412c` passed and queue
`queue_161212a91a904625` was reviewed/incorporated. Source-access operators can
build with the command above and inspect `target/debug/uraion --help`. The full
gate passed in 784.73 seconds.

**Interventions and human effort.** Three assistant-issued prompts and model
switches were needed. The assistant prepared the snapshot, issued a Project-
durable Grant after session-grant friction, inspected changed bytes, checked
acceptance, reviewed/incorporated and mechanically transferred the approved diff
to main. Biological-human/founder minutes were not measured. Setup, review,
transfer, verification and the assistant's own runtime are **excluded** from the
92.93-second figure. Qualitative interventions are not measured labor savings.

**Cost and limitation.** Receipt input/output tokens by turn were 13,907/310,
29,215/2,321 and 29,222/527; local energy/hardware/labor cost is unknown. The first
two noncompletions were detected by changed-byte inspection, not formatting.
This sequential ledger is **not a controlled model ranking or customer-incumbent
comparison**. On another real ticket (#257), two Qwen turns failed after
747.07 seconds, 32 model attempts and 49 tool calls. The direct assistant rescued
that fix; it is excluded from uraion completions. Internal records: #206/#156.

A controlled comparison including all retries and measured total human effort
remains outstanding. So do actual buyer acceptance, independent repeat use,
payment and eligible software renewal. Paid assistance is not software renewal.
These four notes and one captioned recording do not complete a 90-day acquisition
experiment. GitHub links here use the organic cohort; relevant Hugging Face model
cards use a separate `source=huggingface` link. Publication is not a conversion.
