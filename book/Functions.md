



[‌]()[‌]()
Functions 
---------



*Functions* are self-contained chunks of code that perform a specific task. You give a function a name that identifies what it does, and this name is used to “call” the function to perform its task when needed.

Swift’s unified function syntax is flexible enough to express anything from a simple C-style function with no parameter names to a complex Objective-C-style method with local and external parameter names for each parameter. Parameters can provide default values to simplify function calls and can be passed as in-out parameters, which modify a passed variable once the function has completed its execution.

Every function in Swift has a type, consisting of the function’s parameter types and return type. You can use this type like any other type in Swift, which makes it easy to pass functions as parameters to other functions, and to return functions from functions. Functions can also be written within other functions to encapsulate useful functionality within a nested function scope.





[‌]()
### Defining and Calling Functions 

When you define a function, you can optionally define one or more named, typed values that the function takes as input, known as *parameters*. You can also optionally define a type of value that the function will pass back as output when it is done, known as its *return type*.

Every function has a *function name*, which describes the task that the function performs. To use a function, you “call” that function with its name and pass it input values (known as *arguments*) that match the types of the function’s parameters. A function’s arguments must always be provided in the same order as the function’s parameter list.

The function in the example below is called `sayHello(_:)`, because that’s what it does—it takes a person’s name as input and returns a greeting for that person. To accomplish this, you define one input parameter—a `String` value called `personName`—and a return type of `String`, which will contain a greeting for that person:







1.  `func` `sayHello`(`personName`: `String`) -&gt; `String` {
2.  `    let` `greeting` = `"Hello, "` + `personName` + `"!"`
3.  `    return` `greeting`
4.  `}`







All of this information is rolled up into the function’s *definition*, which is prefixed with the `func` keyword. You indicate the function’s return type with the *return arrow* `->` (a hyphen followed by a right angle bracket), which is followed by the name of the type to return.

The definition describes what the function does, what it expects to receive, and what it returns when it is done. The definition makes it easy for the function to be called unambiguously from elsewhere in your code:







1.  `print`(`sayHello`(`"Anna"`))
2.  `// prints "Hello, Anna!"`
3.  `print`(`sayHello`(`"Brian"`))
4.  `// prints "Hello, Brian!"`







You call the `sayHello(_:)` function by passing it a `String` argument value in parentheses, such as `sayHello("Anna")`. Because the function returns a `String` value, `sayHello(_:)` can be wrapped in a call to the `print(_:separator:terminator:)` function to print that string and see its return value, as shown above.

The body of the `sayHello(_:)` function starts by defining a new `String` constant called `greeting` and setting it to a simple greeting message for `personName`. This greeting is then passed back out of the function using the `return` keyword. As soon as `return greeting` is called, the function finishes its execution and returns the current value of `greeting`.

You can call the `sayHello(_:)` function multiple times with different input values. The example above shows what happens if it is called with an input value of `"Anna"`, and an input value of `"Brian"`. The function returns a tailored greeting in each case.

To simplify the body of this function, combine the message creation and the return statement into one line:







1.  `func` `sayHelloAgain`(`personName`: `String`) -&gt; `String` {
2.  `    return` `"Hello again, "` + `personName` + `"!"`
3.  `}`
4.  `print`(`sayHelloAgain`(`"Anna"`))
5.  `// prints "Hello again, Anna!"`











[‌]()
### Function Parameters and Return Values 

Function parameters and return values are extremely flexible in Swift. You can define anything from a simple utility function with a single unnamed parameter to a complex function with expressive parameter names and different parameter options.



[‌]()
### Functions Without Parameters 

Functions are not required to define input parameters. Here’s a function with no input parameters, which always returns the same `String` message whenever it is called:







1.  `func` `sayHelloWorld`() -&gt; `String` {
2.  `    return` `"hello, world"`
3.  `}`
4.  `print`(`sayHelloWorld`())
5.  `// prints "hello, world"`







The function definition still needs parentheses after the function’s name, even though it does not take any parameters. The function name is also followed by an empty pair of parentheses when the function is called.





[‌]()
### Functions With Multiple Parameters 

Functions can have multiple input parameters, which are written within the function’s parentheses, separated by commas.

This function takes a person’s name and whether they have already been greeted as input, and returns an appropriate greeting for that person:







1.  `func` `sayHello`(`personName`: `String`, `alreadyGreeted`: `Bool`) -&gt; `String` {
2.  `    if` `alreadyGreeted` {
3.  `        return` `sayHelloAgain`(`personName`)
4.  `    } else` {
5.  `        return` `sayHello`(`personName`)
6.  `    }`
7.  `}`
8.  `print`(`sayHello`(`"Tim"`, `alreadyGreeted`: `true`))
9.  `// prints "Hello again, Tim!"`







You call the `sayHello(_:alreadyGreeted:)` function by passing it both a `String` argument value and a `Bool` argument value labeled `alreadyGreeted` in parentheses, separated by commas. Note that this function is distinct from the `sayHello(_:)` function shown in an earlier section. Although both functions have names that begin with `sayHello`, the `sayHello(_:alreadyGreeted:)` function takes two arguments but the `sayHello(_:)` function takes only one.

When calling a function with more than one parameter, any argument after the first is labeled according to its corresponding parameter name. Function parameter naming is described in more detail in [Function Parameter Names](Functions.md#TP40016643-CH10-ID166).





[‌]()
### Functions Without Return Values 

Functions are not required to define a return type. Here’s a version of the `sayHello(_:)` function, called `sayGoodbye(_:)`, which prints its own `String` value rather than returning it:







1.  `func` `sayGoodbye`(`personName`: `String`) {
2.  `    print`(`"Goodbye, `\\(`personName`)`!"`)
3.  `}`
4.  `sayGoodbye`(`"Dave"`)
5.  `// prints "Goodbye, Dave!"`







Because it does not need to return a value, the function’s definition does not include the return arrow (`->`) or a return type.



Note

Strictly speaking, the `sayGoodbye(_:)` function *does* still return a value, even though no return value is defined. Functions without a defined return type return a special value of type `Void`. This is simply an empty tuple, in effect a tuple with zero elements, which can be written as `()`.



The return value of a function can be ignored when it is called:







1.  `func` `printAndCount`(`stringToPrint`: `String`) -&gt; `Int` {
2.  `    print`(`stringToPrint`)
3.  `    return` `stringToPrint`.`characters`.`count`
4.  `}`
5.  `func` `printWithoutCounting`(`stringToPrint`: `String`) {
6.  `    printAndCount`(`stringToPrint`)
7.  `}`
8.  `printAndCount`(`"hello, world"`)
9.  `// prints "hello, world" and returns a value of 12`
10. `printWithoutCounting`(`"hello, world"`)
11. `// prints "hello, world" but does not return a value`







The first function, `printAndCount(_:)`, prints a string, and then returns its character count as an `Int`. The second function, `printWithoutCounting`, calls the first function, but ignores its return value. When the second function is called, the message is still printed by the first function, but the returned value is not used.



Note

Return values can be ignored, but a function that says it will return a value must always do so. A function with a defined return type cannot allow control to fall out of the bottom of the function without returning a value, and attempting to do so will result in a compile-time error.







[‌]()
### Functions with Multiple Return Values 

You can use a tuple type as the return type for a function to return multiple values as part of one compound return value.

The example below defines a function called `minMax(_:)`, which finds the smallest and largest numbers in an array of `Int` values:







1.  `func` `minMax`(`array`: \[`Int`\]) -&gt; (`min`: `Int`, `max`: `Int`) {
2.  `    var` `currentMin` = `array`\[`0`\]
3.  `    var` `currentMax` = `array`\[`0`\]
4.  `    for` `value` `in` `array`\[`1`..&lt;`array`.`count`\] {
5.  `        if` `value` &lt; `currentMin` {
6.  `            currentMin` = `value`
7.  `        } else` `if` `value` &gt; `currentMax` {
8.  `            currentMax` = `value`
9.  `        }`
10. `    }`
11. `    return` (`currentMin`, `currentMax`)
12. `}`







The `minMax(_:)` function returns a tuple containing two `Int` values. These values are labeled `min` and `max` so that they can be accessed by name when querying the function’s return value.

The body of the `minMax(_:)` function starts by setting two working variables called `currentMin` and `currentMax` to the value of the first integer in the array. The function then iterates over the remaining values in the array and checks each value to see if it is smaller or larger than the values of `currentMin` and `currentMax` respectively. Finally, the overall minimum and maximum values are returned as a tuple of two `Int` values.

Because the tuple’s member values are named as part of the function’s return type, they can be accessed with dot syntax to retrieve the minimum and maximum found values:







1.  `let` `bounds` = `minMax`(\[`8`, -`6`, `2`, `109`, `3`, `71`\])
2.  `print`(`"min is `\\(`bounds`.`min`)` and max is `\\(`bounds`.`max`)`"`)
3.  `// prints "min is -6 and max is 109"`







Note that the tuple’s members do not need to be named at the point that the tuple is returned from the function, because their names are already specified as part of the function’s return type.



[‌]()
### Optional Tuple Return Types 

If the tuple type to be returned from a function has the potential to have “no value” for the entire tuple, you can use an *optional* tuple return type to reflect the fact that the entire tuple can be `nil`. You write an optional tuple return type by placing a question mark after the tuple type’s closing parenthesis, such as `(Int, Int)?` or `(String, Int, Bool)?`.



Note

An optional tuple type such as `(Int, Int)?` is different from a tuple that contains optional types such as `(Int?, Int?)`. With an optional tuple type, the entire tuple is optional, not just each individual value within the tuple.



The `minMax(_:)` function above returns a tuple containing two `Int` values. However, the function does not perform any safety checks on the array it is passed. If the `array` argument contains an empty array, the `minMax(_:)` function, as defined above, will trigger a runtime error when attempting to access `array[0]`.

To handle this “empty array” scenario safely, write the `minMax(_:)` function with an optional tuple return type and return a value of `nil` when the array is empty:







1.  `func` `minMax`(`array`: \[`Int`\]) -&gt; (`min`: `Int`, `max`: `Int`)? {
2.  `    if` `array`.`isEmpty` { `return` `nil` }
3.  `    var` `currentMin` = `array`\[`0`\]
4.  `    var` `currentMax` = `array`\[`0`\]
5.  `    for` `value` `in` `array`\[`1`..&lt;`array`.`count`\] {
6.  `        if` `value` &lt; `currentMin` {
7.  `            currentMin` = `value`
8.  `        } else` `if` `value` &gt; `currentMax` {
9.  `            currentMax` = `value`
10. `        }`
11. `    }`
12. `    return` (`currentMin`, `currentMax`)
13. `}`







You can use optional binding to check whether this version of the `minMax(_:)` function returns an actual tuple value or `nil`:







1.  `if` `let` `bounds` = `minMax`(\[`8`, -`6`, `2`, `109`, `3`, `71`\]) {
2.  `    print`(`"min is `\\(`bounds`.`min`)` and max is `\\(`bounds`.`max`)`"`)
3.  `}`
4.  `// prints "min is -6 and max is 109"`















[‌]()
### Function Parameter Names 

Function parameters have both an *external parameter name* and a *local parameter name*. An external parameter name is used to label arguments passed to a function call. A local parameter name is used in the implementation of the function.







1.  `func` `someFunction`(`firstParameterName`: `Int`, `secondParameterName`: `Int`) {
2.  `    // function body goes here`
3.  `    // firstParameterName and secondParameterName refer to`
4.  `    // the argument values for the first and second parameters`
5.  `}`
6.  `someFunction`(`1`, `secondParameterName`: `2`)







By default, the first parameter omits its external name, and the second and subsequent parameters use their local name as their external name. All parameters must have unique local names. Although it’s possible for multiple parameters to have the same external name, unique external names help make your code more readable.



[‌]()
### Specifying External Parameter Names 

You write an external parameter name before the local parameter name it supports, separated by a space:







1.  `func` `someFunction`(`externalParameterName` `localParameterName`: `Int`) {
2.  `    // function body goes here, and can use localParameterName`
3.  `    // to refer to the argument value for that parameter`
4.  `}`









Note

If you provide an external parameter name for a parameter, that external name must *always* be used when you call the function.



Here’s a version of the `sayHello(_:)` function that takes the names of two people and returns a greeting for both of them:







1.  `func` `sayHello`(`to` `person`: `String`, `and` `anotherPerson`: `String`) -&gt; `String` {
2.  `    return` `"Hello `\\(`person`)` and `\\(`anotherPerson`)`!"`
3.  `}`
4.  `print`(`sayHello`(`to`: `"Bill"`, `and`: `"Ted"`))
5.  `// prints "Hello Bill and Ted!"`







By specifying external parameter names for both parameters, both the first and second arguments to the `sayHello(to:and:)` function must be labeled when you call it.

The use of external parameter names can allow a function to be called in an expressive, sentence-like manner, while still providing a function body that is readable and clear in intent.





[‌]()
### Omitting External Parameter Names 

If you do not want to use an external name for the second or subsequent parameters of a function, write an underscore (`_`) instead of an explicit external name for that parameter.







1.  `func` `someFunction`(`firstParameterName`: `Int`, `_` `secondParameterName`: `Int`) {
2.  `    // function body goes here`
3.  `    // firstParameterName and secondParameterName refer to`
4.  `    // the argument values for the first and second parameters`
5.  `}`
6.  `someFunction`(`1`, `2`)









Note

Because the first parameter omits its external parameter name by default, explicitly writing an underscore is extraneous.







[‌]()
### Default Parameter Values 

You can define a *default value* for any parameter in a function by assigning a value to the parameter after that parameter’s type. If a default value is defined, you can omit that parameter when calling the function.







1.  `func` `someFunction`(`parameterWithDefault`: `Int` = `12`) {
2.  `    // function body goes here`
3.  `    // if no arguments are passed to the function call,`
4.  `    // value of parameterWithDefault is 12`
5.  `}`
6.  `someFunction`(`6`) `// parameterWithDefault is 6`
7.  `someFunction`() `// parameterWithDefault is 12`









Note

Place parameters with default values at the end of a function’s parameter list. This ensures that all calls to the function use the same order for their nondefault arguments, and makes it clear that the same function is being called in each case.







[‌]()
### Variadic Parameters 

A *variadic parameter* accepts zero or more values of a specified type. You use a variadic parameter to specify that the parameter can be passed a varying number of input values when the function is called. Write variadic parameters by inserting three period characters (`...`) after the parameter’s type name.

The values passed to a variadic parameter are made available within the function’s body as an array of the appropriate type. For example, a variadic parameter with a name of `numbers` and a type of `Double...` is made available within the function’s body as a constant array called `numbers` of type `[Double]`.

The example below calculates the *arithmetic mean* (also known as the *average*) for a list of numbers of any length:







1.  `func` `arithmeticMean`(`numbers`: `Double`...) -&gt; `Double` {
2.  `    var` `total`: `Double` = `0`
3.  `    for` `number` `in` `numbers` {
4.  `        total` += `number`
5.  `    }`
6.  `    return` `total` / `Double`(`numbers`.`count`)
7.  `}`
8.  `arithmeticMean`(`1`, `2`, `3`, `4`, `5`)
9.  `// returns 3.0, which is the arithmetic mean of these five numbers`
10. `arithmeticMean`(`3`, `8.25`, `18.75`)
11. `// returns 10.0, which is the arithmetic mean of these three numbers`









Note

A function may have at most one variadic parameter.







[‌]()
### In-Out Parameters 

Function parameters are constants by default. Trying to change the value of a function parameter from within the body of that function results in a compile-time error. This means that you can’t change the value of a parameter by mistake. If you want a function to modify a parameter’s value, and you want those changes to persist after the function call has ended, define that parameter as an *in-out parameter* instead.

You write an in-out parameter by placing the `inout` keyword at the start of its parameter definition. An in-out parameter has a value that is passed *in* to the function, is modified by the function, and is passed back *out* of the function to replace the original value. For a detailed discussion of the behavior of in-out parameters and associated compiler optimizations, see [In-Out Parameters](Declarations.md#TP40016643-CH34-ID545).

You can only pass a variable as the argument for an in-out parameter. You cannot pass a constant or a literal value as the argument, because constants and literals cannot be modified. You place an ampersand (`&`) directly before a variable’s name when you pass it as an argument to an in-out parameter, to indicate that it can be modified by the function.



Note

In-out parameters cannot have default values, and variadic parameters cannot be marked as `inout`.



Here’s an example of a function called `swapTwoInts(_:_:)`, which has two in-out integer parameters called `a` and `b`:







1.  `func` `swapTwoInts`(`inout` `a`: `Int`, `inout` `_` `b`: `Int`) {
2.  `    let` `temporaryA` = `a`
3.  `    a` = `b`
4.  `    b` = `temporaryA`
5.  `}`







The `swapTwoInts(_:_:)` function simply swaps the value of `b` into `a`, and the value of `a` into `b`. The function performs this swap by storing the value of `a` in a temporary constant called `temporaryA`, assigning the value of `b` to `a`, and then assigning `temporaryA` to `b`.

You can call the `swapTwoInts(_:_:)` function with two variables of type `Int` to swap their values. Note that the names of `someInt` and `anotherInt` are prefixed with an ampersand when they are passed to the `swapTwoInts(_:_:)` function:







1.  `var` `someInt` = `3`
2.  `var` `anotherInt` = `107`
3.  `swapTwoInts`(&`someInt`, &`anotherInt`)
4.  `print`(`"someInt is now `\\(`someInt`)`, and anotherInt is now `\\(`anotherInt`)`"`)
5.  `// prints "someInt is now 107, and anotherInt is now 3"`







The example above shows that the original values of `someInt` and `anotherInt` are modified by the `swapTwoInts(_:_:)` function, even though they were originally defined outside of the function.



Note

In-out parameters are not the same as returning a value from a function. The `swapTwoInts` example above does not define a return type or return a value, but it still modifies the values of `someInt` and `anotherInt`. In-out parameters are an alternative way for a function to have an effect outside of the scope of its function body.









[‌]()
### Function Types 

Every function has a specific *function type*, made up of the parameter types and the return type of the function.

For example:







1.  `func` `addTwoInts`(`a`: `Int`, `_` `b`: `Int`) -&gt; `Int` {
2.  `    return` `a` + `b`
3.  `}`
4.  `func` `multiplyTwoInts`(`a`: `Int`, `_` `b`: `Int`) -&gt; `Int` {
5.  `    return` `a` \* `b`
6.  `}`







This example defines two simple mathematical functions called `addTwoInts` and `multiplyTwoInts`. These functions each take two `Int` values, and return an `Int` value, which is the result of performing an appropriate mathematical operation.

The type of both of these functions is `(Int, Int) -> Int`. This can be read as:

“A function type that has two parameters, both of type `Int`, and that returns a value of type `Int`.”

Here’s another example, for a function with no parameters or return value:







1.  `func` `printHelloWorld`() {
2.  `    print`(`"hello, world"`)
3.  `}`







The type of this function is `() -> Void`, or “a function that has no parameters, and returns `Void`.”



[‌]()
### Using Function Types 

You use function types just like any other types in Swift. For example, you can define a constant or variable to be of a function type and assign an appropriate function to that variable:







1.  `var` `mathFunction`: (`Int`, `Int`) -&gt; `Int` = `addTwoInts`







This can be read as:

“Define a variable called `mathFunction`, which has a type of ‘a function that takes two `Int` values, and returns an `Int` value.’ Set this new variable to refer to the function called `addTwoInts`.”

The `addTwoInts(_:_:)` function has the same type as the `mathFunction` variable, and so this assignment is allowed by Swift’s type-checker.

You can now call the assigned function with the name `mathFunction`:







1.  `print`(`"Result: `\\(`mathFunction`(`2`, `3`))`"`)
2.  `// prints "Result: 5"`







A different function with the same matching type can be assigned to the same variable, in the same way as for non-function types:







1.  `mathFunction` = `multiplyTwoInts`
2.  `print`(`"Result: `\\(`mathFunction`(`2`, `3`))`"`)
3.  `// prints "Result: 6"`







As with any other type, you can leave it to Swift to infer the function type when you assign a function to a constant or variable:







1.  `let` `anotherMathFunction` = `addTwoInts`
2.  `// anotherMathFunction is inferred to be of type (Int, Int) -> Int`











[‌]()
### Function Types as Parameter Types 

You can use a function type such as `(Int, Int) -> Int` as a parameter type for another function. This enables you to leave some aspects of a function’s implementation for the function’s caller to provide when the function is called.

Here’s an example to print the results of the math functions from above:







1.  `func` `printMathResult`(`mathFunction`: (`Int`, `Int`) -&gt; `Int`, `_` `a`: `Int`, `_` `b`: `Int`) {
2.  `    print`(`"Result: `\\(`mathFunction`(`a`, `b`))`"`)
3.  `}`
4.  `printMathResult`(`addTwoInts`, `3`, `5`)
5.  `// prints "Result: 8"`







This example defines a function called `printMathResult(_:_:_:)`, which has three parameters. The first parameter is called `mathFunction`, and is of type `(Int, Int) -> Int`. You can pass any function of that type as the argument for this first parameter. The second and third parameters are called `a` and `b`, and are both of type `Int`. These are used as the two input values for the provided math function.

When `printMathResult(_:_:_:)` is called, it is passed the `addTwoInts(_:_:)` function, and the integer values `3` and `5`. It calls the provided function with the values `3` and `5`, and prints the result of `8`.

The role of `printMathResult(_:_:_:)` is to print the result of a call to a math function of an appropriate type. It doesn’t matter what that function’s implementation actually does—it matters only that the function is of the correct type. This enables `printMathResult(_:_:_:)` to hand off some of its functionality to the caller of the function in a type-safe way.





[‌]()
### Function Types as Return Types 

You can use a function type as the return type of another function. You do this by writing a complete function type immediately after the return arrow (`->`) of the returning function.

The next example defines two simple functions called `stepForward(_:)` and `stepBackward(_:)`. The `stepForward(_:)` function returns a value one more than its input value, and the `stepBackward(_:)` function returns a value one less than its input value. Both functions have a type of `(Int) -> Int`:







1.  `func` `stepForward`(`input`: `Int`) -&gt; `Int` {
2.  `    return` `input` + `1`
3.  `}`
4.  `func` `stepBackward`(`input`: `Int`) -&gt; `Int` {
5.  `    return` `input` - `1`
6.  `}`







Here’s a function called `chooseStepFunction(_:)`, whose return type is “a function of type `(Int) -> Int`”. The ``` chooseStepFunction(_:)``function returns the ``stepForward(_:) ``` function or the `stepBackward(_:)` function based on a Boolean parameter called `backwards`:







1.  `func` `chooseStepFunction`(`backwards`: `Bool`) -&gt; (`Int`) -&gt; `Int` {
2.  `    return` `backwards` ? `stepBackward` : `stepForward`
3.  `}`







You can now use `chooseStepFunction(_:)` to obtain a function that will step in one direction or the other:







1.  `var` `currentValue` = `3`
2.  `let` `moveNearerToZero` = `chooseStepFunction`(`currentValue` &gt; `0`)
3.  `// moveNearerToZero now refers to the stepBackward() function`







The preceding example determines whether a positive or negative step is needed to move a variable called `currentValue` progressively closer to zero. `currentValue` has an initial value of `3`, which means that `currentValue > 0` returns `true`, causing `chooseStepFunction(_:)` to return the `stepBackward(_:)` function. A reference to the returned function is stored in a constant called `moveNearerToZero`.

Now that `moveNearerToZero` refers to the correct function, it can be used to count to zero:







1.  `print`(`"Counting to zero:"`)
2.  `// Counting to zero:`
3.  `while` `currentValue` != `0` {
4.  `    print`(`"`\\(`currentValue`)`... "`)
5.  `    currentValue` = `moveNearerToZero`(`currentValue`)
6.  `}`
7.  `print`(`"zero!"`)
8.  `// 3...`
9.  `// 2...`
10. `// 1...`
11. `// zero!`













[‌]()
### Nested Functions 

All of the functions you have encountered so far in this chapter have been examples of *global functions*, which are defined at a global scope. You can also define functions inside the bodies of other functions, known as *nested functions*.

Nested functions are hidden from the outside world by default, but can still be called and used by their enclosing function. An enclosing function can also return one of its nested functions to allow the nested function to be used in another scope.

You can rewrite the `chooseStepFunction(_:)` example above to use and return nested functions:







1.  `func` `chooseStepFunction`(`backwards`: `Bool`) -&gt; (`Int`) -&gt; `Int` {
2.  `    func` `stepForward`(`input`: `Int`) -&gt; `Int` { `return` `input` + `1` }
3.  `    func` `stepBackward`(`input`: `Int`) -&gt; `Int` { `return` `input` - `1` }
4.  `    return` `backwards` ? `stepBackward` : `stepForward`
5.  `}`
6.  `var` `currentValue` = -`4`
7.  `let` `moveNearerToZero` = `chooseStepFunction`(`currentValue` &gt; `0`)
8.  `// moveNearerToZero now refers to the nested stepForward() function`
9.  `while` `currentValue` != `0` {
10. `    print`(`"`\\(`currentValue`)`... "`)
11. `    currentValue` = `moveNearerToZero`(`currentValue`)
12. `}`
13. `print`(`"zero!"`)
14. `// -4...`
15. `// -3...`
16. `// -2...`
17. `// -1...`
18. `// zero!`












