



[‌](){#TP40016643-CH12}[‌](){#TP40016643-CH12-ID145}
Enumerations {#enumerations .chapter-name}
------------



An *enumeration* defines a common type for a group of related values and enables you to work with those values in a type-safe way within your code.

If you are familiar with C, you will know that C enumerations assign related names to a set of integer values. Enumerations in Swift are much more flexible, and do not have to provide a value for each case of the enumeration. If a value (known as a “raw” value) *is* provided for each enumeration case, the value can be a string, a character, or a value of any integer or floating-point type.

Alternatively, enumeration cases can specify associated values of *any* type to be stored along with each different case value, much as unions or variants do in other languages. You can define a common set of related cases as part of one enumeration, each of which has a different set of values of appropriate types associated with it.

Enumerations in Swift are first-class types in their own right. They adopt many features traditionally supported only by classes, such as computed properties to provide additional information about the enumeration’s current value, and instance methods to provide functionality related to the values the enumeration represents. Enumerations can also define initializers to provide an initial case value; can be extended to expand their functionality beyond their original implementation; and can conform to protocols to provide standard functionality.

For more on these capabilities, see [Properties](Properties.md), [Methods](Methods.md), [Initialization](Initialization.md), [Extensions](Extensions.md), and [Protocols](Protocols.md).





[‌](){#TP40016643-CH12-ID146}
### Enumeration Syntax {#enumeration-syntax .section-name}

You introduce enumerations with the `enum`{.code-voice} keyword and place their entire definition within a pair of braces:







1.  `enum`{.code-voice} `SomeEnumeration`{.vc} {
2.  `    // enumeration definition goes here`{.code-voice}
3.  `}`{.code-voice}







Here’s an example for the four main points of a compass:







1.  `enum`{.code-voice} `CompassPoint`{.vc} {
2.  `    case`{.code-voice} `North`{.vc}
3.  `    case`{.code-voice} `South`{.vc}
4.  `    case`{.code-voice} `East`{.vc}
5.  `    case`{.code-voice} `West`{.vc}
6.  `}`{.code-voice}







The values defined in an enumeration (such as `North`{.code-voice}, `South`{.code-voice}, `East`{.code-voice}, and `West`{.code-voice}) are its *enumeration cases*. You use the `case`{.code-voice} keyword to introduce new enumeration cases.



Note

Unlike C and Objective-C, Swift enumeration cases are not assigned a default integer value when they are created. In the `CompassPoint`{.code-voice} example above, `North`{.code-voice}, `South`{.code-voice}, `East`{.code-voice} and `West`{.code-voice} do not implicitly equal `0`{.code-voice}, `1`{.code-voice}, `2`{.code-voice} and `3`{.code-voice}. Instead, the different enumeration cases are fully-fledged values in their own right, with an explicitly-defined type of `CompassPoint`{.code-voice}.



Multiple cases can appear on a single line, separated by commas:







1.  `enum`{.code-voice} `Planet`{.vc} {
2.  `    case`{.code-voice} `Mercury`{.vc}, `Venus`{.vc}, `Earth`{.vc}, `Mars`{.vc}, `Jupiter`{.vc}, `Saturn`{.vc}, `Uranus`{.vc}, `Neptune`{.vc}
3.  `}`{.code-voice}







Each enumeration definition defines a brand new type. Like other types in Swift, their names (such as `CompassPoint`{.code-voice} and `Planet`{.code-voice}) should start with a capital letter. Give enumeration types singular rather than plural names, so that they read as self-evident:







1.  `var`{.code-voice} `directionToHead`{.vc} = `CompassPoint`{.vc}.`West`{.vc}







The type of `directionToHead`{.code-voice} is inferred when it is initialized with one of the possible values of `CompassPoint`{.code-voice}. Once `directionToHead`{.code-voice} is declared as a `CompassPoint`{.code-voice}, you can set it to a different `CompassPoint`{.code-voice} value using a shorter dot syntax:







1.  `directionToHead`{.code-voice} = .`East`{.vc}







The type of `directionToHead`{.code-voice} is already known, and so you can drop the type when setting its value. This makes for highly readable code when working with explicitly-typed enumeration values.





[‌](){#TP40016643-CH12-ID147}
### Matching Enumeration Values with a Switch Statement {#matching-enumeration-values-with-a-switch-statement .section-name}

You can match individual enumeration values with a `switch`{.code-voice} statement:







1.  `directionToHead`{.code-voice} = .`South`{.vc}
2.  `switch`{.code-voice} `directionToHead`{.vc} {
3.  `case`{.code-voice} .`North`{.vc}:
4.  `    print`{.code-voice}(`"Lots of planets have a north"`{.s})
5.  `case`{.code-voice} .`South`{.vc}:
6.  `    print`{.code-voice}(`"Watch out for penguins"`{.s})
7.  `case`{.code-voice} .`East`{.vc}:
8.  `    print`{.code-voice}(`"Where the sun rises"`{.s})
9.  `case`{.code-voice} .`West`{.vc}:
10. `    print`{.code-voice}(`"Where the skies are blue"`{.s})
11. `}`{.code-voice}
12. `// prints "Watch out for penguins"`{.code-voice}







You can read this code as:

“Consider the value of `directionToHead`{.code-voice}. In the case where it equals `.North`{.code-voice}, print `"Lots of planets have a north"`{.code-voice}. In the case where it equals `.South`{.code-voice}, print `"Watch out for penguins"`{.code-voice}.”

…and so on.

As described in [Control Flow](ControlFlow.md), a `switch`{.code-voice} statement must be exhaustive when considering an enumeration’s cases. If the `case`{.code-voice} for `.West`{.code-voice} is omitted, this code does not compile, because it does not consider the complete list of `CompassPoint`{.code-voice} cases. Requiring exhaustiveness ensures that enumeration cases are not accidentally omitted.

When it is not appropriate to provide a `case`{.code-voice} for every enumeration case, you can provide a `default`{.code-voice} case to cover any cases that are not addressed explicitly:







1.  `let`{.code-voice} `somePlanet`{.vc} = `Planet`{.vc}.`Earth`{.vc}
2.  `switch`{.code-voice} `somePlanet`{.vc} {
3.  `case`{.code-voice} .`Earth`{.vc}:
4.  `    print`{.code-voice}(`"Mostly harmless"`{.s})
5.  `default`{.code-voice}:
6.  `    print`{.code-voice}(`"Not a safe place for humans"`{.s})
7.  `}`{.code-voice}
8.  `// prints "Mostly harmless"`{.code-voice}











[‌](){#TP40016643-CH12-ID148}
### Associated Values {#associated-values .section-name}

The examples in the previous section show how the cases of an enumeration are a defined (and typed) value in their own right. You can set a constant or variable to `Planet.Earth`{.code-voice}, and check for this value later. However, it is sometimes useful to be able to store *associated values* of other types alongside these case values. This enables you to store additional custom information along with the case value, and permits this information to vary each time you use that case in your code.

You can define Swift enumerations to store associated values of any given type, and the value types can be different for each case of the enumeration if needed. Enumerations similar to these are known as *discriminated unions*, *tagged unions*, or *variants* in other programming languages.

For example, suppose an inventory tracking system needs to track products by two different types of barcode. Some products are labeled with 1D barcodes in UPC-A format, which uses the numbers `0`{.code-voice} to `9`{.code-voice}. Each barcode has a “number system” digit, followed by five “manufacturer code” digits and five “product code” digits. These are followed by a “check” digit to verify that the code has been scanned correctly:




![image: ../Art/barcode\_UPC\_2x.png](Art/barcode_UPC_2x.png){width="252" height="120"}



Other products are labeled with 2D barcodes in QR code format, which can use any ISO 8859-1 character and can encode a string up to 2,953 characters long:




![image: ../Art/barcode\_QR\_2x.png](Art/barcode_QR_2x.png){width="169" height="169"}



It would be convenient for an inventory tracking system to be able to store UPC-A barcodes as a tuple of four integers, and QR code barcodes as a string of any length.

In Swift, an enumeration to define product barcodes of either type might look like this:







1.  `enum`{.code-voice} `Barcode`{.vc} {
2.  `    case`{.code-voice} `UPCA`{.vc}(`Int`{.vc}, `Int`{.vc}, `Int`{.vc}, `Int`{.vc})
3.  `    case`{.code-voice} `QRCode`{.vc}(`String`{.vc})
4.  `}`{.code-voice}







This can be read as:

“Define an enumeration type called `Barcode`{.code-voice}, which can take either a value of `UPCA`{.code-voice} with an associated value of type (`Int`{.code-voice}, `Int`{.code-voice}, `Int`{.code-voice}, `Int`{.code-voice}), or a value of `QRCode`{.code-voice} with an associated value of type `String`{.code-voice}.”

This definition does not provide any actual `Int`{.code-voice} or `String`{.code-voice} values—it just defines the *type* of associated values that `Barcode`{.code-voice} constants and variables can store when they are equal to `Barcode.UPCA`{.code-voice} or `Barcode.QRCode`{.code-voice}.

New barcodes can then be created using either type:







1.  `var`{.code-voice} `productBarcode`{.vc} = `Barcode`{.vc}.`UPCA`{.vc}(`8`{.m}, `85909`{.m}, `51226`{.m}, `3`{.m})







This example creates a new variable called `productBarcode`{.code-voice} and assigns it a value of `Barcode.UPCA`{.code-voice} with an associated tuple value of `(8, 85909, 51226, 3)`{.code-voice}.

The same product can be assigned a different type of barcode:







1.  `productBarcode`{.code-voice} = .`QRCode`{.vc}(`"ABCDEFGHIJKLMNOP"`{.s})







At this point, the original `Barcode.UPCA`{.code-voice} and its integer values are replaced by the new `Barcode.QRCode`{.code-voice} and its string value. Constants and variables of type `Barcode`{.code-voice} can store either a `.UPCA`{.code-voice} or a `.QRCode`{.code-voice} (together with their associated values), but they can only store one of them at any given time.

The different barcode types can be checked using a switch statement, as before. This time, however, the associated values can be extracted as part of the switch statement. You extract each associated value as a constant with the `let`{.code-voice} prefix for use within the `switch`{.code-voice} case’s body:







1.  `switch`{.code-voice} `productBarcode`{.vc} {
2.  `case`{.code-voice} .`UPCA`{.vc}(`let`{.kt} `numberSystem`{.vc}, `let`{.kt} `manufacturer`{.vc}, `let`{.kt} `product`{.vc}, `let`{.kt} `check`{.vc}):
3.  `    print`{.code-voice}(`"UPC-A: `{.s}\\(`numberSystem`{.vc})`, `{.s}\\(`manufacturer`{.vc})`, `{.s}\\(`product`{.vc})`, `{.s}\\(`check`{.vc})`."`{.s})
4.  `case`{.code-voice} .`QRCode`{.vc}(`let`{.kt} `productCode`{.vc}):
5.  `    print`{.code-voice}(`"QR code: `{.s}\\(`productCode`{.vc})`."`{.s})
6.  `}`{.code-voice}
7.  `// prints "QR code: ABCDEFGHIJKLMNOP."`{.code-voice}







If all of the associated values for an enumeration case are extracted as constants, or if all are extracted as variables, you can place a single `let`{.code-voice} annotation before the case name, for brevity:







1.  `switch`{.code-voice} `productBarcode`{.vc} {
2.  `case`{.code-voice} `let`{.kt} .`UPCA`{.vc}(`numberSystem`{.vc}, `manufacturer`{.vc}, `product`{.vc}, `check`{.vc}):
3.  `    print`{.code-voice}(`"UPC-A: `{.s}\\(`numberSystem`{.vc})`, `{.s}\\(`manufacturer`{.vc})`, `{.s}\\(`product`{.vc})`, `{.s}\\(`check`{.vc})`."`{.s})
4.  `case`{.code-voice} `let`{.kt} .`QRCode`{.vc}(`productCode`{.vc}):
5.  `    print`{.code-voice}(`"QR code: `{.s}\\(`productCode`{.vc})`."`{.s})
6.  `}`{.code-voice}
7.  `// prints "QR code: ABCDEFGHIJKLMNOP."`{.code-voice}











[‌](){#TP40016643-CH12-ID149}
### Raw Values {#raw-values .section-name}

The barcode example in [Associated Values](Enumerations.md#TP40016643-CH12-ID148) shows how cases of an enumeration can declare that they store associated values of different types. As an alternative to associated values, enumeration cases can come prepopulated with default values (called *raw values*), which are all of the same type.

Here’s an example that stores raw ASCII values alongside named enumeration cases:







1.  `enum`{.code-voice} `ASCIIControlCharacter`{.vc}: `Character`{.n} {
2.  `    case`{.code-voice} `Tab`{.vc} = `"\t"`{.s}
3.  `    case`{.code-voice} `LineFeed`{.vc} = `"\n"`{.s}
4.  `    case`{.code-voice} `CarriageReturn`{.vc} = `"\r"`{.s}
5.  `}`{.code-voice}







Here, the raw values for an enumeration called `ASCIIControlCharacter`{.code-voice} are defined to be of type `Character`{.code-voice}, and are set to some of the more common ASCII control characters. `Character`{.code-voice} values are described in [Strings and Characters](StringsAndCharacters.md).

Raw values can be strings, characters, or any of the integer or floating-point number types. Each raw value must be unique within its enumeration declaration.



Note

Raw values are *not* the same as associated values. Raw values are set to prepopulated values when you first define the enumeration in your code, like the three ASCII codes above. The raw value for a particular enumeration case is always the same. Associated values are set when you create a new constant or variable based on one of the enumeration’s cases, and can be different each time you do so.





[‌](){#TP40016643-CH12-ID535}
### Implicitly Assigned Raw Values {#implicitly-assigned-raw-values .section-name}

When you’re working with enumerations that store integer or string raw values, you don’t have to explicitly assign a raw value for each case. When you don’t, Swift will automatically assign the values for you.

For instance, when integers are used for raw values, the implicit value for each case is one more than the previous case. If the first case doesn’t have a value set, its value is `0`{.code-voice}.

The enumeration below is a refinement of the earlier `Planet`{.code-voice} enumeration, with integer raw values to represent each planet’s order from the sun:







1.  `enum`{.code-voice} `Planet`{.vc}: `Int`{.n} {
2.  `    case`{.code-voice} `Mercury`{.vc} = `1`{.m}, `Venus`{.vc}, `Earth`{.vc}, `Mars`{.vc}, `Jupiter`{.vc}, `Saturn`{.vc}, `Uranus`{.vc}, `Neptune`{.vc}
3.  `}`{.code-voice}







In the example above, `Planet.Mercury`{.code-voice} has an explicit raw value of `1`{.code-voice}, `Planet.Venus`{.code-voice} has an implicit raw value of `2`{.code-voice}, and so on.

When strings are used for raw values, the implicit value for each case is the text of that case’s name.

The enumeration below is a refinement of the earlier `CompassPoint`{.code-voice} enumeration, with string raw values to represent each direction’s name:







1.  `enum`{.code-voice} `CompassPoint`{.vc}: `String`{.n} {
2.  `    case`{.code-voice} `North`{.vc}, `South`{.vc}, `East`{.vc}, `West`{.vc}
3.  `}`{.code-voice}







In the example above, `CompassPoint.South`{.code-voice} has an implicit raw value of `"South"`{.code-voice}, and so on.

You access the raw value of an enumeration case with its `rawValue`{.code-voice} property:







1.  `let`{.code-voice} `earthsOrder`{.vc} = `Planet`{.vc}.`Earth`{.vc}.`rawValue`{.vc}
2.  `// earthsOrder is 3`{.code-voice}
3.  ` `{.code-voice}
4.  `let`{.code-voice} `sunsetDirection`{.vc} = `CompassPoint`{.vc}.`West`{.vc}.`rawValue`{.vc}
5.  `// sunsetDirection is "West"`{.code-voice}











[‌](){#TP40016643-CH12-ID150}
### Initializing from a Raw Value {#initializing-from-a-raw-value .section-name}

If you define an enumeration with a raw-value type, the enumeration automatically receives an initializer that takes a value of the raw value’s type (as a parameter called `rawValue`{.code-voice}) and returns either an enumeration case or `nil`{.code-voice}. You can use this initializer to try to create a new instance of the enumeration.

This example identifies Uranus from its raw value of `7`{.code-voice}:







1.  `let`{.code-voice} `possiblePlanet`{.vc} = `Planet`{.vc}(`rawValue`{.vc}: `7`{.m})
2.  `// possiblePlanet is of type Planet? and equals Planet.Uranus`{.code-voice}







Not all possible `Int`{.code-voice} values will find a matching planet, however. Because of this, the raw value initializer always returns an *optional* enumeration case. In the example above, `possiblePlanet`{.code-voice} is of type `Planet?`{.code-voice}, or “optional `Planet`{.code-voice}.”



Note

The raw value initializer is a failable initializer, because not every raw value will return an enumeration case. For more information, see [Failable Initializers](Declarations.md#TP40016643-CH34-ID376).



If you try to find a planet with a position of `9`{.code-voice}, the optional `Planet`{.code-voice} value returned by the raw value initializer will be `nil`{.code-voice}:







1.  `let`{.code-voice} `positionToFind`{.vc} = `9`{.m}
2.  `if`{.code-voice} `let`{.kt} `somePlanet`{.vc} = `Planet`{.vc}(`rawValue`{.vc}: `positionToFind`{.vc}) {
3.  `    switch`{.code-voice} `somePlanet`{.vc} {
4.  `    case`{.code-voice} .`Earth`{.vc}:
5.  `        print`{.code-voice}(`"Mostly harmless"`{.s})
6.  `    default`{.code-voice}:
7.  `        print`{.code-voice}(`"Not a safe place for humans"`{.s})
8.  `    }`{.code-voice}
9.  `} else`{.code-voice} {
10. `    print`{.code-voice}(`"There isn't a planet at position `{.s}\\(`positionToFind`{.vc})`"`{.s})
11. `}`{.code-voice}
12. `// prints "There isn't a planet at position 9"`{.code-voice}







This example uses optional binding to try to access a planet with a raw value of `9`{.code-voice}. The statement `if let somePlanet = Planet(rawValue: 9)`{.code-voice} creates an optional `Planet`{.code-voice}, and sets `somePlanet`{.code-voice} to the value of that optional `Planet`{.code-voice} if it can be retrieved. In this case, it is not possible to retrieve a planet with a position of `9`{.code-voice}, and so the `else`{.code-voice} branch is executed instead.







[‌](){#TP40016643-CH12-ID536}
### Recursive Enumerations {#recursive-enumerations .section-name}

Enumerations work well for modeling data when there is a fixed number of possibilities that need to be considered, such as the operations used for doing simple integer arithmetic. These operations let you combine simple arithmetic expressions that are made up of integers such as `5`{.code-voice} into more complex ones such as `5 + 4`{.code-voice}.

One important characteristic of arithmetic expressions is that they can be nested. For example, the expression `(5 + 4) * 2`{.code-voice} has a number on the right hand side of the multiplication and another expression on the left hand side of the multiplication. Because the data is nested, the enumeration used to store the data also needs to support nesting—this means the enumeration needs to be recursive.

A *recursive enumeration* is an enumeration that has another instance of the enumeration as the associated value for one or more of the enumeration cases. The compiler has to insert a layer of indirection when it works with recursive enumerations. You indicate that an enumeration case is recursive by writing `indirect`{.code-voice} before it.

For example, here is an enumeration that stores simple arithmetic expressions:







1.  `enum`{.code-voice} `ArithmeticExpression`{.vc} {
2.  `    case`{.code-voice} `Number`{.vc}(`Int`{.vc})
3.  `    indirect`{.code-voice} `case`{.kt} `Addition`{.vc}(`ArithmeticExpression`{.vc}, `ArithmeticExpression`{.vc})
4.  `    indirect`{.code-voice} `case`{.kt} `Multiplication`{.vc}(`ArithmeticExpression`{.vc}, `ArithmeticExpression`{.vc})
5.  `}`{.code-voice}







You can also write `indirect`{.code-voice} before the beginning of the enumeration, to enable indirection for all of the enumeration’s cases that need it:







1.  `indirect`{.code-voice} `enum`{.kt} `ArithmeticExpression`{.vc} {
2.  `    case`{.code-voice} `Number`{.vc}(`Int`{.vc})
3.  `    case`{.code-voice} `Addition`{.vc}(`ArithmeticExpression`{.vc}, `ArithmeticExpression`{.vc})
4.  `    case`{.code-voice} `Multiplication`{.vc}(`ArithmeticExpression`{.vc}, `ArithmeticExpression`{.vc})
5.  `}`{.code-voice}







This enumeration can store three kinds of arithmetic expressions: a plain number, the addition of two expressions, and the multiplication of two expressions. The `Addition`{.code-voice} and `Multiplication`{.code-voice} cases have associated values that are also arithmetic expressions—these associated values make it possible to nest expressions.

A recursive function is a straightforward way to work with data that has a recursive structure. For example, here’s a function that evaluates an arithmetic expression:







1.  `func`{.code-voice} `evaluate`{.vc}(`expression`{.vc}: `ArithmeticExpression`{.n}) -&gt; `Int`{.n} {
2.  `    switch`{.code-voice} `expression`{.vc} {
3.  `    case`{.code-voice} .`Number`{.vc}(`let`{.kt} `value`{.vc}):
4.  `        return`{.code-voice} `value`{.vc}
5.  `    case`{.code-voice} .`Addition`{.vc}(`let`{.kt} `left`{.vc}, `let`{.kt} `right`{.vc}):
6.  `        return`{.code-voice} `evaluate`{.vc}(`left`{.vc}) + `evaluate`{.vc}(`right`{.vc})
7.  `    case`{.code-voice} .`Multiplication`{.vc}(`let`{.kt} `left`{.vc}, `let`{.kt} `right`{.vc}):
8.  `        return`{.code-voice} `evaluate`{.vc}(`left`{.vc}) \* `evaluate`{.vc}(`right`{.vc})
9.  `    }`{.code-voice}
10. `}`{.code-voice}
11. ` `{.code-voice}
12. `// evaluate (5 + 4) * 2`{.code-voice}
13. `let`{.code-voice} `five`{.vc} = `ArithmeticExpression`{.vc}.`Number`{.vc}(`5`{.m})
14. `let`{.code-voice} `four`{.vc} = `ArithmeticExpression`{.vc}.`Number`{.vc}(`4`{.m})
15. `let`{.code-voice} `sum`{.vc} = `ArithmeticExpression`{.vc}.`Addition`{.vc}(`five`{.vc}, `four`{.vc})
16. `let`{.code-voice} `product`{.vc} = `ArithmeticExpression`{.vc}.`Multiplication`{.vc}(`sum`{.vc}, `ArithmeticExpression`{.vc}.`Number`{.vc}(`2`{.m}))
17. `print`{.code-voice}(`evaluate`{.vc}(`product`{.vc}))
18. `// prints "18"`{.code-voice}







This function evaluates a plain number by simply returning the associated value. It evaluates an addition or multiplication by evaluating the expression on the left hand side, evaluating the expression on the right hand side, and then adding them or multiplying them.






