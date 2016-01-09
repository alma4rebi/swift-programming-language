Generic Parameters and Arguments 
--------------------------------

This chapter describes parameters and arguments for generic types, functions, and initializers. When you declare a generic type, function, or initializer, you specify the type parameters that the generic type, function, or initializer can work with. These type parameters act as placeholders that are replaced by actual concrete type arguments when an instance of a generic type is created or a generic function or initializer is called.

For an overview of generics in Swift, see [Generics](Generics.md).

### Generic Parameter Clause 

A *generic parameter clause* specifies the type parameters of a generic type or function, along with any associated constraints and requirements on those parameters. A generic parameter clause is enclosed in angle brackets (&lt;&gt;) and has one of the following forms:


-   ``` 
    <generic parameter list>
    ```

-   ``` 
    <generic parameter list where requirements>
    ```

The *generic parameter list* is a comma-separated list of generic parameters, each of which has the following form:


-   ``` 
    type parameter: constraint
    ```

A generic parameter consists of a *type parameter* followed by an optional *constraint*. A *type parameter* is simply the name of a placeholder type (for instance, `T`, `U`, `V`, `Key`, `Value`, and so on). You have access to the type parameters (and any of their associated types) in the rest of the type, function, or initializer declaration, including in the signature of the function or initializer.

The *constraint* specifies that a type parameter inherits from a specific class or conforms to a protocol or protocol composition. For instance, in the generic function below, the generic parameter `T: Comparable` indicates that any type argument substituted for the type parameter `T` must conform to the `Comparable` protocol.

    func simpleMax&lt;T: Comparable&gt;(x: T, _ y: T) -&gt; T {
        if x &lt; y {
            return y
        }
        return x
    }

Because `Int` and `Double`, for example, both conform to the `Comparable` protocol, this function accepts arguments of either type. In contrast with generic types, you don’t specify a generic argument clause when you use a generic function or initializer. The type arguments are instead inferred from the type of the arguments passed to the function or initializer.

    simpleMax(17, 42) // T is inferred to be Int
    simpleMax(3.14159, 2.71828) // T is inferred to be Double

### Where Clauses 

You can specify additional requirements on type parameters and their associated types by including a `where` clause after the *generic parameter list*. A `where` clause consists of the `where` keyword, followed by a comma-separated list of one or more *requirements*.

The *requirements* in a `where` clause specify that a type parameter inherits from a class or conforms to a protocol or protocol composition. Although the `where` clause provides syntactic sugar for expressing simple constraints on type parameters (for instance, `T: Comparable` is equivalent to `T where T: Comparable` and so on), you can use it to provide more complex constraints on type parameters and their associated types. For instance, you can express the constraints that a generic type `T` inherits from a class `C` and conforms to a protocol `P` as `<T where T: C, T: P>`.

As mentioned above, you can constrain the associated types of type parameters to conform to protocols. For example, the generic parameter clause `<S: SequenceType where S.Generator.Element: Equatable>` specifies that `S` conforms to the `SequenceType` protocol and that the associated type `S.Generator.Element` conforms to the `Equatable` protocol. This constraint ensures that each element of the sequence is equatable.

You can also specify the requirement that two types be identical, using the `==` operator. For example, the generic parameter clause `<S1: SequenceType, S2: SequenceType where S1.Generator.Element == S2.Generator.Element>` expresses the constraints that `S1` and `S2` conform to the `SequenceType` protocol and that the elements of both sequences must be of the same type.

Any type argument substituted for a type parameter must meet all the constraints and requirements placed on the type parameter.

You can overload a generic function or initializer by providing different constraints, requirements, or both on the type parameters in the generic parameter clause. When you call an overloaded generic function or initializer, the compiler uses these constraints to resolve which overloaded function or initializer to invoke.

Grammar of a generic parameter clause

<span class="syntax-def-name">
generic-parameter-clause
</span>
<span class="arrow">
→
</span>`<`<span class="syntactic-cat">[generic-parameter-list](GenericParametersAndArguments.md#generic-parameter-list)</span><span class="optional"><span class="syntactic-cat">[requirement-clause](GenericParametersAndArguments.md#requirement-clause)</span>~opt~</span>`>`

<span class="syntax-def-name">
generic-parameter-list
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[generic-parameter](GenericParametersAndArguments.md#generic-parameter)</span>
</span><span class="alternative">
<span class="syntactic-cat">[generic-parameter](GenericParametersAndArguments.md#generic-parameter)</span>`,`<span class="syntactic-cat">[generic-parameter-list](GenericParametersAndArguments.md#generic-parameter-list)</span>
</span>

<span class="syntax-def-name">
generic-parameter
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[type-name](Types.md#type-name)</span>

<span class="syntax-def-name">
generic-parameter
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[type-name](Types.md#type-name)</span>`:`<span class="syntactic-cat">[type-identifier](Types.md#type-identifier)</span>

<span class="syntax-def-name">
generic-parameter
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[type-name](Types.md#type-name)</span>`:`<span class="syntactic-cat">[protocol-composition-type](Types.md#protocol-composition-type)</span>

<span class="syntax-def-name">
requirement-clause
</span>
<span class="arrow">
→
</span>`where`<span class="syntactic-cat">[requirement-list](GenericParametersAndArguments.md#requirement-list)</span>

<span class="syntax-def-name">
requirement-list
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[requirement](GenericParametersAndArguments.md#requirement)</span>
</span><span class="alternative">
<span class="syntactic-cat">[requirement](GenericParametersAndArguments.md#requirement)</span>`,`<span class="syntactic-cat">[requirement-list](GenericParametersAndArguments.md#requirement-list)</span>
</span>

<span class="syntax-def-name">
requirement
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[conformance-requirement](GenericParametersAndArguments.md#conformance-requirement)</span>
</span><span class="alternative">
<span class="syntactic-cat">[same-type-requirement](GenericParametersAndArguments.md#same-type-requirement)</span>
</span>

<span class="syntax-def-name">
conformance-requirement
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[type-identifier](Types.md#type-identifier)</span>`:`<span class="syntactic-cat">[type-identifier](Types.md#type-identifier)</span>

<span class="syntax-def-name">
conformance-requirement
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[type-identifier](Types.md#type-identifier)</span>`:`<span class="syntactic-cat">[protocol-composition-type](Types.md#protocol-composition-type)</span>

<span class="syntax-def-name">
same-type-requirement
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[type-identifier](Types.md#type-identifier)</span>`==`<span class="syntactic-cat">[type](Types.md#type)</span>

### Generic Argument Clause 

A *generic argument clause* specifies the type arguments of a generic type. A generic argument clause is enclosed in angle brackets (&lt;&gt;) and has the following form:


-   ``` 
    <generic argument list>
    ```

The *generic argument list* is a comma-separated list of type arguments. A *type argument* is the name of an actual concrete type that replaces a corresponding type parameter in the generic parameter clause of a generic type. The result is a specialized version of that generic type. As an example, the Swift standard library defines a generic dictionary type as:

    struct Dictionary&lt;Key: Hashable, Value&gt;: CollectionType, DictionaryLiteralConvertible {
        /* ... */
    }

The specialized version of the generic `Dictionary` type, `Dictionary<String, Int>` is formed by replacing the generic parameters `Key: Hashable` and `Value` with the concrete type arguments `String` and `Int`. Each type argument must satisfy all the constraints of the generic parameter it replaces, including any additional requirements specified in a `where` clause. In the example above, the `Key` type parameter is constrained to conform to the `Hashable` protocol and therefore `String` must also conform to the `Hashable` protocol.

You can also replace a type parameter with a type argument that is itself a specialized version of a generic type (provided it satisfies the appropriate constraints and requirements). For example, you can replace the type parameter `Element` in `Array<Element>` with a specialized version of an array, `Array<Int>`, to form an array whose elements are themselves arrays of integers.

    let arrayOfArrays: Array&lt;Array&lt;Int&gt;&gt; = \[\[1, 2, 3\], \[4, 5, 6\], \[7, 8, 9\]\]

As mentioned in [Generic Parameter Clause](GenericParametersAndArguments.md#TP40016643-CH37-ID407), you don’t use a generic argument clause to specify the type arguments of a generic function or initializer.

Grammar of a generic argument clause

<span class="syntax-def-name">
generic-argument-clause
</span>
<span class="arrow">
→
</span>`<`<span class="syntactic-cat">[generic-argument-list](GenericParametersAndArguments.md#generic-argument-list)</span>`>`

<span class="syntax-def-name">
generic-argument-list
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[generic-argument](GenericParametersAndArguments.md#generic-argument)</span>
</span><span class="alternative">
<span class="syntactic-cat">[generic-argument](GenericParametersAndArguments.md#generic-argument)</span>`,`<span class="syntactic-cat">[generic-argument-list](GenericParametersAndArguments.md#generic-argument-list)</span>
</span>

<span class="syntax-def-name">
generic-argument
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[type](Types.md#type)</span>

