<div class="content-wrapper">

<div id="chapter_container" class="conceptualwithtasks">

[‌](){#TP40016643-CH5}[‌](){#TP40016643-CH5-ID309}
The Basics {#the-basics .chapter-name}
----------

<div class="section section">

Swift is a new programming language for iOS, OS X, watchOS, and tvOS app
development. Nonetheless, many parts of Swift will be familiar from your
experience of developing in C and Objective-C.

Swift provides its own versions of all fundamental C and Objective-C
types, including `Int`{.code-voice} for integers, `Double`{.code-voice}
and `Float`{.code-voice} for floating-point values, `Bool`{.code-voice}
for Boolean values, and `String`{.code-voice} for textual data. Swift
also provides powerful versions of the three primary collection types,
`Array`{.code-voice}, `Set`{.code-voice}, and `Dictionary`{.code-voice},
as described in [Collection Types](CollectionTypes.md).

Like C, Swift uses variables to store and refer to values by an
identifying name. Swift also makes extensive use of variables whose
values cannot be changed. These are known as constants, and are much
more powerful than constants in C. Constants are used throughout Swift
to make code safer and clearer in intent when you work with values that
do not need to change.

In addition to familiar types, Swift introduces advanced types not found
in Objective-C, such as tuples. Tuples enable you to create and pass
around groupings of values. You can use a tuple to return multiple
values from a function as a single compound value.

Swift also introduces optional types, which handle the absence of a
value. Optionals say either “there *is* a value, and it equals *x*” or
“there *isn’t* a value at all”. Using optionals is similar to using
`nil`{.code-voice} with pointers in Objective-C, but they work for any
type, not just classes. Not only are optionals safer and more expressive
than `nil`{.code-voice} pointers in Objective-C, they are at the heart
of many of Swift’s most powerful features.

Swift is a *type-safe* language, which means the language helps you to
be clear about the types of values your code can work with. If part of
your code expects a `String`{.code-voice}, type safety prevents you from
passing it an `Int`{.code-voice} by mistake. Likewise, type safety
prevents you from accidentally passing an optional `String`{.code-voice}
to a piece of code that expects a nonoptional `String`{.code-voice}.
Type safety helps you catch and fix errors as early as possible in the
development process.

</div>

<div class="section section">

[‌](){#TP40016643-CH5-ID310}
### Constants and Variables {#constants-and-variables .section-name}

Constants and variables associate a name (such as
`maximumNumberOfLoginAttempts`{.code-voice} or
`welcomeMessage`{.code-voice}) with a value of a particular type (such
as the number `10`{.code-voice} or the string `"Hello"`{.code-voice}).
The value of a *constant* cannot be changed once it is set, whereas a
*variable* can be set to a different value in the future.

<div class="section section">

[‌](){#TP40016643-CH5-ID311}
### Declaring Constants and Variables {#declaring-constants-and-variables .section-name}

Constants and variables must be declared before they are used. You
declare constants with the `let`{.code-voice} keyword and variables with
the `var`{.code-voice} keyword. Here’s an example of how constants and
variables can be used to track the number of login attempts a user has
made:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `maximumNumberOfLoginAttempts`{.vc} = `10`{.m}
2.  `var`{.code-voice} `currentLoginAttempt`{.vc} = `0`{.m}

</div>

</div>

</div>

This code can be read as:

“Declare a new constant called
`maximumNumberOfLoginAttempts`{.code-voice}, and give it a value of
`10`{.code-voice}. Then, declare a new variable called
`currentLoginAttempt`{.code-voice}, and give it an initial value of
`0`{.code-voice}.”

In this example, the maximum number of allowed login attempts is
declared as a constant, because the maximum value never changes. The
current login attempt counter is declared as a variable, because this
value must be incremented after each failed login attempt.

You can declare multiple constants or multiple variables on a single
line, separated by commas:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `x`{.vc} = `0.0`{.m}, `y`{.vc} = `0.0`{.m},
    `z`{.vc} = `0.0`{.m}

</div>

</div>

</div>

<div class="note">

Note

If a stored value in your code is not going to change, always declare it
as a constant with the `let`{.code-voice} keyword. Use variables only
for storing values that need to be able to change.

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH5-ID312}
### Type Annotations {#type-annotations .section-name}

You can provide a *type annotation* when you declare a constant or
variable, to be clear about the kind of values the constant or variable
can store. Write a type annotation by placing a colon after the constant
or variable name, followed by a space, followed by the name of the type
to use.

This example provides a type annotation for a variable called
`welcomeMessage`{.code-voice}, to indicate that the variable can store
`String`{.code-voice} values:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `welcomeMessage`{.vc}: `String`{.n}

</div>

</div>

</div>

The colon in the declaration means *“…of type…,”* so the code above can
be read as:

“Declare a variable called `welcomeMessage`{.code-voice} that is of type
`String`{.code-voice}.”

The phrase “of type `String`{.code-voice}” means “can store any
`String`{.code-voice} value.” Think of it as meaning “the type of thing”
(or “the kind of thing”) that can be stored.

The `welcomeMessage`{.code-voice} variable can now be set to any string
value without error:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `welcomeMessage`{.code-voice} = `"Hello"`{.s}

</div>

</div>

</div>

You can define multiple related variables of the same type on a single
line, separated by commas, with a single type annotation after the final
variable name:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `red`{.vc}, `green`{.vc}, `blue`{.vc}:
    `Double`{.n}

</div>

</div>

</div>

<div class="note">

Note

It is rare that you need to write type annotations in practice. If you
provide an initial value for a constant or variable at the point that it
is defined, Swift can almost always infer the type to be used for that
constant or variable, as described in [Type Safety and Type
Inference](TheBasics.md#TP40016643-CH5-ID322). In the
`welcomeMessage`{.code-voice} example above, no initial value is
provided, and so the type of the `welcomeMessage`{.code-voice} variable
is specified with a type annotation rather than being inferred from an
initial value.

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH5-ID313}
### Naming Constants and Variables {#naming-constants-and-variables .section-name}

Constant and variable names can contain almost any character, including
Unicode characters:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `π`{.vc} = `3.14159`{.m}
2.  `let`{.code-voice} `你好`{.vc} = `"你好世界"`{.s}
3.  `let`{.code-voice} `🐶🐮`{.vc} = `"dogcow"`{.s}

</div>

</div>

</div>

Constant and variable names cannot contain whitespace characters,
mathematical symbols, arrows, private-use (or invalid) Unicode code
points, or line- and box-drawing characters. Nor can they begin with a
number, although numbers may be included elsewhere within the name.

Once you’ve declared a constant or variable of a certain type, you can’t
redeclare it again with the same name, or change it to store values of a
different type. Nor can you change a constant into a variable or a
variable into a constant.

<div class="note">

Note

If you need to give a constant or variable the same name as a reserved
Swift keyword, surround the keyword with back ticks
(`` ` ``{.code-voice}) when using it as a name. However, avoid using
keywords as names unless you have absolutely no choice.

</div>

You can change the value of an existing variable to another value of a
compatible type. In this example, the value of
`friendlyWelcome`{.code-voice} is changed from `"Hello!"`{.code-voice}
to `"Bonjour!"`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `friendlyWelcome`{.vc} = `"Hello!"`{.s}
2.  `friendlyWelcome`{.code-voice} = `"Bonjour!"`{.s}
3.  `// friendlyWelcome is now "Bonjour!"`{.code-voice}

</div>

</div>

</div>

Unlike a variable, the value of a constant cannot be changed once it is
set. Attempting to do so is reported as an error when your code is
compiled:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `languageName`{.vc} = `"Swift"`{.s}
2.  `languageName`{.code-voice} = `"Swift++"`{.s}
3.  `// this is a compile-time error - languageName cannot be changed`{.code-voice}

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH5-ID314}
### Printing Constants and Variables {#printing-constants-and-variables .section-name}

You can print the current value of a constant or variable with the
`print(_:separator:terminator:)`{.code-voice} function:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `print`{.code-voice}(`friendlyWelcome`{.vc})
2.  `// prints "Bonjour!"`{.code-voice}

</div>

</div>

</div>

The `print(_:separator:terminator:)`{.code-voice} function is a global
function that prints one or more values to an appropriate output. In
Xcode, for example, the `print(_:separator:terminator:)`{.code-voice}
function prints its output in Xcode’s “console” pane. The
`separator`{.code-voice} and `terminator`{.code-voice} parameter have
default values, so you can omit them when you call this function. By
default, the function terminates the line it prints by adding a line
break. To print a value without a line break after it, pass an empty
string as the terminator—for example,
`print(someValue, terminator: "")`{.code-voice}. For information about
parameters with default values, see [Default Parameter
Values](Functions.md#TP40016643-CH10-ID169).

Swift uses *string interpolation* to include the name of a constant or
variable as a placeholder in a longer string, and to prompt Swift to
replace it with the current value of that constant or variable. Wrap the
name in parentheses and escape it with a backslash before the opening
parenthesis:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `print`{.code-voice}(`"The current value of friendlyWelcome is `{.s}\\(`friendlyWelcome`{.vc})`"`{.s})
2.  `// prints "The current value of friendlyWelcome is Bonjour!"`{.code-voice}

</div>

</div>

</div>

<div class="note">

Note

All options you can use with string interpolation are described in
[String Interpolation](StringsAndCharacters.md#TP40016643-CH7-ID292).

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH5-ID315}
### Comments {#comments .section-name}

Use comments to include nonexecutable text in your code, as a note or
reminder to yourself. Comments are ignored by the Swift compiler when
your code is compiled.

Comments in Swift are very similar to comments in C. Single-line
comments begin with two forward-slashes (`//`{.code-voice}):

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `// this is a comment`{.code-voice}

</div>

</div>

</div>

Multiline comments start with a forward-slash followed by an asterisk
(`/*`{.code-voice}) and end with an asterisk followed by a forward-slash
(`*/`{.code-voice}):

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `/* this is also a comment,`{.code-voice}
2.  `but written over multiple lines */`{.code-voice}

</div>

</div>

</div>

Unlike multiline comments in C, multiline comments in Swift can be
nested inside other multiline comments. You write nested comments by
starting a multiline comment block and then starting a second multiline
comment within the first block. The second block is then closed,
followed by the first block:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `/* this is the start of the first multiline comment`{.code-voice}
2.  `/* this is the second, nested multiline comment */`{.code-voice}
3.  `this is the end of the first multiline comment */`{.code-voice}

</div>

</div>

</div>

Nested multiline comments enable you to comment out large blocks of code
quickly and easily, even if the code already contains multiline
comments.

</div>

<div class="section section">

[‌](){#TP40016643-CH5-ID316}
### Semicolons {#semicolons .section-name}

Unlike many other languages, Swift does not require you to write a
semicolon (`;`{.code-voice}) after each statement in your code, although
you can do so if you wish. However, semicolons *are* required if you
want to write multiple separate statements on a single line:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `cat`{.vc} = `"🐱"`{.s}; `print`{.vc}(`cat`{.vc})
2.  `// prints "🐱"`{.code-voice}

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH5-ID317}
### Integers {#integers .section-name}

*Integers* are whole numbers with no fractional component, such as
`42`{.code-voice} and `-23`{.code-voice}. Integers are either *signed*
(positive, zero, or negative) or *unsigned* (positive or zero).

Swift provides signed and unsigned integers in 8, 16, 32, and 64 bit
forms. These integers follow a naming convention similar to C, in that
an 8-bit unsigned integer is of type `UInt8`{.code-voice}, and a 32-bit
signed integer is of type `Int32`{.code-voice}. Like all types in Swift,
these integer types have capitalized names.

<div class="section section">

[‌](){#TP40016643-CH5-ID318}
### Integer Bounds {#integer-bounds .section-name}

You can access the minimum and maximum values of each integer type with
its `min`{.code-voice} and `max`{.code-voice} properties:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `minValue`{.vc} = `UInt8`{.vc}.`min`{.vc}
    `// minValue is equal to 0, and is of type UInt8`{.c}
2.  `let`{.code-voice} `maxValue`{.vc} = `UInt8`{.vc}.`max`{.vc}
    `// maxValue is equal to 255, and is of type UInt8`{.c}

</div>

</div>

</div>

The values of these properties are of the appropriate-sized number type
(such as `UInt8`{.code-voice} in the example above) and can therefore be
used in expressions alongside other values of the same type.

</div>

<div class="section section">

[‌](){#TP40016643-CH5-ID319}
### Int {#int .section-name}

In most cases, you don’t need to pick a specific size of integer to use
in your code. Swift provides an additional integer type,
`Int`{.code-voice}, which has the same size as the current platform’s
native word size:

-   On a 32-bit platform, `Int`{.code-voice} is the same size as
    `Int32`{.code-voice}.

-   On a 64-bit platform, `Int`{.code-voice} is the same size as
    `Int64`{.code-voice}.

Unless you need to work with a specific size of integer, always use
`Int`{.code-voice} for integer values in your code. This aids code
consistency and interoperability. Even on 32-bit platforms,
`Int`{.code-voice} can store any value between
`-2,147,483,648`{.code-voice} and `2,147,483,647`{.code-voice}, and is
large enough for many integer ranges.

</div>

<div class="section section">

[‌](){#TP40016643-CH5-ID320}
### UInt {#uint .section-name}

Swift also provides an unsigned integer type, `UInt`{.code-voice}, which
has the same size as the current platform’s native word size:

-   On a 32-bit platform, `UInt`{.code-voice} is the same size as
    `UInt32`{.code-voice}.

-   On a 64-bit platform, `UInt`{.code-voice} is the same size as
    `UInt64`{.code-voice}.

<div class="note">

Note

Use `UInt`{.code-voice} only when you specifically need an unsigned
integer type with the same size as the platform’s native word size. If
this is not the case, `Int`{.code-voice} is preferred, even when the
values to be stored are known to be non-negative. A consistent use of
`Int`{.code-voice} for integer values aids code interoperability, avoids
the need to convert between different number types, and matches integer
type inference, as described in [Type Safety and Type
Inference](TheBasics.md#TP40016643-CH5-ID322).

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH5-ID321}
### Floating-Point Numbers {#floating-point-numbers .section-name}

*Floating-point numbers* are numbers with a fractional component, such
as `3.14159`{.code-voice}, `0.1`{.code-voice}, and
`-273.15`{.code-voice}.

Floating-point types can represent a much wider range of values than
integer types, and can store numbers that are much larger or smaller
than can be stored in an `Int`{.code-voice}. Swift provides two signed
floating-point number types:

-   `Double`{.code-voice} represents a 64-bit floating-point number.

-   `Float`{.code-voice} represents a 32-bit floating-point number.

<div class="note">

Note

`Double`{.code-voice} has a precision of at least 15 decimal digits,
whereas the precision of `Float`{.code-voice} can be as little as 6
decimal digits. The appropriate floating-point type to use depends on
the nature and range of values you need to work with in your code. In
situations where either type would be appropriate, `Double`{.code-voice}
is preferred.

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH5-ID322}
### Type Safety and Type Inference {#type-safety-and-type-inference .section-name}

Swift is a *type-safe* language. A type safe language encourages you to
be clear about the types of values your code can work with. If part of
your code expects a `String`{.code-voice}, you can’t pass it an
`Int`{.code-voice} by mistake.

Because Swift is type safe, it performs *type checks* when compiling
your code and flags any mismatched types as errors. This enables you to
catch and fix errors as early as possible in the development process.

Type-checking helps you avoid errors when you’re working with different
types of values. However, this doesn’t mean that you have to specify the
type of every constant and variable that you declare. If you don’t
specify the type of value you need, Swift uses *type inference* to work
out the appropriate type. Type inference enables a compiler to deduce
the type of a particular expression automatically when it compiles your
code, simply by examining the values you provide.

Because of type inference, Swift requires far fewer type declarations
than languages such as C or Objective-C. Constants and variables are
still explicitly typed, but much of the work of specifying their type is
done for you.

Type inference is particularly useful when you declare a constant or
variable with an initial value. This is often done by assigning a
*literal value* (or *literal*) to the constant or variable at the point
that you declare it. (A literal value is a value that appears directly
in your source code, such as `42`{.code-voice} and
`3.14159`{.code-voice} in the examples below.)

For example, if you assign a literal value of `42`{.code-voice} to a new
constant without saying what type it is, Swift infers that you want the
constant to be an `Int`{.code-voice}, because you have initialized it
with a number that looks like an integer:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `meaningOfLife`{.vc} = `42`{.m}
2.  `// meaningOfLife is inferred to be of type Int`{.code-voice}

</div>

</div>

</div>

Likewise, if you don’t specify a type for a floating-point literal,
Swift infers that you want to create a `Double`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `pi`{.vc} = `3.14159`{.m}
2.  `// pi is inferred to be of type Double`{.code-voice}

</div>

</div>

</div>

Swift always chooses `Double`{.code-voice} (rather than
`Float`{.code-voice}) when inferring the type of floating-point numbers.

If you combine integer and floating-point literals in an expression, a
type of `Double`{.code-voice} will be inferred from the context:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `anotherPi`{.vc} = `3`{.m} + `0.14159`{.m}
2.  `// anotherPi is also inferred to be of type Double`{.code-voice}

</div>

</div>

</div>

The literal value of `3`{.code-voice} has no explicit type in and of
itself, and so an appropriate output type of `Double`{.code-voice} is
inferred from the presence of a floating-point literal as part of the
addition.

</div>

<div class="section section">

[‌](){#TP40016643-CH5-ID323}
### Numeric Literals {#numeric-literals .section-name}

Integer literals can be written as:

-   A *decimal* number, with no prefix

-   A *binary* number, with a `0b`{.code-voice} prefix

-   An *octal* number, with a `0o`{.code-voice} prefix

-   A *hexadecimal* number, with a `0x`{.code-voice} prefix

All of these integer literals have a decimal value of `17`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `decimalInteger`{.vc} = `17`{.m}
2.  `let`{.code-voice} `binaryInteger`{.vc} = `0b10001`{.m}
    `// 17 in binary notation`{.c}
3.  `let`{.code-voice} `octalInteger`{.vc} = `0o21`{.m}
    `// 17 in octal notation`{.c}
4.  `let`{.code-voice} `hexadecimalInteger`{.vc} = `0x11`{.m}
    `// 17 in hexadecimal notation`{.c}

</div>

</div>

</div>

Floating-point literals can be decimal (with no prefix), or hexadecimal
(with a `0x`{.code-voice} prefix). They must always have a number (or
hexadecimal number) on both sides of the decimal point. Decimal floats
can also have an optional *exponent*, indicated by an uppercase or
lowercase `e`{.code-voice}; hexadecimal floats must have an exponent,
indicated by an uppercase or lowercase `p`{.code-voice}.

For decimal numbers with an exponent of `exp`{.code-voice}, the base
number is multiplied by 10^exp^:

-   `1.25e2`{.code-voice} means 1.25 x 10^2^, or `125.0`{.code-voice}.

-   `1.25e-2`{.code-voice} means 1.25 x 10^-2^, or
    `0.0125`{.code-voice}.

For hexadecimal numbers with an exponent of `exp`{.code-voice}, the base
number is multiplied by 2^exp^:

-   `0xFp2`{.code-voice} means 15 x 2^2^, or `60.0`{.code-voice}.

-   `0xFp-2`{.code-voice} means 15 x 2^-2^, or `3.75`{.code-voice}.

All of these floating-point literals have a decimal value of
`12.1875`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `decimalDouble`{.vc} = `12.1875`{.m}
2.  `let`{.code-voice} `exponentDouble`{.vc} = `1.21875e1`{.m}
3.  `let`{.code-voice} `hexadecimalDouble`{.vc} = `0xC.3p0`{.m}

</div>

</div>

</div>

Numeric literals can contain extra formatting to make them easier to
read. Both integers and floats can be padded with extra zeros and can
contain underscores to help with readability. Neither type of formatting
affects the underlying value of the literal:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `paddedDouble`{.vc} = `000123.456`{.m}
2.  `let`{.code-voice} `oneMillion`{.vc} = `1_000_000`{.m}
3.  `let`{.code-voice} `justOverOneMillion`{.vc} =
    `1_000_000.000_000_1`{.m}

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH5-ID324}
### Numeric Type Conversion {#numeric-type-conversion .section-name}

Use the `Int`{.code-voice} type for all general-purpose integer
constants and variables in your code, even if they are known to be
non-negative. Using the default integer type in everyday situations
means that integer constants and variables are immediately interoperable
in your code and will match the inferred type for integer literal
values.

Use other integer types only when they are specifically needed for the
task at hand, because of explicitly-sized data from an external source,
or for performance, memory usage, or other necessary optimization. Using
explicitly-sized types in these situations helps to catch any accidental
value overflows and implicitly documents the nature of the data being
used.

<div class="section section">

[‌](){#TP40016643-CH5-ID325}
### Integer Conversion {#integer-conversion .section-name}

The range of numbers that can be stored in an integer constant or
variable is different for each numeric type. An `Int8`{.code-voice}
constant or variable can store numbers between `-128`{.code-voice} and
`127`{.code-voice}, whereas a `UInt8`{.code-voice} constant or variable
can store numbers between `0`{.code-voice} and `255`{.code-voice}. A
number that will not fit into a constant or variable of a sized integer
type is reported as an error when your code is compiled:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `cannotBeNegative`{.vc}: `UInt8`{.n} = -`1`{.m}
2.  `// UInt8 cannot store negative numbers, and so this will report an error`{.code-voice}
3.  `let`{.code-voice} `tooBig`{.vc}: `Int8`{.n} =
    `Int8`{.vc}.`max`{.vc} + `1`{.m}
4.  `// Int8 cannot store a number larger than its maximum value,`{.code-voice}
5.  `// and so this will also report an error`{.code-voice}

</div>

</div>

</div>

Because each numeric type can store a different range of values, you
must opt in to numeric type conversion on a case-by-case basis. This
opt-in approach prevents hidden conversion errors and helps make type
conversion intentions explicit in your code.

To convert one specific number type to another, you initialize a new
number of the desired type with the existing value. In the example
below, the constant `twoThousand`{.code-voice} is of type
`UInt16`{.code-voice}, whereas the constant `one`{.code-voice} is of
type `UInt8`{.code-voice}. They cannot be added together directly,
because they are not of the same type. Instead, this example calls
`UInt16(one)`{.code-voice} to create a new `UInt16`{.code-voice}
initialized with the value of `one`{.code-voice}, and uses this value in
place of the original:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `twoThousand`{.vc}: `UInt16`{.n} = `2_000`{.m}
2.  `let`{.code-voice} `one`{.vc}: `UInt8`{.n} = `1`{.m}
3.  `let`{.code-voice} `twoThousandAndOne`{.vc} = `twoThousand`{.vc} +
    `UInt16`{.vc}(`one`{.vc})

</div>

</div>

</div>

Because both sides of the addition are now of type
`UInt16`{.code-voice}, the addition is allowed. The output constant
(`twoThousandAndOne`{.code-voice}) is inferred to be of type
`UInt16`{.code-voice}, because it is the sum of two
`UInt16`{.code-voice} values.

`SomeType(ofInitialValue)`{.code-voice} is the default way to call the
initializer of a Swift type and pass in an initial value. Behind the
scenes, `UInt16`{.code-voice} has an initializer that accepts a
`UInt8`{.code-voice} value, and so this initializer is used to make a
new `UInt16`{.code-voice} from an existing `UInt8`{.code-voice}. You
can’t pass in *any* type here, however—it has to be a type for which
`UInt16`{.code-voice} provides an initializer. Extending existing types
to provide initializers that accept new types (including your own type
definitions) is covered in [Extensions](Extensions.md).

</div>

<div class="section section">

[‌](){#TP40016643-CH5-ID326}
### Integer and Floating-Point Conversion {#integer-and-floating-point-conversion .section-name}

Conversions between integer and floating-point numeric types must be
made explicit:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `three`{.vc} = `3`{.m}
2.  `let`{.code-voice} `pointOneFourOneFiveNine`{.vc} = `0.14159`{.m}
3.  `let`{.code-voice} `pi`{.vc} = `Double`{.vc}(`three`{.vc}) +
    `pointOneFourOneFiveNine`{.vc}
4.  `// pi equals 3.14159, and is inferred to be of type Double`{.code-voice}

</div>

</div>

</div>

Here, the value of the constant `three`{.code-voice} is used to create a
new value of type `Double`{.code-voice}, so that both sides of the
addition are of the same type. Without this conversion in place, the
addition would not be allowed.

Floating-point to integer conversion must also be made explicit. An
integer type can be initialized with a `Double`{.code-voice} or
`Float`{.code-voice} value:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `integerPi`{.vc} = `Int`{.vc}(`pi`{.vc})
2.  `// integerPi equals 3, and is inferred to be of type Int`{.code-voice}

</div>

</div>

</div>

Floating-point values are always truncated when used to initialize a new
integer value in this way. This means that `4.75`{.code-voice} becomes
`4`{.code-voice}, and `-3.9`{.code-voice} becomes `-3`{.code-voice}.

<div class="note">

Note

The rules for combining numeric constants and variables are different
from the rules for numeric literals. The literal value `3`{.code-voice}
can be added directly to the literal value `0.14159`{.code-voice},
because number literals do not have an explicit type in and of
themselves. Their type is inferred only at the point that they are
evaluated by the compiler.

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH5-ID327}
### Type Aliases {#type-aliases .section-name}

*Type aliases* define an alternative name for an existing type. You
define type aliases with the `typealias`{.code-voice} keyword.

Type aliases are useful when you want to refer to an existing type by a
name that is contextually more appropriate, such as when working with
data of a specific size from an external source:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `typealias`{.code-voice} `AudioSample`{.vc} = `UInt16`{.n}

</div>

</div>

</div>

Once you define a type alias, you can use the alias anywhere you might
use the original name:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `maxAmplitudeFound`{.vc} =
    `AudioSample`{.vc}.`min`{.vc}
2.  `// maxAmplitudeFound is now 0`{.code-voice}

</div>

</div>

</div>

Here, `AudioSample`{.code-voice} is defined as an alias for
`UInt16`{.code-voice}. Because it is an alias, the call to
`AudioSample.min`{.code-voice} actually calls `UInt16.min`{.code-voice},
which provides an initial value of `0`{.code-voice} for the
`maxAmplitudeFound`{.code-voice} variable.

</div>

<div class="section section">

[‌](){#TP40016643-CH5-ID328}
### Booleans {#booleans .section-name}

Swift has a basic *Boolean* type, called `Bool`{.code-voice}. Boolean
values are referred to as *logical*, because they can only ever be true
or false. Swift provides two Boolean constant values,
`true`{.code-voice} and `false`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `orangesAreOrange`{.vc} = `true`{.kt}
2.  `let`{.code-voice} `turnipsAreDelicious`{.vc} = `false`{.kt}

</div>

</div>

</div>

The types of `orangesAreOrange`{.code-voice} and
`turnipsAreDelicious`{.code-voice} have been inferred as
`Bool`{.code-voice} from the fact that they were initialized with
Boolean literal values. As with `Int`{.code-voice} and
`Double`{.code-voice} above, you don’t need to declare constants or
variables as `Bool`{.code-voice} if you set them to `true`{.code-voice}
or `false`{.code-voice} as soon as you create them. Type inference helps
make Swift code more concise and readable when it initializes constants
or variables with other values whose type is already known.

Boolean values are particularly useful when you work with conditional
statements such as the `if`{.code-voice} statement:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `if`{.code-voice} `turnipsAreDelicious`{.vc} {
2.  `    print`{.code-voice}(`"Mmm, tasty turnips!"`{.s})
3.  `} else`{.code-voice} {
4.  `    print`{.code-voice}(`"Eww, turnips are horrible."`{.s})
5.  `}`{.code-voice}
6.  `// prints "Eww, turnips are horrible."`{.code-voice}

</div>

</div>

</div>

Conditional statements such as the `if`{.code-voice} statement are
covered in more detail in [Control Flow](ControlFlow.md).

Swift’s type safety prevents non-Boolean values from being substituted
for `Bool`{.code-voice}. The following example reports a compile-time
error:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `i`{.vc} = `1`{.m}
2.  `if`{.code-voice} `i`{.vc} {
3.  `    // this example will not compile, and will report an error`{.code-voice}
4.  `}`{.code-voice}

</div>

</div>

</div>

However, the alternative example below is valid:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `i`{.vc} = `1`{.m}
2.  `if`{.code-voice} `i`{.vc} == `1`{.m} {
3.  `    // this example will compile successfully`{.code-voice}
4.  `}`{.code-voice}

</div>

</div>

</div>

The result of the `i == 1`{.code-voice} comparison is of type
`Bool`{.code-voice}, and so this second example passes the type-check.
Comparisons like `i == 1`{.code-voice} are discussed in [Basic
Operators](BasicOperators.md).

As with other examples of type safety in Swift, this approach avoids
accidental errors and ensures that the intention of a particular section
of code is always clear.

</div>

<div class="section section">

[‌](){#TP40016643-CH5-ID329}
### Tuples {#tuples .section-name}

*Tuples* group multiple values into a single compound value. The values
within a tuple can be of any type and do not have to be of the same type
as each other.

In this example, `(404, "Not Found")`{.code-voice} is a tuple that
describes an *HTTP status code*. An HTTP status code is a special value
returned by a web server whenever you request a web page. A status code
of `404 Not Found`{.code-voice} is returned if you request a webpage
that doesn’t exist.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `http404Error`{.vc} = (`404`{.m},
    `"Not Found"`{.s})
2.  `// http404Error is of type (Int, String), and equals (404, "Not Found")`{.code-voice}

</div>

</div>

</div>

The `(404, "Not Found")`{.code-voice} tuple groups together an
`Int`{.code-voice} and a `String`{.code-voice} to give the HTTP status
code two separate values: a number and a human-readable description. It
can be described as “a tuple of type `(Int, String)`{.code-voice}”.

You can create tuples from any permutation of types, and they can
contain as many different types as you like. There’s nothing stopping
you from having a tuple of type `(Int, Int, Int)`{.code-voice}, or
`(String, Bool)`{.code-voice}, or indeed any other permutation you
require.

You can *decompose* a tuple’s contents into separate constants or
variables, which you then access as usual:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} (`statusCode`{.vc}, `statusMessage`{.vc}) =
    `http404Error`{.vc}
2.  `print`{.code-voice}(`"The status code is `{.s}\\(`statusCode`{.vc})`"`{.s})
3.  `// prints "The status code is 404"`{.code-voice}
4.  `print`{.code-voice}(`"The status message is `{.s}\\(`statusMessage`{.vc})`"`{.s})
5.  `// prints "The status message is Not Found"`{.code-voice}

</div>

</div>

</div>

If you only need some of the tuple’s values, ignore parts of the tuple
with an underscore (`_`{.code-voice}) when you decompose the tuple:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} (`justTheStatusCode`{.vc}, `_`{.kt}) =
    `http404Error`{.vc}
2.  `print`{.code-voice}(`"The status code is `{.s}\\(`justTheStatusCode`{.vc})`"`{.s})
3.  `// prints "The status code is 404"`{.code-voice}

</div>

</div>

</div>

Alternatively, access the individual element values in a tuple using
index numbers starting at zero:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `print`{.code-voice}(`"The status code is `{.s}\\(`http404Error`{.vc}.`0`{.m})`"`{.s})
2.  `// prints "The status code is 404"`{.code-voice}
3.  `print`{.code-voice}(`"The status message is `{.s}\\(`http404Error`{.vc}.`1`{.m})`"`{.s})
4.  `// prints "The status message is Not Found"`{.code-voice}

</div>

</div>

</div>

You can name the individual elements in a tuple when the tuple is
defined:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `http200Status`{.vc} = (`statusCode`{.vc}:
    `200`{.m}, `description`{.vc}: `"OK"`{.s})

</div>

</div>

</div>

If you name the elements in a tuple, you can use the element names to
access the values of those elements:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `print`{.code-voice}(`"The status code is `{.s}\\(`http200Status`{.vc}.`statusCode`{.vc})`"`{.s})
2.  `// prints "The status code is 200"`{.code-voice}
3.  `print`{.code-voice}(`"The status message is `{.s}\\(`http200Status`{.vc}.`description`{.vc})`"`{.s})
4.  `// prints "The status message is OK"`{.code-voice}

</div>

</div>

</div>

Tuples are particularly useful as the return values of functions. A
function that tries to retrieve a web page might return the
`(Int, String)`{.code-voice} tuple type to describe the success or
failure of the page retrieval. By returning a tuple with two distinct
values, each of a different type, the function provides more useful
information about its outcome than if it could only return a single
value of a single type. For more information, see [Functions with
Multiple Return Values](Functions.md#TP40016643-CH10-ID164).

<div class="note">

Note

Tuples are useful for temporary groups of related values. They are not
suited to the creation of complex data structures. If your data
structure is likely to persist beyond a temporary scope, model it as a
class or structure, rather than as a tuple. For more information, see
[Classes and Structures](ClassesAndStructures.md).

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH5-ID330}
### Optionals {#optionals .section-name}

You use *optionals* in situations where a value may be absent. An
optional says:

-   There *is* a value, and it equals *x*

*or*

-   There *isn’t* a value at all

<div class="note">

Note

The concept of optionals doesn’t exist in C or Objective-C. The nearest
thing in Objective-C is the ability to return `nil`{.code-voice} from a
method that would otherwise return an object, with `nil`{.code-voice}
meaning “the absence of a valid object.” However, this only works for
objects—it doesn’t work for structures, basic C types, or enumeration
values. For these types, Objective-C methods typically return a special
value (such as `NSNotFound`{.code-voice}) to indicate the absence of a
value. This approach assumes that the method’s caller knows there is a
special value to test against and remembers to check for it. Swift’s
optionals let you indicate the absence of a value for *any type at all*,
without the need for special constants.

</div>

Here’s an example of how optionals can be used to cope with the absence
of a value. Swift’s `Int`{.code-voice} type has an initializer which
tries to convert a `String`{.code-voice} value into an
`Int`{.code-voice} value. However, not every string can be converted
into an integer. The string `"123"`{.code-voice} can be converted into
the numeric value `123`{.code-voice}, but the string
`"hello, world"`{.code-voice} does not have an obvious numeric value to
convert to.

The example below uses the initializer to try to convert a
`String`{.code-voice} into an `Int`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `possibleNumber`{.vc} = `"123"`{.s}
2.  `let`{.code-voice} `convertedNumber`{.vc} =
    `Int`{.vc}(`possibleNumber`{.vc})
3.  `// convertedNumber is inferred to be of type "Int?", or "optional Int"`{.code-voice}

</div>

</div>

</div>

Because the initializer might fail, it returns an *optional*
`Int`{.code-voice}, rather than an `Int`{.code-voice}. An optional
`Int`{.code-voice} is written as `Int?`{.code-voice}, not
`Int`{.code-voice}. The question mark indicates that the value it
contains is optional, meaning that it might contain *some*
`Int`{.code-voice} value, or it might contain *no value at all*. (It
can’t contain anything else, such as a `Bool`{.code-voice} value or a
`String`{.code-voice} value. It’s either an `Int`{.code-voice}, or it’s
nothing at all.)

<div class="section section">

[‌](){#TP40016643-CH5-ID331}
### nil {#nil .section-name}

You set an optional variable to a valueless state by assigning it the
special value `nil`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `serverResponseCode`{.vc}: `Int`{.n}? = `404`{.m}
2.  `// serverResponseCode contains an actual Int value of 404`{.code-voice}
3.  `serverResponseCode`{.code-voice} = `nil`{.kt}
4.  `// serverResponseCode now contains no value`{.code-voice}

</div>

</div>

</div>

<div class="note">

Note

`nil`{.code-voice} cannot be used with nonoptional constants and
variables. If a constant or variable in your code needs to work with the
absence of a value under certain conditions, always declare it as an
optional value of the appropriate type.

</div>

If you define an optional variable without providing a default value,
the variable is automatically set to `nil`{.code-voice} for you:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `surveyAnswer`{.vc}: `String`{.n}?
2.  `// surveyAnswer is automatically set to nil`{.code-voice}

</div>

</div>

</div>

<div class="note">

Note

Swift’s `nil`{.code-voice} is not the same as `nil`{.code-voice} in
Objective-C. In Objective-C, `nil`{.code-voice} is a pointer to a
nonexistent object. In Swift, `nil`{.code-voice} is not a pointer—it is
the absence of a value of a certain type. Optionals of *any* type can be
set to `nil`{.code-voice}, not just object types.

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH5-ID332}
### If Statements and Forced Unwrapping {#if-statements-and-forced-unwrapping .section-name}

You can use an `if`{.code-voice} statement to find out whether an
optional contains a value by comparing the optional against
`nil`{.code-voice}. You perform this comparison with the “equal to”
operator (`==`{.code-voice}) or the “not equal to” operator
(`!=`{.code-voice}).

If an optional has a value, it is considered to be “not equal to”
`nil`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `if`{.code-voice} `convertedNumber`{.vc} != `nil`{.kt} {
2.  `    print`{.code-voice}(`"convertedNumber contains some integer value."`{.s})
3.  `}`{.code-voice}
4.  `// prints "convertedNumber contains some integer value."`{.code-voice}

</div>

</div>

</div>

Once you’re sure that the optional *does* contain a value, you can
access its underlying value by adding an exclamation mark
(`!`{.code-voice}) to the end of the optional’s name. The exclamation
mark effectively says, “I know that this optional definitely has a
value; please use it.” This is known as *forced unwrapping* of the
optional’s value:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `if`{.code-voice} `convertedNumber`{.vc} != `nil`{.kt} {
2.  `    print`{.code-voice}(`"convertedNumber has an integer value of `{.s}\\(`convertedNumber`{.vc}!)`."`{.s})
3.  `}`{.code-voice}
4.  `// prints "convertedNumber has an integer value of 123."`{.code-voice}

</div>

</div>

</div>

For more on the `if`{.code-voice} statement, see [Control
Flow](ControlFlow.md).

<div class="note">

Note

Trying to use `!`{.code-voice} to access a nonexistent optional value
triggers a runtime error. Always make sure that an optional contains a
non-`nil`{.code-voice} value before using `!`{.code-voice} to
force-unwrap its value.

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH5-ID333}
### Optional Binding {#optional-binding .section-name}

You use *optional binding* to find out whether an optional contains a
value, and if so, to make that value available as a temporary constant.
Optional binding can be used with `if`{.code-voice} and
`while`{.code-voice} statements to check for a value inside an optional,
and to extract that value into a constant, as part of a single action.
`if`{.code-voice} and `while`{.code-voice} statements are described in
more detail in [Control Flow](ControlFlow.md).

Write an optional binding for an `if`{.code-voice} statement as follows:

<span class="caption"></span>
<div class="code-outline">

-   ``` {.code-voice}
    if let constantName = someOptional {
    ```

-   ``` {.code-voice}
        statements
    ```

-   ``` {.code-voice}
    }
    ```

</div>

You can rewrite the `possibleNumber`{.code-voice} example from the
[Optionals](TheBasics.md#TP40016643-CH5-ID330) section to use
optional binding rather than forced unwrapping:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `if`{.code-voice} `let`{.kt} `actualNumber`{.vc} =
    `Int`{.vc}(`possibleNumber`{.vc}) {
2.  `    print`{.code-voice}(`"\'`{.s}\\(`possibleNumber`{.vc})`\' has an integer value of `{.s}\\(`actualNumber`{.vc})`"`{.s})
3.  `} else`{.code-voice} {
4.  `    print`{.code-voice}(`"\'`{.s}\\(`possibleNumber`{.vc})`\' could not be converted to an integer"`{.s})
5.  `}`{.code-voice}
6.  `// prints "'123' has an integer value of 123"`{.code-voice}

</div>

</div>

</div>

This code can be read as:

“If the optional `Int`{.code-voice} returned by
`Int(possibleNumber)`{.code-voice} contains a value, set a new constant
called `actualNumber`{.code-voice} to the value contained in the
optional.”

If the conversion is successful, the `actualNumber`{.code-voice}
constant becomes available for use within the first branch of the
`if`{.code-voice} statement. It has already been initialized with the
value contained *within* the optional, and so there is no need to use
the `!`{.code-voice} suffix to access its value. In this example,
`actualNumber`{.code-voice} is simply used to print the result of the
conversion.

You can include multiple optional bindings in a single `if`{.code-voice}
statement and use a `where`{.code-voice} clause to check for a Boolean
condition. If any of the values in the optional bindings are
`nil`{.code-voice} or the `where`{.code-voice} clause evaluates to
`false`{.code-voice}, the whole optional binding is considered
unsuccessful.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `if`{.code-voice} `let`{.kt} `firstNumber`{.vc} =
    `Int`{.vc}(`"4"`{.s}), `secondNumber`{.vc} = `Int`{.vc}(`"42"`{.s})
    `where`{.kt} `firstNumber`{.vc} &lt; `secondNumber`{.vc} {
2.  `    print`{.code-voice}(`"`{.s}\\(`firstNumber`{.vc})` < `{.s}\\(`secondNumber`{.vc})`"`{.s})
3.  `}`{.code-voice}
4.  `// prints "4 < 42"`{.code-voice}

</div>

</div>

</div>

<div class="note">

Note

Constants created with optional binding in an `if`{.code-voice}
statement. are available only within the body of the `if`{.code-voice}
statement. In contrast, the constants created with a
`guard`{.code-voice} statement are available in the lines of code that
follow the `guard`{.code-voice} statement, as described in [Early
Exit](ControlFlow.md#TP40016643-CH9-ID525),

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH5-ID334}
### Implicitly Unwrapped Optionals {#implicitly-unwrapped-optionals .section-name}

As described above, optionals indicate that a constant or variable is
allowed to have “no value”. Optionals can be checked with an
`if`{.code-voice} statement to see if a value exists, and can be
conditionally unwrapped with optional binding to access the optional’s
value if it does exist.

Sometimes it is clear from a program’s structure that an optional will
*always* have a value, after that value is first set. In these cases, it
is useful to remove the need to check and unwrap the optional’s value
every time it is accessed, because it can be safely assumed to have a
value all of the time.

These kinds of optionals are defined as *implicitly unwrapped
optionals*. You write an implicitly unwrapped optional by placing an
exclamation mark (`String!`{.code-voice}) rather than a question mark
(`String?`{.code-voice}) after the type that you want to make optional.

Implicitly unwrapped optionals are useful when an optional’s value is
confirmed to exist immediately after the optional is first defined and
can definitely be assumed to exist at every point thereafter. The
primary use of implicitly unwrapped optionals in Swift is during class
initialization, as described in [Unowned References and Implicitly
Unwrapped Optional
Properties](AutomaticReferenceCounting.md#TP40016643-CH20-ID55).

An implicitly unwrapped optional is a normal optional behind the scenes,
but can also be used like a nonoptional value, without the need to
unwrap the optional value each time it is accessed. The following
example shows the difference in behavior between an optional string and
an implicitly unwrapped optional string when accessing their wrapped
value as an explicit `String`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `possibleString`{.vc}: `String`{.n}? =
    `"An optional string."`{.s}
2.  `let`{.code-voice} `forcedString`{.vc}: `String`{.n} =
    `possibleString`{.vc}! `// requires an exclamation mark`{.c}
3.  ` `{.code-voice}
4.  `let`{.code-voice} `assumedString`{.vc}: `String`{.n}! =
    `"An implicitly unwrapped optional string."`{.s}
5.  `let`{.code-voice} `implicitString`{.vc}: `String`{.n} =
    `assumedString`{.vc} `// no need for an exclamation mark`{.c}

</div>

</div>

</div>

You can think of an implicitly unwrapped optional as giving permission
for the optional to be unwrapped automatically whenever it is used.
Rather than placing an exclamation mark after the optional’s name each
time you use it, you place an exclamation mark after the optional’s type
when you declare it.

<div class="note">

Note

If an implicitly unwrapped optional is `nil`{.code-voice} and you try to
access its wrapped value, you’ll trigger a runtime error. The result is
exactly the same as if you place an exclamation mark after a normal
optional that does not contain a value.

</div>

You can still treat an implicitly unwrapped optional like a normal
optional, to check if it contains a value:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `if`{.code-voice} `assumedString`{.vc} != `nil`{.kt} {
2.  `    print`{.code-voice}(`assumedString`{.vc})
3.  `}`{.code-voice}
4.  `// prints "An implicitly unwrapped optional string."`{.code-voice}

</div>

</div>

</div>

You can also use an implicitly unwrapped optional with optional binding,
to check and unwrap its value in a single statement:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `if`{.code-voice} `let`{.kt} `definiteString`{.vc} =
    `assumedString`{.vc} {
2.  `    print`{.code-voice}(`definiteString`{.vc})
3.  `}`{.code-voice}
4.  `// prints "An implicitly unwrapped optional string."`{.code-voice}

</div>

</div>

</div>

<div class="note">

Note

Do not use an implicitly unwrapped optional when there is a possibility
of a variable becoming `nil`{.code-voice} at a later point. Always use a
normal optional type if you need to check for a `nil`{.code-voice} value
during the lifetime of a variable.

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH5-ID515}
### Error Handling {#error-handling .section-name}

You use *error handling* to respond to error conditions your program may
encounter during execution.

In contrast to optionals, which can use the presence or absence of a
value to communicate success or failure of a function, error handling
allows you to determine the underlying cause of failure, and, if
necessary, propagate the error to another part of your program.

When a function encounters an error condition, it *throws* an error.
That function’s caller can then *catch* the error and respond
appropriately.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `canThrowAnError`{.vc}() `throws`{.kt} {
2.  `    // this function may or may not throw an error`{.code-voice}
3.  `}`{.code-voice}

</div>

</div>

</div>

A function indicates that it can throw an error by including the
`throws`{.code-voice} keyword in its declaration. When you call a
function that can throw an error, you prepend the `try`{.code-voice}
keyword to the expression.

Swift automatically propagates errors out of their current scope until
they are handled by a `catch`{.code-voice} clause.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `do`{.code-voice} {
2.  `    try`{.code-voice} `canThrowAnError`{.vc}()
3.  `    // no error was thrown`{.code-voice}
4.  `} catch`{.code-voice} {
5.  `    // an error was thrown`{.code-voice}
6.  `}`{.code-voice}

</div>

</div>

</div>

A `do`{.code-voice} statement creates a new containing scope, which
allows errors to be propagated to one or more `catch`{.code-voice}
clauses.

Here’s an example of how error handling can be used to respond to
different error conditions:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `makeASandwich`{.vc}() `throws`{.kt} {
2.  `    // ...`{.code-voice}
3.  `}`{.code-voice}
4.  ` `{.code-voice}
5.  `do`{.code-voice} {
6.  `    try`{.code-voice} `makeASandwich`{.vc}()
7.  `    eatASandwich`{.code-voice}()
8.  `} catch`{.code-voice} `Error`{.vc}.`OutOfCleanDishes`{.vc} {
9.  `    washDishes`{.code-voice}()
10. `} catch`{.code-voice}
    `Error`{.vc}.`MissingIngredients`{.vc}(`let`{.kt}
    `ingredients`{.vc}) {
11. `    buyGroceries`{.code-voice}(`ingredients`{.vc})
12. `}`{.code-voice}

</div>

</div>

</div>

In this example, the `makeASandwich()`{.code-voice} function will throw
an error if no clean dishes are available or if any ingredients are
missing. Because `makeASandwich()`{.code-voice} can throw an error, the
function call is wrapped in a `try`{.code-voice} expression. By wrapping
the function call in a `do`{.code-voice} statement, any errors that are
thrown will be propagated to the provided `catch`{.code-voice} clauses.

If no error is thrown, the `eatASandwich()`{.code-voice} function is
called. If an error is thrown and it matches the
`Error.OutOfCleanDishes`{.code-voice} case, then the
`washDishes()`{.code-voice} function will be called. If an error is
thrown and it matches the `Error.MissingIngredients`{.code-voice} case,
then the `buyGroceries(_:)`{.code-voice} function is called with the
associated `[String]`{.code-voice} value captured by the
`catch`{.code-voice} pattern.

Throwing, catching, and propagating errors is covered in greater detail
in [Error Handling](ErrorHandling.md).

</div>

<div class="section section">

[‌](){#TP40016643-CH5-ID335}
### Assertions {#assertions .section-name}

In some cases, it is simply not possible for your code to continue
execution if a particular condition is not satisfied. In these
situations, you can trigger an *assertion* in your code to end code
execution and to provide an opportunity to debug the cause of the absent
or invalid value.

<div class="section section">

[‌](){#TP40016643-CH5-ID336}
### Debugging with Assertions {#debugging-with-assertions .section-name}

An assertion is a runtime check that a Boolean condition definitely
evaluates to `true`{.code-voice}. Literally put, an assertion “asserts”
that a condition is true. You use an assertion to make sure that an
essential condition is satisfied before executing any further code. If
the condition evaluates to `true`{.code-voice}, code execution continues
as usual; if the condition evaluates to `false`{.code-voice}, code
execution ends, and your app is terminated.

If your code triggers an assertion while running in a debug environment,
such as when you build and run an app in Xcode, you can see exactly
where the invalid state occurred and query the state of your app at the
time that the assertion was triggered. An assertion also lets you
provide a suitable debug message as to the nature of the assert.

You write an assertion by calling the Swift standard library global
`assert(_:_file:line:)`{.code-voice} function. You pass this function an
expression that evaluates to `true`{.code-voice} or `false`{.code-voice}
and a message that should be displayed if the result of the condition is
`false`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `age`{.vc} = -`3`{.m}
2.  `assert`{.code-voice}(`age`{.vc} &gt;= `0`{.m},
    `"A person's age cannot be less than zero"`{.s})
3.  `// this causes the assertion to trigger, because age is not >= 0`{.code-voice}

</div>

</div>

</div>

In this example, code execution will continue only if
`age >= 0`{.code-voice} evaluates to `true`{.code-voice}, that is, if
the value of `age`{.code-voice} is non-negative. If the value of
`age`{.code-voice} *is* negative, as in the code above, then
`age >= 0`{.code-voice} evaluates to `false`{.code-voice}, and the
assertion is triggered, terminating the application.

The assertion message can be omitted if desired, as in the following
example:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `assert`{.code-voice}(`age`{.vc} &gt;= `0`{.m})

</div>

</div>

</div>

<div class="note">

Note

Assertions are disabled when your code is compiled with optimizations,
such as when building with an app target’s default Release configuration
in Xcode.

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH5-ID337}
### When to Use Assertions {#when-to-use-assertions .section-name}

Use an assertion whenever a condition has the potential to be false, but
must *definitely* be true in order for your code to continue execution.
Suitable scenarios for an assertion check include:

-   An integer subscript index is passed to a custom subscript
    implementation, but the subscript index value could be too low or
    too high.

-   A value is passed to a function, but an invalid value means that the
    function cannot fulfill its task.

-   An optional value is currently `nil`{.code-voice}, but a
    non-`nil`{.code-voice} value is essential for subsequent code to
    execute successfully.

See also [Subscripts](Subscripts.md) and
[Functions](Functions.md).

<div class="note">

Note

Assertions cause your app to terminate and are not a substitute for
designing your code in such a way that invalid conditions are unlikely
to arise. Nonetheless, in situations where invalid conditions are
possible, an assertion is an effective way to ensure that such
conditions are highlighted and noticed during development, before your
app is published.

</div>

</div>

</div>

</div>

</div>
