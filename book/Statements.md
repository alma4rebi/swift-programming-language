Statements
----------

In Swift, there are three kinds of statements: simple statements, compiler control statements, and control flow statements. Simple statements are the most common and consist of either an expression or a declaration. Compiler control statements allow the program to change aspects of the compiler’s behavior and include a build configuration and line control statement.

Control flow statements are used to control the flow of execution in a program. There are several types of control flow statements in Swift, including loop statements, branch statements, and control transfer statements. Loop statements allow a block of code to be executed repeatedly, branch statements allow a certain block of code to be executed only when certain conditions are met, and control transfer statements provide a way to alter the order in which code is executed. In addition, Swift provides a `do` statement to introduce scope, and catch and handle errors, and a `defer` statement for running clean-up actions just before the current scope exits.

A semicolon (`;`) can optionally appear after any statement and is used to separate multiple statements if they appear on the same line.

Grammar of a statement

<span class="syntax-def-name">
statement

<span class="arrow">
→
<span class="syntactic-cat">[expression](Expressions.md#expression)<span class="optional">`;`~opt~

<span class="syntax-def-name">
statement

<span class="arrow">
→
<span class="syntactic-cat">[declaration](Declarations.md#declaration)<span class="optional">`;`~opt~

<span class="syntax-def-name">
statement

<span class="arrow">
→
<span class="syntactic-cat">[loop-statement](Statements.md#loop-statement)<span class="optional">`;`~opt~

<span class="syntax-def-name">
statement

<span class="arrow">
→
<span class="syntactic-cat">[branch-statement](Statements.md#branch-statement)<span class="optional">`;`~opt~

<span class="syntax-def-name">
statement

<span class="arrow">
→
<span class="syntactic-cat">[labeled-statement](Statements.md#labeled-statement)<span class="optional">`;`~opt~

<span class="syntax-def-name">
statement

<span class="arrow">
→
<span class="syntactic-cat">[control-transfer-statement](Statements.md#control-transfer-statement)<span class="optional">`;`~opt~

<span class="syntax-def-name">
statement

<span class="arrow">
→
<span class="syntactic-cat">[defer-statement](Statements.md#defer-statement)<span class="optional">`;`~opt~

<span class="syntax-def-name">
statement

<span class="arrow">
→
<span class="syntactic-cat">[do-statement](Statements.md#do-statement)<span class="optional">`:`~opt~

<span class="syntax-def-name">
statement

<span class="arrow">
→
<span class="syntactic-cat">[compiler-control-statement](Statements.md#compiler-control-statement)

<span class="syntax-def-name">
statements

<span class="arrow">
→
<span class="syntactic-cat">[statement](Statements.md#statement)<span class="optional"><span class="syntactic-cat">[statements](Statements.md#statements)~opt~

### Loop Statements

Loop statements allow a block of code to be executed repeatedly, depending on the conditions specified in the loop. Swift has four loop statements: a `for` statement, a `for`-`in` statement, a `while` statement, and a `repeat`-`while` statement.

Control flow in a loop statement can be changed by a `break` statement and a `continue` statement and is discussed in [Break Statement](Statements.md#TP40016643-CH33-ID441) and [Continue Statement](Statements.md#TP40016643-CH33-ID442) below.

Grammar of a loop statement

<span class="syntax-def-name">
loop-statement

<span class="arrow">
→
<span class="syntactic-cat">[for-statement](Statements.md#for-statement)

<span class="syntax-def-name">
loop-statement

<span class="arrow">
→
<span class="syntactic-cat">[for-in-statement](Statements.md#for-in-statement)

<span class="syntax-def-name">
loop-statement

<span class="arrow">
→
<span class="syntactic-cat">[while-statement](Statements.md#while-statement)

<span class="syntax-def-name">
loop-statement

<span class="arrow">
→
<span class="syntactic-cat">[repeat-while-statement](Statements.md#repeat-while-statement)

### For Statement

A `for` statement allows a block of code to be executed repeatedly while incrementing a counter, as long as a condition remains true.

A `for` statement has the following form:

-   ```
    for initialization; condition; increment {
    ```

-   ```
        statements
    ```

-   ```
    }
    ```

The semicolons between the *initialization*, *condition*, and *increment* are required. The braces around the *statements* in the body of the loop are also required.

A `for` statement is executed as follows:

1.  The *initialization* is evaluated only once. It is typically used to declare and initialize any variables that are needed for the remainder of the loop.

2.  The *condition* expression is evaluated.

    If `true`, the program executes the *statements*, and execution continues to step 3. If `false`, the program does not execute the *statements* or the *increment* expression, and the program is finished executing the `for` statement.

3.  The *increment* expression is evaluated, and execution returns to step 2.

Variables defined within the *initialization* are valid only within the scope of the `for` statement itself.

The value of the *condition* expression must have a type that conforms to the `BooleanType` protocol.

Grammar of a for statement

<span class="syntax-def-name">
for-statement

<span class="arrow">
→
`for`<span class="optional"><span class="syntactic-cat">[for-init](Statements.md#for-init)~opt~`;`<span class="optional"><span class="syntactic-cat">[expression](Expressions.md#expression)~opt~`;`<span class="optional"><span class="syntactic-cat">[expression-list](Expressions.md#expression-list)~opt~<span class="syntactic-cat">[code-block](Declarations.md#code-block)

<span class="syntax-def-name">
for-statement

<span class="arrow">
→
`for``(`<span class="optional"><span class="syntactic-cat">[for-init](Statements.md#for-init)~opt~`;`<span class="optional"><span class="syntactic-cat">[expression](Expressions.md#expression)~opt~`;`<span class="optional"><span class="syntactic-cat">[expression-list](Expressions.md#expression-list)~opt~`)`<span class="syntactic-cat">[code-block](Declarations.md#code-block)

<span class="syntax-def-name">
for-init

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[variable-declaration](Declarations.md#variable-declaration)
<span class="alternative">
<span class="syntactic-cat">[expression-list](Expressions.md#expression-list)

### For-In Statement

A `for`-`in` statement allows a block of code to be executed once for each item in a collection (or any type) that conforms to the `SequenceType` protocol.

A `for`-`in` statement has the following form:

-   ```
    for item in collection {
    ```

-   ```
        statements
    ```

-   ```
    }
    ```

The `generate()` method is called on the *collection* expression to obtain a value of a generator type—that is, a type that conforms to the `GeneratorType` protocol. The program begins executing a loop by calling the `next()` method on the stream. If the value returned is not `None`, it is assigned to the *item* pattern, the program executes the *statements*, and then continues execution at the beginning of the loop. Otherwise, the program does not perform assignment or execute the *statements*, and it is finished executing the `for`-`in` statement.

Grammar of a for-in statement

<span class="syntax-def-name">
for-in-statement

<span class="arrow">
→
`for`<span class="optional">`case`~opt~<span class="syntactic-cat">[pattern](Patterns.md#pattern)`in`<span class="syntactic-cat">[expression](Expressions.md#expression)<span class="optional"><span class="syntactic-cat">[where-clause](Statements.md#where-clause)~opt~<span class="syntactic-cat">[code-block](Declarations.md#code-block)

### While Statement

A `while` statement allows a block of code to be executed repeatedly, as long as a condition remains true.

A `while` statement has the following form:

-   ```
    while condition {
    ```

-   ```
        statements
    ```

-   ```
    }
    ```

A `while` statement is executed as follows:

1.  The *condition* is evaluated.

    If `true`, execution continues to step 2. If `false`, the program is finished executing the `while` statement.

2.  The program executes the *statements*, and execution returns to step 1.

Because the value of the *condition* is evaluated before the *statements* are executed, the *statements* in a `while` statement can be executed zero or more times.

The value of the *condition* must have a type that conforms to the `BooleanType` protocol. The condition can also be an optional binding declaration, as discussed in [Optional Binding](TheBasics.md#TP40016643-CH5-ID333).

Grammar of a while statement

<span class="syntax-def-name">
while-statement

<span class="arrow">
→
`while`<span class="syntactic-cat">[condition-clause](Statements.md#condition-clause)<span class="syntactic-cat">[code-block](Declarations.md#code-block)

<span class="syntax-def-name">
condition-clause

<span class="arrow">
→
<span class="syntactic-cat">[expression](Expressions.md#expression)

<span class="syntax-def-name">
condition-clause

<span class="arrow">
→
<span class="syntactic-cat">[expression](Expressions.md#expression)`,`<span class="syntactic-cat">[condition-list](Statements.md#condition-list)

<span class="syntax-def-name">
condition-clause

<span class="arrow">
→
<span class="syntactic-cat">[condition-list](Statements.md#condition-list)

<span class="syntax-def-name">
condition-clause

<span class="arrow">
→
<span class="syntactic-cat">[availability-condition](Statements.md#availability-condition)`,`<span class="syntactic-cat">[expression](Expressions.md#expression)

<span class="syntax-def-name">
condition-list

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[condition](Statements.md#condition)
<span class="alternative">
<span class="syntactic-cat">[condition](Statements.md#condition)`,`<span class="syntactic-cat">[condition-list](Statements.md#condition-list)

<span class="syntax-def-name">
condition

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[availability-condition](Statements.md#availability-condition)
<span class="alternative">
<span class="syntactic-cat">[case-condition](Statements.md#case-condition)
<span class="alternative">
<span class="syntactic-cat">[optional-binding-condition](Statements.md#optional-binding-condition)

<span class="syntax-def-name">
case-condition

<span class="arrow">
→
`case`<span class="syntactic-cat">[pattern](Patterns.md#pattern)<span class="syntactic-cat">[initializer](Declarations.md#initializer)<span class="optional"><span class="syntactic-cat">[where-clause](Statements.md#where-clause)~opt~

<span class="syntax-def-name">
optional-binding-condition

<span class="arrow">
→
<span class="syntactic-cat">[optional-binding-head](Statements.md#optional-binding-head)<span class="optional"><span class="syntactic-cat">[optional-binding-continuation-list](Statements.md#optional-binding-continuation-list)~opt~<span class="optional"><span class="syntactic-cat">[where-clause](Statements.md#where-clause)~opt~

<span class="syntax-def-name">
optional-binding-head

<span class="arrow">
→
`let`<span class="syntactic-cat">[pattern](Patterns.md#pattern)<span class="syntactic-cat">[initializer](Declarations.md#initializer)

<span class="syntax-def-name">
optional-binding-continuation-list

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[optional-binding-continuation](Statements.md#optional-binding-continuation)
<span class="alternative">
<span class="syntactic-cat">[optional-binding-continuation](Statements.md#optional-binding-continuation)`,`<span class="syntactic-cat">[optional-binding-continuation-list](Statements.md#optional-binding-continuation-list)

<span class="syntax-def-name">
optional-binding-continuation

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[pattern](Patterns.md#pattern)<span class="syntactic-cat">[initializer](Declarations.md#initializer)
<span class="alternative">
<span class="syntactic-cat">[optional-binding-head](Statements.md#optional-binding-head)

### Repeat-While Statement

A `repeat`-`while` statement allows a block of code to be executed one or more times, as long as a condition remains true.

A `repeat`-`while` statement has the following form:

-   ```
    repeat {
    ```

-   ```
        statements
    ```

-   ```
    } while condition
    ```

A `repeat`-`while` statement is executed as follows:

1.  The program executes the *statements*, and execution continues to step 2.

2.  The *condition* is evaluated.

    If `true`, execution returns to step 1. If `false`, the program is finished executing the `repeat`-`while` statement.

Because the value of the *condition* is evaluated after the *statements* are executed, the *statements* in a `repeat`-`while` statement are executed at least once.

The value of the *condition* must have a type that conforms to the `BooleanType` protocol. The condition can also be an optional binding declaration, as discussed in [Optional Binding](TheBasics.md#TP40016643-CH5-ID333).

Grammar of a repeat-while statement

<span class="syntax-def-name">
repeat-while-statement

<span class="arrow">
→
`repeat`<span class="syntactic-cat">[code-block](Declarations.md#code-block)`while`<span class="syntactic-cat">[expression](Expressions.md#expression)

### Branch Statements

Branch statements allow the program to execute certain parts of code depending on the value of one or more conditions. The values of the conditions specified in a branch statement control how the program branches and, therefore, what block of code is executed. Swift has three branch statements: an `if` statement, a `guard` statement, and a `switch` statement.

Control flow in an `if` statement or a `switch` statement can be changed by a `break` statement and is discussed in [Break Statement](Statements.md#TP40016643-CH33-ID441) below.

Grammar of a branch statement

<span class="syntax-def-name">
branch-statement

<span class="arrow">
→
<span class="syntactic-cat">[if-statement](Statements.md#if-statement)

<span class="syntax-def-name">
branch-statement

<span class="arrow">
→
<span class="syntactic-cat">[guard-statement](Statements.md#guard-statement)

<span class="syntax-def-name">
branch-statement

<span class="arrow">
→
<span class="syntactic-cat">[switch-statement](Statements.md#switch-statement)

### If Statement

An `if` statement is used for executing code based on the evaluation of one or more conditions.

There are two basic forms of an `if` statement. In each form, the opening and closing braces are required.

The first form allows code to be executed only when a condition is true and has the following form:

-   ```
    if condition {
    ```

-   ```
        statements
    ```

-   ```
    }
    ```

The second form of an `if` statement provides an additional *else clause* (introduced by the `else` keyword) and is used for executing one part of code when the condition is true and another part of code when the same condition is false. When a single else clause is present, an `if` statement has the following form:

-   ```
    if condition {
    ```

-   ```
        statements to execute if condition is true
    ```

-   ```
    } else {
    ```

-   ```
        statements to execute if condition is false
    ```

-   ```
    }
    ```

The else clause of an `if` statement can contain another `if` statement to test more than one condition. An `if` statement chained together in this way has the following form:

-   ```
    if condition 1 {
    ```

-   ```
        statements to execute if condition 1 is true
    ```

-   ```
    } else if condition 2 {
    ```

-   ```
        statements to execute if condition 2 is true
    ```

-   ```
    } else {
    ```

-   ```
        statements to execute if both conditions are false
    ```

-   ```
    }
    ```

The value of any condition in an `if` statement must have a type that conforms to the `BooleanType` protocol. The condition can also be an optional binding declaration, as discussed in [Optional Binding](TheBasics.md#TP40016643-CH5-ID333).

Grammar of an if statement

<span class="syntax-def-name">
if-statement

<span class="arrow">
→
`if`<span class="syntactic-cat">[condition-clause](Statements.md#condition-clause)<span class="syntactic-cat">[code-block](Declarations.md#code-block)<span class="optional"><span class="syntactic-cat">[else-clause](Statements.md#else-clause)~opt~

<span class="syntax-def-name">
else-clause

<span class="arrow">
→
<span class="alternative">
`else`<span class="syntactic-cat">[code-block](Declarations.md#code-block)
<span class="alternative">
`else`<span class="syntactic-cat">[if-statement](Statements.md#if-statement)

### Guard Statement

A `guard` statement is used to transfer program control out of a scope if one or more conditions aren’t met.

A `guard` statement has the following form:

-   ```
    guard condition else {
    ```

-   ```
        statements
    ```

-   ```
    }
    ```

The value of any condition in a `guard` statement must have a type that conforms to the `BooleanType` protocol. The condition can also be an optional binding declaration, as discussed in [Optional Binding](TheBasics.md#TP40016643-CH5-ID333).

Any constants assigned a value from an optional binding declaration in a `guard` statement condition can be used for the rest of the guard statement’s enclosing scope.

The `else` clause of a `guard` statement is required, and must either call a function marked with the `noreturn` attribute or transfer program control outside the guard statement’s enclosing scope using one of the following statements:

-   `return`

-   `break`

-   `continue`

-   `throw`

Control transfer statements are discussed in [Control Transfer Statements](Statements.md#TP40016643-CH33-ID440) below.

Grammar of a guard statement

<span class="syntax-def-name">
guard-statement

<span class="arrow">
→
`guard`<span class="syntactic-cat">[condition-clause](Statements.md#condition-clause)`else`<span class="syntactic-cat">[code-block](Declarations.md#code-block)

### Switch Statement

A `switch` statement allows certain blocks of code to be executed depending on the value of a control expression.

A `switch` statement has the following form:

-   ```
    switch control expression {
    ```

-   ```
    case pattern 1:
    ```

-   ```
        statements
    ```

-   ```
    case pattern 2 where condition:
    ```

-   ```
        statements
    ```

-   ```
    case pattern 3 where condition,
    ```

-   ```
    pattern 4 where condition:
    ```

-   ```
        statements
    ```

-   ```
    default:
    ```

-   ```
        statements
    ```

-   ```
    }
    ```

The *control expression* of the `switch` statement is evaluated and then compared with the patterns specified in each case. If a match is found, the program executes the *statements* listed within the scope of that case. The scope of each case can’t be empty. As a result, you must include at least one statement following the colon (`:`) of each case label. Use a single `break` statement if you don’t intend to execute any code in the body of a matched case.

The values of expressions your code can branch on are very flexible. For instance, in addition to the values of scalar types, such as integers and characters, your code can branch on the values of any type, including floating-point numbers, strings, tuples, instances of custom classes, and optionals. The value of the *control expression* can even be matched to the value of a case in an enumeration and checked for inclusion in a specified range of values. For examples of how to use these various types of values in `switch` statements, see [Switch](ControlFlow.md#TP40016643-CH9-ID129) in [Control Flow](ControlFlow.md).

A `switch` case can optionally contain a where clause after each pattern. A *where clause* is introduced by the `where` keyword followed by an expression, and is used to provide an additional condition before a pattern in a case is considered matched to the *control expression*. If a where clause is present, the *statements* within the relevant case are executed only if the value of the *control expression* matches one of the patterns of the case and the expression of the where clause evaluates to `true`. For instance, a *control expression* matches the case in the example below only if it is a tuple that contains two elements of the same value, such as `(1, 1)`.

    case let (x, y) where x == y:

As the above example shows, patterns in a case can also bind constants using the `let` keyword. These constants can then be referenced in a corresponding where clause and throughout the rest of the code within the scope of the case. That said, if the case contains multiple patterns that match the control expression, none of those patterns can contain constant bindings.

A `switch` statement can also include a default case, introduced by the `default` keyword. The code within a default case is executed only if no other cases match the control expression. A `switch` statement can include only one default case, which must appear at the end of the `switch` statement.

Although the actual execution order of pattern-matching operations, and in particular the evaluation order of patterns in cases, is unspecified, pattern matching in a `switch` statement behaves as if the evaluation is performed in source order—that is, the order in which they appear in source code. As a result, if multiple cases contain patterns that evaluate to the same value, and thus can match the value of the control expression, the program executes only the code within the first matching case in source order.

### Switch Statements Must Be Exhaustive

In Swift, every possible value of the control expression’s type must match the value of at least one pattern of a case. When this simply isn’t feasible (for instance, when the control expression’s type is `Int`), you can include a default case to satisfy the requirement.

### Execution Does Not Fall Through Cases Implicitly

After the code within a matched case has finished executing, the program exits from the `switch` statement. Program execution does not continue or “fall through” to the next case or default case. That said, if you want execution to continue from one case to the next, explicitly include a `fallthrough` statement, which simply consists of the `fallthrough` keyword, in the case from which you want execution to continue. For more information about the `fallthrough` statement, see [Fallthrough Statement](Statements.md#TP40016643-CH33-ID443) below.

Grammar of a switch statement

<span class="syntax-def-name">
switch-statement

<span class="arrow">
→
`switch`<span class="syntactic-cat">[expression](Expressions.md#expression)`{`<span class="optional"><span class="syntactic-cat">[switch-cases](Statements.md#switch-cases)~opt~`}`

<span class="syntax-def-name">
switch-cases

<span class="arrow">
→
<span class="syntactic-cat">[switch-case](Statements.md#switch-case)<span class="optional"><span class="syntactic-cat">[switch-cases](Statements.md#switch-cases)~opt~

<span class="syntax-def-name">
switch-case

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[case-label](Statements.md#case-label)<span class="syntactic-cat">[statements](Statements.md#statements)
<span class="alternative">
<span class="syntactic-cat">[default-label](Statements.md#default-label)<span class="syntactic-cat">[statements](Statements.md#statements)

<span class="syntax-def-name">
case-label

<span class="arrow">
→
`case`<span class="syntactic-cat">[case-item-list](Statements.md#case-item-list)`:`

<span class="syntax-def-name">
case-item-list

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[pattern](Patterns.md#pattern)<span class="optional"><span class="syntactic-cat">[where-clause](Statements.md#where-clause)~opt~
<span class="alternative">
<span class="syntactic-cat">[pattern](Patterns.md#pattern)<span class="optional"><span class="syntactic-cat">[where-clause](Statements.md#where-clause)~opt~`,`<span class="syntactic-cat">[case-item-list](Statements.md#case-item-list)

<span class="syntax-def-name">
default-label

<span class="arrow">
→
`default``:`

<span class="syntax-def-name">
where-clause

<span class="arrow">
→
`where`<span class="syntactic-cat">[where-expression](Statements.md#where-expression)

<span class="syntax-def-name">
where-expression

<span class="arrow">
→
<span class="syntactic-cat">[expression](Expressions.md#expression)

### Labeled Statement

You can prefix a loop statement, an `if` statement, or a `switch` statement with a *statement label*, which consists of the name of the label followed immediately by a colon (:). Use statement labels with `break` and `continue` statements to be explicit about how you want to change control flow in a loop statement or a `switch` statement, as discussed in [Break Statement](Statements.md#TP40016643-CH33-ID441) and [Continue Statement](Statements.md#TP40016643-CH33-ID442) below.

The scope of a labeled statement is the entire statement following the statement label. You can nest labeled statements, but the name of each statement label must be unique.

For more information and to see examples of how to use statement labels, see [Labeled Statements](ControlFlow.md#TP40016643-CH9-ID141) in [Control Flow](ControlFlow.md).

Grammar of a labeled statement

<span class="syntax-def-name">
labeled-statement

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[statement-label](Statements.md#statement-label)<span class="syntactic-cat">[loop-statement](Statements.md#loop-statement)
<span class="alternative">
<span class="syntactic-cat">[statement-label](Statements.md#statement-label)<span class="syntactic-cat">[if-statement](Statements.md#if-statement)
<span class="alternative">
<span class="syntactic-cat">[statement-label](Statements.md#statement-label)<span class="syntactic-cat">[switch-statement](Statements.md#switch-statement)

<span class="syntax-def-name">
statement-label

<span class="arrow">
→
<span class="syntactic-cat">[label-name](Statements.md#label-name)`:`

<span class="syntax-def-name">
label-name

<span class="arrow">
→
<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)

### Control Transfer Statements

Control transfer statements can change the order in which code in your program is executed by unconditionally transferring program control from one piece of code to another. Swift has five control transfer statements: a `break` statement, a `continue` statement, a `fallthrough` statement, a `return` statement, and a `throw` statement.

Grammar of a control transfer statement

<span class="syntax-def-name">
control-transfer-statement

<span class="arrow">
→
<span class="syntactic-cat">[break-statement](Statements.md#break-statement)

<span class="syntax-def-name">
control-transfer-statement

<span class="arrow">
→
<span class="syntactic-cat">[continue-statement](Statements.md#continue-statement)

<span class="syntax-def-name">
control-transfer-statement

<span class="arrow">
→
<span class="syntactic-cat">[fallthrough-statement](Statements.md#fallthrough-statement)

<span class="syntax-def-name">
control-transfer-statement

<span class="arrow">
→
<span class="syntactic-cat">[return-statement](Statements.md#return-statement)

<span class="syntax-def-name">
control-transfer-statement

<span class="arrow">
→
<span class="syntactic-cat">[throw-statement](Statements.md#throw-statement)

### Break Statement

A `break` statement ends program execution of a loop, an `if` statement, or a `switch` statement. A `break` statement can consist of only the `break` keyword, or it can consist of the `break` keyword followed by the name of a statement label, as shown below.

-   ```
    break
    ```

-   ```
    break label name
    ```

When a `break` statement is followed by the name of a statement label, it ends program execution of the loop, `if` statement, or `switch` statement named by that label.

When a `break` statement is not followed by the name of a statement label, it ends program execution of the `switch` statement or the innermost enclosing loop statement in which it occurs. You can’t use an unlabeled `break` statement to break out of an `if` statement.

In both cases, program control is then transferred to the first line of code following the enclosing loop or `switch` statement, if any.

For examples of how to use a `break` statement, see [Break](ControlFlow.md#TP40016643-CH9-ID137) and [Labeled Statements](ControlFlow.md#TP40016643-CH9-ID141) in [Control Flow](ControlFlow.md).

Grammar of a break statement

<span class="syntax-def-name">
break-statement

<span class="arrow">
→
`break`<span class="optional"><span class="syntactic-cat">[label-name](Statements.md#label-name)~opt~

### Continue Statement

A `continue` statement ends program execution of the current iteration of a loop statement but does not stop execution of the loop statement. A `continue` statement can consist of only the `continue` keyword, or it can consist of the `continue` keyword followed by the name of a statement label, as shown below.

-   ```
    continue
    ```

-   ```
    continue label name
    ```

When a `continue` statement is followed by the name of a statement label, it ends program execution of the current iteration of the loop statement named by that label.

When a `continue` statement is not followed by the name of a statement label, it ends program execution of the current iteration of the innermost enclosing loop statement in which it occurs.

In both cases, program control is then transferred to the condition of the enclosing loop statement.

In a `for` statement, the increment expression is still evaluated after the `continue` statement is executed, because the increment expression is evaluated after the execution of the loop’s body.

For examples of how to use a `continue` statement, see [Continue](ControlFlow.md#TP40016643-CH9-ID136) and [Labeled Statements](ControlFlow.md#TP40016643-CH9-ID141) in [Control Flow](ControlFlow.md).

Grammar of a continue statement

<span class="syntax-def-name">
continue-statement

<span class="arrow">
→
`continue`<span class="optional"><span class="syntactic-cat">[label-name](Statements.md#label-name)~opt~

### Fallthrough Statement

A `fallthrough` statement consists of the `fallthrough` keyword and occurs only in a case block of a `switch` statement. A `fallthrough` statement causes program execution to continue from one case in a `switch` statement to the next case. Program execution continues to the next case even if the patterns of the case label do not match the value of the `switch` statement’s control expression.

A `fallthrough` statement can appear anywhere inside a `switch` statement, not just as the last statement of a case block, but it can’t be used in the final case block. It also cannot transfer control into a case block whose pattern contains value binding patterns.

For an example of how to use a `fallthrough` statement in a `switch` statement, see [Control Transfer Statements](ControlFlow.md#TP40016643-CH9-ID135) in [Control Flow](ControlFlow.md).

Grammar of a fallthrough statement

<span class="syntax-def-name">
fallthrough-statement

<span class="arrow">
→
`fallthrough`

### Return Statement

A `return` statement occurs in the body of a function or method definition and causes program execution to return to the calling function or method. Program execution continues at the point immediately following the function or method call.

A `return` statement can consist of only the `return` keyword, or it can consist of the `return` keyword followed by an expression, as shown below.

-   ```
    return
    ```

-   ```
    return expression
    ```

When a `return` statement is followed by an expression, the value of the expression is returned to the calling function or method. If the value of the expression does not match the value of the return type declared in the function or method declaration, the expression’s value is converted to the return type before it is returned to the calling function or method.

Note

As described in [Failable Initializers](Declarations.md#TP40016643-CH34-ID376), a special form of the `return` statement (`return nil`) can be used in a failable initializer to indicate initialization failure.

When a `return` statement is not followed by an expression, it can be used only to return from a function or method that does not return a value (that is, when the return type of the function or method is `Void` or `()`).

Grammar of a return statement

<span class="syntax-def-name">
return-statement

<span class="arrow">
→
`return`<span class="optional"><span class="syntactic-cat">[expression](Expressions.md#expression)~opt~

### Availability Condition

An *availability condition* is used as a condition of an `if`, `while`, and `guard` statement to query the availability of APIs at runtime, based on specified platforms arguments.

An availability condition has the following form:

-   ```
    if #available(platform name version, ..., *) {
    ```

-   ```
        statements to execute if the APIs are available
    ```

-   ```
    } else {
    ```

-   ```
        fallback statements to execute if the APIs are unavailable
    ```

-   ```
    }
    ```

You use an availability condition to execute a block of code, depending on whether the APIs you want to use are available at runtime. The compiler uses the information from the availability condition when it verifies that the APIs in that block of code are available.

The availability condition takes a comma-separated list of platform names and versions. Use `iOS`, `OSX`, and `watchOS` for the platform names, and include the corresponding version numbers. The `*` argument is required and specifies that on any other platform, the body of the code block guarded by the availability condition executes on the minimum deployment target specified by your target.

Unlike Boolean conditions, you can’t combine availability conditions using logical operators such as `&&` and `||`.

Grammar of an availability condition

<span class="syntax-def-name">
availability-condition

<span class="arrow">
→
`#available``(`<span class="syntactic-cat">[availability-arguments](Statements.md#availability-arguments)`)`

<span class="syntax-def-name">
availability-arguments

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[availability-argument](Statements.md#availability-argument)
<span class="alternative">
<span class="syntactic-cat">[availability-argument](Statements.md#availability-argument)`,`<span class="syntactic-cat">[availability-arguments](Statements.md#availability-arguments)

<span class="syntax-def-name">
availability-argument

<span class="arrow">
→
<span class="syntactic-cat">[platform-name](Statements.md#platform-name)<span class="syntactic-cat">[platform-version](Statements.md#platform-version)

<span class="syntax-def-name">
availability-argument

<span class="arrow">
→
`*`

<span class="syntax-def-name">
platform-name

<span class="arrow">
→
<span class="alternative">
`iOS`
<span class="alternative">
`iOSApplicationExtension`

<span class="syntax-def-name">
platform-name

<span class="arrow">
→
<span class="alternative">
`OSX`
<span class="alternative">
`OSXApplicationExtension`

<span class="syntax-def-name">
platform-name

<span class="arrow">
→
`watchOS`

<span class="syntax-def-name">
platform-version

<span class="arrow">
→
<span class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)

<span class="syntax-def-name">
platform-version

<span class="arrow">
→
<span class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)`.`<span class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)

<span class="syntax-def-name">
platform-version

<span class="arrow">
→
<span class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)`.`<span class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)`.`<span class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)

### Throw Statement

A `throw` statement occurs in the body of a throwing function or method, or in the body of a closure expression whose type is marked with the `throws` keyword.

A `throw` statement causes a program to end execution of the current scope and begin error propagation to its enclosing scope. The error that’s thrown continues to propagate until it’s handled by a `catch` clause of a `do` statement.

A `throw` statement consists of the `throw` keyword followed by an expression, as shown below.

-   ```
    throw expression
    ```

The value of the *expression* must have a type that conforms to the `ErrorType` protocol.

For an example of how to use a `throw` statement, see [Propagating Errors Using Throwing Functions](ErrorHandling.md#TP40016643-CH42-ID510) in [Error Handling](ErrorHandling.md).

Grammar of a throw statement

<span class="syntax-def-name">
throw-statement

<span class="arrow">
→
`throw`<span class="syntactic-cat">[expression](Expressions.md#expression)

### Defer Statement

A `defer` statement is used for executing code just before transferring program control outside of the scope that the `defer` statement appears in.

A `defer` statement has the following form:

-   ```
    defer {
    ```

-   ```
        statements
    ```

-   ```
    }
    ```

The statements within the `defer` statement are executed no matter how program control is transferred. This means that a `defer` statement can be used, for example, to perform manual resource management such as closing file descriptors, and to perform actions that need to happen even if an error is thrown.

If multiple `defer` statements appear in the same scope, the order they appear is the reverse of the order they are executed. Executing the last `defer` statement in a given scope first means that statements inside that last `defer` statement can refer to resources that will be cleaned up by other `defer` statements.

    func f() {
        defer { print("First") }
        defer { print("Second") }
        defer { print("Third") }
    }
    f()
    // prints "Third"
    // prints "Second"
    // prints "First"

The statements in the `defer` statement can’t transfer program control outside of the `defer` statement.

Grammar of a defer statement

<span class="syntax-def-name">
defer-statement

<span class="arrow">
→
`defer`<span class="syntactic-cat">[code-block](Declarations.md#code-block)

### Do Statement

The `do` statement is used to introduce a new scope and can optionally contain one or more `catch` clauses, which contain patterns that match against defined error conditions. Variables and constants declared in the scope of a `do` statement can be accessed only within that scope.

A `do` statement in Swift is similar to curly braces (`{}`) in C used to delimit a code block, and does not incur a performance cost at runtime.

A `do` statement has the following form:

-   ```
    do {
    ```

-   ```
        try expression
    ```

-   ```
        statements
    ```

-   ```
    } catch pattern 1 {
    ```

-   ```
        statements
    ```

-   ```
    } catch pattern 2 where condition {
    ```

-   ```
        statements
    ```

-   ```
    }
    ```

Like a `switch` statement, the compiler attempts to infer whether `catch` clauses are exhaustive. If such a determination can be made, the error is considered handled. Otherwise, the error automatically propagates out of the containing scope, either to an enclosing `catch` clause or out of the throwing function must handle the error, or the containing function must be declared with `throws`.

To ensure that an error is handled, use a `catch` clause with a pattern that matches all errors, such as a wildcard pattern (`_`). If a `catch` clause does not specify a pattern, the `catch` clause matches and binds any error to a local constant named `error`. For more information about the pattens you can use in a `catch` clause, see [Patterns](Patterns.md).

To see an example of how to use a `do` statement with several `catch` clauses, see [Handling Errors](ErrorHandling.md#TP40016643-CH42-ID512).

Grammar of a do statement

<span class="syntax-def-name">
do-statement

<span class="arrow">
→
`do`<span class="syntactic-cat">[code-block](Declarations.md#code-block)<span class="optional"><span class="syntactic-cat">[catch-clauses](Statements.md#catch-clauses)~opt~

<span class="syntax-def-name">
catch-clauses

<span class="arrow">
→
<span class="syntactic-cat">[catch-clause](Statements.md#catch-clause)<span class="optional"><span class="syntactic-cat">[catch-clauses](Statements.md#catch-clauses)~opt~

<span class="syntax-def-name">
catch-clause

<span class="arrow">
→
`catch`<span class="optional"><span class="syntactic-cat">[pattern](Patterns.md#pattern)~opt~<span class="optional"><span class="syntactic-cat">[where-clause](Statements.md#where-clause)~opt~<span class="syntactic-cat">[code-block](Declarations.md#code-block)

### Compiler Control Statements

Compiler control statements allow the program to change aspects of the compiler’s behavior. Swift has two complier control statements: a build configuration statement and a line control statement.

Grammar of a compiler control statement

<span class="syntax-def-name">
compiler-control-statement

<span class="arrow">
→
<span class="syntactic-cat">[build-configuration-statement](Statements.md#build-configuration-statement)

<span class="syntax-def-name">
compiler-control-statement

<span class="arrow">
→
<span class="syntactic-cat">[line-control-statement](Statements.md#line-control-statement)

### Build Configuration Statement

A build configuration statement allows code to be conditionally compiled depending on the value of one or more build configurations.

Every build configuration statement begins with `#if` and ends with `#endif`. A simple build configuration statement has the following form:

-   ```
    #if build configuration
    ```

-   ```
    statements
    ```

-   ```
    #endif
    ```

Unlike the condition of an `if` statement, the *build configuration* is evaluated at compile time. As a result, the *statements* are compiled and executed only if the *build configuration* evaluates to `true` at compile time.

The *build configuration* can include the `true` and `false` Boolean literals, an identifier used with the `-D` command line flag, or any of the platform testing functions listed in the table below.

+--------------------------------------+--------------------------------------+
| Function                             | Valid arguments                      |
+======================================+======================================+
| `os()`                  | `OSX`,                  |
|                                      | `iOS`,                  |
|                                      | `watchOS`,              |
|                                      | `tvOS`                  |
+--------------------------------------+--------------------------------------+
| `arch()`                | `i386`,                 |
|                                      | `x86_64`,               |
|                                      | `arm`,                  |
|                                      | `arm64`                 |
+--------------------------------------+--------------------------------------+

Note

The `arch(arm)` build configuration does not return `true` for ARM 64 devices. The `arch(i386)` build configuration returns `true` when code is compiled for the 32–bit iOS simulator.

You can combine build configurations using the logical operators `&&`, `||`, and `!` and use parentheses for grouping.

Similar to an `if` statement, you can add multiple conditional branches to test for different build configurations. You can add any number of additional branches using `#elseif` clauses. You can also add a final additional branch using an `#else` clause. Build configuration statements that contain multiple branches have the following form:

-   ```
    #if build configuration 1
    ```

-   ```
    statements to compile if build configuration 1 is true
    ```

-   ```
    #elseif build configuration 2
    ```

-   ```
    statements to compile if build configuration 2 is true
    ```

-   ```
    #else
    ```

-   ```
    statements to compile if both build configurations are false
    ```

-   ```
    #endif
    ```

Note

Each statement in the body of a build configuration statement is parsed even if it’s not complied.

Grammar of a build configuration statement

<span class="syntax-def-name">
build-configuration-statement

<span class="arrow">
→
`#if`<span class="syntactic-cat">[build-configuration](Statements.md#build-configuration)<span class="optional"><span class="syntactic-cat">[statements](Statements.md#statements)~opt~<span class="optional"><span class="syntactic-cat">[build-configuration-elseif-clauses](Statements.md#build-configuration-elseif-clauses)~opt~<span class="optional"><span class="syntactic-cat">[build-configuration-else-clause](Statements.md#build-configuration-else-clause)~opt~`#endif`

<span class="syntax-def-name">
build-configuration-elseif-clauses

<span class="arrow">
→
<span class="syntactic-cat">[build-configuration-elseif-clause](Statements.md#build-configuration-elseif-clause)<span class="optional"><span class="syntactic-cat">[build-configuration-elseif-clauses](Statements.md#build-configuration-elseif-clauses)~opt~

<span class="syntax-def-name">
build-configuration-elseif-clause

<span class="arrow">
→
`#elseif`<span class="syntactic-cat">[build-configuration](Statements.md#build-configuration)<span class="optional"><span class="syntactic-cat">[statements](Statements.md#statements)~opt~

<span class="syntax-def-name">
build-configuration-else-clause

<span class="arrow">
→
`#else`<span class="optional"><span class="syntactic-cat">[statements](Statements.md#statements)~opt~

<span class="syntax-def-name">
build-configuration

<span class="arrow">
→
<span class="syntactic-cat">[platform-testing-function](Statements.md#platform-testing-function)

<span class="syntax-def-name">
build-configuration

<span class="arrow">
→
<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)

<span class="syntax-def-name">
build-configuration

<span class="arrow">
→
<span class="syntactic-cat">[boolean-literal](LexicalStructure.md#boolean-literal)

<span class="syntax-def-name">
build-configuration

<span class="arrow">
→
`(`<span class="syntactic-cat">[build-configuration](Statements.md#build-configuration)`)`

<span class="syntax-def-name">
build-configuration

<span class="arrow">
→
`!`<span class="syntactic-cat">[build-configuration](Statements.md#build-configuration)

<span class="syntax-def-name">
build-configuration

<span class="arrow">
→
<span class="syntactic-cat">[build-configuration](Statements.md#build-configuration)`&&`<span class="syntactic-cat">[build-configuration](Statements.md#build-configuration)

<span class="syntax-def-name">
build-configuration

<span class="arrow">
→
<span class="syntactic-cat">[build-configuration](Statements.md#build-configuration)`||`<span class="syntactic-cat">[build-configuration](Statements.md#build-configuration)

<span class="syntax-def-name">
platform-testing-function

<span class="arrow">
→
`os``(`<span class="syntactic-cat">[operating-system](Statements.md#operating-system)`)`

<span class="syntax-def-name">
platform-testing-function

<span class="arrow">
→
`arch``(`<span class="syntactic-cat">[architecture](Statements.md#architecture)`)`

<span class="syntax-def-name">
operating-system

<span class="arrow">
→
<span class="alternative">
`OSX`
<span class="alternative">
`iOS`
<span class="alternative">
`watchOS`
<span class="alternative">
`tvOS`

<span class="syntax-def-name">
architecture

<span class="arrow">
→
<span class="alternative">
`i386`
<span class="alternative">
`x86_64`
<span class="alternative">
`arm`
<span class="alternative">
`arm64`

### Line Control Statement

A line control statement is used to specify a line number and filename that can be different from the line number and filename of the source code being compiled. Use a line control statement to change the source code location used by Swift for diagnostic and debugging purposes.

A line control statement has the following form:

-   ```
    #line line number filename
    ```

A line control statement changes the values of the `__LINE__` and `__FILE__` literal expressions, beginning with the line of code following the line control statement. The *line number* changes the value of `__LINE__` and is any integer literal greater than zero. The *filename* changes the value of `__FILE__` and is a string literal.

You can reset the source code location back to the default line numbering and filename by writing a line control statement without specifying a *line number* and *filename*.

A line control statement must appear on its own line and can’t be the last line of a source code file.

Grammar of a line control statement

<span class="syntax-def-name">
line-control-statement

<span class="arrow">
→
`#line`

<span class="syntax-def-name">
line-control-statement

<span class="arrow">
→
`#line`<span class="syntactic-cat">[line-number](Statements.md#line-number)<span class="syntactic-cat">[file-name](Statements.md#file-name)

<span class="syntax-def-name">
line-number

<span class="arrow">
→
<span class="text-description">A decimal integer greater than zero

<span class="syntax-def-name">
file-name

<span class="arrow">
→
<span class="syntactic-cat">[static-string-literal](LexicalStructure.md#static-string-literal)

