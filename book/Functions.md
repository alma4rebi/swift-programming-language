<div class="content-wrapper">

<div id="chapter_container" class="conceptualwithtasks">

[‌](){#TP40016643-CH10}[‌](){#TP40016643-CH10-ID158}
Functions {#functions .chapter-name}
---------

<div class="section section">

*Functions* are self-contained chunks of code that perform a specific
task. You give a function a name that identifies what it does, and this
name is used to “call” the function to perform its task when needed.

Swift’s unified function syntax is flexible enough to express anything
from a simple C-style function with no parameter names to a complex
Objective-C-style method with local and external parameter names for
each parameter. Parameters can provide default values to simplify
function calls and can be passed as in-out parameters, which modify a
passed variable once the function has completed its execution.

Every function in Swift has a type, consisting of the function’s
parameter types and return type. You can use this type like any other
type in Swift, which makes it easy to pass functions as parameters to
other functions, and to return functions from functions. Functions can
also be written within other functions to encapsulate useful
functionality within a nested function scope.

</div>

<div class="section section">

[‌](){#TP40016643-CH10-ID159}
### Defining and Calling Functions {#defining-and-calling-functions .section-name}

When you define a function, you can optionally define one or more named,
typed values that the function takes as input, known as *parameters*.
You can also optionally define a type of value that the function will
pass back as output when it is done, known as its *return type*.

Every function has a *function name*, which describes the task that the
function performs. To use a function, you “call” that function with its
name and pass it input values (known as *arguments*) that match the
types of the function’s parameters. A function’s arguments must always
be provided in the same order as the function’s parameter list.

The function in the example below is called `sayHello(_:)`{.code-voice},
because that’s what it does—it takes a person’s name as input and
returns a greeting for that person. To accomplish this, you define one
input parameter—a `String`{.code-voice} value called
`personName`{.code-voice}—and a return type of `String`{.code-voice},
which will contain a greeting for that person:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `sayHello`{.vc}(`personName`{.vc}: `String`{.n})
    -&gt; `String`{.n} {
2.  `    let`{.code-voice} `greeting`{.vc} = `"Hello, "`{.s} +
    `personName`{.vc} + `"!"`{.s}
3.  `    return`{.code-voice} `greeting`{.vc}
4.  `}`{.code-voice}

</div>

</div>

</div>

All of this information is rolled up into the function’s *definition*,
which is prefixed with the `func`{.code-voice} keyword. You indicate the
function’s return type with the *return arrow* `->`{.code-voice} (a
hyphen followed by a right angle bracket), which is followed by the name
of the type to return.

The definition describes what the function does, what it expects to
receive, and what it returns when it is done. The definition makes it
easy for the function to be called unambiguously from elsewhere in your
code:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `print`{.code-voice}(`sayHello`{.vc}(`"Anna"`{.s}))
2.  `// prints "Hello, Anna!"`{.code-voice}
3.  `print`{.code-voice}(`sayHello`{.vc}(`"Brian"`{.s}))
4.  `// prints "Hello, Brian!"`{.code-voice}

</div>

</div>

</div>

You call the `sayHello(_:)`{.code-voice} function by passing it a
`String`{.code-voice} argument value in parentheses, such as
`sayHello("Anna")`{.code-voice}. Because the function returns a
`String`{.code-voice} value, `sayHello(_:)`{.code-voice} can be wrapped
in a call to the `print(_:separator:terminator:)`{.code-voice} function
to print that string and see its return value, as shown above.

The body of the `sayHello(_:)`{.code-voice} function starts by defining
a new `String`{.code-voice} constant called `greeting`{.code-voice} and
setting it to a simple greeting message for `personName`{.code-voice}.
This greeting is then passed back out of the function using the
`return`{.code-voice} keyword. As soon as `return greeting`{.code-voice}
is called, the function finishes its execution and returns the current
value of `greeting`{.code-voice}.

You can call the `sayHello(_:)`{.code-voice} function multiple times
with different input values. The example above shows what happens if it
is called with an input value of `"Anna"`{.code-voice}, and an input
value of `"Brian"`{.code-voice}. The function returns a tailored
greeting in each case.

To simplify the body of this function, combine the message creation and
the return statement into one line:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `sayHelloAgain`{.vc}(`personName`{.vc}:
    `String`{.n}) -&gt; `String`{.n} {
2.  `    return`{.code-voice} `"Hello again, "`{.s} +
    `personName`{.vc} + `"!"`{.s}
3.  `}`{.code-voice}
4.  `print`{.code-voice}(`sayHelloAgain`{.vc}(`"Anna"`{.s}))
5.  `// prints "Hello again, Anna!"`{.code-voice}

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH10-ID160}
### Function Parameters and Return Values {#function-parameters-and-return-values .section-name}

Function parameters and return values are extremely flexible in Swift.
You can define anything from a simple utility function with a single
unnamed parameter to a complex function with expressive parameter names
and different parameter options.

<div class="section section">

[‌](){#TP40016643-CH10-ID162}
### Functions Without Parameters {#functions-without-parameters .section-name}

Functions are not required to define input parameters. Here’s a function
with no input parameters, which always returns the same
`String`{.code-voice} message whenever it is called:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `sayHelloWorld`{.vc}() -&gt; `String`{.n} {
2.  `    return`{.code-voice} `"hello, world"`{.s}
3.  `}`{.code-voice}
4.  `print`{.code-voice}(`sayHelloWorld`{.vc}())
5.  `// prints "hello, world"`{.code-voice}

</div>

</div>

</div>

The function definition still needs parentheses after the function’s
name, even though it does not take any parameters. The function name is
also followed by an empty pair of parentheses when the function is
called.

</div>

<div class="section section">

[‌](){#TP40016643-CH10-ID528}
### Functions With Multiple Parameters {#functions-with-multiple-parameters .section-name}

Functions can have multiple input parameters, which are written within
the function’s parentheses, separated by commas.

This function takes a person’s name and whether they have already been
greeted as input, and returns an appropriate greeting for that person:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `sayHello`{.vc}(`personName`{.vc}: `String`{.n},
    `alreadyGreeted`{.vc}: `Bool`{.n}) -&gt; `String`{.n} {
2.  `    if`{.code-voice} `alreadyGreeted`{.vc} {
3.  `        return`{.code-voice}
    `sayHelloAgain`{.vc}(`personName`{.vc})
4.  `    } else`{.code-voice} {
5.  `        return`{.code-voice} `sayHello`{.vc}(`personName`{.vc})
6.  `    }`{.code-voice}
7.  `}`{.code-voice}
8.  `print`{.code-voice}(`sayHello`{.vc}(`"Tim"`{.s},
    `alreadyGreeted`{.vc}: `true`{.kt}))
9.  `// prints "Hello again, Tim!"`{.code-voice}

</div>

</div>

</div>

You call the `sayHello(_:alreadyGreeted:)`{.code-voice} function by
passing it both a `String`{.code-voice} argument value and a
`Bool`{.code-voice} argument value labeled `alreadyGreeted`{.code-voice}
in parentheses, separated by commas. Note that this function is distinct
from the `sayHello(_:)`{.code-voice} function shown in an earlier
section. Although both functions have names that begin with
`sayHello`{.code-voice}, the `sayHello(_:alreadyGreeted:)`{.code-voice}
function takes two arguments but the `sayHello(_:)`{.code-voice}
function takes only one.

When calling a function with more than one parameter, any argument after
the first is labeled according to its corresponding parameter name.
Function parameter naming is described in more detail in [Function
Parameter Names](Functions.md#TP40016643-CH10-ID166).

</div>

<div class="section section">

[‌](){#TP40016643-CH10-ID163}
### Functions Without Return Values {#functions-without-return-values .section-name}

Functions are not required to define a return type. Here’s a version of
the `sayHello(_:)`{.code-voice} function, called
`sayGoodbye(_:)`{.code-voice}, which prints its own
`String`{.code-voice} value rather than returning it:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `sayGoodbye`{.vc}(`personName`{.vc}:
    `String`{.n}) {
2.  `    print`{.code-voice}(`"Goodbye, `{.s}\\(`personName`{.vc})`!"`{.s})
3.  `}`{.code-voice}
4.  `sayGoodbye`{.code-voice}(`"Dave"`{.s})
5.  `// prints "Goodbye, Dave!"`{.code-voice}

</div>

</div>

</div>

Because it does not need to return a value, the function’s definition
does not include the return arrow (`->`{.code-voice}) or a return type.

<div class="note">

Note

Strictly speaking, the `sayGoodbye(_:)`{.code-voice} function *does*
still return a value, even though no return value is defined. Functions
without a defined return type return a special value of type
`Void`{.code-voice}. This is simply an empty tuple, in effect a tuple
with zero elements, which can be written as `()`{.code-voice}.

</div>

The return value of a function can be ignored when it is called:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `printAndCount`{.vc}(`stringToPrint`{.vc}:
    `String`{.n}) -&gt; `Int`{.n} {
2.  `    print`{.code-voice}(`stringToPrint`{.vc})
3.  `    return`{.code-voice}
    `stringToPrint`{.vc}.`characters`{.vc}.`count`{.vc}
4.  `}`{.code-voice}
5.  `func`{.code-voice}
    `printWithoutCounting`{.vc}(`stringToPrint`{.vc}: `String`{.n}) {
6.  `    printAndCount`{.code-voice}(`stringToPrint`{.vc})
7.  `}`{.code-voice}
8.  `printAndCount`{.code-voice}(`"hello, world"`{.s})
9.  `// prints "hello, world" and returns a value of 12`{.code-voice}
10. `printWithoutCounting`{.code-voice}(`"hello, world"`{.s})
11. `// prints "hello, world" but does not return a value`{.code-voice}

</div>

</div>

</div>

The first function, `printAndCount(_:)`{.code-voice}, prints a string,
and then returns its character count as an `Int`{.code-voice}. The
second function, `printWithoutCounting`{.code-voice}, calls the first
function, but ignores its return value. When the second function is
called, the message is still printed by the first function, but the
returned value is not used.

<div class="note">

Note

Return values can be ignored, but a function that says it will return a
value must always do so. A function with a defined return type cannot
allow control to fall out of the bottom of the function without
returning a value, and attempting to do so will result in a compile-time
error.

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH10-ID164}
### Functions with Multiple Return Values {#functions-with-multiple-return-values .section-name}

You can use a tuple type as the return type for a function to return
multiple values as part of one compound return value.

The example below defines a function called `minMax(_:)`{.code-voice},
which finds the smallest and largest numbers in an array of
`Int`{.code-voice} values:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `minMax`{.vc}(`array`{.vc}: \[`Int`{.n}\]) -&gt;
    (`min`{.vc}: `Int`{.n}, `max`{.vc}: `Int`{.n}) {
2.  `    var`{.code-voice} `currentMin`{.vc} = `array`{.vc}\[`0`{.m}\]
3.  `    var`{.code-voice} `currentMax`{.vc} = `array`{.vc}\[`0`{.m}\]
4.  `    for`{.code-voice} `value`{.vc} `in`{.kt}
    `array`{.vc}\[`1`{.m}..&lt;`array`{.vc}.`count`{.vc}\] {
5.  `        if`{.code-voice} `value`{.vc} &lt; `currentMin`{.vc} {
6.  `            currentMin`{.code-voice} = `value`{.vc}
7.  `        } else`{.code-voice} `if`{.kt} `value`{.vc} &gt;
    `currentMax`{.vc} {
8.  `            currentMax`{.code-voice} = `value`{.vc}
9.  `        }`{.code-voice}
10. `    }`{.code-voice}
11. `    return`{.code-voice} (`currentMin`{.vc}, `currentMax`{.vc})
12. `}`{.code-voice}

</div>

</div>

</div>

The `minMax(_:)`{.code-voice} function returns a tuple containing two
`Int`{.code-voice} values. These values are labeled `min`{.code-voice}
and `max`{.code-voice} so that they can be accessed by name when
querying the function’s return value.

The body of the `minMax(_:)`{.code-voice} function starts by setting two
working variables called `currentMin`{.code-voice} and
`currentMax`{.code-voice} to the value of the first integer in the
array. The function then iterates over the remaining values in the array
and checks each value to see if it is smaller or larger than the values
of `currentMin`{.code-voice} and `currentMax`{.code-voice} respectively.
Finally, the overall minimum and maximum values are returned as a tuple
of two `Int`{.code-voice} values.

Because the tuple’s member values are named as part of the function’s
return type, they can be accessed with dot syntax to retrieve the
minimum and maximum found values:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `bounds`{.vc} = `minMax`{.vc}(\[`8`{.m},
    -`6`{.m}, `2`{.m}, `109`{.m}, `3`{.m}, `71`{.m}\])
2.  `print`{.code-voice}(`"min is `{.s}\\(`bounds`{.vc}.`min`{.vc})` and max is `{.s}\\(`bounds`{.vc}.`max`{.vc})`"`{.s})
3.  `// prints "min is -6 and max is 109"`{.code-voice}

</div>

</div>

</div>

Note that the tuple’s members do not need to be named at the point that
the tuple is returned from the function, because their names are already
specified as part of the function’s return type.

<div class="section section">

[‌](){#TP40016643-CH10-ID165}
### Optional Tuple Return Types {#optional-tuple-return-types .section-name}

If the tuple type to be returned from a function has the potential to
have “no value” for the entire tuple, you can use an *optional* tuple
return type to reflect the fact that the entire tuple can be
`nil`{.code-voice}. You write an optional tuple return type by placing a
question mark after the tuple type’s closing parenthesis, such as
`(Int, Int)?`{.code-voice} or `(String, Int, Bool)?`{.code-voice}.

<div class="note">

Note

An optional tuple type such as `(Int, Int)?`{.code-voice} is different
from a tuple that contains optional types such as
`(Int?, Int?)`{.code-voice}. With an optional tuple type, the entire
tuple is optional, not just each individual value within the tuple.

</div>

The `minMax(_:)`{.code-voice} function above returns a tuple containing
two `Int`{.code-voice} values. However, the function does not perform
any safety checks on the array it is passed. If the `array`{.code-voice}
argument contains an empty array, the `minMax(_:)`{.code-voice}
function, as defined above, will trigger a runtime error when attempting
to access `array[0]`{.code-voice}.

To handle this “empty array” scenario safely, write the
`minMax(_:)`{.code-voice} function with an optional tuple return type
and return a value of `nil`{.code-voice} when the array is empty:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `minMax`{.vc}(`array`{.vc}: \[`Int`{.n}\]) -&gt;
    (`min`{.vc}: `Int`{.n}, `max`{.vc}: `Int`{.n})? {
2.  `    if`{.code-voice} `array`{.vc}.`isEmpty`{.vc} { `return`{.kt}
    `nil`{.kt} }
3.  `    var`{.code-voice} `currentMin`{.vc} = `array`{.vc}\[`0`{.m}\]
4.  `    var`{.code-voice} `currentMax`{.vc} = `array`{.vc}\[`0`{.m}\]
5.  `    for`{.code-voice} `value`{.vc} `in`{.kt}
    `array`{.vc}\[`1`{.m}..&lt;`array`{.vc}.`count`{.vc}\] {
6.  `        if`{.code-voice} `value`{.vc} &lt; `currentMin`{.vc} {
7.  `            currentMin`{.code-voice} = `value`{.vc}
8.  `        } else`{.code-voice} `if`{.kt} `value`{.vc} &gt;
    `currentMax`{.vc} {
9.  `            currentMax`{.code-voice} = `value`{.vc}
10. `        }`{.code-voice}
11. `    }`{.code-voice}
12. `    return`{.code-voice} (`currentMin`{.vc}, `currentMax`{.vc})
13. `}`{.code-voice}

</div>

</div>

</div>

You can use optional binding to check whether this version of the
`minMax(_:)`{.code-voice} function returns an actual tuple value or
`nil`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `if`{.code-voice} `let`{.kt} `bounds`{.vc} =
    `minMax`{.vc}(\[`8`{.m}, -`6`{.m}, `2`{.m}, `109`{.m}, `3`{.m},
    `71`{.m}\]) {
2.  `    print`{.code-voice}(`"min is `{.s}\\(`bounds`{.vc}.`min`{.vc})` and max is `{.s}\\(`bounds`{.vc}.`max`{.vc})`"`{.s})
3.  `}`{.code-voice}
4.  `// prints "min is -6 and max is 109"`{.code-voice}

</div>

</div>

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH10-ID166}
### Function Parameter Names {#function-parameter-names .section-name}

Function parameters have both an *external parameter name* and a *local
parameter name*. An external parameter name is used to label arguments
passed to a function call. A local parameter name is used in the
implementation of the function.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `someFunction`{.vc}(`firstParameterName`{.vc}:
    `Int`{.n}, `secondParameterName`{.vc}: `Int`{.n}) {
2.  `    // function body goes here`{.code-voice}
3.  `    // firstParameterName and secondParameterName refer to`{.code-voice}
4.  `    // the argument values for the first and second parameters`{.code-voice}
5.  `}`{.code-voice}
6.  `someFunction`{.code-voice}(`1`{.m}, `secondParameterName`{.vc}:
    `2`{.m})

</div>

</div>

</div>

By default, the first parameter omits its external name, and the second
and subsequent parameters use their local name as their external name.
All parameters must have unique local names. Although it’s possible for
multiple parameters to have the same external name, unique external
names help make your code more readable.

<div class="section section">

[‌](){#TP40016643-CH10-ID167}
### Specifying External Parameter Names {#specifying-external-parameter-names .section-name}

You write an external parameter name before the local parameter name it
supports, separated by a space:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `someFunction`{.vc}(`externalParameterName`{.vc}
    `localParameterName`{.vc}: `Int`{.n}) {
2.  `    // function body goes here, and can use localParameterName`{.code-voice}
3.  `    // to refer to the argument value for that parameter`{.code-voice}
4.  `}`{.code-voice}

</div>

</div>

</div>

<div class="note">

Note

If you provide an external parameter name for a parameter, that external
name must *always* be used when you call the function.

</div>

Here’s a version of the `sayHello(_:)`{.code-voice} function that takes
the names of two people and returns a greeting for both of them:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `sayHello`{.vc}(`to`{.vc} `person`{.vc}:
    `String`{.n}, `and`{.vc} `anotherPerson`{.vc}: `String`{.n}) -&gt;
    `String`{.n} {
2.  `    return`{.code-voice}
    `"Hello `{.s}\\(`person`{.vc})` and `{.s}\\(`anotherPerson`{.vc})`!"`{.s}
3.  `}`{.code-voice}
4.  `print`{.code-voice}(`sayHello`{.vc}(`to`{.vc}: `"Bill"`{.s},
    `and`{.vc}: `"Ted"`{.s}))
5.  `// prints "Hello Bill and Ted!"`{.code-voice}

</div>

</div>

</div>

By specifying external parameter names for both parameters, both the
first and second arguments to the `sayHello(to:and:)`{.code-voice}
function must be labeled when you call it.

The use of external parameter names can allow a function to be called in
an expressive, sentence-like manner, while still providing a function
body that is readable and clear in intent.

</div>

<div class="section section">

[‌](){#TP40016643-CH10-ID526}
### Omitting External Parameter Names {#omitting-external-parameter-names .section-name}

If you do not want to use an external name for the second or subsequent
parameters of a function, write an underscore (`_`{.code-voice}) instead
of an explicit external name for that parameter.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `someFunction`{.vc}(`firstParameterName`{.vc}:
    `Int`{.n}, `_`{.kt} `secondParameterName`{.vc}: `Int`{.n}) {
2.  `    // function body goes here`{.code-voice}
3.  `    // firstParameterName and secondParameterName refer to`{.code-voice}
4.  `    // the argument values for the first and second parameters`{.code-voice}
5.  `}`{.code-voice}
6.  `someFunction`{.code-voice}(`1`{.m}, `2`{.m})

</div>

</div>

</div>

<div class="note">

Note

Because the first parameter omits its external parameter name by
default, explicitly writing an underscore is extraneous.

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH10-ID169}
### Default Parameter Values {#default-parameter-values .section-name}

You can define a *default value* for any parameter in a function by
assigning a value to the parameter after that parameter’s type. If a
default value is defined, you can omit that parameter when calling the
function.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `someFunction`{.vc}(`parameterWithDefault`{.vc}:
    `Int`{.n} = `12`{.m}) {
2.  `    // function body goes here`{.code-voice}
3.  `    // if no arguments are passed to the function call,`{.code-voice}
4.  `    // value of parameterWithDefault is 12`{.code-voice}
5.  `}`{.code-voice}
6.  `someFunction`{.code-voice}(`6`{.m})
    `// parameterWithDefault is 6`{.c}
7.  `someFunction`{.code-voice}() `// parameterWithDefault is 12`{.c}

</div>

</div>

</div>

<div class="note">

Note

Place parameters with default values at the end of a function’s
parameter list. This ensures that all calls to the function use the same
order for their nondefault arguments, and makes it clear that the same
function is being called in each case.

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH10-ID171}
### Variadic Parameters {#variadic-parameters .section-name}

A *variadic parameter* accepts zero or more values of a specified type.
You use a variadic parameter to specify that the parameter can be passed
a varying number of input values when the function is called. Write
variadic parameters by inserting three period characters
(`...`{.code-voice}) after the parameter’s type name.

The values passed to a variadic parameter are made available within the
function’s body as an array of the appropriate type. For example, a
variadic parameter with a name of `numbers`{.code-voice} and a type of
`Double...`{.code-voice} is made available within the function’s body as
a constant array called `numbers`{.code-voice} of type
`[Double]`{.code-voice}.

The example below calculates the *arithmetic mean* (also known as the
*average*) for a list of numbers of any length:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `arithmeticMean`{.vc}(`numbers`{.vc}:
    `Double`{.n}...) -&gt; `Double`{.n} {
2.  `    var`{.code-voice} `total`{.vc}: `Double`{.n} = `0`{.m}
3.  `    for`{.code-voice} `number`{.vc} `in`{.kt} `numbers`{.vc} {
4.  `        total`{.code-voice} += `number`{.vc}
5.  `    }`{.code-voice}
6.  `    return`{.code-voice} `total`{.vc} /
    `Double`{.vc}(`numbers`{.vc}.`count`{.vc})
7.  `}`{.code-voice}
8.  `arithmeticMean`{.code-voice}(`1`{.m}, `2`{.m}, `3`{.m}, `4`{.m},
    `5`{.m})
9.  `// returns 3.0, which is the arithmetic mean of these five numbers`{.code-voice}
10. `arithmeticMean`{.code-voice}(`3`{.m}, `8.25`{.m}, `18.75`{.m})
11. `// returns 10.0, which is the arithmetic mean of these three numbers`{.code-voice}

</div>

</div>

</div>

<div class="note">

Note

A function may have at most one variadic parameter.

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH10-ID173}
### In-Out Parameters {#in-out-parameters .section-name}

Function parameters are constants by default. Trying to change the value
of a function parameter from within the body of that function results in
a compile-time error. This means that you can’t change the value of a
parameter by mistake. If you want a function to modify a parameter’s
value, and you want those changes to persist after the function call has
ended, define that parameter as an *in-out parameter* instead.

You write an in-out parameter by placing the `inout`{.code-voice}
keyword at the start of its parameter definition. An in-out parameter
has a value that is passed *in* to the function, is modified by the
function, and is passed back *out* of the function to replace the
original value. For a detailed discussion of the behavior of in-out
parameters and associated compiler optimizations, see [In-Out
Parameters](Declarations.md#TP40016643-CH34-ID545).

You can only pass a variable as the argument for an in-out parameter.
You cannot pass a constant or a literal value as the argument, because
constants and literals cannot be modified. You place an ampersand
(`&`{.code-voice}) directly before a variable’s name when you pass it as
an argument to an in-out parameter, to indicate that it can be modified
by the function.

<div class="note">

Note

In-out parameters cannot have default values, and variadic parameters
cannot be marked as `inout`{.code-voice}.

</div>

Here’s an example of a function called `swapTwoInts(_:_:)`{.code-voice},
which has two in-out integer parameters called `a`{.code-voice} and
`b`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `swapTwoInts`{.vc}(`inout`{.kt} `a`{.vc}:
    `Int`{.n}, `inout`{.kt} `_`{.kt} `b`{.vc}: `Int`{.n}) {
2.  `    let`{.code-voice} `temporaryA`{.vc} = `a`{.vc}
3.  `    a`{.code-voice} = `b`{.vc}
4.  `    b`{.code-voice} = `temporaryA`{.vc}
5.  `}`{.code-voice}

</div>

</div>

</div>

The `swapTwoInts(_:_:)`{.code-voice} function simply swaps the value of
`b`{.code-voice} into `a`{.code-voice}, and the value of
`a`{.code-voice} into `b`{.code-voice}. The function performs this swap
by storing the value of `a`{.code-voice} in a temporary constant called
`temporaryA`{.code-voice}, assigning the value of `b`{.code-voice} to
`a`{.code-voice}, and then assigning `temporaryA`{.code-voice} to
`b`{.code-voice}.

You can call the `swapTwoInts(_:_:)`{.code-voice} function with two
variables of type `Int`{.code-voice} to swap their values. Note that the
names of `someInt`{.code-voice} and `anotherInt`{.code-voice} are
prefixed with an ampersand when they are passed to the
`swapTwoInts(_:_:)`{.code-voice} function:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `someInt`{.vc} = `3`{.m}
2.  `var`{.code-voice} `anotherInt`{.vc} = `107`{.m}
3.  `swapTwoInts`{.code-voice}(&`someInt`{.vc}, &`anotherInt`{.vc})
4.  `print`{.code-voice}(`"someInt is now `{.s}\\(`someInt`{.vc})`, and anotherInt is now `{.s}\\(`anotherInt`{.vc})`"`{.s})
5.  `// prints "someInt is now 107, and anotherInt is now 3"`{.code-voice}

</div>

</div>

</div>

The example above shows that the original values of
`someInt`{.code-voice} and `anotherInt`{.code-voice} are modified by the
`swapTwoInts(_:_:)`{.code-voice} function, even though they were
originally defined outside of the function.

<div class="note">

Note

In-out parameters are not the same as returning a value from a function.
The `swapTwoInts`{.code-voice} example above does not define a return
type or return a value, but it still modifies the values of
`someInt`{.code-voice} and `anotherInt`{.code-voice}. In-out parameters
are an alternative way for a function to have an effect outside of the
scope of its function body.

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH10-ID174}
### Function Types {#function-types .section-name}

Every function has a specific *function type*, made up of the parameter
types and the return type of the function.

For example:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `addTwoInts`{.vc}(`a`{.vc}: `Int`{.n}, `_`{.kt}
    `b`{.vc}: `Int`{.n}) -&gt; `Int`{.n} {
2.  `    return`{.code-voice} `a`{.vc} + `b`{.vc}
3.  `}`{.code-voice}
4.  `func`{.code-voice} `multiplyTwoInts`{.vc}(`a`{.vc}: `Int`{.n},
    `_`{.kt} `b`{.vc}: `Int`{.n}) -&gt; `Int`{.n} {
5.  `    return`{.code-voice} `a`{.vc} \* `b`{.vc}
6.  `}`{.code-voice}

</div>

</div>

</div>

This example defines two simple mathematical functions called
`addTwoInts`{.code-voice} and `multiplyTwoInts`{.code-voice}. These
functions each take two `Int`{.code-voice} values, and return an
`Int`{.code-voice} value, which is the result of performing an
appropriate mathematical operation.

The type of both of these functions is `(Int, Int) -> Int`{.code-voice}.
This can be read as:

“A function type that has two parameters, both of type
`Int`{.code-voice}, and that returns a value of type
`Int`{.code-voice}.”

Here’s another example, for a function with no parameters or return
value:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `printHelloWorld`{.vc}() {
2.  `    print`{.code-voice}(`"hello, world"`{.s})
3.  `}`{.code-voice}

</div>

</div>

</div>

The type of this function is `() -> Void`{.code-voice}, or “a function
that has no parameters, and returns `Void`{.code-voice}.”

<div class="section section">

[‌](){#TP40016643-CH10-ID175}
### Using Function Types {#using-function-types .section-name}

You use function types just like any other types in Swift. For example,
you can define a constant or variable to be of a function type and
assign an appropriate function to that variable:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `mathFunction`{.vc}: (`Int`{.n}, `Int`{.n}) -&gt;
    `Int`{.n} = `addTwoInts`{.vc}

</div>

</div>

</div>

This can be read as:

“Define a variable called `mathFunction`{.code-voice}, which has a type
of ‘a function that takes two `Int`{.code-voice} values, and returns an
`Int`{.code-voice} value.’ Set this new variable to refer to the
function called `addTwoInts`{.code-voice}.”

The `addTwoInts(_:_:)`{.code-voice} function has the same type as the
`mathFunction`{.code-voice} variable, and so this assignment is allowed
by Swift’s type-checker.

You can now call the assigned function with the name
`mathFunction`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `print`{.code-voice}(`"Result: `{.s}\\(`mathFunction`{.vc}(`2`{.m},
    `3`{.m}))`"`{.s})
2.  `// prints "Result: 5"`{.code-voice}

</div>

</div>

</div>

A different function with the same matching type can be assigned to the
same variable, in the same way as for non-function types:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `mathFunction`{.code-voice} = `multiplyTwoInts`{.vc}
2.  `print`{.code-voice}(`"Result: `{.s}\\(`mathFunction`{.vc}(`2`{.m},
    `3`{.m}))`"`{.s})
3.  `// prints "Result: 6"`{.code-voice}

</div>

</div>

</div>

As with any other type, you can leave it to Swift to infer the function
type when you assign a function to a constant or variable:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `anotherMathFunction`{.vc} = `addTwoInts`{.vc}
2.  `// anotherMathFunction is inferred to be of type (Int, Int) -> Int`{.code-voice}

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH10-ID176}
### Function Types as Parameter Types {#function-types-as-parameter-types .section-name}

You can use a function type such as `(Int, Int) -> Int`{.code-voice} as
a parameter type for another function. This enables you to leave some
aspects of a function’s implementation for the function’s caller to
provide when the function is called.

Here’s an example to print the results of the math functions from above:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `printMathResult`{.vc}(`mathFunction`{.vc}:
    (`Int`{.n}, `Int`{.n}) -&gt; `Int`{.n}, `_`{.kt} `a`{.vc}:
    `Int`{.n}, `_`{.kt} `b`{.vc}: `Int`{.n}) {
2.  `    print`{.code-voice}(`"Result: `{.s}\\(`mathFunction`{.vc}(`a`{.vc},
    `b`{.vc}))`"`{.s})
3.  `}`{.code-voice}
4.  `printMathResult`{.code-voice}(`addTwoInts`{.vc}, `3`{.m}, `5`{.m})
5.  `// prints "Result: 8"`{.code-voice}

</div>

</div>

</div>

This example defines a function called
`printMathResult(_:_:_:)`{.code-voice}, which has three parameters. The
first parameter is called `mathFunction`{.code-voice}, and is of type
`(Int, Int) -> Int`{.code-voice}. You can pass any function of that type
as the argument for this first parameter. The second and third
parameters are called `a`{.code-voice} and `b`{.code-voice}, and are
both of type `Int`{.code-voice}. These are used as the two input values
for the provided math function.

When `printMathResult(_:_:_:)`{.code-voice} is called, it is passed the
`addTwoInts(_:_:)`{.code-voice} function, and the integer values
`3`{.code-voice} and `5`{.code-voice}. It calls the provided function
with the values `3`{.code-voice} and `5`{.code-voice}, and prints the
result of `8`{.code-voice}.

The role of `printMathResult(_:_:_:)`{.code-voice} is to print the
result of a call to a math function of an appropriate type. It doesn’t
matter what that function’s implementation actually does—it matters only
that the function is of the correct type. This enables
`printMathResult(_:_:_:)`{.code-voice} to hand off some of its
functionality to the caller of the function in a type-safe way.

</div>

<div class="section section">

[‌](){#TP40016643-CH10-ID177}
### Function Types as Return Types {#function-types-as-return-types .section-name}

You can use a function type as the return type of another function. You
do this by writing a complete function type immediately after the return
arrow (`->`{.code-voice}) of the returning function.

The next example defines two simple functions called
`stepForward(_:)`{.code-voice} and `stepBackward(_:)`{.code-voice}. The
`stepForward(_:)`{.code-voice} function returns a value one more than
its input value, and the `stepBackward(_:)`{.code-voice} function
returns a value one less than its input value. Both functions have a
type of `(Int) -> Int`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `stepForward`{.vc}(`input`{.vc}: `Int`{.n})
    -&gt; `Int`{.n} {
2.  `    return`{.code-voice} `input`{.vc} + `1`{.m}
3.  `}`{.code-voice}
4.  `func`{.code-voice} `stepBackward`{.vc}(`input`{.vc}: `Int`{.n})
    -&gt; `Int`{.n} {
5.  `    return`{.code-voice} `input`{.vc} - `1`{.m}
6.  `}`{.code-voice}

</div>

</div>

</div>

Here’s a function called `chooseStepFunction(_:)`{.code-voice}, whose
return type is “a function of type `(Int) -> Int`{.code-voice}”. The
``` chooseStepFunction(_:)``function returns the ``stepForward(_:) ```{.code-voice}
function or the `stepBackward(_:)`{.code-voice} function based on a
Boolean parameter called `backwards`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `chooseStepFunction`{.vc}(`backwards`{.vc}:
    `Bool`{.n}) -&gt; (`Int`{.n}) -&gt; `Int`{.n} {
2.  `    return`{.code-voice} `backwards`{.vc} ? `stepBackward`{.vc} :
    `stepForward`{.vc}
3.  `}`{.code-voice}

</div>

</div>

</div>

You can now use `chooseStepFunction(_:)`{.code-voice} to obtain a
function that will step in one direction or the other:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `currentValue`{.vc} = `3`{.m}
2.  `let`{.code-voice} `moveNearerToZero`{.vc} =
    `chooseStepFunction`{.vc}(`currentValue`{.vc} &gt; `0`{.m})
3.  `// moveNearerToZero now refers to the stepBackward() function`{.code-voice}

</div>

</div>

</div>

The preceding example determines whether a positive or negative step is
needed to move a variable called `currentValue`{.code-voice}
progressively closer to zero. `currentValue`{.code-voice} has an initial
value of `3`{.code-voice}, which means that
`currentValue > 0`{.code-voice} returns `true`{.code-voice}, causing
`chooseStepFunction(_:)`{.code-voice} to return the
`stepBackward(_:)`{.code-voice} function. A reference to the returned
function is stored in a constant called `moveNearerToZero`{.code-voice}.

Now that `moveNearerToZero`{.code-voice} refers to the correct function,
it can be used to count to zero:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `print`{.code-voice}(`"Counting to zero:"`{.s})
2.  `// Counting to zero:`{.code-voice}
3.  `while`{.code-voice} `currentValue`{.vc} != `0`{.m} {
4.  `    print`{.code-voice}(`"`{.s}\\(`currentValue`{.vc})`... "`{.s})
5.  `    currentValue`{.code-voice} =
    `moveNearerToZero`{.vc}(`currentValue`{.vc})
6.  `}`{.code-voice}
7.  `print`{.code-voice}(`"zero!"`{.s})
8.  `// 3...`{.code-voice}
9.  `// 2...`{.code-voice}
10. `// 1...`{.code-voice}
11. `// zero!`{.code-voice}

</div>

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH10-ID178}
### Nested Functions {#nested-functions .section-name}

All of the functions you have encountered so far in this chapter have
been examples of *global functions*, which are defined at a global
scope. You can also define functions inside the bodies of other
functions, known as *nested functions*.

Nested functions are hidden from the outside world by default, but can
still be called and used by their enclosing function. An enclosing
function can also return one of its nested functions to allow the nested
function to be used in another scope.

You can rewrite the `chooseStepFunction(_:)`{.code-voice} example above
to use and return nested functions:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `chooseStepFunction`{.vc}(`backwards`{.vc}:
    `Bool`{.n}) -&gt; (`Int`{.n}) -&gt; `Int`{.n} {
2.  `    func`{.code-voice} `stepForward`{.vc}(`input`{.vc}: `Int`{.n})
    -&gt; `Int`{.n} { `return`{.kt} `input`{.vc} + `1`{.m} }
3.  `    func`{.code-voice} `stepBackward`{.vc}(`input`{.vc}: `Int`{.n})
    -&gt; `Int`{.n} { `return`{.kt} `input`{.vc} - `1`{.m} }
4.  `    return`{.code-voice} `backwards`{.vc} ? `stepBackward`{.vc} :
    `stepForward`{.vc}
5.  `}`{.code-voice}
6.  `var`{.code-voice} `currentValue`{.vc} = -`4`{.m}
7.  `let`{.code-voice} `moveNearerToZero`{.vc} =
    `chooseStepFunction`{.vc}(`currentValue`{.vc} &gt; `0`{.m})
8.  `// moveNearerToZero now refers to the nested stepForward() function`{.code-voice}
9.  `while`{.code-voice} `currentValue`{.vc} != `0`{.m} {
10. `    print`{.code-voice}(`"`{.s}\\(`currentValue`{.vc})`... "`{.s})
11. `    currentValue`{.code-voice} =
    `moveNearerToZero`{.vc}(`currentValue`{.vc})
12. `}`{.code-voice}
13. `print`{.code-voice}(`"zero!"`{.s})
14. `// -4...`{.code-voice}
15. `// -3...`{.code-voice}
16. `// -2...`{.code-voice}
17. `// -1...`{.code-voice}
18. `// zero!`{.code-voice}

</div>

</div>

</div>

</div>

</div>

</div>
