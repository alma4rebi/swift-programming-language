



[‌]()[‌]()
Statements 
----------



In Swift, there are three kinds of statements: simple statements, compiler control statements, and control flow statements. Simple statements are the most common and consist of either an expression or a declaration. Compiler control statements allow the program to change aspects of the compiler’s behavior and include a build configuration and line control statement.

Control flow statements are used to control the flow of execution in a program. There are several types of control flow statements in Swift, including loop statements, branch statements, and control transfer statements. Loop statements allow a block of code to be executed repeatedly, branch statements allow a certain block of code to be executed only when certain conditions are met, and control transfer statements provide a way to alter the order in which code is executed. In addition, Swift provides a `do` statement to introduce scope, and catch and handle errors, and a `defer` statement for running clean-up actions just before the current scope exits.

A semicolon (`;`) can optionally appear after any statement and is used to separate multiple statements if they appear on the same line.



Grammar of a statement



[‌]()

statement


→
[expression](Expressions.md#expression)`;`~opt~

[‌]()

statement


→
[declaration](Declarations.md#declaration)`;`~opt~

[‌]()

statement


→
[loop-statement](Statements.md#loop-statement)`;`~opt~

[‌]()

statement


→
[branch-statement](Statements.md#branch-statement)`;`~opt~

[‌]()

statement


→
[labeled-statement](Statements.md#labeled-statement)`;`~opt~

[‌]()

statement


→
[control-transfer-statement](Statements.md#control-transfer-statement)`;`~opt~

[‌]()

statement


→
[defer-statement](Statements.md#defer-statement)`;`~opt~

[‌]()

statement


→
[do-statement](Statements.md#do-statement)`:`~opt~

[‌]()

statement


→
[compiler-control-statement](Statements.md#compiler-control-statement)

[‌]()

statements


→
[statement](Statements.md#statement)[statements](Statements.md#statements)~opt~









[‌]()
### Loop Statements 

Loop statements allow a block of code to be executed repeatedly, depending on the conditions specified in the loop. Swift has four loop statements: a `for` statement, a `for`-`in` statement, a `while` statement, and a `repeat`-`while` statement.

Control flow in a loop statement can be changed by a `break` statement and a `continue` statement and is discussed in [Break Statement](Statements.md#TP40016643-CH33-ID441) and [Continue Statement](Statements.md#TP40016643-CH33-ID442) below.



Grammar of a loop statement



[‌]()

loop-statement


→
[for-statement](Statements.md#for-statement)

[‌]()

loop-statement


→
[for-in-statement](Statements.md#for-in-statement)

[‌]()

loop-statement


→
[while-statement](Statements.md#while-statement)

[‌]()

loop-statement


→
[repeat-while-statement](Statements.md#repeat-while-statement)







[‌]()
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



[‌]()

for-statement


→
`for`[for-init](Statements.md#for-init)~opt~`;`[expression](Expressions.md#expression)~opt~`;`[expression-list](Expressions.md#expression-list)~opt~[code-block](Declarations.md#code-block)

[‌]()

for-statement


→
`for``(`[for-init](Statements.md#for-init)~opt~`;`[expression](Expressions.md#expression)~opt~`;`[expression-list](Expressions.md#expression-list)~opt~`)`[code-block](Declarations.md#code-block)





[‌]()

for-init


→

[variable-declaration](Declarations.md#variable-declaration)

[expression-list](Expressions.md#expression-list)










[‌]()
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



[‌]()

for-in-statement


→
`for``case`~opt~[pattern](Patterns.md#pattern)`in`[expression](Expressions.md#expression)[where-clause](Statements.md#where-clause)~opt~[code-block](Declarations.md#code-block)









[‌]()
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



[‌]()

while-statement


→
`while`[condition-clause](Statements.md#condition-clause)[code-block](Declarations.md#code-block)





[‌]()

condition-clause


→
[expression](Expressions.md#expression)

[‌]()

condition-clause


→
[expression](Expressions.md#expression)`,`[condition-list](Statements.md#condition-list)

[‌]()

condition-clause


→
[condition-list](Statements.md#condition-list)

[‌]()

condition-clause


→
[availability-condition](Statements.md#availability-condition)`,`[expression](Expressions.md#expression)





[‌]()

condition-list


→

[condition](Statements.md#condition)

[condition](Statements.md#condition)`,`[condition-list](Statements.md#condition-list)


[‌]()

condition


→

[availability-condition](Statements.md#availability-condition)

[case-condition](Statements.md#case-condition)

[optional-binding-condition](Statements.md#optional-binding-condition)


[‌]()

case-condition


→
`case`[pattern](Patterns.md#pattern)[initializer](Declarations.md#initializer)[where-clause](Statements.md#where-clause)~opt~





[‌]()

optional-binding-condition


→
[optional-binding-head](Statements.md#optional-binding-head)[optional-binding-continuation-list](Statements.md#optional-binding-continuation-list)~opt~[where-clause](Statements.md#where-clause)~opt~

[‌]()

optional-binding-head


→
`let`[pattern](Patterns.md#pattern)[initializer](Declarations.md#initializer)

[‌]()

optional-binding-continuation-list


→

[optional-binding-continuation](Statements.md#optional-binding-continuation)

[optional-binding-continuation](Statements.md#optional-binding-continuation)`,`[optional-binding-continuation-list](Statements.md#optional-binding-continuation-list)


[‌]()

optional-binding-continuation


→

[pattern](Patterns.md#pattern)[initializer](Declarations.md#initializer)

[optional-binding-head](Statements.md#optional-binding-head)










[‌]()
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



[‌]()

repeat-while-statement


→
`repeat`[code-block](Declarations.md#code-block)`while`[expression](Expressions.md#expression)











[‌]()
### Branch Statements 

Branch statements allow the program to execute certain parts of code depending on the value of one or more conditions. The values of the conditions specified in a branch statement control how the program branches and, therefore, what block of code is executed. Swift has three branch statements: an `if` statement, a `guard` statement, and a `switch` statement.

Control flow in an `if` statement or a `switch` statement can be changed by a `break` statement and is discussed in [Break Statement](Statements.md#TP40016643-CH33-ID441) below.



Grammar of a branch statement



[‌]()

branch-statement


→
[if-statement](Statements.md#if-statement)

[‌]()

branch-statement


→
[guard-statement](Statements.md#guard-statement)

[‌]()

branch-statement


→
[switch-statement](Statements.md#switch-statement)







[‌]()
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



[‌]()

if-statement


→
`if`[condition-clause](Statements.md#condition-clause)[code-block](Declarations.md#code-block)[else-clause](Statements.md#else-clause)~opt~

[‌]()

else-clause


→

`else`[code-block](Declarations.md#code-block)

`else`[if-statement](Statements.md#if-statement)










[‌]()
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



[‌]()

guard-statement


→
`guard`[condition-clause](Statements.md#condition-clause)`else`[code-block](Declarations.md#code-block)









[‌]()
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







1.  `case` `let` (`x`, `y`) `where` `x` == `y`:







As the above example shows, patterns in a case can also bind constants using the `let` keyword. These constants can then be referenced in a corresponding where clause and throughout the rest of the code within the scope of the case. That said, if the case contains multiple patterns that match the control expression, none of those patterns can contain constant bindings.

A `switch` statement can also include a default case, introduced by the `default` keyword. The code within a default case is executed only if no other cases match the control expression. A `switch` statement can include only one default case, which must appear at the end of the `switch` statement.

Although the actual execution order of pattern-matching operations, and in particular the evaluation order of patterns in cases, is unspecified, pattern matching in a `switch` statement behaves as if the evaluation is performed in source order—that is, the order in which they appear in source code. As a result, if multiple cases contain patterns that evaluate to the same value, and thus can match the value of the control expression, the program executes only the code within the first matching case in source order.



[‌]()
### Switch Statements Must Be Exhaustive 

In Swift, every possible value of the control expression’s type must match the value of at least one pattern of a case. When this simply isn’t feasible (for instance, when the control expression’s type is `Int`), you can include a default case to satisfy the requirement.





[‌]()
### Execution Does Not Fall Through Cases Implicitly 

After the code within a matched case has finished executing, the program exits from the `switch` statement. Program execution does not continue or “fall through” to the next case or default case. That said, if you want execution to continue from one case to the next, explicitly include a `fallthrough` statement, which simply consists of the `fallthrough` keyword, in the case from which you want execution to continue. For more information about the `fallthrough` statement, see [Fallthrough Statement](Statements.md#TP40016643-CH33-ID443) below.



Grammar of a switch statement



[‌]()

switch-statement


→
`switch`[expression](Expressions.md#expression)`{`[switch-cases](Statements.md#switch-cases)~opt~`}`

[‌]()

switch-cases


→
[switch-case](Statements.md#switch-case)[switch-cases](Statements.md#switch-cases)~opt~

[‌]()

switch-case


→

[case-label](Statements.md#case-label)[statements](Statements.md#statements)

[default-label](Statements.md#default-label)[statements](Statements.md#statements)






[‌]()

case-label


→
`case`[case-item-list](Statements.md#case-item-list)`:`

[‌]()

case-item-list


→

[pattern](Patterns.md#pattern)[where-clause](Statements.md#where-clause)~opt~

[pattern](Patterns.md#pattern)[where-clause](Statements.md#where-clause)~opt~`,`[case-item-list](Statements.md#case-item-list)


[‌]()

default-label


→
`default``:`





[‌]()

where-clause


→
`where`[where-expression](Statements.md#where-expression)

[‌]()

where-expression


→
[expression](Expressions.md#expression)













[‌]()
### Labeled Statement 

You can prefix a loop statement, an `if` statement, or a `switch` statement with a *statement label*, which consists of the name of the label followed immediately by a colon (:). Use statement labels with `break` and `continue` statements to be explicit about how you want to change control flow in a loop statement or a `switch` statement, as discussed in [Break Statement](Statements.md#TP40016643-CH33-ID441) and [Continue Statement](Statements.md#TP40016643-CH33-ID442) below.

The scope of a labeled statement is the entire statement following the statement label. You can nest labeled statements, but the name of each statement label must be unique.

For more information and to see examples of how to use statement labels, see [Labeled Statements](ControlFlow.md#TP40016643-CH9-ID141) in [Control Flow](ControlFlow.md).



Grammar of a labeled statement



[‌]()

labeled-statement


→

[statement-label](Statements.md#statement-label)[loop-statement](Statements.md#loop-statement)

[statement-label](Statements.md#statement-label)[if-statement](Statements.md#if-statement)

[statement-label](Statements.md#statement-label)[switch-statement](Statements.md#switch-statement)


[‌]()

statement-label


→
[label-name](Statements.md#label-name)`:`

[‌]()

label-name


→
[identifier](LexicalStructure.md#identifier)









[‌]()
### Control Transfer Statements 

Control transfer statements can change the order in which code in your program is executed by unconditionally transferring program control from one piece of code to another. Swift has five control transfer statements: a `break` statement, a `continue` statement, a `fallthrough` statement, a `return` statement, and a `throw` statement.



Grammar of a control transfer statement



[‌]()

control-transfer-statement


→
[break-statement](Statements.md#break-statement)

[‌]()

control-transfer-statement


→
[continue-statement](Statements.md#continue-statement)

[‌]()

control-transfer-statement


→
[fallthrough-statement](Statements.md#fallthrough-statement)

[‌]()

control-transfer-statement


→
[return-statement](Statements.md#return-statement)

[‌]()

control-transfer-statement


→
[throw-statement](Statements.md#throw-statement)







[‌]()
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



[‌]()

break-statement


→
`break`[label-name](Statements.md#label-name)~opt~









[‌]()
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



[‌]()

continue-statement


→
`continue`[label-name](Statements.md#label-name)~opt~









[‌]()
### Fallthrough Statement 

A `fallthrough` statement consists of the `fallthrough` keyword and occurs only in a case block of a `switch` statement. A `fallthrough` statement causes program execution to continue from one case in a `switch` statement to the next case. Program execution continues to the next case even if the patterns of the case label do not match the value of the `switch` statement’s control expression.

A `fallthrough` statement can appear anywhere inside a `switch` statement, not just as the last statement of a case block, but it can’t be used in the final case block. It also cannot transfer control into a case block whose pattern contains value binding patterns.

For an example of how to use a `fallthrough` statement in a `switch` statement, see [Control Transfer Statements](ControlFlow.md#TP40016643-CH9-ID135) in [Control Flow](ControlFlow.md).



Grammar of a fallthrough statement



[‌]()

fallthrough-statement


→
`fallthrough`









[‌]()
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



[‌]()

return-statement


→
`return`[expression](Expressions.md#expression)~opt~









[‌]()
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



[‌]()

availability-condition


→
`#available``(`[availability-arguments](Statements.md#availability-arguments)`)`

[‌]()

availability-arguments


→

[availability-argument](Statements.md#availability-argument)

[availability-argument](Statements.md#availability-argument)`,`[availability-arguments](Statements.md#availability-arguments)


[‌]()

availability-argument


→
[platform-name](Statements.md#platform-name)[platform-version](Statements.md#platform-version)

[‌]()

availability-argument


→
`*`





[‌]()

platform-name


→

`iOS`

`iOSApplicationExtension`


[‌]()

platform-name


→

`OSX`

`OSXApplicationExtension`


[‌]()

platform-name


→
`watchOS`

[‌]()

platform-version


→
[decimal-digits](LexicalStructure.md#decimal-digits)

[‌]()

platform-version


→
[decimal-digits](LexicalStructure.md#decimal-digits)`.`[decimal-digits](LexicalStructure.md#decimal-digits)

[‌]()

platform-version


→
[decimal-digits](LexicalStructure.md#decimal-digits)`.`[decimal-digits](LexicalStructure.md#decimal-digits)`.`[decimal-digits](LexicalStructure.md#decimal-digits)









[‌]()
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



[‌]()

throw-statement


→
`throw`[expression](Expressions.md#expression)











[‌]()
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







1.  `func` `f`() {
2.  `    defer` { `print`(`"First"`) }
3.  `    defer` { `print`(`"Second"`) }
4.  `    defer` { `print`(`"Third"`) }
5.  `}`
6.  `f`()
7.  `// prints "Third"`
8.  `// prints "Second"`
9.  `// prints "First"`







The statements in the `defer` statement can’t transfer program control outside of the `defer` statement.



Grammar of a defer statement



[‌]()

defer-statement


→
`defer`[code-block](Declarations.md#code-block)









[‌]()
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



[‌]()

do-statement


→
`do`[code-block](Declarations.md#code-block)[catch-clauses](Statements.md#catch-clauses)~opt~

[‌]()

catch-clauses


→
[catch-clause](Statements.md#catch-clause)[catch-clauses](Statements.md#catch-clauses)~opt~

[‌]()

catch-clause


→
`catch`[pattern](Patterns.md#pattern)~opt~[where-clause](Statements.md#where-clause)~opt~[code-block](Declarations.md#code-block)









[‌]()
### Compiler Control Statements 

Compiler control statements allow the program to change aspects of the compiler’s behavior. Swift has two complier control statements: a build configuration statement and a line control statement.



Grammar of a compiler control statement



[‌]()

compiler-control-statement


→
[build-configuration-statement](Statements.md#build-configuration-statement)

[‌]()

compiler-control-statement


→
[line-control-statement](Statements.md#line-control-statement)







[‌]()
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



[‌]()

build-configuration-statement


→
`#if`[build-configuration](Statements.md#build-configuration)[statements](Statements.md#statements)~opt~[build-configuration-elseif-clauses](Statements.md#build-configuration-elseif-clauses)~opt~[build-configuration-else-clause](Statements.md#build-configuration-else-clause)~opt~`#endif`

[‌]()

build-configuration-elseif-clauses


→
[build-configuration-elseif-clause](Statements.md#build-configuration-elseif-clause)[build-configuration-elseif-clauses](Statements.md#build-configuration-elseif-clauses)~opt~

[‌]()

build-configuration-elseif-clause


→
`#elseif`[build-configuration](Statements.md#build-configuration)[statements](Statements.md#statements)~opt~

[‌]()

build-configuration-else-clause


→
`#else`[statements](Statements.md#statements)~opt~





[‌]()

build-configuration


→
[platform-testing-function](Statements.md#platform-testing-function)

[‌]()

build-configuration


→
[identifier](LexicalStructure.md#identifier)

[‌]()

build-configuration


→
[boolean-literal](LexicalStructure.md#boolean-literal)

[‌]()

build-configuration


→
`(`[build-configuration](Statements.md#build-configuration)`)`

[‌]()

build-configuration


→
`!`[build-configuration](Statements.md#build-configuration)

[‌]()

build-configuration


→
[build-configuration](Statements.md#build-configuration)`&&`[build-configuration](Statements.md#build-configuration)

[‌]()

build-configuration


→
[build-configuration](Statements.md#build-configuration)`||`[build-configuration](Statements.md#build-configuration)





[‌]()

platform-testing-function


→
`os``(`[operating-system](Statements.md#operating-system)`)`

[‌]()

platform-testing-function


→
`arch``(`[architecture](Statements.md#architecture)`)`

[‌]()

operating-system


→

`OSX`

`iOS`

`watchOS`

`tvOS`


[‌]()

architecture


→

`i386`

`x86_64`

`arm`

`arm64`










[‌]()
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



[‌]()

line-control-statement


→
`#line`

[‌]()

line-control-statement


→
`#line`[line-number](Statements.md#line-number)[file-name](Statements.md#file-name)

[‌]()

line-number


→
A decimal integer greater than zero

[‌]()

file-name


→
[static-string-literal](LexicalStructure.md#static-string-literal)












