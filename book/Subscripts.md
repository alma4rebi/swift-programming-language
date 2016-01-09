<div class="content-wrapper">

<div id="chapter_container" class="conceptualwithtasks">

[‌](){#TP40016643-CH16}[‌](){#TP40016643-CH16-ID305}
Subscripts {#subscripts .chapter-name}
----------

<div class="section section">

Classes, structures, and enumerations can define *subscripts*, which are
shortcuts for accessing the member elements of a collection, list, or
sequence. You use subscripts to set and retrieve values by index without
needing separate methods for setting and retrieval. For example, you
access elements in an `Array`{.code-voice} instance as
`someArray[index]`{.code-voice} and elements in a
`Dictionary`{.code-voice} instance as
`someDictionary[key]`{.code-voice}.

You can define multiple subscripts for a single type, and the
appropriate subscript overload to use is selected based on the type of
index value you pass to the subscript. Subscripts are not limited to a
single dimension, and you can define subscripts with multiple input
parameters to suit your custom type’s needs.

</div>

<div class="section section">

[‌](){#TP40016643-CH16-ID306}
### Subscript Syntax {#subscript-syntax .section-name}

Subscripts enable you to query instances of a type by writing one or
more values in square brackets after the instance name. Their syntax is
similar to both instance method syntax and computed property syntax. You
write subscript definitions with the `subscript`{.code-voice} keyword,
and specify one or more input parameters and a return type, in the same
way as instance methods. Unlike instance methods, subscripts can be
read-write or read-only. This behavior is communicated by a getter and
setter in the same way as for computed properties:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `subscript`{.code-voice}(`index`{.vc}: `Int`{.n}) -&gt; `Int`{.n} {
2.  `    get`{.code-voice} {
3.  `        // return an appropriate subscript value here`{.code-voice}
4.  `    }`{.code-voice}
5.  `    set`{.code-voice}(`newValue`{.vc}) {
6.  `        // perform a suitable setting action here`{.code-voice}
7.  `    }`{.code-voice}
8.  `}`{.code-voice}

</div>

</div>

</div>

The type of `newValue`{.code-voice} is the same as the return value of
the subscript. As with computed properties, you can choose not to
specify the setter’s `(newValue)`{.code-voice} parameter. A default
parameter called `newValue`{.code-voice} is provided to your setter if
you do not provide one yourself.

As with read-only computed properties, you can drop the
`get`{.code-voice} keyword for read-only subscripts:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `subscript`{.code-voice}(`index`{.vc}: `Int`{.n}) -&gt; `Int`{.n} {
2.  `    // return an appropriate subscript value here`{.code-voice}
3.  `}`{.code-voice}

</div>

</div>

</div>

Here’s an example of a read-only subscript implementation, which defines
a `TimesTable`{.code-voice} structure to represent an *n*-times-table of
integers:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `struct`{.code-voice} `TimesTable`{.vc} {
2.  `    let`{.code-voice} `multiplier`{.vc}: `Int`{.n}
3.  `    subscript`{.code-voice}(`index`{.vc}: `Int`{.n}) -&gt;
    `Int`{.n} {
4.  `        return`{.code-voice} `multiplier`{.vc} \* `index`{.vc}
5.  `    }`{.code-voice}
6.  `}`{.code-voice}
7.  `let`{.code-voice} `threeTimesTable`{.vc} =
    `TimesTable`{.vc}(`multiplier`{.vc}: `3`{.m})
8.  `print`{.code-voice}(`"six times three is `{.s}\\(`threeTimesTable`{.vc}\[`6`{.m}\])`"`{.s})
9.  `// prints "six times three is 18"`{.code-voice}

</div>

</div>

</div>

In this example, a new instance of `TimesTable`{.code-voice} is created
to represent the three-times-table. This is indicated by passing a value
of `3`{.code-voice} to the structure’s `initializer`{.code-voice} as the
value to use for the instance’s `multiplier`{.code-voice} parameter.

You can query the `threeTimesTable`{.code-voice} instance by calling its
subscript, as shown in the call to `threeTimesTable[6]`{.code-voice}.
This requests the sixth entry in the three-times-table, which returns a
value of `18`{.code-voice}, or `3`{.code-voice} times `6`{.code-voice}.

<div class="note">

Note

An *n*-times-table is based on a fixed mathematical rule. It is not
appropriate to set `threeTimesTable[someIndex]`{.code-voice} to a new
value, and so the subscript for `TimesTable`{.code-voice} is defined as
a read-only subscript.

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH16-ID307}
### Subscript Usage {#subscript-usage .section-name}

The exact meaning of “subscript” depends on the context in which it is
used. Subscripts are typically used as a shortcut for accessing the
member elements in a collection, list, or sequence. You are free to
implement subscripts in the most appropriate way for your particular
class or structure’s functionality.

For example, Swift’s `Dictionary`{.code-voice} type implements a
subscript to set and retrieve the values stored in a
`Dictionary`{.code-voice} instance. You can set a value in a dictionary
by providing a key of the dictionary’s key type within subscript
brackets, and assigning a value of the dictionary’s value type to the
subscript:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `numberOfLegs`{.vc} = \[`"spider"`{.s}: `8`{.m},
    `"ant"`{.s}: `6`{.m}, `"cat"`{.s}: `4`{.m}\]
2.  `numberOfLegs`{.code-voice}\[`"bird"`{.s}\] = `2`{.m}

</div>

</div>

</div>

The example above defines a variable called `numberOfLegs`{.code-voice}
and initializes it with a dictionary literal containing three key-value
pairs. The type of the `numberOfLegs`{.code-voice} dictionary is
inferred to be `[String: Int]`{.code-voice}. After creating the
dictionary, this example uses subscript assignment to add a
`String`{.code-voice} key of `"bird"`{.code-voice} and an
`Int`{.code-voice} value of `2`{.code-voice} to the dictionary.

For more information about `Dictionary`{.code-voice} subscripting, see
[Accessing and Modifying a
Dictionary](CollectionTypes.md#TP40016643-CH8-ID116).

<div class="note">

Note

Swift’s `Dictionary`{.code-voice} type implements its key-value
subscripting as a subscript that takes and returns an *optional* type.
For the `numberOfLegs`{.code-voice} dictionary above, the key-value
subscript takes and returns a value of type `Int?`{.code-voice}, or
“optional int”. The `Dictionary`{.code-voice} type uses an optional
subscript type to model the fact that not every key will have a value,
and to give a way to delete a value for a key by assigning a
`nil`{.code-voice} value for that key.

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH16-ID308}
### Subscript Options {#subscript-options .section-name}

Subscripts can take any number of input parameters, and these input
parameters can be of any type. Subscripts can also return any type.
Subscripts can use variable parameters and variadic parameters, but
cannot use in-out parameters or provide default parameter values.

A class or structure can provide as many subscript implementations as it
needs, and the appropriate subscript to be used will be inferred based
on the types of the value or values that are contained within the
subscript brackets at the point that the subscript is used. This
definition of multiple subscripts is known as *subscript overloading*.

While it is most common for a subscript to take a single parameter, you
can also define a subscript with multiple parameters if it is
appropriate for your type. The following example defines a
`Matrix`{.code-voice} structure, which represents a two-dimensional
matrix of `Double`{.code-voice} values. The `Matrix`{.code-voice}
structure’s subscript takes two integer parameters:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `struct`{.code-voice} `Matrix`{.vc} {
2.  `    let`{.code-voice} `rows`{.vc}: `Int`{.n}, `columns`{.vc}:
    `Int`{.n}
3.  `    var`{.code-voice} `grid`{.vc}: \[`Double`{.n}\]
4.  `    init`{.code-voice}(`rows`{.vc}: `Int`{.n}, `columns`{.vc}:
    `Int`{.n}) {
5.  `        self`{.code-voice}.`rows`{.vc} = `rows`{.vc}
6.  `        self`{.code-voice}.`columns`{.vc} = `columns`{.vc}
7.  `        grid`{.code-voice} = `Array`{.vc}(`count`{.vc}:
    `rows`{.vc} \* `columns`{.vc}, `repeatedValue`{.vc}: `0.0`{.m})
8.  `    }`{.code-voice}
9.  `    func`{.code-voice} `indexIsValidForRow`{.vc}(`row`{.vc}:
    `Int`{.n}, `column`{.vc}: `Int`{.n}) -&gt; `Bool`{.n} {
10. `        return`{.code-voice} `row`{.vc} &gt;= `0`{.m} && `row`{.vc}
    &lt; `rows`{.vc} && `column`{.vc} &gt;= `0`{.m} && `column`{.vc}
    &lt; `columns`{.vc}
11. `    }`{.code-voice}
12. `    subscript`{.code-voice}(`row`{.vc}: `Int`{.n}, `column`{.vc}:
    `Int`{.n}) -&gt; `Double`{.n} {
13. `        get`{.code-voice} {
14. `            assert`{.code-voice}(`indexIsValidForRow`{.vc}(`row`{.vc},
    `column`{.vc}: `column`{.vc}), `"Index out of range"`{.s})
15. `            return`{.code-voice} `grid`{.vc}\[(`row`{.vc} \*
    `columns`{.vc}) + `column`{.vc}\]
16. `        }`{.code-voice}
17. `        set`{.code-voice} {
18. `            assert`{.code-voice}(`indexIsValidForRow`{.vc}(`row`{.vc},
    `column`{.vc}: `column`{.vc}), `"Index out of range"`{.s})
19. `            grid`{.code-voice}\[(`row`{.vc} \* `columns`{.vc}) +
    `column`{.vc}\] = `newValue`{.vc}
20. `        }`{.code-voice}
21. `    }`{.code-voice}
22. `}`{.code-voice}

</div>

</div>

</div>

`Matrix`{.code-voice} provides an initializer that takes two parameters
called `rows`{.code-voice} and `columns`{.code-voice}, and creates an
array that is large enough to store `rows * columns`{.code-voice} values
of type `Double`{.code-voice}. Each position in the matrix is given an
initial value of `0.0`{.code-voice}. To achieve this, the array’s size,
and an initial cell value of `0.0`{.code-voice}, are passed to an array
initializer that creates and initializes a new array of the correct
size. This initializer is described in more detail in [Creating an Array
with a Default Value](CollectionTypes.md#TP40016643-CH8-ID501).

You can construct a new `Matrix`{.code-voice} instance by passing an
appropriate row and column count to its initializer:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `matrix`{.vc} = `Matrix`{.vc}(`rows`{.vc}:
    `2`{.m}, `columns`{.vc}: `2`{.m})

</div>

</div>

</div>

The preceding example creates a new `Matrix`{.code-voice} instance with
two rows and two columns. The `grid`{.code-voice} array for this
`Matrix`{.code-voice} instance is effectively a flattened version of the
matrix, as read from top left to bottom right:

<div class="figure">

<span class="caption"></span> ![image:
../Art/subscriptMatrix01\_2x.png](Art/subscriptMatrix01_2x.png){width="280"
height="173"}

</div>

Values in the matrix can be set by passing row and column values into
the subscript, separated by a comma:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `matrix`{.code-voice}\[`0`{.m}, `1`{.m}\] = `1.5`{.m}
2.  `matrix`{.code-voice}\[`1`{.m}, `0`{.m}\] = `3.2`{.m}

</div>

</div>

</div>

These two statements call the subscript’s setter to set a value of
`1.5`{.code-voice} in the top right position of the matrix (where
`row`{.code-voice} is `0`{.code-voice} and `column`{.code-voice} is
`1`{.code-voice}), and `3.2`{.code-voice} in the bottom left position
(where `row`{.code-voice} is `1`{.code-voice} and `column`{.code-voice}
is `0`{.code-voice}):

<div class="figure">

<span class="caption"></span> ![image:
../Art/subscriptMatrix02\_2x.png](Art/subscriptMatrix02_2x.png){width="98"
height="62"}

</div>

The `Matrix`{.code-voice} subscript’s getter and setter both contain an
assertion to check that the subscript’s `row`{.code-voice} and
`column`{.code-voice} values are valid. To assist with these assertions,
`Matrix`{.code-voice} includes a convenience method called
`indexIsValidForRow(_:column:)`{.code-voice}, which checks whether the
requested `row`{.code-voice} and `column`{.code-voice} are inside the
bounds of the matrix:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `indexIsValidForRow`{.vc}(`row`{.vc}: `Int`{.n},
    `column`{.vc}: `Int`{.n}) -&gt; `Bool`{.n} {
2.  `    return`{.code-voice} `row`{.vc} &gt;= `0`{.m} && `row`{.vc}
    &lt; `rows`{.vc} && `column`{.vc} &gt;= `0`{.m} && `column`{.vc}
    &lt; `columns`{.vc}
3.  `}`{.code-voice}

</div>

</div>

</div>

An assertion is triggered if you try to access a subscript that is
outside of the matrix bounds:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `someValue`{.vc} = `matrix`{.vc}\[`2`{.m},
    `2`{.m}\]
2.  `// this triggers an assert, because [2, 2] is outside of the matrix bounds`{.code-voice}

</div>

</div>

</div>

</div>

</div>

</div>
