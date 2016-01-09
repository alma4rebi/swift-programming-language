<div class="content-wrapper">

<div id="chapter_container" class="conceptualwithtasks">

[‌](){#TP40016643-CH2}[‌](){#TP40016643-CH2-ID1}
A Swift Tour {#a-swift-tour .chapter-name}
------------

<div class="section section">

Tradition suggests that the first program in a new language should print
the words “Hello, world!” on the screen. In Swift, this can be done in a
single line:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `print`{.code-voice}(`"Hello, world!"`{.s})

</div>

</div>

</div>

If you have written code in C or Objective-C, this syntax looks familiar
to you—in Swift, this line of code is a complete program. You don’t need
to import a separate library for functionality like input/output or
string handling. Code written at global scope is used as the entry point
for the program, so you don’t need a `main()`{.code-voice} function. You
also don’t need to write semicolons at the end of every statement.

This tour gives you enough information to start writing code in Swift by
showing you how to accomplish a variety of programming tasks. Don’t
worry if you don’t understand something—everything introduced in this
tour is explained in detail in the rest of this book.

</div>

<div class="section section">

<div class="note playground">

Note

On a Mac, download the Playground and double-click the file to open it
in Xcode: <https://developer.apple.com/go/?id=swift-tour>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH2-ID461}
### Simple Values {#simple-values .section-name}

Use `let`{.code-voice} to make a constant and `var`{.code-voice} to make
a variable. The value of a constant doesn’t need to be known at compile
time, but you must assign it a value exactly once. This means you can
use constants to name a value that you determine once but use in many
places.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `myVariable`{.vc} = `42`{.m}
2.  `myVariable`{.code-voice} = `50`{.m}
3.  `let`{.code-voice} `myConstant`{.vc} = `42`{.m}

</div>

</div>

</div>

A constant or variable must have the same type as the value you want to
assign to it. However, you don’t always have to write the type
explicitly. Providing a value when you create a constant or variable
lets the compiler infer its type. In the example above, the compiler
infers that `myVariable`{.code-voice} is an integer because its initial
value is an integer.

If the initial value doesn’t provide enough information (or if there is
no initial value), specify the type by writing it after the variable,
separated by a colon.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `implicitInteger`{.vc} = `70`{.m}
2.  `let`{.code-voice} `implicitDouble`{.vc} = `70.0`{.m}
3.  `let`{.code-voice} `explicitDouble`{.vc}: `Double`{.n} = `70`{.m}

</div>

</div>

</div>

<div class="note">

Experiment

Create a constant with an explicit type of `Float`{.code-voice} and a
value of `4`{.code-voice}.

</div>

Values are never implicitly converted to another type. If you need to
convert a value to a different type, explicitly make an instance of the
desired type.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `label`{.vc} = `"The width is "`{.s}
2.  `let`{.code-voice} `width`{.vc} = `94`{.m}
3.  `let`{.code-voice} `widthLabel`{.vc} = `label`{.vc} +
    `String`{.vc}(`width`{.vc})

</div>

</div>

</div>

<div class="note">

Experiment

Try removing the conversion to `String`{.code-voice} from the last line.
What error do you get?

</div>

There’s an even simpler way to include values in strings: Write the
value in parentheses, and write a backslash (`\`{.code-voice}) before
the parentheses. For example:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `apples`{.vc} = `3`{.m}
2.  `let`{.code-voice} `oranges`{.vc} = `5`{.m}
3.  `let`{.code-voice} `appleSummary`{.vc} =
    `"I have `{.s}\\(`apples`{.vc})` apples."`{.s}
4.  `let`{.code-voice} `fruitSummary`{.vc} =
    `"I have `{.s}\\(`apples`{.vc} +
    `oranges`{.vc})` pieces of fruit."`{.s}

</div>

</div>

</div>

<div class="note">

Experiment

Use `\()`{.code-voice} to include a floating-point calculation in a
string and to include someone’s name in a greeting.

</div>

Create arrays and dictionaries using brackets (`[]`{.code-voice}), and
access their elements by writing the index or key in brackets. A comma
is allowed after the last element.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `shoppingList`{.vc} = \[`"catfish"`{.s},
    `"water"`{.s}, `"tulips"`{.s}, `"blue paint"`{.s}\]
2.  `shoppingList`{.code-voice}\[`1`{.m}\] = `"bottle of water"`{.s}
3.  ` `{.code-voice}
4.  `var`{.code-voice} `occupations`{.vc} = \[
5.  `    "Malcolm"`{.code-voice}: `"Captain"`{.s},
6.  `    "Kaylee"`{.code-voice}: `"Mechanic"`{.s},
7.  `]`{.code-voice}
8.  `occupations`{.code-voice}\[`"Jayne"`{.s}\] =
    `"Public Relations"`{.s}

</div>

</div>

</div>

To create an empty array or dictionary, use the initializer syntax.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `emptyArray`{.vc} = \[`String`{.vc}\]()
2.  `let`{.code-voice} `emptyDictionary`{.vc} = \[`String`{.vc}:
    `Float`{.vc}\]()

</div>

</div>

</div>

If type information can be inferred, you can write an empty array as
`[]`{.code-voice} and an empty dictionary as `[:]`{.code-voice}—for
example, when you set a new value for a variable or pass an argument to
a function.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `shoppingList`{.code-voice} = \[\]
2.  `occupations`{.code-voice} = \[:\]

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH2-ID462}
### Control Flow {#control-flow .section-name}

Use `if`{.code-voice} and `switch`{.code-voice} to make conditionals,
and use `for`{.code-voice}-`in`{.code-voice}, `for`{.code-voice},
`while`{.code-voice}, and `repeat`{.code-voice}-`while`{.code-voice} to
make loops. Parentheses around the condition or loop variable are
optional. Braces around the body are required.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `individualScores`{.vc} = \[`75`{.m}, `43`{.m},
    `103`{.m}, `87`{.m}, `12`{.m}\]
2.  `var`{.code-voice} `teamScore`{.vc} = `0`{.m}
3.  `for`{.code-voice} `score`{.vc} `in`{.kt} `individualScores`{.vc} {
4.  `    if`{.code-voice} `score`{.vc} &gt; `50`{.m} {
5.  `        teamScore`{.code-voice} += `3`{.m}
6.  `    } else`{.code-voice} {
7.  `        teamScore`{.code-voice} += `1`{.m}
8.  `    }`{.code-voice}
9.  `}`{.code-voice}
10. `print`{.code-voice}(`teamScore`{.vc})

</div>

</div>

</div>

In an `if`{.code-voice} statement, the conditional must be a Boolean
expression—this means that code such as `if score { ... }`{.code-voice}
is an error, not an implicit comparison to zero.

You can use `if`{.code-voice} and `let`{.code-voice} together to work
with values that might be missing. These values are represented as
optionals. An optional value either contains a value or contains
`nil`{.code-voice} to indicate that a value is missing. Write a question
mark (`?`{.code-voice}) after the type of a value to mark the value as
optional.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `optionalString`{.vc}: `String`{.n}? =
    `"Hello"`{.s}
2.  `print`{.code-voice}(`optionalString`{.vc} == `nil`{.kt})
3.  ` `{.code-voice}
4.  `var`{.code-voice} `optionalName`{.vc}: `String`{.n}? =
    `"John Appleseed"`{.s}
5.  `var`{.code-voice} `greeting`{.vc} = `"Hello!"`{.s}
6.  `if`{.code-voice} `let`{.kt} `name`{.vc} = `optionalName`{.vc} {
7.  `    greeting`{.code-voice} = `"Hello, `{.s}\\(`name`{.vc})`"`{.s}
8.  `}`{.code-voice}

</div>

</div>

</div>

<div class="note">

Experiment

Change `optionalName`{.code-voice} to `nil`{.code-voice}. What greeting
do you get? Add an `else`{.code-voice} clause that sets a different
greeting if `optionalName`{.code-voice} is `nil`{.code-voice}.

</div>

If the optional value is `nil`{.code-voice}, the conditional is
`false`{.code-voice} and the code in braces is skipped. Otherwise, the
optional value is unwrapped and assigned to the constant after
`let`{.code-voice}, which makes the unwrapped value available inside the
block of code.

Another way to handle optional values is to provide a default value
using the `??`{.code-voice} operator. If the optional value is missing,
the default value is used instead.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `nickName`{.vc}: `String`{.n}? = `nil`{.kt}
2.  `let`{.code-voice} `fullName`{.vc}: `String`{.n} =
    `"John Appleseed"`{.s}
3.  `let`{.code-voice} `informalGreeting`{.vc} =
    `"Hi `{.s}\\(`nickName`{.vc} ?? `fullName`{.vc})`"`{.s}

</div>

</div>

</div>

Switches support any kind of data and a wide variety of comparison
operations—they aren’t limited to integers and tests for equality.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `vegetable`{.vc} = `"red pepper"`{.s}
2.  `switch`{.code-voice} `vegetable`{.vc} {
3.  `case`{.code-voice} `"celery"`{.s}:
4.  `    print`{.code-voice}(`"Add some raisins and make ants on a log."`{.s})
5.  `case`{.code-voice} `"cucumber"`{.s}, `"watercress"`{.s}:
6.  `    print`{.code-voice}(`"That would make a good tea sandwich."`{.s})
7.  `case`{.code-voice} `let`{.kt} `x`{.vc} `where`{.kt}
    `x`{.vc}.`hasSuffix`{.vc}(`"pepper"`{.s}):
8.  `    print`{.code-voice}(`"Is it a spicy `{.s}\\(`x`{.vc})`?"`{.s})
9.  `default`{.code-voice}:
10. `    print`{.code-voice}(`"Everything tastes good in soup."`{.s})
11. `}`{.code-voice}

</div>

</div>

</div>

<div class="note">

Experiment

Try removing the default case. What error do you get?

</div>

Notice how `let`{.code-voice} can be used in a pattern to assign the
value that matched that part of a pattern to a constant.

After executing the code inside the switch case that matched, the
program exits from the switch statement. Execution doesn’t continue to
the next case, so there is no need to explicitly break out of the switch
at the end of each case’s code.

You use `for`{.code-voice}-`in`{.code-voice} to iterate over items in a
dictionary by providing a pair of names to use for each key-value pair.
Dictionaries are an unordered collection, so their keys and values are
iterated over in an arbitrary order.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `interestingNumbers`{.vc} = \[
2.  `    "Prime"`{.code-voice}: \[`2`{.m}, `3`{.m}, `5`{.m}, `7`{.m},
    `11`{.m}, `13`{.m}\],
3.  `    "Fibonacci"`{.code-voice}: \[`1`{.m}, `1`{.m}, `2`{.m},
    `3`{.m}, `5`{.m}, `8`{.m}\],
4.  `    "Square"`{.code-voice}: \[`1`{.m}, `4`{.m}, `9`{.m}, `16`{.m},
    `25`{.m}\],
5.  `]`{.code-voice}
6.  `var`{.code-voice} `largest`{.vc} = `0`{.m}
7.  `for`{.code-voice} (`kind`{.vc}, `numbers`{.vc}) `in`{.kt}
    `interestingNumbers`{.vc} {
8.  `    for`{.code-voice} `number`{.vc} `in`{.kt} `numbers`{.vc} {
9.  `        if`{.code-voice} `number`{.vc} &gt; `largest`{.vc} {
10. `            largest`{.code-voice} = `number`{.vc}
11. `        }`{.code-voice}
12. `    }`{.code-voice}
13. `}`{.code-voice}
14. `print`{.code-voice}(`largest`{.vc})

</div>

</div>

</div>

<div class="note">

Experiment

Add another variable to keep track of which kind of number was the
largest, as well as what that largest number was.

</div>

Use `while`{.code-voice} to repeat a block of code until a condition
changes. The condition of a loop can be at the end instead, ensuring
that the loop is run at least once.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `n`{.vc} = `2`{.m}
2.  `while`{.code-voice} `n`{.vc} &lt; `100`{.m} {
3.  `    n`{.code-voice} = `n`{.vc} \* `2`{.m}
4.  `}`{.code-voice}
5.  `print`{.code-voice}(`n`{.vc})
6.  ` `{.code-voice}
7.  `var`{.code-voice} `m`{.vc} = `2`{.m}
8.  `repeat`{.code-voice} {
9.  `    m`{.code-voice} = `m`{.vc} \* `2`{.m}
10. `} while`{.code-voice} `m`{.vc} &lt; `100`{.m}
11. `print`{.code-voice}(`m`{.vc})

</div>

</div>

</div>

You can keep an index in a loop—either by using `..<`{.code-voice} to
make a range of indexes or by writing an explicit initialization,
condition, and increment. These two loops do the same thing:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `firstForLoop`{.vc} = `0`{.m}
2.  `for`{.code-voice} `i`{.vc} `in`{.kt} `0`{.m}..&lt;`4`{.m} {
3.  `    firstForLoop`{.code-voice} += `i`{.vc}
4.  `}`{.code-voice}
5.  `print`{.code-voice}(`firstForLoop`{.vc})
6.  ` `{.code-voice}
7.  `var`{.code-voice} `secondForLoop`{.vc} = `0`{.m}
8.  `for`{.code-voice} `var`{.kt} `i`{.vc} = `0`{.m}; `i`{.vc} &lt;
    `4`{.m}; ++`i`{.vc} {
9.  `    secondForLoop`{.code-voice} += `i`{.vc}
10. `}`{.code-voice}
11. `print`{.code-voice}(`secondForLoop`{.vc})

</div>

</div>

</div>

Use `..<`{.code-voice} to make a range that omits its upper value, and
use `...`{.code-voice} to make a range that includes both values.

</div>

<div class="section section">

[‌](){#TP40016643-CH2-ID463}
### Functions and Closures {#functions-and-closures .section-name}

Use `func`{.code-voice} to declare a function. Call a function by
following its name with a list of arguments in parentheses. Use
`->`{.code-voice} to separate the parameter names and types from the
function’s return type.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `greet`{.vc}(`name`{.vc}: `String`{.n},
    `day`{.vc}: `String`{.n}) -&gt; `String`{.n} {
2.  `    return`{.code-voice}
    `"Hello `{.s}\\(`name`{.vc})`, today is `{.s}\\(`day`{.vc})`."`{.s}
3.  `}`{.code-voice}
4.  `greet`{.code-voice}(`"Bob"`{.s}, `day`{.vc}: `"Tuesday"`{.s})

</div>

</div>

</div>

<div class="note">

Experiment

Remove the `day`{.code-voice} parameter. Add a parameter to include
today’s lunch special in the greeting.

</div>

Use a tuple to make a compound value—for example, to return multiple
values from a function. The elements of a tuple can be referred to
either by name or by number.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `calculateStatistics`{.vc}(`scores`{.vc}:
    \[`Int`{.n}\]) -&gt; (`min`{.vc}: `Int`{.n}, `max`{.vc}: `Int`{.n},
    `sum`{.vc}: `Int`{.n}) {
2.  `    var`{.code-voice} `min`{.vc} = `scores`{.vc}\[`0`{.m}\]
3.  `    var`{.code-voice} `max`{.vc} = `scores`{.vc}\[`0`{.m}\]
4.  `    var`{.code-voice} `sum`{.vc} = `0`{.m}
5.  `    `{.code-voice}
6.  `    for`{.code-voice} `score`{.vc} `in`{.kt} `scores`{.vc} {
7.  `        if`{.code-voice} `score`{.vc} &gt; `max`{.vc} {
8.  `            max`{.code-voice} = `score`{.vc}
9.  `        } else`{.code-voice} `if`{.kt} `score`{.vc} &lt; `min`{.vc}
    {
10. `            min`{.code-voice} = `score`{.vc}
11. `        }`{.code-voice}
12. `        sum`{.code-voice} += `score`{.vc}
13. `    }`{.code-voice}
14. `    `{.code-voice}
15. `    return`{.code-voice} (`min`{.vc}, `max`{.vc}, `sum`{.vc})
16. `}`{.code-voice}
17. `let`{.code-voice} `statistics`{.vc} =
    `calculateStatistics`{.vc}(\[`5`{.m}, `3`{.m}, `100`{.m}, `3`{.m},
    `9`{.m}\])
18. `print`{.code-voice}(`statistics`{.vc}.`sum`{.vc})
19. `print`{.code-voice}(`statistics`{.vc}.`2`{.m})

</div>

</div>

</div>

Functions can also take a variable number of arguments, collecting them
into an array.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `sumOf`{.vc}(`numbers`{.vc}: `Int`{.n}...) -&gt;
    `Int`{.n} {
2.  `    var`{.code-voice} `sum`{.vc} = `0`{.m}
3.  `    for`{.code-voice} `number`{.vc} `in`{.kt} `numbers`{.vc} {
4.  `        sum`{.code-voice} += `number`{.vc}
5.  `    }`{.code-voice}
6.  `    return`{.code-voice} `sum`{.vc}
7.  `}`{.code-voice}
8.  `sumOf`{.code-voice}()
9.  `sumOf`{.code-voice}(`42`{.m}, `597`{.m}, `12`{.m})

</div>

</div>

</div>

<div class="note">

Experiment

Write a function that calculates the average of its arguments.

</div>

Functions can be nested. Nested functions have access to variables that
were declared in the outer function. You can use nested functions to
organize the code in a function that is long or complex.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `returnFifteen`{.vc}() -&gt; `Int`{.n} {
2.  `    var`{.code-voice} `y`{.vc} = `10`{.m}
3.  `    func`{.code-voice} `add`{.vc}() {
4.  `        y`{.code-voice} += `5`{.m}
5.  `    }`{.code-voice}
6.  `    add`{.code-voice}()
7.  `    return`{.code-voice} `y`{.vc}
8.  `}`{.code-voice}
9.  `returnFifteen`{.code-voice}()

</div>

</div>

</div>

Functions are a first-class type. This means that a function can return
another function as its value.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `makeIncrementer`{.vc}() -&gt; ((`Int`{.n})
    -&gt; `Int`{.n}) {
2.  `    func`{.code-voice} `addOne`{.vc}(`number`{.vc}: `Int`{.n})
    -&gt; `Int`{.n} {
3.  `        return`{.code-voice} `1`{.m} + `number`{.vc}
4.  `    }`{.code-voice}
5.  `    return`{.code-voice} `addOne`{.vc}
6.  `}`{.code-voice}
7.  `var`{.code-voice} `increment`{.vc} = `makeIncrementer`{.vc}()
8.  `increment`{.code-voice}(`7`{.m})

</div>

</div>

</div>

A function can take another function as one of its arguments.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `hasAnyMatches`{.vc}(`list`{.vc}: \[`Int`{.n}\],
    `condition`{.vc}: (`Int`{.n}) -&gt; `Bool`{.n}) -&gt; `Bool`{.n} {
2.  `    for`{.code-voice} `item`{.vc} `in`{.kt} `list`{.vc} {
3.  `        if`{.code-voice} `condition`{.vc}(`item`{.vc}) {
4.  `            return`{.code-voice} `true`{.kt}
5.  `        }`{.code-voice}
6.  `    }`{.code-voice}
7.  `    return`{.code-voice} `false`{.kt}
8.  `}`{.code-voice}
9.  `func`{.code-voice} `lessThanTen`{.vc}(`number`{.vc}: `Int`{.n})
    -&gt; `Bool`{.n} {
10. `    return`{.code-voice} `number`{.vc} &lt; `10`{.m}
11. `}`{.code-voice}
12. `var`{.code-voice} `numbers`{.vc} = \[`20`{.m}, `19`{.m}, `7`{.m},
    `12`{.m}\]
13. `hasAnyMatches`{.code-voice}(`numbers`{.vc}, `condition`{.vc}:
    `lessThanTen`{.vc})

</div>

</div>

</div>

Functions are actually a special case of closures: blocks of code that
can be called later. The code in a closure has access to things like
variables and functions that were available in the scope where the
closure was created, even if the closure is in a different scope when it
is executed—you saw an example of this already with nested functions.
You can write a closure without a name by surrounding code with braces
(`{}`{.code-voice}). Use `in`{.code-voice} to separate the arguments and
return type from the body.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `numbers`{.code-voice}.`map`{.vc}({
2.  `    (number`{.code-voice}: `Int`{.n}) -&gt; `Int`{.n} `in`{.kt}
3.  `    let`{.code-voice} `result`{.vc} = `3`{.m} \* `number`{.vc}
4.  `    return`{.code-voice} `result`{.vc}
5.  `})`{.code-voice}

</div>

</div>

</div>

<div class="note">

Experiment

Rewrite the closure to return zero for all odd numbers.

</div>

You have several options for writing closures more concisely. When a
closure’s type is already known, such as the callback for a delegate,
you can omit the type of its parameters, its return type, or both.
Single statement closures implicitly return the value of their only
statement.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `mappedNumbers`{.vc} =
    `numbers`{.vc}.`map`{.vc}({ `number`{.vc} `in`{.kt} `3`{.m} \*
    `number`{.vc} })
2.  `print`{.code-voice}(`mappedNumbers`{.vc})

</div>

</div>

</div>

You can refer to parameters by number instead of by name—this approach
is especially useful in very short closures. A closure passed as the
last argument to a function can appear immediately after the
parentheses. When a closure is the only argument to a function, you can
omit the parentheses entirely.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `sortedNumbers`{.vc} = `numbers`{.vc}.`sort`{.vc}
    { `$0`{.vc} &gt; `$1`{.vc} }
2.  `print`{.code-voice}(`sortedNumbers`{.vc})

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH2-ID464}
### Objects and Classes {#objects-and-classes .section-name}

Use `class`{.code-voice} followed by the class’s name to create a class.
A property declaration in a class is written the same way as a constant
or variable declaration, except that it is in the context of a class.
Likewise, method and function declarations are written the same way.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `class`{.code-voice} `Shape`{.vc} {
2.  `    var`{.code-voice} `numberOfSides`{.vc} = `0`{.m}
3.  `    func`{.code-voice} `simpleDescription`{.vc}() -&gt;
    `String`{.n} {
4.  `        return`{.code-voice}
    `"A shape with `{.s}\\(`numberOfSides`{.vc})` sides."`{.s}
5.  `    }`{.code-voice}
6.  `}`{.code-voice}

</div>

</div>

</div>

<div class="note">

Experiment

Add a constant property with `let`{.code-voice}, and add another method
that takes an argument.

</div>

Create an instance of a class by putting parentheses after the class
name. Use dot syntax to access the properties and methods of the
instance.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `shape`{.vc} = `Shape`{.vc}()
2.  `shape`{.code-voice}.`numberOfSides`{.vc} = `7`{.m}
3.  `var`{.code-voice} `shapeDescription`{.vc} =
    `shape`{.vc}.`simpleDescription`{.vc}()

</div>

</div>

</div>

This version of the `Shape`{.code-voice} class is missing something
important: an initializer to set up the class when an instance is
created. Use `init`{.code-voice} to create one.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `class`{.code-voice} `NamedShape`{.vc} {
2.  `    var`{.code-voice} `numberOfSides`{.vc}: `Int`{.n} = `0`{.m}
3.  `    var`{.code-voice} `name`{.vc}: `String`{.n}
4.  `    `{.code-voice}
5.  `    init`{.code-voice}(`name`{.vc}: `String`{.n}) {
6.  `        self`{.code-voice}.`name`{.vc} = `name`{.vc}
7.  `    }`{.code-voice}
8.  `    `{.code-voice}
9.  `    func`{.code-voice} `simpleDescription`{.vc}() -&gt;
    `String`{.n} {
10. `        return`{.code-voice}
    `"A shape with `{.s}\\(`numberOfSides`{.vc})` sides."`{.s}
11. `    }`{.code-voice}
12. `}`{.code-voice}

</div>

</div>

</div>

Notice how `self`{.code-voice} is used to distinguish the
`name`{.code-voice} property from the `name`{.code-voice} argument to
the initializer. The arguments to the initializer are passed like a
function call when you create an instance of the class. Every property
needs a value assigned—either in its declaration (as with
`numberOfSides`{.code-voice}) or in the initializer (as with
`name`{.code-voice}).

Use `deinit`{.code-voice} to create a deinitializer if you need to
perform some cleanup before the object is deallocated.

Subclasses include their superclass name after their class name,
separated by a colon. There is no requirement for classes to subclass
any standard root class, so you can include or omit a superclass as
needed.

Methods on a subclass that override the superclass’s implementation are
marked with `override`{.code-voice}—overriding a method by accident,
without `override`{.code-voice}, is detected by the compiler as an
error. The compiler also detects methods with `override`{.code-voice}
that don’t actually override any method in the superclass.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `class`{.code-voice} `Square`{.vc}: `NamedShape`{.n} {
2.  `    var`{.code-voice} `sideLength`{.vc}: `Double`{.n}
3.  `    `{.code-voice}
4.  `    init`{.code-voice}(`sideLength`{.vc}: `Double`{.n},
    `name`{.vc}: `String`{.n}) {
5.  `        self`{.code-voice}.`sideLength`{.vc} = `sideLength`{.vc}
6.  `        super`{.code-voice}.`init`{.kt}(`name`{.vc}: `name`{.vc})
7.  `        numberOfSides`{.code-voice} = `4`{.m}
8.  `    }`{.code-voice}
9.  `    `{.code-voice}
10. `    func`{.code-voice} `area`{.vc}() -&gt; `Double`{.n} {
11. `        return`{.code-voice} `sideLength`{.vc} \* `sideLength`{.vc}
12. `    }`{.code-voice}
13. `    `{.code-voice}
14. `    override`{.code-voice} `func`{.kt} `simpleDescription`{.vc}()
    -&gt; `String`{.n} {
15. `        return`{.code-voice}
    `"A square with sides of length `{.s}\\(`sideLength`{.vc})`."`{.s}
16. `    }`{.code-voice}
17. `}`{.code-voice}
18. `let`{.code-voice} `test`{.vc} = `Square`{.vc}(`sideLength`{.vc}:
    `5.2`{.m}, `name`{.vc}: `"my test square"`{.s})
19. `test`{.code-voice}.`area`{.vc}()
20. `test`{.code-voice}.`simpleDescription`{.vc}()

</div>

</div>

</div>

<div class="note">

Experiment

Make another subclass of `NamedShape`{.code-voice} called
`Circle`{.code-voice} that takes a radius and a name as arguments to its
initializer. Implement an `area()`{.code-voice} and a
`simpleDescription()`{.code-voice} method on the `Circle`{.code-voice}
class.

</div>

In addition to simple properties that are stored, properties can have a
getter and a setter.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `class`{.code-voice} `EquilateralTriangle`{.vc}: `NamedShape`{.n} {
2.  `    var`{.code-voice} `sideLength`{.vc}: `Double`{.n} = `0.0`{.m}
3.  `    `{.code-voice}
4.  `    init`{.code-voice}(`sideLength`{.vc}: `Double`{.n},
    `name`{.vc}: `String`{.n}) {
5.  `        self`{.code-voice}.`sideLength`{.vc} = `sideLength`{.vc}
6.  `        super`{.code-voice}.`init`{.kt}(`name`{.vc}: `name`{.vc})
7.  `        numberOfSides`{.code-voice} = `3`{.m}
8.  `    }`{.code-voice}
9.  `    `{.code-voice}
10. `    var`{.code-voice} `perimeter`{.vc}: `Double`{.n} {
11. `        get`{.code-voice} {
12. `            return`{.code-voice} `3.0`{.m} \* `sideLength`{.vc}
13. `        }`{.code-voice}
14. `        set`{.code-voice} {
15. `            sideLength`{.code-voice} = `newValue`{.vc} / `3.0`{.m}
16. `        }`{.code-voice}
17. `    }`{.code-voice}
18. `    `{.code-voice}
19. `    override`{.code-voice} `func`{.kt} `simpleDescription`{.vc}()
    -&gt; `String`{.n} {
20. `        return`{.code-voice}
    `"An equilateral triangle with sides of length `{.s}\\(`sideLength`{.vc})`."`{.s}
21. `    }`{.code-voice}
22. `}`{.code-voice}
23. `var`{.code-voice} `triangle`{.vc} =
    `EquilateralTriangle`{.vc}(`sideLength`{.vc}: `3.1`{.m},
    `name`{.vc}: `"a triangle"`{.s})
24. `print`{.code-voice}(`triangle`{.vc}.`perimeter`{.vc})
25. `triangle`{.code-voice}.`perimeter`{.vc} = `9.9`{.m}
26. `print`{.code-voice}(`triangle`{.vc}.`sideLength`{.vc})

</div>

</div>

</div>

In the setter for `perimeter`{.code-voice}, the new value has the
implicit name `newValue`{.code-voice}. You can provide an explicit name
in parentheses after `set`{.code-voice}.

Notice that the initializer for the `EquilateralTriangle`{.code-voice}
class has three different steps:

1.  Setting the value of properties that the subclass declares.

2.  Calling the superclass’s initializer.

3.  Changing the value of properties defined by the superclass. Any
    additional setup work that uses methods, getters, or setters can
    also be done at this point.

If you don’t need to compute the property but still need to provide code
that is run before and after setting a new value, use
`willSet`{.code-voice} and `didSet`{.code-voice}. The code you provide
is run any time the value changes outside of an initializer. For
example, the class below ensures that the side length of its triangle is
always the same as the side length of its square.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `class`{.code-voice} `TriangleAndSquare`{.vc} {
2.  `    var`{.code-voice} `triangle`{.vc}: `EquilateralTriangle`{.n} {
3.  `        willSet`{.code-voice} {
4.  `            square`{.code-voice}.`sideLength`{.vc} =
    `newValue`{.vc}.`sideLength`{.vc}
5.  `        }`{.code-voice}
6.  `    }`{.code-voice}
7.  `    var`{.code-voice} `square`{.vc}: `Square`{.n} {
8.  `        willSet`{.code-voice} {
9.  `            triangle`{.code-voice}.`sideLength`{.vc} =
    `newValue`{.vc}.`sideLength`{.vc}
10. `        }`{.code-voice}
11. `    }`{.code-voice}
12. `    init`{.code-voice}(`size`{.vc}: `Double`{.n}, `name`{.vc}:
    `String`{.n}) {
13. `        square`{.code-voice} = `Square`{.vc}(`sideLength`{.vc}:
    `size`{.vc}, `name`{.vc}: `name`{.vc})
14. `        triangle`{.code-voice} =
    `EquilateralTriangle`{.vc}(`sideLength`{.vc}: `size`{.vc},
    `name`{.vc}: `name`{.vc})
15. `    }`{.code-voice}
16. `}`{.code-voice}
17. `var`{.code-voice} `triangleAndSquare`{.vc} =
    `TriangleAndSquare`{.vc}(`size`{.vc}: `10`{.m}, `name`{.vc}:
    `"another test shape"`{.s})
18. `print`{.code-voice}(`triangleAndSquare`{.vc}.`square`{.vc}.`sideLength`{.vc})
19. `print`{.code-voice}(`triangleAndSquare`{.vc}.`triangle`{.vc}.`sideLength`{.vc})
20. `triangleAndSquare`{.code-voice}.`square`{.vc} =
    `Square`{.vc}(`sideLength`{.vc}: `50`{.m}, `name`{.vc}:
    `"larger square"`{.s})
21. `print`{.code-voice}(`triangleAndSquare`{.vc}.`triangle`{.vc}.`sideLength`{.vc})

</div>

</div>

</div>

When working with optional values, you can write `?`{.code-voice} before
operations like methods, properties, and subscripting. If the value
before the `?`{.code-voice} is `nil`{.code-voice}, everything after the
`?`{.code-voice} is ignored and the value of the whole expression is
`nil`{.code-voice}. Otherwise, the optional value is unwrapped, and
everything after the `?`{.code-voice} acts on the unwrapped value. In
both cases, the value of the whole expression is an optional value.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `optionalSquare`{.vc}: `Square`{.n}? =
    `Square`{.vc}(`sideLength`{.vc}: `2.5`{.m}, `name`{.vc}:
    `"optional square"`{.s})
2.  `let`{.code-voice} `sideLength`{.vc} =
    `optionalSquare`{.vc}?.`sideLength`{.vc}

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH2-ID465}
### Enumerations and Structures {#enumerations-and-structures .section-name}

Use `enum`{.code-voice} to create an enumeration. Like classes and all
other named types, enumerations can have methods associated with them.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `enum`{.code-voice} `Rank`{.vc}: `Int`{.n} {
2.  `    case`{.code-voice} `Ace`{.vc} = `1`{.m}
3.  `    case`{.code-voice} `Two`{.vc}, `Three`{.vc}, `Four`{.vc},
    `Five`{.vc}, `Six`{.vc}, `Seven`{.vc}, `Eight`{.vc}, `Nine`{.vc},
    `Ten`{.vc}
4.  `    case`{.code-voice} `Jack`{.vc}, `Queen`{.vc}, `King`{.vc}
5.  `    func`{.code-voice} `simpleDescription`{.vc}() -&gt;
    `String`{.n} {
6.  `        switch`{.code-voice} `self`{.kt} {
7.  `        case`{.code-voice} .`Ace`{.vc}:
8.  `            return`{.code-voice} `"ace"`{.s}
9.  `        case`{.code-voice} .`Jack`{.vc}:
10. `            return`{.code-voice} `"jack"`{.s}
11. `        case`{.code-voice} .`Queen`{.vc}:
12. `            return`{.code-voice} `"queen"`{.s}
13. `        case`{.code-voice} .`King`{.vc}:
14. `            return`{.code-voice} `"king"`{.s}
15. `        default`{.code-voice}:
16. `            return`{.code-voice}
    `String`{.vc}(`self`{.kt}.`rawValue`{.vc})
17. `        }`{.code-voice}
18. `    }`{.code-voice}
19. `}`{.code-voice}
20. `let`{.code-voice} `ace`{.vc} = `Rank`{.vc}.`Ace`{.vc}
21. `let`{.code-voice} `aceRawValue`{.vc} = `ace`{.vc}.`rawValue`{.vc}

</div>

</div>

</div>

<div class="note">

Experiment

Write a function that compares two `Rank`{.code-voice} values by
comparing their raw values.

</div>

In the example above, the raw-value type of the enumeration is
`Int`{.code-voice}, so you only have to specify the first raw value. The
rest of the raw values are assigned in order. You can also use strings
or floating-point numbers as the raw type of an enumeration. Use the
`rawValue`{.code-voice} property to access the raw value of an
enumeration case.

Use the `init?(rawValue:)`{.code-voice} initializer to make an instance
of an enumeration from a raw value.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `if`{.code-voice} `let`{.kt} `convertedRank`{.vc} =
    `Rank`{.vc}(`rawValue`{.vc}: `3`{.m}) {
2.  `    let`{.code-voice} `threeDescription`{.vc} =
    `convertedRank`{.vc}.`simpleDescription`{.vc}()
3.  `}`{.code-voice}

</div>

</div>

</div>

The case values of an enumeration are actual values, not just another
way of writing their raw values. In fact, in cases where there isn’t a
meaningful raw value, you don’t have to provide one.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `enum`{.code-voice} `Suit`{.vc} {
2.  `    case`{.code-voice} `Spades`{.vc}, `Hearts`{.vc},
    `Diamonds`{.vc}, `Clubs`{.vc}
3.  `    func`{.code-voice} `simpleDescription`{.vc}() -&gt;
    `String`{.n} {
4.  `        switch`{.code-voice} `self`{.kt} {
5.  `        case`{.code-voice} .`Spades`{.vc}:
6.  `            return`{.code-voice} `"spades"`{.s}
7.  `        case`{.code-voice} .`Hearts`{.vc}:
8.  `            return`{.code-voice} `"hearts"`{.s}
9.  `        case`{.code-voice} .`Diamonds`{.vc}:
10. `            return`{.code-voice} `"diamonds"`{.s}
11. `        case`{.code-voice} .`Clubs`{.vc}:
12. `            return`{.code-voice} `"clubs"`{.s}
13. `        }`{.code-voice}
14. `    }`{.code-voice}
15. `}`{.code-voice}
16. `let`{.code-voice} `hearts`{.vc} = `Suit`{.vc}.`Hearts`{.vc}
17. `let`{.code-voice} `heartsDescription`{.vc} =
    `hearts`{.vc}.`simpleDescription`{.vc}()

</div>

</div>

</div>

<div class="note">

Experiment

Add a `color()`{.code-voice} method to `Suit`{.code-voice} that returns
“black” for spades and clubs, and returns “red” for hearts and diamonds.

</div>

Notice the two ways that the `Hearts`{.code-voice} case of the
enumeration is referred to above: When assigning a value to the
`hearts`{.code-voice} constant, the enumeration case
`Suit.Hearts`{.code-voice} is referred to by its full name because the
constant doesn’t have an explicit type specified. Inside the switch, the
enumeration case is referred to by the abbreviated form
`.Hearts`{.code-voice} because the value of `self`{.code-voice} is
already known to be a suit. You can use the abbreviated form anytime the
value’s type is already known.

Use `struct`{.code-voice} to create a structure. Structures support many
of the same behaviors as classes, including methods and initializers.
One of the most important differences between structures and classes is
that structures are always copied when they are passed around in your
code, but classes are passed by reference.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `struct`{.code-voice} `Card`{.vc} {
2.  `    var`{.code-voice} `rank`{.vc}: `Rank`{.n}
3.  `    var`{.code-voice} `suit`{.vc}: `Suit`{.n}
4.  `    func`{.code-voice} `simpleDescription`{.vc}() -&gt;
    `String`{.n} {
5.  `        return`{.code-voice}
    `"The `{.s}\\(`rank`{.vc}.`simpleDescription`{.vc}())` of `{.s}\\(`suit`{.vc}.`simpleDescription`{.vc}())`"`{.s}
6.  `    }`{.code-voice}
7.  `}`{.code-voice}
8.  `let`{.code-voice} `threeOfSpades`{.vc} = `Card`{.vc}(`rank`{.vc}:
    .`Three`{.vc}, `suit`{.vc}: .`Spades`{.vc})
9.  `let`{.code-voice} `threeOfSpadesDescription`{.vc} =
    `threeOfSpades`{.vc}.`simpleDescription`{.vc}()

</div>

</div>

</div>

<div class="note">

Experiment

Add a method to `Card`{.code-voice} that creates a full deck of cards,
with one card of each combination of rank and suit.

</div>

An instance of an enumeration case can have values associated with the
instance. Instances of the same enumeration case can have different
values associated with them. You provide the associated values when you
create the instance. Associated values and raw values are different: The
raw value of an enumeration case is the same for all of its instances,
and you provide the raw value when you define the enumeration.

For example, consider the case of requesting the sunrise and sunset time
from a server. The server either responds with the information or it
responds with some error information.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `enum`{.code-voice} `ServerResponse`{.vc} {
2.  `    case`{.code-voice} `Result`{.vc}(`String`{.vc}, `String`{.vc})
3.  `    case`{.code-voice} `Error`{.vc}(`String`{.vc})
4.  `}`{.code-voice}
5.  ` `{.code-voice}
6.  `let`{.code-voice} `success`{.vc} =
    `ServerResponse`{.vc}.`Result`{.vc}(`"6:00 am"`{.s},
    `"8:09 pm"`{.s})
7.  `let`{.code-voice} `failure`{.vc} =
    `ServerResponse`{.vc}.`Error`{.vc}(`"Out of cheese."`{.s})
8.  ` `{.code-voice}
9.  `switch`{.code-voice} `success`{.vc} {
10. `case`{.code-voice} `let`{.kt} .`Result`{.vc}(`sunrise`{.vc},
    `sunset`{.vc}):
11. `    print`{.code-voice}(`"Sunrise is at `{.s}\\(`sunrise`{.vc})` and sunset is at `{.s}\\(`sunset`{.vc})`."`{.s})
12. `case`{.code-voice} `let`{.kt} .`Error`{.vc}(`error`{.vc}):
13. `    print`{.code-voice}(`"Failure...  `{.s}\\(`error`{.vc})`"`{.s})
14. `}`{.code-voice}

</div>

</div>

</div>

<div class="note">

Experiment

Add a third case to `ServerResponse`{.code-voice} and to the switch.

</div>

Notice how the sunrise and sunset times are extracted from the
`ServerResponse`{.code-voice} value as part of matching the value
against the switch cases.

</div>

<div class="section section">

[‌](){#TP40016643-CH2-ID466}
### Protocols and Extensions {#protocols-and-extensions .section-name}

Use `protocol`{.code-voice} to declare a protocol.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `protocol`{.code-voice} `ExampleProtocol`{.vc} {
2.  `    var`{.code-voice} `simpleDescription`{.vc}: `String`{.n} {
    `get`{.kt} }
3.  `    mutating`{.code-voice} `func`{.kt} `adjust`{.vc}()
4.  `}`{.code-voice}

</div>

</div>

</div>

Classes, enumerations, and structs can all adopt protocols.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `class`{.code-voice} `SimpleClass`{.vc}: `ExampleProtocol`{.n} {
2.  `    var`{.code-voice} `simpleDescription`{.vc}: `String`{.n} =
    `"A very simple class."`{.s}
3.  `    var`{.code-voice} `anotherProperty`{.vc}: `Int`{.n} =
    `69105`{.m}
4.  `    func`{.code-voice} `adjust`{.vc}() {
5.  `        simpleDescription`{.code-voice} +=
    `"  Now 100% adjusted."`{.s}
6.  `    }`{.code-voice}
7.  `}`{.code-voice}
8.  `var`{.code-voice} `a`{.vc} = `SimpleClass`{.vc}()
9.  `a`{.code-voice}.`adjust`{.vc}()
10. `let`{.code-voice} `aDescription`{.vc} =
    `a`{.vc}.`simpleDescription`{.vc}
11. ` `{.code-voice}
12. `struct`{.code-voice} `SimpleStructure`{.vc}: `ExampleProtocol`{.n}
    {
13. `    var`{.code-voice} `simpleDescription`{.vc}: `String`{.n} =
    `"A simple structure"`{.s}
14. `    mutating`{.code-voice} `func`{.kt} `adjust`{.vc}() {
15. `        simpleDescription`{.code-voice} += `" (adjusted)"`{.s}
16. `    }`{.code-voice}
17. `}`{.code-voice}
18. `var`{.code-voice} `b`{.vc} = `SimpleStructure`{.vc}()
19. `b`{.code-voice}.`adjust`{.vc}()
20. `let`{.code-voice} `bDescription`{.vc} =
    `b`{.vc}.`simpleDescription`{.vc}

</div>

</div>

</div>

<div class="note">

Experiment

Write an enumeration that conforms to this protocol.

</div>

Notice the use of the `mutating`{.code-voice} keyword in the declaration
of `SimpleStructure`{.code-voice} to mark a method that modifies the
structure. The declaration of `SimpleClass`{.code-voice} doesn’t need
any of its methods marked as mutating because methods on a class can
always modify the class.

Use `extension`{.code-voice} to add functionality to an existing type,
such as new methods and computed properties. You can use an extension to
add protocol conformance to a type that is declared elsewhere, or even
to a type that you imported from a library or framework.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `extension`{.code-voice} `Int`{.n}: `ExampleProtocol`{.n} {
2.  `    var`{.code-voice} `simpleDescription`{.vc}: `String`{.n} {
3.  `        return`{.code-voice}
    `"The number `{.s}\\(`self`{.kt})`"`{.s}
4.  `    }`{.code-voice}
5.  `    mutating`{.code-voice} `func`{.kt} `adjust`{.vc}() {
6.  `        self`{.code-voice} += `42`{.m}
7.  `    }`{.code-voice}
8.  `}`{.code-voice}
9.  `print`{.code-voice}(`7`{.m}.`simpleDescription`{.vc})

</div>

</div>

</div>

<div class="note">

Experiment

Write an extension for the `Double`{.code-voice} type that adds an
`absoluteValue`{.code-voice} property.

</div>

You can use a protocol name just like any other named type—for example,
to create a collection of objects that have different types but that all
conform to a single protocol. When you work with values whose type is a
protocol type, methods outside the protocol definition are not
available.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `protocolValue`{.vc}: `ExampleProtocol`{.n} =
    `a`{.vc}
2.  `print`{.code-voice}(`protocolValue`{.vc}.`simpleDescription`{.vc})
3.  `// print(protocolValue.anotherProperty)  // Uncomment to see the error`{.code-voice}

</div>

</div>

</div>

Even though the variable `protocolValue`{.code-voice} has a runtime type
of `SimpleClass`{.code-voice}, the compiler treats it as the given type
of `ExampleProtocol`{.code-voice}. This means that you can’t
accidentally access methods or properties that the class implements in
addition to its protocol conformance.

</div>

<div class="section section">

[‌](){#TP40016643-CH2-NoLink_19}
### Generics {#generics .section-name}

Write a name inside angle brackets to make a generic function or type.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice}
    `repeatItem`{.vc}&lt;`Item`{.vc}&gt;(`item`{.vc}: `Item`{.n},
    `numberOfTimes`{.vc}: `Int`{.n}) -&gt; \[`Item`{.n}\] {
2.  `    var`{.code-voice} `result`{.vc} = \[`Item`{.n}\]()
3.  `    for`{.code-voice} `_`{.kt} `in`{.kt}
    `0`{.m}..&lt;`numberOfTimes`{.vc} {
4.  `        result`{.code-voice}.`append`{.vc}(`item`{.vc})
5.  `    }`{.code-voice}
6.  `    return`{.code-voice} `result`{.vc}
7.  `}`{.code-voice}
8.  `repeatItem`{.code-voice}(`"knock"`{.s},
    `numberOfTimes`{.vc}:`4`{.m})

</div>

</div>

</div>

You can make generic forms of functions and methods, as well as classes,
enumerations, and structures.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `// Reimplement the Swift standard library's optional type`{.code-voice}
2.  `enum`{.code-voice} `OptionalValue`{.vc}&lt;`Wrapped`{.vc}&gt; {
3.  `    case`{.code-voice} `None`{.vc}
4.  `    case`{.code-voice} `Some`{.vc}(`Wrapped`{.vc})
5.  `}`{.code-voice}
6.  `var`{.code-voice} `possibleInteger`{.vc}:
    `OptionalValue`{.n}&lt;`Int`{.n}&gt; = .`None`{.vc}
7.  `possibleInteger`{.code-voice} = .`Some`{.vc}(`100`{.m})

</div>

</div>

</div>

Use `where`{.code-voice} after the type name to specify a list of
requirements—for example, to require the type to implement a protocol,
to require two types to be the same, or to require a class to have a
particular superclass.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `anyCommonElements`{.vc} &lt;`T`{.vc}:
    `SequenceType`{.n}, `U`{.vc}: `SequenceType`{.n} `where`{.kt}
    `T`{.n}.`Generator`{.n}.`Element`{.n}: `Equatable`{.vc},
    `T`{.n}.`Generator`{.n}.`Element`{.n} ==
    `U`{.n}.`Generator`{.n}.`Element`{.n}&gt; (`lhs`{.vc}: `T`{.n},
    `_`{.kt} `rhs`{.vc}: `U`{.n}) -&gt; `Bool`{.n} {
2.  `    for`{.code-voice} `lhsItem`{.vc} `in`{.kt} `lhs`{.vc} {
3.  `        for`{.code-voice} `rhsItem`{.vc} `in`{.kt} `rhs`{.vc} {
4.  `            if`{.code-voice} `lhsItem`{.vc} == `rhsItem`{.vc} {
5.  `                return`{.code-voice} `true`{.kt}
6.  `            }`{.code-voice}
7.  `        }`{.code-voice}
8.  `    }`{.code-voice}
9.  `    return`{.code-voice} `false`{.kt}
10. `}`{.code-voice}
11. `anyCommonElements`{.code-voice}(\[`1`{.m}, `2`{.m}, `3`{.m}\],
    \[`3`{.m}\])

</div>

</div>

</div>

<div class="note">

Experiment

Modify the `anyCommonElements(_:_:)`{.code-voice} function to make a
function that returns an array of the elements that any two sequences
have in common.

</div>

Writing `<T: Equatable>`{.code-voice} is the same as writing
`<T where T: Equatable>`{.code-voice}.

</div>

</div>

</div>
