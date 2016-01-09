<div class="content-wrapper">

<div id="chapter_container" class="conceptualwithtasks">

[‌](){#TP40016643-CH33}[‌](){#TP40016643-CH33-ID428}
Statements {#statements .chapter-name}
----------

<div class="section section">

In Swift, there are three kinds of statements: simple statements,
compiler control statements, and control flow statements. Simple
statements are the most common and consist of either an expression or a
declaration. Compiler control statements allow the program to change
aspects of the compiler’s behavior and include a build configuration and
line control statement.

Control flow statements are used to control the flow of execution in a
program. There are several types of control flow statements in Swift,
including loop statements, branch statements, and control transfer
statements. Loop statements allow a block of code to be executed
repeatedly, branch statements allow a certain block of code to be
executed only when certain conditions are met, and control transfer
statements provide a way to alter the order in which code is executed.
In addition, Swift provides a `do`{.code-voice} statement to introduce
scope, and catch and handle errors, and a `defer`{.code-voice} statement
for running clean-up actions just before the current scope exits.

A semicolon (`;`{.code-voice}) can optionally appear after any statement
and is used to separate multiple statements if they appear on the same
line.

<div class="syntax-defs">

Grammar of a statement

<div class="syntax-defs-group">

[‌](){#statement} <span class="syntax-def-name"> statement </span> <span
class="arrow"> → </span><span
class="syntactic-cat">[expression](Expressions.md#expression)</span><span
class="optional">`;`{.literal}~opt~</span>

[‌](){#TP40016643-CH33-NoLink_656} <span class="syntax-def-name">
statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[declaration](Declarations.md#declaration)</span><span
class="optional">`;`{.literal}~opt~</span>

[‌](){#TP40016643-CH33-NoLink_657} <span class="syntax-def-name">
statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[loop-statement](Statements.md#loop-statement)</span><span
class="optional">`;`{.literal}~opt~</span>

[‌](){#TP40016643-CH33-NoLink_658} <span class="syntax-def-name">
statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[branch-statement](Statements.md#branch-statement)</span><span
class="optional">`;`{.literal}~opt~</span>

[‌](){#TP40016643-CH33-NoLink_659} <span class="syntax-def-name">
statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[labeled-statement](Statements.md#labeled-statement)</span><span
class="optional">`;`{.literal}~opt~</span>

[‌](){#TP40016643-CH33-NoLink_660} <span class="syntax-def-name">
statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[control-transfer-statement](Statements.md#control-transfer-statement)</span><span
class="optional">`;`{.literal}~opt~</span>

[‌](){#TP40016643-CH33-NoLink_661} <span class="syntax-def-name">
statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[defer-statement](Statements.md#defer-statement)</span><span
class="optional">`;`{.literal}~opt~</span>

[‌](){#TP40016643-CH33-NoLink_662} <span class="syntax-def-name">
statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[do-statement](Statements.md#do-statement)</span><span
class="optional">`:`{.literal}~opt~</span>

[‌](){#TP40016643-CH33-NoLink_663} <span class="syntax-def-name">
statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[compiler-control-statement](Statements.md#compiler-control-statement)</span>

[‌](){#statements} <span class="syntax-def-name"> statements </span>
<span class="arrow"> → </span><span
class="syntactic-cat">[statement](Statements.md#statement)</span><span
class="optional"><span
class="syntactic-cat">[statements](Statements.md#statements)</span>~opt~</span>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH33-ID429}
### Loop Statements {#loop-statements .section-name}

Loop statements allow a block of code to be executed repeatedly,
depending on the conditions specified in the loop. Swift has four loop
statements: a `for`{.code-voice} statement, a
`for`{.code-voice}-`in`{.code-voice} statement, a `while`{.code-voice}
statement, and a `repeat`{.code-voice}-`while`{.code-voice} statement.

Control flow in a loop statement can be changed by a
`break`{.code-voice} statement and a `continue`{.code-voice} statement
and is discussed in [Break
Statement](Statements.md#TP40016643-CH33-ID441) and [Continue
Statement](Statements.md#TP40016643-CH33-ID442) below.

<div class="syntax-defs">

Grammar of a loop statement

<div class="syntax-defs-group">

[‌](){#loop-statement} <span class="syntax-def-name"> loop-statement
</span> <span class="arrow"> → </span><span
class="syntactic-cat">[for-statement](Statements.md#for-statement)</span>

[‌](){#TP40016643-CH33-NoLink_667} <span class="syntax-def-name">
loop-statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[for-in-statement](Statements.md#for-in-statement)</span>

[‌](){#TP40016643-CH33-NoLink_668} <span class="syntax-def-name">
loop-statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[while-statement](Statements.md#while-statement)</span>

[‌](){#TP40016643-CH33-NoLink_669} <span class="syntax-def-name">
loop-statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[repeat-while-statement](Statements.md#repeat-while-statement)</span>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH33-ID430}
### For Statement {#for-statement .section-name}

A `for`{.code-voice} statement allows a block of code to be executed
repeatedly while incrementing a counter, as long as a condition remains
true.

A `for`{.code-voice} statement has the following form:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    for initialization; condition; increment {
    ```

-   ``` {.code-voice}
        statements
    ```

-   ``` {.code-voice}
    }
    ```

</div>

The semicolons between the *initialization*, *condition*, and
*increment* are required. The braces around the *statements* in the body
of the loop are also required.

A `for`{.code-voice} statement is executed as follows:

1.  The *initialization* is evaluated only once. It is typically used to
    declare and initialize any variables that are needed for the
    remainder of the loop.

2.  The *condition* expression is evaluated.

    If `true`{.code-voice}, the program executes the *statements*, and
    execution continues to step 3. If `false`{.code-voice}, the program
    does not execute the *statements* or the *increment* expression, and
    the program is finished executing the `for`{.code-voice} statement.

3.  The *increment* expression is evaluated, and execution returns to
    step 2.

Variables defined within the *initialization* are valid only within the
scope of the `for`{.code-voice} statement itself.

The value of the *condition* expression must have a type that conforms
to the `BooleanType`{.code-voice} protocol.

<div class="syntax-defs">

Grammar of a for statement

<div class="syntax-defs-group">

[‌](){#for-statement} <span class="syntax-def-name"> for-statement
</span> <span class="arrow"> → </span>`for`{.literal}<span
class="optional"><span
class="syntactic-cat">[for-init](Statements.md#for-init)</span>~opt~</span>`;`{.literal}<span
class="optional"><span
class="syntactic-cat">[expression](Expressions.md#expression)</span>~opt~</span>`;`{.literal}<span
class="optional"><span
class="syntactic-cat">[expression-list](Expressions.md#expression-list)</span>~opt~</span><span
class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

[‌](){#TP40016643-CH33-NoLink_672} <span class="syntax-def-name">
for-statement </span> <span class="arrow"> →
</span>`for`{.literal}`(`{.literal}<span class="optional"><span
class="syntactic-cat">[for-init](Statements.md#for-init)</span>~opt~</span>`;`{.literal}<span
class="optional"><span
class="syntactic-cat">[expression](Expressions.md#expression)</span>~opt~</span>`;`{.literal}<span
class="optional"><span
class="syntactic-cat">[expression-list](Expressions.md#expression-list)</span>~opt~</span>`)`{.literal}<span
class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

</div>

<div class="syntax-defs-group">

[‌](){#for-init} <span class="syntax-def-name"> for-init </span> <span
class="arrow"> → </span><span class="alternative"> <span
class="syntactic-cat">[variable-declaration](Declarations.md#variable-declaration)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[expression-list](Expressions.md#expression-list)</span>
</span>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH33-ID431}
### For-In Statement {#for-in-statement .section-name}

A `for`{.code-voice}-`in`{.code-voice} statement allows a block of code
to be executed once for each item in a collection (or any type) that
conforms to the `SequenceType`{.code-voice} protocol.

A `for`{.code-voice}-`in`{.code-voice} statement has the following form:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    for item in collection {
    ```

-   ``` {.code-voice}
        statements
    ```

-   ``` {.code-voice}
    }
    ```

</div>

The `generate()`{.code-voice} method is called on the *collection*
expression to obtain a value of a generator type—that is, a type that
conforms to the `GeneratorType`{.code-voice} protocol. The program
begins executing a loop by calling the `next()`{.code-voice} method on
the stream. If the value returned is not `None`{.code-voice}, it is
assigned to the *item* pattern, the program executes the *statements*,
and then continues execution at the beginning of the loop. Otherwise,
the program does not perform assignment or execute the *statements*, and
it is finished executing the `for`{.code-voice}-`in`{.code-voice}
statement.

<div class="syntax-defs">

Grammar of a for-in statement

<div class="syntax-defs-group">

[‌](){#for-in-statement} <span class="syntax-def-name"> for-in-statement
</span> <span class="arrow"> → </span>`for`{.literal}<span
class="optional">`case`{.literal}~opt~</span><span
class="syntactic-cat">[pattern](Patterns.md#pattern)</span>`in`{.literal}<span
class="syntactic-cat">[expression](Expressions.md#expression)</span><span
class="optional"><span
class="syntactic-cat">[where-clause](Statements.md#where-clause)</span>~opt~</span><span
class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH33-ID432}
### While Statement {#while-statement .section-name}

A `while`{.code-voice} statement allows a block of code to be executed
repeatedly, as long as a condition remains true.

A `while`{.code-voice} statement has the following form:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    while condition {
    ```

-   ``` {.code-voice}
        statements
    ```

-   ``` {.code-voice}
    }
    ```

</div>

A `while`{.code-voice} statement is executed as follows:

1.  The *condition* is evaluated.

    If `true`{.code-voice}, execution continues to step 2. If
    `false`{.code-voice}, the program is finished executing the
    `while`{.code-voice} statement.

2.  The program executes the *statements*, and execution returns to
    step 1.

Because the value of the *condition* is evaluated before the
*statements* are executed, the *statements* in a `while`{.code-voice}
statement can be executed zero or more times.

The value of the *condition* must have a type that conforms to the
`BooleanType`{.code-voice} protocol. The condition can also be an
optional binding declaration, as discussed in [Optional
Binding](TheBasics.md#TP40016643-CH5-ID333).

<div class="syntax-defs">

Grammar of a while statement

<div class="syntax-defs-group">

[‌](){#while-statement} <span class="syntax-def-name"> while-statement
</span> <span class="arrow"> → </span>`while`{.literal}<span
class="syntactic-cat">[condition-clause](Statements.md#condition-clause)</span><span
class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

</div>

<div class="syntax-defs-group">

[‌](){#condition-clause} <span class="syntax-def-name"> condition-clause
</span> <span class="arrow"> → </span><span
class="syntactic-cat">[expression](Expressions.md#expression)</span>

[‌](){#TP40016643-CH33-NoLink_679} <span class="syntax-def-name">
condition-clause </span> <span class="arrow"> → </span><span
class="syntactic-cat">[expression](Expressions.md#expression)</span>`,`{.literal}<span
class="syntactic-cat">[condition-list](Statements.md#condition-list)</span>

[‌](){#TP40016643-CH33-NoLink_680} <span class="syntax-def-name">
condition-clause </span> <span class="arrow"> → </span><span
class="syntactic-cat">[condition-list](Statements.md#condition-list)</span>

[‌](){#TP40016643-CH33-NoLink_681} <span class="syntax-def-name">
condition-clause </span> <span class="arrow"> → </span><span
class="syntactic-cat">[availability-condition](Statements.md#availability-condition)</span>`,`{.literal}<span
class="syntactic-cat">[expression](Expressions.md#expression)</span>

</div>

<div class="syntax-defs-group">

[‌](){#condition-list} <span class="syntax-def-name"> condition-list
</span> <span class="arrow"> → </span><span class="alternative"> <span
class="syntactic-cat">[condition](Statements.md#condition)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[condition](Statements.md#condition)</span>`,`{.literal}<span
class="syntactic-cat">[condition-list](Statements.md#condition-list)</span>
</span>

[‌](){#condition} <span class="syntax-def-name"> condition </span> <span
class="arrow"> → </span><span class="alternative"> <span
class="syntactic-cat">[availability-condition](Statements.md#availability-condition)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[case-condition](Statements.md#case-condition)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[optional-binding-condition](Statements.md#optional-binding-condition)</span>
</span>

[‌](){#case-condition} <span class="syntax-def-name"> case-condition
</span> <span class="arrow"> → </span>`case`{.literal}<span
class="syntactic-cat">[pattern](Patterns.md#pattern)</span><span
class="syntactic-cat">[initializer](Declarations.md#initializer)</span><span
class="optional"><span
class="syntactic-cat">[where-clause](Statements.md#where-clause)</span>~opt~</span>

</div>

<div class="syntax-defs-group">

[‌](){#optional-binding-condition} <span class="syntax-def-name">
optional-binding-condition </span> <span class="arrow"> → </span><span
class="syntactic-cat">[optional-binding-head](Statements.md#optional-binding-head)</span><span
class="optional"><span
class="syntactic-cat">[optional-binding-continuation-list](Statements.md#optional-binding-continuation-list)</span>~opt~</span><span
class="optional"><span
class="syntactic-cat">[where-clause](Statements.md#where-clause)</span>~opt~</span>

[‌](){#optional-binding-head} <span class="syntax-def-name">
optional-binding-head </span> <span class="arrow"> →
</span>`let`{.literal}<span
class="syntactic-cat">[pattern](Patterns.md#pattern)</span><span
class="syntactic-cat">[initializer](Declarations.md#initializer)</span>

[‌](){#optional-binding-continuation-list} <span
class="syntax-def-name"> optional-binding-continuation-list </span>
<span class="arrow"> → </span><span class="alternative"> <span
class="syntactic-cat">[optional-binding-continuation](Statements.md#optional-binding-continuation)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[optional-binding-continuation](Statements.md#optional-binding-continuation)</span>`,`{.literal}<span
class="syntactic-cat">[optional-binding-continuation-list](Statements.md#optional-binding-continuation-list)</span>
</span>

[‌](){#optional-binding-continuation} <span class="syntax-def-name">
optional-binding-continuation </span> <span class="arrow"> →
</span><span class="alternative"> <span
class="syntactic-cat">[pattern](Patterns.md#pattern)</span><span
class="syntactic-cat">[initializer](Declarations.md#initializer)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[optional-binding-head](Statements.md#optional-binding-head)</span>
</span>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH33-ID433}
### Repeat-While Statement {#repeat-while-statement .section-name}

A `repeat`{.code-voice}-`while`{.code-voice} statement allows a block of
code to be executed one or more times, as long as a condition remains
true.

A `repeat`{.code-voice}-`while`{.code-voice} statement has the following
form:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    repeat {
    ```

-   ``` {.code-voice}
        statements
    ```

-   ``` {.code-voice}
    } while condition
    ```

</div>

A `repeat`{.code-voice}-`while`{.code-voice} statement is executed as
follows:

1.  The program executes the *statements*, and execution continues to
    step 2.

2.  The *condition* is evaluated.

    If `true`{.code-voice}, execution returns to step 1. If
    `false`{.code-voice}, the program is finished executing the
    `repeat`{.code-voice}-`while`{.code-voice} statement.

Because the value of the *condition* is evaluated after the *statements*
are executed, the *statements* in a
`repeat`{.code-voice}-`while`{.code-voice} statement are executed at
least once.

The value of the *condition* must have a type that conforms to the
`BooleanType`{.code-voice} protocol. The condition can also be an
optional binding declaration, as discussed in [Optional
Binding](TheBasics.md#TP40016643-CH5-ID333).

<div class="syntax-defs">

Grammar of a repeat-while statement

<div class="syntax-defs-group">

[‌](){#repeat-while-statement} <span class="syntax-def-name">
repeat-while-statement </span> <span class="arrow"> →
</span>`repeat`{.literal}<span
class="syntactic-cat">[code-block](Declarations.md#code-block)</span>`while`{.literal}<span
class="syntactic-cat">[expression](Expressions.md#expression)</span>

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH33-ID434}
### Branch Statements {#branch-statements .section-name}

Branch statements allow the program to execute certain parts of code
depending on the value of one or more conditions. The values of the
conditions specified in a branch statement control how the program
branches and, therefore, what block of code is executed. Swift has three
branch statements: an `if`{.code-voice} statement, a
`guard`{.code-voice} statement, and a `switch`{.code-voice} statement.

Control flow in an `if`{.code-voice} statement or a
`switch`{.code-voice} statement can be changed by a `break`{.code-voice}
statement and is discussed in [Break
Statement](Statements.md#TP40016643-CH33-ID441) below.

<div class="syntax-defs">

Grammar of a branch statement

<div class="syntax-defs-group">

[‌](){#branch-statement} <span class="syntax-def-name"> branch-statement
</span> <span class="arrow"> → </span><span
class="syntactic-cat">[if-statement](Statements.md#if-statement)</span>

[‌](){#TP40016643-CH33-NoLink_693} <span class="syntax-def-name">
branch-statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[guard-statement](Statements.md#guard-statement)</span>

[‌](){#TP40016643-CH33-NoLink_694} <span class="syntax-def-name">
branch-statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[switch-statement](Statements.md#switch-statement)</span>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH33-ID435}
### If Statement {#if-statement .section-name}

An `if`{.code-voice} statement is used for executing code based on the
evaluation of one or more conditions.

There are two basic forms of an `if`{.code-voice} statement. In each
form, the opening and closing braces are required.

The first form allows code to be executed only when a condition is true
and has the following form:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    if condition {
    ```

-   ``` {.code-voice}
        statements
    ```

-   ``` {.code-voice}
    }
    ```

</div>

The second form of an `if`{.code-voice} statement provides an additional
*else clause* (introduced by the `else`{.code-voice} keyword) and is
used for executing one part of code when the condition is true and
another part of code when the same condition is false. When a single
else clause is present, an `if`{.code-voice} statement has the following
form:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    if condition {
    ```

-   ``` {.code-voice}
        statements to execute if condition is true
    ```

-   ``` {.code-voice}
    } else {
    ```

-   ``` {.code-voice}
        statements to execute if condition is false
    ```

-   ``` {.code-voice}
    }
    ```

</div>

The else clause of an `if`{.code-voice} statement can contain another
`if`{.code-voice} statement to test more than one condition. An
`if`{.code-voice} statement chained together in this way has the
following form:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    if condition 1 {
    ```

-   ``` {.code-voice}
        statements to execute if condition 1 is true
    ```

-   ``` {.code-voice}
    } else if condition 2 {
    ```

-   ``` {.code-voice}
        statements to execute if condition 2 is true
    ```

-   ``` {.code-voice}
    } else {
    ```

-   ``` {.code-voice}
        statements to execute if both conditions are false
    ```

-   ``` {.code-voice}
    }
    ```

</div>

The value of any condition in an `if`{.code-voice} statement must have a
type that conforms to the `BooleanType`{.code-voice} protocol. The
condition can also be an optional binding declaration, as discussed in
[Optional Binding](TheBasics.md#TP40016643-CH5-ID333).

<div class="syntax-defs">

Grammar of an if statement

<div class="syntax-defs-group">

[‌](){#if-statement} <span class="syntax-def-name"> if-statement </span>
<span class="arrow"> → </span>`if`{.literal}<span
class="syntactic-cat">[condition-clause](Statements.md#condition-clause)</span><span
class="syntactic-cat">[code-block](Declarations.md#code-block)</span><span
class="optional"><span
class="syntactic-cat">[else-clause](Statements.md#else-clause)</span>~opt~</span>

[‌](){#else-clause} <span class="syntax-def-name"> else-clause </span>
<span class="arrow"> → </span><span class="alternative">
`else`{.literal}<span
class="syntactic-cat">[code-block](Declarations.md#code-block)</span>
</span><span class="alternative"> `else`{.literal}<span
class="syntactic-cat">[if-statement](Statements.md#if-statement)</span>
</span>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH33-ID524}
### Guard Statement {#guard-statement .section-name}

A `guard`{.code-voice} statement is used to transfer program control out
of a scope if one or more conditions aren’t met.

A `guard`{.code-voice} statement has the following form:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    guard condition else {
    ```

-   ``` {.code-voice}
        statements
    ```

-   ``` {.code-voice}
    }
    ```

</div>

The value of any condition in a `guard`{.code-voice} statement must have
a type that conforms to the `BooleanType`{.code-voice} protocol. The
condition can also be an optional binding declaration, as discussed in
[Optional Binding](TheBasics.md#TP40016643-CH5-ID333).

Any constants assigned a value from an optional binding declaration in a
`guard`{.code-voice} statement condition can be used for the rest of the
guard statement’s enclosing scope.

The `else`{.code-voice} clause of a `guard`{.code-voice} statement is
required, and must either call a function marked with the
`noreturn`{.code-voice} attribute or transfer program control outside
the guard statement’s enclosing scope using one of the following
statements:

-   `return`{.code-voice}

-   `break`{.code-voice}

-   `continue`{.code-voice}

-   `throw`{.code-voice}

Control transfer statements are discussed in [Control Transfer
Statements](Statements.md#TP40016643-CH33-ID440) below.

<div class="syntax-defs">

Grammar of a guard statement

<div class="syntax-defs-group">

[‌](){#guard-statement} <span class="syntax-def-name"> guard-statement
</span> <span class="arrow"> → </span>`guard`{.literal}<span
class="syntactic-cat">[condition-clause](Statements.md#condition-clause)</span>`else`{.literal}<span
class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH33-ID436}
### Switch Statement {#switch-statement .section-name}

A `switch`{.code-voice} statement allows certain blocks of code to be
executed depending on the value of a control expression.

A `switch`{.code-voice} statement has the following form:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    switch control expression {
    ```

-   ``` {.code-voice}
    case pattern 1:
    ```

-   ``` {.code-voice}
        statements
    ```

-   ``` {.code-voice}
    case pattern 2 where condition:
    ```

-   ``` {.code-voice}
        statements
    ```

-   ``` {.code-voice}
    case pattern 3 where condition,
    ```

-   ``` {.code-voice}
    pattern 4 where condition:
    ```

-   ``` {.code-voice}
        statements
    ```

-   ``` {.code-voice}
    default:
    ```

-   ``` {.code-voice}
        statements
    ```

-   ``` {.code-voice}
    }
    ```

</div>

The *control expression* of the `switch`{.code-voice} statement is
evaluated and then compared with the patterns specified in each case. If
a match is found, the program executes the *statements* listed within
the scope of that case. The scope of each case can’t be empty. As a
result, you must include at least one statement following the colon
(`:`{.code-voice}) of each case label. Use a single `break`{.code-voice}
statement if you don’t intend to execute any code in the body of a
matched case.

The values of expressions your code can branch on are very flexible. For
instance, in addition to the values of scalar types, such as integers
and characters, your code can branch on the values of any type,
including floating-point numbers, strings, tuples, instances of custom
classes, and optionals. The value of the *control expression* can even
be matched to the value of a case in an enumeration and checked for
inclusion in a specified range of values. For examples of how to use
these various types of values in `switch`{.code-voice} statements, see
[Switch](ControlFlow.md#TP40016643-CH9-ID129) in [Control
Flow](ControlFlow.md).

A `switch`{.code-voice} case can optionally contain a where clause after
each pattern. A *where clause* is introduced by the `where`{.code-voice}
keyword followed by an expression, and is used to provide an additional
condition before a pattern in a case is considered matched to the
*control expression*. If a where clause is present, the *statements*
within the relevant case are executed only if the value of the *control
expression* matches one of the patterns of the case and the expression
of the where clause evaluates to `true`{.code-voice}. For instance, a
*control expression* matches the case in the example below only if it is
a tuple that contains two elements of the same value, such as
`(1, 1)`{.code-voice}.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `case`{.code-voice} `let`{.kt} (`x`{.vc}, `y`{.vc}) `where`{.kt}
    `x`{.vc} == `y`{.vc}:

</div>

</div>

</div>

As the above example shows, patterns in a case can also bind constants
using the `let`{.code-voice} keyword. These constants can then be
referenced in a corresponding where clause and throughout the rest of
the code within the scope of the case. That said, if the case contains
multiple patterns that match the control expression, none of those
patterns can contain constant bindings.

A `switch`{.code-voice} statement can also include a default case,
introduced by the `default`{.code-voice} keyword. The code within a
default case is executed only if no other cases match the control
expression. A `switch`{.code-voice} statement can include only one
default case, which must appear at the end of the `switch`{.code-voice}
statement.

Although the actual execution order of pattern-matching operations, and
in particular the evaluation order of patterns in cases, is unspecified,
pattern matching in a `switch`{.code-voice} statement behaves as if the
evaluation is performed in source order—that is, the order in which they
appear in source code. As a result, if multiple cases contain patterns
that evaluate to the same value, and thus can match the value of the
control expression, the program executes only the code within the first
matching case in source order.

<div class="section section">

[‌](){#TP40016643-CH33-ID437}
### Switch Statements Must Be Exhaustive {#switch-statements-must-be-exhaustive .section-name}

In Swift, every possible value of the control expression’s type must
match the value of at least one pattern of a case. When this simply
isn’t feasible (for instance, when the control expression’s type is
`Int`{.code-voice}), you can include a default case to satisfy the
requirement.

</div>

<div class="section section">

[‌](){#TP40016643-CH33-ID438}
### Execution Does Not Fall Through Cases Implicitly {#execution-does-not-fall-through-cases-implicitly .section-name}

After the code within a matched case has finished executing, the program
exits from the `switch`{.code-voice} statement. Program execution does
not continue or “fall through” to the next case or default case. That
said, if you want execution to continue from one case to the next,
explicitly include a `fallthrough`{.code-voice} statement, which simply
consists of the `fallthrough`{.code-voice} keyword, in the case from
which you want execution to continue. For more information about the
`fallthrough`{.code-voice} statement, see [Fallthrough
Statement](Statements.md#TP40016643-CH33-ID443) below.

<div class="syntax-defs">

Grammar of a switch statement

<div class="syntax-defs-group">

[‌](){#switch-statement} <span class="syntax-def-name"> switch-statement
</span> <span class="arrow"> → </span>`switch`{.literal}<span
class="syntactic-cat">[expression](Expressions.md#expression)</span>`{`{.literal}<span
class="optional"><span
class="syntactic-cat">[switch-cases](Statements.md#switch-cases)</span>~opt~</span>`}`{.literal}

[‌](){#switch-cases} <span class="syntax-def-name"> switch-cases </span>
<span class="arrow"> → </span><span
class="syntactic-cat">[switch-case](Statements.md#switch-case)</span><span
class="optional"><span
class="syntactic-cat">[switch-cases](Statements.md#switch-cases)</span>~opt~</span>

[‌](){#switch-case} <span class="syntax-def-name"> switch-case </span>
<span class="arrow"> → </span><span class="alternative"> <span
class="syntactic-cat">[case-label](Statements.md#case-label)</span><span
class="syntactic-cat">[statements](Statements.md#statements)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[default-label](Statements.md#default-label)</span><span
class="syntactic-cat">[statements](Statements.md#statements)</span>
</span>

</div>

<div class="syntax-defs-group">

[‌](){#case-label} <span class="syntax-def-name"> case-label </span>
<span class="arrow"> → </span>`case`{.literal}<span
class="syntactic-cat">[case-item-list](Statements.md#case-item-list)</span>`:`{.literal}

[‌](){#case-item-list} <span class="syntax-def-name"> case-item-list
</span> <span class="arrow"> → </span><span class="alternative"> <span
class="syntactic-cat">[pattern](Patterns.md#pattern)</span><span
class="optional"><span
class="syntactic-cat">[where-clause](Statements.md#where-clause)</span>~opt~</span>
</span><span class="alternative"> <span
class="syntactic-cat">[pattern](Patterns.md#pattern)</span><span
class="optional"><span
class="syntactic-cat">[where-clause](Statements.md#where-clause)</span>~opt~</span>`,`{.literal}<span
class="syntactic-cat">[case-item-list](Statements.md#case-item-list)</span>
</span>

[‌](){#default-label} <span class="syntax-def-name"> default-label
</span> <span class="arrow"> → </span>`default`{.literal}`:`{.literal}

</div>

<div class="syntax-defs-group">

[‌](){#where-clause} <span class="syntax-def-name"> where-clause </span>
<span class="arrow"> → </span>`where`{.literal}<span
class="syntactic-cat">[where-expression](Statements.md#where-expression)</span>

[‌](){#where-expression} <span class="syntax-def-name"> where-expression
</span> <span class="arrow"> → </span><span
class="syntactic-cat">[expression](Expressions.md#expression)</span>

</div>

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH33-ID439}
### Labeled Statement {#labeled-statement .section-name}

You can prefix a loop statement, an `if`{.code-voice} statement, or a
`switch`{.code-voice} statement with a *statement label*, which consists
of the name of the label followed immediately by a colon (:). Use
statement labels with `break`{.code-voice} and `continue`{.code-voice}
statements to be explicit about how you want to change control flow in a
loop statement or a `switch`{.code-voice} statement, as discussed in
[Break Statement](Statements.md#TP40016643-CH33-ID441) and [Continue
Statement](Statements.md#TP40016643-CH33-ID442) below.

The scope of a labeled statement is the entire statement following the
statement label. You can nest labeled statements, but the name of each
statement label must be unique.

For more information and to see examples of how to use statement labels,
see [Labeled Statements](ControlFlow.md#TP40016643-CH9-ID141) in
[Control Flow](ControlFlow.md).

<div class="syntax-defs">

Grammar of a labeled statement

<div class="syntax-defs-group">

[‌](){#labeled-statement} <span class="syntax-def-name">
labeled-statement </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[statement-label](Statements.md#statement-label)</span><span
class="syntactic-cat">[loop-statement](Statements.md#loop-statement)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[statement-label](Statements.md#statement-label)</span><span
class="syntactic-cat">[if-statement](Statements.md#if-statement)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[statement-label](Statements.md#statement-label)</span><span
class="syntactic-cat">[switch-statement](Statements.md#switch-statement)</span>
</span>

[‌](){#statement-label} <span class="syntax-def-name"> statement-label
</span> <span class="arrow"> → </span><span
class="syntactic-cat">[label-name](Statements.md#label-name)</span>`:`{.literal}

[‌](){#label-name} <span class="syntax-def-name"> label-name </span>
<span class="arrow"> → </span><span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH33-ID440}
### Control Transfer Statements {#control-transfer-statements .section-name}

Control transfer statements can change the order in which code in your
program is executed by unconditionally transferring program control from
one piece of code to another. Swift has five control transfer
statements: a `break`{.code-voice} statement, a `continue`{.code-voice}
statement, a `fallthrough`{.code-voice} statement, a
`return`{.code-voice} statement, and a `throw`{.code-voice} statement.

<div class="syntax-defs">

Grammar of a control transfer statement

<div class="syntax-defs-group">

[‌](){#control-transfer-statement} <span class="syntax-def-name">
control-transfer-statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[break-statement](Statements.md#break-statement)</span>

[‌](){#TP40016643-CH33-NoLink_715} <span class="syntax-def-name">
control-transfer-statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[continue-statement](Statements.md#continue-statement)</span>

[‌](){#TP40016643-CH33-NoLink_716} <span class="syntax-def-name">
control-transfer-statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[fallthrough-statement](Statements.md#fallthrough-statement)</span>

[‌](){#TP40016643-CH33-NoLink_717} <span class="syntax-def-name">
control-transfer-statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[return-statement](Statements.md#return-statement)</span>

[‌](){#TP40016643-CH33-NoLink_718} <span class="syntax-def-name">
control-transfer-statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[throw-statement](Statements.md#throw-statement)</span>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH33-ID441}
### Break Statement {#break-statement .section-name}

A `break`{.code-voice} statement ends program execution of a loop, an
`if`{.code-voice} statement, or a `switch`{.code-voice} statement. A
`break`{.code-voice} statement can consist of only the
`break`{.code-voice} keyword, or it can consist of the
`break`{.code-voice} keyword followed by the name of a statement label,
as shown below.

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    break
    ```

-   ``` {.code-voice}
    break label name
    ```

</div>

When a `break`{.code-voice} statement is followed by the name of a
statement label, it ends program execution of the loop,
`if`{.code-voice} statement, or `switch`{.code-voice} statement named by
that label.

When a `break`{.code-voice} statement is not followed by the name of a
statement label, it ends program execution of the `switch`{.code-voice}
statement or the innermost enclosing loop statement in which it occurs.
You can’t use an unlabeled `break`{.code-voice} statement to break out
of an `if`{.code-voice} statement.

In both cases, program control is then transferred to the first line of
code following the enclosing loop or `switch`{.code-voice} statement, if
any.

For examples of how to use a `break`{.code-voice} statement, see
[Break](ControlFlow.md#TP40016643-CH9-ID137) and [Labeled
Statements](ControlFlow.md#TP40016643-CH9-ID141) in [Control
Flow](ControlFlow.md).

<div class="syntax-defs">

Grammar of a break statement

<div class="syntax-defs-group">

[‌](){#break-statement} <span class="syntax-def-name"> break-statement
</span> <span class="arrow"> → </span>`break`{.literal}<span
class="optional"><span
class="syntactic-cat">[label-name](Statements.md#label-name)</span>~opt~</span>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH33-ID442}
### Continue Statement {#continue-statement .section-name}

A `continue`{.code-voice} statement ends program execution of the
current iteration of a loop statement but does not stop execution of the
loop statement. A `continue`{.code-voice} statement can consist of only
the `continue`{.code-voice} keyword, or it can consist of the
`continue`{.code-voice} keyword followed by the name of a statement
label, as shown below.

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    continue
    ```

-   ``` {.code-voice}
    continue label name
    ```

</div>

When a `continue`{.code-voice} statement is followed by the name of a
statement label, it ends program execution of the current iteration of
the loop statement named by that label.

When a `continue`{.code-voice} statement is not followed by the name of
a statement label, it ends program execution of the current iteration of
the innermost enclosing loop statement in which it occurs.

In both cases, program control is then transferred to the condition of
the enclosing loop statement.

In a `for`{.code-voice} statement, the increment expression is still
evaluated after the `continue`{.code-voice} statement is executed,
because the increment expression is evaluated after the execution of the
loop’s body.

For examples of how to use a `continue`{.code-voice} statement, see
[Continue](ControlFlow.md#TP40016643-CH9-ID136) and [Labeled
Statements](ControlFlow.md#TP40016643-CH9-ID141) in [Control
Flow](ControlFlow.md).

<div class="syntax-defs">

Grammar of a continue statement

<div class="syntax-defs-group">

[‌](){#continue-statement} <span class="syntax-def-name">
continue-statement </span> <span class="arrow"> →
</span>`continue`{.literal}<span class="optional"><span
class="syntactic-cat">[label-name](Statements.md#label-name)</span>~opt~</span>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH33-ID443}
### Fallthrough Statement {#fallthrough-statement .section-name}

A `fallthrough`{.code-voice} statement consists of the
`fallthrough`{.code-voice} keyword and occurs only in a case block of a
`switch`{.code-voice} statement. A `fallthrough`{.code-voice} statement
causes program execution to continue from one case in a
`switch`{.code-voice} statement to the next case. Program execution
continues to the next case even if the patterns of the case label do not
match the value of the `switch`{.code-voice} statement’s control
expression.

A `fallthrough`{.code-voice} statement can appear anywhere inside a
`switch`{.code-voice} statement, not just as the last statement of a
case block, but it can’t be used in the final case block. It also cannot
transfer control into a case block whose pattern contains value binding
patterns.

For an example of how to use a `fallthrough`{.code-voice} statement in a
`switch`{.code-voice} statement, see [Control Transfer
Statements](ControlFlow.md#TP40016643-CH9-ID135) in [Control
Flow](ControlFlow.md).

<div class="syntax-defs">

Grammar of a fallthrough statement

<div class="syntax-defs-group">

[‌](){#fallthrough-statement} <span class="syntax-def-name">
fallthrough-statement </span> <span class="arrow"> →
</span>`fallthrough`{.literal}

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH33-ID444}
### Return Statement {#return-statement .section-name}

A `return`{.code-voice} statement occurs in the body of a function or
method definition and causes program execution to return to the calling
function or method. Program execution continues at the point immediately
following the function or method call.

A `return`{.code-voice} statement can consist of only the
`return`{.code-voice} keyword, or it can consist of the
`return`{.code-voice} keyword followed by an expression, as shown below.

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    return
    ```

-   ``` {.code-voice}
    return expression
    ```

</div>

When a `return`{.code-voice} statement is followed by an expression, the
value of the expression is returned to the calling function or method.
If the value of the expression does not match the value of the return
type declared in the function or method declaration, the expression’s
value is converted to the return type before it is returned to the
calling function or method.

<div class="note">

Note

As described in [Failable
Initializers](Declarations.md#TP40016643-CH34-ID376), a special form
of the `return`{.code-voice} statement (`return nil`{.code-voice}) can
be used in a failable initializer to indicate initialization failure.

</div>

When a `return`{.code-voice} statement is not followed by an expression,
it can be used only to return from a function or method that does not
return a value (that is, when the return type of the function or method
is `Void`{.code-voice} or `()`{.code-voice}).

<div class="syntax-defs">

Grammar of a return statement

<div class="syntax-defs-group">

[‌](){#return-statement} <span class="syntax-def-name"> return-statement
</span> <span class="arrow"> → </span>`return`{.literal}<span
class="optional"><span
class="syntactic-cat">[expression](Expressions.md#expression)</span>~opt~</span>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH33-ID522}
### Availability Condition {#availability-condition .section-name}

An *availability condition* is used as a condition of an
`if`{.code-voice}, `while`{.code-voice}, and `guard`{.code-voice}
statement to query the availability of APIs at runtime, based on
specified platforms arguments.

An availability condition has the following form:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    if #available(platform name version, ..., *) {
    ```

-   ``` {.code-voice}
        statements to execute if the APIs are available
    ```

-   ``` {.code-voice}
    } else {
    ```

-   ``` {.code-voice}
        fallback statements to execute if the APIs are unavailable
    ```

-   ``` {.code-voice}
    }
    ```

</div>

You use an availability condition to execute a block of code, depending
on whether the APIs you want to use are available at runtime. The
compiler uses the information from the availability condition when it
verifies that the APIs in that block of code are available.

The availability condition takes a comma-separated list of platform
names and versions. Use `iOS`{.code-voice}, `OSX`{.code-voice}, and
`watchOS`{.code-voice} for the platform names, and include the
corresponding version numbers. The `*`{.code-voice} argument is required
and specifies that on any other platform, the body of the code block
guarded by the availability condition executes on the minimum deployment
target specified by your target.

Unlike Boolean conditions, you can’t combine availability conditions
using logical operators such as `&&`{.code-voice} and `||`{.code-voice}.

<div class="syntax-defs">

Grammar of an availability condition

<div class="syntax-defs-group">

[‌](){#availability-condition} <span class="syntax-def-name">
availability-condition </span> <span class="arrow"> →
</span>`#available`{.literal}`(`{.literal}<span
class="syntactic-cat">[availability-arguments](Statements.md#availability-arguments)</span>`)`{.literal}

[‌](){#availability-arguments} <span class="syntax-def-name">
availability-arguments </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[availability-argument](Statements.md#availability-argument)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[availability-argument](Statements.md#availability-argument)</span>`,`{.literal}<span
class="syntactic-cat">[availability-arguments](Statements.md#availability-arguments)</span>
</span>

[‌](){#availability-argument} <span class="syntax-def-name">
availability-argument </span> <span class="arrow"> → </span><span
class="syntactic-cat">[platform-name](Statements.md#platform-name)</span><span
class="syntactic-cat">[platform-version](Statements.md#platform-version)</span>

[‌](){#TP40016643-CH33-NoLink_732} <span class="syntax-def-name">
availability-argument </span> <span class="arrow"> →
</span>`*`{.literal}

</div>

<div class="syntax-defs-group">

[‌](){#platform-name} <span class="syntax-def-name"> platform-name
</span> <span class="arrow"> → </span><span class="alternative">
`iOS`{.literal} </span><span class="alternative">
`iOSApplicationExtension`{.literal} </span>

[‌](){#TP40016643-CH33-NoLink_734} <span class="syntax-def-name">
platform-name </span> <span class="arrow"> → </span><span
class="alternative"> `OSX`{.literal} </span><span class="alternative">
`OSXApplicationExtension`{.literal} </span>

[‌](){#TP40016643-CH33-NoLink_735} <span class="syntax-def-name">
platform-name </span> <span class="arrow"> → </span>`watchOS`{.literal}

[‌](){#platform-version} <span class="syntax-def-name"> platform-version
</span> <span class="arrow"> → </span><span
class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)</span>

[‌](){#TP40016643-CH33-NoLink_737} <span class="syntax-def-name">
platform-version </span> <span class="arrow"> → </span><span
class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)</span>`.`{.literal}<span
class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)</span>

[‌](){#TP40016643-CH33-NoLink_738} <span class="syntax-def-name">
platform-version </span> <span class="arrow"> → </span><span
class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)</span>`.`{.literal}<span
class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)</span>`.`{.literal}<span
class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)</span>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH33-ID518}
### Throw Statement {#throw-statement .section-name}

A `throw`{.code-voice} statement occurs in the body of a throwing
function or method, or in the body of a closure expression whose type is
marked with the `throws`{.code-voice} keyword.

A `throw`{.code-voice} statement causes a program to end execution of
the current scope and begin error propagation to its enclosing scope.
The error that’s thrown continues to propagate until it’s handled by a
`catch`{.code-voice} clause of a `do`{.code-voice} statement.

A `throw`{.code-voice} statement consists of the `throw`{.code-voice}
keyword followed by an expression, as shown below.

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    throw expression
    ```

</div>

The value of the *expression* must have a type that conforms to the
`ErrorType`{.code-voice} protocol.

For an example of how to use a `throw`{.code-voice} statement, see
[Propagating Errors Using Throwing
Functions](ErrorHandling.md#TP40016643-CH42-ID510) in [Error
Handling](ErrorHandling.md).

<div class="syntax-defs">

Grammar of a throw statement

<div class="syntax-defs-group">

[‌](){#throw-statement} <span class="syntax-def-name"> throw-statement
</span> <span class="arrow"> → </span>`throw`{.literal}<span
class="syntactic-cat">[expression](Expressions.md#expression)</span>

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH33-ID532}
### Defer Statement {#defer-statement .section-name}

A `defer`{.code-voice} statement is used for executing code just before
transferring program control outside of the scope that the
`defer`{.code-voice} statement appears in.

A `defer`{.code-voice} statement has the following form:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    defer {
    ```

-   ``` {.code-voice}
        statements
    ```

-   ``` {.code-voice}
    }
    ```

</div>

The statements within the `defer`{.code-voice} statement are executed no
matter how program control is transferred. This means that a
`defer`{.code-voice} statement can be used, for example, to perform
manual resource management such as closing file descriptors, and to
perform actions that need to happen even if an error is thrown.

If multiple `defer`{.code-voice} statements appear in the same scope,
the order they appear is the reverse of the order they are executed.
Executing the last `defer`{.code-voice} statement in a given scope first
means that statements inside that last `defer`{.code-voice} statement
can refer to resources that will be cleaned up by other
`defer`{.code-voice} statements.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `f`{.vc}() {
2.  `    defer`{.code-voice} { `print`{.vc}(`"First"`{.s}) }
3.  `    defer`{.code-voice} { `print`{.vc}(`"Second"`{.s}) }
4.  `    defer`{.code-voice} { `print`{.vc}(`"Third"`{.s}) }
5.  `}`{.code-voice}
6.  `f`{.code-voice}()
7.  `// prints "Third"`{.code-voice}
8.  `// prints "Second"`{.code-voice}
9.  `// prints "First"`{.code-voice}

</div>

</div>

</div>

The statements in the `defer`{.code-voice} statement can’t transfer
program control outside of the `defer`{.code-voice} statement.

<div class="syntax-defs">

Grammar of a defer statement

<div class="syntax-defs-group">

[‌](){#defer-statement} <span class="syntax-def-name"> defer-statement
</span> <span class="arrow"> → </span>`defer`{.literal}<span
class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH33-ID533}
### Do Statement {#do-statement .section-name}

The `do`{.code-voice} statement is used to introduce a new scope and can
optionally contain one or more `catch`{.code-voice} clauses, which
contain patterns that match against defined error conditions. Variables
and constants declared in the scope of a `do`{.code-voice} statement can
be accessed only within that scope.

A `do`{.code-voice} statement in Swift is similar to curly braces
(`{}`{.code-voice}) in C used to delimit a code block, and does not
incur a performance cost at runtime.

A `do`{.code-voice} statement has the following form:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    do {
    ```

-   ``` {.code-voice}
        try expression
    ```

-   ``` {.code-voice}
        statements
    ```

-   ``` {.code-voice}
    } catch pattern 1 {
    ```

-   ``` {.code-voice}
        statements
    ```

-   ``` {.code-voice}
    } catch pattern 2 where condition {
    ```

-   ``` {.code-voice}
        statements
    ```

-   ``` {.code-voice}
    }
    ```

</div>

Like a `switch`{.code-voice} statement, the compiler attempts to infer
whether `catch`{.code-voice} clauses are exhaustive. If such a
determination can be made, the error is considered handled. Otherwise,
the error automatically propagates out of the containing scope, either
to an enclosing `catch`{.code-voice} clause or out of the throwing
function must handle the error, or the containing function must be
declared with `throws`{.code-voice}.

To ensure that an error is handled, use a `catch`{.code-voice} clause
with a pattern that matches all errors, such as a wildcard pattern
(`_`{.code-voice}). If a `catch`{.code-voice} clause does not specify a
pattern, the `catch`{.code-voice} clause matches and binds any error to
a local constant named `error`{.code-voice}. For more information about
the pattens you can use in a `catch`{.code-voice} clause, see
[Patterns](Patterns.md).

To see an example of how to use a `do`{.code-voice} statement with
several `catch`{.code-voice} clauses, see [Handling
Errors](ErrorHandling.md#TP40016643-CH42-ID512).

<div class="syntax-defs">

Grammar of a do statement

<div class="syntax-defs-group">

[‌](){#do-statement} <span class="syntax-def-name"> do-statement </span>
<span class="arrow"> → </span>`do`{.literal}<span
class="syntactic-cat">[code-block](Declarations.md#code-block)</span><span
class="optional"><span
class="syntactic-cat">[catch-clauses](Statements.md#catch-clauses)</span>~opt~</span>

[‌](){#catch-clauses} <span class="syntax-def-name"> catch-clauses
</span> <span class="arrow"> → </span><span
class="syntactic-cat">[catch-clause](Statements.md#catch-clause)</span><span
class="optional"><span
class="syntactic-cat">[catch-clauses](Statements.md#catch-clauses)</span>~opt~</span>

[‌](){#catch-clause} <span class="syntax-def-name"> catch-clause </span>
<span class="arrow"> → </span>`catch`{.literal}<span
class="optional"><span
class="syntactic-cat">[pattern](Patterns.md#pattern)</span>~opt~</span><span
class="optional"><span
class="syntactic-cat">[where-clause](Statements.md#where-clause)</span>~opt~</span><span
class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH33-ID538}
### Compiler Control Statements {#compiler-control-statements .section-name}

Compiler control statements allow the program to change aspects of the
compiler’s behavior. Swift has two complier control statements: a build
configuration statement and a line control statement.

<div class="syntax-defs">

Grammar of a compiler control statement

<div class="syntax-defs-group">

[‌](){#compiler-control-statement} <span class="syntax-def-name">
compiler-control-statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[build-configuration-statement](Statements.md#build-configuration-statement)</span>

[‌](){#TP40016643-CH33-NoLink_749} <span class="syntax-def-name">
compiler-control-statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[line-control-statement](Statements.md#line-control-statement)</span>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH33-ID539}
### Build Configuration Statement {#build-configuration-statement .section-name}

A build configuration statement allows code to be conditionally compiled
depending on the value of one or more build configurations.

Every build configuration statement begins with `#if`{.code-voice} and
ends with `#endif`{.code-voice}. A simple build configuration statement
has the following form:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    #if build configuration
    ```

-   ``` {.code-voice}
    statements
    ```

-   ``` {.code-voice}
    #endif
    ```

</div>

Unlike the condition of an `if`{.code-voice} statement, the *build
configuration* is evaluated at compile time. As a result, the
*statements* are compiled and executed only if the *build configuration*
evaluates to `true`{.code-voice} at compile time.

The *build configuration* can include the `true`{.code-voice} and
`false`{.code-voice} Boolean literals, an identifier used with the
`-D`{.code-voice} command line flag, or any of the platform testing
functions listed in the table below.

<div class="tableholder">

+--------------------------------------+--------------------------------------+
| Function                             | Valid arguments                      |
+======================================+======================================+
| `os()`{.code-voice}                  | `OSX`{.code-voice},                  |
|                                      | `iOS`{.code-voice},                  |
|                                      | `watchOS`{.code-voice},              |
|                                      | `tvOS`{.code-voice}                  |
+--------------------------------------+--------------------------------------+
| `arch()`{.code-voice}                | `i386`{.code-voice},                 |
|                                      | `x86_64`{.code-voice},               |
|                                      | `arm`{.code-voice},                  |
|                                      | `arm64`{.code-voice}                 |
+--------------------------------------+--------------------------------------+

</div>

<div class="note">

Note

The `arch(arm)`{.code-voice} build configuration does not return
`true`{.code-voice} for ARM 64 devices. The `arch(i386)`{.code-voice}
build configuration returns `true`{.code-voice} when code is compiled
for the 32–bit iOS simulator.

</div>

You can combine build configurations using the logical operators
`&&`{.code-voice}, `||`{.code-voice}, and `!`{.code-voice} and use
parentheses for grouping.

Similar to an `if`{.code-voice} statement, you can add multiple
conditional branches to test for different build configurations. You can
add any number of additional branches using `#elseif`{.code-voice}
clauses. You can also add a final additional branch using an
`#else`{.code-voice} clause. Build configuration statements that contain
multiple branches have the following form:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    #if build configuration 1
    ```

-   ``` {.code-voice}
    statements to compile if build configuration 1 is true
    ```

-   ``` {.code-voice}
    #elseif build configuration 2
    ```

-   ``` {.code-voice}
    statements to compile if build configuration 2 is true
    ```

-   ``` {.code-voice}
    #else
    ```

-   ``` {.code-voice}
    statements to compile if both build configurations are false
    ```

-   ``` {.code-voice}
    #endif
    ```

</div>

<div class="note">

Note

Each statement in the body of a build configuration statement is parsed
even if it’s not complied.

</div>

<div class="syntax-defs">

Grammar of a build configuration statement

<div class="syntax-defs-group">

[‌](){#build-configuration-statement} <span class="syntax-def-name">
build-configuration-statement </span> <span class="arrow"> →
</span>`#if`{.literal}<span
class="syntactic-cat">[build-configuration](Statements.md#build-configuration)</span><span
class="optional"><span
class="syntactic-cat">[statements](Statements.md#statements)</span>~opt~</span><span
class="optional"><span
class="syntactic-cat">[build-configuration-elseif-clauses](Statements.md#build-configuration-elseif-clauses)</span>~opt~</span><span
class="optional"><span
class="syntactic-cat">[build-configuration-else-clause](Statements.md#build-configuration-else-clause)</span>~opt~</span>`#endif`{.literal}

[‌](){#build-configuration-elseif-clauses} <span
class="syntax-def-name"> build-configuration-elseif-clauses </span>
<span class="arrow"> → </span><span
class="syntactic-cat">[build-configuration-elseif-clause](Statements.md#build-configuration-elseif-clause)</span><span
class="optional"><span
class="syntactic-cat">[build-configuration-elseif-clauses](Statements.md#build-configuration-elseif-clauses)</span>~opt~</span>

[‌](){#build-configuration-elseif-clause} <span class="syntax-def-name">
build-configuration-elseif-clause </span> <span class="arrow"> →
</span>`#elseif`{.literal}<span
class="syntactic-cat">[build-configuration](Statements.md#build-configuration)</span><span
class="optional"><span
class="syntactic-cat">[statements](Statements.md#statements)</span>~opt~</span>

[‌](){#build-configuration-else-clause} <span class="syntax-def-name">
build-configuration-else-clause </span> <span class="arrow"> →
</span>`#else`{.literal}<span class="optional"><span
class="syntactic-cat">[statements](Statements.md#statements)</span>~opt~</span>

</div>

<div class="syntax-defs-group">

[‌](){#build-configuration} <span class="syntax-def-name">
build-configuration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[platform-testing-function](Statements.md#platform-testing-function)</span>

[‌](){#TP40016643-CH33-NoLink_758} <span class="syntax-def-name">
build-configuration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

[‌](){#TP40016643-CH33-NoLink_759} <span class="syntax-def-name">
build-configuration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[boolean-literal](LexicalStructure.md#boolean-literal)</span>

[‌](){#TP40016643-CH33-NoLink_760} <span class="syntax-def-name">
build-configuration </span> <span class="arrow"> →
</span>`(`{.literal}<span
class="syntactic-cat">[build-configuration](Statements.md#build-configuration)</span>`)`{.literal}

[‌](){#TP40016643-CH33-NoLink_761} <span class="syntax-def-name">
build-configuration </span> <span class="arrow"> →
</span>`!`{.literal}<span
class="syntactic-cat">[build-configuration](Statements.md#build-configuration)</span>

[‌](){#TP40016643-CH33-NoLink_762} <span class="syntax-def-name">
build-configuration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[build-configuration](Statements.md#build-configuration)</span>`&&`{.literal}<span
class="syntactic-cat">[build-configuration](Statements.md#build-configuration)</span>

[‌](){#TP40016643-CH33-NoLink_763} <span class="syntax-def-name">
build-configuration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[build-configuration](Statements.md#build-configuration)</span>`||`{.literal}<span
class="syntactic-cat">[build-configuration](Statements.md#build-configuration)</span>

</div>

<div class="syntax-defs-group">

[‌](){#platform-testing-function} <span class="syntax-def-name">
platform-testing-function </span> <span class="arrow"> →
</span>`os`{.literal}`(`{.literal}<span
class="syntactic-cat">[operating-system](Statements.md#operating-system)</span>`)`{.literal}

[‌](){#TP40016643-CH33-NoLink_765} <span class="syntax-def-name">
platform-testing-function </span> <span class="arrow"> →
</span>`arch`{.literal}`(`{.literal}<span
class="syntactic-cat">[architecture](Statements.md#architecture)</span>`)`{.literal}

[‌](){#operating-system} <span class="syntax-def-name"> operating-system
</span> <span class="arrow"> → </span><span class="alternative">
`OSX`{.literal} </span><span class="alternative"> `iOS`{.literal}
</span><span class="alternative"> `watchOS`{.literal} </span><span
class="alternative"> `tvOS`{.literal} </span>

[‌](){#architecture} <span class="syntax-def-name"> architecture </span>
<span class="arrow"> → </span><span class="alternative">
`i386`{.literal} </span><span class="alternative"> `x86_64`{.literal}
</span><span class="alternative"> `arm`{.literal} </span><span
class="alternative"> `arm64`{.literal} </span>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH33-ID540}
### Line Control Statement {#line-control-statement .section-name}

A line control statement is used to specify a line number and filename
that can be different from the line number and filename of the source
code being compiled. Use a line control statement to change the source
code location used by Swift for diagnostic and debugging purposes.

A line control statement has the following form:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    #line line number filename
    ```

</div>

A line control statement changes the values of the
`__LINE__`{.code-voice} and `__FILE__`{.code-voice} literal expressions,
beginning with the line of code following the line control statement.
The *line number* changes the value of `__LINE__`{.code-voice} and is
any integer literal greater than zero. The *filename* changes the value
of `__FILE__`{.code-voice} and is a string literal.

You can reset the source code location back to the default line
numbering and filename by writing a line control statement without
specifying a *line number* and *filename*.

A line control statement must appear on its own line and can’t be the
last line of a source code file.

<div class="syntax-defs">

Grammar of a line control statement

<div class="syntax-defs-group">

[‌](){#line-control-statement} <span class="syntax-def-name">
line-control-statement </span> <span class="arrow"> →
</span>`#line`{.literal}

[‌](){#TP40016643-CH33-NoLink_770} <span class="syntax-def-name">
line-control-statement </span> <span class="arrow"> →
</span>`#line`{.literal}<span
class="syntactic-cat">[line-number](Statements.md#line-number)</span><span
class="syntactic-cat">[file-name](Statements.md#file-name)</span>

[‌](){#line-number} <span class="syntax-def-name"> line-number </span>
<span class="arrow"> → </span><span class="text-description">A decimal
integer greater than zero</span>

[‌](){#file-name} <span class="syntax-def-name"> file-name </span> <span
class="arrow"> → </span><span
class="syntactic-cat">[static-string-literal](LexicalStructure.md#static-string-literal)</span>

</div>

</div>

</div>

</div>

</div>

</div>
