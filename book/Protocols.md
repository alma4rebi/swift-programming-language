



[‌]()[‌]()
Protocols 
---------



A *protocol* defines a blueprint of methods, properties, and other requirements that suit a particular task or piece of functionality. The protocol can then be *adopted* by a class, structure, or enumeration to provide an actual implementation of those requirements. Any type that satisfies the requirements of a protocol is said to *conform* to that protocol.

In addition to specifying requirements that conforming types must implement, you can extend a protocol to implement some of these requirements or to implement additional functionality that conforming types can take advantage of.





[‌]()
### Protocol Syntax 

You define protocols in a very similar way to classes, structures, and enumerations:







1.  `protocol` `SomeProtocol` {
2.  `    // protocol definition goes here`
3.  `}`







Custom types state that they adopt a particular protocol by placing the protocol’s name after the type’s name, separated by a colon, as part of their definition. Multiple protocols can be listed, and are separated by commas:







1.  `struct` `SomeStructure`: `FirstProtocol`, `AnotherProtocol` {
2.  `    // structure definition goes here`
3.  `}`







If a class has a superclass, list the superclass name before any protocols it adopts, followed by a comma:







1.  `class` `SomeClass`: `SomeSuperclass`, `FirstProtocol`, `AnotherProtocol` {
2.  `    // class definition goes here`
3.  `}`











[‌]()
### Property Requirements 

A protocol can require any conforming type to provide an instance property or type property with a particular name and type. The protocol doesn’t specify whether the property should be a stored property or a computed property—it only specifies the required property name and type. The protocol also specifies whether each property must be gettable or gettable *and* settable.

If a protocol requires a property to be gettable and settable, that property requirement cannot be fulfilled by a constant stored property or a read-only computed property. If the protocol only requires a property to be gettable, the requirement can be satisfied by any kind of property, and it is valid for the property to be also settable if this is useful for your own code.

Property requirements are always declared as variable properties, prefixed with the `var` keyword. Gettable and settable properties are indicated by writing `{ get set }` after their type declaration, and gettable properties are indicated by writing `{ get }`.







1.  `protocol` `SomeProtocol` {
2.  `    var` `mustBeSettable`: `Int` { `get` `set` }
3.  `    var` `doesNotNeedToBeSettable`: `Int` { `get` }
4.  `}`







Always prefix type property requirements with the `static` keyword when you define them in a protocol. This rule pertains even though type property requirements can be prefixed with the `class` or `static` keyword when implemented by a class:







1.  `protocol` `AnotherProtocol` {
2.  `    static` `var` `someTypeProperty`: `Int` { `get` `set` }
3.  `}`







Here’s an example of a protocol with a single instance property requirement:







1.  `protocol` `FullyNamed` {
2.  `    var` `fullName`: `String` { `get` }
3.  `}`







The `FullyNamed` protocol requires a conforming type to provide a fully-qualified name. The protocol doesn’t specify anything else about the nature of the conforming type—it only specifies that the type must be able to provide a full name for itself. The protocol states that any `FullyNamed` type must have a gettable instance property called `fullName`, which is of type `String`.

Here’s an example of a simple structure that adopts and conforms to the `FullyNamed` protocol:







1.  `struct` `Person`: `FullyNamed` {
2.  `    var` `fullName`: `String`
3.  `}`
4.  `let` `john` = `Person`(`fullName`: `"John Appleseed"`)
5.  `// john.fullName is "John Appleseed"`







This example defines a structure called `Person`, which represents a specific named person. It states that it adopts the `FullyNamed` protocol as part of the first line of its definition.

Each instance of `Person` has a single stored property called `fullName`, which is of type `String`. This matches the single requirement of the `FullyNamed` protocol, and means that `Person` has correctly conformed to the protocol. (Swift reports an error at compile-time if a protocol requirement is not fulfilled.)

Here’s a more complex class, which also adopts and conforms to the `FullyNamed` protocol:







1.  `class` `Starship`: `FullyNamed` {
2.  `    var` `prefix`: `String`?
3.  `    var` `name`: `String`
4.  `    init`(`name`: `String`, `prefix`: `String`? = `nil`) {
5.  `        self`.`name` = `name`
6.  `        self`.`prefix` = `prefix`
7.  `    }`
8.  `    var` `fullName`: `String` {
9.  `        return` (`prefix` != `nil` ? `prefix`! + `" "` : `""`) + `name`
10. `    }`
11. `}`
12. `var` `ncc1701` = `Starship`(`name`: `"Enterprise"`, `prefix`: `"USS"`)
13. `// ncc1701.fullName is "USS Enterprise"`







This class implements the `fullName` property requirement as a computed read-only property for a starship. Each `Starship` class instance stores a mandatory `name` and an optional `prefix`. The `fullName` property uses the `prefix` value if it exists, and prepends it to the beginning of `name` to create a full name for the starship.





[‌]()
### Method Requirements 

Protocols can require specific instance methods and type methods to be implemented by conforming types. These methods are written as part of the protocol’s definition in exactly the same way as for normal instance and type methods, but without curly braces or a method body. Variadic parameters are allowed, subject to the same rules as for normal methods. Default values, however, cannot be specified for method parameters within a protocol’s definition.

As with type property requirements, you always prefix type method requirements with the `static` keyword when they are defined in a protocol. This is true even though type method requirements are prefixed with the `class` or `static` keyword when implemented by a class:







1.  `protocol` `SomeProtocol` {
2.  `    static` `func` `someTypeMethod`()
3.  `}`







The following example defines a protocol with a single instance method requirement:







1.  `protocol` `RandomNumberGenerator` {
2.  `    func` `random`() -&gt; `Double`
3.  `}`







This protocol, `RandomNumberGenerator`, requires any conforming type to have an instance method called `random`, which returns a `Double` value whenever it is called. Although it is not specified as part of the protocol, it is assumed that this value will be a number from `0.0` up to (but not including) `1.0`.

The `RandomNumberGenerator` protocol does not make any assumptions about how each random number will be generated—it simply requires the generator to provide a standard way to generate a new random number.

Here’s an implementation of a class that adopts and conforms to the `RandomNumberGenerator` protocol. This class implements a pseudorandom number generator algorithm known as a *linear congruential generator*:







1.  `class` `LinearCongruentialGenerator`: `RandomNumberGenerator` {
2.  `    var` `lastRandom` = `42.0`
3.  `    let` `m` = `139968.0`
4.  `    let` `a` = `3877.0`
5.  `    let` `c` = `29573.0`
6.  `    func` `random`() -&gt; `Double` {
7.  `        lastRandom` = ((`lastRandom` \* `a` + `c`) % `m`)
8.  `        return` `lastRandom` / `m`
9.  `    }`
10. `}`
11. `let` `generator` = `LinearCongruentialGenerator`()
12. `print`(`"Here's a random number: `\\(`generator`.`random`())`"`)
13. `// prints "Here's a random number: 0.37464991998171"`
14. `print`(`"And another one: `\\(`generator`.`random`())`"`)
15. `// prints "And another one: 0.729023776863283"`











[‌]()
### Mutating Method Requirements 

It is sometimes necessary for a method to modify (or *mutate*) the instance it belongs to. For instance methods on value types (that is, structures and enumerations) you place the `mutating` keyword before a method’s `func` keyword to indicate that the method is allowed to modify the instance it belongs to and any properties of that instance. This process is described in [Modifying Value Types from Within Instance Methods](Methods.md#TP40016643-CH15-ID239).

If you define a protocol instance method requirement that is intended to mutate instances of any type that adopts the protocol, mark the method with the `mutating` keyword as part of the protocol’s definition. This enables structures and enumerations to adopt the protocol and satisfy that method requirement.



Note

If you mark a protocol instance method requirement as `mutating`, you do not need to write the `mutating` keyword when writing an implementation of that method for a class. The `mutating` keyword is only used by structures and enumerations.



The example below defines a protocol called `Togglable`, which defines a single instance method requirement called `toggle`. As its name suggests, the `toggle()` method is intended to toggle or invert the state of any conforming type, typically by modifying a property of that type.

The `toggle()` method is marked with the `mutating` keyword as part of the `Togglable` protocol definition, to indicate that the method is expected to mutate the state of a conforming instance when it is called:







1.  `protocol` `Togglable` {
2.  `    mutating` `func` `toggle`()
3.  `}`







If you implement the `Togglable` protocol for a structure or enumeration, that structure or enumeration can conform to the protocol by providing an implementation of the `toggle()` method that is also marked as `mutating`.

The example below defines an enumeration called `OnOffSwitch`. This enumeration toggles between two states, indicated by the enumeration cases `On` and `Off`. The enumeration’s `toggle` implementation is marked as `mutating`, to match the `Togglable` protocol’s requirements:







1.  `enum` `OnOffSwitch`: `Togglable` {
2.  `    case` `Off`, `On`
3.  `    mutating` `func` `toggle`() {
4.  `        switch` `self` {
5.  `        case` `Off`:
6.  `            self` = `On`
7.  `        case` `On`:
8.  `            self` = `Off`
9.  `        }`
10. `    }`
11. `}`
12. `var` `lightSwitch` = `OnOffSwitch`.`Off`
13. `lightSwitch`.`toggle`()
14. `// lightSwitch is now equal to .On`











[‌]()
### Initializer Requirements 

Protocols can require specific initializers to be implemented by conforming types. You write these initializers as part of the protocol’s definition in exactly the same way as for normal initializers, but without curly braces or an initializer body:







1.  `protocol` `SomeProtocol` {
2.  `    init`(`someParameter`: `Int`)
3.  `}`









[‌]()
### Class Implementations of Protocol Initializer Requirements 

You can implement a protocol initializer requirement on a conforming class as either a designated initializer or a convenience initializer. In both cases, you must mark the initializer implementation with the `required` modifier:







1.  `class` `SomeClass`: `SomeProtocol` {
2.  `    required` `init`(`someParameter`: `Int`) {
3.  `        // initializer implementation goes here`
4.  `    }`
5.  `}`







The use of the `required` modifier ensures that you provide an explicit or inherited implementation of the initializer requirement on all subclasses of the conforming class, such that they also conform to the protocol.

For more information on required initializers, see [Required Initializers](Initialization.md#TP40016643-CH18-ID231).



Note

You do not need to mark protocol initializer implementations with the `required` modifier on classes that are marked with the `final` modifier, because final classes cannot be subclassed. For more on the `final` modifier, see [Preventing Overrides](Inheritance.md#TP40016643-CH17-ID202).



If a subclass overrides a designated initializer from a superclass, and also implements a matching initializer requirement from a protocol, mark the initializer implementation with both the `required` and `override` modifiers:







1.  `protocol` `SomeProtocol` {
2.  `    init`()
3.  `}`
4.  ` `
5.  `class` `SomeSuperClass` {
6.  `    init`() {
7.  `        // initializer implementation goes here`
8.  `    }`
9.  `}`
10. ` `
11. `class` `SomeSubClass`: `SomeSuperClass`, `SomeProtocol` {
12. `    // "required" from SomeProtocol conformance; "override" from SomeSuperClass`
13. `    required` `override` `init`() {
14. `        // initializer implementation goes here`
15. `    }`
16. `}`











[‌]()
### Failable Initializer Requirements 

Protocols can define failable initializer requirements for conforming types, as defined in [Failable Initializers](Initialization.md#TP40016643-CH18-ID224).

A failable initializer requirement can be satisfied by a failable or nonfailable initializer on a conforming type. A nonfailable initializer requirement can be satisfied by a nonfailable initializer or an implicitly unwrapped failable initializer.







[‌]()
### Protocols as Types 

Protocols do not actually implement any functionality themselves. Nonetheless, any protocol you create will become a fully-fledged type for use in your code.

Because it is a type, you can use a protocol in many places where other types are allowed, including:

-   As a parameter type or return type in a function, method, or initializer

-   As the type of a constant, variable, or property

-   As the type of items in an array, dictionary, or other container



Note

Because protocols are types, begin their names with a capital letter (such as `FullyNamed` and `RandomNumberGenerator`) to match the names of other types in Swift (such as `Int`, `String`, and `Double`).



Here’s an example of a protocol used as a type:







1.  `class` `Dice` {
2.  `    let` `sides`: `Int`
3.  `    let` `generator`: `RandomNumberGenerator`
4.  `    init`(`sides`: `Int`, `generator`: `RandomNumberGenerator`) {
5.  `        self`.`sides` = `sides`
6.  `        self`.`generator` = `generator`
7.  `    }`
8.  `    func` `roll`() -&gt; `Int` {
9.  `        return` `Int`(`generator`.`random`() \* `Double`(`sides`)) + `1`
10. `    }`
11. `}`







This example defines a new class called `Dice`, which represents an *n*-sided dice for use in a board game. `Dice` instances have an integer property called `sides`, which represents how many sides they have, and a property called `generator`, which provides a random number generator from which to create dice roll values.

The `generator` property is of type `RandomNumberGenerator`. Therefore, you can set it to an instance of *any* type that adopts the `RandomNumberGenerator` protocol. Nothing else is required of the instance you assign to this property, except that the instance must adopt the `RandomNumberGenerator` protocol.

`Dice` also has an initializer, to set up its initial state. This initializer has a parameter called `generator`, which is also of type `RandomNumberGenerator`. You can pass a value of any conforming type in to this parameter when initializing a new `Dice` instance.

`Dice` provides one instance method, `roll`, which returns an integer value between 1 and the number of sides on the dice. This method calls the generator’s `random()` method to create a new random number between `0.0` and `1.0`, and uses this random number to create a dice roll value within the correct range. Because `generator` is known to adopt `RandomNumberGenerator`, it is guaranteed to have a `random()` method to call.

Here’s how the `Dice` class can be used to create a six-sided dice with a `LinearCongruentialGenerator` instance as its random number generator:







1.  `var` `d6` = `Dice`(`sides`: `6`, `generator`: `LinearCongruentialGenerator`())
2.  `for` `_` `in` `1`...`5` {
3.  `    print`(`"Random dice roll is `\\(`d6`.`roll`())`"`)
4.  `}`
5.  `// Random dice roll is 3`
6.  `// Random dice roll is 5`
7.  `// Random dice roll is 4`
8.  `// Random dice roll is 5`
9.  `// Random dice roll is 4`











[‌]()
### Delegation 

*Delegation* is a design pattern that enables a class or structure to hand off (or *delegate*) some of its responsibilities to an instance of another type. This design pattern is implemented by defining a protocol that encapsulates the delegated responsibilities, such that a conforming type (known as a delegate) is guaranteed to provide the functionality that has been delegated. Delegation can be used to respond to a particular action, or to retrieve data from an external source without needing to know the underlying type of that source.

The example below defines two protocols for use with dice-based board games:







1.  `protocol` `DiceGame` {
2.  `    var` `dice`: `Dice` { `get` }
3.  `    func` `play`()
4.  `}`
5.  `protocol` `DiceGameDelegate` {
6.  `    func` `gameDidStart`(`game`: `DiceGame`)
7.  `    func` `game`(`game`: `DiceGame`, `didStartNewTurnWithDiceRoll` `diceRoll`: `Int`)
8.  `    func` `gameDidEnd`(`game`: `DiceGame`)
9.  `}`







The `DiceGame` protocol is a protocol that can be adopted by any game that involves dice. The `DiceGameDelegate` protocol can be adopted by any type to track the progress of a `DiceGame`.

Here’s a version of the *Snakes and Ladders* game originally introduced in [Control Flow](ControlFlow.md). This version is adapted to use a `Dice` instance for its dice-rolls; to adopt the `DiceGame` protocol; and to notify a `DiceGameDelegate` about its progress:







1.  `class` `SnakesAndLadders`: `DiceGame` {
2.  `    let` `finalSquare` = `25`
3.  `    let` `dice` = `Dice`(`sides`: `6`, `generator`: `LinearCongruentialGenerator`())
4.  `    var` `square` = `0`
5.  `    var` `board`: \[`Int`\]
6.  `    init`() {
7.  `        board` = \[`Int`\](`count`: `finalSquare` + `1`, `repeatedValue`: `0`)
8.  `        board`\[`03`\] = +`08`; `board`\[`06`\] = +`11`; `board`\[`09`\] = +`09`; `board`\[`10`\] = +`02`
9.  `        board`\[`14`\] = -`10`; `board`\[`19`\] = -`11`; `board`\[`22`\] = -`02`; `board`\[`24`\] = -`08`
10. `    }`
11. `    var` `delegate`: `DiceGameDelegate`?
12. `    func` `play`() {
13. `        square` = `0`
14. `        delegate`?.`gameDidStart`(`self`)
15. `        gameLoop`: `while` `square` != `finalSquare` {
16. `            let` `diceRoll` = `dice`.`roll`()
17. `            delegate`?.`game`(`self`, `didStartNewTurnWithDiceRoll`: `diceRoll`)
18. `            switch` `square` + `diceRoll` {
19. `            case` `finalSquare`:
20. `                break` `gameLoop`
21. `            case` `let` `newSquare` `where` `newSquare` &gt; `finalSquare`:
22. `                continue` `gameLoop`
23. `            default`:
24. `                square` += `diceRoll`
25. `                square` += `board`\[`square`\]
26. `            }`
27. `        }`
28. `        delegate`?.`gameDidEnd`(`self`)
29. `    }`
30. `}`







For a description of the *Snakes and Ladders* gameplay, see [Break](ControlFlow.md#TP40016643-CH9-ID137) section of the [Control Flow](ControlFlow.md).

This version of the game is wrapped up as a class called `SnakesAndLadders`, which adopts the `DiceGame` protocol. It provides a gettable `dice` property and a `play()` method in order to conform to the protocol. (The `dice` property is declared as a constant property because it does not need to change after initialization, and the protocol only requires that it is gettable.)

The *Snakes and Ladders* game board setup takes place within the class’s `init()` initializer. All game logic is moved into the protocol’s `play` method, which uses the protocol’s required `dice` property to provide its dice roll values.

Note that the `delegate` property is defined as an *optional* `DiceGameDelegate`, because a delegate isn’t required in order to play the game. Because it is of an optional type, the `delegate` property is automatically set to an initial value of `nil`. Thereafter, the game instantiator has the option to set the property to a suitable delegate.

`DiceGameDelegate` provides three methods for tracking the progress of a game. These three methods have been incorporated into the game logic within the `play()` method above, and are called when a new game starts, a new turn begins, or the game ends.

Because the `delegate` property is an *optional* `DiceGameDelegate`, the `play()` method uses optional chaining each time it calls a method on the delegate. If the `delegate` property is nil, these delegate calls fail gracefully and without error. If the `delegate` property is non-nil, the delegate methods are called, and are passed the `SnakesAndLadders` instance as a parameter.

This next example shows a class called `DiceGameTracker`, which adopts the `DiceGameDelegate` protocol:







1.  `class` `DiceGameTracker`: `DiceGameDelegate` {
2.  `    var` `numberOfTurns` = `0`
3.  `    func` `gameDidStart`(`game`: `DiceGame`) {
4.  `        numberOfTurns` = `0`
5.  `        if` `game` `is` `SnakesAndLadders` {
6.  `            print`(`"Started a new game of Snakes and Ladders"`)
7.  `        }`
8.  `        print`(`"The game is using a `\\(`game`.`dice`.`sides`)`-sided dice"`)
9.  `    }`
10. `    func` `game`(`game`: `DiceGame`, `didStartNewTurnWithDiceRoll` `diceRoll`: `Int`) {
11. `        ++numberOfTurns`
12. `        print`(`"Rolled a `\\(`diceRoll`)`"`)
13. `    }`
14. `    func` `gameDidEnd`(`game`: `DiceGame`) {
15. `        print`(`"The game lasted for `\\(`numberOfTurns`)` turns"`)
16. `    }`
17. `}`







`DiceGameTracker` implements all three methods required by `DiceGameDelegate`. It uses these methods to keep track of the number of turns a game has taken. It resets a `numberOfTurns` property to zero when the game starts, increments it each time a new turn begins, and prints out the total number of turns once the game has ended.

The implementation of `gameDidStart` shown above uses the `game` parameter to print some introductory information about the game that is about to be played. The `game` parameter has a type of `DiceGame`, not `SnakesAndLadders`, and so `gameDidStart` can access and use only methods and properties that are implemented as part of the `DiceGame` protocol. However, the method is still able to use type casting to query the type of the underlying instance. In this example, it checks whether `game` is actually an instance of `SnakesAndLadders` behind the scenes, and prints an appropriate message if so.

`gameDidStart` also accesses the `dice` property of the passed `game` parameter. Because `game` is known to conform to the `DiceGame` protocol, it is guaranteed to have a `dice` property, and so the `gameDidStart(_:)` method is able to access and print the dice’s `sides` property, regardless of what kind of game is being played.

Here’s how `DiceGameTracker` looks in action:







1.  `let` `tracker` = `DiceGameTracker`()
2.  `let` `game` = `SnakesAndLadders`()
3.  `game`.`delegate` = `tracker`
4.  `game`.`play`()
5.  `// Started a new game of Snakes and Ladders`
6.  `// The game is using a 6-sided dice`
7.  `// Rolled a 3`
8.  `// Rolled a 5`
9.  `// Rolled a 4`
10. `// Rolled a 5`
11. `// The game lasted for 4 turns`











[‌]()
### Adding Protocol Conformance with an Extension 

You can extend an existing type to adopt and conform to a new protocol, even if you do not have access to the source code for the existing type. Extensions can add new properties, methods, and subscripts to an existing type, and are therefore able to add any requirements that a protocol may demand. For more about extensions, see [Extensions](Extensions.md).



Note

Existing instances of a type automatically adopt and conform to a protocol when that conformance is added to the instance’s type in an extension.



For example, this protocol, called `TextRepresentable`, can be implemented by any type that has a way to be represented as text. This might be a description of itself, or a text version of its current state:







1.  `protocol` `TextRepresentable` {
2.  `    var` `textualDescription`: `String` { `get` }
3.  `}`







The `Dice` class from earlier can be extended to adopt and conform to `TextRepresentable`:







1.  `extension` `Dice`: `TextRepresentable` {
2.  `    var` `textualDescription`: `String` {
3.  `        return` `"A `\\(`sides`)`-sided dice"`
4.  `    }`
5.  `}`







This extension adopts the new protocol in exactly the same way as if `Dice` had provided it in its original implementation. The protocol name is provided after the type name, separated by a colon, and an implementation of all requirements of the protocol is provided within the extension’s curly braces.

Any `Dice` instance can now be treated as `TextRepresentable`:







1.  `let` `d12` = `Dice`(`sides`: `12`, `generator`: `LinearCongruentialGenerator`())
2.  `print`(`d12`.`textualDescription`)
3.  `// prints "A 12-sided dice"`







Similarly, the `SnakesAndLadders` game class can be extended to adopt and conform to the `TextRepresentable` protocol:







1.  `extension` `SnakesAndLadders`: `TextRepresentable` {
2.  `    var` `textualDescription`: `String` {
3.  `        return` `"A game of Snakes and Ladders with `\\(`finalSquare`)` squares"`
4.  `    }`
5.  `}`
6.  `print`(`game`.`textualDescription`)
7.  `// prints "A game of Snakes and Ladders with 25 squares"`









[‌]()
### Declaring Protocol Adoption with an Extension 

If a type already conforms to all of the requirements of a protocol, but has not yet stated that it adopts that protocol, you can make it adopt the protocol with an empty extension:







1.  `struct` `Hamster` {
2.  `    var` `name`: `String`
3.  `    var` `textualDescription`: `String` {
4.  `        return` `"A hamster named `\\(`name`)`"`
5.  `    }`
6.  `}`
7.  `extension` `Hamster`: `TextRepresentable` {}







Instances of `Hamster` can now be used wherever `TextRepresentable` is the required type:







1.  `let` `simonTheHamster` = `Hamster`(`name`: `"Simon"`)
2.  `let` `somethingTextRepresentable`: `TextRepresentable` = `simonTheHamster`
3.  `print`(`somethingTextRepresentable`.`textualDescription`)
4.  `// prints "A hamster named Simon"`









Note

Types do not automatically adopt a protocol just by satisfying its requirements. They must always explicitly declare their adoption of the protocol.









[‌]()
### Collections of Protocol Types 

A protocol can be used as the type to be stored in a collection such as an array or a dictionary, as mentioned in [Protocols as Types](Protocols.md#TP40016643-CH25-ID275). This example creates an array of `TextRepresentable` things:







1.  `let` `things`: \[`TextRepresentable`\] = \[`game`, `d12`, `simonTheHamster`\]







It is now possible to iterate over the items in the array, and print each item’s textual description:







1.  `for` `thing` `in` `things` {
2.  `    print`(`thing`.`textualDescription`)
3.  `}`
4.  `// A game of Snakes and Ladders with 25 squares`
5.  `// A 12-sided dice`
6.  `// A hamster named Simon`







Note that the `thing` constant is of type `TextRepresentable`. It is not of type `Dice`, or `DiceGame`, or `Hamster`, even if the actual instance behind the scenes is of one of those types. Nonetheless, because it is of type `TextRepresentable`, and anything that is `TextRepresentable` is known to have a `textualDescription` property, it is safe to access `thing.textualDescription` each time through the loop.





[‌]()
### Protocol Inheritance 

A protocol can *inherit* one or more other protocols and can add further requirements on top of the requirements it inherits. The syntax for protocol inheritance is similar to the syntax for class inheritance, but with the option to list multiple inherited protocols, separated by commas:







1.  `protocol` `InheritingProtocol`: `SomeProtocol`, `AnotherProtocol` {
2.  `    // protocol definition goes here`
3.  `}`







Here’s an example of a protocol that inherits the `TextRepresentable` protocol from above:







1.  `protocol` `PrettyTextRepresentable`: `TextRepresentable` {
2.  `    var` `prettyTextualDescription`: `String` { `get` }
3.  `}`







This example defines a new protocol, `PrettyTextRepresentable`, which inherits from `TextRepresentable`. Anything that adopts `PrettyTextRepresentable` must satisfy all of the requirements enforced by `TextRepresentable`, *plus* the additional requirements enforced by `PrettyTextRepresentable`. In this example, `PrettyTextRepresentable` adds a single requirement to provide a gettable property called `prettyTextualDescription` that returns a `String`.

The `SnakesAndLadders` class can be extended to adopt and conform to `PrettyTextRepresentable`:







1.  `extension` `SnakesAndLadders`: `PrettyTextRepresentable` {
2.  `    var` `prettyTextualDescription`: `String` {
3.  `        var` `output` = `textualDescription` + `":\n"`
4.  `        for` `index` `in` `1`...`finalSquare` {
5.  `            switch` `board`\[`index`\] {
6.  `            case` `let` `ladder` `where` `ladder` &gt; `0`:
7.  `                output` += `"▲ "`
8.  `            case` `let` `snake` `where` `snake` &lt; `0`:
9.  `                output` += `"▼ "`
10. `            default`:
11. `                output` += `"○ "`
12. `            }`
13. `        }`
14. `        return` `output`
15. `    }`
16. `}`







This extension states that it adopts the `PrettyTextRepresentable` protocol and provides an implementation of the `prettyTextualDescription` property for the `SnakesAndLadders` type. Anything that is `PrettyTextRepresentable` must also be `TextRepresentable`, and so the implementation of `prettyTextualDescription` starts by accessing the `textualDescription` property from the `TextRepresentable` protocol to begin an output string. It appends a colon and a line break, and uses this as the start of its pretty text representation. It then iterates through the array of board squares, and appends a geometric shape to represent the contents of each square:

-   If the square’s value is greater than `0`, it is the base of a ladder, and is represented by `▲`.

-   If the square’s value is less than `0`, it is the head of a snake, and is represented by `▼`.

-   Otherwise, the square’s value is `0`, and it is a “free” square, represented by `○`.

The `prettyTextualDescription` property can now be used to print a pretty text description of any `SnakesAndLadders` instance:







1.  `print`(`game`.`prettyTextualDescription`)
2.  `// A game of Snakes and Ladders with 25 squares:`
3.  `// ○ ○ ▲ ○ ○ ▲ ○ ○ ▲ ▲ ○ ○ ○ ▼ ○ ○ ○ ○ ▼ ○ ○ ▼ ○ ▼ ○`











[‌]()
### Class-Only Protocols 

You can limit protocol adoption to class types (and not structures or enumerations) by adding the `class` keyword to a protocol’s inheritance list. The `class` keyword must always appear first in a protocol’s inheritance list, before any inherited protocols:







1.  `protocol` `SomeClassOnlyProtocol`: `class`, `SomeInheritedProtocol` {
2.  `    // class-only protocol definition goes here`
3.  `}`







In the example above, `SomeClassOnlyProtocol` can only be adopted by class types. It is a compile-time error to write a structure or enumeration definition that tries to adopt `SomeClassOnlyProtocol`.



Note

Use a class-only protocol when the behavior defined by that protocol’s requirements assumes or requires that a conforming type has reference semantics rather than value semantics. For more on reference and value semantics, see [Structures and Enumerations Are Value Types](ClassesAndStructures.md#TP40016643-CH13-ID88) and [Classes Are Reference Types](ClassesAndStructures.md#TP40016643-CH13-ID89).







[‌]()
### Protocol Composition 

It can be useful to require a type to conform to multiple protocols at once. You can combine multiple protocols into a single requirement with a *protocol composition*. Protocol compositions have the form `protocol`. You can list as many protocols within the pair of angle brackets (`<>`) as you need, separated by commas.

Here’s an example that combines two protocols called `Named` and `Aged` into a single protocol composition requirement on a function parameter:







1.  `protocol` `Named` {
2.  `    var` `name`: `String` { `get` }
3.  `}`
4.  `protocol` `Aged` {
5.  `    var` `age`: `Int` { `get` }
6.  `}`
7.  `struct` `Person`: `Named`, `Aged` {
8.  `    var` `name`: `String`
9.  `    var` `age`: `Int`
10. `}`
11. `func` `wishHappyBirthday`(`celebrator`: `protocol`&lt;`Named`, `Aged`&gt;) {
12. `    print`(`"Happy birthday `\\(`celebrator`.`name`)` - you're `\\(`celebrator`.`age`)`!"`)
13. `}`
14. `let` `birthdayPerson` = `Person`(`name`: `"Malcolm"`, `age`: `21`)
15. `wishHappyBirthday`(`birthdayPerson`)
16. `// prints "Happy birthday Malcolm - you're 21!"`







This example defines a protocol called `Named`, with a single requirement for a gettable `String` property called `name`. It also defines a protocol called `Aged`, with a single requirement for a gettable `Int` property called `age`. Both of these protocols are adopted by a structure called `Person`.

The example also defines a function called `wishHappyBirthday`, which takes a single parameter called `celebrator`. The type of this parameter is `protocol`, which means “any type that conforms to both the `Named` and `Aged` protocols.” It doesn’t matter what specific type is passed to the function, as long as it conforms to both of the required protocols.

The example then creates a new `Person` instance called `birthdayPerson` and passes this new instance to the `wishHappyBirthday(_:)` function. Because `Person` conforms to both protocols, this is a valid call, and the `wishHappyBirthday(_:)` function is able to print its birthday greeting.



Note

Protocol compositions do not define a new, permanent protocol type. Rather, they define a temporary local protocol that has the combined requirements of all protocols in the composition.







[‌]()
### Checking for Protocol Conformance 

You can use the `is` and `as` operators described in [Type Casting](TypeCasting.md) to check for protocol conformance, and to cast to a specific protocol. Checking for and casting to a protocol follows exactly the same syntax as checking for and casting to a type:

-   The `is` operator returns `true` if an instance conforms to a protocol and returns `false` if it does not.

-   The `as?` version of the downcast operator returns an optional value of the protocol’s type, and this value is `nil` if the instance does not conform to that protocol.

-   The `as!` version of the downcast operator forces the downcast to the protocol type and triggers a runtime error if the downcast does not succeed.

This example defines a protocol called `HasArea`, with a single property requirement of a gettable `Double` property called `area`:







1.  `protocol` `HasArea` {
2.  `    var` `area`: `Double` { `get` }
3.  `}`







Here are two classes, `Circle` and `Country`, both of which conform to the `HasArea` protocol:







1.  `class` `Circle`: `HasArea` {
2.  `    let` `pi` = `3.1415927`
3.  `    var` `radius`: `Double`
4.  `    var` `area`: `Double` { `return` `pi` \* `radius` \* `radius` }
5.  `    init`(`radius`: `Double`) { `self`.`radius` = `radius` }
6.  `}`
7.  `class` `Country`: `HasArea` {
8.  `    var` `area`: `Double`
9.  `    init`(`area`: `Double`) { `self`.`area` = `area` }
10. `}`







The `Circle` class implements the `area` property requirement as a computed property, based on a stored `radius` property. The `Country` class implements the `area` requirement directly as a stored property. Both classes correctly conform to the `HasArea` protocol.

Here’s a class called `Animal`, which does not conform to the `HasArea` protocol:







1.  `class` `Animal` {
2.  `    var` `legs`: `Int`
3.  `    init`(`legs`: `Int`) { `self`.`legs` = `legs` }
4.  `}`







The `Circle`, `Country` and `Animal` classes do not have a shared base class. Nonetheless, they are all classes, and so instances of all three types can be used to initialize an array that stores values of type `AnyObject`:







1.  `let` `objects`: \[`AnyObject`\] = \[
2.  `    Circle`(`radius`: `2.0`),
3.  `    Country`(`area`: `243_610`),
4.  `    Animal`(`legs`: `4`)
5.  `]`







The `objects` array is initialized with an array literal containing a `Circle` instance with a radius of 2 units; a `Country` instance initialized with the surface area of the United Kingdom in square kilometers; and an `Animal` instance with four legs.

The `objects` array can now be iterated, and each object in the array can be checked to see if it conforms to the `HasArea` protocol:







1.  `for` `object` `in` `objects` {
2.  `    if` `let` `objectWithArea` = `object` `as`? `HasArea` {
3.  `        print`(`"Area is `\\(`objectWithArea`.`area`)`"`)
4.  `    } else` {
5.  `        print`(`"Something that doesn't have an area"`)
6.  `    }`
7.  `}`
8.  `// Area is 12.5663708`
9.  `// Area is 243610.0`
10. `// Something that doesn't have an area`







Whenever an object in the array conforms to the `HasArea` protocol, the optional value returned by the `as?` operator is unwrapped with optional binding into a constant called `objectWithArea`. The `objectWithArea` constant is known to be of type `HasArea`, and so its `area` property can be accessed and printed in a type-safe way.

Note that the underlying objects are not changed by the casting process. They continue to be a `Circle`, a `Country` and an `Animal`. However, at the point that they are stored in the `objectWithArea` constant, they are only known to be of type `HasArea`, and so only their `area` property can be accessed.





[‌]()
### Optional Protocol Requirements 

You can define *optional requirements* for protocols, These requirements do not have to be implemented by types that conform to the protocol. Optional requirements are prefixed by the `optional` modifier as part of the protocol’s definition. When you use a method or property in an optional requirement, its type automatically becomes an optional. For example, a method of type `(Int) -> String` becomes `((Int) -> String)?`. Note that the entire function type is wrapped in the optional, not method’s the return value.

An optional protocol requirement can be called with optional chaining, to account for the possibility that the requirement was not implemented by a type that conforms to the protocol. You check for an implementation of an optional method by writing a question mark after the name of the method when it is called, such as `someOptionalMethod?(someArgument)`. For information on optional chaining, see [Optional Chaining](OptionalChaining.md).



Note

Optional protocol requirements can only be specified if your protocol is marked with the `@objc` attribute.

This attribute indicates that the protocol should be exposed to Objective-C code and is described in *Using Swift with Cocoa and Objective-C (Swift 2.1)*. Even if you are not interoperating with Objective-C, you need to mark your protocols with the `@objc` attribute if you want to specify optional requirements.

Note also that `@objc` protocols can be adopted only by classes that inherit from Objective-C classes or other `@objc` classes. They can’t be adopted by structures or enumerations.



The following example defines an integer-counting class called `Counter`, which uses an external data source to provide its increment amount. This data source is defined by the `CounterDataSource` protocol, which has two optional requirements:







1.  `@objc` `protocol` `CounterDataSource` {
2.  `    optional` `func` `incrementForCount`(`count`: `Int`) -&gt; `Int`
3.  `    optional` `var` `fixedIncrement`: `Int` { `get` }
4.  `}`







The `CounterDataSource` protocol defines an optional method requirement called `incrementForCount(_:)` and an optional property requirement called `fixedIncrement`. These requirements define two different ways for data sources to provide an appropriate increment amount for a `Counter` instance.



Note

Strictly speaking, you can write a custom class that conforms to `CounterDataSource` without implementing *either* protocol requirement. They are both optional, after all. Although technically allowed, this wouldn’t make for a very good data source.



The `Counter` class, defined below, has an optional `dataSource` property of type `CounterDataSource?`:







1.  `class` `Counter` {
2.  `    var` `count` = `0`
3.  `    var` `dataSource`: `CounterDataSource`?
4.  `    func` `increment`() {
5.  `        if` `let` `amount` = `dataSource`?.`incrementForCount`?(`count`) {
6.  `            count` += `amount`
7.  `        } else` `if` `let` `amount` = `dataSource`?.`fixedIncrement` {
8.  `            count` += `amount`
9.  `        }`
10. `    }`
11. `}`







The `Counter` class stores its current value in a variable property called `count`. The `Counter` class also defines a method called `increment`, which increments the `count` property every time the method is called.

The `increment()` method first tries to retrieve an increment amount by looking for an implementation of the `incrementForCount(_:)` method on its data source. The `increment()` method uses optional chaining to try to call `incrementForCount(_:)`, and passes the current `count` value as the method’s single argument.

Note that *two* levels of optional chaining are at play here. First, it is possible that `dataSource` may be `nil`, and so `dataSource` has a question mark after its name to indicate that `incrementForCount(_:)` should be called only if `dataSource` isn’t `nil`. Second, even if `dataSource` *does* exist, there is no guarantee that it implements `incrementForCount(_:)`, because it is an optional requirement. Here, the possibility that `incrementForCount(_:)` might not be implemented is also handled by optional chaining. The call to `incrementForCount(_:)` happens only if `incrementForCount(_:)` exists—that is, if it isn’t `nil`. This is why `incrementForCount(_:)` is also written with a question mark after its name.

Because the call to `incrementForCount(_:)` can fail for either of these two reasons, the call returns an *optional* `Int` value. This is true even though `incrementForCount(_:)` is defined as returning a nonoptional `Int` value in the definition of `CounterDataSource`. Even though there are two optional chaining operations, one after another, the result is still wrapped in a single optional. For more information about using multiple optional chaining operations, see [Linking Multiple Levels of Chaining](OptionalChaining.md#TP40016643-CH21-ID252).

After calling `incrementForCount(_:)`, the optional `Int` that it returns is unwrapped into a constant called `amount`, using optional binding. If the optional `Int` does contain a value—that is, if the delegate and method both exist, and the method returned a value—the unwrapped `amount` is added onto the stored `count` property, and incrementation is complete.

If it is *not* possible to retrieve a value from the `incrementForCount(_:)` method—either because `dataSource` is nil, or because the data source does not implement `incrementForCount(_:)`—then the `increment()` method tries to retrieve a value from the data source’s `fixedIncrement` property instead. The `fixedIncrement` property is also an optional requirement, so its value is an optional `Int` value, even though `fixedIncrement` is defined as a nonoptional `Int` property as part of the `CounterDataSource` protocol definition.

Here’s a simple `CounterDataSource` implementation where the data source returns a constant value of `3` every time it is queried. It does this by implementing the optional `fixedIncrement` property requirement:







1.  `class` `ThreeSource`: `NSObject`, `CounterDataSource` {
2.  `    let` `fixedIncrement` = `3`
3.  `}`







You can use an instance of `ThreeSource` as the data source for a new `Counter` instance:







1.  `var` `counter` = `Counter`()
2.  `counter`.`dataSource` = `ThreeSource`()
3.  `for` `_` `in` `1`...`4` {
4.  `    counter`.`increment`()
5.  `    print`(`counter`.`count`)
6.  `}`
7.  `// 3`
8.  `// 6`
9.  `// 9`
10. `// 12`







The code above creates a new `Counter` instance; sets its data source to be a new `ThreeSource` instance; and calls the counter’s `increment()` method four times. As expected, the counter’s `count` property increases by three each time `increment()` is called.

Here’s a more complex data source called `TowardsZeroSource`, which makes a `Counter` instance count up or down towards zero from its current `count` value:







1.  `@objc` `class` `TowardsZeroSource`: `NSObject`, `CounterDataSource` {
2.  `    func` `incrementForCount`(`count`: `Int`) -&gt; `Int` {
3.  `        if` `count` == `0` {
4.  `            return` `0`
5.  `        } else` `if` `count` &lt; `0` {
6.  `            return` `1`
7.  `        } else` {
8.  `            return` -`1`
9.  `        }`
10. `    }`
11. `}`







The `TowardsZeroSource` class implements the optional `incrementForCount(_:)` method from the `CounterDataSource` protocol and uses the `count` argument value to work out which direction to count in. If `count` is already zero, the method returns `0` to indicate that no further counting should take place.

You can use an instance of `TowardsZeroSource` with the existing `Counter` instance to count from `-4` to zero. Once the counter reaches zero, no more counting takes place:







1.  `counter`.`count` = -`4`
2.  `counter`.`dataSource` = `TowardsZeroSource`()
3.  `for` `_` `in` `1`...`5` {
4.  `    counter`.`increment`()
5.  `    print`(`counter`.`count`)
6.  `}`
7.  `// -3`
8.  `// -2`
9.  `// -1`
10. `// 0`
11. `// 0`











[‌]()
### Protocol Extensions 

Protocols can be extended to provide method and property implementations to conforming types. This allows you to define behavior on protocols themselves, rather than in each type’s individual conformance or in a global function.

For example, the `RandomNumberGenerator` protocol can be extended to provide a `randomBool()` method, which uses the result of the required `random()` method to return a random `Bool` value:







1.  `extension` `RandomNumberGenerator` {
2.  `    func` `randomBool`() -&gt; `Bool` {
3.  `        return` `random`() &gt; `0.5`
4.  `    }`
5.  `}`







By creating an extension on the protocol, all conforming types automatically gain this method implementation without any additional modification.







1.  `let` `generator` = `LinearCongruentialGenerator`()
2.  `print`(`"Here's a random number: `\\(`generator`.`random`())`"`)
3.  `// prints "Here's a random number: 0.37464991998171"`
4.  `print`(`"And here's a random Boolean: `\\(`generator`.`randomBool`())`"`)
5.  `// prints "And here's a random Boolean: true"`









[‌]()
### Providing Default Implementations 

You can use protocol extensions to provide a default implementation to any method or property requirement of that protocol. If a conforming type provides its own implementation of a required method or property, that implementation will be used instead of the one provided by the extension.



Note

Protocol requirements with default implementations provided by extensions are distinct from optional protocol requirements. Although conforming types don’t have to provide their own implementation of either, requirements with default implementations can be called without optional chaining.



For example, the `PrettyTextRepresentable` protocol, which inherits the `TextRepresentable` protocol can provide a default implementation of its required `prettyTextualDescription` property to simply return the result of accessing the `textualDescription` property:







1.  `extension` `PrettyTextRepresentable` {
2.  `    var` `prettyTextualDescription`: `String` {
3.  `        return` `textualDescription`
4.  `    }`
5.  `}`











[‌]()
### Adding Constraints to Protocol Extensions 

When you define a protocol extension, you can specify constraints that conforming types must satisfy before the methods and properties of the extension are available. You write these constraints after the name of the protocol you’re extending using a `where` clause, as described in [Where Clauses](Generics.md#TP40016643-CH26-ID192).

For instance, you can define an extension to the `CollectionType` protocol that applies to any collection whose elements conform to the `TextRepresentable` protocol from the example above.







1.  `extension` `CollectionType` `where` `Generator`.`Element`: `TextRepresentable` {
2.  `    var` `textualDescription`: `String` {
3.  `        let` `itemsAsText` = `self`.`map` { `$0`.`textualDescription` }
4.  `        return` `"["` + `itemsAsText`.`joinWithSeparator`(`", "`) + `"]"`
5.  `    }`
6.  `}`







The `textualDescription` property returns the textual description of the entire collection by concatenating the textual representation of each element in the collection into a comma-separated list, enclosed in brackets.

Consider the `Hamster` structure from before, which conforms to the `TextRepresentable` protocol, and an array of `Hamster` values:







1.  `let` `murrayTheHamster` = `Hamster`(`name`: `"Murray"`)
2.  `let` `morganTheHamster` = `Hamster`(`name`: `"Morgan"`)
3.  `let` `mauriceTheHamster` = `Hamster`(`name`: `"Maurice"`)
4.  `let` `hamsters` = \[`murrayTheHamster`, `morganTheHamster`, `mauriceTheHamster`\]







Because `Array` conforms to `CollectionType` and the array’s elements conform to the `TextRepresentable` protocol, the array can use the `textualDescription` property to get a textual representation of its contents:







1.  `print`(`hamsters`.`textualDescription`)
2.  `// prints "[A hamster named Murray, A hamster named Morgan, A hamster named Maurice]"`









Note

If a conforming type satisfies the requirements for multiple constrained extensions that provide implementations for the same method or property, Swift will use the implementation corresponding to the most specialized constraints.










