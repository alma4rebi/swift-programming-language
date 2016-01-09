<div class="content-wrapper">

<div id="chapter_container" class="conceptualwithtasks">

[‌](){#TP40016643-CH6}[‌](){#TP40016643-CH6-ID60}
Basic Operators {#basic-operators .chapter-name}
---------------

<div class="section section">

An *operator* is a special symbol or phrase that you use to check,
change, or combine values. For example, the addition operator
(`+`{.code-voice}) adds two numbers together (as in
`let i = 1 + 2`{.code-voice}). More complex examples include the logical
AND operator `&&`{.code-voice} (as in
`if enteredDoorCode && passedRetinaScan`{.code-voice}) and the increment
operator `++i`{.code-voice}, which is a shortcut to increase the value
of `i`{.code-voice} by `1`{.code-voice}.

Swift supports most standard C operators and improves several
capabilities to eliminate common coding errors. The assignment operator
(`=`{.code-voice}) does not return a value, to prevent it from being
mistakenly used when the equal to operator (`==`{.code-voice}) is
intended. Arithmetic operators (`+`{.code-voice}, `-`{.code-voice},
`*`{.code-voice}, `/`{.code-voice}, `%`{.code-voice} and so forth)
detect and disallow value overflow, to avoid unexpected results when
working with numbers that become larger or smaller than the allowed
value range of the type that stores them. You can opt in to value
overflow behavior by using Swift’s overflow operators, as described in
[Overflow Operators](AdvancedOperators.md#TP40016643-CH27-ID37).

Unlike C, Swift lets you perform remainder (`%`{.code-voice})
calculations on floating-point numbers. Swift also provides two range
operators (`a..<b`{.code-voice} and `a...b`{.code-voice}) not found in
C, as a shortcut for expressing a range of values.

This chapter describes the common operators in Swift. [Advanced
Operators](AdvancedOperators.md) covers Swift’s advanced operators,
and describes how to define your own custom operators and implement the
standard operators for your own custom types.

</div>

<div class="section section">

[‌](){#TP40016643-CH6-ID61}
### Terminology {#terminology .section-name}

Operators are unary, binary, or ternary:

-   *Unary* operators operate on a single target (such as
    `-a`{.code-voice}). Unary *prefix* operators appear immediately
    before their target (such as `!b`{.code-voice}), and unary *postfix*
    operators appear immediately after their target (such as
    `i++`{.code-voice}).

-   *Binary* operators operate on two targets (such as
    `2 + 3`{.code-voice}) and are *infix* because they appear in between
    their two targets.

-   *Ternary* operators operate on three targets. Like C, Swift has only
    one ternary operator, the ternary conditional operator
    (`a ? b : c`{.code-voice}).

The values that operators affect are *operands*. In the expression
`1 + 2`{.code-voice}, the `+`{.code-voice} symbol is a binary operator
and its two operands are the values `1`{.code-voice} and
`2`{.code-voice}.

</div>

<div class="section section">

[‌](){#TP40016643-CH6-ID62}
### Assignment Operator {#assignment-operator .section-name}

The *assignment operator* (`a = b`{.code-voice}) initializes or updates
the value of `a`{.code-voice} with the value of `b`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `b`{.vc} = `10`{.m}
2.  `var`{.code-voice} `a`{.vc} = `5`{.m}
3.  `a`{.code-voice} = `b`{.vc}
4.  `// a is now equal to 10`{.code-voice}

</div>

</div>

</div>

If the right side of the assignment is a tuple with multiple values, its
elements can be decomposed into multiple constants or variables at once:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} (`x`{.vc}, `y`{.vc}) = (`1`{.m}, `2`{.m})
2.  `// x is equal to 1, and y is equal to 2`{.code-voice}

</div>

</div>

</div>

Unlike the assignment operator in C and Objective-C, the assignment
operator in Swift does not itself return a value. The following
statement is not valid:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `if`{.code-voice} `x`{.vc} = `y`{.vc} {
2.  `    // this is not valid, because x = y does not return a value`{.code-voice}
3.  `}`{.code-voice}

</div>

</div>

</div>

This feature prevents the assignment operator (`=`{.code-voice}) from
being used by accident when the equal to operator (`==`{.code-voice}) is
actually intended. By making `if x = y`{.code-voice} invalid, Swift
helps you to avoid these kinds of errors in your code.

</div>

<div class="section section">

[‌](){#TP40016643-CH6-ID63}
### Arithmetic Operators {#arithmetic-operators .section-name}

Swift supports the four standard *arithmetic operators* for all number
types:

-   Addition (`+`{.code-voice})

-   Subtraction (`-`{.code-voice})

-   Multiplication (`*`{.code-voice})

-   Division (`/`{.code-voice})

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `1`{.code-voice} + `2`{.m} `// equals 3`{.c}
2.  `5`{.code-voice} - `3`{.m} `// equals 2`{.c}
3.  `2`{.code-voice} \* `3`{.m} `// equals 6`{.c}
4.  `10.0`{.code-voice} / `2.5`{.m} `// equals 4.0`{.c}

</div>

</div>

</div>

Unlike the arithmetic operators in C and Objective-C, the Swift
arithmetic operators do not allow values to overflow by default. You can
opt in to value overflow behavior by using Swift’s overflow operators
(such as `a &+ b`{.code-voice}). See [Overflow
Operators](AdvancedOperators.md#TP40016643-CH27-ID37).

The addition operator is also supported for `String`{.code-voice}
concatenation:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `"hello, "`{.code-voice} + `"world"`{.s}
    `// equals "hello, world"`{.c}

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH6-ID64}
### Remainder Operator {#remainder-operator .section-name}

The *remainder operator* (`a % b`{.code-voice}) works out how many
multiples of `b`{.code-voice} will fit inside `a`{.code-voice} and
returns the value that is left over (known as the *remainder*).

<div class="note">

Note

The remainder operator (`%`{.code-voice}) is also known as a *modulo
operator* in other languages. However, its behavior in Swift for
negative numbers means that it is, strictly speaking, a remainder rather
than a modulo operation.

</div>

Here’s how the remainder operator works. To calculate
`9 % 4`{.code-voice}, you first work out how many `4`{.code-voice}s will
fit inside `9`{.code-voice}:

<div class="figure">

<span class="caption"></span> ![image:
../Art/remainderInteger\_2x.png](Art/remainderInteger_2x.png){width="337"
height="66"}

</div>

You can fit two `4`{.code-voice}s inside `9`{.code-voice}, and the
remainder is `1`{.code-voice} (shown in orange).

In Swift, this would be written as:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `9`{.code-voice} % `4`{.m} `// equals 1`{.c}

</div>

</div>

</div>

To determine the answer for `a % b`{.code-voice}, the `%`{.code-voice}
operator calculates the following equation and returns
`remainder`{.code-voice} as its output:

`a`{.code-voice} = (`b`{.code-voice} x `some multiplier`{.code-voice}) +
`remainder`{.code-voice}

where `some multiplier`{.code-voice} is the largest number of multiples
of `b`{.code-voice} that will fit inside `a`{.code-voice}.

Inserting `9`{.code-voice} and `4`{.code-voice} into this equation
yields:

`9`{.code-voice} = (`4`{.code-voice} x `2`{.code-voice}) +
`1`{.code-voice}

The same method is applied when calculating the remainder for a negative
value of `a`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `-9`{.code-voice} % `4`{.m} `// equals -1`{.c}

</div>

</div>

</div>

Inserting `-9`{.code-voice} and `4`{.code-voice} into the equation
yields:

`-9`{.code-voice} = (`4`{.code-voice} x `-2`{.code-voice}) +
`-1`{.code-voice}

giving a remainder value of `-1`{.code-voice}.

The sign of `b`{.code-voice} is ignored for negative values of
`b`{.code-voice}. This means that `a % b`{.code-voice} and
`a % -b`{.code-voice} always give the same answer.

</div>

<div class="section section">

[‌](){#TP40016643-CH6-ID65}
### Floating-Point Remainder Calculations {#floating-point-remainder-calculations .section-name}

Unlike the remainder operator in C and Objective-C, Swift’s remainder
operator can also operate on floating-point numbers:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `8`{.code-voice} % `2.5`{.m} `// equals 0.5`{.c}

</div>

</div>

</div>

In this example, `8`{.code-voice} divided by `2.5`{.code-voice} equals
`3`{.code-voice}, with a remainder of `0.5`{.code-voice}, so the
remainder operator returns a `Double`{.code-voice} value of
`0.5`{.code-voice}.

<div class="figure">

<span class="caption"></span> ![image:
../Art/remainderFloat\_2x.png](Art/remainderFloat_2x.png){width="301"
height="66"}

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH6-ID66}
### Increment and Decrement Operators {#increment-and-decrement-operators .section-name}

Like C, Swift provides an *increment operator* (`++`{.code-voice}) and a
*decrement operator* (`--`{.code-voice}) as a shortcut to increase or
decrease the value of a numeric variable by `1`{.code-voice}. You can
use these operators with variables of any integer or floating-point
type.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `i`{.vc} = `0`{.m}
2.  `++i`{.code-voice} `// i now equals 1`{.c}

</div>

</div>

</div>

Each time you call `++i`{.code-voice}, the value of `i`{.code-voice} is
increased by `1`{.code-voice}. Essentially, `++i`{.code-voice} is
shorthand for saying `i = i + 1`{.code-voice}. Likewise,
`--i`{.code-voice} can be used as shorthand for
`i = i - 1`{.code-voice}.

The `++`{.code-voice} and `--`{.code-voice} symbols can be used as
prefix operators or as postfix operators. `++i`{.code-voice} and
`i++`{.code-voice} are both valid ways to increase the value of
`i`{.code-voice} by `1`{.code-voice}. Similarly, `--i`{.code-voice} and
`i--`{.code-voice} are both valid ways to decrease the value of
`i`{.code-voice} by `1`{.code-voice}.

Note that these operators modify `i`{.code-voice} and also return a
value. If you only want to increment or decrement the value stored in
`i`{.code-voice}, you can ignore the returned value. However, if you
*do* use the returned value, it will be different based on whether you
used the prefix or postfix version of the operator, according to the
following rules:

-   If the operator is written *before* the variable, it increments the
    variable *before* returning its value.

-   If the operator is written *after* the variable, it increments the
    variable *after* returning its value.

For example:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `a`{.vc} = `0`{.m}
2.  `let`{.code-voice} `b`{.vc} = ++`a`{.vc}
3.  `// a and b are now both equal to 1`{.code-voice}
4.  `let`{.code-voice} `c`{.vc} = `a`{.vc}++
5.  `// a is now equal to 2, but c has been set to the pre-increment value of 1`{.code-voice}

</div>

</div>

</div>

In the example above, `let b = ++a`{.code-voice} increments
`a`{.code-voice} *before* returning its value. This is why both
`a`{.code-voice} and `b`{.code-voice} are equal to the new value of
`1`{.code-voice}.

However, `let c = a++`{.code-voice} increments `a`{.code-voice} *after*
returning its value. This means that `c`{.code-voice} gets the old value
of `1`{.code-voice}, and `a`{.code-voice} is then updated to equal
`2`{.code-voice}.

Unless you need the specific behavior of `i++`{.code-voice}, it is
recommended that you use `++i`{.code-voice} and `--i`{.code-voice} in
all cases, because they have the typical expected behavior of modifying
`i`{.code-voice} and returning the result.

</div>

<div class="section section">

[‌](){#TP40016643-CH6-ID67}
### Unary Minus Operator {#unary-minus-operator .section-name}

The sign of a numeric value can be toggled using a prefixed
`-`{.code-voice}, known as the *unary minus operator*:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `three`{.vc} = `3`{.m}
2.  `let`{.code-voice} `minusThree`{.vc} = -`three`{.vc}
    `// minusThree equals -3`{.c}
3.  `let`{.code-voice} `plusThree`{.vc} = -`minusThree`{.vc}
    `// plusThree equals 3, or "minus minus three"`{.c}

</div>

</div>

</div>

The unary minus operator (`-`{.code-voice}) is prepended directly before
the value it operates on, without any white space.

</div>

<div class="section section">

[‌](){#TP40016643-CH6-ID68}
### Unary Plus Operator {#unary-plus-operator .section-name}

The *unary plus operator* (`+`{.code-voice}) simply returns the value it
operates on, without any change:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `minusSix`{.vc} = -`6`{.m}
2.  `let`{.code-voice} `alsoMinusSix`{.vc} = +`minusSix`{.vc}
    `// alsoMinusSix equals -6`{.c}

</div>

</div>

</div>

Although the unary plus operator doesn’t actually do anything, you can
use it to provide symmetry in your code for positive numbers when also
using the unary minus operator for negative numbers.

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH6-ID69}
### Compound Assignment Operators {#compound-assignment-operators .section-name}

Like C, Swift provides *compound assignment operators* that combine
assignment (`=`{.code-voice}) with another operation. One example is the
*addition assignment operator* (`+=`{.code-voice}):

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `a`{.vc} = `1`{.m}
2.  `a`{.code-voice} += `2`{.m}
3.  `// a is now equal to 3`{.code-voice}

</div>

</div>

</div>

The expression `a += 2`{.code-voice} is shorthand for
`a = a + 2`{.code-voice}. Effectively, the addition and the assignment
are combined into one operator that performs both tasks at the same
time.

<div class="note">

Note

The compound assignment operators do not return a value. You cannot
write `let b = a += 2`{.code-voice}, for example. This behavior is
different from the increment and decrement operators mentioned above.

</div>

A complete list of compound assignment operators can be found in
[Expressions](Expressions.md).

</div>

<div class="section section">

[‌](){#TP40016643-CH6-ID70}
### Comparison Operators {#comparison-operators .section-name}

Swift supports all standard C *comparison operators*:

-   Equal to (`a == b`{.code-voice})

-   Not equal to (`a != b`{.code-voice})

-   Greater than (`a > b`{.code-voice})

-   Less than (`a < b`{.code-voice})

-   Greater than or equal to (`a >= b`{.code-voice})

-   Less than or equal to (`a <= b`{.code-voice})

<div class="note">

Note

Swift also provides two *identity operators* (`===`{.code-voice} and
`!==`{.code-voice}), which you use to test whether two object references
both refer to the same object instance. For more information, see
[Classes and Structures](ClassesAndStructures.md).

</div>

Each of the comparison operators returns a `Bool`{.code-voice} value to
indicate whether or not the statement is true:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `1`{.code-voice} == `1`{.m} `// true, because 1 is equal to 1`{.c}
2.  `2`{.code-voice} != `1`{.m}
    `// true, because 2 is not equal to 1`{.c}
3.  `2`{.code-voice} &gt; `1`{.m}
    `// true, because 2 is greater than 1`{.c}
4.  `1`{.code-voice} &lt; `2`{.m}
    `// true, because 1 is less than 2`{.c}
5.  `1`{.code-voice} &gt;= `1`{.m}
    `// true, because 1 is greater than or equal to 1`{.c}
6.  `2`{.code-voice} &lt;= `1`{.m}
    `// false, because 2 is not less than or equal to 1`{.c}

</div>

</div>

</div>

Comparison operators are often used in conditional statements, such as
the `if`{.code-voice} statement:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `name`{.vc} = `"world"`{.s}
2.  `if`{.code-voice} `name`{.vc} == `"world"`{.s} {
3.  `    print`{.code-voice}(`"hello, world"`{.s})
4.  `} else`{.code-voice} {
5.  `    print`{.code-voice}(`"I'm sorry `{.s}\\(`name`{.vc})`, but I don't recognize you"`{.s})
6.  `}`{.code-voice}
7.  `// prints "hello, world", because name is indeed equal to "world"`{.code-voice}

</div>

</div>

</div>

For more on the `if`{.code-voice} statement, see [Control
Flow](ControlFlow.md).

</div>

<div class="section section">

[‌](){#TP40016643-CH6-ID71}
### Ternary Conditional Operator {#ternary-conditional-operator .section-name}

The *ternary conditional operator* is a special operator with three
parts, which takes the form `question ? answer1 : answer2`{.code-voice}.
It is a shortcut for evaluating one of two expressions based on whether
`question`{.code-voice} is true or false. If `question`{.code-voice} is
true, it evaluates `answer1`{.code-voice} and returns its value;
otherwise, it evaluates `answer2`{.code-voice} and returns its value.

The ternary conditional operator is shorthand for the code below:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `if`{.code-voice} `question`{.vc} {
2.  `    answer1`{.code-voice}
3.  `} else`{.code-voice} {
4.  `    answer2`{.code-voice}
5.  `}`{.code-voice}

</div>

</div>

</div>

Here’s an example, which calculates the height for a table row. The row
height should be 50 points taller than the content height if the row has
a header, and 20 points taller if the row doesn’t have a header:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `contentHeight`{.vc} = `40`{.m}
2.  `let`{.code-voice} `hasHeader`{.vc} = `true`{.kt}
3.  `let`{.code-voice} `rowHeight`{.vc} = `contentHeight`{.vc} +
    (`hasHeader`{.vc} ? `50`{.m} : `20`{.m})
4.  `// rowHeight is equal to 90`{.code-voice}

</div>

</div>

</div>

The preceding example is shorthand for the code below:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `contentHeight`{.vc} = `40`{.m}
2.  `let`{.code-voice} `hasHeader`{.vc} = `true`{.kt}
3.  `var`{.code-voice} `rowHeight`{.vc} = `contentHeight`{.vc}
4.  `if`{.code-voice} `hasHeader`{.vc} {
5.  `    rowHeight`{.code-voice} = `rowHeight`{.vc} + `50`{.m}
6.  `} else`{.code-voice} {
7.  `    rowHeight`{.code-voice} = `rowHeight`{.vc} + `20`{.m}
8.  `}`{.code-voice}
9.  `// rowHeight is equal to 90`{.code-voice}

</div>

</div>

</div>

The first example’s use of the ternary conditional operator means that
`rowHeight`{.code-voice} can be set to the correct value on a single
line of code. This is more concise than the second example, and removes
the need for `rowHeight`{.code-voice} to be a variable, because its
value does not need to be modified within an `if`{.code-voice}
statement.

The ternary conditional operator provides an efficient shorthand for
deciding which of two expressions to consider. Use the ternary
conditional operator with care, however. Its conciseness can lead to
hard-to-read code if overused. Avoid combining multiple instances of the
ternary conditional operator into one compound statement.

</div>

<div class="section section">

[‌](){#TP40016643-CH6-ID72}
### Nil Coalescing Operator {#nil-coalescing-operator .section-name}

The *nil coalescing operator* (`a ?? b`{.code-voice}) unwraps an
optional `a`{.code-voice} if it contains a value, or returns a default
value `b`{.code-voice} if `a`{.code-voice} is `nil`{.code-voice}. The
expression `a`{.code-voice} is always of an optional type. The
expression `b`{.code-voice} must match the type that is stored inside
`a`{.code-voice}.

The nil coalescing operator is shorthand for the code below:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `a`{.code-voice} != `nil`{.kt} ? `a`{.vc}! : `b`{.vc}

</div>

</div>

</div>

The code above uses the ternary conditional operator and forced
unwrapping (`a!`{.code-voice}) to access the value wrapped inside
`a`{.code-voice} when `a`{.code-voice} is not `nil`{.code-voice}, and to
return `b`{.code-voice} otherwise. The nil coalescing operator provides
a more elegant way to encapsulate this conditional checking and
unwrapping in a concise and readable form.

<div class="note">

Note

If the value of `a`{.code-voice} is non-`nil`{.code-voice}, the value of
`b`{.code-voice} is not evaluated. This is known as *short-circuit
evaluation*.

</div>

The example below uses the nil coalescing operator to choose between a
default color name and an optional user-defined color name:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `defaultColorName`{.vc} = `"red"`{.s}
2.  `var`{.code-voice} `userDefinedColorName`{.vc}: `String`{.n}?
    `// defaults to nil`{.c}
3.  ` `{.code-voice}
4.  `var`{.code-voice} `colorNameToUse`{.vc} =
    `userDefinedColorName`{.vc} ?? `defaultColorName`{.vc}
5.  `// userDefinedColorName is nil, so colorNameToUse is set to the default of "red"`{.code-voice}

</div>

</div>

</div>

The `userDefinedColorName`{.code-voice} variable is defined as an
optional `String`{.code-voice}, with a default value of
`nil`{.code-voice}. Because `userDefinedColorName`{.code-voice} is of an
optional type, you can use the nil coalescing operator to consider its
value. In the example above, the operator is used to determine an
initial value for a `String`{.code-voice} variable called
`colorNameToUse`{.code-voice}. Because
`userDefinedColorName`{.code-voice} is `nil`{.code-voice}, the
expression `userDefinedColorName ?? defaultColorName`{.code-voice}
returns the value of `defaultColorName`{.code-voice}, or
`"red"`{.code-voice}.

If you assign a non-`nil`{.code-voice} value to
`userDefinedColorName`{.code-voice} and perform the nil coalescing
operator check again, the value wrapped inside
`userDefinedColorName`{.code-voice} is used instead of the default:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `userDefinedColorName`{.code-voice} = `"green"`{.s}
2.  `colorNameToUse`{.code-voice} = `userDefinedColorName`{.vc} ??
    `defaultColorName`{.vc}
3.  `// userDefinedColorName is not nil, so colorNameToUse is set to "green"`{.code-voice}

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH6-ID73}
### Range Operators {#range-operators .section-name}

Swift includes two *range operators*, which are shortcuts for expressing
a range of values.

<div class="section section">

[‌](){#TP40016643-CH6-ID74}
### Closed Range Operator {#closed-range-operator .section-name}

The *closed range operator* (`a...b`{.code-voice}) defines a range that
runs from `a`{.code-voice} to `b`{.code-voice}, and includes the values
`a`{.code-voice} and `b`{.code-voice}. The value of `a`{.code-voice}
must not be greater than `b`{.code-voice}.

The closed range operator is useful when iterating over a range in which
you want all of the values to be used, such as with a
`for`{.code-voice}-`in`{.code-voice} loop:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `for`{.code-voice} `index`{.vc} `in`{.kt} `1`{.m}...`5`{.m} {
2.  `    print`{.code-voice}(`"`{.s}\\(`index`{.vc})` times 5 is `{.s}\\(`index`{.vc} \*
    `5`{.m})`"`{.s})
3.  `}`{.code-voice}
4.  `// 1 times 5 is 5`{.code-voice}
5.  `// 2 times 5 is 10`{.code-voice}
6.  `// 3 times 5 is 15`{.code-voice}
7.  `// 4 times 5 is 20`{.code-voice}
8.  `// 5 times 5 is 25`{.code-voice}

</div>

</div>

</div>

For more on `for`{.code-voice}-`in`{.code-voice} loops, see [Control
Flow](ControlFlow.md).

</div>

<div class="section section">

[‌](){#TP40016643-CH6-ID75}
### Half-Open Range Operator {#half-open-range-operator .section-name}

The *half-open range operator* (`a..<b`{.code-voice}) defines a range
that runs from `a`{.code-voice} to `b`{.code-voice}, but does not
include `b`{.code-voice}. It is said to be *half-open* because it
contains its first value, but not its final value. As with the closed
range operator, the value of `a`{.code-voice} must not be greater than
`b`{.code-voice}. If the value of `a`{.code-voice} is equal to
`b`{.code-voice}, then the resulting range will be empty.

Half-open ranges are particularly useful when you work with zero-based
lists such as arrays, where it is useful to count up to (but not
including) the length of the list:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `names`{.vc} = \[`"Anna"`{.s}, `"Alex"`{.s},
    `"Brian"`{.s}, `"Jack"`{.s}\]
2.  `let`{.code-voice} `count`{.vc} = `names`{.vc}.`count`{.vc}
3.  `for`{.code-voice} `i`{.vc} `in`{.kt} `0`{.m}..&lt;`count`{.vc} {
4.  `    print`{.code-voice}(`"Person `{.s}\\(`i`{.vc} +
    `1`{.m})` is called `{.s}\\(`names`{.vc}\[`i`{.vc}\])`"`{.s})
5.  `}`{.code-voice}
6.  `// Person 1 is called Anna`{.code-voice}
7.  `// Person 2 is called Alex`{.code-voice}
8.  `// Person 3 is called Brian`{.code-voice}
9.  `// Person 4 is called Jack`{.code-voice}

</div>

</div>

</div>

Note that the array contains four items, but `0..<count`{.code-voice}
only counts as far as `3`{.code-voice} (the index of the last item in
the array), because it is a half-open range. For more on arrays, see
[Arrays](CollectionTypes.md#TP40016643-CH8-ID107).

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH6-ID76}
### Logical Operators {#logical-operators .section-name}

*Logical operators* modify or combine the Boolean logic values
`true`{.code-voice} and `false`{.code-voice}. Swift supports the three
standard logical operators found in C-based languages:

-   Logical NOT (`!a`{.code-voice})

-   Logical AND (`a && b`{.code-voice})

-   Logical OR (`a || b`{.code-voice})

<div class="section section">

[‌](){#TP40016643-CH6-ID77}
### Logical NOT Operator {#logical-not-operator .section-name}

The *logical NOT operator* (`!a`{.code-voice}) inverts a Boolean value
so that `true`{.code-voice} becomes `false`{.code-voice}, and
`false`{.code-voice} becomes `true`{.code-voice}.

The logical NOT operator is a prefix operator, and appears immediately
before the value it operates on, without any white space. It can be read
as “not `a`{.code-voice}”, as seen in the following example:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `allowedEntry`{.vc} = `false`{.kt}
2.  `if`{.code-voice} !`allowedEntry`{.vc} {
3.  `    print`{.code-voice}(`"ACCESS DENIED"`{.s})
4.  `}`{.code-voice}
5.  `// prints "ACCESS DENIED"`{.code-voice}

</div>

</div>

</div>

The phrase `if !allowedEntry`{.code-voice} can be read as “if not
allowed entry.” The subsequent line is only executed if “not allowed
entry” is true; that is, if `allowedEntry`{.code-voice} is
`false`{.code-voice}.

As in this example, careful choice of Boolean constant and variable
names can help to keep code readable and concise, while avoiding double
negatives or confusing logic statements.

</div>

<div class="section section">

[‌](){#TP40016643-CH6-ID78}
### Logical AND Operator {#logical-and-operator .section-name}

The *logical AND operator* (`a && b`{.code-voice}) creates logical
expressions where both values must be `true`{.code-voice} for the
overall expression to also be `true`{.code-voice}.

If either value is `false`{.code-voice}, the overall expression will
also be `false`{.code-voice}. In fact, if the *first* value is
`false`{.code-voice}, the second value won’t even be evaluated, because
it can’t possibly make the overall expression equate to
`true`{.code-voice}. This is known as *short-circuit evaluation*.

This example considers two `Bool`{.code-voice} values and only allows
access if both values are `true`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `enteredDoorCode`{.vc} = `true`{.kt}
2.  `let`{.code-voice} `passedRetinaScan`{.vc} = `false`{.kt}
3.  `if`{.code-voice} `enteredDoorCode`{.vc} && `passedRetinaScan`{.vc}
    {
4.  `    print`{.code-voice}(`"Welcome!"`{.s})
5.  `} else`{.code-voice} {
6.  `    print`{.code-voice}(`"ACCESS DENIED"`{.s})
7.  `}`{.code-voice}
8.  `// prints "ACCESS DENIED"`{.code-voice}

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH6-ID79}
### Logical OR Operator {#logical-or-operator .section-name}

The *logical OR operator* (`a || b`{.code-voice}) is an infix operator
made from two adjacent pipe characters. You use it to create logical
expressions in which only *one* of the two values has to be
`true`{.code-voice} for the overall expression to be
`true`{.code-voice}.

Like the Logical AND operator above, the Logical OR operator uses
short-circuit evaluation to consider its expressions. If the left side
of a Logical OR expression is `true`{.code-voice}, the right side is not
evaluated, because it cannot change the outcome of the overall
expression.

In the example below, the first `Bool`{.code-voice} value
(`hasDoorKey`{.code-voice}) is `false`{.code-voice}, but the second
value (`knowsOverridePassword`{.code-voice}) is `true`{.code-voice}.
Because one value is `true`{.code-voice}, the overall expression also
evaluates to `true`{.code-voice}, and access is allowed:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `hasDoorKey`{.vc} = `false`{.kt}
2.  `let`{.code-voice} `knowsOverridePassword`{.vc} = `true`{.kt}
3.  `if`{.code-voice} `hasDoorKey`{.vc} || `knowsOverridePassword`{.vc}
    {
4.  `    print`{.code-voice}(`"Welcome!"`{.s})
5.  `} else`{.code-voice} {
6.  `    print`{.code-voice}(`"ACCESS DENIED"`{.s})
7.  `}`{.code-voice}
8.  `// prints "Welcome!"`{.code-voice}

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH6-ID80}
### Combining Logical Operators {#combining-logical-operators .section-name}

You can combine multiple logical operators to create longer compound
expressions:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `if`{.code-voice} `enteredDoorCode`{.vc} && `passedRetinaScan`{.vc}
    || `hasDoorKey`{.vc} || `knowsOverridePassword`{.vc} {
2.  `    print`{.code-voice}(`"Welcome!"`{.s})
3.  `} else`{.code-voice} {
4.  `    print`{.code-voice}(`"ACCESS DENIED"`{.s})
5.  `}`{.code-voice}
6.  `// prints "Welcome!"`{.code-voice}

</div>

</div>

</div>

This example uses multiple `&&`{.code-voice} and `||`{.code-voice}
operators to create a longer compound expression. However, the
`&&`{.code-voice} and `||`{.code-voice} operators still operate on only
two values, so this is actually three smaller expressions chained
together. The example can be read as:

If we’ve entered the correct door code and passed the retina scan, or if
we have a valid door key, or if we know the emergency override password,
then allow access.

Based on the values of `enteredDoorCode`{.code-voice},
`passedRetinaScan`{.code-voice}, and `hasDoorKey`{.code-voice}, the
first two subexpressions are `false`{.code-voice}. However, the
emergency override password is known, so the overall compound expression
still evaluates to `true`{.code-voice}.

<div class="note">

Note

The Swift logical operators `&&`{.code-voice} and `||`{.code-voice} are
left-associative, meaning that compound expressions with multiple
logical operators evaluate the leftmost subexpression first.

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH6-ID81}
### Explicit Parentheses {#explicit-parentheses .section-name}

It is sometimes useful to include parentheses when they are not strictly
needed, to make the intention of a complex expression easier to read. In
the door access example above, it is useful to add parentheses around
the first part of the compound expression to make its intent explicit:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `if`{.code-voice} (`enteredDoorCode`{.vc} &&
    `passedRetinaScan`{.vc}) || `hasDoorKey`{.vc} ||
    `knowsOverridePassword`{.vc} {
2.  `    print`{.code-voice}(`"Welcome!"`{.s})
3.  `} else`{.code-voice} {
4.  `    print`{.code-voice}(`"ACCESS DENIED"`{.s})
5.  `}`{.code-voice}
6.  `// prints "Welcome!"`{.code-voice}

</div>

</div>

</div>

The parentheses make it clear that the first two values are considered
as part of a separate possible state in the overall logic. The output of
the compound expression doesn’t change, but the overall intention is
clearer to the reader. Readability is always preferred over brevity; use
parentheses where they help to make your intentions clear.

</div>

</div>

</div>

</div>
