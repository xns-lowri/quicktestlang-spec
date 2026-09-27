# Language Model

## Test Program Package
A QTL test program contains the following source files:
- Test sequence source code file
- Config and limit values file
- Optional: Test assets (e.g. waveforms)

The source code is compiled into executable VM bytecode and packaged with the config/limits and assets files (package tbd) before being made available to test units.
- TODO: consider options for signing/verifying versions, possibly out of scope for the language?

## Program Structure
The test sequence program is comprised of `reqs`, `setup`, `step`, and `finally` blocks:
| Block ID | Description | Ordering | Amount required |
|---|---|---|---|
| `reqs` | Metadata block defining required test modules, resource (e.g. pin or port) mappings and aliases (including special functions: power & internal resources), config and limits mapping, and test output (results) data mapping. | First | One, required |
| `setup` | Instruction sequence to perform at the beginning of each test cycle | Before `step` blocks | One, optional |
| `step` | Instruction sequence to perform for each logical 'step' of a test cycle | Order of execution | One or more required |
| `finally` | Instruction sequence to perform at the end of each test cycle (e.g. safe power down sequence). This block is executed for all test cycles, after the last `step` has been performed, irrespective of test result or `step` blocks skipped. |

TODOs:
- sections: metadata, init, test
- mapping in values from limit file (+ identifiers)

TODOs - metadata:
- aliasing resources (e.g. input pin given name that identifies net on DUT)
- setting up resources & resource pin mapping/direction
- dut/fixture id
