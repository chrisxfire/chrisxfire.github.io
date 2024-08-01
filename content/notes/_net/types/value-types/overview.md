---
title: overview
date: 2021-11-05T21:11:04-0600
draft: false
weight: -1
---
# Primitive Types
Value types store on the stack.

## Signed integrals
For Integers (zero, positive, and negative whole numbers).
| .NET Type      | C# Alias | Range                                        | Suffix |
| -------------- | -------- | -------------------------------------------- | ------ |
| `System.Sbyte` | `sbyte`  | -128 to 127                                  |        |
| `System.Int16` | `short`  | -32768 to 32767                              |        |
| `System.Int32` | `int`    | -2147483648 to 2147483647                    |        |
| `System.Int64` | `long`   | -9223372036854775808 to 9223372036854775807l | or L   |

## Unsigned integrals
For Cardinals (zero and positive whole numbers).
| .NET Type       | C# Alias | Range                       | Suffix |
| --------------- | -------- | --------------------------- | ------ |
| `System.Byte`   | `byte`   | 0 to 255                    |        |
| `System.Uint16` | `ushort` | 0 to 65535                  |        |
| `System.Uint32` | `uint`   | 0 to 4294967295u            | or U   |
| `System.Uint64` | `ulong`  | 0 to 18446744073709551615ul | or UL  |

## Native-sized Integers
The aliases nint and nuint are for native-sized integers, meaning that they store a 32-bit integer for 32-bit processors and 64-bit integers for 64-bit processors.

## Unicode characters
| .NET Type     | C# Alias | Range            |
| ------------- | -------- | ---------------- |
| `System.Char` | `char`   | U+OOOO to U+FFFF |

Characters can be created with:
- Character literal: `'j'`
- Unicode escape: `'\u0006'`
- Hex escape: `'\x006A'`
- Cast: `(char)106`

## Floating point types
For Reals (floating point numbers)
| .NET Type       | C# Alias | Range                                           | Suffix | Precision     |
| --------------- | -------- | ----------------------------------------------- | ------ | ------------- |
| `System.Single` | `float`  | -3.402823E+38 to 3.402823E+38                   | f or F | ~6-9 digits   |
| `System.Double` | `double` | -1.79769313486232E+308 to 1.79769313486232E+308 | d or D | ~15-17 digits |

- `double.NaN` represents not-a-number (like dividing by zero).
- `double.Epsilon` represents the smallest positive number that can be stored in a double.

For Accurate Reals (use in science, engineering, or financial applications)
| .NET Type      | C# Alias | Range                                                           | Suffix | Precision    |
| -------------- | -------- | --------------------------------------------------------------- | ------ | ------------ |
| System.Decimal | decimal  | -79228162514264337593543950335 to 79228162514264337593543950335 | m or M | 28-29 digits |

## Numerics
- `System.Numerics.BigInteger` - An integer with no lower or upper bounds. 
- `System.Numerics.Complex` - Complex numbers.
- `System.Numerics.Quaternion` - Quaternion numbers.

## Boolean
| .NET Type      | C# Alias |
| -------------- | -------- |
| System.Boolean | bool     |

# Operators
`+ - /  %` and:
- Increment: `++`
- Decrement: `--`
- Assignment: `+=` `-=`
- Exponents: There is no exponent operator. Use `System.Math.Pow()`.

## Increment and decrement operators
`++` and `--` can be used before or after the value.

# Methods
All types have these methods:
- `Equals(object)` - Boolean if the current type equals object.
- `GetType()` - Return the type.
- `ToString()` - Converts a given type to a string.
