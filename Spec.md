# QTL Specification

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

## Language Constructs

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
