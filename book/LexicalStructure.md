



[‌](){#TP40016643-CH30}[‌](){#TP40016643-CH30-ID410}
Lexical Structure {#lexical-structure .chapter-name}
-----------------



The *lexical structure* of Swift describes what sequence of characters form valid tokens of the language. These valid tokens form the lowest-level building blocks of the language and are used to describe the rest of the language in subsequent chapters. A token consists of an identifier, keyword, punctuation, literal, or operator.

In most cases, tokens are generated from the characters of a Swift source file by considering the longest possible substring from the input text, within the constraints of the grammar that are specified below. This behavior is referred to as *longest match* or *maximal munch*.





[‌](){#TP40016643-CH30-ID411}
### Whitespace and Comments {#whitespace-and-comments .section-name}

Whitespace has two uses: to separate tokens in the source file and to help determine whether an operator is a prefix or postfix (see [Operators](LexicalStructure.md#TP40016643-CH30-ID418)), but is otherwise ignored. The following characters are considered whitespace: space (U+0020), line feed (U+000A), carriage return (U+000D), horizontal tab (U+0009), vertical tab (U+000B), form feed (U+000C) and null (U+0000).

Comments are treated as whitespace by the compiler. Single line comments begin with `//`{.code-voice} and continue until a line feed (U+000A) or carriage return (U+000D). Multiline comments begin with `/*`{.code-voice} and end with `*/`{.code-voice}. Nesting multiline comments is allowed, but the comment markers must be balanced.

Comments can contain additional formatting and markup, as described in *Markup Formatting Reference*.





[‌](){#TP40016643-CH30-ID412}
### Identifiers {#identifiers .section-name}

*Identifiers* begin with an uppercase or lowercase letter A through Z, an underscore (`_`{.code-voice}), a noncombining alphanumeric Unicode character in the Basic Multilingual Plane, or a character outside the Basic Multilingual Plane that isn’t in a Private Use Area. After the first character, digits and combining Unicode characters are also allowed.

To use a reserved word as an identifier, put a backtick (`` ` ``{.code-voice}) before and after it. For example, `class`{.code-voice} is not a valid identifier, but `` `class` ``{.code-voice} is valid. The backticks are not considered part of the identifier; `` `x` ``{.code-voice} and `x`{.code-voice} have the same meaning.

Inside a closure with no explicit parameter names, the parameters are implicitly named `$0`{.code-voice}, `$1`{.code-voice}, `$2`{.code-voice}, and so on. These names are valid identifiers within the scope of the closure.



Grammar of an identifier



[‌](){#identifier}

identifier


→
[identifier-head](LexicalStructure.md#identifier-head)[identifier-characters](LexicalStructure.md#identifier-characters)~opt~

[‌](){#TP40016643-CH30-NoLink_516}

identifier


→
`` ` ``{.literal}[identifier-head](LexicalStructure.md#identifier-head)[identifier-characters](LexicalStructure.md#identifier-characters)~opt~`` ` ``{.literal}

[‌](){#TP40016643-CH30-NoLink_517}

identifier


→
[implicit-parameter-name](LexicalStructure.md#implicit-parameter-name)

[‌](){#identifier-list}

identifier-list


→

[identifier](LexicalStructure.md#identifier)

[identifier](LexicalStructure.md#identifier)`,`{.literal}[identifier-list](LexicalStructure.md#identifier-list)






[‌](){#identifier-head}

identifier-head


→
Upper- or lowercase letter A through Z

[‌](){#TP40016643-CH30-NoLink_520}

identifier-head


→
`_`{.literal}

[‌](){#TP40016643-CH30-NoLink_521}

identifier-head


→
U+00A8, U+00AA, U+00AD, U+00AF, U+00B2–U+00B5, or U+00B7–U+00BA

[‌](){#TP40016643-CH30-NoLink_522}

identifier-head


→
U+00BC–U+00BE, U+00C0–U+00D6, U+00D8–U+00F6, or U+00F8–U+00FF

[‌](){#TP40016643-CH30-NoLink_523}

identifier-head


→
U+0100–U+02FF, U+0370–U+167F, U+1681–U+180D, or U+180F–U+1DBF

[‌](){#TP40016643-CH30-NoLink_524}

identifier-head


→
U+1E00–U+1FFF

[‌](){#TP40016643-CH30-NoLink_525}

identifier-head


→
U+200B–U+200D, U+202A–U+202E, U+203F–U+2040, U+2054, or U+2060–U+206F

[‌](){#TP40016643-CH30-NoLink_526}

identifier-head


→
U+2070–U+20CF, U+2100–U+218F, U+2460–U+24FF, or U+2776–U+2793

[‌](){#TP40016643-CH30-NoLink_527}

identifier-head


→
U+2C00–U+2DFF or U+2E80–U+2FFF

[‌](){#TP40016643-CH30-NoLink_528}

identifier-head


→
U+3004–U+3007, U+3021–U+302F, U+3031–U+303F, or U+3040–U+D7FF

[‌](){#TP40016643-CH30-NoLink_529}

identifier-head


→
U+F900–U+FD3D, U+FD40–U+FDCF, U+FDF0–U+FE1F, or U+FE30–U+FE44

[‌](){#TP40016643-CH30-NoLink_530}

identifier-head


→
U+FE47–U+FFFD

[‌](){#TP40016643-CH30-NoLink_531}

identifier-head


→
U+10000–U+1FFFD, U+20000–U+2FFFD, U+30000–U+3FFFD, or U+40000–U+4FFFD

[‌](){#TP40016643-CH30-NoLink_532}

identifier-head


→
U+50000–U+5FFFD, U+60000–U+6FFFD, U+70000–U+7FFFD, or U+80000–U+8FFFD

[‌](){#TP40016643-CH30-NoLink_533}

identifier-head


→
U+90000–U+9FFFD, U+A0000–U+AFFFD, U+B0000–U+BFFFD, or U+C0000–U+CFFFD

[‌](){#TP40016643-CH30-NoLink_534}

identifier-head


→
U+D0000–U+DFFFD or U+E0000–U+EFFFD





[‌](){#identifier-character}

identifier-character


→
Digit 0 through 9

[‌](){#TP40016643-CH30-NoLink_536}

identifier-character


→
U+0300–U+036F, U+1DC0–U+1DFF, U+20D0–U+20FF, or U+FE20–U+FE2F

[‌](){#TP40016643-CH30-NoLink_537}

identifier-character


→
[identifier-head](LexicalStructure.md#identifier-head)

[‌](){#identifier-characters}

identifier-characters


→
[identifier-character](LexicalStructure.md#identifier-character)[identifier-characters](LexicalStructure.md#identifier-characters)~opt~





[‌](){#implicit-parameter-name}

implicit-parameter-name


→
`$`{.literal}[decimal-digits](LexicalStructure.md#decimal-digits)









[‌](){#TP40016643-CH30-ID413}
### Keywords and Punctuation {#keywords-and-punctuation .section-name}

The following keywords are reserved and can’t be used as identifiers, unless they’re escaped with backticks, as described above in [Identifiers](LexicalStructure.md#TP40016643-CH30-ID412).

-   Keywords used in declarations: `class`{.code-voice}, `deinit`{.code-voice}, `enum`{.code-voice}, `extension`{.code-voice}, `func`{.code-voice}, `import`{.code-voice}, `init`{.code-voice}, `inout`{.code-voice}, `internal`{.code-voice}, `let`{.code-voice}, `operator`{.code-voice}, `private`{.code-voice}, `protocol`{.code-voice}, `public`{.code-voice}, `static`{.code-voice}, `struct`{.code-voice}, `subscript`{.code-voice}, `typealias`{.code-voice}, and `var`{.code-voice}.

-   Keywords used in statements: `break`{.code-voice}, `case`{.code-voice}, `continue`{.code-voice}, `default`{.code-voice}, `defer`{.code-voice}, `do`{.code-voice}, `else`{.code-voice}, `fallthrough`{.code-voice}, `for`{.code-voice}, `guard`{.code-voice}, `if`{.code-voice}, `in`{.code-voice}, `repeat`{.code-voice}, `return`{.code-voice}, `switch`{.code-voice}, `where`{.code-voice}, and `while`{.code-voice}.

-   Keywords used in expressions and types: `as`{.code-voice}, `catch`{.code-voice}, `dynamicType`{.code-voice}, `false`{.code-voice}, `is`{.code-voice}, `nil`{.code-voice}, `rethrows`{.code-voice}, `super`{.code-voice}, `self`{.code-voice}, `Self`{.code-voice}, `throw`{.code-voice}, `throws`{.code-voice}, `true`{.code-voice}, `try`{.code-voice}, `__COLUMN__`{.code-voice}, `__FILE__`{.code-voice}, `__FUNCTION__`{.code-voice}, and `__LINE__`{.code-voice}.

-   Keywords used in patterns: `_`{.code-voice}.



-   Keywords reserved in particular contexts: `associativity`{.code-voice}, `convenience`{.code-voice}, `dynamic`{.code-voice}, `didSet`{.code-voice}, `final`{.code-voice}, `get`{.code-voice}, `infix`{.code-voice}, `indirect`{.code-voice}, `lazy`{.code-voice}, `left`{.code-voice}, `mutating`{.code-voice}, `none`{.code-voice}, `nonmutating`{.code-voice}, `optional`{.code-voice}, `override`{.code-voice}, `postfix`{.code-voice}, `precedence`{.code-voice}, `prefix`{.code-voice}, `Protocol`{.code-voice}, `required`{.code-voice}, `right`{.code-voice}, `set`{.code-voice}, `Type`{.code-voice}, `unowned`{.code-voice}, `weak`{.code-voice}, and `willSet`{.code-voice}. Outside the context in which they appear in the grammar, they can be used as identifiers.

The following tokens are reserved as punctuation and can’t be used as custom operators: `(`{.code-voice}, `)`{.code-voice}, `{`{.code-voice}, `}`{.code-voice}, `[`{.code-voice}, `]`{.code-voice}, `.`{.code-voice}, `,`{.code-voice}, `:`{.code-voice}, `;`{.code-voice}, `=`{.code-voice}, `@`{.code-voice}, `#`{.code-voice}, `&`{.code-voice} (as a prefix operator), `->`{.code-voice}, `` ` ``{.code-voice}, `?`{.code-voice}, and `!`{.code-voice} (as a postfix operator).





[‌](){#TP40016643-CH30-ID414}
### Literals {#literals .section-name}

A *literal* is the source code representation of a value of a type, such as a number or string.

The following are examples of literals:







1.  `42`{.code-voice} `// Integer literal`{.c}
2.  `3.14159`{.code-voice} `// Floating-point literal`{.c}
3.  `"Hello, world!"`{.code-voice} `// String literal`{.c}
4.  `true`{.code-voice} `// Boolean literal`{.c}







A literal doesn’t have a type on its own. Instead, a literal is parsed as having infinite precision and Swift’s type inference attempts to infer a type for the literal. For example, in the declaration `let x: Int8 = 42`{.code-voice}, Swift uses the explicit type annotation (`: Int8`{.code-voice}) to infer that the type of the integer literal `42`{.code-voice} is `Int8`{.code-voice}. If there isn’t suitable type information available, Swift infers that the literal’s type is one of the default literal types defined in the Swift standard library. The default types are `Int`{.code-voice} for integer literals, `Double`{.code-voice} for floating-point literals, `String`{.code-voice} for string literals, and `Bool`{.code-voice} for Boolean literals. For example, in the declaration `let str = "Hello, world"`{.code-voice}, the default inferred type of the string literal `"Hello, world"`{.code-voice} is `String`{.code-voice}.

When specifying the type annotation for a literal value, the annotation’s type must be a type that can be instantiated from that literal value. That is, the type must conform to one of the following Swift standard library protocols: `IntegerLiteralConvertible`{.code-voice} for integer literals, `FloatingPointLiteralConvertible`{.code-voice} for floating-point literals, `StringLiteralConvertible`{.code-voice} for string literals, and `BooleanLiteralConvertible`{.code-voice} for Boolean literals. For example, `Int8`{.code-voice} conforms to the `IntegerLiteralConvertible`{.code-voice} protocol, and therefore it can be used in the type annotation for the integer literal `42`{.code-voice} in the declaration `let x: Int8 = 42`{.code-voice}.



Grammar of a literal



[‌](){#literal}

literal


→

[numeric-literal](LexicalStructure.md#numeric-literal)

[string-literal](LexicalStructure.md#string-literal)

[boolean-literal](LexicalStructure.md#boolean-literal)

[nil-literal](LexicalStructure.md#nil-literal)






[‌](){#numeric-literal}

numeric-literal


→

`-`{.literal}~opt~[integer-literal](LexicalStructure.md#integer-literal)

`-`{.literal}~opt~[floating-point-literal](LexicalStructure.md#floating-point-literal)


[‌](){#boolean-literal}

boolean-literal


→

`true`{.literal}

`false`{.literal}


[‌](){#nil-literal}

nil-literal


→
`nil`{.literal}







[‌](){#TP40016643-CH30-ID415}
### Integer Literals {#integer-literals .section-name}

*Integer literals* represent integer values of unspecified precision. By default, integer literals are expressed in decimal; you can specify an alternate base using a prefix. Binary literals begin with `0b`{.code-voice}, octal literals begin with `0o`{.code-voice}, and hexadecimal literals begin with `0x`{.code-voice}.

Decimal literals contain the digits `0`{.code-voice} through `9`{.code-voice}. Binary literals contain `0`{.code-voice} and `1`{.code-voice}, octal literals contain `0`{.code-voice} through `7`{.code-voice}, and hexadecimal literals contain `0`{.code-voice} through `9`{.code-voice} as well as `A`{.code-voice} through `F`{.code-voice} in upper- or lowercase.

Negative integers literals are expressed by prepending a minus sign (`-`{.code-voice}) to an integer literal, as in `-42`{.code-voice}.

Underscores (`_`{.code-voice}) are allowed between digits for readability, but they are ignored and therefore don’t affect the value of the literal. Integer literals can begin with leading zeros (`0`{.code-voice}), but they are likewise ignored and don’t affect the base or value of the literal.

Unless otherwise specified, the default inferred type of an integer literal is the Swift standard library type `Int`{.code-voice}. The Swift standard library also defines types for various sizes of signed and unsigned integers, as described in [Integers](TheBasics.md#TP40016643-CH5-ID317).



Grammar of an integer literal



[‌](){#integer-literal}

integer-literal


→
[binary-literal](LexicalStructure.md#binary-literal)

[‌](){#TP40016643-CH30-NoLink_547}

integer-literal


→
[octal-literal](LexicalStructure.md#octal-literal)

[‌](){#TP40016643-CH30-NoLink_548}

integer-literal


→
[decimal-literal](LexicalStructure.md#decimal-literal)

[‌](){#TP40016643-CH30-NoLink_549}

integer-literal


→
[hexadecimal-literal](LexicalStructure.md#hexadecimal-literal)





[‌](){#binary-literal}

binary-literal


→
`0b`{.literal}[binary-digit](LexicalStructure.md#binary-digit)[binary-literal-characters](LexicalStructure.md#binary-literal-characters)~opt~

[‌](){#binary-digit}

binary-digit


→
Digit 0 or 1

[‌](){#binary-literal-character}

binary-literal-character


→

[binary-digit](LexicalStructure.md#binary-digit)

`_`{.literal}


[‌](){#binary-literal-characters}

binary-literal-characters


→
[binary-literal-character](LexicalStructure.md#binary-literal-character)[binary-literal-characters](LexicalStructure.md#binary-literal-characters)~opt~





[‌](){#octal-literal}

octal-literal


→
`0o`{.literal}[octal-digit](LexicalStructure.md#octal-digit)[octal-literal-characters](LexicalStructure.md#octal-literal-characters)~opt~

[‌](){#octal-digit}

octal-digit


→
Digit 0 through 7

[‌](){#octal-literal-character}

octal-literal-character


→

[octal-digit](LexicalStructure.md#octal-digit)

`_`{.literal}


[‌](){#octal-literal-characters}

octal-literal-characters


→
[octal-literal-character](LexicalStructure.md#octal-literal-character)[octal-literal-characters](LexicalStructure.md#octal-literal-characters)~opt~





[‌](){#decimal-literal}

decimal-literal


→
[decimal-digit](LexicalStructure.md#decimal-digit)[decimal-literal-characters](LexicalStructure.md#decimal-literal-characters)~opt~

[‌](){#decimal-digit}

decimal-digit


→
Digit 0 through 9

[‌](){#decimal-digits}

decimal-digits


→
[decimal-digit](LexicalStructure.md#decimal-digit)[decimal-digits](LexicalStructure.md#decimal-digits)~opt~

[‌](){#decimal-literal-character}

decimal-literal-character


→

[decimal-digit](LexicalStructure.md#decimal-digit)

`_`{.literal}


[‌](){#decimal-literal-characters}

decimal-literal-characters


→
[decimal-literal-character](LexicalStructure.md#decimal-literal-character)[decimal-literal-characters](LexicalStructure.md#decimal-literal-characters)~opt~





[‌](){#hexadecimal-literal}

hexadecimal-literal


→
`0x`{.literal}[hexadecimal-digit](LexicalStructure.md#hexadecimal-digit)[hexadecimal-literal-characters](LexicalStructure.md#hexadecimal-literal-characters)~opt~

[‌](){#hexadecimal-digit}

hexadecimal-digit


→
Digit 0 through 9, a through f, or A through F

[‌](){#hexadecimal-literal-character}

hexadecimal-literal-character


→

[hexadecimal-digit](LexicalStructure.md#hexadecimal-digit)

`_`{.literal}


[‌](){#hexadecimal-literal-characters}

hexadecimal-literal-characters


→
[hexadecimal-literal-character](LexicalStructure.md#hexadecimal-literal-character)[hexadecimal-literal-characters](LexicalStructure.md#hexadecimal-literal-characters)~opt~









[‌](){#TP40016643-CH30-ID416}
### Floating-Point Literals {#floating-point-literals .section-name}

*Floating-point literals* represent floating-point values of unspecified precision.

By default, floating-point literals are expressed in decimal (with no prefix), but they can also be expressed in hexadecimal (with a `0x`{.code-voice} prefix).

Decimal floating-point literals consist of a sequence of decimal digits followed by either a decimal fraction, a decimal exponent, or both. The decimal fraction consists of a decimal point (`.`{.code-voice}) followed by a sequence of decimal digits. The exponent consists of an upper- or lowercase `e`{.code-voice} prefix followed by a sequence of decimal digits that indicates what power of 10 the value preceding the `e`{.code-voice} is multiplied by. For example, `1.25e2`{.code-voice} represents 1.25 x 10^2^, which evaluates to `125.0`{.code-voice}. Similarly, `1.25e-2`{.code-voice} represents 1.25 x 10^-2^, which evaluates to `0.0125`{.code-voice}.

Hexadecimal floating-point literals consist of a `0x`{.code-voice} prefix, followed by an optional hexadecimal fraction, followed by a hexadecimal exponent. The hexadecimal fraction consists of a decimal point followed by a sequence of hexadecimal digits. The exponent consists of an upper- or lowercase `p`{.code-voice} prefix followed by a sequence of decimal digits that indicates what power of 2 the value preceding the `p`{.code-voice} is multiplied by. For example, `0xFp2`{.code-voice} represents 15 x 2^2^, which evaluates to `60`{.code-voice}. Similarly, `0xFp-2`{.code-voice} represents 15 x 2^-2^, which evaluates to `3.75`{.code-voice}.

Negative floating-point literals are expressed by prepending a minus sign (`-`{.code-voice}) to a floating-point literal, as in `-42.5`{.code-voice}.

Underscores (`_`{.code-voice}) are allowed between digits for readability, but are ignored and therefore don’t affect the value of the literal. Floating-point literals can begin with leading zeros (`0`{.code-voice}), but are likewise ignored and don’t affect the base or value of the literal.

Unless otherwise specified, the default inferred type of a floating-point literal is the Swift standard library type `Double`{.code-voice}, which represents a 64-bit floating-point number. The Swift standard library also defines a `Float`{.code-voice} type, which represents a 32-bit floating-point number.



Grammar of a floating-point literal



[‌](){#floating-point-literal}

floating-point-literal


→
[decimal-literal](LexicalStructure.md#decimal-literal)[decimal-fraction](LexicalStructure.md#decimal-fraction)~opt~[decimal-exponent](LexicalStructure.md#decimal-exponent)~opt~

[‌](){#TP40016643-CH30-NoLink_569}

floating-point-literal


→
[hexadecimal-literal](LexicalStructure.md#hexadecimal-literal)[hexadecimal-fraction](LexicalStructure.md#hexadecimal-fraction)~opt~[hexadecimal-exponent](LexicalStructure.md#hexadecimal-exponent)





[‌](){#decimal-fraction}

decimal-fraction


→
`.`{.literal}[decimal-literal](LexicalStructure.md#decimal-literal)

[‌](){#decimal-exponent}

decimal-exponent


→
[floating-point-e](LexicalStructure.md#floating-point-e)[sign](LexicalStructure.md#sign)~opt~[decimal-literal](LexicalStructure.md#decimal-literal)





[‌](){#hexadecimal-fraction}

hexadecimal-fraction


→
`.`{.literal}[hexadecimal-digit](LexicalStructure.md#hexadecimal-digit)[hexadecimal-literal-characters](LexicalStructure.md#hexadecimal-literal-characters)~opt~

[‌](){#hexadecimal-exponent}

hexadecimal-exponent


→
[floating-point-p](LexicalStructure.md#floating-point-p)[sign](LexicalStructure.md#sign)~opt~[decimal-literal](LexicalStructure.md#decimal-literal)





[‌](){#floating-point-e}

floating-point-e


→

`e`{.literal}

`E`{.literal}


[‌](){#floating-point-p}

floating-point-p


→

`p`{.literal}

`P`{.literal}


[‌](){#sign}

sign


→

`+`{.literal}

`-`{.literal}










[‌](){#TP40016643-CH30-ID417}
### String Literals {#string-literals .section-name}

A string literal is a sequence of characters surrounded by double quotes, with the following form:




-   ``` {.code-voice}
    "characters"
    ```



String literals cannot contain an unescaped double quote (`"`{.code-voice}), an unescaped backslash (`\`{.code-voice}), a carriage return, or a line feed.

Special characters can be included in string literals using the following escape sequences:

-   Null Character (`\0`{.code-voice})

-   Backslash (`\\`{.code-voice})

-   Horizontal Tab (`\t`{.code-voice})

-   Line Feed (`\n`{.code-voice})

-   Carriage Return (`\r`{.code-voice})

-   Double Quote (`\"`{.code-voice})

-   Single Quote (`\'`{.code-voice})

-   Unicode scalar (`\u{`{.code-voice}*n*`}`{.code-voice}), where *n* is between one and eight hexadecimal digits

The value of an expression can be inserted into a string literal by placing the expression in parentheses after a backslash (`\`{.code-voice}). The interpolated expression can contain a string literal, but can’t contain an unescaped backslash (`\`{.code-voice}), a carriage return, or a line feed.

For example, all the following string literals have the same value:







1.  `"1 2 3"`{.code-voice}
2.  `"1 2 `{.code-voice}\\(`"3"`{.s})`"`{.s}
3.  `"1 2 `{.code-voice}\\(`3`{.m})`"`{.s}
4.  `"1 2 `{.code-voice}\\(`1`{.m} + `2`{.m})`"`{.s}
5.  `let`{.code-voice} `x`{.vc} = `3`{.m}; `"1 2 `{.s}\\(`x`{.vc})`"`{.s}







The default inferred type of a string literal is `String`{.code-voice}. For more information about the `String`{.code-voice} type, see [Strings and Characters](StringsAndCharacters.md) and *String Structure Reference*.

String literals that are concatenated by the `+`{.code-voice} operator are concatenated at compile time. For example, the values of `textA`{.code-voice} and `textB`{.code-voice} in the example below are identical—no runtime concatenation is performed.







1.  `let`{.code-voice} `textA`{.vc} = `"Hello "`{.s} + `"world"`{.s}
2.  `let`{.code-voice} `textB`{.vc} = `"Hello world"`{.s}









Grammar of a string literal



[‌](){#string-literal}

string-literal


→

[static-string-literal](LexicalStructure.md#static-string-literal)

[interpolated-string-literal](LexicalStructure.md#interpolated-string-literal)






[‌](){#static-string-literal}

static-string-literal


→
`"`{.literal}[quoted-text](LexicalStructure.md#quoted-text)~opt~`"`{.literal}

[‌](){#quoted-text}

quoted-text


→
[quoted-text-item](LexicalStructure.md#quoted-text-item)[quoted-text](LexicalStructure.md#quoted-text)~opt~

[‌](){#quoted-text-item}

quoted-text-item


→
[escaped-character](LexicalStructure.md#escaped-character)

[‌](){#TP40016643-CH30-NoLink_582}

quoted-text-item


→
Any Unicode scalar value except `"`{.literal}, `\`{.literal}, U+000A, or U+000D





[‌](){#interpolated-string-literal}

interpolated-string-literal


→
`"`{.literal}[interpolated-text](LexicalStructure.md#interpolated-text)~opt~`"`{.literal}

[‌](){#interpolated-text}

interpolated-text


→
[interpolated-text-item](LexicalStructure.md#interpolated-text-item)[interpolated-text](LexicalStructure.md#interpolated-text)~opt~

[‌](){#interpolated-text-item}

interpolated-text-item


→

`\(`{.literal}[expression](Expressions.md#expression)`)`{.literal}

[quoted-text-item](LexicalStructure.md#quoted-text-item)






[‌](){#escaped-character}

escaped-character


→

`\0`{.literal}

`\\`{.literal}

`\t`{.literal}

`\n`{.literal}

`\r`{.literal}

`\"`{.literal}

`\'`{.literal}


[‌](){#TP40016643-CH30-NoLink_587}

escaped-character


→
`\u`{.literal}`{`{.literal}[unicode-scalar-digits](LexicalStructure.md#unicode-scalar-digits)`}`{.literal}

[‌](){#unicode-scalar-digits}

unicode-scalar-digits


→
Between one and eight hexadecimal digits











[‌](){#TP40016643-CH30-ID418}
### Operators {#operators .section-name}

The Swift standard library defines a number of operators for your use, many of which are discussed in [Basic Operators](BasicOperators.md) and [Advanced Operators](AdvancedOperators.md). The present section describes which characters can be used to define custom operators.

Custom operators can begin with one of the ASCII characters `/`{.code-voice}, `=`{.code-voice}, `-`{.code-voice}, `+`{.code-voice}, `!`{.code-voice}, `*`{.code-voice}, `%`{.code-voice}, ``{.code-voice}, `&`{.code-voice}, `|`{.code-voice}, `^`{.code-voice}, `?`{.code-voice}, or `~`{.code-voice}, or one of the Unicode characters defined in the grammar below (which include characters from the *Mathematical Operators*, *Miscellaneous Symbols*, and *Dingbats* Unicode blocks, among others). After the first character, combining Unicode characters are also allowed. You can also define custom operators as a sequence of two or more dots (for example, `....`{.code-voice}). Although you can define custom operators that contain a question mark character (`?`{.code-voice}), they can’t consist of a single question mark character only.



Note

The tokens `=`{.code-voice}, `->`{.code-voice}, `//`{.code-voice}, `/*`{.code-voice}, `*/`{.code-voice}, `.`{.code-voice}, the prefix operators ``{.code-voice}, `!`{.code-voice}, and `?`{.code-voice} are reserved. These tokens can’t be overloaded, nor can they be used as custom operators.



The whitespace around an operator is used to determine whether an operator is used as a prefix operator, a postfix operator, or a binary operator. This behavior is summarized in the following rules:

-   If an operator has whitespace around both sides or around neither side, it is treated as a binary operator. As an example, the `+`{.code-voice} operator in `a+b`{.code-voice} and `a + b`{.code-voice} is treated as a binary operator.

-   If an operator has whitespace on the left side only, it is treated as a prefix unary operator. As an example, the `++`{.code-voice} operator in `a ++b`{.code-voice} is treated as a prefix unary operator.

-   If an operator has whitespace on the right side only, it is treated as a postfix unary operator. As an example, the `++`{.code-voice} operator in `a++ b`{.code-voice} is treated as a postfix unary operator.

-   If an operator has no whitespace on the left but is followed immediately by a dot (`.`{.code-voice}), it is treated as a postfix unary operator. As an example, the `++`{.code-voice} operator in `a++.b`{.code-voice} is treated as a postfix unary operator (`a++ .b`{.code-voice} rather than `a ++ .b`{.code-voice}).

For the purposes of these rules, the characters `(`{.code-voice}, `[`{.code-voice}, and `{`{.code-voice} before an operator, the characters `)`{.code-voice}, `]`{.code-voice}, and `}`{.code-voice} after an operator, and the characters `,`{.code-voice}, `;`{.code-voice}, and `:`{.code-voice} are also considered whitespace.

There is one caveat to the rules above. If the `!`{.code-voice} or `?`{.code-voice} predefined operator has no whitespace on the left, it is treated as a postfix operator, regardless of whether it has whitespace on the right. To use the `?`{.code-voice} as the optional-chaining operator, it must not have whitespace on the left. To use it in the ternary conditional (`?`{.code-voice} `:`{.code-voice}) operator, it must have whitespace around both sides.

In certain constructs, operators with a leading ``{.code-voice} may be split into two or more tokens. The remainder is treated the same way and may be split again. As a result, there is no need to use whitespace to disambiguate between the closing `>`{.code-voice} characters in constructs like `Dictionary>`{.code-voice}. In this example, the closing `>`{.code-voice} characters are not treated as a single token that may then be misinterpreted as a bit shift `>>`{.code-voice} operator.

To learn how to define new, custom operators, see [Custom Operators](AdvancedOperators.md#TP40016643-CH27-ID46) and [Operator Declaration](Declarations.md#TP40016643-CH34-ID380). To learn how to overload existing operators, see [Operator Functions](AdvancedOperators.md#TP40016643-CH27-ID42).



Grammar of operators



[‌](){#operator}

operator


→
[operator-head](LexicalStructure.md#operator-head)[operator-characters](LexicalStructure.md#operator-characters)~opt~

[‌](){#TP40016643-CH30-NoLink_592}

operator


→
[dot-operator-head](LexicalStructure.md#dot-operator-head)[dot-operator-characters](LexicalStructure.md#dot-operator-characters)~opt~





[‌](){#operator-head}

operator-head


→

`/`{.literal}

`=`{.literal}

`-`{.literal}

`+`{.literal}

`!`{.literal}

`*`{.literal}

`%`{.literal}

`<`{.literal}

`>`{.literal}

`&`{.literal}

`|`{.literal}

`^`{.literal}

`~`{.literal}

`?`{.literal}


[‌](){#TP40016643-CH30-NoLink_594}

operator-head


→
U+00A1–U+00A7

[‌](){#TP40016643-CH30-NoLink_595}

operator-head


→
U+00A9 or U+00AB

[‌](){#TP40016643-CH30-NoLink_596}

operator-head


→
U+00AC or U+00AE

[‌](){#TP40016643-CH30-NoLink_597}

operator-head


→
U+00B0–U+00B1, U+00B6, U+00BB, U+00BF, U+00D7, or U+00F7

[‌](){#TP40016643-CH30-NoLink_598}

operator-head


→
U+2016–U+2017 or U+2020–U+2027

[‌](){#TP40016643-CH30-NoLink_599}

operator-head


→
U+2030–U+203E

[‌](){#TP40016643-CH30-NoLink_600}

operator-head


→
U+2041–U+2053

[‌](){#TP40016643-CH30-NoLink_601}

operator-head


→
U+2055–U+205E

[‌](){#TP40016643-CH30-NoLink_602}

operator-head


→
U+2190–U+23FF

[‌](){#TP40016643-CH30-NoLink_603}

operator-head


→
U+2500–U+2775

[‌](){#TP40016643-CH30-NoLink_604}

operator-head


→
U+2794–U+2BFF

[‌](){#TP40016643-CH30-NoLink_605}

operator-head


→
U+2E00–U+2E7F

[‌](){#TP40016643-CH30-NoLink_606}

operator-head


→
U+3001–U+3003

[‌](){#TP40016643-CH30-NoLink_607}

operator-head


→
U+3008–U+3030





[‌](){#operator-character}

operator-character


→
[operator-head](LexicalStructure.md#operator-head)

[‌](){#TP40016643-CH30-NoLink_609}

operator-character


→
U+0300–U+036F

[‌](){#TP40016643-CH30-NoLink_610}

operator-character


→
U+1DC0–U+1DFF

[‌](){#TP40016643-CH30-NoLink_611}

operator-character


→
U+20D0–U+20FF

[‌](){#TP40016643-CH30-NoLink_612}

operator-character


→
U+FE00–U+FE0F

[‌](){#TP40016643-CH30-NoLink_613}

operator-character


→
U+FE20–U+FE2F

[‌](){#TP40016643-CH30-NoLink_614}

operator-character


→
U+E0100–U+E01EF

[‌](){#operator-characters}

operator-characters


→
[operator-character](LexicalStructure.md#operator-character)[operator-characters](LexicalStructure.md#operator-characters)~opt~





[‌](){#dot-operator-head}

dot-operator-head


→
`..`{.literal}

[‌](){#dot-operator-character}

dot-operator-character


→

`.`{.literal}

[operator-character](LexicalStructure.md#operator-character)


[‌](){#dot-operator-characters}

dot-operator-characters


→
[dot-operator-character](LexicalStructure.md#dot-operator-character)[dot-operator-characters](LexicalStructure.md#dot-operator-characters)~opt~





[‌](){#binary-operator}

binary-operator


→
[operator](LexicalStructure.md#operator)

[‌](){#prefix-operator}

prefix-operator


→
[operator](LexicalStructure.md#operator)

[‌](){#postfix-operator}

postfix-operator


→
[operator](LexicalStructure.md#operator)










