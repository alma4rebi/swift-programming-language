



[‌]()[‌]()
Document Revision History 
-------------------------



This table describes the changes to *The Swift Programming Language*.



+--------------------------------------+--------------------------------------+
| Date                                 | Notes                                |
+======================================+======================================+
| 2015-12-03                           | -   Updated for Swift 2.2.           |
|                                      |                                      |
|                                      | -   Removed discussion of            |
|                                      |     `var` patterns,     |
|                                      |     variable function arguments, and |
|                                      |     the special syntax for           |
|                                      |     curried functions.               |
+--------------------------------------+--------------------------------------+
| 2015-10-20                           | -   Updated for Swift 2.1.           |
|                                      |                                      |
|                                      | -   Updated the [String              |
|                                      |     Interpolation](StringsAndCharact |
|                                      | ers.md#TP40016643-CH7-ID292)      |
|                                      |     and [String                      |
|                                      |     Literals](LexicalStructure.md |
|                                      | #TP40016643-CH30-ID417)              |
|                                      |     sections now that string         |
|                                      |     interpolations can contain       |
|                                      |     string literals.                 |
|                                      |                                      |
|                                      | -   Added the [Nonescaping           |
|                                      |     Closures](Closures.md#TP40016 |
|                                      | 643-CH11-ID546)                      |
|                                      |     section with information about   |
|                                      |     the                              |
|                                      |     `@noescape` attribu |
|                                      | te.                                  |
|                                      |                                      |
|                                      | -   Updated the [Declaration         |
|                                      |     Attributes](Attributes.md#TP4 |
|                                      | 0016643-CH35-ID348)                  |
|                                      |     and [Build Configuration         |
|                                      |     Statement](Statements.md#TP40 |
|                                      | 016643-CH33-ID539)                   |
|                                      |     sections with information        |
|                                      |     about tvOS.                      |
|                                      |                                      |
|                                      | -   Added information about the      |
|                                      |     behavior of in-out parameters to |
|                                      |     the [In-Out                      |
|                                      |     Parameters](Declarations.md#T |
|                                      | P40016643-CH34-ID545) section.       |
|                                      |                                      |
|                                      | -   Added information to the         |
|                                      |     [Capture                         |
|                                      |     Lists](Expressions.md#TP40016 |
|                                      | 643-CH32-ID544)                      |
|                                      |     section about how values         |
|                                      |     specified in closure capture     |
|                                      |     lists are captured.              |
|                                      |                                      |
|                                      | -   Updated the [Accessing           |
|                                      |     Properties Through Optional      |
|                                      |     Chaining](OptionalChaining.md |
|                                      | #TP40016643-CH21-ID248)              |
|                                      |     section to clarify how           |
|                                      |     assignment through optional      |
|                                      |     chaining behaves.                |
|                                      |                                      |
|                                      | -   Improved the discussion of       |
|                                      |     autoclosures in the              |
|                                      |     [Autoclosures](Closures.md#TP |
|                                      | 40016643-CH11-ID543) section.        |
|                                      |                                      |
|                                      | -   Added an example that uses the   |
|                                      |     `??` operator to    |
|                                      |     the [A Swift                     |
|                                      |     Tour](GuidedTour.md) chapter. |
+--------------------------------------+--------------------------------------+
| 2015-09-16                           | -   Updated for Swift 2.0.           |
|                                      |                                      |
|                                      | -   Added information about error    |
|                                      |     handling to the [Error           |
|                                      |     Handling](ErrorHandling.md)   |
|                                      |     chapter, the [Do                 |
|                                      |     Statement](Statements.md#TP40 |
|                                      | 016643-CH33-ID533)                   |
|                                      |     section, the [Throw              |
|                                      |     Statement](Statements.md#TP40 |
|                                      | 016643-CH33-ID518)                   |
|                                      |     section, the [Defer              |
|                                      |     Statement](Statements.md#TP40 |
|                                      | 016643-CH33-ID532)                   |
|                                      |     section, and the [Try            |
|                                      |     Operator](Expressions.md#TP40 |
|                                      | 016643-CH32-ID516) section.          |
|                                      |                                      |
|                                      | -   Updated the [Representing and    |
|                                      |     Throwing                         |
|                                      |     Errors](ErrorHandling.md#TP40 |
|                                      | 016643-CH42-ID509)                   |
|                                      |     section, now that all types can  |
|                                      |     conform to the                   |
|                                      |     `ErrorType` protoco |
|                                      | l.                                   |
|                                      |                                      |
|                                      | -   Added information about the new  |
|                                      |     `try?` keyword to   |
|                                      |     the [Converting Errors to        |
|                                      |     Optional                         |
|                                      |     Values](ErrorHandling.md#TP40 |
|                                      | 016643-CH42-ID542) section.          |
|                                      |                                      |
|                                      | -   Added information about          |
|                                      |     recursive enumerations to the    |
|                                      |     [Recursive                       |
|                                      |     Enumerations](Enumerations.md |
|                                      | #TP40016643-CH12-ID536)              |
|                                      |     section of the                   |
|                                      |     [Enumerations](Enumerations.xhtm |
|                                      | l)                                   |
|                                      |     chapter and the [Enumerations    |
|                                      |     with Cases of Any                |
|                                      |     Type](Declarations.md#TP40016 |
|                                      | 643-CH34-ID365)                      |
|                                      |     section of the                   |
|                                      |     [Declarations](Declarations.xhtm |
|                                      | l) chapter.                          |
|                                      |                                      |
|                                      | -   Added information about API      |
|                                      |     availability checking to the     |
|                                      |     [Checking API                    |
|                                      |     Availability](ControlFlow.md# |
|                                      | TP40016643-CH9-ID523)                |
|                                      |     section of the [Control          |
|                                      |     Flow](ControlFlow.md) chapter |
|                                      |     and the [Availability            |
|                                      |     Condition](Statements.md#TP40 |
|                                      | 016643-CH33-ID522)                   |
|                                      |     section of the                   |
|                                      |     [Statements](Statements.md) c |
|                                      | hapter.                              |
|                                      |                                      |
|                                      | -   Added information about the new  |
|                                      |     `guard` statement   |
|                                      |     to the [Early                    |
|                                      |     Exit](ControlFlow.md#TP400166 |
|                                      | 43-CH9-ID525)                        |
|                                      |     section of the [Control          |
|                                      |     Flow](ControlFlow.md) chapter |
|                                      |     and the [Guard                   |
|                                      |     Statement](Statements.md#TP40 |
|                                      | 016643-CH33-ID524)                   |
|                                      |     section of the                   |
|                                      |     [Statements](Statements.md) c |
|                                      | hapter.                              |
|                                      |                                      |
|                                      | -   Added information about protocol |
|                                      |     extensions to the [Protocol      |
|                                      |     Extensions](Protocols.md#TP40 |
|                                      | 016643-CH25-ID521)                   |
|                                      |     section of the                   |
|                                      |     [Protocols](Protocols.md) cha |
|                                      | pter.                                |
|                                      |                                      |
|                                      | -   Added information about access   |
|                                      |     control for unit testing to the  |
|                                      |     [Access Levels for Unit Test     |
|                                      |     Targets](AccessControl.md#TP4 |
|                                      | 0016643-CH41-ID519)                  |
|                                      |     section of the [Access           |
|                                      |     Control](AccessControl.md) ch |
|                                      | apter.                               |
|                                      |                                      |
|                                      | -   Added information about the new  |
|                                      |     optional pattern to the          |
|                                      |     [Optional                        |
|                                      |     Pattern](Patterns.md#TP400166 |
|                                      | 43-CH36-ID520)                       |
|                                      |     section of the                   |
|                                      |     [Patterns](Patterns.md) chapt |
|                                      | er.                                  |
|                                      |                                      |
|                                      | -   Updated the                      |
|                                      |     [Repeat-While](ControlFlow.md |
|                                      | #TP40016643-CH9-ID126)               |
|                                      |     section with information about   |
|                                      |     the                              |
|                                      |     `repeat`-`while`{.c |
|                                      | ode-voice} loop.                     |
|                                      |                                      |
|                                      | -   Updated the [Strings and         |
|                                      |     Characters](StringsAndCharacters |
|                                      | .md)                              |
|                                      |     chapter, now that                |
|                                      |     `String` no longer  |
|                                      |     conforms to the                  |
|                                      |     `CollectionType`    |
|                                      |     protocol from the Swift          |
|                                      |     standard library.                |
|                                      |                                      |
|                                      | -   Added information about the new  |
|                                      |     Swift standard library           |
|                                      |     `print(_:separator:terminator)`{ |
|                                      | .code-voice}                         |
|                                      |     function to the [Printing        |
|                                      |     Constants and                    |
|                                      |     Variables](TheBasics.md#TP400 |
|                                      | 16643-CH5-ID314) section.            |
|                                      |                                      |
|                                      | -   Added information about the      |
|                                      |     behavior of enumeration cases    |
|                                      |     with `String` raw   |
|                                      |     values to the [Implicitly        |
|                                      |     Assigned Raw                     |
|                                      |     Values](Enumerations.md#TP400 |
|                                      | 16643-CH12-ID535)                    |
|                                      |     section of the                   |
|                                      |     [Enumerations](Enumerations.xhtm |
|                                      | l)                                   |
|                                      |     chapter and the [Enumerations    |
|                                      |     with Cases of a Raw-Value        |
|                                      |     Type](Declarations.md#TP40016 |
|                                      | 643-CH34-ID366)                      |
|                                      |     section of the                   |
|                                      |     [Declarations](Declarations.xhtm |
|                                      | l) chapter.                          |
|                                      |                                      |
|                                      | -   Added information about the      |
|                                      |     `@autoclosure`      |
|                                      |     attribute—including its          |
|                                      |     `@autoclosure(escaping)`{.code-v |
|                                      | oice}                                |
|                                      |     form—to the                      |
|                                      |     [Autoclosures](Closures.md#TP |
|                                      | 40016643-CH11-ID543) section.        |
|                                      |                                      |
|                                      | -   Updated the [Declaration         |
|                                      |     Attributes](Attributes.md#TP4 |
|                                      | 0016643-CH35-ID348)                  |
|                                      |     section with information about   |
|                                      |     the `@available`    |
|                                      |     and                              |
|                                      |     `@warn_unused_result`{.code-voic |
|                                      | e} attributes.                       |
|                                      |                                      |
|                                      | -   Updated the [Type                |
|                                      |     Attributes](Attributes.md#TP4 |
|                                      | 0016643-CH35-ID350)                  |
|                                      |     section with information about   |
|                                      |     the                              |
|                                      |     `@convention` attri |
|                                      | bute.                                |
|                                      |                                      |
|                                      | -   Added an example of using        |
|                                      |     multiple optional bindings with  |
|                                      |     a `where` clause to |
|                                      |     the [Optional                    |
|                                      |     Binding](TheBasics.md#TP40016 |
|                                      | 643-CH5-ID333) section.              |
|                                      |                                      |
|                                      | -   Added information to the [String |
|                                      |     Literals](LexicalStructure.md |
|                                      | #TP40016643-CH30-ID417)              |
|                                      |     section about how concatenating  |
|                                      |     string literals using the        |
|                                      |     `+` operator        |
|                                      |     happens at compile time.         |
|                                      |                                      |
|                                      | -   Added information to the         |
|                                      |     [Metatype                        |
|                                      |     Type](Types.md#TP40016643-CH3 |
|                                      | 1-ID455)                             |
|                                      |     section about comparing metatype |
|                                      |     values and using them to         |
|                                      |     construct instances with         |
|                                      |     initializer expressions.         |
|                                      |                                      |
|                                      | -   Added a note to the [Debugging   |
|                                      |     with                             |
|                                      |     Assertions](TheBasics.md#TP40 |
|                                      | 016643-CH5-ID336)                    |
|                                      |     section about when user-defined  |
|                                      |     assertions are disabled.         |
|                                      |                                      |
|                                      | -   Updated the discussion of the    |
|                                      |     `@NSManaged`        |
|                                      |     attribute in the [Declaration    |
|                                      |     Attributes](Attributes.md#TP4 |
|                                      | 0016643-CH35-ID348)                  |
|                                      |     section, now that the attribute  |
|                                      |     can be applied to certain        |
|                                      |     instance methods.                |
|                                      |                                      |
|                                      | -   Updated the [Variadic            |
|                                      |     Parameters](Functions.md#TP40 |
|                                      | 016643-CH10-ID171)                   |
|                                      |     section, now that variadic       |
|                                      |     parameters can be declared in    |
|                                      |     any position in a function’s     |
|                                      |     parameter list.                  |
|                                      |                                      |
|                                      | -   Added information to the         |
|                                      |     [Overriding a Failable           |
|                                      |     Initializer](Initialization.xhtm |
|                                      | l#TP40016643-CH18-ID229)             |
|                                      |     section about how a nonfailable  |
|                                      |     initializer can delegate up to a |
|                                      |     failable initializer by          |
|                                      |     force-unwrapping the result of   |
|                                      |     the superclass’s initializer.    |
|                                      |                                      |
|                                      | -   Added information about using    |
|                                      |     enumeration cases as functions   |
|                                      |     to the [Enumerations with Cases  |
|                                      |     of Any                           |
|                                      |     Type](Declarations.md#TP40016 |
|                                      | 643-CH34-ID365) section.             |
|                                      |                                      |
|                                      | -   Added information about          |
|                                      |     explicitly referencing an        |
|                                      |     initializer to the [Initializer  |
|                                      |     Expression](Expressions.md#TP |
|                                      | 40016643-CH32-ID399) section.        |
|                                      |                                      |
|                                      | -   Added information about build    |
|                                      |     configuration and line control   |
|                                      |     statements to the [Compiler      |
|                                      |     Control                          |
|                                      |     Statements](Statements.md#TP4 |
|                                      | 0016643-CH33-ID538) section.         |
|                                      |                                      |
|                                      | -   Added a note to the [Metatype    |
|                                      |     Type](Types.md#TP40016643-CH3 |
|                                      | 1-ID455)                             |
|                                      |     section about constructing class |
|                                      |     instances from metatype values.  |
|                                      |                                      |
|                                      | -   Added a note to the [Weak        |
|                                      |     References](AutomaticReferenceCo |
|                                      | unting.md#TP40016643-CH20-ID53)   |
|                                      |     section about weak references    |
|                                      |     being unsuitable for caching.    |
|                                      |                                      |
|                                      | -   Updated a note in the [Type      |
|                                      |     Properties](Properties.md#TP4 |
|                                      | 0016643-CH14-ID264)                  |
|                                      |     section to mention that stored   |
|                                      |     type properties are              |
|                                      |     lazily initialized.              |
|                                      |                                      |
|                                      | -   Updated the [Capturing           |
|                                      |     Values](Closures.md#TP4001664 |
|                                      | 3-CH11-ID103)                        |
|                                      |     section to clarify how variables |
|                                      |     and constants are captured       |
|                                      |     in closures.                     |
|                                      |                                      |
|                                      | -   Updated the [Declaration         |
|                                      |     Attributes](Attributes.md#TP4 |
|                                      | 0016643-CH35-ID348)                  |
|                                      |     section to describe when you can |
|                                      |     apply the `@objc`   |
|                                      |     attribute to classes.            |
|                                      |                                      |
|                                      | -   Added a note to the [Handling    |
|                                      |     Errors](ErrorHandling.md#TP40 |
|                                      | 016643-CH42-ID512)                   |
|                                      |     section about the performance of |
|                                      |     executing a                      |
|                                      |     `throw` statement.  |
|                                      |     Added similar information about  |
|                                      |     the `do` statement  |
|                                      |     in the [Do                       |
|                                      |     Statement](Statements.md#TP40 |
|                                      | 016643-CH33-ID533) section.          |
|                                      |                                      |
|                                      | -   Updated the [Type                |
|                                      |     Properties](Properties.md#TP4 |
|                                      | 0016643-CH14-ID264)                  |
|                                      |     section with information about   |
|                                      |     stored and computed type         |
|                                      |     properties for classes,          |
|                                      |     structures, and enumerations.    |
|                                      |                                      |
|                                      | -   Updated the [Break               |
|                                      |     Statement](Statements.md#TP40 |
|                                      | 016643-CH33-ID441)                   |
|                                      |     section with information about   |
|                                      |     labeled break statements.        |
|                                      |                                      |
|                                      | -   Updated a note in the [Property  |
|                                      |     Observers](Properties.md#TP40 |
|                                      | 016643-CH14-ID262)                   |
|                                      |     section to clarify the behavior  |
|                                      |     of `willSet` and    |
|                                      |     `didSet` observers. |
|                                      |                                      |
|                                      | -   Added a note to the [Access      |
|                                      |     Levels](AccessControl.md#TP40 |
|                                      | 016643-CH41-ID5)                     |
|                                      |     section with information about   |
|                                      |     the scope of                     |
|                                      |     `private` access.   |
|                                      |                                      |
|                                      | -   Added a note to the [Weak        |
|                                      |     References](AutomaticReferenceCo |
|                                      | unting.md#TP40016643-CH20-ID53)   |
|                                      |     section about the differences in |
|                                      |     weak references between garbage  |
|                                      |     collected systems and ARC.       |
|                                      |                                      |
|                                      | -   Updated the [Special Characters  |
|                                      |     in String                        |
|                                      |     Literals](StringsAndCharacters.x |
|                                      | html#TP40016643-CH7-ID295)           |
|                                      |     section with a more precise      |
|                                      |     definition of Unicode scalars.   |
+--------------------------------------+--------------------------------------+
| 2015-04-08                           | -   Updated for Swift 1.2.           |
|                                      |                                      |
|                                      | -   Swift now has a native           |
|                                      |     `Set`               |
|                                      |     collection type. For more        |
|                                      |     information, see                 |
|                                      |     [Sets](CollectionTypes.md#TP4 |
|                                      | 0016643-CH8-ID484).                  |
|                                      |                                      |
|                                      | -   `@autoclosure` is   |
|                                      |     now an attribute of the          |
|                                      |     parameter declaration, not       |
|                                      |     its type. There is also a new    |
|                                      |     `@noescape`         |
|                                      |     parameter declaration attribute. |
|                                      |     For more information, see        |
|                                      |     [Declaration                     |
|                                      |     Attributes](Attributes.md#TP4 |
|                                      | 0016643-CH35-ID348).                 |
|                                      |                                      |
|                                      | -   Type methods and properties now  |
|                                      |     use the `static`    |
|                                      |     keyword as a                     |
|                                      |     declaration modifier. For more   |
|                                      |     information see [Type Variable   |
|                                      |     Properties](Declarations.md#T |
|                                      | P40016643-CH34-ID483).               |
|                                      |                                      |
|                                      | -   Swift now includes the           |
|                                      |     `as?` and           |
|                                      |     `as!` failable      |
|                                      |     downcast operators. For more     |
|                                      |     information, see [Checking for   |
|                                      |     Protocol                         |
|                                      |     Conformance](Protocols.md#TP4 |
|                                      | 0016643-CH25-ID283).                 |
|                                      |                                      |
|                                      | -   Added a new guide section about  |
|                                      |     [String                          |
|                                      |     Indices](StringsAndCharacters.xh |
|                                      | tml#TP40016643-CH7-ID534).           |
|                                      |                                      |
|                                      | -   Removed the overflow division    |
|                                      |     (`&/`) and overflow |
|                                      |     remainder (`&%`)    |
|                                      |     operators from [Overflow         |
|                                      |     Operators](AdvancedOperators.xht |
|                                      | ml#TP40016643-CH27-ID37).            |
|                                      |                                      |
|                                      | -   Updated the rules for constant   |
|                                      |     and constant property            |
|                                      |     declaration and initialization.  |
|                                      |     For more information, see        |
|                                      |     [Constant                        |
|                                      |     Declaration](Declarations.md# |
|                                      | TP40016643-CH34-ID355).              |
|                                      |                                      |
|                                      | -   Updated the definition of        |
|                                      |     Unicode scalars in               |
|                                      |     string literals. See [Special    |
|                                      |     Characters in String             |
|                                      |     Literals](StringsAndCharacters.x |
|                                      | html#TP40016643-CH7-ID295).          |
|                                      |                                      |
|                                      | -   Updated [Range                   |
|                                      |     Operators](BasicOperators.md# |
|                                      | TP40016643-CH6-ID73)                 |
|                                      |     to note that a half-open range   |
|                                      |     with the same start and end      |
|                                      |     index will be empty.             |
|                                      |                                      |
|                                      | -   Updated [Closures Are Reference  |
|                                      |     Types](Closures.md#TP40016643 |
|                                      | -CH11-ID104)                         |
|                                      |     to clarify the capturing rules   |
|                                      |     for variables.                   |
|                                      |                                      |
|                                      | -   Updated [Value                   |
|                                      |     Overflow](AdvancedOperators.xhtm |
|                                      | l#TP40016643-CH27-ID38)              |
|                                      |     to clarify the overflow behavior |
|                                      |     of signed and unsigned integers  |
|                                      |                                      |
|                                      | -   Updated [Protocol                |
|                                      |     Declaration](Declarations.md# |
|                                      | TP40016643-CH34-ID369)               |
|                                      |     to clarify protocol declaration  |
|                                      |     scope and members.               |
|                                      |                                      |
|                                      | -   Updated [Defining a Capture      |
|                                      |     List](AutomaticReferenceCounting |
|                                      | .md#TP40016643-CH20-ID58)         |
|                                      |     to clarify the syntax for weak   |
|                                      |     and unowned references in        |
|                                      |     closure capture lists.           |
|                                      |                                      |
|                                      | -   Updated                          |
|                                      |     [Operators](LexicalStructure.xht |
|                                      | ml#TP40016643-CH30-ID418)            |
|                                      |     to explicitly mention examples   |
|                                      |     of supported characters for      |
|                                      |     custom operators, such as those  |
|                                      |     in the Mathematical Operators,   |
|                                      |     Miscellaneous Symbols, and       |
|                                      |     Dingbats Unicode blocks.         |
|                                      |                                      |
|                                      | -   Constants can now be declared    |
|                                      |     without being initialized in     |
|                                      |     local function scope. They must  |
|                                      |     have a set value before          |
|                                      |     first use. For more information, |
|                                      |     see [Constant                    |
|                                      |     Declaration](Declarations.md# |
|                                      | TP40016643-CH34-ID355).              |
|                                      |                                      |
|                                      | -   In an initializer, constant      |
|                                      |     properties can now only assign a |
|                                      |     value once. For more             |
|                                      |     information, see [Assigning      |
|                                      |     Constant Properties During       |
|                                      |     Initialization](Initialization.x |
|                                      | html#TP40016643-CH18-ID212).         |
|                                      |                                      |
|                                      | -   Multiple optional bindings can   |
|                                      |     now appear in a single           |
|                                      |     `if` statement as a |
|                                      |     comma-separated list of          |
|                                      |     assignment expressions. For more |
|                                      |     information, see [Optional       |
|                                      |     Binding](TheBasics.md#TP40016 |
|                                      | 643-CH5-ID333).                      |
|                                      |                                      |
|                                      | -   An [Optional-Chaining            |
|                                      |     Expression](Expressions.md#TP |
|                                      | 40016643-CH32-ID405)                 |
|                                      |     must appear within a             |
|                                      |     postfix expression.              |
|                                      |                                      |
|                                      | -   Protocol casts are no longer     |
|                                      |     limited to                       |
|                                      |     `@objc` protocols.  |
|                                      |                                      |
|                                      | -   Type casts that can fail at      |
|                                      |     runtime now use the              |
|                                      |     `as?` or            |
|                                      |     `as!` operator, and |
|                                      |     type casts that are guaranteed   |
|                                      |     not to fail use the              |
|                                      |     `as` operator. For  |
|                                      |     more information, see            |
|                                      |     [Type-Casting                    |
|                                      |     Operators](Expressions.md#TP4 |
|                                      | 0016643-CH32-ID388).                 |
+--------------------------------------+--------------------------------------+
| 2014-10-16                           | -   Updated for Swift 1.1.           |
|                                      |                                      |
|                                      | -   Added a full guide to [Failable  |
|                                      |     Initializers](Initialization.xht |
|                                      | ml#TP40016643-CH18-ID224).           |
|                                      |                                      |
|                                      | -   Added a description of [Failable |
|                                      |     Initializer                      |
|                                      |     Requirements](Protocols.md#TP |
|                                      | 40016643-CH25-ID274)                 |
|                                      |     for protocols.                   |
|                                      |                                      |
|                                      | -   Constants and variables of type  |
|                                      |     `Any` can now       |
|                                      |     contain function instances.      |
|                                      |     Updated the example for          |
|                                      |     [Any](TypeCasting.md#TP400166 |
|                                      | 43-CH22-ID344)                       |
|                                      |     to show how to check for and     |
|                                      |     cast to a function type within a |
|                                      |     `switch` statement. |
|                                      |                                      |
|                                      | -   Enumerations with raw values now |
|                                      |     have a `rawValue`   |
|                                      |     property rather than a           |
|                                      |     `toRaw()` method    |
|                                      |     and a failable initializer with  |
|                                      |     a `rawValue`        |
|                                      |     parameter rather than a          |
|                                      |     `fromRaw()` method. |
|                                      |     For more information, see [Raw   |
|                                      |     Values](Enumerations.md#TP400 |
|                                      | 16643-CH12-ID149)                    |
|                                      |     and [Enumerations with Cases of  |
|                                      |     a Raw-Value                      |
|                                      |     Type](Declarations.md#TP40016 |
|                                      | 643-CH34-ID366).                     |
|                                      |                                      |
|                                      | -   Added a new reference section    |
|                                      |     about [Failable                  |
|                                      |     Initializers](Declarations.md |
|                                      | #TP40016643-CH34-ID376),             |
|                                      |     which can trigger                |
|                                      |     initialization failure.          |
|                                      |                                      |
|                                      | -   Custom operators can now contain |
|                                      |     the `?` character.  |
|                                      |     Updated the                      |
|                                      |     [Operators](LexicalStructure.xht |
|                                      | ml#TP40016643-CH30-ID418)            |
|                                      |     reference to describe the        |
|                                      |     revised rules. Removed a         |
|                                      |     duplicate description of the     |
|                                      |     valid set of operator characters |
|                                      |     from [Custom                     |
|                                      |     Operators](AdvancedOperators.xht |
|                                      | ml#TP40016643-CH27-ID46).            |
+--------------------------------------+--------------------------------------+
| 2014-08-18                           | -   New document that describes      |
|                                      |     Swift 1.0, Apple’s new           |
|                                      |     programming language for         |
|                                      |     building iOS and OS X apps.      |
|                                      |                                      |
|                                      | -   Added a new section about        |
|                                      |     [Initializer                     |
|                                      |     Requirements](Protocols.md#TP |
|                                      | 40016643-CH25-ID272)                 |
|                                      |     in protocols.                    |
|                                      |                                      |
|                                      | -   Added a new section about        |
|                                      |     [Class-Only                      |
|                                      |     Protocols](Protocols.md#TP400 |
|                                      | 16643-CH25-ID281).                   |
|                                      |                                      |
|                                      | -   [Assertions](TheBasics.md#TP4 |
|                                      | 0016643-CH5-ID335)                   |
|                                      |     can now use                      |
|                                      |     string interpolation. Removed a  |
|                                      |     note to the contrary.            |
|                                      |                                      |
|                                      | -   Updated the [Concatenating       |
|                                      |     Strings and                      |
|                                      |     Characters](StringsAndCharacters |
|                                      | .md#TP40016643-CH7-ID291)         |
|                                      |     section to reflect the fact that |
|                                      |     `String` and        |
|                                      |     `Character` values  |
|                                      |     can no longer be combined with   |
|                                      |     the addition operator            |
|                                      |     (`+`) or addition   |
|                                      |     assignment operator              |
|                                      |     (`+=`). These       |
|                                      |     operators are now used only with |
|                                      |     `String` values.    |
|                                      |     Use the `String`    |
|                                      |     type’s `append(_:)` |
|                                      |     method to append a single        |
|                                      |     `Character` value   |
|                                      |     onto the end of a string.        |
|                                      |                                      |
|                                      | -   Added information about the      |
|                                      |     `availability`      |
|                                      |     attribute to the [Declaration    |
|                                      |     Attributes](Attributes.md#TP4 |
|                                      | 0016643-CH35-ID348) section.         |
|                                      |                                      |
|                                      | -   [Optionals](TheBasics.md#TP40 |
|                                      | 016643-CH5-ID330)                    |
|                                      |     no longer implicitly evaluate to |
|                                      |     `true` when they    |
|                                      |     have a value and                 |
|                                      |     `false` when they   |
|                                      |     do not, to avoid confusion when  |
|                                      |     working with optional            |
|                                      |     `Bool` values.      |
|                                      |     Instead, make an explicit check  |
|                                      |     against `nil` with  |
|                                      |     the `==` or         |
|                                      |     `!=` operators to   |
|                                      |     find out if an optional contains |
|                                      |     a value.                         |
|                                      |                                      |
|                                      | -   Swift now has a [Nil Coalescing  |
|                                      |     Operator](BasicOperators.md#T |
|                                      | P40016643-CH6-ID72)                  |
|                                      |     (`a ?? b`), which   |
|                                      |     unwraps an optional’s value if   |
|                                      |     it exists, or returns a default  |
|                                      |     value if the optional is         |
|                                      |     `nil`.              |
|                                      |                                      |
|                                      | -   Updated and expanded the         |
|                                      |     [Comparing                       |
|                                      |     Strings](StringsAndCharacters.xh |
|                                      | tml#TP40016643-CH7-ID298)            |
|                                      |     section to reflect and           |
|                                      |     demonstrate that string and      |
|                                      |     character comparison and prefix  |
|                                      |     / suffix comparison are now      |
|                                      |     based on Unicode canonical       |
|                                      |     equivalence of extended          |
|                                      |     grapheme clusters.               |
|                                      |                                      |
|                                      | -   You can now try to set a         |
|                                      |     property’s value, assign to a    |
|                                      |     subscript, or call a mutating    |
|                                      |     method or operator through       |
|                                      |     [Optional                        |
|                                      |     Chaining](OptionalChaining.md |
|                                      | ).                                   |
|                                      |     The information about [Accessing |
|                                      |     Properties Through Optional      |
|                                      |     Chaining](OptionalChaining.md |
|                                      | #TP40016643-CH21-ID248)              |
|                                      |     has been updated accordingly,    |
|                                      |     and the examples of checking for |
|                                      |     method call success in [Calling  |
|                                      |     Methods Through Optional         |
|                                      |     Chaining](OptionalChaining.md |
|                                      | #TP40016643-CH21-ID249)              |
|                                      |     have been expanded to show how   |
|                                      |     to check for property            |
|                                      |     setting success.                 |
|                                      |                                      |
|                                      | -   Added a new section about        |
|                                      |     [Accessing Subscripts of         |
|                                      |     Optional                         |
|                                      |     Type](OptionalChaining.md#TP4 |
|                                      | 0016643-CH21-ID251)                  |
|                                      |     through optional chaining.       |
|                                      |                                      |
|                                      | -   Updated the [Accessing and       |
|                                      |     Modifying an                     |
|                                      |     Array](CollectionTypes.md#TP4 |
|                                      | 0016643-CH8-ID110)                   |
|                                      |     section to note that you can no  |
|                                      |     longer append a single item to   |
|                                      |     an array with the                |
|                                      |     `+=` operator.      |
|                                      |     Instead, use the                 |
|                                      |     `append(_:)`        |
|                                      |     method, or append a single-item  |
|                                      |     array with the                   |
|                                      |     `+=` operator.      |
|                                      |                                      |
|                                      | -   Added a note that the start      |
|                                      |     value `a` for the   |
|                                      |     [Range                           |
|                                      |     Operators](BasicOperators.md# |
|                                      | TP40016643-CH6-ID73)                 |
|                                      |     `a...b` and         |
|                                      |     `a..<b` must not be |
|                                      |     greater than the end value       |
|                                      |     `b`.                |
|                                      |                                      |
|                                      | -   Rewrote the                      |
|                                      |     [Inheritance](Inheritance.md) |
|                                      |     chapter to remove its            |
|                                      |     introductory coverage of         |
|                                      |     initializer overrides. This      |
|                                      |     chapter now focuses more on the  |
|                                      |     addition of new functionality in |
|                                      |     a subclass, and the modification |
|                                      |     of existing functionality        |
|                                      |     with overrides. The chapter’s    |
|                                      |     example of [Overriding Property  |
|                                      |     Getters and                      |
|                                      |     Setters](Inheritance.md#TP400 |
|                                      | 16643-CH17-ID200)                    |
|                                      |     has been rewritten to show how   |
|                                      |     to override a                    |
|                                      |     `description` prope |
|                                      | rty.                                 |
|                                      |     (The examples of modifying an    |
|                                      |     inherited property’s default     |
|                                      |     value in a subclass initializer  |
|                                      |     have been moved to the           |
|                                      |     [Initialization](Initialization. |
|                                      | xhtml) chapter.)                     |
|                                      |                                      |
|                                      | -   Updated the [Initializer         |
|                                      |     Inheritance and                  |
|                                      |     Overriding](Initialization.md |
|                                      | #TP40016643-CH18-ID221)              |
|                                      |     section to note that overrides   |
|                                      |     of a designated initializer must |
|                                      |     now be marked with the           |
|                                      |     `override` modifier |
|                                      | .                                    |
|                                      |                                      |
|                                      | -   Updated the [Required            |
|                                      |     Initializers](Initialization.xht |
|                                      | ml#TP40016643-CH18-ID231)            |
|                                      |     section to note that the         |
|                                      |     `required` modifier |
|                                      |     is now written before every      |
|                                      |     subclass implementation of a     |
|                                      |     required initializer, and that   |
|                                      |     the requirements for required    |
|                                      |     initializers can now be          |
|                                      |     satisfied by automatically       |
|                                      |     inherited initializers.          |
|                                      |                                      |
|                                      | -   Infix [Operator                  |
|                                      |     Functions](AdvancedOperators.xht |
|                                      | ml#TP40016643-CH27-ID42)             |
|                                      |     no longer require the            |
|                                      |     `@infix` attribute. |
|                                      |                                      |
|                                      | -   The `@prefix` and   |
|                                      |     `@postfix`          |
|                                      |     attributes for [Prefix and       |
|                                      |     Postfix                          |
|                                      |     Operators](AdvancedOperators.xht |
|                                      | ml#TP40016643-CH27-ID43)             |
|                                      |     have been replaced by            |
|                                      |     `prefix` and        |
|                                      |     `postfix`           |
|                                      |     declaration modifiers.           |
|                                      |                                      |
|                                      | -   Added a note about the order in  |
|                                      |     which [Prefix and Postfix        |
|                                      |     Operators](AdvancedOperators.xht |
|                                      | ml#TP40016643-CH27-ID43)             |
|                                      |     are applied when both a prefix   |
|                                      |     and a postfix operator are       |
|                                      |     applied to the same operand.     |
|                                      |                                      |
|                                      | -   Operator functions for [Compound |
|                                      |     Assignment                       |
|                                      |     Operators](AdvancedOperators.xht |
|                                      | ml#TP40016643-CH27-ID44)             |
|                                      |     no longer use the                |
|                                      |     `@assignment`       |
|                                      |     attribute when defining          |
|                                      |     the function.                    |
|                                      |                                      |
|                                      | -   The order in which modifiers are |
|                                      |     specified when defining [Custom  |
|                                      |     Operators](AdvancedOperators.xht |
|                                      | ml#TP40016643-CH27-ID46)             |
|                                      |     has changed. You now write       |
|                                      |     `prefix operator`   |
|                                      |     rather than                      |
|                                      |     `operator prefix`,  |
|                                      |     for example.                     |
|                                      |                                      |
|                                      | -   Added information about the      |
|                                      |     `dynamic`           |
|                                      |     declaration modifier in          |
|                                      |     [Declaration                     |
|                                      |     Modifiers](Declarations.md#TP |
|                                      | 40016643-CH34-ID381).                |
|                                      |                                      |
|                                      | -   Added information about how type |
|                                      |     inference works with             |
|                                      |     [Literals](LexicalStructure.xhtm |
|                                      | l#TP40016643-CH30-ID414).            |
|                                      |                                      |
|                                      | -   Added more information about     |
|                                      |     curried functions.               |
|                                      |                                      |
|                                      | -   Added a new chapter about        |
|                                      |     [Access                          |
|                                      |     Control](AccessControl.md).   |
|                                      |                                      |
|                                      | -   Updated the [Strings and         |
|                                      |     Characters](StringsAndCharacters |
|                                      | .md)                              |
|                                      |     chapter to reflect the fact that |
|                                      |     Swift’s `Character` |
|                                      |     type now represents a single     |
|                                      |     Unicode extended                 |
|                                      |     grapheme cluster. Includes a new |
|                                      |     section on [Extended Grapheme    |
|                                      |     Clusters](StringsAndCharacters.x |
|                                      | html#TP40016643-CH7-ID296)           |
|                                      |     and more information about       |
|                                      |     [Unicode                         |
|                                      |     Scalars](StringsAndCharacters.xh |
|                                      | tml#TP40016643-CH7-ID294)            |
|                                      |     and [Comparing                   |
|                                      |     Strings](StringsAndCharacters.xh |
|                                      | tml#TP40016643-CH7-ID298).           |
|                                      |                                      |
|                                      | -   Updated the [String              |
|                                      |     Literals](StringsAndCharacters.x |
|                                      | html#TP40016643-CH7-ID286)           |
|                                      |     section to note that Unicode     |
|                                      |     scalars inside string literals   |
|                                      |     are now written as               |
|                                      |     `\u{n}`, where      |
|                                      |     `n` is a            |
|                                      |     hexadecimal number between 0 and |
|                                      |     10FFFF, the range of             |
|                                      |     Unicode’s codespace.             |
|                                      |                                      |
|                                      | -   The `NSString`      |
|                                      |     `length` property   |
|                                      |     is now mapped onto Swift’s       |
|                                      |     native `String`     |
|                                      |     type as                          |
|                                      |     `utf16Count`, not   |
|                                      |     `utf16count`.       |
|                                      |                                      |
|                                      | -   Swift’s native                   |
|                                      |     `String` type no    |
|                                      |     longer has an                    |
|                                      |     `uppercaseString`   |
|                                      |     or                               |
|                                      |     `lowercaseString` p |
|                                      | roperty.                             |
|                                      |     The corresponding section in     |
|                                      |     [Strings and                     |
|                                      |     Characters](StringsAndCharacters |
|                                      | .md)                              |
|                                      |     has been removed, and various    |
|                                      |     code examples have been updated. |
|                                      |                                      |
|                                      | -   Added a new section about        |
|                                      |     [Initializer Parameters Without  |
|                                      |     External                         |
|                                      |     Names](Initialization.md#TP40 |
|                                      | 016643-CH18-ID210).                  |
|                                      |                                      |
|                                      | -   Added a new section about        |
|                                      |     [Required                        |
|                                      |     Initializers](Initialization.xht |
|                                      | ml#TP40016643-CH18-ID231).           |
|                                      |                                      |
|                                      | -   Added a new section about        |
|                                      |     [Optional Tuple Return           |
|                                      |     Types](Functions.md#TP4001664 |
|                                      | 3-CH10-ID165).                       |
|                                      |                                      |
|                                      | -   Updated the [Type                |
|                                      |     Annotations](TheBasics.md#TP4 |
|                                      | 0016643-CH5-ID312)                   |
|                                      |     section to note that multiple    |
|                                      |     related variables can be defined |
|                                      |     on a single line with one        |
|                                      |     type annotation.                 |
|                                      |                                      |
|                                      | -   The `@optional`,    |
|                                      |     `@lazy`,            |
|                                      |     `@final`, and       |
|                                      |     `@required`         |
|                                      |     attributes are now the           |
|                                      |     `optional`,         |
|                                      |     `lazy`,             |
|                                      |     `final`, and        |
|                                      |     `required`          |
|                                      |     [Declaration                     |
|                                      |     Modifiers](Declarations.md#TP |
|                                      | 40016643-CH34-ID381).                |
|                                      |                                      |
|                                      | -   Updated the entire book to refer |
|                                      |     to `..<` as the     |
|                                      |     [Half-Open Range                 |
|                                      |     Operator](BasicOperators.md#T |
|                                      | P40016643-CH6-ID75)                  |
|                                      |     (rather than the “half-closed    |
|                                      |     range operator”).                |
|                                      |                                      |
|                                      | -   Updated the [Accessing and       |
|                                      |     Modifying a                      |
|                                      |     Dictionary](CollectionTypes.xhtm |
|                                      | l#TP40016643-CH8-ID116)              |
|                                      |     section to note that             |
|                                      |     `Dictionary` now    |
|                                      |     has a Boolean                    |
|                                      |     `isEmpty` property. |
|                                      |                                      |
|                                      | -   Clarified the full list of       |
|                                      |     characters that can be used when |
|                                      |     defining [Custom                 |
|                                      |     Operators](AdvancedOperators.xht |
|                                      | ml#TP40016643-CH27-ID46).            |
|                                      |                                      |
|                                      | -   `nil` and the       |
|                                      |     Booleans `true` and |
|                                      |     `false` are now     |
|                                      |     [Literals](LexicalStructure.xhtm |
|                                      | l#TP40016643-CH30-ID414).            |
|                                      |                                      |
|                                      | -   Swift’s `Array`     |
|                                      |     type now has full                |
|                                      |     value semantics. Updated the     |
|                                      |     information about [Mutability of |
|                                      |     Collections](CollectionTypes.xht |
|                                      | ml#TP40016643-CH8-ID106)             |
|                                      |     and                              |
|                                      |     [Arrays](CollectionTypes.md#T |
|                                      | P40016643-CH8-ID107)                 |
|                                      |     to reflect the new approach.     |
|                                      |     Also clarified the [Assignment   |
|                                      |     and Copy Behavior for Strings,   |
|                                      |     Arrays, and                      |
|                                      |     Dictionaries](ClassesAndStructur |
|                                      | es.md#TP40016643-CH13-ID93).      |
|                                      |                                      |
|                                      | -   [Array Type Shorthand            |
|                                      |     Syntax](CollectionTypes.md#TP |
|                                      | 40016643-CH8-ID108)                  |
|                                      |     is now written as                |
|                                      |     `[SomeType]` rather |
|                                      |     than `SomeType[]`.  |
|                                      |                                      |
|                                      | -   Added a new section about        |
|                                      |     [Dictionary Type Shorthand       |
|                                      |     Syntax](CollectionTypes.md#TP |
|                                      | 40016643-CH8-ID114),                 |
|                                      |     which is written as              |
|                                      |     `[KeyType: ValueType]`{.code-voi |
|                                      | ce}.                                 |
|                                      |                                      |
|                                      | -   Added a new section about [Hash  |
|                                      |     Values for Set                   |
|                                      |     Types](CollectionTypes.md#TP4 |
|                                      | 0016643-CH8-ID493).                  |
|                                      |                                      |
|                                      | -   Examples of [Closure             |
|                                      |     Expressions](Closures.md#TP40 |
|                                      | 016643-CH11-ID95)                    |
|                                      |     now use the global               |
|                                      |     `sorted(_:_:)`      |
|                                      |     function rather than the global  |
|                                      |     `sort(_:_:)`        |
|                                      |     function, to reflect the new     |
|                                      |     array value semantics.           |
|                                      |                                      |
|                                      | -   Updated the information about    |
|                                      |     [Memberwise Initializers for     |
|                                      |     Structure                        |
|                                      |     Types](Initialization.md#TP40 |
|                                      | 016643-CH18-ID214)                   |
|                                      |     to clarify that the memberwise   |
|                                      |     structure initializer is made    |
|                                      |     available even if a structure’s  |
|                                      |     stored properties do not have    |
|                                      |     default values.                  |
|                                      |                                      |
|                                      | -   Updated to `..<`    |
|                                      |     rather than `..`    |
|                                      |     for the [Half-Open Range         |
|                                      |     Operator](BasicOperators.md#T |
|                                      | P40016643-CH6-ID75).                 |
|                                      |                                      |
|                                      | -   Added an example of [Extending a |
|                                      |     Generic                          |
|                                      |     Type](Generics.md#TP40016643- |
|                                      | CH26-ID185).                         |
+--------------------------------------+--------------------------------------+








