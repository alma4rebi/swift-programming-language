<div class="content-wrapper">

<div id="chapter_container" class="conceptualwithtasks">

[‌](){#TP40016643-CH36}[‌](){#TP40016643-CH36-ID419}
Patterns {#patterns .chapter-name}
--------

<div class="section section">

A *pattern* represents the structure of a single value or a composite
value. For example, the structure of a tuple `(1, 2)`{.code-voice} is a
comma-separated list of two elements. Because patterns represent the
structure of a value rather than any one particular value, you can match
them with a variety of values. For instance, the pattern
`(x, y)`{.code-voice} matches the tuple `(1, 2)`{.code-voice} and any
other two-element tuple. In addition to matching a pattern with a value,
you can extract part or all of a composite value and bind each part to a
constant or variable name.

In Swift, there are two basic kinds of patterns: those that successfully
match any kind of value, and those that may fail to match a specified
value at runtime.

The first kind of pattern is used for destructuring values in simple
variable, constant, and optional bindings. These include wildcard
patterns, identifier patterns, and any value binding or tuple patterns
containing them. You can specify a type annotation for these patterns to
constrain them to match only values of a certain type.

The second kind of pattern is used for full pattern matching, where the
values you’re trying to match against may not be there at runtime. These
include enumeration case patterns, optional patterns, expression
patterns, and type-casting patterns. You use these patterns in a case
label of a `switch`{.code-voice} statement, a `catch`{.code-voice}
clause of a `do`{.code-voice} statement, or in the case condition of an
`if`{.code-voice}, `while`{.code-voice}, `guard`{.code-voice}, or
`for`{.code-voice}-`in`{.code-voice} statement.

<div class="syntax-defs">

Grammar of a pattern

<div class="syntax-defs-group">

[‌](){#pattern} <span class="syntax-def-name"> pattern </span> <span
class="arrow"> → </span><span
class="syntactic-cat">[wildcard-pattern](Patterns.md#wildcard-pattern)</span><span
class="optional"><span
class="syntactic-cat">[type-annotation](Types.md#type-annotation)</span>~opt~</span>

[‌](){#TP40016643-CH36-NoLink_625} <span class="syntax-def-name">
pattern </span> <span class="arrow"> → </span><span
class="syntactic-cat">[identifier-pattern](Patterns.md#identifier-pattern)</span><span
class="optional"><span
class="syntactic-cat">[type-annotation](Types.md#type-annotation)</span>~opt~</span>

[‌](){#TP40016643-CH36-NoLink_626} <span class="syntax-def-name">
pattern </span> <span class="arrow"> → </span><span
class="syntactic-cat">[value-binding-pattern](Patterns.md#value-binding-pattern)</span>

[‌](){#TP40016643-CH36-NoLink_627} <span class="syntax-def-name">
pattern </span> <span class="arrow"> → </span><span
class="syntactic-cat">[tuple-pattern](Patterns.md#tuple-pattern)</span><span
class="optional"><span
class="syntactic-cat">[type-annotation](Types.md#type-annotation)</span>~opt~</span>

[‌](){#TP40016643-CH36-NoLink_628} <span class="syntax-def-name">
pattern </span> <span class="arrow"> → </span><span
class="syntactic-cat">[enum-case-pattern](Patterns.md#enum-case-pattern)</span>

[‌](){#TP40016643-CH36-NoLink_629} <span class="syntax-def-name">
pattern </span> <span class="arrow"> → </span><span
class="syntactic-cat">[optional-pattern](Patterns.md#optional-pattern)</span>

[‌](){#TP40016643-CH36-NoLink_630} <span class="syntax-def-name">
pattern </span> <span class="arrow"> → </span><span
class="syntactic-cat">[type-casting-pattern](Patterns.md#type-casting-pattern)</span>

[‌](){#TP40016643-CH36-NoLink_631} <span class="syntax-def-name">
pattern </span> <span class="arrow"> → </span><span
class="syntactic-cat">[expression-pattern](Patterns.md#expression-pattern)</span>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH36-ID420}
### Wildcard Pattern {#wildcard-pattern .section-name}

A *wildcard pattern* matches and ignores any value and consists of an
underscore (`_`{.code-voice}). Use a wildcard pattern when you don’t
care about the values being matched against. For example, the following
code iterates through the closed range `1...3`{.code-voice}, ignoring
the current value of the range on each iteration of the loop:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `for`{.code-voice} `_`{.kt} `in`{.kt} `1`{.m}...`3`{.m} {
2.  `    // Do something three times.`{.code-voice}
3.  `}`{.code-voice}

</div>

</div>

</div>

<div class="syntax-defs">

Grammar of a wildcard pattern

<div class="syntax-defs-group">

[‌](){#wildcard-pattern} <span class="syntax-def-name"> wildcard-pattern
</span> <span class="arrow"> → </span>`_`{.literal}

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH36-ID421}
### Identifier Pattern {#identifier-pattern .section-name}

An *identifier pattern* matches any value and binds the matched value to
a variable or constant name. For example, in the following constant
declaration, `someValue`{.code-voice} is an identifier pattern that
matches the value `42`{.code-voice} of type `Int`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `someValue`{.vc} = `42`{.m}

</div>

</div>

</div>

When the match succeeds, the value `42`{.code-voice} is bound (assigned)
to the constant name `someValue`{.code-voice}.

When the pattern on the left-hand side of a variable or constant
declaration is an identifier pattern, the identifier pattern is
implicitly a subpattern of a value-binding pattern.

<div class="syntax-defs">

Grammar of an identifier pattern

<div class="syntax-defs-group">

[‌](){#identifier-pattern} <span class="syntax-def-name">
identifier-pattern </span> <span class="arrow"> → </span><span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH36-ID422}
### Value-Binding Pattern {#value-binding-pattern .section-name}

A *value-binding pattern* binds matched values to constant names.

Identifiers patterns within a value-binding pattern bind new named
constants to their matching values. For example, you can decompose the
elements of a tuple and bind the value of each element to a
corresponding identifier pattern.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `point`{.vc} = (`3`{.m}, `2`{.m})
2.  `switch`{.code-voice} `point`{.vc} {
3.  `    // Bind x and y to the elements of point.`{.code-voice}
4.  `case`{.code-voice} `let`{.kt} (`x`{.vc}, `y`{.vc}):
5.  `    print`{.code-voice}(`"The point is at (`{.s}\\(`x`{.vc})`, `{.s}\\(`y`{.vc})`)."`{.s})
6.  `}`{.code-voice}
7.  `// prints "The point is at (3, 2)."`{.code-voice}

</div>

</div>

</div>

In the example above, `let`{.code-voice} distributes to each identifier
pattern in the tuple pattern `(x, y)`{.code-voice}. Because of this
behavior, the `switch`{.code-voice} cases
`case let (x, y):`{.code-voice} and `case (let x, let y):`{.code-voice}
match the same values.

<div class="syntax-defs">

Grammar of a value-binding pattern

<div class="syntax-defs-group">

[‌](){#value-binding-pattern} <span class="syntax-def-name">
value-binding-pattern </span> <span class="arrow"> →
</span>`let`{.literal}<span
class="syntactic-cat">[pattern](Patterns.md#pattern)</span>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH36-ID423}
### Tuple Pattern {#tuple-pattern .section-name}

A *tuple pattern* is a comma-separated list of zero or more patterns,
enclosed in parentheses. Tuple patterns match values of corresponding
tuple types.

You can constrain a tuple pattern to match certain kinds of tuple types
by using type annotations. For example, the tuple pattern
`(x, y): (Int, Int)`{.code-voice} in the constant declaration
`let (x, y): (Int, Int) = (1, 2)`{.code-voice} matches only tuple types
in which both elements are of type `Int`{.code-voice}.

When a tuple pattern is used as the pattern in a
`for`{.code-voice}-`in`{.code-voice} statement or in a variable or
constant declaration, it can contain only wildcard patterns, identifier
patterns, optional patterns, or other tuple patterns that contain those.
For example, the following code isn’t valid because the element
`0`{.code-voice} in the tuple pattern `(x, 0)`{.code-voice} is an
expression pattern:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `points`{.vc} = \[(`0`{.m}, `0`{.m}), (`1`{.m},
    `0`{.m}), (`1`{.m}, `1`{.m}), (`2`{.m}, `0`{.m}), (`2`{.m},
    `1`{.m})\]
2.  `// This code isn't valid.`{.code-voice}
3.  `for`{.code-voice} (`x`{.vc}, `0`{.m}) `in`{.kt} `points`{.vc} {
4.  `    /* ... */`{.code-voice}
5.  `}`{.code-voice}

</div>

</div>

</div>

The parentheses around a tuple pattern that contains a single element
have no effect. The pattern matches values of that single element’s
type. For example, the following are equivalent:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `a`{.vc} = `2`{.m} `// a: Int = 2`{.c}
2.  `let`{.code-voice} (`a`{.vc}) = `2`{.m} `// a: Int = 2`{.c}
3.  `let`{.code-voice} (`a`{.vc}): `Int`{.n} = `2`{.m}
    `// a: Int = 2`{.c}

</div>

</div>

</div>

<div class="syntax-defs">

Grammar of a tuple pattern

<div class="syntax-defs-group">

[‌](){#tuple-pattern} <span class="syntax-def-name"> tuple-pattern
</span> <span class="arrow"> → </span>`(`{.literal}<span
class="optional"><span
class="syntactic-cat">[tuple-pattern-element-list](Patterns.md#tuple-pattern-element-list)</span>~opt~</span>`)`{.literal}

[‌](){#tuple-pattern-element-list} <span class="syntax-def-name">
tuple-pattern-element-list </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[tuple-pattern-element](Patterns.md#tuple-pattern-element)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[tuple-pattern-element](Patterns.md#tuple-pattern-element)</span>`,`{.literal}<span
class="syntactic-cat">[tuple-pattern-element-list](Patterns.md#tuple-pattern-element-list)</span>
</span>

[‌](){#tuple-pattern-element} <span class="syntax-def-name">
tuple-pattern-element </span> <span class="arrow"> → </span><span
class="syntactic-cat">[pattern](Patterns.md#pattern)</span>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH36-ID424}
### Enumeration Case Pattern {#enumeration-case-pattern .section-name}

An *enumeration case pattern* matches a case of an existing enumeration
type. Enumeration case patterns appear in `switch`{.code-voice}
statement case labels and in the case conditions of `if`{.code-voice},
`while`{.code-voice}, `guard`{.code-voice}, and
`for`{.code-voice}-`in`{.code-voice} statements.

If the enumeration case you’re trying to match has any associated
values, the corresponding enumeration case pattern must specify a tuple
pattern that contains one element for each associated value. For an
example that uses a `switch`{.code-voice} statement to match enumeration
cases containing associated values, see [Associated
Values](Enumerations.md#TP40016643-CH12-ID148).

<div class="syntax-defs">

Grammar of an enumeration case pattern

<div class="syntax-defs-group">

[‌](){#enum-case-pattern} <span class="syntax-def-name">
enum-case-pattern </span> <span class="arrow"> → </span><span
class="optional"><span
class="syntactic-cat">[type-identifier](Types.md#type-identifier)</span>~opt~</span>`.`{.literal}<span
class="syntactic-cat">[enum-case-name](Declarations.md#enum-case-name)</span><span
class="optional"><span
class="syntactic-cat">[tuple-pattern](Patterns.md#tuple-pattern)</span>~opt~</span>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH36-ID520}
### Optional Pattern {#optional-pattern .section-name}

An *optional pattern* matches values wrapped in a
`Some(Wrapped)`{.code-voice} case of an `Optional<Wrapped>`{.code-voice}
or `ImplicitlyUnwrappedOptional<Wrapped>`{.code-voice} enumeration.
Optional patterns consist of an identifier pattern followed immediately
by a question mark and appear in the same places as enumeration case
patterns.

Because optional patterns are syntactic sugar for
`Optional`{.code-voice} and `ImplicitlyUnwrappedOptional`{.code-voice}
enumeration case patterns, the following are equivalent:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `someOptional`{.vc}: `Int`{.n}? = `42`{.m}
2.  `// Match using an enumeration case pattern`{.code-voice}
3.  `if`{.code-voice} `case`{.kt} .`Some`{.vc}(`let`{.kt} `x`{.vc}) =
    `someOptional`{.vc} {
4.  `    print`{.code-voice}(`x`{.vc})
5.  `}`{.code-voice}
6.  ` `{.code-voice}
7.  `// Match using an optional pattern`{.code-voice}
8.  `if`{.code-voice} `case`{.kt} `let`{.kt} `x`{.vc}? =
    `someOptional`{.vc} {
9.  `    print`{.code-voice}(`x`{.vc})
10. `}`{.code-voice}

</div>

</div>

</div>

The optional pattern provides a convenient way to iterate over an array
of optional values in a `for`{.code-voice}-`in`{.code-voice} statement,
executing the body of the loop only for non-`nil`{.code-voice} elements.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `arrayOfOptionalInts`{.vc}: \[`Int`{.n}?\] =
    \[`nil`{.kt}, `2`{.m}, `3`{.m}, `nil`{.kt}, `5`{.m}\]
2.  `// Match only non-nil values`{.code-voice}
3.  `for`{.code-voice} `case`{.kt} `let`{.kt} `number`{.vc}? `in`{.kt}
    `arrayOfOptionalInts`{.vc} {
4.  `    print`{.code-voice}(`"Found a `{.s}\\(`number`{.vc})`"`{.s})
5.  `}`{.code-voice}
6.  `// Found a 2`{.code-voice}
7.  `// Found a 3`{.code-voice}
8.  `// Found a 5`{.code-voice}

</div>

</div>

</div>

<div class="syntax-defs">

Grammar of an optional pattern

<div class="syntax-defs-group">

[‌](){#optional-pattern} <span class="syntax-def-name"> optional-pattern
</span> <span class="arrow"> → </span><span
class="syntactic-cat">[identifier-pattern](Patterns.md#identifier-pattern)</span>`?`{.literal}

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH36-ID425}
### Type-Casting Patterns {#type-casting-patterns .section-name}

There are two type-casting patterns, the `is`{.code-voice} pattern and
the `as`{.code-voice} pattern. The `is`{.code-voice} pattern appears
only in `switch`{.code-voice} statement case labels. The
`is`{.code-voice} and `as`{.code-voice} patterns have the following
form:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    is type
    ```

-   ``` {.code-voice}
    pattern as type
    ```

</div>

The `is`{.code-voice} pattern matches a value if the type of that value
at runtime is the same as the type specified in the right-hand side of
the `is`{.code-voice} pattern—or a subclass of that type. The
`is`{.code-voice} pattern behaves like the `is`{.code-voice} operator in
that they both perform a type cast but discard the returned type.

The `as`{.code-voice} pattern matches a value if the type of that value
at runtime is the same as the type specified in the right-hand side of
the `as`{.code-voice} pattern—or a subclass of that type. If the match
succeeds, the type of the matched value is cast to the *pattern*
specified in the left-hand side of the `as`{.code-voice} pattern.

For an example that uses a `switch`{.code-voice} statement to match
values with `is`{.code-voice} and `as`{.code-voice} patterns, see [Type
Casting for Any and AnyObject](TypeCasting.md#TP40016643-CH22-ID342).

<div class="syntax-defs">

Grammar of a type casting pattern

<div class="syntax-defs-group">

[‌](){#type-casting-pattern} <span class="syntax-def-name">
type-casting-pattern </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[is-pattern](Patterns.md#is-pattern)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[as-pattern](Patterns.md#as-pattern)</span>
</span>

[‌](){#is-pattern} <span class="syntax-def-name"> is-pattern </span>
<span class="arrow"> → </span>`is`{.literal}<span
class="syntactic-cat">[type](Types.md#type)</span>

[‌](){#as-pattern} <span class="syntax-def-name"> as-pattern </span>
<span class="arrow"> → </span><span
class="syntactic-cat">[pattern](Patterns.md#pattern)</span>`as`{.literal}<span
class="syntactic-cat">[type](Types.md#type)</span>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH36-ID426}
### Expression Pattern {#expression-pattern .section-name}

An *expression pattern* represents the value of an expression.
Expression patterns appear only in `switch`{.code-voice} statement case
labels.

The expression represented by the expression pattern is compared with
the value of an input expression using the Swift standard library
`~=`{.code-voice} operator. The matches succeeds if the
`~=`{.code-voice} operator returns `true`{.code-voice}. By default, the
`~=`{.code-voice} operator compares two values of the same type using
the `==`{.code-voice} operator. It can also match an integer value with
a range of integers in an `Range`{.code-voice} object, as the following
example shows:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `point`{.vc} = (`1`{.m}, `2`{.m})
2.  `switch`{.code-voice} `point`{.vc} {
3.  `case`{.code-voice} (`0`{.m}, `0`{.m}):
4.  `    print`{.code-voice}(`"(0, 0) is at the origin."`{.s})
5.  `case`{.code-voice} (-`2`{.m}...`2`{.m}, -`2`{.m}...`2`{.m}):
6.  `    print`{.code-voice}(`"(`{.s}\\(`point`{.vc}.`0`{.m})`, `{.s}\\(`point`{.vc}.`1`{.m})`) is near the origin."`{.s})
7.  `default`{.code-voice}:
8.  `    print`{.code-voice}(`"The point is at (`{.s}\\(`point`{.vc}.`0`{.m})`, `{.s}\\(`point`{.vc}.`1`{.m})`)."`{.s})
9.  `}`{.code-voice}
10. `// prints "(1, 2) is near the origin."`{.code-voice}

</div>

</div>

</div>

You can overload the `~=`{.code-voice} operator to provide custom
expression matching behavior. For example, you can rewrite the above
example to compare the `point`{.code-voice} expression with a string
representations of points.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `// Overload the ~= operator to match a string with an integer`{.code-voice}
2.  `func`{.code-voice} \~=(`pattern`{.vc}: `String`{.n}, `value`{.vc}:
    `Int`{.n}) -&gt; `Bool`{.n} {
3.  `    return`{.code-voice} `pattern`{.vc} ==
    `"`{.s}\\(`value`{.vc})`"`{.s}
4.  `}`{.code-voice}
5.  `switch`{.code-voice} `point`{.vc} {
6.  `case`{.code-voice} (`"0"`{.s}, `"0"`{.s}):
7.  `    print`{.code-voice}(`"(0, 0) is at the origin."`{.s})
8.  `default`{.code-voice}:
9.  `    print`{.code-voice}(`"The point is at (`{.s}\\(`point`{.vc}.`0`{.m})`, `{.s}\\(`point`{.vc}.`1`{.m})`)."`{.s})
10. `}`{.code-voice}
11. `// prints "The point is at (1, 2)."`{.code-voice}

</div>

</div>

</div>

<div class="syntax-defs">

Grammar of an expression pattern

<div class="syntax-defs-group">

[‌](){#expression-pattern} <span class="syntax-def-name">
expression-pattern </span> <span class="arrow"> → </span><span
class="syntactic-cat">[expression](Expressions.md#expression)</span>

</div>

</div>

</div>

</div>

</div>
