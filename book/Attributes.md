



[‌](){#TP40016643-CH35}[‌](){#TP40016643-CH35-ID347}
Attributes {#attributes .chapter-name}
----------



*Attributes* provide more information about a declaration or type. There are two kinds of attributes in Swift, those that apply to declarations and those that apply to types.

You specify an attribute by writing the `@`{.code-voice} symbol followed by the attribute’s name and any arguments that the attribute accepts:




-   ``` {.code-voice}
    @attribute name
    ```

-   ``` {.code-voice}
    @attribute name(attribute arguments)
    ```



Some declaration attributes accept arguments that specify more information about the attribute and how it applies to a particular declaration. These *attribute arguments* are enclosed in parentheses, and their format is defined by the attribute they belong to.





[‌](){#TP40016643-CH35-ID348}
### Declaration Attributes {#declaration-attributes .section-name}

You can apply a declaration attribute to declarations only. However, you can also apply the `noreturn`{.code-voice} attribute to a function or method *type*.

`autoclosure`{.code-voice}

:   This attribute is used to delay the evaluation of an expression by automatically wrapping that expression in a closure with no arguments. Apply this attribute to a parameter declaration for a function or method type that takes no arguments and that returns the type of the expression. Declarations with the `autoclosure`{.code-voice} attribute imply `noescape`{.code-voice} as well, except when passed the optional attribute argument `escaping`{.code-voice}. For an example of how to use the `autoclosure`{.code-voice} attribute, see [Autoclosures](Closures.md#TP40016643-CH11-ID543) and [Function Type](Types.md#TP40016643-CH31-ID449).

`available`{.code-voice}

:   Apply this attribute to any declaration to indicate the declaration’s lifecycle relative to certain platforms and operating system versions.

    The `available`{.code-voice} attribute always appears with a list of two or more comma-separated attribute arguments. These arguments begin with one of the following platform names:

    -   `iOS`{.code-voice}

    -   `iOSApplicationExtension`{.code-voice}

    -   `OSX`{.code-voice}

    -   `OSXApplicationExtension`{.code-voice}

    -   `watchOS`{.code-voice}

    -   `watchOSApplicationExtension`{.code-voice}

    -   `tvOS`{.code-voice}

    -   `tvOSApplicationExtension`{.code-voice}

    You can also use an asterisk (`*`{.code-voice}) to indicate the availability of the declaration on all of the platform names listed above.

    The remaining arguments can appear in any order and specify additional information about the declaration’s lifecycle, including important milestones.

    -   The `unavailable`{.code-voice} argument indicates that the declaration isn’t available on the specified platform.

    -   The `introduced`{.code-voice} argument indicates the first version of the specified platform in which the declaration was introduced. It has the following form:

        

        

        -   ``` {.code-voice}
            introduced=version number
            ```

        

        The *version number* consists of one or more positive integers, separated by periods.

    -   The `deprecated`{.code-voice} argument indicates the first version of the specified platform in which the declaration was deprecated. It has the following form:

        

        

        -   ``` {.code-voice}
            deprecated=version number
            ```

        

        The *version number* consists of one or more positive integers, separated by periods.

    -   The `obsoleted`{.code-voice} argument indicates the first version of the specified platform in which the declaration was obsoleted. When a declaration is obsoleted, it’s removed from the specified platform and can no longer be used. It has the following form:

        

        

        -   ``` {.code-voice}
            obsoleted=version number
            ```

        

        The *version number* consists of one or more positive integers, separated by periods.

    -   The `message`{.code-voice} argument is used to provide a textual message that’s displayed by the compiler when emitting a warning or error about the use of a deprecated or obsoleted declaration. It has the following form:

        

        

        -   ``` {.code-voice}
            message=message
            ```

        

        The *message* consists of a string literal.

    -   The `renamed`{.code-voice} argument is used to provide a textual message that indicates the new name for a declaration that’s been renamed. The new name is displayed by the compiler when emitting an error about the use of a renamed declaration. It has the following form:

        

        

        -   ``` {.code-voice}
            renamed=new name
            ```

        

        The *new name* consists of a string literal.

        You can use the `renamed`{.code-voice} argument in conjunction with the `unavailable`{.code-voice} argument and a type alias declaration to indicate to clients of your code that a declaration has been renamed. For example, this is useful when the name of a declaration is changed between releases of a framework or library.

        

        

        

        1.  `// First release`{.code-voice}
        2.  `protocol`{.code-voice} `MyProtocol`{.vc} {
        3.  `    // protocol definition`{.code-voice}
        4.  `}`{.code-voice}

        

        

        

        

        

        

        1.  `// Subsequent release renames MyProtocol`{.code-voice}
        2.  `protocol`{.code-voice} `MyRenamedProtocol`{.vc} {
        3.  `    // protocol definition`{.code-voice}
        4.  `}`{.code-voice}
        5.  ` `{.code-voice}
        6.  `@available`{.code-voice}(\*, `unavailable`{.vc}, `renamed`{.vc}=`"MyRenamedProtocol"`{.s})
        7.  `typealias`{.code-voice} `MyProtocol`{.vc} = `MyRenamedProtocol`{.n}

        

        

        

    You can apply multiple `available`{.code-voice} attributes on a single declaration to specify the declaration’s availability on different platforms. The compiler uses an `available`{.code-voice} attribute only when the attribute specifies a platform that matches the current target platform.

    If an `available`{.code-voice} attribute only specifies an `introduced`{.code-voice} argument in addition to a platform name argument, the following shorthand syntax can be used instead:

    

    

    -   ``` {.code-voice}
        @available(platform name version number, *)
        ```

    

    The shorthand syntax for `available`{.code-voice} attributes allows for availability for multiple platforms to be expressed concisely. Although the two forms are functionally equivalent, the shorthand form is preferred whenever possible.

    

    

    

    1.  `@available`{.code-voice}(`iOS`{.kt} `8.0`{.m}, `OSX`{.kt} `10.10`{.m}, \*)
    2.  `class`{.code-voice} `MyClass`{.vc} {
    3.  `    // class definition`{.code-voice}
    4.  `}`{.code-voice}

    

    

    



`objc`{.code-voice}

:   Apply this attribute to any declaration that can be represented in Objective-C—for example, non-nested classes, protocols, nongeneric enumerations (constrained to integer raw-value types), properties and methods (including getters and setters) of classes and protocols, initializers, deinitializers, and subscripts. The `objc`{.code-voice} attribute tells the compiler that a declaration is available to use in Objective-C code.

    Classes marked with the `objc`{.code-voice} attribute must inherit from a class defined in Objective-C. If you apply the `objc`{.code-voice} attribute to a class or protocol, it’s implicitly applied to the Objective-C compatible members of that class or protocol. The compiler also implicitly adds the `objc`{.code-voice} attribute to a class that inherits from another class marked with the `objc`{.code-voice} attribute or a class defined in Objective-C. Protocols marked with the `objc`{.code-voice} attribute can’t inherit from protocols that aren’t.

    If you apply the `objc`{.code-voice} attribute to an enumeration, each enumeration case is exposed to Objective-C code as the concatenation of the enumeration name and the case name. For example, a case named `Venus`{.code-voice} in a Swift `Planet`{.code-voice} enumeration is exposed to Objective-C code as a case named `PlanetVenus`{.code-voice}.

    The `objc`{.code-voice} attribute optionally accepts a single attribute argument, which consists of an identifier. Use this attribute when you want to expose a different name to Objective-C for the entity the `objc`{.code-voice} attribute applies to. You can use this argument to name classes, protocols, methods, getters, setters, and initializers. The example below exposes the getter for the `enabled`{.code-voice} property of the `ExampleClass`{.code-voice} to Objective-C code as `isEnabled`{.code-voice} rather than just as the name of the property itself.

    

    

    

    1.  `@objc`{.code-voice}
    2.  `class`{.code-voice} `ExampleClass`{.vc}: `NSObject`{.n} {
    3.  `    var`{.code-voice} `enabled`{.vc}: `Bool`{.n} {
    4.  `        @objc`{.code-voice}(`isEnabled`{.vc}) `get`{.kt} {
    5.  `            // Return the appropriate value`{.code-voice}
    6.  `        }`{.code-voice}
    7.  `    }`{.code-voice}
    8.  `}`{.code-voice}

    

    

    



`noescape`{.code-voice}

:   Apply this attribute to a function or method declaration to indicate that a parameter will not be stored for later execution, such that it is guaranteed not to outlive the lifetime of the call. Function type parameters with the `noescape`{.code-voice} declaration attribute do not require explicit use of `self.`{.code-voice} for properties or methods. For an example of how to use the `noescape`{.code-voice} attribute, see [Nonescaping Closures](Closures.md#TP40016643-CH11-ID546).

`nonobjc`{.code-voice}

:   Apply this attribute to a method, property, subscript, or initializer declaration to suppress an implicit `objc`{.code-voice} attribute. The `nonobjc`{.code-voice} attribute tells the compiler to make the declaration unavailable in Objective-C code, even though it is possible to represent it in Objective-C.

    You use the `nonobjc`{.code-voice} attribute to resolve circularity for bridging methods in a class marked with the `objc`{.code-voice} attribute, and to allow overloading of methods and initializers in a class marked with the `objc`{.code-voice} attribute.

    A method marked with the `nonobjc`{.code-voice} attribute cannot override a method marked with the `objc`{.code-voice} attribute. However, a method marked with the `objc`{.code-voice} attribute can override a method marked with the `nonobjc`{.code-voice} attribute. Similarly, a method marked with the `nonobjc`{.code-voice} attribute cannot satisfy a protocol requirement for a method marked with the `@objc`{.code-voice} attribute.

`noreturn`{.code-voice}

:   Apply this attribute to a function or method declaration to indicate that the corresponding type of that function or method, `T`{.code-voice}, is `@noreturn T`{.code-voice}. You can mark a function or method type with this attribute to indicate that the function or method doesn’t return to its caller.

    You can override a function or method that is not marked with the `noreturn`{.code-voice} attribute with a function or method that is. That said, you can’t override a function or method that is marked with the `noreturn`{.code-voice} attribute with a function or method that is not. Similar rules apply when you implement a protocol method in a conforming type.

`NSApplicationMain`{.code-voice}

:   Apply this attribute to a class to indicate that it is the application delegate. Using this attribute is equivalent to calling the `NSApplicationMain(_:_:)`{.code-voice} function and passing this class’s name as the name of the delegate class.

    If you do not use this attribute, supply a `main.swift`{.code-voice} file with a `main()`{.code-voice} function that calls the `NSApplicationMain(_:_:)`{.code-voice} function. For example, if your app uses a custom subclass of `NSApplication`{.code-voice} as its principal class, call the `NSApplicationMain`{.code-voice} function instead of using this attribute.

`NSCopying`{.code-voice}

:   Apply this attribute to a stored variable property of a class. This attribute causes the property’s setter to be synthesized with a *copy* of the property’s value—returned by the `copyWithZone(_:)`{.code-voice} method—instead of the value of the property itself. The type of the property must conform to the `NSCopying`{.code-voice} protocol.

    The `NSCopying`{.code-voice} attribute behaves in a way similar to the Objective-C `copy`{.code-voice} property attribute.



`NSManaged`{.code-voice}

:   Apply this attribute to an instance method or stored variable property of a class that inherits from `NSManagedObject`{.code-voice} to indicate that Core Data dynamically provides its implementation at runtime, based on the associated entity description. For a property marked with the `NSManaged`{.code-voice} attribute, Core Data also provides the storage at runtime.

`testable`{.code-voice}

:   Apply this attribute to `import`{.code-voice} declarations for modules compiled with testing enabled to access any entities marked with the `internal`{.code-voice} access level modifier as if they were declared with the `public`{.code-voice} access level modifier.

`UIApplicationMain`{.code-voice}

:   Apply this attribute to a class to indicate that it is the application delegate. Using this attribute is equivalent to calling the `UIApplicationMain`{.code-voice} function and passing this class’s name as the name of the delegate class.

    If you do not use this attribute, supply a `main.swift`{.code-voice} file with a `main`{.code-voice} function that calls the `UIApplicationMain(_:_:_:)`{.code-voice} function. For example, if your app uses a custom subclass of `UIApplication`{.code-voice} as its principal class, call the `UIApplicationMain(_:_:_:)`{.code-voice} function instead of using this attribute.



`warn_unused_result`{.code-voice}

:   Apply this attribute to a method or function declaration to have the compiler emit a warning when the method or function is called without using its result.

    You can use this attribute to provide a warning message about incorrect usage of a nonmutating method that has a mutating counterpart.

    The `warn_unused_result`{.code-voice} attribute optionally accepts one of the two attribute arguments below.

    -   The `message`{.code-voice} argument is used to provide a textual warning message that’s displayed when the function or method is called, but its result isn’t used. It has the following form:

        

        

        -   ``` {.code-voice}
            message=message
            ```

        

        The *message* consists of a string literal.

    -   The `mutable_variant`{.code-voice} argument is used to provide the name of the mutating version of the method that should be used if the nonmutating method is called on a mutable value and the result isn’t used. It has the following form, where the *method name* consists of a string literal:

        

        

        -   ``` {.code-voice}
            mutable_variant=method name
            ```

        

        For example, the Swift standard library provides both the mutating method `sortInPlace()`{.code-voice} and the nonmutating method `sort()`{.code-voice} to collections whose generator element conforms to the `Comparable`{.code-voice} protocol. If you call the `sort()`{.code-voice} method without using its result, it’s likely that you actually intended to use the mutating variant, `sortInPlace()`{.code-voice} instead.



[‌](){#TP40016643-CH35-ID349}
### Declaration Attributes Used by Interface Builder {#declaration-attributes-used-by-interface-builder .section-name}

Interface Builder attributes are declaration attributes used by Interface Builder to synchronize with Xcode. Swift provides the following Interface Builder attributes: `IBAction`{.code-voice}, `IBDesignable`{.code-voice}, `IBInspectable`{.code-voice}, and `IBOutlet`{.code-voice}. These attributes are conceptually the same as their Objective-C counterparts.

You apply the `IBOutlet`{.code-voice} and `IBInspectable`{.code-voice} attributes to property declarations of a class. You apply the `IBAction`{.code-voice} attribute to method declarations of a class and the `IBDesignable`{.code-voice} attribute to class declarations.







[‌](){#TP40016643-CH35-ID350}
### Type Attributes {#type-attributes .section-name}

You can apply type attributes to types only. However, you can also apply the `noreturn`{.code-voice} attribute to a function or method *declaration*.

`convention`{.code-voice}

:   Apply this attribute to the type of a function to indicate its calling conventions.

    The `convention`{.code-voice} attribute always appears with one of the attribute arguments below.

    -   The `swift`{.code-voice} argument is used to indicate a Swift function reference. This is the standard calling convention for function values in Swift.

    -   The `block`{.code-voice} argument is used to indicate an Objective-C compatible block reference. The function value is represented as a reference to the block object, which is an `id`{.code-voice}-compatible Objective-C object that embeds its invocation function within the object. The invocation function uses the C calling convention.

    -   The `c`{.code-voice} argument is used to indicate a C function reference. The function value carries no context and uses the C calling convention.

    A function with C function calling conventions can be used as a function with Objective-C block calling conventions, and a function with Objective-C block calling conventions can be used as a function with Swift function calling conventions. However, only nongeneric global functions, and local functions or closures that don’t capture any local variables, can be used as a function with C function calling conventions.

`noreturn`{.code-voice}

:   Apply this attribute to the type of a function or method to indicate that the function or method doesn’t return to its caller. You can also mark a function or method declaration with this attribute to indicate that the corresponding type of that function or method, `T`{.code-voice}, is `@noreturn T`{.code-voice}.



Grammar of an attribute



[‌](){#attribute}

attribute


→
`@`{.literal}[attribute-name](Attributes.md#attribute-name)[attribute-argument-clause](Attributes.md#attribute-argument-clause)~opt~

[‌](){#attribute-name}

attribute-name


→
[identifier](LexicalStructure.md#identifier)

[‌](){#attribute-argument-clause}

attribute-argument-clause


→
`(`{.literal}[balanced-tokens](Attributes.md#balanced-tokens)~opt~`)`{.literal}

[‌](){#attributes}

attributes


→
[attribute](Attributes.md#attribute)[attributes](Attributes.md#attributes)~opt~





[‌](){#balanced-tokens}

balanced-tokens


→
[balanced-token](Attributes.md#balanced-token)[balanced-tokens](Attributes.md#balanced-tokens)~opt~

[‌](){#balanced-token}

balanced-token


→
`(`{.literal}[balanced-tokens](Attributes.md#balanced-tokens)~opt~`)`{.literal}

[‌](){#TP40016643-CH35-NoLink_225}

balanced-token


→
`[`{.literal}[balanced-tokens](Attributes.md#balanced-tokens)~opt~`]`{.literal}

[‌](){#TP40016643-CH35-NoLink_226}

balanced-token


→
`{`{.literal}[balanced-tokens](Attributes.md#balanced-tokens)~opt~`}`{.literal}

[‌](){#TP40016643-CH35-NoLink_227}

balanced-token


→
Any identifier, keyword, literal, or operator

[‌](){#TP40016643-CH35-NoLink_228}

balanced-token


→
Any punctuation except `(`{.literal}, `)`{.literal}, `[`{.literal}, `]`{.literal}, `{`{.literal}, or `}`{.literal}










