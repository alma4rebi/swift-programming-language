Summary of the Grammar
----------------------

### Statements

Grammar of a statement

<span class="syntax-def-name">
statement

<span class="arrow">
→
<span class="syntactic-cat">[expression](Expressions.md#expression)<span class="optional">`;`~opt~

<span class="syntax-def-name">
statement

<span class="arrow">
→
<span class="syntactic-cat">[declaration](Declarations.md#declaration)<span class="optional">`;`~opt~

<span class="syntax-def-name">
statement

<span class="arrow">
→
<span class="syntactic-cat">[loop-statement](Statements.md#loop-statement)<span class="optional">`;`~opt~

<span class="syntax-def-name">
statement

<span class="arrow">
→
<span class="syntactic-cat">[branch-statement](Statements.md#branch-statement)<span class="optional">`;`~opt~

<span class="syntax-def-name">
statement

<span class="arrow">
→
<span class="syntactic-cat">[labeled-statement](Statements.md#labeled-statement)<span class="optional">`;`~opt~

<span class="syntax-def-name">
statement

<span class="arrow">
→
<span class="syntactic-cat">[control-transfer-statement](Statements.md#control-transfer-statement)<span class="optional">`;`~opt~

<span class="syntax-def-name">
statement

<span class="arrow">
→
<span class="syntactic-cat">[defer-statement](Statements.md#defer-statement)<span class="optional">`;`~opt~

<span class="syntax-def-name">
statement

<span class="arrow">
→
<span class="syntactic-cat">[do-statement](Statements.md#do-statement)<span class="optional">`:`~opt~

<span class="syntax-def-name">
statement

<span class="arrow">
→
<span class="syntactic-cat">[compiler-control-statement](Statements.md#compiler-control-statement)

<span class="syntax-def-name">
statements

<span class="arrow">
→
<span class="syntactic-cat">[statement](Statements.md#statement)<span class="optional"><span class="syntactic-cat">[statements](Statements.md#statements)~opt~

Grammar of a loop statement

<span class="syntax-def-name">
loop-statement

<span class="arrow">
→
<span class="syntactic-cat">[for-statement](Statements.md#for-statement)

<span class="syntax-def-name">
loop-statement

<span class="arrow">
→
<span class="syntactic-cat">[for-in-statement](Statements.md#for-in-statement)

<span class="syntax-def-name">
loop-statement

<span class="arrow">
→
<span class="syntactic-cat">[while-statement](Statements.md#while-statement)

<span class="syntax-def-name">
loop-statement

<span class="arrow">
→
<span class="syntactic-cat">[repeat-while-statement](Statements.md#repeat-while-statement)

Grammar of a for statement

<span class="syntax-def-name">
for-statement

<span class="arrow">
→
`for`<span class="optional"><span class="syntactic-cat">[for-init](Statements.md#for-init)~opt~`;`<span class="optional"><span class="syntactic-cat">[expression](Expressions.md#expression)~opt~`;`<span class="optional"><span class="syntactic-cat">[expression-list](Expressions.md#expression-list)~opt~<span class="syntactic-cat">[code-block](Declarations.md#code-block)

<span class="syntax-def-name">
for-statement

<span class="arrow">
→
`for``(`<span class="optional"><span class="syntactic-cat">[for-init](Statements.md#for-init)~opt~`;`<span class="optional"><span class="syntactic-cat">[expression](Expressions.md#expression)~opt~`;`<span class="optional"><span class="syntactic-cat">[expression-list](Expressions.md#expression-list)~opt~`)`<span class="syntactic-cat">[code-block](Declarations.md#code-block)

<span class="syntax-def-name">
for-init

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[variable-declaration](Declarations.md#variable-declaration)
<span class="alternative">
<span class="syntactic-cat">[expression-list](Expressions.md#expression-list)

Grammar of a for-in statement

<span class="syntax-def-name">
for-in-statement

<span class="arrow">
→
`for`<span class="optional">`case`~opt~<span class="syntactic-cat">[pattern](Patterns.md#pattern)`in`<span class="syntactic-cat">[expression](Expressions.md#expression)<span class="optional"><span class="syntactic-cat">[where-clause](Statements.md#where-clause)~opt~<span class="syntactic-cat">[code-block](Declarations.md#code-block)

Grammar of a while statement

<span class="syntax-def-name">
while-statement

<span class="arrow">
→
`while`<span class="syntactic-cat">[condition-clause](Statements.md#condition-clause)<span class="syntactic-cat">[code-block](Declarations.md#code-block)

<span class="syntax-def-name">
condition-clause

<span class="arrow">
→
<span class="syntactic-cat">[expression](Expressions.md#expression)

<span class="syntax-def-name">
condition-clause

<span class="arrow">
→
<span class="syntactic-cat">[expression](Expressions.md#expression)`,`<span class="syntactic-cat">[condition-list](Statements.md#condition-list)

<span class="syntax-def-name">
condition-clause

<span class="arrow">
→
<span class="syntactic-cat">[condition-list](Statements.md#condition-list)

<span class="syntax-def-name">
condition-clause

<span class="arrow">
→
<span class="syntactic-cat">[availability-condition](Statements.md#availability-condition)`,`<span class="syntactic-cat">[expression](Expressions.md#expression)

<span class="syntax-def-name">
condition-list

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[condition](Statements.md#condition)
<span class="alternative">
<span class="syntactic-cat">[condition](Statements.md#condition)`,`<span class="syntactic-cat">[condition-list](Statements.md#condition-list)

<span class="syntax-def-name">
condition

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[availability-condition](Statements.md#availability-condition)
<span class="alternative">
<span class="syntactic-cat">[case-condition](Statements.md#case-condition)
<span class="alternative">
<span class="syntactic-cat">[optional-binding-condition](Statements.md#optional-binding-condition)

<span class="syntax-def-name">
case-condition

<span class="arrow">
→
`case`<span class="syntactic-cat">[pattern](Patterns.md#pattern)<span class="syntactic-cat">[initializer](Declarations.md#initializer)<span class="optional"><span class="syntactic-cat">[where-clause](Statements.md#where-clause)~opt~

<span class="syntax-def-name">
optional-binding-condition

<span class="arrow">
→
<span class="syntactic-cat">[optional-binding-head](Statements.md#optional-binding-head)<span class="optional"><span class="syntactic-cat">[optional-binding-continuation-list](Statements.md#optional-binding-continuation-list)~opt~<span class="optional"><span class="syntactic-cat">[where-clause](Statements.md#where-clause)~opt~

<span class="syntax-def-name">
optional-binding-head

<span class="arrow">
→
`let`<span class="syntactic-cat">[pattern](Patterns.md#pattern)<span class="syntactic-cat">[initializer](Declarations.md#initializer)

<span class="syntax-def-name">
optional-binding-continuation-list

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[optional-binding-continuation](Statements.md#optional-binding-continuation)
<span class="alternative">
<span class="syntactic-cat">[optional-binding-continuation](Statements.md#optional-binding-continuation)`,`<span class="syntactic-cat">[optional-binding-continuation-list](Statements.md#optional-binding-continuation-list)

<span class="syntax-def-name">
optional-binding-continuation

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[pattern](Patterns.md#pattern)<span class="syntactic-cat">[initializer](Declarations.md#initializer)
<span class="alternative">
<span class="syntactic-cat">[optional-binding-head](Statements.md#optional-binding-head)

Grammar of a repeat-while statement

<span class="syntax-def-name">
repeat-while-statement

<span class="arrow">
→
`repeat`<span class="syntactic-cat">[code-block](Declarations.md#code-block)`while`<span class="syntactic-cat">[expression](Expressions.md#expression)

Grammar of a branch statement

<span class="syntax-def-name">
branch-statement

<span class="arrow">
→
<span class="syntactic-cat">[if-statement](Statements.md#if-statement)

<span class="syntax-def-name">
branch-statement

<span class="arrow">
→
<span class="syntactic-cat">[guard-statement](Statements.md#guard-statement)

<span class="syntax-def-name">
branch-statement

<span class="arrow">
→
<span class="syntactic-cat">[switch-statement](Statements.md#switch-statement)

Grammar of an if statement

<span class="syntax-def-name">
if-statement

<span class="arrow">
→
`if`<span class="syntactic-cat">[condition-clause](Statements.md#condition-clause)<span class="syntactic-cat">[code-block](Declarations.md#code-block)<span class="optional"><span class="syntactic-cat">[else-clause](Statements.md#else-clause)~opt~

<span class="syntax-def-name">
else-clause

<span class="arrow">
→
<span class="alternative">
`else`<span class="syntactic-cat">[code-block](Declarations.md#code-block)
<span class="alternative">
`else`<span class="syntactic-cat">[if-statement](Statements.md#if-statement)

Grammar of a guard statement

<span class="syntax-def-name">
guard-statement

<span class="arrow">
→
`guard`<span class="syntactic-cat">[condition-clause](Statements.md#condition-clause)`else`<span class="syntactic-cat">[code-block](Declarations.md#code-block)

Grammar of a switch statement

<span class="syntax-def-name">
switch-statement

<span class="arrow">
→
`switch`<span class="syntactic-cat">[expression](Expressions.md#expression)`{`<span class="optional"><span class="syntactic-cat">[switch-cases](Statements.md#switch-cases)~opt~`}`

<span class="syntax-def-name">
switch-cases

<span class="arrow">
→
<span class="syntactic-cat">[switch-case](Statements.md#switch-case)<span class="optional"><span class="syntactic-cat">[switch-cases](Statements.md#switch-cases)~opt~

<span class="syntax-def-name">
switch-case

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[case-label](Statements.md#case-label)<span class="syntactic-cat">[statements](Statements.md#statements)
<span class="alternative">
<span class="syntactic-cat">[default-label](Statements.md#default-label)<span class="syntactic-cat">[statements](Statements.md#statements)

<span class="syntax-def-name">
case-label

<span class="arrow">
→
`case`<span class="syntactic-cat">[case-item-list](Statements.md#case-item-list)`:`

<span class="syntax-def-name">
case-item-list

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[pattern](Patterns.md#pattern)<span class="optional"><span class="syntactic-cat">[where-clause](Statements.md#where-clause)~opt~
<span class="alternative">
<span class="syntactic-cat">[pattern](Patterns.md#pattern)<span class="optional"><span class="syntactic-cat">[where-clause](Statements.md#where-clause)~opt~`,`<span class="syntactic-cat">[case-item-list](Statements.md#case-item-list)

<span class="syntax-def-name">
default-label

<span class="arrow">
→
`default``:`

<span class="syntax-def-name">
where-clause

<span class="arrow">
→
`where`<span class="syntactic-cat">[where-expression](Statements.md#where-expression)

<span class="syntax-def-name">
where-expression

<span class="arrow">
→
<span class="syntactic-cat">[expression](Expressions.md#expression)

Grammar of a labeled statement

<span class="syntax-def-name">
labeled-statement

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[statement-label](Statements.md#statement-label)<span class="syntactic-cat">[loop-statement](Statements.md#loop-statement)
<span class="alternative">
<span class="syntactic-cat">[statement-label](Statements.md#statement-label)<span class="syntactic-cat">[if-statement](Statements.md#if-statement)
<span class="alternative">
<span class="syntactic-cat">[statement-label](Statements.md#statement-label)<span class="syntactic-cat">[switch-statement](Statements.md#switch-statement)

<span class="syntax-def-name">
statement-label

<span class="arrow">
→
<span class="syntactic-cat">[label-name](Statements.md#label-name)`:`

<span class="syntax-def-name">
label-name

<span class="arrow">
→
<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)

Grammar of a control transfer statement

<span class="syntax-def-name">
control-transfer-statement

<span class="arrow">
→
<span class="syntactic-cat">[break-statement](Statements.md#break-statement)

<span class="syntax-def-name">
control-transfer-statement

<span class="arrow">
→
<span class="syntactic-cat">[continue-statement](Statements.md#continue-statement)

<span class="syntax-def-name">
control-transfer-statement

<span class="arrow">
→
<span class="syntactic-cat">[fallthrough-statement](Statements.md#fallthrough-statement)

<span class="syntax-def-name">
control-transfer-statement

<span class="arrow">
→
<span class="syntactic-cat">[return-statement](Statements.md#return-statement)

<span class="syntax-def-name">
control-transfer-statement

<span class="arrow">
→
<span class="syntactic-cat">[throw-statement](Statements.md#throw-statement)

Grammar of a break statement

<span class="syntax-def-name">
break-statement

<span class="arrow">
→
`break`<span class="optional"><span class="syntactic-cat">[label-name](Statements.md#label-name)~opt~

Grammar of a continue statement

<span class="syntax-def-name">
continue-statement

<span class="arrow">
→
`continue`<span class="optional"><span class="syntactic-cat">[label-name](Statements.md#label-name)~opt~

Grammar of a fallthrough statement

<span class="syntax-def-name">
fallthrough-statement

<span class="arrow">
→
`fallthrough`

Grammar of a return statement

<span class="syntax-def-name">
return-statement

<span class="arrow">
→
`return`<span class="optional"><span class="syntactic-cat">[expression](Expressions.md#expression)~opt~

Grammar of an availability condition

<span class="syntax-def-name">
availability-condition

<span class="arrow">
→
`#available``(`<span class="syntactic-cat">[availability-arguments](Statements.md#availability-arguments)`)`

<span class="syntax-def-name">
availability-arguments

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[availability-argument](Statements.md#availability-argument)
<span class="alternative">
<span class="syntactic-cat">[availability-argument](Statements.md#availability-argument)`,`<span class="syntactic-cat">[availability-arguments](Statements.md#availability-arguments)

<span class="syntax-def-name">
availability-argument

<span class="arrow">
→
<span class="syntactic-cat">[platform-name](Statements.md#platform-name)<span class="syntactic-cat">[platform-version](Statements.md#platform-version)

<span class="syntax-def-name">
availability-argument

<span class="arrow">
→
`*`

<span class="syntax-def-name">
platform-name

<span class="arrow">
→
<span class="alternative">
`iOS`
<span class="alternative">
`iOSApplicationExtension`

<span class="syntax-def-name">
platform-name

<span class="arrow">
→
<span class="alternative">
`OSX`
<span class="alternative">
`OSXApplicationExtension`

<span class="syntax-def-name">
platform-name

<span class="arrow">
→
`watchOS`

<span class="syntax-def-name">
platform-version

<span class="arrow">
→
<span class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)

<span class="syntax-def-name">
platform-version

<span class="arrow">
→
<span class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)`.`<span class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)

<span class="syntax-def-name">
platform-version

<span class="arrow">
→
<span class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)`.`<span class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)`.`<span class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)

Grammar of a throw statement

<span class="syntax-def-name">
throw-statement

<span class="arrow">
→
`throw`<span class="syntactic-cat">[expression](Expressions.md#expression)

Grammar of a defer statement

<span class="syntax-def-name">
defer-statement

<span class="arrow">
→
`defer`<span class="syntactic-cat">[code-block](Declarations.md#code-block)

Grammar of a do statement

<span class="syntax-def-name">
do-statement

<span class="arrow">
→
`do`<span class="syntactic-cat">[code-block](Declarations.md#code-block)<span class="optional"><span class="syntactic-cat">[catch-clauses](Statements.md#catch-clauses)~opt~

<span class="syntax-def-name">
catch-clauses

<span class="arrow">
→
<span class="syntactic-cat">[catch-clause](Statements.md#catch-clause)<span class="optional"><span class="syntactic-cat">[catch-clauses](Statements.md#catch-clauses)~opt~

<span class="syntax-def-name">
catch-clause

<span class="arrow">
→
`catch`<span class="optional"><span class="syntactic-cat">[pattern](Patterns.md#pattern)~opt~<span class="optional"><span class="syntactic-cat">[where-clause](Statements.md#where-clause)~opt~<span class="syntactic-cat">[code-block](Declarations.md#code-block)

Grammar of a compiler control statement

<span class="syntax-def-name">
compiler-control-statement

<span class="arrow">
→
<span class="syntactic-cat">[build-configuration-statement](Statements.md#build-configuration-statement)

<span class="syntax-def-name">
compiler-control-statement

<span class="arrow">
→
<span class="syntactic-cat">[line-control-statement](Statements.md#line-control-statement)

Grammar of a build configuration statement

<span class="syntax-def-name">
build-configuration-statement

<span class="arrow">
→
`#if`<span class="syntactic-cat">[build-configuration](Statements.md#build-configuration)<span class="optional"><span class="syntactic-cat">[statements](Statements.md#statements)~opt~<span class="optional"><span class="syntactic-cat">[build-configuration-elseif-clauses](Statements.md#build-configuration-elseif-clauses)~opt~<span class="optional"><span class="syntactic-cat">[build-configuration-else-clause](Statements.md#build-configuration-else-clause)~opt~`#endif`

<span class="syntax-def-name">
build-configuration-elseif-clauses

<span class="arrow">
→
<span class="syntactic-cat">[build-configuration-elseif-clause](Statements.md#build-configuration-elseif-clause)<span class="optional"><span class="syntactic-cat">[build-configuration-elseif-clauses](Statements.md#build-configuration-elseif-clauses)~opt~

<span class="syntax-def-name">
build-configuration-elseif-clause

<span class="arrow">
→
`#elseif`<span class="syntactic-cat">[build-configuration](Statements.md#build-configuration)<span class="optional"><span class="syntactic-cat">[statements](Statements.md#statements)~opt~

<span class="syntax-def-name">
build-configuration-else-clause

<span class="arrow">
→
`#else`<span class="optional"><span class="syntactic-cat">[statements](Statements.md#statements)~opt~

<span class="syntax-def-name">
build-configuration

<span class="arrow">
→
<span class="syntactic-cat">[platform-testing-function](Statements.md#platform-testing-function)

<span class="syntax-def-name">
build-configuration

<span class="arrow">
→
<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)

<span class="syntax-def-name">
build-configuration

<span class="arrow">
→
<span class="syntactic-cat">[boolean-literal](LexicalStructure.md#boolean-literal)

<span class="syntax-def-name">
build-configuration

<span class="arrow">
→
`(`<span class="syntactic-cat">[build-configuration](Statements.md#build-configuration)`)`

<span class="syntax-def-name">
build-configuration

<span class="arrow">
→
`!`<span class="syntactic-cat">[build-configuration](Statements.md#build-configuration)

<span class="syntax-def-name">
build-configuration

<span class="arrow">
→
<span class="syntactic-cat">[build-configuration](Statements.md#build-configuration)`&&`<span class="syntactic-cat">[build-configuration](Statements.md#build-configuration)

<span class="syntax-def-name">
build-configuration

<span class="arrow">
→
<span class="syntactic-cat">[build-configuration](Statements.md#build-configuration)`||`<span class="syntactic-cat">[build-configuration](Statements.md#build-configuration)

<span class="syntax-def-name">
platform-testing-function

<span class="arrow">
→
`os``(`<span class="syntactic-cat">[operating-system](Statements.md#operating-system)`)`

<span class="syntax-def-name">
platform-testing-function

<span class="arrow">
→
`arch``(`<span class="syntactic-cat">[architecture](Statements.md#architecture)`)`

<span class="syntax-def-name">
operating-system

<span class="arrow">
→
<span class="alternative">
`OSX`
<span class="alternative">
`iOS`
<span class="alternative">
`watchOS`
<span class="alternative">
`tvOS`

<span class="syntax-def-name">
architecture

<span class="arrow">
→
<span class="alternative">
`i386`
<span class="alternative">
`x86_64`
<span class="alternative">
`arm`
<span class="alternative">
`arm64`

Grammar of a line control statement

<span class="syntax-def-name">
line-control-statement

<span class="arrow">
→
`#line`

<span class="syntax-def-name">
line-control-statement

<span class="arrow">
→
`#line`<span class="syntactic-cat">[line-number](Statements.md#line-number)<span class="syntactic-cat">[file-name](Statements.md#file-name)

<span class="syntax-def-name">
line-number

<span class="arrow">
→
<span class="text-description">A decimal integer greater than zero

<span class="syntax-def-name">
file-name

<span class="arrow">
→
<span class="syntactic-cat">[static-string-literal](LexicalStructure.md#static-string-literal)

### Generic Parameters and Arguments

Grammar of a generic parameter clause

<span class="syntax-def-name">
generic-parameter-clause

<span class="arrow">
→
`<`<span class="syntactic-cat">[generic-parameter-list](GenericParametersAndArguments.md#generic-parameter-list)<span class="optional"><span class="syntactic-cat">[requirement-clause](GenericParametersAndArguments.md#requirement-clause)~opt~`>`

<span class="syntax-def-name">
generic-parameter-list

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[generic-parameter](GenericParametersAndArguments.md#generic-parameter)
<span class="alternative">
<span class="syntactic-cat">[generic-parameter](GenericParametersAndArguments.md#generic-parameter)`,`<span class="syntactic-cat">[generic-parameter-list](GenericParametersAndArguments.md#generic-parameter-list)

<span class="syntax-def-name">
generic-parameter

<span class="arrow">
→
<span class="syntactic-cat">[type-name](Types.md#type-name)

<span class="syntax-def-name">
generic-parameter

<span class="arrow">
→
<span class="syntactic-cat">[type-name](Types.md#type-name)`:`<span class="syntactic-cat">[type-identifier](Types.md#type-identifier)

<span class="syntax-def-name">
generic-parameter

<span class="arrow">
→
<span class="syntactic-cat">[type-name](Types.md#type-name)`:`<span class="syntactic-cat">[protocol-composition-type](Types.md#protocol-composition-type)

<span class="syntax-def-name">
requirement-clause

<span class="arrow">
→
`where`<span class="syntactic-cat">[requirement-list](GenericParametersAndArguments.md#requirement-list)

<span class="syntax-def-name">
requirement-list

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[requirement](GenericParametersAndArguments.md#requirement)
<span class="alternative">
<span class="syntactic-cat">[requirement](GenericParametersAndArguments.md#requirement)`,`<span class="syntactic-cat">[requirement-list](GenericParametersAndArguments.md#requirement-list)

<span class="syntax-def-name">
requirement

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[conformance-requirement](GenericParametersAndArguments.md#conformance-requirement)
<span class="alternative">
<span class="syntactic-cat">[same-type-requirement](GenericParametersAndArguments.md#same-type-requirement)

<span class="syntax-def-name">
conformance-requirement

<span class="arrow">
→
<span class="syntactic-cat">[type-identifier](Types.md#type-identifier)`:`<span class="syntactic-cat">[type-identifier](Types.md#type-identifier)

<span class="syntax-def-name">
conformance-requirement

<span class="arrow">
→
<span class="syntactic-cat">[type-identifier](Types.md#type-identifier)`:`<span class="syntactic-cat">[protocol-composition-type](Types.md#protocol-composition-type)

<span class="syntax-def-name">
same-type-requirement

<span class="arrow">
→
<span class="syntactic-cat">[type-identifier](Types.md#type-identifier)`==`<span class="syntactic-cat">[type](Types.md#type)

Grammar of a generic argument clause

<span class="syntax-def-name">
generic-argument-clause

<span class="arrow">
→
`<`<span class="syntactic-cat">[generic-argument-list](GenericParametersAndArguments.md#generic-argument-list)`>`

<span class="syntax-def-name">
generic-argument-list

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[generic-argument](GenericParametersAndArguments.md#generic-argument)
<span class="alternative">
<span class="syntactic-cat">[generic-argument](GenericParametersAndArguments.md#generic-argument)`,`<span class="syntactic-cat">[generic-argument-list](GenericParametersAndArguments.md#generic-argument-list)

<span class="syntax-def-name">
generic-argument

<span class="arrow">
→
<span class="syntactic-cat">[type](Types.md#type)

### Declarations

Grammar of a declaration

<span class="syntax-def-name">
declaration

<span class="arrow">
→
<span class="syntactic-cat">[import-declaration](Declarations.md#import-declaration)

<span class="syntax-def-name">
declaration

<span class="arrow">
→
<span class="syntactic-cat">[constant-declaration](Declarations.md#constant-declaration)

<span class="syntax-def-name">
declaration

<span class="arrow">
→
<span class="syntactic-cat">[variable-declaration](Declarations.md#variable-declaration)

<span class="syntax-def-name">
declaration

<span class="arrow">
→
<span class="syntactic-cat">[typealias-declaration](Declarations.md#typealias-declaration)

<span class="syntax-def-name">
declaration

<span class="arrow">
→
<span class="syntactic-cat">[function-declaration](Declarations.md#function-declaration)

<span class="syntax-def-name">
declaration

<span class="arrow">
→
<span class="syntactic-cat">[enum-declaration](Declarations.md#enum-declaration)

<span class="syntax-def-name">
declaration

<span class="arrow">
→
<span class="syntactic-cat">[struct-declaration](Declarations.md#struct-declaration)

<span class="syntax-def-name">
declaration

<span class="arrow">
→
<span class="syntactic-cat">[class-declaration](Declarations.md#class-declaration)

<span class="syntax-def-name">
declaration

<span class="arrow">
→
<span class="syntactic-cat">[protocol-declaration](Declarations.md#protocol-declaration)

<span class="syntax-def-name">
declaration

<span class="arrow">
→
<span class="syntactic-cat">[initializer-declaration](Declarations.md#initializer-declaration)

<span class="syntax-def-name">
declaration

<span class="arrow">
→
<span class="syntactic-cat">[deinitializer-declaration](Declarations.md#deinitializer-declaration)

<span class="syntax-def-name">
declaration

<span class="arrow">
→
<span class="syntactic-cat">[extension-declaration](Declarations.md#extension-declaration)

<span class="syntax-def-name">
declaration

<span class="arrow">
→
<span class="syntactic-cat">[subscript-declaration](Declarations.md#subscript-declaration)

<span class="syntax-def-name">
declaration

<span class="arrow">
→
<span class="syntactic-cat">[operator-declaration](Declarations.md#operator-declaration)

<span class="syntax-def-name">
declarations

<span class="arrow">
→
<span class="syntactic-cat">[declaration](Declarations.md#declaration)<span class="optional"><span class="syntactic-cat">[declarations](Declarations.md#declarations)~opt~

Grammar of a top-level declaration

<span class="syntax-def-name">
top-level-declaration

<span class="arrow">
→
<span class="optional"><span class="syntactic-cat">[statements](Statements.md#statements)~opt~

Grammar of a code block

<span class="syntax-def-name">
code-block

<span class="arrow">
→
`{`<span class="optional"><span class="syntactic-cat">[statements](Statements.md#statements)~opt~`}`

Grammar of an import declaration

<span class="syntax-def-name">
import-declaration

<span class="arrow">
→
<span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)~opt~`import`<span class="optional"><span class="syntactic-cat">[import-kind](Declarations.md#import-kind)~opt~<span class="syntactic-cat">[import-path](Declarations.md#import-path)

<span class="syntax-def-name">
import-kind

<span class="arrow">
→
<span class="alternative">
`typealias`
<span class="alternative">
`struct`
<span class="alternative">
`class`
<span class="alternative">
`enum`
<span class="alternative">
`protocol`
<span class="alternative">
`var`
<span class="alternative">
`func`

<span class="syntax-def-name">
import-path

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[import-path-identifier](Declarations.md#import-path-identifier)
<span class="alternative">
<span class="syntactic-cat">[import-path-identifier](Declarations.md#import-path-identifier)`.`<span class="syntactic-cat">[import-path](Declarations.md#import-path)

<span class="syntax-def-name">
import-path-identifier

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)
<span class="alternative">
<span class="syntactic-cat">[operator](LexicalStructure.md#operator)

Grammar of a constant declaration

<span class="syntax-def-name">
constant-declaration

<span class="arrow">
→
<span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)~opt~<span class="optional"><span class="syntactic-cat">[declaration-modifiers](Declarations.md#declaration-modifiers)~opt~`let`<span class="syntactic-cat">[pattern-initializer-list](Declarations.md#pattern-initializer-list)

<span class="syntax-def-name">
pattern-initializer-list

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[pattern-initializer](Declarations.md#pattern-initializer)
<span class="alternative">
<span class="syntactic-cat">[pattern-initializer](Declarations.md#pattern-initializer)`,`<span class="syntactic-cat">[pattern-initializer-list](Declarations.md#pattern-initializer-list)

<span class="syntax-def-name">
pattern-initializer

<span class="arrow">
→
<span class="syntactic-cat">[pattern](Patterns.md#pattern)<span class="optional"><span class="syntactic-cat">[initializer](Declarations.md#initializer)~opt~

<span class="syntax-def-name">
initializer

<span class="arrow">
→
`=`<span class="syntactic-cat">[expression](Expressions.md#expression)

Grammar of a variable declaration

<span class="syntax-def-name">
variable-declaration

<span class="arrow">
→
<span class="syntactic-cat">[variable-declaration-head](Declarations.md#variable-declaration-head)<span class="syntactic-cat">[pattern-initializer-list](Declarations.md#pattern-initializer-list)

<span class="syntax-def-name">
variable-declaration

<span class="arrow">
→
<span class="syntactic-cat">[variable-declaration-head](Declarations.md#variable-declaration-head)<span class="syntactic-cat">[variable-name](Declarations.md#variable-name)<span class="syntactic-cat">[type-annotation](Types.md#type-annotation)<span class="syntactic-cat">[code-block](Declarations.md#code-block)

<span class="syntax-def-name">
variable-declaration

<span class="arrow">
→
<span class="syntactic-cat">[variable-declaration-head](Declarations.md#variable-declaration-head)<span class="syntactic-cat">[variable-name](Declarations.md#variable-name)<span class="syntactic-cat">[type-annotation](Types.md#type-annotation)<span class="syntactic-cat">[getter-setter-block](Declarations.md#getter-setter-block)

<span class="syntax-def-name">
variable-declaration

<span class="arrow">
→
<span class="syntactic-cat">[variable-declaration-head](Declarations.md#variable-declaration-head)<span class="syntactic-cat">[variable-name](Declarations.md#variable-name)<span class="syntactic-cat">[type-annotation](Types.md#type-annotation)<span class="syntactic-cat">[getter-setter-keyword-block](Declarations.md#getter-setter-keyword-block)

<span class="syntax-def-name">
variable-declaration

<span class="arrow">
→
<span class="syntactic-cat">[variable-declaration-head](Declarations.md#variable-declaration-head)<span class="syntactic-cat">[variable-name](Declarations.md#variable-name)<span class="syntactic-cat">[initializer](Declarations.md#initializer)<span class="syntactic-cat">[willSet-didSet-block](Declarations.md#willSet-didSet-block)

<span class="syntax-def-name">
variable-declaration

<span class="arrow">
→
<span class="syntactic-cat">[variable-declaration-head](Declarations.md#variable-declaration-head)<span class="syntactic-cat">[variable-name](Declarations.md#variable-name)<span class="syntactic-cat">[type-annotation](Types.md#type-annotation)<span class="optional"><span class="syntactic-cat">[initializer](Declarations.md#initializer)~opt~<span class="syntactic-cat">[willSet-didSet-block](Declarations.md#willSet-didSet-block)

<span class="syntax-def-name">
variable-declaration-head

<span class="arrow">
→
<span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)~opt~<span class="optional"><span class="syntactic-cat">[declaration-modifiers](Declarations.md#declaration-modifiers)~opt~`var`

<span class="syntax-def-name">
variable-name

<span class="arrow">
→
<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)

<span class="syntax-def-name">
getter-setter-block

<span class="arrow">
→
<span class="syntactic-cat">[code-block](Declarations.md#code-block)

<span class="syntax-def-name">
getter-setter-block

<span class="arrow">
→
`{`<span class="syntactic-cat">[getter-clause](Declarations.md#getter-clause)<span class="optional"><span class="syntactic-cat">[setter-clause](Declarations.md#setter-clause)~opt~`}`

<span class="syntax-def-name">
getter-setter-block

<span class="arrow">
→
`{`<span class="syntactic-cat">[setter-clause](Declarations.md#setter-clause)<span class="syntactic-cat">[getter-clause](Declarations.md#getter-clause)`}`

<span class="syntax-def-name">
getter-clause

<span class="arrow">
→
<span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)~opt~`get`<span class="syntactic-cat">[code-block](Declarations.md#code-block)

<span class="syntax-def-name">
setter-clause

<span class="arrow">
→
<span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)~opt~`set`<span class="optional"><span class="syntactic-cat">[setter-name](Declarations.md#setter-name)~opt~<span class="syntactic-cat">[code-block](Declarations.md#code-block)

<span class="syntax-def-name">
setter-name

<span class="arrow">
→
`(`<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)`)`

<span class="syntax-def-name">
getter-setter-keyword-block

<span class="arrow">
→
`{`<span class="syntactic-cat">[getter-keyword-clause](Declarations.md#getter-keyword-clause)<span class="optional"><span class="syntactic-cat">[setter-keyword-clause](Declarations.md#setter-keyword-clause)~opt~`}`

<span class="syntax-def-name">
getter-setter-keyword-block

<span class="arrow">
→
`{`<span class="syntactic-cat">[setter-keyword-clause](Declarations.md#setter-keyword-clause)<span class="syntactic-cat">[getter-keyword-clause](Declarations.md#getter-keyword-clause)`}`

<span class="syntax-def-name">
getter-keyword-clause

<span class="arrow">
→
<span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)~opt~`get`

<span class="syntax-def-name">
setter-keyword-clause

<span class="arrow">
→
<span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)~opt~`set`

<span class="syntax-def-name">
willSet-didSet-block

<span class="arrow">
→
`{`<span class="syntactic-cat">[willSet-clause](Declarations.md#willSet-clause)<span class="optional"><span class="syntactic-cat">[didSet-clause](Declarations.md#didSet-clause)~opt~`}`

<span class="syntax-def-name">
willSet-didSet-block

<span class="arrow">
→
`{`<span class="syntactic-cat">[didSet-clause](Declarations.md#didSet-clause)<span class="optional"><span class="syntactic-cat">[willSet-clause](Declarations.md#willSet-clause)~opt~`}`

<span class="syntax-def-name">
willSet-clause

<span class="arrow">
→
<span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)~opt~`willSet`<span class="optional"><span class="syntactic-cat">[setter-name](Declarations.md#setter-name)~opt~<span class="syntactic-cat">[code-block](Declarations.md#code-block)

<span class="syntax-def-name">
didSet-clause

<span class="arrow">
→
<span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)~opt~`didSet`<span class="optional"><span class="syntactic-cat">[setter-name](Declarations.md#setter-name)~opt~<span class="syntactic-cat">[code-block](Declarations.md#code-block)

Grammar of a type alias declaration

<span class="syntax-def-name">
typealias-declaration

<span class="arrow">
→
<span class="syntactic-cat">[typealias-head](Declarations.md#typealias-head)<span class="syntactic-cat">[typealias-assignment](Declarations.md#typealias-assignment)

<span class="syntax-def-name">
typealias-head

<span class="arrow">
→
<span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)~opt~<span class="optional"><span class="syntactic-cat">[access-level-modifier](Declarations.md#access-level-modifier)~opt~`typealias`<span class="syntactic-cat">[typealias-name](Declarations.md#typealias-name)

<span class="syntax-def-name">
typealias-name

<span class="arrow">
→
<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)

<span class="syntax-def-name">
typealias-assignment

<span class="arrow">
→
`=`<span class="syntactic-cat">[type](Types.md#type)

Grammar of a function declaration

<span class="syntax-def-name">
function-declaration

<span class="arrow">
→
<span class="syntactic-cat">[function-head](Declarations.md#function-head)<span class="syntactic-cat">[function-name](Declarations.md#function-name)<span class="optional"><span class="syntactic-cat">[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)~opt~<span class="syntactic-cat">[function-signature](Declarations.md#function-signature)<span class="optional"><span class="syntactic-cat">[function-body](Declarations.md#function-body)~opt~

<span class="syntax-def-name">
function-head

<span class="arrow">
→
<span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)~opt~<span class="optional"><span class="syntactic-cat">[declaration-modifiers](Declarations.md#declaration-modifiers)~opt~`func`

<span class="syntax-def-name">
function-name

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)
<span class="alternative">
<span class="syntactic-cat">[operator](LexicalStructure.md#operator)

<span class="syntax-def-name">
function-signature

<span class="arrow">
→
<span class="syntactic-cat">[parameter-clause](Declarations.md#parameter-clause)<span class="optional">`throws`~opt~<span class="optional"><span class="syntactic-cat">[function-result](Declarations.md#function-result)~opt~

<span class="syntax-def-name">
function-signature

<span class="arrow">
→
<span class="syntactic-cat">[parameter-clause](Declarations.md#parameter-clause)`rethrows`<span class="optional"><span class="syntactic-cat">[function-result](Declarations.md#function-result)~opt~

<span class="syntax-def-name">
function-result

<span class="arrow">
→
`->`<span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)~opt~<span class="syntactic-cat">[type](Types.md#type)

<span class="syntax-def-name">
function-body

<span class="arrow">
→
<span class="syntactic-cat">[code-block](Declarations.md#code-block)

<span class="syntax-def-name">
parameter-clause

<span class="arrow">
→
<span class="alternative">
`(``)`
<span class="alternative">
`(`<span class="syntactic-cat">[parameter-list](Declarations.md#parameter-list)`)`

<span class="syntax-def-name">
parameter-list

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[parameter](Declarations.md#parameter)
<span class="alternative">
<span class="syntactic-cat">[parameter](Declarations.md#parameter)`,`<span class="syntactic-cat">[parameter-list](Declarations.md#parameter-list)

<span class="syntax-def-name">
parameter

<span class="arrow">
→
<span class="optional">`let`~opt~<span class="optional"><span class="syntactic-cat">[external-parameter-name](Declarations.md#external-parameter-name)~opt~<span class="syntactic-cat">[local-parameter-name](Declarations.md#local-parameter-name)<span class="syntactic-cat">[type-annotation](Types.md#type-annotation)<span class="optional"><span class="syntactic-cat">[default-argument-clause](Declarations.md#default-argument-clause)~opt~

<span class="syntax-def-name">
parameter

<span class="arrow">
→
`inout`<span class="optional"><span class="syntactic-cat">[external-parameter-name](Declarations.md#external-parameter-name)~opt~<span class="syntactic-cat">[local-parameter-name](Declarations.md#local-parameter-name)<span class="syntactic-cat">[type-annotation](Types.md#type-annotation)

<span class="syntax-def-name">
parameter

<span class="arrow">
→
<span class="optional"><span class="syntactic-cat">[external-parameter-name](Declarations.md#external-parameter-name)~opt~<span class="syntactic-cat">[local-parameter-name](Declarations.md#local-parameter-name)<span class="syntactic-cat">[type-annotation](Types.md#type-annotation)`...`

<span class="syntax-def-name">
external-parameter-name

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)
<span class="alternative">
`_`

<span class="syntax-def-name">
local-parameter-name

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)
<span class="alternative">
`_`

<span class="syntax-def-name">
default-argument-clause

<span class="arrow">
→
`=`<span class="syntactic-cat">[expression](Expressions.md#expression)

Grammar of an enumeration declaration

<span class="syntax-def-name">
enum-declaration

<span class="arrow">
→
<span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)~opt~<span class="optional"><span class="syntactic-cat">[access-level-modifier](Declarations.md#access-level-modifier)~opt~<span class="syntactic-cat">[union-style-enum](Declarations.md#union-style-enum)

<span class="syntax-def-name">
enum-declaration

<span class="arrow">
→
<span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)~opt~<span class="optional"><span class="syntactic-cat">[access-level-modifier](Declarations.md#access-level-modifier)~opt~<span class="syntactic-cat">[raw-value-style-enum](Declarations.md#raw-value-style-enum)

<span class="syntax-def-name">
union-style-enum

<span class="arrow">
→
<span class="optional">`indirect`~opt~`enum`<span class="syntactic-cat">[enum-name](Declarations.md#enum-name)<span class="optional"><span class="syntactic-cat">[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)~opt~<span class="optional"><span class="syntactic-cat">[type-inheritance-clause](Types.md#type-inheritance-clause)~opt~`{`<span class="optional"><span class="syntactic-cat">[union-style-enum-members](Declarations.md#union-style-enum-members)~opt~`}`

<span class="syntax-def-name">
union-style-enum-members

<span class="arrow">
→
<span class="syntactic-cat">[union-style-enum-member](Declarations.md#union-style-enum-member)<span class="optional"><span class="syntactic-cat">[union-style-enum-members](Declarations.md#union-style-enum-members)~opt~

<span class="syntax-def-name">
union-style-enum-member

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[declaration](Declarations.md#declaration)
<span class="alternative">
<span class="syntactic-cat">[union-style-enum-case-clause](Declarations.md#union-style-enum-case-clause)

<span class="syntax-def-name">
union-style-enum-case-clause

<span class="arrow">
→
<span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)~opt~<span class="optional">`indirect`~opt~`case`<span class="syntactic-cat">[union-style-enum-case-list](Declarations.md#union-style-enum-case-list)

<span class="syntax-def-name">
union-style-enum-case-list

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[union-style-enum-case](Declarations.md#union-style-enum-case)
<span class="alternative">
<span class="syntactic-cat">[union-style-enum-case](Declarations.md#union-style-enum-case)`,`<span class="syntactic-cat">[union-style-enum-case-list](Declarations.md#union-style-enum-case-list)

<span class="syntax-def-name">
union-style-enum-case

<span class="arrow">
→
<span class="syntactic-cat">[enum-case-name](Declarations.md#enum-case-name)<span class="optional"><span class="syntactic-cat">[tuple-type](Types.md#tuple-type)~opt~

<span class="syntax-def-name">
enum-name

<span class="arrow">
→
<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)

<span class="syntax-def-name">
enum-case-name

<span class="arrow">
→
<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)

<span class="syntax-def-name">
raw-value-style-enum

<span class="arrow">
→
`enum`<span class="syntactic-cat">[enum-name](Declarations.md#enum-name)<span class="optional"><span class="syntactic-cat">[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)~opt~<span class="syntactic-cat">[type-inheritance-clause](Types.md#type-inheritance-clause)`{`<span class="syntactic-cat">[raw-value-style-enum-members](Declarations.md#raw-value-style-enum-members)`}`

<span class="syntax-def-name">
raw-value-style-enum-members

<span class="arrow">
→
<span class="syntactic-cat">[raw-value-style-enum-member](Declarations.md#raw-value-style-enum-member)<span class="optional"><span class="syntactic-cat">[raw-value-style-enum-members](Declarations.md#raw-value-style-enum-members)~opt~

<span class="syntax-def-name">
raw-value-style-enum-member

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[declaration](Declarations.md#declaration)
<span class="alternative">
<span class="syntactic-cat">[raw-value-style-enum-case-clause](Declarations.md#raw-value-style-enum-case-clause)

<span class="syntax-def-name">
raw-value-style-enum-case-clause

<span class="arrow">
→
<span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)~opt~`case`<span class="syntactic-cat">[raw-value-style-enum-case-list](Declarations.md#raw-value-style-enum-case-list)

<span class="syntax-def-name">
raw-value-style-enum-case-list

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[raw-value-style-enum-case](Declarations.md#raw-value-style-enum-case)
<span class="alternative">
<span class="syntactic-cat">[raw-value-style-enum-case](Declarations.md#raw-value-style-enum-case)`,`<span class="syntactic-cat">[raw-value-style-enum-case-list](Declarations.md#raw-value-style-enum-case-list)

<span class="syntax-def-name">
raw-value-style-enum-case

<span class="arrow">
→
<span class="syntactic-cat">[enum-case-name](Declarations.md#enum-case-name)<span class="optional"><span class="syntactic-cat">[raw-value-assignment](Declarations.md#raw-value-assignment)~opt~

<span class="syntax-def-name">
raw-value-assignment

<span class="arrow">
→
`=`<span class="syntactic-cat">[raw-value-literal](Declarations.md#raw-value-literal)

<span class="syntax-def-name">
raw-value-literal

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[numeric-literal](LexicalStructure.md#numeric-literal)
<span class="alternative">
<span class="syntactic-cat">[static-string-literal](LexicalStructure.md#static-string-literal)
<span class="alternative">
<span class="syntactic-cat">[boolean-literal](LexicalStructure.md#boolean-literal)

Grammar of a structure declaration

<span class="syntax-def-name">
struct-declaration

<span class="arrow">
→
<span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)~opt~<span class="optional"><span class="syntactic-cat">[access-level-modifier](Declarations.md#access-level-modifier)~opt~`struct`<span class="syntactic-cat">[struct-name](Declarations.md#struct-name)<span class="optional"><span class="syntactic-cat">[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)~opt~<span class="optional"><span class="syntactic-cat">[type-inheritance-clause](Types.md#type-inheritance-clause)~opt~<span class="syntactic-cat">[struct-body](Declarations.md#struct-body)

<span class="syntax-def-name">
struct-name

<span class="arrow">
→
<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)

<span class="syntax-def-name">
struct-body

<span class="arrow">
→
`{`<span class="optional"><span class="syntactic-cat">[declarations](Declarations.md#declarations)~opt~`}`

Grammar of a class declaration

<span class="syntax-def-name">
class-declaration

<span class="arrow">
→
<span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)~opt~<span class="optional"><span class="syntactic-cat">[access-level-modifier](Declarations.md#access-level-modifier)~opt~`class`<span class="syntactic-cat">[class-name](Declarations.md#class-name)<span class="optional"><span class="syntactic-cat">[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)~opt~<span class="optional"><span class="syntactic-cat">[type-inheritance-clause](Types.md#type-inheritance-clause)~opt~<span class="syntactic-cat">[class-body](Declarations.md#class-body)

<span class="syntax-def-name">
class-name

<span class="arrow">
→
<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)

<span class="syntax-def-name">
class-body

<span class="arrow">
→
`{`<span class="optional"><span class="syntactic-cat">[declarations](Declarations.md#declarations)~opt~`}`

Grammar of a protocol declaration

<span class="syntax-def-name">
protocol-declaration

<span class="arrow">
→
<span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)~opt~<span class="optional"><span class="syntactic-cat">[access-level-modifier](Declarations.md#access-level-modifier)~opt~`protocol`<span class="syntactic-cat">[protocol-name](Declarations.md#protocol-name)<span class="optional"><span class="syntactic-cat">[type-inheritance-clause](Types.md#type-inheritance-clause)~opt~<span class="syntactic-cat">[protocol-body](Declarations.md#protocol-body)

<span class="syntax-def-name">
protocol-name

<span class="arrow">
→
<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)

<span class="syntax-def-name">
protocol-body

<span class="arrow">
→
`{`<span class="optional"><span class="syntactic-cat">[protocol-member-declarations](Declarations.md#protocol-member-declarations)~opt~`}`

<span class="syntax-def-name">
protocol-member-declaration

<span class="arrow">
→
<span class="syntactic-cat">[protocol-property-declaration](Declarations.md#protocol-property-declaration)

<span class="syntax-def-name">
protocol-member-declaration

<span class="arrow">
→
<span class="syntactic-cat">[protocol-method-declaration](Declarations.md#protocol-method-declaration)

<span class="syntax-def-name">
protocol-member-declaration

<span class="arrow">
→
<span class="syntactic-cat">[protocol-initializer-declaration](Declarations.md#protocol-initializer-declaration)

<span class="syntax-def-name">
protocol-member-declaration

<span class="arrow">
→
<span class="syntactic-cat">[protocol-subscript-declaration](Declarations.md#protocol-subscript-declaration)

<span class="syntax-def-name">
protocol-member-declaration

<span class="arrow">
→
<span class="syntactic-cat">[protocol-associated-type-declaration](Declarations.md#protocol-associated-type-declaration)

<span class="syntax-def-name">
protocol-member-declarations

<span class="arrow">
→
<span class="syntactic-cat">[protocol-member-declaration](Declarations.md#protocol-member-declaration)<span class="optional"><span class="syntactic-cat">[protocol-member-declarations](Declarations.md#protocol-member-declarations)~opt~

Grammar of a protocol property declaration

<span class="syntax-def-name">
protocol-property-declaration

<span class="arrow">
→
<span class="syntactic-cat">[variable-declaration-head](Declarations.md#variable-declaration-head)<span class="syntactic-cat">[variable-name](Declarations.md#variable-name)<span class="syntactic-cat">[type-annotation](Types.md#type-annotation)<span class="syntactic-cat">[getter-setter-keyword-block](Declarations.md#getter-setter-keyword-block)

Grammar of a protocol method declaration

<span class="syntax-def-name">
protocol-method-declaration

<span class="arrow">
→
<span class="syntactic-cat">[function-head](Declarations.md#function-head)<span class="syntactic-cat">[function-name](Declarations.md#function-name)<span class="optional"><span class="syntactic-cat">[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)~opt~<span class="syntactic-cat">[function-signature](Declarations.md#function-signature)

Grammar of a protocol initializer declaration

<span class="syntax-def-name">
protocol-initializer-declaration

<span class="arrow">
→
<span class="syntactic-cat">[initializer-head](Declarations.md#initializer-head)<span class="optional"><span class="syntactic-cat">[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)~opt~<span class="syntactic-cat">[parameter-clause](Declarations.md#parameter-clause)<span class="optional">`throws`~opt~

<span class="syntax-def-name">
protocol-initializer-declaration

<span class="arrow">
→
<span class="syntactic-cat">[initializer-head](Declarations.md#initializer-head)<span class="optional"><span class="syntactic-cat">[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)~opt~<span class="syntactic-cat">[parameter-clause](Declarations.md#parameter-clause)`rethrows`

Grammar of a protocol subscript declaration

<span class="syntax-def-name">
protocol-subscript-declaration

<span class="arrow">
→
<span class="syntactic-cat">[subscript-head](Declarations.md#subscript-head)<span class="syntactic-cat">[subscript-result](Declarations.md#subscript-result)<span class="syntactic-cat">[getter-setter-keyword-block](Declarations.md#getter-setter-keyword-block)

Grammar of a protocol associated type declaration

<span class="syntax-def-name">
protocol-associated-type-declaration

<span class="arrow">
→
<span class="syntactic-cat">[typealias-head](Declarations.md#typealias-head)<span class="optional"><span class="syntactic-cat">[type-inheritance-clause](Types.md#type-inheritance-clause)~opt~<span class="optional"><span class="syntactic-cat">[typealias-assignment](Declarations.md#typealias-assignment)~opt~

Grammar of an initializer declaration

<span class="syntax-def-name">
initializer-declaration

<span class="arrow">
→
<span class="syntactic-cat">[initializer-head](Declarations.md#initializer-head)<span class="optional"><span class="syntactic-cat">[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)~opt~<span class="syntactic-cat">[parameter-clause](Declarations.md#parameter-clause)<span class="optional">`throws`~opt~<span class="syntactic-cat">[initializer-body](Declarations.md#initializer-body)

<span class="syntax-def-name">
initializer-declaration

<span class="arrow">
→
<span class="syntactic-cat">[initializer-head](Declarations.md#initializer-head)<span class="optional"><span class="syntactic-cat">[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)~opt~<span class="syntactic-cat">[parameter-clause](Declarations.md#parameter-clause)`rethrows`<span class="syntactic-cat">[initializer-body](Declarations.md#initializer-body)

<span class="syntax-def-name">
initializer-head

<span class="arrow">
→
<span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)~opt~<span class="optional"><span class="syntactic-cat">[declaration-modifiers](Declarations.md#declaration-modifiers)~opt~`init`

<span class="syntax-def-name">
initializer-head

<span class="arrow">
→
<span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)~opt~<span class="optional"><span class="syntactic-cat">[declaration-modifiers](Declarations.md#declaration-modifiers)~opt~`init``?`

<span class="syntax-def-name">
initializer-head

<span class="arrow">
→
<span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)~opt~<span class="optional"><span class="syntactic-cat">[declaration-modifiers](Declarations.md#declaration-modifiers)~opt~`init``!`

<span class="syntax-def-name">
initializer-body

<span class="arrow">
→
<span class="syntactic-cat">[code-block](Declarations.md#code-block)

Grammar of a deinitializer declaration

<span class="syntax-def-name">
deinitializer-declaration

<span class="arrow">
→
<span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)~opt~`deinit`<span class="syntactic-cat">[code-block](Declarations.md#code-block)

Grammar of an extension declaration

<span class="syntax-def-name">
extension-declaration

<span class="arrow">
→
<span class="optional"><span class="syntactic-cat">[access-level-modifier](Declarations.md#access-level-modifier)~opt~`extension`<span class="syntactic-cat">[type-identifier](Types.md#type-identifier)<span class="optional"><span class="syntactic-cat">[type-inheritance-clause](Types.md#type-inheritance-clause)~opt~<span class="syntactic-cat">[extension-body](Declarations.md#extension-body)

<span class="syntax-def-name">
extension-body

<span class="arrow">
→
`{`<span class="optional"><span class="syntactic-cat">[declarations](Declarations.md#declarations)~opt~`}`

Grammar of a subscript declaration

<span class="syntax-def-name">
subscript-declaration

<span class="arrow">
→
<span class="syntactic-cat">[subscript-head](Declarations.md#subscript-head)<span class="syntactic-cat">[subscript-result](Declarations.md#subscript-result)<span class="syntactic-cat">[code-block](Declarations.md#code-block)

<span class="syntax-def-name">
subscript-declaration

<span class="arrow">
→
<span class="syntactic-cat">[subscript-head](Declarations.md#subscript-head)<span class="syntactic-cat">[subscript-result](Declarations.md#subscript-result)<span class="syntactic-cat">[getter-setter-block](Declarations.md#getter-setter-block)

<span class="syntax-def-name">
subscript-declaration

<span class="arrow">
→
<span class="syntactic-cat">[subscript-head](Declarations.md#subscript-head)<span class="syntactic-cat">[subscript-result](Declarations.md#subscript-result)<span class="syntactic-cat">[getter-setter-keyword-block](Declarations.md#getter-setter-keyword-block)

<span class="syntax-def-name">
subscript-head

<span class="arrow">
→
<span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)~opt~<span class="optional"><span class="syntactic-cat">[declaration-modifiers](Declarations.md#declaration-modifiers)~opt~`subscript`<span class="syntactic-cat">[parameter-clause](Declarations.md#parameter-clause)

<span class="syntax-def-name">
subscript-result

<span class="arrow">
→
`->`<span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)~opt~<span class="syntactic-cat">[type](Types.md#type)

Grammar of an operator declaration

<span class="syntax-def-name">
operator-declaration

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[prefix-operator-declaration](Declarations.md#prefix-operator-declaration)
<span class="alternative">
<span class="syntactic-cat">[postfix-operator-declaration](Declarations.md#postfix-operator-declaration)
<span class="alternative">
<span class="syntactic-cat">[infix-operator-declaration](Declarations.md#infix-operator-declaration)

<span class="syntax-def-name">
prefix-operator-declaration

<span class="arrow">
→
`prefix``operator`<span class="syntactic-cat">[operator](LexicalStructure.md#operator)`{``}`

<span class="syntax-def-name">
postfix-operator-declaration

<span class="arrow">
→
`postfix``operator`<span class="syntactic-cat">[operator](LexicalStructure.md#operator)`{``}`

<span class="syntax-def-name">
infix-operator-declaration

<span class="arrow">
→
`infix``operator`<span class="syntactic-cat">[operator](LexicalStructure.md#operator)`{`<span class="optional"><span class="syntactic-cat">[infix-operator-attributes](Declarations.md#infix-operator-attributes)~opt~`}`

<span class="syntax-def-name">
infix-operator-attributes

<span class="arrow">
→
<span class="optional"><span class="syntactic-cat">[precedence-clause](Declarations.md#precedence-clause)~opt~<span class="optional"><span class="syntactic-cat">[associativity-clause](Declarations.md#associativity-clause)~opt~

<span class="syntax-def-name">
precedence-clause

<span class="arrow">
→
`precedence`<span class="syntactic-cat">[precedence-level](Declarations.md#precedence-level)

<span class="syntax-def-name">
precedence-level

<span class="arrow">
→
<span class="text-description">A decimal integer between 0 and 255, inclusive

<span class="syntax-def-name">
associativity-clause

<span class="arrow">
→
`associativity`<span class="syntactic-cat">[associativity](Declarations.md#associativity)

<span class="syntax-def-name">
associativity

<span class="arrow">
→
<span class="alternative">
`left`
<span class="alternative">
`right`
<span class="alternative">
`none`

Grammar of a declaration modifier

<span class="syntax-def-name">
declaration-modifier

<span class="arrow">
→
<span class="alternative">
`class`
<span class="alternative">
`convenience`
<span class="alternative">
`dynamic`
<span class="alternative">
`final`
<span class="alternative">
`infix`
<span class="alternative">
`lazy`
<span class="alternative">
`mutating`
<span class="alternative">
`nonmutating`
<span class="alternative">
`optional`
<span class="alternative">
`override`
<span class="alternative">
`postfix`
<span class="alternative">
`prefix`
<span class="alternative">
`required`
<span class="alternative">
`static`
<span class="alternative">
`unowned`
<span class="alternative">
`unowned``(``safe``)`
<span class="alternative">
`unowned``(``unsafe``)`
<span class="alternative">
`weak`

<span class="syntax-def-name">
declaration-modifier

<span class="arrow">
→
<span class="syntactic-cat">[access-level-modifier](Declarations.md#access-level-modifier)

<span class="syntax-def-name">
declaration-modifiers

<span class="arrow">
→
<span class="syntactic-cat">[declaration-modifier](Declarations.md#declaration-modifier)<span class="optional"><span class="syntactic-cat">[declaration-modifiers](Declarations.md#declaration-modifiers)~opt~

<span class="syntax-def-name">
access-level-modifier

<span class="arrow">
→
<span class="alternative">
`internal`
<span class="alternative">
`internal``(``set``)`

<span class="syntax-def-name">
access-level-modifier

<span class="arrow">
→
<span class="alternative">
`private`
<span class="alternative">
`private``(``set``)`

<span class="syntax-def-name">
access-level-modifier

<span class="arrow">
→
<span class="alternative">
`public`
<span class="alternative">
`public``(``set``)`

### Patterns

Grammar of a pattern

<span class="syntax-def-name">
pattern

<span class="arrow">
→
<span class="syntactic-cat">[wildcard-pattern](Patterns.md#wildcard-pattern)<span class="optional"><span class="syntactic-cat">[type-annotation](Types.md#type-annotation)~opt~

<span class="syntax-def-name">
pattern

<span class="arrow">
→
<span class="syntactic-cat">[identifier-pattern](Patterns.md#identifier-pattern)<span class="optional"><span class="syntactic-cat">[type-annotation](Types.md#type-annotation)~opt~

<span class="syntax-def-name">
pattern

<span class="arrow">
→
<span class="syntactic-cat">[value-binding-pattern](Patterns.md#value-binding-pattern)

<span class="syntax-def-name">
pattern

<span class="arrow">
→
<span class="syntactic-cat">[tuple-pattern](Patterns.md#tuple-pattern)<span class="optional"><span class="syntactic-cat">[type-annotation](Types.md#type-annotation)~opt~

<span class="syntax-def-name">
pattern

<span class="arrow">
→
<span class="syntactic-cat">[enum-case-pattern](Patterns.md#enum-case-pattern)

<span class="syntax-def-name">
pattern

<span class="arrow">
→
<span class="syntactic-cat">[optional-pattern](Patterns.md#optional-pattern)

<span class="syntax-def-name">
pattern

<span class="arrow">
→
<span class="syntactic-cat">[type-casting-pattern](Patterns.md#type-casting-pattern)

<span class="syntax-def-name">
pattern

<span class="arrow">
→
<span class="syntactic-cat">[expression-pattern](Patterns.md#expression-pattern)

Grammar of a wildcard pattern

<span class="syntax-def-name">
wildcard-pattern

<span class="arrow">
→
`_`

Grammar of an identifier pattern

<span class="syntax-def-name">
identifier-pattern

<span class="arrow">
→
<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)

Grammar of a value-binding pattern

<span class="syntax-def-name">
value-binding-pattern

<span class="arrow">
→
`let`<span class="syntactic-cat">[pattern](Patterns.md#pattern)

Grammar of a tuple pattern

<span class="syntax-def-name">
tuple-pattern

<span class="arrow">
→
`(`<span class="optional"><span class="syntactic-cat">[tuple-pattern-element-list](Patterns.md#tuple-pattern-element-list)~opt~`)`

<span class="syntax-def-name">
tuple-pattern-element-list

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[tuple-pattern-element](Patterns.md#tuple-pattern-element)
<span class="alternative">
<span class="syntactic-cat">[tuple-pattern-element](Patterns.md#tuple-pattern-element)`,`<span class="syntactic-cat">[tuple-pattern-element-list](Patterns.md#tuple-pattern-element-list)

<span class="syntax-def-name">
tuple-pattern-element

<span class="arrow">
→
<span class="syntactic-cat">[pattern](Patterns.md#pattern)

Grammar of an enumeration case pattern

<span class="syntax-def-name">
enum-case-pattern

<span class="arrow">
→
<span class="optional"><span class="syntactic-cat">[type-identifier](Types.md#type-identifier)~opt~`.`<span class="syntactic-cat">[enum-case-name](Declarations.md#enum-case-name)<span class="optional"><span class="syntactic-cat">[tuple-pattern](Patterns.md#tuple-pattern)~opt~

Grammar of an optional pattern

<span class="syntax-def-name">
optional-pattern

<span class="arrow">
→
<span class="syntactic-cat">[identifier-pattern](Patterns.md#identifier-pattern)`?`

Grammar of a type casting pattern

<span class="syntax-def-name">
type-casting-pattern

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[is-pattern](Patterns.md#is-pattern)
<span class="alternative">
<span class="syntactic-cat">[as-pattern](Patterns.md#as-pattern)

<span class="syntax-def-name">
is-pattern

<span class="arrow">
→
`is`<span class="syntactic-cat">[type](Types.md#type)

<span class="syntax-def-name">
as-pattern

<span class="arrow">
→
<span class="syntactic-cat">[pattern](Patterns.md#pattern)`as`<span class="syntactic-cat">[type](Types.md#type)

Grammar of an expression pattern

<span class="syntax-def-name">
expression-pattern

<span class="arrow">
→
<span class="syntactic-cat">[expression](Expressions.md#expression)

### Attributes

Grammar of an attribute

<span class="syntax-def-name">
attribute

<span class="arrow">
→
`@`<span class="syntactic-cat">[attribute-name](Attributes.md#attribute-name)<span class="optional"><span class="syntactic-cat">[attribute-argument-clause](Attributes.md#attribute-argument-clause)~opt~

<span class="syntax-def-name">
attribute-name

<span class="arrow">
→
<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)

<span class="syntax-def-name">
attribute-argument-clause

<span class="arrow">
→
`(`<span class="optional"><span class="syntactic-cat">[balanced-tokens](Attributes.md#balanced-tokens)~opt~`)`

<span class="syntax-def-name">
attributes

<span class="arrow">
→
<span class="syntactic-cat">[attribute](Attributes.md#attribute)<span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)~opt~

<span class="syntax-def-name">
balanced-tokens

<span class="arrow">
→
<span class="syntactic-cat">[balanced-token](Attributes.md#balanced-token)<span class="optional"><span class="syntactic-cat">[balanced-tokens](Attributes.md#balanced-tokens)~opt~

<span class="syntax-def-name">
balanced-token

<span class="arrow">
→
`(`<span class="optional"><span class="syntactic-cat">[balanced-tokens](Attributes.md#balanced-tokens)~opt~`)`

<span class="syntax-def-name">
balanced-token

<span class="arrow">
→
`[`<span class="optional"><span class="syntactic-cat">[balanced-tokens](Attributes.md#balanced-tokens)~opt~`]`

<span class="syntax-def-name">
balanced-token

<span class="arrow">
→
`{`<span class="optional"><span class="syntactic-cat">[balanced-tokens](Attributes.md#balanced-tokens)~opt~`}`

<span class="syntax-def-name">
balanced-token

<span class="arrow">
→
<span class="text-description">Any identifier, keyword, literal, or operator

<span class="syntax-def-name">
balanced-token

<span class="arrow">
→
<span class="text-description">Any punctuation except `(`, `)`, `[`, `]`, `{`, or `}`

### Expressions

Grammar of an expression

<span class="syntax-def-name">
expression

<span class="arrow">
→
<span class="optional"><span class="syntactic-cat">[try-operator](Expressions.md#try-operator)~opt~<span class="syntactic-cat">[prefix-expression](Expressions.md#prefix-expression)<span class="optional"><span class="syntactic-cat">[binary-expressions](Expressions.md#binary-expressions)~opt~

<span class="syntax-def-name">
expression-list

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[expression](Expressions.md#expression)
<span class="alternative">
<span class="syntactic-cat">[expression](Expressions.md#expression)`,`<span class="syntactic-cat">[expression-list](Expressions.md#expression-list)

Grammar of a prefix expression

<span class="syntax-def-name">
prefix-expression

<span class="arrow">
→
<span class="optional"><span class="syntactic-cat">[prefix-operator](LexicalStructure.md#prefix-operator)~opt~<span class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)

<span class="syntax-def-name">
prefix-expression

<span class="arrow">
→
<span class="syntactic-cat">[in-out-expression](Expressions.md#in-out-expression)

<span class="syntax-def-name">
in-out-expression

<span class="arrow">
→
`&`<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)

Grammar of a try expression

<span class="syntax-def-name">
try-operator

<span class="arrow">
→
<span class="alternative">
`try`
<span class="alternative">
`try``?`
<span class="alternative">
`try``!`

Grammar of a binary expression

<span class="syntax-def-name">
binary-expression

<span class="arrow">
→
<span class="syntactic-cat">[binary-operator](LexicalStructure.md#binary-operator)<span class="syntactic-cat">[prefix-expression](Expressions.md#prefix-expression)

<span class="syntax-def-name">
binary-expression

<span class="arrow">
→
<span class="syntactic-cat">[assignment-operator](Expressions.md#assignment-operator)<span class="optional"><span class="syntactic-cat">[try-operator](Expressions.md#try-operator)~opt~<span class="syntactic-cat">[prefix-expression](Expressions.md#prefix-expression)

<span class="syntax-def-name">
binary-expression

<span class="arrow">
→
<span class="syntactic-cat">[conditional-operator](Expressions.md#conditional-operator)<span class="optional"><span class="syntactic-cat">[try-operator](Expressions.md#try-operator)~opt~<span class="syntactic-cat">[prefix-expression](Expressions.md#prefix-expression)

<span class="syntax-def-name">
binary-expression

<span class="arrow">
→
<span class="syntactic-cat">[type-casting-operator](Expressions.md#type-casting-operator)

<span class="syntax-def-name">
binary-expressions

<span class="arrow">
→
<span class="syntactic-cat">[binary-expression](Expressions.md#binary-expression)<span class="optional"><span class="syntactic-cat">[binary-expressions](Expressions.md#binary-expressions)~opt~

Grammar of an assignment operator

<span class="syntax-def-name">
assignment-operator

<span class="arrow">
→
`=`

Grammar of a conditional operator

<span class="syntax-def-name">
conditional-operator

<span class="arrow">
→
`?`<span class="optional"><span class="syntactic-cat">[try-operator](Expressions.md#try-operator)~opt~<span class="syntactic-cat">[expression](Expressions.md#expression)`:`

Grammar of a type-casting operator

<span class="syntax-def-name">
type-casting-operator

<span class="arrow">
→
`is`<span class="syntactic-cat">[type](Types.md#type)

<span class="syntax-def-name">
type-casting-operator

<span class="arrow">
→
`as`<span class="syntactic-cat">[type](Types.md#type)

<span class="syntax-def-name">
type-casting-operator

<span class="arrow">
→
`as``?`<span class="syntactic-cat">[type](Types.md#type)

<span class="syntax-def-name">
type-casting-operator

<span class="arrow">
→
`as``!`<span class="syntactic-cat">[type](Types.md#type)

Grammar of a primary expression

<span class="syntax-def-name">
primary-expression

<span class="arrow">
→
<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)<span class="optional"><span class="syntactic-cat">[generic-argument-clause](GenericParametersAndArguments.md#generic-argument-clause)~opt~

<span class="syntax-def-name">
primary-expression

<span class="arrow">
→
<span class="syntactic-cat">[literal-expression](Expressions.md#literal-expression)

<span class="syntax-def-name">
primary-expression

<span class="arrow">
→
<span class="syntactic-cat">[self-expression](Expressions.md#self-expression)

<span class="syntax-def-name">
primary-expression

<span class="arrow">
→
<span class="syntactic-cat">[superclass-expression](Expressions.md#superclass-expression)

<span class="syntax-def-name">
primary-expression

<span class="arrow">
→
<span class="syntactic-cat">[closure-expression](Expressions.md#closure-expression)

<span class="syntax-def-name">
primary-expression

<span class="arrow">
→
<span class="syntactic-cat">[parenthesized-expression](Expressions.md#parenthesized-expression)

<span class="syntax-def-name">
primary-expression

<span class="arrow">
→
<span class="syntactic-cat">[implicit-member-expression](Expressions.md#implicit-member-expression)

<span class="syntax-def-name">
primary-expression

<span class="arrow">
→
<span class="syntactic-cat">[wildcard-expression](Expressions.md#wildcard-expression)

Grammar of a literal expression

<span class="syntax-def-name">
literal-expression

<span class="arrow">
→
<span class="syntactic-cat">[literal](LexicalStructure.md#literal)

<span class="syntax-def-name">
literal-expression

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[array-literal](Expressions.md#array-literal)
<span class="alternative">
<span class="syntactic-cat">[dictionary-literal](Expressions.md#dictionary-literal)

<span class="syntax-def-name">
literal-expression

<span class="arrow">
→
<span class="alternative">
`__FILE__`
<span class="alternative">
`__LINE__`
<span class="alternative">
`__COLUMN__`
<span class="alternative">
`__FUNCTION__`

<span class="syntax-def-name">
array-literal

<span class="arrow">
→
`[`<span class="optional"><span class="syntactic-cat">[array-literal-items](Expressions.md#array-literal-items)~opt~`]`

<span class="syntax-def-name">
array-literal-items

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[array-literal-item](Expressions.md#array-literal-item)<span class="optional">`,`~opt~
<span class="alternative">
<span class="syntactic-cat">[array-literal-item](Expressions.md#array-literal-item)`,`<span class="syntactic-cat">[array-literal-items](Expressions.md#array-literal-items)

<span class="syntax-def-name">
array-literal-item

<span class="arrow">
→
<span class="syntactic-cat">[expression](Expressions.md#expression)

<span class="syntax-def-name">
dictionary-literal

<span class="arrow">
→
<span class="alternative">
`[`<span class="syntactic-cat">[dictionary-literal-items](Expressions.md#dictionary-literal-items)`]`
<span class="alternative">
`[``:``]`

<span class="syntax-def-name">
dictionary-literal-items

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[dictionary-literal-item](Expressions.md#dictionary-literal-item)<span class="optional">`,`~opt~
<span class="alternative">
<span class="syntactic-cat">[dictionary-literal-item](Expressions.md#dictionary-literal-item)`,`<span class="syntactic-cat">[dictionary-literal-items](Expressions.md#dictionary-literal-items)

<span class="syntax-def-name">
dictionary-literal-item

<span class="arrow">
→
<span class="syntactic-cat">[expression](Expressions.md#expression)`:`<span class="syntactic-cat">[expression](Expressions.md#expression)

Grammar of a self expression

<span class="syntax-def-name">
self-expression

<span class="arrow">
→
<span class="alternative">
`self`
<span class="alternative">
<span class="syntactic-cat">[self-method-expression](Expressions.md#self-method-expression)
<span class="alternative">
<span class="syntactic-cat">[self-subscript-expression](Expressions.md#self-subscript-expression)
<span class="alternative">
<span class="syntactic-cat">[self-initializer-expression](Expressions.md#self-initializer-expression)

<span class="syntax-def-name">
self-method-expression

<span class="arrow">
→
`self``.`<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)

<span class="syntax-def-name">
self-subscript-expression

<span class="arrow">
→
`self``[`<span class="syntactic-cat">[expression-list](Expressions.md#expression-list)`]`

<span class="syntax-def-name">
self-initializer-expression

<span class="arrow">
→
`self``.``init`

Grammar of a superclass expression

<span class="syntax-def-name">
superclass-expression

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[superclass-method-expression](Expressions.md#superclass-method-expression)
<span class="alternative">
<span class="syntactic-cat">[superclass-subscript-expression](Expressions.md#superclass-subscript-expression)
<span class="alternative">
<span class="syntactic-cat">[superclass-initializer-expression](Expressions.md#superclass-initializer-expression)

<span class="syntax-def-name">
superclass-method-expression

<span class="arrow">
→
`super``.`<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)

<span class="syntax-def-name">
superclass-subscript-expression

<span class="arrow">
→
`super``[`<span class="syntactic-cat">[expression-list](Expressions.md#expression-list)`]`

<span class="syntax-def-name">
superclass-initializer-expression

<span class="arrow">
→
`super``.``init`

Grammar of a closure expression

<span class="syntax-def-name">
closure-expression

<span class="arrow">
→
`{`<span class="optional"><span class="syntactic-cat">[closure-signature](Expressions.md#closure-signature)~opt~<span class="syntactic-cat">[statements](Statements.md#statements)`}`

<span class="syntax-def-name">
closure-signature

<span class="arrow">
→
<span class="syntactic-cat">[parameter-clause](Declarations.md#parameter-clause)<span class="optional"><span class="syntactic-cat">[function-result](Declarations.md#function-result)~opt~`in`

<span class="syntax-def-name">
closure-signature

<span class="arrow">
→
<span class="syntactic-cat">[identifier-list](LexicalStructure.md#identifier-list)<span class="optional"><span class="syntactic-cat">[function-result](Declarations.md#function-result)~opt~`in`

<span class="syntax-def-name">
closure-signature

<span class="arrow">
→
<span class="syntactic-cat">[capture-list](Expressions.md#capture-list)<span class="syntactic-cat">[parameter-clause](Declarations.md#parameter-clause)<span class="optional"><span class="syntactic-cat">[function-result](Declarations.md#function-result)~opt~`in`

<span class="syntax-def-name">
closure-signature

<span class="arrow">
→
<span class="syntactic-cat">[capture-list](Expressions.md#capture-list)<span class="syntactic-cat">[identifier-list](LexicalStructure.md#identifier-list)<span class="optional"><span class="syntactic-cat">[function-result](Declarations.md#function-result)~opt~`in`

<span class="syntax-def-name">
closure-signature

<span class="arrow">
→
<span class="syntactic-cat">[capture-list](Expressions.md#capture-list)`in`

<span class="syntax-def-name">
capture-list

<span class="arrow">
→
`[`<span class="syntactic-cat">[capture-list-items](Expressions.md#capture-list-items)`]`

<span class="syntax-def-name">
capture-list-items

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[capture-list-item](Expressions.md#capture-list-item)
<span class="alternative">
<span class="syntactic-cat">[capture-list-item](Expressions.md#capture-list-item)`,`<span class="syntactic-cat">[capture-list-items](Expressions.md#capture-list-items)

<span class="syntax-def-name">
capture-list-item

<span class="arrow">
→
<span class="optional"><span class="syntactic-cat">[capture-specifier](Expressions.md#capture-specifier)~opt~<span class="syntactic-cat">[expression](Expressions.md#expression)

<span class="syntax-def-name">
capture-specifier

<span class="arrow">
→
<span class="alternative">
`weak`
<span class="alternative">
`unowned`
<span class="alternative">
`unowned(safe)`
<span class="alternative">
`unowned(unsafe)`

Grammar of a implicit member expression

<span class="syntax-def-name">
implicit-member-expression

<span class="arrow">
→
`.`<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)

Grammar of a parenthesized expression

<span class="syntax-def-name">
parenthesized-expression

<span class="arrow">
→
`(`<span class="optional"><span class="syntactic-cat">[expression-element-list](Expressions.md#expression-element-list)~opt~`)`

<span class="syntax-def-name">
expression-element-list

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[expression-element](Expressions.md#expression-element)
<span class="alternative">
<span class="syntactic-cat">[expression-element](Expressions.md#expression-element)`,`<span class="syntactic-cat">[expression-element-list](Expressions.md#expression-element-list)

<span class="syntax-def-name">
expression-element

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[expression](Expressions.md#expression)
<span class="alternative">
<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)`:`<span class="syntactic-cat">[expression](Expressions.md#expression)

Grammar of a wildcard expression

<span class="syntax-def-name">
wildcard-expression

<span class="arrow">
→
`_`

Grammar of a postfix expression

<span class="syntax-def-name">
postfix-expression

<span class="arrow">
→
<span class="syntactic-cat">[primary-expression](Expressions.md#primary-expression)

<span class="syntax-def-name">
postfix-expression

<span class="arrow">
→
<span class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)<span class="syntactic-cat">[postfix-operator](LexicalStructure.md#postfix-operator)

<span class="syntax-def-name">
postfix-expression

<span class="arrow">
→
<span class="syntactic-cat">[function-call-expression](Expressions.md#function-call-expression)

<span class="syntax-def-name">
postfix-expression

<span class="arrow">
→
<span class="syntactic-cat">[initializer-expression](Expressions.md#initializer-expression)

<span class="syntax-def-name">
postfix-expression

<span class="arrow">
→
<span class="syntactic-cat">[explicit-member-expression](Expressions.md#explicit-member-expression)

<span class="syntax-def-name">
postfix-expression

<span class="arrow">
→
<span class="syntactic-cat">[postfix-self-expression](Expressions.md#postfix-self-expression)

<span class="syntax-def-name">
postfix-expression

<span class="arrow">
→
<span class="syntactic-cat">[dynamic-type-expression](Expressions.md#dynamic-type-expression)

<span class="syntax-def-name">
postfix-expression

<span class="arrow">
→
<span class="syntactic-cat">[subscript-expression](Expressions.md#subscript-expression)

<span class="syntax-def-name">
postfix-expression

<span class="arrow">
→
<span class="syntactic-cat">[forced-value-expression](Expressions.md#forced-value-expression)

<span class="syntax-def-name">
postfix-expression

<span class="arrow">
→
<span class="syntactic-cat">[optional-chaining-expression](Expressions.md#optional-chaining-expression)

Grammar of a function call expression

<span class="syntax-def-name">
function-call-expression

<span class="arrow">
→
<span class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)<span class="syntactic-cat">[parenthesized-expression](Expressions.md#parenthesized-expression)

<span class="syntax-def-name">
function-call-expression

<span class="arrow">
→
<span class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)<span class="optional"><span class="syntactic-cat">[parenthesized-expression](Expressions.md#parenthesized-expression)~opt~<span class="syntactic-cat">[trailing-closure](Expressions.md#trailing-closure)

<span class="syntax-def-name">
trailing-closure

<span class="arrow">
→
<span class="syntactic-cat">[closure-expression](Expressions.md#closure-expression)

Grammar of an initializer expression

<span class="syntax-def-name">
initializer-expression

<span class="arrow">
→
<span class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)`.``init`

Grammar of an explicit member expression

<span class="syntax-def-name">
explicit-member-expression

<span class="arrow">
→
<span class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)`.`<span class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)

<span class="syntax-def-name">
explicit-member-expression

<span class="arrow">
→
<span class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)`.`<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)<span class="optional"><span class="syntactic-cat">[generic-argument-clause](GenericParametersAndArguments.md#generic-argument-clause)~opt~

Grammar of a self expression

<span class="syntax-def-name">
postfix-self-expression

<span class="arrow">
→
<span class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)`.``self`

Grammar of a dynamic type expression

<span class="syntax-def-name">
dynamic-type-expression

<span class="arrow">
→
<span class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)`.``dynamicType`

Grammar of a subscript expression

<span class="syntax-def-name">
subscript-expression

<span class="arrow">
→
<span class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)`[`<span class="syntactic-cat">[expression-list](Expressions.md#expression-list)`]`

Grammar of a forced-value expression

<span class="syntax-def-name">
forced-value-expression

<span class="arrow">
→
<span class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)`!`

Grammar of an optional-chaining expression

<span class="syntax-def-name">
optional-chaining-expression

<span class="arrow">
→
<span class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)`?`

### Lexical Structure

Grammar of an identifier

<span class="syntax-def-name">
identifier

<span class="arrow">
→
<span class="syntactic-cat">[identifier-head](LexicalStructure.md#identifier-head)<span class="optional"><span class="syntactic-cat">[identifier-characters](LexicalStructure.md#identifier-characters)~opt~

<span class="syntax-def-name">
identifier

<span class="arrow">
→
`` ` ``<span class="syntactic-cat">[identifier-head](LexicalStructure.md#identifier-head)<span class="optional"><span class="syntactic-cat">[identifier-characters](LexicalStructure.md#identifier-characters)~opt~`` ` ``

<span class="syntax-def-name">
identifier

<span class="arrow">
→
<span class="syntactic-cat">[implicit-parameter-name](LexicalStructure.md#implicit-parameter-name)

<span class="syntax-def-name">
identifier-list

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)
<span class="alternative">
<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)`,`<span class="syntactic-cat">[identifier-list](LexicalStructure.md#identifier-list)

<span class="syntax-def-name">
identifier-head

<span class="arrow">
→
<span class="text-description">Upper- or lowercase letter A through Z

<span class="syntax-def-name">
identifier-head

<span class="arrow">
→
`_`

<span class="syntax-def-name">
identifier-head

<span class="arrow">
→
<span class="text-description">U+00A8, U+00AA, U+00AD, U+00AF, U+00B2–U+00B5, or U+00B7–U+00BA

<span class="syntax-def-name">
identifier-head

<span class="arrow">
→
<span class="text-description">U+00BC–U+00BE, U+00C0–U+00D6, U+00D8–U+00F6, or U+00F8–U+00FF

<span class="syntax-def-name">
identifier-head

<span class="arrow">
→
<span class="text-description">U+0100–U+02FF, U+0370–U+167F, U+1681–U+180D, or U+180F–U+1DBF

<span class="syntax-def-name">
identifier-head

<span class="arrow">
→
<span class="text-description">U+1E00–U+1FFF

<span class="syntax-def-name">
identifier-head

<span class="arrow">
→
<span class="text-description">U+200B–U+200D, U+202A–U+202E, U+203F–U+2040, U+2054, or U+2060–U+206F

<span class="syntax-def-name">
identifier-head

<span class="arrow">
→
<span class="text-description">U+2070–U+20CF, U+2100–U+218F, U+2460–U+24FF, or U+2776–U+2793

<span class="syntax-def-name">
identifier-head

<span class="arrow">
→
<span class="text-description">U+2C00–U+2DFF or U+2E80–U+2FFF

<span class="syntax-def-name">
identifier-head

<span class="arrow">
→
<span class="text-description">U+3004–U+3007, U+3021–U+302F, U+3031–U+303F, or U+3040–U+D7FF

<span class="syntax-def-name">
identifier-head

<span class="arrow">
→
<span class="text-description">U+F900–U+FD3D, U+FD40–U+FDCF, U+FDF0–U+FE1F, or U+FE30–U+FE44

<span class="syntax-def-name">
identifier-head

<span class="arrow">
→
<span class="text-description">U+FE47–U+FFFD

<span class="syntax-def-name">
identifier-head

<span class="arrow">
→
<span class="text-description">U+10000–U+1FFFD, U+20000–U+2FFFD, U+30000–U+3FFFD, or U+40000–U+4FFFD

<span class="syntax-def-name">
identifier-head

<span class="arrow">
→
<span class="text-description">U+50000–U+5FFFD, U+60000–U+6FFFD, U+70000–U+7FFFD, or U+80000–U+8FFFD

<span class="syntax-def-name">
identifier-head

<span class="arrow">
→
<span class="text-description">U+90000–U+9FFFD, U+A0000–U+AFFFD, U+B0000–U+BFFFD, or U+C0000–U+CFFFD

<span class="syntax-def-name">
identifier-head

<span class="arrow">
→
<span class="text-description">U+D0000–U+DFFFD or U+E0000–U+EFFFD

<span class="syntax-def-name">
identifier-character

<span class="arrow">
→
<span class="text-description">Digit 0 through 9

<span class="syntax-def-name">
identifier-character

<span class="arrow">
→
<span class="text-description">U+0300–U+036F, U+1DC0–U+1DFF, U+20D0–U+20FF, or U+FE20–U+FE2F

<span class="syntax-def-name">
identifier-character

<span class="arrow">
→
<span class="syntactic-cat">[identifier-head](LexicalStructure.md#identifier-head)

<span class="syntax-def-name">
identifier-characters

<span class="arrow">
→
<span class="syntactic-cat">[identifier-character](LexicalStructure.md#identifier-character)<span class="optional"><span class="syntactic-cat">[identifier-characters](LexicalStructure.md#identifier-characters)~opt~

<span class="syntax-def-name">
implicit-parameter-name

<span class="arrow">
→
`$`<span class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)

Grammar of a literal

<span class="syntax-def-name">
literal

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[numeric-literal](LexicalStructure.md#numeric-literal)
<span class="alternative">
<span class="syntactic-cat">[string-literal](LexicalStructure.md#string-literal)
<span class="alternative">
<span class="syntactic-cat">[boolean-literal](LexicalStructure.md#boolean-literal)
<span class="alternative">
<span class="syntactic-cat">[nil-literal](LexicalStructure.md#nil-literal)

<span class="syntax-def-name">
numeric-literal

<span class="arrow">
→
<span class="alternative">
<span class="optional">`-`~opt~<span class="syntactic-cat">[integer-literal](LexicalStructure.md#integer-literal)
<span class="alternative">
<span class="optional">`-`~opt~<span class="syntactic-cat">[floating-point-literal](LexicalStructure.md#floating-point-literal)

<span class="syntax-def-name">
boolean-literal

<span class="arrow">
→
<span class="alternative">
`true`
<span class="alternative">
`false`

<span class="syntax-def-name">
nil-literal

<span class="arrow">
→
`nil`

Grammar of an integer literal

<span class="syntax-def-name">
integer-literal

<span class="arrow">
→
<span class="syntactic-cat">[binary-literal](LexicalStructure.md#binary-literal)

<span class="syntax-def-name">
integer-literal

<span class="arrow">
→
<span class="syntactic-cat">[octal-literal](LexicalStructure.md#octal-literal)

<span class="syntax-def-name">
integer-literal

<span class="arrow">
→
<span class="syntactic-cat">[decimal-literal](LexicalStructure.md#decimal-literal)

<span class="syntax-def-name">
integer-literal

<span class="arrow">
→
<span class="syntactic-cat">[hexadecimal-literal](LexicalStructure.md#hexadecimal-literal)

<span class="syntax-def-name">
binary-literal

<span class="arrow">
→
`0b`<span class="syntactic-cat">[binary-digit](LexicalStructure.md#binary-digit)<span class="optional"><span class="syntactic-cat">[binary-literal-characters](LexicalStructure.md#binary-literal-characters)~opt~

<span class="syntax-def-name">
binary-digit

<span class="arrow">
→
<span class="text-description">Digit 0 or 1

<span class="syntax-def-name">
binary-literal-character

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[binary-digit](LexicalStructure.md#binary-digit)
<span class="alternative">
`_`

<span class="syntax-def-name">
binary-literal-characters

<span class="arrow">
→
<span class="syntactic-cat">[binary-literal-character](LexicalStructure.md#binary-literal-character)<span class="optional"><span class="syntactic-cat">[binary-literal-characters](LexicalStructure.md#binary-literal-characters)~opt~

<span class="syntax-def-name">
octal-literal

<span class="arrow">
→
`0o`<span class="syntactic-cat">[octal-digit](LexicalStructure.md#octal-digit)<span class="optional"><span class="syntactic-cat">[octal-literal-characters](LexicalStructure.md#octal-literal-characters)~opt~

<span class="syntax-def-name">
octal-digit

<span class="arrow">
→
<span class="text-description">Digit 0 through 7

<span class="syntax-def-name">
octal-literal-character

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[octal-digit](LexicalStructure.md#octal-digit)
<span class="alternative">
`_`

<span class="syntax-def-name">
octal-literal-characters

<span class="arrow">
→
<span class="syntactic-cat">[octal-literal-character](LexicalStructure.md#octal-literal-character)<span class="optional"><span class="syntactic-cat">[octal-literal-characters](LexicalStructure.md#octal-literal-characters)~opt~

<span class="syntax-def-name">
decimal-literal

<span class="arrow">
→
<span class="syntactic-cat">[decimal-digit](LexicalStructure.md#decimal-digit)<span class="optional"><span class="syntactic-cat">[decimal-literal-characters](LexicalStructure.md#decimal-literal-characters)~opt~

<span class="syntax-def-name">
decimal-digit

<span class="arrow">
→
<span class="text-description">Digit 0 through 9

<span class="syntax-def-name">
decimal-digits

<span class="arrow">
→
<span class="syntactic-cat">[decimal-digit](LexicalStructure.md#decimal-digit)<span class="optional"><span class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)~opt~

<span class="syntax-def-name">
decimal-literal-character

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[decimal-digit](LexicalStructure.md#decimal-digit)
<span class="alternative">
`_`

<span class="syntax-def-name">
decimal-literal-characters

<span class="arrow">
→
<span class="syntactic-cat">[decimal-literal-character](LexicalStructure.md#decimal-literal-character)<span class="optional"><span class="syntactic-cat">[decimal-literal-characters](LexicalStructure.md#decimal-literal-characters)~opt~

<span class="syntax-def-name">
hexadecimal-literal

<span class="arrow">
→
`0x`<span class="syntactic-cat">[hexadecimal-digit](LexicalStructure.md#hexadecimal-digit)<span class="optional"><span class="syntactic-cat">[hexadecimal-literal-characters](LexicalStructure.md#hexadecimal-literal-characters)~opt~

<span class="syntax-def-name">
hexadecimal-digit

<span class="arrow">
→
<span class="text-description">Digit 0 through 9, a through f, or A through F

<span class="syntax-def-name">
hexadecimal-literal-character

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[hexadecimal-digit](LexicalStructure.md#hexadecimal-digit)
<span class="alternative">
`_`

<span class="syntax-def-name">
hexadecimal-literal-characters

<span class="arrow">
→
<span class="syntactic-cat">[hexadecimal-literal-character](LexicalStructure.md#hexadecimal-literal-character)<span class="optional"><span class="syntactic-cat">[hexadecimal-literal-characters](LexicalStructure.md#hexadecimal-literal-characters)~opt~

Grammar of a floating-point literal

<span class="syntax-def-name">
floating-point-literal

<span class="arrow">
→
<span class="syntactic-cat">[decimal-literal](LexicalStructure.md#decimal-literal)<span class="optional"><span class="syntactic-cat">[decimal-fraction](LexicalStructure.md#decimal-fraction)~opt~<span class="optional"><span class="syntactic-cat">[decimal-exponent](LexicalStructure.md#decimal-exponent)~opt~

<span class="syntax-def-name">
floating-point-literal

<span class="arrow">
→
<span class="syntactic-cat">[hexadecimal-literal](LexicalStructure.md#hexadecimal-literal)<span class="optional"><span class="syntactic-cat">[hexadecimal-fraction](LexicalStructure.md#hexadecimal-fraction)~opt~<span class="syntactic-cat">[hexadecimal-exponent](LexicalStructure.md#hexadecimal-exponent)

<span class="syntax-def-name">
decimal-fraction

<span class="arrow">
→
`.`<span class="syntactic-cat">[decimal-literal](LexicalStructure.md#decimal-literal)

<span class="syntax-def-name">
decimal-exponent

<span class="arrow">
→
<span class="syntactic-cat">[floating-point-e](LexicalStructure.md#floating-point-e)<span class="optional"><span class="syntactic-cat">[sign](LexicalStructure.md#sign)~opt~<span class="syntactic-cat">[decimal-literal](LexicalStructure.md#decimal-literal)

<span class="syntax-def-name">
hexadecimal-fraction

<span class="arrow">
→
`.`<span class="syntactic-cat">[hexadecimal-digit](LexicalStructure.md#hexadecimal-digit)<span class="optional"><span class="syntactic-cat">[hexadecimal-literal-characters](LexicalStructure.md#hexadecimal-literal-characters)~opt~

<span class="syntax-def-name">
hexadecimal-exponent

<span class="arrow">
→
<span class="syntactic-cat">[floating-point-p](LexicalStructure.md#floating-point-p)<span class="optional"><span class="syntactic-cat">[sign](LexicalStructure.md#sign)~opt~<span class="syntactic-cat">[decimal-literal](LexicalStructure.md#decimal-literal)

<span class="syntax-def-name">
floating-point-e

<span class="arrow">
→
<span class="alternative">
`e`
<span class="alternative">
`E`

<span class="syntax-def-name">
floating-point-p

<span class="arrow">
→
<span class="alternative">
`p`
<span class="alternative">
`P`

<span class="syntax-def-name">
sign

<span class="arrow">
→
<span class="alternative">
`+`
<span class="alternative">
`-`

Grammar of a string literal

<span class="syntax-def-name">
string-literal

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[static-string-literal](LexicalStructure.md#static-string-literal)
<span class="alternative">
<span class="syntactic-cat">[interpolated-string-literal](LexicalStructure.md#interpolated-string-literal)

<span class="syntax-def-name">
static-string-literal

<span class="arrow">
→
`"`<span class="optional"><span class="syntactic-cat">[quoted-text](LexicalStructure.md#quoted-text)~opt~`"`

<span class="syntax-def-name">
quoted-text

<span class="arrow">
→
<span class="syntactic-cat">[quoted-text-item](LexicalStructure.md#quoted-text-item)<span class="optional"><span class="syntactic-cat">[quoted-text](LexicalStructure.md#quoted-text)~opt~

<span class="syntax-def-name">
quoted-text-item

<span class="arrow">
→
<span class="syntactic-cat">[escaped-character](LexicalStructure.md#escaped-character)

<span class="syntax-def-name">
quoted-text-item

<span class="arrow">
→
<span class="text-description">Any Unicode scalar value except `"`, ``, U+000A, or U+000D

<span class="syntax-def-name">
interpolated-string-literal

<span class="arrow">
→
`"`<span class="optional"><span class="syntactic-cat">[interpolated-text](LexicalStructure.md#interpolated-text)~opt~`"`

<span class="syntax-def-name">
interpolated-text

<span class="arrow">
→
<span class="syntactic-cat">[interpolated-text-item](LexicalStructure.md#interpolated-text-item)<span class="optional"><span class="syntactic-cat">[interpolated-text](LexicalStructure.md#interpolated-text)~opt~

<span class="syntax-def-name">
interpolated-text-item

<span class="arrow">
→
<span class="alternative">
`(`<span class="syntactic-cat">[expression](Expressions.md#expression)`)`
<span class="alternative">
<span class="syntactic-cat">[quoted-text-item](LexicalStructure.md#quoted-text-item)

<span class="syntax-def-name">
escaped-character

<span class="arrow">
→
<span class="alternative">
`0`
<span class="alternative">
`\`
<span class="alternative">
`t`
<span class="alternative">
`n`
<span class="alternative">
`r`
<span class="alternative">
`"`
<span class="alternative">
`'`

<span class="syntax-def-name">
escaped-character

<span class="arrow">
→
`u``{`<span class="syntactic-cat">[unicode-scalar-digits](LexicalStructure.md#unicode-scalar-digits)`}`

<span class="syntax-def-name">
unicode-scalar-digits

<span class="arrow">
→
<span class="text-description">Between one and eight hexadecimal digits

Grammar of operators

<span class="syntax-def-name">
operator

<span class="arrow">
→
<span class="syntactic-cat">[operator-head](LexicalStructure.md#operator-head)<span class="optional"><span class="syntactic-cat">[operator-characters](LexicalStructure.md#operator-characters)~opt~

<span class="syntax-def-name">
operator

<span class="arrow">
→
<span class="syntactic-cat">[dot-operator-head](LexicalStructure.md#dot-operator-head)<span class="optional"><span class="syntactic-cat">[dot-operator-characters](LexicalStructure.md#dot-operator-characters)~opt~

<span class="syntax-def-name">
operator-head

<span class="arrow">
→
<span class="alternative">
`/`
<span class="alternative">
`=`
<span class="alternative">
`-`
<span class="alternative">
`+`
<span class="alternative">
`!`
<span class="alternative">
`*`
<span class="alternative">
`%`
<span class="alternative">
`<`
<span class="alternative">
`>`
<span class="alternative">
`&`
<span class="alternative">
`|`
<span class="alternative">
`^`
<span class="alternative">
`~`
<span class="alternative">
`?`

<span class="syntax-def-name">
operator-head

<span class="arrow">
→
<span class="text-description">U+00A1–U+00A7

<span class="syntax-def-name">
operator-head

<span class="arrow">
→
<span class="text-description">U+00A9 or U+00AB

<span class="syntax-def-name">
operator-head

<span class="arrow">
→
<span class="text-description">U+00AC or U+00AE

<span class="syntax-def-name">
operator-head

<span class="arrow">
→
<span class="text-description">U+00B0–U+00B1, U+00B6, U+00BB, U+00BF, U+00D7, or U+00F7

<span class="syntax-def-name">
operator-head

<span class="arrow">
→
<span class="text-description">U+2016–U+2017 or U+2020–U+2027

<span class="syntax-def-name">
operator-head

<span class="arrow">
→
<span class="text-description">U+2030–U+203E

<span class="syntax-def-name">
operator-head

<span class="arrow">
→
<span class="text-description">U+2041–U+2053

<span class="syntax-def-name">
operator-head

<span class="arrow">
→
<span class="text-description">U+2055–U+205E

<span class="syntax-def-name">
operator-head

<span class="arrow">
→
<span class="text-description">U+2190–U+23FF

<span class="syntax-def-name">
operator-head

<span class="arrow">
→
<span class="text-description">U+2500–U+2775

<span class="syntax-def-name">
operator-head

<span class="arrow">
→
<span class="text-description">U+2794–U+2BFF

<span class="syntax-def-name">
operator-head

<span class="arrow">
→
<span class="text-description">U+2E00–U+2E7F

<span class="syntax-def-name">
operator-head

<span class="arrow">
→
<span class="text-description">U+3001–U+3003

<span class="syntax-def-name">
operator-head

<span class="arrow">
→
<span class="text-description">U+3008–U+3030

<span class="syntax-def-name">
operator-character

<span class="arrow">
→
<span class="syntactic-cat">[operator-head](LexicalStructure.md#operator-head)

<span class="syntax-def-name">
operator-character

<span class="arrow">
→
<span class="text-description">U+0300–U+036F

<span class="syntax-def-name">
operator-character

<span class="arrow">
→
<span class="text-description">U+1DC0–U+1DFF

<span class="syntax-def-name">
operator-character

<span class="arrow">
→
<span class="text-description">U+20D0–U+20FF

<span class="syntax-def-name">
operator-character

<span class="arrow">
→
<span class="text-description">U+FE00–U+FE0F

<span class="syntax-def-name">
operator-character

<span class="arrow">
→
<span class="text-description">U+FE20–U+FE2F

<span class="syntax-def-name">
operator-character

<span class="arrow">
→
<span class="text-description">U+E0100–U+E01EF

<span class="syntax-def-name">
operator-characters

<span class="arrow">
→
<span class="syntactic-cat">[operator-character](LexicalStructure.md#operator-character)<span class="optional"><span class="syntactic-cat">[operator-characters](LexicalStructure.md#operator-characters)~opt~

<span class="syntax-def-name">
dot-operator-head

<span class="arrow">
→
`..`

<span class="syntax-def-name">
dot-operator-character

<span class="arrow">
→
<span class="alternative">
`.`
<span class="alternative">
<span class="syntactic-cat">[operator-character](LexicalStructure.md#operator-character)

<span class="syntax-def-name">
dot-operator-characters

<span class="arrow">
→
<span class="syntactic-cat">[dot-operator-character](LexicalStructure.md#dot-operator-character)<span class="optional"><span class="syntactic-cat">[dot-operator-characters](LexicalStructure.md#dot-operator-characters)~opt~

<span class="syntax-def-name">
binary-operator

<span class="arrow">
→
<span class="syntactic-cat">[operator](LexicalStructure.md#operator)

<span class="syntax-def-name">
prefix-operator

<span class="arrow">
→
<span class="syntactic-cat">[operator](LexicalStructure.md#operator)

<span class="syntax-def-name">
postfix-operator

<span class="arrow">
→
<span class="syntactic-cat">[operator](LexicalStructure.md#operator)

### Types

Grammar of a type

<span class="syntax-def-name">
type

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[array-type](Types.md#array-type)
<span class="alternative">
<span class="syntactic-cat">[dictionary-type](Types.md#dictionary-type)
<span class="alternative">
<span class="syntactic-cat">[function-type](Types.md#function-type)
<span class="alternative">
<span class="syntactic-cat">[type-identifier](Types.md#type-identifier)
<span class="alternative">
<span class="syntactic-cat">[tuple-type](Types.md#tuple-type)
<span class="alternative">
<span class="syntactic-cat">[optional-type](Types.md#optional-type)
<span class="alternative">
<span class="syntactic-cat">[implicitly-unwrapped-optional-type](Types.md#implicitly-unwrapped-optional-type)
<span class="alternative">
<span class="syntactic-cat">[protocol-composition-type](Types.md#protocol-composition-type)
<span class="alternative">
<span class="syntactic-cat">[metatype-type](Types.md#metatype-type)

Grammar of a type annotation

<span class="syntax-def-name">
type-annotation

<span class="arrow">
→
`:`<span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)~opt~<span class="syntactic-cat">[type](Types.md#type)

Grammar of a type identifier

<span class="syntax-def-name">
type-identifier

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[type-name](Types.md#type-name)<span class="optional"><span class="syntactic-cat">[generic-argument-clause](GenericParametersAndArguments.md#generic-argument-clause)~opt~
<span class="alternative">
<span class="syntactic-cat">[type-name](Types.md#type-name)<span class="optional"><span class="syntactic-cat">[generic-argument-clause](GenericParametersAndArguments.md#generic-argument-clause)~opt~`.`<span class="syntactic-cat">[type-identifier](Types.md#type-identifier)

<span class="syntax-def-name">
type-name

<span class="arrow">
→
<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)

Grammar of a tuple type

<span class="syntax-def-name">
tuple-type

<span class="arrow">
→
`(`<span class="optional"><span class="syntactic-cat">[tuple-type-body](Types.md#tuple-type-body)~opt~`)`

<span class="syntax-def-name">
tuple-type-body

<span class="arrow">
→
<span class="syntactic-cat">[tuple-type-element-list](Types.md#tuple-type-element-list)<span class="optional">`...`~opt~

<span class="syntax-def-name">
tuple-type-element-list

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[tuple-type-element](Types.md#tuple-type-element)
<span class="alternative">
<span class="syntactic-cat">[tuple-type-element](Types.md#tuple-type-element)`,`<span class="syntactic-cat">[tuple-type-element-list](Types.md#tuple-type-element-list)

<span class="syntax-def-name">
tuple-type-element

<span class="arrow">
→
<span class="alternative">
<span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)~opt~<span class="optional">`inout`~opt~<span class="syntactic-cat">[type](Types.md#type)
<span class="alternative">
<span class="optional">`inout`~opt~<span class="syntactic-cat">[element-name](Types.md#element-name)<span class="syntactic-cat">[type-annotation](Types.md#type-annotation)

<span class="syntax-def-name">
element-name

<span class="arrow">
→
<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)

Grammar of a function type

<span class="syntax-def-name">
function-type

<span class="arrow">
→
<span class="syntactic-cat">[type](Types.md#type)<span class="optional">`throws`~opt~`->`<span class="syntactic-cat">[type](Types.md#type)

<span class="syntax-def-name">
function-type

<span class="arrow">
→
<span class="syntactic-cat">[type](Types.md#type)`rethrows``->`<span class="syntactic-cat">[type](Types.md#type)

Grammar of an array type

<span class="syntax-def-name">
array-type

<span class="arrow">
→
`[`<span class="syntactic-cat">[type](Types.md#type)`]`

Grammar of a dictionary type

<span class="syntax-def-name">
dictionary-type

<span class="arrow">
→
`[`<span class="syntactic-cat">[type](Types.md#type)`:`<span class="syntactic-cat">[type](Types.md#type)`]`

Grammar of an optional type

<span class="syntax-def-name">
optional-type

<span class="arrow">
→
<span class="syntactic-cat">[type](Types.md#type)`?`

Grammar of an implicitly unwrapped optional type

<span class="syntax-def-name">
implicitly-unwrapped-optional-type

<span class="arrow">
→
<span class="syntactic-cat">[type](Types.md#type)`!`

Grammar of a protocol composition type

<span class="syntax-def-name">
protocol-composition-type

<span class="arrow">
→
`protocol``<`<span class="optional"><span class="syntactic-cat">[protocol-identifier-list](Types.md#protocol-identifier-list)~opt~`>`

<span class="syntax-def-name">
protocol-identifier-list

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[protocol-identifier](Types.md#protocol-identifier)
<span class="alternative">
<span class="syntactic-cat">[protocol-identifier](Types.md#protocol-identifier)`,`<span class="syntactic-cat">[protocol-identifier-list](Types.md#protocol-identifier-list)

<span class="syntax-def-name">
protocol-identifier

<span class="arrow">
→
<span class="syntactic-cat">[type-identifier](Types.md#type-identifier)

Grammar of a metatype type

<span class="syntax-def-name">
metatype-type

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[type](Types.md#type)`.``Type`
<span class="alternative">
<span class="syntactic-cat">[type](Types.md#type)`.``Protocol`

Grammar of a type inheritance clause

<span class="syntax-def-name">
type-inheritance-clause

<span class="arrow">
→
`:`<span class="syntactic-cat">[class-requirement](Types.md#class-requirement)`,`<span class="syntactic-cat">[type-inheritance-list](Types.md#type-inheritance-list)

<span class="syntax-def-name">
type-inheritance-clause

<span class="arrow">
→
`:`<span class="syntactic-cat">[class-requirement](Types.md#class-requirement)

<span class="syntax-def-name">
type-inheritance-clause

<span class="arrow">
→
`:`<span class="syntactic-cat">[type-inheritance-list](Types.md#type-inheritance-list)

<span class="syntax-def-name">
type-inheritance-list

<span class="arrow">
→
<span class="alternative">
<span class="syntactic-cat">[type-identifier](Types.md#type-identifier)
<span class="alternative">
<span class="syntactic-cat">[type-identifier](Types.md#type-identifier)`,`<span class="syntactic-cat">[type-inheritance-list](Types.md#type-inheritance-list)

<span class="syntax-def-name">
class-requirement

<span class="arrow">
→
`class`

