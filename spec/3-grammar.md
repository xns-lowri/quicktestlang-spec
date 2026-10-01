# Grammar

## Top Level Declarations
### Requirements Data
A typical requirements data block is shown below:

    reqs {
        alias: "test name",
        modules: [
            {
                type: "module_type",
                slot: 0,
                config: {
                    input_low: 0.7V,
                    input_high: 2.3V
                },
                pinmap: [
                    {
                        id: "pin0",
                        alias: "ENABLE",
                        dir: "output",
                        default: "low",
                    }
                ]
            }
        ],
        params: [
            {
                alias: "param1",
                type: number,
                unit: V
            }
        ],
        results: [
            {
                alias: "measurement1",
                type: number,
                unit: mV
            }
        ],
        fixture_id: "identifier string"
    }
TODO better explanation??

### Step Declarations

`group "name" { ... };` groups related test steps together into each distinct part of the test sequence (e.g. power-on test, comms test, etc)

`step "name" { ... };` main test code structure, contains all operations for performing one logical step of the test sequence (e.g. voltage regulator output, quiescent current draw, etc)
    
## Statements
TODO


### Expressions
`edge(input, direction);` detect an edge on digital input
alt: hdl-inspired - `posedge input`

`expect condition [after t0] [within t1];`

`(let) variable = value;` create temporary variable within the current scope - as of yet still undecided on weak or strong types

`wait time;` pause for time

`wait condition [within time];` pause execution until condition is satisfied, optionally with timeout

`wait for { condition1; [condition2;] [...] };` pause execution until any condition is satisfied

### Function Invocation

### Conditional Syntax

### Operator Precedence


## EBNF Notation
    "word"          literal keyword/token
    name            another grammar rule
    [ item ]        optional
    { item }        zero or more repetitions
    item | item     alternative
