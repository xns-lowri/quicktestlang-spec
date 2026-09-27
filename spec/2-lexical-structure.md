# Lexical Structure

## Source Files
- Source files are UTF-8 encoded
- Keywords are case-sensitive 
- Identifiers must match `^[a-zA-Z_][a-zA-Z0-9_]*` and are case-sensitive
- Whitespace separates tokens but is otherwise insignificant
- Statements are terminated by a semicolon `;`
- Blocks are enclosed by braces `{ }`
- Function arguments are enclosed by parentheses `()` and separated by commas `,`
- Comments begin with `//` and end at a newline

## Literals

### Boolean Literals
Boolean literals are `true` and `false`.

Tristate literals are `high`, `low`, and `hiz`.

### Numeric Literals
Integers and decimals supported, decimal precision and rounding to be rationalised at compile time based on target hardware.

Integer literals must match `^[-+]?[0-9][0-9]*`

Decimal literals must match `^[-+]?[0-9][0-9]*\.[0-9][0-9]*`

- Positive numbers may start with `+` or 0..9, negative numbers must start with `-`
  - A unary operator followed by a positive number will (not? - todo) be coerced to a negative literal (e.g. `x = -3.45` and `x = - 3.45`)
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

## Data Types
The following data types are provided:

### Discrete types
    bool                    true/false
    3state                  high/low/hiz
### Numeric types
    u8  u16  u32  u64       unsigned integers
    i8  i16  i32  i64       signed integers
    f32  f64                floating point
### Text types
    char                    single character
    string                  character string

## Operators
    + - * / %          arithmetic operators
    == != < <= > >=    comparison operators
    && || !            logical operators
    & | ^ ~ << >>      bitwise operators

### Type Conversion and Promotion
Types will always be promoted or implicitly converted where conversion is guaranteed not to be lossy:
TODO table of conversions

Types will never be converted implicitly where conversion may be lossy, a compiler error will be generated. Use `as` to type cast instead.

Signed and unsigned values may(?) be mixed, but arithmetic overflow or underflow (or sign change for unsigned values) will generate runtime faults (is this a bad idea??).

### Bitwise operators
Bitwise shift operators `<<` and `>>` perform arithmetic shifts 

TODO
- float conversion
- operator precedence

## Keywords

    after
    as
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

TODO revise/complete according to later spec
