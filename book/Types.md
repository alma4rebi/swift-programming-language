Types
-----

In Swift, there are two kinds of types: named types and compound types. A *named type* is a type that can be given a particular name when it is defined. Named types include classes, structures, enumerations, and protocols. For example, instances of a user-defined class named `MyClass` have the type `MyClass`. In addition to user-defined named types, the Swift standard library defines many commonly used named types, including those that represent arrays, dictionaries, and optional values.

Data types that are normally considered basic or primitive in other languages—such as types that represent numbers, characters, and strings—are actually named types, defined and implemented in the Swift standard library using structures. Because they are named types, you can extend their behavior to suit the needs of your program, using an extension declaration, discussed in [Extensions](Extensions.md) and [Extension Declaration](Declarations.md#TP40016643-CH34-ID378).

A *compound type* is a type without a name, defined in the Swift language itself. There are two compound types: function types and tuple types. A compound type may contain named types and other compound types. For instance, the tuple type `(Int, (Int, Int))` contains two elements: The first is the named type `Int`, and the second is another compound type `(Int, Int)`.

This chapter discusses the types defined in the Swift language itself and describes the type inference behavior of Swift.

Grammar of a type

<span class="syntax-def-name">
type

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[array-type](Types.md#array-type)
<span class="alternative">
<span class="syntactic-cat">[dictionary-type](Types.md#dictionary-type)
<span class="alternative">
<span class="syntactic-cat">[function-type](Types.md#function-type)
<span class="alternative">
<span class="syntactic-cat">[type-identifier](Types.md#type-identifier)
<span class="alternative">
<span class="syntactic-cat">[tuple-type](Types.md#tuple-type)
<span class="alternative">
<span class="syntactic-cat">[optional-type](Types.md#optional-type)
<span class="alternative">
<span class="syntactic-cat">[implicitly-unwrapped-optional-type](Types.md#implicitly-unwrapped-optional-type)
<span class="alternative">
<span class="syntactic-cat">[protocol-composition-type](Types.md#protocol-composition-type)
<span class="alternative">
<span class="syntactic-cat">[metatype-type](Types.md#metatype-type)

### Type Annotation

A *type annotation* explicitly specifies the type of a variable or expression. Type annotations begin with a colon (`:`) and end with a type, as the following examples show:

    let someTuple: (Double, Double) = (3.14159, 2.71828)
    func someFunction(a: Int) { /* ... */ }

In the first example, the expression `someTuple` is specified to have the tuple type `(Double, Double)`. In the second example, the parameter `a` to the function `someFunction` is specified to have the type `Int`.

Type annotations can contain an optional list of type attributes before the type.

Grammar of a type annotation

<span class="syntax-def-name">
type-annotation

<span class="arrow">
→
`:`<span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)~opt~<span class="syntactic-cat">[type](Types.md#type)

### Type Identifier

A type identifier refers to either a named type or a type alias of a named or compound type.

Most of the time, a type identifier directly refers to a named type with the same name as the identifier. For example, `Int` is a type identifier that directly refers to the named type `Int`, and the type identifier `Dictionary<String, Int>` directly refers to the named type `Dictionary<String, Int>`.

There are two cases in which a type identifier does not refer to a type with the same name. In the first case, a type identifier refers to a type alias of a named or compound type. For instance, in the example below, the use of `Point` in the type annotation refers to the tuple type `(Int, Int)`.

    typealias Point = (Int, Int)
    let origin: Point = (0, 0)

In the second case, a type identifier uses dot (`.`) syntax to refer to named types declared in other modules or nested within other types. For example, the type identifier in the following code references the named type `MyType` that is declared in the `ExampleModule` module.

    var someValue: ExampleModule.MyType

Grammar of a type identifier

<span class="syntax-def-name">
type-identifier

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[type-name](Types.md#type-name)<span class="optional"><span class="syntactic-cat">[generic-argument-clause](GenericParametersAndArguments.md#generic-argument-clause)~opt~
<span class="alternative">
<span class="syntactic-cat">[type-name](Types.md#type-name)<span class="optional"><span class="syntactic-cat">[generic-argument-clause](GenericParametersAndArguments.md#generic-argument-clause)~opt~`.`<span class="syntactic-cat">[type-identifier](Types.md#type-identifier)

<span class="syntax-def-name">
type-name

<span class="arrow">
→
<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)

### Tuple Type

A tuple type is a comma-separated list of zero or more types, enclosed in parentheses.

You can use a tuple type as the return type of a function to enable the function to return a single tuple containing multiple values. You can also name the elements of a tuple type and use those names to refer to the values of the individual elements. An element name consists of an identifier followed immediately by a colon (:). For an example that demonstrates both of these features, see [Functions with Multiple Return Values](Functions.md#TP40016643-CH10-ID164).

`Void` is a type alias for the empty tuple type, `()`. If there is only one element inside the parentheses, the type is simply the type of that element. For example, the type of `(Int)` is `Int`, not `(Int)`. As a result, you can name a tuple element only when the tuple type has two or more elements.

Grammar of a tuple type

<span class="syntax-def-name">
tuple-type

<span class="arrow">
→
`(`<span class="optional"><span class="syntactic-cat">[tuple-type-body](Types.md#tuple-type-body)~opt~`)`

<span class="syntax-def-name">
tuple-type-body

<span class="arrow">
→
<span class="syntactic-cat">[tuple-type-element-list](Types.md#tuple-type-element-list)<span class="optional">`...`~opt~

<span class="syntax-def-name">
tuple-type-element-list

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[tuple-type-element](Types.md#tuple-type-element)
<span class="alternative">
<span class="syntactic-cat">[tuple-type-element](Types.md#tuple-type-element)`,`<span class="syntactic-cat">[tuple-type-element-list](Types.md#tuple-type-element-list)

<span class="syntax-def-name">
tuple-type-element

<span class="arrow">
→
<span class="alternative">
<span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)~opt~<span class="optional">`inout`~opt~<span class="syntactic-cat">[type](Types.md#type)
<span class="alternative">
<span class="optional">`inout`~opt~<span class="syntactic-cat">[element-name](Types.md#element-name)<span class="syntactic-cat">[type-annotation](Types.md#type-annotation)

<span class="syntax-def-name">
element-name

<span class="arrow">
→
<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)

### Function Type

A function type represents the type of a function, method, or closure and consists of a parameter and return type separated by an arrow (`->`):

-   ```
    parameter type -> return type
    ```

Because the *parameter type* and the *return type* can be a tuple type, function types support functions and methods that take multiple parameters and return multiple values.

A parameter declaration for a function type with a parameter type of `Void` can apply the `autoclosure` attribute to capture an implicit closure over a specified expression instead of the expression itself. This provides a syntactically convenient way to defer the evaluation of an expression until its value is used in the function body. For an example of an autoclosure function type parameter, see [Autoclosures](Closures.md#TP40016643-CH11-ID543).

A function type can have a variadic parameter in its *parameter type*. Syntactically, a variadic parameter consists of a base type name followed immediately by three dots (`...`), as in `Int...`. A variadic parameter is treated as an array that contains elements of the base type name. For instance, the variadic parameter `Int...` is treated as `[Int]`. For an example that uses a variadic parameter, see [Variadic Parameters](Functions.md#TP40016643-CH10-ID171).

To specify an in-out parameter, prefix the parameter type with the `inout` keyword. You can’t mark a variadic parameter or a return type with the `inout` keyword. In-out parameters are discussed in [In-Out Parameters](Functions.md#TP40016643-CH10-ID173).

If a function type includes more than a single arrow (`->`), the function types are grouped from right to left. For example, the function type `Int -> Int -> Int` is understood as `Int -> (Int -> Int)`—that is, a function that takes an `Int` and returns another function that takes and returns an `Int`.

Function types that can throw an error must be marked with the `throws` keyword, and function types that can rethrow an error must be marked with the `rethrows` keyword. The `throws` keyword is part of a function’s type, and nonthrowing functions are subtypes of throwing functions. As a result, you can use a nonthrowing function in the same places as a throwing one. Throwing and rethrowing functions are described in [Throwing Functions and Methods](Declarations.md#TP40016643-CH34-ID530) and [Rethrowing Functions and Methods](Declarations.md#TP40016643-CH34-ID531).

Grammar of a function type

<span class="syntax-def-name">
function-type

<span class="arrow">
→
<span class="syntactic-cat">[type](Types.md#type)<span class="optional">`throws`~opt~`->`<span class="syntactic-cat">[type](Types.md#type)

<span class="syntax-def-name">
function-type

<span class="arrow">
→
<span class="syntactic-cat">[type](Types.md#type)`rethrows``->`<span class="syntactic-cat">[type](Types.md#type)

### Array Type

The Swift language provides the following syntactic sugar for the Swift standard library `Array<Element>` type:

-   ```
    [type]
    ```

In other words, the following two declarations are equivalent:

    let someArray: Array<String> = \["Alex", "Brian", "Dave"\]
    let someArray: \[String\] = \["Alex", "Brian", "Dave"\]

In both cases, the constant `someArray` is declared as an array of strings. The elements of an array can be accessed through subscripting by specifying a valid index value in square brackets: `someArray[0]` refers to the element at index 0, `"Alex"`.

You can create multidimensional arrays by nesting pairs of square brackets, where the name of the base type of the elements is contained in the innermost pair of square brackets. For example, you can create a three-dimensional array of integers using three sets of square brackets:

    var array3D: \[\[\[Int\]\]\] = \[\[\[1, 2\], \[3, 4\]\], \[\[5, 6\], \[7, 8\]\]\]

When accessing the elements in a multidimensional array, the left-most subscript index refers to the element at that index in the outermost array. The next subscript index to the right refers to the element at that index in the array that’s nested one level in. And so on. This means that in the example above, `array3D[0]` refers to `[[1, 2], [3, 4]]`, `array3D[0][1]` refers to `[3, 4]`, and `array3D[0][1][1]` refers to the value 4.

For a detailed discussion of the Swift standard library `Array` type, see [Arrays](CollectionTypes.md#TP40016643-CH8-ID107).

Grammar of an array type

<span class="syntax-def-name">
array-type

<span class="arrow">
→
`[`<span class="syntactic-cat">[type](Types.md#type)`]`

### Dictionary Type

The Swift language provides the following syntactic sugar for the Swift standard library `Dictionary<Key, Value>` type:

-   ```
    [key type: value type]
    ```

In other words, the following two declarations are equivalent:

    let someDictionary: \[String: Int\] = \["Alex": 31, "Paul": 39\]
    let someDictionary: Dictionary<String, Int> = \["Alex": 31, "Paul": 39\]

In both cases, the constant `someDictionary` is declared as a dictionary with strings as keys and integers as values.

The values of a dictionary can be accessed through subscripting by specifying the corresponding key in square brackets: `someDictionary["Alex"]` refers to the value associated with the key `"Alex"`. The subscript returns an optional value of the dictionary’s value type. If the specified key isn’t contained in the dictionary, the subscript returns `nil`.

The key type of a dictionary must conform to the Swift standard library `Hashable` protocol.

For a detailed discussion of the Swift standard library `Dictionary` type, see [Dictionaries](CollectionTypes.md#TP40016643-CH8-ID113).

Grammar of a dictionary type

<span class="syntax-def-name">
dictionary-type

<span class="arrow">
→
`[`<span class="syntactic-cat">[type](Types.md#type)`:`<span class="syntactic-cat">[type](Types.md#type)`]`

### Optional Type

The Swift language defines the postfix `?` as syntactic sugar for the named type `Optional<Wrapped>`, which is defined in the Swift standard library. In other words, the following two declarations are equivalent:

    var optionalInteger: Int?
    var optionalInteger: Optional<Int>

In both cases, the variable `optionalInteger` is declared to have the type of an optional integer. Note that no whitespace may appear between the type and the `?`.

The type `Optional<Wrapped>` is an enumeration with two cases, `None` and `Some(Wrapped)`, which are used to represent values that may or may not be present. Any type can be explicitly declared to be (or implicitly converted to) an optional type. If you don’t provide an initial value when you declare an optional variable or property, its value automatically defaults to `nil`.

If an instance of an optional type contains a value, you can access that value using the postfix operator `!`, as shown below:

    optionalInteger = 42
    optionalInteger! // 42

Using the `!` operator to unwrap an optional that has a value of `nil` results in a runtime error.

You can also use optional chaining and optional binding to conditionally perform an operation on an optional expression. If the value is `nil`, no operation is performed and therefore no runtime error is produced.

For more information and to see examples that show how to use optional types, see [Optionals](TheBasics.md#TP40016643-CH5-ID330).

Grammar of an optional type

<span class="syntax-def-name">
optional-type

<span class="arrow">
→
<span class="syntactic-cat">[type](Types.md#type)`?`

### Implicitly Unwrapped Optional Type

The Swift language defines the postfix `!` as syntactic sugar for the named type `ImplicitlyUnwrappedOptional<Wrapped>`, which is defined in the Swift standard library. In other words, the following two declarations are equivalent:

    var implicitlyUnwrappedString: String!
    var implicitlyUnwrappedString: ImplicitlyUnwrappedOptional<String>

In both cases, the variable `implicitlyUnwrappedString` is declared to have the type of an implicitly unwrapped optional string. Note that no whitespace may appear between the type and the `!`.

You can use implicitly unwrapped optionals in all the same places in your code that you can use optionals. For instance, you can assign values of implicitly unwrapped optionals to variables, constants, and properties of optionals, and vice versa.

As with optionals, if you don’t provide an initial value when you declare an implicitly unwrapped optional variable or property, its value automatically defaults to `nil`.

Because the value of an implicitly unwrapped optional is automatically unwrapped when you use it, there’s no need to use the `!` operator to unwrap it. That said, if you try to use an implicitly unwrapped optional that has a value of `nil`, you’ll get a runtime error.

Use optional chaining to conditionally perform an operation on an implicitly unwrapped optional expression. If the value is `nil`, no operation is performed and therefore no runtime error is produced.

For more information about implicitly unwrapped optional types, see [Implicitly Unwrapped Optionals](TheBasics.md#TP40016643-CH5-ID334).

Grammar of an implicitly unwrapped optional type

<span class="syntax-def-name">
implicitly-unwrapped-optional-type

<span class="arrow">
→
<span class="syntactic-cat">[type](Types.md#type)`!`

### Protocol Composition Type

A protocol composition type describes a type that conforms to each protocol in a list of specified protocols. Protocol composition types may be used in type annotations and in generic parameters.

Protocol composition types have the following form:

-   ```
    protocol<Protocol 1, Protocol 2>
    ```

A protocol composition type allows you to specify a value whose type conforms to the requirements of multiple protocols without having to explicitly define a new, named protocol that inherits from each protocol you want the type to conform to. For example, specifying a protocol composition type `protocol<ProtocolA, ProtocolB, ProtocolC>` is effectively the same as defining a new protocol `ProtocolD` that inherits from `ProtocolA`, `ProtocolB`, and `ProtocolC`, but without having to introduce a new name.

Each item in a protocol composition list must be either the name of protocol or a type alias of a protocol composition type. If the list is empty, it specifies the empty protocol composition type, which every type conforms to.

Grammar of a protocol composition type

<span class="syntax-def-name">
protocol-composition-type

<span class="arrow">
→
`protocol``<`<span class="optional"><span class="syntactic-cat">[protocol-identifier-list](Types.md#protocol-identifier-list)~opt~`>`

<span class="syntax-def-name">
protocol-identifier-list

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[protocol-identifier](Types.md#protocol-identifier)
<span class="alternative">
<span class="syntactic-cat">[protocol-identifier](Types.md#protocol-identifier)`,`<span class="syntactic-cat">[protocol-identifier-list](Types.md#protocol-identifier-list)

<span class="syntax-def-name">
protocol-identifier

<span class="arrow">
→
<span class="syntactic-cat">[type-identifier](Types.md#type-identifier)

### Metatype Type

A metatype type refers to the type of any type, including class types, structure types, enumeration types, and protocol types.

The metatype of a class, structure, or enumeration type is the name of that type followed by `.Type`. The metatype of a protocol type—not the concrete type that conforms to the protocol at runtime—is the name of that protocol followed by `.Protocol`. For example, the metatype of the class type `SomeClass` is `SomeClass.Type` and the metatype of the protocol `SomeProtocol` is `SomeProtocol.Protocol`.

You can use the postfix `self` expression to access a type as a value. For example, `SomeClass.self` returns `SomeClass` itself, not an instance of `SomeClass`. And `SomeProtocol.self` returns `SomeProtocol` itself, not an instance of a type that conforms to `SomeProtocol` at runtime. You can use a `dynamicType` expression with an instance of a type to access that instance’s dynamic, runtime type as a value, as the following example shows:

    class SomeBaseClass {
        class func printClassName() {
            print("SomeBaseClass")
        }
    }
    class SomeSubClass: SomeBaseClass {
        override class func printClassName() {
            print("SomeSubClass")
        }
    }
    let someInstance: SomeBaseClass = SomeSubClass()
    // The compile-time type of someInstance is SomeBaseClass,
    // and the runtime type of someInstance is SomeBaseClass
    someInstance.dynamicType.printClassName()
    // prints "SomeSubClass"

Use the identity operators (`===` and `!==`) to test whether an instance’s runtime type is the same as its compile-time type.

    if someInstance.dynamicType === someInstance.self {
        print("The dynamic and static type of someInstance are the same")
    } else {
        print("The dynamic and static type of someInstance are different")
    }
    // prints "The dynamic and static type of someInstance are different"

Use an initializer expression to construct an instance of a type from that type’s metatype value. For class instances, the initializer that’s called must be marked with the `required` keyword or the entire class marked with the `final` keyword.

    class AnotherSubClass: SomeBaseClass {
        let string: String
        required init(string: String) {
            self.string = string
        }
        override class func printClassName() {
            print("AnotherSubClass")
        }
    }
    let metatype: AnotherSubClass.Type = AnotherSubClass.self
    let anotherInstance = metatype.init(string: "some string")

Grammar of a metatype type

<span class="syntax-def-name">
metatype-type

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[type](Types.md#type)`.``Type`
<span class="alternative">
<span class="syntactic-cat">[type](Types.md#type)`.``Protocol`

### Type Inheritance Clause

A type inheritance clause is used to specify which class a named type inherits from and which protocols a named type conforms to. A type inheritance clause is also used to specify a `class` requirement on a protocol. A type inheritance clause begins with a colon (`:`), followed by either a `class` requirement, a list of type identifiers, or both.

Class types can inherit from a single superclass and conform to any number of protocols. When defining a class, the name of the superclass must appear first in the list of type identifiers, followed by any number of protocols the class must conform to. If the class does not inherit from another class, the list can begin with a protocol instead. For an extended discussion and several examples of class inheritance, see [Inheritance](Inheritance.md).

Other named types can only inherit from or conform to a list of protocols. Protocol types can inherit from any number of other protocols. When a protocol type inherits from other protocols, the set of requirements from those other protocols are aggregated together, and any type that inherits from the current protocol must conform to all of those requirements. As discussed in [Protocol Declaration](Declarations.md#TP40016643-CH34-ID369), you can include the `class` keyword as the first item in the type inheritance clause to mark a protocol declaration with a `class` requirement.

A type inheritance clause in an enumeration definition can be either a list of protocols, or in the case of an enumeration that assigns raw values to its cases, a single, named type that specifies the type of those raw values. For an example of an enumeration definition that uses a type inheritance clause to specify the type of its raw values, see [Raw Values](Enumerations.md#TP40016643-CH12-ID149).

Grammar of a type inheritance clause

<span class="syntax-def-name">
type-inheritance-clause

<span class="arrow">
→
`:`<span class="syntactic-cat">[class-requirement](Types.md#class-requirement)`,`<span class="syntactic-cat">[type-inheritance-list](Types.md#type-inheritance-list)

<span class="syntax-def-name">
type-inheritance-clause

<span class="arrow">
→
`:`<span class="syntactic-cat">[class-requirement](Types.md#class-requirement)

<span class="syntax-def-name">
type-inheritance-clause

<span class="arrow">
→
`:`<span class="syntactic-cat">[type-inheritance-list](Types.md#type-inheritance-list)

<span class="syntax-def-name">
type-inheritance-list

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[type-identifier](Types.md#type-identifier)
<span class="alternative">
<span class="syntactic-cat">[type-identifier](Types.md#type-identifier)`,`<span class="syntactic-cat">[type-inheritance-list](Types.md#type-inheritance-list)

<span class="syntax-def-name">
class-requirement

<span class="arrow">
→
`class`

### Type Inference

Swift uses type inference extensively, allowing you to omit the type or part of the type of many variables and expressions in your code. For example, instead of writing `var x: Int = 0`, you can write `var x = 0`, omitting the type completely—the compiler correctly infers that `x` names a value of type `Int`. Similarly, you can omit part of a type when the full type can be inferred from context. For instance, if you write `let dict: Dictionary = ["A": 1]`, the compiler infers that `dict` has the type `Dictionary<String, Int>`.

In both of the examples above, the type information is passed up from the leaves of the expression tree to its root. That is, the type of `x` in `var x: Int = 0` is inferred by first checking the type of `0` and then passing this type information up to the root (the variable `x`).

In Swift, type information can also flow in the opposite direction—from the root down to the leaves. In the following example, for instance, the explicit type annotation (`: Float`) on the constant `eFloat` causes the numeric literal `2.71828` to have an inferred type of `Float` instead of `Double`.

    let e = 2.71828 // The type of e is inferred to be Double.
    let eFloat: Float = 2.71828 // The type of eFloat is Float.

Type inference in Swift operates at the level of a single expression or statement. This means that all of the information needed to infer an omitted type or part of a type in an expression must be accessible from type-checking the expression or one of its subexpressions.

