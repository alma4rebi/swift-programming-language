<div class="content-wrapper">

<div id="chapter_container" class="conceptualwithtasks">

[‌](){#TP40016643-CH19}[‌](){#TP40016643-CH19-ID142}
Deinitialization {#deinitialization .chapter-name}
----------------

<div class="section section">

A *deinitializer* is called immediately before a class instance is
deallocated. You write deinitializers with the `deinit`{.code-voice}
keyword, similar to how initializers are written with the
`init`{.code-voice} keyword. Deinitializers are only available on class
types.

</div>

<div class="section section">

[‌](){#TP40016643-CH19-ID143}
### How Deinitialization Works {#how-deinitialization-works .section-name}

Swift automatically deallocates your instances when they are no longer
needed, to free up resources. Swift handles the memory management of
instances through *automatic reference counting* (*ARC*), as described
in [Automatic Reference Counting](AutomaticReferenceCounting.md).
Typically you don’t need to perform manual clean-up when your instances
are deallocated. However, when you are working with your own resources,
you might need to perform some additional clean-up yourself. For
example, if you create a custom class to open a file and write some data
to it, you might need to close the file before the class instance is
deallocated.

Class definitions can have at most one deinitializer per class. The
deinitializer does not take any parameters and is written without
parentheses:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `deinit`{.code-voice} {
2.  `    // perform the deinitialization`{.code-voice}
3.  `}`{.code-voice}

</div>

</div>

</div>

Deinitializers are called automatically, just before instance
deallocation takes place. You are not allowed to call a deinitializer
yourself. Superclass deinitializers are inherited by their subclasses,
and the superclass deinitializer is called automatically at the end of a
subclass deinitializer implementation. Superclass deinitializers are
always called, even if a subclass does not provide its own
deinitializer.

Because an instance is not deallocated until after its deinitializer is
called, a deinitializer can access all properties of the instance it is
called on and can modify its behavior based on those properties (such as
looking up the name of a file that needs to be closed).

</div>

<div class="section section">

[‌](){#TP40016643-CH19-ID144}
### Deinitializers in Action {#deinitializers-in-action .section-name}

Here’s an example of a deinitializer in action. This example defines two
new types, `Bank`{.code-voice} and `Player`{.code-voice}, for a simple
game. The `Bank`{.code-voice} class manages a made-up currency, which
can never have more than 10,000 coins in circulation. There can only
ever be one `Bank`{.code-voice} in the game, and so the
`Bank`{.code-voice} is implemented as a class with type properties and
methods to store and manage its current state:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `class`{.code-voice} `Bank`{.vc} {
2.  `    static`{.code-voice} `var`{.kt} `coinsInBank`{.vc} =
    `10_000`{.m}
3.  `    static`{.code-voice} `func`{.kt} `vendCoins`{.vc}(`var`{.kt}
    `numberOfCoinsToVend`{.vc}: `Int`{.n}) -&gt; `Int`{.n} {
4.  `        numberOfCoinsToVend`{.code-voice} =
    `min`{.vc}(`numberOfCoinsToVend`{.vc}, `coinsInBank`{.vc})
5.  `        coinsInBank`{.code-voice} -= `numberOfCoinsToVend`{.vc}
6.  `        return`{.code-voice} `numberOfCoinsToVend`{.vc}
7.  `    }`{.code-voice}
8.  `    static`{.code-voice} `func`{.kt}
    `receiveCoins`{.vc}(`coins`{.vc}: `Int`{.n}) {
9.  `        coinsInBank`{.code-voice} += `coins`{.vc}
10. `    }`{.code-voice}
11. `}`{.code-voice}

</div>

</div>

</div>

`Bank`{.code-voice} keeps track of the current number of coins it holds
with its `coinsInBank`{.code-voice} property. It also offers two
methods—`vendCoins(_:)`{.code-voice} and
`receiveCoins(_:)`{.code-voice}—to handle the distribution and
collection of coins.

`vendCoins(_:)`{.code-voice} checks that there are enough coins in the
bank before distributing them. If there are not enough coins,
`Bank`{.code-voice} returns a smaller number than the number that was
requested (and returns zero if no coins are left in the bank).
`vendCoins(_:)`{.code-voice} declares `numberOfCoinsToVend`{.code-voice}
as a variable parameter, so that the number can be modified within the
method’s body without the need to declare a new variable. It returns an
integer value to indicate the actual number of coins that were provided.

The `receiveCoins(_:)`{.code-voice} method simply adds the received
number of coins back into the bank’s coin store.

The `Player`{.code-voice} class describes a player in the game. Each
player has a certain number of coins stored in their purse at any time.
This is represented by the player’s `coinsInPurse`{.code-voice}
property:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `class`{.code-voice} `Player`{.vc} {
2.  `    var`{.code-voice} `coinsInPurse`{.vc}: `Int`{.n}
3.  `    init`{.code-voice}(`coins`{.vc}: `Int`{.n}) {
4.  `        coinsInPurse`{.code-voice} =
    `Bank`{.vc}.`vendCoins`{.vc}(`coins`{.vc})
5.  `    }`{.code-voice}
6.  `    func`{.code-voice} `winCoins`{.vc}(`coins`{.vc}: `Int`{.n}) {
7.  `        coinsInPurse`{.code-voice} +=
    `Bank`{.vc}.`vendCoins`{.vc}(`coins`{.vc})
8.  `    }`{.code-voice}
9.  `    deinit`{.code-voice} {
10. `        Bank`{.code-voice}.`receiveCoins`{.vc}(`coinsInPurse`{.vc})
11. `    }`{.code-voice}
12. `}`{.code-voice}

</div>

</div>

</div>

Each `Player`{.code-voice} instance is initialized with a starting
allowance of a specified number of coins from the bank during
initialization, although a `Player`{.code-voice} instance may receive
fewer than that number if not enough coins are available.

The `Player`{.code-voice} class defines a `winCoins(_:)`{.code-voice}
method, which retrieves a certain number of coins from the bank and adds
them to the player’s purse. The `Player`{.code-voice} class also
implements a deinitializer, which is called just before a
`Player`{.code-voice} instance is deallocated. Here, the deinitializer
simply returns all of the player’s coins to the bank:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `playerOne`{.vc}: `Player`{.n}? =
    `Player`{.vc}(`coins`{.vc}: `100`{.m})
2.  `print`{.code-voice}(`"A new player has joined the game with `{.s}\\(`playerOne`{.vc}!.`coinsInPurse`{.vc})` coins"`{.s})
3.  `// prints "A new player has joined the game with 100 coins"`{.code-voice}
4.  `print`{.code-voice}(`"There are now `{.s}\\(`Bank`{.vc}.`coinsInBank`{.vc})` coins left in the bank"`{.s})
5.  `// prints "There are now 9900 coins left in the bank"`{.code-voice}

</div>

</div>

</div>

A new `Player`{.code-voice} instance is created, with a request for 100
coins if they are available. This `Player`{.code-voice} instance is
stored in an optional `Player`{.code-voice} variable called
`playerOne`{.code-voice}. An optional variable is used here, because
players can leave the game at any point. The optional lets you track
whether there is currently a player in the game.

Because `playerOne`{.code-voice} is an optional, it is qualified with an
exclamation mark (`!`{.code-voice}) when its `coinsInPurse`{.code-voice}
property is accessed to print its default number of coins, and whenever
its `winCoins(_:)`{.code-voice} method is called:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `playerOne`{.code-voice}!.`winCoins`{.vc}(`2_000`{.m})
2.  `print`{.code-voice}(`"PlayerOne won 2000 coins & now has `{.s}\\(`playerOne`{.vc}!.`coinsInPurse`{.vc})` coins"`{.s})
3.  `// prints "PlayerOne won 2000 coins & now has 2100 coins"`{.code-voice}
4.  `print`{.code-voice}(`"The bank now only has `{.s}\\(`Bank`{.vc}.`coinsInBank`{.vc})` coins left"`{.s})
5.  `// prints "The bank now only has 7900 coins left"`{.code-voice}

</div>

</div>

</div>

Here, the player has won 2,000 coins. The player’s purse now contains
2,100 coins, and the bank has only 7,900 coins left.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `playerOne`{.code-voice} = `nil`{.kt}
2.  `print`{.code-voice}(`"PlayerOne has left the game"`{.s})
3.  `// prints "PlayerOne has left the game"`{.code-voice}
4.  `print`{.code-voice}(`"The bank now has `{.s}\\(`Bank`{.vc}.`coinsInBank`{.vc})` coins"`{.s})
5.  `// prints "The bank now has 10000 coins"`{.code-voice}

</div>

</div>

</div>

The player has now left the game. This is indicated by setting the
optional `playerOne`{.code-voice} variable to `nil`{.code-voice},
meaning “no `Player`{.code-voice} instance.” At the point that this
happens, the `playerOne`{.code-voice} variable’s reference to the
`Player`{.code-voice} instance is broken. No other properties or
variables are still referring to the `Player`{.code-voice} instance, and
so it is deallocated in order to free up its memory. Just before this
happens, its deinitializer is called automatically, and its coins are
returned to the bank.

</div>

</div>

</div>
