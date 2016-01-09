



[‌]()[‌]()
Declarations 
------------



A *declaration* introduces a new name or construct into your program. For example, you use declarations to introduce functions and methods, variables and constants, and to define new, named enumeration, structure, class, and protocol types. You can also use a declaration to extend the behavior of an existing named type and to import symbols into your program that are declared elsewhere.

In Swift, most declarations are also definitions in the sense that they are implemented or initialized at the same time they are declared. That said, because protocols don’t implement their members, most protocol members are declarations only. For convenience and because the distinction isn’t that important in Swift, the term *declaration* covers both declarations and definitions.



Grammar of a declaration



[‌]()

declaration


→
[import-declaration](Declarations.md#import-declaration)

[‌]()

declaration


→
[constant-declaration](Declarations.md#constant-declaration)

[‌]()

declaration


→
[variable-declaration](Declarations.md#variable-declaration)

[‌]()

declaration


→
[typealias-declaration](Declarations.md#typealias-declaration)

[‌]()

declaration


→
[function-declaration](Declarations.md#function-declaration)

[‌]()

declaration


→
[enum-declaration](Declarations.md#enum-declaration)

[‌]()

declaration


→
[struct-declaration](Declarations.md#struct-declaration)

[‌]()

declaration


→
[class-declaration](Declarations.md#class-declaration)

[‌]()

declaration


→
[protocol-declaration](Declarations.md#protocol-declaration)

[‌]()

declaration


→
[initializer-declaration](Declarations.md#initializer-declaration)

[‌]()

declaration


→
[deinitializer-declaration](Declarations.md#deinitializer-declaration)

[‌]()

declaration


→
[extension-declaration](Declarations.md#extension-declaration)

[‌]()

declaration


→
[subscript-declaration](Declarations.md#subscript-declaration)

[‌]()

declaration


→
[operator-declaration](Declarations.md#operator-declaration)

[‌]()

declarations


→
[declaration](Declarations.md#declaration)[declarations](Declarations.md#declarations)~opt~









[‌]()
### Top-Level Code 

The top-level code in a Swift source file consists of zero or more statements, declarations, and expressions. By default, variables, constants, and other named declarations that are declared at the top-level of a source file are accessible to code in every source file that is part of the same module. You can override this default behavior by marking the declaration with an access level modifier, as described in [Access Control Levels](Declarations.md#TP40016643-CH34-ID382).



Grammar of a top-level declaration



[‌]()

top-level-declaration


→
[statements](Statements.md#statements)~opt~









[‌]()
### Code Blocks 

A *code block* is used by a variety of declarations and control structures to group statements together. It has the following form:




-   ``` 
    {
    ```

-   ``` 
        statements
    ```

-   ``` 
    }
    ```



The *statements* inside a code block include declarations, expressions, and other kinds of statements and are executed in order of their appearance in source code.



Grammar of a code block



[‌]()

code-block


→
`{`[statements](Statements.md#statements)~opt~`}`









[‌]()
### Import Declaration 

An *import declaration* lets you access symbols that are declared outside the current file. The basic form imports the entire module; it consists of the `import` keyword followed by a module name:




-   ``` 
    import module
    ```



Providing more detail limits which symbols are imported—you can specify a specific submodule or a specific declaration within a module or submodule. When this detailed form is used, only the imported symbol (and not the module that declares it) is made available in the current scope.




-   ``` 
    import import kind module.symbol name
    ```

-   ``` 
    import module.submodule
    ```





Grammar of an import declaration



[‌]()

import-declaration


→
[attributes](Attributes.md#attributes)~opt~`import`[import-kind](Declarations.md#import-kind)~opt~[import-path](Declarations.md#import-path)





[‌]()

import-kind


→

`typealias`

`struct`

`class`

`enum`

`protocol`

`var`

`func`


[‌]()

import-path


→

[import-path-identifier](Declarations.md#import-path-identifier)

[import-path-identifier](Declarations.md#import-path-identifier)`.`[import-path](Declarations.md#import-path)


[‌]()

import-path-identifier


→

[identifier](LexicalStructure.md#identifier)

[operator](LexicalStructure.md#operator)










[‌]()
### Constant Declaration 

A *constant declaration* introduces a constant named value into your program. Constant declarations are declared using the `let` keyword and have the following form:




-   ``` 
    let constant name: type = expression
    ```



A constant declaration defines an immutable binding between the *constant name* and the value of the initializer *expression*; after the value of a constant is set, it cannot be changed. That said, if a constant is initialized with a class object, the object itself can change, but the binding between the constant name and the object it refers to can’t.

When a constant is declared at global scope, it must be initialized with a value. When a constant declaration occurs in the context of a class or structure declaration, it is considered a *constant property*. Constant declarations are not computed properties and therefore do not have getters or setters.

If the *constant name* of a constant declaration is a tuple pattern, the name of each item in the tuple is bound to the corresponding value in the initializer *expression*.







1.  `let` (`firstNumber`, `secondNumber`) = (`10`, `42`)







In this example, `firstNumber` is a named constant for the value `10`, and `secondNumber` is a named constant for the value `42`. Both constants can now be used independently:







1.  `print`(`"The first number is `\\(`firstNumber`)`."`)
2.  `// prints "The first number is 10."`
3.  `print`(`"The second number is `\\(`secondNumber`)`."`)
4.  `// prints "The second number is 42."`







The type annotation (`:` *type*) is optional in a constant declaration when the type of the *constant name* can be inferred, as described in [Type Inference](Types.md#TP40016643-CH31-ID457).

To declare a constant type property, mark the declaration with the `static` declaration modifier. Type properties are discussed in [Type Properties](Properties.md#TP40016643-CH14-ID264).

For more information about constants and for guidance about when to use them, see [Constants and Variables](TheBasics.md#TP40016643-CH5-ID310) and [Stored Properties](Properties.md#TP40016643-CH14-ID255).



Grammar of a constant declaration



[‌]()

constant-declaration


→
[attributes](Attributes.md#attributes)~opt~[declaration-modifiers](Declarations.md#declaration-modifiers)~opt~`let`[pattern-initializer-list](Declarations.md#pattern-initializer-list)





[‌]()

pattern-initializer-list


→

[pattern-initializer](Declarations.md#pattern-initializer)

[pattern-initializer](Declarations.md#pattern-initializer)`,`[pattern-initializer-list](Declarations.md#pattern-initializer-list)


[‌]()

pattern-initializer


→
[pattern](Patterns.md#pattern)[initializer](Declarations.md#initializer)~opt~

[‌]()

initializer


→
`=`[expression](Expressions.md#expression)









[‌]()
### Variable Declaration 

A *variable declaration* introduces a variable named value into your program and is declared using the `var` keyword.

Variable declarations have several forms that declare different kinds of named, mutable values, including stored and computed variables and properties, stored variable and property observers, and static variable properties. The appropriate form to use depends on the scope at which the variable is declared and the kind of variable you intend to declare.



Note

You can also declare properties in the context of a protocol declaration, as described in [Protocol Property Declaration](Declarations.md#TP40016643-CH34-ID370).



You can override a property in a subclass by marking the subclass’s property declaration with the `override` declaration modifier, as described in [Overriding](Inheritance.md#TP40016643-CH17-ID196).



[‌]()
### Stored Variables and Stored Variable Properties 

The following form declares a stored variable or stored variable property:




-   ``` 
    var variable name: type = expression
    ```



You define this form of a variable declaration at global scope, the local scope of a function, or in the context of a class or structure declaration. When a variable declaration of this form is declared at global scope or the local scope of a function, it is referred to as a *stored variable*. When it is declared in the context of a class or structure declaration, it is referred to as a *stored variable property*.

The initializer *expression* can’t be present in a protocol declaration, but in all other contexts, the initializer *expression* is optional. That said, if no initializer *expression* is present, the variable declaration must include an explicit type annotation (`:` *type*).

As with constant declarations, if the *variable name* is a tuple pattern, the name of each item in the tuple is bound to the corresponding value in the initializer *expression*.

As their names suggest, the value of a stored variable or a stored variable property is stored in memory.





[‌]()
### Computed Variables and Computed Properties 

The following form declares a computed variable or computed property:




-   ``` 
    var variable name: type {
    ```

-   ``` 
    get {
    ```

-   ``` 
        statements
    ```

-   ``` 
    }
    ```

-   ``` 
    set(setter name) {
    ```

-   ``` 
        statements
    ```

-   ``` 
    }
    ```

-   ``` 
    }
    ```



You define this form of a variable declaration at global scope, the local scope of a function, or in the context of a class, structure, enumeration, or extension declaration. When a variable declaration of this form is declared at global scope or the local scope of a function, it is referred to as a *computed variable*. When it is declared in the context of a class, structure, or extension declaration, it is referred to as a *computed property*.

The getter is used to read the value, and the setter is used to write the value. The setter clause is optional, and when only a getter is needed, you can omit both clauses and simply return the requested value directly, as described in [Read-Only Computed Properties](Properties.md#TP40016643-CH14-ID261). But if you provide a setter clause, you must also provide a getter clause.

The *setter name* and enclosing parentheses is optional. If you provide a setter name, it is used as the name of the parameter to the setter. If you do not provide a setter name, the default parameter name to the setter is `newValue`, as described in [Shorthand Setter Declaration](Properties.md#TP40016643-CH14-ID260).

Unlike stored named values and stored variable properties, the value of a computed named value or a computed property is not stored in memory.

For more information and to see examples of computed properties, see [Computed Properties](Properties.md#TP40016643-CH14-ID259).





[‌]()
### Stored Variable Observers and Property Observers 

You can also declare a stored variable or property with `willSet` and `didSet` observers. A stored variable or property declared with observers has the following form:




-   ``` 
    var variable name: type = expression {
    ```

-   ``` 
    willSet(setter name) {
    ```

-   ``` 
        statements
    ```

-   ``` 
    }
    ```

-   ``` 
    didSet(setter name) {
    ```

-   ``` 
        statements
    ```

-   ``` 
    }
    ```

-   ``` 
    }
    ```



You define this form of a variable declaration at global scope, the local scope of a function, or in the context of a class or structure declaration. When a variable declaration of this form is declared at global scope or the local scope of a function, the observers are referred to as *stored variable observers*. When it is declared in the context of a class or structure declaration, the observers are referred to as *property observers*.

You can add property observers to any stored property. You can also add property observers to any inherited property (whether stored or computed) by overriding the property within a subclass, as described in [Overriding Property Observers](Inheritance.md#TP40016643-CH17-ID201).

The initializer *expression* is optional in the context of a class or structure declaration, but required elsewhere. The *type* annotation is optional when the type can be inferred from the initializer *expression*.

The `willSet` and `didSet` observers provide a way to observe (and to respond appropriately) when the value of a variable or property is being set. The observers are not called when the variable or property is first initialized. Instead, they are called only when the value is set outside of an initialization context.

A `willSet` observer is called just before the value of the variable or property is set. The new value is passed to the `willSet` observer as a constant, and therefore it can’t be changed in the implementation of the `willSet` clause. The `didSet` observer is called immediately after the new value is set. In contrast to the `willSet` observer, the old value of the variable or property is passed to the `didSet` observer in case you still need access to it. That said, if you assign a value to a variable or property within its own `didSet` observer clause, that new value that you assign will replace the one that was just set and passed to the `willSet` observer.

The *setter name* and enclosing parentheses in the `willSet` and `didSet` clauses are optional. If you provide setter names, they are used as the parameter names to the `willSet` and `didSet` observers. If you do not provide setter names, the default parameter name to the `willSet` observer is `newValue` and the default parameter name to the `didSet` observer is `oldValue`.

The `didSet` clause is optional when you provide a `willSet` clause. Likewise, the `willSet` clause is optional when you provide a `didSet` clause.

For more information and to see an example of how to use property observers, see [Property Observers](Properties.md#TP40016643-CH14-ID262).





[‌]()
### Type Variable Properties 

To declare a type variable property, mark the declaration with the `static` declaration modifier. Classes may mark type computed properties with the `class` declaration modifier instead to allow subclasses to override the superclass’s implementation. Type properties are discussed in [Type Properties](Properties.md#TP40016643-CH14-ID264).



Note

In a class declaration, the `static` keyword has the same effect as marking the declaration with both the `class` and `final` declaration modifiers.





Grammar of a variable declaration



[‌]()

variable-declaration


→
[variable-declaration-head](Declarations.md#variable-declaration-head)[pattern-initializer-list](Declarations.md#pattern-initializer-list)

[‌]()

variable-declaration


→
[variable-declaration-head](Declarations.md#variable-declaration-head)[variable-name](Declarations.md#variable-name)[type-annotation](Types.md#type-annotation)[code-block](Declarations.md#code-block)

[‌]()

variable-declaration


→
[variable-declaration-head](Declarations.md#variable-declaration-head)[variable-name](Declarations.md#variable-name)[type-annotation](Types.md#type-annotation)[getter-setter-block](Declarations.md#getter-setter-block)

[‌]()

variable-declaration


→
[variable-declaration-head](Declarations.md#variable-declaration-head)[variable-name](Declarations.md#variable-name)[type-annotation](Types.md#type-annotation)[getter-setter-keyword-block](Declarations.md#getter-setter-keyword-block)

[‌]()

variable-declaration


→
[variable-declaration-head](Declarations.md#variable-declaration-head)[variable-name](Declarations.md#variable-name)[initializer](Declarations.md#initializer)[willSet-didSet-block](Declarations.md#willSet-didSet-block)

[‌]()

variable-declaration


→
[variable-declaration-head](Declarations.md#variable-declaration-head)[variable-name](Declarations.md#variable-name)[type-annotation](Types.md#type-annotation)[initializer](Declarations.md#initializer)~opt~[willSet-didSet-block](Declarations.md#willSet-didSet-block)





[‌]()

variable-declaration-head


→
[attributes](Attributes.md#attributes)~opt~[declaration-modifiers](Declarations.md#declaration-modifiers)~opt~`var`

[‌]()

variable-name


→
[identifier](LexicalStructure.md#identifier)





[‌]()

getter-setter-block


→
[code-block](Declarations.md#code-block)

[‌]()

getter-setter-block


→
`{`[getter-clause](Declarations.md#getter-clause)[setter-clause](Declarations.md#setter-clause)~opt~`}`

[‌]()

getter-setter-block


→
`{`[setter-clause](Declarations.md#setter-clause)[getter-clause](Declarations.md#getter-clause)`}`

[‌]()

getter-clause


→
[attributes](Attributes.md#attributes)~opt~`get`[code-block](Declarations.md#code-block)

[‌]()

setter-clause


→
[attributes](Attributes.md#attributes)~opt~`set`[setter-name](Declarations.md#setter-name)~opt~[code-block](Declarations.md#code-block)

[‌]()

setter-name


→
`(`[identifier](LexicalStructure.md#identifier)`)`





[‌]()

getter-setter-keyword-block


→
`{`[getter-keyword-clause](Declarations.md#getter-keyword-clause)[setter-keyword-clause](Declarations.md#setter-keyword-clause)~opt~`}`

[‌]()

getter-setter-keyword-block


→
`{`[setter-keyword-clause](Declarations.md#setter-keyword-clause)[getter-keyword-clause](Declarations.md#getter-keyword-clause)`}`

[‌]()

getter-keyword-clause


→
[attributes](Attributes.md#attributes)~opt~`get`

[‌]()

setter-keyword-clause


→
[attributes](Attributes.md#attributes)~opt~`set`





[‌]()

willSet-didSet-block


→
`{`[willSet-clause](Declarations.md#willSet-clause)[didSet-clause](Declarations.md#didSet-clause)~opt~`}`

[‌]()

willSet-didSet-block


→
`{`[didSet-clause](Declarations.md#didSet-clause)[willSet-clause](Declarations.md#willSet-clause)~opt~`}`

[‌]()

willSet-clause


→
[attributes](Attributes.md#attributes)~opt~`willSet`[setter-name](Declarations.md#setter-name)~opt~[code-block](Declarations.md#code-block)

[‌]()

didSet-clause


→
[attributes](Attributes.md#attributes)~opt~`didSet`[setter-name](Declarations.md#setter-name)~opt~[code-block](Declarations.md#code-block)











[‌]()
### Type Alias Declaration 

A *type alias declaration* introduces a named alias of an existing type into your program. Type alias declarations are declared using the `typealias` keyword and have the following form:




-   ``` 
    typealias name = existing type
    ```



After a type alias is declared, the aliased *name* can be used instead of the *existing type* everywhere in your program. The *existing type* can be a named type or a compound type. Type aliases do not create new types; they simply allow a name to refer to an existing type.

See also [Protocol Associated Type Declaration](Declarations.md#TP40016643-CH34-ID374).



Grammar of a type alias declaration



[‌]()

typealias-declaration


→
[typealias-head](Declarations.md#typealias-head)[typealias-assignment](Declarations.md#typealias-assignment)

[‌]()

typealias-head


→
[attributes](Attributes.md#attributes)~opt~[access-level-modifier](Declarations.md#access-level-modifier)~opt~`typealias`[typealias-name](Declarations.md#typealias-name)

[‌]()

typealias-name


→
[identifier](LexicalStructure.md#identifier)

[‌]()

typealias-assignment


→
`=`[type](Types.md#type)









[‌]()
### Function Declaration 

A *function declaration* introduces a function or method into your program. A function declared in the context of class, structure, enumeration, or protocol is referred to as a *method*. Function declarations are declared using the `func` keyword and have the following form:




-   ``` 
    func function name(parameters) -> return type {
    ```

-   ``` 
        statements
    ```

-   ``` 
    }
    ```



If the function has a return type of `Void`, the return type can be omitted as follows:




-   ``` 
    func function name(parameters) {
    ```

-   ``` 
        statements
    ```

-   ``` 
    }
    ```



The type of each parameter must be included—it can’t be inferred. Although the parameters to a function are constants by default, you can write `let` in front of a parameter’s name to emphasize this behavior. If you write `inout` in front of a parameter’s name, the parameter can be modified inside the scope of the function. In-out parameters are discussed in detail in [In-Out Parameters](Declarations.md#TP40016643-CH34-ID545), below.

Functions can return multiple values using a tuple type as the return type of the function.

A function definition can appear inside another function declaration. This kind of function is known as a *nested function*. For a discussion of nested functions, see [Nested Functions](Functions.md#TP40016643-CH10-ID178).



[‌]()
### Parameter Names 

Function parameters are a comma separated list where each parameter has one of several forms. The order of arguments in a function call must match the order of parameters in the function’s declaration. The simplest entry in a parameter list has the following form:




-   ``` 
    parameter name: parameter type
    ```



A parameter has a local name, which is used within the function body, as well as an external name, which is used as a label for the argument when calling the method. By default, the external name of the first parameter is omitted, and the second and subsequent parameters use their local names as external names. For example:







1.  `func` `f`(`x`: `Int`, `y`: `Int`) -&gt; `Int` { `return` `x` + `y` }
2.  `f`(`1`, `y`: `2`) `// y is labeled, x is not`







You can override the default behavior for how parameter names are used with one of the following forms:




-   ``` 
    external parameter name local parameter name: parameter type
    ```

-   ``` 
    _ local parameter name: parameter type
    ```



A name before the local parameter name gives the parameter an external name, which can be different from the local parameter name. The external parameter name must be used when the function is called. The corresponding argument must have the external name in function or method calls.

An underscore (`_`) before a local parameter name gives that parameter no name to be used in function calls. The corresponding argument must have no name in function or method calls.







1.  `func` `f`(`x` `x`: `Int`, `withY` `y`: `Int`, `_` `z`: `Int`) -&gt; `Int` { `return` `x` + `y` + `z` }
2.  `f`(`x`: `1`, `withY`: `2`, `3`) `// x and y are labeled, z is not`











[‌]()
### In-Out Parameters 

In-out parameters are passed as follows:

1.  When the function is called, the value of the argument is copied.

2.  In the body of the function, the copy is modified.

3.  When the function returns, the copy’s value is assigned to the original argument.

This behavior is known as *copy-in copy-out* or *call by value result*. For example, when a computed property or a property with observers is passed as an in-out parameter, its getter is called as part of the function call and its setter is called as part of the function return.

As an optimization, when the argument is a value stored at a physical address in memory, the same memory location is used both inside and outside the function body. The optimized behavior is known as *call by reference*; it satisfies all of the requirements of the copy-in copy-out model while removing the overhead of copying. Write your code using the model given by copy-in copy-out, without depending on the call-by-reference optimization, so that it behaves correctly with or without the optimization.

Do not access the value that was passed as an in-out argument, even if the original argument is available in the current scope. When the function returns, your changes to the original are overwritten with the value of the copy. Do not depend on the implementation of the call-by-reference optimization to try to keep the changes from being overwritten.

You can’t pass the same argument to multiple in-out parameters because the order in which the copies are written back is not well defined, which means the final value of the original would also not be well defined. For example:







1.  `var` `x` = `10`
2.  `func` `f`(`inout` `a`: `Int`, `inout` `_` `b`: `Int`) {
3.  `    a` += `1`
4.  `    b` += `10`
5.  `}`
6.  `f`(&`x`, &`x`) `// Invalid, in-out arguments alias each other`







There is no copy-out at the end of closures or nested functions. This means if a closure is called after the function returns, any changes that closure makes to the in-out parameters do not get copied back to the original. For example:







1.  `func` `outer`(`inout` `a`: `Int`) -&gt; () -&gt; `Void` {
2.  `    func` `inner`() {
3.  `        a` += `1`
4.  `    }`
5.  `    return` `inner`
6.  `}`
7.  ` `
8.  `var` `x` = `10`
9.  `let` `f` = `outer`(&`x`)
10. `f`()
11. `print`(`x`)
12. `// prints "10"`







The value of `x` is not changed by `inner()` incrementing `a`, because `inner()` is called after `outer()` returns. To change the value of `x`, `inner()` would need to be called before `outer()` returned.

For more discussion and examples of in-out parameters, see [In-Out Parameters](Functions.md#TP40016643-CH10-ID173).





[‌]()
### Special Kinds of Parameters 

Parameters can be ignored, take a variable number of values, and provide default values using the following forms:




-   ``` 
    _ : parameter type
    ```

-   ``` 
    parameter name: parameter type...
    ```

-   ``` 
    parameter name: parameter type = default argument value
    ```



An underscore (`_`) parameter is explicitly ignored and can’t be accessed within the body of the function.

A parameter with a base type name followed immediately by three dots (`...`) is understood as a variadic parameter. A function can have at most one variadic parameter. A variadic parameter is treated as an array that contains elements of the base type name. For instance, the variadic parameter `Int...` is treated as `[Int]`. For an example that uses a variadic parameter, see [Variadic Parameters](Functions.md#TP40016643-CH10-ID171).

A parameter with an equals sign (`=`) and an expression after its type is understood to have a default value of the given expression. The given expression is evaluated when the function is called. If the parameter is omitted when calling the function, the default value is used instead.







1.  `func` `f`(`x`: `Int` = `42`) -&gt; `Int` { `return` `x` }
2.  `f`() `// Valid, uses default value`
3.  `f`(`7`) `// Valid, value provided without its name`
4.  `f`(`x`: `7`) `// Invalid, name and value provided`











[‌]()
### Special Kinds of Methods 

Methods on an enumeration or a structure that modify `self` must be marked with the `mutating` declaration modifier.

Methods that override a superclass method must be marked with the `override` declaration modifier. It’s a compile-time error to override a method without the `override` modifier or to use the `override` modifier on a method that doesn’t override a superclass method.

Methods associated with a type rather than an instance of a type must be marked with the `static` declaration modifier for enumerations and structures or the `class` declaration modifier for classes.





[‌]()
### Throwing Functions and Methods 

Functions and methods that can throw an error must be marked with the `throws` keyword. These functions and methods are known as *throwing functions* and *throwing methods*. They have the following form:




-   ``` 
    func function name(parameters) throws -> return type {
    ```

-   ``` 
        statements
    ```

-   ``` 
    }
    ```



Calls to a throwing function or method must be wrapped in a `try` or `try!` expression (that is, in the scope of a `try` or `try!` operator).

The `throws` keyword is part of a function’s type, and nonthrowing functions are subtypes of throwing functions. As a result, you can use a nonthrowing function in the same places as a throwing one.

You can’t overload a function based only on whether the function can throw an error. That said, you can overload a function based on whether a function *parameter* can throw an error.

A throwing method can’t override a nonthrowing method, and a throwing method can’t satisfy a protocol requirement for a nonthrowing method. That said, a nonthrowing method can override a throwing method, and a nonthrowing method can satisfy a protocol requirement for a throwing.





[‌]()
### Rethrowing Functions and Methods 

A function or method can be declared with the `rethrows` keyword to indicate that it throws an error only if one of it’s function parameters throws an error. These functions and methods are known as *rethrowing functions* and *rethrowing methods*. Rethrowing functions and methods must have at least one throwing function parameter.







1.  `func` `functionWithCallback`(`callback`: () `throws` -&gt; `Int`) `rethrows` {
2.  `    try` `callback`()
3.  `}`







A throwing method can’t override a rethrowing method, and a throwing method can’t satisfy a protocol requirement for a rethrowing method. That said, a rethrowing method can override a throwing method, and a rethrowing method can satisfy a protocol requirement for a throwing method.



Grammar of a function declaration



[‌]()

function-declaration


→
[function-head](Declarations.md#function-head)[function-name](Declarations.md#function-name)[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)~opt~[function-signature](Declarations.md#function-signature)[function-body](Declarations.md#function-body)~opt~





[‌]()

function-head


→
[attributes](Attributes.md#attributes)~opt~[declaration-modifiers](Declarations.md#declaration-modifiers)~opt~`func`

[‌]()

function-name


→

[identifier](LexicalStructure.md#identifier)

[operator](LexicalStructure.md#operator)






[‌]()

function-signature


→
[parameter-clause](Declarations.md#parameter-clause)`throws`~opt~[function-result](Declarations.md#function-result)~opt~

[‌]()

function-signature


→
[parameter-clause](Declarations.md#parameter-clause)`rethrows`[function-result](Declarations.md#function-result)~opt~

[‌]()

function-result


→
`->`[attributes](Attributes.md#attributes)~opt~[type](Types.md#type)

[‌]()

function-body


→
[code-block](Declarations.md#code-block)





[‌]()

parameter-clause


→

`(``)`

`(`[parameter-list](Declarations.md#parameter-list)`)`


[‌]()

parameter-list


→

[parameter](Declarations.md#parameter)

[parameter](Declarations.md#parameter)`,`[parameter-list](Declarations.md#parameter-list)


[‌]()

parameter


→
`let`~opt~[external-parameter-name](Declarations.md#external-parameter-name)~opt~[local-parameter-name](Declarations.md#local-parameter-name)[type-annotation](Types.md#type-annotation)[default-argument-clause](Declarations.md#default-argument-clause)~opt~

[‌]()

parameter


→
`inout`[external-parameter-name](Declarations.md#external-parameter-name)~opt~[local-parameter-name](Declarations.md#local-parameter-name)[type-annotation](Types.md#type-annotation)

[‌]()

parameter


→
[external-parameter-name](Declarations.md#external-parameter-name)~opt~[local-parameter-name](Declarations.md#local-parameter-name)[type-annotation](Types.md#type-annotation)`...`

[‌]()

external-parameter-name


→

[identifier](LexicalStructure.md#identifier)

`_`


[‌]()

local-parameter-name


→

[identifier](LexicalStructure.md#identifier)

`_`


[‌]()

default-argument-clause


→
`=`[expression](Expressions.md#expression)











[‌]()
### Enumeration Declaration 

An *enumeration declaration* introduces a named enumeration type into your program.

Enumeration declarations have two basic forms and are declared using the `enum` keyword. The body of an enumeration declared using either form contains zero or more values—called *enumeration cases*—and any number of declarations, including computed properties, instance methods, type methods, initializers, type aliases, and even other enumeration, structure, and class declarations. Enumeration declarations can’t contain deinitializer or protocol declarations.

Enumeration types can adopt any number of protocols, but can’t inherit from classes, structures, or other enumerations.

Unlike classes and structures, enumeration types do not have an implicitly provided default initializer; all initializers must be declared explicitly. Initializers can delegate to other initializers in the enumeration, but the initialization process is complete only after an initializer assigns one of the enumeration cases to `self`.

Like structures but unlike classes, enumerations are value types; instances of an enumeration are copied when assigned to variables or constants, or when passed as arguments to a function call. For information about value types, see [Structures and Enumerations Are Value Types](ClassesAndStructures.md#TP40016643-CH13-ID88).

You can extend the behavior of an enumeration type with an extension declaration, as discussed in [Extension Declaration](Declarations.md#TP40016643-CH34-ID378).



[‌]()
### Enumerations with Cases of Any Type 

The following form declares an enumeration type that contains enumeration cases of any type:




-   ``` 
    enum enumeration name: adopted protocols {
    ```

-   ``` 
        case enumeration case 1
    ```

-   ``` 
        case enumeration case 2(associated value types)
    ```

-   ``` 
    }
    ```



Enumerations declared in this form are sometimes called *discriminated unions* in other programming languages.

In this form, each case block consists of the `case` keyword followed by one or more enumeration cases, separated by commas. The name of each case must be unique. Each case can also specify that it stores values of a given type. These types are specified in the *associated value types* tuple, immediately following the name of the case.

Enumeration cases that store associated values can be used as functions that create instances of the enumeration with the specified associated values. And just like functions, you can get a reference to an enumeration case and apply it later in your code.







1.  `enum` `Number` {
2.  `    case` `Integer`(`Int`)
3.  `    case` `Real`(`Double`)
4.  `}`
5.  `let` `f` = `Number`.`Integer`
6.  `// f is a function of type (Int) -> Number`
7.  ` `
8.  `// Apply f to create an array of Number instances with integer values`
9.  `let` `evenInts`: \[`Number`\] = \[`0`, `2`, `4`, `6`\].`map`(`f`)







For more information and to see examples of cases with associated value types, see [Associated Values](Enumerations.md#TP40016643-CH12-ID148).



[‌]()
### Enumerations with Indirection 

Enumerations can have a recursive structure, that is, they can have cases with associated values that are instances of the enumeration type itself. However, instances of enumeration types have value semantics, which means they have a fixed layout in memory. To support recursion, the compiler must insert a layer of indirection.

To enable indirection for a particular enumeration case, mark it with the `indirect` declaration modifier.







1.  `enum` `Tree`&lt;`T`&gt; {
2.  `    case` `Empty`
3.  `    indirect` `case` `Node`(`value`: `T`, `left`: `Tree`, `right`: `Tree`)
4.  `}`







To enable indirection for all the cases of an enumeration, mark the entire enumeration with the `indirect` modifier—this is convenient when the enumeration contains many cases that would each need to be marked with the `indirect` modifier.

An enumeration case that’s marked with the `indirect` modifier must have an associated value. An enumeration that is marked with the `indirect` modifier can contain a mixture of cases that have associated values and cases those that don’t. That said, it can’t contain any cases that are also marked with the `indirect` modifier.







[‌]()
### Enumerations with Cases of a Raw-Value Type 

The following form declares an enumeration type that contains enumeration cases of the same basic type:




-   ``` 
    enum enumeration name: raw-value type, adopted protocols {
    ```

-   ``` 
        case enumeration case 1 = raw value 1
    ```

-   ``` 
        case enumeration case 2 = raw value 2
    ```

-   ``` 
    }
    ```



In this form, each case block consists of the `case` keyword, followed by one or more enumeration cases, separated by commas. Unlike the cases in the first form, each case has an underlying value, called a *raw value*, of the same basic type. The type of these values is specified in the *raw-value type* and must represent an integer, floating-point number, string, or single character. In particular, the *raw-value type* must conform to the `Equatable` protocol and one of the following literal-convertible protocols: `IntegerLiteralConvertible` for integer literals, `FloatingPointLiteralConvertible` for floating-point literals, `StringLiteralConvertible` for string literals that contain any number of characters, and `ExtendedGraphemeClusterLiteralConvertible` for string literals that contain only a single character. Each case must have a unique name and be assigned a unique raw value.

If the raw-value type is specified as `Int` and you don’t assign a value to the cases explicitly, they are implicitly assigned the values `0`, `1`, `2`, and so on. Each unassigned case of type `Int` is implicitly assigned a raw value that is automatically incremented from the raw value of the previous case.







1.  `enum` `ExampleEnum`: `Int` {
2.  `    case` `A`, `B`, `C` = `5`, `D`
3.  `}`







In the above example, the raw value of `ExampleEnum.A` is `0` and the value of `ExampleEnum.B` is `1`. And because the value of `ExampleEnum.C` is explicitly set to `5`, the value of `ExampleEnum.D` is automatically incremented from `5` and is therefore `6`.

If the raw-value type is specified as `String` and you don’t assign values to the cases explicitly, each unassigned case is implicitly assigned a string with the same text as the name of that case.







1.  `enum` `WeekendDay`: `String` {
2.  `    case` `Saturday`, `Sunday`
3.  `}`







In the above example, the raw value of `WeekendDay.Saturday` is `"Saturday"`, and the raw value of `WeekendDay.Sunday` is `"Sunday"`.

Enumerations that have cases of a raw-value type implicitly conform to the `RawRepresentable` protocol, defined in the Swift standard library. As a result, they have a `rawValue` property and a failable initializer with the signature `init?(rawValue: RawValue)`. You can use the `rawValue` property to access the raw value of an enumeration case, as in `ExampleEnum.B.rawValue`. You can also use a raw value to find a corresponding case, if there is one, by calling the enumeration’s failable initializer, as in `ExampleEnum(rawValue: 5)`, which returns an optional case. For more information and to see examples of cases with raw-value types, see [Raw Values](Enumerations.md#TP40016643-CH12-ID149).





[‌]()
### Accessing Enumeration Cases 

To reference the case of an enumeration type, use dot (`.`) syntax, as in `EnumerationType.EnumerationCase`. When the enumeration type can be inferred from context, you can omit it (the dot is still required), as described in [Enumeration Syntax](Enumerations.md#TP40016643-CH12-ID146) and [Implicit Member Expression](Expressions.md#TP40016643-CH32-ID394).

To check the values of enumeration cases, use a `switch` statement, as shown in [Matching Enumeration Values with a Switch Statement](Enumerations.md#TP40016643-CH12-ID147). The enumeration type is pattern-matched against the enumeration case patterns in the case blocks of the `switch` statement, as described in [Enumeration Case Pattern](Patterns.md#TP40016643-CH36-ID424).



Grammar of an enumeration declaration



[‌]()

enum-declaration


→
[attributes](Attributes.md#attributes)~opt~[access-level-modifier](Declarations.md#access-level-modifier)~opt~[union-style-enum](Declarations.md#union-style-enum)

[‌]()

enum-declaration


→
[attributes](Attributes.md#attributes)~opt~[access-level-modifier](Declarations.md#access-level-modifier)~opt~[raw-value-style-enum](Declarations.md#raw-value-style-enum)





[‌]()

union-style-enum


→
`indirect`~opt~`enum`[enum-name](Declarations.md#enum-name)[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)~opt~[type-inheritance-clause](Types.md#type-inheritance-clause)~opt~`{`[union-style-enum-members](Declarations.md#union-style-enum-members)~opt~`}`

[‌]()

union-style-enum-members


→
[union-style-enum-member](Declarations.md#union-style-enum-member)[union-style-enum-members](Declarations.md#union-style-enum-members)~opt~

[‌]()

union-style-enum-member


→

[declaration](Declarations.md#declaration)

[union-style-enum-case-clause](Declarations.md#union-style-enum-case-clause)


[‌]()

union-style-enum-case-clause


→
[attributes](Attributes.md#attributes)~opt~`indirect`~opt~`case`[union-style-enum-case-list](Declarations.md#union-style-enum-case-list)

[‌]()

union-style-enum-case-list


→

[union-style-enum-case](Declarations.md#union-style-enum-case)

[union-style-enum-case](Declarations.md#union-style-enum-case)`,`[union-style-enum-case-list](Declarations.md#union-style-enum-case-list)


[‌]()

union-style-enum-case


→
[enum-case-name](Declarations.md#enum-case-name)[tuple-type](Types.md#tuple-type)~opt~

[‌]()

enum-name


→
[identifier](LexicalStructure.md#identifier)

[‌]()

enum-case-name


→
[identifier](LexicalStructure.md#identifier)





[‌]()

raw-value-style-enum


→
`enum`[enum-name](Declarations.md#enum-name)[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)~opt~[type-inheritance-clause](Types.md#type-inheritance-clause)`{`[raw-value-style-enum-members](Declarations.md#raw-value-style-enum-members)`}`

[‌]()

raw-value-style-enum-members


→
[raw-value-style-enum-member](Declarations.md#raw-value-style-enum-member)[raw-value-style-enum-members](Declarations.md#raw-value-style-enum-members)~opt~

[‌]()

raw-value-style-enum-member


→

[declaration](Declarations.md#declaration)

[raw-value-style-enum-case-clause](Declarations.md#raw-value-style-enum-case-clause)


[‌]()

raw-value-style-enum-case-clause


→
[attributes](Attributes.md#attributes)~opt~`case`[raw-value-style-enum-case-list](Declarations.md#raw-value-style-enum-case-list)

[‌]()

raw-value-style-enum-case-list


→

[raw-value-style-enum-case](Declarations.md#raw-value-style-enum-case)

[raw-value-style-enum-case](Declarations.md#raw-value-style-enum-case)`,`[raw-value-style-enum-case-list](Declarations.md#raw-value-style-enum-case-list)


[‌]()

raw-value-style-enum-case


→
[enum-case-name](Declarations.md#enum-case-name)[raw-value-assignment](Declarations.md#raw-value-assignment)~opt~

[‌]()

raw-value-assignment


→
`=`[raw-value-literal](Declarations.md#raw-value-literal)

[‌]()

raw-value-literal


→

[numeric-literal](LexicalStructure.md#numeric-literal)

[static-string-literal](LexicalStructure.md#static-string-literal)

[boolean-literal](LexicalStructure.md#boolean-literal)












[‌]()
### Structure Declaration 

A *structure declaration* introduces a named structure type into your program. Structure declarations are declared using the `struct` keyword and have the following form:




-   ``` 
    struct structure name: adopted protocols {
    ```

-   ``` 
        declarations
    ```

-   ``` 
    }
    ```



The body of a structure contains zero or more *declarations*. These *declarations* can include both stored and computed properties, type properties, instance methods, type methods, initializers, subscripts, type aliases, and even other structure, class, and enumeration declarations. Structure declarations can’t contain deinitializer or protocol declarations. For a discussion and several examples of structures that include various kinds of declarations, see [Classes and Structures](ClassesAndStructures.md).

Structure types can adopt any number of protocols, but can’t inherit from classes, enumerations, or other structures.

There are three ways create an instance of a previously declared structure:

-   Call one of the initializers declared within the structure, as described in [Initializers](Initialization.md#TP40016643-CH18-ID205).

-   If no initializers are declared, call the structure’s memberwise initializer, as described in [Memberwise Initializers for Structure Types](Initialization.md#TP40016643-CH18-ID214).

-   If no initializers are declared, and all properties of the structure declaration were given initial values, call the structure’s default initializer, as described in [Default Initializers](Initialization.md#TP40016643-CH18-ID213).

The process of initializing a structure’s declared properties is described in [Initialization](Initialization.md).

Properties of a structure instance can be accessed using dot (`.`) syntax, as described in [Accessing Properties](ClassesAndStructures.md#TP40016643-CH13-ID86).

Structures are value types; instances of a structure are copied when assigned to variables or constants, or when passed as arguments to a function call. For information about value types, see [Structures and Enumerations Are Value Types](ClassesAndStructures.md#TP40016643-CH13-ID88).

You can extend the behavior of a structure type with an extension declaration, as discussed in [Extension Declaration](Declarations.md#TP40016643-CH34-ID378).



Grammar of a structure declaration



[‌]()

struct-declaration


→
[attributes](Attributes.md#attributes)~opt~[access-level-modifier](Declarations.md#access-level-modifier)~opt~`struct`[struct-name](Declarations.md#struct-name)[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)~opt~[type-inheritance-clause](Types.md#type-inheritance-clause)~opt~[struct-body](Declarations.md#struct-body)

[‌]()

struct-name


→
[identifier](LexicalStructure.md#identifier)

[‌]()

struct-body


→
`{`[declarations](Declarations.md#declarations)~opt~`}`









[‌]()
### Class Declaration 

A *class declaration* introduces a named class type into your program. Class declarations are declared using the `class` keyword and have the following form:




-   ``` 
    class class name: superclass, adopted protocols {
    ```

-   ``` 
        declarations
    ```

-   ``` 
    }
    ```



The body of a class contains zero or more *declarations*. These *declarations* can include both stored and computed properties, instance methods, type methods, initializers, a single deinitializer, subscripts, type aliases, and even other class, structure, and enumeration declarations. Class declarations can’t contain protocol declarations. For a discussion and several examples of classes that include various kinds of declarations, see [Classes and Structures](ClassesAndStructures.md).

A class type can inherit from only one parent class, its *superclass*, but can adopt any number of protocols. The *superclass* appears first after the *class name* and colon, followed by any *adopted protocols*. Generic classes can inherit from other generic and nongeneric classes, but a nongeneric class can inherit only from other nongeneric classes. When you write the name of a generic superclass class after the colon, you must include the full name of that generic class, including its generic parameter clause.

As discussed in [Initializer Declaration](Declarations.md#TP40016643-CH34-ID375), classes can have designated and convenience initializers. The designated initializer of a class must initialize all of the class’s declared properties and it must do so before calling any of its superclass’s designated initializers.

A class can override properties, methods, subscripts, and initializers of its superclass. Overridden properties, methods, subscripts, and designated initializers must be marked with the `override` declaration modifier.

To require that subclasses implement a superclass’s initializer, mark the superclass’s initializer with the `required` declaration modifier. The subclass’s implementation of that initializer must also be marked with the `required` declaration modifier.

Although properties and methods declared in the *superclass* are inherited by the current class, designated initializers declared in the *superclass* are not. That said, if the current class overrides all of the superclass’s designated initializers, it inherits the superclass’s convenience initializers. Swift classes do not inherit from a universal base class.

There are two ways create an instance of a previously declared class:

-   Call one of the initializers declared within the class, as described in [Initializers](Initialization.md#TP40016643-CH18-ID205).

-   If no initializers are declared, and all properties of the class declaration were given initial values, call the class’s default initializer, as described in [Default Initializers](Initialization.md#TP40016643-CH18-ID213).

Access properties of a class instance with dot (`.`) syntax, as described in [Accessing Properties](ClassesAndStructures.md#TP40016643-CH13-ID86).

Classes are reference types; instances of a class are referred to, rather than copied, when assigned to variables or constants, or when passed as arguments to a function call. For information about reference types, see [Structures and Enumerations Are Value Types](ClassesAndStructures.md#TP40016643-CH13-ID88).

You can extend the behavior of a class type with an extension declaration, as discussed in [Extension Declaration](Declarations.md#TP40016643-CH34-ID378).



Grammar of a class declaration



[‌]()

class-declaration


→
[attributes](Attributes.md#attributes)~opt~[access-level-modifier](Declarations.md#access-level-modifier)~opt~`class`[class-name](Declarations.md#class-name)[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)~opt~[type-inheritance-clause](Types.md#type-inheritance-clause)~opt~[class-body](Declarations.md#class-body)

[‌]()

class-name


→
[identifier](LexicalStructure.md#identifier)

[‌]()

class-body


→
`{`[declarations](Declarations.md#declarations)~opt~`}`









[‌]()
### Protocol Declaration 

A *protocol declaration* introduces a named protocol type into your program. Protocol declarations are declared at global scope using the `protocol` keyword and have the following form:




-   ``` 
    protocol protocol name: inherited protocols {
    ```

-   ``` 
        protocol member declarations
    ```

-   ``` 
    }
    ```



The body of a protocol contains zero or more *protocol member declarations*, which describe the conformance requirements that any type adopting the protocol must fulfill. In particular, a protocol can declare that conforming types must implement certain properties, methods, initializers, and subscripts. Protocols can also declare special kinds of type aliases, called *associated types*, that can specify relationships among the various declarations of the protocol. Protocol declarations can’t contain class, structure, enumeration, or other protocol declarations. The *protocol member declarations* are discussed in detail below.

Protocol types can inherit from any number of other protocols. When a protocol type inherits from other protocols, the set of requirements from those other protocols are aggregated, and any type that inherits from the current protocol must conform to all those requirements. For an example of how to use protocol inheritance, see [Protocol Inheritance](Protocols.md#TP40016643-CH25-ID280).



Note

You can also aggregate the conformance requirements of multiple protocols using protocol composition types, as described in [Protocol Composition Type](Types.md#TP40016643-CH31-ID454) and [Protocol Composition](Protocols.md#TP40016643-CH25-ID282).



You can add protocol conformance to a previously declared type by adopting the protocol in an extension declaration of that type. In the extension, you must implement all of the adopted protocol’s requirements. If the type already implements all of the requirements, you can leave the body of the extension declaration empty.

By default, types that conform to a protocol must implement all properties, methods, and subscripts declared in the protocol. That said, you can mark these protocol member declarations with the `optional` declaration modifier to specify that their implementation by a conforming type is optional. The `optional` modifier can be applied only to protocols that are marked with the `objc` attribute. As a result, only class types can adopt and conform to a protocol that contains optional member requirements. For more information about how to use the `optional` declaration modifier and for guidance about how to access optional protocol members—for example, when you’re not sure whether a conforming type implements them—see [Optional Protocol Requirements](Protocols.md#TP40016643-CH25-ID284).

To restrict the adoption of a protocol to class types only, mark the protocol with the `class` requirement by writing the `class` keyword as the first item in the *inherited protocols* list after the colon. For example, the following protocol can be adopted only by class types:







1.  `protocol` `SomeProtocol`: `class` {
2.  `    /* Protocol members go here */`
3.  `}`







Any protocol that inherits from a protocol that’s marked with the `class` requirement can likewise be adopted only by class types.



Note

If a protocol is marked with the `objc` attribute, the `class` requirement is implicitly applied to that protocol; there’s no need to mark the protocol with the `class` requirement explicitly.



Protocols are named types, and thus they can appear in all the same places in your code as other named types, as discussed in [Protocols as Types](Protocols.md#TP40016643-CH25-ID275). However, you can’t construct an instance of a protocol, because protocols do not actually provide the implementations for the requirements they specify.

You can use protocols to declare which methods a delegate of a class or structure should implement, as described in [Delegation](Protocols.md#TP40016643-CH25-ID276).



Grammar of a protocol declaration



[‌]()

protocol-declaration


→
[attributes](Attributes.md#attributes)~opt~[access-level-modifier](Declarations.md#access-level-modifier)~opt~`protocol`[protocol-name](Declarations.md#protocol-name)[type-inheritance-clause](Types.md#type-inheritance-clause)~opt~[protocol-body](Declarations.md#protocol-body)

[‌]()

protocol-name


→
[identifier](LexicalStructure.md#identifier)

[‌]()

protocol-body


→
`{`[protocol-member-declarations](Declarations.md#protocol-member-declarations)~opt~`}`





[‌]()

protocol-member-declaration


→
[protocol-property-declaration](Declarations.md#protocol-property-declaration)

[‌]()

protocol-member-declaration


→
[protocol-method-declaration](Declarations.md#protocol-method-declaration)

[‌]()

protocol-member-declaration


→
[protocol-initializer-declaration](Declarations.md#protocol-initializer-declaration)

[‌]()

protocol-member-declaration


→
[protocol-subscript-declaration](Declarations.md#protocol-subscript-declaration)

[‌]()

protocol-member-declaration


→
[protocol-associated-type-declaration](Declarations.md#protocol-associated-type-declaration)

[‌]()

protocol-member-declarations


→
[protocol-member-declaration](Declarations.md#protocol-member-declaration)[protocol-member-declarations](Declarations.md#protocol-member-declarations)~opt~







[‌]()
### Protocol Property Declaration 

Protocols declare that conforming types must implement a property by including a *protocol property declaration* in the body of the protocol declaration. Protocol property declarations have a special form of a variable declaration:




-   ``` 
    var property name: type { get set }
    ```



As with other protocol member declarations, these property declarations declare only the getter and setter requirements for types that conform to the protocol. As a result, you don’t implement the getter or setter directly in the protocol in which it is declared.

The getter and setter requirements can be satisfied by a conforming type in a variety of ways. If a property declaration includes both the `get` and `set` keywords, a conforming type can implement it with a stored variable property or a computed property that is both readable and writeable (that is, one that implements both a getter and a setter). However, that property declaration can’t be implemented as a constant property or a read-only computed property. If a property declaration includes only the `get` keyword, it can be implemented as any kind of property. For examples of conforming types that implement the property requirements of a protocol, see [Property Requirements](Protocols.md#TP40016643-CH25-ID269).

See also [Variable Declaration](Declarations.md#TP40016643-CH34-ID356).



Grammar of a protocol property declaration



[‌]()

protocol-property-declaration


→
[variable-declaration-head](Declarations.md#variable-declaration-head)[variable-name](Declarations.md#variable-name)[type-annotation](Types.md#type-annotation)[getter-setter-keyword-block](Declarations.md#getter-setter-keyword-block)









[‌]()
### Protocol Method Declaration 

Protocols declare that conforming types must implement a method by including a protocol method declaration in the body of the protocol declaration. Protocol method declarations have the same form as function declarations, with two exceptions: They don’t include a function body, and you can’t provide any default parameter values as part of the function declaration. For examples of conforming types that implement the method requirements of a protocol, see [Method Requirements](Protocols.md#TP40016643-CH25-ID270).

To declare a class or static method requirement in a protocol declaration, mark the method declaration with the `static` declaration modifier. Classes that implement this method declare the method with the `class` modifier. Structures that implement it must declare the method with the `static` declaration modifier instead. If you’re implementing the method in an extension, use the `class` modifier if you’re extending a class and the `static` modifier if you’re extending a structure.

See also [Function Declaration](Declarations.md#TP40016643-CH34-ID362).



Grammar of a protocol method declaration



[‌]()

protocol-method-declaration


→
[function-head](Declarations.md#function-head)[function-name](Declarations.md#function-name)[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)~opt~[function-signature](Declarations.md#function-signature)









[‌]()
### Protocol Initializer Declaration 

Protocols declare that conforming types must implement an initializer by including a protocol initializer declaration in the body of the protocol declaration. Protocol initializer declarations have the same form as initializer declarations, except they don’t include the initializer’s body.

A conforming type can satisfy a nonfailable protocol initializer requirement by implementing a nonfailable initializer or an `init!` failable initializer. A conforming type can satisfy a failable protocol initializer requirement by implementing any kind of initializer.

When a class implements an initializer to satisfy a protocol’s initializer requirement, the initializer must be marked with the `required` declaration modifier if the class is not already marked with the `final` declaration modifier.

See also [Initializer Declaration](Declarations.md#TP40016643-CH34-ID375).



Grammar of a protocol initializer declaration



[‌]()

protocol-initializer-declaration


→
[initializer-head](Declarations.md#initializer-head)[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)~opt~[parameter-clause](Declarations.md#parameter-clause)`throws`~opt~

[‌]()

protocol-initializer-declaration


→
[initializer-head](Declarations.md#initializer-head)[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)~opt~[parameter-clause](Declarations.md#parameter-clause)`rethrows`









[‌]()
### Protocol Subscript Declaration 

Protocols declare that conforming types must implement a subscript by including a protocol subscript declaration in the body of the protocol declaration. Protocol subscript declarations have a special form of a subscript declaration:




-   ``` 
    subscript (parameters) -> return type { get set }
    ```



Subscript declarations only declare the minimum getter and setter implementation requirements for types that conform to the protocol. If the subscript declaration includes both the `get` and `set` keywords, a conforming type must implement both a getter and a setter clause. If the subscript declaration includes only the `get` keyword, a conforming type must implement *at least* a getter clause and optionally can implement a setter clause.

See also [Subscript Declaration](Declarations.md#TP40016643-CH34-ID379).



Grammar of a protocol subscript declaration



[‌]()

protocol-subscript-declaration


→
[subscript-head](Declarations.md#subscript-head)[subscript-result](Declarations.md#subscript-result)[getter-setter-keyword-block](Declarations.md#getter-setter-keyword-block)









[‌]()
### Protocol Associated Type Declaration 

Protocols declare associated types using the `typealias` keyword. An associated type provides an alias for a type that is used as part of a protocol’s declaration. Associated types are similar to type parameters in generic parameter clauses, but they’re associated with `Self` in the protocol in which they’re declared. In that context, `Self` refers to the eventual type that conforms to the protocol. For more information and examples, see [Associated Types](Generics.md#TP40016643-CH26-ID189).

See also [Type Alias Declaration](Declarations.md#TP40016643-CH34-ID361).



Grammar of a protocol associated type declaration



[‌]()

protocol-associated-type-declaration


→
[typealias-head](Declarations.md#typealias-head)[type-inheritance-clause](Types.md#type-inheritance-clause)~opt~[typealias-assignment](Declarations.md#typealias-assignment)~opt~











[‌]()
### Initializer Declaration 

An *initializer declaration* introduces an initializer for a class, structure, or enumeration into your program. Initializer declarations are declared using the `init` keyword and have two basic forms.

Structure, enumeration, and class types can have any number of initializers, but the rules and associated behavior for class initializers are different. Unlike structures and enumerations, classes have two kinds of initializers: designated initializers and convenience initializers, as described in [Initialization](Initialization.md).

The following form declares initializers for structures, enumerations, and designated initializers of classes:




-   ``` 
    init(parameters) {
    ```

-   ``` 
        statements
    ```

-   ``` 
    }
    ```



A designated initializer of a class initializes all of the class’s properties directly. It can’t call any other initializers of the same class, and if the class has a superclass, it must call one of the superclass’s designated initializers. If the class inherits any properties from its superclass, one of the superclass’s designated initializers must be called before any of these properties can be set or modified in the current class.

Designated initializers can be declared in the context of a class declaration only and therefore can’t be added to a class using an extension declaration.

Initializers in structures and enumerations can call other declared initializers to delegate part or all of the initialization process.

To declare convenience initializers for a class, mark the initializer declaration with the `convenience` declaration modifier.




-   ``` 
    convenience init(parameters) {
    ```

-   ``` 
        statements
    ```

-   ``` 
    }
    ```



Convenience initializers can delegate the initialization process to another convenience initializer or to one of the class’s designated initializers. That said, the initialization processes must end with a call to a designated initializer that ultimately initializes the class’s properties. Convenience initializers can’t call a superclass’s initializers.

You can mark designated and convenience initializers with the `required` declaration modifier to require that every subclass implement the initializer. A subclass’s implementation of that initializer must also be marked with the `required` declaration modifier.

By default, initializers declared in a superclass are not inherited by subclasses. That said, if a subclass initializes all of its stored properties with default values and doesn’t define any initializers of its own, it inherits all of the superclass’s initializers. If the subclass overrides all of the superclass’s designated initializers, it inherits the superclass’s convenience initializers.

As with methods, properties, and subscripts, you need to mark overridden designated initializers with the `override` declaration modifier.



Note

If you mark an initializer with the `required` declaration modifier, you don’t also mark the initializer with the `override` modifier when you override the required initializer in a subclass.



Just like functions and methods, initializers can throw or rethrow errors. And just like functions and methods, you use the `throws` or `rethrows` keyword after an initializer’s parameters to indicate the appropriate behavior.

To see examples of initializers in various type declarations, see [Initialization](Initialization.md).



[‌]()
### Failable Initializers 

A *failable initializer* is a type of initializer that produces an optional instance or an implicitly unwrapped optional instance of the type the initializer is declared on. As a result, a failable initializer can return `nil` to indicate that initialization failed.

To declare a failable initializer that produces an optional instance, append a question mark to the `init` keyword in the initializer declaration (`init?`). To declare a failable initializer that produces an implicitly unwrapped optional instance, append an exclamation mark instead (`init!`). The example below shows an `init?` failable initializer that produces an optional instance of a structure.







1.  `struct` `SomeStruct` {
2.  `    let` `string`: `String`
3.  `    // produces an optional instance of 'SomeStruct'`
4.  `    init`?(`input`: `String`) {
5.  `        if` `input`.`isEmpty` {
6.  `            // discard 'self' and return 'nil'`
7.  `            return` `nil`
8.  `        }`
9.  `        string` = `input`
10. `    }`
11. `}`







You call an `init?` failable initializer in the same way that you call a nonfailable initializer, except that you must deal with the optionality of the result.







1.  `if` `let` `actualInstance` = `SomeStruct`(`input`: `"Hello"`) {
2.  `    // do something with the instance of 'SomeStruct'`
3.  `} else` {
4.  `    // initialization of 'SomeStruct' failed and the initializer returned 'nil'`
5.  `}`







A failable initializer of a structure or an enumeration can return `nil` at any point in the implementation of the initializer’s body. A failable initializer of a class, however, can return `nil` only after all stored properties of that class are initialized and `self.init` or `super.init` is called (that is, any initializer delegation is performed).

A failable initializer can delegate to any kind of initializer. A nonfailable initializer can delegate to another nonfailable initializer or to an `init!` failable initializer. A nonfailable initializer can delegate to an `init?` failable initializer by force-unwrapping the result of the superclass’s initializer—for example, by writing `super.init()!`.

Initialization failure propagates through initializer delegation. Specifically, if a failable initializer delegates to an initializer that fails and returns `nil`, then the initializer that delegated also fails and implicitly returns `nil`. If a nonfailable initializer delegates to an `init!` failable initializer that fails and returns `nil`, then a runtime error is raised (as if you used the `!` operator to unwrap an optional that has a `nil` value).

A failable designated initializer can be overridden in a subclass by any kind of designated initializer. A nonfailable designated initializer can be overridden in a subclass by a nonfailable designated initializer only.

For more information and to see examples of failable initializers, see [Failable Initializers](Initialization.md#TP40016643-CH18-ID224).



Grammar of an initializer declaration



[‌]()

initializer-declaration


→
[initializer-head](Declarations.md#initializer-head)[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)~opt~[parameter-clause](Declarations.md#parameter-clause)`throws`~opt~[initializer-body](Declarations.md#initializer-body)

[‌]()

initializer-declaration


→
[initializer-head](Declarations.md#initializer-head)[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)~opt~[parameter-clause](Declarations.md#parameter-clause)`rethrows`[initializer-body](Declarations.md#initializer-body)

[‌]()

initializer-head


→
[attributes](Attributes.md#attributes)~opt~[declaration-modifiers](Declarations.md#declaration-modifiers)~opt~`init`

[‌]()

initializer-head


→
[attributes](Attributes.md#attributes)~opt~[declaration-modifiers](Declarations.md#declaration-modifiers)~opt~`init``?`

[‌]()

initializer-head


→
[attributes](Attributes.md#attributes)~opt~[declaration-modifiers](Declarations.md#declaration-modifiers)~opt~`init``!`

[‌]()

initializer-body


→
[code-block](Declarations.md#code-block)











[‌]()
### Deinitializer Declaration 

A *deinitializer declaration* declares a deinitializer for a class type. Deinitializers take no parameters and have the following form:




-   ``` 
    deinit {
    ```

-   ``` 
        statements
    ```

-   ``` 
    }
    ```



A deinitializer is called automatically when there are no longer any references to a class object, just before the class object is deallocated. A deinitializer can be declared only in the body of a class declaration—but not in an extension of a class—and each class can have at most one.

A subclass inherits its superclass’s deinitializer, which is implicitly called just before the subclass object is deallocated. The subclass object is not deallocated until all deinitializers in its inheritance chain have finished executing.

Deinitializers are not called directly.

For an example of how to use a deinitializer in a class declaration, see [Deinitialization](Deinitialization.md).



Grammar of a deinitializer declaration



[‌]()

deinitializer-declaration


→
[attributes](Attributes.md#attributes)~opt~`deinit`[code-block](Declarations.md#code-block)









[‌]()
### Extension Declaration 

An *extension declaration* allows you to extend the behavior of existing class, structure, and enumeration types. Extension declarations are declared using the `extension` keyword and have the following form:




-   ``` 
    extension type name: adopted protocols {
    ```

-   ``` 
        declarations
    ```

-   ``` 
    }
    ```



The body of an extension declaration contains zero or more *declarations*. These *declarations* can include computed properties, computed type properties, instance methods, type methods, initializers, subscript declarations, and even class, structure, and enumeration declarations. Extension declarations can’t contain deinitializer or protocol declarations, stored properties, property observers, or other extension declarations. For a discussion and several examples of extensions that include various kinds of declarations, see [Extensions](Extensions.md).

Extension declarations can add protocol conformance to an existing class, structure, and enumeration type in the *adopted protocols*. Extension declarations can’t add class inheritance to an existing class, and therefore you can specify only a list of protocols after the *type name* and colon.

Properties, methods, and initializers of an existing type can’t be overridden in an extension of that type.

Extension declarations can contain initializer declarations. That said, if the type you’re extending is defined in another module, an initializer declaration must delegate to an initializer already defined in that module to ensure members of that type are properly initialized.



Grammar of an extension declaration



[‌]()

extension-declaration


→
[access-level-modifier](Declarations.md#access-level-modifier)~opt~`extension`[type-identifier](Types.md#type-identifier)[type-inheritance-clause](Types.md#type-inheritance-clause)~opt~[extension-body](Declarations.md#extension-body)

[‌]()

extension-body


→
`{`[declarations](Declarations.md#declarations)~opt~`}`









[‌]()
### Subscript Declaration 

A *subscript* declaration allows you to add subscripting support for objects of a particular type and are typically used to provide a convenient syntax for accessing the elements in a collection, list, or sequence. Subscript declarations are declared using the `subscript` keyword and have the following form:




-   ``` 
    subscript (parameters) -> return type {
    ```

-   ``` 
        get {
    ```

-   ``` 
            statements
    ```

-   ``` 
        }
    ```

-   ``` 
        set(setter name) {
    ```

-   ``` 
            statements
    ```

-   ``` 
        }
    ```

-   ``` 
    }
    ```



Subscript declarations can appear only in the context of a class, structure, enumeration, extension, or protocol declaration.

The *parameters* specify one or more indexes used to access elements of the corresponding type in a subscript expression (for example, the `i` in the expression `object[i]`). Although the indexes used to access the elements can be of any type, each parameter must include a type annotation to specify the type of each index. The *return type* specifies the type of the element being accessed.

As with computed properties, subscript declarations support reading and writing the value of the accessed elements. The getter is used to read the value, and the setter is used to write the value. The setter clause is optional, and when only a getter is needed, you can omit both clauses and simply return the requested value directly. That said, if you provide a setter clause, you must also provide a getter clause.

The *setter name* and enclosing parentheses are optional. If you provide a setter name, it is used as the name of the parameter to the setter. If you do not provide a setter name, the default parameter name to the setter is `value`. The type of the *setter name* must be the same as the *return type*.

You can overload a subscript declaration in the type in which it is declared, as long as the *parameters* or the *return type* differ from the one you’re overloading. You can also override a subscript declaration inherited from a superclass. When you do so, you must mark the overridden subscript declaration with the `override` declaration modifier.

You can also declare subscripts in the context of a protocol declaration, as described in [Protocol Subscript Declaration](Declarations.md#TP40016643-CH34-ID373).

For more information about subscripting and to see examples of subscript declarations, see [Subscripts](Subscripts.md).



Grammar of a subscript declaration



[‌]()

subscript-declaration


→
[subscript-head](Declarations.md#subscript-head)[subscript-result](Declarations.md#subscript-result)[code-block](Declarations.md#code-block)

[‌]()

subscript-declaration


→
[subscript-head](Declarations.md#subscript-head)[subscript-result](Declarations.md#subscript-result)[getter-setter-block](Declarations.md#getter-setter-block)

[‌]()

subscript-declaration


→
[subscript-head](Declarations.md#subscript-head)[subscript-result](Declarations.md#subscript-result)[getter-setter-keyword-block](Declarations.md#getter-setter-keyword-block)

[‌]()

subscript-head


→
[attributes](Attributes.md#attributes)~opt~[declaration-modifiers](Declarations.md#declaration-modifiers)~opt~`subscript`[parameter-clause](Declarations.md#parameter-clause)

[‌]()

subscript-result


→
`->`[attributes](Attributes.md#attributes)~opt~[type](Types.md#type)









[‌]()
### Operator Declaration 

An *operator declaration* introduces a new infix, prefix, or postfix operator into your program and is declared using the `operator` keyword.

You can declare operators of three different fixities: infix, prefix, and postfix. The *fixity* of an operator specifies the relative position of an operator to its operands.

There are three basic forms of an operator declaration, one for each fixity. The fixity of the operator is specified by marking the operator declaration with the `infix`, `prefix`, or `postfix` declaration modifier before the `operator` keyword. In each form, the name of the operator can contain only the operator characters defined in [Operators](LexicalStructure.md#TP40016643-CH30-ID418).

The following form declares a new infix operator:




-   ``` 
    infix operator operator name {
    ```

-   ``` 
        precedence precedence level
    ```

-   ``` 
        associativity associativity
    ```

-   ``` 
    }
    ```



An *infix operator* is a binary operator that is written between its two operands, such as the familiar addition operator (`+`) in the expression `1 + 2`.

Infix operators can optionally specify a precedence, associativity, or both.

The *precedence* of an operator specifies how tightly an operator binds to its operands in the absence of grouping parentheses. You specify the precedence of an operator by writing the context-sensitive `precedence` keyword followed by the *precedence level*. The *precedence level* can be any whole number (decimal integer) from 0 to 255; unlike decimal integer literals, it can’t contain any underscore characters. Although the precedence level is a specific number, it is significant only relative to another operator. That is, when two operators compete with each other for their operands, such as in the expression `2 + 3 * 5`, the operator with the higher precedence level binds more tightly to its operands.

The *associativity* of an operator specifies how a sequence of operators with the same precedence level are grouped together in the absence of grouping parentheses. You specify the associativity of an operator by writing the context-sensitive `associativity` keyword followed by the *associativity*, which is one of the context-sensitive keywords `left`, `right`, or `none`. Operators that are left-associative group left-to-right. For example, the subtraction operator (`-`) is left-associative, and therefore the expression `4 - 5 - 6` is grouped as `(4 - 5) - 6` and evaluates to `-7`. Operators that are right-associative group right-to-left, and operators that are specified with an associativity of `none` don’t associate at all. Nonassociative operators of the same precedence level can’t appear adjacent to each to other. For example, `1 < 2 < 3` is not a valid expression.

Infix operators that are declared without specifying a precedence or associativity are initialized with a precedence level of 100 and an associativity of `none`.

The following form declares a new prefix operator:




-   ``` 
    prefix operator operator name {}
    ```



A *prefix operator* is a unary operator that is written immediately before its operand, such as the prefix increment operator (`++`) is in the expression `++i`.

Prefix operators declarations don’t specify a precedence level. Prefix operators are nonassociative.

The following form declares a new postfix operator:




-   ``` 
    postfix operator operator name {}
    ```



A *postfix operator* is a unary operator that is written immediately after its operand, such as the postfix increment operator (`++`) is in the expression `i++`.

As with prefix operators, postfix operator declarations don’t specify a precedence level. Postfix operators are nonassociative.

After declaring a new operator, you implement it by declaring a function that has the same name as the operator. If you’re implementing a prefix or postfix operator, you must also mark that function declaration with the corresponding `prefix` or `postfix` declaration modifier. If you’re implementing an infix operator, you don’t mark that function declaration with the `infix` declaration modifier. To see an example of how to create and implement a new operator, see [Custom Operators](AdvancedOperators.md#TP40016643-CH27-ID46).



Grammar of an operator declaration



[‌]()

operator-declaration


→

[prefix-operator-declaration](Declarations.md#prefix-operator-declaration)

[postfix-operator-declaration](Declarations.md#postfix-operator-declaration)

[infix-operator-declaration](Declarations.md#infix-operator-declaration)






[‌]()

prefix-operator-declaration


→
`prefix``operator`[operator](LexicalStructure.md#operator)`{``}`

[‌]()

postfix-operator-declaration


→
`postfix``operator`[operator](LexicalStructure.md#operator)`{``}`

[‌]()

infix-operator-declaration


→
`infix``operator`[operator](LexicalStructure.md#operator)`{`[infix-operator-attributes](Declarations.md#infix-operator-attributes)~opt~`}`





[‌]()

infix-operator-attributes


→
[precedence-clause](Declarations.md#precedence-clause)~opt~[associativity-clause](Declarations.md#associativity-clause)~opt~

[‌]()

precedence-clause


→
`precedence`[precedence-level](Declarations.md#precedence-level)

[‌]()

precedence-level


→
A decimal integer between 0 and 255, inclusive

[‌]()

associativity-clause


→
`associativity`[associativity](Declarations.md#associativity)

[‌]()

associativity


→

`left`

`right`

`none`










[‌]()
### Declaration Modifiers 

*Declaration modifiers* are keywords or context-sensitive keywords that modify the behavior or meaning of a declaration. You specify a declaration modifier by writing the appropriate keyword or context-sensitive keyword between a declaration’s attributes (if any) and the keyword that introduces the declaration.

`dynamic`

:   Apply this modifier to any member of a class that can be represented by Objective-C. When you mark a member declaration with the `dynamic` modifier, access to that member is always dynamically dispatched using the Objective-C runtime. Access to that member is never inlined or devirtualized by the compiler.

    Because declarations marked with the `dynamic` modifier are dispatched using the Objective-C runtime, they’re implicitly marked with the `objc` attribute.

`final`

:   Apply this modifier to a class or to a property, method, or subscript member of a class. It’s applied to a class to indicate that the class can’t be subclassed. It’s applied to a property, method, or subscript of a class to indicate that a class member can’t be overridden in any subclass.



`lazy`

:   Apply this modifier to a stored variable property of a class or structure to indicate that the property’s initial value is calculated and stored at most once, when the property is first accessed. For an example of how to use the `lazy` modifier, see [Lazy Stored Properties](Properties.md#TP40016643-CH14-ID257).

`optional`

:   Apply this modifier to a protocol’s property, method, or subscript members to indicate that a conforming type isn’t required to implement those members.

    You can apply the `optional` modifier only to protocols that are marked with the `objc` attribute. As a result, only class types can adopt and conform to a protocol that contains optional member requirements. For more information about how to use the `optional` modifier and for guidance about how to access optional protocol members—for example, when you’re not sure whether a conforming type implements them—see [Optional Protocol Requirements](Protocols.md#TP40016643-CH25-ID284).



`required`

:   Apply this modifier to a designated or convenience initializer of a class to indicate that every subclass must implement that initializer. The subclass’s implementation of that initializer must also be marked with the `required` modifier.

`weak`

:   The `weak` modifier is applied to a variable or a stored variable property to indicate that the variable or property has a weak reference to the object stored as its value. The type of the variable or property must be an optional class type. Use the `weak` modifier to avoid strong reference cycles. For an example and more information about the `weak` modifier, see [Weak References](AutomaticReferenceCounting.md#TP40016643-CH20-ID53).



[‌]()
### Access Control Levels 

Swift provides three levels of access control: public, internal, and private. You can mark a declaration with one of the access-level modifiers below to specify the declaration’s access level. Access control is discussed in detail in [Access Control](AccessControl.md).

`public`

:   Apply this modifier to a declaration to indicate the declaration can be accessed by code in the same module as the declaration. Declarations marked with the `public` access-level modifier can also be accessed by code in a module that imports the module that contains that declaration.

`internal`

:   Apply this modifier to a declaration to indicate the declaration can be accessed only by code in the same module as the declaration. By default, most declarations are implicitly marked with the `internal` access-level modifier.

`private`

:   Apply this modifier to a declaration to indicate the declaration can be accessed only by code in the same source file as the declaration.

Each access-level modifier above optionally accepts a single argument, which consists of the `set` keyword enclosed in parentheses (for instance, `private(set)`). Use this form of an access-level modifier when you want to specify an access level for the setter of a variable or subscript that’s less than or equal to the access level of the variable or subscript itself, as discussed in [Getters and Setters](AccessControl.md#TP40016643-CH41-ID18).



Grammar of a declaration modifier



[‌]()

declaration-modifier


→

`class`

`convenience`

`dynamic`

`final`

`infix`

`lazy`

`mutating`

`nonmutating`

`optional`

`override`

`postfix`

`prefix`

`required`

`static`

`unowned`

`unowned``(``safe``)`

`unowned``(``unsafe``)`

`weak`


[‌]()

declaration-modifier


→
[access-level-modifier](Declarations.md#access-level-modifier)

[‌]()

declaration-modifiers


→
[declaration-modifier](Declarations.md#declaration-modifier)[declaration-modifiers](Declarations.md#declaration-modifiers)~opt~





[‌]()

access-level-modifier


→

`internal`

`internal``(``set``)`


[‌]()

access-level-modifier


→

`private`

`private``(``set``)`


[‌]()

access-level-modifier


→

`public`

`public``(``set``)`













