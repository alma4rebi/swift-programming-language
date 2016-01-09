



[‌](){#TP40016643-CH31}[‌](){#TP40016643-CH31-ID445}
Types {#types .chapter-name}
-----



In Swift, there are two kinds of types: named types and compound types. A *named type* is a type that can be given a particular name when it is defined. Named types include classes, structures, enumerations, and protocols. For example, instances of a user-defined class named `MyClass`{.code-voice} have the type `MyClass`{.code-voice}. In addition to user-defined named types, the Swift standard library defines many commonly used named types, including those that represent arrays, dictionaries, and optional values.

Data types that are normally considered basic or primitive in other languages—such as types that represent numbers, characters, and strings—are actually named types, defined and implemented in the Swift standard library using structures. Because they are named types, you can extend their behavior to suit the needs of your program, using an extension declaration, discussed in [Extensions](Extensions.md) and [Extension Declaration](Declarations.md#TP40016643-CH34-ID378).

A *compound type* is a type without a name, defined in the Swift language itself. There are two compound types: function types and tuple types. A compound type may contain named types and other compound types. For instance, the tuple type `(Int, (Int, Int))`{.code-voice} contains two elements: The first is the named type `Int`{.code-voice}, and the second is another compound type `(Int, Int)`{.code-voice}.

This chapter discusses the types defined in the Swift language itself and describes the type inference behavior of Swift.



Grammar of a type



[‌](){#type}

type


→

[array-type](Types.md#array-type)

[dictionary-type](Types.md#dictionary-type)

[function-type](Types.md#function-type)

[type-identifier](Types.md#type-identifier)

[tuple-type](Types.md#tuple-type)

[optional-type](Types.md#optional-type)

[implicitly-unwrapped-optional-type](Types.md#implicitly-unwrapped-optional-type)

[protocol-composition-type](Types.md#protocol-composition-type)

[metatype-type](Types.md#metatype-type)










[‌](){#TP40016643-CH31-ID446}
### Type Annotation {#type-annotation .section-name}

A *type annotation* explicitly specifies the type of a variable or expression. Type annotations begin with a colon (`:`{.code-voice}) and end with a type, as the following examples show:







1.  `let`{.code-voice} `someTuple`{.vc}: (`Double`{.n}, `Double`{.n}) = (`3.14159`{.m}, `2.71828`{.m})
2.  `func`{.code-voice} `someFunction`{.vc}(`a`{.vc}: `Int`{.n}) { `/* ... */`{.c} }







In the first example, the expression `someTuple`{.code-voice} is specified to have the tuple type `(Double, Double)`{.code-voice}. In the second example, the parameter `a`{.code-voice} to the function `someFunction`{.code-voice} is specified to have the type `Int`{.code-voice}.

Type annotations can contain an optional list of type attributes before the type.



Grammar of a type annotation



[‌](){#type-annotation}

type-annotation


→
`:`{.literal}[attributes](Attributes.md#attributes)~opt~[type](Types.md#type)









[‌](){#TP40016643-CH31-ID447}
### Type Identifier {#type-identifier .section-name}

A type identifier refers to either a named type or a type alias of a named or compound type.

Most of the time, a type identifier directly refers to a named type with the same name as the identifier. For example, `Int`{.code-voice} is a type identifier that directly refers to the named type `Int`{.code-voice}, and the type identifier `Dictionary`{.code-voice} directly refers to the named type `Dictionary`{.code-voice}.

There are two cases in which a type identifier does not refer to a type with the same name. In the first case, a type identifier refers to a type alias of a named or compound type. For instance, in the example below, the use of `Point`{.code-voice} in the type annotation refers to the tuple type `(Int, Int)`{.code-voice}.







1.  `typealias`{.code-voice} `Point`{.vc} = (`Int`{.n}, `Int`{.n})
2.  `let`{.code-voice} `origin`{.vc}: `Point`{.n} = (`0`{.m}, `0`{.m})







In the second case, a type identifier uses dot (`.`{.code-voice}) syntax to refer to named types declared in other modules or nested within other types. For example, the type identifier in the following code references the named type `MyType`{.code-voice} that is declared in the `ExampleModule`{.code-voice} module.







1.  `var`{.code-voice} `someValue`{.vc}: `ExampleModule`{.n}.`MyType`{.n}









Grammar of a type identifier



[‌](){#type-identifier}

type-identifier


→

[type-name](Types.md#type-name)[generic-argument-clause](GenericParametersAndArguments.md#generic-argument-clause)~opt~

[type-name](Types.md#type-name)[generic-argument-clause](GenericParametersAndArguments.md#generic-argument-clause)~opt~`.`{.literal}[type-identifier](Types.md#type-identifier)


[‌](){#type-name}

type-name


→
[identifier](LexicalStructure.md#identifier)









[‌](){#TP40016643-CH31-ID448}
### Tuple Type {#tuple-type .section-name}

A tuple type is a comma-separated list of zero or more types, enclosed in parentheses.

You can use a tuple type as the return type of a function to enable the function to return a single tuple containing multiple values. You can also name the elements of a tuple type and use those names to refer to the values of the individual elements. An element name consists of an identifier followed immediately by a colon (:). For an example that demonstrates both of these features, see [Functions with Multiple Return Values](Functions.md#TP40016643-CH10-ID164).

`Void`{.code-voice} is a type alias for the empty tuple type, `()`{.code-voice}. If there is only one element inside the parentheses, the type is simply the type of that element. For example, the type of `(Int)`{.code-voice} is `Int`{.code-voice}, not `(Int)`{.code-voice}. As a result, you can name a tuple element only when the tuple type has two or more elements.



Grammar of a tuple type



[‌](){#tuple-type}

tuple-type


→
`(`{.literal}[tuple-type-body](Types.md#tuple-type-body)~opt~`)`{.literal}

[‌](){#tuple-type-body}

tuple-type-body


→
[tuple-type-element-list](Types.md#tuple-type-element-list)`...`{.literal}~opt~

[‌](){#tuple-type-element-list}

tuple-type-element-list


→

[tuple-type-element](Types.md#tuple-type-element)

[tuple-type-element](Types.md#tuple-type-element)`,`{.literal}[tuple-type-element-list](Types.md#tuple-type-element-list)


[‌](){#tuple-type-element}

tuple-type-element


→

[attributes](Attributes.md#attributes)~opt~`inout`{.literal}~opt~[type](Types.md#type)

`inout`{.literal}~opt~[element-name](Types.md#element-name)[type-annotation](Types.md#type-annotation)


[‌](){#element-name}

element-name


→
[identifier](LexicalStructure.md#identifier)









[‌](){#TP40016643-CH31-ID449}
### Function Type {#function-type .section-name}

A function type represents the type of a function, method, or closure and consists of a parameter and return type separated by an arrow (`->`{.code-voice}):




-   ``` {.code-voice}
    parameter type -> return type
    ```



Because the *parameter type* and the *return type* can be a tuple type, function types support functions and methods that take multiple parameters and return multiple values.

A parameter declaration for a function type with a parameter type of `Void`{.code-voice} can apply the `autoclosure`{.code-voice} attribute to capture an implicit closure over a specified expression instead of the expression itself. This provides a syntactically convenient way to defer the evaluation of an expression until its value is used in the function body. For an example of an autoclosure function type parameter, see [Autoclosures](Closures.md#TP40016643-CH11-ID543).

A function type can have a variadic parameter in its *parameter type*. Syntactically, a variadic parameter consists of a base type name followed immediately by three dots (`...`{.code-voice}), as in `Int...`{.code-voice}. A variadic parameter is treated as an array that contains elements of the base type name. For instance, the variadic parameter `Int...`{.code-voice} is treated as `[Int]`{.code-voice}. For an example that uses a variadic parameter, see [Variadic Parameters](Functions.md#TP40016643-CH10-ID171).

To specify an in-out parameter, prefix the parameter type with the `inout`{.code-voice} keyword. You can’t mark a variadic parameter or a return type with the `inout`{.code-voice} keyword. In-out parameters are discussed in [In-Out Parameters](Functions.md#TP40016643-CH10-ID173).

If a function type includes more than a single arrow (`->`{.code-voice}), the function types are grouped from right to left. For example, the function type `Int -> Int -> Int`{.code-voice} is understood as `Int -> (Int -> Int)`{.code-voice}—that is, a function that takes an `Int`{.code-voice} and returns another function that takes and returns an `Int`{.code-voice}.

Function types that can throw an error must be marked with the `throws`{.code-voice} keyword, and function types that can rethrow an error must be marked with the `rethrows`{.code-voice} keyword. The `throws`{.code-voice} keyword is part of a function’s type, and nonthrowing functions are subtypes of throwing functions. As a result, you can use a nonthrowing function in the same places as a throwing one. Throwing and rethrowing functions are described in [Throwing Functions and Methods](Declarations.md#TP40016643-CH34-ID530) and [Rethrowing Functions and Methods](Declarations.md#TP40016643-CH34-ID531).



Grammar of a function type



[‌](){#function-type}

function-type


→
[type](Types.md#type)`throws`{.literal}~opt~`->`{.literal}[type](Types.md#type)

[‌](){#TP40016643-CH31-NoLink_789}

function-type


→
[type](Types.md#type)`rethrows`{.literal}`->`{.literal}[type](Types.md#type)









[‌](){#TP40016643-CH31-ID450}
### Array Type {#array-type .section-name}

The Swift language provides the following syntactic sugar for the Swift standard library `Array`{.code-voice} type:




-   ``` {.code-voice}
    [type]
    ```



In other words, the following two declarations are equivalent:







1.  `let`{.code-voice} `someArray`{.vc}: `Array`{.n}&lt;`String`{.n}&gt; = \[`"Alex"`{.s}, `"Brian"`{.s}, `"Dave"`{.s}\]
2.  `let`{.code-voice} `someArray`{.vc}: \[`String`{.n}\] = \[`"Alex"`{.s}, `"Brian"`{.s}, `"Dave"`{.s}\]







In both cases, the constant `someArray`{.code-voice} is declared as an array of strings. The elements of an array can be accessed through subscripting by specifying a valid index value in square brackets: `someArray[0]`{.code-voice} refers to the element at index 0, `"Alex"`{.code-voice}.

You can create multidimensional arrays by nesting pairs of square brackets, where the name of the base type of the elements is contained in the innermost pair of square brackets. For example, you can create a three-dimensional array of integers using three sets of square brackets:







1.  `var`{.code-voice} `array3D`{.vc}: \[\[\[`Int`{.n}\]\]\] = \[\[\[`1`{.m}, `2`{.m}\], \[`3`{.m}, `4`{.m}\]\], \[\[`5`{.m}, `6`{.m}\], \[`7`{.m}, `8`{.m}\]\]\]







When accessing the elements in a multidimensional array, the left-most subscript index refers to the element at that index in the outermost array. The next subscript index to the right refers to the element at that index in the array that’s nested one level in. And so on. This means that in the example above, `array3D[0]`{.code-voice} refers to `[[1, 2], [3, 4]]`{.code-voice}, `array3D[0][1]`{.code-voice} refers to `[3, 4]`{.code-voice}, and `array3D[0][1][1]`{.code-voice} refers to the value 4.

For a detailed discussion of the Swift standard library `Array`{.code-voice} type, see [Arrays](CollectionTypes.md#TP40016643-CH8-ID107).



Grammar of an array type



[‌](){#array-type}

array-type


→
`[`{.literal}[type](Types.md#type)`]`{.literal}









[‌](){#TP40016643-CH31-ID451}
### Dictionary Type {#dictionary-type .section-name}

The Swift language provides the following syntactic sugar for the Swift standard library `Dictionary`{.code-voice} type:




-   ``` {.code-voice}
    [key type: value type]
    ```



In other words, the following two declarations are equivalent:







1.  `let`{.code-voice} `someDictionary`{.vc}: \[`String`{.n}: `Int`{.n}\] = \[`"Alex"`{.s}: `31`{.m}, `"Paul"`{.s}: `39`{.m}\]
2.  `let`{.code-voice} `someDictionary`{.vc}: `Dictionary`{.n}&lt;`String`{.n}, `Int`{.n}&gt; = \[`"Alex"`{.s}: `31`{.m}, `"Paul"`{.s}: `39`{.m}\]







In both cases, the constant `someDictionary`{.code-voice} is declared as a dictionary with strings as keys and integers as values.

The values of a dictionary can be accessed through subscripting by specifying the corresponding key in square brackets: `someDictionary["Alex"]`{.code-voice} refers to the value associated with the key `"Alex"`{.code-voice}. The subscript returns an optional value of the dictionary’s value type. If the specified key isn’t contained in the dictionary, the subscript returns `nil`{.code-voice}.

The key type of a dictionary must conform to the Swift standard library `Hashable`{.code-voice} protocol.

For a detailed discussion of the Swift standard library `Dictionary`{.code-voice} type, see [Dictionaries](CollectionTypes.md#TP40016643-CH8-ID113).



Grammar of a dictionary type



[‌](){#dictionary-type}

dictionary-type


→
`[`{.literal}[type](Types.md#type)`:`{.literal}[type](Types.md#type)`]`{.literal}









[‌](){#TP40016643-CH31-ID452}
### Optional Type {#optional-type .section-name}

The Swift language defines the postfix `?`{.code-voice} as syntactic sugar for the named type `Optional`{.code-voice}, which is defined in the Swift standard library. In other words, the following two declarations are equivalent:







1.  `var`{.code-voice} `optionalInteger`{.vc}: `Int`{.n}?
2.  `var`{.code-voice} `optionalInteger`{.vc}: `Optional`{.n}&lt;`Int`{.n}&gt;







In both cases, the variable `optionalInteger`{.code-voice} is declared to have the type of an optional integer. Note that no whitespace may appear between the type and the `?`{.code-voice}.

The type `Optional`{.code-voice} is an enumeration with two cases, `None`{.code-voice} and `Some(Wrapped)`{.code-voice}, which are used to represent values that may or may not be present. Any type can be explicitly declared to be (or implicitly converted to) an optional type. If you don’t provide an initial value when you declare an optional variable or property, its value automatically defaults to `nil`{.code-voice}.

If an instance of an optional type contains a value, you can access that value using the postfix operator `!`{.code-voice}, as shown below:







1.  `optionalInteger`{.code-voice} = `42`{.m}
2.  `optionalInteger`{.code-voice}! `// 42`{.c}







Using the `!`{.code-voice} operator to unwrap an optional that has a value of `nil`{.code-voice} results in a runtime error.

You can also use optional chaining and optional binding to conditionally perform an operation on an optional expression. If the value is `nil`{.code-voice}, no operation is performed and therefore no runtime error is produced.

For more information and to see examples that show how to use optional types, see [Optionals](TheBasics.md#TP40016643-CH5-ID330).



Grammar of an optional type



[‌](){#optional-type}

optional-type


→
[type](Types.md#type)`?`{.literal}









[‌](){#TP40016643-CH31-ID453}
### Implicitly Unwrapped Optional Type {#implicitly-unwrapped-optional-type .section-name}

The Swift language defines the postfix `!`{.code-voice} as syntactic sugar for the named type `ImplicitlyUnwrappedOptional`{.code-voice}, which is defined in the Swift standard library. In other words, the following two declarations are equivalent:







1.  `var`{.code-voice} `implicitlyUnwrappedString`{.vc}: `String`{.n}!
2.  `var`{.code-voice} `implicitlyUnwrappedString`{.vc}: `ImplicitlyUnwrappedOptional`{.n}&lt;`String`{.n}&gt;







In both cases, the variable `implicitlyUnwrappedString`{.code-voice} is declared to have the type of an implicitly unwrapped optional string. Note that no whitespace may appear between the type and the `!`{.code-voice}.

You can use implicitly unwrapped optionals in all the same places in your code that you can use optionals. For instance, you can assign values of implicitly unwrapped optionals to variables, constants, and properties of optionals, and vice versa.

As with optionals, if you don’t provide an initial value when you declare an implicitly unwrapped optional variable or property, its value automatically defaults to `nil`{.code-voice}.

Because the value of an implicitly unwrapped optional is automatically unwrapped when you use it, there’s no need to use the `!`{.code-voice} operator to unwrap it. That said, if you try to use an implicitly unwrapped optional that has a value of `nil`{.code-voice}, you’ll get a runtime error.

Use optional chaining to conditionally perform an operation on an implicitly unwrapped optional expression. If the value is `nil`{.code-voice}, no operation is performed and therefore no runtime error is produced.

For more information about implicitly unwrapped optional types, see [Implicitly Unwrapped Optionals](TheBasics.md#TP40016643-CH5-ID334).



Grammar of an implicitly unwrapped optional type



[‌](){#implicitly-unwrapped-optional-type}

implicitly-unwrapped-optional-type


→
[type](Types.md#type)`!`{.literal}









[‌](){#TP40016643-CH31-ID454}
### Protocol Composition Type {#protocol-composition-type .section-name}

A protocol composition type describes a type that conforms to each protocol in a list of specified protocols. Protocol composition types may be used in type annotations and in generic parameters.

Protocol composition types have the following form:




-   ``` {.code-voice}
    protocol
    ```



A protocol composition type allows you to specify a value whose type conforms to the requirements of multiple protocols without having to explicitly define a new, named protocol that inherits from each protocol you want the type to conform to. For example, specifying a protocol composition type `protocol`{.code-voice} is effectively the same as defining a new protocol `ProtocolD`{.code-voice} that inherits from `ProtocolA`{.code-voice}, `ProtocolB`{.code-voice}, and `ProtocolC`{.code-voice}, but without having to introduce a new name.

Each item in a protocol composition list must be either the name of protocol or a type alias of a protocol composition type. If the list is empty, it specifies the empty protocol composition type, which every type conforms to.



Grammar of a protocol composition type



[‌](){#protocol-composition-type}

protocol-composition-type


→
`protocol`{.literal}`[protocol-identifier-list](Types.md#protocol-identifier-list)~opt~`>`{.literal}

[‌](){#protocol-identifier-list}

protocol-identifier-list


→

[protocol-identifier](Types.md#protocol-identifier)

[protocol-identifier](Types.md#protocol-identifier)`,`{.literal}[protocol-identifier-list](Types.md#protocol-identifier-list)


[‌](){#protocol-identifier}

protocol-identifier


→
[type-identifier](Types.md#type-identifier)









[‌](){#TP40016643-CH31-ID455}
### Metatype Type {#metatype-type .section-name}

A metatype type refers to the type of any type, including class types, structure types, enumeration types, and protocol types.

The metatype of a class, structure, or enumeration type is the name of that type followed by `.Type`{.code-voice}. The metatype of a protocol type—not the concrete type that conforms to the protocol at runtime—is the name of that protocol followed by `.Protocol`{.code-voice}. For example, the metatype of the class type `SomeClass`{.code-voice} is `SomeClass.Type`{.code-voice} and the metatype of the protocol `SomeProtocol`{.code-voice} is `SomeProtocol.Protocol`{.code-voice}.

You can use the postfix `self`{.code-voice} expression to access a type as a value. For example, `SomeClass.self`{.code-voice} returns `SomeClass`{.code-voice} itself, not an instance of `SomeClass`{.code-voice}. And `SomeProtocol.self`{.code-voice} returns `SomeProtocol`{.code-voice} itself, not an instance of a type that conforms to `SomeProtocol`{.code-voice} at runtime. You can use a `dynamicType`{.code-voice} expression with an instance of a type to access that instance’s dynamic, runtime type as a value, as the following example shows:







1.  `class`{.code-voice} `SomeBaseClass`{.vc} {
2.  `    class`{.code-voice} `func`{.kt} `printClassName`{.vc}() {
3.  `        print`{.code-voice}(`"SomeBaseClass"`{.s})
4.  `    }`{.code-voice}
5.  `}`{.code-voice}
6.  `class`{.code-voice} `SomeSubClass`{.vc}: `SomeBaseClass`{.n} {
7.  `    override`{.code-voice} `class`{.kt} `func`{.kt} `printClassName`{.vc}() {
8.  `        print`{.code-voice}(`"SomeSubClass"`{.s})
9.  `    }`{.code-voice}
10. `}`{.code-voice}
11. `let`{.code-voice} `someInstance`{.vc}: `SomeBaseClass`{.n} = `SomeSubClass`{.vc}()
12. `// The compile-time type of someInstance is SomeBaseClass,`{.code-voice}
13. `// and the runtime type of someInstance is SomeBaseClass`{.code-voice}
14. `someInstance`{.code-voice}.`dynamicType`{.kt}.`printClassName`{.vc}()
15. `// prints "SomeSubClass"`{.code-voice}







Use the identity operators (`===`{.code-voice} and `!==`{.code-voice}) to test whether an instance’s runtime type is the same as its compile-time type.







1.  `if`{.code-voice} `someInstance`{.vc}.`dynamicType`{.kt} === `someInstance`{.vc}.`self`{.kt} {
2.  `    print`{.code-voice}(`"The dynamic and static type of someInstance are the same"`{.s})
3.  `} else`{.code-voice} {
4.  `    print`{.code-voice}(`"The dynamic and static type of someInstance are different"`{.s})
5.  `}`{.code-voice}
6.  `// prints "The dynamic and static type of someInstance are different"`{.code-voice}







Use an initializer expression to construct an instance of a type from that type’s metatype value. For class instances, the initializer that’s called must be marked with the `required`{.code-voice} keyword or the entire class marked with the `final`{.code-voice} keyword.







1.  `class`{.code-voice} `AnotherSubClass`{.vc}: `SomeBaseClass`{.n} {
2.  `    let`{.code-voice} `string`{.vc}: `String`{.n}
3.  `    required`{.code-voice} `init`{.kt}(`string`{.vc}: `String`{.n}) {
4.  `        self`{.code-voice}.`string`{.vc} = `string`{.vc}
5.  `    }`{.code-voice}
6.  `    override`{.code-voice} `class`{.kt} `func`{.kt} `printClassName`{.vc}() {
7.  `        print`{.code-voice}(`"AnotherSubClass"`{.s})
8.  `    }`{.code-voice}
9.  `}`{.code-voice}
10. `let`{.code-voice} `metatype`{.vc}: `AnotherSubClass`{.n}.`Type`{.vc} = `AnotherSubClass`{.vc}.`self`{.kt}
11. `let`{.code-voice} `anotherInstance`{.vc} = `metatype`{.vc}.`init`{.kt}(`string`{.vc}: `"some string"`{.s})









Grammar of a metatype type



[‌](){#metatype-type}

metatype-type


→

[type](Types.md#type)`.`{.literal}`Type`{.literal}

[type](Types.md#type)`.`{.literal}`Protocol`{.literal}










[‌](){#TP40016643-CH31-ID456}
### Type Inheritance Clause {#type-inheritance-clause .section-name}

A type inheritance clause is used to specify which class a named type inherits from and which protocols a named type conforms to. A type inheritance clause is also used to specify a `class`{.code-voice} requirement on a protocol. A type inheritance clause begins with a colon (`:`{.code-voice}), followed by either a `class`{.code-voice} requirement, a list of type identifiers, or both.

Class types can inherit from a single superclass and conform to any number of protocols. When defining a class, the name of the superclass must appear first in the list of type identifiers, followed by any number of protocols the class must conform to. If the class does not inherit from another class, the list can begin with a protocol instead. For an extended discussion and several examples of class inheritance, see [Inheritance](Inheritance.md).

Other named types can only inherit from or conform to a list of protocols. Protocol types can inherit from any number of other protocols. When a protocol type inherits from other protocols, the set of requirements from those other protocols are aggregated together, and any type that inherits from the current protocol must conform to all of those requirements. As discussed in [Protocol Declaration](Declarations.md#TP40016643-CH34-ID369), you can include the `class`{.code-voice} keyword as the first item in the type inheritance clause to mark a protocol declaration with a `class`{.code-voice} requirement.

A type inheritance clause in an enumeration definition can be either a list of protocols, or in the case of an enumeration that assigns raw values to its cases, a single, named type that specifies the type of those raw values. For an example of an enumeration definition that uses a type inheritance clause to specify the type of its raw values, see [Raw Values](Enumerations.md#TP40016643-CH12-ID149).



Grammar of a type inheritance clause



[‌](){#type-inheritance-clause}

type-inheritance-clause


→
`:`{.literal}[class-requirement](Types.md#class-requirement)`,`{.literal}[type-inheritance-list](Types.md#type-inheritance-list)

[‌](){#TP40016643-CH31-NoLink_806}

type-inheritance-clause


→
`:`{.literal}[class-requirement](Types.md#class-requirement)

[‌](){#TP40016643-CH31-NoLink_807}

type-inheritance-clause


→
`:`{.literal}[type-inheritance-list](Types.md#type-inheritance-list)

[‌](){#type-inheritance-list}

type-inheritance-list


→

[type-identifier](Types.md#type-identifier)

[type-identifier](Types.md#type-identifier)`,`{.literal}[type-inheritance-list](Types.md#type-inheritance-list)


[‌](){#class-requirement}

class-requirement


→
`class`{.literal}









[‌](){#TP40016643-CH31-ID457}
### Type Inference {#type-inference .section-name}

Swift uses type inference extensively, allowing you to omit the type or part of the type of many variables and expressions in your code. For example, instead of writing `var x: Int = 0`{.code-voice}, you can write `var x = 0`{.code-voice}, omitting the type completely—the compiler correctly infers that `x`{.code-voice} names a value of type `Int`{.code-voice}. Similarly, you can omit part of a type when the full type can be inferred from context. For instance, if you write `let dict: Dictionary = ["A": 1]`{.code-voice}, the compiler infers that `dict`{.code-voice} has the type `Dictionary`{.code-voice}.

In both of the examples above, the type information is passed up from the leaves of the expression tree to its root. That is, the type of `x`{.code-voice} in `var x: Int = 0`{.code-voice} is inferred by first checking the type of `0`{.code-voice} and then passing this type information up to the root (the variable `x`{.code-voice}).

In Swift, type information can also flow in the opposite direction—from the root down to the leaves. In the following example, for instance, the explicit type annotation (`: Float`{.code-voice}) on the constant `eFloat`{.code-voice} causes the numeric literal `2.71828`{.code-voice} to have an inferred type of `Float`{.code-voice} instead of `Double`{.code-voice}.







1.  `let`{.code-voice} `e`{.vc} = `2.71828`{.m} `// The type of e is inferred to be Double.`{.c}
2.  `let`{.code-voice} `eFloat`{.vc}: `Float`{.n} = `2.71828`{.m} `// The type of eFloat is Float.`{.c}







Type inference in Swift operates at the level of a single expression or statement. This means that all of the information needed to infer an omitted type or part of a type in an expression must be accessible from type-checking the expression or one of its subexpressions.






