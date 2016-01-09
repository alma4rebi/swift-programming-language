



[‌](){#TP40016643-CH23}[‌](){#TP40016643-CH23-ID242}
Nested Types {#nested-types .chapter-name}
------------



Enumerations are often created to support a specific class or structure’s functionality. Similarly, it can be convenient to define utility classes and structures purely for use within the context of a more complex type. To accomplish this, Swift enables you to define *nested types*, whereby you nest supporting enumerations, classes, and structures within the definition of the type they support.

To nest a type within another type, write its definition within the outer braces of the type it supports. Types can be nested to as many levels as are required.





[‌](){#TP40016643-CH23-ID243}
### Nested Types in Action {#nested-types-in-action .section-name}

The example below defines a structure called `BlackjackCard`{.code-voice}, which models a playing card as used in the game of Blackjack. The `BlackJack`{.code-voice} structure contains two nested enumeration types called `Suit`{.code-voice} and `Rank`{.code-voice}.

In Blackjack, the Ace cards have a value of either one or eleven. This feature is represented by a structure called `Values`{.code-voice}, which is nested within the `Rank`{.code-voice} enumeration:







1.  `struct`{.code-voice} `BlackjackCard`{.vc} {
2.  `    `{.code-voice}
3.  `    // nested Suit enumeration`{.code-voice}
4.  `    enum`{.code-voice} `Suit`{.vc}: `Character`{.n} {
5.  `        case`{.code-voice} `Spades`{.vc} = `"♠"`{.s}, `Hearts`{.vc} = `"♡"`{.s}, `Diamonds`{.vc} = `"♢"`{.s}, `Clubs`{.vc} = `"♣"`{.s}
6.  `    }`{.code-voice}
7.  `    `{.code-voice}
8.  `    // nested Rank enumeration`{.code-voice}
9.  `    enum`{.code-voice} `Rank`{.vc}: `Int`{.n} {
10. `        case`{.code-voice} `Two`{.vc} = `2`{.m}, `Three`{.vc}, `Four`{.vc}, `Five`{.vc}, `Six`{.vc}, `Seven`{.vc}, `Eight`{.vc}, `Nine`{.vc}, `Ten`{.vc}
11. `        case`{.code-voice} `Jack`{.vc}, `Queen`{.vc}, `King`{.vc}, `Ace`{.vc}
12. `        struct`{.code-voice} `Values`{.vc} {
13. `            let`{.code-voice} `first`{.vc}: `Int`{.n}, `second`{.vc}: `Int`{.n}?
14. `        }`{.code-voice}
15. `        var`{.code-voice} `values`{.vc}: `Values`{.n} {
16. `            switch`{.code-voice} `self`{.kt} {
17. `            case`{.code-voice} .`Ace`{.vc}:
18. `                return`{.code-voice} `Values`{.vc}(`first`{.vc}: `1`{.m}, `second`{.vc}: `11`{.m})
19. `            case`{.code-voice} .`Jack`{.vc}, .`Queen`{.vc}, .`King`{.vc}:
20. `                return`{.code-voice} `Values`{.vc}(`first`{.vc}: `10`{.m}, `second`{.vc}: `nil`{.kt})
21. `            default`{.code-voice}:
22. `                return`{.code-voice} `Values`{.vc}(`first`{.vc}: `self`{.kt}.`rawValue`{.vc}, `second`{.vc}: `nil`{.kt})
23. `            }`{.code-voice}
24. `        }`{.code-voice}
25. `    }`{.code-voice}
26. `    `{.code-voice}
27. `    // BlackjackCard properties and methods`{.code-voice}
28. `    let`{.code-voice} `rank`{.vc}: `Rank`{.n}, `suit`{.vc}: `Suit`{.n}
29. `    var`{.code-voice} `description`{.vc}: `String`{.n} {
30. `        var`{.code-voice} `output`{.vc} = `"suit is `{.s}\\(`suit`{.vc}.`rawValue`{.vc})`,"`{.s}
31. `        output`{.code-voice} += `" value is `{.s}\\(`rank`{.vc}.`values`{.vc}.`first`{.vc})`"`{.s}
32. `        if`{.code-voice} `let`{.kt} `second`{.vc} = `rank`{.vc}.`values`{.vc}.`second`{.vc} {
33. `            output`{.code-voice} += `" or `{.s}\\(`second`{.vc})`"`{.s}
34. `        }`{.code-voice}
35. `        return`{.code-voice} `output`{.vc}
36. `    }`{.code-voice}
37. `}`{.code-voice}







The `Suit`{.code-voice} enumeration describes the four common playing card suits, together with a raw `Character`{.code-voice} value to represent their symbol.

The `Rank`{.code-voice} enumeration describes the thirteen possible playing card ranks, together with a raw `Int`{.code-voice} value to represent their face value. (This raw `Int`{.code-voice} value is not used for the Jack, Queen, King, and Ace cards.)

As mentioned above, the `Rank`{.code-voice} enumeration defines a further nested structure of its own, called `Values`{.code-voice}. This structure encapsulates the fact that most cards have one value, but the Ace card has two values. The `Values`{.code-voice} structure defines two properties to represent this:

-   `first`{.code-voice}, of type `Int`{.code-voice}

-   `second`{.code-voice}, of type `Int?`{.code-voice}, or “optional `Int`{.code-voice}”

`Rank`{.code-voice} also defines a computed property, `values`{.code-voice}, which returns an instance of the `Values`{.code-voice} structure. This computed property considers the rank of the card and initializes a new `Values`{.code-voice} instance with appropriate values based on its rank. It uses special values for `Jack`{.code-voice}, `Queen`{.code-voice}, `King`{.code-voice}, and `Ace`{.code-voice}. For the numeric cards, it uses the rank’s raw `Int`{.code-voice} value.

The `BlackjackCard`{.code-voice} structure itself has two properties—`rank`{.code-voice} and `suit`{.code-voice}. It also defines a computed property called `description`{.code-voice}, which uses the values stored in `rank`{.code-voice} and `suit`{.code-voice} to build a description of the name and value of the card. The `description`{.code-voice} property uses optional binding to check whether there is a second value to display, and if so, inserts additional description detail for that second value.

Because `BlackjackCard`{.code-voice} is a structure with no custom initializers, it has an implicit memberwise initializer, as described in [Memberwise Initializers for Structure Types](Initialization.md#TP40016643-CH18-ID214). You can use this initializer to initialize a new constant called `theAceOfSpades`{.code-voice}:







1.  `let`{.code-voice} `theAceOfSpades`{.vc} = `BlackjackCard`{.vc}(`rank`{.vc}: .`Ace`{.vc}, `suit`{.vc}: .`Spades`{.vc})
2.  `print`{.code-voice}(`"theAceOfSpades: `{.s}\\(`theAceOfSpades`{.vc}.`description`{.vc})`"`{.s})
3.  `// prints "theAceOfSpades: suit is ♠, value is 1 or 11"`{.code-voice}







Even though `Rank`{.code-voice} and `Suit`{.code-voice} are nested within `BlackjackCard`{.code-voice}, their type can be inferred from context, and so the initialization of this instance is able to refer to the enumeration cases by their case names (`.Ace`{.code-voice} and `.Spades`{.code-voice}) alone. In the example above, the `description`{.code-voice} property correctly reports that the Ace of Spades has a value of `1`{.code-voice} or `11`{.code-voice}.





[‌](){#TP40016643-CH23-ID244}
### Referring to Nested Types {#referring-to-nested-types .section-name}

To use a nested type outside of its definition context, prefix its name with the name of the type it is nested within:







1.  `let`{.code-voice} `heartsSymbol`{.vc} = `BlackjackCard`{.vc}.`Suit`{.vc}.`Hearts`{.vc}.`rawValue`{.vc}
2.  `// heartsSymbol is "♡"`{.code-voice}







For the example above, this enables the names of `Suit`{.code-voice}, `Rank`{.code-voice}, and `Values`{.code-voice} to be kept deliberately short, because their names are naturally qualified by the context in which they are defined.






