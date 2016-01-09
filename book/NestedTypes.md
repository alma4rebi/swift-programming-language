



[‌]()[‌]()
Nested Types 
------------



Enumerations are often created to support a specific class or structure’s functionality. Similarly, it can be convenient to define utility classes and structures purely for use within the context of a more complex type. To accomplish this, Swift enables you to define *nested types*, whereby you nest supporting enumerations, classes, and structures within the definition of the type they support.

To nest a type within another type, write its definition within the outer braces of the type it supports. Types can be nested to as many levels as are required.





[‌]()
### Nested Types in Action 

The example below defines a structure called `BlackjackCard`, which models a playing card as used in the game of Blackjack. The `BlackJack` structure contains two nested enumeration types called `Suit` and `Rank`.

In Blackjack, the Ace cards have a value of either one or eleven. This feature is represented by a structure called `Values`, which is nested within the `Rank` enumeration:







1.  `struct` `BlackjackCard` {
2.  `    `
3.  `    // nested Suit enumeration`
4.  `    enum` `Suit`: `Character` {
5.  `        case` `Spades` = `"♠"`, `Hearts` = `"♡"`, `Diamonds` = `"♢"`, `Clubs` = `"♣"`
6.  `    }`
7.  `    `
8.  `    // nested Rank enumeration`
9.  `    enum` `Rank`: `Int` {
10. `        case` `Two` = `2`, `Three`, `Four`, `Five`, `Six`, `Seven`, `Eight`, `Nine`, `Ten`
11. `        case` `Jack`, `Queen`, `King`, `Ace`
12. `        struct` `Values` {
13. `            let` `first`: `Int`, `second`: `Int`?
14. `        }`
15. `        var` `values`: `Values` {
16. `            switch` `self` {
17. `            case` .`Ace`:
18. `                return` `Values`(`first`: `1`, `second`: `11`)
19. `            case` .`Jack`, .`Queen`, .`King`:
20. `                return` `Values`(`first`: `10`, `second`: `nil`)
21. `            default`:
22. `                return` `Values`(`first`: `self`.`rawValue`, `second`: `nil`)
23. `            }`
24. `        }`
25. `    }`
26. `    `
27. `    // BlackjackCard properties and methods`
28. `    let` `rank`: `Rank`, `suit`: `Suit`
29. `    var` `description`: `String` {
30. `        var` `output` = `"suit is `\\(`suit`.`rawValue`)`,"`
31. `        output` += `" value is `\\(`rank`.`values`.`first`)`"`
32. `        if` `let` `second` = `rank`.`values`.`second` {
33. `            output` += `" or `\\(`second`)`"`
34. `        }`
35. `        return` `output`
36. `    }`
37. `}`







The `Suit` enumeration describes the four common playing card suits, together with a raw `Character` value to represent their symbol.

The `Rank` enumeration describes the thirteen possible playing card ranks, together with a raw `Int` value to represent their face value. (This raw `Int` value is not used for the Jack, Queen, King, and Ace cards.)

As mentioned above, the `Rank` enumeration defines a further nested structure of its own, called `Values`. This structure encapsulates the fact that most cards have one value, but the Ace card has two values. The `Values` structure defines two properties to represent this:

-   `first`, of type `Int`

-   `second`, of type `Int?`, or “optional `Int`”

`Rank` also defines a computed property, `values`, which returns an instance of the `Values` structure. This computed property considers the rank of the card and initializes a new `Values` instance with appropriate values based on its rank. It uses special values for `Jack`, `Queen`, `King`, and `Ace`. For the numeric cards, it uses the rank’s raw `Int` value.

The `BlackjackCard` structure itself has two properties—`rank` and `suit`. It also defines a computed property called `description`, which uses the values stored in `rank` and `suit` to build a description of the name and value of the card. The `description` property uses optional binding to check whether there is a second value to display, and if so, inserts additional description detail for that second value.

Because `BlackjackCard` is a structure with no custom initializers, it has an implicit memberwise initializer, as described in [Memberwise Initializers for Structure Types](Initialization.md#TP40016643-CH18-ID214). You can use this initializer to initialize a new constant called `theAceOfSpades`:







1.  `let` `theAceOfSpades` = `BlackjackCard`(`rank`: .`Ace`, `suit`: .`Spades`)
2.  `print`(`"theAceOfSpades: `\\(`theAceOfSpades`.`description`)`"`)
3.  `// prints "theAceOfSpades: suit is ♠, value is 1 or 11"`







Even though `Rank` and `Suit` are nested within `BlackjackCard`, their type can be inferred from context, and so the initialization of this instance is able to refer to the enumeration cases by their case names (`.Ace` and `.Spades`) alone. In the example above, the `description` property correctly reports that the Ace of Spades has a value of `1` or `11`.





[‌]()
### Referring to Nested Types 

To use a nested type outside of its definition context, prefix its name with the name of the type it is nested within:







1.  `let` `heartsSymbol` = `BlackjackCard`.`Suit`.`Hearts`.`rawValue`
2.  `// heartsSymbol is "♡"`







For the example above, this enables the names of `Suit`, `Rank`, and `Values` to be kept deliberately short, because their names are naturally qualified by the context in which they are defined.






