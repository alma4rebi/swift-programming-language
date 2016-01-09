<div class="content-wrapper">

<div id="chapter_container" class="conceptualwithtasks">

[‌](){#TP40016643-CH21}[‌](){#TP40016643-CH21-ID245}
Optional Chaining {#optional-chaining .chapter-name}
-----------------

<div class="section section">

*Optional chaining* is a process for querying and calling properties,
methods, and subscripts on an optional that might currently be
`nil`{.code-voice}. If the optional contains a value, the property,
method, or subscript call succeeds; if the optional is
`nil`{.code-voice}, the property, method, or subscript call returns
`nil`{.code-voice}. Multiple queries can be chained together, and the
entire chain fails gracefully if any link in the chain is
`nil`{.code-voice}.

<div class="note">

Note

Optional chaining in Swift is similar to messaging `nil`{.code-voice} in
Objective-C, but in a way that works for any type, and that can be
checked for success or failure.

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH21-ID246}
### Optional Chaining as an Alternative to Forced Unwrapping {#optional-chaining-as-an-alternative-to-forced-unwrapping .section-name}

You specify optional chaining by placing a question mark
(`?`{.code-voice}) after the optional value on which you wish to call a
property, method or subscript if the optional is non-`nil`{.code-voice}.
This is very similar to placing an exclamation mark (`!`{.code-voice})
after an optional value to force the unwrapping of its value. The main
difference is that optional chaining fails gracefully when the optional
is `nil`{.code-voice}, whereas forced unwrapping triggers a runtime
error when the optional is `nil`{.code-voice}.

To reflect the fact that optional chaining can be called on a
`nil`{.code-voice} value, the result of an optional chaining call is
always an optional value, even if the property, method, or subscript you
are querying returns a nonoptional value. You can use this optional
return value to check whether the optional chaining call was successful
(the returned optional contains a value), or did not succeed due to a
`nil`{.code-voice} value in the chain (the returned optional value is
`nil`{.code-voice}).

Specifically, the result of an optional chaining call is of the same
type as the expected return value, but wrapped in an optional. A
property that normally returns an `Int`{.code-voice} will return an
`Int?`{.code-voice} when accessed through optional chaining.

The next several code snippets demonstrate how optional chaining differs
from forced unwrapping and enables you to check for success.

First, two classes called `Person`{.code-voice} and
`Residence`{.code-voice} are defined:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `class`{.code-voice} `Person`{.vc} {
2.  `    var`{.code-voice} `residence`{.vc}: `Residence`{.n}?
3.  `}`{.code-voice}
4.  ` `{.code-voice}
5.  `class`{.code-voice} `Residence`{.vc} {
6.  `    var`{.code-voice} `numberOfRooms`{.vc} = `1`{.m}
7.  `}`{.code-voice}

</div>

</div>

</div>

`Residence`{.code-voice} instances have a single `Int`{.code-voice}
property called `numberOfRooms`{.code-voice}, with a default value of
`1`{.code-voice}. `Person`{.code-voice} instances have an optional
`residence`{.code-voice} property of type `Residence?`{.code-voice}.

If you create a new `Person`{.code-voice} instance, its
`residence`{.code-voice} property is default initialized to
`nil`{.code-voice}, by virtue of being optional. In the code below,
`john`{.code-voice} has a `residence`{.code-voice} property value of
`nil`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `john`{.vc} = `Person`{.vc}()

</div>

</div>

</div>

If you try to access the `numberOfRooms`{.code-voice} property of this
person’s `residence`{.code-voice}, by placing an exclamation mark after
`residence`{.code-voice} to force the unwrapping of its value, you
trigger a runtime error, because there is no `residence`{.code-voice}
value to unwrap:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `roomCount`{.vc} =
    `john`{.vc}.`residence`{.vc}!.`numberOfRooms`{.vc}
2.  `// this triggers a runtime error`{.code-voice}

</div>

</div>

</div>

The code above succeeds when `john.residence`{.code-voice} has a
non-`nil`{.code-voice} value and will set `roomCount`{.code-voice} to an
`Int`{.code-voice} value containing the appropriate number of rooms.
However, this code always triggers a runtime error when
`residence`{.code-voice} is `nil`{.code-voice}, as illustrated above.

Optional chaining provides an alternative way to access the value of
`numberOfRooms`{.code-voice}. To use optional chaining, use a question
mark in place of the exclamation mark:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `if`{.code-voice} `let`{.kt} `roomCount`{.vc} =
    `john`{.vc}.`residence`{.vc}?.`numberOfRooms`{.vc} {
2.  `    print`{.code-voice}(`"John's residence has `{.s}\\(`roomCount`{.vc})` room(s)."`{.s})
3.  `} else`{.code-voice} {
4.  `    print`{.code-voice}(`"Unable to retrieve the number of rooms."`{.s})
5.  `}`{.code-voice}
6.  `// prints "Unable to retrieve the number of rooms."`{.code-voice}

</div>

</div>

</div>

This tells Swift to “chain” on the optional `residence`{.code-voice}
property and to retrieve the value of `numberOfRooms`{.code-voice} if
`residence`{.code-voice} exists.

Because the attempt to access `numberOfRooms`{.code-voice} has the
potential to fail, the optional chaining attempt returns a value of type
`Int?`{.code-voice}, or “optional `Int`{.code-voice}”. When
`residence`{.code-voice} is `nil`{.code-voice}, as in the example above,
this optional `Int`{.code-voice} will also be `nil`{.code-voice}, to
reflect the fact that it was not possible to access
`numberOfRooms`{.code-voice}. The optional `Int`{.code-voice} is
accessed through optional binding to unwrap the integer and assign the
nonoptional value to the `roomCount`{.code-voice} variable.

Note that this is true even though `numberOfRooms`{.code-voice} is a
nonoptional `Int`{.code-voice}. The fact that it is queried through an
optional chain means that the call to `numberOfRooms`{.code-voice} will
always return an `Int?`{.code-voice} instead of an `Int`{.code-voice}.

You can assign a `Residence`{.code-voice} instance to
`john.residence`{.code-voice}, so that it no longer has a
`nil`{.code-voice} value:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `john`{.code-voice}.`residence`{.vc} = `Residence`{.vc}()

</div>

</div>

</div>

`john.residence`{.code-voice} now contains an actual
`Residence`{.code-voice} instance, rather than `nil`{.code-voice}. If
you try to access `numberOfRooms`{.code-voice} with the same optional
chaining as before, it will now return an `Int?`{.code-voice} that
contains the default `numberOfRooms`{.code-voice} value of
`1`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `if`{.code-voice} `let`{.kt} `roomCount`{.vc} =
    `john`{.vc}.`residence`{.vc}?.`numberOfRooms`{.vc} {
2.  `    print`{.code-voice}(`"John's residence has `{.s}\\(`roomCount`{.vc})` room(s)."`{.s})
3.  `} else`{.code-voice} {
4.  `    print`{.code-voice}(`"Unable to retrieve the number of rooms."`{.s})
5.  `}`{.code-voice}
6.  `// prints "John's residence has 1 room(s)."`{.code-voice}

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH21-ID247}
### Defining Model Classes for Optional Chaining {#defining-model-classes-for-optional-chaining .section-name}

You can use optional chaining with calls to properties, methods, and
subscripts that are more than one level deep. This enables you to drill
down into subproperties within complex models of interrelated types, and
to check whether it is possible to access properties, methods, and
subscripts on those subproperties.

The code snippets below define four model classes for use in several
subsequent examples, including examples of multilevel optional chaining.
These classes expand upon the `Person`{.code-voice} and
`Residence`{.code-voice} model from above by adding a
`Room`{.code-voice} and `Address`{.code-voice} class, with associated
properties, methods, and subscripts.

The `Person`{.code-voice} class is defined in the same way as before:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `class`{.code-voice} `Person`{.vc} {
2.  `    var`{.code-voice} `residence`{.vc}: `Residence`{.n}?
3.  `}`{.code-voice}

</div>

</div>

</div>

The `Residence`{.code-voice} class is more complex than before. This
time, the `Residence`{.code-voice} class defines a variable property
called `rooms`{.code-voice}, which is initialized with an empty array of
type `[Room]`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `class`{.code-voice} `Residence`{.vc} {
2.  `    var`{.code-voice} `rooms`{.vc} = \[`Room`{.vc}\]()
3.  `    var`{.code-voice} `numberOfRooms`{.vc}: `Int`{.n} {
4.  `        return`{.code-voice} `rooms`{.vc}.`count`{.vc}
5.  `    }`{.code-voice}
6.  `    subscript`{.code-voice}(`i`{.vc}: `Int`{.n}) -&gt; `Room`{.n} {
7.  `        get`{.code-voice} {
8.  `            return`{.code-voice} `rooms`{.vc}\[`i`{.vc}\]
9.  `        }`{.code-voice}
10. `        set`{.code-voice} {
11. `            rooms`{.code-voice}\[`i`{.vc}\] = `newValue`{.vc}
12. `        }`{.code-voice}
13. `    }`{.code-voice}
14. `    func`{.code-voice} `printNumberOfRooms`{.vc}() {
15. `        print`{.code-voice}(`"The number of rooms is `{.s}\\(`numberOfRooms`{.vc})`"`{.s})
16. `    }`{.code-voice}
17. `    var`{.code-voice} `address`{.vc}: `Address`{.n}?
18. `}`{.code-voice}

</div>

</div>

</div>

Because this version of `Residence`{.code-voice} stores an array of
`Room`{.code-voice} instances, its `numberOfRooms`{.code-voice} property
is implemented as a computed property, not a stored property. The
computed `numberOfRooms`{.code-voice} property simply returns the value
of the `count`{.code-voice} property from the `rooms`{.code-voice}
array.

As a shortcut to accessing its `rooms`{.code-voice} array, this version
of `Residence`{.code-voice} provides a read-write subscript that
provides access to the room at the requested index in the
`rooms`{.code-voice} array.

This version of `Residence`{.code-voice} also provides a method called
`printNumberOfRooms`{.code-voice}, which simply prints the number of
rooms in the residence.

Finally, `Residence`{.code-voice} defines an optional property called
`address`{.code-voice}, with a type of `Address?`{.code-voice}. The
`Address`{.code-voice} class type for this property is defined below.

The `Room`{.code-voice} class used for the `rooms`{.code-voice} array is
a simple class with one property called `name`{.code-voice}, and an
initializer to set that property to a suitable room name:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `class`{.code-voice} `Room`{.vc} {
2.  `    let`{.code-voice} `name`{.vc}: `String`{.n}
3.  `    init`{.code-voice}(`name`{.vc}: `String`{.n}) {
    `self`{.kt}.`name`{.vc} = `name`{.vc} }
4.  `}`{.code-voice}

</div>

</div>

</div>

The final class in this model is called `Address`{.code-voice}. This
class has three optional properties of type `String?`{.code-voice}. The
first two properties, `buildingName`{.code-voice} and
`buildingNumber`{.code-voice}, are alternative ways to identify a
particular building as part of an address. The third property,
`street`{.code-voice}, is used to name the street for that address:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `class`{.code-voice} `Address`{.vc} {
2.  `    var`{.code-voice} `buildingName`{.vc}: `String`{.n}?
3.  `    var`{.code-voice} `buildingNumber`{.vc}: `String`{.n}?
4.  `    var`{.code-voice} `street`{.vc}: `String`{.n}?
5.  `    func`{.code-voice} `buildingIdentifier`{.vc}() -&gt;
    `String`{.n}? {
6.  `        if`{.code-voice} `buildingName`{.vc} != `nil`{.kt} {
7.  `            return`{.code-voice} `buildingName`{.vc}
8.  `        } else`{.code-voice} `if`{.kt} `buildingNumber`{.vc} !=
    `nil`{.kt} && `street`{.vc} != `nil`{.kt} {
9.  `            return`{.code-voice}
    `"`{.s}\\(`buildingNumber`{.vc})` `{.s}\\(`street`{.vc})`"`{.s}
10. `        } else`{.code-voice} {
11. `            return`{.code-voice} `nil`{.kt}
12. `        }`{.code-voice}
13. `    }`{.code-voice}
14. `}`{.code-voice}

</div>

</div>

</div>

The `Address`{.code-voice} class also provides a method called
`buildingIdentifier()`{.code-voice}, which has a return type of
`String?`{.code-voice}. This method checks the properties of the address
and returns `buildingName`{.code-voice} if it has a value, or
`buildingNumber`{.code-voice} concatenated with `street`{.code-voice} if
both have values, or `nil`{.code-voice} otherwise.

</div>

<div class="section section">

[‌](){#TP40016643-CH21-ID248}
### Accessing Properties Through Optional Chaining {#accessing-properties-through-optional-chaining .section-name}

As demonstrated in [Optional Chaining as an Alternative to Forced
Unwrapping](OptionalChaining.md#TP40016643-CH21-ID246), you can use
optional chaining to access a property on an optional value, and to
check if that property access is successful.

Use the classes defined above to create a new `Person`{.code-voice}
instance, and try to access its `numberOfRooms`{.code-voice} property as
before:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `john`{.vc} = `Person`{.vc}()
2.  `if`{.code-voice} `let`{.kt} `roomCount`{.vc} =
    `john`{.vc}.`residence`{.vc}?.`numberOfRooms`{.vc} {
3.  `    print`{.code-voice}(`"John's residence has `{.s}\\(`roomCount`{.vc})` room(s)."`{.s})
4.  `} else`{.code-voice} {
5.  `    print`{.code-voice}(`"Unable to retrieve the number of rooms."`{.s})
6.  `}`{.code-voice}
7.  `// prints "Unable to retrieve the number of rooms."`{.code-voice}

</div>

</div>

</div>

Because `john.residence`{.code-voice} is `nil`{.code-voice}, this
optional chaining call fails in the same way as before.

You can also attempt to set a property’s value through optional
chaining:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `someAddress`{.vc} = `Address`{.vc}()
2.  `someAddress`{.code-voice}.`buildingNumber`{.vc} = `"29"`{.s}
3.  `someAddress`{.code-voice}.`street`{.vc} = `"Acacia Road"`{.s}
4.  `john`{.code-voice}.`residence`{.vc}?.`address`{.vc} =
    `someAddress`{.vc}

</div>

</div>

</div>

In this example, the attempt to set the `address`{.code-voice} property
of `john.residence`{.code-voice} will fail, because
`john.residence`{.code-voice} is currently `nil`{.code-voice}.

The assignment is part of the optional chaining, which means none of the
code on the right hand side of the `=`{.code-voice} operator is
evaluated. In the previous example, it’s not easy to see that
`someAddress`{.code-voice} is never evaluated, because accessing a
constant doesn’t have any side effects. The listing below does the same
assignment, but it uses a function to create the address. The function
prints “Function was called” before returning a value, which lets you
see whether the right hand side of the `=`{.code-voice} operator was
evaluated.

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `createAddress`{.vc}() -&gt; `Address`{.n} {
2.  `    print`{.code-voice}(`"Function was called."`{.s})
3.  `    `{.code-voice}
4.  `    let`{.code-voice} `someAddress`{.vc} = `Address`{.vc}()
5.  `    someAddress`{.code-voice}.`buildingNumber`{.vc} = `"29"`{.s}
6.  `    someAddress`{.code-voice}.`street`{.vc} = `"Acacia Road"`{.s}
7.  `    `{.code-voice}
8.  `    return`{.code-voice} `someAddress`{.vc}
9.  `}`{.code-voice}
10. `john`{.code-voice}.`residence`{.vc}?.`address`{.vc} =
    `createAddress`{.vc}()

</div>

</div>

</div>

You can tell that the `createAddress()`{.code-voice} function isn’t
called, because nothing is printed.

</div>

<div class="section section">

[‌](){#TP40016643-CH21-ID249}
### Calling Methods Through Optional Chaining {#calling-methods-through-optional-chaining .section-name}

You can use optional chaining to call a method on an optional value, and
to check whether that method call is successful. You can do this even if
that method does not define a return value.

The `printNumberOfRooms()`{.code-voice} method on the
`Residence`{.code-voice} class prints the current value of
`numberOfRooms`{.code-voice}. Here’s how the method looks:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `printNumberOfRooms`{.vc}() {
2.  `    print`{.code-voice}(`"The number of rooms is `{.s}\\(`numberOfRooms`{.vc})`"`{.s})
3.  `}`{.code-voice}

</div>

</div>

</div>

This method does not specify a return type. However, functions and
methods with no return type have an implicit return type of
`Void`{.code-voice}, as described in [Functions Without Return
Values](Functions.md#TP40016643-CH10-ID163). This means that they
return a value of `()`{.code-voice}, or an empty tuple.

If you call this method on an optional value with optional chaining, the
method’s return type will be `Void?`{.code-voice}, not
`Void`{.code-voice}, because return values are always of an optional
type when called through optional chaining. This enables you to use an
`if`{.code-voice} statement to check whether it was possible to call the
`printNumberOfRooms()`{.code-voice} method, even though the method does
not itself define a return value. Compare the return value from the
`printNumberOfRooms`{.code-voice} call against `nil`{.code-voice} to see
if the method call was successful:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `if`{.code-voice}
    `john`{.vc}.`residence`{.vc}?.`printNumberOfRooms`{.vc}() !=
    `nil`{.kt} {
2.  `    print`{.code-voice}(`"It was possible to print the number of rooms."`{.s})
3.  `} else`{.code-voice} {
4.  `    print`{.code-voice}(`"It was not possible to print the number of rooms."`{.s})
5.  `}`{.code-voice}
6.  `// prints "It was not possible to print the number of rooms."`{.code-voice}

</div>

</div>

</div>

The same is true if you attempt to set a property through optional
chaining. The example above in [Accessing Properties Through Optional
Chaining](OptionalChaining.md#TP40016643-CH21-ID248) attempts to set
an `address`{.code-voice} value for `john.residence`{.code-voice}, even
though the `residence`{.code-voice} property is `nil`{.code-voice}. Any
attempt to set a property through optional chaining returns a value of
type `Void?`{.code-voice}, which enables you to compare against
`nil`{.code-voice} to see if the property was set successfully:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `if`{.code-voice} (`john`{.vc}.`residence`{.vc}?.`address`{.vc} =
    `someAddress`{.vc}) != `nil`{.kt} {
2.  `    print`{.code-voice}(`"It was possible to set the address."`{.s})
3.  `} else`{.code-voice} {
4.  `    print`{.code-voice}(`"It was not possible to set the address."`{.s})
5.  `}`{.code-voice}
6.  `// prints "It was not possible to set the address."`{.code-voice}

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH21-ID250}
### Accessing Subscripts Through Optional Chaining {#accessing-subscripts-through-optional-chaining .section-name}

You can use optional chaining to try to retrieve and set a value from a
subscript on an optional value, and to check whether that subscript call
is successful.

<div class="note">

Note

When you access a subscript on an optional value through optional
chaining, you place the question mark *before* the subscript’s brackets,
not after. The optional chaining question mark always follows
immediately after the part of the expression that is optional.

</div>

The example below tries to retrieve the name of the first room in the
`rooms`{.code-voice} array of the `john.residence`{.code-voice} property
using the subscript defined on the `Residence`{.code-voice} class.
Because `john.residence`{.code-voice} is currently `nil`{.code-voice},
the subscript call fails:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `if`{.code-voice} `let`{.kt} `firstRoomName`{.vc} =
    `john`{.vc}.`residence`{.vc}?\[`0`{.m}\].`name`{.vc} {
2.  `    print`{.code-voice}(`"The first room name is `{.s}\\(`firstRoomName`{.vc})`."`{.s})
3.  `} else`{.code-voice} {
4.  `    print`{.code-voice}(`"Unable to retrieve the first room name."`{.s})
5.  `}`{.code-voice}
6.  `// prints "Unable to retrieve the first room name."`{.code-voice}

</div>

</div>

</div>

The optional chaining question mark in this subscript call is placed
immediately after `john.residence`{.code-voice}, before the subscript
brackets, because `john.residence`{.code-voice} is the optional value on
which optional chaining is being attempted.

Similarly, you can try to set a new value through a subscript with
optional chaining:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `john`{.code-voice}.`residence`{.vc}?\[`0`{.m}\] =
    `Room`{.vc}(`name`{.vc}: `"Bathroom"`{.s})

</div>

</div>

</div>

This subscript setting attempt also fails, because
`residence`{.code-voice} is currently `nil`{.code-voice}.

If you create and assign an actual `Residence`{.code-voice} instance to
`john.residence`{.code-voice}, with one or more `Room`{.code-voice}
instances in its `rooms`{.code-voice} array, you can use the
`Residence`{.code-voice} subscript to access the actual items in the
`rooms`{.code-voice} array through optional chaining:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `johnsHouse`{.vc} = `Residence`{.vc}()
2.  `johnsHouse`{.code-voice}.`rooms`{.vc}.`append`{.vc}(`Room`{.vc}(`name`{.vc}:
    `"Living Room"`{.s}))
3.  `johnsHouse`{.code-voice}.`rooms`{.vc}.`append`{.vc}(`Room`{.vc}(`name`{.vc}:
    `"Kitchen"`{.s}))
4.  `john`{.code-voice}.`residence`{.vc} = `johnsHouse`{.vc}
5.  ` `{.code-voice}
6.  `if`{.code-voice} `let`{.kt} `firstRoomName`{.vc} =
    `john`{.vc}.`residence`{.vc}?\[`0`{.m}\].`name`{.vc} {
7.  `    print`{.code-voice}(`"The first room name is `{.s}\\(`firstRoomName`{.vc})`."`{.s})
8.  `} else`{.code-voice} {
9.  `    print`{.code-voice}(`"Unable to retrieve the first room name."`{.s})
10. `}`{.code-voice}
11. `// prints "The first room name is Living Room."`{.code-voice}

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH21-ID251}
### Accessing Subscripts of Optional Type {#accessing-subscripts-of-optional-type .section-name}

If a subscript returns a value of optional type—such as the key
subscript of Swift’s `Dictionary`{.code-voice} type—place a question
mark *after* the subscript’s closing bracket to chain on its optional
return value:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `testScores`{.vc} = \[`"Dave"`{.s}: \[`86`{.m},
    `82`{.m}, `84`{.m}\], `"Bev"`{.s}: \[`79`{.m}, `94`{.m},
    `81`{.m}\]\]
2.  `testScores`{.code-voice}\[`"Dave"`{.s}\]?\[`0`{.m}\] = `91`{.m}
3.  `testScores`{.code-voice}\[`"Bev"`{.s}\]?\[`0`{.m}\]++
4.  `testScores`{.code-voice}\[`"Brian"`{.s}\]?\[`0`{.m}\] = `72`{.m}
5.  `// the "Dave" array is now [91, 82, 84] and the "Bev" array is now [80, 94, 81]`{.code-voice}

</div>

</div>

</div>

The example above defines a dictionary called `testScores`{.code-voice},
which contains two key-value pairs that map a `String`{.code-voice} key
to an array of `Int`{.code-voice} values. The example uses optional
chaining to set the first item in the `"Dave"`{.code-voice} array to
`91`{.code-voice}; to increment the first item in the
`"Bev"`{.code-voice} array by `1`{.code-voice}; and to try to set the
first item in an array for a key of `"Brian"`{.code-voice}. The first
two calls succeed, because the `testScores`{.code-voice} dictionary
contains keys for `"Dave"`{.code-voice} and `"Bev"`{.code-voice}. The
third call fails, because the `testScores`{.code-voice} dictionary does
not contain a key for `"Brian"`{.code-voice}.

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH21-ID252}
### Linking Multiple Levels of Chaining {#linking-multiple-levels-of-chaining .section-name}

You can link together multiple levels of optional chaining to drill down
to properties, methods, and subscripts deeper within a model. However,
multiple levels of optional chaining do not add more levels of
optionality to the returned value.

To put it another way:

-   If the type you are trying to retrieve is not optional, it will
    become optional because of the optional chaining.

-   If the type you are trying to retrieve is *already* optional, it
    will not become *more* optional because of the chaining.

Therefore:

-   If you try to retrieve an `Int`{.code-voice} value through optional
    chaining, an `Int?`{.code-voice} is always returned, no matter how
    many levels of chaining are used.

-   Similarly, if you try to retrieve an `Int?`{.code-voice} value
    through optional chaining, an `Int?`{.code-voice} is always
    returned, no matter how many levels of chaining are used.

The example below tries to access the `street`{.code-voice} property of
the `address`{.code-voice} property of the `residence`{.code-voice}
property of `john`{.code-voice}. There are *two* levels of optional
chaining in use here, to chain through the `residence`{.code-voice} and
`address`{.code-voice} properties, both of which are of optional type:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `if`{.code-voice} `let`{.kt} `johnsStreet`{.vc} =
    `john`{.vc}.`residence`{.vc}?.`address`{.vc}?.`street`{.vc} {
2.  `    print`{.code-voice}(`"John's street name is `{.s}\\(`johnsStreet`{.vc})`."`{.s})
3.  `} else`{.code-voice} {
4.  `    print`{.code-voice}(`"Unable to retrieve the address."`{.s})
5.  `}`{.code-voice}
6.  `// prints "Unable to retrieve the address."`{.code-voice}

</div>

</div>

</div>

The value of `john.residence`{.code-voice} currently contains a valid
`Residence`{.code-voice} instance. However, the value of
`john.residence.address`{.code-voice} is currently `nil`{.code-voice}.
Because of this, the call to
`john.residence?.address?.street`{.code-voice} fails.

Note that in the example above, you are trying to retrieve the value of
the `street`{.code-voice} property. The type of this property is
`String?`{.code-voice}. The return value of
`john.residence?.address?.street`{.code-voice} is therefore also
`String?`{.code-voice}, even though two levels of optional chaining are
applied in addition to the underlying optional type of the property.

If you set an actual `Address`{.code-voice} instance as the value for
`john.residence.address`{.code-voice}, and set an actual value for the
address’s `street`{.code-voice} property, you can access the value of
the `street`{.code-voice} property through multilevel optional chaining:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `johnsAddress`{.vc} = `Address`{.vc}()
2.  `johnsAddress`{.code-voice}.`buildingName`{.vc} =
    `"The Larches"`{.s}
3.  `johnsAddress`{.code-voice}.`street`{.vc} = `"Laurel Street"`{.s}
4.  `john`{.code-voice}.`residence`{.vc}?.`address`{.vc} =
    `johnsAddress`{.vc}
5.  ` `{.code-voice}
6.  `if`{.code-voice} `let`{.kt} `johnsStreet`{.vc} =
    `john`{.vc}.`residence`{.vc}?.`address`{.vc}?.`street`{.vc} {
7.  `    print`{.code-voice}(`"John's street name is `{.s}\\(`johnsStreet`{.vc})`."`{.s})
8.  `} else`{.code-voice} {
9.  `    print`{.code-voice}(`"Unable to retrieve the address."`{.s})
10. `}`{.code-voice}
11. `// prints "John's street name is Laurel Street."`{.code-voice}

</div>

</div>

</div>

In this example, the attempt to set the `address`{.code-voice} property
of `john.residence`{.code-voice} will succeed, because the value of
`john.residence`{.code-voice} currently contains a valid
`Residence`{.code-voice} instance.

</div>

<div class="section section">

[‌](){#TP40016643-CH21-ID253}
### Chaining on Methods with Optional Return Values {#chaining-on-methods-with-optional-return-values .section-name}

The previous example shows how to retrieve the value of a property of
optional type through optional chaining. You can also use optional
chaining to call a method that returns a value of optional type, and to
chain on that method’s return value if needed.

The example below calls the `Address`{.code-voice} class’s
`buildingIdentifier()`{.code-voice} method through optional chaining.
This method returns a value of type `String?`{.code-voice}. As described
above, the ultimate return type of this method call after optional
chaining is also `String?`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `if`{.code-voice} `let`{.kt} `buildingIdentifier`{.vc} =
    `john`{.vc}.`residence`{.vc}?.`address`{.vc}?.`buildingIdentifier`{.vc}()
    {
2.  `    print`{.code-voice}(`"John's building identifier is `{.s}\\(`buildingIdentifier`{.vc})`."`{.s})
3.  `}`{.code-voice}
4.  `// prints "John's building identifier is The Larches."`{.code-voice}

</div>

</div>

</div>

If you want to perform further optional chaining on this method’s return
value, place the optional chaining question mark *after* the method’s
parentheses:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `if`{.code-voice} `let`{.kt} `beginsWithThe`{.vc} =
2.  `    john`{.code-voice}.`residence`{.vc}?.`address`{.vc}?.`buildingIdentifier`{.vc}()?.`hasPrefix`{.vc}(`"The"`{.s})
    {
3.  `        if`{.code-voice} `beginsWithThe`{.vc} {
4.  `            print`{.code-voice}(`"John's building identifier begins with \"The\"."`{.s})
5.  `        } else`{.code-voice} {
6.  `            print`{.code-voice}(`"John's building identifier does not begin with \"The\"."`{.s})
7.  `        }`{.code-voice}
8.  `}`{.code-voice}
9.  `// prints "John's building identifier begins with "The"."`{.code-voice}

</div>

</div>

</div>

<div class="note">

Note

In the example above, you place the optional chaining question mark
*after* the parentheses, because the optional value you are chaining on
is the `buildingIdentifier()`{.code-voice} method’s return value, and
not the `buildingIdentifier()`{.code-voice} method itself.

</div>

</div>

</div>

</div>
