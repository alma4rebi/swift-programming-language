<div class="content-wrapper">

<div id="chapter_container" class="conceptualwithtasks">

[‌](){#TP40016643-CH7}[‌](){#TP40016643-CH7-ID285}
Strings and Characters {#strings-and-characters .chapter-name}
----------------------

<div class="section section">

A *string* is a series of characters, such as
`"hello, world"`{.code-voice} or `"albatross"`{.code-voice}. Swift
strings are represented by the `String`{.code-voice} type. The contents
of a `String`{.code-voice} can be accessed in various ways, including as
a collection of `Character`{.code-voice} values.

Swift’s `String`{.code-voice} and `Character`{.code-voice} types provide
a fast, Unicode-compliant way to work with text in your code. The syntax
for string creation and manipulation is lightweight and readable, with a
string literal syntax that is similar to C. String concatenation is as
simple as combining two strings with the `+`{.code-voice} operator, and
string mutability is managed by choosing between a constant or a
variable, just like any other value in Swift. You can also use strings
to insert constants, variables, literals, and expressions into longer
strings, in a process known as string interpolation. This makes it easy
to create custom string values for display, storage, and printing.

Despite this simplicity of syntax, Swift’s `String`{.code-voice} type is
a fast, modern string implementation. Every string is composed of
encoding-independent Unicode characters, and provides support for
accessing those characters in various Unicode representations.

<div class="note">

Note

Swift’s `String`{.code-voice} type is bridged with Foundation’s
`NSString`{.code-voice} class. If you are working with the Foundation
framework in Cocoa, the entire `NSString`{.code-voice} API is available
to call on any `String`{.code-voice} value you create when type cast to
`NSString`{.code-voice}, as described in
[AnyObject](TypeCasting.md#TP40016643-CH22-ID343). You can also use a
`String`{.code-voice} value with any API that requires an
`NSString`{.code-voice} instance.

For more information about using `String`{.code-voice} with Foundation
and Cocoa, see *Using Swift with Cocoa and Objective-C (Swift 2.1)*.

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH7-ID286}
### String Literals {#string-literals .section-name}

You can include predefined `String`{.code-voice} values within your code
as *string literals*. A string literal is a fixed sequence of textual
characters surrounded by a pair of double quotes (`""`{.code-voice}).

Use a string literal as an initial value for a constant or variable:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `someString`{.vc} =
    `"Some string literal value"`{.s}

</div>

</div>

</div>

Note that Swift infers a type of `String`{.code-voice} for the
`someString`{.code-voice} constant, because it is initialized with a
string literal value.

<div class="note">

Note

For information about using special characters in string literals, see
[Special Characters in String
Literals](StringsAndCharacters.md#TP40016643-CH7-ID295).

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH7-ID287}
### Initializing an Empty String {#initializing-an-empty-string .section-name}

To create an empty `String`{.code-voice} value as the starting point for
building a longer string, either assign an empty string literal to a
variable, or initialize a new `String`{.code-voice} instance with
initializer syntax:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `emptyString`{.vc} = `""`{.s}
    `// empty string literal`{.c}
2.  `var`{.code-voice} `anotherEmptyString`{.vc} = `String`{.vc}()
    `// initializer syntax`{.c}
3.  `// these two strings are both empty, and are equivalent to each other`{.code-voice}

</div>

</div>

</div>

Find out whether a `String`{.code-voice} value is empty by checking its
Boolean `isEmpty`{.code-voice} property:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `if`{.code-voice} `emptyString`{.vc}.`isEmpty`{.vc} {
2.  `    print`{.code-voice}(`"Nothing to see here"`{.s})
3.  `}`{.code-voice}
4.  `// prints "Nothing to see here"`{.code-voice}

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH7-ID288}
### String Mutability {#string-mutability .section-name}

You indicate whether a particular `String`{.code-voice} can be modified
(or *mutated*) by assigning it to a variable (in which case it can be
modified), or to a constant (in which case it cannot be modified):

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `variableString`{.vc} = `"Horse"`{.s}
2.  `variableString`{.code-voice} += `" and carriage"`{.s}
3.  `// variableString is now "Horse and carriage"`{.code-voice}
4.  ` `{.code-voice}
5.  `let`{.code-voice} `constantString`{.vc} = `"Highlander"`{.s}
6.  `constantString`{.code-voice} += `" and another Highlander"`{.s}
7.  `// this reports a compile-time error - a constant string cannot be modified`{.code-voice}

</div>

</div>

</div>

<div class="note">

Note

This approach is different from string mutation in Objective-C and
Cocoa, where you choose between two classes (`NSString`{.code-voice} and
`NSMutableString`{.code-voice}) to indicate whether a string can be
mutated.

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH7-ID289}
### Strings Are Value Types {#strings-are-value-types .section-name}

Swift’s `String`{.code-voice} type is a *value type*. If you create a
new `String`{.code-voice} value, that `String`{.code-voice} value is
*copied* when it is passed to a function or method, or when it is
assigned to a constant or variable. In each case, a new copy of the
existing `String`{.code-voice} value is created, and the new copy is
passed or assigned, not the original version. Value types are described
in [Structures and Enumerations Are Value
Types](ClassesAndStructures.md#TP40016643-CH13-ID88).

Swift’s copy-by-default `String`{.code-voice} behavior ensures that when
a function or method passes you a `String`{.code-voice} value, it is
clear that you own that exact `String`{.code-voice} value, regardless of
where it came from. You can be confident that the string you are passed
will not be modified unless you modify it yourself.

Behind the scenes, Swift’s compiler optimizes string usage so that
actual copying takes place only when absolutely necessary. This means
you always get great performance when working with strings as value
types.

</div>

<div class="section section">

[‌](){#TP40016643-CH7-ID290}
### Working with Characters {#working-with-characters .section-name}

You can access the individual `Character`{.code-voice} values for a
`String`{.code-voice} by iterating over its `characters`{.code-voice}
property with a `for`{.code-voice}-`in`{.code-voice} loop:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `for`{.code-voice} `character`{.vc} `in`{.kt}
    `"Dog!🐶"`{.s}.`characters`{.vc} {
2.  `    print`{.code-voice}(`character`{.vc})
3.  `}`{.code-voice}
4.  `// D`{.code-voice}
5.  `// o`{.code-voice}
6.  `// g`{.code-voice}
7.  `// !`{.code-voice}
8.  `// 🐶`{.code-voice}

</div>

</div>

</div>

The `for`{.code-voice}-`in`{.code-voice} loop is described in [For
Loops](ControlFlow.md#TP40016643-CH9-ID121).

Alternatively, you can create a stand-alone `Character`{.code-voice}
constant or variable from a single-character string literal by providing
a `Character`{.code-voice} type annotation:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `exclamationMark`{.vc}: `Character`{.n} =
    `"!"`{.s}

</div>

</div>

</div>

`String`{.code-voice} values can be constructed by passing an array of
`Character`{.code-voice} values as an argument to its initializer:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `catCharacters`{.vc}: \[`Character`{.n}\] =
    \[`"C"`{.s}, `"a"`{.s}, `"t"`{.s}, `"!"`{.s}, `"🐱"`{.s}\]
2.  `let`{.code-voice} `catString`{.vc} =
    `String`{.vc}(`catCharacters`{.vc})
3.  `print`{.code-voice}(`catString`{.vc})
4.  `// prints "Cat!🐱"`{.code-voice}

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH7-ID291}
### Concatenating Strings and Characters {#concatenating-strings-and-characters .section-name}

`String`{.code-voice} values can be added together (or *concatenated*)
with the addition operator (`+`{.code-voice}) to create a new
`String`{.code-voice} value:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `string1`{.vc} = `"hello"`{.s}
2.  `let`{.code-voice} `string2`{.vc} = `" there"`{.s}
3.  `var`{.code-voice} `welcome`{.vc} = `string1`{.vc} + `string2`{.vc}
4.  `// welcome now equals "hello there"`{.code-voice}

</div>

</div>

</div>

You can also append a `String`{.code-voice} value to an existing
`String`{.code-voice} variable with the addition assignment operator
(`+=`{.code-voice}):

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `instruction`{.vc} = `"look over"`{.s}
2.  `instruction`{.code-voice} += `string2`{.vc}
3.  `// instruction now equals "look over there"`{.code-voice}

</div>

</div>

</div>

You can append a `Character`{.code-voice} value to a
`String`{.code-voice} variable with the `String`{.code-voice} type’s
`append()`{.code-voice} method:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `exclamationMark`{.vc}: `Character`{.n} =
    `"!"`{.s}
2.  `welcome`{.code-voice}.`append`{.vc}(`exclamationMark`{.vc})
3.  `// welcome now equals "hello there!"`{.code-voice}

</div>

</div>

</div>

<div class="note">

Note

You can’t append a `String`{.code-voice} or `Character`{.code-voice} to
an existing `Character`{.code-voice} variable, because a
`Character`{.code-voice} value must contain a single character only.

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH7-ID292}
### String Interpolation {#string-interpolation .section-name}

*String interpolation* is a way to construct a new `String`{.code-voice}
value from a mix of constants, variables, literals, and expressions by
including their values inside a string literal. Each item that you
insert into the string literal is wrapped in a pair of parentheses,
prefixed by a backslash:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `multiplier`{.vc} = `3`{.m}
2.  `let`{.code-voice} `message`{.vc} =
    `"`{.s}\\(`multiplier`{.vc})` times 2.5 is `{.s}\\(`Double`{.vc}(`multiplier`{.vc}) \*
    `2.5`{.m})`"`{.s}
3.  `// message is "3 times 2.5 is 7.5"`{.code-voice}

</div>

</div>

</div>

In the example above, the value of `multiplier`{.code-voice} is inserted
into a string literal as `\(multiplier)`{.code-voice}. This placeholder
is replaced with the actual value of `multiplier`{.code-voice} when the
string interpolation is evaluated to create an actual string.

The value of `multiplier`{.code-voice} is also part of a larger
expression later in the string. This expression calculates the value of
`Double(multiplier) * 2.5`{.code-voice} and inserts the result
(`7.5`{.code-voice}) into the string. In this case, the expression is
written as `\(Double(multiplier) * 2.5)`{.code-voice} when it is
included inside the string literal.

<div class="note">

Note

The expressions you write inside parentheses within an interpolated
string cannot contain an unescaped backslash (`\`{.code-voice}), a
carriage return, or a line feed. However, they can contain other string
literals.

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH7-ID293}
### Unicode {#unicode .section-name}

*Unicode* is an international standard for encoding, representing, and
processing text in different writing systems. It enables you to
represent almost any character from any language in a standardized form,
and to read and write those characters to and from an external source
such as a text file or web page. Swift’s `String`{.code-voice} and
`Character`{.code-voice} types are fully Unicode-compliant, as described
in this section.

<div class="section section">

[‌](){#TP40016643-CH7-ID294}
### Unicode Scalars {#unicode-scalars .section-name}

Behind the scenes, Swift’s native `String`{.code-voice} type is built
from *Unicode scalar* values. A Unicode scalar is a unique 21-bit number
for a character or modifier, such as `U+0061`{.code-voice} for
`LATIN SMALL LETTER A`{.code-voice} (`"a"`{.code-voice}), or
`U+1F425`{.code-voice} for `FRONT-FACING BABY CHICK`{.code-voice}
(`"🐥"`{.code-voice}).

<div class="note">

Note

A Unicode scalar is any Unicode *code point* in the range
`U+0000`{.code-voice} to `U+D7FF`{.code-voice} inclusive or
`U+E000`{.code-voice} to `U+10FFFF`{.code-voice} inclusive. Unicode
scalars do not include the Unicode *surrogate pair* code points, which
are the code points in the range `U+D800`{.code-voice} to
`U+DFFF`{.code-voice} inclusive.

</div>

Note that not all 21-bit Unicode scalars are assigned to a
character—some scalars are reserved for future assignment. Scalars that
have been assigned to a character typically also have a name, such as
`LATIN SMALL LETTER A`{.code-voice} and
`FRONT-FACING BABY CHICK`{.code-voice} in the examples above.

</div>

<div class="section section">

[‌](){#TP40016643-CH7-ID295}
### Special Characters in String Literals {#special-characters-in-string-literals .section-name}

String literals can include the following special characters:

-   The escaped special characters `\0`{.code-voice} (null character),
    `\\`{.code-voice} (backslash), `\t`{.code-voice} (horizontal tab),
    `\n`{.code-voice} (line feed), `\r`{.code-voice} (carriage return),
    `\"`{.code-voice} (double quote) and `\'`{.code-voice}
    (single quote)

-   An arbitrary Unicode scalar, written as
    `\u{`{.code-voice}*n*`}`{.code-voice}, where *n* is a 1–8 digit
    hexadecimal number with a value equal to a valid Unicode code point

The code below shows four examples of these special characters. The
`wiseWords`{.code-voice} constant contains two escaped double quote
characters. The `dollarSign`{.code-voice}, `blackHeart`{.code-voice},
and `sparklingHeart`{.code-voice} constants demonstrate the Unicode
scalar format:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `wiseWords`{.vc} =
    `"\"Imagination is more important than knowledge\" - Einstein"`{.s}
2.  `// "Imagination is more important than knowledge" - Einstein`{.code-voice}
3.  `let`{.code-voice} `dollarSign`{.vc} = `"\u{24}"`{.s}
    `// $,  Unicode scalar U+0024`{.c}
4.  `let`{.code-voice} `blackHeart`{.vc} = `"\u{2665}"`{.s}
    `// ♥,  Unicode scalar U+2665`{.c}
5.  `let`{.code-voice} `sparklingHeart`{.vc} = `"\u{1F496}"`{.s}
    `// 💖, Unicode scalar U+1F496`{.c}

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH7-ID296}
### Extended Grapheme Clusters {#extended-grapheme-clusters .section-name}

Every instance of Swift’s `Character`{.code-voice} type represents a
single *extended grapheme cluster*. An extended grapheme cluster is a
sequence of one or more Unicode scalars that (when combined) produce a
single human-readable character.

Here’s an example. The letter `é`{.code-voice} can be represented as the
single Unicode scalar `é`{.code-voice}
(`LATIN SMALL LETTER E WITH ACUTE`{.code-voice}, or
`U+00E9`{.code-voice}). However, the same letter can also be represented
as a *pair* of scalars—a standard letter `e`{.code-voice}
(`LATIN SMALL LETTER E`{.code-voice}, or `U+0065`{.code-voice}),
followed by the `COMBINING ACUTE ACCENT`{.code-voice} scalar
(`U+0301`{.code-voice}). The `COMBINING ACUTE ACCENT`{.code-voice}
scalar is graphically applied to the scalar that precedes it, turning an
`e`{.code-voice} into an `é`{.code-voice} when it is rendered by a
Unicode-aware text-rendering system.

In both cases, the letter `é`{.code-voice} is represented as a single
Swift `Character`{.code-voice} value that represents an extended
grapheme cluster. In the first case, the cluster contains a single
scalar; in the second case, it is a cluster of two scalars:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `eAcute`{.vc}: `Character`{.n} = `"\u{E9}"`{.s}
    `// é`{.c}
2.  `let`{.code-voice} `combinedEAcute`{.vc}: `Character`{.n} =
    `"\u{65}\u{301}"`{.s} `// e followed by ́`{.c}
3.  `// eAcute is é, combinedEAcute is é`{.code-voice}

</div>

</div>

</div>

Extended grapheme clusters are a flexible way to represent many complex
script characters as a single `Character`{.code-voice} value. For
example, Hangul syllables from the Korean alphabet can be represented as
either a precomposed or decomposed sequence. Both of these
representations qualify as a single `Character`{.code-voice} value in
Swift:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `precomposed`{.vc}: `Character`{.n} =
    `"\u{D55C}"`{.s} `// 한`{.c}
2.  `let`{.code-voice} `decomposed`{.vc}: `Character`{.n} =
    `"\u{1112}\u{1161}\u{11AB}"`{.s} `// ᄒ, ᅡ, ᆫ`{.c}
3.  `// precomposed is 한, decomposed is 한`{.code-voice}

</div>

</div>

</div>

Extended grapheme clusters enable scalars for enclosing marks (such as
`COMBINING ENCLOSING CIRCLE`{.code-voice}, or `U+20DD`{.code-voice}) to
enclose other Unicode scalars as part of a single
`Character`{.code-voice} value:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `enclosedEAcute`{.vc}: `Character`{.n} =
    `"\u{E9}\u{20DD}"`{.s}
2.  `// enclosedEAcute is é⃝`{.code-voice}

</div>

</div>

</div>

Unicode scalars for regional indicator symbols can be combined in pairs
to make a single `Character`{.code-voice} value, such as this
combination of `REGIONAL INDICATOR SYMBOL LETTER U`{.code-voice}
(`U+1F1FA`{.code-voice}) and
`REGIONAL INDICATOR SYMBOL LETTER S`{.code-voice}
(`U+1F1F8`{.code-voice}):

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `regionalIndicatorForUS`{.vc}: `Character`{.n} =
    `"\u{1F1FA}\u{1F1F8}"`{.s}
2.  `// regionalIndicatorForUS is 🇺🇸`{.code-voice}

</div>

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH7-ID297}
### Counting Characters {#counting-characters .section-name}

To retrieve a count of the `Character`{.code-voice} values in a string,
use the `count`{.code-voice} property of the string’s
`characters`{.code-voice} property:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `unusualMenagerie`{.vc} =
    `"Koala 🐨, Snail 🐌, Penguin 🐧, Dromedary 🐪"`{.s}
2.  `print`{.code-voice}(`"unusualMenagerie has `{.s}\\(`unusualMenagerie`{.vc}.`characters`{.vc}.`count`{.vc})` characters"`{.s})
3.  `// prints "unusualMenagerie has 40 characters"`{.code-voice}

</div>

</div>

</div>

Note that Swift’s use of extended grapheme clusters for
`Character`{.code-voice} values means that string concatenation and
modification may not always affect a string’s character count.

For example, if you initialize a new string with the four-character word
`cafe`{.code-voice}, and then append a
`COMBINING ACUTE ACCENT`{.code-voice} (`U+0301`{.code-voice}) to the end
of the string, the resulting string will still have a character count of
`4`{.code-voice}, with a fourth character of `é`{.code-voice}, not
`e`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `word`{.vc} = `"cafe"`{.s}
2.  `print`{.code-voice}(`"the number of characters in `{.s}\\(`word`{.vc})` is `{.s}\\(`word`{.vc}.`characters`{.vc}.`count`{.vc})`"`{.s})
3.  `// prints "the number of characters in cafe is 4"`{.code-voice}
4.  ` `{.code-voice}
5.  `word`{.code-voice} += `"\u{301}"`{.s}
    `// COMBINING ACUTE ACCENT, U+0301`{.c}
6.  ` `{.code-voice}
7.  `print`{.code-voice}(`"the number of characters in `{.s}\\(`word`{.vc})` is `{.s}\\(`word`{.vc}.`characters`{.vc}.`count`{.vc})`"`{.s})
8.  `// prints "the number of characters in café is 4"`{.code-voice}

</div>

</div>

</div>

<div class="note">

Note

Extended grapheme clusters can be composed of one or more Unicode
scalars. This means that different characters—and different
representations of the same character—can require different amounts of
memory to store. Because of this, characters in Swift do not each take
up the same amount of memory within a string’s representation. As a
result, the number of characters in a string cannot be calculated
without iterating through the string to determine its extended grapheme
cluster boundaries. If you are working with particularly long string
values, be aware that the `characters`{.code-voice} property must
iterate over the Unicode scalars in the entire string in order to
determine the characters for that string.

The count of the characters returned by the `characters`{.code-voice}
property is not always the same as the `length`{.code-voice} property of
an `NSString`{.code-voice} that contains the same characters. The length
of an `NSString`{.code-voice} is based on the number of 16-bit code
units within the string’s UTF-16 representation and not the number of
Unicode extended grapheme clusters within the string.

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH7-ID494}
### Accessing and Modifying a String {#accessing-and-modifying-a-string .section-name}

You access and modify a string through its methods and properties, or by
using subscript syntax.

<div class="section section">

[‌](){#TP40016643-CH7-ID534}
### String Indices {#string-indices .section-name}

Each `String`{.code-voice} value has an associated *index type*,
`String.Index`{.code-voice}, which corresponds to the position of each
`Character`{.code-voice} in the string.

As mentioned above, different characters can require different amounts
of memory to store, so in order to determine which
`Character`{.code-voice} is at a particular position, you must iterate
over each Unicode scalar from the start or end of that
`String`{.code-voice}. For this reason, Swift strings cannot be indexed
by integer values.

Use the `startIndex`{.code-voice} property to access the position of the
first `Character`{.code-voice} of a `String`{.code-voice}. The
`endIndex`{.code-voice} property is the position after the last
character in a `String`{.code-voice}. As a result, the
`endIndex`{.code-voice} property isn’t a valid argument to a string’s
subscript. If a `String`{.code-voice} is empty,
`startIndex`{.code-voice} and `endIndex`{.code-voice} are equal.

A `String.Index`{.code-voice} value can access its immediately preceding
index by calling the `predecessor()`{.code-voice} method, and its
immediately succeeding index by calling the `successor()`{.code-voice}
method. Any index in a `String`{.code-voice} can be accessed from any
other index by chaining these methods together, or by using the
`advancedBy(_:)`{.code-voice} method. Attempting to access an index
outside of a string’s range will trigger a runtime error.

You can use subscript syntax to access the `Character`{.code-voice} at a
particular `String`{.code-voice} index.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `greeting`{.vc} = `"Guten Tag!"`{.s}
2.  `greeting`{.code-voice}\[`greeting`{.vc}.`startIndex`{.vc}\]
3.  `// G`{.code-voice}
4.  `greeting`{.code-voice}\[`greeting`{.vc}.`endIndex`{.vc}.`predecessor`{.vc}()\]
5.  `// !`{.code-voice}
6.  `greeting`{.code-voice}\[`greeting`{.vc}.`startIndex`{.vc}.`successor`{.vc}()\]
7.  `// u`{.code-voice}
8.  `let`{.code-voice} `index`{.vc} =
    `greeting`{.vc}.`startIndex`{.vc}.`advancedBy`{.vc}(`7`{.m})
9.  `greeting`{.code-voice}\[`index`{.vc}\]
10. `// a`{.code-voice}

</div>

</div>

</div>

Attempting to access a `Character`{.code-voice} at an index outside of a
string’s range will trigger a runtime error.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `greeting`{.code-voice}\[`greeting`{.vc}.`endIndex`{.vc}\]
    `// error`{.c}
2.  `greeting`{.code-voice}.`endIndex`{.vc}.`successor`{.vc}()
    `// error`{.c}

</div>

</div>

</div>

Use the `indices`{.code-voice} property of the `characters`{.code-voice}
property to create a `Range`{.code-voice} of all of the indexes used to
access individual characters in a string.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `for`{.code-voice} `index`{.vc} `in`{.kt}
    `greeting`{.vc}.`characters`{.vc}.`indices`{.vc} {
2.  `    print`{.code-voice}(`"`{.s}\\(`greeting`{.vc}\[`index`{.vc}\])` "`{.s},
    `terminator`{.vc}: `""`{.s})
3.  `}`{.code-voice}
4.  `// prints "G u t e n   T a g ! "`{.code-voice}

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH7-ID496}
### Inserting and Removing {#inserting-and-removing .section-name}

To insert a character into a string at a specified index, use the
`insert(_:atIndex:)`{.code-voice} method.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `welcome`{.vc} = `"hello"`{.s}
2.  `welcome`{.code-voice}.`insert`{.vc}(`"!"`{.s}, `atIndex`{.vc}:
    `welcome`{.vc}.`endIndex`{.vc})
3.  `// welcome now equals "hello!"`{.code-voice}

</div>

</div>

</div>

To insert the contents of another string at a specified index, use the
`insertContentsOf(_:at:)`{.code-voice} method.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `welcome`{.code-voice}.`insertContentsOf`{.vc}(`" there"`{.s}.`characters`{.vc},
    `at`{.vc}: `welcome`{.vc}.`endIndex`{.vc}.`predecessor`{.vc}())
2.  `// welcome now equals "hello there!"`{.code-voice}

</div>

</div>

</div>

To remove a character from a string at a specified index, use the
`removeAtIndex(_:)`{.code-voice} method.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `welcome`{.code-voice}.`removeAtIndex`{.vc}(`welcome`{.vc}.`endIndex`{.vc}.`predecessor`{.vc}())
2.  `// welcome now equals "hello there"`{.code-voice}

</div>

</div>

</div>

To remove a substring at a specified range, use the
`removeRange(_:)`{.code-voice} method:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `range`{.vc} =
    `welcome`{.vc}.`endIndex`{.vc}.`advancedBy`{.vc}(-`6`{.m})..&lt;`welcome`{.vc}.`endIndex`{.vc}
2.  `welcome`{.code-voice}.`removeRange`{.vc}(`range`{.vc})
3.  `// welcome now equals "hello"`{.code-voice}

</div>

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH7-ID298}
### Comparing Strings {#comparing-strings .section-name}

Swift provides three ways to compare textual values: string and
character equality, prefix equality, and suffix equality.

<div class="section section">

[‌](){#TP40016643-CH7-ID299}
### String and Character Equality {#string-and-character-equality .section-name}

String and character equality is checked with the “equal to” operator
(`==`{.code-voice}) and the “not equal to” operator (`!=`{.code-voice}),
as described in [Comparison
Operators](BasicOperators.md#TP40016643-CH6-ID70):

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `quotation`{.vc} =
    `"We're a lot alike, you and I."`{.s}
2.  `let`{.code-voice} `sameQuotation`{.vc} =
    `"We're a lot alike, you and I."`{.s}
3.  `if`{.code-voice} `quotation`{.vc} == `sameQuotation`{.vc} {
4.  `    print`{.code-voice}(`"These two strings are considered equal"`{.s})
5.  `}`{.code-voice}
6.  `// prints "These two strings are considered equal"`{.code-voice}

</div>

</div>

</div>

Two `String`{.code-voice} values (or two `Character`{.code-voice}
values) are considered equal if their extended grapheme clusters are
*canonically equivalent*. Extended grapheme clusters are canonically
equivalent if they have the same linguistic meaning and appearance, even
if they are composed from different Unicode scalars behind the scenes.

For example, `LATIN SMALL LETTER E WITH ACUTE`{.code-voice}
(`U+00E9`{.code-voice}) is canonically equivalent to
`LATIN SMALL LETTER E`{.code-voice} (`U+0065`{.code-voice}) followed by
`COMBINING ACUTE ACCENT`{.code-voice} (`U+0301`{.code-voice}). Both of
these extended grapheme clusters are valid ways to represent the
character `é`{.code-voice}, and so they are considered to be canonically
equivalent:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `// "Voulez-vous un café?" using LATIN SMALL LETTER E WITH ACUTE`{.code-voice}
2.  `let`{.code-voice} `eAcuteQuestion`{.vc} =
    `"Voulez-vous un caf\u{E9}?"`{.s}
3.  ` `{.code-voice}
4.  `// "Voulez-vous un café?" using LATIN SMALL LETTER E and COMBINING ACUTE ACCENT`{.code-voice}
5.  `let`{.code-voice} `combinedEAcuteQuestion`{.vc} =
    `"Voulez-vous un caf\u{65}\u{301}?"`{.s}
6.  ` `{.code-voice}
7.  `if`{.code-voice} `eAcuteQuestion`{.vc} ==
    `combinedEAcuteQuestion`{.vc} {
8.  `    print`{.code-voice}(`"These two strings are considered equal"`{.s})
9.  `}`{.code-voice}
10. `// prints "These two strings are considered equal"`{.code-voice}

</div>

</div>

</div>

Conversely, `LATIN CAPITAL LETTER A`{.code-voice}
(`U+0041`{.code-voice}, or `"A"`{.code-voice}), as used in English, is
*not* equivalent to `CYRILLIC CAPITAL LETTER A`{.code-voice}
(`U+0410`{.code-voice}, or `"А"`{.code-voice}), as used in Russian. The
characters are visually similar, but do not have the same linguistic
meaning:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `latinCapitalLetterA`{.vc}: `Character`{.n} =
    `"\u{41}"`{.s}
2.  ` `{.code-voice}
3.  `let`{.code-voice} `cyrillicCapitalLetterA`{.vc}: `Character`{.n} =
    `"\u{0410}"`{.s}
4.  ` `{.code-voice}
5.  `if`{.code-voice} `latinCapitalLetterA`{.vc} !=
    `cyrillicCapitalLetterA`{.vc} {
6.  `    print`{.code-voice}(`"These two characters are not equivalent"`{.s})
7.  `}`{.code-voice}
8.  `// prints "These two characters are not equivalent"`{.code-voice}

</div>

</div>

</div>

<div class="note">

Note

String and character comparisons in Swift are not locale-sensitive.

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH7-ID300}
### Prefix and Suffix Equality {#prefix-and-suffix-equality .section-name}

To check whether a string has a particular string prefix or suffix, call
the string’s `hasPrefix(_:)`{.code-voice} and
`hasSuffix(_:)`{.code-voice} methods, both of which take a single
argument of type `String`{.code-voice} and return a Boolean value.

The examples below consider an array of strings representing the scene
locations from the first two acts of Shakespeare’s *Romeo and Juliet*:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `romeoAndJuliet`{.vc} = \[
2.  `    "Act 1 Scene 1: Verona, A public place"`{.code-voice},
3.  `    "Act 1 Scene 2: Capulet's mansion"`{.code-voice},
4.  `    "Act 1 Scene 3: A room in Capulet's mansion"`{.code-voice},
5.  `    "Act 1 Scene 4: A street outside Capulet's mansion"`{.code-voice},
6.  `    "Act 1 Scene 5: The Great Hall in Capulet's mansion"`{.code-voice},
7.  `    "Act 2 Scene 1: Outside Capulet's mansion"`{.code-voice},
8.  `    "Act 2 Scene 2: Capulet's orchard"`{.code-voice},
9.  `    "Act 2 Scene 3: Outside Friar Lawrence's cell"`{.code-voice},
10. `    "Act 2 Scene 4: A street in Verona"`{.code-voice},
11. `    "Act 2 Scene 5: Capulet's mansion"`{.code-voice},
12. `    "Act 2 Scene 6: Friar Lawrence's cell"`{.code-voice}
13. `]`{.code-voice}

</div>

</div>

</div>

You can use the `hasPrefix(_:)`{.code-voice} method with the
`romeoAndJuliet`{.code-voice} array to count the number of scenes in Act
1 of the play:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `act1SceneCount`{.vc} = `0`{.m}
2.  `for`{.code-voice} `scene`{.vc} `in`{.kt} `romeoAndJuliet`{.vc} {
3.  `    if`{.code-voice} `scene`{.vc}.`hasPrefix`{.vc}(`"Act 1 "`{.s})
    {
4.  `        ++act1SceneCount`{.code-voice}
5.  `    }`{.code-voice}
6.  `}`{.code-voice}
7.  `print`{.code-voice}(`"There are `{.s}\\(`act1SceneCount`{.vc})` scenes in Act 1"`{.s})
8.  `// prints "There are 5 scenes in Act 1"`{.code-voice}

</div>

</div>

</div>

Similarly, use the `hasSuffix(_:)`{.code-voice} method to count the
number of scenes that take place in or around Capulet’s mansion and
Friar Lawrence’s cell:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `mansionCount`{.vc} = `0`{.m}
2.  `var`{.code-voice} `cellCount`{.vc} = `0`{.m}
3.  `for`{.code-voice} `scene`{.vc} `in`{.kt} `romeoAndJuliet`{.vc} {
4.  `    if`{.code-voice}
    `scene`{.vc}.`hasSuffix`{.vc}(`"Capulet's mansion"`{.s}) {
5.  `        ++mansionCount`{.code-voice}
6.  `    } else`{.code-voice} `if`{.kt}
    `scene`{.vc}.`hasSuffix`{.vc}(`"Friar Lawrence's cell"`{.s}) {
7.  `        ++cellCount`{.code-voice}
8.  `    }`{.code-voice}
9.  `}`{.code-voice}
10. `print`{.code-voice}(`"`{.s}\\(`mansionCount`{.vc})` mansion scenes; `{.s}\\(`cellCount`{.vc})` cell scenes"`{.s})
11. `// prints "6 mansion scenes; 2 cell scenes"`{.code-voice}

</div>

</div>

</div>

<div class="note">

Note

The `hasPrefix(_:)`{.code-voice} and `hasSuffix(_:)`{.code-voice}
methods perform a character-by-character canonical equivalence
comparison between the extended grapheme clusters in each string, as
described in [String and Character
Equality](StringsAndCharacters.md#TP40016643-CH7-ID299).

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH7-ID301}
### Unicode Representations of Strings {#unicode-representations-of-strings .section-name}

When a Unicode string is written to a text file or some other storage,
the Unicode scalars in that string are encoded in one of several
Unicode-defined *encoding forms*. Each form encodes the string in small
chunks known as *code units*. These include the UTF-8 encoding form
(which encodes a string as 8-bit code units), the UTF-16 encoding form
(which encodes a string as 16-bit code units), and the UTF-32 encoding
form (which encodes a string as 32-bit code units).

Swift provides several different ways to access Unicode representations
of strings. You can iterate over the string with a
`for`{.code-voice}-`in`{.code-voice} statement, to access its individual
`Character`{.code-voice} values as Unicode extended grapheme clusters.
This process is described in [Working with
Characters](StringsAndCharacters.md#TP40016643-CH7-ID290).

Alternatively, access a `String`{.code-voice} value in one of three
other Unicode-compliant representations:

-   A collection of UTF-8 code units (accessed with the string’s
    `utf8`{.code-voice} property)

-   A collection of UTF-16 code units (accessed with the string’s
    `utf16`{.code-voice} property)

-   A collection of 21-bit Unicode scalar values, equivalent to the
    string’s UTF-32 encoding form (accessed with the string’s
    `unicodeScalars`{.code-voice} property)

Each example below shows a different representation of the following
string, which is made up of the characters `D`{.code-voice},
`o`{.code-voice}, `g`{.code-voice}, `‼`{.code-voice}
(`DOUBLE EXCLAMATION MARK`{.code-voice}, or Unicode scalar
`U+203C`{.code-voice}), and the 🐶 character (`DOG FACE`{.code-voice}, or
Unicode scalar `U+1F436`{.code-voice}):

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `dogString`{.vc} = `"Dog‼🐶"`{.s}

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH7-ID302}
### UTF-8 Representation {#utf-8-representation .section-name}

You can access a UTF-8 representation of a `String`{.code-voice} by
iterating over its `utf8`{.code-voice} property. This property is of
type `String.UTF8View`{.code-voice}, which is a collection of unsigned
8-bit (`UInt8`{.code-voice}) values, one for each byte in the string’s
UTF-8 representation:

<div class="figure">

<span class="caption"></span> ![image:
../Art/UTF8\_2x.png](Art/UTF8_2x.png){width="476" height="229"}

</div>

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `for`{.code-voice} `codeUnit`{.vc} `in`{.kt}
    `dogString`{.vc}.`utf8`{.vc} {
2.  `    print`{.code-voice}(`"`{.s}\\(`codeUnit`{.vc})` "`{.s},
    `terminator`{.vc}: `""`{.s})
3.  `}`{.code-voice}
4.  `print`{.code-voice}(`""`{.s})
5.  `// 68 111 103 226 128 188 240 159 144 182`{.code-voice}

</div>

</div>

</div>

In the example above, the first three decimal `codeUnit`{.code-voice}
values (`68`{.code-voice}, `111`{.code-voice}, `103`{.code-voice})
represent the characters `D`{.code-voice}, `o`{.code-voice}, and
`g`{.code-voice}, whose UTF-8 representation is the same as their ASCII
representation. The next three decimal `codeUnit`{.code-voice} values
(`226`{.code-voice}, `128`{.code-voice}, `188`{.code-voice}) are a
three-byte UTF-8 representation of the
`DOUBLE EXCLAMATION MARK`{.code-voice} character. The last four
`codeUnit`{.code-voice} values (`240`{.code-voice}, `159`{.code-voice},
`144`{.code-voice}, `182`{.code-voice}) are a four-byte UTF-8
representation of the `DOG FACE`{.code-voice} character.

</div>

<div class="section section">

[‌](){#TP40016643-CH7-ID303}
### UTF-16 Representation {#utf-16-representation .section-name}

You can access a UTF-16 representation of a `String`{.code-voice} by
iterating over its `utf16`{.code-voice} property. This property is of
type `String.UTF16View`{.code-voice}, which is a collection of unsigned
16-bit (`UInt16`{.code-voice}) values, one for each 16-bit code unit in
the string’s UTF-16 representation:

<div class="figure">

<span class="caption"></span> ![image:
../Art/UTF16\_2x.png](Art/UTF16_2x.png){width="477" height="229"}

</div>

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `for`{.code-voice} `codeUnit`{.vc} `in`{.kt}
    `dogString`{.vc}.`utf16`{.vc} {
2.  `    print`{.code-voice}(`"`{.s}\\(`codeUnit`{.vc})` "`{.s},
    `terminator`{.vc}: `""`{.s})
3.  `}`{.code-voice}
4.  `print`{.code-voice}(`""`{.s})
5.  `// 68 111 103 8252 55357 56374`{.code-voice}

</div>

</div>

</div>

Again, the first three `codeUnit`{.code-voice} values
(`68`{.code-voice}, `111`{.code-voice}, `103`{.code-voice}) represent
the characters `D`{.code-voice}, `o`{.code-voice}, and `g`{.code-voice},
whose UTF-16 code units have the same values as in the string’s UTF-8
representation (because these Unicode scalars represent ASCII
characters).

The fourth `codeUnit`{.code-voice} value (`8252`{.code-voice}) is a
decimal equivalent of the hexadecimal value `203C`{.code-voice}, which
represents the Unicode scalar `U+203C`{.code-voice} for the
`DOUBLE EXCLAMATION MARK`{.code-voice} character. This character can be
represented as a single code unit in UTF-16.

The fifth and sixth `codeUnit`{.code-voice} values (`55357`{.code-voice}
and `56374`{.code-voice}) are a UTF-16 surrogate pair representation of
the `DOG FACE`{.code-voice} character. These values are a high-surrogate
value of `U+D83D`{.code-voice} (decimal value `55357`{.code-voice}) and
a low-surrogate value of `U+DC36`{.code-voice} (decimal value
`56374`{.code-voice}).

</div>

<div class="section section">

[‌](){#TP40016643-CH7-ID304}
### Unicode Scalar Representation {#unicode-scalar-representation .section-name}

You can access a Unicode scalar representation of a
`String`{.code-voice} value by iterating over its
`unicodeScalars`{.code-voice} property. This property is of type
`UnicodeScalarView`{.code-voice}, which is a collection of values of
type `UnicodeScalar`{.code-voice}.

Each `UnicodeScalar`{.code-voice} has a `value`{.code-voice} property
that returns the scalar’s 21-bit value, represented within a
`UInt32`{.code-voice} value:

<div class="figure">

<span class="caption"></span> ![image:
../Art/UnicodeScalar\_2x.png](Art/UnicodeScalar_2x.png){width="477"
height="229"}

</div>

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `for`{.code-voice} `scalar`{.vc} `in`{.kt}
    `dogString`{.vc}.`unicodeScalars`{.vc} {
2.  `    print`{.code-voice}(`"`{.s}\\(`scalar`{.vc}.`value`{.vc})` "`{.s},
    `terminator`{.vc}: `""`{.s})
3.  `}`{.code-voice}
4.  `print`{.code-voice}(`""`{.s})
5.  `// 68 111 103 8252 128054`{.code-voice}

</div>

</div>

</div>

The `value`{.code-voice} properties for the first three
`UnicodeScalar`{.code-voice} values (`68`{.code-voice},
`111`{.code-voice}, `103`{.code-voice}) once again represent the
characters `D`{.code-voice}, `o`{.code-voice}, and `g`{.code-voice}.

The fourth `codeUnit`{.code-voice} value (`8252`{.code-voice}) is again
a decimal equivalent of the hexadecimal value `203C`{.code-voice}, which
represents the Unicode scalar `U+203C`{.code-voice} for the
`DOUBLE EXCLAMATION MARK`{.code-voice} character.

The `value`{.code-voice} property of the fifth and final
`UnicodeScalar`{.code-voice}, `128054`{.code-voice}, is a decimal
equivalent of the hexadecimal value `1F436`{.code-voice}, which
represents the Unicode scalar `U+1F436`{.code-voice} for the
`DOG FACE`{.code-voice} character.

As an alternative to querying their `value`{.code-voice} properties,
each `UnicodeScalar`{.code-voice} value can also be used to construct a
new `String`{.code-voice} value, such as with string interpolation:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `for`{.code-voice} `scalar`{.vc} `in`{.kt}
    `dogString`{.vc}.`unicodeScalars`{.vc} {
2.  `    print`{.code-voice}(`"`{.s}\\(`scalar`{.vc})` "`{.s})
3.  `}`{.code-voice}
4.  `// D`{.code-voice}
5.  `// o`{.code-voice}
6.  `// g`{.code-voice}
7.  `// ‼`{.code-voice}
8.  `// 🐶`{.code-voice}

</div>

</div>

</div>

</div>

</div>

</div>

</div>
