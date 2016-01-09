



[‌]()[‌]()
A Swift Tour 
------------



Tradition suggests that the first program in a new language should print the words “Hello, world!” on the screen. In Swift, this can be done in a single line:







1.  `print`(`"Hello, world!"`)







If you have written code in C or Objective-C, this syntax looks familiar to you—in Swift, this line of code is a complete program. You don’t need to import a separate library for functionality like input/output or string handling. Code written at global scope is used as the entry point for the program, so you don’t need a `main()` function. You also don’t need to write semicolons at the end of every statement.

This tour gives you enough information to start writing code in Swift by showing you how to accomplish a variety of programming tasks. Don’t worry if you don’t understand something—everything introduced in this tour is explained in detail in the rest of this book.







Note

On a Mac, download the Playground and double-click the file to open it in Xcode: 







[‌]()
### Simple Values 

Use `let` to make a constant and `var` to make a variable. The value of a constant doesn’t need to be known at compile time, but you must assign it a value exactly once. This means you can use constants to name a value that you determine once but use in many places.







1.  `var` `myVariable` = `42`
2.  `myVariable` = `50`
3.  `let` `myConstant` = `42`







A constant or variable must have the same type as the value you want to assign to it. However, you don’t always have to write the type explicitly. Providing a value when you create a constant or variable lets the compiler infer its type. In the example above, the compiler infers that `myVariable` is an integer because its initial value is an integer.

If the initial value doesn’t provide enough information (or if there is no initial value), specify the type by writing it after the variable, separated by a colon.







1.  `let` `implicitInteger` = `70`
2.  `let` `implicitDouble` = `70.0`
3.  `let` `explicitDouble`: `Double` = `70`









Experiment

Create a constant with an explicit type of `Float` and a value of `4`.



Values are never implicitly converted to another type. If you need to convert a value to a different type, explicitly make an instance of the desired type.







1.  `let` `label` = `"The width is "`
2.  `let` `width` = `94`
3.  `let` `widthLabel` = `label` + `String`(`width`)









Experiment

Try removing the conversion to `String` from the last line. What error do you get?



There’s an even simpler way to include values in strings: Write the value in parentheses, and write a backslash (`\`) before the parentheses. For example:







1.  `let` `apples` = `3`
2.  `let` `oranges` = `5`
3.  `let` `appleSummary` = `"I have `\\(`apples`)` apples."`
4.  `let` `fruitSummary` = `"I have `\\(`apples` + `oranges`)` pieces of fruit."`









Experiment

Use `\()` to include a floating-point calculation in a string and to include someone’s name in a greeting.



Create arrays and dictionaries using brackets (`[]`), and access their elements by writing the index or key in brackets. A comma is allowed after the last element.







1.  `var` `shoppingList` = \[`"catfish"`, `"water"`, `"tulips"`, `"blue paint"`\]
2.  `shoppingList`\[`1`\] = `"bottle of water"`
3.  ` `
4.  `var` `occupations` = \[
5.  `    "Malcolm"`: `"Captain"`,
6.  `    "Kaylee"`: `"Mechanic"`,
7.  `]`
8.  `occupations`\[`"Jayne"`\] = `"Public Relations"`







To create an empty array or dictionary, use the initializer syntax.







1.  `let` `emptyArray` = \[`String`\]()
2.  `let` `emptyDictionary` = \[`String`: `Float`\]()







If type information can be inferred, you can write an empty array as `[]` and an empty dictionary as `[:]`—for example, when you set a new value for a variable or pass an argument to a function.







1.  `shoppingList` = \[\]
2.  `occupations` = \[:\]











[‌]()
### Control Flow 

Use `if` and `switch` to make conditionals, and use `for`-`in`, `for`, `while`, and `repeat`-`while` to make loops. Parentheses around the condition or loop variable are optional. Braces around the body are required.







1.  `let` `individualScores` = \[`75`, `43`, `103`, `87`, `12`\]
2.  `var` `teamScore` = `0`
3.  `for` `score` `in` `individualScores` {
4.  `    if` `score` &gt; `50` {
5.  `        teamScore` += `3`
6.  `    } else` {
7.  `        teamScore` += `1`
8.  `    }`
9.  `}`
10. `print`(`teamScore`)







In an `if` statement, the conditional must be a Boolean expression—this means that code such as `if score { ... }` is an error, not an implicit comparison to zero.

You can use `if` and `let` together to work with values that might be missing. These values are represented as optionals. An optional value either contains a value or contains `nil` to indicate that a value is missing. Write a question mark (`?`) after the type of a value to mark the value as optional.







1.  `var` `optionalString`: `String`? = `"Hello"`
2.  `print`(`optionalString` == `nil`)
3.  ` `
4.  `var` `optionalName`: `String`? = `"John Appleseed"`
5.  `var` `greeting` = `"Hello!"`
6.  `if` `let` `name` = `optionalName` {
7.  `    greeting` = `"Hello, `\\(`name`)`"`
8.  `}`









Experiment

Change `optionalName` to `nil`. What greeting do you get? Add an `else` clause that sets a different greeting if `optionalName` is `nil`.



If the optional value is `nil`, the conditional is `false` and the code in braces is skipped. Otherwise, the optional value is unwrapped and assigned to the constant after `let`, which makes the unwrapped value available inside the block of code.

Another way to handle optional values is to provide a default value using the `??` operator. If the optional value is missing, the default value is used instead.







1.  `let` `nickName`: `String`? = `nil`
2.  `let` `fullName`: `String` = `"John Appleseed"`
3.  `let` `informalGreeting` = `"Hi `\\(`nickName` ?? `fullName`)`"`







Switches support any kind of data and a wide variety of comparison operations—they aren’t limited to integers and tests for equality.







1.  `let` `vegetable` = `"red pepper"`
2.  `switch` `vegetable` {
3.  `case` `"celery"`:
4.  `    print`(`"Add some raisins and make ants on a log."`)
5.  `case` `"cucumber"`, `"watercress"`:
6.  `    print`(`"That would make a good tea sandwich."`)
7.  `case` `let` `x` `where` `x`.`hasSuffix`(`"pepper"`):
8.  `    print`(`"Is it a spicy `\\(`x`)`?"`)
9.  `default`:
10. `    print`(`"Everything tastes good in soup."`)
11. `}`









Experiment

Try removing the default case. What error do you get?



Notice how `let` can be used in a pattern to assign the value that matched that part of a pattern to a constant.

After executing the code inside the switch case that matched, the program exits from the switch statement. Execution doesn’t continue to the next case, so there is no need to explicitly break out of the switch at the end of each case’s code.

You use `for`-`in` to iterate over items in a dictionary by providing a pair of names to use for each key-value pair. Dictionaries are an unordered collection, so their keys and values are iterated over in an arbitrary order.







1.  `let` `interestingNumbers` = \[
2.  `    "Prime"`: \[`2`, `3`, `5`, `7`, `11`, `13`\],
3.  `    "Fibonacci"`: \[`1`, `1`, `2`, `3`, `5`, `8`\],
4.  `    "Square"`: \[`1`, `4`, `9`, `16`, `25`\],
5.  `]`
6.  `var` `largest` = `0`
7.  `for` (`kind`, `numbers`) `in` `interestingNumbers` {
8.  `    for` `number` `in` `numbers` {
9.  `        if` `number` &gt; `largest` {
10. `            largest` = `number`
11. `        }`
12. `    }`
13. `}`
14. `print`(`largest`)









Experiment

Add another variable to keep track of which kind of number was the largest, as well as what that largest number was.



Use `while` to repeat a block of code until a condition changes. The condition of a loop can be at the end instead, ensuring that the loop is run at least once.







1.  `var` `n` = `2`
2.  `while` `n` &lt; `100` {
3.  `    n` = `n` \* `2`
4.  `}`
5.  `print`(`n`)
6.  ` `
7.  `var` `m` = `2`
8.  `repeat` {
9.  `    m` = `m` \* `2`
10. `} while` `m` &lt; `100`
11. `print`(`m`)







You can keep an index in a loop—either by using `..<` to make a range of indexes or by writing an explicit initialization, condition, and increment. These two loops do the same thing:







1.  `var` `firstForLoop` = `0`
2.  `for` `i` `in` `0`..&lt;`4` {
3.  `    firstForLoop` += `i`
4.  `}`
5.  `print`(`firstForLoop`)
6.  ` `
7.  `var` `secondForLoop` = `0`
8.  `for` `var` `i` = `0`; `i` &lt; `4`; ++`i` {
9.  `    secondForLoop` += `i`
10. `}`
11. `print`(`secondForLoop`)







Use `..<` to make a range that omits its upper value, and use `...` to make a range that includes both values.





[‌]()
### Functions and Closures 

Use `func` to declare a function. Call a function by following its name with a list of arguments in parentheses. Use `->` to separate the parameter names and types from the function’s return type.







1.  `func` `greet`(`name`: `String`, `day`: `String`) -&gt; `String` {
2.  `    return` `"Hello `\\(`name`)`, today is `\\(`day`)`."`
3.  `}`
4.  `greet`(`"Bob"`, `day`: `"Tuesday"`)









Experiment

Remove the `day` parameter. Add a parameter to include today’s lunch special in the greeting.



Use a tuple to make a compound value—for example, to return multiple values from a function. The elements of a tuple can be referred to either by name or by number.







1.  `func` `calculateStatistics`(`scores`: \[`Int`\]) -&gt; (`min`: `Int`, `max`: `Int`, `sum`: `Int`) {
2.  `    var` `min` = `scores`\[`0`\]
3.  `    var` `max` = `scores`\[`0`\]
4.  `    var` `sum` = `0`
5.  `    `
6.  `    for` `score` `in` `scores` {
7.  `        if` `score` &gt; `max` {
8.  `            max` = `score`
9.  `        } else` `if` `score` &lt; `min` {
10. `            min` = `score`
11. `        }`
12. `        sum` += `score`
13. `    }`
14. `    `
15. `    return` (`min`, `max`, `sum`)
16. `}`
17. `let` `statistics` = `calculateStatistics`(\[`5`, `3`, `100`, `3`, `9`\])
18. `print`(`statistics`.`sum`)
19. `print`(`statistics`.`2`)







Functions can also take a variable number of arguments, collecting them into an array.







1.  `func` `sumOf`(`numbers`: `Int`...) -&gt; `Int` {
2.  `    var` `sum` = `0`
3.  `    for` `number` `in` `numbers` {
4.  `        sum` += `number`
5.  `    }`
6.  `    return` `sum`
7.  `}`
8.  `sumOf`()
9.  `sumOf`(`42`, `597`, `12`)









Experiment

Write a function that calculates the average of its arguments.



Functions can be nested. Nested functions have access to variables that were declared in the outer function. You can use nested functions to organize the code in a function that is long or complex.







1.  `func` `returnFifteen`() -&gt; `Int` {
2.  `    var` `y` = `10`
3.  `    func` `add`() {
4.  `        y` += `5`
5.  `    }`
6.  `    add`()
7.  `    return` `y`
8.  `}`
9.  `returnFifteen`()







Functions are a first-class type. This means that a function can return another function as its value.







1.  `func` `makeIncrementer`() -&gt; ((`Int`) -&gt; `Int`) {
2.  `    func` `addOne`(`number`: `Int`) -&gt; `Int` {
3.  `        return` `1` + `number`
4.  `    }`
5.  `    return` `addOne`
6.  `}`
7.  `var` `increment` = `makeIncrementer`()
8.  `increment`(`7`)







A function can take another function as one of its arguments.







1.  `func` `hasAnyMatches`(`list`: \[`Int`\], `condition`: (`Int`) -&gt; `Bool`) -&gt; `Bool` {
2.  `    for` `item` `in` `list` {
3.  `        if` `condition`(`item`) {
4.  `            return` `true`
5.  `        }`
6.  `    }`
7.  `    return` `false`
8.  `}`
9.  `func` `lessThanTen`(`number`: `Int`) -&gt; `Bool` {
10. `    return` `number` &lt; `10`
11. `}`
12. `var` `numbers` = \[`20`, `19`, `7`, `12`\]
13. `hasAnyMatches`(`numbers`, `condition`: `lessThanTen`)







Functions are actually a special case of closures: blocks of code that can be called later. The code in a closure has access to things like variables and functions that were available in the scope where the closure was created, even if the closure is in a different scope when it is executed—you saw an example of this already with nested functions. You can write a closure without a name by surrounding code with braces (`{}`). Use `in` to separate the arguments and return type from the body.







1.  `numbers`.`map`({
2.  `    (number`: `Int`) -&gt; `Int` `in`
3.  `    let` `result` = `3` \* `number`
4.  `    return` `result`
5.  `})`









Experiment

Rewrite the closure to return zero for all odd numbers.



You have several options for writing closures more concisely. When a closure’s type is already known, such as the callback for a delegate, you can omit the type of its parameters, its return type, or both. Single statement closures implicitly return the value of their only statement.







1.  `let` `mappedNumbers` = `numbers`.`map`({ `number` `in` `3` \* `number` })
2.  `print`(`mappedNumbers`)







You can refer to parameters by number instead of by name—this approach is especially useful in very short closures. A closure passed as the last argument to a function can appear immediately after the parentheses. When a closure is the only argument to a function, you can omit the parentheses entirely.







1.  `let` `sortedNumbers` = `numbers`.`sort` { `$0` &gt; `$1` }
2.  `print`(`sortedNumbers`)











[‌]()
### Objects and Classes 

Use `class` followed by the class’s name to create a class. A property declaration in a class is written the same way as a constant or variable declaration, except that it is in the context of a class. Likewise, method and function declarations are written the same way.







1.  `class` `Shape` {
2.  `    var` `numberOfSides` = `0`
3.  `    func` `simpleDescription`() -&gt; `String` {
4.  `        return` `"A shape with `\\(`numberOfSides`)` sides."`
5.  `    }`
6.  `}`









Experiment

Add a constant property with `let`, and add another method that takes an argument.



Create an instance of a class by putting parentheses after the class name. Use dot syntax to access the properties and methods of the instance.







1.  `var` `shape` = `Shape`()
2.  `shape`.`numberOfSides` = `7`
3.  `var` `shapeDescription` = `shape`.`simpleDescription`()







This version of the `Shape` class is missing something important: an initializer to set up the class when an instance is created. Use `init` to create one.







1.  `class` `NamedShape` {
2.  `    var` `numberOfSides`: `Int` = `0`
3.  `    var` `name`: `String`
4.  `    `
5.  `    init`(`name`: `String`) {
6.  `        self`.`name` = `name`
7.  `    }`
8.  `    `
9.  `    func` `simpleDescription`() -&gt; `String` {
10. `        return` `"A shape with `\\(`numberOfSides`)` sides."`
11. `    }`
12. `}`







Notice how `self` is used to distinguish the `name` property from the `name` argument to the initializer. The arguments to the initializer are passed like a function call when you create an instance of the class. Every property needs a value assigned—either in its declaration (as with `numberOfSides`) or in the initializer (as with `name`).

Use `deinit` to create a deinitializer if you need to perform some cleanup before the object is deallocated.

Subclasses include their superclass name after their class name, separated by a colon. There is no requirement for classes to subclass any standard root class, so you can include or omit a superclass as needed.

Methods on a subclass that override the superclass’s implementation are marked with `override`—overriding a method by accident, without `override`, is detected by the compiler as an error. The compiler also detects methods with `override` that don’t actually override any method in the superclass.







1.  `class` `Square`: `NamedShape` {
2.  `    var` `sideLength`: `Double`
3.  `    `
4.  `    init`(`sideLength`: `Double`, `name`: `String`) {
5.  `        self`.`sideLength` = `sideLength`
6.  `        super`.`init`(`name`: `name`)
7.  `        numberOfSides` = `4`
8.  `    }`
9.  `    `
10. `    func` `area`() -&gt; `Double` {
11. `        return` `sideLength` \* `sideLength`
12. `    }`
13. `    `
14. `    override` `func` `simpleDescription`() -&gt; `String` {
15. `        return` `"A square with sides of length `\\(`sideLength`)`."`
16. `    }`
17. `}`
18. `let` `test` = `Square`(`sideLength`: `5.2`, `name`: `"my test square"`)
19. `test`.`area`()
20. `test`.`simpleDescription`()









Experiment

Make another subclass of `NamedShape` called `Circle` that takes a radius and a name as arguments to its initializer. Implement an `area()` and a `simpleDescription()` method on the `Circle` class.



In addition to simple properties that are stored, properties can have a getter and a setter.







1.  `class` `EquilateralTriangle`: `NamedShape` {
2.  `    var` `sideLength`: `Double` = `0.0`
3.  `    `
4.  `    init`(`sideLength`: `Double`, `name`: `String`) {
5.  `        self`.`sideLength` = `sideLength`
6.  `        super`.`init`(`name`: `name`)
7.  `        numberOfSides` = `3`
8.  `    }`
9.  `    `
10. `    var` `perimeter`: `Double` {
11. `        get` {
12. `            return` `3.0` \* `sideLength`
13. `        }`
14. `        set` {
15. `            sideLength` = `newValue` / `3.0`
16. `        }`
17. `    }`
18. `    `
19. `    override` `func` `simpleDescription`() -&gt; `String` {
20. `        return` `"An equilateral triangle with sides of length `\\(`sideLength`)`."`
21. `    }`
22. `}`
23. `var` `triangle` = `EquilateralTriangle`(`sideLength`: `3.1`, `name`: `"a triangle"`)
24. `print`(`triangle`.`perimeter`)
25. `triangle`.`perimeter` = `9.9`
26. `print`(`triangle`.`sideLength`)







In the setter for `perimeter`, the new value has the implicit name `newValue`. You can provide an explicit name in parentheses after `set`.

Notice that the initializer for the `EquilateralTriangle` class has three different steps:

1.  Setting the value of properties that the subclass declares.

2.  Calling the superclass’s initializer.

3.  Changing the value of properties defined by the superclass. Any additional setup work that uses methods, getters, or setters can also be done at this point.

If you don’t need to compute the property but still need to provide code that is run before and after setting a new value, use `willSet` and `didSet`. The code you provide is run any time the value changes outside of an initializer. For example, the class below ensures that the side length of its triangle is always the same as the side length of its square.







1.  `class` `TriangleAndSquare` {
2.  `    var` `triangle`: `EquilateralTriangle` {
3.  `        willSet` {
4.  `            square`.`sideLength` = `newValue`.`sideLength`
5.  `        }`
6.  `    }`
7.  `    var` `square`: `Square` {
8.  `        willSet` {
9.  `            triangle`.`sideLength` = `newValue`.`sideLength`
10. `        }`
11. `    }`
12. `    init`(`size`: `Double`, `name`: `String`) {
13. `        square` = `Square`(`sideLength`: `size`, `name`: `name`)
14. `        triangle` = `EquilateralTriangle`(`sideLength`: `size`, `name`: `name`)
15. `    }`
16. `}`
17. `var` `triangleAndSquare` = `TriangleAndSquare`(`size`: `10`, `name`: `"another test shape"`)
18. `print`(`triangleAndSquare`.`square`.`sideLength`)
19. `print`(`triangleAndSquare`.`triangle`.`sideLength`)
20. `triangleAndSquare`.`square` = `Square`(`sideLength`: `50`, `name`: `"larger square"`)
21. `print`(`triangleAndSquare`.`triangle`.`sideLength`)







When working with optional values, you can write `?` before operations like methods, properties, and subscripting. If the value before the `?` is `nil`, everything after the `?` is ignored and the value of the whole expression is `nil`. Otherwise, the optional value is unwrapped, and everything after the `?` acts on the unwrapped value. In both cases, the value of the whole expression is an optional value.







1.  `let` `optionalSquare`: `Square`? = `Square`(`sideLength`: `2.5`, `name`: `"optional square"`)
2.  `let` `sideLength` = `optionalSquare`?.`sideLength`











[‌]()
### Enumerations and Structures 

Use `enum` to create an enumeration. Like classes and all other named types, enumerations can have methods associated with them.







1.  `enum` `Rank`: `Int` {
2.  `    case` `Ace` = `1`
3.  `    case` `Two`, `Three`, `Four`, `Five`, `Six`, `Seven`, `Eight`, `Nine`, `Ten`
4.  `    case` `Jack`, `Queen`, `King`
5.  `    func` `simpleDescription`() -&gt; `String` {
6.  `        switch` `self` {
7.  `        case` .`Ace`:
8.  `            return` `"ace"`
9.  `        case` .`Jack`:
10. `            return` `"jack"`
11. `        case` .`Queen`:
12. `            return` `"queen"`
13. `        case` .`King`:
14. `            return` `"king"`
15. `        default`:
16. `            return` `String`(`self`.`rawValue`)
17. `        }`
18. `    }`
19. `}`
20. `let` `ace` = `Rank`.`Ace`
21. `let` `aceRawValue` = `ace`.`rawValue`









Experiment

Write a function that compares two `Rank` values by comparing their raw values.



In the example above, the raw-value type of the enumeration is `Int`, so you only have to specify the first raw value. The rest of the raw values are assigned in order. You can also use strings or floating-point numbers as the raw type of an enumeration. Use the `rawValue` property to access the raw value of an enumeration case.

Use the `init?(rawValue:)` initializer to make an instance of an enumeration from a raw value.







1.  `if` `let` `convertedRank` = `Rank`(`rawValue`: `3`) {
2.  `    let` `threeDescription` = `convertedRank`.`simpleDescription`()
3.  `}`







The case values of an enumeration are actual values, not just another way of writing their raw values. In fact, in cases where there isn’t a meaningful raw value, you don’t have to provide one.







1.  `enum` `Suit` {
2.  `    case` `Spades`, `Hearts`, `Diamonds`, `Clubs`
3.  `    func` `simpleDescription`() -&gt; `String` {
4.  `        switch` `self` {
5.  `        case` .`Spades`:
6.  `            return` `"spades"`
7.  `        case` .`Hearts`:
8.  `            return` `"hearts"`
9.  `        case` .`Diamonds`:
10. `            return` `"diamonds"`
11. `        case` .`Clubs`:
12. `            return` `"clubs"`
13. `        }`
14. `    }`
15. `}`
16. `let` `hearts` = `Suit`.`Hearts`
17. `let` `heartsDescription` = `hearts`.`simpleDescription`()









Experiment

Add a `color()` method to `Suit` that returns “black” for spades and clubs, and returns “red” for hearts and diamonds.



Notice the two ways that the `Hearts` case of the enumeration is referred to above: When assigning a value to the `hearts` constant, the enumeration case `Suit.Hearts` is referred to by its full name because the constant doesn’t have an explicit type specified. Inside the switch, the enumeration case is referred to by the abbreviated form `.Hearts` because the value of `self` is already known to be a suit. You can use the abbreviated form anytime the value’s type is already known.

Use `struct` to create a structure. Structures support many of the same behaviors as classes, including methods and initializers. One of the most important differences between structures and classes is that structures are always copied when they are passed around in your code, but classes are passed by reference.







1.  `struct` `Card` {
2.  `    var` `rank`: `Rank`
3.  `    var` `suit`: `Suit`
4.  `    func` `simpleDescription`() -&gt; `String` {
5.  `        return` `"The `\\(`rank`.`simpleDescription`())` of `\\(`suit`.`simpleDescription`())`"`
6.  `    }`
7.  `}`
8.  `let` `threeOfSpades` = `Card`(`rank`: .`Three`, `suit`: .`Spades`)
9.  `let` `threeOfSpadesDescription` = `threeOfSpades`.`simpleDescription`()









Experiment

Add a method to `Card` that creates a full deck of cards, with one card of each combination of rank and suit.



An instance of an enumeration case can have values associated with the instance. Instances of the same enumeration case can have different values associated with them. You provide the associated values when you create the instance. Associated values and raw values are different: The raw value of an enumeration case is the same for all of its instances, and you provide the raw value when you define the enumeration.

For example, consider the case of requesting the sunrise and sunset time from a server. The server either responds with the information or it responds with some error information.







1.  `enum` `ServerResponse` {
2.  `    case` `Result`(`String`, `String`)
3.  `    case` `Error`(`String`)
4.  `}`
5.  ` `
6.  `let` `success` = `ServerResponse`.`Result`(`"6:00 am"`, `"8:09 pm"`)
7.  `let` `failure` = `ServerResponse`.`Error`(`"Out of cheese."`)
8.  ` `
9.  `switch` `success` {
10. `case` `let` .`Result`(`sunrise`, `sunset`):
11. `    print`(`"Sunrise is at `\\(`sunrise`)` and sunset is at `\\(`sunset`)`."`)
12. `case` `let` .`Error`(`error`):
13. `    print`(`"Failure...  `\\(`error`)`"`)
14. `}`









Experiment

Add a third case to `ServerResponse` and to the switch.



Notice how the sunrise and sunset times are extracted from the `ServerResponse` value as part of matching the value against the switch cases.





[‌]()
### Protocols and Extensions 

Use `protocol` to declare a protocol.







1.  `protocol` `ExampleProtocol` {
2.  `    var` `simpleDescription`: `String` { `get` }
3.  `    mutating` `func` `adjust`()
4.  `}`







Classes, enumerations, and structs can all adopt protocols.







1.  `class` `SimpleClass`: `ExampleProtocol` {
2.  `    var` `simpleDescription`: `String` = `"A very simple class."`
3.  `    var` `anotherProperty`: `Int` = `69105`
4.  `    func` `adjust`() {
5.  `        simpleDescription` += `"  Now 100% adjusted."`
6.  `    }`
7.  `}`
8.  `var` `a` = `SimpleClass`()
9.  `a`.`adjust`()
10. `let` `aDescription` = `a`.`simpleDescription`
11. ` `
12. `struct` `SimpleStructure`: `ExampleProtocol` {
13. `    var` `simpleDescription`: `String` = `"A simple structure"`
14. `    mutating` `func` `adjust`() {
15. `        simpleDescription` += `" (adjusted)"`
16. `    }`
17. `}`
18. `var` `b` = `SimpleStructure`()
19. `b`.`adjust`()
20. `let` `bDescription` = `b`.`simpleDescription`









Experiment

Write an enumeration that conforms to this protocol.



Notice the use of the `mutating` keyword in the declaration of `SimpleStructure` to mark a method that modifies the structure. The declaration of `SimpleClass` doesn’t need any of its methods marked as mutating because methods on a class can always modify the class.

Use `extension` to add functionality to an existing type, such as new methods and computed properties. You can use an extension to add protocol conformance to a type that is declared elsewhere, or even to a type that you imported from a library or framework.







1.  `extension` `Int`: `ExampleProtocol` {
2.  `    var` `simpleDescription`: `String` {
3.  `        return` `"The number `\\(`self`)`"`
4.  `    }`
5.  `    mutating` `func` `adjust`() {
6.  `        self` += `42`
7.  `    }`
8.  `}`
9.  `print`(`7`.`simpleDescription`)









Experiment

Write an extension for the `Double` type that adds an `absoluteValue` property.



You can use a protocol name just like any other named type—for example, to create a collection of objects that have different types but that all conform to a single protocol. When you work with values whose type is a protocol type, methods outside the protocol definition are not available.







1.  `let` `protocolValue`: `ExampleProtocol` = `a`
2.  `print`(`protocolValue`.`simpleDescription`)
3.  `// print(protocolValue.anotherProperty)  // Uncomment to see the error`







Even though the variable `protocolValue` has a runtime type of `SimpleClass`, the compiler treats it as the given type of `ExampleProtocol`. This means that you can’t accidentally access methods or properties that the class implements in addition to its protocol conformance.





[‌]()
### Generics 

Write a name inside angle brackets to make a generic function or type.







1.  `func` `repeatItem`&lt;`Item`&gt;(`item`: `Item`, `numberOfTimes`: `Int`) -&gt; \[`Item`\] {
2.  `    var` `result` = \[`Item`\]()
3.  `    for` `_` `in` `0`..&lt;`numberOfTimes` {
4.  `        result`.`append`(`item`)
5.  `    }`
6.  `    return` `result`
7.  `}`
8.  `repeatItem`(`"knock"`, `numberOfTimes`:`4`)







You can make generic forms of functions and methods, as well as classes, enumerations, and structures.







1.  `// Reimplement the Swift standard library's optional type`
2.  `enum` `OptionalValue`&lt;`Wrapped`&gt; {
3.  `    case` `None`
4.  `    case` `Some`(`Wrapped`)
5.  `}`
6.  `var` `possibleInteger`: `OptionalValue`&lt;`Int`&gt; = .`None`
7.  `possibleInteger` = .`Some`(`100`)







Use `where` after the type name to specify a list of requirements—for example, to require the type to implement a protocol, to require two types to be the same, or to require a class to have a particular superclass.







1.  `func` `anyCommonElements` &lt;`T`: `SequenceType`, `U`: `SequenceType` `where` `T`.`Generator`.`Element`: `Equatable`, `T`.`Generator`.`Element` == `U`.`Generator`.`Element`&gt; (`lhs`: `T`, `_` `rhs`: `U`) -&gt; `Bool` {
2.  `    for` `lhsItem` `in` `lhs` {
3.  `        for` `rhsItem` `in` `rhs` {
4.  `            if` `lhsItem` == `rhsItem` {
5.  `                return` `true`
6.  `            }`
7.  `        }`
8.  `    }`
9.  `    return` `false`
10. `}`
11. `anyCommonElements`(\[`1`, `2`, `3`\], \[`3`\])









Experiment

Modify the `anyCommonElements(_:_:)` function to make a function that returns an array of the elements that any two sequences have in common.



Writing `` is the same as writing ``.






