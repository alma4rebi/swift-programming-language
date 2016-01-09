<div class="content-wrapper">

<div id="chapter_container" class="conceptualwithtasks">

[‌](){#TP40016643-CH17}[‌](){#TP40016643-CH17-ID193}
Inheritance {#inheritance .chapter-name}
-----------

<div class="section section">

A class can *inherit* methods, properties, and other characteristics
from another class. When one class inherits from another, the inheriting
class is known as a *subclass*, and the class it inherits from is known
as its *superclass*. Inheritance is a fundamental behavior that
differentiates classes from other types in Swift.

Classes in Swift can call and access methods, properties, and subscripts
belonging to their superclass and can provide their own overriding
versions of those methods, properties, and subscripts to refine or
modify their behavior. Swift helps to ensure your overrides are correct
by checking that the override definition has a matching superclass
definition.

Classes can also add property observers to inherited properties in order
to be notified when the value of a property changes. Property observers
can be added to any property, regardless of whether it was originally
defined as a stored or computed property.

</div>

<div class="section section">

[‌](){#TP40016643-CH17-ID194}
### Defining a Base Class {#defining-a-base-class .section-name}

Any class that does not inherit from another class is known as a *base
class*.

<div class="note">

Note

Swift classes do not inherit from a universal base class. Classes you
define without specifying a superclass automatically become base classes
for you to build upon.

</div>

The example below defines a base class called `Vehicle`{.code-voice}.
This base class defines a stored property called
`currentSpeed`{.code-voice}, with a default value of `0.0`{.code-voice}
(inferring a property type of `Double`{.code-voice}). The
`currentSpeed`{.code-voice} property’s value is used by a read-only
computed `String`{.code-voice} property called
`description`{.code-voice} to create a description of the vehicle.

The `Vehicle`{.code-voice} base class also defines a method called
`makeNoise`{.code-voice}. This method does not actually do anything for
a base `Vehicle`{.code-voice} instance, but will be customized by
subclasses of `Vehicle`{.code-voice} later on:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `class`{.code-voice} `Vehicle`{.vc} {
2.  `    var`{.code-voice} `currentSpeed`{.vc} = `0.0`{.m}
3.  `    var`{.code-voice} `description`{.vc}: `String`{.n} {
4.  `        return`{.code-voice}
    `"traveling at `{.s}\\(`currentSpeed`{.vc})` miles per hour"`{.s}
5.  `    }`{.code-voice}
6.  `    func`{.code-voice} `makeNoise`{.vc}() {
7.  `        // do nothing - an arbitrary vehicle doesn't necessarily make a noise`{.code-voice}
8.  `    }`{.code-voice}
9.  `}`{.code-voice}

</div>

</div>

</div>

You create a new instance of `Vehicle`{.code-voice} with *initializer
syntax*, which is written as a `TypeName`{.code-voice} followed by empty
parentheses:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `someVehicle`{.vc} = `Vehicle`{.vc}()

</div>

</div>

</div>

Having created a new `Vehicle`{.code-voice} instance, you can access its
`description`{.code-voice} property to print a human-readable
description of the vehicle’s current speed:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `print`{.code-voice}(`"Vehicle: `{.s}\\(`someVehicle`{.vc}.`description`{.vc})`"`{.s})
2.  `// Vehicle: traveling at 0.0 miles per hour`{.code-voice}

</div>

</div>

</div>

The `Vehicle`{.code-voice} class defines common characteristics for an
arbitrary vehicle, but is not much use in itself. To make it more
useful, you need to refine it to describe more specific kinds of
vehicle.

</div>

<div class="section section">

[‌](){#TP40016643-CH17-ID195}
### Subclassing {#subclassing .section-name}

*Subclassing* is the act of basing a new class on an existing class. The
subclass inherits characteristics from the existing class, which you can
then refine. You can also add new characteristics to the subclass.

To indicate that a subclass has a superclass, write the subclass name
before the superclass name, separated by a colon:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `class`{.code-voice} `SomeSubclass`{.vc}: `SomeSuperclass`{.n} {
2.  `    // subclass definition goes here`{.code-voice}
3.  `}`{.code-voice}

</div>

</div>

</div>

The following example defines a subclass called `Bicycle`{.code-voice},
with a superclass of `Vehicle`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `class`{.code-voice} `Bicycle`{.vc}: `Vehicle`{.n} {
2.  `    var`{.code-voice} `hasBasket`{.vc} = `false`{.kt}
3.  `}`{.code-voice}

</div>

</div>

</div>

The new `Bicycle`{.code-voice} class automatically gains all of the
characteristics of `Vehicle`{.code-voice}, such as its
`currentSpeed`{.code-voice} and `description`{.code-voice} properties
and its `makeNoise()`{.code-voice} method.

In addition to the characteristics it inherits, the
`Bicycle`{.code-voice} class defines a new stored property,
`hasBasket`{.code-voice}, with a default value of `false`{.code-voice}
(inferring a type of `Bool`{.code-voice} for the property).

By default, any new `Bicycle`{.code-voice} instance you create will not
have a basket. You can set the `hasBasket`{.code-voice} property to
`true`{.code-voice} for a particular `Bicycle`{.code-voice} instance
after that instance is created:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `bicycle`{.vc} = `Bicycle`{.vc}()
2.  `bicycle`{.code-voice}.`hasBasket`{.vc} = `true`{.kt}

</div>

</div>

</div>

You can also modify the inherited `currentSpeed`{.code-voice} property
of a `Bicycle`{.code-voice} instance, and query the instance’s inherited
`description`{.code-voice} property:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `bicycle`{.code-voice}.`currentSpeed`{.vc} = `15.0`{.m}
2.  `print`{.code-voice}(`"Bicycle: `{.s}\\(`bicycle`{.vc}.`description`{.vc})`"`{.s})
3.  `// Bicycle: traveling at 15.0 miles per hour`{.code-voice}

</div>

</div>

</div>

Subclasses can themselves be subclassed. The next example creates a
subclass of `Bicycle`{.code-voice} for a two-seater bicycle known as a
“tandem”:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `class`{.code-voice} `Tandem`{.vc}: `Bicycle`{.n} {
2.  `    var`{.code-voice} `currentNumberOfPassengers`{.vc} = `0`{.m}
3.  `}`{.code-voice}

</div>

</div>

</div>

`Tandem`{.code-voice} inherits all of the properties and methods from
`Bicycle`{.code-voice}, which in turn inherits all of the properties and
methods from `Vehicle`{.code-voice}. The `Tandem`{.code-voice} subclass
also adds a new stored property called
`currentNumberOfPassengers`{.code-voice}, with a default value of
`0`{.code-voice}.

If you create an instance of `Tandem`{.code-voice}, you can work with
any of its new and inherited properties, and query the read-only
`description`{.code-voice} property it inherits from
`Vehicle`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `tandem`{.vc} = `Tandem`{.vc}()
2.  `tandem`{.code-voice}.`hasBasket`{.vc} = `true`{.kt}
3.  `tandem`{.code-voice}.`currentNumberOfPassengers`{.vc} = `2`{.m}
4.  `tandem`{.code-voice}.`currentSpeed`{.vc} = `22.0`{.m}
5.  `print`{.code-voice}(`"Tandem: `{.s}\\(`tandem`{.vc}.`description`{.vc})`"`{.s})
6.  `// Tandem: traveling at 22.0 miles per hour`{.code-voice}

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH17-ID196}
### Overriding {#overriding .section-name}

A subclass can provide its own custom implementation of an instance
method, type method, instance property, type property, or subscript that
it would otherwise inherit from a superclass. This is known as
*overriding*.

To override a characteristic that would otherwise be inherited, you
prefix your overriding definition with the `override`{.code-voice}
keyword. Doing so clarifies that you intend to provide an override and
have not provided a matching definition by mistake. Overriding by
accident can cause unexpected behavior, and any overrides without the
`override`{.code-voice} keyword are diagnosed as an error when your code
is compiled.

The `override`{.code-voice} keyword also prompts the Swift compiler to
check that your overriding class’s superclass (or one of its parents)
has a declaration that matches the one you provided for the override.
This check ensures that your overriding definition is correct.

<div class="section section">

[‌](){#TP40016643-CH17-ID197}
### Accessing Superclass Methods, Properties, and Subscripts {#accessing-superclass-methods-properties-and-subscripts .section-name}

When you provide a method, property, or subscript override for a
subclass, it is sometimes useful to use the existing superclass
implementation as part of your override. For example, you can refine the
behavior of that existing implementation, or store a modified value in
an existing inherited variable.

Where this is appropriate, you access the superclass version of a
method, property, or subscript by using the `super`{.code-voice} prefix:

-   An overridden method named `someMethod()`{.code-voice} can call the
    superclass version of `someMethod()`{.code-voice} by calling
    `super.someMethod()`{.code-voice} within the overriding
    method implementation.

-   An overridden property called `someProperty`{.code-voice} can access
    the superclass version of `someProperty`{.code-voice} as
    `super.someProperty`{.code-voice} within the overriding getter or
    setter implementation.

-   An overridden subscript for `someIndex`{.code-voice} can access the
    superclass version of the same subscript as
    `super[someIndex]`{.code-voice} from within the overriding
    subscript implementation.

</div>

<div class="section section">

[‌](){#TP40016643-CH17-ID198}
### Overriding Methods {#overriding-methods .section-name}

You can override an inherited instance or type method to provide a
tailored or alternative implementation of the method within your
subclass.

The following example defines a new subclass of `Vehicle`{.code-voice}
called `Train`{.code-voice}, which overrides the
`makeNoise()`{.code-voice} method that `Train`{.code-voice} inherits
from `Vehicle`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `class`{.code-voice} `Train`{.vc}: `Vehicle`{.n} {
2.  `    override`{.code-voice} `func`{.kt} `makeNoise`{.vc}() {
3.  `        print`{.code-voice}(`"Choo Choo"`{.s})
4.  `    }`{.code-voice}
5.  `}`{.code-voice}

</div>

</div>

</div>

If you create a new instance of `Train`{.code-voice} and call its
`makeNoise()`{.code-voice} method, you can see that the
`Train`{.code-voice} subclass version of the method is called:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `train`{.vc} = `Train`{.vc}()
2.  `train`{.code-voice}.`makeNoise`{.vc}()
3.  `// prints "Choo Choo"`{.code-voice}

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH17-ID199}
### Overriding Properties {#overriding-properties .section-name}

You can override an inherited instance or type property to provide your
own custom getter and setter for that property, or to add property
observers to enable the overriding property to observe when the
underlying property value changes.

<div class="section section">

[‌](){#TP40016643-CH17-ID200}
### Overriding Property Getters and Setters {#overriding-property-getters-and-setters .section-name}

You can provide a custom getter (and setter, if appropriate) to override
*any* inherited property, regardless of whether the inherited property
is implemented as a stored or computed property at source. The stored or
computed nature of an inherited property is not known by a subclass—it
only knows that the inherited property has a certain name and type. You
must always state both the name and the type of the property you are
overriding, to enable the compiler to check that your override matches a
superclass property with the same name and type.

You can present an inherited read-only property as a read-write property
by providing both a getter and a setter in your subclass property
override. You cannot, however, present an inherited read-write property
as a read-only property.

<div class="note">

Note

If you provide a setter as part of a property override, you must also
provide a getter for that override. If you don’t want to modify the
inherited property’s value within the overriding getter, you can simply
pass through the inherited value by returning
`super.someProperty`{.code-voice} from the getter, where
`someProperty`{.code-voice} is the name of the property you are
overriding.

</div>

The following example defines a new class called `Car`{.code-voice},
which is a subclass of `Vehicle`{.code-voice}. The `Car`{.code-voice}
class introduces a new stored property called `gear`{.code-voice}, with
a default integer value of `1`{.code-voice}. The `Car`{.code-voice}
class also overrides the `description`{.code-voice} property it inherits
from `Vehicle`{.code-voice}, to provide a custom description that
includes the current gear:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `class`{.code-voice} `Car`{.vc}: `Vehicle`{.n} {
2.  `    var`{.code-voice} `gear`{.vc} = `1`{.m}
3.  `    override`{.code-voice} `var`{.kt} `description`{.vc}:
    `String`{.n} {
4.  `        return`{.code-voice} `super`{.kt}.`description`{.vc} +
    `" in gear `{.s}\\(`gear`{.vc})`"`{.s}
5.  `    }`{.code-voice}
6.  `}`{.code-voice}

</div>

</div>

</div>

The override of the `description`{.code-voice} property starts by
calling `super.description`{.code-voice}, which returns the
`Vehicle`{.code-voice} class’s `description`{.code-voice} property. The
`Car`{.code-voice} class’s version of `description`{.code-voice} then
adds some extra text onto the end of this description to provide
information about the current gear.

If you create an instance of the `Car`{.code-voice} class and set its
`gear`{.code-voice} and `currentSpeed`{.code-voice} properties, you can
see that its `description`{.code-voice} property returns the tailored
description defined within the `Car`{.code-voice} class:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `car`{.vc} = `Car`{.vc}()
2.  `car`{.code-voice}.`currentSpeed`{.vc} = `25.0`{.m}
3.  `car`{.code-voice}.`gear`{.vc} = `3`{.m}
4.  `print`{.code-voice}(`"Car: `{.s}\\(`car`{.vc}.`description`{.vc})`"`{.s})
5.  `// Car: traveling at 25.0 miles per hour in gear 3`{.code-voice}

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH17-ID201}
### Overriding Property Observers {#overriding-property-observers .section-name}

You can use property overriding to add property observers to an
inherited property. This enables you to be notified when the value of an
inherited property changes, regardless of how that property was
originally implemented. For more information on property observers, see
[Property Observers](Properties.md#TP40016643-CH14-ID262).

<div class="note">

Note

You cannot add property observers to inherited constant stored
properties or inherited read-only computed properties. The value of
these properties cannot be set, and so it is not appropriate to provide
a `willSet`{.code-voice} or `didSet`{.code-voice} implementation as part
of an override.

Note also that you cannot provide both an overriding setter and an
overriding property observer for the same property. If you want to
observe changes to a property’s value, and you are already providing a
custom setter for that property, you can simply observe any value
changes from within the custom setter.

</div>

The following example defines a new class called
`AutomaticCar`{.code-voice}, which is a subclass of `Car`{.code-voice}.
The `AutomaticCar`{.code-voice} class represents a car with an automatic
gearbox, which automatically selects an appropriate gear to use based on
the current speed:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `class`{.code-voice} `AutomaticCar`{.vc}: `Car`{.n} {
2.  `    override`{.code-voice} `var`{.kt} `currentSpeed`{.vc}:
    `Double`{.n} {
3.  `        didSet`{.code-voice} {
4.  `            gear`{.code-voice} = `Int`{.vc}(`currentSpeed`{.vc} /
    `10.0`{.m}) + `1`{.m}
5.  `        }`{.code-voice}
6.  `    }`{.code-voice}
7.  `}`{.code-voice}

</div>

</div>

</div>

Whenever you set the `currentSpeed`{.code-voice} property of an
`AutomaticCar`{.code-voice} instance, the property’s
`didSet`{.code-voice} observer sets the instance’s `gear`{.code-voice}
property to an appropriate choice of gear for the new speed.
Specifically, the property observer chooses a gear that is the new
`currentSpeed`{.code-voice} value divided by `10`{.code-voice}, rounded
down to the nearest integer, plus `1`{.code-voice}. A speed of
`35.0`{.code-voice} produces a gear of `4`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `let`{.code-voice} `automatic`{.vc} = `AutomaticCar`{.vc}()
2.  `automatic`{.code-voice}.`currentSpeed`{.vc} = `35.0`{.m}
3.  `print`{.code-voice}(`"AutomaticCar: `{.s}\\(`automatic`{.vc}.`description`{.vc})`"`{.s})
4.  `// AutomaticCar: traveling at 35.0 miles per hour in gear 4`{.code-voice}

</div>

</div>

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH17-ID202}
### Preventing Overrides {#preventing-overrides .section-name}

You can prevent a method, property, or subscript from being overridden
by marking it as *final*. Do this by writing the `final`{.code-voice}
modifier before the method, property, or subscript’s introducer keyword
(such as `final var`{.code-voice}, `final func`{.code-voice},
`final class func`{.code-voice}, and `final subscript`{.code-voice}).

Any attempt to override a final method, property, or subscript in a
subclass is reported as a compile-time error. Methods, properties, or
subscripts that you add to a class in an extension can also be marked as
final within the extension’s definition.

You can mark an entire class as final by writing the
`final`{.code-voice} modifier before the `class`{.code-voice} keyword in
its class definition (`final class`{.code-voice}). Any attempt to
subclass a final class is reported as a compile-time error.

</div>

</div>

</div>
