---
layout: post
title: 'Data Types'
description: 'floats, integers, and a bit of floating point arithmetic, math.isclose()'
date: 2024-01-15 15:30:00 +0000
category: articles
tags: [python]
comments: true
---

<!-- more -->

- <p>Entities in a program like variables and functions, always have an associated type to determine what kind of data it can hold and operations it can do</p>
    <style>
      table {
        font-size: 19px;
        border-collapse: collapse;
        width: 100%;
      }
      th, td {
        border: 1px solid black;
        padding: 8px;
        text-align: left;
      }
      th {
        background-color: #f2f2f2;
      }
    </style>
  <table>
    <tr>
      <th>Entity</th>
      <th>Description</th>
      <th>In Python</th>
    </tr>
    <tr>
      <td>Variables</td>
      <td>Each variable has a type that dictates what kind of data it can store, like integers, floating-point numbers, characters, complex data structures, etc.</td>
      <td>In Python, variables are dynamically typed. E.g., <code>x = 5</code> (integer), <code>y = "Hello"</code> (string).</td>
    </tr>
    <tr>
      <td>Functions</td>
      <td>Functions have types in the form of return types and parameter types. The return type specifies the type of data the function will return, and parameter types specifies the types of arguments that the function can accept.</td>
      <td>In Python, function parameters and return types can be annotated but are not enforced. E.g., <code>def add(a: int, b: int) -&gt; int</code>.</td>
    </tr>
    <tr>
      <td>Objects</td>
      <td>In object-oriented programming, objects are instances of classes, and each class defines a type. This type determines the methods and attributes of the object.</td>
      <td>Python is an object-oriented language. E.g., <code>class Car: pass</code> defines a new type <code>Car</code>.</td>
    </tr>
    <tr>
      <td>Type Systems</td>
      <td>Programming languages can be statically typed (types checked at compile time) or dynamically typed (types checked at runtime). Examples of statically typed languages include C, C++, and Java, while dynamically typed languages include Python and JavaScript.</td>
      <td>Python is dynamically typed. Types are inferred and checked at runtime.</td>
    </tr>
    <tr>
      <td>Type Safety and Inference</td>
      <td>Some languages enforce type safety, ensuring type compatibility and preventing type errors. Others support type inference, where the compiler automatically deduces the types of variables in certain contexts.</td>
      <td>Python supports type inference and has optional type annotations for improved readability and support for static analysis tools like Mypy.</td>
    </tr>
  </table>

- INTEGERS: like 10_000_000 (the underscores are for readability, it's allowed in python). Integers have exact represantation in python and can be any of any magnitude. In contrast, Java has fixed represenatation for its data types. The `int` type in Java is a 32-bit signed integer, which limits its range from -2,147,483,648 to 2,147,483,647. When this range is exceeded, an overflow occurs, leading to unexpected results.

- FLOAT: represent real numbers/floating point like `3.14` or `3_200.5_200`

- <p>FLOAT REPRESENTATIONS: <a href="https://en.wikipedia.org/wiki/Floating-point_arithmetic">wikipedia.org/wiki/Floating-point_arithmetic</a>. Because of this, we dont have exact representation when we use floats, because some numbers need to be represented "infinitely" like 1/3 would be 0.33333.... it's not a limitation of python but just generally in computer languages.</p>

```python
# float numbers in computers are kind of "cheated" because theyre approximated
# due to the inherent limitations of representing decimal numbers in binary format
num = 0.1
print(num)
# prints: 0.1
print(num.hex())
# prints: 0x1.999999999999ap-4
'''
0x: prefix that says it's in hexadecimal
1.999999999999a: significand (or mantissa) of the floating-point number
p-4: exponnent. p indicates binary exponent
it means that the significand is multiplied by 2^(−4) 2(or divided by 2^4, which is 16)

.hex() reveals the precise value that is stored in memory
demonstrating the slight difference from the exact decimal 0.1

when converted to decimal, this is very close to but not exactly 0.1
'''

# -----------------------------

# Alternatively:
print(format(0.1, '.25f'))
# 0.1000000000000000055511151
'''
the format function with the .25f format specifier shows the number with 25 decimal places

the printed 0.1000000000000000055511151 reveals the actual decimal value stored in memory

this value is extremely close to 0.1, but not exactly 0.1, due to the binary representation limitations
'''

# -----------------------------

print(format(0.125, '.25f'))
# 0.1250000000000000000000000
'''
this one is exact, as 0.125 is a number that can be precisely expressed in binary floating point systems because of the sum of powers of  1/2
'''

# -----------------------------

boolean_value = (0.1 + 0.1 + 0.1) == 0.3
print(boolean_value) # False
'''
as we can see, a comparison of the floats of (0.1 +0.1 + 0.1) to the number 0.3 returns false
even though in the real world maths, when summed, it should be equal
'''

# why it's false
print(format((0.1 + 0.1 + 0.1), '.25f')) # 0.3000000000000000444089210
print(format((0.3), '.25f')) # 0.2999999999999999888977698
```

- <p>thus avoid direct equality operators with floating point numbers with equality because of inherent rounding errors. compare them within tolerance or the "epsilon" with math.isclose(). tho for most general purposes, the default precision of floating-point numbers is sufficient</p>

```python
import math

# compare if two floating-point numbers are "close enough"
num1 = 0.1 + 0.1 + 0.1
num2 = 0.3
are_close = math.isclose(num1, num2, rel_tol=1e-9)
print(are_close) # True

# math.isclose checks if num1 and num2 are close to each other
# within a relative tolerance of 1e-9 (scientific notation in python)
```

- <p><a href="https://docs.python.org/3/library/decimal.html">DECIMAL</a>: python's decimal type is more precise and handles fractions better, but not as easy to work with than floats as well as its performance is slower, consumes more memory, and calculations with it are slower.</p>

```python
from decimal import Decimal, getcontext

# set precision for decimal
getcontext().prec = 28

# decimal operations
decimal_result = Decimal('1') / Decimal('7')
print("Decimal:", decimal_result)
# Decimal: 0.1428571428571428571428571429

# equivalent operation w/ float
float_result = 1.0 / 7.0
print("Float:", float_result)
# Float: 0.14285714285714285
```
