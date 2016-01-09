



[‌](){#TP40016643-CH14}[‌](){#TP40016643-CH14-ID254}
Properties {#properties .chapter-name}
----------



*Properties* associate values with a particular class, structure, or enumeration. Stored properties store constant and variable values as part of an instance, whereas computed properties calculate (rather than store) a value. Computed properties are provided by classes, structures, and enumerations. Stored properties are provided only by classes and structures.

Stored and computed properties are usually associated with instances of a particular type. However, properties can also be associated with the type itself. Such properties are known as type properties.

In addition, you can define property observers to monitor changes in a property’s value, which you can respond to with custom actions. Property observers can be added to stored properties you define yourself, and also to properties that a subclass inherits from its superclass.





[‌](){#TP40016643-CH14-ID255}
### Stored Properties {#stored-properties .section-name}

In its simplest form, a stored property is a constant or variable that is stored as part of an instance of a particular class or structure. Stored properties can be either *variable stored properties* (introduced by the `var`{.code-voice} keyword) or *constant stored properties* (introduced by the `let`{.code-voice} keyword).

You can provide a default value for a stored property as part of its definition, as described in [Default Property Values](Initialization.md#TP40016643-CH18-ID206). You can also set and modify the initial value for a stored property during initialization. This is true even for constant stored properties, as described in [Assigning Constant Properties During Initialization](Initialization.md#TP40016643-CH18-ID212).

The example below defines a structure called `FixedLengthRange`{.code-voice}, which describes a range of integers whose range length cannot be changed once it is created:







1.  `struct`{.code-voice} `FixedLengthRange`{.vc} {
2.  `    var`{.code-voice} `firstValue`{.vc}: `Int`{.n}
3.  `    let`{.code-voice} `length`{.vc}: `Int`{.n}
4.  `}`{.code-voice}
5.  `var`{.code-voice} `rangeOfThreeItems`{.vc} = `FixedLengthRange`{.vc}(`firstValue`{.vc}: `0`{.m}, `length`{.vc}: `3`{.m})
6.  `// the range represents integer values 0, 1, and 2`{.code-voice}
7.  `rangeOfThreeItems`{.code-voice}.`firstValue`{.vc} = `6`{.m}
8.  `// the range now represents integer values 6, 7, and 8`{.code-voice}







Instances of `FixedLengthRange`{.code-voice} have a variable stored property called `firstValue`{.code-voice} and a constant stored property called `length`{.code-voice}. In the example above, `length`{.code-voice} is initialized when the new range is created and cannot be changed thereafter, because it is a constant property.



[‌](){#TP40016643-CH14-ID256}
### Stored Properties of Constant Structure Instances {#stored-properties-of-constant-structure-instances .section-name}

If you create an instance of a structure and assign that instance to a constant, you cannot modify the instance’s properties, even if they were declared as variable properties:







1.  `let`{.code-voice} `rangeOfFourItems`{.vc} = `FixedLengthRange`{.vc}(`firstValue`{.vc}: `0`{.m}, `length`{.vc}: `4`{.m})
2.  `// this range represents integer values 0, 1, 2, and 3`{.code-voice}
3.  `rangeOfFourItems`{.code-voice}.`firstValue`{.vc} = `6`{.m}
4.  `// this will report an error, even though firstValue is a variable property`{.code-voice}







Because `rangeOfFourItems`{.code-voice} is declared as a constant (with the `let`{.code-voice} keyword), it is not possible to change its `firstValue`{.code-voice} property, even though `firstValue`{.code-voice} is a variable property.

This behavior is due to structures being *value types*. When an instance of a value type is marked as a constant, so are all of its properties.

The same is not true for classes, which are *reference types*. If you assign an instance of a reference type to a constant, you can still change that instance’s variable properties.





[‌](){#TP40016643-CH14-ID257}
### Lazy Stored Properties {#lazy-stored-properties .section-name}

A *lazy stored property* is a property whose initial value is not calculated until the first time it is used. You indicate a lazy stored property by writing the `lazy`{.code-voice} modifier before its declaration.



Note

You must always declare a lazy property as a variable (with the `var`{.code-voice} keyword), because its initial value might not be retrieved until after instance initialization completes. Constant properties must always have a value *before* initialization completes, and therefore cannot be declared as lazy.



Lazy properties are useful when the initial value for a property is dependent on outside factors whose values are not known until after an instance’s initialization is complete. Lazy properties are also useful when the initial value for a property requires complex or computationally expensive setup that should not be performed unless or until it is needed.

The example below uses a lazy stored property to avoid unnecessary initialization of a complex class. This example defines two classes called `DataImporter`{.code-voice} and `DataManager`{.code-voice}, neither of which is shown in full:







1.  `class`{.code-voice} `DataImporter`{.vc} {
2.  `    /*`{.code-voice}
3.  `    DataImporter is a class to import data from an external file.`{.code-voice}
4.  `    The class is assumed to take a non-trivial amount of time to initialize.`{.code-voice}
5.  `    */`{.code-voice}
6.  `    var`{.code-voice} `fileName`{.vc} = `"data.txt"`{.s}
7.  `    // the DataImporter class would provide data importing functionality here`{.code-voice}
8.  `}`{.code-voice}
9.  ` `{.code-voice}
10. `class`{.code-voice} `DataManager`{.vc} {
11. `    lazy`{.code-voice} `var`{.kt} `importer`{.vc} = `DataImporter`{.vc}()
12. `    var`{.code-voice} `data`{.vc} = \[`String`{.vc}\]()
13. `    // the DataManager class would provide data management functionality here`{.code-voice}
14. `}`{.code-voice}
15. ` `{.code-voice}
16. `let`{.code-voice} `manager`{.vc} = `DataManager`{.vc}()
17. `manager`{.code-voice}.`data`{.vc}.`append`{.vc}(`"Some data"`{.s})
18. `manager`{.code-voice}.`data`{.vc}.`append`{.vc}(`"Some more data"`{.s})
19. `// the DataImporter instance for the importer property has not yet been created`{.code-voice}







The `DataManager`{.code-voice} class has a stored property called `data`{.code-voice}, which is initialized with a new, empty array of `String`{.code-voice} values. Although the rest of its functionality is not shown, the purpose of this `DataManager`{.code-voice} class is to manage and provide access to this array of `String`{.code-voice} data.

Part of the functionality of the `DataManager`{.code-voice} class is the ability to import data from a file. This functionality is provided by the `DataImporter`{.code-voice} class, which is assumed to take a non-trivial amount of time to initialize. This might be because a `DataImporter`{.code-voice} instance needs to open a file and read its contents into memory when the `DataImporter`{.code-voice} instance is initialized.

It is possible for a `DataManager`{.code-voice} instance to manage its data without ever importing data from a file, so there is no need to create a new `DataImporter`{.code-voice} instance when the `DataManager`{.code-voice} itself is created. Instead, it makes more sense to create the `DataImporter`{.code-voice} instance if and when it is first used.

Because it is marked with the `lazy`{.code-voice} modifier, the `DataImporter`{.code-voice} instance for the `importer`{.code-voice} property is only created when the `importer`{.code-voice} property is first accessed, such as when its `fileName`{.code-voice} property is queried:







1.  `print`{.code-voice}(`manager`{.vc}.`importer`{.vc}.`fileName`{.vc})
2.  `// the DataImporter instance for the importer property has now been created`{.code-voice}
3.  `// prints "data.txt"`{.code-voice}









Note

If a property marked with the `lazy`{.code-voice} modifier is accessed by multiple threads simultaneously and the property has not yet been initialized, there is no guarantee that the property will be initialized only once.







[‌](){#TP40016643-CH14-ID258}
### Stored Properties and Instance Variables {#stored-properties-and-instance-variables .section-name}

If you have experience with Objective-C, you may know that it provides *two* ways to store values and references as part of a class instance. In addition to properties, you can use instance variables as a backing store for the values stored in a property.

Swift unifies these concepts into a single property declaration. A Swift property does not have a corresponding instance variable, and the backing store for a property is not accessed directly. This approach avoids confusion about how the value is accessed in different contexts and simplifies the property’s declaration into a single, definitive statement. All information about the property—including its name, type, and memory management characteristics—is defined in a single location as part of the type’s definition.







[‌](){#TP40016643-CH14-ID259}
### Computed Properties {#computed-properties .section-name}

In addition to stored properties, classes, structures, and enumerations can define *computed properties*, which do not actually store a value. Instead, they provide a getter and an optional setter to retrieve and set other properties and values indirectly.







1.  `struct`{.code-voice} `Point`{.vc} {
2.  `    var`{.code-voice} `x`{.vc} = `0.0`{.m}, `y`{.vc} = `0.0`{.m}
3.  `}`{.code-voice}
4.  `struct`{.code-voice} `Size`{.vc} {
5.  `    var`{.code-voice} `width`{.vc} = `0.0`{.m}, `height`{.vc} = `0.0`{.m}
6.  `}`{.code-voice}
7.  `struct`{.code-voice} `Rect`{.vc} {
8.  `    var`{.code-voice} `origin`{.vc} = `Point`{.vc}()
9.  `    var`{.code-voice} `size`{.vc} = `Size`{.vc}()
10. `    var`{.code-voice} `center`{.vc}: `Point`{.n} {
11. `        get`{.code-voice} {
12. `            let`{.code-voice} `centerX`{.vc} = `origin`{.vc}.`x`{.vc} + (`size`{.vc}.`width`{.vc} / `2`{.m})
13. `            let`{.code-voice} `centerY`{.vc} = `origin`{.vc}.`y`{.vc} + (`size`{.vc}.`height`{.vc} / `2`{.m})
14. `            return`{.code-voice} `Point`{.vc}(`x`{.vc}: `centerX`{.vc}, `y`{.vc}: `centerY`{.vc})
15. `        }`{.code-voice}
16. `        set`{.code-voice}(`newCenter`{.vc}) {
17. `            origin`{.code-voice}.`x`{.vc} = `newCenter`{.vc}.`x`{.vc} - (`size`{.vc}.`width`{.vc} / `2`{.m})
18. `            origin`{.code-voice}.`y`{.vc} = `newCenter`{.vc}.`y`{.vc} - (`size`{.vc}.`height`{.vc} / `2`{.m})
19. `        }`{.code-voice}
20. `    }`{.code-voice}
21. `}`{.code-voice}
22. `var`{.code-voice} `square`{.vc} = `Rect`{.vc}(`origin`{.vc}: `Point`{.vc}(`x`{.vc}: `0.0`{.m}, `y`{.vc}: `0.0`{.m}),
23. `    size`{.code-voice}: `Size`{.vc}(`width`{.vc}: `10.0`{.m}, `height`{.vc}: `10.0`{.m}))
24. `let`{.code-voice} `initialSquareCenter`{.vc} = `square`{.vc}.`center`{.vc}
25. `square`{.code-voice}.`center`{.vc} = `Point`{.vc}(`x`{.vc}: `15.0`{.m}, `y`{.vc}: `15.0`{.m})
26. `print`{.code-voice}(`"square.origin is now at (`{.s}\\(`square`{.vc}.`origin`{.vc}.`x`{.vc})`, `{.s}\\(`square`{.vc}.`origin`{.vc}.`y`{.vc})`)"`{.s})
27. `// prints "square.origin is now at (10.0, 10.0)"`{.code-voice}







This example defines three structures for working with geometric shapes:

-   `Point`{.code-voice} encapsulates an `(x, y)`{.code-voice} coordinate.

-   `Size`{.code-voice} encapsulates a `width`{.code-voice} and a `height`{.code-voice}.

-   `Rect`{.code-voice} defines a rectangle by an origin point and a size.

The `Rect`{.code-voice} structure also provides a computed property called `center`{.code-voice}. The current center position of a `Rect`{.code-voice} can always be determined from its `origin`{.code-voice} and `size`{.code-voice}, and so you don’t need to store the center point as an explicit `Point`{.code-voice} value. Instead, `Rect`{.code-voice} defines a custom getter and setter for a computed variable called `center`{.code-voice}, to enable you to work with the rectangle’s `center`{.code-voice} as if it were a real stored property.

The preceding example creates a new `Rect`{.code-voice} variable called `square`{.code-voice}. The `square`{.code-voice} variable is initialized with an origin point of `(0, 0)`{.code-voice}, and a width and height of `10`{.code-voice}. This square is represented by the blue square in the diagram below.

The `square`{.code-voice} variable’s `center`{.code-voice} property is then accessed through dot syntax (`square.center`{.code-voice}), which causes the getter for `center`{.code-voice} to be called, to retrieve the current property value. Rather than returning an existing value, the getter actually calculates and returns a new `Point`{.code-voice} to represent the center of the square. As can be seen above, the getter correctly returns a center point of `(5, 5)`{.code-voice}.

The `center`{.code-voice} property is then set to a new value of `(15, 15)`{.code-voice}, which moves the square up and to the right, to the new position shown by the orange square in the diagram below. Setting the `center`{.code-voice} property calls the setter for `center`{.code-voice}, which modifies the `x`{.code-voice} and `y`{.code-voice} values of the stored `origin`{.code-voice} property, and moves the square to its new position.




![image: ../Art/computedProperties\_2x.png](Art/computedProperties_2x.png){width="388" height="387"}





[‌](){#TP40016643-CH14-ID260}
### Shorthand Setter Declaration {#shorthand-setter-declaration .section-name}

If a computed property’s setter does not define a name for the new value to be set, a default name of `newValue`{.code-voice} is used. Here’s an alternative version of the `Rect`{.code-voice} structure, which takes advantage of this shorthand notation:







1.  `struct`{.code-voice} `AlternativeRect`{.vc} {
2.  `    var`{.code-voice} `origin`{.vc} = `Point`{.vc}()
3.  `    var`{.code-voice} `size`{.vc} = `Size`{.vc}()
4.  `    var`{.code-voice} `center`{.vc}: `Point`{.n} {
5.  `        get`{.code-voice} {
6.  `            let`{.code-voice} `centerX`{.vc} = `origin`{.vc}.`x`{.vc} + (`size`{.vc}.`width`{.vc} / `2`{.m})
7.  `            let`{.code-voice} `centerY`{.vc} = `origin`{.vc}.`y`{.vc} + (`size`{.vc}.`height`{.vc} / `2`{.m})
8.  `            return`{.code-voice} `Point`{.vc}(`x`{.vc}: `centerX`{.vc}, `y`{.vc}: `centerY`{.vc})
9.  `        }`{.code-voice}
10. `        set`{.code-voice} {
11. `            origin`{.code-voice}.`x`{.vc} = `newValue`{.vc}.`x`{.vc} - (`size`{.vc}.`width`{.vc} / `2`{.m})
12. `            origin`{.code-voice}.`y`{.vc} = `newValue`{.vc}.`y`{.vc} - (`size`{.vc}.`height`{.vc} / `2`{.m})
13. `        }`{.code-voice}
14. `    }`{.code-voice}
15. `}`{.code-voice}











[‌](){#TP40016643-CH14-ID261}
### Read-Only Computed Properties {#read-only-computed-properties .section-name}

A computed property with a getter but no setter is known as a *read-only computed property*. A read-only computed property always returns a value, and can be accessed through dot syntax, but cannot be set to a different value.



Note

You must declare computed properties—including read-only computed properties—as variable properties with the `var`{.code-voice} keyword, because their value is not fixed. The `let`{.code-voice} keyword is only used for constant properties, to indicate that their values cannot be changed once they are set as part of instance initialization.



You can simplify the declaration of a read-only computed property by removing the `get`{.code-voice} keyword and its braces:







1.  `struct`{.code-voice} `Cuboid`{.vc} {
2.  `    var`{.code-voice} `width`{.vc} = `0.0`{.m}, `height`{.vc} = `0.0`{.m}, `depth`{.vc} = `0.0`{.m}
3.  `    var`{.code-voice} `volume`{.vc}: `Double`{.n} {
4.  `        return`{.code-voice} `width`{.vc} \* `height`{.vc} \* `depth`{.vc}
5.  `    }`{.code-voice}
6.  `}`{.code-voice}
7.  `let`{.code-voice} `fourByFiveByTwo`{.vc} = `Cuboid`{.vc}(`width`{.vc}: `4.0`{.m}, `height`{.vc}: `5.0`{.m}, `depth`{.vc}: `2.0`{.m})
8.  `print`{.code-voice}(`"the volume of fourByFiveByTwo is `{.s}\\(`fourByFiveByTwo`{.vc}.`volume`{.vc})`"`{.s})
9.  `// prints "the volume of fourByFiveByTwo is 40.0"`{.code-voice}







This example defines a new structure called `Cuboid`{.code-voice}, which represents a 3D rectangular box with `width`{.code-voice}, `height`{.code-voice}, and `depth`{.code-voice} properties. This structure also has a read-only computed property called `volume`{.code-voice}, which calculates and returns the current volume of the cuboid. It doesn’t make sense for `volume`{.code-voice} to be settable, because it would be ambiguous as to which values of `width`{.code-voice}, `height`{.code-voice}, and `depth`{.code-voice} should be used for a particular `volume`{.code-voice} value. Nonetheless, it is useful for a `Cuboid`{.code-voice} to provide a read-only computed property to enable external users to discover its current calculated volume.







[‌](){#TP40016643-CH14-ID262}
### Property Observers {#property-observers .section-name}

*Property observers* observe and respond to changes in a property’s value. Property observers are called every time a property’s value is set, even if the new value is the same as the property’s current value.

You can add property observers to any stored properties you define, apart from lazy stored properties. You can also add property observers to any inherited property (whether stored or computed) by overriding the property within a subclass. Property overriding is described in [Overriding](Inheritance.md#TP40016643-CH17-ID196).



Note

You don’t need to define property observers for non-overridden computed properties, because you can observe and respond to changes to their value in the computed property’s setter.



You have the option to define either or both of these observers on a property:

-   `willSet`{.code-voice} is called just before the value is stored.

-   `didSet`{.code-voice} is called immediately after the new value is stored.

If you implement a `willSet`{.code-voice} observer, it is passed the new property value as a constant parameter. You can specify a name for this parameter as part of your `willSet`{.code-voice} implementation. If you don’t write the parameter name and parentheses within your implementation, the parameter is made available with a default parameter name of `newValue`{.code-voice}.

Similarly, if you implement a `didSet`{.code-voice} observer, it will be passed a constant parameter containing the old property value. You can name the parameter or use the default parameter name of `oldValue`{.code-voice}.



Note

The `willSet`{.code-voice} and `didSet`{.code-voice} observers of superclass properties are called when a property is set in a subclass initializer.

For more information about initializer delegation, see [Initializer Delegation for Value Types](Initialization.md#TP40016643-CH18-ID215) and [Initializer Delegation for Class Types](Initialization.md#TP40016643-CH18-ID219).



Here’s an example of `willSet`{.code-voice} and `didSet`{.code-voice} in action. The example below defines a new class called `StepCounter`{.code-voice}, which tracks the total number of steps that a person takes while walking. This class might be used with input data from a pedometer or other step counter to keep track of a person’s exercise during their daily routine.







1.  `class`{.code-voice} `StepCounter`{.vc} {
2.  `    var`{.code-voice} `totalSteps`{.vc}: `Int`{.n} = `0`{.m} {
3.  `        willSet`{.code-voice}(`newTotalSteps`{.vc}) {
4.  `            print`{.code-voice}(`"About to set totalSteps to `{.s}\\(`newTotalSteps`{.vc})`"`{.s})
5.  `        }`{.code-voice}
6.  `        didSet`{.code-voice} {
7.  `            if`{.code-voice} `totalSteps`{.vc} &gt; `oldValue`{.vc} {
8.  `                print`{.code-voice}(`"Added `{.s}\\(`totalSteps`{.vc} - `oldValue`{.vc})` steps"`{.s})
9.  `            }`{.code-voice}
10. `        }`{.code-voice}
11. `    }`{.code-voice}
12. `}`{.code-voice}
13. `let`{.code-voice} `stepCounter`{.vc} = `StepCounter`{.vc}()
14. `stepCounter`{.code-voice}.`totalSteps`{.vc} = `200`{.m}
15. `// About to set totalSteps to 200`{.code-voice}
16. `// Added 200 steps`{.code-voice}
17. `stepCounter`{.code-voice}.`totalSteps`{.vc} = `360`{.m}
18. `// About to set totalSteps to 360`{.code-voice}
19. `// Added 160 steps`{.code-voice}
20. `stepCounter`{.code-voice}.`totalSteps`{.vc} = `896`{.m}
21. `// About to set totalSteps to 896`{.code-voice}
22. `// Added 536 steps`{.code-voice}







The `StepCounter`{.code-voice} class declares a `totalSteps`{.code-voice} property of type `Int`{.code-voice}. This is a stored property with `willSet`{.code-voice} and `didSet`{.code-voice} observers.

The `willSet`{.code-voice} and `didSet`{.code-voice} observers for `totalSteps`{.code-voice} are called whenever the property is assigned a new value. This is true even if the new value is the same as the current value.

This example’s `willSet`{.code-voice} observer uses a custom parameter name of `newTotalSteps`{.code-voice} for the upcoming new value. In this example, it simply prints out the value that is about to be set.

The `didSet`{.code-voice} observer is called after the value of `totalSteps`{.code-voice} is updated. It compares the new value of `totalSteps`{.code-voice} against the old value. If the total number of steps has increased, a message is printed to indicate how many new steps have been taken. The `didSet`{.code-voice} observer does not provide a custom parameter name for the old value, and the default name of `oldValue`{.code-voice} is used instead.



Note

If you assign a value to a property within its own `didSet`{.code-voice} observer, the new value that you assign will replace the one that was just set.







[‌](){#TP40016643-CH14-ID263}
### Global and Local Variables {#global-and-local-variables .section-name}

The capabilities described above for computing and observing properties are also available to *global variables* and *local variables*. Global variables are variables that are defined outside of any function, method, closure, or type context. Local variables are variables that are defined within a function, method, or closure context.

The global and local variables you have encountered in previous chapters have all been *stored variables*. Stored variables, like stored properties, provide storage for a value of a certain type and allow that value to be set and retrieved.

However, you can also define *computed variables* and define observers for stored variables, in either a global or local scope. Computed variables calculate rather than store a value, and are written in the same way as computed properties.



Note

Global constants and variables are always computed lazily, in a similar manner to [Lazy Stored Properties](Properties.md#TP40016643-CH14-ID257). Unlike lazy stored properties, global constants and variables do not need to be marked with the `lazy`{.code-voice} modifier.

Local constants and variables are never computed lazily.







[‌](){#TP40016643-CH14-ID264}
### Type Properties {#type-properties .section-name}

Instance properties are properties that belong to an instance of a particular type. Every time you create a new instance of that type, it has its own set of property values, separate from any other instance.

You can also define properties that belong to the type itself, not to any one instance of that type. There will only ever be one copy of these properties, no matter how many instances of that type you create. These kinds of properties are called *type properties*.

Type properties are useful for defining values that are universal to *all* instances of a particular type, such as a constant property that all instances can use (like a static constant in C), or a variable property that stores a value that is global to all instances of that type (like a static variable in C).

Stored type properties can be variables or constants. Computed type properties are always declared as variable properties, in the same way as computed instance properties.



Note

Unlike stored instance properties, you must always give stored type properties a default value. This is because the type itself does not have an initializer that can assign a value to a stored type property at initialization time.

Stored type properties are lazily initialized on their first access. They are guaranteed to be initialized only once, even when accessed by multiple threads simultaneously, and they do not need to be marked with the `lazy`{.code-voice} modifier.





[‌](){#TP40016643-CH14-ID265}
### Type Property Syntax {#type-property-syntax .section-name}

In C and Objective-C, you define static constants and variables associated with a type as *global* static variables. In Swift, however, type properties are written as part of the type’s definition, within the type’s outer curly braces, and each type property is explicitly scoped to the type it supports.

You define type properties with the `static`{.code-voice} keyword. For computed type properties for class types, you can use the `class`{.code-voice} keyword instead to allow subclasses to override the superclass’s implementation. The example below shows the syntax for stored and computed type properties:







1.  `struct`{.code-voice} `SomeStructure`{.vc} {
2.  `    static`{.code-voice} `var`{.kt} `storedTypeProperty`{.vc} = `"Some value."`{.s}
3.  `    static`{.code-voice} `var`{.kt} `computedTypeProperty`{.vc}: `Int`{.n} {
4.  `        return`{.code-voice} `1`{.m}
5.  `    }`{.code-voice}
6.  `}`{.code-voice}
7.  `enum`{.code-voice} `SomeEnumeration`{.vc} {
8.  `    static`{.code-voice} `var`{.kt} `storedTypeProperty`{.vc} = `"Some value."`{.s}
9.  `    static`{.code-voice} `var`{.kt} `computedTypeProperty`{.vc}: `Int`{.n} {
10. `        return`{.code-voice} `6`{.m}
11. `    }`{.code-voice}
12. `}`{.code-voice}
13. `class`{.code-voice} `SomeClass`{.vc} {
14. `    static`{.code-voice} `var`{.kt} `storedTypeProperty`{.vc} = `"Some value."`{.s}
15. `    static`{.code-voice} `var`{.kt} `computedTypeProperty`{.vc}: `Int`{.n} {
16. `        return`{.code-voice} `27`{.m}
17. `    }`{.code-voice}
18. `    class`{.code-voice} `var`{.kt} `overrideableComputedTypeProperty`{.vc}: `Int`{.n} {
19. `        return`{.code-voice} `107`{.m}
20. `    }`{.code-voice}
21. `}`{.code-voice}









Note

The computed type property examples above are for read-only computed type properties, but you can also define read-write computed type properties with the same syntax as for computed instance properties.







[‌](){#TP40016643-CH14-ID266}
### Querying and Setting Type Properties {#querying-and-setting-type-properties .section-name}

Type properties are queried and set with dot syntax, just like instance properties. However, type properties are queried and set on the *type*, not on an instance of that type. For example:







1.  `print`{.code-voice}(`SomeStructure`{.vc}.`storedTypeProperty`{.vc})
2.  `// prints "Some value."`{.code-voice}
3.  `SomeStructure`{.code-voice}.`storedTypeProperty`{.vc} = `"Another value."`{.s}
4.  `print`{.code-voice}(`SomeStructure`{.vc}.`storedTypeProperty`{.vc})
5.  `// prints "Another value."`{.code-voice}
6.  `print`{.code-voice}(`SomeEnumeration`{.vc}.`computedTypeProperty`{.vc})
7.  `// prints "6"`{.code-voice}
8.  `print`{.code-voice}(`SomeClass`{.vc}.`computedTypeProperty`{.vc})
9.  `// prints "27"`{.code-voice}







The examples that follow use two stored type properties as part of a structure that models an audio level meter for a number of audio channels. Each channel has an integer audio level between `0`{.code-voice} and `10`{.code-voice} inclusive.

The figure below illustrates how two of these audio channels can be combined to model a stereo audio level meter. When a channel’s audio level is `0`{.code-voice}, none of the lights for that channel are lit. When the audio level is `10`{.code-voice}, all of the lights for that channel are lit. In this figure, the left channel has a current level of `9`{.code-voice}, and the right channel has a current level of `7`{.code-voice}:




![image: ../Art/staticPropertiesVUMeter\_2x.png](Art/staticPropertiesVUMeter_2x.png){width="243" height="357"}



The audio channels described above are represented by instances of the `AudioChannel`{.code-voice} structure:







1.  `struct`{.code-voice} `AudioChannel`{.vc} {
2.  `    static`{.code-voice} `let`{.kt} `thresholdLevel`{.vc} = `10`{.m}
3.  `    static`{.code-voice} `var`{.kt} `maxInputLevelForAllChannels`{.vc} = `0`{.m}
4.  `    var`{.code-voice} `currentLevel`{.vc}: `Int`{.n} = `0`{.m} {
5.  `        didSet`{.code-voice} {
6.  `            if`{.code-voice} `currentLevel`{.vc} &gt; `AudioChannel`{.vc}.`thresholdLevel`{.vc} {
7.  `                // cap the new audio level to the threshold level`{.code-voice}
8.  `                currentLevel`{.code-voice} = `AudioChannel`{.vc}.`thresholdLevel`{.vc}
9.  `            }`{.code-voice}
10. `            if`{.code-voice} `currentLevel`{.vc} &gt; `AudioChannel`{.vc}.`maxInputLevelForAllChannels`{.vc} {
11. `                // store this as the new overall maximum input level`{.code-voice}
12. `                AudioChannel`{.code-voice}.`maxInputLevelForAllChannels`{.vc} = `currentLevel`{.vc}
13. `            }`{.code-voice}
14. `        }`{.code-voice}
15. `    }`{.code-voice}
16. `}`{.code-voice}







The `AudioChannel`{.code-voice} structure defines two stored type properties to support its functionality. The first, `thresholdLevel`{.code-voice}, defines the maximum threshold value an audio level can take. This is a constant value of `10`{.code-voice} for all `AudioChannel`{.code-voice} instances. If an audio signal comes in with a higher value than `10`{.code-voice}, it will be capped to this threshold value (as described below).

The second type property is a variable stored property called `maxInputLevelForAllChannels`{.code-voice}. This keeps track of the maximum input value that has been received by *any* `AudioChannel`{.code-voice} instance. It starts with an initial value of `0`{.code-voice}.

The `AudioChannel`{.code-voice} structure also defines a stored instance property called `currentLevel`{.code-voice}, which represents the channel’s current audio level on a scale of `0`{.code-voice} to `10`{.code-voice}.

The `currentLevel`{.code-voice} property has a `didSet`{.code-voice} property observer to check the value of `currentLevel`{.code-voice} whenever it is set. This observer performs two checks:

-   If the new value of `currentLevel`{.code-voice} is greater than the allowed `thresholdLevel`{.code-voice}, the property observer caps `currentLevel`{.code-voice} to `thresholdLevel`{.code-voice}.

-   If the new value of `currentLevel`{.code-voice} (after any capping) is higher than any value previously received by *any* `AudioChannel`{.code-voice} instance, the property observer stores the new `currentLevel`{.code-voice} value in the `maxInputLevelForAllChannels`{.code-voice} type property.



Note

In the first of these two checks, the `didSet`{.code-voice} observer sets `currentLevel`{.code-voice} to a different value. This does not, however, cause the observer to be called again.



You can use the `AudioChannel`{.code-voice} structure to create two new audio channels called `leftChannel`{.code-voice} and `rightChannel`{.code-voice}, to represent the audio levels of a stereo sound system:







1.  `var`{.code-voice} `leftChannel`{.vc} = `AudioChannel`{.vc}()
2.  `var`{.code-voice} `rightChannel`{.vc} = `AudioChannel`{.vc}()







If you set the `currentLevel`{.code-voice} of the *left* channel to `7`{.code-voice}, you can see that the `maxInputLevelForAllChannels`{.code-voice} type property is updated to equal `7`{.code-voice}:







1.  `leftChannel`{.code-voice}.`currentLevel`{.vc} = `7`{.m}
2.  `print`{.code-voice}(`leftChannel`{.vc}.`currentLevel`{.vc})
3.  `// prints "7"`{.code-voice}
4.  `print`{.code-voice}(`AudioChannel`{.vc}.`maxInputLevelForAllChannels`{.vc})
5.  `// prints "7"`{.code-voice}







If you try to set the `currentLevel`{.code-voice} of the *right* channel to `11`{.code-voice}, you can see that the right channel’s `currentLevel`{.code-voice} property is capped to the maximum value of `10`{.code-voice}, and the `maxInputLevelForAllChannels`{.code-voice} type property is updated to equal `10`{.code-voice}:







1.  `rightChannel`{.code-voice}.`currentLevel`{.vc} = `11`{.m}
2.  `print`{.code-voice}(`rightChannel`{.vc}.`currentLevel`{.vc})
3.  `// prints "10"`{.code-voice}
4.  `print`{.code-voice}(`AudioChannel`{.vc}.`maxInputLevelForAllChannels`{.vc})
5.  `// prints "10"`{.code-voice}














