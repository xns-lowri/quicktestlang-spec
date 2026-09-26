# Lexical Structure


## Literals

### Boolean Literals
Boolean values are widely supported, with first-class access to bitfields.

Boolean literals are `true` and `false`.

### Number Literals
Integers and decimals supported, decimal precision and rounding to be rationalised at compile time based on target hardware.

Integer literals must match `^[0-9+-][0-9]*`

Decimal literals must match `^[0-9+-][0-9]*\.[0-9][0-9]*`

- Positive numbers may start with `+` or 0..9, negative numbers must start with `-`
  - A unary operator followed by a positive number will be coerced to a negative literal (e.g. `x = -3.45` and `x = - 3.45`)
- Any number of digits allowed before or after an optional decimal point
- Inclusion of decimal point denotes a decimal value (and must be followed by at least one digit)
- Future support anticipates 0x and 0b prefixes for hex and binary literals respectively, if needed

### String Literals
Single character values are enclosed with `''`, multiple character strings are enclosed with `""`.

The following escape sequences are recognised:

    \"    quotation mark
    \\    backslash
    \n    newline
    \t    tab

TODO allowing unicode strings for ux, ascii support for e.g. comms testing

### Unit literals
TODO special literals for units e.g A, V, mA, mV etc

## Operators
TODO all the favourites from == to +

## Top Level Program Structure
`meta { ... }` header data structure

`group "name" { ... };` groups related test steps together into each distinct part of the test sequence (e.g. power-on test, comms test, etc)

`step "name" { ... };` main test code structure, contains all operations for performing one logical step of the test sequence (e.g. voltage regulator output, quiescent current draw, etc)

## Statement Grammar
### Grammar notation
    "word"      literal keyword/token
    name        another grammar rule
    [ item ]    optional
    { item }    zero or more repetitions
    item | item alternative

### Syntax Rules
TODO

## Expressions
`edge(input, direction);` detect an edge on digital input

`expect condition [after t0] [within t1];`

`(let) variable = value;` create temporary variable within the current scope - as of yet still undecided on weak or strong types

`wait time;` pause for time
`wait condition [within time];` pause execution until condition is satisfied, optionally with timeout
`wait for { condition1; [condition2;] [...] };` pause execution until any condition is satisfied


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

## Data Types
?
