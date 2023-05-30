---
title: "notes > dotnet > types > value types > value types"
date: 2021-11-05T21:11:04-0600
draft: true
---
# Primitive Types
Value types store on the stack.
System.Object –> System.ValueType –>

## Signed integrals
For Integers (zero, postive, and negative whole numbers).
<u>.NET TypeC# AliasRangeSuffix</u>
System.Sbytesbyte-128 to 127
System.Int16short -32768 to 32767
System.Int32 int-2147483648 to 2147483647
System.Int64long -9223372036854775808 to 9223372036854775807l or L

## Unsigned integrals
For Cardinals (zero and postive whole numbers).
<u>.NET TypeC# AliasRangeSuffix</u>
System.Bytebyte0 to 255
System.Uint16ushort0 to 65535
System.Uint32uint0 to 4294967295u or U
System.Uint64ulong0 to 18446744073709551615ul or UL

## Native-sized Integers
The aliases nint and nuint are for native-sized integers, meaning that they store a 32-bit integer for 32-bit processors and 64-bit integers for 64-bit processors.

## Unicode characters
<u>.NET TypeC# AliasRange</u>
System.CharcharU+OOOO to U+FFFF

Characters can be created with:
Character literal: 'j'
Unicode escape:'\u0006'
Hex escape:'\x006A'
Cast:(char)106

## Floating point types
For Reals (floating point numbers)
<u>.NET TypeC# AliasRangeSuffixPrecision</u>
System.Singlefloat-3.402823E+38 to 3.402823E+38f or F~6-9 digits
System.Doubledoublesee belowd or D~15-17 digits
- Range: -1.79769313486232E+308 to 1.79769313486232E+308
- double.NaN represents not-a-number (like dividing by zero).
- double.Epsilon represents the smallest positive number that can be stored in a double.

For Accurate Reals (use in science, engineering, or financial applications)
<u>.NET TypeC# AliasRangeSuffixPrecision</u>
System.Decimaldecimalsee belowm or M28-29 digits
- Range: -79228162514264337593543950335 to 79228162514264337593543950335

## Numerics
System.Numerics.BigIntegerArbitrarily large integers.
System.Numerics.ComplexComplex numbers.
System.Numerics.QuaternionQuaternion numbers.

## Boolean
<u>.NET TypeC# Alias</u>
System.Booleanbool

# Operators
+ - / * %
Increment: ++
Decrement: --
Assignment: += -=
Exponents: There is no exponent operator. Use System.Math.Pow().

## Increment and decrement operators
++ and -- can be used before or after the value.

# Methods
All types have these methods:
.Equals(*object*)Boolean if the current type equals *object*.
.GetType()Return the type.
.ToString()Converts a given type to a string.

# Properties
.MinValue
.MaxValue