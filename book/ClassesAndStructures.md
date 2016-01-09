<div class="content-wrapper">

<div id="chapter_container" class="conceptualwithtasks">

[‌](){#TP40016643-CH13}[‌](){#TP40016643-CH13-ID82}
Classes and Structures {#classes-and-structures .chapter-name}
----------------------

<div class="section section">

*Classes* and *structures* are general-purpose, flexible constructs that
become the building blocks of your program’s code. You define properties
and methods to add functionality to your classes and structures by using
exactly the same syntax as for constants, variables, and functions.

Unlike other programming languages, Swift does not require you to create
separate interface and implementation files for custom classes and
structures. In Swift, you define a class or a structure in a single
file, and the external interface to that class or structure is
automatically made available for other code to use.

<div class="note">

Note

An instance of a *class* is traditionally known as an *object*. However,
Swift classes and structures are much closer in functionality than in
other languages, and much of this chapter describes functionality that
can apply to instances of *either* a class or a structure type. Because
of this, the more general term *instance* is used.

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH13-ID83}
### Comparing Classes and Structures {#comparing-classes-and-structures .section-name}

Classes and structures in Swift have many things in common. Both can:

-   Define properties to store values

-   Define methods to provide functionality

-   Define subscripts to provide access to their values using subscript
    syntax

-   Define initializers to set up their initial state

-   Be extended to expand their functionality beyond a default
    implementation

-   Conform to protocols to provide standard functionality of a certain
    kind

For more information, see [Properties](Properties.md),
[Methods](Methods.md), [Subscripts](Subscripts.md),
[Initialization](Initialization.md), [Extensions](Extensions.md),
and [Protocols](Protocols.md).

Classes have additional capabilities that structures do not:

-   Inheritance enables one class to inherit the characteristics
    of another.

-   Type casting enables you to check and interpret the type of a class
    instance at runtime.

-   Deinitializers enable an instance of a class to free up any
    resources it has assigned.

-   Reference counting allows more than one reference to a
    class instance.

For more information, see [Inheritance](Inheritance.md), [Type
Casting](TypeCasting.md), [Deinitialization](Deinitialization.md),
and [Automatic Reference Counting](AutomaticReferenceCounting.md).

<div class="note">

Note

Structures are always copied when they are passed around in your code,
and do not use reference counting.

</div>

<div class="section section">

[‌](){#TP40016643-CH13-ID84}
### Definition Syntax {#definition-syntax .section-name}

Classes and structures have a similar definition syntax. You introduce
classes with the `class`{.code-voice} keyword and structures with the
`struct`{.code-voice} keyword. Both place their entire definition within
a pair of braces:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `class`{.code-voice} `SomeClass`{.vc} {
2.  `    // class definition goes here`{.code-voice}
3.  `}`{.code-voice}
4.  `struct`{.code-voice} `SomeStructure`{.vc} {
5.  `    // structure definition goes here`{.code-voice}
6.  `}`{.code-voice}

</div>

</div>

</div>

<div class="note">

Note

Whenever you define a new class or structure, you effectively define a
brand new Swift type. Give types `UpperCamelCase`{.code-voice} names
(such as `SomeClass`{.code-voice} and `SomeStructure`{.code-voice} here)
to match the capitalization of standard Swift types (such as
`String`{.code-voice}, `Int`{.code-voice}, and `Bool`{.code-voice}).
Conversely, always give properties and methods
`lowerCamelCase`{.code-voice} names (such as `frameRate`{.code-voice}
and `incrementCount`{.code-voice}) to differentiate them from type
names.

</div>

Here’s an example of a structure definition and a class definition:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `struct`{.code-voice} `Resolution`{.vc} {
2.  `    var`{.code-voice} `width`{.vc} = `0`{.m}
3.  `    var`{.code-voice} `height`{.vc} = `0`{.m}
4.  `}`{.code-voice}
5.  `class`{.code-voice} `VideoMode`{.vc} {
6.  `    var`{.code-voice} `resolution`{.vc} = `Resolution`{.vc}()
7.  `    var`{.code-voice} `interlaced`{.vc} = `false`{.kt}
8.  `    var`{.code-voice} `frameRate`{.vc} = `0.0`{.m}
9.  `    var`{.code-voice} `name`{.vc}: `String`{.n}?
10. `}`{.code-voice}

</div>

</div>

</div>

The example above defines a new structure called
`Resolution`{.code-voice}, to describe a pixel-based display resolution.
This structure has two stored properties called `width`{.code-voice} and
`height`{.code-voice}. Stored properties are constants or variables that
are bundled up and stored as part of the class or structure. These two
properties are inferred to be of type `Int`{.code-voice} by setting them
to an initial integer value of `0`{.code-voice}.

The example above also defines a new class called
`VideoMode`{.code-voice}, to describe a specific video mode for video
display. This class has four variable stored properties. The first,
`resolution`{.code-voice}, is initialized with a new
`Resolution`{.code-voice} structure instance, which infers a property
type of `Resolution`{.code-voice}. For the other three properties, new
`VideoMode`{.code-voice} instances will be initialized with an
`interlaced`{.code-voice} setting of `false`{.code-voice} (meaning
“noninterlaced video”), a playback frame rate of `0.0`{.code-voice}, and
an optional `String`{.code-voice} value called `name`{.code-voice}. The
`name`{.code-voice} property is automatically given a default value of
`nil`{.code-voice}, or “no `name`{.code-voice} value”, because it is of
an optional type.

</div>

<div class="section section">

[‌](){#TP40016643-CH13-ID85}
### Class and Structure Instances {#class-and-structure-instances .section-name}

The `Resolution`{.code-voice} structure definition and the
`VideoMode`{.code-voice} class definition only describe what a
`Resolution`{.code-voice} or `VideoMode`{.code-voice} will look like.
They themselves do not describe a specific resolution or video mode. To
do that, you need to create an instance of the structure or class.

The syntax for creating instances is very similar for both structures
and classes:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `someResolution`{.vc} = `Resolution`{.vc}()
2.  `let`{.code-voice} `someVideoMode`{.vc} = `VideoMode`{.vc}()

</div>

</div>

</div>

Structures and classes both use initializer syntax for new instances.
The simplest form of initializer syntax uses the type name of the class
or structure followed by empty parentheses, such as
`Resolution()`{.code-voice} or `VideoMode()`{.code-voice}. This creates
a new instance of the class or structure, with any properties
initialized to their default values. Class and structure initialization
is described in more detail in [Initialization](Initialization.md).

</div>

<div class="section section">

[‌](){#TP40016643-CH13-ID86}
### Accessing Properties {#accessing-properties .section-name}

You can access the properties of an instance using *dot syntax*. In dot
syntax, you write the property name immediately after the instance name,
separated by a period (`.`{.code-voice}), without any spaces:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `print`{.code-voice}(`"The width of someResolution is `{.s}\\(`someResolution`{.vc}.`width`{.vc})`"`{.s})
2.  `// prints "The width of someResolution is 0"`{.code-voice}

</div>

</div>

</div>

In this example, `someResolution.width`{.code-voice} refers to the
`width`{.code-voice} property of `someResolution`{.code-voice}, and
returns its default initial value of `0`{.code-voice}.

You can drill down into sub-properties, such as the `width`{.code-voice}
property in the `resolution`{.code-voice} property of a
`VideoMode`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `print`{.code-voice}(`"The width of someVideoMode is `{.s}\\(`someVideoMode`{.vc}.`resolution`{.vc}.`width`{.vc})`"`{.s})
2.  `// prints "The width of someVideoMode is 0"`{.code-voice}

</div>

</div>

</div>

You can also use dot syntax to assign a new value to a variable
property:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `someVideoMode`{.code-voice}.`resolution`{.vc}.`width`{.vc} =
    `1280`{.m}
2.  `print`{.code-voice}(`"The width of someVideoMode is now `{.s}\\(`someVideoMode`{.vc}.`resolution`{.vc}.`width`{.vc})`"`{.s})
3.  `// prints "The width of someVideoMode is now 1280"`{.code-voice}

</div>

</div>

</div>

<div class="note">

Note

Unlike Objective-C, Swift enables you to set sub-properties of a
structure property directly. In the last example above, the
`width`{.code-voice} property of the `resolution`{.code-voice} property
of `someVideoMode`{.code-voice} is set directly, without your needing to
set the entire `resolution`{.code-voice} property to a new value.

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH13-ID87}
### Memberwise Initializers for Structure Types {#memberwise-initializers-for-structure-types .section-name}

All structures have an automatically-generated *memberwise initializer*,
which you can use to initialize the member properties of new structure
instances. Initial values for the properties of the new instance can be
passed to the memberwise initializer by name:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `vga`{.vc} = `Resolution`{.vc}(`width`{.vc}:
    `640`{.m}, `height`{.vc}: `480`{.m})

</div>

</div>

</div>

Unlike structures, class instances do not receive a default memberwise
initializer. Initializers are described in more detail in
[Initialization](Initialization.md).

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH13-ID88}
### Structures and Enumerations Are Value Types {#structures-and-enumerations-are-value-types .section-name}

A *value type* is a type whose value is *copied* when it is assigned to
a variable or constant, or when it is passed to a function.

You’ve actually been using value types extensively throughout the
previous chapters. In fact, all of the basic types in Swift—integers,
floating-point numbers, Booleans, strings, arrays and dictionaries—are
value types, and are implemented as structures behind the scenes.

All structures and enumerations are value types in Swift. This means
that any structure and enumeration instances you create—and any value
types they have as properties—are always copied when they are passed
around in your code.

Consider this example, which uses the `Resolution`{.code-voice}
structure from the previous example:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `hd`{.vc} = `Resolution`{.vc}(`width`{.vc}:
    `1920`{.m}, `height`{.vc}: `1080`{.m})
2.  `var`{.code-voice} `cinema`{.vc} = `hd`{.vc}

</div>

</div>

</div>

This example declares a constant called `hd`{.code-voice} and sets it to
a `Resolution`{.code-voice} instance initialized with the width and
height of full HD video (`1920`{.code-voice} pixels wide by
`1080`{.code-voice} pixels high).

It then declares a variable called `cinema`{.code-voice} and sets it to
the current value of `hd`{.code-voice}. Because
`Resolution`{.code-voice} is a structure, a *copy* of the existing
instance is made, and this new copy is assigned to
`cinema`{.code-voice}. Even though `hd`{.code-voice} and
`cinema`{.code-voice} now have the same width and height, they are two
completely different instances behind the scenes.

Next, the `width`{.code-voice} property of `cinema`{.code-voice} is
amended to be the width of the slightly-wider 2K standard used for
digital cinema projection (`2048`{.code-voice} pixels wide and
`1080`{.code-voice} pixels high):

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `cinema`{.code-voice}.`width`{.vc} = `2048`{.m}

</div>

</div>

</div>

Checking the `width`{.code-voice} property of `cinema`{.code-voice}
shows that it has indeed changed to be `2048`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `print`{.code-voice}(`"cinema is now `{.s}\\(`cinema`{.vc}.`width`{.vc})` pixels wide"`{.s})
2.  `// prints "cinema is now 2048 pixels wide"`{.code-voice}

</div>

</div>

</div>

However, the `width`{.code-voice} property of the original
`hd`{.code-voice} instance still has the old value of
`1920`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `print`{.code-voice}(`"hd is still `{.s}\\(`hd`{.vc}.`width`{.vc})` pixels wide"`{.s})
2.  `// prints "hd is still 1920 pixels wide"`{.code-voice}

</div>

</div>

</div>

When `cinema`{.code-voice} was given the current value of
`hd`{.code-voice}, the *values* stored in `hd`{.code-voice} were copied
into the new `cinema`{.code-voice} instance. The end result is two
completely separate instances, which just happened to contain the same
numeric values. Because they are separate instances, setting the width
of `cinema`{.code-voice} to `2048`{.code-voice} doesn’t affect the width
stored in `hd`{.code-voice}.

The same behavior applies to enumerations:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `enum`{.code-voice} `CompassPoint`{.vc} {
2.  `    case`{.code-voice} `North`{.vc}, `South`{.vc}, `East`{.vc},
    `West`{.vc}
3.  `}`{.code-voice}
4.  `var`{.code-voice} `currentDirection`{.vc} =
    `CompassPoint`{.vc}.`West`{.vc}
5.  `let`{.code-voice} `rememberedDirection`{.vc} =
    `currentDirection`{.vc}
6.  `currentDirection`{.code-voice} = .`East`{.vc}
7.  `if`{.code-voice} `rememberedDirection`{.vc} == .`West`{.vc} {
8.  `    print`{.code-voice}(`"The remembered direction is still .West"`{.s})
9.  `}`{.code-voice}
10. `// prints "The remembered direction is still .West"`{.code-voice}

</div>

</div>

</div>

When `rememberedDirection`{.code-voice} is assigned the value of
`currentDirection`{.code-voice}, it is actually set to a copy of that
value. Changing the value of `currentDirection`{.code-voice} thereafter
does not affect the copy of the original value that was stored in
`rememberedDirection`{.code-voice}.

</div>

<div class="section section">

[‌](){#TP40016643-CH13-ID89}
### Classes Are Reference Types {#classes-are-reference-types .section-name}

Unlike value types, *reference types* are *not* copied when they are
assigned to a variable or constant, or when they are passed to a
function. Rather than a copy, a reference to the same existing instance
is used instead.

Here’s an example, using the `VideoMode`{.code-voice} class defined
above:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `tenEighty`{.vc} = `VideoMode`{.vc}()
2.  `tenEighty`{.code-voice}.`resolution`{.vc} = `hd`{.vc}
3.  `tenEighty`{.code-voice}.`interlaced`{.vc} = `true`{.kt}
4.  `tenEighty`{.code-voice}.`name`{.vc} = `"1080i"`{.s}
5.  `tenEighty`{.code-voice}.`frameRate`{.vc} = `25.0`{.m}

</div>

</div>

</div>

This example declares a new constant called `tenEighty`{.code-voice} and
sets it to refer to a new instance of the `VideoMode`{.code-voice}
class. The video mode is assigned a copy of the HD resolution of
`1920`{.code-voice} by `1080`{.code-voice} from before. It is set to be
interlaced, and is given a name of `"1080i"`{.code-voice}. Finally, it
is set to a frame rate of `25.0`{.code-voice} frames per second.

Next, `tenEighty`{.code-voice} is assigned to a new constant, called
`alsoTenEighty`{.code-voice}, and the frame rate of
`alsoTenEighty`{.code-voice} is modified:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `alsoTenEighty`{.vc} = `tenEighty`{.vc}
2.  `alsoTenEighty`{.code-voice}.`frameRate`{.vc} = `30.0`{.m}

</div>

</div>

</div>

Because classes are reference types, `tenEighty`{.code-voice} and
`alsoTenEighty`{.code-voice} actually both refer to the *same*
`VideoMode`{.code-voice} instance. Effectively, they are just two
different names for the same single instance.

Checking the `frameRate`{.code-voice} property of
`tenEighty`{.code-voice} shows that it correctly reports the new frame
rate of `30.0`{.code-voice} from the underlying `VideoMode`{.code-voice}
instance:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `print`{.code-voice}(`"The frameRate property of tenEighty is now `{.s}\\(`tenEighty`{.vc}.`frameRate`{.vc})`"`{.s})
2.  `// prints "The frameRate property of tenEighty is now 30.0"`{.code-voice}

</div>

</div>

</div>

Note that `tenEighty`{.code-voice} and `alsoTenEighty`{.code-voice} are
declared as *constants*, rather than variables. However, you can still
change `tenEighty.frameRate`{.code-voice} and
`alsoTenEighty.frameRate`{.code-voice} because the values of the
`tenEighty`{.code-voice} and `alsoTenEighty`{.code-voice} constants
themselves do not actually change. `tenEighty`{.code-voice} and
`alsoTenEighty`{.code-voice} themselves do not “store” the
`VideoMode`{.code-voice} instance—instead, they both *refer* to a
`VideoMode`{.code-voice} instance behind the scenes. It is the
`frameRate`{.code-voice} property of the underlying
`VideoMode`{.code-voice} that is changed, not the values of the constant
references to that `VideoMode`{.code-voice}.

<div class="section section">

[‌](){#TP40016643-CH13-ID90}
### Identity Operators {#identity-operators .section-name}

Because classes are reference types, it is possible for multiple
constants and variables to refer to the same single instance of a class
behind the scenes. (The same is not true for structures and
enumerations, because they are always copied when they are assigned to a
constant or variable, or passed to a function.)

It can sometimes be useful to find out if two constants or variables
refer to exactly the same instance of a class. To enable this, Swift
provides two identity operators:

-   Identical to (`===`{.code-voice})

-   Not identical to (`!==`{.code-voice})

Use these operators to check whether two constants or variables refer to
the same single instance:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `if`{.code-voice} `tenEighty`{.vc} === `alsoTenEighty`{.vc} {
2.  `    print`{.code-voice}(`"tenEighty and alsoTenEighty refer to the same VideoMode instance."`{.s})
3.  `}`{.code-voice}
4.  `// prints "tenEighty and alsoTenEighty refer to the same VideoMode instance."`{.code-voice}

</div>

</div>

</div>

Note that “identical to” (represented by three equals signs, or
`===`{.code-voice}) does not mean the same thing as “equal to”
(represented by two equals signs, or `==`{.code-voice}):

-   “Identical to” means that two constants or variables of class type
    refer to exactly the same class instance.

-   “Equal to” means that two instances are considered “equal” or
    “equivalent” in value, for some appropriate meaning of “equal”, as
    defined by the type’s designer.

When you define your own custom classes and structures, it is your
responsibility to decide what qualifies as two instances being “equal”.
The process of defining your own implementations of the “equal to” and
“not equal to” operators is described in [Equivalence
Operators](AdvancedOperators.md#TP40016643-CH27-ID45).

</div>

<div class="section section">

[‌](){#TP40016643-CH13-ID91}
### Pointers {#pointers .section-name}

If you have experience with C, C++, or Objective-C, you may know that
these languages use *pointers* to refer to addresses in memory. A Swift
constant or variable that refers to an instance of some reference type
is similar to a pointer in C, but is not a direct pointer to an address
in memory, and does not require you to write an asterisk
(`*`{.code-voice}) to indicate that you are creating a reference.
Instead, these references are defined like any other constant or
variable in Swift.

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH13-ID92}
### Choosing Between Classes and Structures {#choosing-between-classes-and-structures .section-name}

You can use both classes and structures to define custom data types to
use as the building blocks of your program’s code.

However, structure instances are always passed by *value*, and class
instances are always passed by *reference*. This means that they are
suited to different kinds of tasks. As you consider the data constructs
and functionality that you need for a project, decide whether each data
construct should be defined as a class or as a structure.

As a general guideline, consider creating a structure when one or more
of these conditions apply:

-   The structure’s primary purpose is to encapsulate a few relatively
    simple data values.

-   It is reasonable to expect that the encapsulated values will be
    copied rather than referenced when you assign or pass around an
    instance of that structure.

-   Any properties stored by the structure are themselves value types,
    which would also be expected to be copied rather than referenced.

-   The structure does not need to inherit properties or behavior from
    another existing type.

Examples of good candidates for structures include:

-   The size of a geometric shape, perhaps encapsulating a
    `width`{.code-voice} property and a `height`{.code-voice} property,
    both of type `Double`{.code-voice}.

-   A way to refer to ranges within a series, perhaps encapsulating a
    `start`{.code-voice} property and a `length`{.code-voice} property,
    both of type `Int`{.code-voice}.

-   A point in a 3D coordinate system, perhaps encapsulating
    `x`{.code-voice}, `y`{.code-voice} and `z`{.code-voice} properties,
    each of type `Double`{.code-voice}.

In all other cases, define a class, and create instances of that class
to be managed and passed by reference. In practice, this means that most
custom data constructs should be classes, not structures.

</div>

<div class="section section">

[‌](){#TP40016643-CH13-ID93}
### Assignment and Copy Behavior for Strings, Arrays, and Dictionaries {#assignment-and-copy-behavior-for-strings-arrays-and-dictionaries .section-name}

In Swift, many basic data types such as `String`{.code-voice},
`Array`{.code-voice}, and `Dictionary`{.code-voice} are implemented as
structures. This means that data such as strings, arrays, and
dictionaries are copied when they are assigned to a new constant or
variable, or when they are passed to a function or method.

This behavior is different from Foundation: `NSString`{.code-voice},
`NSArray`{.code-voice}, and `NSDictionary`{.code-voice} are implemented
as classes, not structures. Strings, arrays, and dictionaries in
Foundation are always assigned and passed around as a reference to an
existing instance, rather than as a copy.

<div class="note">

Note

The description above refers to the “copying” of strings, arrays, and
dictionaries. The behavior you see in your code will always be as if a
copy took place. However, Swift only performs an *actual* copy behind
the scenes when it is absolutely necessary to do so. Swift manages all
value copying to ensure optimal performance, and you should not avoid
assignment to try to preempt this optimization.

</div>

</div>

</div>

</div>
