



[‌](){#TP40016643-CH24}[‌](){#TP40016643-CH24-ID151}
Extensions {#extensions .chapter-name}
----------



*Extensions* add new functionality to an existing class, structure, enumeration, or protocol type. This includes the ability to extend types for which you do not have access to the original source code (known as *retroactive modeling*). Extensions are similar to categories in Objective-C. (Unlike Objective-C categories, Swift extensions do not have names.)

Extensions in Swift can:

-   Add computed properties and computed type properties

-   Define instance methods and type methods

-   Provide new initializers

-   Define subscripts

-   Define and use new nested types

-   Make an existing type conform to a protocol

In Swift, you can even extend a protocol to provide implementations of its requirements or add additional functionality that conforming types can take advantage of. For more details, see [Protocol Extensions](Protocols.md#TP40016643-CH25-ID521).



Note

Extensions can add new functionality to a type, but they cannot override existing functionality.







[‌](){#TP40016643-CH24-ID470}
### Extension Syntax {#extension-syntax .section-name}

Declare extensions with the `extension`{.code-voice} keyword:







1.  `extension`{.code-voice} `SomeType`{.n} {
2.  `    // new functionality to add to SomeType goes here`{.code-voice}
3.  `}`{.code-voice}







An extension can extend an existing type to make it adopt one or more protocols. Where this is the case, the protocol names are written in exactly the same way as for a class or structure:







1.  `extension`{.code-voice} `SomeType`{.n}: `SomeProtocol`{.n}, `AnotherProtocol`{.n} {
2.  `    // implementation of protocol requirements goes here`{.code-voice}
3.  `}`{.code-voice}







Adding protocol conformance in this way is described in [Adding Protocol Conformance with an Extension](Protocols.md#TP40016643-CH25-ID277).



Note

If you define an extension to add new functionality to an existing type, the new functionality will be available on all existing instances of that type, even if they were created before the extension was defined.







[‌](){#TP40016643-CH24-ID152}
### Computed Properties {#computed-properties .section-name}

Extensions can add computed instance properties and computed type properties to existing types. This example adds five computed instance properties to Swift’s built-in `Double`{.code-voice} type, to provide basic support for working with distance units:







1.  `extension`{.code-voice} `Double`{.n} {
2.  `    var`{.code-voice} `km`{.vc}: `Double`{.n} { `return`{.kt} `self`{.kt} \* `1_000.0`{.m} }
3.  `    var`{.code-voice} `m`{.vc}: `Double`{.n} { `return`{.kt} `self`{.kt} }
4.  `    var`{.code-voice} `cm`{.vc}: `Double`{.n} { `return`{.kt} `self`{.kt} / `100.0`{.m} }
5.  `    var`{.code-voice} `mm`{.vc}: `Double`{.n} { `return`{.kt} `self`{.kt} / `1_000.0`{.m} }
6.  `    var`{.code-voice} `ft`{.vc}: `Double`{.n} { `return`{.kt} `self`{.kt} / `3.28084`{.m} }
7.  `}`{.code-voice}
8.  `let`{.code-voice} `oneInch`{.vc} = `25.4`{.m}.`mm`{.vc}
9.  `print`{.code-voice}(`"One inch is `{.s}\\(`oneInch`{.vc})` meters"`{.s})
10. `// prints "One inch is 0.0254 meters"`{.code-voice}
11. `let`{.code-voice} `threeFeet`{.vc} = `3`{.m}.`ft`{.vc}
12. `print`{.code-voice}(`"Three feet is `{.s}\\(`threeFeet`{.vc})` meters"`{.s})
13. `// prints "Three feet is 0.914399970739201 meters"`{.code-voice}







These computed properties express that a `Double`{.code-voice} value should be considered as a certain unit of length. Although they are implemented as computed properties, the names of these properties can be appended to a floating-point literal value with dot syntax, as a way to use that literal value to perform distance conversions.

In this example, a `Double`{.code-voice} value of `1.0`{.code-voice} is considered to represent “one meter”. This is why the `m`{.code-voice} computed property returns `self`{.code-voice}—the expression `1.m`{.code-voice} is considered to calculate a `Double`{.code-voice} value of `1.0`{.code-voice}.

Other units require some conversion to be expressed as a value measured in meters. One kilometer is the same as 1,000 meters, so the `km`{.code-voice} computed property multiplies the value by `1_000.00`{.code-voice} to convert into a number expressed in meters. Similarly, there are 3.28084 feet in a meter, and so the `ft`{.code-voice} computed property divides the underlying `Double`{.code-voice} value by `3.28084`{.code-voice}, to convert it from feet to meters.

These properties are read-only computed properties, and so they are expressed without the `get`{.code-voice} keyword, for brevity. Their return value is of type `Double`{.code-voice}, and can be used within mathematical calculations wherever a `Double`{.code-voice} is accepted:







1.  `let`{.code-voice} `aMarathon`{.vc} = `42`{.m}.`km`{.vc} + `195`{.m}.`m`{.vc}
2.  `print`{.code-voice}(`"A marathon is `{.s}\\(`aMarathon`{.vc})` meters long"`{.s})
3.  `// prints "A marathon is 42195.0 meters long"`{.code-voice}









Note

Extensions can add new computed properties, but they cannot add stored properties, or add property observers to existing properties.







[‌](){#TP40016643-CH24-ID153}
### Initializers {#initializers .section-name}

Extensions can add new initializers to existing types. This enables you to extend other types to accept your own custom types as initializer parameters, or to provide additional initialization options that were not included as part of the type’s original implementation.

Extensions can add new convenience initializers to a class, but they cannot add new designated initializers or deinitializers to a class. Designated initializers and deinitializers must always be provided by the original class implementation.



Note

If you use an extension to add an initializer to a value type that provides default values for all of its stored properties and does not define any custom initializers, you can call the default initializer and memberwise initializer for that value type from within your extension’s initializer.

This would not be the case if you had written the initializer as part of the value type’s original implementation, as described in [Initializer Delegation for Value Types](Initialization.md#TP40016643-CH18-ID215).



The example below defines a custom `Rect`{.code-voice} structure to represent a geometric rectangle. The example also defines two supporting structures called `Size`{.code-voice} and `Point`{.code-voice}, both of which provide default values of `0.0`{.code-voice} for all of their properties:







1.  `struct`{.code-voice} `Size`{.vc} {
2.  `    var`{.code-voice} `width`{.vc} = `0.0`{.m}, `height`{.vc} = `0.0`{.m}
3.  `}`{.code-voice}
4.  `struct`{.code-voice} `Point`{.vc} {
5.  `    var`{.code-voice} `x`{.vc} = `0.0`{.m}, `y`{.vc} = `0.0`{.m}
6.  `}`{.code-voice}
7.  `struct`{.code-voice} `Rect`{.vc} {
8.  `    var`{.code-voice} `origin`{.vc} = `Point`{.vc}()
9.  `    var`{.code-voice} `size`{.vc} = `Size`{.vc}()
10. `}`{.code-voice}







Because the `Rect`{.code-voice} structure provides default values for all of its properties, it receives a default initializer and a memberwise initializer automatically, as described in [Default Initializers](Initialization.md#TP40016643-CH18-ID213). These initializers can be used to create new `Rect`{.code-voice} instances:







1.  `let`{.code-voice} `defaultRect`{.vc} = `Rect`{.vc}()
2.  `let`{.code-voice} `memberwiseRect`{.vc} = `Rect`{.vc}(`origin`{.vc}: `Point`{.vc}(`x`{.vc}: `2.0`{.m}, `y`{.vc}: `2.0`{.m}),
3.  `    size`{.code-voice}: `Size`{.vc}(`width`{.vc}: `5.0`{.m}, `height`{.vc}: `5.0`{.m}))







You can extend the `Rect`{.code-voice} structure to provide an additional initializer that takes a specific center point and size:







1.  `extension`{.code-voice} `Rect`{.n} {
2.  `    init`{.code-voice}(`center`{.vc}: `Point`{.n}, `size`{.vc}: `Size`{.n}) {
3.  `        let`{.code-voice} `originX`{.vc} = `center`{.vc}.`x`{.vc} - (`size`{.vc}.`width`{.vc} / `2`{.m})
4.  `        let`{.code-voice} `originY`{.vc} = `center`{.vc}.`y`{.vc} - (`size`{.vc}.`height`{.vc} / `2`{.m})
5.  `        self`{.code-voice}.`init`{.kt}(`origin`{.vc}: `Point`{.vc}(`x`{.vc}: `originX`{.vc}, `y`{.vc}: `originY`{.vc}), `size`{.vc}: `size`{.vc})
6.  `    }`{.code-voice}
7.  `}`{.code-voice}







This new initializer starts by calculating an appropriate origin point based on the provided `center`{.code-voice} point and `size`{.code-voice} value. The initializer then calls the structure’s automatic memberwise initializer `init(origin:size:)`{.code-voice}, which stores the new origin and size values in the appropriate properties:







1.  `let`{.code-voice} `centerRect`{.vc} = `Rect`{.vc}(`center`{.vc}: `Point`{.vc}(`x`{.vc}: `4.0`{.m}, `y`{.vc}: `4.0`{.m}),
2.  `    size`{.code-voice}: `Size`{.vc}(`width`{.vc}: `3.0`{.m}, `height`{.vc}: `3.0`{.m}))
3.  `// centerRect's origin is (2.5, 2.5) and its size is (3.0, 3.0)`{.code-voice}









Note

If you provide a new initializer with an extension, you are still responsible for making sure that each instance is fully initialized once the initializer completes.







[‌](){#TP40016643-CH24-ID154}
### Methods {#methods .section-name}

Extensions can add new instance methods and type methods to existing types. The following example adds a new instance method called `repetitions`{.code-voice} to the `Int`{.code-voice} type:







1.  `extension`{.code-voice} `Int`{.n} {
2.  `    func`{.code-voice} `repetitions`{.vc}(`task`{.vc}: () -&gt; `Void`{.n}) {
3.  `        for`{.code-voice} `_`{.kt} `in`{.kt} `0`{.m}..&lt;`self`{.kt} {
4.  `            task`{.code-voice}()
5.  `        }`{.code-voice}
6.  `    }`{.code-voice}
7.  `}`{.code-voice}







The `repetitions(_:)`{.code-voice} method takes a single argument of type `() -> Void`{.code-voice}, which indicates a function that has no parameters and does not return a value.

After defining this extension, you can call the `repetitions(_:)`{.code-voice} method on any integer number to perform a task that many number of times:







1.  `3`{.code-voice}.`repetitions`{.vc}({
2.  `    print`{.code-voice}(`"Hello!"`{.s})
3.  `})`{.code-voice}
4.  `// Hello!`{.code-voice}
5.  `// Hello!`{.code-voice}
6.  `// Hello!`{.code-voice}







Use trailing closure syntax to make the call more succinct:







1.  `3`{.code-voice}.`repetitions`{.vc} {
2.  `    print`{.code-voice}(`"Goodbye!"`{.s})
3.  `}`{.code-voice}
4.  `// Goodbye!`{.code-voice}
5.  `// Goodbye!`{.code-voice}
6.  `// Goodbye!`{.code-voice}









[‌](){#TP40016643-CH24-ID155}
### Mutating Instance Methods {#mutating-instance-methods .section-name}

Instance methods added with an extension can also modify (or *mutate*) the instance itself. Structure and enumeration methods that modify `self`{.code-voice} or its properties must mark the instance method as `mutating`{.code-voice}, just like mutating methods from an original implementation.

The example below adds a new mutating method called `square`{.code-voice} to Swift’s `Int`{.code-voice} type, which squares the original value:







1.  `extension`{.code-voice} `Int`{.n} {
2.  `    mutating`{.code-voice} `func`{.kt} `square`{.vc}() {
3.  `        self`{.code-voice} = `self`{.kt} \* `self`{.kt}
4.  `    }`{.code-voice}
5.  `}`{.code-voice}
6.  `var`{.code-voice} `someInt`{.vc} = `3`{.m}
7.  `someInt`{.code-voice}.`square`{.vc}()
8.  `// someInt is now 9`{.code-voice}













[‌](){#TP40016643-CH24-ID156}
### Subscripts {#subscripts .section-name}

Extensions can add new subscripts to an existing type. This example adds an integer subscript to Swift’s built-in `Int`{.code-voice} type. This subscript `[n]`{.code-voice} returns the decimal digit `n`{.code-voice} places in from the right of the number:

-   `123456789[0]`{.code-voice} returns `9`{.code-voice}

-   `123456789[1]`{.code-voice} returns `8`{.code-voice}

…and so on:







1.  `extension`{.code-voice} `Int`{.n} {
2.  `    subscript`{.code-voice}(`var`{.kt} `digitIndex`{.vc}: `Int`{.n}) -&gt; `Int`{.n} {
3.  `        var`{.code-voice} `decimalBase`{.vc} = `1`{.m}
4.  `        while`{.code-voice} `digitIndex`{.vc} &gt; `0`{.m} {
5.  `            decimalBase`{.code-voice} \*= `10`{.m}
6.  `            --digitIndex`{.code-voice}
7.  `        }`{.code-voice}
8.  `        return`{.code-voice} (`self`{.kt} / `decimalBase`{.vc}) % `10`{.m}
9.  `    }`{.code-voice}
10. `}`{.code-voice}
11. `746381295`{.code-voice}\[`0`{.m}\]
12. `// returns 5`{.code-voice}
13. `746381295`{.code-voice}\[`1`{.m}\]
14. `// returns 9`{.code-voice}
15. `746381295`{.code-voice}\[`2`{.m}\]
16. `// returns 2`{.code-voice}
17. `746381295`{.code-voice}\[`8`{.m}\]
18. `// returns 7`{.code-voice}







If the `Int`{.code-voice} value does not have enough digits for the requested index, the subscript implementation returns `0`{.code-voice}, as if the number had been padded with zeros to the left:







1.  `746381295`{.code-voice}\[`9`{.m}\]
2.  `// returns 0, as if you had requested:`{.code-voice}
3.  `0746381295`{.code-voice}\[`9`{.m}\]











[‌](){#TP40016643-CH24-ID157}
### Nested Types {#nested-types .section-name}

Extensions can add new nested types to existing classes, structures and enumerations:







1.  `extension`{.code-voice} `Int`{.n} {
2.  `    enum`{.code-voice} `Kind`{.vc} {
3.  `        case`{.code-voice} `Negative`{.vc}, `Zero`{.vc}, `Positive`{.vc}
4.  `    }`{.code-voice}
5.  `    var`{.code-voice} `kind`{.vc}: `Kind`{.n} {
6.  `        switch`{.code-voice} `self`{.kt} {
7.  `        case`{.code-voice} `0`{.m}:
8.  `            return`{.code-voice} .`Zero`{.vc}
9.  `        case`{.code-voice} `let`{.kt} `x`{.vc} `where`{.kt} `x`{.vc} &gt; `0`{.m}:
10. `            return`{.code-voice} .`Positive`{.vc}
11. `        default`{.code-voice}:
12. `            return`{.code-voice} .`Negative`{.vc}
13. `        }`{.code-voice}
14. `    }`{.code-voice}
15. `}`{.code-voice}







This example adds a new nested enumeration to `Int`{.code-voice}. This enumeration, called `Kind`{.code-voice}, expresses the kind of number that a particular integer represents. Specifically, it expresses whether the number is negative, zero, or positive.

This example also adds a new computed instance property to `Int`{.code-voice}, called `kind`{.code-voice}, which returns the appropriate `Kind`{.code-voice} enumeration case for that integer.

The nested enumeration can now be used with any `Int`{.code-voice} value:







1.  `func`{.code-voice} `printIntegerKinds`{.vc}(`numbers`{.vc}: \[`Int`{.n}\]) {
2.  `    for`{.code-voice} `number`{.vc} `in`{.kt} `numbers`{.vc} {
3.  `        switch`{.code-voice} `number`{.vc}.`kind`{.vc} {
4.  `        case`{.code-voice} .`Negative`{.vc}:
5.  `            print`{.code-voice}(`"- "`{.s}, `terminator`{.vc}: `""`{.s})
6.  `        case`{.code-voice} .`Zero`{.vc}:
7.  `            print`{.code-voice}(`"0 "`{.s}, `terminator`{.vc}: `""`{.s})
8.  `        case`{.code-voice} .`Positive`{.vc}:
9.  `            print`{.code-voice}(`"+ "`{.s}, `terminator`{.vc}: `""`{.s})
10. `        }`{.code-voice}
11. `    }`{.code-voice}
12. `    print`{.code-voice}(`""`{.s})
13. `}`{.code-voice}
14. `printIntegerKinds`{.code-voice}(\[`3`{.m}, `19`{.m}, -`27`{.m}, `0`{.m}, -`6`{.m}, `0`{.m}, `7`{.m}\])
15. `// prints "+ + - 0 - 0 +"`{.code-voice}







This function, `printIntegerKinds`{.code-voice}, takes an input array of `Int`{.code-voice} values and iterates over those values in turn. For each integer in the array, the function considers the `kind`{.code-voice} computed property for that integer, and prints an appropriate description.



Note

`number.kind`{.code-voice} is already known to be of type `Int.Kind`{.code-voice}. Because of this, all of the `Int.Kind`{.code-voice} case values can be written in shorthand form inside the `switch`{.code-voice} statement, such as `.Negative`{.code-voice} rather than `Int.Kind.Negative`{.code-voice}.








