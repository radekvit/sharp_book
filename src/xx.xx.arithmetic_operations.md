# Arithmetic operations

Sharp has the following arithmetic operators:

| **Operator**   | **Syntax** | **Overload Definition** (inside or outside of class) |
| unary plus     | `+x`       | `fn operator +(x: & T)` |
| unary minus    | `-x`       | `fn operator -(x: & T)` |
| addition       | `x + y`    | `fn operator +(x: & T, y: & T2)` |
| subtraction    | `x - y`    | `fn operator -(x: & T, y: & T2)` |
| multiplication | `x * y`    | `fn operator *(x: & T, y: & T2)` |
| power          | `x ** y`   | `fn operator **(x: & T, y: & T2)` |
| division       | `x / y`    | `fn operator /(x: & T, y: & T2)` |
| modulo         | `x % y`    | `fn operator %(x: & T, y: & T2)` |
| bitwise NOT    | `~x`       | `fn operator ~(x: & T)` |
| bitwise AND    | `x & y`    | `fn operator &(x: & T, y: & T2)` |
| bitwise OR     | `x | y`    | `fn operator |(x: & T, y: & T2)` |
| bitwise XOR    | `x ^ y`    | `fn operator ^(x: & T, y: & T2)` |
| bitwise shift left | `x << y`    | `fn operator <<(x: & T, y: & T2)` |
| bitwise shift right | `x >> y`    | `fn operator >>(x: & T, y: & T2)` |

In-class definitions are `friend` automatically.
Operator overloads may return any type and may take `mut &` as arguments instead of `&`.

## Built-in arithmetic rules
All arithmetic operations compute the result and do not modify the arguments.

## Arithmetic conversions
The conversion rules for built-in arithmetic are:

* If both operands are of the same type, no conversion is performed.
* If either operand is `f64`, the other operand is converted to `f64`.
* If either operand is `f32`, the other operand is converted to `f32`.
* If both operands are either *signed* or *unsigned*, the operand with the smaller size is cast to the larger size (e.g. `i8 + i32` is equivalent to `i8 as i32 + i32`)
* If one operand is signed and the other is unsigned:
  * If either of the operands is `u64`, the compiler issues an error.
  * If the unsigned operand is larger, both operands are converted to a signed type larger than the unsigned type (e.g. `u32 + i8` is equivalent to `u32 as i64 + i8 as i64`).
  * If the signed operand is larger, the unsigned operand is converted to the signed operand's type.

## Overflows
Overflows and underflows are well-defined.
For signed integers, 2's complement is used; the value of maximal value + 1 is the minimal value.
For unsigned integers, the maximal value + 1 is 0.

# Unary arithmetic operators
## Unary +


# Binary arithmetic operators