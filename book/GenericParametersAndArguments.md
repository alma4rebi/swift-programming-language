



[‌](){#TP40016643-CH37}[‌](){#TP40016643-CH37-ID406}
Generic Parameters and Arguments {#generic-parameters-and-arguments .chapter-name}
--------------------------------



This chapter describes parameters and arguments for generic types, functions, and initializers. When you declare a generic type, function, or initializer, you specify the type parameters that the generic type, function, or initializer can work with. These type parameters act as placeholders that are replaced by actual concrete type arguments when an instance of a generic type is created or a generic function or initializer is called.

For an overview of generics in Swift, see [Generics](Generics.md).





[‌](){#TP40016643-CH37-ID407}
### Generic Parameter Clause {#generic-parameter-clause .section-name}

A *generic parameter clause* specifies the type parameters of a generic type or function, along with any associated constraints and requirements on those parameters. A generic parameter clause is enclosed in angle brackets (&lt;&gt;) and has one of the following forms:




-   ``` {.code-voice}
    
    ```

-   ``` {.code-voice}
    
    ```



The *generic parameter list* is a comma-separated list of generic parameters, each of which has the following form:




-   ``` {.code-voice}
    type parameter: constraint
    ```



A generic parameter consists of a *type parameter* followed by an optional *constraint*. A *type parameter* is simply the name of a placeholder type (for instance, `T`{.code-voice}, `U`{.code-voice}, `V`{.code-voice}, `Key`{.code-voice}, `Value`{.code-voice}, and so on). You have access to the type parameters (and any of their associated types) in the rest of the type, function, or initializer declaration, including in the signature of the function or initializer.

The *constraint* specifies that a type parameter inherits from a specific class or conforms to a protocol or protocol composition. For instance, in the generic function below, the generic parameter `T: Comparable`{.code-voice} indicates that any type argument substituted for the type parameter `T`{.code-voice} must conform to the `Comparable`{.code-voice} protocol.







1.  `func`{.code-voice} `simpleMax`{.vc}&lt;`T`{.vc}: `Comparable`{.n}&gt;(`x`{.vc}: `T`{.n}, `_`{.kt} `y`{.vc}: `T`{.n}) -&gt; `T`{.n} {
2.  `    if`{.code-voice} `x`{.vc} &lt; `y`{.vc} {
3.  `        return`{.code-voice} `y`{.vc}
4.  `    }`{.code-voice}
5.  `    return`{.code-voice} `x`{.vc}
6.  `}`{.code-voice}







Because `Int`{.code-voice} and `Double`{.code-voice}, for example, both conform to the `Comparable`{.code-voice} protocol, this function accepts arguments of either type. In contrast with generic types, you don’t specify a generic argument clause when you use a generic function or initializer. The type arguments are instead inferred from the type of the arguments passed to the function or initializer.







1.  `simpleMax`{.code-voice}(`17`{.m}, `42`{.m}) `// T is inferred to be Int`{.c}
2.  `simpleMax`{.code-voice}(`3.14159`{.m}, `2.71828`{.m}) `// T is inferred to be Double`{.c}









[‌](){#TP40016643-CH37-ID408}
### Where Clauses {#where-clauses .section-name}

You can specify additional requirements on type parameters and their associated types by including a `where`{.code-voice} clause after the *generic parameter list*. A `where`{.code-voice} clause consists of the `where`{.code-voice} keyword, followed by a comma-separated list of one or more *requirements*.

The *requirements* in a `where`{.code-voice} clause specify that a type parameter inherits from a class or conforms to a protocol or protocol composition. Although the `where`{.code-voice} clause provides syntactic sugar for expressing simple constraints on type parameters (for instance, `T: Comparable`{.code-voice} is equivalent to `T where T: Comparable`{.code-voice} and so on), you can use it to provide more complex constraints on type parameters and their associated types. For instance, you can express the constraints that a generic type `T`{.code-voice} inherits from a class `C`{.code-voice} and conforms to a protocol `P`{.code-voice} as ``{.code-voice}.

As mentioned above, you can constrain the associated types of type parameters to conform to protocols. For example, the generic parameter clause ``{.code-voice} specifies that `S`{.code-voice} conforms to the `SequenceType`{.code-voice} protocol and that the associated type `S.Generator.Element`{.code-voice} conforms to the `Equatable`{.code-voice} protocol. This constraint ensures that each element of the sequence is equatable.

You can also specify the requirement that two types be identical, using the `==`{.code-voice} operator. For example, the generic parameter clause ``{.code-voice} expresses the constraints that `S1`{.code-voice} and `S2`{.code-voice} conform to the `SequenceType`{.code-voice} protocol and that the elements of both sequences must be of the same type.

Any type argument substituted for a type parameter must meet all the constraints and requirements placed on the type parameter.

You can overload a generic function or initializer by providing different constraints, requirements, or both on the type parameters in the generic parameter clause. When you call an overloaded generic function or initializer, the compiler uses these constraints to resolve which overloaded function or initializer to invoke.



Grammar of a generic parameter clause



[‌](){#generic-parameter-clause}

generic-parameter-clause


→
`[generic-parameter-list](GenericParametersAndArguments.md#generic-parameter-list)[requirement-clause](GenericParametersAndArguments.md#requirement-clause)~opt~`>`{.literal}

[‌](){#generic-parameter-list}

generic-parameter-list


→

[generic-parameter](GenericParametersAndArguments.md#generic-parameter)

[generic-parameter](GenericParametersAndArguments.md#generic-parameter)`,`{.literal}[generic-parameter-list](GenericParametersAndArguments.md#generic-parameter-list)


[‌](){#generic-parameter}

generic-parameter


→
[type-name](Types.md#type-name)

[‌](){#TP40016643-CH37-NoLink_501}

generic-parameter


→
[type-name](Types.md#type-name)`:`{.literal}[type-identifier](Types.md#type-identifier)

[‌](){#TP40016643-CH37-NoLink_502}

generic-parameter


→
[type-name](Types.md#type-name)`:`{.literal}[protocol-composition-type](Types.md#protocol-composition-type)





[‌](){#requirement-clause}

requirement-clause


→
`where`{.literal}[requirement-list](GenericParametersAndArguments.md#requirement-list)

[‌](){#requirement-list}

requirement-list


→

[requirement](GenericParametersAndArguments.md#requirement)

[requirement](GenericParametersAndArguments.md#requirement)`,`{.literal}[requirement-list](GenericParametersAndArguments.md#requirement-list)


[‌](){#requirement}

requirement


→

[conformance-requirement](GenericParametersAndArguments.md#conformance-requirement)

[same-type-requirement](GenericParametersAndArguments.md#same-type-requirement)






[‌](){#conformance-requirement}

conformance-requirement


→
[type-identifier](Types.md#type-identifier)`:`{.literal}[type-identifier](Types.md#type-identifier)

[‌](){#TP40016643-CH37-NoLink_507}

conformance-requirement


→
[type-identifier](Types.md#type-identifier)`:`{.literal}[protocol-composition-type](Types.md#protocol-composition-type)

[‌](){#same-type-requirement}

same-type-requirement


→
[type-identifier](Types.md#type-identifier)`==`{.literal}[type](Types.md#type)











[‌](){#TP40016643-CH37-ID409}
### Generic Argument Clause {#generic-argument-clause .section-name}

A *generic argument clause* specifies the type arguments of a generic type. A generic argument clause is enclosed in angle brackets (&lt;&gt;) and has the following form:




-   ``` {.code-voice}
    
    ```



The *generic argument list* is a comma-separated list of type arguments. A *type argument* is the name of an actual concrete type that replaces a corresponding type parameter in the generic parameter clause of a generic type. The result is a specialized version of that generic type. As an example, the Swift standard library defines a generic dictionary type as:







1.  `struct`{.code-voice} `Dictionary`{.vc}&lt;`Key`{.vc}: `Hashable`{.vc}, `Value`{.vc}&gt;: `CollectionType`{.n}, `DictionaryLiteralConvertible`{.n} {
2.  `    /* ... */`{.code-voice}
3.  `}`{.code-voice}







The specialized version of the generic `Dictionary`{.code-voice} type, `Dictionary`{.code-voice} is formed by replacing the generic parameters `Key: Hashable`{.code-voice} and `Value`{.code-voice} with the concrete type arguments `String`{.code-voice} and `Int`{.code-voice}. Each type argument must satisfy all the constraints of the generic parameter it replaces, including any additional requirements specified in a `where`{.code-voice} clause. In the example above, the `Key`{.code-voice} type parameter is constrained to conform to the `Hashable`{.code-voice} protocol and therefore `String`{.code-voice} must also conform to the `Hashable`{.code-voice} protocol.

You can also replace a type parameter with a type argument that is itself a specialized version of a generic type (provided it satisfies the appropriate constraints and requirements). For example, you can replace the type parameter `Element`{.code-voice} in `Array`{.code-voice} with a specialized version of an array, `Array`{.code-voice}, to form an array whose elements are themselves arrays of integers.







1.  `let`{.code-voice} `arrayOfArrays`{.vc}: `Array`{.n}&lt;`Array`{.n}&lt;`Int`{.n}&gt;&gt; = \[\[`1`{.m}, `2`{.m}, `3`{.m}\], \[`4`{.m}, `5`{.m}, `6`{.m}\], \[`7`{.m}, `8`{.m}, `9`{.m}\]\]







As mentioned in [Generic Parameter Clause](GenericParametersAndArguments.md#TP40016643-CH37-ID407), you don’t use a generic argument clause to specify the type arguments of a generic function or initializer.



Grammar of a generic argument clause



[‌](){#generic-argument-clause}

generic-argument-clause


→
`[generic-argument-list](GenericParametersAndArguments.md#generic-argument-list)`>`{.literal}

[‌](){#generic-argument-list}

generic-argument-list


→

[generic-argument](GenericParametersAndArguments.md#generic-argument)

[generic-argument](GenericParametersAndArguments.md#generic-argument)`,`{.literal}[generic-argument-list](GenericParametersAndArguments.md#generic-argument-list)


[‌](){#generic-argument}

generic-argument


→
[type](Types.md#type)










