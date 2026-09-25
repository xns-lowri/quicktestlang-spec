# quicktestlang-spec
Specification documents for Quick Test Language.

## Goals
QTL is a concise domain-specific language for describing automated production test sequences.

Design priorities:
- Test sequence laid out and readable in order of execution
- Minimal boilerplate
- Safe test failure and error handling behaviour
- Explicit, deterministic timing
- Easy static analysis and validation
- Bounded control flow (only within test steps, and selectively skipping test steps after failures)
- Test limits 

Primary features:
- Metadata block specifying tester and DUT parameters (identifiers, resource requirements, signal and power config/limits, expected test record outputs/format)
- Grouping of individual instructions into logical 'test steps'
  - Failing a test step may allow some or all subsequent test steps to be skipped.
  - Instructions within a step will be completed in full after recording a failure.
- Instruction for performing or otherwise recording a test measurement value.
- Instruction (or modifier) for recording a test failure with a message and value.
