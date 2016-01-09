<div class="content-wrapper">

<div id="chapter_container" class="conceptualwithtasks">

[‌](){#TP40016643-CH32}[‌](){#TP40016643-CH32-ID383}
Expressions {#expressions .chapter-name}
-----------

<div class="section section">

In Swift, there are four kinds of expressions: prefix expressions,
binary expressions, primary expressions, and postfix expressions.
Evaluating an expression returns a value, causes a side effect, or both.

Prefix and binary expressions let you apply operators to smaller
expressions. Primary expressions are conceptually the simplest kind of
expression, and they provide a way to access values. Postfix
expressions, like prefix and binary expressions, let you build up more
complex expressions using postfixes such as function calls and member
access. Each kind of expression is described in detail in the sections
below.

<div class="syntax-defs">

Grammar of an expression

<div class="syntax-defs-group">

[‌](){#expression} <span class="syntax-def-name"> expression </span>
<span class="arrow"> → </span><span class="optional"><span
class="syntactic-cat">[try-operator](Expressions.md#try-operator)</span>~opt~</span><span
class="syntactic-cat">[prefix-expression](Expressions.md#prefix-expression)</span><span
class="optional"><span
class="syntactic-cat">[binary-expressions](Expressions.md#binary-expressions)</span>~opt~</span>

[‌](){#expression-list} <span class="syntax-def-name"> expression-list
</span> <span class="arrow"> → </span><span class="alternative"> <span
class="syntactic-cat">[expression](Expressions.md#expression)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[expression](Expressions.md#expression)</span>`,`{.literal}<span
class="syntactic-cat">[expression-list](Expressions.md#expression-list)</span>
</span>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH32-ID384}
### Prefix Expressions {#prefix-expressions .section-name}

*Prefix expressions* combine an optional prefix operator with an
expression. Prefix operators take one argument, the expression that
follows them.

For information about the behavior of these operators, see [Basic
Operators](BasicOperators.md) and [Advanced
Operators](AdvancedOperators.md).

For information about the operators provided by the Swift standard
library, see *Swift Standard Library Operators Reference*.

In addition to the standard library operators, you use `&`{.code-voice}
immediately before the name of a variable that’s being passed as an
in-out argument to a function call expression. For more information and
to see an example, see [In-Out
Parameters](Functions.md#TP40016643-CH10-ID173).

<div class="syntax-defs">

Grammar of a prefix expression

<div class="syntax-defs-group">

[‌](){#prefix-expression} <span class="syntax-def-name">
prefix-expression </span> <span class="arrow"> → </span><span
class="optional"><span
class="syntactic-cat">[prefix-operator](LexicalStructure.md#prefix-operator)</span>~opt~</span><span
class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span>

[‌](){#TP40016643-CH32-NoLink_398} <span class="syntax-def-name">
prefix-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[in-out-expression](Expressions.md#in-out-expression)</span>

[‌](){#in-out-expression} <span class="syntax-def-name">
in-out-expression </span> <span class="arrow"> →
</span>`&`{.literal}<span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH32-ID516}
### Try Operator {#try-operator .section-name}

A *try expression* consists of the `try`{.code-voice} operator followed
by an expression that can throw an error. It has the following form:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    try expression
    ```

</div>

An *optional-try expression* consists of the `try?`{.code-voice}
operator followed by an expression that can throw an error. It has the
following form:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    try? expression
    ```

</div>

If the *expression* does not throw an error, the value of the
optional-try expression is an optional containing the value of the
*expression*. Otherwise, the value of the optional-try expression is
`nil`{.code-voice}.

A *forced-try expression* consists of the `try!`{.code-voice} operator
followed by an expression that can throw an error. It has the following
form:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    try! expression
    ```

</div>

If the *expression* throws an error, a runtime error is produced.

When the expression on the left hand side of a binary operator is marked
with `try`{.code-voice}, `try?`{.code-voice}, or `try!`{.code-voice},
that operator applies to the whole binary expression. That said, you can
use parentheses to be explicit about the scope of the operator’s
application.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `sum`{.code-voice} = `try`{.kt} `someThrowingFunction`{.vc}() +
    `anotherThrowingFunction`{.vc}()
    `// try applies to both function calls`{.c}
2.  `sum`{.code-voice} = `try`{.kt} (`someThrowingFunction`{.vc}() +
    `anotherThrowingFunction`{.vc}())
    `// try apllies to both function calls`{.c}
3.  `sum`{.code-voice} = (`try`{.kt} `someThrowingFunction`{.vc}()) +
    `anotherThrowingFunction`{.vc}()
    `// Error: try applies only to the first function call`{.c}

</div>

</div>

</div>

A `try`{.code-voice} expression can’t appear on the right hand side of a
binary operator, unless the binary operator is the assignment operator
or the `try`{.code-voice} expression is enclosed in parentheses.

For more information and to see examples of how to use
`try`{.code-voice}, `try?`{.code-voice}, and `try!`{.code-voice}, see
[Error Handling](ErrorHandling.md).

<div class="syntax-defs">

Grammar of a try expression

<div class="syntax-defs-group">

[‌](){#try-operator} <span class="syntax-def-name"> try-operator </span>
<span class="arrow"> → </span><span class="alternative"> `try`{.literal}
</span><span class="alternative"> `try`{.literal}`?`{.literal}
</span><span class="alternative"> `try`{.literal}`!`{.literal} </span>

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH32-ID385}
### Binary Expressions {#binary-expressions .section-name}

*Binary expressions* combine an infix binary operator with the
expression that it takes as its left-hand and right-hand arguments. It
has the following form:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    left-hand argument operator right-hand argument
    ```

</div>

For information about the behavior of these operators, see [Basic
Operators](BasicOperators.md) and [Advanced
Operators](AdvancedOperators.md).

For information about the operators provided by the Swift standard
library, see *Swift Standard Library Operators Reference*.

<div class="note">

Note

At parse time, an expression made up of binary operators is represented
as a flat list. This list is transformed into a tree by applying
operator precedence. For example, the expression
`2 + 3 * 5`{.code-voice} is initially understood as a flat list of five
items, `2`{.code-voice}, `+`{.code-voice}, `3`{.code-voice},
`*`{.code-voice}, and `5`{.code-voice}. This process transforms it into
the tree (2 + (3 \* 5)).

</div>

<div class="syntax-defs">

Grammar of a binary expression

<div class="syntax-defs-group">

[‌](){#binary-expression} <span class="syntax-def-name">
binary-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[binary-operator](LexicalStructure.md#binary-operator)</span><span
class="syntactic-cat">[prefix-expression](Expressions.md#prefix-expression)</span>

[‌](){#TP40016643-CH32-NoLink_405} <span class="syntax-def-name">
binary-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[assignment-operator](Expressions.md#assignment-operator)</span><span
class="optional"><span
class="syntactic-cat">[try-operator](Expressions.md#try-operator)</span>~opt~</span><span
class="syntactic-cat">[prefix-expression](Expressions.md#prefix-expression)</span>

[‌](){#TP40016643-CH32-NoLink_406} <span class="syntax-def-name">
binary-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[conditional-operator](Expressions.md#conditional-operator)</span><span
class="optional"><span
class="syntactic-cat">[try-operator](Expressions.md#try-operator)</span>~opt~</span><span
class="syntactic-cat">[prefix-expression](Expressions.md#prefix-expression)</span>

[‌](){#TP40016643-CH32-NoLink_407} <span class="syntax-def-name">
binary-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[type-casting-operator](Expressions.md#type-casting-operator)</span>

[‌](){#binary-expressions} <span class="syntax-def-name">
binary-expressions </span> <span class="arrow"> → </span><span
class="syntactic-cat">[binary-expression](Expressions.md#binary-expression)</span><span
class="optional"><span
class="syntactic-cat">[binary-expressions](Expressions.md#binary-expressions)</span>~opt~</span>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH32-ID386}
### Assignment Operator {#assignment-operator .section-name}

The *assignment operator* sets a new value for a given expression. It
has the following form:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    expression = value
    ```

</div>

The value of the *expression* is set to the value obtained by evaluating
the *value*. If the *expression* is a tuple, the *value* must be a tuple
with the same number of elements. (Nested tuples are allowed.)
Assignment is performed from each part of the *value* to the
corresponding part of the *expression*. For example:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `(a`{.code-voice}, `_`{.kt}, (`b`{.vc}, `c`{.vc})) = (`"test"`{.s},
    `9.45`{.m}, (`12`{.m}, `3`{.m}))
2.  `// a is "test", b is 12, c is 3, and 9.45 is ignored`{.code-voice}

</div>

</div>

</div>

The assignment operator does not return any value.

<div class="syntax-defs">

Grammar of an assignment operator

<div class="syntax-defs-group">

[‌](){#assignment-operator} <span class="syntax-def-name">
assignment-operator </span> <span class="arrow"> → </span>`=`{.literal}

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH32-ID387}
### Ternary Conditional Operator {#ternary-conditional-operator .section-name}

The *ternary conditional operator* evaluates to one of two given values
based on the value of a condition. It has the following form:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    condition ? expression used if true : expression used if false
    ```

</div>

If the *condition* evaluates to `true`{.code-voice}, the conditional
operator evaluates the first expression and returns its value.
Otherwise, it evaluates the second expression and returns its value. The
unused expression is not evaluated.

For an example that uses the ternary conditional operator, see [Ternary
Conditional Operator](BasicOperators.md#TP40016643-CH6-ID71).

<div class="syntax-defs">

Grammar of a conditional operator

<div class="syntax-defs-group">

[‌](){#conditional-operator} <span class="syntax-def-name">
conditional-operator </span> <span class="arrow"> →
</span>`?`{.literal}<span class="optional"><span
class="syntactic-cat">[try-operator](Expressions.md#try-operator)</span>~opt~</span><span
class="syntactic-cat">[expression](Expressions.md#expression)</span>`:`{.literal}

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH32-ID388}
### Type-Casting Operators {#type-casting-operators .section-name}

There are four type-casting operators: the `is`{.code-voice} operator,
the `as`{.code-voice} operator, the `as?`{.code-voice} operator, and the
`as!`{.code-voice} operator.

They have the following form:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    expression is type
    ```

-   ``` {.code-voice}
    expression as type
    ```

-   ``` {.code-voice}
    expression as? type
    ```

-   ``` {.code-voice}
    expression as! type
    ```

</div>

The `is`{.code-voice} operator checks at runtime whether the
*expression* can be cast to the specified *type*. It returns
`true`{.code-voice} if the *expression* can be cast to the specified
*type*; otherwise, it returns `false`{.code-voice}.

The `as`{.code-voice} operator performs a cast when it is known at
compile time that the cast always succeeds, such as upcasting or
bridging. Upcasting lets you use an expression as an instance of its
type’s supertype, without using an intermediate variable. The following
approaches are equivalent:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `f`{.vc}(`any`{.vc}: `Any`{.n}) {
    `print`{.vc}(`"Function for Any"`{.s}) }
2.  `func`{.code-voice} `f`{.vc}(`int`{.vc}: `Int`{.n}) {
    `print`{.vc}(`"Function for Int"`{.s}) }
3.  `let`{.code-voice} `x`{.vc} = `10`{.m}
4.  `f`{.code-voice}(`x`{.vc})
5.  `// prints "Function for Int"`{.code-voice}
6.  ` `{.code-voice}
7.  `let`{.code-voice} `y`{.vc}: `Any`{.n} = `x`{.vc}
8.  `f`{.code-voice}(`y`{.vc})
9.  `// prints "Function for Any"`{.code-voice}
10. ` `{.code-voice}
11. `f`{.code-voice}(`x`{.vc} `as`{.kt} `Any`{.n})
12. `// prints "Function for Any"`{.code-voice}

</div>

</div>

</div>

Bridging lets you use an expression of a Swift standard library type
such as `String`{.code-voice} as its corresponding Foundation type such
as `NSString`{.code-voice} without needing to create a new instance. For
more information on bridging, see Working with Cocoa Data Types in
*Using Swift with Cocoa and Objective-C (Swift 2.1)*.

The `as?`{.code-voice} operator performs a conditional cast of the
*expression* to the specified *type*. The `as?`{.code-voice} operator
returns an optional of the specified *type*. At runtime, if the cast
succeeds, the value of *expression* is wrapped in an optional and
returned; otherwise, the value returned is `nil`{.code-voice}. If
casting to the specified *type* is guaranteed to fail or is guaranteed
to succeed, a compile-time error is raised.

The `as!`{.code-voice} operator performs a forced cast of the
*expression* to the specified *type*. The `as!`{.code-voice} operator
returns a value of the specified *type*, not an optional type. If the
cast fails, a runtime error is raised. The behavior of
`x as! T`{.code-voice} is the same as the behavior of
`(x as? T)!`{.code-voice}.

For more information about type casting and to see examples that use the
type-casting operators, see [Type Casting](TypeCasting.md).

<div class="syntax-defs">

Grammar of a type-casting operator

<div class="syntax-defs-group">

[‌](){#type-casting-operator} <span class="syntax-def-name">
type-casting-operator </span> <span class="arrow"> →
</span>`is`{.literal}<span
class="syntactic-cat">[type](Types.md#type)</span>

[‌](){#TP40016643-CH32-NoLink_415} <span class="syntax-def-name">
type-casting-operator </span> <span class="arrow"> →
</span>`as`{.literal}<span
class="syntactic-cat">[type](Types.md#type)</span>

[‌](){#TP40016643-CH32-NoLink_416} <span class="syntax-def-name">
type-casting-operator </span> <span class="arrow"> →
</span>`as`{.literal}`?`{.literal}<span
class="syntactic-cat">[type](Types.md#type)</span>

[‌](){#TP40016643-CH32-NoLink_417} <span class="syntax-def-name">
type-casting-operator </span> <span class="arrow"> →
</span>`as`{.literal}`!`{.literal}<span
class="syntactic-cat">[type](Types.md#type)</span>

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH32-ID389}
### Primary Expressions {#primary-expressions .section-name}

*Primary expressions* are the most basic kind of expression. They can be
used as expressions on their own, and they can be combined with other
tokens to make prefix expressions, binary expressions, and postfix
expressions.

<div class="syntax-defs">

Grammar of a primary expression

<div class="syntax-defs-group">

[‌](){#primary-expression} <span class="syntax-def-name">
primary-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span><span
class="optional"><span
class="syntactic-cat">[generic-argument-clause](GenericParametersAndArguments.md#generic-argument-clause)</span>~opt~</span>

[‌](){#TP40016643-CH32-NoLink_420} <span class="syntax-def-name">
primary-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[literal-expression](Expressions.md#literal-expression)</span>

[‌](){#TP40016643-CH32-NoLink_421} <span class="syntax-def-name">
primary-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[self-expression](Expressions.md#self-expression)</span>

[‌](){#TP40016643-CH32-NoLink_422} <span class="syntax-def-name">
primary-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[superclass-expression](Expressions.md#superclass-expression)</span>

[‌](){#TP40016643-CH32-NoLink_423} <span class="syntax-def-name">
primary-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[closure-expression](Expressions.md#closure-expression)</span>

[‌](){#TP40016643-CH32-NoLink_424} <span class="syntax-def-name">
primary-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[parenthesized-expression](Expressions.md#parenthesized-expression)</span>

[‌](){#TP40016643-CH32-NoLink_425} <span class="syntax-def-name">
primary-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[implicit-member-expression](Expressions.md#implicit-member-expression)</span>

[‌](){#TP40016643-CH32-NoLink_426} <span class="syntax-def-name">
primary-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[wildcard-expression](Expressions.md#wildcard-expression)</span>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH32-ID390}
### Literal Expression {#literal-expression .section-name}

A *literal expression* consists of either an ordinary literal (such as a
string or a number), an array or dictionary literal, or one of the
following special literals:

<div class="tableholder">

+--------------------------+--------------------------+--------------------------+
| Literal                  | Type                     | Value                    |
+==========================+==========================+==========================+
| `__FILE__`{.code-voice}  | `String`{.code-voice}    | The name of the file in  |
|                          |                          | which it appears.        |
+--------------------------+--------------------------+--------------------------+
| `__LINE__`{.code-voice}  | `Int`{.code-voice}       | The line number on which |
|                          |                          | it appears.              |
+--------------------------+--------------------------+--------------------------+
| `__COLUMN__`{.code-voice | `Int`{.code-voice}       | The column number in     |
| }                        |                          | which it begins.         |
+--------------------------+--------------------------+--------------------------+
| `__FUNCTION__`{.code-voi | `String`{.code-voice}    | The name of the          |
| ce}                      |                          | declaration in which it  |
|                          |                          | appears.                 |
+--------------------------+--------------------------+--------------------------+

</div>

Inside a function, the value of `__FUNCTION__`{.code-voice} is the name
of that function, inside a method it is the name of that method, inside
a property getter or setter it is the name of that property, inside
special members like `init`{.code-voice} or `subscript`{.code-voice} it
is the name of that keyword, and at the top level of a file it is the
name of the current module.

When used as the default value of a function or method, the special
literal’s value is determined when the default value expression is
evaluated at the call site.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `logFunctionName`{.vc}(`string`{.vc}:
    `String`{.n} = `__FUNCTION__`{.kt}) {
2.  `    print`{.code-voice}(`string`{.vc})
3.  `}`{.code-voice}
4.  `func`{.code-voice} `myFunction`{.vc}() {
5.  `    logFunctionName`{.code-voice}() `// Prints "myFunction()".`{.c}
6.  `}`{.code-voice}

</div>

</div>

</div>

An *array literal* is an ordered collection of values. It has the
following form:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    [value 1, value 2, ...]
    ```

</div>

The last expression in the array can be followed by an optional comma.
The value of an array literal has type `[T]`{.code-voice}, where
`T`{.code-voice} is the type of the expressions inside it. If there are
expressions of multiple types, `T`{.code-voice} is their closest common
supertype. Empty array literals are written using an empty pair of
square brackets and can be used to create an empty array of a specified
type.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `emptyArray`{.vc}: \[`Double`{.n}\] = \[\]

</div>

</div>

</div>

A *dictionary literal* is an unordered collection of key-value pairs. It
has the following form:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    [key 1: value 1, key 2: value 2, ...]
    ```

</div>

The last expression in the dictionary can be followed by an optional
comma. The value of a dictionary literal has type
`[Key: Value]`{.code-voice}, where `Key`{.code-voice} is the type of its
key expressions and `Value`{.code-voice} is the type of its value
expressions. If there are expressions of multiple types,
`Key`{.code-voice} and `Value`{.code-voice} are the closest common
supertype for their respective values. An empty dictionary literal is
written as a colon inside a pair of brackets (`[:]`{.code-voice}) to
distinguish it from an empty array literal. You can use an empty
dictionary literal to create an empty dictionary literal of specified
key and value types.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `emptyDictionary`{.vc}: \[`String`{.n}:
    `Double`{.n}\] = \[:\]

</div>

</div>

</div>

<div class="syntax-defs">

Grammar of a literal expression

<div class="syntax-defs-group">

[‌](){#literal-expression} <span class="syntax-def-name">
literal-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[literal](LexicalStructure.md#literal)</span>

[‌](){#TP40016643-CH32-NoLink_429} <span class="syntax-def-name">
literal-expression </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[array-literal](Expressions.md#array-literal)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[dictionary-literal](Expressions.md#dictionary-literal)</span>
</span>

[‌](){#TP40016643-CH32-NoLink_430} <span class="syntax-def-name">
literal-expression </span> <span class="arrow"> → </span><span
class="alternative"> `__FILE__`{.literal} </span><span
class="alternative"> `__LINE__`{.literal} </span><span
class="alternative"> `__COLUMN__`{.literal} </span><span
class="alternative"> `__FUNCTION__`{.literal} </span>

</div>

<div class="syntax-defs-group">

[‌](){#array-literal} <span class="syntax-def-name"> array-literal
</span> <span class="arrow"> → </span>`[`{.literal}<span
class="optional"><span
class="syntactic-cat">[array-literal-items](Expressions.md#array-literal-items)</span>~opt~</span>`]`{.literal}

[‌](){#array-literal-items} <span class="syntax-def-name">
array-literal-items </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[array-literal-item](Expressions.md#array-literal-item)</span><span
class="optional">`,`{.literal}~opt~</span> </span><span
class="alternative"> <span
class="syntactic-cat">[array-literal-item](Expressions.md#array-literal-item)</span>`,`{.literal}<span
class="syntactic-cat">[array-literal-items](Expressions.md#array-literal-items)</span>
</span>

[‌](){#array-literal-item} <span class="syntax-def-name">
array-literal-item </span> <span class="arrow"> → </span><span
class="syntactic-cat">[expression](Expressions.md#expression)</span>

</div>

<div class="syntax-defs-group">

[‌](){#dictionary-literal} <span class="syntax-def-name">
dictionary-literal </span> <span class="arrow"> → </span><span
class="alternative"> `[`{.literal}<span
class="syntactic-cat">[dictionary-literal-items](Expressions.md#dictionary-literal-items)</span>`]`{.literal}
</span><span class="alternative">
`[`{.literal}`:`{.literal}`]`{.literal} </span>

[‌](){#dictionary-literal-items} <span class="syntax-def-name">
dictionary-literal-items </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[dictionary-literal-item](Expressions.md#dictionary-literal-item)</span><span
class="optional">`,`{.literal}~opt~</span> </span><span
class="alternative"> <span
class="syntactic-cat">[dictionary-literal-item](Expressions.md#dictionary-literal-item)</span>`,`{.literal}<span
class="syntactic-cat">[dictionary-literal-items](Expressions.md#dictionary-literal-items)</span>
</span>

[‌](){#dictionary-literal-item} <span class="syntax-def-name">
dictionary-literal-item </span> <span class="arrow"> → </span><span
class="syntactic-cat">[expression](Expressions.md#expression)</span>`:`{.literal}<span
class="syntactic-cat">[expression](Expressions.md#expression)</span>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH32-ID391}
### Self Expression {#self-expression .section-name}

The `self`{.code-voice} expression is an explicit reference to the
current type or instance of the type in which it occurs. It has the
following forms:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    self
    ```

-   ``` {.code-voice}
    self.member name
    ```

-   ``` {.code-voice}
    self[subscript index]
    ```

-   ``` {.code-voice}
    self(initializer arguments)
    ```

-   ``` {.code-voice}
    self.init(initializer arguments)
    ```

</div>

In an initializer, subscript, or instance method, `self`{.code-voice}
refers to the current instance of the type in which it occurs. In a type
method, `self`{.code-voice} refers to the current type in which it
occurs.

The `self`{.code-voice} expression is used to specify scope when
accessing members, providing disambiguation when there is another
variable of the same name in scope, such as a function parameter. For
example:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `class`{.code-voice} `SomeClass`{.vc} {
2.  `    var`{.code-voice} `greeting`{.vc}: `String`{.n}
3.  `    init`{.code-voice}(`greeting`{.vc}: `String`{.n}) {
4.  `        self`{.code-voice}.`greeting`{.vc} = `greeting`{.vc}
5.  `    }`{.code-voice}
6.  `}`{.code-voice}

</div>

</div>

</div>

In a mutating method of a value type, you can assign a new instance of
that value type to `self`{.code-voice}. For example:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `struct`{.code-voice} `Point`{.vc} {
2.  `    var`{.code-voice} `x`{.vc} = `0.0`{.m}, `y`{.vc} = `0.0`{.m}
3.  `    mutating`{.code-voice} `func`{.kt}
    `moveByX`{.vc}(`deltaX`{.vc}: `Double`{.n}, `y`{.vc} `deltaY`{.vc}:
    `Double`{.n}) {
4.  `        self`{.code-voice} = `Point`{.vc}(`x`{.vc}: `x`{.vc} +
    `deltaX`{.vc}, `y`{.vc}: `y`{.vc} + `deltaY`{.vc})
5.  `    }`{.code-voice}
6.  `}`{.code-voice}

</div>

</div>

</div>

<div class="syntax-defs">

Grammar of a self expression

<div class="syntax-defs-group">

[‌](){#self-expression} <span class="syntax-def-name"> self-expression
</span> <span class="arrow"> → </span><span class="alternative">
`self`{.literal} </span><span class="alternative"> <span
class="syntactic-cat">[self-method-expression](Expressions.md#self-method-expression)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[self-subscript-expression](Expressions.md#self-subscript-expression)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[self-initializer-expression](Expressions.md#self-initializer-expression)</span>
</span>

</div>

<div class="syntax-defs-group">

[‌](){#self-method-expression} <span class="syntax-def-name">
self-method-expression </span> <span class="arrow"> →
</span>`self`{.literal}`.`{.literal}<span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

[‌](){#self-subscript-expression} <span class="syntax-def-name">
self-subscript-expression </span> <span class="arrow"> →
</span>`self`{.literal}`[`{.literal}<span
class="syntactic-cat">[expression-list](Expressions.md#expression-list)</span>`]`{.literal}

[‌](){#self-initializer-expression} <span class="syntax-def-name">
self-initializer-expression </span> <span class="arrow"> →
</span>`self`{.literal}`.`{.literal}`init`{.literal}

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH32-ID392}
### Superclass Expression {#superclass-expression .section-name}

A *superclass expression* lets a class interact with its superclass. It
has one of the following forms:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    super.member name
    ```

-   ``` {.code-voice}
    super[subscript index]
    ```

-   ``` {.code-voice}
    super.init(initializer arguments)
    ```

</div>

The first form is used to access a member of the superclass. The second
form is used to access the superclass’s subscript implementation. The
third form is used to access an initializer of the superclass.

Subclasses can use a superclass expression in their implementation of
members, subscripting, and initializers to make use of the
implementation in their superclass.

<div class="syntax-defs">

Grammar of a superclass expression

<div class="syntax-defs-group">

[‌](){#superclass-expression} <span class="syntax-def-name">
superclass-expression </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[superclass-method-expression](Expressions.md#superclass-method-expression)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[superclass-subscript-expression](Expressions.md#superclass-subscript-expression)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[superclass-initializer-expression](Expressions.md#superclass-initializer-expression)</span>
</span>

</div>

<div class="syntax-defs-group">

[‌](){#superclass-method-expression} <span class="syntax-def-name">
superclass-method-expression </span> <span class="arrow"> →
</span>`super`{.literal}`.`{.literal}<span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

[‌](){#superclass-subscript-expression} <span class="syntax-def-name">
superclass-subscript-expression </span> <span class="arrow"> →
</span>`super`{.literal}`[`{.literal}<span
class="syntactic-cat">[expression-list](Expressions.md#expression-list)</span>`]`{.literal}

[‌](){#superclass-initializer-expression} <span class="syntax-def-name">
superclass-initializer-expression </span> <span class="arrow"> →
</span>`super`{.literal}`.`{.literal}`init`{.literal}

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH32-ID393}
### Closure Expression {#closure-expression .section-name}

A *closure expression* creates a closure, also known as a *lambda* or an
*anonymous function* in other programming languages. Like a function
declaration, a closure contains statements which it executes, and it
captures constants and variables from its enclosing scope. It has the
following form:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    { (parameters) -> return type in
    ```

-   ``` {.code-voice}
        statements
    ```

-   ``` {.code-voice}
    }
    ```

</div>

The *parameters* have the same form as the parameters in a function
declaration, as described in [Function
Declaration](Declarations.md#TP40016643-CH34-ID362).

There are several special forms that allow closures to be written more
concisely:

-   A closure can omit the types of its parameters, its return type,
    or both. If you omit the parameter names and both types, omit the
    `in`{.code-voice} keyword before the statements. If the omitted
    types can’t be inferred, a compile-time error is raised.

-   A closure may omit names for its parameters. Its parameters are then
    implicitly named `$`{.code-voice} followed by their position:
    `$0`{.code-voice}, `$1`{.code-voice}, `$2`{.code-voice}, and so on.

-   A closure that consists of only a single expression is understood to
    return the value of that expression. The contents of this expression
    are also considered when performing type inference on the
    surrounding expression.

The following closure expressions are equivalent:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `myFunction`{.code-voice} {
2.  `    (x`{.code-voice}: `Int`{.n}, `y`{.vc}: `Int`{.n}) -&gt;
    `Int`{.n} `in`{.kt}
3.  `    return`{.code-voice} `x`{.vc} + `y`{.vc}
4.  `}`{.code-voice}
5.  ` `{.code-voice}
6.  `myFunction`{.code-voice} {
7.  `    (x`{.code-voice}, `y`{.vc}) `in`{.kt}
8.  `    return`{.code-voice} `x`{.vc} + `y`{.vc}
9.  `}`{.code-voice}
10. ` `{.code-voice}
11. `myFunction`{.code-voice} { `return`{.kt} `$0`{.vc} + `$1`{.vc} }
12. ` `{.code-voice}
13. `myFunction`{.code-voice} { `$0`{.vc} + `$1`{.vc} }

</div>

</div>

</div>

For information about passing a closure as an argument to a function,
see [Function Call Expression](Expressions.md#TP40016643-CH32-ID398).

<div class="section section">

[‌](){#TP40016643-CH32-ID544}
### Capture Lists {#capture-lists .section-name}

By default, a closure expression captures constants and variables from
its surrounding scope with strong references to those values. You can
use a *capture list* to explicitly control how values are captured in a
closure.

A capture list is written as a comma separated list of expressions
surrounded by square brackets, before the list of parameters. If you use
a capture list, you must also use the `in`{.code-voice} keyword, even if
you omit the parameter names, parameter types, and return type.

The entries in the capture list are initialized when the closure is
created. For each entry in the capture list, a constant is initialized
to the value of the constant or variable that has the same name in the
surrounding scope. For example in the code below, `a`{.code-voice} is
included in the capture list but `b`{.code-voice} is not, which gives
them different behavior.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `a`{.vc} = `0`{.m}
2.  `var`{.code-voice} `b`{.vc} = `0`{.m}
3.  `let`{.code-voice} `closure`{.vc} = { \[`a`{.vc}\] `in`{.kt}
4.  `    print`{.code-voice}(`a`{.vc}, `b`{.vc})
5.  `}`{.code-voice}
6.  ` `{.code-voice}
7.  `a`{.code-voice} = `10`{.m}
8.  `b`{.code-voice} = `10`{.m}
9.  `closure`{.code-voice}()
10. `// prints "0 10"`{.code-voice}

</div>

</div>

</div>

There are two different things named `a`{.code-voice}, the variable in
the surrounding scope and the constant in the closure’s scope, but only
one variable named `b`{.code-voice}. The `a`{.code-voice} in the inner
scope is initialized with the value of the `a`{.code-voice} in the outer
scope when the closure is created, but their values are not connected in
any special way. This means that a change to the value of
`a`{.code-voice} in the outer scope does not effect the value of
`a`{.code-voice} in the inner scope, nor does a change to
`a`{.code-voice} inside the closure effect the value of `a`{.code-voice}
outside the closure. In contrast, there is only one variable named
`b`{.code-voice}—the `b`{.code-voice} in the outer scope—so changes from
inside or outside the closure are visible in both places.

This distinction is not visible when the captured variable’s type has
reference semantics. For example, there are two things named
`x`{.code-voice} in the code below, a variable in the outer scope and a
constant in the inner scope, but they both refer to the same object
because of reference semantics.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `class`{.code-voice} `SimpleClass`{.vc} {
2.  `    var`{.code-voice} `value`{.vc}: `Int`{.n} = `0`{.m}
3.  `}`{.code-voice}
4.  `var`{.code-voice} `x`{.vc} = `SimpleClass`{.vc}()
5.  `var`{.code-voice} `y`{.vc} = `SimpleClass`{.vc}()
6.  `let`{.code-voice} `closure`{.vc} = { \[`x`{.vc}\] `in`{.kt}
7.  `    print`{.code-voice}(`x`{.vc}.`value`{.vc},
    `y`{.vc}.`value`{.vc})
8.  `}`{.code-voice}
9.  ` `{.code-voice}
10. `x`{.code-voice}.`value`{.vc} = `10`{.m}
11. `y`{.code-voice}.`value`{.vc} = `10`{.m}
12. `closure`{.code-voice}()
13. `// prints "10 10"`{.code-voice}

</div>

</div>

</div>

If the type of the expression’s value is a class, you can mark the
expression in a capture list with `weak`{.code-voice} or
`unowned`{.code-voice} to capture a weak or unowned reference to the
expression’s value.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `myFunction`{.code-voice} { `print`{.vc}(`self`{.kt}.`title`{.vc}) }
    `// strong capture`{.c}
2.  `myFunction`{.code-voice} { \[`weak`{.vc} `self`{.kt}\] `in`{.kt}
    `print`{.vc}(`self`{.kt}!.`title`{.vc}) } `// weak capture`{.c}
3.  `myFunction`{.code-voice} { \[`unowned`{.vc} `self`{.kt}\] `in`{.kt}
    `print`{.vc}(`self`{.kt}.`title`{.vc}) } `// unowned capture`{.c}

</div>

</div>

</div>

You can also bind an arbitrary expression to a named value in a capture
list. The expression is evaluated when the closure is created, and the
value is captured with the specified strength. For example:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `// Weak capture of "self.parent" as "parent"`{.code-voice}
2.  `myFunction`{.code-voice} { \[`weak`{.vc} `parent`{.vc} =
    `self`{.kt}.`parent`{.vc}\] `in`{.kt}
    `print`{.vc}(`parent`{.vc}!.`title`{.vc}) }

</div>

</div>

</div>

For more information and examples of closure expressions, see [Closure
Expressions](Closures.md#TP40016643-CH11-ID95). For more information
and examples of capture lists, see [Resolving Strong Reference Cycles
for Closures](AutomaticReferenceCounting.md#TP40016643-CH20-ID57).

<div class="syntax-defs">

Grammar of a closure expression

<div class="syntax-defs-group">

[‌](){#closure-expression} <span class="syntax-def-name">
closure-expression </span> <span class="arrow"> →
</span>`{`{.literal}<span class="optional"><span
class="syntactic-cat">[closure-signature](Expressions.md#closure-signature)</span>~opt~</span><span
class="syntactic-cat">[statements](Statements.md#statements)</span>`}`{.literal}

</div>

<div class="syntax-defs-group">

[‌](){#closure-signature} <span class="syntax-def-name">
closure-signature </span> <span class="arrow"> → </span><span
class="syntactic-cat">[parameter-clause](Declarations.md#parameter-clause)</span><span
class="optional"><span
class="syntactic-cat">[function-result](Declarations.md#function-result)</span>~opt~</span>`in`{.literal}

[‌](){#TP40016643-CH32-NoLink_450} <span class="syntax-def-name">
closure-signature </span> <span class="arrow"> → </span><span
class="syntactic-cat">[identifier-list](LexicalStructure.md#identifier-list)</span><span
class="optional"><span
class="syntactic-cat">[function-result](Declarations.md#function-result)</span>~opt~</span>`in`{.literal}

[‌](){#TP40016643-CH32-NoLink_451} <span class="syntax-def-name">
closure-signature </span> <span class="arrow"> → </span><span
class="syntactic-cat">[capture-list](Expressions.md#capture-list)</span><span
class="syntactic-cat">[parameter-clause](Declarations.md#parameter-clause)</span><span
class="optional"><span
class="syntactic-cat">[function-result](Declarations.md#function-result)</span>~opt~</span>`in`{.literal}

[‌](){#TP40016643-CH32-NoLink_452} <span class="syntax-def-name">
closure-signature </span> <span class="arrow"> → </span><span
class="syntactic-cat">[capture-list](Expressions.md#capture-list)</span><span
class="syntactic-cat">[identifier-list](LexicalStructure.md#identifier-list)</span><span
class="optional"><span
class="syntactic-cat">[function-result](Declarations.md#function-result)</span>~opt~</span>`in`{.literal}

[‌](){#TP40016643-CH32-NoLink_453} <span class="syntax-def-name">
closure-signature </span> <span class="arrow"> → </span><span
class="syntactic-cat">[capture-list](Expressions.md#capture-list)</span>`in`{.literal}

</div>

<div class="syntax-defs-group">

[‌](){#capture-list} <span class="syntax-def-name"> capture-list </span>
<span class="arrow"> → </span>`[`{.literal}<span
class="syntactic-cat">[capture-list-items](Expressions.md#capture-list-items)</span>`]`{.literal}

[‌](){#capture-list-items} <span class="syntax-def-name">
capture-list-items </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[capture-list-item](Expressions.md#capture-list-item)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[capture-list-item](Expressions.md#capture-list-item)</span>`,`{.literal}<span
class="syntactic-cat">[capture-list-items](Expressions.md#capture-list-items)</span>
</span>

[‌](){#capture-list-item} <span class="syntax-def-name">
capture-list-item </span> <span class="arrow"> → </span><span
class="optional"><span
class="syntactic-cat">[capture-specifier](Expressions.md#capture-specifier)</span>~opt~</span><span
class="syntactic-cat">[expression](Expressions.md#expression)</span>

[‌](){#capture-specifier} <span class="syntax-def-name">
capture-specifier </span> <span class="arrow"> → </span><span
class="alternative"> `weak`{.literal} </span><span class="alternative">
`unowned`{.literal} </span><span class="alternative">
`unowned(safe)`{.literal} </span><span class="alternative">
`unowned(unsafe)`{.literal} </span>

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH32-ID394}
### Implicit Member Expression {#implicit-member-expression .section-name}

An *implicit member expression* is an abbreviated way to access a member
of a type, such as an enumeration case or a type method, in a context
where type inference can determine the implied type. It has the
following form:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    .member name
    ```

</div>

For example:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `x`{.vc} = `MyEnumeration`{.vc}.`SomeValue`{.vc}
2.  `x`{.code-voice} = .`AnotherValue`{.vc}

</div>

</div>

</div>

<div class="syntax-defs">

Grammar of a implicit member expression

<div class="syntax-defs-group">

[‌](){#implicit-member-expression} <span class="syntax-def-name">
implicit-member-expression </span> <span class="arrow"> →
</span>`.`{.literal}<span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH32-ID395}
### Parenthesized Expression {#parenthesized-expression .section-name}

A *parenthesized expression* consists of a comma-separated list of
expressions surrounded by parentheses. Each expression can have an
optional identifier before it, separated by a colon (`:`{.code-voice}).
It has the following form:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    (identifier 1: expression 1, identifier 2: expression 2, ...)
    ```

</div>

Use parenthesized expressions to create tuples and to pass arguments to
a function call. If there is only one value inside the parenthesized
expression, the type of the parenthesized expression is the type of that
value. For example, the type of the parenthesized expression
`(1)`{.code-voice} is `Int`{.code-voice}, not `(Int)`{.code-voice}.

<div class="syntax-defs">

Grammar of a parenthesized expression

<div class="syntax-defs-group">

[‌](){#parenthesized-expression} <span class="syntax-def-name">
parenthesized-expression </span> <span class="arrow"> →
</span>`(`{.literal}<span class="optional"><span
class="syntactic-cat">[expression-element-list](Expressions.md#expression-element-list)</span>~opt~</span>`)`{.literal}

[‌](){#expression-element-list} <span class="syntax-def-name">
expression-element-list </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[expression-element](Expressions.md#expression-element)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[expression-element](Expressions.md#expression-element)</span>`,`{.literal}<span
class="syntactic-cat">[expression-element-list](Expressions.md#expression-element-list)</span>
</span>

[‌](){#expression-element} <span class="syntax-def-name">
expression-element </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[expression](Expressions.md#expression)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>`:`{.literal}<span
class="syntactic-cat">[expression](Expressions.md#expression)</span>
</span>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH32-ID396}
### Wildcard Expression {#wildcard-expression .section-name}

A *wildcard expression* is used to explicitly ignore a value during an
assignment. For example, in the following assignment 10 is assigned to
`x`{.code-voice} and 20 is ignored:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `(x`{.code-voice}, `_`{.kt}) = (`10`{.m}, `20`{.m})
2.  `// x is 10, and 20 is ignored`{.code-voice}

</div>

</div>

</div>

<div class="syntax-defs">

Grammar of a wildcard expression

<div class="syntax-defs-group">

[‌](){#wildcard-expression} <span class="syntax-def-name">
wildcard-expression </span> <span class="arrow"> → </span>`_`{.literal}

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH32-ID397}
### Postfix Expressions {#postfix-expressions .section-name}

*Postfix expressions* are formed by applying a postfix operator or other
postfix syntax to an expression. Syntactically, every primary expression
is also a postfix expression.

For information about the behavior of these operators, see [Basic
Operators](BasicOperators.md) and [Advanced
Operators](AdvancedOperators.md).

For information about the operators provided by the Swift standard
library, see *Swift Standard Library Operators Reference*.

<div class="syntax-defs">

Grammar of a postfix expression

<div class="syntax-defs-group">

[‌](){#postfix-expression} <span class="syntax-def-name">
postfix-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[primary-expression](Expressions.md#primary-expression)</span>

[‌](){#TP40016643-CH32-NoLink_468} <span class="syntax-def-name">
postfix-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span><span
class="syntactic-cat">[postfix-operator](LexicalStructure.md#postfix-operator)</span>

[‌](){#TP40016643-CH32-NoLink_469} <span class="syntax-def-name">
postfix-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[function-call-expression](Expressions.md#function-call-expression)</span>

[‌](){#TP40016643-CH32-NoLink_470} <span class="syntax-def-name">
postfix-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[initializer-expression](Expressions.md#initializer-expression)</span>

[‌](){#TP40016643-CH32-NoLink_471} <span class="syntax-def-name">
postfix-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[explicit-member-expression](Expressions.md#explicit-member-expression)</span>

[‌](){#TP40016643-CH32-NoLink_472} <span class="syntax-def-name">
postfix-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[postfix-self-expression](Expressions.md#postfix-self-expression)</span>

[‌](){#TP40016643-CH32-NoLink_473} <span class="syntax-def-name">
postfix-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[dynamic-type-expression](Expressions.md#dynamic-type-expression)</span>

[‌](){#TP40016643-CH32-NoLink_474} <span class="syntax-def-name">
postfix-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[subscript-expression](Expressions.md#subscript-expression)</span>

[‌](){#TP40016643-CH32-NoLink_475} <span class="syntax-def-name">
postfix-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[forced-value-expression](Expressions.md#forced-value-expression)</span>

[‌](){#TP40016643-CH32-NoLink_476} <span class="syntax-def-name">
postfix-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[optional-chaining-expression](Expressions.md#optional-chaining-expression)</span>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH32-ID398}
### Function Call Expression {#function-call-expression .section-name}

A *function call expression* consists of a function name followed by a
comma-separated list of the function’s arguments in parentheses.
Function call expressions have the following form:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    function name(argument value 1, argument value 2)
    ```

</div>

The *function name* can be any expression whose value is of a function
type.

If the function definition includes names for its parameters, the
function call must include names before its argument values separated by
a colon (`:`{.code-voice}). This kind of function call expression has
the following form:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    function name(argument name 1: argument value 1, argument name 2: argument value 2)
    ```

</div>

A function call expression can include a trailing closure in the form of
a closure expression immediately after the closing parenthesis. The
trailing closure is understood as an argument to the function, added
after the last parenthesized argument. The following function calls are
equivalent:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `// someFunction takes an integer and a closure as its arguments`{.code-voice}
2.  `someFunction`{.code-voice}(`x`{.vc}, `f`{.vc}: {`$0`{.vc} ==
    `13`{.m}})
3.  `someFunction`{.code-voice}(`x`{.vc}) {`$0`{.vc} == `13`{.m}}

</div>

</div>

</div>

If the trailing closure is the function’s only argument, the parentheses
can be omitted.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `// someFunction takes a closure as its only argument`{.code-voice}
2.  `myData`{.code-voice}.`someMethod`{.vc}() {`$0`{.vc} == `13`{.m}}
3.  `myData`{.code-voice}.`someMethod`{.vc} {`$0`{.vc} == `13`{.m}}

</div>

</div>

</div>

<div class="syntax-defs">

Grammar of a function call expression

<div class="syntax-defs-group">

[‌](){#function-call-expression} <span class="syntax-def-name">
function-call-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span><span
class="syntactic-cat">[parenthesized-expression](Expressions.md#parenthesized-expression)</span>

[‌](){#TP40016643-CH32-NoLink_479} <span class="syntax-def-name">
function-call-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span><span
class="optional"><span
class="syntactic-cat">[parenthesized-expression](Expressions.md#parenthesized-expression)</span>~opt~</span><span
class="syntactic-cat">[trailing-closure](Expressions.md#trailing-closure)</span>

[‌](){#trailing-closure} <span class="syntax-def-name"> trailing-closure
</span> <span class="arrow"> → </span><span
class="syntactic-cat">[closure-expression](Expressions.md#closure-expression)</span>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH32-ID399}
### Initializer Expression {#initializer-expression .section-name}

An *initializer expression* provides access to a type’s initializer. It
has the following form:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    expression.init(initializer arguments)
    ```

</div>

You use the initializer expression in a function call expression to
initialize a new instance of a type. You also use an initializer
expression to delegate to the initializer of a superclass.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `class`{.code-voice} `SomeSubClass`{.vc}: `SomeSuperClass`{.n} {
2.  `    override`{.code-voice} `init`{.kt}() {
3.  `        // subclass initialization goes here`{.code-voice}
4.  `        super`{.code-voice}.`init`{.kt}()
5.  `    }`{.code-voice}
6.  `}`{.code-voice}

</div>

</div>

</div>

Like a function, an initializer can be used as a value. For example:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `// Type annotation is required because String has multiple initializers.`{.code-voice}
2.  `let`{.code-voice} `initializer`{.vc}: `Int`{.n} -&gt; `String`{.n}
    = `String`{.vc}.`init`{.kt}
3.  `let`{.code-voice} `oneTwoThree`{.vc} = \[`1`{.m}, `2`{.m},
    `3`{.m}\].`map`{.vc}(`initializer`{.vc}).`reduce`{.vc}(`""`{.s},
    `combine`{.vc}: +)
4.  `print`{.code-voice}(`oneTwoThree`{.vc})
5.  `// prints "123"`{.code-voice}

</div>

</div>

</div>

If you specify a type by name, you can access the type’s initializer
without using an initializer expression. In all other cases, you must
use an initializer expression.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `s1`{.vc} =
    `SomeType`{.vc}.`init`{.kt}(`data`{.vc}: `3`{.m}) `// Valid`{.c}
2.  `let`{.code-voice} `s2`{.vc} = `SomeType`{.vc}(`data`{.vc}: `1`{.m})
    `// Also valid`{.c}
3.  ` `{.code-voice}
4.  `let`{.code-voice} `s4`{.vc} =
    `someValue`{.vc}.`dynamicType`{.kt}(`data`{.vc}: `5`{.m})
    `// Error`{.c}
5.  `let`{.code-voice} `s3`{.vc} =
    `someValue`{.vc}.`dynamicType`{.kt}.`init`{.kt}(`data`{.vc}:
    `7`{.m}) `// Valid`{.c}

</div>

</div>

</div>

<div class="syntax-defs">

Grammar of an initializer expression

<div class="syntax-defs-group">

[‌](){#initializer-expression} <span class="syntax-def-name">
initializer-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span>`.`{.literal}`init`{.literal}

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH32-ID400}
### Explicit Member Expression {#explicit-member-expression .section-name}

An *explicit member expression* allows access to the members of a named
type, a tuple, or a module. It consists of a period (`.`{.code-voice})
between the item and the identifier of its member.

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    expression.member name
    ```

</div>

The members of a named type are named as part of the type’s declaration
or extension. For example:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `class`{.code-voice} `SomeClass`{.vc} {
2.  `    var`{.code-voice} `someProperty`{.vc} = `42`{.m}
3.  `}`{.code-voice}
4.  `let`{.code-voice} `c`{.vc} = `SomeClass`{.vc}()
5.  `let`{.code-voice} `y`{.vc} = `c`{.vc}.`someProperty`{.vc}
    `// Member access`{.c}

</div>

</div>

</div>

The members of a tuple are implicitly named using integers in the order
they appear, starting from zero. For example:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `t`{.vc} = (`10`{.m}, `20`{.m}, `30`{.m})
2.  `t`{.code-voice}.`0`{.m} = `t`{.vc}.`1`{.m}
3.  `// Now t is (20, 20, 30)`{.code-voice}

</div>

</div>

</div>

The members of a module access the top-level declarations of that
module.

If a period appears at the beginning of a line, it is understood as part
of an explicit member expression, not as an implicit member expression.
For example, the following listing shows chained method calls split over
several lines:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `x`{.vc} = \[`10`{.m}, `3`{.m}, `20`{.m},
    `15`{.m}, `4`{.m}\]
2.  `    .sort`{.code-voice}()
3.  `    .filter`{.code-voice} { `$0`{.vc} &gt; `5`{.m} }
4.  `    .map`{.code-voice} { `$0`{.vc} \* `100`{.m} }

</div>

</div>

</div>

<div class="syntax-defs">

Grammar of an explicit member expression

<div class="syntax-defs-group">

[‌](){#explicit-member-expression} <span class="syntax-def-name">
explicit-member-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span>`.`{.literal}<span
class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)</span>

[‌](){#TP40016643-CH32-NoLink_485} <span class="syntax-def-name">
explicit-member-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span>`.`{.literal}<span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span><span
class="optional"><span
class="syntactic-cat">[generic-argument-clause](GenericParametersAndArguments.md#generic-argument-clause)</span>~opt~</span>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH32-ID401}
### Postfix Self Expression {#postfix-self-expression .section-name}

A postfix `self`{.code-voice} expression consists of an expression or
the name of a type, immediately followed by `.self`{.code-voice}. It has
the following forms:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    expression.self
    ```

-   ``` {.code-voice}
    type.self
    ```

</div>

The first form evaluates to the value of the *expression*. For example,
`x.self`{.code-voice} evaluates to `x`{.code-voice}.

The second form evaluates to the value of the *type*. Use this form to
access a type as a value. For example, because
`SomeClass.self`{.code-voice} evaluates to the `SomeClass`{.code-voice}
type itself, you can pass it to a function or method that accepts a
type-level argument.

<div class="syntax-defs">

Grammar of a self expression

<div class="syntax-defs-group">

[‌](){#postfix-self-expression} <span class="syntax-def-name">
postfix-self-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span>`.`{.literal}`self`{.literal}

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH32-ID402}
### Dynamic Type Expression {#dynamic-type-expression .section-name}

A `dynamicType`{.code-voice} expression consists of an expression,
immediately followed by `.dynamicType`{.code-voice}. It has the
following form:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    expression.dynamicType
    ```

</div>

The *expression* can’t be the name of a type. The entire
`dynamicType`{.code-voice} expression evaluates to the value of the
runtime type of the *expression*, as the following example shows:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `class`{.code-voice} `SomeBaseClass`{.vc} {
2.  `    class`{.code-voice} `func`{.kt} `printClassName`{.vc}() {
3.  `        print`{.code-voice}(`"SomeBaseClass"`{.s})
4.  `    }`{.code-voice}
5.  `}`{.code-voice}
6.  `class`{.code-voice} `SomeSubClass`{.vc}: `SomeBaseClass`{.n} {
7.  `    override`{.code-voice} `class`{.kt} `func`{.kt}
    `printClassName`{.vc}() {
8.  `        print`{.code-voice}(`"SomeSubClass"`{.s})
9.  `    }`{.code-voice}
10. `}`{.code-voice}
11. `let`{.code-voice} `someInstance`{.vc}: `SomeBaseClass`{.n} =
    `SomeSubClass`{.vc}()
12. `// someInstance has a static type of SomeBaseClass at compile time, and`{.code-voice}
13. `// it has a dynamc type of SomeSubClass at runtime`{.code-voice}
14. `someInstance`{.code-voice}.`dynamicType`{.kt}.`printClassName`{.vc}()
15. `// prints "SomeSubClass"`{.code-voice}

</div>

</div>

</div>

<div class="syntax-defs">

Grammar of a dynamic type expression

<div class="syntax-defs-group">

[‌](){#dynamic-type-expression} <span class="syntax-def-name">
dynamic-type-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span>`.`{.literal}`dynamicType`{.literal}

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH32-ID403}
### Subscript Expression {#subscript-expression .section-name}

A *subscript expression* provides subscript access using the getter and
setter of the corresponding subscript declaration. It has the following
form:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    expression[index expressions]
    ```

</div>

To evaluate the value of a subscript expression, the subscript getter
for the *expression*’s type is called with the *index expressions*
passed as the subscript parameters. To set its value, the subscript
setter is called in the same way.

For information about subscript declarations, see [Protocol Subscript
Declaration](Declarations.md#TP40016643-CH34-ID373).

<div class="syntax-defs">

Grammar of a subscript expression

<div class="syntax-defs-group">

[‌](){#subscript-expression} <span class="syntax-def-name">
subscript-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span>`[`{.literal}<span
class="syntactic-cat">[expression-list](Expressions.md#expression-list)</span>`]`{.literal}

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH32-ID404}
### Forced-Value Expression {#forced-value-expression .section-name}

A *forced-value expression* unwraps an optional value that you are
certain is not `nil`{.code-voice}. It has the following form:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    expression!
    ```

</div>

If the value of the *expression* is not `nil`{.code-voice}, the optional
value is unwrapped and returned with the corresponding nonoptional type.
Otherwise, a runtime error is raised.

The unwrapped value of a forced-value expression can be modified, either
by mutating the value itself, or by assigning to one of the value’s
members. For example:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `x`{.vc}: `Int`{.n}? = `0`{.m}
2.  `x`{.code-voice}!++
3.  `// x is now 1`{.code-voice}
4.  ` `{.code-voice}
5.  `var`{.code-voice} `someDictionary`{.vc} = \[`"a"`{.s}: \[`1`{.m},
    `2`{.m}, `3`{.m}\], `"b"`{.s}: \[`10`{.m}, `20`{.m}\]\]
6.  `someDictionary`{.code-voice}\[`"a"`{.s}\]!\[`0`{.m}\] = `100`{.m}
7.  `// someDictionary is now ["b": [10, 20], "a": [100, 2, 3]]`{.code-voice}

</div>

</div>

</div>

<div class="syntax-defs">

Grammar of a forced-value expression

<div class="syntax-defs-group">

[‌](){#forced-value-expression} <span class="syntax-def-name">
forced-value-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span>`!`{.literal}

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH32-ID405}
### Optional-Chaining Expression {#optional-chaining-expression .section-name}

An *optional-chaining expression* provides a simplified syntax for using
optional values in postfix expressions. It has the following form:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    expression?
    ```

</div>

The postfix `?`{.code-voice} operator makes an optional-chaining
expression from an expression without changing the expression’s value.

Optional-chaining expressions must appear within a postfix expression,
and they cause the postfix expression to be evaluated in a special way.
If the value of the optional-chaining expression is `nil`{.code-voice},
all of the other operations in the postfix expression are ignored and
the entire postfix expression evaluates to `nil`{.code-voice}. If the
value of the optional-chaining expression is not `nil`{.code-voice}, the
value of the optional-chaining expression is unwrapped and used to
evaluate the rest of the postfix expression. In either case, the value
of the postfix expression is still of an optional type.

If a postfix expression that contains an optional-chaining expression is
nested inside other postfix expressions, only the outermost expression
returns an optional type. In the example below, when `c`{.code-voice} is
not `nil`{.code-voice}, its value is unwrapped and used to evaluate
`.property`{.code-voice}, the value of which is used to evaluate
`.performAction()`{.code-voice}. The entire expression
`c?.property.performAction()`{.code-voice} has a value of an optional
type.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `c`{.vc}: `SomeClass`{.n}?
2.  `var`{.code-voice} `result`{.vc}: `Bool`{.n}? =
    `c`{.vc}?.`property`{.vc}.`performAction`{.vc}()

</div>

</div>

</div>

The following example shows the behavior of the example above without
using optional chaining.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `result`{.vc}: `Bool`{.n}? = `nil`{.kt}
2.  `if`{.code-voice} `let`{.kt} `unwrappedC`{.vc} = `c`{.vc} {
3.  `    result`{.code-voice} =
    `unwrappedC`{.vc}.`property`{.vc}.`performAction`{.vc}()
4.  `}`{.code-voice}

</div>

</div>

</div>

The unwrapped value of an optional-chaining expression can be modified,
either by mutating the value itself, or by assigning to one of the
value’s members. If the value of the optional-chaining expression is
`nil`{.code-voice}, the expression on the right hand side of the
assignment operator is not evaluated. For example:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `someFunctionWithSideEffects`{.vc}() -&gt;
    `Int`{.n} {
2.  `    return`{.code-voice} `42`{.m} `// No actual side effects.`{.c}
3.  `}`{.code-voice}
4.  `var`{.code-voice} `someDictionary`{.vc} = \[`"a"`{.s}: \[`1`{.m},
    `2`{.m}, `3`{.m}\], `"b"`{.s}: \[`10`{.m}, `20`{.m}\]\]
5.  ` `{.code-voice}
6.  `someDictionary`{.code-voice}\[`"not here"`{.s}\]?\[`0`{.m}\] =
    `someFunctionWithSideEffects`{.vc}()
7.  `// someFunctionWithSideEffects is not evaluated`{.code-voice}
8.  `// someDictionary is still ["b": [10, 20], "a": [1, 2, 3]]`{.code-voice}
9.  ` `{.code-voice}
10. `someDictionary`{.code-voice}\[`"a"`{.s}\]?\[`0`{.m}\] =
    `someFunctionWithSideEffects`{.vc}()
11. `// someFunctionWithSideEffects is evaluated and returns 42`{.code-voice}
12. `// someDictionary is now ["b": [10, 20], "a": [42, 2, 3]]`{.code-voice}

</div>

</div>

</div>

<div class="syntax-defs">

Grammar of an optional-chaining expression

<div class="syntax-defs-group">

[‌](){#optional-chaining-expression} <span class="syntax-def-name">
optional-chaining-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span>`?`{.literal}

</div>

</div>

</div>

</div>

</div>

</div>
