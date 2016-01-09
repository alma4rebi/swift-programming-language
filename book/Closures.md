<div class="content-wrapper">

<div id="chapter_container" class="conceptualwithtasks">

[‌](){#TP40016643-CH11}[‌](){#TP40016643-CH11-ID94}
Closures {#closures .chapter-name}
--------

<div class="section section">

*Closures* are self-contained blocks of functionality that can be passed
around and used in your code. Closures in Swift are similar to blocks in
C and Objective-C and to lambdas in other programming languages.

Closures can capture and store references to any constants and variables
from the context in which they are defined. This is known as *closing
over* those constants and variables. Swift handles all of the memory
management of capturing for you.

<div class="note">

Note

Don’t worry if you are not familiar with the concept of capturing. It is
explained in detail below in [Capturing
Values](Closures.md#TP40016643-CH11-ID103).

</div>

Global and nested functions, as introduced in
[Functions](Functions.md), are actually special cases of closures.
Closures take one of three forms:

-   Global functions are closures that have a name and do not capture
    any values.

-   Nested functions are closures that have a name and can capture
    values from their enclosing function.

-   Closure expressions are unnamed closures written in a lightweight
    syntax that can capture values from their surrounding context.

Swift’s closure expressions have a clean, clear style, with
optimizations that encourage brief, clutter-free syntax in common
scenarios. These optimizations include:

-   Inferring parameter and return value types from context

-   Implicit returns from single-expression closures

-   Shorthand argument names

-   Trailing closure syntax

</div>

<div class="section section">

[‌](){#TP40016643-CH11-ID95}
### Closure Expressions {#closure-expressions .section-name}

Nested functions, as introduced in [Nested
Functions](Functions.md#TP40016643-CH10-ID178), are a convenient
means of naming and defining self-contained blocks of code as part of a
larger function. However, it is sometimes useful to write shorter
versions of function-like constructs without a full declaration and
name. This is particularly true when you work with functions or methods
that take functions as one or more of their arguments.

*Closure expressions* are a way to write inline closures in a brief,
focused syntax. Closure expressions provide several syntax optimizations
for writing closures in a shortened form without loss of clarity or
intent. The closure expression examples below illustrate these
optimizations by refining a single example of the
`sort(_:)`{.code-voice} method over several iterations, each of which
expresses the same functionality in a more succinct way.

<div class="section section">

[‌](){#TP40016643-CH11-ID96}
### The Sort Method {#the-sort-method .section-name}

Swift’s standard library provides a method called
`sort(_:)`{.code-voice}, which sorts an array of values of a known type,
based on the output of a sorting closure that you provide. Once it
completes the sorting process, the `sort(_:)`{.code-voice} method
returns a new array of the same type and size as the old one, with its
elements in the correct sorted order. The original array is not modified
by the `sort(_:)`{.code-voice} method.

The closure expression examples below use the `sort(_:)`{.code-voice}
method to sort an array of `String`{.code-voice} values in reverse
alphabetical order. Here’s the initial array to be sorted:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `names`{.vc} = \[`"Chris"`{.s}, `"Alex"`{.s},
    `"Ewa"`{.s}, `"Barry"`{.s}, `"Daniella"`{.s}\]

</div>

</div>

</div>

The `sort(_:)`{.code-voice} method accepts a closure that takes two
arguments of the same type as the array’s contents, and returns a
`Bool`{.code-voice} value to say whether the first value should appear
before or after the second value once the values are sorted. The sorting
closure needs to return `true`{.code-voice} if the first value should
appear *before* the second value, and `false`{.code-voice} otherwise.

This example is sorting an array of `String`{.code-voice} values, and so
the sorting closure needs to be a function of type
`(String, String) -> Bool`{.code-voice}.

One way to provide the sorting closure is to write a normal function of
the correct type, and to pass it in as an argument to the
`sort(_:)`{.code-voice} method:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `backwards`{.vc}(`s1`{.vc}: `String`{.n},
    `_`{.kt} `s2`{.vc}: `String`{.n}) -&gt; `Bool`{.n} {
2.  `    return`{.code-voice} `s1`{.vc} &gt; `s2`{.vc}
3.  `}`{.code-voice}
4.  `var`{.code-voice} `reversed`{.vc} =
    `names`{.vc}.`sort`{.vc}(`backwards`{.vc})
5.  `// reversed is equal to ["Ewa", "Daniella", "Chris", "Barry", "Alex"]`{.code-voice}

</div>

</div>

</div>

If the first string (`s1`{.code-voice}) is greater than the second
string (`s2`{.code-voice}), the `backwards(_:_:)`{.code-voice} function
will return `true`{.code-voice}, indicating that `s1`{.code-voice}
should appear before `s2`{.code-voice} in the sorted array. For
characters in strings, “greater than” means “appears later in the
alphabet than”. This means that the letter `"B"`{.code-voice} is
“greater than” the letter `"A"`{.code-voice}, and the string
`"Tom"`{.code-voice} is greater than the string `"Tim"`{.code-voice}.
This gives a reverse alphabetical sort, with `"Barry"`{.code-voice}
being placed before `"Alex"`{.code-voice}, and so on.

However, this is a rather long-winded way to write what is essentially a
single-expression function (`a > b`{.code-voice}). In this example, it
would be preferable to write the sorting closure inline, using closure
expression syntax.

</div>

<div class="section section">

[‌](){#TP40016643-CH11-ID97}
### Closure Expression Syntax {#closure-expression-syntax .section-name}

Closure expression syntax has the following general form:

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

Closure expression syntax can use constant parameters, variable
parameters, and `inout`{.code-voice} parameters. Default values cannot
be provided. Variadic parameters can be used if you name the variadic
parameter. Tuples can also be used as parameter types and return types.

The example below shows a closure expression version of the
`backwards(_:_:)`{.code-voice} function from earlier:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `reversed`{.code-voice} = `names`{.vc}.`sort`{.vc}({ (`s1`{.vc}:
    `String`{.n}, `s2`{.vc}: `String`{.n}) -&gt; `Bool`{.n} `in`{.kt}
2.  `    return`{.code-voice} `s1`{.vc} &gt; `s2`{.vc}
3.  `})`{.code-voice}

</div>

</div>

</div>

Note that the declaration of parameters and return type for this inline
closure is identical to the declaration from the
`backwards(_:_:)`{.code-voice} function. In both cases, it is written as
`(s1: String, s2: String) -> Bool`{.code-voice}. However, for the inline
closure expression, the parameters and return type are written *inside*
the curly braces, not outside of them.

The start of the closure’s body is introduced by the `in`{.code-voice}
keyword. This keyword indicates that the definition of the closure’s
parameters and return type has finished, and the body of the closure is
about to begin.

Because the body of the closure is so short, it can even be written on a
single line:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `reversed`{.code-voice} = `names`{.vc}.`sort`{.vc}( { (`s1`{.vc}:
    `String`{.n}, `s2`{.vc}: `String`{.n}) -&gt; `Bool`{.n} `in`{.kt}
    `return`{.kt} `s1`{.vc} &gt; `s2`{.vc} } )

</div>

</div>

</div>

This illustrates that the overall call to the `sort(_:)`{.code-voice}
method has remained the same. A pair of parentheses still wrap the
entire argument for the method. However, that argument is now an inline
closure.

</div>

<div class="section section">

[‌](){#TP40016643-CH11-ID98}
### Inferring Type From Context {#inferring-type-from-context .section-name}

Because the sorting closure is passed as an argument to a method, Swift
can infer the types of its parameters and the type of the value it
returns. The `sort(_:)`{.code-voice} method is being called on an array
of strings, so its argument must be a function of type
`(String, String) -> Bool`{.code-voice}. This means that the
`(String, String)`{.code-voice} and `Bool`{.code-voice} types do not
need to be written as part of the closure expression’s definition.
Because all of the types can be inferred, the return arrow
(`->`{.code-voice}) and the parentheses around the names of the
parameters can also be omitted:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `reversed`{.code-voice} = `names`{.vc}.`sort`{.vc}( { `s1`{.vc},
    `s2`{.vc} `in`{.kt} `return`{.kt} `s1`{.vc} &gt; `s2`{.vc} } )

</div>

</div>

</div>

It is always possible to infer the parameter types and return type when
passing a closure to a function or method as an inline closure
expression. As a result, you never need to write an inline closure in
its fullest form when the closure is used as a function or method
argument.

Nonetheless, you can still make the types explicit if you wish, and
doing so is encouraged if it avoids ambiguity for readers of your code.
In the case of the `sort(_:)`{.code-voice} method, the purpose of the
closure is clear from the fact that sorting is taking place, and it is
safe for a reader to assume that the closure is likely to be working
with `String`{.code-voice} values, because it is assisting with the
sorting of an array of strings.

</div>

<div class="section section">

[‌](){#TP40016643-CH11-ID99}
### Implicit Returns from Single-Expression Closures {#implicit-returns-from-single-expression-closures .section-name}

Single-expression closures can implicitly return the result of their
single expression by omitting the `return`{.code-voice} keyword from
their declaration, as in this version of the previous example:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `reversed`{.code-voice} = `names`{.vc}.`sort`{.vc}( { `s1`{.vc},
    `s2`{.vc} `in`{.kt} `s1`{.vc} &gt; `s2`{.vc} } )

</div>

</div>

</div>

Here, the function type of the `sort(_:)`{.code-voice} method’s argument
makes it clear that a `Bool`{.code-voice} value must be returned by the
closure. Because the closure’s body contains a single expression
(`s1 > s2`{.code-voice}) that returns a `Bool`{.code-voice} value, there
is no ambiguity, and the `return`{.code-voice} keyword can be omitted.

</div>

<div class="section section">

[‌](){#TP40016643-CH11-ID100}
### Shorthand Argument Names {#shorthand-argument-names .section-name}

Swift automatically provides shorthand argument names to inline
closures, which can be used to refer to the values of the closure’s
arguments by the names `$0`{.code-voice}, `$1`{.code-voice},
`$2`{.code-voice}, and so on.

If you use these shorthand argument names within your closure
expression, you can omit the closure’s argument list from its
definition, and the number and type of the shorthand argument names will
be inferred from the expected function type. The `in`{.code-voice}
keyword can also be omitted, because the closure expression is made up
entirely of its body:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `reversed`{.code-voice} = `names`{.vc}.`sort`{.vc}( { `$0`{.vc} &gt;
    `$1`{.vc} } )

</div>

</div>

</div>

Here, `$0`{.code-voice} and `$1`{.code-voice} refer to the closure’s
first and second `String`{.code-voice} arguments.

</div>

<div class="section section">

[‌](){#TP40016643-CH11-ID101}
### Operator Functions {#operator-functions .section-name}

There’s actually an even *shorter* way to write the closure expression
above. Swift’s `String`{.code-voice} type defines its string-specific
implementation of the greater-than operator (`>`{.code-voice}) as a
function that has two parameters of type `String`{.code-voice}, and
returns a value of type `Bool`{.code-voice}. This exactly matches the
function type needed by the `sort(_:)`{.code-voice} method. Therefore,
you can simply pass in the greater-than operator, and Swift will infer
that you want to use its string-specific implementation:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `reversed`{.code-voice} = `names`{.vc}.`sort`{.vc}(&gt;)

</div>

</div>

</div>

For more about operator functions, see [Operator
Functions](AdvancedOperators.md#TP40016643-CH27-ID42).

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH11-ID102}
### Trailing Closures {#trailing-closures .section-name}

If you need to pass a closure expression to a function as the function’s
final argument and the closure expression is long, it can be useful to
write it as a *trailing closure* instead. A trailing closure is a
closure expression that is written outside of (and *after*) the
parentheses of the function call it supports:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice}
    `someFunctionThatTakesAClosure`{.vc}(`closure`{.vc}: () -&gt;
    `Void`{.n}) {
2.  `    // function body goes here`{.code-voice}
3.  `}`{.code-voice}
4.  ` `{.code-voice}
5.  `// here's how you call this function without using a trailing closure:`{.code-voice}
6.  ` `{.code-voice}
7.  `someFunctionThatTakesAClosure`{.code-voice}({
8.  `    // closure's body goes here`{.code-voice}
9.  `})`{.code-voice}
10. ` `{.code-voice}
11. `// here's how you call this function with a trailing closure instead:`{.code-voice}
12. ` `{.code-voice}
13. `someFunctionThatTakesAClosure`{.code-voice}() {
14. `    // trailing closure's body goes here`{.code-voice}
15. `}`{.code-voice}

</div>

</div>

</div>

The string-sorting closure from the [Closure Expression
Syntax](Closures.md#TP40016643-CH11-ID97) section above can be
written outside of the `sort(_:)`{.code-voice} method’s parentheses as a
trailing closure:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `reversed`{.code-voice} = `names`{.vc}.`sort`{.vc}() {
    `$0`{.vc} &gt; `$1`{.vc} }

</div>

</div>

</div>

If a closure expression is provided as the function or method’s only
argument and you provide that expression as a trailing closure, you do
not need to write a pair of parentheses `()`{.code-voice} after the
function or method’s name when you call the function:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `reversed`{.code-voice} = `names`{.vc}.`sort`{.vc} { `$0`{.vc} &gt;
    `$1`{.vc} }

</div>

</div>

</div>

Trailing closures are most useful when the closure is sufficiently long
that it is not possible to write it inline on a single line. As an
example, Swift’s `Array`{.code-voice} type has a `map(_:)`{.code-voice}
method which takes a closure expression as its single argument. The
closure is called once for each item in the array, and returns an
alternative mapped value (possibly of some other type) for that item.
The nature of the mapping and the type of the returned value is left up
to the closure to specify.

After applying the provided closure to each array element, the
`map(_:)`{.code-voice} method returns a new array containing all of the
new mapped values, in the same order as their corresponding values in
the original array.

Here’s how you can use the `map(_:)`{.code-voice} method with a trailing
closure to convert an array of `Int`{.code-voice} values into an array
of `String`{.code-voice} values. The array `[16, 58, 510]`{.code-voice}
is used to create the new array
`["OneSix", "FiveEight", "FiveOneZero"]`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `digitNames`{.vc} = \[
2.  `    0`{.code-voice}: `"Zero"`{.s}, `1`{.m}: `"One"`{.s}, `2`{.m}:
    `"Two"`{.s}, `3`{.m}: `"Three"`{.s}, `4`{.m}: `"Four"`{.s},
3.  `    5`{.code-voice}: `"Five"`{.s}, `6`{.m}: `"Six"`{.s}, `7`{.m}:
    `"Seven"`{.s}, `8`{.m}: `"Eight"`{.s}, `9`{.m}: `"Nine"`{.s}
4.  `]`{.code-voice}
5.  `let`{.code-voice} `numbers`{.vc} = \[`16`{.m}, `58`{.m},
    `510`{.m}\]

</div>

</div>

</div>

The code above creates a dictionary of mappings between the integer
digits and English-language versions of their names. It also defines an
array of integers, ready to be converted into strings.

You can now use the `numbers`{.code-voice} array to create an array of
`String`{.code-voice} values, by passing a closure expression to the
array’s `map(_:)`{.code-voice} method as a trailing closure:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `strings`{.vc} = `numbers`{.vc}.`map`{.vc} {
2.  `    (number`{.code-voice}) -&gt; `String`{.n} `in`{.kt}
3.  `    var`{.code-voice} `number`{.vc} = `number`{.vc}
4.  `    var`{.code-voice} `output`{.vc} = `""`{.s}
5.  `    while`{.code-voice} `number`{.vc} &gt; `0`{.m} {
6.  `        output`{.code-voice} = `digitNames`{.vc}\[`number`{.vc} %
    `10`{.m}\]! + `output`{.vc}
7.  `        number`{.code-voice} /= `10`{.m}
8.  `    }`{.code-voice}
9.  `    return`{.code-voice} `output`{.vc}
10. `}`{.code-voice}
11. `// strings is inferred to be of type [String]`{.code-voice}
12. `// its value is ["OneSix", "FiveEight", "FiveOneZero"]`{.code-voice}

</div>

</div>

</div>

The `map(_:)`{.code-voice} method calls the closure expression once for
each item in the array. You do not need to specify the type of the
closure’s input parameter, `number`{.code-voice}, because the type can
be inferred from the values in the array to be mapped.

In this example, the variable `number`{.code-voice} is initialized with
the value of the closure’s `number`{.code-voice} parameter, so that the
value can be modified within the closure body. (The parameters to
functions and closures are always constants.) The closure expression
also specifies a return type of `String`{.code-voice}, to indicate the
type that will be stored in the mapped output array.

The closure expression builds a string called `output`{.code-voice} each
time it is called. It calculates the last digit of `number`{.code-voice}
by using the remainder operator (`number % 10`{.code-voice}), and uses
this digit to look up an appropriate string in the
`digitNames`{.code-voice} dictionary. The closure can be used to create
a string representation of any integer number greater than zero.

<div class="note">

Note

The call to the `digitNames`{.code-voice} dictionary’s subscript is
followed by an exclamation mark (`!`{.code-voice}), because dictionary
subscripts return an optional value to indicate that the dictionary
lookup can fail if the key does not exist. In the example above, it is
guaranteed that `number % 10`{.code-voice} will always be a valid
subscript key for the `digitNames`{.code-voice} dictionary, and so an
exclamation mark is used to force-unwrap the `String`{.code-voice} value
stored in the subscript’s optional return value.

</div>

The string retrieved from the `digitNames`{.code-voice} dictionary is
added to the *front* of `output`{.code-voice}, effectively building a
string version of the number in reverse. (The expression
`number % 10`{.code-voice} gives a value of `6`{.code-voice} for
`16`{.code-voice}, `8`{.code-voice} for `58`{.code-voice}, and
`0`{.code-voice} for `510`{.code-voice}.)

The `number`{.code-voice} variable is then divided by `10`{.code-voice}.
Because it is an integer, it is rounded down during the division, so
`16`{.code-voice} becomes `1`{.code-voice}, `58`{.code-voice} becomes
`5`{.code-voice}, and `510`{.code-voice} becomes `51`{.code-voice}.

The process is repeated until `number`{.code-voice} is equal to
`0`{.code-voice}, at which point the `output`{.code-voice} string is
returned by the closure, and is added to the output array by the
`map(_:)`{.code-voice} method.

The use of trailing closure syntax in the example above neatly
encapsulates the closure’s functionality immediately after the function
that closure supports, without needing to wrap the entire closure within
the `map(_:)`{.code-voice} method’s outer parentheses.

</div>

<div class="section section">

[‌](){#TP40016643-CH11-ID103}
### Capturing Values {#capturing-values .section-name}

A closure can *capture* constants and variables from the surrounding
context in which it is defined. The closure can then refer to and modify
the values of those constants and variables from within its body, even
if the original scope that defined the constants and variables no longer
exists.

In Swift, the simplest form of a closure that can capture values is a
nested function, written within the body of another function. A nested
function can capture any of its outer function’s arguments and can also
capture any constants and variables defined within the outer function.

Here’s an example of a function called `makeIncrementer`{.code-voice},
which contains a nested function called `incrementer`{.code-voice}. The
nested `incrementer()`{.code-voice} function captures two values,
`runningTotal`{.code-voice} and `amount`{.code-voice}, from its
surrounding context. After capturing these values,
`incrementer`{.code-voice} is returned by `makeIncrementer`{.code-voice}
as a closure that increments `runningTotal`{.code-voice} by
`amount`{.code-voice} each time it is called.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `makeIncrementer`{.vc}(`forIncrement`{.vc}
    `amount`{.vc}: `Int`{.n}) -&gt; () -&gt; `Int`{.n} {
2.  `    var`{.code-voice} `runningTotal`{.vc} = `0`{.m}
3.  `    func`{.code-voice} `incrementer`{.vc}() -&gt; `Int`{.n} {
4.  `        runningTotal`{.code-voice} += `amount`{.vc}
5.  `        return`{.code-voice} `runningTotal`{.vc}
6.  `    }`{.code-voice}
7.  `    return`{.code-voice} `incrementer`{.vc}
8.  `}`{.code-voice}

</div>

</div>

</div>

The return type of `makeIncrementer`{.code-voice} is
`() -> Int`{.code-voice}. This means that it returns a *function*,
rather than a simple value. The function it returns has no parameters,
and returns an `Int`{.code-voice} value each time it is called. To learn
how functions can return other functions, see [Function Types as Return
Types](Functions.md#TP40016643-CH10-ID177).

The `makeIncrementer(forIncrement:)`{.code-voice} function defines an
integer variable called `runningTotal`{.code-voice}, to store the
current running total of the incrementer that will be returned. This
variable is initialized with a value of `0`{.code-voice}.

The `makeIncrementer(forIncrement:)`{.code-voice} function has a single
`Int`{.code-voice} parameter with an external name of
`forIncrement`{.code-voice}, and a local name of `amount`{.code-voice}.
The argument value passed to this parameter specifies how much
`runningTotal`{.code-voice} should be incremented by each time the
returned incrementer function is called. The
`makeIncrementer`{.code-voice} function defines a nested function called
`incrementer`{.code-voice}, which performs the actual incrementing. This
function simply adds `amount`{.code-voice} to
`runningTotal`{.code-voice}, and returns the result.

When considered in isolation, the nested `incrementer()`{.code-voice}
function might seem unusual:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `incrementer`{.vc}() -&gt; `Int`{.n} {
2.  `    runningTotal`{.code-voice} += `amount`{.vc}
3.  `    return`{.code-voice} `runningTotal`{.vc}
4.  `}`{.code-voice}

</div>

</div>

</div>

The `incrementer()`{.code-voice} function doesn’t have any parameters,
and yet it refers to `runningTotal`{.code-voice} and
`amount`{.code-voice} from within its function body. It does this by
capturing a *reference* to `runningTotal`{.code-voice} and
`amount`{.code-voice} from the surrounding function and using them
within its own function body. Capturing by reference ensures that
`runningTotal`{.code-voice} and `amount`{.code-voice} do not disappear
when the call to `makeIncrementer`{.code-voice} ends, and also ensures
that `runningTotal`{.code-voice} is available the next time the
`incrementer`{.code-voice} function is called.

<div class="note">

Note

As an optimization, Swift may instead capture and store a *copy* of a
value if that value is not mutated by a closure, and if the value is not
mutated after the closure is created.

Swift also handles all memory management involved in disposing of
variables when they are no longer needed.

</div>

Here’s an example of `makeIncrementer`{.code-voice} in action:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `incrementByTen`{.vc} =
    `makeIncrementer`{.vc}(`forIncrement`{.vc}: `10`{.m})

</div>

</div>

</div>

This example sets a constant called `incrementByTen`{.code-voice} to
refer to an incrementer function that adds `10`{.code-voice} to its
`runningTotal`{.code-voice} variable each time it is called. Calling the
function multiple times shows this behavior in action:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `incrementByTen`{.code-voice}()
2.  `// returns a value of 10`{.code-voice}
3.  `incrementByTen`{.code-voice}()
4.  `// returns a value of 20`{.code-voice}
5.  `incrementByTen`{.code-voice}()
6.  `// returns a value of 30`{.code-voice}

</div>

</div>

</div>

If you create a second incrementer, it will have its own stored
reference to a new, separate `runningTotal`{.code-voice} variable:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `incrementBySeven`{.vc} =
    `makeIncrementer`{.vc}(`forIncrement`{.vc}: `7`{.m})
2.  `incrementBySeven`{.code-voice}()
3.  `// returns a value of 7`{.code-voice}

</div>

</div>

</div>

Calling the original incrementer (`incrementByTen`{.code-voice}) again
continues to increment its own `runningTotal`{.code-voice} variable, and
does not affect the variable captured by
`incrementBySeven`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `incrementByTen`{.code-voice}()
2.  `// returns a value of 40`{.code-voice}

</div>

</div>

</div>

<div class="note">

Note

If you assign a closure to a property of a class instance, and the
closure captures that instance by referring to the instance or its
members, you will create a strong reference cycle between the closure
and the instance. Swift uses *capture lists* to break these strong
reference cycles. For more information, see [Strong Reference Cycles for
Closures](AutomaticReferenceCounting.md#TP40016643-CH20-ID56).

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH11-ID104}
### Closures Are Reference Types {#closures-are-reference-types .section-name}

In the example above, `incrementBySeven`{.code-voice} and
`incrementByTen`{.code-voice} are constants, but the closures these
constants refer to are still able to increment the
`runningTotal`{.code-voice} variables that they have captured. This is
because functions and closures are *reference types*.

Whenever you assign a function or a closure to a constant or a variable,
you are actually setting that constant or variable to be a *reference*
to the function or closure. In the example above, it is the choice of
closure that `incrementByTen`{.code-voice} *refers to* that is constant,
and not the contents of the closure itself.

This also means that if you assign a closure to two different constants
or variables, both of those constants or variables will refer to the
same closure:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `alsoIncrementByTen`{.vc} = `incrementByTen`{.vc}
2.  `alsoIncrementByTen`{.code-voice}()
3.  `// returns a value of 50`{.code-voice}

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH11-ID546}
### Nonescaping Closures {#nonescaping-closures .section-name}

A closure is said to *escape* a function when the closure is passed as
an argument to the function, but is called after the function returns.
When you declare a function that takes a closure as one of its
parameters, you can write `@noescape`{.code-voice} before the parameter
name to indicate that the closure is not allowed to escape. Marking a
closure with `@noescape`{.code-voice} lets the compiler make more
aggressive optimizations because it knows more information about the
closure’s lifespan.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice}
    `someFunctionWithNoescapeClosure`{.vc}(`@noescape`{.kt}
    `closure`{.vc}: () -&gt; `Void`{.n}) {
2.  `    closure`{.code-voice}()
3.  `}`{.code-voice}

</div>

</div>

</div>

As an example, the `sort(_:)`{.code-voice} method takes a closure as its
parameter, which is used to compare elements. The parameter is marked
`@noescape`{.code-voice} because it is guaranteed not to be needed after
sorting is complete.

One way that a closure can escape is by being stored in a variable that
is defined outside the function. As an example, many functions that
start an asynchronous operation take a closure argument as a completion
handler. The function returns after it starts the operation, but the
closure isn’t called until the operation is completed—the closure needs
to escape, to be called later. For example:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `completionHandlers`{.vc}: \[() -&gt;
    `Void`{.n}\] = \[\]
2.  `func`{.code-voice}
    `someFunctionWithEscapingClosure`{.vc}(`completionHandler`{.vc}: ()
    -&gt; `Void`{.n}) {
3.  `    completionHandlers`{.code-voice}.`append`{.vc}(`completionHandler`{.vc})
4.  `}`{.code-voice}

</div>

</div>

</div>

The `someFunctionWithEscapingClosure(_:)`{.code-voice} function takes a
closure as its argument and adds it to an array that’s declared outside
the function. If you tried to mark the parameter of this function with
`@noescape`{.code-voice}, you would get a compiler error.

Marking a closure with `@noescape`{.code-voice} lets you refer to
`self`{.code-voice} implicitly within the closure.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `class`{.code-voice} `SomeClass`{.vc} {
2.  `    var`{.code-voice} `x`{.vc} = `10`{.m}
3.  `    func`{.code-voice} `doSomething`{.vc}() {
4.  `        someFunctionWithEscapingClosure`{.code-voice} {
    `self`{.kt}.`x`{.vc} = `100`{.m} }
5.  `        someFunctionWithNoescapeClosure`{.code-voice} { `x`{.vc} =
    `200`{.m} }
6.  `    }`{.code-voice}
7.  `}`{.code-voice}
8.  ` `{.code-voice}
9.  `let`{.code-voice} `instance`{.vc} = `SomeClass`{.vc}()
10. `instance`{.code-voice}.`doSomething`{.vc}()
11. `print`{.code-voice}(`instance`{.vc}.`x`{.vc})
12. `// prints "200"`{.code-voice}
13. ` `{.code-voice}
14. `completionHandlers`{.code-voice}.`first`{.vc}?()
15. `print`{.code-voice}(`instance`{.vc}.`x`{.vc})
16. `// prints "100"`{.code-voice}

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH11-ID543}
### Autoclosures {#autoclosures .section-name}

An *autoclosure* is a closure that is automatically created to wrap an
expression that’s being passed as an argument to a function. It doesn’t
take any arguments, and when it’s called, it returns the value of the
expression that’s wrapped inside of it. This syntactic convenience lets
you omit braces around a function’s parameter by writing a normal
expression instead of an explicit closure.

It’s common to *call* functions that take autoclosures, but it’s not
common to *implement* that kind of function. For example, the
`assert(condition:message:file:line:)`{.code-voice} function takes an
autoclosure for its `condition`{.code-voice} and `message`{.code-voice}
parameters; its `condition`{.code-voice} parameter is evaluated only in
debug builds and its `message`{.code-voice} parameter is evaluated only
if `condition`{.code-voice} is `false`{.code-voice}.

An autoclosure lets you delay evaluation, because the code inside isn’t
run until you call the closure. Delaying evaluation is useful for code
that has side effects or is computationally expensive, because it lets
you control when that code is evaluated. The code below shows how a
closure delays evaluation.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `customersInLine`{.vc} = \[`"Chris"`{.s},
    `"Alex"`{.s}, `"Ewa"`{.s}, `"Barry"`{.s}, `"Daniella"`{.s}\]
2.  `print`{.code-voice}(`customersInLine`{.vc}.`count`{.vc})
3.  `// prints "5"`{.code-voice}
4.  ` `{.code-voice}
5.  `let`{.code-voice} `customerProvider`{.vc} = {
    `customersInLine`{.vc}.`removeAtIndex`{.vc}(`0`{.m}) }
6.  `print`{.code-voice}(`customersInLine`{.vc}.`count`{.vc})
7.  `// prints "5"`{.code-voice}
8.  ` `{.code-voice}
9.  `print`{.code-voice}(`"Now serving `{.s}\\(`customerProvider`{.vc}())`!"`{.s})
10. `// prints "Now serving Chris!"`{.code-voice}
11. `print`{.code-voice}(`customersInLine`{.vc}.`count`{.vc})
12. `// prints "4"`{.code-voice}

</div>

</div>

</div>

Even though the first element of the `customersInLine`{.code-voice}
array is removed by the code inside the closure, the array element isn’t
removed until the closure is actually called. If the closure is never
called, the expression inside the closure is never evaluated, which
means the array element is never removed. Note that the type of
`customerProvider`{.code-voice} is not `String`{.code-voice} but
`() -> String`{.code-voice}—a function with no parameters that returns a
string.

You get the same behavior of delayed evaluation when you pass a closure
as an argument to a function.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `// customersInLine is ["Alex", "Ewa", "Barry", "Daniella"]`{.code-voice}
2.  `func`{.code-voice} `serveCustomer`{.vc}(`customerProvider`{.vc}: ()
    -&gt; `String`{.n}) {
3.  `    print`{.code-voice}(`"Now serving `{.s}\\(`customerProvider`{.vc}())`!"`{.s})
4.  `}`{.code-voice}
5.  `serveCustomer`{.code-voice}( {
    `customersInLine`{.vc}.`removeAtIndex`{.vc}(`0`{.m}) } )
6.  `// prints "Now serving Alex!"`{.code-voice}

</div>

</div>

</div>

The `serveCustomer(_:)`{.code-voice} function in the listing above takes
an explicit closure that returns a customer’s name. The version of
`serveCustomer(_:)`{.code-voice} below performs the same operation but,
instead of taking an explicit closure, it takes an autoclosure by
marking its parameter with the `@autoclosure`{.code-voice} attribute.
Now you can call the function as if it took a `String`{.code-voice}
argument instead of a closure. The argument is automatically converted
to a closure, because the `customerProvider`{.code-voice} parameter is
marked with the `@autoclosure`{.code-voice} attribute.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `// customersInLine is ["Ewa", "Barry", "Daniella"]`{.code-voice}
2.  `func`{.code-voice} `serveCustomer`{.vc}(`@autoclosure`{.kt}
    `customerProvider`{.vc}: () -&gt; `String`{.n}) {
3.  `    print`{.code-voice}(`"Now serving `{.s}\\(`customerProvider`{.vc}())`!"`{.s})
4.  `}`{.code-voice}
5.  `serveCustomer`{.code-voice}(`customersInLine`{.vc}.`removeAtIndex`{.vc}(`0`{.m}))
6.  `// prints "Now serving Ewa!"`{.code-voice}

</div>

</div>

</div>

<div class="note">

Note

Overusing autoclosures can make your code hard to understand. The
context and function name should make it clear that evaluation is being
deferred.

</div>

The `@autoclosure`{.code-voice} attribute implies the
`@noescape`{.code-voice} attribute, which is described above in
[Nonescaping Closures](Closures.md#TP40016643-CH11-ID546). If you
want an autoclosure that is allowed to escape, use the
`@autoclosure(escaping)`{.code-voice} form of the attribute.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `// customersInLine is ["Barry", "Daniella"]`{.code-voice}
2.  `var`{.code-voice} `customerProviders`{.vc}: \[() -&gt;
    `String`{.n}\] = \[\]
3.  `func`{.code-voice}
    `collectCustomerProviders`{.vc}(`@autoclosure(escaping)`{.kt}
    `customerProvider`{.vc}: () -&gt; `String`{.n}) {
4.  `    customerProviders`{.code-voice}.`append`{.vc}(`customerProvider`{.vc})
5.  `}`{.code-voice}
6.  `collectCustomerProviders`{.code-voice}(`customersInLine`{.vc}.`removeAtIndex`{.vc}(`0`{.m}))
7.  `collectCustomerProviders`{.code-voice}(`customersInLine`{.vc}.`removeAtIndex`{.vc}(`0`{.m}))
8.  ` `{.code-voice}
9.  `print`{.code-voice}(`"Collected `{.s}\\(`customerProviders`{.vc}.`count`{.vc})` closures."`{.s})
10. `// prints "Collected 2 closures."`{.code-voice}
11. `for`{.code-voice} `customerProvider`{.vc} `in`{.kt}
    `customerProviders`{.vc} {
12. `    print`{.code-voice}(`"Now serving `{.s}\\(`customerProvider`{.vc}())`!"`{.s})
13. `}`{.code-voice}
14. `// prints "Now serving Barry!"`{.code-voice}
15. `// prints "Now serving Daniella!"`{.code-voice}

</div>

</div>

</div>

In the code above, instead of calling the closure passed to it as its
`customer`{.code-voice} argument, the
`collectCustomerProviders(_:)`{.code-voice} function appends the closure
to the `customerProviders`{.code-voice} array. The array is declared
outside the scope of the function, which means the closures in the array
can be executed after the function returns. As a result, the value of
the `customer`{.code-voice} argument must be allowed to escape the
function’s scope.

</div>

</div>

</div>
