# Grammar
## Grammar notation
    "word"      literal keyword/token
    name        another grammar rule
    [ item ]    optional
    { item }    zero or more repetitions
    item | item alternative

## Syntax Rules
TODO

## Expressions
`edge(input, direction);` detect an edge on digital input

`expect condition [after t0] [within t1];`

`(let) variable = value;` create temporary variable within the current scope - as of yet still undecided on weak or strong types

`wait time;` pause for time
`wait condition [within time];` pause execution until condition is satisfied, optionally with timeout
`wait for { condition1; [condition2;] [...] };` pause execution until any condition is satisfied
