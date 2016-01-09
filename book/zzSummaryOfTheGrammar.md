



[‌]()[‌]()
Summary of the Grammar 
----------------------



[‌]()
### Statements 



Grammar of a statement



[‌]()

statement


→
[expression](Expressions.md#expression)`;`~opt~

[‌]()

statement


→
[declaration](Declarations.md#declaration)`;`~opt~

[‌]()

statement


→
[loop-statement](Statements.md#loop-statement)`;`~opt~

[‌]()

statement


→
[branch-statement](Statements.md#branch-statement)`;`~opt~

[‌]()

statement


→
[labeled-statement](Statements.md#labeled-statement)`;`~opt~

[‌]()

statement


→
[control-transfer-statement](Statements.md#control-transfer-statement)`;`~opt~

[‌]()

statement


→
[defer-statement](Statements.md#defer-statement)`;`~opt~

[‌]()

statement


→
[do-statement](Statements.md#do-statement)`:`~opt~

[‌]()

statement


→
[compiler-control-statement](Statements.md#compiler-control-statement)

[‌]()

statements


→
[statement](Statements.md#statement)[statements](Statements.md#statements)~opt~







Grammar of a loop statement



[‌]()

loop-statement


→
[for-statement](Statements.md#for-statement)

[‌]()

loop-statement


→
[for-in-statement](Statements.md#for-in-statement)

[‌]()

loop-statement


→
[while-statement](Statements.md#while-statement)

[‌]()

loop-statement


→
[repeat-while-statement](Statements.md#repeat-while-statement)







Grammar of a for statement



[‌]()

for-statement


→
`for`[for-init](Statements.md#for-init)~opt~`;`[expression](Expressions.md#expression)~opt~`;`[expression-list](Expressions.md#expression-list)~opt~[code-block](Declarations.md#code-block)

[‌]()

for-statement


→
`for``(`[for-init](Statements.md#for-init)~opt~`;`[expression](Expressions.md#expression)~opt~`;`[expression-list](Expressions.md#expression-list)~opt~`)`[code-block](Declarations.md#code-block)





[‌]()

for-init


→

[variable-declaration](Declarations.md#variable-declaration)

[expression-list](Expressions.md#expression-list)








Grammar of a for-in statement



[‌]()

for-in-statement


→
`for``case`~opt~[pattern](Patterns.md#pattern)`in`[expression](Expressions.md#expression)[where-clause](Statements.md#where-clause)~opt~[code-block](Declarations.md#code-block)







Grammar of a while statement



[‌]()

while-statement


→
`while`[condition-clause](Statements.md#condition-clause)[code-block](Declarations.md#code-block)





[‌]()

condition-clause


→
[expression](Expressions.md#expression)

[‌]()

condition-clause


→
[expression](Expressions.md#expression)`,`[condition-list](Statements.md#condition-list)

[‌]()

condition-clause


→
[condition-list](Statements.md#condition-list)

[‌]()

condition-clause


→
[availability-condition](Statements.md#availability-condition)`,`[expression](Expressions.md#expression)





[‌]()

condition-list


→

[condition](Statements.md#condition)

[condition](Statements.md#condition)`,`[condition-list](Statements.md#condition-list)


[‌]()

condition


→

[availability-condition](Statements.md#availability-condition)

[case-condition](Statements.md#case-condition)

[optional-binding-condition](Statements.md#optional-binding-condition)


[‌]()

case-condition


→
`case`[pattern](Patterns.md#pattern)[initializer](Declarations.md#initializer)[where-clause](Statements.md#where-clause)~opt~





[‌]()

optional-binding-condition


→
[optional-binding-head](Statements.md#optional-binding-head)[optional-binding-continuation-list](Statements.md#optional-binding-continuation-list)~opt~[where-clause](Statements.md#where-clause)~opt~

[‌]()

optional-binding-head


→
`let`[pattern](Patterns.md#pattern)[initializer](Declarations.md#initializer)

[‌]()

optional-binding-continuation-list


→

[optional-binding-continuation](Statements.md#optional-binding-continuation)

[optional-binding-continuation](Statements.md#optional-binding-continuation)`,`[optional-binding-continuation-list](Statements.md#optional-binding-continuation-list)


[‌]()

optional-binding-continuation


→

[pattern](Patterns.md#pattern)[initializer](Declarations.md#initializer)

[optional-binding-head](Statements.md#optional-binding-head)








Grammar of a repeat-while statement



[‌]()

repeat-while-statement


→
`repeat`[code-block](Declarations.md#code-block)`while`[expression](Expressions.md#expression)







Grammar of a branch statement



[‌]()

branch-statement


→
[if-statement](Statements.md#if-statement)

[‌]()

branch-statement


→
[guard-statement](Statements.md#guard-statement)

[‌]()

branch-statement


→
[switch-statement](Statements.md#switch-statement)







Grammar of an if statement



[‌]()

if-statement


→
`if`[condition-clause](Statements.md#condition-clause)[code-block](Declarations.md#code-block)[else-clause](Statements.md#else-clause)~opt~

[‌]()

else-clause


→

`else`[code-block](Declarations.md#code-block)

`else`[if-statement](Statements.md#if-statement)








Grammar of a guard statement



[‌]()

guard-statement


→
`guard`[condition-clause](Statements.md#condition-clause)`else`[code-block](Declarations.md#code-block)







Grammar of a switch statement



[‌]()

switch-statement


→
`switch`[expression](Expressions.md#expression)`{`[switch-cases](Statements.md#switch-cases)~opt~`}`

[‌]()

switch-cases


→
[switch-case](Statements.md#switch-case)[switch-cases](Statements.md#switch-cases)~opt~

[‌]()

switch-case


→

[case-label](Statements.md#case-label)[statements](Statements.md#statements)

[default-label](Statements.md#default-label)[statements](Statements.md#statements)






[‌]()

case-label


→
`case`[case-item-list](Statements.md#case-item-list)`:`

[‌]()

case-item-list


→

[pattern](Patterns.md#pattern)[where-clause](Statements.md#where-clause)~opt~

[pattern](Patterns.md#pattern)[where-clause](Statements.md#where-clause)~opt~`,`[case-item-list](Statements.md#case-item-list)


[‌]()

default-label


→
`default``:`





[‌]()

where-clause


→
`where`[where-expression](Statements.md#where-expression)

[‌]()

where-expression


→
[expression](Expressions.md#expression)







Grammar of a labeled statement



[‌]()

labeled-statement


→

[statement-label](Statements.md#statement-label)[loop-statement](Statements.md#loop-statement)

[statement-label](Statements.md#statement-label)[if-statement](Statements.md#if-statement)

[statement-label](Statements.md#statement-label)[switch-statement](Statements.md#switch-statement)


[‌]()

statement-label


→
[label-name](Statements.md#label-name)`:`

[‌]()

label-name


→
[identifier](LexicalStructure.md#identifier)







Grammar of a control transfer statement



[‌]()

control-transfer-statement


→
[break-statement](Statements.md#break-statement)

[‌]()

control-transfer-statement


→
[continue-statement](Statements.md#continue-statement)

[‌]()

control-transfer-statement


→
[fallthrough-statement](Statements.md#fallthrough-statement)

[‌]()

control-transfer-statement


→
[return-statement](Statements.md#return-statement)

[‌]()

control-transfer-statement


→
[throw-statement](Statements.md#throw-statement)







Grammar of a break statement



[‌]()

break-statement


→
`break`[label-name](Statements.md#label-name)~opt~







Grammar of a continue statement



[‌]()

continue-statement


→
`continue`[label-name](Statements.md#label-name)~opt~







Grammar of a fallthrough statement



[‌]()

fallthrough-statement


→
`fallthrough`







Grammar of a return statement



[‌]()

return-statement


→
`return`[expression](Expressions.md#expression)~opt~







Grammar of an availability condition



[‌]()

availability-condition


→
`#available``(`[availability-arguments](Statements.md#availability-arguments)`)`

[‌]()

availability-arguments


→

[availability-argument](Statements.md#availability-argument)

[availability-argument](Statements.md#availability-argument)`,`[availability-arguments](Statements.md#availability-arguments)


[‌]()

availability-argument


→
[platform-name](Statements.md#platform-name)[platform-version](Statements.md#platform-version)

[‌]()

availability-argument


→
`*`





[‌]()

platform-name


→

`iOS`

`iOSApplicationExtension`


[‌]()

platform-name


→

`OSX`

`OSXApplicationExtension`


[‌]()

platform-name


→
`watchOS`

[‌]()

platform-version


→
[decimal-digits](LexicalStructure.md#decimal-digits)

[‌]()

platform-version


→
[decimal-digits](LexicalStructure.md#decimal-digits)`.`[decimal-digits](LexicalStructure.md#decimal-digits)

[‌]()

platform-version


→
[decimal-digits](LexicalStructure.md#decimal-digits)`.`[decimal-digits](LexicalStructure.md#decimal-digits)`.`[decimal-digits](LexicalStructure.md#decimal-digits)







Grammar of a throw statement



[‌]()

throw-statement


→
`throw`[expression](Expressions.md#expression)







Grammar of a defer statement



[‌]()

defer-statement


→
`defer`[code-block](Declarations.md#code-block)







Grammar of a do statement



[‌]()

do-statement


→
`do`[code-block](Declarations.md#code-block)[catch-clauses](Statements.md#catch-clauses)~opt~

[‌]()

catch-clauses


→
[catch-clause](Statements.md#catch-clause)[catch-clauses](Statements.md#catch-clauses)~opt~

[‌]()

catch-clause


→
`catch`[pattern](Patterns.md#pattern)~opt~[where-clause](Statements.md#where-clause)~opt~[code-block](Declarations.md#code-block)







Grammar of a compiler control statement



[‌]()

compiler-control-statement


→
[build-configuration-statement](Statements.md#build-configuration-statement)

[‌]()

compiler-control-statement


→
[line-control-statement](Statements.md#line-control-statement)







Grammar of a build configuration statement



[‌]()

build-configuration-statement


→
`#if`[build-configuration](Statements.md#build-configuration)[statements](Statements.md#statements)~opt~[build-configuration-elseif-clauses](Statements.md#build-configuration-elseif-clauses)~opt~[build-configuration-else-clause](Statements.md#build-configuration-else-clause)~opt~`#endif`

[‌]()

build-configuration-elseif-clauses


→
[build-configuration-elseif-clause](Statements.md#build-configuration-elseif-clause)[build-configuration-elseif-clauses](Statements.md#build-configuration-elseif-clauses)~opt~

[‌]()

build-configuration-elseif-clause


→
`#elseif`[build-configuration](Statements.md#build-configuration)[statements](Statements.md#statements)~opt~

[‌]()

build-configuration-else-clause


→
`#else`[statements](Statements.md#statements)~opt~





[‌]()

build-configuration


→
[platform-testing-function](Statements.md#platform-testing-function)

[‌]()

build-configuration


→
[identifier](LexicalStructure.md#identifier)

[‌]()

build-configuration


→
[boolean-literal](LexicalStructure.md#boolean-literal)

[‌]()

build-configuration


→
`(`[build-configuration](Statements.md#build-configuration)`)`

[‌]()

build-configuration


→
`!`[build-configuration](Statements.md#build-configuration)

[‌]()

build-configuration


→
[build-configuration](Statements.md#build-configuration)`&&`[build-configuration](Statements.md#build-configuration)

[‌]()

build-configuration


→
[build-configuration](Statements.md#build-configuration)`||`[build-configuration](Statements.md#build-configuration)





[‌]()

platform-testing-function


→
`os``(`[operating-system](Statements.md#operating-system)`)`

[‌]()

platform-testing-function


→
`arch``(`[architecture](Statements.md#architecture)`)`

[‌]()

operating-system


→

`OSX`

`iOS`

`watchOS`

`tvOS`


[‌]()

architecture


→

`i386`

`x86_64`

`arm`

`arm64`








Grammar of a line control statement



[‌]()

line-control-statement


→
`#line`

[‌]()

line-control-statement


→
`#line`[line-number](Statements.md#line-number)[file-name](Statements.md#file-name)

[‌]()

line-number


→
A decimal integer greater than zero

[‌]()

file-name


→
[static-string-literal](LexicalStructure.md#static-string-literal)









[‌]()
### Generic Parameters and Arguments 



Grammar of a generic parameter clause



[‌]()

generic-parameter-clause


→
`[generic-parameter-list](GenericParametersAndArguments.md#generic-parameter-list)[requirement-clause](GenericParametersAndArguments.md#requirement-clause)~opt~`>`

[‌]()

generic-parameter-list


→

[generic-parameter](GenericParametersAndArguments.md#generic-parameter)

[generic-parameter](GenericParametersAndArguments.md#generic-parameter)`,`[generic-parameter-list](GenericParametersAndArguments.md#generic-parameter-list)


[‌]()

generic-parameter


→
[type-name](Types.md#type-name)

[‌]()

generic-parameter


→
[type-name](Types.md#type-name)`:`[type-identifier](Types.md#type-identifier)

[‌]()

generic-parameter


→
[type-name](Types.md#type-name)`:`[protocol-composition-type](Types.md#protocol-composition-type)





[‌]()

requirement-clause


→
`where`[requirement-list](GenericParametersAndArguments.md#requirement-list)

[‌]()

requirement-list


→

[requirement](GenericParametersAndArguments.md#requirement)

[requirement](GenericParametersAndArguments.md#requirement)`,`[requirement-list](GenericParametersAndArguments.md#requirement-list)


[‌]()

requirement


→

[conformance-requirement](GenericParametersAndArguments.md#conformance-requirement)

[same-type-requirement](GenericParametersAndArguments.md#same-type-requirement)






[‌]()

conformance-requirement


→
[type-identifier](Types.md#type-identifier)`:`[type-identifier](Types.md#type-identifier)

[‌]()

conformance-requirement


→
[type-identifier](Types.md#type-identifier)`:`[protocol-composition-type](Types.md#protocol-composition-type)

[‌]()

same-type-requirement


→
[type-identifier](Types.md#type-identifier)`==`[type](Types.md#type)







Grammar of a generic argument clause



[‌]()

generic-argument-clause


→
`[generic-argument-list](GenericParametersAndArguments.md#generic-argument-list)`>`

[‌]()

generic-argument-list


→

[generic-argument](GenericParametersAndArguments.md#generic-argument)

[generic-argument](GenericParametersAndArguments.md#generic-argument)`,`[generic-argument-list](GenericParametersAndArguments.md#generic-argument-list)


[‌]()

generic-argument


→
[type](Types.md#type)









[‌]()
### Declarations 



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







Grammar of a top-level declaration



[‌]()

top-level-declaration


→
[statements](Statements.md#statements)~opt~







Grammar of a code block



[‌]()

code-block


→
`{`[statements](Statements.md#statements)~opt~`}`







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







Grammar of a protocol property declaration



[‌]()

protocol-property-declaration


→
[variable-declaration-head](Declarations.md#variable-declaration-head)[variable-name](Declarations.md#variable-name)[type-annotation](Types.md#type-annotation)[getter-setter-keyword-block](Declarations.md#getter-setter-keyword-block)







Grammar of a protocol method declaration



[‌]()

protocol-method-declaration


→
[function-head](Declarations.md#function-head)[function-name](Declarations.md#function-name)[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)~opt~[function-signature](Declarations.md#function-signature)







Grammar of a protocol initializer declaration



[‌]()

protocol-initializer-declaration


→
[initializer-head](Declarations.md#initializer-head)[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)~opt~[parameter-clause](Declarations.md#parameter-clause)`throws`~opt~

[‌]()

protocol-initializer-declaration


→
[initializer-head](Declarations.md#initializer-head)[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)~opt~[parameter-clause](Declarations.md#parameter-clause)`rethrows`







Grammar of a protocol subscript declaration



[‌]()

protocol-subscript-declaration


→
[subscript-head](Declarations.md#subscript-head)[subscript-result](Declarations.md#subscript-result)[getter-setter-keyword-block](Declarations.md#getter-setter-keyword-block)







Grammar of a protocol associated type declaration



[‌]()

protocol-associated-type-declaration


→
[typealias-head](Declarations.md#typealias-head)[type-inheritance-clause](Types.md#type-inheritance-clause)~opt~[typealias-assignment](Declarations.md#typealias-assignment)~opt~







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







Grammar of a deinitializer declaration



[‌]()

deinitializer-declaration


→
[attributes](Attributes.md#attributes)~opt~`deinit`[code-block](Declarations.md#code-block)







Grammar of an extension declaration



[‌]()

extension-declaration


→
[access-level-modifier](Declarations.md#access-level-modifier)~opt~`extension`[type-identifier](Types.md#type-identifier)[type-inheritance-clause](Types.md#type-inheritance-clause)~opt~[extension-body](Declarations.md#extension-body)

[‌]()

extension-body


→
`{`[declarations](Declarations.md#declarations)~opt~`}`







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










[‌]()
### Patterns 



Grammar of a pattern



[‌]()

pattern


→
[wildcard-pattern](Patterns.md#wildcard-pattern)[type-annotation](Types.md#type-annotation)~opt~

[‌]()

pattern


→
[identifier-pattern](Patterns.md#identifier-pattern)[type-annotation](Types.md#type-annotation)~opt~

[‌]()

pattern


→
[value-binding-pattern](Patterns.md#value-binding-pattern)

[‌]()

pattern


→
[tuple-pattern](Patterns.md#tuple-pattern)[type-annotation](Types.md#type-annotation)~opt~

[‌]()

pattern


→
[enum-case-pattern](Patterns.md#enum-case-pattern)

[‌]()

pattern


→
[optional-pattern](Patterns.md#optional-pattern)

[‌]()

pattern


→
[type-casting-pattern](Patterns.md#type-casting-pattern)

[‌]()

pattern


→
[expression-pattern](Patterns.md#expression-pattern)







Grammar of a wildcard pattern



[‌]()

wildcard-pattern


→
`_`







Grammar of an identifier pattern



[‌]()

identifier-pattern


→
[identifier](LexicalStructure.md#identifier)







Grammar of a value-binding pattern



[‌]()

value-binding-pattern


→
`let`[pattern](Patterns.md#pattern)







Grammar of a tuple pattern



[‌]()

tuple-pattern


→
`(`[tuple-pattern-element-list](Patterns.md#tuple-pattern-element-list)~opt~`)`

[‌]()

tuple-pattern-element-list


→

[tuple-pattern-element](Patterns.md#tuple-pattern-element)

[tuple-pattern-element](Patterns.md#tuple-pattern-element)`,`[tuple-pattern-element-list](Patterns.md#tuple-pattern-element-list)


[‌]()

tuple-pattern-element


→
[pattern](Patterns.md#pattern)







Grammar of an enumeration case pattern



[‌]()

enum-case-pattern


→
[type-identifier](Types.md#type-identifier)~opt~`.`[enum-case-name](Declarations.md#enum-case-name)[tuple-pattern](Patterns.md#tuple-pattern)~opt~







Grammar of an optional pattern



[‌]()

optional-pattern


→
[identifier-pattern](Patterns.md#identifier-pattern)`?`







Grammar of a type casting pattern



[‌]()

type-casting-pattern


→

[is-pattern](Patterns.md#is-pattern)

[as-pattern](Patterns.md#as-pattern)


[‌]()

is-pattern


→
`is`[type](Types.md#type)

[‌]()

as-pattern


→
[pattern](Patterns.md#pattern)`as`[type](Types.md#type)







Grammar of an expression pattern



[‌]()

expression-pattern


→
[expression](Expressions.md#expression)









[‌]()
### Attributes 



Grammar of an attribute



[‌]()

attribute


→
`@`[attribute-name](Attributes.md#attribute-name)[attribute-argument-clause](Attributes.md#attribute-argument-clause)~opt~

[‌]()

attribute-name


→
[identifier](LexicalStructure.md#identifier)

[‌]()

attribute-argument-clause


→
`(`[balanced-tokens](Attributes.md#balanced-tokens)~opt~`)`

[‌]()

attributes


→
[attribute](Attributes.md#attribute)[attributes](Attributes.md#attributes)~opt~





[‌]()

balanced-tokens


→
[balanced-token](Attributes.md#balanced-token)[balanced-tokens](Attributes.md#balanced-tokens)~opt~

[‌]()

balanced-token


→
`(`[balanced-tokens](Attributes.md#balanced-tokens)~opt~`)`

[‌]()

balanced-token


→
`[`[balanced-tokens](Attributes.md#balanced-tokens)~opt~`]`

[‌]()

balanced-token


→
`{`[balanced-tokens](Attributes.md#balanced-tokens)~opt~`}`

[‌]()

balanced-token


→
Any identifier, keyword, literal, or operator

[‌]()

balanced-token


→
Any punctuation except `(`, `)`, `[`, `]`, `{`, or `}`









[‌]()
### Expressions 



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







Grammar of a try expression



[‌]()

try-operator


→

`try`

`try``?`

`try``!`








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







Grammar of an assignment operator



[‌]()

assignment-operator


→
`=`







Grammar of a conditional operator



[‌]()

conditional-operator


→
`?`[try-operator](Expressions.md#try-operator)~opt~[expression](Expressions.md#expression)`:`







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








Grammar of a implicit member expression



[‌]()

implicit-member-expression


→
`.`[identifier](LexicalStructure.md#identifier)







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








Grammar of a wildcard expression



[‌]()

wildcard-expression


→
`_`







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







Grammar of an initializer expression



[‌]()

initializer-expression


→
[postfix-expression](Expressions.md#postfix-expression)`.``init`







Grammar of an explicit member expression



[‌]()

explicit-member-expression


→
[postfix-expression](Expressions.md#postfix-expression)`.`[decimal-digits](LexicalStructure.md#decimal-digits)

[‌]()

explicit-member-expression


→
[postfix-expression](Expressions.md#postfix-expression)`.`[identifier](LexicalStructure.md#identifier)[generic-argument-clause](GenericParametersAndArguments.md#generic-argument-clause)~opt~







Grammar of a self expression



[‌]()

postfix-self-expression


→
[postfix-expression](Expressions.md#postfix-expression)`.``self`







Grammar of a dynamic type expression



[‌]()

dynamic-type-expression


→
[postfix-expression](Expressions.md#postfix-expression)`.``dynamicType`







Grammar of a subscript expression



[‌]()

subscript-expression


→
[postfix-expression](Expressions.md#postfix-expression)`[`[expression-list](Expressions.md#expression-list)`]`







Grammar of a forced-value expression



[‌]()

forced-value-expression


→
[postfix-expression](Expressions.md#postfix-expression)`!`







Grammar of an optional-chaining expression



[‌]()

optional-chaining-expression


→
[postfix-expression](Expressions.md#postfix-expression)`?`









[‌]()
### Lexical Structure 



Grammar of an identifier



[‌]()

identifier


→
[identifier-head](LexicalStructure.md#identifier-head)[identifier-characters](LexicalStructure.md#identifier-characters)~opt~

[‌]()

identifier


→
`` ` ``[identifier-head](LexicalStructure.md#identifier-head)[identifier-characters](LexicalStructure.md#identifier-characters)~opt~`` ` ``

[‌]()

identifier


→
[implicit-parameter-name](LexicalStructure.md#implicit-parameter-name)

[‌]()

identifier-list


→

[identifier](LexicalStructure.md#identifier)

[identifier](LexicalStructure.md#identifier)`,`[identifier-list](LexicalStructure.md#identifier-list)






[‌]()

identifier-head


→
Upper- or lowercase letter A through Z

[‌]()

identifier-head


→
`_`

[‌]()

identifier-head


→
U+00A8, U+00AA, U+00AD, U+00AF, U+00B2–U+00B5, or U+00B7–U+00BA

[‌]()

identifier-head


→
U+00BC–U+00BE, U+00C0–U+00D6, U+00D8–U+00F6, or U+00F8–U+00FF

[‌]()

identifier-head


→
U+0100–U+02FF, U+0370–U+167F, U+1681–U+180D, or U+180F–U+1DBF

[‌]()

identifier-head


→
U+1E00–U+1FFF

[‌]()

identifier-head


→
U+200B–U+200D, U+202A–U+202E, U+203F–U+2040, U+2054, or U+2060–U+206F

[‌]()

identifier-head


→
U+2070–U+20CF, U+2100–U+218F, U+2460–U+24FF, or U+2776–U+2793

[‌]()

identifier-head


→
U+2C00–U+2DFF or U+2E80–U+2FFF

[‌]()

identifier-head


→
U+3004–U+3007, U+3021–U+302F, U+3031–U+303F, or U+3040–U+D7FF

[‌]()

identifier-head


→
U+F900–U+FD3D, U+FD40–U+FDCF, U+FDF0–U+FE1F, or U+FE30–U+FE44

[‌]()

identifier-head


→
U+FE47–U+FFFD

[‌]()

identifier-head


→
U+10000–U+1FFFD, U+20000–U+2FFFD, U+30000–U+3FFFD, or U+40000–U+4FFFD

[‌]()

identifier-head


→
U+50000–U+5FFFD, U+60000–U+6FFFD, U+70000–U+7FFFD, or U+80000–U+8FFFD

[‌]()

identifier-head


→
U+90000–U+9FFFD, U+A0000–U+AFFFD, U+B0000–U+BFFFD, or U+C0000–U+CFFFD

[‌]()

identifier-head


→
U+D0000–U+DFFFD or U+E0000–U+EFFFD





[‌]()

identifier-character


→
Digit 0 through 9

[‌]()

identifier-character


→
U+0300–U+036F, U+1DC0–U+1DFF, U+20D0–U+20FF, or U+FE20–U+FE2F

[‌]()

identifier-character


→
[identifier-head](LexicalStructure.md#identifier-head)

[‌]()

identifier-characters


→
[identifier-character](LexicalStructure.md#identifier-character)[identifier-characters](LexicalStructure.md#identifier-characters)~opt~





[‌]()

implicit-parameter-name


→
`$`[decimal-digits](LexicalStructure.md#decimal-digits)







Grammar of a literal



[‌]()

literal


→

[numeric-literal](LexicalStructure.md#numeric-literal)

[string-literal](LexicalStructure.md#string-literal)

[boolean-literal](LexicalStructure.md#boolean-literal)

[nil-literal](LexicalStructure.md#nil-literal)






[‌]()

numeric-literal


→

`-`~opt~[integer-literal](LexicalStructure.md#integer-literal)

`-`~opt~[floating-point-literal](LexicalStructure.md#floating-point-literal)


[‌]()

boolean-literal


→

`true`

`false`


[‌]()

nil-literal


→
`nil`







Grammar of an integer literal



[‌]()

integer-literal


→
[binary-literal](LexicalStructure.md#binary-literal)

[‌]()

integer-literal


→
[octal-literal](LexicalStructure.md#octal-literal)

[‌]()

integer-literal


→
[decimal-literal](LexicalStructure.md#decimal-literal)

[‌]()

integer-literal


→
[hexadecimal-literal](LexicalStructure.md#hexadecimal-literal)





[‌]()

binary-literal


→
`0b`[binary-digit](LexicalStructure.md#binary-digit)[binary-literal-characters](LexicalStructure.md#binary-literal-characters)~opt~

[‌]()

binary-digit


→
Digit 0 or 1

[‌]()

binary-literal-character


→

[binary-digit](LexicalStructure.md#binary-digit)

`_`


[‌]()

binary-literal-characters


→
[binary-literal-character](LexicalStructure.md#binary-literal-character)[binary-literal-characters](LexicalStructure.md#binary-literal-characters)~opt~





[‌]()

octal-literal


→
`0o`[octal-digit](LexicalStructure.md#octal-digit)[octal-literal-characters](LexicalStructure.md#octal-literal-characters)~opt~

[‌]()

octal-digit


→
Digit 0 through 7

[‌]()

octal-literal-character


→

[octal-digit](LexicalStructure.md#octal-digit)

`_`


[‌]()

octal-literal-characters


→
[octal-literal-character](LexicalStructure.md#octal-literal-character)[octal-literal-characters](LexicalStructure.md#octal-literal-characters)~opt~





[‌]()

decimal-literal


→
[decimal-digit](LexicalStructure.md#decimal-digit)[decimal-literal-characters](LexicalStructure.md#decimal-literal-characters)~opt~

[‌]()

decimal-digit


→
Digit 0 through 9

[‌]()

decimal-digits


→
[decimal-digit](LexicalStructure.md#decimal-digit)[decimal-digits](LexicalStructure.md#decimal-digits)~opt~

[‌]()

decimal-literal-character


→

[decimal-digit](LexicalStructure.md#decimal-digit)

`_`


[‌]()

decimal-literal-characters


→
[decimal-literal-character](LexicalStructure.md#decimal-literal-character)[decimal-literal-characters](LexicalStructure.md#decimal-literal-characters)~opt~





[‌]()

hexadecimal-literal


→
`0x`[hexadecimal-digit](LexicalStructure.md#hexadecimal-digit)[hexadecimal-literal-characters](LexicalStructure.md#hexadecimal-literal-characters)~opt~

[‌]()

hexadecimal-digit


→
Digit 0 through 9, a through f, or A through F

[‌]()

hexadecimal-literal-character


→

[hexadecimal-digit](LexicalStructure.md#hexadecimal-digit)

`_`


[‌]()

hexadecimal-literal-characters


→
[hexadecimal-literal-character](LexicalStructure.md#hexadecimal-literal-character)[hexadecimal-literal-characters](LexicalStructure.md#hexadecimal-literal-characters)~opt~







Grammar of a floating-point literal



[‌]()

floating-point-literal


→
[decimal-literal](LexicalStructure.md#decimal-literal)[decimal-fraction](LexicalStructure.md#decimal-fraction)~opt~[decimal-exponent](LexicalStructure.md#decimal-exponent)~opt~

[‌]()

floating-point-literal


→
[hexadecimal-literal](LexicalStructure.md#hexadecimal-literal)[hexadecimal-fraction](LexicalStructure.md#hexadecimal-fraction)~opt~[hexadecimal-exponent](LexicalStructure.md#hexadecimal-exponent)





[‌]()

decimal-fraction


→
`.`[decimal-literal](LexicalStructure.md#decimal-literal)

[‌]()

decimal-exponent


→
[floating-point-e](LexicalStructure.md#floating-point-e)[sign](LexicalStructure.md#sign)~opt~[decimal-literal](LexicalStructure.md#decimal-literal)





[‌]()

hexadecimal-fraction


→
`.`[hexadecimal-digit](LexicalStructure.md#hexadecimal-digit)[hexadecimal-literal-characters](LexicalStructure.md#hexadecimal-literal-characters)~opt~

[‌]()

hexadecimal-exponent


→
[floating-point-p](LexicalStructure.md#floating-point-p)[sign](LexicalStructure.md#sign)~opt~[decimal-literal](LexicalStructure.md#decimal-literal)





[‌]()

floating-point-e


→

`e`

`E`


[‌]()

floating-point-p


→

`p`

`P`


[‌]()

sign


→

`+`

`-`








Grammar of a string literal



[‌]()

string-literal


→

[static-string-literal](LexicalStructure.md#static-string-literal)

[interpolated-string-literal](LexicalStructure.md#interpolated-string-literal)






[‌]()

static-string-literal


→
`"`[quoted-text](LexicalStructure.md#quoted-text)~opt~`"`

[‌]()

quoted-text


→
[quoted-text-item](LexicalStructure.md#quoted-text-item)[quoted-text](LexicalStructure.md#quoted-text)~opt~

[‌]()

quoted-text-item


→
[escaped-character](LexicalStructure.md#escaped-character)

[‌]()

quoted-text-item


→
Any Unicode scalar value except `"`, `\`, U+000A, or U+000D





[‌]()

interpolated-string-literal


→
`"`[interpolated-text](LexicalStructure.md#interpolated-text)~opt~`"`

[‌]()

interpolated-text


→
[interpolated-text-item](LexicalStructure.md#interpolated-text-item)[interpolated-text](LexicalStructure.md#interpolated-text)~opt~

[‌]()

interpolated-text-item


→

`\(`[expression](Expressions.md#expression)`)`

[quoted-text-item](LexicalStructure.md#quoted-text-item)






[‌]()

escaped-character


→

`\0`

`\\`

`\t`

`\n`

`\r`

`\"`

`\'`


[‌]()

escaped-character


→
`\u``{`[unicode-scalar-digits](LexicalStructure.md#unicode-scalar-digits)`}`

[‌]()

unicode-scalar-digits


→
Between one and eight hexadecimal digits







Grammar of operators



[‌]()

operator


→
[operator-head](LexicalStructure.md#operator-head)[operator-characters](LexicalStructure.md#operator-characters)~opt~

[‌]()

operator


→
[dot-operator-head](LexicalStructure.md#dot-operator-head)[dot-operator-characters](LexicalStructure.md#dot-operator-characters)~opt~





[‌]()

operator-head


→

`/`

`=`

`-`

`+`

`!`

`*`

`%`

`<`

`>`

`&`

`|`

`^`

`~`

`?`


[‌]()

operator-head


→
U+00A1–U+00A7

[‌]()

operator-head


→
U+00A9 or U+00AB

[‌]()

operator-head


→
U+00AC or U+00AE

[‌]()

operator-head


→
U+00B0–U+00B1, U+00B6, U+00BB, U+00BF, U+00D7, or U+00F7

[‌]()

operator-head


→
U+2016–U+2017 or U+2020–U+2027

[‌]()

operator-head


→
U+2030–U+203E

[‌]()

operator-head


→
U+2041–U+2053

[‌]()

operator-head


→
U+2055–U+205E

[‌]()

operator-head


→
U+2190–U+23FF

[‌]()

operator-head


→
U+2500–U+2775

[‌]()

operator-head


→
U+2794–U+2BFF

[‌]()

operator-head


→
U+2E00–U+2E7F

[‌]()

operator-head


→
U+3001–U+3003

[‌]()

operator-head


→
U+3008–U+3030





[‌]()

operator-character


→
[operator-head](LexicalStructure.md#operator-head)

[‌]()

operator-character


→
U+0300–U+036F

[‌]()

operator-character


→
U+1DC0–U+1DFF

[‌]()

operator-character


→
U+20D0–U+20FF

[‌]()

operator-character


→
U+FE00–U+FE0F

[‌]()

operator-character


→
U+FE20–U+FE2F

[‌]()

operator-character


→
U+E0100–U+E01EF

[‌]()

operator-characters


→
[operator-character](LexicalStructure.md#operator-character)[operator-characters](LexicalStructure.md#operator-characters)~opt~





[‌]()

dot-operator-head


→
`..`

[‌]()

dot-operator-character


→

`.`

[operator-character](LexicalStructure.md#operator-character)


[‌]()

dot-operator-characters


→
[dot-operator-character](LexicalStructure.md#dot-operator-character)[dot-operator-characters](LexicalStructure.md#dot-operator-characters)~opt~





[‌]()

binary-operator


→
[operator](LexicalStructure.md#operator)

[‌]()

prefix-operator


→
[operator](LexicalStructure.md#operator)

[‌]()

postfix-operator


→
[operator](LexicalStructure.md#operator)









[‌]()
### Types 



Grammar of a type



[‌]()

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








Grammar of a type annotation



[‌]()

type-annotation


→
`:`[attributes](Attributes.md#attributes)~opt~[type](Types.md#type)







Grammar of a type identifier



[‌]()

type-identifier


→

[type-name](Types.md#type-name)[generic-argument-clause](GenericParametersAndArguments.md#generic-argument-clause)~opt~

[type-name](Types.md#type-name)[generic-argument-clause](GenericParametersAndArguments.md#generic-argument-clause)~opt~`.`[type-identifier](Types.md#type-identifier)


[‌]()

type-name


→
[identifier](LexicalStructure.md#identifier)







Grammar of a tuple type



[‌]()

tuple-type


→
`(`[tuple-type-body](Types.md#tuple-type-body)~opt~`)`

[‌]()

tuple-type-body


→
[tuple-type-element-list](Types.md#tuple-type-element-list)`...`~opt~

[‌]()

tuple-type-element-list


→

[tuple-type-element](Types.md#tuple-type-element)

[tuple-type-element](Types.md#tuple-type-element)`,`[tuple-type-element-list](Types.md#tuple-type-element-list)


[‌]()

tuple-type-element


→

[attributes](Attributes.md#attributes)~opt~`inout`~opt~[type](Types.md#type)

`inout`~opt~[element-name](Types.md#element-name)[type-annotation](Types.md#type-annotation)


[‌]()

element-name


→
[identifier](LexicalStructure.md#identifier)







Grammar of a function type



[‌]()

function-type


→
[type](Types.md#type)`throws`~opt~`->`[type](Types.md#type)

[‌]()

function-type


→
[type](Types.md#type)`rethrows``->`[type](Types.md#type)







Grammar of an array type



[‌]()

array-type


→
`[`[type](Types.md#type)`]`







Grammar of a dictionary type



[‌]()

dictionary-type


→
`[`[type](Types.md#type)`:`[type](Types.md#type)`]`







Grammar of an optional type



[‌]()

optional-type


→
[type](Types.md#type)`?`







Grammar of an implicitly unwrapped optional type



[‌]()

implicitly-unwrapped-optional-type


→
[type](Types.md#type)`!`







Grammar of a protocol composition type



[‌]()

protocol-composition-type


→
`protocol``[protocol-identifier-list](Types.md#protocol-identifier-list)~opt~`>`

[‌]()

protocol-identifier-list


→

[protocol-identifier](Types.md#protocol-identifier)

[protocol-identifier](Types.md#protocol-identifier)`,`[protocol-identifier-list](Types.md#protocol-identifier-list)


[‌]()

protocol-identifier


→
[type-identifier](Types.md#type-identifier)







Grammar of a metatype type



[‌]()

metatype-type


→

[type](Types.md#type)`.``Type`

[type](Types.md#type)`.``Protocol`








Grammar of a type inheritance clause



[‌]()

type-inheritance-clause


→
`:`[class-requirement](Types.md#class-requirement)`,`[type-inheritance-list](Types.md#type-inheritance-list)

[‌]()

type-inheritance-clause


→
`:`[class-requirement](Types.md#class-requirement)

[‌]()

type-inheritance-clause


→
`:`[type-inheritance-list](Types.md#type-inheritance-list)

[‌]()

type-inheritance-list


→

[type-identifier](Types.md#type-identifier)

[type-identifier](Types.md#type-identifier)`,`[type-inheritance-list](Types.md#type-inheritance-list)


[‌]()

class-requirement


→
`class`










