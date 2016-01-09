



[‌](){#TP40016643-CH32}[‌](){#TP40016643-CH32-ID383}
Expressions {#expressions .chapter-name}
-----------



In Swift, there are four kinds of expressions: prefix expressions, binary expressions, primary expressions, and postfix expressions. Evaluating an expression returns a value, causes a side effect, or both.

Prefix and binary expressions let you apply operators to smaller expressions. Primary expressions are conceptually the simplest kind of expression, and they provide a way to access values. Postfix expressions, like prefix and binary expressions, let you build up more complex expressions using postfixes such as function calls and member access. Each kind of expression is described in detail in the sections below.



Grammar of an expression



[‌](){#expression}

expression


→
[try-operator](Expressions.md#try-operator)~opt~[prefix-expression](Expressions.md#prefix-expression)[binary-expressions](Expressions.md#binary-expressions)~opt~

[‌](){#expression-list}

expression-list


→

[expression](Expressions.md#expression)

[expression](Expressions.md#expression)`,`{.literal}[expression-list](Expressions.md#expression-list)










[‌](){#TP40016643-CH32-ID384}
### Prefix Expressions {#prefix-expressions .section-name}

*Prefix expressions* combine an optional prefix operator with an expression. Prefix operators take one argument, the expression that follows them.

For information about the behavior of these operators, see [Basic Operators](BasicOperators.md) and [Advanced Operators](AdvancedOperators.md).

For information about the operators provided by the Swift standard library, see *Swift Standard Library Operators Reference*.

In addition to the standard library operators, you use `&`{.code-voice} immediately before the name of a variable that’s being passed as an in-out argument to a function call expression. For more information and to see an example, see [In-Out Parameters](Functions.md#TP40016643-CH10-ID173).



Grammar of a prefix expression



[‌](){#prefix-expression}

prefix-expression


→
[prefix-operator](LexicalStructure.md#prefix-operator)~opt~[postfix-expression](Expressions.md#postfix-expression)

[‌](){#TP40016643-CH32-NoLink_398}

prefix-expression


→
[in-out-expression](Expressions.md#in-out-expression)

[‌](){#in-out-expression}

in-out-expression


→
`&`{.literal}[identifier](LexicalStructure.md#identifier)







[‌](){#TP40016643-CH32-ID516}
### Try Operator {#try-operator .section-name}

A *try expression* consists of the `try`{.code-voice} operator followed by an expression that can throw an error. It has the following form:




-   ``` {.code-voice}
    try expression
    ```



An *optional-try expression* consists of the `try?`{.code-voice} operator followed by an expression that can throw an error. It has the following form:




-   ``` {.code-voice}
    try? expression
    ```



If the *expression* does not throw an error, the value of the optional-try expression is an optional containing the value of the *expression*. Otherwise, the value of the optional-try expression is `nil`{.code-voice}.

A *forced-try expression* consists of the `try!`{.code-voice} operator followed by an expression that can throw an error. It has the following form:




-   ``` {.code-voice}
    try! expression
    ```



If the *expression* throws an error, a runtime error is produced.

When the expression on the left hand side of a binary operator is marked with `try`{.code-voice}, `try?`{.code-voice}, or `try!`{.code-voice}, that operator applies to the whole binary expression. That said, you can use parentheses to be explicit about the scope of the operator’s application.







1.  `sum`{.code-voice} = `try`{.kt} `someThrowingFunction`{.vc}() + `anotherThrowingFunction`{.vc}() `// try applies to both function calls`{.c}
2.  `sum`{.code-voice} = `try`{.kt} (`someThrowingFunction`{.vc}() + `anotherThrowingFunction`{.vc}()) `// try apllies to both function calls`{.c}
3.  `sum`{.code-voice} = (`try`{.kt} `someThrowingFunction`{.vc}()) + `anotherThrowingFunction`{.vc}() `// Error: try applies only to the first function call`{.c}







A `try`{.code-voice} expression can’t appear on the right hand side of a binary operator, unless the binary operator is the assignment operator or the `try`{.code-voice} expression is enclosed in parentheses.

For more information and to see examples of how to use `try`{.code-voice}, `try?`{.code-voice}, and `try!`{.code-voice}, see [Error Handling](ErrorHandling.md).



Grammar of a try expression



[‌](){#try-operator}

try-operator


→

`try`{.literal}

`try`{.literal}`?`{.literal}

`try`{.literal}`!`{.literal}












[‌](){#TP40016643-CH32-ID385}
### Binary Expressions {#binary-expressions .section-name}

*Binary expressions* combine an infix binary operator with the expression that it takes as its left-hand and right-hand arguments. It has the following form:




-   ``` {.code-voice}
    left-hand argument operator right-hand argument
    ```



For information about the behavior of these operators, see [Basic Operators](BasicOperators.md) and [Advanced Operators](AdvancedOperators.md).

For information about the operators provided by the Swift standard library, see *Swift Standard Library Operators Reference*.



Note

At parse time, an expression made up of binary operators is represented as a flat list. This list is transformed into a tree by applying operator precedence. For example, the expression `2 + 3 * 5`{.code-voice} is initially understood as a flat list of five items, `2`{.code-voice}, `+`{.code-voice}, `3`{.code-voice}, `*`{.code-voice}, and `5`{.code-voice}. This process transforms it into the tree (2 + (3 \* 5)).





Grammar of a binary expression



[‌](){#binary-expression}

binary-expression


→
[binary-operator](LexicalStructure.md#binary-operator)[prefix-expression](Expressions.md#prefix-expression)

[‌](){#TP40016643-CH32-NoLink_405}

binary-expression


→
[assignment-operator](Expressions.md#assignment-operator)[try-operator](Expressions.md#try-operator)~opt~[prefix-expression](Expressions.md#prefix-expression)

[‌](){#TP40016643-CH32-NoLink_406}

binary-expression


→
[conditional-operator](Expressions.md#conditional-operator)[try-operator](Expressions.md#try-operator)~opt~[prefix-expression](Expressions.md#prefix-expression)

[‌](){#TP40016643-CH32-NoLink_407}

binary-expression


→
[type-casting-operator](Expressions.md#type-casting-operator)

[‌](){#binary-expressions}

binary-expressions


→
[binary-expression](Expressions.md#binary-expression)[binary-expressions](Expressions.md#binary-expressions)~opt~







[‌](){#TP40016643-CH32-ID386}
### Assignment Operator {#assignment-operator .section-name}

The *assignment operator* sets a new value for a given expression. It has the following form:




-   ``` {.code-voice}
    expression = value
    ```



The value of the *expression* is set to the value obtained by evaluating the *value*. If the *expression* is a tuple, the *value* must be a tuple with the same number of elements. (Nested tuples are allowed.) Assignment is performed from each part of the *value* to the corresponding part of the *expression*. For example:







1.  `(a`{.code-voice}, `_`{.kt}, (`b`{.vc}, `c`{.vc})) = (`"test"`{.s}, `9.45`{.m}, (`12`{.m}, `3`{.m}))
2.  `// a is "test", b is 12, c is 3, and 9.45 is ignored`{.code-voice}







The assignment operator does not return any value.



Grammar of an assignment operator



[‌](){#assignment-operator}

assignment-operator


→
`=`{.literal}









[‌](){#TP40016643-CH32-ID387}
### Ternary Conditional Operator {#ternary-conditional-operator .section-name}

The *ternary conditional operator* evaluates to one of two given values based on the value of a condition. It has the following form:




-   ``` {.code-voice}
    condition ? expression used if true : expression used if false
    ```



If the *condition* evaluates to `true`{.code-voice}, the conditional operator evaluates the first expression and returns its value. Otherwise, it evaluates the second expression and returns its value. The unused expression is not evaluated.

For an example that uses the ternary conditional operator, see [Ternary Conditional Operator](BasicOperators.md#TP40016643-CH6-ID71).



Grammar of a conditional operator



[‌](){#conditional-operator}

conditional-operator


→
`?`{.literal}[try-operator](Expressions.md#try-operator)~opt~[expression](Expressions.md#expression)`:`{.literal}









[‌](){#TP40016643-CH32-ID388}
### Type-Casting Operators {#type-casting-operators .section-name}

There are four type-casting operators: the `is`{.code-voice} operator, the `as`{.code-voice} operator, the `as?`{.code-voice} operator, and the `as!`{.code-voice} operator.

They have the following form:




-   ``` {.code-voice}
    expression is type
    ```

-   ``` {.code-voice}
    expression as type
    ```

-   ``` {.code-voice}
    expression as? type
    ```

-   ``` {.code-voice}
    expression as! type
    ```



The `is`{.code-voice} operator checks at runtime whether the *expression* can be cast to the specified *type*. It returns `true`{.code-voice} if the *expression* can be cast to the specified *type*; otherwise, it returns `false`{.code-voice}.

The `as`{.code-voice} operator performs a cast when it is known at compile time that the cast always succeeds, such as upcasting or bridging. Upcasting lets you use an expression as an instance of its type’s supertype, without using an intermediate variable. The following approaches are equivalent:







1.  `func`{.code-voice} `f`{.vc}(`any`{.vc}: `Any`{.n}) { `print`{.vc}(`"Function for Any"`{.s}) }
2.  `func`{.code-voice} `f`{.vc}(`int`{.vc}: `Int`{.n}) { `print`{.vc}(`"Function for Int"`{.s}) }
3.  `let`{.code-voice} `x`{.vc} = `10`{.m}
4.  `f`{.code-voice}(`x`{.vc})
5.  `// prints "Function for Int"`{.code-voice}
6.  ` `{.code-voice}
7.  `let`{.code-voice} `y`{.vc}: `Any`{.n} = `x`{.vc}
8.  `f`{.code-voice}(`y`{.vc})
9.  `// prints "Function for Any"`{.code-voice}
10. ` `{.code-voice}
11. `f`{.code-voice}(`x`{.vc} `as`{.kt} `Any`{.n})
12. `// prints "Function for Any"`{.code-voice}







Bridging lets you use an expression of a Swift standard library type such as `String`{.code-voice} as its corresponding Foundation type such as `NSString`{.code-voice} without needing to create a new instance. For more information on bridging, see Working with Cocoa Data Types in *Using Swift with Cocoa and Objective-C (Swift 2.1)*.

The `as?`{.code-voice} operator performs a conditional cast of the *expression* to the specified *type*. The `as?`{.code-voice} operator returns an optional of the specified *type*. At runtime, if the cast succeeds, the value of *expression* is wrapped in an optional and returned; otherwise, the value returned is `nil`{.code-voice}. If casting to the specified *type* is guaranteed to fail or is guaranteed to succeed, a compile-time error is raised.

The `as!`{.code-voice} operator performs a forced cast of the *expression* to the specified *type*. The `as!`{.code-voice} operator returns a value of the specified *type*, not an optional type. If the cast fails, a runtime error is raised. The behavior of `x as! T`{.code-voice} is the same as the behavior of `(x as? T)!`{.code-voice}.

For more information about type casting and to see examples that use the type-casting operators, see [Type Casting](TypeCasting.md).



Grammar of a type-casting operator



[‌](){#type-casting-operator}

type-casting-operator


→
`is`{.literal}[type](Types.md#type)

[‌](){#TP40016643-CH32-NoLink_415}

type-casting-operator


→
`as`{.literal}[type](Types.md#type)

[‌](){#TP40016643-CH32-NoLink_416}

type-casting-operator


→
`as`{.literal}`?`{.literal}[type](Types.md#type)

[‌](){#TP40016643-CH32-NoLink_417}

type-casting-operator


→
`as`{.literal}`!`{.literal}[type](Types.md#type)











[‌](){#TP40016643-CH32-ID389}
### Primary Expressions {#primary-expressions .section-name}

*Primary expressions* are the most basic kind of expression. They can be used as expressions on their own, and they can be combined with other tokens to make prefix expressions, binary expressions, and postfix expressions.



Grammar of a primary expression



[‌](){#primary-expression}

primary-expression


→
[identifier](LexicalStructure.md#identifier)[generic-argument-clause](GenericParametersAndArguments.md#generic-argument-clause)~opt~

[‌](){#TP40016643-CH32-NoLink_420}

primary-expression


→
[literal-expression](Expressions.md#literal-expression)

[‌](){#TP40016643-CH32-NoLink_421}

primary-expression


→
[self-expression](Expressions.md#self-expression)

[‌](){#TP40016643-CH32-NoLink_422}

primary-expression


→
[superclass-expression](Expressions.md#superclass-expression)

[‌](){#TP40016643-CH32-NoLink_423}

primary-expression


→
[closure-expression](Expressions.md#closure-expression)

[‌](){#TP40016643-CH32-NoLink_424}

primary-expression


→
[parenthesized-expression](Expressions.md#parenthesized-expression)

[‌](){#TP40016643-CH32-NoLink_425}

primary-expression


→
[implicit-member-expression](Expressions.md#implicit-member-expression)

[‌](){#TP40016643-CH32-NoLink_426}

primary-expression


→
[wildcard-expression](Expressions.md#wildcard-expression)







[‌](){#TP40016643-CH32-ID390}
### Literal Expression {#literal-expression .section-name}

A *literal expression* consists of either an ordinary literal (such as a string or a number), an array or dictionary literal, or one of the following special literals:



+--------------------------+--------------------------+--------------------------+
| Literal                  | Type                     | Value                    |
+==========================+==========================+==========================+
| `__FILE__`{.code-voice}  | `String`{.code-voice}    | The name of the file in  |
|                          |                          | which it appears.        |
+--------------------------+--------------------------+--------------------------+
| `__LINE__`{.code-voice}  | `Int`{.code-voice}       | The line number on which |
|                          |                          | it appears.              |
+--------------------------+--------------------------+--------------------------+
| `__COLUMN__`{.code-voice | `Int`{.code-voice}       | The column number in     |
| }                        |                          | which it begins.         |
+--------------------------+--------------------------+--------------------------+
| `__FUNCTION__`{.code-voi | `String`{.code-voice}    | The name of the          |
| ce}                      |                          | declaration in which it  |
|                          |                          | appears.                 |
+--------------------------+--------------------------+--------------------------+



Inside a function, the value of `__FUNCTION__`{.code-voice} is the name of that function, inside a method it is the name of that method, inside a property getter or setter it is the name of that property, inside special members like `init`{.code-voice} or `subscript`{.code-voice} it is the name of that keyword, and at the top level of a file it is the name of the current module.

When used as the default value of a function or method, the special literal’s value is determined when the default value expression is evaluated at the call site.







1.  `func`{.code-voice} `logFunctionName`{.vc}(`string`{.vc}: `String`{.n} = `__FUNCTION__`{.kt}) {
2.  `    print`{.code-voice}(`string`{.vc})
3.  `}`{.code-voice}
4.  `func`{.code-voice} `myFunction`{.vc}() {
5.  `    logFunctionName`{.code-voice}() `// Prints "myFunction()".`{.c}
6.  `}`{.code-voice}







An *array literal* is an ordered collection of values. It has the following form:




-   ``` {.code-voice}
    [value 1, value 2, ...]
    ```



The last expression in the array can be followed by an optional comma. The value of an array literal has type `[T]`{.code-voice}, where `T`{.code-voice} is the type of the expressions inside it. If there are expressions of multiple types, `T`{.code-voice} is their closest common supertype. Empty array literals are written using an empty pair of square brackets and can be used to create an empty array of a specified type.







1.  `var`{.code-voice} `emptyArray`{.vc}: \[`Double`{.n}\] = \[\]







A *dictionary literal* is an unordered collection of key-value pairs. It has the following form:




-   ``` {.code-voice}
    [key 1: value 1, key 2: value 2, ...]
    ```



The last expression in the dictionary can be followed by an optional comma. The value of a dictionary literal has type `[Key: Value]`{.code-voice}, where `Key`{.code-voice} is the type of its key expressions and `Value`{.code-voice} is the type of its value expressions. If there are expressions of multiple types, `Key`{.code-voice} and `Value`{.code-voice} are the closest common supertype for their respective values. An empty dictionary literal is written as a colon inside a pair of brackets (`[:]`{.code-voice}) to distinguish it from an empty array literal. You can use an empty dictionary literal to create an empty dictionary literal of specified key and value types.







1.  `var`{.code-voice} `emptyDictionary`{.vc}: \[`String`{.n}: `Double`{.n}\] = \[:\]









Grammar of a literal expression



[‌](){#literal-expression}

literal-expression


→
[literal](LexicalStructure.md#literal)

[‌](){#TP40016643-CH32-NoLink_429}

literal-expression


→

[array-literal](Expressions.md#array-literal)

[dictionary-literal](Expressions.md#dictionary-literal)


[‌](){#TP40016643-CH32-NoLink_430}

literal-expression


→

`__FILE__`{.literal}

`__LINE__`{.literal}

`__COLUMN__`{.literal}

`__FUNCTION__`{.literal}






[‌](){#array-literal}

array-literal


→
`[`{.literal}[array-literal-items](Expressions.md#array-literal-items)~opt~`]`{.literal}

[‌](){#array-literal-items}

array-literal-items


→

[array-literal-item](Expressions.md#array-literal-item)`,`{.literal}~opt~

[array-literal-item](Expressions.md#array-literal-item)`,`{.literal}[array-literal-items](Expressions.md#array-literal-items)


[‌](){#array-literal-item}

array-literal-item


→
[expression](Expressions.md#expression)





[‌](){#dictionary-literal}

dictionary-literal


→

`[`{.literal}[dictionary-literal-items](Expressions.md#dictionary-literal-items)`]`{.literal}

`[`{.literal}`:`{.literal}`]`{.literal}


[‌](){#dictionary-literal-items}

dictionary-literal-items


→

[dictionary-literal-item](Expressions.md#dictionary-literal-item)`,`{.literal}~opt~

[dictionary-literal-item](Expressions.md#dictionary-literal-item)`,`{.literal}[dictionary-literal-items](Expressions.md#dictionary-literal-items)


[‌](){#dictionary-literal-item}

dictionary-literal-item


→
[expression](Expressions.md#expression)`:`{.literal}[expression](Expressions.md#expression)









[‌](){#TP40016643-CH32-ID391}
### Self Expression {#self-expression .section-name}

The `self`{.code-voice} expression is an explicit reference to the current type or instance of the type in which it occurs. It has the following forms:




-   ``` {.code-voice}
    self
    ```

-   ``` {.code-voice}
    self.member name
    ```

-   ``` {.code-voice}
    self[subscript index]
    ```

-   ``` {.code-voice}
    self(initializer arguments)
    ```

-   ``` {.code-voice}
    self.init(initializer arguments)
    ```



In an initializer, subscript, or instance method, `self`{.code-voice} refers to the current instance of the type in which it occurs. In a type method, `self`{.code-voice} refers to the current type in which it occurs.

The `self`{.code-voice} expression is used to specify scope when accessing members, providing disambiguation when there is another variable of the same name in scope, such as a function parameter. For example:







1.  `class`{.code-voice} `SomeClass`{.vc} {
2.  `    var`{.code-voice} `greeting`{.vc}: `String`{.n}
3.  `    init`{.code-voice}(`greeting`{.vc}: `String`{.n}) {
4.  `        self`{.code-voice}.`greeting`{.vc} = `greeting`{.vc}
5.  `    }`{.code-voice}
6.  `}`{.code-voice}







In a mutating method of a value type, you can assign a new instance of that value type to `self`{.code-voice}. For example:







1.  `struct`{.code-voice} `Point`{.vc} {
2.  `    var`{.code-voice} `x`{.vc} = `0.0`{.m}, `y`{.vc} = `0.0`{.m}
3.  `    mutating`{.code-voice} `func`{.kt} `moveByX`{.vc}(`deltaX`{.vc}: `Double`{.n}, `y`{.vc} `deltaY`{.vc}: `Double`{.n}) {
4.  `        self`{.code-voice} = `Point`{.vc}(`x`{.vc}: `x`{.vc} + `deltaX`{.vc}, `y`{.vc}: `y`{.vc} + `deltaY`{.vc})
5.  `    }`{.code-voice}
6.  `}`{.code-voice}









Grammar of a self expression



[‌](){#self-expression}

self-expression


→

`self`{.literal}

[self-method-expression](Expressions.md#self-method-expression)

[self-subscript-expression](Expressions.md#self-subscript-expression)

[self-initializer-expression](Expressions.md#self-initializer-expression)






[‌](){#self-method-expression}

self-method-expression


→
`self`{.literal}`.`{.literal}[identifier](LexicalStructure.md#identifier)

[‌](){#self-subscript-expression}

self-subscript-expression


→
`self`{.literal}`[`{.literal}[expression-list](Expressions.md#expression-list)`]`{.literal}

[‌](){#self-initializer-expression}

self-initializer-expression


→
`self`{.literal}`.`{.literal}`init`{.literal}









[‌](){#TP40016643-CH32-ID392}
### Superclass Expression {#superclass-expression .section-name}

A *superclass expression* lets a class interact with its superclass. It has one of the following forms:




-   ``` {.code-voice}
    super.member name
    ```

-   ``` {.code-voice}
    super[subscript index]
    ```

-   ``` {.code-voice}
    super.init(initializer arguments)
    ```



The first form is used to access a member of the superclass. The second form is used to access the superclass’s subscript implementation. The third form is used to access an initializer of the superclass.

Subclasses can use a superclass expression in their implementation of members, subscripting, and initializers to make use of the implementation in their superclass.



Grammar of a superclass expression



[‌](){#superclass-expression}

superclass-expression


→

[superclass-method-expression](Expressions.md#superclass-method-expression)

[superclass-subscript-expression](Expressions.md#superclass-subscript-expression)

[superclass-initializer-expression](Expressions.md#superclass-initializer-expression)






[‌](){#superclass-method-expression}

superclass-method-expression


→
`super`{.literal}`.`{.literal}[identifier](LexicalStructure.md#identifier)

[‌](){#superclass-subscript-expression}

superclass-subscript-expression


→
`super`{.literal}`[`{.literal}[expression-list](Expressions.md#expression-list)`]`{.literal}

[‌](){#superclass-initializer-expression}

superclass-initializer-expression


→
`super`{.literal}`.`{.literal}`init`{.literal}









[‌](){#TP40016643-CH32-ID393}
### Closure Expression {#closure-expression .section-name}

A *closure expression* creates a closure, also known as a *lambda* or an *anonymous function* in other programming languages. Like a function declaration, a closure contains statements which it executes, and it captures constants and variables from its enclosing scope. It has the following form:




-   ``` {.code-voice}
    { (parameters) -> return type in
    ```

-   ``` {.code-voice}
        statements
    ```

-   ``` {.code-voice}
    }
    ```



The *parameters* have the same form as the parameters in a function declaration, as described in [Function Declaration](Declarations.md#TP40016643-CH34-ID362).

There are several special forms that allow closures to be written more concisely:

-   A closure can omit the types of its parameters, its return type, or both. If you omit the parameter names and both types, omit the `in`{.code-voice} keyword before the statements. If the omitted types can’t be inferred, a compile-time error is raised.

-   A closure may omit names for its parameters. Its parameters are then implicitly named `$`{.code-voice} followed by their position: `$0`{.code-voice}, `$1`{.code-voice}, `$2`{.code-voice}, and so on.

-   A closure that consists of only a single expression is understood to return the value of that expression. The contents of this expression are also considered when performing type inference on the surrounding expression.

The following closure expressions are equivalent:







1.  `myFunction`{.code-voice} {
2.  `    (x`{.code-voice}: `Int`{.n}, `y`{.vc}: `Int`{.n}) -&gt; `Int`{.n} `in`{.kt}
3.  `    return`{.code-voice} `x`{.vc} + `y`{.vc}
4.  `}`{.code-voice}
5.  ` `{.code-voice}
6.  `myFunction`{.code-voice} {
7.  `    (x`{.code-voice}, `y`{.vc}) `in`{.kt}
8.  `    return`{.code-voice} `x`{.vc} + `y`{.vc}
9.  `}`{.code-voice}
10. ` `{.code-voice}
11. `myFunction`{.code-voice} { `return`{.kt} `$0`{.vc} + `$1`{.vc} }
12. ` `{.code-voice}
13. `myFunction`{.code-voice} { `$0`{.vc} + `$1`{.vc} }







For information about passing a closure as an argument to a function, see [Function Call Expression](Expressions.md#TP40016643-CH32-ID398).



[‌](){#TP40016643-CH32-ID544}
### Capture Lists {#capture-lists .section-name}

By default, a closure expression captures constants and variables from its surrounding scope with strong references to those values. You can use a *capture list* to explicitly control how values are captured in a closure.

A capture list is written as a comma separated list of expressions surrounded by square brackets, before the list of parameters. If you use a capture list, you must also use the `in`{.code-voice} keyword, even if you omit the parameter names, parameter types, and return type.

The entries in the capture list are initialized when the closure is created. For each entry in the capture list, a constant is initialized to the value of the constant or variable that has the same name in the surrounding scope. For example in the code below, `a`{.code-voice} is included in the capture list but `b`{.code-voice} is not, which gives them different behavior.







1.  `var`{.code-voice} `a`{.vc} = `0`{.m}
2.  `var`{.code-voice} `b`{.vc} = `0`{.m}
3.  `let`{.code-voice} `closure`{.vc} = { \[`a`{.vc}\] `in`{.kt}
4.  `    print`{.code-voice}(`a`{.vc}, `b`{.vc})
5.  `}`{.code-voice}
6.  ` `{.code-voice}
7.  `a`{.code-voice} = `10`{.m}
8.  `b`{.code-voice} = `10`{.m}
9.  `closure`{.code-voice}()
10. `// prints "0 10"`{.code-voice}







There are two different things named `a`{.code-voice}, the variable in the surrounding scope and the constant in the closure’s scope, but only one variable named `b`{.code-voice}. The `a`{.code-voice} in the inner scope is initialized with the value of the `a`{.code-voice} in the outer scope when the closure is created, but their values are not connected in any special way. This means that a change to the value of `a`{.code-voice} in the outer scope does not effect the value of `a`{.code-voice} in the inner scope, nor does a change to `a`{.code-voice} inside the closure effect the value of `a`{.code-voice} outside the closure. In contrast, there is only one variable named `b`{.code-voice}—the `b`{.code-voice} in the outer scope—so changes from inside or outside the closure are visible in both places.

This distinction is not visible when the captured variable’s type has reference semantics. For example, there are two things named `x`{.code-voice} in the code below, a variable in the outer scope and a constant in the inner scope, but they both refer to the same object because of reference semantics.







1.  `class`{.code-voice} `SimpleClass`{.vc} {
2.  `    var`{.code-voice} `value`{.vc}: `Int`{.n} = `0`{.m}
3.  `}`{.code-voice}
4.  `var`{.code-voice} `x`{.vc} = `SimpleClass`{.vc}()
5.  `var`{.code-voice} `y`{.vc} = `SimpleClass`{.vc}()
6.  `let`{.code-voice} `closure`{.vc} = { \[`x`{.vc}\] `in`{.kt}
7.  `    print`{.code-voice}(`x`{.vc}.`value`{.vc}, `y`{.vc}.`value`{.vc})
8.  `}`{.code-voice}
9.  ` `{.code-voice}
10. `x`{.code-voice}.`value`{.vc} = `10`{.m}
11. `y`{.code-voice}.`value`{.vc} = `10`{.m}
12. `closure`{.code-voice}()
13. `// prints "10 10"`{.code-voice}







If the type of the expression’s value is a class, you can mark the expression in a capture list with `weak`{.code-voice} or `unowned`{.code-voice} to capture a weak or unowned reference to the expression’s value.







1.  `myFunction`{.code-voice} { `print`{.vc}(`self`{.kt}.`title`{.vc}) } `// strong capture`{.c}
2.  `myFunction`{.code-voice} { \[`weak`{.vc} `self`{.kt}\] `in`{.kt} `print`{.vc}(`self`{.kt}!.`title`{.vc}) } `// weak capture`{.c}
3.  `myFunction`{.code-voice} { \[`unowned`{.vc} `self`{.kt}\] `in`{.kt} `print`{.vc}(`self`{.kt}.`title`{.vc}) } `// unowned capture`{.c}







You can also bind an arbitrary expression to a named value in a capture list. The expression is evaluated when the closure is created, and the value is captured with the specified strength. For example:







1.  `// Weak capture of "self.parent" as "parent"`{.code-voice}
2.  `myFunction`{.code-voice} { \[`weak`{.vc} `parent`{.vc} = `self`{.kt}.`parent`{.vc}\] `in`{.kt} `print`{.vc}(`parent`{.vc}!.`title`{.vc}) }







For more information and examples of closure expressions, see [Closure Expressions](Closures.md#TP40016643-CH11-ID95). For more information and examples of capture lists, see [Resolving Strong Reference Cycles for Closures](AutomaticReferenceCounting.md#TP40016643-CH20-ID57).



Grammar of a closure expression



[‌](){#closure-expression}

closure-expression


→
`{`{.literal}[closure-signature](Expressions.md#closure-signature)~opt~[statements](Statements.md#statements)`}`{.literal}





[‌](){#closure-signature}

closure-signature


→
[parameter-clause](Declarations.md#parameter-clause)[function-result](Declarations.md#function-result)~opt~`in`{.literal}

[‌](){#TP40016643-CH32-NoLink_450}

closure-signature


→
[identifier-list](LexicalStructure.md#identifier-list)[function-result](Declarations.md#function-result)~opt~`in`{.literal}

[‌](){#TP40016643-CH32-NoLink_451}

closure-signature


→
[capture-list](Expressions.md#capture-list)[parameter-clause](Declarations.md#parameter-clause)[function-result](Declarations.md#function-result)~opt~`in`{.literal}

[‌](){#TP40016643-CH32-NoLink_452}

closure-signature


→
[capture-list](Expressions.md#capture-list)[identifier-list](LexicalStructure.md#identifier-list)[function-result](Declarations.md#function-result)~opt~`in`{.literal}

[‌](){#TP40016643-CH32-NoLink_453}

closure-signature


→
[capture-list](Expressions.md#capture-list)`in`{.literal}





[‌](){#capture-list}

capture-list


→
`[`{.literal}[capture-list-items](Expressions.md#capture-list-items)`]`{.literal}

[‌](){#capture-list-items}

capture-list-items


→

[capture-list-item](Expressions.md#capture-list-item)

[capture-list-item](Expressions.md#capture-list-item)`,`{.literal}[capture-list-items](Expressions.md#capture-list-items)


[‌](){#capture-list-item}

capture-list-item


→
[capture-specifier](Expressions.md#capture-specifier)~opt~[expression](Expressions.md#expression)

[‌](){#capture-specifier}

capture-specifier


→

`weak`{.literal}

`unowned`{.literal}

`unowned(safe)`{.literal}

`unowned(unsafe)`{.literal}












[‌](){#TP40016643-CH32-ID394}
### Implicit Member Expression {#implicit-member-expression .section-name}

An *implicit member expression* is an abbreviated way to access a member of a type, such as an enumeration case or a type method, in a context where type inference can determine the implied type. It has the following form:




-   ``` {.code-voice}
    .member name
    ```



For example:







1.  `var`{.code-voice} `x`{.vc} = `MyEnumeration`{.vc}.`SomeValue`{.vc}
2.  `x`{.code-voice} = .`AnotherValue`{.vc}









Grammar of a implicit member expression



[‌](){#implicit-member-expression}

implicit-member-expression


→
`.`{.literal}[identifier](LexicalStructure.md#identifier)









[‌](){#TP40016643-CH32-ID395}
### Parenthesized Expression {#parenthesized-expression .section-name}

A *parenthesized expression* consists of a comma-separated list of expressions surrounded by parentheses. Each expression can have an optional identifier before it, separated by a colon (`:`{.code-voice}). It has the following form:




-   ``` {.code-voice}
    (identifier 1: expression 1, identifier 2: expression 2, ...)
    ```



Use parenthesized expressions to create tuples and to pass arguments to a function call. If there is only one value inside the parenthesized expression, the type of the parenthesized expression is the type of that value. For example, the type of the parenthesized expression `(1)`{.code-voice} is `Int`{.code-voice}, not `(Int)`{.code-voice}.



Grammar of a parenthesized expression



[‌](){#parenthesized-expression}

parenthesized-expression


→
`(`{.literal}[expression-element-list](Expressions.md#expression-element-list)~opt~`)`{.literal}

[‌](){#expression-element-list}

expression-element-list


→

[expression-element](Expressions.md#expression-element)

[expression-element](Expressions.md#expression-element)`,`{.literal}[expression-element-list](Expressions.md#expression-element-list)


[‌](){#expression-element}

expression-element


→

[expression](Expressions.md#expression)

[identifier](LexicalStructure.md#identifier)`:`{.literal}[expression](Expressions.md#expression)










[‌](){#TP40016643-CH32-ID396}
### Wildcard Expression {#wildcard-expression .section-name}

A *wildcard expression* is used to explicitly ignore a value during an assignment. For example, in the following assignment 10 is assigned to `x`{.code-voice} and 20 is ignored:







1.  `(x`{.code-voice}, `_`{.kt}) = (`10`{.m}, `20`{.m})
2.  `// x is 10, and 20 is ignored`{.code-voice}









Grammar of a wildcard expression



[‌](){#wildcard-expression}

wildcard-expression


→
`_`{.literal}











[‌](){#TP40016643-CH32-ID397}
### Postfix Expressions {#postfix-expressions .section-name}

*Postfix expressions* are formed by applying a postfix operator or other postfix syntax to an expression. Syntactically, every primary expression is also a postfix expression.

For information about the behavior of these operators, see [Basic Operators](BasicOperators.md) and [Advanced Operators](AdvancedOperators.md).

For information about the operators provided by the Swift standard library, see *Swift Standard Library Operators Reference*.



Grammar of a postfix expression



[‌](){#postfix-expression}

postfix-expression


→
[primary-expression](Expressions.md#primary-expression)

[‌](){#TP40016643-CH32-NoLink_468}

postfix-expression


→
[postfix-expression](Expressions.md#postfix-expression)[postfix-operator](LexicalStructure.md#postfix-operator)

[‌](){#TP40016643-CH32-NoLink_469}

postfix-expression


→
[function-call-expression](Expressions.md#function-call-expression)

[‌](){#TP40016643-CH32-NoLink_470}

postfix-expression


→
[initializer-expression](Expressions.md#initializer-expression)

[‌](){#TP40016643-CH32-NoLink_471}

postfix-expression


→
[explicit-member-expression](Expressions.md#explicit-member-expression)

[‌](){#TP40016643-CH32-NoLink_472}

postfix-expression


→
[postfix-self-expression](Expressions.md#postfix-self-expression)

[‌](){#TP40016643-CH32-NoLink_473}

postfix-expression


→
[dynamic-type-expression](Expressions.md#dynamic-type-expression)

[‌](){#TP40016643-CH32-NoLink_474}

postfix-expression


→
[subscript-expression](Expressions.md#subscript-expression)

[‌](){#TP40016643-CH32-NoLink_475}

postfix-expression


→
[forced-value-expression](Expressions.md#forced-value-expression)

[‌](){#TP40016643-CH32-NoLink_476}

postfix-expression


→
[optional-chaining-expression](Expressions.md#optional-chaining-expression)







[‌](){#TP40016643-CH32-ID398}
### Function Call Expression {#function-call-expression .section-name}

A *function call expression* consists of a function name followed by a comma-separated list of the function’s arguments in parentheses. Function call expressions have the following form:




-   ``` {.code-voice}
    function name(argument value 1, argument value 2)
    ```



The *function name* can be any expression whose value is of a function type.

If the function definition includes names for its parameters, the function call must include names before its argument values separated by a colon (`:`{.code-voice}). This kind of function call expression has the following form:




-   ``` {.code-voice}
    function name(argument name 1: argument value 1, argument name 2: argument value 2)
    ```



A function call expression can include a trailing closure in the form of a closure expression immediately after the closing parenthesis. The trailing closure is understood as an argument to the function, added after the last parenthesized argument. The following function calls are equivalent:







1.  `// someFunction takes an integer and a closure as its arguments`{.code-voice}
2.  `someFunction`{.code-voice}(`x`{.vc}, `f`{.vc}: {`$0`{.vc} == `13`{.m}})
3.  `someFunction`{.code-voice}(`x`{.vc}) {`$0`{.vc} == `13`{.m}}







If the trailing closure is the function’s only argument, the parentheses can be omitted.







1.  `// someFunction takes a closure as its only argument`{.code-voice}
2.  `myData`{.code-voice}.`someMethod`{.vc}() {`$0`{.vc} == `13`{.m}}
3.  `myData`{.code-voice}.`someMethod`{.vc} {`$0`{.vc} == `13`{.m}}









Grammar of a function call expression



[‌](){#function-call-expression}

function-call-expression


→
[postfix-expression](Expressions.md#postfix-expression)[parenthesized-expression](Expressions.md#parenthesized-expression)

[‌](){#TP40016643-CH32-NoLink_479}

function-call-expression


→
[postfix-expression](Expressions.md#postfix-expression)[parenthesized-expression](Expressions.md#parenthesized-expression)~opt~[trailing-closure](Expressions.md#trailing-closure)

[‌](){#trailing-closure}

trailing-closure


→
[closure-expression](Expressions.md#closure-expression)









[‌](){#TP40016643-CH32-ID399}
### Initializer Expression {#initializer-expression .section-name}

An *initializer expression* provides access to a type’s initializer. It has the following form:




-   ``` {.code-voice}
    expression.init(initializer arguments)
    ```



You use the initializer expression in a function call expression to initialize a new instance of a type. You also use an initializer expression to delegate to the initializer of a superclass.







1.  `class`{.code-voice} `SomeSubClass`{.vc}: `SomeSuperClass`{.n} {
2.  `    override`{.code-voice} `init`{.kt}() {
3.  `        // subclass initialization goes here`{.code-voice}
4.  `        super`{.code-voice}.`init`{.kt}()
5.  `    }`{.code-voice}
6.  `}`{.code-voice}







Like a function, an initializer can be used as a value. For example:







1.  `// Type annotation is required because String has multiple initializers.`{.code-voice}
2.  `let`{.code-voice} `initializer`{.vc}: `Int`{.n} -&gt; `String`{.n} = `String`{.vc}.`init`{.kt}
3.  `let`{.code-voice} `oneTwoThree`{.vc} = \[`1`{.m}, `2`{.m}, `3`{.m}\].`map`{.vc}(`initializer`{.vc}).`reduce`{.vc}(`""`{.s}, `combine`{.vc}: +)
4.  `print`{.code-voice}(`oneTwoThree`{.vc})
5.  `// prints "123"`{.code-voice}







If you specify a type by name, you can access the type’s initializer without using an initializer expression. In all other cases, you must use an initializer expression.







1.  `let`{.code-voice} `s1`{.vc} = `SomeType`{.vc}.`init`{.kt}(`data`{.vc}: `3`{.m}) `// Valid`{.c}
2.  `let`{.code-voice} `s2`{.vc} = `SomeType`{.vc}(`data`{.vc}: `1`{.m}) `// Also valid`{.c}
3.  ` `{.code-voice}
4.  `let`{.code-voice} `s4`{.vc} = `someValue`{.vc}.`dynamicType`{.kt}(`data`{.vc}: `5`{.m}) `// Error`{.c}
5.  `let`{.code-voice} `s3`{.vc} = `someValue`{.vc}.`dynamicType`{.kt}.`init`{.kt}(`data`{.vc}: `7`{.m}) `// Valid`{.c}









Grammar of an initializer expression



[‌](){#initializer-expression}

initializer-expression


→
[postfix-expression](Expressions.md#postfix-expression)`.`{.literal}`init`{.literal}









[‌](){#TP40016643-CH32-ID400}
### Explicit Member Expression {#explicit-member-expression .section-name}

An *explicit member expression* allows access to the members of a named type, a tuple, or a module. It consists of a period (`.`{.code-voice}) between the item and the identifier of its member.




-   ``` {.code-voice}
    expression.member name
    ```



The members of a named type are named as part of the type’s declaration or extension. For example:







1.  `class`{.code-voice} `SomeClass`{.vc} {
2.  `    var`{.code-voice} `someProperty`{.vc} = `42`{.m}
3.  `}`{.code-voice}
4.  `let`{.code-voice} `c`{.vc} = `SomeClass`{.vc}()
5.  `let`{.code-voice} `y`{.vc} = `c`{.vc}.`someProperty`{.vc} `// Member access`{.c}







The members of a tuple are implicitly named using integers in the order they appear, starting from zero. For example:







1.  `var`{.code-voice} `t`{.vc} = (`10`{.m}, `20`{.m}, `30`{.m})
2.  `t`{.code-voice}.`0`{.m} = `t`{.vc}.`1`{.m}
3.  `// Now t is (20, 20, 30)`{.code-voice}







The members of a module access the top-level declarations of that module.

If a period appears at the beginning of a line, it is understood as part of an explicit member expression, not as an implicit member expression. For example, the following listing shows chained method calls split over several lines:







1.  `let`{.code-voice} `x`{.vc} = \[`10`{.m}, `3`{.m}, `20`{.m}, `15`{.m}, `4`{.m}\]
2.  `    .sort`{.code-voice}()
3.  `    .filter`{.code-voice} { `$0`{.vc} &gt; `5`{.m} }
4.  `    .map`{.code-voice} { `$0`{.vc} \* `100`{.m} }









Grammar of an explicit member expression



[‌](){#explicit-member-expression}

explicit-member-expression


→
[postfix-expression](Expressions.md#postfix-expression)`.`{.literal}[decimal-digits](LexicalStructure.md#decimal-digits)

[‌](){#TP40016643-CH32-NoLink_485}

explicit-member-expression


→
[postfix-expression](Expressions.md#postfix-expression)`.`{.literal}[identifier](LexicalStructure.md#identifier)[generic-argument-clause](GenericParametersAndArguments.md#generic-argument-clause)~opt~









[‌](){#TP40016643-CH32-ID401}
### Postfix Self Expression {#postfix-self-expression .section-name}

A postfix `self`{.code-voice} expression consists of an expression or the name of a type, immediately followed by `.self`{.code-voice}. It has the following forms:




-   ``` {.code-voice}
    expression.self
    ```

-   ``` {.code-voice}
    type.self
    ```



The first form evaluates to the value of the *expression*. For example, `x.self`{.code-voice} evaluates to `x`{.code-voice}.

The second form evaluates to the value of the *type*. Use this form to access a type as a value. For example, because `SomeClass.self`{.code-voice} evaluates to the `SomeClass`{.code-voice} type itself, you can pass it to a function or method that accepts a type-level argument.



Grammar of a self expression



[‌](){#postfix-self-expression}

postfix-self-expression


→
[postfix-expression](Expressions.md#postfix-expression)`.`{.literal}`self`{.literal}









[‌](){#TP40016643-CH32-ID402}
### Dynamic Type Expression {#dynamic-type-expression .section-name}

A `dynamicType`{.code-voice} expression consists of an expression, immediately followed by `.dynamicType`{.code-voice}. It has the following form:




-   ``` {.code-voice}
    expression.dynamicType
    ```



The *expression* can’t be the name of a type. The entire `dynamicType`{.code-voice} expression evaluates to the value of the runtime type of the *expression*, as the following example shows:







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
12. `// someInstance has a static type of SomeBaseClass at compile time, and`{.code-voice}
13. `// it has a dynamc type of SomeSubClass at runtime`{.code-voice}
14. `someInstance`{.code-voice}.`dynamicType`{.kt}.`printClassName`{.vc}()
15. `// prints "SomeSubClass"`{.code-voice}









Grammar of a dynamic type expression



[‌](){#dynamic-type-expression}

dynamic-type-expression


→
[postfix-expression](Expressions.md#postfix-expression)`.`{.literal}`dynamicType`{.literal}









[‌](){#TP40016643-CH32-ID403}
### Subscript Expression {#subscript-expression .section-name}

A *subscript expression* provides subscript access using the getter and setter of the corresponding subscript declaration. It has the following form:




-   ``` {.code-voice}
    expression[index expressions]
    ```



To evaluate the value of a subscript expression, the subscript getter for the *expression*’s type is called with the *index expressions* passed as the subscript parameters. To set its value, the subscript setter is called in the same way.

For information about subscript declarations, see [Protocol Subscript Declaration](Declarations.md#TP40016643-CH34-ID373).



Grammar of a subscript expression



[‌](){#subscript-expression}

subscript-expression


→
[postfix-expression](Expressions.md#postfix-expression)`[`{.literal}[expression-list](Expressions.md#expression-list)`]`{.literal}









[‌](){#TP40016643-CH32-ID404}
### Forced-Value Expression {#forced-value-expression .section-name}

A *forced-value expression* unwraps an optional value that you are certain is not `nil`{.code-voice}. It has the following form:




-   ``` {.code-voice}
    expression!
    ```



If the value of the *expression* is not `nil`{.code-voice}, the optional value is unwrapped and returned with the corresponding nonoptional type. Otherwise, a runtime error is raised.

The unwrapped value of a forced-value expression can be modified, either by mutating the value itself, or by assigning to one of the value’s members. For example:







1.  `var`{.code-voice} `x`{.vc}: `Int`{.n}? = `0`{.m}
2.  `x`{.code-voice}!++
3.  `// x is now 1`{.code-voice}
4.  ` `{.code-voice}
5.  `var`{.code-voice} `someDictionary`{.vc} = \[`"a"`{.s}: \[`1`{.m}, `2`{.m}, `3`{.m}\], `"b"`{.s}: \[`10`{.m}, `20`{.m}\]\]
6.  `someDictionary`{.code-voice}\[`"a"`{.s}\]!\[`0`{.m}\] = `100`{.m}
7.  `// someDictionary is now ["b": [10, 20], "a": [100, 2, 3]]`{.code-voice}









Grammar of a forced-value expression



[‌](){#forced-value-expression}

forced-value-expression


→
[postfix-expression](Expressions.md#postfix-expression)`!`{.literal}









[‌](){#TP40016643-CH32-ID405}
### Optional-Chaining Expression {#optional-chaining-expression .section-name}

An *optional-chaining expression* provides a simplified syntax for using optional values in postfix expressions. It has the following form:




-   ``` {.code-voice}
    expression?
    ```



The postfix `?`{.code-voice} operator makes an optional-chaining expression from an expression without changing the expression’s value.

Optional-chaining expressions must appear within a postfix expression, and they cause the postfix expression to be evaluated in a special way. If the value of the optional-chaining expression is `nil`{.code-voice}, all of the other operations in the postfix expression are ignored and the entire postfix expression evaluates to `nil`{.code-voice}. If the value of the optional-chaining expression is not `nil`{.code-voice}, the value of the optional-chaining expression is unwrapped and used to evaluate the rest of the postfix expression. In either case, the value of the postfix expression is still of an optional type.

If a postfix expression that contains an optional-chaining expression is nested inside other postfix expressions, only the outermost expression returns an optional type. In the example below, when `c`{.code-voice} is not `nil`{.code-voice}, its value is unwrapped and used to evaluate `.property`{.code-voice}, the value of which is used to evaluate `.performAction()`{.code-voice}. The entire expression `c?.property.performAction()`{.code-voice} has a value of an optional type.







1.  `var`{.code-voice} `c`{.vc}: `SomeClass`{.n}?
2.  `var`{.code-voice} `result`{.vc}: `Bool`{.n}? = `c`{.vc}?.`property`{.vc}.`performAction`{.vc}()







The following example shows the behavior of the example above without using optional chaining.







1.  `var`{.code-voice} `result`{.vc}: `Bool`{.n}? = `nil`{.kt}
2.  `if`{.code-voice} `let`{.kt} `unwrappedC`{.vc} = `c`{.vc} {
3.  `    result`{.code-voice} = `unwrappedC`{.vc}.`property`{.vc}.`performAction`{.vc}()
4.  `}`{.code-voice}







The unwrapped value of an optional-chaining expression can be modified, either by mutating the value itself, or by assigning to one of the value’s members. If the value of the optional-chaining expression is `nil`{.code-voice}, the expression on the right hand side of the assignment operator is not evaluated. For example:







1.  `func`{.code-voice} `someFunctionWithSideEffects`{.vc}() -&gt; `Int`{.n} {
2.  `    return`{.code-voice} `42`{.m} `// No actual side effects.`{.c}
3.  `}`{.code-voice}
4.  `var`{.code-voice} `someDictionary`{.vc} = \[`"a"`{.s}: \[`1`{.m}, `2`{.m}, `3`{.m}\], `"b"`{.s}: \[`10`{.m}, `20`{.m}\]\]
5.  ` `{.code-voice}
6.  `someDictionary`{.code-voice}\[`"not here"`{.s}\]?\[`0`{.m}\] = `someFunctionWithSideEffects`{.vc}()
7.  `// someFunctionWithSideEffects is not evaluated`{.code-voice}
8.  `// someDictionary is still ["b": [10, 20], "a": [1, 2, 3]]`{.code-voice}
9.  ` `{.code-voice}
10. `someDictionary`{.code-voice}\[`"a"`{.s}\]?\[`0`{.m}\] = `someFunctionWithSideEffects`{.vc}()
11. `// someFunctionWithSideEffects is evaluated and returns 42`{.code-voice}
12. `// someDictionary is now ["b": [10, 20], "a": [42, 2, 3]]`{.code-voice}









Grammar of an optional-chaining expression



[‌](){#optional-chaining-expression}

optional-chaining-expression


→
[postfix-expression](Expressions.md#postfix-expression)`?`{.literal}












