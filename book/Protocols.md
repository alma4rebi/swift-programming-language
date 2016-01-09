



[‌](){#TP40016643-CH25}[‌](){#TP40016643-CH25-ID267}
Protocols {#protocols .chapter-name}
---------



A *protocol* defines a blueprint of methods, properties, and other requirements that suit a particular task or piece of functionality. The protocol can then be *adopted* by a class, structure, or enumeration to provide an actual implementation of those requirements. Any type that satisfies the requirements of a protocol is said to *conform* to that protocol.

In addition to specifying requirements that conforming types must implement, you can extend a protocol to implement some of these requirements or to implement additional functionality that conforming types can take advantage of.





[‌](){#TP40016643-CH25-ID268}
### Protocol Syntax {#protocol-syntax .section-name}

You define protocols in a very similar way to classes, structures, and enumerations:







1.  `protocol`{.code-voice} `SomeProtocol`{.vc} {
2.  `    // protocol definition goes here`{.code-voice}
3.  `}`{.code-voice}







Custom types state that they adopt a particular protocol by placing the protocol’s name after the type’s name, separated by a colon, as part of their definition. Multiple protocols can be listed, and are separated by commas:







1.  `struct`{.code-voice} `SomeStructure`{.vc}: `FirstProtocol`{.n}, `AnotherProtocol`{.n} {
2.  `    // structure definition goes here`{.code-voice}
3.  `}`{.code-voice}







If a class has a superclass, list the superclass name before any protocols it adopts, followed by a comma:







1.  `class`{.code-voice} `SomeClass`{.vc}: `SomeSuperclass`{.n}, `FirstProtocol`{.n}, `AnotherProtocol`{.n} {
2.  `    // class definition goes here`{.code-voice}
3.  `}`{.code-voice}











[‌](){#TP40016643-CH25-ID269}
### Property Requirements {#property-requirements .section-name}

A protocol can require any conforming type to provide an instance property or type property with a particular name and type. The protocol doesn’t specify whether the property should be a stored property or a computed property—it only specifies the required property name and type. The protocol also specifies whether each property must be gettable or gettable *and* settable.

If a protocol requires a property to be gettable and settable, that property requirement cannot be fulfilled by a constant stored property or a read-only computed property. If the protocol only requires a property to be gettable, the requirement can be satisfied by any kind of property, and it is valid for the property to be also settable if this is useful for your own code.

Property requirements are always declared as variable properties, prefixed with the `var`{.code-voice} keyword. Gettable and settable properties are indicated by writing `{ get set }`{.code-voice} after their type declaration, and gettable properties are indicated by writing `{ get }`{.code-voice}.







1.  `protocol`{.code-voice} `SomeProtocol`{.vc} {
2.  `    var`{.code-voice} `mustBeSettable`{.vc}: `Int`{.n} { `get`{.kt} `set`{.kt} }
3.  `    var`{.code-voice} `doesNotNeedToBeSettable`{.vc}: `Int`{.n} { `get`{.kt} }
4.  `}`{.code-voice}







Always prefix type property requirements with the `static`{.code-voice} keyword when you define them in a protocol. This rule pertains even though type property requirements can be prefixed with the `class`{.code-voice} or `static`{.code-voice} keyword when implemented by a class:







1.  `protocol`{.code-voice} `AnotherProtocol`{.vc} {
2.  `    static`{.code-voice} `var`{.kt} `someTypeProperty`{.vc}: `Int`{.n} { `get`{.kt} `set`{.kt} }
3.  `}`{.code-voice}







Here’s an example of a protocol with a single instance property requirement:







1.  `protocol`{.code-voice} `FullyNamed`{.vc} {
2.  `    var`{.code-voice} `fullName`{.vc}: `String`{.n} { `get`{.kt} }
3.  `}`{.code-voice}







The `FullyNamed`{.code-voice} protocol requires a conforming type to provide a fully-qualified name. The protocol doesn’t specify anything else about the nature of the conforming type—it only specifies that the type must be able to provide a full name for itself. The protocol states that any `FullyNamed`{.code-voice} type must have a gettable instance property called `fullName`{.code-voice}, which is of type `String`{.code-voice}.

Here’s an example of a simple structure that adopts and conforms to the `FullyNamed`{.code-voice} protocol:







1.  `struct`{.code-voice} `Person`{.vc}: `FullyNamed`{.n} {
2.  `    var`{.code-voice} `fullName`{.vc}: `String`{.n}
3.  `}`{.code-voice}
4.  `let`{.code-voice} `john`{.vc} = `Person`{.vc}(`fullName`{.vc}: `"John Appleseed"`{.s})
5.  `// john.fullName is "John Appleseed"`{.code-voice}







This example defines a structure called `Person`{.code-voice}, which represents a specific named person. It states that it adopts the `FullyNamed`{.code-voice} protocol as part of the first line of its definition.

Each instance of `Person`{.code-voice} has a single stored property called `fullName`{.code-voice}, which is of type `String`{.code-voice}. This matches the single requirement of the `FullyNamed`{.code-voice} protocol, and means that `Person`{.code-voice} has correctly conformed to the protocol. (Swift reports an error at compile-time if a protocol requirement is not fulfilled.)

Here’s a more complex class, which also adopts and conforms to the `FullyNamed`{.code-voice} protocol:







1.  `class`{.code-voice} `Starship`{.vc}: `FullyNamed`{.n} {
2.  `    var`{.code-voice} `prefix`{.vc}: `String`{.n}?
3.  `    var`{.code-voice} `name`{.vc}: `String`{.n}
4.  `    init`{.code-voice}(`name`{.vc}: `String`{.n}, `prefix`{.vc}: `String`{.n}? = `nil`{.kt}) {
5.  `        self`{.code-voice}.`name`{.vc} = `name`{.vc}
6.  `        self`{.code-voice}.`prefix`{.vc} = `prefix`{.vc}
7.  `    }`{.code-voice}
8.  `    var`{.code-voice} `fullName`{.vc}: `String`{.n} {
9.  `        return`{.code-voice} (`prefix`{.vc} != `nil`{.kt} ? `prefix`{.vc}! + `" "`{.s} : `""`{.s}) + `name`{.vc}
10. `    }`{.code-voice}
11. `}`{.code-voice}
12. `var`{.code-voice} `ncc1701`{.vc} = `Starship`{.vc}(`name`{.vc}: `"Enterprise"`{.s}, `prefix`{.vc}: `"USS"`{.s})
13. `// ncc1701.fullName is "USS Enterprise"`{.code-voice}







This class implements the `fullName`{.code-voice} property requirement as a computed read-only property for a starship. Each `Starship`{.code-voice} class instance stores a mandatory `name`{.code-voice} and an optional `prefix`{.code-voice}. The `fullName`{.code-voice} property uses the `prefix`{.code-voice} value if it exists, and prepends it to the beginning of `name`{.code-voice} to create a full name for the starship.





[‌](){#TP40016643-CH25-ID270}
### Method Requirements {#method-requirements .section-name}

Protocols can require specific instance methods and type methods to be implemented by conforming types. These methods are written as part of the protocol’s definition in exactly the same way as for normal instance and type methods, but without curly braces or a method body. Variadic parameters are allowed, subject to the same rules as for normal methods. Default values, however, cannot be specified for method parameters within a protocol’s definition.

As with type property requirements, you always prefix type method requirements with the `static`{.code-voice} keyword when they are defined in a protocol. This is true even though type method requirements are prefixed with the `class`{.code-voice} or `static`{.code-voice} keyword when implemented by a class:







1.  `protocol`{.code-voice} `SomeProtocol`{.vc} {
2.  `    static`{.code-voice} `func`{.kt} `someTypeMethod`{.vc}()
3.  `}`{.code-voice}







The following example defines a protocol with a single instance method requirement:







1.  `protocol`{.code-voice} `RandomNumberGenerator`{.vc} {
2.  `    func`{.code-voice} `random`{.vc}() -&gt; `Double`{.n}
3.  `}`{.code-voice}







This protocol, `RandomNumberGenerator`{.code-voice}, requires any conforming type to have an instance method called `random`{.code-voice}, which returns a `Double`{.code-voice} value whenever it is called. Although it is not specified as part of the protocol, it is assumed that this value will be a number from `0.0`{.code-voice} up to (but not including) `1.0`{.code-voice}.

The `RandomNumberGenerator`{.code-voice} protocol does not make any assumptions about how each random number will be generated—it simply requires the generator to provide a standard way to generate a new random number.

Here’s an implementation of a class that adopts and conforms to the `RandomNumberGenerator`{.code-voice} protocol. This class implements a pseudorandom number generator algorithm known as a *linear congruential generator*:







1.  `class`{.code-voice} `LinearCongruentialGenerator`{.vc}: `RandomNumberGenerator`{.n} {
2.  `    var`{.code-voice} `lastRandom`{.vc} = `42.0`{.m}
3.  `    let`{.code-voice} `m`{.vc} = `139968.0`{.m}
4.  `    let`{.code-voice} `a`{.vc} = `3877.0`{.m}
5.  `    let`{.code-voice} `c`{.vc} = `29573.0`{.m}
6.  `    func`{.code-voice} `random`{.vc}() -&gt; `Double`{.n} {
7.  `        lastRandom`{.code-voice} = ((`lastRandom`{.vc} \* `a`{.vc} + `c`{.vc}) % `m`{.vc})
8.  `        return`{.code-voice} `lastRandom`{.vc} / `m`{.vc}
9.  `    }`{.code-voice}
10. `}`{.code-voice}
11. `let`{.code-voice} `generator`{.vc} = `LinearCongruentialGenerator`{.vc}()
12. `print`{.code-voice}(`"Here's a random number: `{.s}\\(`generator`{.vc}.`random`{.vc}())`"`{.s})
13. `// prints "Here's a random number: 0.37464991998171"`{.code-voice}
14. `print`{.code-voice}(`"And another one: `{.s}\\(`generator`{.vc}.`random`{.vc}())`"`{.s})
15. `// prints "And another one: 0.729023776863283"`{.code-voice}











[‌](){#TP40016643-CH25-ID271}
### Mutating Method Requirements {#mutating-method-requirements .section-name}

It is sometimes necessary for a method to modify (or *mutate*) the instance it belongs to. For instance methods on value types (that is, structures and enumerations) you place the `mutating`{.code-voice} keyword before a method’s `func`{.code-voice} keyword to indicate that the method is allowed to modify the instance it belongs to and any properties of that instance. This process is described in [Modifying Value Types from Within Instance Methods](Methods.md#TP40016643-CH15-ID239).

If you define a protocol instance method requirement that is intended to mutate instances of any type that adopts the protocol, mark the method with the `mutating`{.code-voice} keyword as part of the protocol’s definition. This enables structures and enumerations to adopt the protocol and satisfy that method requirement.



Note

If you mark a protocol instance method requirement as `mutating`{.code-voice}, you do not need to write the `mutating`{.code-voice} keyword when writing an implementation of that method for a class. The `mutating`{.code-voice} keyword is only used by structures and enumerations.



The example below defines a protocol called `Togglable`{.code-voice}, which defines a single instance method requirement called `toggle`{.code-voice}. As its name suggests, the `toggle()`{.code-voice} method is intended to toggle or invert the state of any conforming type, typically by modifying a property of that type.

The `toggle()`{.code-voice} method is marked with the `mutating`{.code-voice} keyword as part of the `Togglable`{.code-voice} protocol definition, to indicate that the method is expected to mutate the state of a conforming instance when it is called:







1.  `protocol`{.code-voice} `Togglable`{.vc} {
2.  `    mutating`{.code-voice} `func`{.kt} `toggle`{.vc}()
3.  `}`{.code-voice}







If you implement the `Togglable`{.code-voice} protocol for a structure or enumeration, that structure or enumeration can conform to the protocol by providing an implementation of the `toggle()`{.code-voice} method that is also marked as `mutating`{.code-voice}.

The example below defines an enumeration called `OnOffSwitch`{.code-voice}. This enumeration toggles between two states, indicated by the enumeration cases `On`{.code-voice} and `Off`{.code-voice}. The enumeration’s `toggle`{.code-voice} implementation is marked as `mutating`{.code-voice}, to match the `Togglable`{.code-voice} protocol’s requirements:







1.  `enum`{.code-voice} `OnOffSwitch`{.vc}: `Togglable`{.n} {
2.  `    case`{.code-voice} `Off`{.vc}, `On`{.vc}
3.  `    mutating`{.code-voice} `func`{.kt} `toggle`{.vc}() {
4.  `        switch`{.code-voice} `self`{.kt} {
5.  `        case`{.code-voice} `Off`{.vc}:
6.  `            self`{.code-voice} = `On`{.vc}
7.  `        case`{.code-voice} `On`{.vc}:
8.  `            self`{.code-voice} = `Off`{.vc}
9.  `        }`{.code-voice}
10. `    }`{.code-voice}
11. `}`{.code-voice}
12. `var`{.code-voice} `lightSwitch`{.vc} = `OnOffSwitch`{.vc}.`Off`{.vc}
13. `lightSwitch`{.code-voice}.`toggle`{.vc}()
14. `// lightSwitch is now equal to .On`{.code-voice}











[‌](){#TP40016643-CH25-ID272}
### Initializer Requirements {#initializer-requirements .section-name}

Protocols can require specific initializers to be implemented by conforming types. You write these initializers as part of the protocol’s definition in exactly the same way as for normal initializers, but without curly braces or an initializer body:







1.  `protocol`{.code-voice} `SomeProtocol`{.vc} {
2.  `    init`{.code-voice}(`someParameter`{.vc}: `Int`{.n})
3.  `}`{.code-voice}









[‌](){#TP40016643-CH25-ID273}
### Class Implementations of Protocol Initializer Requirements {#class-implementations-of-protocol-initializer-requirements .section-name}

You can implement a protocol initializer requirement on a conforming class as either a designated initializer or a convenience initializer. In both cases, you must mark the initializer implementation with the `required`{.code-voice} modifier:







1.  `class`{.code-voice} `SomeClass`{.vc}: `SomeProtocol`{.n} {
2.  `    required`{.code-voice} `init`{.kt}(`someParameter`{.vc}: `Int`{.n}) {
3.  `        // initializer implementation goes here`{.code-voice}
4.  `    }`{.code-voice}
5.  `}`{.code-voice}







The use of the `required`{.code-voice} modifier ensures that you provide an explicit or inherited implementation of the initializer requirement on all subclasses of the conforming class, such that they also conform to the protocol.

For more information on required initializers, see [Required Initializers](Initialization.md#TP40016643-CH18-ID231).



Note

You do not need to mark protocol initializer implementations with the `required`{.code-voice} modifier on classes that are marked with the `final`{.code-voice} modifier, because final classes cannot be subclassed. For more on the `final`{.code-voice} modifier, see [Preventing Overrides](Inheritance.md#TP40016643-CH17-ID202).



If a subclass overrides a designated initializer from a superclass, and also implements a matching initializer requirement from a protocol, mark the initializer implementation with both the `required`{.code-voice} and `override`{.code-voice} modifiers:







1.  `protocol`{.code-voice} `SomeProtocol`{.vc} {
2.  `    init`{.code-voice}()
3.  `}`{.code-voice}
4.  ` `{.code-voice}
5.  `class`{.code-voice} `SomeSuperClass`{.vc} {
6.  `    init`{.code-voice}() {
7.  `        // initializer implementation goes here`{.code-voice}
8.  `    }`{.code-voice}
9.  `}`{.code-voice}
10. ` `{.code-voice}
11. `class`{.code-voice} `SomeSubClass`{.vc}: `SomeSuperClass`{.n}, `SomeProtocol`{.n} {
12. `    // "required" from SomeProtocol conformance; "override" from SomeSuperClass`{.code-voice}
13. `    required`{.code-voice} `override`{.kt} `init`{.kt}() {
14. `        // initializer implementation goes here`{.code-voice}
15. `    }`{.code-voice}
16. `}`{.code-voice}











[‌](){#TP40016643-CH25-ID274}
### Failable Initializer Requirements {#failable-initializer-requirements .section-name}

Protocols can define failable initializer requirements for conforming types, as defined in [Failable Initializers](Initialization.md#TP40016643-CH18-ID224).

A failable initializer requirement can be satisfied by a failable or nonfailable initializer on a conforming type. A nonfailable initializer requirement can be satisfied by a nonfailable initializer or an implicitly unwrapped failable initializer.







[‌](){#TP40016643-CH25-ID275}
### Protocols as Types {#protocols-as-types .section-name}

Protocols do not actually implement any functionality themselves. Nonetheless, any protocol you create will become a fully-fledged type for use in your code.

Because it is a type, you can use a protocol in many places where other types are allowed, including:

-   As a parameter type or return type in a function, method, or initializer

-   As the type of a constant, variable, or property

-   As the type of items in an array, dictionary, or other container



Note

Because protocols are types, begin their names with a capital letter (such as `FullyNamed`{.code-voice} and `RandomNumberGenerator`{.code-voice}) to match the names of other types in Swift (such as `Int`{.code-voice}, `String`{.code-voice}, and `Double`{.code-voice}).



Here’s an example of a protocol used as a type:







1.  `class`{.code-voice} `Dice`{.vc} {
2.  `    let`{.code-voice} `sides`{.vc}: `Int`{.n}
3.  `    let`{.code-voice} `generator`{.vc}: `RandomNumberGenerator`{.n}
4.  `    init`{.code-voice}(`sides`{.vc}: `Int`{.n}, `generator`{.vc}: `RandomNumberGenerator`{.n}) {
5.  `        self`{.code-voice}.`sides`{.vc} = `sides`{.vc}
6.  `        self`{.code-voice}.`generator`{.vc} = `generator`{.vc}
7.  `    }`{.code-voice}
8.  `    func`{.code-voice} `roll`{.vc}() -&gt; `Int`{.n} {
9.  `        return`{.code-voice} `Int`{.vc}(`generator`{.vc}.`random`{.vc}() \* `Double`{.vc}(`sides`{.vc})) + `1`{.m}
10. `    }`{.code-voice}
11. `}`{.code-voice}







This example defines a new class called `Dice`{.code-voice}, which represents an *n*-sided dice for use in a board game. `Dice`{.code-voice} instances have an integer property called `sides`{.code-voice}, which represents how many sides they have, and a property called `generator`{.code-voice}, which provides a random number generator from which to create dice roll values.

The `generator`{.code-voice} property is of type `RandomNumberGenerator`{.code-voice}. Therefore, you can set it to an instance of *any* type that adopts the `RandomNumberGenerator`{.code-voice} protocol. Nothing else is required of the instance you assign to this property, except that the instance must adopt the `RandomNumberGenerator`{.code-voice} protocol.

`Dice`{.code-voice} also has an initializer, to set up its initial state. This initializer has a parameter called `generator`{.code-voice}, which is also of type `RandomNumberGenerator`{.code-voice}. You can pass a value of any conforming type in to this parameter when initializing a new `Dice`{.code-voice} instance.

`Dice`{.code-voice} provides one instance method, `roll`{.code-voice}, which returns an integer value between 1 and the number of sides on the dice. This method calls the generator’s `random()`{.code-voice} method to create a new random number between `0.0`{.code-voice} and `1.0`{.code-voice}, and uses this random number to create a dice roll value within the correct range. Because `generator`{.code-voice} is known to adopt `RandomNumberGenerator`{.code-voice}, it is guaranteed to have a `random()`{.code-voice} method to call.

Here’s how the `Dice`{.code-voice} class can be used to create a six-sided dice with a `LinearCongruentialGenerator`{.code-voice} instance as its random number generator:







1.  `var`{.code-voice} `d6`{.vc} = `Dice`{.vc}(`sides`{.vc}: `6`{.m}, `generator`{.vc}: `LinearCongruentialGenerator`{.vc}())
2.  `for`{.code-voice} `_`{.kt} `in`{.kt} `1`{.m}...`5`{.m} {
3.  `    print`{.code-voice}(`"Random dice roll is `{.s}\\(`d6`{.vc}.`roll`{.vc}())`"`{.s})
4.  `}`{.code-voice}
5.  `// Random dice roll is 3`{.code-voice}
6.  `// Random dice roll is 5`{.code-voice}
7.  `// Random dice roll is 4`{.code-voice}
8.  `// Random dice roll is 5`{.code-voice}
9.  `// Random dice roll is 4`{.code-voice}











[‌](){#TP40016643-CH25-ID276}
### Delegation {#delegation .section-name}

*Delegation* is a design pattern that enables a class or structure to hand off (or *delegate*) some of its responsibilities to an instance of another type. This design pattern is implemented by defining a protocol that encapsulates the delegated responsibilities, such that a conforming type (known as a delegate) is guaranteed to provide the functionality that has been delegated. Delegation can be used to respond to a particular action, or to retrieve data from an external source without needing to know the underlying type of that source.

The example below defines two protocols for use with dice-based board games:







1.  `protocol`{.code-voice} `DiceGame`{.vc} {
2.  `    var`{.code-voice} `dice`{.vc}: `Dice`{.n} { `get`{.kt} }
3.  `    func`{.code-voice} `play`{.vc}()
4.  `}`{.code-voice}
5.  `protocol`{.code-voice} `DiceGameDelegate`{.vc} {
6.  `    func`{.code-voice} `gameDidStart`{.vc}(`game`{.vc}: `DiceGame`{.n})
7.  `    func`{.code-voice} `game`{.vc}(`game`{.vc}: `DiceGame`{.n}, `didStartNewTurnWithDiceRoll`{.vc} `diceRoll`{.vc}: `Int`{.n})
8.  `    func`{.code-voice} `gameDidEnd`{.vc}(`game`{.vc}: `DiceGame`{.n})
9.  `}`{.code-voice}







The `DiceGame`{.code-voice} protocol is a protocol that can be adopted by any game that involves dice. The `DiceGameDelegate`{.code-voice} protocol can be adopted by any type to track the progress of a `DiceGame`{.code-voice}.

Here’s a version of the *Snakes and Ladders* game originally introduced in [Control Flow](ControlFlow.md). This version is adapted to use a `Dice`{.code-voice} instance for its dice-rolls; to adopt the `DiceGame`{.code-voice} protocol; and to notify a `DiceGameDelegate`{.code-voice} about its progress:







1.  `class`{.code-voice} `SnakesAndLadders`{.vc}: `DiceGame`{.n} {
2.  `    let`{.code-voice} `finalSquare`{.vc} = `25`{.m}
3.  `    let`{.code-voice} `dice`{.vc} = `Dice`{.vc}(`sides`{.vc}: `6`{.m}, `generator`{.vc}: `LinearCongruentialGenerator`{.vc}())
4.  `    var`{.code-voice} `square`{.vc} = `0`{.m}
5.  `    var`{.code-voice} `board`{.vc}: \[`Int`{.n}\]
6.  `    init`{.code-voice}() {
7.  `        board`{.code-voice} = \[`Int`{.vc}\](`count`{.vc}: `finalSquare`{.vc} + `1`{.m}, `repeatedValue`{.vc}: `0`{.m})
8.  `        board`{.code-voice}\[`03`{.m}\] = +`08`{.m}; `board`{.vc}\[`06`{.m}\] = +`11`{.m}; `board`{.vc}\[`09`{.m}\] = +`09`{.m}; `board`{.vc}\[`10`{.m}\] = +`02`{.m}
9.  `        board`{.code-voice}\[`14`{.m}\] = -`10`{.m}; `board`{.vc}\[`19`{.m}\] = -`11`{.m}; `board`{.vc}\[`22`{.m}\] = -`02`{.m}; `board`{.vc}\[`24`{.m}\] = -`08`{.m}
10. `    }`{.code-voice}
11. `    var`{.code-voice} `delegate`{.vc}: `DiceGameDelegate`{.n}?
12. `    func`{.code-voice} `play`{.vc}() {
13. `        square`{.code-voice} = `0`{.m}
14. `        delegate`{.code-voice}?.`gameDidStart`{.vc}(`self`{.kt})
15. `        gameLoop`{.code-voice}: `while`{.kt} `square`{.vc} != `finalSquare`{.vc} {
16. `            let`{.code-voice} `diceRoll`{.vc} = `dice`{.vc}.`roll`{.vc}()
17. `            delegate`{.code-voice}?.`game`{.vc}(`self`{.kt}, `didStartNewTurnWithDiceRoll`{.vc}: `diceRoll`{.vc})
18. `            switch`{.code-voice} `square`{.vc} + `diceRoll`{.vc} {
19. `            case`{.code-voice} `finalSquare`{.vc}:
20. `                break`{.code-voice} `gameLoop`{.vc}
21. `            case`{.code-voice} `let`{.kt} `newSquare`{.vc} `where`{.kt} `newSquare`{.vc} &gt; `finalSquare`{.vc}:
22. `                continue`{.code-voice} `gameLoop`{.vc}
23. `            default`{.code-voice}:
24. `                square`{.code-voice} += `diceRoll`{.vc}
25. `                square`{.code-voice} += `board`{.vc}\[`square`{.vc}\]
26. `            }`{.code-voice}
27. `        }`{.code-voice}
28. `        delegate`{.code-voice}?.`gameDidEnd`{.vc}(`self`{.kt})
29. `    }`{.code-voice}
30. `}`{.code-voice}







For a description of the *Snakes and Ladders* gameplay, see [Break](ControlFlow.md#TP40016643-CH9-ID137) section of the [Control Flow](ControlFlow.md).

This version of the game is wrapped up as a class called `SnakesAndLadders`{.code-voice}, which adopts the `DiceGame`{.code-voice} protocol. It provides a gettable `dice`{.code-voice} property and a `play()`{.code-voice} method in order to conform to the protocol. (The `dice`{.code-voice} property is declared as a constant property because it does not need to change after initialization, and the protocol only requires that it is gettable.)

The *Snakes and Ladders* game board setup takes place within the class’s `init()`{.code-voice} initializer. All game logic is moved into the protocol’s `play`{.code-voice} method, which uses the protocol’s required `dice`{.code-voice} property to provide its dice roll values.

Note that the `delegate`{.code-voice} property is defined as an *optional* `DiceGameDelegate`{.code-voice}, because a delegate isn’t required in order to play the game. Because it is of an optional type, the `delegate`{.code-voice} property is automatically set to an initial value of `nil`{.code-voice}. Thereafter, the game instantiator has the option to set the property to a suitable delegate.

`DiceGameDelegate`{.code-voice} provides three methods for tracking the progress of a game. These three methods have been incorporated into the game logic within the `play()`{.code-voice} method above, and are called when a new game starts, a new turn begins, or the game ends.

Because the `delegate`{.code-voice} property is an *optional* `DiceGameDelegate`{.code-voice}, the `play()`{.code-voice} method uses optional chaining each time it calls a method on the delegate. If the `delegate`{.code-voice} property is nil, these delegate calls fail gracefully and without error. If the `delegate`{.code-voice} property is non-nil, the delegate methods are called, and are passed the `SnakesAndLadders`{.code-voice} instance as a parameter.

This next example shows a class called `DiceGameTracker`{.code-voice}, which adopts the `DiceGameDelegate`{.code-voice} protocol:







1.  `class`{.code-voice} `DiceGameTracker`{.vc}: `DiceGameDelegate`{.n} {
2.  `    var`{.code-voice} `numberOfTurns`{.vc} = `0`{.m}
3.  `    func`{.code-voice} `gameDidStart`{.vc}(`game`{.vc}: `DiceGame`{.n}) {
4.  `        numberOfTurns`{.code-voice} = `0`{.m}
5.  `        if`{.code-voice} `game`{.vc} `is`{.kt} `SnakesAndLadders`{.n} {
6.  `            print`{.code-voice}(`"Started a new game of Snakes and Ladders"`{.s})
7.  `        }`{.code-voice}
8.  `        print`{.code-voice}(`"The game is using a `{.s}\\(`game`{.vc}.`dice`{.vc}.`sides`{.vc})`-sided dice"`{.s})
9.  `    }`{.code-voice}
10. `    func`{.code-voice} `game`{.vc}(`game`{.vc}: `DiceGame`{.n}, `didStartNewTurnWithDiceRoll`{.vc} `diceRoll`{.vc}: `Int`{.n}) {
11. `        ++numberOfTurns`{.code-voice}
12. `        print`{.code-voice}(`"Rolled a `{.s}\\(`diceRoll`{.vc})`"`{.s})
13. `    }`{.code-voice}
14. `    func`{.code-voice} `gameDidEnd`{.vc}(`game`{.vc}: `DiceGame`{.n}) {
15. `        print`{.code-voice}(`"The game lasted for `{.s}\\(`numberOfTurns`{.vc})` turns"`{.s})
16. `    }`{.code-voice}
17. `}`{.code-voice}







`DiceGameTracker`{.code-voice} implements all three methods required by `DiceGameDelegate`{.code-voice}. It uses these methods to keep track of the number of turns a game has taken. It resets a `numberOfTurns`{.code-voice} property to zero when the game starts, increments it each time a new turn begins, and prints out the total number of turns once the game has ended.

The implementation of `gameDidStart`{.code-voice} shown above uses the `game`{.code-voice} parameter to print some introductory information about the game that is about to be played. The `game`{.code-voice} parameter has a type of `DiceGame`{.code-voice}, not `SnakesAndLadders`{.code-voice}, and so `gameDidStart`{.code-voice} can access and use only methods and properties that are implemented as part of the `DiceGame`{.code-voice} protocol. However, the method is still able to use type casting to query the type of the underlying instance. In this example, it checks whether `game`{.code-voice} is actually an instance of `SnakesAndLadders`{.code-voice} behind the scenes, and prints an appropriate message if so.

`gameDidStart`{.code-voice} also accesses the `dice`{.code-voice} property of the passed `game`{.code-voice} parameter. Because `game`{.code-voice} is known to conform to the `DiceGame`{.code-voice} protocol, it is guaranteed to have a `dice`{.code-voice} property, and so the `gameDidStart(_:)`{.code-voice} method is able to access and print the dice’s `sides`{.code-voice} property, regardless of what kind of game is being played.

Here’s how `DiceGameTracker`{.code-voice} looks in action:







1.  `let`{.code-voice} `tracker`{.vc} = `DiceGameTracker`{.vc}()
2.  `let`{.code-voice} `game`{.vc} = `SnakesAndLadders`{.vc}()
3.  `game`{.code-voice}.`delegate`{.vc} = `tracker`{.vc}
4.  `game`{.code-voice}.`play`{.vc}()
5.  `// Started a new game of Snakes and Ladders`{.code-voice}
6.  `// The game is using a 6-sided dice`{.code-voice}
7.  `// Rolled a 3`{.code-voice}
8.  `// Rolled a 5`{.code-voice}
9.  `// Rolled a 4`{.code-voice}
10. `// Rolled a 5`{.code-voice}
11. `// The game lasted for 4 turns`{.code-voice}











[‌](){#TP40016643-CH25-ID277}
### Adding Protocol Conformance with an Extension {#adding-protocol-conformance-with-an-extension .section-name}

You can extend an existing type to adopt and conform to a new protocol, even if you do not have access to the source code for the existing type. Extensions can add new properties, methods, and subscripts to an existing type, and are therefore able to add any requirements that a protocol may demand. For more about extensions, see [Extensions](Extensions.md).



Note

Existing instances of a type automatically adopt and conform to a protocol when that conformance is added to the instance’s type in an extension.



For example, this protocol, called `TextRepresentable`{.code-voice}, can be implemented by any type that has a way to be represented as text. This might be a description of itself, or a text version of its current state:







1.  `protocol`{.code-voice} `TextRepresentable`{.vc} {
2.  `    var`{.code-voice} `textualDescription`{.vc}: `String`{.n} { `get`{.kt} }
3.  `}`{.code-voice}







The `Dice`{.code-voice} class from earlier can be extended to adopt and conform to `TextRepresentable`{.code-voice}:







1.  `extension`{.code-voice} `Dice`{.n}: `TextRepresentable`{.n} {
2.  `    var`{.code-voice} `textualDescription`{.vc}: `String`{.n} {
3.  `        return`{.code-voice} `"A `{.s}\\(`sides`{.vc})`-sided dice"`{.s}
4.  `    }`{.code-voice}
5.  `}`{.code-voice}







This extension adopts the new protocol in exactly the same way as if `Dice`{.code-voice} had provided it in its original implementation. The protocol name is provided after the type name, separated by a colon, and an implementation of all requirements of the protocol is provided within the extension’s curly braces.

Any `Dice`{.code-voice} instance can now be treated as `TextRepresentable`{.code-voice}:







1.  `let`{.code-voice} `d12`{.vc} = `Dice`{.vc}(`sides`{.vc}: `12`{.m}, `generator`{.vc}: `LinearCongruentialGenerator`{.vc}())
2.  `print`{.code-voice}(`d12`{.vc}.`textualDescription`{.vc})
3.  `// prints "A 12-sided dice"`{.code-voice}







Similarly, the `SnakesAndLadders`{.code-voice} game class can be extended to adopt and conform to the `TextRepresentable`{.code-voice} protocol:







1.  `extension`{.code-voice} `SnakesAndLadders`{.n}: `TextRepresentable`{.n} {
2.  `    var`{.code-voice} `textualDescription`{.vc}: `String`{.n} {
3.  `        return`{.code-voice} `"A game of Snakes and Ladders with `{.s}\\(`finalSquare`{.vc})` squares"`{.s}
4.  `    }`{.code-voice}
5.  `}`{.code-voice}
6.  `print`{.code-voice}(`game`{.vc}.`textualDescription`{.vc})
7.  `// prints "A game of Snakes and Ladders with 25 squares"`{.code-voice}









[‌](){#TP40016643-CH25-ID278}
### Declaring Protocol Adoption with an Extension {#declaring-protocol-adoption-with-an-extension .section-name}

If a type already conforms to all of the requirements of a protocol, but has not yet stated that it adopts that protocol, you can make it adopt the protocol with an empty extension:







1.  `struct`{.code-voice} `Hamster`{.vc} {
2.  `    var`{.code-voice} `name`{.vc}: `String`{.n}
3.  `    var`{.code-voice} `textualDescription`{.vc}: `String`{.n} {
4.  `        return`{.code-voice} `"A hamster named `{.s}\\(`name`{.vc})`"`{.s}
5.  `    }`{.code-voice}
6.  `}`{.code-voice}
7.  `extension`{.code-voice} `Hamster`{.n}: `TextRepresentable`{.n} {}







Instances of `Hamster`{.code-voice} can now be used wherever `TextRepresentable`{.code-voice} is the required type:







1.  `let`{.code-voice} `simonTheHamster`{.vc} = `Hamster`{.vc}(`name`{.vc}: `"Simon"`{.s})
2.  `let`{.code-voice} `somethingTextRepresentable`{.vc}: `TextRepresentable`{.n} = `simonTheHamster`{.vc}
3.  `print`{.code-voice}(`somethingTextRepresentable`{.vc}.`textualDescription`{.vc})
4.  `// prints "A hamster named Simon"`{.code-voice}









Note

Types do not automatically adopt a protocol just by satisfying its requirements. They must always explicitly declare their adoption of the protocol.









[‌](){#TP40016643-CH25-ID279}
### Collections of Protocol Types {#collections-of-protocol-types .section-name}

A protocol can be used as the type to be stored in a collection such as an array or a dictionary, as mentioned in [Protocols as Types](Protocols.md#TP40016643-CH25-ID275). This example creates an array of `TextRepresentable`{.code-voice} things:







1.  `let`{.code-voice} `things`{.vc}: \[`TextRepresentable`{.n}\] = \[`game`{.vc}, `d12`{.vc}, `simonTheHamster`{.vc}\]







It is now possible to iterate over the items in the array, and print each item’s textual description:







1.  `for`{.code-voice} `thing`{.vc} `in`{.kt} `things`{.vc} {
2.  `    print`{.code-voice}(`thing`{.vc}.`textualDescription`{.vc})
3.  `}`{.code-voice}
4.  `// A game of Snakes and Ladders with 25 squares`{.code-voice}
5.  `// A 12-sided dice`{.code-voice}
6.  `// A hamster named Simon`{.code-voice}







Note that the `thing`{.code-voice} constant is of type `TextRepresentable`{.code-voice}. It is not of type `Dice`{.code-voice}, or `DiceGame`{.code-voice}, or `Hamster`{.code-voice}, even if the actual instance behind the scenes is of one of those types. Nonetheless, because it is of type `TextRepresentable`{.code-voice}, and anything that is `TextRepresentable`{.code-voice} is known to have a `textualDescription`{.code-voice} property, it is safe to access `thing.textualDescription`{.code-voice} each time through the loop.





[‌](){#TP40016643-CH25-ID280}
### Protocol Inheritance {#protocol-inheritance .section-name}

A protocol can *inherit* one or more other protocols and can add further requirements on top of the requirements it inherits. The syntax for protocol inheritance is similar to the syntax for class inheritance, but with the option to list multiple inherited protocols, separated by commas:







1.  `protocol`{.code-voice} `InheritingProtocol`{.vc}: `SomeProtocol`{.n}, `AnotherProtocol`{.n} {
2.  `    // protocol definition goes here`{.code-voice}
3.  `}`{.code-voice}







Here’s an example of a protocol that inherits the `TextRepresentable`{.code-voice} protocol from above:







1.  `protocol`{.code-voice} `PrettyTextRepresentable`{.vc}: `TextRepresentable`{.n} {
2.  `    var`{.code-voice} `prettyTextualDescription`{.vc}: `String`{.n} { `get`{.kt} }
3.  `}`{.code-voice}







This example defines a new protocol, `PrettyTextRepresentable`{.code-voice}, which inherits from `TextRepresentable`{.code-voice}. Anything that adopts `PrettyTextRepresentable`{.code-voice} must satisfy all of the requirements enforced by `TextRepresentable`{.code-voice}, *plus* the additional requirements enforced by `PrettyTextRepresentable`{.code-voice}. In this example, `PrettyTextRepresentable`{.code-voice} adds a single requirement to provide a gettable property called `prettyTextualDescription`{.code-voice} that returns a `String`{.code-voice}.

The `SnakesAndLadders`{.code-voice} class can be extended to adopt and conform to `PrettyTextRepresentable`{.code-voice}:







1.  `extension`{.code-voice} `SnakesAndLadders`{.n}: `PrettyTextRepresentable`{.n} {
2.  `    var`{.code-voice} `prettyTextualDescription`{.vc}: `String`{.n} {
3.  `        var`{.code-voice} `output`{.vc} = `textualDescription`{.vc} + `":\n"`{.s}
4.  `        for`{.code-voice} `index`{.vc} `in`{.kt} `1`{.m}...`finalSquare`{.vc} {
5.  `            switch`{.code-voice} `board`{.vc}\[`index`{.vc}\] {
6.  `            case`{.code-voice} `let`{.kt} `ladder`{.vc} `where`{.kt} `ladder`{.vc} &gt; `0`{.m}:
7.  `                output`{.code-voice} += `"▲ "`{.s}
8.  `            case`{.code-voice} `let`{.kt} `snake`{.vc} `where`{.kt} `snake`{.vc} &lt; `0`{.m}:
9.  `                output`{.code-voice} += `"▼ "`{.s}
10. `            default`{.code-voice}:
11. `                output`{.code-voice} += `"○ "`{.s}
12. `            }`{.code-voice}
13. `        }`{.code-voice}
14. `        return`{.code-voice} `output`{.vc}
15. `    }`{.code-voice}
16. `}`{.code-voice}







This extension states that it adopts the `PrettyTextRepresentable`{.code-voice} protocol and provides an implementation of the `prettyTextualDescription`{.code-voice} property for the `SnakesAndLadders`{.code-voice} type. Anything that is `PrettyTextRepresentable`{.code-voice} must also be `TextRepresentable`{.code-voice}, and so the implementation of `prettyTextualDescription`{.code-voice} starts by accessing the `textualDescription`{.code-voice} property from the `TextRepresentable`{.code-voice} protocol to begin an output string. It appends a colon and a line break, and uses this as the start of its pretty text representation. It then iterates through the array of board squares, and appends a geometric shape to represent the contents of each square:

-   If the square’s value is greater than `0`{.code-voice}, it is the base of a ladder, and is represented by `▲`{.code-voice}.

-   If the square’s value is less than `0`{.code-voice}, it is the head of a snake, and is represented by `▼`{.code-voice}.

-   Otherwise, the square’s value is `0`{.code-voice}, and it is a “free” square, represented by `○`{.code-voice}.

The `prettyTextualDescription`{.code-voice} property can now be used to print a pretty text description of any `SnakesAndLadders`{.code-voice} instance:







1.  `print`{.code-voice}(`game`{.vc}.`prettyTextualDescription`{.vc})
2.  `// A game of Snakes and Ladders with 25 squares:`{.code-voice}
3.  `// ○ ○ ▲ ○ ○ ▲ ○ ○ ▲ ▲ ○ ○ ○ ▼ ○ ○ ○ ○ ▼ ○ ○ ▼ ○ ▼ ○`{.code-voice}











[‌](){#TP40016643-CH25-ID281}
### Class-Only Protocols {#class-only-protocols .section-name}

You can limit protocol adoption to class types (and not structures or enumerations) by adding the `class`{.code-voice} keyword to a protocol’s inheritance list. The `class`{.code-voice} keyword must always appear first in a protocol’s inheritance list, before any inherited protocols:







1.  `protocol`{.code-voice} `SomeClassOnlyProtocol`{.vc}: `class`{.kt}, `SomeInheritedProtocol`{.n} {
2.  `    // class-only protocol definition goes here`{.code-voice}
3.  `}`{.code-voice}







In the example above, `SomeClassOnlyProtocol`{.code-voice} can only be adopted by class types. It is a compile-time error to write a structure or enumeration definition that tries to adopt `SomeClassOnlyProtocol`{.code-voice}.



Note

Use a class-only protocol when the behavior defined by that protocol’s requirements assumes or requires that a conforming type has reference semantics rather than value semantics. For more on reference and value semantics, see [Structures and Enumerations Are Value Types](ClassesAndStructures.md#TP40016643-CH13-ID88) and [Classes Are Reference Types](ClassesAndStructures.md#TP40016643-CH13-ID89).







[‌](){#TP40016643-CH25-ID282}
### Protocol Composition {#protocol-composition .section-name}

It can be useful to require a type to conform to multiple protocols at once. You can combine multiple protocols into a single requirement with a *protocol composition*. Protocol compositions have the form `protocol`{.code-voice}. You can list as many protocols within the pair of angle brackets (`<>`{.code-voice}) as you need, separated by commas.

Here’s an example that combines two protocols called `Named`{.code-voice} and `Aged`{.code-voice} into a single protocol composition requirement on a function parameter:







1.  `protocol`{.code-voice} `Named`{.vc} {
2.  `    var`{.code-voice} `name`{.vc}: `String`{.n} { `get`{.kt} }
3.  `}`{.code-voice}
4.  `protocol`{.code-voice} `Aged`{.vc} {
5.  `    var`{.code-voice} `age`{.vc}: `Int`{.n} { `get`{.kt} }
6.  `}`{.code-voice}
7.  `struct`{.code-voice} `Person`{.vc}: `Named`{.n}, `Aged`{.n} {
8.  `    var`{.code-voice} `name`{.vc}: `String`{.n}
9.  `    var`{.code-voice} `age`{.vc}: `Int`{.n}
10. `}`{.code-voice}
11. `func`{.code-voice} `wishHappyBirthday`{.vc}(`celebrator`{.vc}: `protocol`{.kt}&lt;`Named`{.n}, `Aged`{.n}&gt;) {
12. `    print`{.code-voice}(`"Happy birthday `{.s}\\(`celebrator`{.vc}.`name`{.vc})` - you're `{.s}\\(`celebrator`{.vc}.`age`{.vc})`!"`{.s})
13. `}`{.code-voice}
14. `let`{.code-voice} `birthdayPerson`{.vc} = `Person`{.vc}(`name`{.vc}: `"Malcolm"`{.s}, `age`{.vc}: `21`{.m})
15. `wishHappyBirthday`{.code-voice}(`birthdayPerson`{.vc})
16. `// prints "Happy birthday Malcolm - you're 21!"`{.code-voice}







This example defines a protocol called `Named`{.code-voice}, with a single requirement for a gettable `String`{.code-voice} property called `name`{.code-voice}. It also defines a protocol called `Aged`{.code-voice}, with a single requirement for a gettable `Int`{.code-voice} property called `age`{.code-voice}. Both of these protocols are adopted by a structure called `Person`{.code-voice}.

The example also defines a function called `wishHappyBirthday`{.code-voice}, which takes a single parameter called `celebrator`{.code-voice}. The type of this parameter is `protocol`{.code-voice}, which means “any type that conforms to both the `Named`{.code-voice} and `Aged`{.code-voice} protocols.” It doesn’t matter what specific type is passed to the function, as long as it conforms to both of the required protocols.

The example then creates a new `Person`{.code-voice} instance called `birthdayPerson`{.code-voice} and passes this new instance to the `wishHappyBirthday(_:)`{.code-voice} function. Because `Person`{.code-voice} conforms to both protocols, this is a valid call, and the `wishHappyBirthday(_:)`{.code-voice} function is able to print its birthday greeting.



Note

Protocol compositions do not define a new, permanent protocol type. Rather, they define a temporary local protocol that has the combined requirements of all protocols in the composition.







[‌](){#TP40016643-CH25-ID283}
### Checking for Protocol Conformance {#checking-for-protocol-conformance .section-name}

You can use the `is`{.code-voice} and `as`{.code-voice} operators described in [Type Casting](TypeCasting.md) to check for protocol conformance, and to cast to a specific protocol. Checking for and casting to a protocol follows exactly the same syntax as checking for and casting to a type:

-   The `is`{.code-voice} operator returns `true`{.code-voice} if an instance conforms to a protocol and returns `false`{.code-voice} if it does not.

-   The `as?`{.code-voice} version of the downcast operator returns an optional value of the protocol’s type, and this value is `nil`{.code-voice} if the instance does not conform to that protocol.

-   The `as!`{.code-voice} version of the downcast operator forces the downcast to the protocol type and triggers a runtime error if the downcast does not succeed.

This example defines a protocol called `HasArea`{.code-voice}, with a single property requirement of a gettable `Double`{.code-voice} property called `area`{.code-voice}:







1.  `protocol`{.code-voice} `HasArea`{.vc} {
2.  `    var`{.code-voice} `area`{.vc}: `Double`{.n} { `get`{.kt} }
3.  `}`{.code-voice}







Here are two classes, `Circle`{.code-voice} and `Country`{.code-voice}, both of which conform to the `HasArea`{.code-voice} protocol:







1.  `class`{.code-voice} `Circle`{.vc}: `HasArea`{.n} {
2.  `    let`{.code-voice} `pi`{.vc} = `3.1415927`{.m}
3.  `    var`{.code-voice} `radius`{.vc}: `Double`{.n}
4.  `    var`{.code-voice} `area`{.vc}: `Double`{.n} { `return`{.kt} `pi`{.vc} \* `radius`{.vc} \* `radius`{.vc} }
5.  `    init`{.code-voice}(`radius`{.vc}: `Double`{.n}) { `self`{.kt}.`radius`{.vc} = `radius`{.vc} }
6.  `}`{.code-voice}
7.  `class`{.code-voice} `Country`{.vc}: `HasArea`{.n} {
8.  `    var`{.code-voice} `area`{.vc}: `Double`{.n}
9.  `    init`{.code-voice}(`area`{.vc}: `Double`{.n}) { `self`{.kt}.`area`{.vc} = `area`{.vc} }
10. `}`{.code-voice}







The `Circle`{.code-voice} class implements the `area`{.code-voice} property requirement as a computed property, based on a stored `radius`{.code-voice} property. The `Country`{.code-voice} class implements the `area`{.code-voice} requirement directly as a stored property. Both classes correctly conform to the `HasArea`{.code-voice} protocol.

Here’s a class called `Animal`{.code-voice}, which does not conform to the `HasArea`{.code-voice} protocol:







1.  `class`{.code-voice} `Animal`{.vc} {
2.  `    var`{.code-voice} `legs`{.vc}: `Int`{.n}
3.  `    init`{.code-voice}(`legs`{.vc}: `Int`{.n}) { `self`{.kt}.`legs`{.vc} = `legs`{.vc} }
4.  `}`{.code-voice}







The `Circle`{.code-voice}, `Country`{.code-voice} and `Animal`{.code-voice} classes do not have a shared base class. Nonetheless, they are all classes, and so instances of all three types can be used to initialize an array that stores values of type `AnyObject`{.code-voice}:







1.  `let`{.code-voice} `objects`{.vc}: \[`AnyObject`{.n}\] = \[
2.  `    Circle`{.code-voice}(`radius`{.vc}: `2.0`{.m}),
3.  `    Country`{.code-voice}(`area`{.vc}: `243_610`{.m}),
4.  `    Animal`{.code-voice}(`legs`{.vc}: `4`{.m})
5.  `]`{.code-voice}







The `objects`{.code-voice} array is initialized with an array literal containing a `Circle`{.code-voice} instance with a radius of 2 units; a `Country`{.code-voice} instance initialized with the surface area of the United Kingdom in square kilometers; and an `Animal`{.code-voice} instance with four legs.

The `objects`{.code-voice} array can now be iterated, and each object in the array can be checked to see if it conforms to the `HasArea`{.code-voice} protocol:







1.  `for`{.code-voice} `object`{.vc} `in`{.kt} `objects`{.vc} {
2.  `    if`{.code-voice} `let`{.kt} `objectWithArea`{.vc} = `object`{.vc} `as`{.kt}? `HasArea`{.n} {
3.  `        print`{.code-voice}(`"Area is `{.s}\\(`objectWithArea`{.vc}.`area`{.vc})`"`{.s})
4.  `    } else`{.code-voice} {
5.  `        print`{.code-voice}(`"Something that doesn't have an area"`{.s})
6.  `    }`{.code-voice}
7.  `}`{.code-voice}
8.  `// Area is 12.5663708`{.code-voice}
9.  `// Area is 243610.0`{.code-voice}
10. `// Something that doesn't have an area`{.code-voice}







Whenever an object in the array conforms to the `HasArea`{.code-voice} protocol, the optional value returned by the `as?`{.code-voice} operator is unwrapped with optional binding into a constant called `objectWithArea`{.code-voice}. The `objectWithArea`{.code-voice} constant is known to be of type `HasArea`{.code-voice}, and so its `area`{.code-voice} property can be accessed and printed in a type-safe way.

Note that the underlying objects are not changed by the casting process. They continue to be a `Circle`{.code-voice}, a `Country`{.code-voice} and an `Animal`{.code-voice}. However, at the point that they are stored in the `objectWithArea`{.code-voice} constant, they are only known to be of type `HasArea`{.code-voice}, and so only their `area`{.code-voice} property can be accessed.





[‌](){#TP40016643-CH25-ID284}
### Optional Protocol Requirements {#optional-protocol-requirements .section-name}

You can define *optional requirements* for protocols, These requirements do not have to be implemented by types that conform to the protocol. Optional requirements are prefixed by the `optional`{.code-voice} modifier as part of the protocol’s definition. When you use a method or property in an optional requirement, its type automatically becomes an optional. For example, a method of type `(Int) -> String`{.code-voice} becomes `((Int) -> String)?`{.code-voice}. Note that the entire function type is wrapped in the optional, not method’s the return value.

An optional protocol requirement can be called with optional chaining, to account for the possibility that the requirement was not implemented by a type that conforms to the protocol. You check for an implementation of an optional method by writing a question mark after the name of the method when it is called, such as `someOptionalMethod?(someArgument)`{.code-voice}. For information on optional chaining, see [Optional Chaining](OptionalChaining.md).



Note

Optional protocol requirements can only be specified if your protocol is marked with the `@objc`{.code-voice} attribute.

This attribute indicates that the protocol should be exposed to Objective-C code and is described in *Using Swift with Cocoa and Objective-C (Swift 2.1)*. Even if you are not interoperating with Objective-C, you need to mark your protocols with the `@objc`{.code-voice} attribute if you want to specify optional requirements.

Note also that `@objc`{.code-voice} protocols can be adopted only by classes that inherit from Objective-C classes or other `@objc`{.code-voice} classes. They can’t be adopted by structures or enumerations.



The following example defines an integer-counting class called `Counter`{.code-voice}, which uses an external data source to provide its increment amount. This data source is defined by the `CounterDataSource`{.code-voice} protocol, which has two optional requirements:







1.  `@objc`{.code-voice} `protocol`{.kt} `CounterDataSource`{.vc} {
2.  `    optional`{.code-voice} `func`{.kt} `incrementForCount`{.vc}(`count`{.vc}: `Int`{.n}) -&gt; `Int`{.n}
3.  `    optional`{.code-voice} `var`{.kt} `fixedIncrement`{.vc}: `Int`{.n} { `get`{.kt} }
4.  `}`{.code-voice}







The `CounterDataSource`{.code-voice} protocol defines an optional method requirement called `incrementForCount(_:)`{.code-voice} and an optional property requirement called `fixedIncrement`{.code-voice}. These requirements define two different ways for data sources to provide an appropriate increment amount for a `Counter`{.code-voice} instance.



Note

Strictly speaking, you can write a custom class that conforms to `CounterDataSource`{.code-voice} without implementing *either* protocol requirement. They are both optional, after all. Although technically allowed, this wouldn’t make for a very good data source.



The `Counter`{.code-voice} class, defined below, has an optional `dataSource`{.code-voice} property of type `CounterDataSource?`{.code-voice}:







1.  `class`{.code-voice} `Counter`{.vc} {
2.  `    var`{.code-voice} `count`{.vc} = `0`{.m}
3.  `    var`{.code-voice} `dataSource`{.vc}: `CounterDataSource`{.n}?
4.  `    func`{.code-voice} `increment`{.vc}() {
5.  `        if`{.code-voice} `let`{.kt} `amount`{.vc} = `dataSource`{.vc}?.`incrementForCount`{.vc}?(`count`{.vc}) {
6.  `            count`{.code-voice} += `amount`{.vc}
7.  `        } else`{.code-voice} `if`{.kt} `let`{.kt} `amount`{.vc} = `dataSource`{.vc}?.`fixedIncrement`{.vc} {
8.  `            count`{.code-voice} += `amount`{.vc}
9.  `        }`{.code-voice}
10. `    }`{.code-voice}
11. `}`{.code-voice}







The `Counter`{.code-voice} class stores its current value in a variable property called `count`{.code-voice}. The `Counter`{.code-voice} class also defines a method called `increment`{.code-voice}, which increments the `count`{.code-voice} property every time the method is called.

The `increment()`{.code-voice} method first tries to retrieve an increment amount by looking for an implementation of the `incrementForCount(_:)`{.code-voice} method on its data source. The `increment()`{.code-voice} method uses optional chaining to try to call `incrementForCount(_:)`{.code-voice}, and passes the current `count`{.code-voice} value as the method’s single argument.

Note that *two* levels of optional chaining are at play here. First, it is possible that `dataSource`{.code-voice} may be `nil`{.code-voice}, and so `dataSource`{.code-voice} has a question mark after its name to indicate that `incrementForCount(_:)`{.code-voice} should be called only if `dataSource`{.code-voice} isn’t `nil`{.code-voice}. Second, even if `dataSource`{.code-voice} *does* exist, there is no guarantee that it implements `incrementForCount(_:)`{.code-voice}, because it is an optional requirement. Here, the possibility that `incrementForCount(_:)`{.code-voice} might not be implemented is also handled by optional chaining. The call to `incrementForCount(_:)`{.code-voice} happens only if `incrementForCount(_:)`{.code-voice} exists—that is, if it isn’t `nil`{.code-voice}. This is why `incrementForCount(_:)`{.code-voice} is also written with a question mark after its name.

Because the call to `incrementForCount(_:)`{.code-voice} can fail for either of these two reasons, the call returns an *optional* `Int`{.code-voice} value. This is true even though `incrementForCount(_:)`{.code-voice} is defined as returning a nonoptional `Int`{.code-voice} value in the definition of `CounterDataSource`{.code-voice}. Even though there are two optional chaining operations, one after another, the result is still wrapped in a single optional. For more information about using multiple optional chaining operations, see [Linking Multiple Levels of Chaining](OptionalChaining.md#TP40016643-CH21-ID252).

After calling `incrementForCount(_:)`{.code-voice}, the optional `Int`{.code-voice} that it returns is unwrapped into a constant called `amount`{.code-voice}, using optional binding. If the optional `Int`{.code-voice} does contain a value—that is, if the delegate and method both exist, and the method returned a value—the unwrapped `amount`{.code-voice} is added onto the stored `count`{.code-voice} property, and incrementation is complete.

If it is *not* possible to retrieve a value from the `incrementForCount(_:)`{.code-voice} method—either because `dataSource`{.code-voice} is nil, or because the data source does not implement `incrementForCount(_:)`{.code-voice}—then the `increment()`{.code-voice} method tries to retrieve a value from the data source’s `fixedIncrement`{.code-voice} property instead. The `fixedIncrement`{.code-voice} property is also an optional requirement, so its value is an optional `Int`{.code-voice} value, even though `fixedIncrement`{.code-voice} is defined as a nonoptional `Int`{.code-voice} property as part of the `CounterDataSource`{.code-voice} protocol definition.

Here’s a simple `CounterDataSource`{.code-voice} implementation where the data source returns a constant value of `3`{.code-voice} every time it is queried. It does this by implementing the optional `fixedIncrement`{.code-voice} property requirement:







1.  `class`{.code-voice} `ThreeSource`{.vc}: `NSObject`{.n}, `CounterDataSource`{.n} {
2.  `    let`{.code-voice} `fixedIncrement`{.vc} = `3`{.m}
3.  `}`{.code-voice}







You can use an instance of `ThreeSource`{.code-voice} as the data source for a new `Counter`{.code-voice} instance:







1.  `var`{.code-voice} `counter`{.vc} = `Counter`{.vc}()
2.  `counter`{.code-voice}.`dataSource`{.vc} = `ThreeSource`{.vc}()
3.  `for`{.code-voice} `_`{.kt} `in`{.kt} `1`{.m}...`4`{.m} {
4.  `    counter`{.code-voice}.`increment`{.vc}()
5.  `    print`{.code-voice}(`counter`{.vc}.`count`{.vc})
6.  `}`{.code-voice}
7.  `// 3`{.code-voice}
8.  `// 6`{.code-voice}
9.  `// 9`{.code-voice}
10. `// 12`{.code-voice}







The code above creates a new `Counter`{.code-voice} instance; sets its data source to be a new `ThreeSource`{.code-voice} instance; and calls the counter’s `increment()`{.code-voice} method four times. As expected, the counter’s `count`{.code-voice} property increases by three each time `increment()`{.code-voice} is called.

Here’s a more complex data source called `TowardsZeroSource`{.code-voice}, which makes a `Counter`{.code-voice} instance count up or down towards zero from its current `count`{.code-voice} value:







1.  `@objc`{.code-voice} `class`{.kt} `TowardsZeroSource`{.vc}: `NSObject`{.n}, `CounterDataSource`{.n} {
2.  `    func`{.code-voice} `incrementForCount`{.vc}(`count`{.vc}: `Int`{.n}) -&gt; `Int`{.n} {
3.  `        if`{.code-voice} `count`{.vc} == `0`{.m} {
4.  `            return`{.code-voice} `0`{.m}
5.  `        } else`{.code-voice} `if`{.kt} `count`{.vc} &lt; `0`{.m} {
6.  `            return`{.code-voice} `1`{.m}
7.  `        } else`{.code-voice} {
8.  `            return`{.code-voice} -`1`{.m}
9.  `        }`{.code-voice}
10. `    }`{.code-voice}
11. `}`{.code-voice}







The `TowardsZeroSource`{.code-voice} class implements the optional `incrementForCount(_:)`{.code-voice} method from the `CounterDataSource`{.code-voice} protocol and uses the `count`{.code-voice} argument value to work out which direction to count in. If `count`{.code-voice} is already zero, the method returns `0`{.code-voice} to indicate that no further counting should take place.

You can use an instance of `TowardsZeroSource`{.code-voice} with the existing `Counter`{.code-voice} instance to count from `-4`{.code-voice} to zero. Once the counter reaches zero, no more counting takes place:







1.  `counter`{.code-voice}.`count`{.vc} = -`4`{.m}
2.  `counter`{.code-voice}.`dataSource`{.vc} = `TowardsZeroSource`{.vc}()
3.  `for`{.code-voice} `_`{.kt} `in`{.kt} `1`{.m}...`5`{.m} {
4.  `    counter`{.code-voice}.`increment`{.vc}()
5.  `    print`{.code-voice}(`counter`{.vc}.`count`{.vc})
6.  `}`{.code-voice}
7.  `// -3`{.code-voice}
8.  `// -2`{.code-voice}
9.  `// -1`{.code-voice}
10. `// 0`{.code-voice}
11. `// 0`{.code-voice}











[‌](){#TP40016643-CH25-ID521}
### Protocol Extensions {#protocol-extensions .section-name}

Protocols can be extended to provide method and property implementations to conforming types. This allows you to define behavior on protocols themselves, rather than in each type’s individual conformance or in a global function.

For example, the `RandomNumberGenerator`{.code-voice} protocol can be extended to provide a `randomBool()`{.code-voice} method, which uses the result of the required `random()`{.code-voice} method to return a random `Bool`{.code-voice} value:







1.  `extension`{.code-voice} `RandomNumberGenerator`{.n} {
2.  `    func`{.code-voice} `randomBool`{.vc}() -&gt; `Bool`{.n} {
3.  `        return`{.code-voice} `random`{.vc}() &gt; `0.5`{.m}
4.  `    }`{.code-voice}
5.  `}`{.code-voice}







By creating an extension on the protocol, all conforming types automatically gain this method implementation without any additional modification.







1.  `let`{.code-voice} `generator`{.vc} = `LinearCongruentialGenerator`{.vc}()
2.  `print`{.code-voice}(`"Here's a random number: `{.s}\\(`generator`{.vc}.`random`{.vc}())`"`{.s})
3.  `// prints "Here's a random number: 0.37464991998171"`{.code-voice}
4.  `print`{.code-voice}(`"And here's a random Boolean: `{.s}\\(`generator`{.vc}.`randomBool`{.vc}())`"`{.s})
5.  `// prints "And here's a random Boolean: true"`{.code-voice}









[‌](){#TP40016643-CH25-ID529}
### Providing Default Implementations {#providing-default-implementations .section-name}

You can use protocol extensions to provide a default implementation to any method or property requirement of that protocol. If a conforming type provides its own implementation of a required method or property, that implementation will be used instead of the one provided by the extension.



Note

Protocol requirements with default implementations provided by extensions are distinct from optional protocol requirements. Although conforming types don’t have to provide their own implementation of either, requirements with default implementations can be called without optional chaining.



For example, the `PrettyTextRepresentable`{.code-voice} protocol, which inherits the `TextRepresentable`{.code-voice} protocol can provide a default implementation of its required `prettyTextualDescription`{.code-voice} property to simply return the result of accessing the `textualDescription`{.code-voice} property:







1.  `extension`{.code-voice} `PrettyTextRepresentable`{.n} {
2.  `    var`{.code-voice} `prettyTextualDescription`{.vc}: `String`{.n} {
3.  `        return`{.code-voice} `textualDescription`{.vc}
4.  `    }`{.code-voice}
5.  `}`{.code-voice}











[‌](){#TP40016643-CH25-ID527}
### Adding Constraints to Protocol Extensions {#adding-constraints-to-protocol-extensions .section-name}

When you define a protocol extension, you can specify constraints that conforming types must satisfy before the methods and properties of the extension are available. You write these constraints after the name of the protocol you’re extending using a `where`{.code-voice} clause, as described in [Where Clauses](Generics.md#TP40016643-CH26-ID192).

For instance, you can define an extension to the `CollectionType`{.code-voice} protocol that applies to any collection whose elements conform to the `TextRepresentable`{.code-voice} protocol from the example above.







1.  `extension`{.code-voice} `CollectionType`{.n} `where`{.kt} `Generator`{.vc}.`Element`{.vc}: `TextRepresentable`{.vc} {
2.  `    var`{.code-voice} `textualDescription`{.vc}: `String`{.n} {
3.  `        let`{.code-voice} `itemsAsText`{.vc} = `self`{.kt}.`map`{.vc} { `$0`{.vc}.`textualDescription`{.vc} }
4.  `        return`{.code-voice} `"["`{.s} + `itemsAsText`{.vc}.`joinWithSeparator`{.vc}(`", "`{.s}) + `"]"`{.s}
5.  `    }`{.code-voice}
6.  `}`{.code-voice}







The `textualDescription`{.code-voice} property returns the textual description of the entire collection by concatenating the textual representation of each element in the collection into a comma-separated list, enclosed in brackets.

Consider the `Hamster`{.code-voice} structure from before, which conforms to the `TextRepresentable`{.code-voice} protocol, and an array of `Hamster`{.code-voice} values:







1.  `let`{.code-voice} `murrayTheHamster`{.vc} = `Hamster`{.vc}(`name`{.vc}: `"Murray"`{.s})
2.  `let`{.code-voice} `morganTheHamster`{.vc} = `Hamster`{.vc}(`name`{.vc}: `"Morgan"`{.s})
3.  `let`{.code-voice} `mauriceTheHamster`{.vc} = `Hamster`{.vc}(`name`{.vc}: `"Maurice"`{.s})
4.  `let`{.code-voice} `hamsters`{.vc} = \[`murrayTheHamster`{.vc}, `morganTheHamster`{.vc}, `mauriceTheHamster`{.vc}\]







Because `Array`{.code-voice} conforms to `CollectionType`{.code-voice} and the array’s elements conform to the `TextRepresentable`{.code-voice} protocol, the array can use the `textualDescription`{.code-voice} property to get a textual representation of its contents:







1.  `print`{.code-voice}(`hamsters`{.vc}.`textualDescription`{.vc})
2.  `// prints "[A hamster named Murray, A hamster named Morgan, A hamster named Maurice]"`{.code-voice}









Note

If a conforming type satisfies the requirements for multiple constrained extensions that provide implementations for the same method or property, Swift will use the implementation corresponding to the most specialized constraints.










