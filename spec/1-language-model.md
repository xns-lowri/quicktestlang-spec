# Language Model

## Test Program Package
A QTL test program contains the following source files:
- Test sequence source code file
- Config and limit values file
- Optional: Test assets (e.g. waveforms)

The source code is compiled into executable VM bytecode and packaged with the config/limits and assets files (package tbd) before being made available to test units.
- TODO: consider options for signing/verifying versions, possibly out of scope for the language?

## Program Structure
At the top level, a test sequence program is comprised of `reqs`, `setup`, `step`, and `finally` blocks:
| Block ID | Description | Ordering | Amount required |
|---|---|---|---|
| `reqs` | Metadata block defining required test modules, resource (e.g. pin or port) mappings and aliases (including special functions: power & internal resources), config and limits mapping, and test output (results) data mapping. | First | One |
| `setup` | Instruction sequence to perform at the beginning of each test cycle | Before `step` blocks | One, optional |
| `step` | Instruction sequence to perform for each logical 'step' of a test cycle | Order of execution | One or more required |
| `finally` | Instruction sequence to perform at the end of each test cycle (e.g. safe power down sequence). This block is executed for all test cycles, after the last `step` has been performed, irrespective of test result or `step` blocks skipped. | After `step` blocks | One, optional |

### `reqs` block
The `reqs` block functions as the definition for all resources required (and made available) by the test sequence program. This block is presented similarly to a JSON object, with key-value pairs used to specify values for the fields provided. This block must only contain assignments to the provided fields, and may not contain executable instructions.

#### `reqs` fields:
- modules []
  - config (module-wide setup parameters)
  - pinmap (pin usages, configuration, aliases)
- params []
  - alias
  - type
- results []
  - alias
  - type
- fixture_id


### `setup` block
The `setup` block is the first instruction block executed in a given context. The two contexts allowing a `setup` block are the top-level program (before all `step` blocks) and as the first statement inside a `step` block. A `setup` block may not contain `test` operators.

When implemented at the top level, the `setup` block runs once before any subsequent `step` blocks.

When implemented in a `step` block, the block runs once before subsequent statements in the enclosing block.

### `step` block
The `step` block contains all instructions required to perform one logical step of a test sequence. It is up to the engineer to decide what may or may not constitute a 'test step', but the design of this language is centred on using the distinction to group a set of measurements and tests by function for the purposes of reporting results, and provide means for common 'test sequence' flow control (e.g. skip all subsequent steps if the DUT doesn't take power) without exposing full control of the test state machine to the test sequence program.

### `finally` block
The `finally` block is the last instruction block executed in a given context. The two contexts allowing a `finally` block are the top-level program (after all `step` blocks) and as the last statement inside a `step` block. A `finally` block may not contain `test` operators.

When implemented at the top level, the `finally` block always runs once after all `step` blocks have executed, regardless of any blocks skipped or the outcome of the test.

When implemented in a `step` block, the block runs once after all preceding statements in the block have been executed, or after a `break` statement is encountered within the block (before flow continues to the next available `step` block, or the test complete sequence).
