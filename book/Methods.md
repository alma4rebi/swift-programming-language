<div class="content-wrapper">

<div id="chapter_container" class="conceptualwithtasks">

[‌](){#TP40016643-CH15}[‌](){#TP40016643-CH15-ID234}
Methods {#methods .chapter-name}
-------

<div class="section section">

*Methods* are functions that are associated with a particular type.
Classes, structures, and enumerations can all define instance methods,
which encapsulate specific tasks and functionality for working with an
instance of a given type. Classes, structures, and enumerations can also
define type methods, which are associated with the type itself. Type
methods are similar to class methods in Objective-C.

The fact that structures and enumerations can define methods in Swift is
a major difference from C and Objective-C. In Objective-C, classes are
the only types that can define methods. In Swift, you can choose whether
to define a class, structure, or enumeration, and still have the
flexibility to define methods on the type you create.

</div>

<div class="section section">

[‌](){#TP40016643-CH15-ID235}
### Instance Methods {#instance-methods .section-name}

*Instance methods* are functions that belong to instances of a
particular class, structure, or enumeration. They support the
functionality of those instances, either by providing ways to access and
modify instance properties, or by providing functionality related to the
instance’s purpose. Instance methods have exactly the same syntax as
functions, as described in [Functions](Functions.md).

You write an instance method within the opening and closing braces of
the type it belongs to. An instance method has implicit access to all
other instance methods and properties of that type. An instance method
can be called only on a specific instance of the type it belongs to. It
cannot be called in isolation without an existing instance.

Here’s an example that defines a simple `Counter`{.code-voice} class,
which can be used to count the number of times an action occurs:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `class`{.code-voice} `Counter`{.vc} {
2.  `    var`{.code-voice} `count`{.vc} = `0`{.m}
3.  `    func`{.code-voice} `increment`{.vc}() {
4.  `        ++count`{.code-voice}
5.  `    }`{.code-voice}
6.  `    func`{.code-voice} `incrementBy`{.vc}(`amount`{.vc}: `Int`{.n})
    {
7.  `        count`{.code-voice} += `amount`{.vc}
8.  `    }`{.code-voice}
9.  `    func`{.code-voice} `reset`{.vc}() {
10. `        count`{.code-voice} = `0`{.m}
11. `    }`{.code-voice}
12. `}`{.code-voice}

</div>

</div>

</div>

The `Counter`{.code-voice} class defines three instance methods:

-   `increment`{.code-voice} increments the counter by `1`{.code-voice}.

-   `incrementBy(amount: Int)`{.code-voice} increments the counter by a
    specified integer amount.

-   `reset`{.code-voice} resets the counter to zero.

The `Counter`{.code-voice} class also declares a variable property,
`count`{.code-voice}, to keep track of the current counter value.

You call instance methods with the same dot syntax as properties:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `counter`{.vc} = `Counter`{.vc}()
2.  `// the initial counter value is 0`{.code-voice}
3.  `counter`{.code-voice}.`increment`{.vc}()
4.  `// the counter's value is now 1`{.code-voice}
5.  `counter`{.code-voice}.`incrementBy`{.vc}(`5`{.m})
6.  `// the counter's value is now 6`{.code-voice}
7.  `counter`{.code-voice}.`reset`{.vc}()
8.  `// the counter's value is now 0`{.code-voice}

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH15-ID236}
### Local and External Parameter Names for Methods {#local-and-external-parameter-names-for-methods .section-name}

Function parameters can have both a local name (for use within the
function’s body) and an external name (for use when calling the
function), as described in [Specifying External Parameter
Names](Functions.md#TP40016643-CH10-ID167). The same is true for
method parameters, because methods are just functions that are
associated with a type.

Methods in Swift are very similar to their counterparts in Objective-C.
As in Objective-C, the name of a method in Swift typically refers to the
method’s first parameter using a preposition such as
`with`{.code-voice}, `for`{.code-voice}, or `by`{.code-voice}, as seen
in the `incrementBy(_:)`{.code-voice} method from the preceding
`Counter`{.code-voice} class example. The use of a preposition enables
the method to be read as a sentence when it is called.

Swift gives the *first* parameter name in a method a local parameter
name by default, and gives the second and subsequent parameter names
both local *and* external parameter names by default. This convention
matches the typical naming and calling convention you will be familiar
with from writing Objective-C methods, and makes for expressive method
calls without the need to qualify your parameter names.

Consider this alternative version of the `Counter`{.code-voice} class,
which defines a more complex form of the `incrementBy(_:)`{.code-voice}
method:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `class`{.code-voice} `Counter`{.vc} {
2.  `    var`{.code-voice} `count`{.vc}: `Int`{.n} = `0`{.m}
3.  `    func`{.code-voice} `incrementBy`{.vc}(`amount`{.vc}: `Int`{.n},
    `numberOfTimes`{.vc}: `Int`{.n}) {
4.  `        count`{.code-voice} += `amount`{.vc} \*
    `numberOfTimes`{.vc}
5.  `    }`{.code-voice}
6.  `}`{.code-voice}

</div>

</div>

</div>

This `incrementBy(_:numberOfTimes:)`{.code-voice} method has two
parameters—`amount`{.code-voice} and `numberOfTimes`{.code-voice}. By
default, Swift treats `amount`{.code-voice} as a local name only, but
treats `numberOfTimes`{.code-voice} as both a local *and* an external
name. You call the method as follows:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `counter`{.vc} = `Counter`{.vc}()
2.  `counter`{.code-voice}.`incrementBy`{.vc}(`5`{.m},
    `numberOfTimes`{.vc}: `3`{.m})
3.  `// counter value is now 15`{.code-voice}

</div>

</div>

</div>

You don’t need to define an external parameter name for the first
argument value, because its purpose is clear from the function name
`incrementBy(_:numberOfTimes:)`{.code-voice}. The second argument,
however, is qualified by an external parameter name to make its purpose
clear when the method is called.

The behavior described above means that method definitions in Swift are
written with the same grammatical style as Objective-C, and are called
in a natural, expressive way.

</div>

<div class="section section">

[‌](){#TP40016643-CH15-ID237}
### Modifying External Parameter Name Behavior for Methods {#modifying-external-parameter-name-behavior-for-methods .section-name}

Sometimes it’s useful to provide an external parameter name for a
method’s first parameter, even though this is not the default behavior.
To do so, you can add an explicit external name yourself.

Conversely, if you do not want to provide an external name for the
second or subsequent parameter of a method, override the default
behavior by using an underscore character (`_`{.code-voice}) as an
explicit external parameter name for that parameter.

</div>

<div class="section section">

[‌](){#TP40016643-CH15-ID238}
### The self Property {#the-self-property .section-name}

Every instance of a type has an implicit property called
`self`{.code-voice}, which is exactly equivalent to the instance itself.
You use the `self`{.code-voice} property to refer to the current
instance within its own instance methods.

The `increment()`{.code-voice} method in the example above could have
been written like this:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `increment`{.vc}() {
2.  `    self`{.code-voice}.`count`{.vc}++
3.  `}`{.code-voice}

</div>

</div>

</div>

In practice, you don’t need to write `self`{.code-voice} in your code
very often. If you don’t explicitly write `self`{.code-voice}, Swift
assumes that you are referring to a property or method of the current
instance whenever you use a known property or method name within a
method. This assumption is demonstrated by the use of
`count`{.code-voice} (rather than `self.count`{.code-voice}) inside the
three instance methods for `Counter`{.code-voice}.

The main exception to this rule occurs when a parameter name for an
instance method has the same name as a property of that instance. In
this situation, the parameter name takes precedence, and it becomes
necessary to refer to the property in a more qualified way. You use the
`self`{.code-voice} property to distinguish between the parameter name
and the property name.

Here, `self`{.code-voice} disambiguates between a method parameter
called `x`{.code-voice} and an instance property that is also called
`x`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `struct`{.code-voice} `Point`{.vc} {
2.  `    var`{.code-voice} `x`{.vc} = `0.0`{.m}, `y`{.vc} = `0.0`{.m}
3.  `    func`{.code-voice} `isToTheRightOfX`{.vc}(`x`{.vc}:
    `Double`{.n}) -&gt; `Bool`{.n} {
4.  `        return`{.code-voice} `self`{.kt}.`x`{.vc} &gt; `x`{.vc}
5.  `    }`{.code-voice}
6.  `}`{.code-voice}
7.  `let`{.code-voice} `somePoint`{.vc} = `Point`{.vc}(`x`{.vc}:
    `4.0`{.m}, `y`{.vc}: `5.0`{.m})
8.  `if`{.code-voice} `somePoint`{.vc}.`isToTheRightOfX`{.vc}(`1.0`{.m})
    {
9.  `    print`{.code-voice}(`"This point is to the right of the line where x == 1.0"`{.s})
10. `}`{.code-voice}
11. `// prints "This point is to the right of the line where x == 1.0"`{.code-voice}

</div>

</div>

</div>

Without the `self`{.code-voice} prefix, Swift would assume that both
uses of `x`{.code-voice} referred to the method parameter called
`x`{.code-voice}.

</div>

<div class="section section">

[‌](){#TP40016643-CH15-ID239}
### Modifying Value Types from Within Instance Methods {#modifying-value-types-from-within-instance-methods .section-name}

Structures and enumerations are *value types*. By default, the
properties of a value type cannot be modified from within its instance
methods.

However, if you need to modify the properties of your structure or
enumeration within a particular method, you can opt in to *mutating*
behavior for that method. The method can then mutate (that is, change)
its properties from within the method, and any changes that it makes are
written back to the original structure when the method ends. The method
can also assign a completely new instance to its implicit
`self`{.code-voice} property, and this new instance will replace the
existing one when the method ends.

You can opt in to this behavior by placing the `mutating`{.code-voice}
keyword before the `func`{.code-voice} keyword for that method:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `struct`{.code-voice} `Point`{.vc} {
2.  `    var`{.code-voice} `x`{.vc} = `0.0`{.m}, `y`{.vc} = `0.0`{.m}
3.  `    mutating`{.code-voice} `func`{.kt}
    `moveByX`{.vc}(`deltaX`{.vc}: `Double`{.n}, `y`{.vc} `deltaY`{.vc}:
    `Double`{.n}) {
4.  `        x`{.code-voice} += `deltaX`{.vc}
5.  `        y`{.code-voice} += `deltaY`{.vc}
6.  `    }`{.code-voice}
7.  `}`{.code-voice}
8.  `var`{.code-voice} `somePoint`{.vc} = `Point`{.vc}(`x`{.vc}:
    `1.0`{.m}, `y`{.vc}: `1.0`{.m})
9.  `somePoint`{.code-voice}.`moveByX`{.vc}(`2.0`{.m}, `y`{.vc}:
    `3.0`{.m})
10. `print`{.code-voice}(`"The point is now at (`{.s}\\(`somePoint`{.vc}.`x`{.vc})`, `{.s}\\(`somePoint`{.vc}.`y`{.vc})`)"`{.s})
11. `// prints "The point is now at (3.0, 4.0)"`{.code-voice}

</div>

</div>

</div>

The `Point`{.code-voice} structure above defines a mutating
`moveByX(_:y:)`{.code-voice} method, which moves a `Point`{.code-voice}
instance by a certain amount. Instead of returning a new point, this
method actually modifies the point on which it is called. The
`mutating`{.code-voice} keyword is added to its definition to enable it
to modify its properties.

Note that you cannot call a mutating method on a constant of structure
type, because its properties cannot be changed, even if they are
variable properties, as described in [Stored Properties of Constant
Structure Instances](Properties.md#TP40016643-CH14-ID256):

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `fixedPoint`{.vc} = `Point`{.vc}(`x`{.vc}:
    `3.0`{.m}, `y`{.vc}: `3.0`{.m})
2.  `fixedPoint`{.code-voice}.`moveByX`{.vc}(`2.0`{.m}, `y`{.vc}:
    `3.0`{.m})
3.  `// this will report an error`{.code-voice}

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH15-ID240}
### Assigning to self Within a Mutating Method {#assigning-to-self-within-a-mutating-method .section-name}

Mutating methods can assign an entirely new instance to the implicit
`self`{.code-voice} property. The `Point`{.code-voice} example shown
above could have been written in the following way instead:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `struct`{.code-voice} `Point`{.vc} {
2.  `    var`{.code-voice} `x`{.vc} = `0.0`{.m}, `y`{.vc} = `0.0`{.m}
3.  `    mutating`{.code-voice} `func`{.kt}
    `moveByX`{.vc}(`deltaX`{.vc}: `Double`{.n}, `y`{.vc} `deltaY`{.vc}:
    `Double`{.n}) {
4.  `        self`{.code-voice} = `Point`{.vc}(`x`{.vc}: `x`{.vc} +
    `deltaX`{.vc}, `y`{.vc}: `y`{.vc} + `deltaY`{.vc})
5.  `    }`{.code-voice}
6.  `}`{.code-voice}

</div>

</div>

</div>

This version of the mutating `moveByX(_:y:)`{.code-voice} method creates
a brand new structure whose `x`{.code-voice} and `y`{.code-voice} values
are set to the target location. The end result of calling this
alternative version of the method will be exactly the same as for
calling the earlier version.

Mutating methods for enumerations can set the implicit
`self`{.code-voice} parameter to be a different case from the same
enumeration:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `enum`{.code-voice} `TriStateSwitch`{.vc} {
2.  `    case`{.code-voice} `Off`{.vc}, `Low`{.vc}, `High`{.vc}
3.  `    mutating`{.code-voice} `func`{.kt} `next`{.vc}() {
4.  `        switch`{.code-voice} `self`{.kt} {
5.  `        case`{.code-voice} `Off`{.vc}:
6.  `            self`{.code-voice} = `Low`{.vc}
7.  `        case`{.code-voice} `Low`{.vc}:
8.  `            self`{.code-voice} = `High`{.vc}
9.  `        case`{.code-voice} `High`{.vc}:
10. `            self`{.code-voice} = `Off`{.vc}
11. `        }`{.code-voice}
12. `    }`{.code-voice}
13. `}`{.code-voice}
14. `var`{.code-voice} `ovenLight`{.vc} =
    `TriStateSwitch`{.vc}.`Low`{.vc}
15. `ovenLight`{.code-voice}.`next`{.vc}()
16. `// ovenLight is now equal to .High`{.code-voice}
17. `ovenLight`{.code-voice}.`next`{.vc}()
18. `// ovenLight is now equal to .Off`{.code-voice}

</div>

</div>

</div>

This example defines an enumeration for a three-state switch. The switch
cycles between three different power states (`Off`{.code-voice},
`Low`{.code-voice} and `High`{.code-voice}) every time its
`next()`{.code-voice} method is called.

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH15-ID241}
### Type Methods {#type-methods .section-name}

Instance methods, as described above, are methods that are called on an
instance of a particular type. You can also define methods that are
called on the type itself. These kinds of methods are called *type
methods*. You indicate type methods by writing the `static`{.code-voice}
keyword before the method’s `func`{.code-voice} keyword. Classes may
also use the `class`{.code-voice} keyword to allow subclasses to
override the superclass’s implementation of that method.

<div class="note">

Note

In Objective-C, you can define type-level methods only for Objective-C
classes. In Swift, you can define type-level methods for all classes,
structures, and enumerations. Each type method is explicitly scoped to
the type it supports.

</div>

Type methods are called with dot syntax, like instance methods. However,
you call type methods on the type, not on an instance of that type.
Here’s how you call a type method on a class called
`SomeClass`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `class`{.code-voice} `SomeClass`{.vc} {
2.  `    class`{.code-voice} `func`{.kt} `someTypeMethod`{.vc}() {
3.  `        // type method implementation goes here`{.code-voice}
4.  `    }`{.code-voice}
5.  `}`{.code-voice}
6.  `SomeClass`{.code-voice}.`someTypeMethod`{.vc}()

</div>

</div>

</div>

Within the body of a type method, the implicit `self`{.code-voice}
property refers to the type itself, rather than an instance of that
type. For structures and enumerations, this means that you can use
`self`{.code-voice} to disambiguate between type properties and type
method parameters, just as you do for instance properties and instance
method parameters.

More generally, any unqualified method and property names that you use
within the body of a type method will refer to other type-level methods
and properties. A type method can call another type method with the
other method’s name, without needing to prefix it with the type name.
Similarly, type methods on structures and enumerations can access type
properties by using the type property’s name without a type name prefix.

The example below defines a structure called
`LevelTracker`{.code-voice}, which tracks a player’s progress through
the different levels or stages of a game. It is a single-player game,
but can store information for multiple players on a single device.

All of the game’s levels (apart from level one) are locked when the game
is first played. Every time a player finishes a level, that level is
unlocked for all players on the device. The `LevelTracker`{.code-voice}
structure uses type properties and methods to keep track of which levels
of the game have been unlocked. It also tracks the current level for an
individual player.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `struct`{.code-voice} `LevelTracker`{.vc} {
2.  `    static`{.code-voice} `var`{.kt} `highestUnlockedLevel`{.vc} =
    `1`{.m}
3.  `    static`{.code-voice} `func`{.kt}
    `unlockLevel`{.vc}(`level`{.vc}: `Int`{.n}) {
4.  `        if`{.code-voice} `level`{.vc} &gt;
    `highestUnlockedLevel`{.vc} { `highestUnlockedLevel`{.vc} =
    `level`{.vc} }
5.  `    }`{.code-voice}
6.  `    static`{.code-voice} `func`{.kt}
    `levelIsUnlocked`{.vc}(`level`{.vc}: `Int`{.n}) -&gt; `Bool`{.n} {
7.  `        return`{.code-voice} `level`{.vc} &lt;=
    `highestUnlockedLevel`{.vc}
8.  `    }`{.code-voice}
9.  `    var`{.code-voice} `currentLevel`{.vc} = `1`{.m}
10. `    mutating`{.code-voice} `func`{.kt}
    `advanceToLevel`{.vc}(`level`{.vc}: `Int`{.n}) -&gt; `Bool`{.n} {
11. `        if`{.code-voice}
    `LevelTracker`{.vc}.`levelIsUnlocked`{.vc}(`level`{.vc}) {
12. `            currentLevel`{.code-voice} = `level`{.vc}
13. `            return`{.code-voice} `true`{.kt}
14. `        } else`{.code-voice} {
15. `            return`{.code-voice} `false`{.kt}
16. `        }`{.code-voice}
17. `    }`{.code-voice}
18. `}`{.code-voice}

</div>

</div>

</div>

The `LevelTracker`{.code-voice} structure keeps track of the highest
level that any player has unlocked. This value is stored in a type
property called `highestUnlockedLevel`{.code-voice}.

`LevelTracker`{.code-voice} also defines two type functions to work with
the `highestUnlockedLevel`{.code-voice} property. The first is a type
function called `unlockLevel`{.code-voice}, which updates the value of
`highestUnlockedLevel`{.code-voice} whenever a new level is unlocked.
The second is a convenience type function called
`levelIsUnlocked`{.code-voice}, which returns `true`{.code-voice} if a
particular level number is already unlocked. (Note that these type
methods can access the `highestUnlockedLevel`{.code-voice} type property
without your needing to write it as
`LevelTracker.highestUnlockedLevel`{.code-voice}.)

In addition to its type property and type methods,
`LevelTracker`{.code-voice} tracks an individual player’s progress
through the game. It uses an instance property called
`currentLevel`{.code-voice} to track the level that a player is
currently playing.

To help manage the `currentLevel`{.code-voice} property,
`LevelTracker`{.code-voice} defines an instance method called
`advanceToLevel`{.code-voice}. Before updating
`currentLevel`{.code-voice}, this method checks whether the requested
new level is already unlocked. The `advanceToLevel(_:)`{.code-voice}
method returns a Boolean value to indicate whether or not it was
actually able to set `currentLevel`{.code-voice}.

The `LevelTracker`{.code-voice} structure is used with the
`Player`{.code-voice} class, shown below, to track and update the
progress of an individual player:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `class`{.code-voice} `Player`{.vc} {
2.  `    var`{.code-voice} `tracker`{.vc} = `LevelTracker`{.vc}()
3.  `    let`{.code-voice} `playerName`{.vc}: `String`{.n}
4.  `    func`{.code-voice} `completedLevel`{.vc}(`level`{.vc}:
    `Int`{.n}) {
5.  `        LevelTracker`{.code-voice}.`unlockLevel`{.vc}(`level`{.vc} +
    `1`{.m})
6.  `        tracker`{.code-voice}.`advanceToLevel`{.vc}(`level`{.vc} +
    `1`{.m})
7.  `    }`{.code-voice}
8.  `    init`{.code-voice}(`name`{.vc}: `String`{.n}) {
9.  `        playerName`{.code-voice} = `name`{.vc}
10. `    }`{.code-voice}
11. `}`{.code-voice}

</div>

</div>

</div>

The `Player`{.code-voice} class creates a new instance of
`LevelTracker`{.code-voice} to track that player’s progress. It also
provides a method called `completedLevel`{.code-voice}, which is called
whenever a player completes a particular level. This method unlocks the
next level for all players and updates the player’s progress to move
them to the next level. (The Boolean return value of
`advanceToLevel`{.code-voice} is ignored, because the level is known to
have been unlocked by the call to
`LevelTracker.unlockLevel`{.code-voice} on the previous line.)

You can create an instance of the `Player`{.code-voice} class for a new
player, and see what happens when the player completes level one:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `player`{.vc} = `Player`{.vc}(`name`{.vc}:
    `"Argyrios"`{.s})
2.  `player`{.code-voice}.`completedLevel`{.vc}(`1`{.m})
3.  `print`{.code-voice}(`"highest unlocked level is now `{.s}\\(`LevelTracker`{.vc}.`highestUnlockedLevel`{.vc})`"`{.s})
4.  `// prints "highest unlocked level is now 2"`{.code-voice}

</div>

</div>

</div>

If you create a second player, whom you try to move to a level that is
not yet unlocked by any player in the game, the attempt to set the
player’s current level fails:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `player`{.code-voice} = `Player`{.vc}(`name`{.vc}: `"Beto"`{.s})
2.  `if`{.code-voice}
    `player`{.vc}.`tracker`{.vc}.`advanceToLevel`{.vc}(`6`{.m}) {
3.  `    print`{.code-voice}(`"player is now on level 6"`{.s})
4.  `} else`{.code-voice} {
5.  `    print`{.code-voice}(`"level 6 has not yet been unlocked"`{.s})
6.  `}`{.code-voice}
7.  `// prints "level 6 has not yet been unlocked"`{.code-voice}

</div>

</div>

</div>

</div>

</div>

</div>
