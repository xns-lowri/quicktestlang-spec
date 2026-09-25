# quicktestlang-spec
Specification documents for Quick Test Language.

## Goals
QTL is a concise domain-specific language for describing automated production test sequences.

### Design priorities:
- Test sequence laid out and readable in order of execution
- Minimal boilerplate
- Safe test failure and error handling behaviour
- Explicit, deterministic timing
- Easy static analysis and validation
- Bounded control flow (only within test steps, and selectively skipping test steps after failures)
- Test limits 

### Primary features:
- Metadata block specifying tester and DUT parameters (identifiers, resource requirements, signal and power config/limits, expected test record outputs/format)
- Grouping of individual instructions into logical 'test steps'
  - Failing a test step may allow some or all subsequent test steps to be skipped.
  - Instructions within a step will be completed in full after recording a failure.
- Instruction for performing or otherwise recording a test measurement value.
- Instruction (or modifier) for recording a test failure with a message and value.

## Language Specification

### Program Package
- Test definition file
  - Compiled test sequence
- DUT Config and Test Limit values
- Assets (e.g. waveforms)

### Lexical and Syntax Rules
#### Source Files
- Source files are UTF-8 encoded
- Keywords are case-sensitive 
- Identifiers must match ^[a-zA-Z_][a-zA-Z0-9_]* and are case-sensitive
- Whitespace (including newlines) separates tokens but is otherwise insignificant
- Statements are terminated by a semicolon ;
- Blocks are delimited by braces { }

### Program Structure
meta { ... } //header data structure
group "name" { ... }; //groups related test steps together into each distinct part of the test sequence (e.g. power-on test, comms test, etc)
step "name" { ... }; //main test code structure, contains all operations for performing one logical step of the test sequence (e.g. voltage regulator output, quiescent current draw, etc)

### Operations

edge(input, direction); //detect an edge on digital input

expect condition [after t0] [within t1];

(let) variable = value; //create temporary variable within the current scope - as of yet still undecided on weak or strong types

wait time; //pause for time
wait condition [within time]; //pause execution until condition is satisfied, optionally with timeout
wait for { condition1; [condition2;] [...] }; //pause execution until any condition is satisfied


## Keywords

after
edge
expect
fail
for
in
(let)
test
set
step
wait
within
