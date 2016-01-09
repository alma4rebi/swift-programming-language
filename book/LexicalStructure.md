Lexical Structure
-----------------

The *lexical structure* of Swift describes what sequence of characters form valid tokens of the language. These valid tokens form the lowest-level building blocks of the language and are used to describe the rest of the language in subsequent chapters. A token consists of an identifier, keyword, punctuation, literal, or operator.

In most cases, tokens are generated from the characters of a Swift source file by considering the longest possible substring from the input text, within the constraints of the grammar that are specified below. This behavior is referred to as *longest match* or *maximal munch*.

### Whitespace and Comments

Whitespace has two uses: to separate tokens in the source file and to help determine whether an operator is a prefix or postfix (see [Operators](LexicalStructure.md#TP40016643-CH30-ID418)), but is otherwise ignored. The following characters are considered whitespace: space (U+0020), line feed (U+000A), carriage return (U+000D), horizontal tab (U+0009), vertical tab (U+000B), form feed (U+000C) and null (U+0000).

Comments are treated as whitespace by the compiler. Single line comments begin with `//` and continue until a line feed (U+000A) or carriage return (U+000D). Multiline comments begin with `/*` and end with `*/`. Nesting multiline comments is allowed, but the comment markers must be balanced.

Comments can contain additional formatting and markup, as described in *Markup Formatting Reference*.

### Identifiers

*Identifiers* begin with an uppercase or lowercase letter A through Z, an underscore (`_`), a noncombining alphanumeric Unicode character in the Basic Multilingual Plane, or a character outside the Basic Multilingual Plane that isn’t in a Private Use Area. After the first character, digits and combining Unicode characters are also allowed.

To use a reserved word as an identifier, put a backtick (`` ` ``) before and after it. For example, `class` is not a valid identifier, but `` `class` `` is valid. The backticks are not considered part of the identifier; `` `x` `` and `x` have the same meaning.

Inside a closure with no explicit parameter names, the parameters are implicitly named `$0`, `$1`, `$2`, and so on. These names are valid identifiers within the scope of the closure.

Grammar of an identifier

<span class="syntax-def-name">
identifier

<span class="arrow">
→
<span class="syntactic-cat">[identifier-head](LexicalStructure.md#identifier-head)<span class="optional"><span class="syntactic-cat">[identifier-characters](LexicalStructure.md#identifier-characters)~opt~

<span class="syntax-def-name">
identifier

<span class="arrow">
→
`` ` ``<span class="syntactic-cat">[identifier-head](LexicalStructure.md#identifier-head)<span class="optional"><span class="syntactic-cat">[identifier-characters](LexicalStructure.md#identifier-characters)~opt~`` ` ``

<span class="syntax-def-name">
identifier

<span class="arrow">
→
<span class="syntactic-cat">[implicit-parameter-name](LexicalStructure.md#implicit-parameter-name)

<span class="syntax-def-name">
identifier-list

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)
<span class="alternative">
<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)`,`<span class="syntactic-cat">[identifier-list](LexicalStructure.md#identifier-list)

<span class="syntax-def-name">
identifier-head

<span class="arrow">
→
<span class="text-description">Upper- or lowercase letter A through Z

<span class="syntax-def-name">
identifier-head

<span class="arrow">
→
`_`

<span class="syntax-def-name">
identifier-head

<span class="arrow">
→
<span class="text-description">U+00A8, U+00AA, U+00AD, U+00AF, U+00B2–U+00B5, or U+00B7–U+00BA

<span class="syntax-def-name">
identifier-head

<span class="arrow">
→
<span class="text-description">U+00BC–U+00BE, U+00C0–U+00D6, U+00D8–U+00F6, or U+00F8–U+00FF

<span class="syntax-def-name">
identifier-head

<span class="arrow">
→
<span class="text-description">U+0100–U+02FF, U+0370–U+167F, U+1681–U+180D, or U+180F–U+1DBF

<span class="syntax-def-name">
identifier-head

<span class="arrow">
→
<span class="text-description">U+1E00–U+1FFF

<span class="syntax-def-name">
identifier-head

<span class="arrow">
→
<span class="text-description">U+200B–U+200D, U+202A–U+202E, U+203F–U+2040, U+2054, or U+2060–U+206F

<span class="syntax-def-name">
identifier-head

<span class="arrow">
→
<span class="text-description">U+2070–U+20CF, U+2100–U+218F, U+2460–U+24FF, or U+2776–U+2793

<span class="syntax-def-name">
identifier-head

<span class="arrow">
→
<span class="text-description">U+2C00–U+2DFF or U+2E80–U+2FFF

<span class="syntax-def-name">
identifier-head

<span class="arrow">
→
<span class="text-description">U+3004–U+3007, U+3021–U+302F, U+3031–U+303F, or U+3040–U+D7FF

<span class="syntax-def-name">
identifier-head

<span class="arrow">
→
<span class="text-description">U+F900–U+FD3D, U+FD40–U+FDCF, U+FDF0–U+FE1F, or U+FE30–U+FE44

<span class="syntax-def-name">
identifier-head

<span class="arrow">
→
<span class="text-description">U+FE47–U+FFFD

<span class="syntax-def-name">
identifier-head

<span class="arrow">
→
<span class="text-description">U+10000–U+1FFFD, U+20000–U+2FFFD, U+30000–U+3FFFD, or U+40000–U+4FFFD

<span class="syntax-def-name">
identifier-head

<span class="arrow">
→
<span class="text-description">U+50000–U+5FFFD, U+60000–U+6FFFD, U+70000–U+7FFFD, or U+80000–U+8FFFD

<span class="syntax-def-name">
identifier-head

<span class="arrow">
→
<span class="text-description">U+90000–U+9FFFD, U+A0000–U+AFFFD, U+B0000–U+BFFFD, or U+C0000–U+CFFFD

<span class="syntax-def-name">
identifier-head

<span class="arrow">
→
<span class="text-description">U+D0000–U+DFFFD or U+E0000–U+EFFFD

<span class="syntax-def-name">
identifier-character

<span class="arrow">
→
<span class="text-description">Digit 0 through 9

<span class="syntax-def-name">
identifier-character

<span class="arrow">
→
<span class="text-description">U+0300–U+036F, U+1DC0–U+1DFF, U+20D0–U+20FF, or U+FE20–U+FE2F

<span class="syntax-def-name">
identifier-character

<span class="arrow">
→
<span class="syntactic-cat">[identifier-head](LexicalStructure.md#identifier-head)

<span class="syntax-def-name">
identifier-characters

<span class="arrow">
→
<span class="syntactic-cat">[identifier-character](LexicalStructure.md#identifier-character)<span class="optional"><span class="syntactic-cat">[identifier-characters](LexicalStructure.md#identifier-characters)~opt~

<span class="syntax-def-name">
implicit-parameter-name

<span class="arrow">
→
`$`<span class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)

### Keywords and Punctuation

The following keywords are reserved and can’t be used as identifiers, unless they’re escaped with backticks, as described above in [Identifiers](LexicalStructure.md#TP40016643-CH30-ID412).

-   Keywords used in declarations: `class`, `deinit`, `enum`, `extension`, `func`, `import`, `init`, `inout`, `internal`, `let`, `operator`, `private`, `protocol`, `public`, `static`, `struct`, `subscript`, `typealias`, and `var`.

-   Keywords used in statements: `break`, `case`, `continue`, `default`, `defer`, `do`, `else`, `fallthrough`, `for`, `guard`, `if`, `in`, `repeat`, `return`, `switch`, `where`, and `while`.

-   Keywords used in expressions and types: `as`, `catch`, `dynamicType`, `false`, `is`, `nil`, `rethrows`, `super`, `self`, `Self`, `throw`, `throws`, `true`, `try`, `__COLUMN__`, `__FILE__`, `__FUNCTION__`, and `__LINE__`.

-   Keywords used in patterns: `_`.

<!-- -->

-   Keywords reserved in particular contexts: `associativity`, `convenience`, `dynamic`, `didSet`, `final`, `get`, `infix`, `indirect`, `lazy`, `left`, `mutating`, `none`, `nonmutating`, `optional`, `override`, `postfix`, `precedence`, `prefix`, `Protocol`, `required`, `right`, `set`, `Type`, `unowned`, `weak`, and `willSet`. Outside the context in which they appear in the grammar, they can be used as identifiers.

The following tokens are reserved as punctuation and can’t be used as custom operators: `(`, `)`, `{`, `}`, `[`, `]`, `.`, `,`, `:`, `;`, `=`, `@`, `#`, `&` (as a prefix operator), `->`, `` ` ``, `?`, and `!` (as a postfix operator).

### Literals

A *literal* is the source code representation of a value of a type, such as a number or string.

The following are examples of literals:

    42 // Integer literal
    3.14159 // Floating-point literal
    "Hello, world!" // String literal
    true // Boolean literal

A literal doesn’t have a type on its own. Instead, a literal is parsed as having infinite precision and Swift’s type inference attempts to infer a type for the literal. For example, in the declaration `let x: Int8 = 42`, Swift uses the explicit type annotation (`: Int8`) to infer that the type of the integer literal `42` is `Int8`. If there isn’t suitable type information available, Swift infers that the literal’s type is one of the default literal types defined in the Swift standard library. The default types are `Int` for integer literals, `Double` for floating-point literals, `String` for string literals, and `Bool` for Boolean literals. For example, in the declaration `let str = "Hello, world"`, the default inferred type of the string literal `"Hello, world"` is `String`.

When specifying the type annotation for a literal value, the annotation’s type must be a type that can be instantiated from that literal value. That is, the type must conform to one of the following Swift standard library protocols: `IntegerLiteralConvertible` for integer literals, `FloatingPointLiteralConvertible` for floating-point literals, `StringLiteralConvertible` for string literals, and `BooleanLiteralConvertible` for Boolean literals. For example, `Int8` conforms to the `IntegerLiteralConvertible` protocol, and therefore it can be used in the type annotation for the integer literal `42` in the declaration `let x: Int8 = 42`.

Grammar of a literal

<span class="syntax-def-name">
literal

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[numeric-literal](LexicalStructure.md#numeric-literal)
<span class="alternative">
<span class="syntactic-cat">[string-literal](LexicalStructure.md#string-literal)
<span class="alternative">
<span class="syntactic-cat">[boolean-literal](LexicalStructure.md#boolean-literal)
<span class="alternative">
<span class="syntactic-cat">[nil-literal](LexicalStructure.md#nil-literal)

<span class="syntax-def-name">
numeric-literal

<span class="arrow">
→
<span class="alternative">
<span class="optional">`-`~opt~<span class="syntactic-cat">[integer-literal](LexicalStructure.md#integer-literal)
<span class="alternative">
<span class="optional">`-`~opt~<span class="syntactic-cat">[floating-point-literal](LexicalStructure.md#floating-point-literal)

<span class="syntax-def-name">
boolean-literal

<span class="arrow">
→
<span class="alternative">
`true`
<span class="alternative">
`false`

<span class="syntax-def-name">
nil-literal

<span class="arrow">
→
`nil`

### Integer Literals

*Integer literals* represent integer values of unspecified precision. By default, integer literals are expressed in decimal; you can specify an alternate base using a prefix. Binary literals begin with `0b`, octal literals begin with `0o`, and hexadecimal literals begin with `0x`.

Decimal literals contain the digits `0` through `9`. Binary literals contain `0` and `1`, octal literals contain `0` through `7`, and hexadecimal literals contain `0` through `9` as well as `A` through `F` in upper- or lowercase.

Negative integers literals are expressed by prepending a minus sign (`-`) to an integer literal, as in `-42`.

Underscores (`_`) are allowed between digits for readability, but they are ignored and therefore don’t affect the value of the literal. Integer literals can begin with leading zeros (`0`), but they are likewise ignored and don’t affect the base or value of the literal.

Unless otherwise specified, the default inferred type of an integer literal is the Swift standard library type `Int`. The Swift standard library also defines types for various sizes of signed and unsigned integers, as described in [Integers](TheBasics.md#TP40016643-CH5-ID317).

Grammar of an integer literal

<span class="syntax-def-name">
integer-literal

<span class="arrow">
→
<span class="syntactic-cat">[binary-literal](LexicalStructure.md#binary-literal)

<span class="syntax-def-name">
integer-literal

<span class="arrow">
→
<span class="syntactic-cat">[octal-literal](LexicalStructure.md#octal-literal)

<span class="syntax-def-name">
integer-literal

<span class="arrow">
→
<span class="syntactic-cat">[decimal-literal](LexicalStructure.md#decimal-literal)

<span class="syntax-def-name">
integer-literal

<span class="arrow">
→
<span class="syntactic-cat">[hexadecimal-literal](LexicalStructure.md#hexadecimal-literal)

<span class="syntax-def-name">
binary-literal

<span class="arrow">
→
`0b`<span class="syntactic-cat">[binary-digit](LexicalStructure.md#binary-digit)<span class="optional"><span class="syntactic-cat">[binary-literal-characters](LexicalStructure.md#binary-literal-characters)~opt~

<span class="syntax-def-name">
binary-digit

<span class="arrow">
→
<span class="text-description">Digit 0 or 1

<span class="syntax-def-name">
binary-literal-character

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[binary-digit](LexicalStructure.md#binary-digit)
<span class="alternative">
`_`

<span class="syntax-def-name">
binary-literal-characters

<span class="arrow">
→
<span class="syntactic-cat">[binary-literal-character](LexicalStructure.md#binary-literal-character)<span class="optional"><span class="syntactic-cat">[binary-literal-characters](LexicalStructure.md#binary-literal-characters)~opt~

<span class="syntax-def-name">
octal-literal

<span class="arrow">
→
`0o`<span class="syntactic-cat">[octal-digit](LexicalStructure.md#octal-digit)<span class="optional"><span class="syntactic-cat">[octal-literal-characters](LexicalStructure.md#octal-literal-characters)~opt~

<span class="syntax-def-name">
octal-digit

<span class="arrow">
→
<span class="text-description">Digit 0 through 7

<span class="syntax-def-name">
octal-literal-character

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[octal-digit](LexicalStructure.md#octal-digit)
<span class="alternative">
`_`

<span class="syntax-def-name">
octal-literal-characters

<span class="arrow">
→
<span class="syntactic-cat">[octal-literal-character](LexicalStructure.md#octal-literal-character)<span class="optional"><span class="syntactic-cat">[octal-literal-characters](LexicalStructure.md#octal-literal-characters)~opt~

<span class="syntax-def-name">
decimal-literal

<span class="arrow">
→
<span class="syntactic-cat">[decimal-digit](LexicalStructure.md#decimal-digit)<span class="optional"><span class="syntactic-cat">[decimal-literal-characters](LexicalStructure.md#decimal-literal-characters)~opt~

<span class="syntax-def-name">
decimal-digit

<span class="arrow">
→
<span class="text-description">Digit 0 through 9

<span class="syntax-def-name">
decimal-digits

<span class="arrow">
→
<span class="syntactic-cat">[decimal-digit](LexicalStructure.md#decimal-digit)<span class="optional"><span class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)~opt~

<span class="syntax-def-name">
decimal-literal-character

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[decimal-digit](LexicalStructure.md#decimal-digit)
<span class="alternative">
`_`

<span class="syntax-def-name">
decimal-literal-characters

<span class="arrow">
→
<span class="syntactic-cat">[decimal-literal-character](LexicalStructure.md#decimal-literal-character)<span class="optional"><span class="syntactic-cat">[decimal-literal-characters](LexicalStructure.md#decimal-literal-characters)~opt~

<span class="syntax-def-name">
hexadecimal-literal

<span class="arrow">
→
`0x`<span class="syntactic-cat">[hexadecimal-digit](LexicalStructure.md#hexadecimal-digit)<span class="optional"><span class="syntactic-cat">[hexadecimal-literal-characters](LexicalStructure.md#hexadecimal-literal-characters)~opt~

<span class="syntax-def-name">
hexadecimal-digit

<span class="arrow">
→
<span class="text-description">Digit 0 through 9, a through f, or A through F

<span class="syntax-def-name">
hexadecimal-literal-character

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[hexadecimal-digit](LexicalStructure.md#hexadecimal-digit)
<span class="alternative">
`_`

<span class="syntax-def-name">
hexadecimal-literal-characters

<span class="arrow">
→
<span class="syntactic-cat">[hexadecimal-literal-character](LexicalStructure.md#hexadecimal-literal-character)<span class="optional"><span class="syntactic-cat">[hexadecimal-literal-characters](LexicalStructure.md#hexadecimal-literal-characters)~opt~

### Floating-Point Literals

*Floating-point literals* represent floating-point values of unspecified precision.

By default, floating-point literals are expressed in decimal (with no prefix), but they can also be expressed in hexadecimal (with a `0x` prefix).

Decimal floating-point literals consist of a sequence of decimal digits followed by either a decimal fraction, a decimal exponent, or both. The decimal fraction consists of a decimal point (`.`) followed by a sequence of decimal digits. The exponent consists of an upper- or lowercase `e` prefix followed by a sequence of decimal digits that indicates what power of 10 the value preceding the `e` is multiplied by. For example, `1.25e2` represents 1.25 x 10^2^, which evaluates to `125.0`. Similarly, `1.25e-2` represents 1.25 x 10^-2^, which evaluates to `0.0125`.

Hexadecimal floating-point literals consist of a `0x` prefix, followed by an optional hexadecimal fraction, followed by a hexadecimal exponent. The hexadecimal fraction consists of a decimal point followed by a sequence of hexadecimal digits. The exponent consists of an upper- or lowercase `p` prefix followed by a sequence of decimal digits that indicates what power of 2 the value preceding the `p` is multiplied by. For example, `0xFp2` represents 15 x 2^2^, which evaluates to `60`. Similarly, `0xFp-2` represents 15 x 2^-2^, which evaluates to `3.75`.

Negative floating-point literals are expressed by prepending a minus sign (`-`) to a floating-point literal, as in `-42.5`.

Underscores (`_`) are allowed between digits for readability, but are ignored and therefore don’t affect the value of the literal. Floating-point literals can begin with leading zeros (`0`), but are likewise ignored and don’t affect the base or value of the literal.

Unless otherwise specified, the default inferred type of a floating-point literal is the Swift standard library type `Double`, which represents a 64-bit floating-point number. The Swift standard library also defines a `Float` type, which represents a 32-bit floating-point number.

Grammar of a floating-point literal

<span class="syntax-def-name">
floating-point-literal

<span class="arrow">
→
<span class="syntactic-cat">[decimal-literal](LexicalStructure.md#decimal-literal)<span class="optional"><span class="syntactic-cat">[decimal-fraction](LexicalStructure.md#decimal-fraction)~opt~<span class="optional"><span class="syntactic-cat">[decimal-exponent](LexicalStructure.md#decimal-exponent)~opt~

<span class="syntax-def-name">
floating-point-literal

<span class="arrow">
→
<span class="syntactic-cat">[hexadecimal-literal](LexicalStructure.md#hexadecimal-literal)<span class="optional"><span class="syntactic-cat">[hexadecimal-fraction](LexicalStructure.md#hexadecimal-fraction)~opt~<span class="syntactic-cat">[hexadecimal-exponent](LexicalStructure.md#hexadecimal-exponent)

<span class="syntax-def-name">
decimal-fraction

<span class="arrow">
→
`.`<span class="syntactic-cat">[decimal-literal](LexicalStructure.md#decimal-literal)

<span class="syntax-def-name">
decimal-exponent

<span class="arrow">
→
<span class="syntactic-cat">[floating-point-e](LexicalStructure.md#floating-point-e)<span class="optional"><span class="syntactic-cat">[sign](LexicalStructure.md#sign)~opt~<span class="syntactic-cat">[decimal-literal](LexicalStructure.md#decimal-literal)

<span class="syntax-def-name">
hexadecimal-fraction

<span class="arrow">
→
`.`<span class="syntactic-cat">[hexadecimal-digit](LexicalStructure.md#hexadecimal-digit)<span class="optional"><span class="syntactic-cat">[hexadecimal-literal-characters](LexicalStructure.md#hexadecimal-literal-characters)~opt~

<span class="syntax-def-name">
hexadecimal-exponent

<span class="arrow">
→
<span class="syntactic-cat">[floating-point-p](LexicalStructure.md#floating-point-p)<span class="optional"><span class="syntactic-cat">[sign](LexicalStructure.md#sign)~opt~<span class="syntactic-cat">[decimal-literal](LexicalStructure.md#decimal-literal)

<span class="syntax-def-name">
floating-point-e

<span class="arrow">
→
<span class="alternative">
`e`
<span class="alternative">
`E`

<span class="syntax-def-name">
floating-point-p

<span class="arrow">
→
<span class="alternative">
`p`
<span class="alternative">
`P`

<span class="syntax-def-name">
sign

<span class="arrow">
→
<span class="alternative">
`+`
<span class="alternative">
`-`

### String Literals

A string literal is a sequence of characters surrounded by double quotes, with the following form:

-   ```
    "characters"
    ```

String literals cannot contain an unescaped double quote (`"`), an unescaped backslash (``), a carriage return, or a line feed.

Special characters can be included in string literals using the following escape sequences:

-   Null Character (`0`)

-   Backslash (`\`)

-   Horizontal Tab (`t`)

-   Line Feed (`n`)

-   Carriage Return (`r`)

-   Double Quote (`"`)

-   Single Quote (`'`)

-   Unicode scalar (`u{`*n*`}`), where *n* is between one and eight hexadecimal digits

The value of an expression can be inserted into a string literal by placing the expression in parentheses after a backslash (``). The interpolated expression can contain a string literal, but can’t contain an unescaped backslash (``), a carriage return, or a line feed.

For example, all the following string literals have the same value:

    "1 2 3"
    "1 2 \("3")"
    "1 2 \(3)"
    "1 2 \(1 + 2)"
    let x = 3; "1 2 \(x)"

The default inferred type of a string literal is `String`. For more information about the `String` type, see [Strings and Characters](StringsAndCharacters.md) and *String Structure Reference*.

String literals that are concatenated by the `+` operator are concatenated at compile time. For example, the values of `textA` and `textB` in the example below are identical—no runtime concatenation is performed.

    let textA = "Hello " + "world"
    let textB = "Hello world"

Grammar of a string literal

<span class="syntax-def-name">
string-literal

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[static-string-literal](LexicalStructure.md#static-string-literal)
<span class="alternative">
<span class="syntactic-cat">[interpolated-string-literal](LexicalStructure.md#interpolated-string-literal)

<span class="syntax-def-name">
static-string-literal

<span class="arrow">
→
`"`<span class="optional"><span class="syntactic-cat">[quoted-text](LexicalStructure.md#quoted-text)~opt~`"`

<span class="syntax-def-name">
quoted-text

<span class="arrow">
→
<span class="syntactic-cat">[quoted-text-item](LexicalStructure.md#quoted-text-item)<span class="optional"><span class="syntactic-cat">[quoted-text](LexicalStructure.md#quoted-text)~opt~

<span class="syntax-def-name">
quoted-text-item

<span class="arrow">
→
<span class="syntactic-cat">[escaped-character](LexicalStructure.md#escaped-character)

<span class="syntax-def-name">
quoted-text-item

<span class="arrow">
→
<span class="text-description">Any Unicode scalar value except `"`, ``, U+000A, or U+000D

<span class="syntax-def-name">
interpolated-string-literal

<span class="arrow">
→
`"`<span class="optional"><span class="syntactic-cat">[interpolated-text](LexicalStructure.md#interpolated-text)~opt~`"`

<span class="syntax-def-name">
interpolated-text

<span class="arrow">
→
<span class="syntactic-cat">[interpolated-text-item](LexicalStructure.md#interpolated-text-item)<span class="optional"><span class="syntactic-cat">[interpolated-text](LexicalStructure.md#interpolated-text)~opt~

<span class="syntax-def-name">
interpolated-text-item

<span class="arrow">
→
<span class="alternative">
`(`<span class="syntactic-cat">[expression](Expressions.md#expression)`)`
<span class="alternative">
<span class="syntactic-cat">[quoted-text-item](LexicalStructure.md#quoted-text-item)

<span class="syntax-def-name">
escaped-character

<span class="arrow">
→
<span class="alternative">
`0`
<span class="alternative">
`\`
<span class="alternative">
`t`
<span class="alternative">
`n`
<span class="alternative">
`r`
<span class="alternative">
`"`
<span class="alternative">
`'`

<span class="syntax-def-name">
escaped-character

<span class="arrow">
→
`u``{`<span class="syntactic-cat">[unicode-scalar-digits](LexicalStructure.md#unicode-scalar-digits)`}`

<span class="syntax-def-name">
unicode-scalar-digits

<span class="arrow">
→
<span class="text-description">Between one and eight hexadecimal digits

### Operators

The Swift standard library defines a number of operators for your use, many of which are discussed in [Basic Operators](BasicOperators.md) and [Advanced Operators](AdvancedOperators.md). The present section describes which characters can be used to define custom operators.

Custom operators can begin with one of the ASCII characters `/`, `=`, `-`, `+`, `!`, `*`, `%`, `<`, `>`, `&`, `|`, `^`, `?`, or `~`, or one of the Unicode characters defined in the grammar below (which include characters from the *Mathematical Operators*, *Miscellaneous Symbols*, and *Dingbats* Unicode blocks, among others). After the first character, combining Unicode characters are also allowed. You can also define custom operators as a sequence of two or more dots (for example, `....`). Although you can define custom operators that contain a question mark character (`?`), they can’t consist of a single question mark character only.

#### Note

The tokens `=`, `->`, `//`, `/*`, `*/`, `.`, the prefix operators `<`, `&`, and `?`, the infix operator `?`, and the postfix operators `>`, `!`, and `?` are reserved. These tokens can’t be overloaded, nor can they be used as custom operators.

The whitespace around an operator is used to determine whether an operator is used as a prefix operator, a postfix operator, or a binary operator. This behavior is summarized in the following rules:

-   If an operator has whitespace around both sides or around neither side, it is treated as a binary operator. As an example, the `+` operator in `a+b` and `a + b` is treated as a binary operator.

-   If an operator has whitespace on the left side only, it is treated as a prefix unary operator. As an example, the `++` operator in `a ++b` is treated as a prefix unary operator.

-   If an operator has whitespace on the right side only, it is treated as a postfix unary operator. As an example, the `++` operator in `a++ b` is treated as a postfix unary operator.

-   If an operator has no whitespace on the left but is followed immediately by a dot (`.`), it is treated as a postfix unary operator. As an example, the `++` operator in `a++.b` is treated as a postfix unary operator (`a++ .b` rather than `a ++ .b`).

For the purposes of these rules, the characters `(`, `[`, and `{` before an operator, the characters `)`, `]`, and `}` after an operator, and the characters `,`, `;`, and `:` are also considered whitespace.

There is one caveat to the rules above. If the `!` or `?` predefined operator has no whitespace on the left, it is treated as a postfix operator, regardless of whether it has whitespace on the right. To use the `?` as the optional-chaining operator, it must not have whitespace on the left. To use it in the ternary conditional (`?` `:`) operator, it must have whitespace around both sides.

In certain constructs, operators with a leading `<` or `>` may be split into two or more tokens. The remainder is treated the same way and may be split again. As a result, there is no need to use whitespace to disambiguate between the closing `>` characters in constructs like `Dictionary<String, Array<Int>>`. In this example, the closing `>` characters are not treated as a single token that may then be misinterpreted as a bit shift `>>` operator.

To learn how to define new, custom operators, see [Custom Operators](AdvancedOperators.md#TP40016643-CH27-ID46) and [Operator Declaration](Declarations.md#TP40016643-CH34-ID380). To learn how to overload existing operators, see [Operator Functions](AdvancedOperators.md#TP40016643-CH27-ID42).

Grammar of operators

<span class="syntax-def-name">
operator

<span class="arrow">
→
<span class="syntactic-cat">[operator-head](LexicalStructure.md#operator-head)<span class="optional"><span class="syntactic-cat">[operator-characters](LexicalStructure.md#operator-characters)~opt~

<span class="syntax-def-name">
operator

<span class="arrow">
→
<span class="syntactic-cat">[dot-operator-head](LexicalStructure.md#dot-operator-head)<span class="optional"><span class="syntactic-cat">[dot-operator-characters](LexicalStructure.md#dot-operator-characters)~opt~

<span class="syntax-def-name">
operator-head

<span class="arrow">
→
<span class="alternative">
`/`
<span class="alternative">
`=`
<span class="alternative">
`-`
<span class="alternative">
`+`
<span class="alternative">
`!`
<span class="alternative">
`*`
<span class="alternative">
`%`
<span class="alternative">
`<`
<span class="alternative">
`>`
<span class="alternative">
`&`
<span class="alternative">
`|`
<span class="alternative">
`^`
<span class="alternative">
`~`
<span class="alternative">
`?`

<span class="syntax-def-name">
operator-head

<span class="arrow">
→
<span class="text-description">U+00A1–U+00A7

<span class="syntax-def-name">
operator-head

<span class="arrow">
→
<span class="text-description">U+00A9 or U+00AB

<span class="syntax-def-name">
operator-head

<span class="arrow">
→
<span class="text-description">U+00AC or U+00AE

<span class="syntax-def-name">
operator-head

<span class="arrow">
→
<span class="text-description">U+00B0–U+00B1, U+00B6, U+00BB, U+00BF, U+00D7, or U+00F7

<span class="syntax-def-name">
operator-head

<span class="arrow">
→
<span class="text-description">U+2016–U+2017 or U+2020–U+2027

<span class="syntax-def-name">
operator-head

<span class="arrow">
→
<span class="text-description">U+2030–U+203E

<span class="syntax-def-name">
operator-head

<span class="arrow">
→
<span class="text-description">U+2041–U+2053

<span class="syntax-def-name">
operator-head

<span class="arrow">
→
<span class="text-description">U+2055–U+205E

<span class="syntax-def-name">
operator-head

<span class="arrow">
→
<span class="text-description">U+2190–U+23FF

<span class="syntax-def-name">
operator-head

<span class="arrow">
→
<span class="text-description">U+2500–U+2775

<span class="syntax-def-name">
operator-head

<span class="arrow">
→
<span class="text-description">U+2794–U+2BFF

<span class="syntax-def-name">
operator-head

<span class="arrow">
→
<span class="text-description">U+2E00–U+2E7F

<span class="syntax-def-name">
operator-head

<span class="arrow">
→
<span class="text-description">U+3001–U+3003

<span class="syntax-def-name">
operator-head

<span class="arrow">
→
<span class="text-description">U+3008–U+3030

<span class="syntax-def-name">
operator-character

<span class="arrow">
→
<span class="syntactic-cat">[operator-head](LexicalStructure.md#operator-head)

<span class="syntax-def-name">
operator-character

<span class="arrow">
→
<span class="text-description">U+0300–U+036F

<span class="syntax-def-name">
operator-character

<span class="arrow">
→
<span class="text-description">U+1DC0–U+1DFF

<span class="syntax-def-name">
operator-character

<span class="arrow">
→
<span class="text-description">U+20D0–U+20FF

<span class="syntax-def-name">
operator-character

<span class="arrow">
→
<span class="text-description">U+FE00–U+FE0F

<span class="syntax-def-name">
operator-character

<span class="arrow">
→
<span class="text-description">U+FE20–U+FE2F

<span class="syntax-def-name">
operator-character

<span class="arrow">
→
<span class="text-description">U+E0100–U+E01EF

<span class="syntax-def-name">
operator-characters

<span class="arrow">
→
<span class="syntactic-cat">[operator-character](LexicalStructure.md#operator-character)<span class="optional"><span class="syntactic-cat">[operator-characters](LexicalStructure.md#operator-characters)~opt~

<span class="syntax-def-name">
dot-operator-head

<span class="arrow">
→
`..`

<span class="syntax-def-name">
dot-operator-character

<span class="arrow">
→
<span class="alternative">
`.`
<span class="alternative">
<span class="syntactic-cat">[operator-character](LexicalStructure.md#operator-character)

<span class="syntax-def-name">
dot-operator-characters

<span class="arrow">
→
<span class="syntactic-cat">[dot-operator-character](LexicalStructure.md#dot-operator-character)<span class="optional"><span class="syntactic-cat">[dot-operator-characters](LexicalStructure.md#dot-operator-characters)~opt~

<span class="syntax-def-name">
binary-operator

<span class="arrow">
→
<span class="syntactic-cat">[operator](LexicalStructure.md#operator)

<span class="syntax-def-name">
prefix-operator

<span class="arrow">
→
<span class="syntactic-cat">[operator](LexicalStructure.md#operator)

<span class="syntax-def-name">
postfix-operator

<span class="arrow">
→
<span class="syntactic-cat">[operator](LexicalStructure.md#operator)

