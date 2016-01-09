<div class="content-wrapper">

<div id="chapter_container" class="conceptualwithtasks">

[‌](){#TP40016643-CH41}[‌](){#TP40016643-CH41-ID3}
Access Control {#access-control .chapter-name}
--------------

<div class="section section">

*Access control* restricts access to parts of your code from code in
other source files and modules. This feature enables you to hide the
implementation details of your code, and to specify a preferred
interface through which that code can be accessed and used.

You can assign specific access levels to individual types (classes,
structures, and enumerations), as well as to properties, methods,
initializers, and subscripts belonging to those types. Protocols can be
restricted to a certain context, as can global constants, variables, and
functions.

In addition to offering various levels of access control, Swift reduces
the need to specify explicit access control levels by providing default
access levels for typical scenarios. Indeed, if you are writing a
single-target app, you may not need to specify explicit access control
levels at all.

<div class="note">

Note

The various aspects of your code that can have access control applied to
them (properties, types, functions, and so on) are referred to as
“entities” in the sections below, for brevity.

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH41-ID4}
### Modules and Source Files {#modules-and-source-files .section-name}

Swift’s access control model is based on the concept of modules and
source files.

A *module* is a single unit of code distribution—a framework or
application that is built and shipped as a single unit and that can be
imported by another module with Swift’s `import`{.code-voice} keyword.

Each build target (such as an app bundle or framework) in Xcode is
treated as a separate module in Swift. If you group together aspects of
your app’s code as a stand-alone framework—perhaps to encapsulate and
reuse that code across multiple applications—then everything you define
within that framework will be part of a separate module when it is
imported and used within an app, or when it is used within another
framework.

A *source file* is a single Swift source code file within a module (in
effect, a single file within an app or framework). Although it is common
to define individual types in separate source files, a single source
file can contain definitions for multiple types, functions, and so on.

</div>

<div class="section section">

[‌](){#TP40016643-CH41-ID5}
### Access Levels {#access-levels .section-name}

Swift provides three different *access levels* for entities within your
code. These access levels are relative to the source file in which an
entity is defined, and also relative to the module that source file
belongs to.

-   *Public access* enables entities to be used within any source file
    from their defining module, and also in a source file from another
    module that imports the defining module. You typically use public
    access when specifying the public interface to a framework.

-   *Internal access* enables entities to be used within any source file
    from their defining module, but not in any source file outside of
    that module. You typically use internal access when defining an
    app’s or a framework’s internal structure.

-   *Private access* restricts the use of an entity to its own defining
    source file. Use private access to hide the implementation details
    of a specific piece of functionality.

Public access is the highest (least restrictive) access level and
private access is the lowest (or most restrictive) access level.

<div class="note">

Note

Private access in Swift differs from private access in most other
languages, as it’s scoped to the enclosing source file rather than to
the enclosing declaration. This means that a type can access any private
entities that are defined in the same source file as itself, but an
extension cannot access that type’s private members if it’s defined in a
separate source file.

</div>

<div class="section section">

[‌](){#TP40016643-CH41-ID6}
### Guiding Principle of Access Levels {#guiding-principle-of-access-levels .section-name}

Access levels in Swift follow an overall guiding principle: *No entity
can be defined in terms of another entity that has a lower (more
restrictive) access level.*

For example:

-   A public variable cannot be defined as having an internal or private
    type, because the type might not be available everywhere that the
    public variable is used.

-   A function cannot have a higher access level than its parameter
    types and return type, because the function could be used in
    situations where its constituent types are not available to the
    surrounding code.

The specific implications of this guiding principle for different
aspects of the language are covered in detail below.

</div>

<div class="section section">

[‌](){#TP40016643-CH41-ID7}
### Default Access Levels {#default-access-levels .section-name}

All entities in your code (with a few specific exceptions, as described
later in this chapter) have a default access level of internal if you do
not specify an explicit access level yourself. As a result, in many
cases you do not need to specify an explicit access level in your code.

</div>

<div class="section section">

[‌](){#TP40016643-CH41-ID8}
### Access Levels for Single-Target Apps {#access-levels-for-single-target-apps .section-name}

When you write a simple single-target app, the code in your app is
typically self-contained within the app and does not need to be made
available outside of the app’s module. The default access level of
internal already matches this requirement. Therefore, you do not need to
specify a custom access level. You may, however, want to mark some parts
of your code as private in order to hide their implementation details
from other code within the app’s module.

</div>

<div class="section section">

[‌](){#TP40016643-CH41-ID9}
### Access Levels for Frameworks {#access-levels-for-frameworks .section-name}

When you develop a framework, mark the public-facing interface to that
framework as public so that it can be viewed and accessed by other
modules, such as an app that imports the framework. This public-facing
interface is the application programming interface (or API) for the
framework.

<div class="note">

Note

Any internal implementation details of your framework can still use the
default access level of internal, or can be marked as private if you
want to hide them from other parts of the framework’s internal code. You
need to mark an entity as public only if you want it to become part of
your framework’s API.

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH41-ID519}
### Access Levels for Unit Test Targets {#access-levels-for-unit-test-targets .section-name}

When you write an app with a unit test target, the code in your app
needs to be made available to that module in order to be tested. By
default, only entities marked as public are accessible to other modules.
However, a unit test target can access any internal entity, if you mark
the import declaration for a product module with the
`@testable`{.code-voice} attribute and compile that product module with
testing enabled.

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH41-ID10}
### Access Control Syntax {#access-control-syntax .section-name}

Define the access level for an entity by placing one of the
`public`{.code-voice}, `internal`{.code-voice}, or
`private`{.code-voice} modifiers before the entity’s introducer:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `public`{.code-voice} `class`{.kt} `SomePublicClass`{.vc} {}
2.  `internal`{.code-voice} `class`{.kt} `SomeInternalClass`{.vc} {}
3.  `private`{.code-voice} `class`{.kt} `SomePrivateClass`{.vc} {}
4.  ` `{.code-voice}
5.  `public`{.code-voice} `var`{.kt} `somePublicVariable`{.vc} = `0`{.m}
6.  `internal`{.code-voice} `let`{.kt} `someInternalConstant`{.vc} =
    `0`{.m}
7.  `private`{.code-voice} `func`{.kt} `somePrivateFunction`{.vc}() {}

</div>

</div>

</div>

Unless otherwise specified, the default access level is internal, as
described in [Default Access
Levels](AccessControl.md#TP40016643-CH41-ID7). This means that
`SomeInternalClass`{.code-voice} and `someInternalConstant`{.code-voice}
can be written without an explicit access level modifier, and will still
have an access level of internal:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `class`{.code-voice} `SomeInternalClass`{.vc} {}
    `// implicitly internal`{.c}
2.  `let`{.code-voice} `someInternalConstant`{.vc} = `0`{.m}
    `// implicitly internal`{.c}

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH41-ID11}
### Custom Types {#custom-types .section-name}

If you want to specify an explicit access level for a custom type, do so
at the point that you define the type. The new type can then be used
wherever its access level permits. For example, if you define a private
class, that class can only be used as the type of a property, or as a
function parameter or return type, in the source file in which the
private class is defined.

The access control level of a type also affects the default access level
of that type’s *members* (its properties, methods, initializers, and
subscripts). If you define a type’s access level as private, the default
access level of its members will also be private. If you define a type’s
access level as internal or public (or use the default access level of
internal without specifying an access level explicitly), the default
access level of the type’s members will be internal.

<div class="note">

Note

As mentioned above, a public type defaults to having internal members,
not public members. If you want a type member to be public, you must
explicitly mark it as such. This requirement ensures that the
public-facing API for a type is something you opt in to publishing, and
avoids presenting the internal workings of a type as public API by
mistake.

</div>

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `public`{.code-voice} `class`{.kt} `SomePublicClass`{.vc} {
    `// explicitly public class`{.c}
2.  `    public`{.code-voice} `var`{.kt} `somePublicProperty`{.vc} =
    `0`{.m} `// explicitly public class member`{.c}
3.  `    var`{.code-voice} `someInternalProperty`{.vc} = `0`{.m}
    `// implicitly internal class member`{.c}
4.  `    private`{.code-voice} `func`{.kt} `somePrivateMethod`{.vc}() {}
    `// explicitly private class member`{.c}
5.  `}`{.code-voice}
6.  ` `{.code-voice}
7.  `class`{.code-voice} `SomeInternalClass`{.vc} {
    `// implicitly internal class`{.c}
8.  `    var`{.code-voice} `someInternalProperty`{.vc} = `0`{.m}
    `// implicitly internal class member`{.c}
9.  `    private`{.code-voice} `func`{.kt} `somePrivateMethod`{.vc}() {}
    `// explicitly private class member`{.c}
10. `}`{.code-voice}
11. ` `{.code-voice}
12. `private`{.code-voice} `class`{.kt} `SomePrivateClass`{.vc} {
    `// explicitly private class`{.c}
13. `    var`{.code-voice} `somePrivateProperty`{.vc} = `0`{.m}
    `// implicitly private class member`{.c}
14. `    func`{.code-voice} `somePrivateMethod`{.vc}() {}
    `// implicitly private class member`{.c}
15. `}`{.code-voice}

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH41-ID12}
### Tuple Types {#tuple-types .section-name}

The access level for a tuple type is the most restrictive access level
of all types used in that tuple. For example, if you compose a tuple
from two different types, one with internal access and one with private
access, the access level for that compound tuple type will be private.

<div class="note">

Note

Tuple types do not have a standalone definition in the way that classes,
structures, enumerations, and functions do. A tuple type’s access level
is deduced automatically when the tuple type is used, and cannot be
specified explicitly.

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH41-ID13}
### Function Types {#function-types .section-name}

The access level for a function type is calculated as the most
restrictive access level of the function’s parameter types and return
type. You must specify the access level explicitly as part of the
function’s definition if the function’s calculated access level does not
match the contextual default.

The example below defines a global function called
`someFunction`{.code-voice}, without providing a specific access level
modifier for the function itself. You might expect this function to have
the default access level of “internal”, but this is not the case. In
fact, `someFunction`{.code-voice} will not compile as written below:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `func`{.code-voice} `someFunction`{.vc}() -&gt;
    (`SomeInternalClass`{.n}, `SomePrivateClass`{.n}) {
2.  `    // function implementation goes here`{.code-voice}
3.  `}`{.code-voice}

</div>

</div>

</div>

The function’s return type is a tuple type composed from two of the
custom classes defined above in [Custom
Types](AccessControl.md#TP40016643-CH41-ID11). One of these classes
was defined as “internal”, and the other was defined as “private”.
Therefore, the overall access level of the compound tuple type is
“private” (the minimum access level of the tuple’s constituent types).

Because the function’s return type is private, you must mark the
function’s overall access level with the `private`{.code-voice} modifier
for the function declaration to be valid:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `private`{.code-voice} `func`{.kt} `someFunction`{.vc}() -&gt;
    (`SomeInternalClass`{.n}, `SomePrivateClass`{.n}) {
2.  `    // function implementation goes here`{.code-voice}
3.  `}`{.code-voice}

</div>

</div>

</div>

It is not valid to mark the definition of `someFunction`{.code-voice}
with the `public`{.code-voice} or `internal`{.code-voice} modifiers, or
to use the default setting of internal, because public or internal users
of the function might not have appropriate access to the private class
used in the function’s return type.

</div>

<div class="section section">

[‌](){#TP40016643-CH41-ID14}
### Enumeration Types {#enumeration-types .section-name}

The individual cases of an enumeration automatically receive the same
access level as the enumeration they belong to. You cannot specify a
different access level for individual enumeration cases.

In the example below, the `CompassPoint`{.code-voice} enumeration has an
explicit access level of “public”. The enumeration cases
`North`{.code-voice}, `South`{.code-voice}, `East`{.code-voice}, and
`West`{.code-voice} therefore also have an access level of “public”:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `public`{.code-voice} `enum`{.kt} `CompassPoint`{.vc} {
2.  `    case`{.code-voice} `North`{.vc}
3.  `    case`{.code-voice} `South`{.vc}
4.  `    case`{.code-voice} `East`{.vc}
5.  `    case`{.code-voice} `West`{.vc}
6.  `}`{.code-voice}

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH41-ID468}
### Raw Values and Associated Values {#raw-values-and-associated-values .section-name}

The types used for any raw values or associated values in an enumeration
definition must have an access level at least as high as the
enumeration’s access level. You cannot use a `private`{.code-voice} type
as the raw-value type of an enumeration with an `internal`{.code-voice}
access level, for example.

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH41-ID15}
### Nested Types {#nested-types .section-name}

Nested types defined within a private type have an automatic access
level of private. Nested types defined within a public type or an
internal type have an automatic access level of internal. If you want a
nested type within a public type to be publicly available, you must
explicitly declare the nested type as public.

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH41-ID16}
### Subclassing {#subclassing .section-name}

You can subclass any class that can be accessed in the current access
context. A subclass cannot have a higher access level than its
superclass—for example, you cannot write a public subclass of an
internal superclass.

In addition, you can override any class member (method, property,
initializer, or subscript) that is visible in a certain access context.

An override can make an inherited class member more accessible than its
superclass version. In the example below, class `A`{.code-voice} is a
public class with a private method called `someMethod()`{.code-voice}.
Class `B`{.code-voice} is a subclass of `A`{.code-voice}, with a reduced
access level of “internal”. Nonetheless, class `B`{.code-voice} provides
an override of `someMethod()`{.code-voice} with an access level of
“internal”, which is *higher* than the original implementation of
`someMethod()`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `public`{.code-voice} `class`{.kt} `A`{.vc} {
2.  `    private`{.code-voice} `func`{.kt} `someMethod`{.vc}() {}
3.  `}`{.code-voice}
4.  ` `{.code-voice}
5.  `internal`{.code-voice} `class`{.kt} `B`{.vc}: `A`{.n} {
6.  `    override`{.code-voice} `internal`{.kt} `func`{.kt}
    `someMethod`{.vc}() {}
7.  `}`{.code-voice}

</div>

</div>

</div>

It is even valid for a subclass member to call a superclass member that
has lower access permissions than the subclass member, as long as the
call to the superclass’s member takes place within an allowed access
level context (that is, within the same source file as the superclass
for a private member call, or within the same module as the superclass
for an internal member call):

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `public`{.code-voice} `class`{.kt} `A`{.vc} {
2.  `    private`{.code-voice} `func`{.kt} `someMethod`{.vc}() {}
3.  `}`{.code-voice}
4.  ` `{.code-voice}
5.  `internal`{.code-voice} `class`{.kt} `B`{.vc}: `A`{.n} {
6.  `    override`{.code-voice} `internal`{.kt} `func`{.kt}
    `someMethod`{.vc}() {
7.  `        super`{.code-voice}.`someMethod`{.vc}()
8.  `    }`{.code-voice}
9.  `}`{.code-voice}

</div>

</div>

</div>

Because superclass `A`{.code-voice} and subclass `B`{.code-voice} are
defined in the same source file, it is valid for the `B`{.code-voice}
implementation of `someMethod()`{.code-voice} to call
`super.someMethod()`{.code-voice}.

</div>

<div class="section section">

[‌](){#TP40016643-CH41-ID17}
### Constants, Variables, Properties, and Subscripts {#constants-variables-properties-and-subscripts .section-name}

A constant, variable, or property cannot be more public than its type.
It is not valid to write a public property with a private type, for
example. Similarly, a subscript cannot be more public than either its
index type or return type.

If a constant, variable, property, or subscript makes use of a private
type, the constant, variable, property, or subscript must also be marked
as `private`{.code-voice}:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `private`{.code-voice} `var`{.kt} `privateInstance`{.vc} =
    `SomePrivateClass`{.vc}()

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH41-ID18}
### Getters and Setters {#getters-and-setters .section-name}

Getters and setters for constants, variables, properties, and subscripts
automatically receive the same access level as the constant, variable,
property, or subscript they belong to.

You can give a setter a *lower* access level than its corresponding
getter, to restrict the read-write scope of that variable, property, or
subscript. You assign a lower access level by writing
`private(set)`{.code-voice} or `internal(set)`{.code-voice} before the
`var`{.code-voice} or `subscript`{.code-voice} introducer.

<div class="note">

Note

This rule applies to stored properties as well as computed properties.
Even though you do not write an explicit getter and setter for a stored
property, Swift still synthesizes an implicit getter and setter for you
to provide access to the stored property’s backing storage. Use
`private(set)`{.code-voice} and `internal(set)`{.code-voice} to change
the access level of this synthesized setter in exactly the same way as
for an explicit setter in a computed property.

</div>

The example below defines a structure called
`TrackedString`{.code-voice}, which keeps track of the number of times a
string property is modified:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `struct`{.code-voice} `TrackedString`{.vc} {
2.  `    private(set)`{.code-voice} `var`{.kt} `numberOfEdits`{.vc} =
    `0`{.m}
3.  `    var`{.code-voice} `value`{.vc}: `String`{.n} = `""`{.s} {
4.  `        didSet`{.code-voice} {
5.  `            numberOfEdits`{.code-voice}++
6.  `        }`{.code-voice}
7.  `    }`{.code-voice}
8.  `}`{.code-voice}

</div>

</div>

</div>

The `TrackedString`{.code-voice} structure defines a stored string
property called `value`{.code-voice}, with an initial value of
`""`{.code-voice} (an empty string). The structure also defines a stored
integer property called `numberOfEdits`{.code-voice}, which is used to
track the number of times that `value`{.code-voice} is modified. This
modification tracking is implemented with a `didSet`{.code-voice}
property observer on the `value`{.code-voice} property, which increments
`numberOfEdits`{.code-voice} every time the `value`{.code-voice}
property is set to a new value.

The `TrackedString`{.code-voice} structure and the `value`{.code-voice}
property do not provide an explicit access level modifier, and so they
both receive the default access level of internal. However, the access
level for the `numberOfEdits`{.code-voice} property is marked with a
`private(set)`{.code-voice} modifier to indicate that the property
should be settable only from within the same source file as the
`TrackedString`{.code-voice} structure’s definition. The property’s
getter still has the default access level of internal, but its setter is
now private to the source file in which `TrackedString`{.code-voice} is
defined. This enables `TrackedString`{.code-voice} to modify the
`numberOfEdits`{.code-voice} property internally, but to present the
property as a read-only property when it is used by other source files
within the same module.

If you create a `TrackedString`{.code-voice} instance and modify its
string value a few times, you can see the `numberOfEdits`{.code-voice}
property value update to match the number of modifications:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `var`{.code-voice} `stringToEdit`{.vc} = `TrackedString`{.vc}()
2.  `stringToEdit`{.code-voice}.`value`{.vc} =
    `"This string will be tracked."`{.s}
3.  `stringToEdit`{.code-voice}.`value`{.vc} +=
    `" This edit will increment numberOfEdits."`{.s}
4.  `stringToEdit`{.code-voice}.`value`{.vc} +=
    `" So will this one."`{.s}
5.  `print`{.code-voice}(`"The number of edits is `{.s}\\(`stringToEdit`{.vc}.`numberOfEdits`{.vc})`"`{.s})
6.  `// prints "The number of edits is 3"`{.code-voice}

</div>

</div>

</div>

Although you can query the current value of the
`numberOfEdits`{.code-voice} property from within another source file,
you cannot *modify* the property from another source file. This
restriction protects the implementation details of the
`TrackedString`{.code-voice} edit-tracking functionality, while still
providing convenient access to an aspect of that functionality.

Note that you can assign an explicit access level for both a getter and
a setter if required. The example below shows a version of the
`TrackedString`{.code-voice} structure in which the structure is defined
with an explicit access level of public. The structure’s members
(including the `numberOfEdits`{.code-voice} property) therefore have an
internal access level by default. You can make the structure’s
`numberOfEdits`{.code-voice} property getter public, and its property
setter private, by combining the `public`{.code-voice} and
`private(set)`{.code-voice} access level modifiers:

<div class="section code-listing">

<div class="code-sample">

<div class="Swift">

1.  `public`{.code-voice} `struct`{.kt} `TrackedString`{.vc} {
2.  `    public`{.code-voice} `private(set)`{.kt} `var`{.kt}
    `numberOfEdits`{.vc} = `0`{.m}
3.  `    public`{.code-voice} `var`{.kt} `value`{.vc}: `String`{.n} =
    `""`{.s} {
4.  `        didSet`{.code-voice} {
5.  `            numberOfEdits`{.code-voice}++
6.  `        }`{.code-voice}
7.  `    }`{.code-voice}
8.  `    public`{.code-voice} `init`{.kt}() {}
9.  `}`{.code-voice}

</div>

</div>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH41-ID19}
### Initializers {#initializers .section-name}

Custom initializers can be assigned an access level less than or equal
to the type that they initialize. The only exception is for required
initializers (as defined in [Required
Initializers](Initialization.md#TP40016643-CH18-ID231)). A required
initializer must have the same access level as the class it belongs to.

As with function and method parameters, the types of an initializer’s
parameters cannot be more private than the initializer’s own access
level.

<div class="section section">

[‌](){#TP40016643-CH41-ID20}
### Default Initializers {#default-initializers .section-name}

As described in [Default
Initializers](Initialization.md#TP40016643-CH18-ID213), Swift
automatically provides a *default initializer* without any arguments for
any structure or base class that provides default values for all of its
properties and does not provide at least one initializer itself.

A default initializer has the same access level as the type it
initializes, unless that type is defined as `public`{.code-voice}. For a
type that is defined as `public`{.code-voice}, the default initializer
is considered internal. If you want a public type to be initializable
with a no-argument initializer when used in another module, you must
explicitly provide a public no-argument initializer yourself as part of
the type’s definition.

</div>

<div class="section section">

[‌](){#TP40016643-CH41-ID21}
### Default Memberwise Initializers for Structure Types {#default-memberwise-initializers-for-structure-types .section-name}

The default memberwise initializer for a structure type is considered
private if any of the structure’s stored properties are private.
Otherwise, the initializer has an access level of internal.

As with the default initializer above, if you want a public structure
type to be initializable with a memberwise initializer when used in
another module, you must provide a public memberwise initializer
yourself as part of the type’s definition.

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH41-ID22}
### Protocols {#protocols .section-name}

If you want to assign an explicit access level to a protocol type, do so
at the point that you define the protocol. This enables you to create
protocols that can only be adopted within a certain access context.

The access level of each requirement within a protocol definition is
automatically set to the same access level as the protocol. You cannot
set a protocol requirement to a different access level than the protocol
it supports. This ensures that all of the protocol’s requirements will
be visible on any type that adopts the protocol.

<div class="note">

Note

If you define a public protocol, the protocol’s requirements require a
public access level for those requirements when they are implemented.
This behavior is different from other types, where a public type
definition implies an access level of internal for the type’s members.

</div>

<div class="section section">

[‌](){#TP40016643-CH41-ID23}
### Protocol Inheritance {#protocol-inheritance .section-name}

If you define a new protocol that inherits from an existing protocol,
the new protocol can have at most the same access level as the protocol
it inherits from. You cannot write a public protocol that inherits from
an internal protocol, for example.

</div>

<div class="section section">

[‌](){#TP40016643-CH41-ID24}
### Protocol Conformance {#protocol-conformance .section-name}

A type can conform to a protocol with a lower access level than the type
itself. For example, you can define a public type that can be used in
other modules, but whose conformance to an internal protocol can only be
used within the internal protocol’s defining module.

The context in which a type conforms to a particular protocol is the
minimum of the type’s access level and the protocol’s access level. If a
type is public, but a protocol it conforms to is internal, the type’s
conformance to that protocol is also internal.

When you write or extend a type to conform to a protocol, you must
ensure that the type’s implementation of each protocol requirement has
at least the same access level as the type’s conformance to that
protocol. For example, if a public type conforms to an internal
protocol, the type’s implementation of each protocol requirement must be
at least “internal”.

<div class="note">

Note

In Swift, as in Objective-C, protocol conformance is global—it is not
possible for a type to conform to a protocol in two different ways
within the same program.

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH41-ID25}
### Extensions {#extensions .section-name}

You can extend a class, structure, or enumeration in any access context
in which the class, structure, or enumeration is available. Any type
members added in an extension have the same default access level as type
members declared in the original type being extended. If you extend a
public or internal type, any new type members you add will have a
default access level of internal. If you extend a private type, any new
type members you add will have a default access level of private.

Alternatively, you can mark an extension with an explicit access level
modifier (for example, `private extension`{.code-voice}) to set a new
default access level for all members defined within the extension. This
new default can still be overridden within the extension for individual
type members.

<div class="section section">

[‌](){#TP40016643-CH41-NoLink_31}
### Adding Protocol Conformance with an Extension {#adding-protocol-conformance-with-an-extension .section-name}

You cannot provide an explicit access level modifier for an extension if
you are using that extension to add protocol conformance. Instead, the
protocol’s own access level is used to provide the default access level
for each protocol requirement implementation within the extension.

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH41-ID26}
### Generics {#generics .section-name}

The access level for a generic type or generic function is the minimum
of the access level of the generic type or function itself and the
access level of any type constraints on its type parameters.

</div>

<div class="section section">

[‌](){#TP40016643-CH41-ID27}
### Type Aliases {#type-aliases .section-name}

Any type aliases you define are treated as distinct types for the
purposes of access control. A type alias can have an access level less
than or equal to the access level of the type it aliases. For example, a
private type alias can alias a private, internal, or public type, but a
public type alias cannot alias an internal or private type.

<div class="note">

Note

This rule also applies to type aliases for associated types used to
satisfy protocol conformances.

</div>

</div>

</div>

</div>
