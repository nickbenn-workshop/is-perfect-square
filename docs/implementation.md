---
title: Implementation
nav_order: 2
---

{% include abbreviations.md %}

# {{ page.title }}
{:.no_toc}

<details markdown="block">
  <summary>Page contents</summary>
* TOC
{:toc}
</details>

## Declaration

In the `com.tlglearning.Square` class, the `isPerfectSquare` method is declared with the following signature, return type, and modifiers:
 
```java
public static boolean isPerfectSquare(long input) throws IllegalArgumentException
```

The implementation **must not** change the modifiers, return type, method name, parameter types/number/order, or possible exceptions shown above.

## Specifications

The implementation **must** provide this functionality:

1. If `input` is negative, `isPerfectSquare(input)` **must** throw `java.lang.IllegalArgumentException`;

2. Otherwise, if `input` is a perfect square, `isPerfectSquare(input)` **must** return `true`; 

3. Otherwise, `isPerfectSquare(input)` **must** return `false`.

## Tips

1. For computing square roots, `Math.sqrt(input)` is preferred over `Math.pow(input, 0.5)`. In particular, the former provides a stronger accuracy guarantee than the latter when `input` is an `int` or `long` perfect square that can be represented exactly as a `float` or `double` (respectively).

2. Whenever practical, perform calculations in the integer domain.

    For example, if `a` and `b` are both non-negative `long` values, and if you think that `b` _might_ be the square root of `a`:

    * Checking to see if `b` actually is the square root of `a` by evaluating the `boolean` expression `a == b * b` will work correctly for all `b <= 3_037_000_499L` (the largest `long` value whose square also fits within the range of `long`).

    * On the other hand, testing this with `Math.sqrt(a) == b` can give a _false positive_ result for many large `a` and `b` values. Try this with any `b`, where `b >= 67_108_864 && b <= 3_037_000_499L`, and with `a` taking the squared value of `b`: Not only does `boolean` expression `Math.sqrt(a) == b` evaluate to `true` (as expected); the expression `Math.sqrt(a + 1) == b` evalues to `true` as well! As the value of `a` and `b` increase, there are more and more of these false positives. 
   
    Note that this doesn't mean you shouldn't use the `Math.sqrt` method in your implementation, but only that you shouldn't rely on it exclusively.

4. There are multiple ways to round a floating-point value to an integer, including these:

    * The `Math.round` method rounds a `double` or `float` to the nearest integer, returning the value as a `long` or `int`, respectively.

    * Casting with `(long)` or `(int)` (for example) truncates the fractional portion of a `double` or `float`, effectively rounding toward zero (0), and instructs the compiler to treat the result as a `long` or `int`, respectively.

    * The `Math.floor` method rounds down (toward $-\infty$), returning the value as a `double` (not a `long` or `int`) without a fractional part.

    * The `Math.ceil` method rounds up (toward $\infty$), returning the value as a `double` (not a `long` or `int`) without a fractional part.

5. You may find it useful to create one or more additional `static` methods as "helpers"; the problem can be solved without doing so, however.

6. Do not hesitate to declare any `static` fields (especially `static final` constants) that you feel might simplify or clarify your code.

7. The method to be completed includes a `TODO` comment to that effect.
