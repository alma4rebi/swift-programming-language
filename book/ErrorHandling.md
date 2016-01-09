



[‌](){#TP40016643-CH42}[‌](){#TP40016643-CH42-ID508}
Error Handling {#error-handling .chapter-name}
--------------



*Error handling* is the process of responding to and recovering from error conditions in your program. Swift provides first-class support for throwing, catching, propagating, and manipulating recoverable errors at runtime.

Some operations aren’t guaranteed to always complete execution or produce a useful output. Optionals are used to represent the absence of a value, but when an operation fails, it’s often useful to understand what caused the failure, so that your code can respond accordingly.

As an example, consider the task of reading and processing data from a file on disk. There are a number of ways this task can fail, including the file not existing at the specified path, the file not having read permissions, or the file not being encoded in a compatible format. Distinguishing among these different situations allows a program to resolve some errors and to communicate to the user any errors it can’t resolve.



Note

Error handling in Swift interoperates with error handling patterns that use the `NSError`{.code-voice} class in Cocoa and Objective-C. For more information about this class, see Error Handling in *Using Swift with Cocoa and Objective-C (Swift 2.1)*.







[‌](){#TP40016643-CH42-ID509}
### Representing and Throwing Errors {#representing-and-throwing-errors .section-name}

In Swift, errors are represented by values of types that conform to the `ErrorType`{.code-voice} protocol. This empty protocol indicates that a type can be used for error handling.

Swift enumerations are particularly well suited to modeling a group of related error conditions, with associated values allowing for additional information about the nature of an error to be communicated. For example, here’s how you might represent the error conditions of operating a vending machine inside a game:







1.  `enum`{.code-voice} `VendingMachineError`{.vc}: `ErrorType`{.n} {
2.  `    case`{.code-voice} `InvalidSelection`{.vc}
3.  `    case`{.code-voice} `InsufficientFunds`{.vc}(`coinsNeeded`{.vc}: `Int`{.vc})
4.  `    case`{.code-voice} `OutOfStock`{.vc}
5.  `}`{.code-voice}







Throwing an error lets you indicate that something unexpected happened and the normal flow of execution can’t continue. You use a `throw`{.code-voice} statement to throw an error. For example, the following code throws an error to indicate that five additional coins are needed by the vending machine:







1.  `throw`{.code-voice} `VendingMachineError`{.vc}.`InsufficientFunds`{.vc}(`coinsNeeded`{.vc}: `5`{.m})











[‌](){#TP40016643-CH42-ID512}
### Handling Errors {#handling-errors .section-name}

When an error is thrown, some surrounding piece of code must be responsible for handling the error—for example, by correcting the problem, trying an alternative approach, or informing the user of the failure.

There are four ways to handle errors in Swift. You can propagate the error from a function to the code that calls that function, handle the error using a `do`{.code-voice}-`catch`{.code-voice} statement, handle the error as an optional value, or assert that the error will not occur. Each approach is described in a section below.

When a function throws an error, it changes the flow of your program, so it’s important that you can quickly identify places in your code that can throw errors. To identify these places in your code, write the `try`{.code-voice} keyword—or the `try?`{.code-voice} or `try!`{.code-voice} variation—before a piece of code that calls a function, method, or initializer that can throw an error. These keywords are described in the sections below.



Note

Error handling in Swift resembles exception handling in other languages, with the use of the `try`{.code-voice}, `catch`{.code-voice} and `throw`{.code-voice} keywords. Unlike exception handling in many languages—including Objective-C—error handling in Swift does not involve unwinding the call stack, a process that can be computationally expensive. As such, the performance characteristics of a `throw`{.code-voice} statement are comparable to those of a `return`{.code-voice} statement.





[‌](){#TP40016643-CH42-ID510}
### Propagating Errors Using Throwing Functions {#propagating-errors-using-throwing-functions .section-name}

To indicate that a function, method, or initializer can throw an error, you write the `throws`{.code-voice} keyword in the function’s declaration after its parameters. A function marked with `throws`{.code-voice} is called a *throwing function*. If the function specifies a return type, you write the `throws`{.code-voice} keyword before the return arrow (`->`{.code-voice}).







1.  `func`{.code-voice} `canThrowErrors`{.vc}() `throws`{.kt} -&gt; `String`{.n}
2.  ` `{.code-voice}
3.  `func`{.code-voice} `cannotThrowErrors`{.vc}() -&gt; `String`{.n}







A throwing function propagates errors that are thrown inside of it to the scope from which it’s called.



Note

Only throwing functions can propagate errors. Any errors thrown inside a nonthrowing function must be handled inside the function.



In the example below, the `VendingMachine`{.code-voice} class has a `vend(itemNamed:)`{.code-voice} method that throws an appropriate `VendingMachineError`{.code-voice} if the requested item is not available, is out of stock, or has a cost that exceeds the current deposited amount:







1.  `struct`{.code-voice} `Item`{.vc} {
2.  `    var`{.code-voice} `price`{.vc}: `Int`{.n}
3.  `    var`{.code-voice} `count`{.vc}: `Int`{.n}
4.  `}`{.code-voice}
5.  ` `{.code-voice}
6.  `class`{.code-voice} `VendingMachine`{.vc} {
7.  `    var`{.code-voice} `inventory`{.vc} = \[
8.  `        "Candy Bar"`{.code-voice}: `Item`{.vc}(`price`{.vc}: `12`{.m}, `count`{.vc}: `7`{.m}),
9.  `        "Chips"`{.code-voice}: `Item`{.vc}(`price`{.vc}: `10`{.m}, `count`{.vc}: `4`{.m}),
10. `        "Pretzels"`{.code-voice}: `Item`{.vc}(`price`{.vc}: `7`{.m}, `count`{.vc}: `11`{.m})
11. `    ]`{.code-voice}
12. `    var`{.code-voice} `coinsDeposited`{.vc} = `0`{.m}
13. `    func`{.code-voice} `dispenseSnack`{.vc}(`snack`{.vc}: `String`{.n}) {
14. `        print`{.code-voice}(`"Dispensing `{.s}\\(`snack`{.vc})`"`{.s})
15. `    }`{.code-voice}
16. `    `{.code-voice}
17. `    func`{.code-voice} `vend`{.vc}(`itemNamed`{.vc} `name`{.vc}: `String`{.n}) `throws`{.kt} {
18. `        guard`{.code-voice} `var`{.kt} `item`{.vc} = `inventory`{.vc}\[`name`{.vc}\] `else`{.kt} {
19. `            throw`{.code-voice} `VendingMachineError`{.vc}.`InvalidSelection`{.vc}
20. `        }`{.code-voice}
21. `        `{.code-voice}
22. `        guard`{.code-voice} `item`{.vc}.`count`{.vc} &gt; `0`{.m} `else`{.kt} {
23. `            throw`{.code-voice} `VendingMachineError`{.vc}.`OutOfStock`{.vc}
24. `        }`{.code-voice}
25. `        `{.code-voice}
26. `        guard`{.code-voice} `item`{.vc}.`price`{.vc} &lt;= `coinsDeposited`{.vc} `else`{.kt} {
27. `            throw`{.code-voice} `VendingMachineError`{.vc}.`InsufficientFunds`{.vc}(`coinsNeeded`{.vc}: `item`{.vc}.`price`{.vc} - `coinsDeposited`{.vc})
28. `        }`{.code-voice}
29. `        `{.code-voice}
30. `        coinsDeposited`{.code-voice} -= `item`{.vc}.`price`{.vc}
31. `        --item`{.code-voice}.`count`{.vc}
32. `        inventory`{.code-voice}\[`name`{.vc}\] = `item`{.vc}
33. `        dispenseSnack`{.code-voice}(`name`{.vc})
34. `    }`{.code-voice}
35. `}`{.code-voice}







The implementation of the `vend(itemNamed:)`{.code-voice} method uses `guard`{.code-voice} statements to exit the method early and throw appropriate errors if any of the requirements for purchasing a snack aren’t met. Because a `throw`{.code-voice} statement immediately transfers program control, an item will be vended only if all of these requirements are met.

Because the `vend(itemNamed:)`{.code-voice} method propagates any errors it throws, places in your code that call it must either handle the errors directly—using a `do`{.code-voice}-`catch`{.code-voice} statement, `try?`{.code-voice}, or `try!`{.code-voice}—or continue to propagate them. For example, the `buyFavoriteSnack(_:vendingMachine:)`{.code-voice} in the example below is also a throwing function, and any errors that the `vend(itemNamed:)`{.code-voice} method throws will propagate up to the point where the `buyFavoriteSnack(_:vendingMachine:)`{.code-voice} function is called.







1.  `let`{.code-voice} `favoriteSnacks`{.vc} = \[
2.  `    "Alice"`{.code-voice}: `"Chips"`{.s},
3.  `    "Bob"`{.code-voice}: `"Licorice"`{.s},
4.  `    "Eve"`{.code-voice}: `"Pretzels"`{.s},
5.  `]`{.code-voice}
6.  `func`{.code-voice} `buyFavoriteSnack`{.vc}(`person`{.vc}: `String`{.n}, `vendingMachine`{.vc}: `VendingMachine`{.n}) `throws`{.kt} {
7.  `    let`{.code-voice} `snackName`{.vc} = `favoriteSnacks`{.vc}\[`person`{.vc}\] ?? `"Candy Bar"`{.s}
8.  `    try`{.code-voice} `vendingMachine`{.vc}.`vend`{.vc}(`itemNamed`{.vc}: `snackName`{.vc})
9.  `}`{.code-voice}







In this example, the `buyFavoriteSnack(_:vendingMachine:)`{.code-voice} function looks up a given person’s favorite snack and tries to buy it for them by calling the `vend(itemNamed:)`{.code-voice} method. Because the `vend(itemNamed:)`{.code-voice} method can throw an error, it’s called with the `try`{.code-voice} keyword in front of it.





[‌](){#TP40016643-CH42-ID541}
### Handling Errors Using Do-Catch {#handling-errors-using-do-catch .section-name}

You use a `do`{.code-voice}-`catch`{.code-voice} statement to handle errors by running a block of code. If an error is thrown by the code in the `do`{.code-voice} clause, it is matched against the `catch`{.code-voice} clauses to determine which one of them can handle the error.

Here is the general form of a `do`{.code-voice}-`catch`{.code-voice} statement:




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



You write a pattern after `catch`{.code-voice} to indicate what errors that clause can handle. If a `catch`{.code-voice} clause doesn’t have a pattern, the clause matches any error and binds the error to a local constant named `error`{.code-voice}. For more information about pattern matching, see [Patterns](Patterns.md).

The `catch`{.code-voice} clauses don’t have to handle every possible error that the code in its `do`{.code-voice} clause can throw. If none of the `catch`{.code-voice} clauses handle the error, the error propagates to the surrounding scope. However, the error must be handled by *some* surrounding scope—either by an enclosing `do`{.code-voice}-`catch`{.code-voice} clause that handles the error or by being inside a throwing function. For example, the following code handles all three cases of the `VendingMachineError`{.code-voice} enumeration, but all other errors have to be handled by its surrounding scope:







1.  `var`{.code-voice} `vendingMachine`{.vc} = `VendingMachine`{.vc}()
2.  `vendingMachine`{.code-voice}.`coinsDeposited`{.vc} = `8`{.m}
3.  `do`{.code-voice} {
4.  `    try`{.code-voice} `buyFavoriteSnack`{.vc}(`"Alice"`{.s}, `vendingMachine`{.vc}: `vendingMachine`{.vc})
5.  `} catch`{.code-voice} `VendingMachineError`{.vc}.`InvalidSelection`{.vc} {
6.  `    print`{.code-voice}(`"Invalid Selection."`{.s})
7.  `} catch`{.code-voice} `VendingMachineError`{.vc}.`OutOfStock`{.vc} {
8.  `    print`{.code-voice}(`"Out of Stock."`{.s})
9.  `} catch`{.code-voice} `VendingMachineError`{.vc}.`InsufficientFunds`{.vc}(`let`{.kt} `coinsNeeded`{.vc}) {
10. `    print`{.code-voice}(`"Insufficient funds. Please insert an additional `{.s}\\(`coinsNeeded`{.vc})` coins."`{.s})
11. `}`{.code-voice}
12. `// prints "Insufficient funds. Please insert an additional 2 coins."`{.code-voice}







In the above example, the `buyFavoriteSnack(_:vendingMachine:)`{.code-voice} function is called in a `try`{.code-voice} expression, because it can throw an error. If an error is thrown, execution immediately transfers to the `catch`{.code-voice} clauses, which decide whether to allow propagation to continue. If no error is thrown, the remaining statements in the `do`{.code-voice} statement are executed.





[‌](){#TP40016643-CH42-ID542}
### Converting Errors to Optional Values {#converting-errors-to-optional-values .section-name}

You use `try?`{.code-voice} to handle an error by converting it to an optional value. If an error is thrown while evaluating the `try?`{.code-voice} expression, the value of the expression is `nil`{.code-voice}. For example, in the following code `x`{.code-voice} and `y`{.code-voice} have the same value and behavior:







1.  `func`{.code-voice} `someThrowingFunction`{.vc}() `throws`{.kt} -&gt; `Int`{.n} {
2.  `    // ...`{.code-voice}
3.  `}`{.code-voice}
4.  ` `{.code-voice}
5.  `let`{.code-voice} `x`{.vc} = `try`{.kt}? `someThrowingFunction`{.vc}()
6.  ` `{.code-voice}
7.  `let`{.code-voice} `y`{.vc}: `Int`{.n}?
8.  `do`{.code-voice} {
9.  `    y`{.code-voice} = `try`{.kt} `someThrowingFunction`{.vc}()
10. `} catch`{.code-voice} {
11. `    y`{.code-voice} = `nil`{.kt}
12. `}`{.code-voice}







If `someThrowingFunction()`{.code-voice} throws an error, the value of `x`{.code-voice} and `y`{.code-voice} is `nil`{.code-voice}. Otherwise, the value of `x`{.code-voice} and `y`{.code-voice} is the value that the function returned. Note that `x`{.code-voice} and `y`{.code-voice} are an optional of whatever type `someThrowingFunction()`{.code-voice} returns. Here the function returns an integer, so `x`{.code-voice} and `y`{.code-voice} are optional integers.

Using `try?`{.code-voice} lets you write concise error handling code when you want to handle all errors in the same way. For example, the following code uses several approaches to fetch data, or returns `nil`{.code-voice} if all of the approaches fail.







1.  `func`{.code-voice} `fetchData`{.vc}() -&gt; `Data`{.n}? {
2.  `    if`{.code-voice} `let`{.kt} `data`{.vc} = `try`{.kt}? `fetchDataFromDisk`{.vc}() { `return`{.kt} `data`{.vc} }
3.  `    if`{.code-voice} `let`{.kt} `data`{.vc} = `try`{.kt}? `fetchDataFromServer`{.vc}() { `return`{.kt} `data`{.vc} }
4.  `    return`{.code-voice} `nil`{.kt}
5.  `}`{.code-voice}











[‌](){#TP40016643-CH42-ID513}
### Disabling Error Propagation {#disabling-error-propagation .section-name}

Sometimes you know a throwing function or method won’t, in fact, throw an error at runtime. On those occasions, you can write `try!`{.code-voice} before the expression to disable error propagation and wrap the call in a runtime assertion that no error will be thrown. If an error actually is thrown, you’ll get a runtime error.

For example, the following code uses a `loadImage(_:)`{.code-voice} function, which loads the image resource at a given path or throws an error if the image can’t be loaded. In this case, because the image is shipped with the application, no error will be thrown at runtime, so it is appropriate to disable error propagation.







1.  `let`{.code-voice} `photo`{.vc} = `try`{.kt}! `loadImage`{.vc}(`"./Resources/John Appleseed.jpg"`{.s})













[‌](){#TP40016643-CH42-ID514}
### Specifying Cleanup Actions {#specifying-cleanup-actions .section-name}

You use a `defer`{.code-voice} statement to execute a set of statements just before code execution leaves the current block of code. This statement lets you do any necessary cleanup that should be performed regardless of *how* execution leaves the current block of code—whether it leaves because an error was thrown or because of a statement such as `return`{.code-voice} or `break`{.code-voice}. For example, you can use a `defer`{.code-voice} statement to ensure that file descriptors are closed and manually allocated memory is freed.

A `defer`{.code-voice} statement defers execution until the current scope is exited. This statement consists of the `defer`{.code-voice} keyword and the statements to be executed later. The deferred statements may not contain any code that would transfer control out of the statements, such as a `break`{.code-voice} or a `return`{.code-voice} statement, or by throwing an error. Deferred actions are executed in reverse order of how they are specified—that is, the code in the first `defer`{.code-voice} statement executes after code in the second, and so on.







1.  `func`{.code-voice} `processFile`{.vc}(`filename`{.vc}: `String`{.n}) `throws`{.kt} {
2.  `    if`{.code-voice} `exists`{.vc}(`filename`{.vc}) {
3.  `        let`{.code-voice} `file`{.vc} = `open`{.vc}(`filename`{.vc})
4.  `        defer`{.code-voice} {
5.  `            close`{.code-voice}(`file`{.vc})
6.  `        }`{.code-voice}
7.  `        while`{.code-voice} `let`{.kt} `line`{.vc} = `try`{.kt} `file`{.vc}.`readline`{.vc}() {
8.  `            // Work with the file.`{.code-voice}
9.  `        }`{.code-voice}
10. `        // close(file) is called here, at the end of the scope.`{.code-voice}
11. `    }`{.code-voice}
12. `}`{.code-voice}







The above example uses a `defer`{.code-voice} statement to ensure that the `open(_:)`{.code-voice} function has a corresponding call to `close(_:)`{.code-voice}.



Note

You can use a `defer`{.code-voice} statement even when no error handling code is involved.








