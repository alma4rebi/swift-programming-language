



[‌](){#TP40016643-CH22}[‌](){#TP40016643-CH22-ID338}
Type Casting {#type-casting .chapter-name}
------------



*Type casting* is a way to check the type of an instance, or to treat that instance as a different superclass or subclass from somewhere else in its own class hierarchy.

Type casting in Swift is implemented with the `is`{.code-voice} and `as`{.code-voice} operators. These two operators provide a simple and expressive way to check the type of a value or cast a value to a different type.

You can also use type casting to check whether a type conforms to a protocol, as described in [Checking for Protocol Conformance](Protocols.md#TP40016643-CH25-ID283).





[‌](){#TP40016643-CH22-ID339}
### Defining a Class Hierarchy for Type Casting {#defining-a-class-hierarchy-for-type-casting .section-name}

You can use type casting with a hierarchy of classes and subclasses to check the type of a particular class instance and to cast that instance to another class within the same hierarchy. The three code snippets below define a hierarchy of classes and an array containing instances of those classes, for use in an example of type casting.

The first snippet defines a new base class called `MediaItem`{.code-voice}. This class provides basic functionality for any kind of item that appears in a digital media library. Specifically, it declares a `name`{.code-voice} property of type `String`{.code-voice}, and an `init name`{.code-voice} initializer. (It is assumed that all media items, including all movies and songs, will have a name.)







1.  `class`{.code-voice} `MediaItem`{.vc} {
2.  `    var`{.code-voice} `name`{.vc}: `String`{.n}
3.  `    init`{.code-voice}(`name`{.vc}: `String`{.n}) {
4.  `        self`{.code-voice}.`name`{.vc} = `name`{.vc}
5.  `    }`{.code-voice}
6.  `}`{.code-voice}







The next snippet defines two subclasses of `MediaItem`{.code-voice}. The first subclass, `Movie`{.code-voice}, encapsulates additional information about a movie or film. It adds a `director`{.code-voice} property on top of the base `MediaItem`{.code-voice} class, with a corresponding initializer. The second subclass, `Song`{.code-voice}, adds an `artist`{.code-voice} property and initializer on top of the base class:







1.  `class`{.code-voice} `Movie`{.vc}: `MediaItem`{.n} {
2.  `    var`{.code-voice} `director`{.vc}: `String`{.n}
3.  `    init`{.code-voice}(`name`{.vc}: `String`{.n}, `director`{.vc}: `String`{.n}) {
4.  `        self`{.code-voice}.`director`{.vc} = `director`{.vc}
5.  `        super`{.code-voice}.`init`{.kt}(`name`{.vc}: `name`{.vc})
6.  `    }`{.code-voice}
7.  `}`{.code-voice}
8.  ` `{.code-voice}
9.  `class`{.code-voice} `Song`{.vc}: `MediaItem`{.n} {
10. `    var`{.code-voice} `artist`{.vc}: `String`{.n}
11. `    init`{.code-voice}(`name`{.vc}: `String`{.n}, `artist`{.vc}: `String`{.n}) {
12. `        self`{.code-voice}.`artist`{.vc} = `artist`{.vc}
13. `        super`{.code-voice}.`init`{.kt}(`name`{.vc}: `name`{.vc})
14. `    }`{.code-voice}
15. `}`{.code-voice}







The final snippet creates a constant array called `library`{.code-voice}, which contains two `Movie`{.code-voice} instances and three `Song`{.code-voice} instances. The type of the `library`{.code-voice} array is inferred by initializing it with the contents of an array literal. Swift’s type checker is able to deduce that `Movie`{.code-voice} and `Song`{.code-voice} have a common superclass of `MediaItem`{.code-voice}, and so it infers a type of `[MediaItem]`{.code-voice} for the `library`{.code-voice} array:







1.  `let`{.code-voice} `library`{.vc} = \[
2.  `    Movie`{.code-voice}(`name`{.vc}: `"Casablanca"`{.s}, `director`{.vc}: `"Michael Curtiz"`{.s}),
3.  `    Song`{.code-voice}(`name`{.vc}: `"Blue Suede Shoes"`{.s}, `artist`{.vc}: `"Elvis Presley"`{.s}),
4.  `    Movie`{.code-voice}(`name`{.vc}: `"Citizen Kane"`{.s}, `director`{.vc}: `"Orson Welles"`{.s}),
5.  `    Song`{.code-voice}(`name`{.vc}: `"The One And Only"`{.s}, `artist`{.vc}: `"Chesney Hawkes"`{.s}),
6.  `    Song`{.code-voice}(`name`{.vc}: `"Never Gonna Give You Up"`{.s}, `artist`{.vc}: `"Rick Astley"`{.s})
7.  `]`{.code-voice}
8.  `// the type of "library" is inferred to be [MediaItem]`{.code-voice}







The items stored in `library`{.code-voice} are still `Movie`{.code-voice} and `Song`{.code-voice} instances behind the scenes. However, if you iterate over the contents of this array, the items you receive back are typed as `MediaItem`{.code-voice}, and not as `Movie`{.code-voice} or `Song`{.code-voice}. In order to work with them as their native type, you need to *check* their type, or *downcast* them to a different type, as described below.





[‌](){#TP40016643-CH22-ID340}
### Checking Type {#checking-type .section-name}

Use the *type check operator* (`is`{.code-voice}) to check whether an instance is of a certain subclass type. The type check operator returns `true`{.code-voice} if the instance is of that subclass type and `false`{.code-voice} if it is not.

The example below defines two variables, `movieCount`{.code-voice} and `songCount`{.code-voice}, which count the number of `Movie`{.code-voice} and `Song`{.code-voice} instances in the `library`{.code-voice} array:







1.  `var`{.code-voice} `movieCount`{.vc} = `0`{.m}
2.  `var`{.code-voice} `songCount`{.vc} = `0`{.m}
3.  ` `{.code-voice}
4.  `for`{.code-voice} `item`{.vc} `in`{.kt} `library`{.vc} {
5.  `    if`{.code-voice} `item`{.vc} `is`{.kt} `Movie`{.n} {
6.  `        ++movieCount`{.code-voice}
7.  `    } else`{.code-voice} `if`{.kt} `item`{.vc} `is`{.kt} `Song`{.n} {
8.  `        ++songCount`{.code-voice}
9.  `    }`{.code-voice}
10. `}`{.code-voice}
11. ` `{.code-voice}
12. `print`{.code-voice}(`"Media library contains `{.s}\\(`movieCount`{.vc})` movies and `{.s}\\(`songCount`{.vc})` songs"`{.s})
13. `// prints "Media library contains 2 movies and 3 songs"`{.code-voice}







This example iterates through all items in the `library`{.code-voice} array. On each pass, the `for`{.code-voice}-`in`{.code-voice} loop sets the `item`{.code-voice} constant to the next `MediaItem`{.code-voice} in the array.

`item is Movie`{.code-voice} returns `true`{.code-voice} if the current `MediaItem`{.code-voice} is a `Movie`{.code-voice} instance and `false`{.code-voice} if it is not. Similarly, `item is Song`{.code-voice} checks whether the item is a `Song`{.code-voice} instance. At the end of the `for`{.code-voice}-`in`{.code-voice} loop, the values of `movieCount`{.code-voice} and `songCount`{.code-voice} contain a count of how many `MediaItem`{.code-voice} instances were found of each type.





[‌](){#TP40016643-CH22-ID341}
### Downcasting {#downcasting .section-name}

A constant or variable of a certain class type may actually refer to an instance of a subclass behind the scenes. Where you believe this is the case, you can try to *downcast* to the subclass type with a *type cast operator* (`as?`{.code-voice} or `as!`{.code-voice}).

Because downcasting can fail, the type cast operator comes in two different forms. The conditional form, `as?`{.code-voice}, returns an optional value of the type you are trying to downcast to. The forced form, `as!`{.code-voice}, attempts the downcast and force-unwraps the result as a single compound action.

Use the conditional form of the type cast operator (`as?`{.code-voice}) when you are not sure if the downcast will succeed. This form of the operator will always return an optional value, and the value will be `nil`{.code-voice} if the downcast was not possible. This enables you to check for a successful downcast.

Use the forced form of the type cast operator (`as!`{.code-voice}) only when you are sure that the downcast will always succeed. This form of the operator will trigger a runtime error if you try to downcast to an incorrect class type.

The example below iterates over each `MediaItem`{.code-voice} in `library`{.code-voice}, and prints an appropriate description for each item. To do this, it needs to access each item as a true `Movie`{.code-voice} or `Song`{.code-voice}, and not just as a `MediaItem`{.code-voice}. This is necessary in order for it to be able to access the `director`{.code-voice} or `artist`{.code-voice} property of a `Movie`{.code-voice} or `Song`{.code-voice} for use in the description.

In this example, each item in the array might be a `Movie`{.code-voice}, or it might be a `Song`{.code-voice}. You don’t know in advance which actual class to use for each item, and so it is appropriate to use the conditional form of the type cast operator (`as?`{.code-voice}) to check the downcast each time through the loop:







1.  `for`{.code-voice} `item`{.vc} `in`{.kt} `library`{.vc} {
2.  `    if`{.code-voice} `let`{.kt} `movie`{.vc} = `item`{.vc} `as`{.kt}? `Movie`{.n} {
3.  `        print`{.code-voice}(`"Movie: '`{.s}\\(`movie`{.vc}.`name`{.vc})`', dir. `{.s}\\(`movie`{.vc}.`director`{.vc})`"`{.s})
4.  `    } else`{.code-voice} `if`{.kt} `let`{.kt} `song`{.vc} = `item`{.vc} `as`{.kt}? `Song`{.n} {
5.  `        print`{.code-voice}(`"Song: '`{.s}\\(`song`{.vc}.`name`{.vc})`', by `{.s}\\(`song`{.vc}.`artist`{.vc})`"`{.s})
6.  `    }`{.code-voice}
7.  `}`{.code-voice}
8.  ` `{.code-voice}
9.  `// Movie: 'Casablanca', dir. Michael Curtiz`{.code-voice}
10. `// Song: 'Blue Suede Shoes', by Elvis Presley`{.code-voice}
11. `// Movie: 'Citizen Kane', dir. Orson Welles`{.code-voice}
12. `// Song: 'The One And Only', by Chesney Hawkes`{.code-voice}
13. `// Song: 'Never Gonna Give You Up', by Rick Astley`{.code-voice}







The example starts by trying to downcast the current `item`{.code-voice} as a `Movie`{.code-voice}. Because `item`{.code-voice} is a `MediaItem`{.code-voice} instance, it’s possible that it *might* be a `Movie`{.code-voice}; equally, it’s also possible that it might be a `Song`{.code-voice}, or even just a base `MediaItem`{.code-voice}. Because of this uncertainty, the `as?`{.code-voice} form of the type cast operator returns an *optional* value when attempting to downcast to a subclass type. The result of `item as? Movie`{.code-voice} is of type `Movie?`{.code-voice}, or “optional `Movie`{.code-voice}”.

Downcasting to `Movie`{.code-voice} fails when applied to the `Song`{.code-voice} instances in the library array. To cope with this, the example above uses optional binding to check whether the optional `Movie`{.code-voice} actually contains a value (that is, to find out whether the downcast succeeded.) This optional binding is written “`if let movie = item as? Movie`{.code-voice}”, which can be read as:

“Try to access `item`{.code-voice} as a `Movie`{.code-voice}. If this is successful, set a new temporary constant called `movie`{.code-voice} to the value stored in the returned optional `Movie`{.code-voice}.”

If the downcasting succeeds, the properties of `movie`{.code-voice} are then used to print a description for that `Movie`{.code-voice} instance, including the name of its `director`{.code-voice}. A similar principle is used to check for `Song`{.code-voice} instances, and to print an appropriate description (including `artist`{.code-voice} name) whenever a `Song`{.code-voice} is found in the library.



Note

Casting does not actually modify the instance or change its values. The underlying instance remains the same; it is simply treated and accessed as an instance of the type to which it has been cast.







[‌](){#TP40016643-CH22-ID342}
### Type Casting for Any and AnyObject {#type-casting-for-any-and-anyobject .section-name}

Swift provides two special type aliases for working with non-specific types:

-   `AnyObject`{.code-voice} can represent an instance of any class type.

-   `Any`{.code-voice} can represent an instance of any type at all, including function types.



Note

Use `Any`{.code-voice} and `AnyObject`{.code-voice} only when you explicitly need the behavior and capabilities they provide. It is always better to be specific about the types you expect to work with in your code.





[‌](){#TP40016643-CH22-ID343}
### AnyObject {#anyobject .section-name}

When working with Cocoa APIs, it is common to receive an array with a type of `[AnyObject]`{.code-voice}, or “an array of values of any object type”. This is because Objective-C does not have explicitly typed arrays. However, you can often be confident about the type of objects contained in such an array just from the information you know about the API that provided the array.

In these situations, you can use the forced version of the type cast operator (`as!`{.code-voice}) to downcast each item in the array to a more specific class type than `AnyObject`{.code-voice}, without the need for optional unwrapping.

The example below defines an array of type `[AnyObject]`{.code-voice} and populates this array with three instances of the `Movie`{.code-voice} class:







1.  `let`{.code-voice} `someObjects`{.vc}: \[`AnyObject`{.n}\] = \[
2.  `    Movie`{.code-voice}(`name`{.vc}: `"2001: A Space Odyssey"`{.s}, `director`{.vc}: `"Stanley Kubrick"`{.s}),
3.  `    Movie`{.code-voice}(`name`{.vc}: `"Moon"`{.s}, `director`{.vc}: `"Duncan Jones"`{.s}),
4.  `    Movie`{.code-voice}(`name`{.vc}: `"Alien"`{.s}, `director`{.vc}: `"Ridley Scott"`{.s})
5.  `]`{.code-voice}







Because this array is known to contain only `Movie`{.code-voice} instances, you can downcast and unwrap directly to a nonoptional `Movie`{.code-voice} with the forced version of the type cast operator (`as!`{.code-voice}):







1.  `for`{.code-voice} `object`{.vc} `in`{.kt} `someObjects`{.vc} {
2.  `    let`{.code-voice} `movie`{.vc} = `object`{.vc} `as`{.kt}! `Movie`{.n}
3.  `    print`{.code-voice}(`"Movie: '`{.s}\\(`movie`{.vc}.`name`{.vc})`', dir. `{.s}\\(`movie`{.vc}.`director`{.vc})`"`{.s})
4.  `}`{.code-voice}
5.  `// Movie: '2001: A Space Odyssey', dir. Stanley Kubrick`{.code-voice}
6.  `// Movie: 'Moon', dir. Duncan Jones`{.code-voice}
7.  `// Movie: 'Alien', dir. Ridley Scott`{.code-voice}







For an even shorter form of this loop, downcast the `someObjects`{.code-voice} array to a type of `[Movie]`{.code-voice} instead of downcasting each item:







1.  `for`{.code-voice} `movie`{.vc} `in`{.kt} `someObjects`{.vc} `as`{.kt}! \[`Movie`{.n}\] {
2.  `    print`{.code-voice}(`"Movie: '`{.s}\\(`movie`{.vc}.`name`{.vc})`', dir. `{.s}\\(`movie`{.vc}.`director`{.vc})`"`{.s})
3.  `}`{.code-voice}
4.  `// Movie: '2001: A Space Odyssey', dir. Stanley Kubrick`{.code-voice}
5.  `// Movie: 'Moon', dir. Duncan Jones`{.code-voice}
6.  `// Movie: 'Alien', dir. Ridley Scott`{.code-voice}











[‌](){#TP40016643-CH22-ID344}
### Any {#any .section-name}

Here’s an example of using `Any`{.code-voice} to work with a mix of different types, including function types and non-class types. The example creates an array called `things`{.code-voice}, which can store values of type `Any`{.code-voice}:







1.  `var`{.code-voice} `things`{.vc} = \[`Any`{.vc}\]()
2.  ` `{.code-voice}
3.  `things`{.code-voice}.`append`{.vc}(`0`{.m})
4.  `things`{.code-voice}.`append`{.vc}(`0.0`{.m})
5.  `things`{.code-voice}.`append`{.vc}(`42`{.m})
6.  `things`{.code-voice}.`append`{.vc}(`3.14159`{.m})
7.  `things`{.code-voice}.`append`{.vc}(`"hello"`{.s})
8.  `things`{.code-voice}.`append`{.vc}((`3.0`{.m}, `5.0`{.m}))
9.  `things`{.code-voice}.`append`{.vc}(`Movie`{.vc}(`name`{.vc}: `"Ghostbusters"`{.s}, `director`{.vc}: `"Ivan Reitman"`{.s}))
10. `things`{.code-voice}.`append`{.vc}({ (`name`{.vc}: `String`{.n}) -&gt; `String`{.n} `in`{.kt} `"Hello, `{.s}\\(`name`{.vc})`"`{.s} })







The `things`{.code-voice} array contains two `Int`{.code-voice} values, two `Double`{.code-voice} values, a `String`{.code-voice} value, a tuple of type `(Double, Double)`{.code-voice}, the movie “Ghostbusters”, and a closure expression that takes a `String`{.code-voice} value and returns another `String`{.code-voice} value.

You can use the `is`{.code-voice} and `as`{.code-voice} operators in a `switch`{.code-voice} statement’s cases to discover the specific type of a constant or variable that is known only to be of type `Any`{.code-voice} or `AnyObject`{.code-voice}. The example below iterates over the items in the `things`{.code-voice} array and queries the type of each item with a `switch`{.code-voice} statement. Several of the `switch`{.code-voice} statement’s cases bind their matched value to a constant of the specified type to enable its value to be printed:







1.  `for`{.code-voice} `thing`{.vc} `in`{.kt} `things`{.vc} {
2.  `    switch`{.code-voice} `thing`{.vc} {
3.  `    case`{.code-voice} `0`{.m} `as`{.kt} `Int`{.n}:
4.  `        print`{.code-voice}(`"zero as an Int"`{.s})
5.  `    case`{.code-voice} `0`{.m} `as`{.kt} `Double`{.n}:
6.  `        print`{.code-voice}(`"zero as a Double"`{.s})
7.  `    case`{.code-voice} `let`{.kt} `someInt`{.vc} `as`{.kt} `Int`{.n}:
8.  `        print`{.code-voice}(`"an integer value of `{.s}\\(`someInt`{.vc})`"`{.s})
9.  `    case`{.code-voice} `let`{.kt} `someDouble`{.vc} `as`{.kt} `Double`{.n} `where`{.kt} `someDouble`{.vc} &gt; `0`{.m}:
10. `        print`{.code-voice}(`"a positive double value of `{.s}\\(`someDouble`{.vc})`"`{.s})
11. `    case`{.code-voice} `is`{.kt} `Double`{.n}:
12. `        print`{.code-voice}(`"some other double value that I don't want to print"`{.s})
13. `    case`{.code-voice} `let`{.kt} `someString`{.vc} `as`{.kt} `String`{.n}:
14. `        print`{.code-voice}(`"a string value of \"`{.s}\\(`someString`{.vc})`\""`{.s})
15. `    case`{.code-voice} `let`{.kt} (`x`{.vc}, `y`{.vc}) `as`{.kt} (`Double`{.n}, `Double`{.n}):
16. `        print`{.code-voice}(`"an (x, y) point at `{.s}\\(`x`{.vc})`, `{.s}\\(`y`{.vc})`"`{.s})
17. `    case`{.code-voice} `let`{.kt} `movie`{.vc} `as`{.kt} `Movie`{.n}:
18. `        print`{.code-voice}(`"a movie called '`{.s}\\(`movie`{.vc}.`name`{.vc})`', dir. `{.s}\\(`movie`{.vc}.`director`{.vc})`"`{.s})
19. `    case`{.code-voice} `let`{.kt} `stringConverter`{.vc} `as`{.kt} `String`{.n} -&gt; `String`{.n}:
20. `        print`{.code-voice}(`stringConverter`{.vc}(`"Michael"`{.s}))
21. `    default`{.code-voice}:
22. `        print`{.code-voice}(`"something else"`{.s})
23. `    }`{.code-voice}
24. `}`{.code-voice}
25. ` `{.code-voice}
26. `// zero as an Int`{.code-voice}
27. `// zero as a Double`{.code-voice}
28. `// an integer value of 42`{.code-voice}
29. `// a positive double value of 3.14159`{.code-voice}
30. `// a string value of "hello"`{.code-voice}
31. `// an (x, y) point at 3.0, 5.0`{.code-voice}
32. `// a movie called 'Ghostbusters', dir. Ivan Reitman`{.code-voice}
33. `// Hello, Michael`{.code-voice}














