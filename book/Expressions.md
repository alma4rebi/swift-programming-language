



[‌]()[‌]()
Expressions 
-----------



In Swift, there are four kinds of expressions: prefix expressions, binary expressions, primary expressions, and postfix expressions. Evaluating an expression returns a value, causes a side effect, or both.

Prefix and binary expressions let you apply operators to smaller expressions. Primary expressions are conceptually the simplest kind of expression, and they provide a way to access values. Postfix expressions, like prefix and binary expressions, let you build up more complex expressions using postfixes such as function calls and member access. Each kind of expression is described in detail in the sections below.



Grammar of an expression



[‌]()

expression


→
[try-operator](Expressions.md#try-operator)~opt~[prefix-expression](Expressions.md#prefix-expression)[binary-expressions](Expressions.md#binary-expressions)~opt~

[‌]()

expression-list


→

[expression](Expressions.md#expression)

[expression](Expressions.md#expression)`,`[expression-list](Expressions.md#expression-list)










[‌]()
### Prefix Expressions 

*Prefix expressions* combine an optional prefix operator with an expression. Prefix operators take one argument, the expression that follows them.

For information about the behavior of these operators, see [Basic Operators](BasicOperators.md) and [Advanced Operators](AdvancedOperators.md).

For information about the operators provided by the Swift standard library, see *Swift Standard Library Operators Reference*.

In addition to the standard library operators, you use `&` immediately before the name of a variable that’s being passed as an in-out argument to a function call expression. For more information and to see an example, see [In-Out Parameters](Functions.md#TP40016643-CH10-ID173).



Grammar of a prefix expression



[‌]()

prefix-expression


→
[prefix-operator](LexicalStructure.md#prefix-operator)~opt~[postfix-expression](Expressions.md#postfix-expression)

[‌]()

prefix-expression


→
[in-out-expression](Expressions.md#in-out-expression)

[‌]()

in-out-expression


→
`&`[identifier](LexicalStructure.md#identifier)







[‌]()
### Try Operator 

A *try expression* consists of the `try` operator followed by an expression that can throw an error. It has the following form:




-   ``` 
    try expression
    ```



An *optional-try expression* consists of the `try?` operator followed by an expression that can throw an error. It has the following form:




-   ``` 
    try? expression
    ```



If the *expression* does not throw an error, the value of the optional-try expression is an optional containing the value of the *expression*. Otherwise, the value of the optional-try expression is `nil`.

A *forced-try expression* consists of the `try!` operator followed by an expression that can throw an error. It has the following form:




-   ``` 
    try! expression
    ```



If the *expression* throws an error, a runtime error is produced.

When the expression on the left hand side of a binary operator is marked with `try`, `try?`, or `try!`, that operator applies to the whole binary expression. That said, you can use parentheses to be explicit about the scope of the operator’s application.







1.  `sum` = `try` `someThrowingFunction`() + `anotherThrowingFunction`() `// try applies to both function calls`
2.  `sum` = `try` (`someThrowingFunction`() + `anotherThrowingFunction`()) `// try apllies to both function calls`
3.  `sum` = (`try` `someThrowingFunction`()) + `anotherThrowingFunction`() `// Error: try applies only to the first function call`







A `try` expression can’t appear on the right hand side of a binary operator, unless the binary operator is the assignment operator or the `try` expression is enclosed in parentheses.

For more information and to see examples of how to use `try`, `try?`, and `try!`, see [Error Handling](ErrorHandling.md).



Grammar of a try expression



[‌]()

try-operator


→

`try`

`try``?`

`try``!`












[‌]()
### Binary Expressions 

*Binary expressions* combine an infix binary operator with the expression that it takes as its left-hand and right-hand arguments. It has the following form:




-   ``` 
    left-hand argument operator right-hand argument
    ```



For information about the behavior of these operators, see [Basic Operators](BasicOperators.md) and [Advanced Operators](AdvancedOperators.md).

For information about the operators provided by the Swift standard library, see *Swift Standard Library Operators Reference*.



Note

At parse time, an expression made up of binary operators is represented as a flat list. This list is transformed into a tree by applying operator precedence. For example, the expression `2 + 3 * 5` is initially understood as a flat list of five items, `2`, `+`, `3`, `*`, and `5`. This process transforms it into the tree (2 + (3 \* 5)).





Grammar of a binary expression



[‌]()

binary-expression


→
[binary-operator](LexicalStructure.md#binary-operator)[prefix-expression](Expressions.md#prefix-expression)

[‌]()

binary-expression


→
[assignment-operator](Expressions.md#assignment-operator)[try-operator](Expressions.md#try-operator)~opt~[prefix-expression](Expressions.md#prefix-expression)

[‌]()

binary-expression


→
[conditional-operator](Expressions.md#conditional-operator)[try-operator](Expressions.md#try-operator)~opt~[prefix-expression](Expressions.md#prefix-expression)

[‌]()

binary-expression


→
[type-casting-operator](Expressions.md#type-casting-operator)

[‌]()

binary-expressions


→
[binary-expression](Expressions.md#binary-expression)[binary-expressions](Expressions.md#binary-expressions)~opt~







[‌]()
### Assignment Operator 

The *assignment operator* sets a new value for a given expression. It has the following form:




-   ``` 
    expression = value
    ```



The value of the *expression* is set to the value obtained by evaluating the *value*. If the *expression* is a tuple, the *value* must be a tuple with the same number of elements. (Nested tuples are allowed.) Assignment is performed from each part of the *value* to the corresponding part of the *expression*. For example:







1.  `(a`, `_`, (`b`, `c`)) = (`"test"`, `9.45`, (`12`, `3`))
2.  `// a is "test", b is 12, c is 3, and 9.45 is ignored`







The assignment operator does not return any value.



Grammar of an assignment operator



[‌]()

assignment-operator


→
`=`









[‌]()
### Ternary Conditional Operator 

The *ternary conditional operator* evaluates to one of two given values based on the value of a condition. It has the following form:




-   ``` 
    condition ? expression used if true : expression used if false
    ```



If the *condition* evaluates to `true`, the conditional operator evaluates the first expression and returns its value. Otherwise, it evaluates the second expression and returns its value. The unused expression is not evaluated.

For an example that uses the ternary conditional operator, see [Ternary Conditional Operator](BasicOperators.md#TP40016643-CH6-ID71).



Grammar of a conditional operator



[‌]()

conditional-operator


→
`?`[try-operator](Expressions.md#try-operator)~opt~[expression](Expressions.md#expression)`:`









[‌]()
### Type-Casting Operators 

There are four type-casting operators: the `is` operator, the `as` operator, the `as?` operator, and the `as!` operator.

They have the following form:




-   ``` 
    expression is type
    ```

-   ``` 
    expression as type
    ```

-   ``` 
    expression as? type
    ```

-   ``` 
    expression as! type
    ```



The `is` operator checks at runtime whether the *expression* can be cast to the specified *type*. It returns `true` if the *expression* can be cast to the specified *type*; otherwise, it returns `false`.

The `as` operator performs a cast when it is known at compile time that the cast always succeeds, such as upcasting or bridging. Upcasting lets you use an expression as an instance of its type’s supertype, without using an intermediate variable. The following approaches are equivalent:







1.  `func` `f`(`any`: `Any`) { `print`(`"Function for Any"`) }
2.  `func` `f`(`int`: `Int`) { `print`(`"Function for Int"`) }
3.  `let` `x` = `10`
4.  `f`(`x`)
5.  `// prints "Function for Int"`
6.  ` `
7.  `let` `y`: `Any` = `x`
8.  `f`(`y`)
9.  `// prints "Function for Any"`
10. ` `
11. `f`(`x` `as` `Any`)
12. `// prints "Function for Any"`







Bridging lets you use an expression of a Swift standard library type such as `String` as its corresponding Foundation type such as `NSString` without needing to create a new instance. For more information on bridging, see Working with Cocoa Data Types in *Using Swift with Cocoa and Objective-C (Swift 2.1)*.

The `as?` operator performs a conditional cast of the *expression* to the specified *type*. The `as?` operator returns an optional of the specified *type*. At runtime, if the cast succeeds, the value of *expression* is wrapped in an optional and returned; otherwise, the value returned is `nil`. If casting to the specified *type* is guaranteed to fail or is guaranteed to succeed, a compile-time error is raised.

The `as!` operator performs a forced cast of the *expression* to the specified *type*. The `as!` operator returns a value of the specified *type*, not an optional type. If the cast fails, a runtime error is raised. The behavior of `x as! T` is the same as the behavior of `(x as? T)!`.

For more information about type casting and to see examples that use the type-casting operators, see [Type Casting](TypeCasting.md).



Grammar of a type-casting operator



[‌]()

type-casting-operator


→
`is`[type](Types.md#type)

[‌]()

type-casting-operator


→
`as`[type](Types.md#type)

[‌]()

type-casting-operator


→
`as``?`[type](Types.md#type)

[‌]()

type-casting-operator


→
`as``!`[type](Types.md#type)











[‌]()
### Primary Expressions 

*Primary expressions* are the most basic kind of expression. They can be used as expressions on their own, and they can be combined with other tokens to make prefix expressions, binary expressions, and postfix expressions.



Grammar of a primary expression



[‌]()

primary-expression


→
[identifier](LexicalStructure.md#identifier)[generic-argument-clause](GenericParametersAndArguments.md#generic-argument-clause)~opt~

[‌]()

primary-expression


→
[literal-expression](Expressions.md#literal-expression)

[‌]()

primary-expression


→
[self-expression](Expressions.md#self-expression)

[‌]()

primary-expression


→
[superclass-expression](Expressions.md#superclass-expression)

[‌]()

primary-expression


→
[closure-expression](Expressions.md#closure-expression)

[‌]()

primary-expression


→
[parenthesized-expression](Expressions.md#parenthesized-expression)

[‌]()

primary-expression


→
[implicit-member-expression](Expressions.md#implicit-member-expression)

[‌]()

primary-expression


→
[wildcard-expression](Expressions.md#wildcard-expression)







[‌]()
### Literal Expression 

A *literal expression* consists of either an ordinary literal (such as a string or a number), an array or dictionary literal, or one of the following special literals:



+--------------------------+--------------------------+--------------------------+
| Literal                  | Type                     | Value                    |
+==========================+==========================+==========================+
| `__FILE__`  | `String`    | The name of the file in  |
|                          |                          | which it appears.        |
+--------------------------+--------------------------+--------------------------+
| `__LINE__`  | `Int`       | The line number on which |
|                          |                          | it appears.              |
+--------------------------+--------------------------+--------------------------+
| `__COLUMN__`       | The column number in     |
| }                        |                          | which it begins.         |
+--------------------------+--------------------------+--------------------------+
| `__FUNCTION__`    | The name of the          |
| ce}                      |                          | declaration in which it  |
|                          |                          | appears.                 |
+--------------------------+--------------------------+--------------------------+



Inside a function, the value of `__FUNCTION__` is the name of that function, inside a method it is the name of that method, inside a property getter or setter it is the name of that property, inside special members like `init` or `subscript` it is the name of that keyword, and at the top level of a file it is the name of the current module.

When used as the default value of a function or method, the special literal’s value is determined when the default value expression is evaluated at the call site.







1.  `func` `logFunctionName`(`string`: `String` = `__FUNCTION__`) {
2.  `    print`(`string`)
3.  `}`
4.  `func` `myFunction`() {
5.  `    logFunctionName`() `// Prints "myFunction()".`
6.  `}`







An *array literal* is an ordered collection of values. It has the following form:




-   ``` 
    [value 1, value 2, ...]
    ```



The last expression in the array can be followed by an optional comma. The value of an array literal has type `[T]`, where `T` is the type of the expressions inside it. If there are expressions of multiple types, `T` is their closest common supertype. Empty array literals are written using an empty pair of square brackets and can be used to create an empty array of a specified type.







1.  `var` `emptyArray`: \[`Double`\] = \[\]







A *dictionary literal* is an unordered collection of key-value pairs. It has the following form:




-   ``` 
    [key 1: value 1, key 2: value 2, ...]
    ```



The last expression in the dictionary can be followed by an optional comma. The value of a dictionary literal has type `[Key: Value]`, where `Key` is the type of its key expressions and `Value` is the type of its value expressions. If there are expressions of multiple types, `Key` and `Value` are the closest common supertype for their respective values. An empty dictionary literal is written as a colon inside a pair of brackets (`[:]`) to distinguish it from an empty array literal. You can use an empty dictionary literal to create an empty dictionary literal of specified key and value types.







1.  `var` `emptyDictionary`: \[`String`: `Double`\] = \[:\]









Grammar of a literal expression



[‌]()

literal-expression


→
[literal](LexicalStructure.md#literal)

[‌]()

literal-expression


→

[array-literal](Expressions.md#array-literal)

[dictionary-literal](Expressions.md#dictionary-literal)


[‌]()

literal-expression


→

`__FILE__`

`__LINE__`

`__COLUMN__`

`__FUNCTION__`






[‌]()

array-literal


→
`[`[array-literal-items](Expressions.md#array-literal-items)~opt~`]`

[‌]()

array-literal-items


→

[array-literal-item](Expressions.md#array-literal-item)`,`~opt~

[array-literal-item](Expressions.md#array-literal-item)`,`[array-literal-items](Expressions.md#array-literal-items)


[‌]()

array-literal-item


→
[expression](Expressions.md#expression)





[‌]()

dictionary-literal


→

`[`[dictionary-literal-items](Expressions.md#dictionary-literal-items)`]`

`[``:``]`


[‌]()

dictionary-literal-items


→

[dictionary-literal-item](Expressions.md#dictionary-literal-item)`,`~opt~

[dictionary-literal-item](Expressions.md#dictionary-literal-item)`,`[dictionary-literal-items](Expressions.md#dictionary-literal-items)


[‌]()

dictionary-literal-item


→
[expression](Expressions.md#expression)`:`[expression](Expressions.md#expression)









[‌]()
### Self Expression 

The `self` expression is an explicit reference to the current type or instance of the type in which it occurs. It has the following forms:




-   ``` 
    self
    ```

-   ``` 
    self.member name
    ```

-   ``` 
    self[subscript index]
    ```

-   ``` 
    self(initializer arguments)
    ```

-   ``` 
    self.init(initializer arguments)
    ```



In an initializer, subscript, or instance method, `self` refers to the current instance of the type in which it occurs. In a type method, `self` refers to the current type in which it occurs.

The `self` expression is used to specify scope when accessing members, providing disambiguation when there is another variable of the same name in scope, such as a function parameter. For example:







1.  `class` `SomeClass` {
2.  `    var` `greeting`: `String`
3.  `    init`(`greeting`: `String`) {
4.  `        self`.`greeting` = `greeting`
5.  `    }`
6.  `}`







In a mutating method of a value type, you can assign a new instance of that value type to `self`. For example:







1.  `struct` `Point` {
2.  `    var` `x` = `0.0`, `y` = `0.0`
3.  `    mutating` `func` `moveByX`(`deltaX`: `Double`, `y` `deltaY`: `Double`) {
4.  `        self` = `Point`(`x`: `x` + `deltaX`, `y`: `y` + `deltaY`)
5.  `    }`
6.  `}`









Grammar of a self expression



[‌]()

self-expression


→

`self`

[self-method-expression](Expressions.md#self-method-expression)

[self-subscript-expression](Expressions.md#self-subscript-expression)

[self-initializer-expression](Expressions.md#self-initializer-expression)






[‌]()

self-method-expression


→
`self``.`[identifier](LexicalStructure.md#identifier)

[‌]()

self-subscript-expression


→
`self``[`[expression-list](Expressions.md#expression-list)`]`

[‌]()

self-initializer-expression


→
`self``.``init`









[‌]()
### Superclass Expression 

A *superclass expression* lets a class interact with its superclass. It has one of the following forms:




-   ``` 
    super.member name
    ```

-   ``` 
    super[subscript index]
    ```

-   ``` 
    super.init(initializer arguments)
    ```



The first form is used to access a member of the superclass. The second form is used to access the superclass’s subscript implementation. The third form is used to access an initializer of the superclass.

Subclasses can use a superclass expression in their implementation of members, subscripting, and initializers to make use of the implementation in their superclass.



Grammar of a superclass expression



[‌]()

superclass-expression


→

[superclass-method-expression](Expressions.md#superclass-method-expression)

[superclass-subscript-expression](Expressions.md#superclass-subscript-expression)

[superclass-initializer-expression](Expressions.md#superclass-initializer-expression)






[‌]()

superclass-method-expression


→
`super``.`[identifier](LexicalStructure.md#identifier)

[‌]()

superclass-subscript-expression


→
`super``[`[expression-list](Expressions.md#expression-list)`]`

[‌]()

superclass-initializer-expression


→
`super``.``init`









[‌]()
### Closure Expression 

A *closure expression* creates a closure, also known as a *lambda* or an *anonymous function* in other programming languages. Like a function declaration, a closure contains statements which it executes, and it captures constants and variables from its enclosing scope. It has the following form:




-   ``` 
    { (parameters) -> return type in
    ```

-   ``` 
        statements
    ```

-   ``` 
    }
    ```



The *parameters* have the same form as the parameters in a function declaration, as described in [Function Declaration](Declarations.md#TP40016643-CH34-ID362).

There are several special forms that allow closures to be written more concisely:

-   A closure can omit the types of its parameters, its return type, or both. If you omit the parameter names and both types, omit the `in` keyword before the statements. If the omitted types can’t be inferred, a compile-time error is raised.

-   A closure may omit names for its parameters. Its parameters are then implicitly named `$` followed by their position: `$0`, `$1`, `$2`, and so on.

-   A closure that consists of only a single expression is understood to return the value of that expression. The contents of this expression are also considered when performing type inference on the surrounding expression.

The following closure expressions are equivalent:







1.  `myFunction` {
2.  `    (x`: `Int`, `y`: `Int`) -&gt; `Int` `in`
3.  `    return` `x` + `y`
4.  `}`
5.  ` `
6.  `myFunction` {
7.  `    (x`, `y`) `in`
8.  `    return` `x` + `y`
9.  `}`
10. ` `
11. `myFunction` { `return` `$0` + `$1` }
12. ` `
13. `myFunction` { `$0` + `$1` }







For information about passing a closure as an argument to a function, see [Function Call Expression](Expressions.md#TP40016643-CH32-ID398).



[‌]()
### Capture Lists 

By default, a closure expression captures constants and variables from its surrounding scope with strong references to those values. You can use a *capture list* to explicitly control how values are captured in a closure.

A capture list is written as a comma separated list of expressions surrounded by square brackets, before the list of parameters. If you use a capture list, you must also use the `in` keyword, even if you omit the parameter names, parameter types, and return type.

The entries in the capture list are initialized when the closure is created. For each entry in the capture list, a constant is initialized to the value of the constant or variable that has the same name in the surrounding scope. For example in the code below, `a` is included in the capture list but `b` is not, which gives them different behavior.







1.  `var` `a` = `0`
2.  `var` `b` = `0`
3.  `let` `closure` = { \[`a`\] `in`
4.  `    print`(`a`, `b`)
5.  `}`
6.  ` `
7.  `a` = `10`
8.  `b` = `10`
9.  `closure`()
10. `// prints "0 10"`







There are two different things named `a`, the variable in the surrounding scope and the constant in the closure’s scope, but only one variable named `b`. The `a` in the inner scope is initialized with the value of the `a` in the outer scope when the closure is created, but their values are not connected in any special way. This means that a change to the value of `a` in the outer scope does not effect the value of `a` in the inner scope, nor does a change to `a` inside the closure effect the value of `a` outside the closure. In contrast, there is only one variable named `b`—the `b` in the outer scope—so changes from inside or outside the closure are visible in both places.

This distinction is not visible when the captured variable’s type has reference semantics. For example, there are two things named `x` in the code below, a variable in the outer scope and a constant in the inner scope, but they both refer to the same object because of reference semantics.







1.  `class` `SimpleClass` {
2.  `    var` `value`: `Int` = `0`
3.  `}`
4.  `var` `x` = `SimpleClass`()
5.  `var` `y` = `SimpleClass`()
6.  `let` `closure` = { \[`x`\] `in`
7.  `    print`(`x`.`value`, `y`.`value`)
8.  `}`
9.  ` `
10. `x`.`value` = `10`
11. `y`.`value` = `10`
12. `closure`()
13. `// prints "10 10"`







If the type of the expression’s value is a class, you can mark the expression in a capture list with `weak` or `unowned` to capture a weak or unowned reference to the expression’s value.







1.  `myFunction` { `print`(`self`.`title`) } `// strong capture`
2.  `myFunction` { \[`weak` `self`\] `in` `print`(`self`!.`title`) } `// weak capture`
3.  `myFunction` { \[`unowned` `self`\] `in` `print`(`self`.`title`) } `// unowned capture`







You can also bind an arbitrary expression to a named value in a capture list. The expression is evaluated when the closure is created, and the value is captured with the specified strength. For example:







1.  `// Weak capture of "self.parent" as "parent"`
2.  `myFunction` { \[`weak` `parent` = `self`.`parent`\] `in` `print`(`parent`!.`title`) }







For more information and examples of closure expressions, see [Closure Expressions](Closures.md#TP40016643-CH11-ID95). For more information and examples of capture lists, see [Resolving Strong Reference Cycles for Closures](AutomaticReferenceCounting.md#TP40016643-CH20-ID57).



Grammar of a closure expression



[‌]()

closure-expression


→
`{`[closure-signature](Expressions.md#closure-signature)~opt~[statements](Statements.md#statements)`}`





[‌]()

closure-signature


→
[parameter-clause](Declarations.md#parameter-clause)[function-result](Declarations.md#function-result)~opt~`in`

[‌]()

closure-signature


→
[identifier-list](LexicalStructure.md#identifier-list)[function-result](Declarations.md#function-result)~opt~`in`

[‌]()

closure-signature


→
[capture-list](Expressions.md#capture-list)[parameter-clause](Declarations.md#parameter-clause)[function-result](Declarations.md#function-result)~opt~`in`

[‌]()

closure-signature


→
[capture-list](Expressions.md#capture-list)[identifier-list](LexicalStructure.md#identifier-list)[function-result](Declarations.md#function-result)~opt~`in`

[‌]()

closure-signature


→
[capture-list](Expressions.md#capture-list)`in`





[‌]()

capture-list


→
`[`[capture-list-items](Expressions.md#capture-list-items)`]`

[‌]()

capture-list-items


→

[capture-list-item](Expressions.md#capture-list-item)

[capture-list-item](Expressions.md#capture-list-item)`,`[capture-list-items](Expressions.md#capture-list-items)


[‌]()

capture-list-item


→
[capture-specifier](Expressions.md#capture-specifier)~opt~[expression](Expressions.md#expression)

[‌]()

capture-specifier


→

`weak`

`unowned`

`unowned(safe)`

`unowned(unsafe)`












[‌]()
### Implicit Member Expression 

An *implicit member expression* is an abbreviated way to access a member of a type, such as an enumeration case or a type method, in a context where type inference can determine the implied type. It has the following form:




-   ``` 
    .member name
    ```



For example:







1.  `var` `x` = `MyEnumeration`.`SomeValue`
2.  `x` = .`AnotherValue`









Grammar of a implicit member expression



[‌]()

implicit-member-expression


→
`.`[identifier](LexicalStructure.md#identifier)









[‌]()
### Parenthesized Expression 

A *parenthesized expression* consists of a comma-separated list of expressions surrounded by parentheses. Each expression can have an optional identifier before it, separated by a colon (`:`). It has the following form:




-   ``` 
    (identifier 1: expression 1, identifier 2: expression 2, ...)
    ```



Use parenthesized expressions to create tuples and to pass arguments to a function call. If there is only one value inside the parenthesized expression, the type of the parenthesized expression is the type of that value. For example, the type of the parenthesized expression `(1)` is `Int`, not `(Int)`.



Grammar of a parenthesized expression



[‌]()

parenthesized-expression


→
`(`[expression-element-list](Expressions.md#expression-element-list)~opt~`)`

[‌]()

expression-element-list


→

[expression-element](Expressions.md#expression-element)

[expression-element](Expressions.md#expression-element)`,`[expression-element-list](Expressions.md#expression-element-list)


[‌]()

expression-element


→

[expression](Expressions.md#expression)

[identifier](LexicalStructure.md#identifier)`:`[expression](Expressions.md#expression)










[‌]()
### Wildcard Expression 

A *wildcard expression* is used to explicitly ignore a value during an assignment. For example, in the following assignment 10 is assigned to `x` and 20 is ignored:







1.  `(x`, `_`) = (`10`, `20`)
2.  `// x is 10, and 20 is ignored`









Grammar of a wildcard expression



[‌]()

wildcard-expression


→
`_`











[‌]()
### Postfix Expressions 

*Postfix expressions* are formed by applying a postfix operator or other postfix syntax to an expression. Syntactically, every primary expression is also a postfix expression.

For information about the behavior of these operators, see [Basic Operators](BasicOperators.md) and [Advanced Operators](AdvancedOperators.md).

For information about the operators provided by the Swift standard library, see *Swift Standard Library Operators Reference*.



Grammar of a postfix expression



[‌]()

postfix-expression


→
[primary-expression](Expressions.md#primary-expression)

[‌]()

postfix-expression


→
[postfix-expression](Expressions.md#postfix-expression)[postfix-operator](LexicalStructure.md#postfix-operator)

[‌]()

postfix-expression


→
[function-call-expression](Expressions.md#function-call-expression)

[‌]()

postfix-expression


→
[initializer-expression](Expressions.md#initializer-expression)

[‌]()

postfix-expression


→
[explicit-member-expression](Expressions.md#explicit-member-expression)

[‌]()

postfix-expression


→
[postfix-self-expression](Expressions.md#postfix-self-expression)

[‌]()

postfix-expression


→
[dynamic-type-expression](Expressions.md#dynamic-type-expression)

[‌]()

postfix-expression


→
[subscript-expression](Expressions.md#subscript-expression)

[‌]()

postfix-expression


→
[forced-value-expression](Expressions.md#forced-value-expression)

[‌]()

postfix-expression


→
[optional-chaining-expression](Expressions.md#optional-chaining-expression)







[‌]()
### Function Call Expression 

A *function call expression* consists of a function name followed by a comma-separated list of the function’s arguments in parentheses. Function call expressions have the following form:




-   ``` 
    function name(argument value 1, argument value 2)
    ```



The *function name* can be any expression whose value is of a function type.

If the function definition includes names for its parameters, the function call must include names before its argument values separated by a colon (`:`). This kind of function call expression has the following form:




-   ``` 
    function name(argument name 1: argument value 1, argument name 2: argument value 2)
    ```



A function call expression can include a trailing closure in the form of a closure expression immediately after the closing parenthesis. The trailing closure is understood as an argument to the function, added after the last parenthesized argument. The following function calls are equivalent:







1.  `// someFunction takes an integer and a closure as its arguments`
2.  `someFunction`(`x`, `f`: {`$0` == `13`})
3.  `someFunction`(`x`) {`$0` == `13`}







If the trailing closure is the function’s only argument, the parentheses can be omitted.







1.  `// someFunction takes a closure as its only argument`
2.  `myData`.`someMethod`() {`$0` == `13`}
3.  `myData`.`someMethod` {`$0` == `13`}









Grammar of a function call expression



[‌]()

function-call-expression


→
[postfix-expression](Expressions.md#postfix-expression)[parenthesized-expression](Expressions.md#parenthesized-expression)

[‌]()

function-call-expression


→
[postfix-expression](Expressions.md#postfix-expression)[parenthesized-expression](Expressions.md#parenthesized-expression)~opt~[trailing-closure](Expressions.md#trailing-closure)

[‌]()

trailing-closure


→
[closure-expression](Expressions.md#closure-expression)









[‌]()
### Initializer Expression 

An *initializer expression* provides access to a type’s initializer. It has the following form:




-   ``` 
    expression.init(initializer arguments)
    ```



You use the initializer expression in a function call expression to initialize a new instance of a type. You also use an initializer expression to delegate to the initializer of a superclass.







1.  `class` `SomeSubClass`: `SomeSuperClass` {
2.  `    override` `init`() {
3.  `        // subclass initialization goes here`
4.  `        super`.`init`()
5.  `    }`
6.  `}`







Like a function, an initializer can be used as a value. For example:







1.  `// Type annotation is required because String has multiple initializers.`
2.  `let` `initializer`: `Int` -&gt; `String` = `String`.`init`
3.  `let` `oneTwoThree` = \[`1`, `2`, `3`\].`map`(`initializer`).`reduce`(`""`, `combine`: +)
4.  `print`(`oneTwoThree`)
5.  `// prints "123"`







If you specify a type by name, you can access the type’s initializer without using an initializer expression. In all other cases, you must use an initializer expression.







1.  `let` `s1` = `SomeType`.`init`(`data`: `3`) `// Valid`
2.  `let` `s2` = `SomeType`(`data`: `1`) `// Also valid`
3.  ` `
4.  `let` `s4` = `someValue`.`dynamicType`(`data`: `5`) `// Error`
5.  `let` `s3` = `someValue`.`dynamicType`.`init`(`data`: `7`) `// Valid`









Grammar of an initializer expression



[‌]()

initializer-expression


→
[postfix-expression](Expressions.md#postfix-expression)`.``init`









[‌]()
### Explicit Member Expression 

An *explicit member expression* allows access to the members of a named type, a tuple, or a module. It consists of a period (`.`) between the item and the identifier of its member.




-   ``` 
    expression.member name
    ```



The members of a named type are named as part of the type’s declaration or extension. For example:







1.  `class` `SomeClass` {
2.  `    var` `someProperty` = `42`
3.  `}`
4.  `let` `c` = `SomeClass`()
5.  `let` `y` = `c`.`someProperty` `// Member access`







The members of a tuple are implicitly named using integers in the order they appear, starting from zero. For example:







1.  `var` `t` = (`10`, `20`, `30`)
2.  `t`.`0` = `t`.`1`
3.  `// Now t is (20, 20, 30)`







The members of a module access the top-level declarations of that module.

If a period appears at the beginning of a line, it is understood as part of an explicit member expression, not as an implicit member expression. For example, the following listing shows chained method calls split over several lines:







1.  `let` `x` = \[`10`, `3`, `20`, `15`, `4`\]
2.  `    .sort`()
3.  `    .filter` { `$0` &gt; `5` }
4.  `    .map` { `$0` \* `100` }









Grammar of an explicit member expression



[‌]()

explicit-member-expression


→
[postfix-expression](Expressions.md#postfix-expression)`.`[decimal-digits](LexicalStructure.md#decimal-digits)

[‌]()

explicit-member-expression


→
[postfix-expression](Expressions.md#postfix-expression)`.`[identifier](LexicalStructure.md#identifier)[generic-argument-clause](GenericParametersAndArguments.md#generic-argument-clause)~opt~









[‌]()
### Postfix Self Expression 

A postfix `self` expression consists of an expression or the name of a type, immediately followed by `.self`. It has the following forms:




-   ``` 
    expression.self
    ```

-   ``` 
    type.self
    ```



The first form evaluates to the value of the *expression*. For example, `x.self` evaluates to `x`.

The second form evaluates to the value of the *type*. Use this form to access a type as a value. For example, because `SomeClass.self` evaluates to the `SomeClass` type itself, you can pass it to a function or method that accepts a type-level argument.



Grammar of a self expression



[‌]()

postfix-self-expression


→
[postfix-expression](Expressions.md#postfix-expression)`.``self`









[‌]()
### Dynamic Type Expression 

A `dynamicType` expression consists of an expression, immediately followed by `.dynamicType`. It has the following form:




-   ``` 
    expression.dynamicType
    ```



The *expression* can’t be the name of a type. The entire `dynamicType` expression evaluates to the value of the runtime type of the *expression*, as the following example shows:







1.  `class` `SomeBaseClass` {
2.  `    class` `func` `printClassName`() {
3.  `        print`(`"SomeBaseClass"`)
4.  `    }`
5.  `}`
6.  `class` `SomeSubClass`: `SomeBaseClass` {
7.  `    override` `class` `func` `printClassName`() {
8.  `        print`(`"SomeSubClass"`)
9.  `    }`
10. `}`
11. `let` `someInstance`: `SomeBaseClass` = `SomeSubClass`()
12. `// someInstance has a static type of SomeBaseClass at compile time, and`
13. `// it has a dynamc type of SomeSubClass at runtime`
14. `someInstance`.`dynamicType`.`printClassName`()
15. `// prints "SomeSubClass"`









Grammar of a dynamic type expression



[‌]()

dynamic-type-expression


→
[postfix-expression](Expressions.md#postfix-expression)`.``dynamicType`









[‌]()
### Subscript Expression 

A *subscript expression* provides subscript access using the getter and setter of the corresponding subscript declaration. It has the following form:




-   ``` 
    expression[index expressions]
    ```



To evaluate the value of a subscript expression, the subscript getter for the *expression*’s type is called with the *index expressions* passed as the subscript parameters. To set its value, the subscript setter is called in the same way.

For information about subscript declarations, see [Protocol Subscript Declaration](Declarations.md#TP40016643-CH34-ID373).



Grammar of a subscript expression



[‌]()

subscript-expression


→
[postfix-expression](Expressions.md#postfix-expression)`[`[expression-list](Expressions.md#expression-list)`]`









[‌]()
### Forced-Value Expression 

A *forced-value expression* unwraps an optional value that you are certain is not `nil`. It has the following form:




-   ``` 
    expression!
    ```



If the value of the *expression* is not `nil`, the optional value is unwrapped and returned with the corresponding nonoptional type. Otherwise, a runtime error is raised.

The unwrapped value of a forced-value expression can be modified, either by mutating the value itself, or by assigning to one of the value’s members. For example:







1.  `var` `x`: `Int`? = `0`
2.  `x`!++
3.  `// x is now 1`
4.  ` `
5.  `var` `someDictionary` = \[`"a"`: \[`1`, `2`, `3`\], `"b"`: \[`10`, `20`\]\]
6.  `someDictionary`\[`"a"`\]!\[`0`\] = `100`
7.  `// someDictionary is now ["b": [10, 20], "a": [100, 2, 3]]`









Grammar of a forced-value expression



[‌]()

forced-value-expression


→
[postfix-expression](Expressions.md#postfix-expression)`!`









[‌]()
### Optional-Chaining Expression 

An *optional-chaining expression* provides a simplified syntax for using optional values in postfix expressions. It has the following form:




-   ``` 
    expression?
    ```



The postfix `?` operator makes an optional-chaining expression from an expression without changing the expression’s value.

Optional-chaining expressions must appear within a postfix expression, and they cause the postfix expression to be evaluated in a special way. If the value of the optional-chaining expression is `nil`, all of the other operations in the postfix expression are ignored and the entire postfix expression evaluates to `nil`. If the value of the optional-chaining expression is not `nil`, the value of the optional-chaining expression is unwrapped and used to evaluate the rest of the postfix expression. In either case, the value of the postfix expression is still of an optional type.

If a postfix expression that contains an optional-chaining expression is nested inside other postfix expressions, only the outermost expression returns an optional type. In the example below, when `c` is not `nil`, its value is unwrapped and used to evaluate `.property`, the value of which is used to evaluate `.performAction()`. The entire expression `c?.property.performAction()` has a value of an optional type.







1.  `var` `c`: `SomeClass`?
2.  `var` `result`: `Bool`? = `c`?.`property`.`performAction`()







The following example shows the behavior of the example above without using optional chaining.







1.  `var` `result`: `Bool`? = `nil`
2.  `if` `let` `unwrappedC` = `c` {
3.  `    result` = `unwrappedC`.`property`.`performAction`()
4.  `}`







The unwrapped value of an optional-chaining expression can be modified, either by mutating the value itself, or by assigning to one of the value’s members. If the value of the optional-chaining expression is `nil`, the expression on the right hand side of the assignment operator is not evaluated. For example:







1.  `func` `someFunctionWithSideEffects`() -&gt; `Int` {
2.  `    return` `42` `// No actual side effects.`
3.  `}`
4.  `var` `someDictionary` = \[`"a"`: \[`1`, `2`, `3`\], `"b"`: \[`10`, `20`\]\]
5.  ` `
6.  `someDictionary`\[`"not here"`\]?\[`0`\] = `someFunctionWithSideEffects`()
7.  `// someFunctionWithSideEffects is not evaluated`
8.  `// someDictionary is still ["b": [10, 20], "a": [1, 2, 3]]`
9.  ` `
10. `someDictionary`\[`"a"`\]?\[`0`\] = `someFunctionWithSideEffects`()
11. `// someFunctionWithSideEffects is evaluated and returns 42`
12. `// someDictionary is now ["b": [10, 20], "a": [42, 2, 3]]`









Grammar of an optional-chaining expression



[‌]()

optional-chaining-expression


→
[postfix-expression](Expressions.md#postfix-expression)`?`












