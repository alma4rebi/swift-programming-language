Summary of the Grammar 
----------------------

### Statements 

Grammar of a statement

<span class="syntax-def-name">
statement
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[expression](Expressions.md#expression)</span><span class="optional">`;`~opt~</span>

<span class="syntax-def-name">
statement
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[declaration](Declarations.md#declaration)</span><span class="optional">`;`~opt~</span>

<span class="syntax-def-name">
statement
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[loop-statement](Statements.md#loop-statement)</span><span class="optional">`;`~opt~</span>

<span class="syntax-def-name">
statement
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[branch-statement](Statements.md#branch-statement)</span><span class="optional">`;`~opt~</span>

<span class="syntax-def-name">
statement
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[labeled-statement](Statements.md#labeled-statement)</span><span class="optional">`;`~opt~</span>

<span class="syntax-def-name">
statement
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[control-transfer-statement](Statements.md#control-transfer-statement)</span><span class="optional">`;`~opt~</span>

<span class="syntax-def-name">
statement
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[defer-statement](Statements.md#defer-statement)</span><span class="optional">`;`~opt~</span>

<span class="syntax-def-name">
statement
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[do-statement](Statements.md#do-statement)</span><span class="optional">`:`~opt~</span>

<span class="syntax-def-name">
statement
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[compiler-control-statement](Statements.md#compiler-control-statement)</span>

<span class="syntax-def-name">
statements
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[statement](Statements.md#statement)</span><span class="optional"><span class="syntactic-cat">[statements](Statements.md#statements)</span>~opt~</span>

Grammar of a loop statement

<span class="syntax-def-name">
loop-statement
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[for-statement](Statements.md#for-statement)</span>

<span class="syntax-def-name">
loop-statement
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[for-in-statement](Statements.md#for-in-statement)</span>

<span class="syntax-def-name">
loop-statement
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[while-statement](Statements.md#while-statement)</span>

<span class="syntax-def-name">
loop-statement
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[repeat-while-statement](Statements.md#repeat-while-statement)</span>

Grammar of a for statement

<span class="syntax-def-name">
for-statement
</span>
<span class="arrow">
→
</span>`for`<span class="optional"><span class="syntactic-cat">[for-init](Statements.md#for-init)</span>~opt~</span>`;`<span class="optional"><span class="syntactic-cat">[expression](Expressions.md#expression)</span>~opt~</span>`;`<span class="optional"><span class="syntactic-cat">[expression-list](Expressions.md#expression-list)</span>~opt~</span><span class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

<span class="syntax-def-name">
for-statement
</span>
<span class="arrow">
→
</span>`for``(`<span class="optional"><span class="syntactic-cat">[for-init](Statements.md#for-init)</span>~opt~</span>`;`<span class="optional"><span class="syntactic-cat">[expression](Expressions.md#expression)</span>~opt~</span>`;`<span class="optional"><span class="syntactic-cat">[expression-list](Expressions.md#expression-list)</span>~opt~</span>`)`<span class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

<span class="syntax-def-name">
for-init
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[variable-declaration](Declarations.md#variable-declaration)</span>
</span><span class="alternative">
<span class="syntactic-cat">[expression-list](Expressions.md#expression-list)</span>
</span>

Grammar of a for-in statement

<span class="syntax-def-name">
for-in-statement
</span>
<span class="arrow">
→
</span>`for`<span class="optional">`case`~opt~</span><span class="syntactic-cat">[pattern](Patterns.md#pattern)</span>`in`<span class="syntactic-cat">[expression](Expressions.md#expression)</span><span class="optional"><span class="syntactic-cat">[where-clause](Statements.md#where-clause)</span>~opt~</span><span class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

Grammar of a while statement

<span class="syntax-def-name">
while-statement
</span>
<span class="arrow">
→
</span>`while`<span class="syntactic-cat">[condition-clause](Statements.md#condition-clause)</span><span class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

<span class="syntax-def-name">
condition-clause
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[expression](Expressions.md#expression)</span>

<span class="syntax-def-name">
condition-clause
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[expression](Expressions.md#expression)</span>`,`<span class="syntactic-cat">[condition-list](Statements.md#condition-list)</span>

<span class="syntax-def-name">
condition-clause
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[condition-list](Statements.md#condition-list)</span>

<span class="syntax-def-name">
condition-clause
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[availability-condition](Statements.md#availability-condition)</span>`,`<span class="syntactic-cat">[expression](Expressions.md#expression)</span>

<span class="syntax-def-name">
condition-list
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[condition](Statements.md#condition)</span>
</span><span class="alternative">
<span class="syntactic-cat">[condition](Statements.md#condition)</span>`,`<span class="syntactic-cat">[condition-list](Statements.md#condition-list)</span>
</span>

<span class="syntax-def-name">
condition
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[availability-condition](Statements.md#availability-condition)</span>
</span><span class="alternative">
<span class="syntactic-cat">[case-condition](Statements.md#case-condition)</span>
</span><span class="alternative">
<span class="syntactic-cat">[optional-binding-condition](Statements.md#optional-binding-condition)</span>
</span>

<span class="syntax-def-name">
case-condition
</span>
<span class="arrow">
→
</span>`case`<span class="syntactic-cat">[pattern](Patterns.md#pattern)</span><span class="syntactic-cat">[initializer](Declarations.md#initializer)</span><span class="optional"><span class="syntactic-cat">[where-clause](Statements.md#where-clause)</span>~opt~</span>

<span class="syntax-def-name">
optional-binding-condition
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[optional-binding-head](Statements.md#optional-binding-head)</span><span class="optional"><span class="syntactic-cat">[optional-binding-continuation-list](Statements.md#optional-binding-continuation-list)</span>~opt~</span><span class="optional"><span class="syntactic-cat">[where-clause](Statements.md#where-clause)</span>~opt~</span>

<span class="syntax-def-name">
optional-binding-head
</span>
<span class="arrow">
→
</span>`let`<span class="syntactic-cat">[pattern](Patterns.md#pattern)</span><span class="syntactic-cat">[initializer](Declarations.md#initializer)</span>

<span class="syntax-def-name">
optional-binding-continuation-list
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[optional-binding-continuation](Statements.md#optional-binding-continuation)</span>
</span><span class="alternative">
<span class="syntactic-cat">[optional-binding-continuation](Statements.md#optional-binding-continuation)</span>`,`<span class="syntactic-cat">[optional-binding-continuation-list](Statements.md#optional-binding-continuation-list)</span>
</span>

<span class="syntax-def-name">
optional-binding-continuation
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[pattern](Patterns.md#pattern)</span><span class="syntactic-cat">[initializer](Declarations.md#initializer)</span>
</span><span class="alternative">
<span class="syntactic-cat">[optional-binding-head](Statements.md#optional-binding-head)</span>
</span>

Grammar of a repeat-while statement

<span class="syntax-def-name">
repeat-while-statement
</span>
<span class="arrow">
→
</span>`repeat`<span class="syntactic-cat">[code-block](Declarations.md#code-block)</span>`while`<span class="syntactic-cat">[expression](Expressions.md#expression)</span>

Grammar of a branch statement

<span class="syntax-def-name">
branch-statement
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[if-statement](Statements.md#if-statement)</span>

<span class="syntax-def-name">
branch-statement
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[guard-statement](Statements.md#guard-statement)</span>

<span class="syntax-def-name">
branch-statement
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[switch-statement](Statements.md#switch-statement)</span>

Grammar of an if statement

<span class="syntax-def-name">
if-statement
</span>
<span class="arrow">
→
</span>`if`<span class="syntactic-cat">[condition-clause](Statements.md#condition-clause)</span><span class="syntactic-cat">[code-block](Declarations.md#code-block)</span><span class="optional"><span class="syntactic-cat">[else-clause](Statements.md#else-clause)</span>~opt~</span>

<span class="syntax-def-name">
else-clause
</span>
<span class="arrow">
→
</span><span class="alternative">
`else`<span class="syntactic-cat">[code-block](Declarations.md#code-block)</span>
</span><span class="alternative">
`else`<span class="syntactic-cat">[if-statement](Statements.md#if-statement)</span>
</span>

Grammar of a guard statement

<span class="syntax-def-name">
guard-statement
</span>
<span class="arrow">
→
</span>`guard`<span class="syntactic-cat">[condition-clause](Statements.md#condition-clause)</span>`else`<span class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

Grammar of a switch statement

<span class="syntax-def-name">
switch-statement
</span>
<span class="arrow">
→
</span>`switch`<span class="syntactic-cat">[expression](Expressions.md#expression)</span>`{`<span class="optional"><span class="syntactic-cat">[switch-cases](Statements.md#switch-cases)</span>~opt~</span>`}`

<span class="syntax-def-name">
switch-cases
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[switch-case](Statements.md#switch-case)</span><span class="optional"><span class="syntactic-cat">[switch-cases](Statements.md#switch-cases)</span>~opt~</span>

<span class="syntax-def-name">
switch-case
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[case-label](Statements.md#case-label)</span><span class="syntactic-cat">[statements](Statements.md#statements)</span>
</span><span class="alternative">
<span class="syntactic-cat">[default-label](Statements.md#default-label)</span><span class="syntactic-cat">[statements](Statements.md#statements)</span>
</span>

<span class="syntax-def-name">
case-label
</span>
<span class="arrow">
→
</span>`case`<span class="syntactic-cat">[case-item-list](Statements.md#case-item-list)</span>`:`

<span class="syntax-def-name">
case-item-list
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[pattern](Patterns.md#pattern)</span><span class="optional"><span class="syntactic-cat">[where-clause](Statements.md#where-clause)</span>~opt~</span>
</span><span class="alternative">
<span class="syntactic-cat">[pattern](Patterns.md#pattern)</span><span class="optional"><span class="syntactic-cat">[where-clause](Statements.md#where-clause)</span>~opt~</span>`,`<span class="syntactic-cat">[case-item-list](Statements.md#case-item-list)</span>
</span>

<span class="syntax-def-name">
default-label
</span>
<span class="arrow">
→
</span>`default``:`

<span class="syntax-def-name">
where-clause
</span>
<span class="arrow">
→
</span>`where`<span class="syntactic-cat">[where-expression](Statements.md#where-expression)</span>

<span class="syntax-def-name">
where-expression
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[expression](Expressions.md#expression)</span>

Grammar of a labeled statement

<span class="syntax-def-name">
labeled-statement
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[statement-label](Statements.md#statement-label)</span><span class="syntactic-cat">[loop-statement](Statements.md#loop-statement)</span>
</span><span class="alternative">
<span class="syntactic-cat">[statement-label](Statements.md#statement-label)</span><span class="syntactic-cat">[if-statement](Statements.md#if-statement)</span>
</span><span class="alternative">
<span class="syntactic-cat">[statement-label](Statements.md#statement-label)</span><span class="syntactic-cat">[switch-statement](Statements.md#switch-statement)</span>
</span>

<span class="syntax-def-name">
statement-label
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[label-name](Statements.md#label-name)</span>`:`

<span class="syntax-def-name">
label-name
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

Grammar of a control transfer statement

<span class="syntax-def-name">
control-transfer-statement
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[break-statement](Statements.md#break-statement)</span>

<span class="syntax-def-name">
control-transfer-statement
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[continue-statement](Statements.md#continue-statement)</span>

<span class="syntax-def-name">
control-transfer-statement
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[fallthrough-statement](Statements.md#fallthrough-statement)</span>

<span class="syntax-def-name">
control-transfer-statement
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[return-statement](Statements.md#return-statement)</span>

<span class="syntax-def-name">
control-transfer-statement
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[throw-statement](Statements.md#throw-statement)</span>

Grammar of a break statement

<span class="syntax-def-name">
break-statement
</span>
<span class="arrow">
→
</span>`break`<span class="optional"><span class="syntactic-cat">[label-name](Statements.md#label-name)</span>~opt~</span>

Grammar of a continue statement

<span class="syntax-def-name">
continue-statement
</span>
<span class="arrow">
→
</span>`continue`<span class="optional"><span class="syntactic-cat">[label-name](Statements.md#label-name)</span>~opt~</span>

Grammar of a fallthrough statement

<span class="syntax-def-name">
fallthrough-statement
</span>
<span class="arrow">
→
</span>`fallthrough`

Grammar of a return statement

<span class="syntax-def-name">
return-statement
</span>
<span class="arrow">
→
</span>`return`<span class="optional"><span class="syntactic-cat">[expression](Expressions.md#expression)</span>~opt~</span>

Grammar of an availability condition

<span class="syntax-def-name">
availability-condition
</span>
<span class="arrow">
→
</span>`#available``(`<span class="syntactic-cat">[availability-arguments](Statements.md#availability-arguments)</span>`)`

<span class="syntax-def-name">
availability-arguments
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[availability-argument](Statements.md#availability-argument)</span>
</span><span class="alternative">
<span class="syntactic-cat">[availability-argument](Statements.md#availability-argument)</span>`,`<span class="syntactic-cat">[availability-arguments](Statements.md#availability-arguments)</span>
</span>

<span class="syntax-def-name">
availability-argument
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[platform-name](Statements.md#platform-name)</span><span class="syntactic-cat">[platform-version](Statements.md#platform-version)</span>

<span class="syntax-def-name">
availability-argument
</span>
<span class="arrow">
→
</span>`*`

<span class="syntax-def-name">
platform-name
</span>
<span class="arrow">
→
</span><span class="alternative">
`iOS`
</span><span class="alternative">
`iOSApplicationExtension`
</span>

<span class="syntax-def-name">
platform-name
</span>
<span class="arrow">
→
</span><span class="alternative">
`OSX`
</span><span class="alternative">
`OSXApplicationExtension`
</span>

<span class="syntax-def-name">
platform-name
</span>
<span class="arrow">
→
</span>`watchOS`

<span class="syntax-def-name">
platform-version
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)</span>

<span class="syntax-def-name">
platform-version
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)</span>`.`<span class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)</span>

<span class="syntax-def-name">
platform-version
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)</span>`.`<span class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)</span>`.`<span class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)</span>

Grammar of a throw statement

<span class="syntax-def-name">
throw-statement
</span>
<span class="arrow">
→
</span>`throw`<span class="syntactic-cat">[expression](Expressions.md#expression)</span>

Grammar of a defer statement

<span class="syntax-def-name">
defer-statement
</span>
<span class="arrow">
→
</span>`defer`<span class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

Grammar of a do statement

<span class="syntax-def-name">
do-statement
</span>
<span class="arrow">
→
</span>`do`<span class="syntactic-cat">[code-block](Declarations.md#code-block)</span><span class="optional"><span class="syntactic-cat">[catch-clauses](Statements.md#catch-clauses)</span>~opt~</span>

<span class="syntax-def-name">
catch-clauses
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[catch-clause](Statements.md#catch-clause)</span><span class="optional"><span class="syntactic-cat">[catch-clauses](Statements.md#catch-clauses)</span>~opt~</span>

<span class="syntax-def-name">
catch-clause
</span>
<span class="arrow">
→
</span>`catch`<span class="optional"><span class="syntactic-cat">[pattern](Patterns.md#pattern)</span>~opt~</span><span class="optional"><span class="syntactic-cat">[where-clause](Statements.md#where-clause)</span>~opt~</span><span class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

Grammar of a compiler control statement

<span class="syntax-def-name">
compiler-control-statement
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[build-configuration-statement](Statements.md#build-configuration-statement)</span>

<span class="syntax-def-name">
compiler-control-statement
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[line-control-statement](Statements.md#line-control-statement)</span>

Grammar of a build configuration statement

<span class="syntax-def-name">
build-configuration-statement
</span>
<span class="arrow">
→
</span>`#if`<span class="syntactic-cat">[build-configuration](Statements.md#build-configuration)</span><span class="optional"><span class="syntactic-cat">[statements](Statements.md#statements)</span>~opt~</span><span class="optional"><span class="syntactic-cat">[build-configuration-elseif-clauses](Statements.md#build-configuration-elseif-clauses)</span>~opt~</span><span class="optional"><span class="syntactic-cat">[build-configuration-else-clause](Statements.md#build-configuration-else-clause)</span>~opt~</span>`#endif`

<span class="syntax-def-name">
build-configuration-elseif-clauses
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[build-configuration-elseif-clause](Statements.md#build-configuration-elseif-clause)</span><span class="optional"><span class="syntactic-cat">[build-configuration-elseif-clauses](Statements.md#build-configuration-elseif-clauses)</span>~opt~</span>

<span class="syntax-def-name">
build-configuration-elseif-clause
</span>
<span class="arrow">
→
</span>`#elseif`<span class="syntactic-cat">[build-configuration](Statements.md#build-configuration)</span><span class="optional"><span class="syntactic-cat">[statements](Statements.md#statements)</span>~opt~</span>

<span class="syntax-def-name">
build-configuration-else-clause
</span>
<span class="arrow">
→
</span>`#else`<span class="optional"><span class="syntactic-cat">[statements](Statements.md#statements)</span>~opt~</span>

<span class="syntax-def-name">
build-configuration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[platform-testing-function](Statements.md#platform-testing-function)</span>

<span class="syntax-def-name">
build-configuration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

<span class="syntax-def-name">
build-configuration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[boolean-literal](LexicalStructure.md#boolean-literal)</span>

<span class="syntax-def-name">
build-configuration
</span>
<span class="arrow">
→
</span>`(`<span class="syntactic-cat">[build-configuration](Statements.md#build-configuration)</span>`)`

<span class="syntax-def-name">
build-configuration
</span>
<span class="arrow">
→
</span>`!`<span class="syntactic-cat">[build-configuration](Statements.md#build-configuration)</span>

<span class="syntax-def-name">
build-configuration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[build-configuration](Statements.md#build-configuration)</span>`&&`<span class="syntactic-cat">[build-configuration](Statements.md#build-configuration)</span>

<span class="syntax-def-name">
build-configuration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[build-configuration](Statements.md#build-configuration)</span>`||`<span class="syntactic-cat">[build-configuration](Statements.md#build-configuration)</span>

<span class="syntax-def-name">
platform-testing-function
</span>
<span class="arrow">
→
</span>`os``(`<span class="syntactic-cat">[operating-system](Statements.md#operating-system)</span>`)`

<span class="syntax-def-name">
platform-testing-function
</span>
<span class="arrow">
→
</span>`arch``(`<span class="syntactic-cat">[architecture](Statements.md#architecture)</span>`)`

<span class="syntax-def-name">
operating-system
</span>
<span class="arrow">
→
</span><span class="alternative">
`OSX`
</span><span class="alternative">
`iOS`
</span><span class="alternative">
`watchOS`
</span><span class="alternative">
`tvOS`
</span>

<span class="syntax-def-name">
architecture
</span>
<span class="arrow">
→
</span><span class="alternative">
`i386`
</span><span class="alternative">
`x86_64`
</span><span class="alternative">
`arm`
</span><span class="alternative">
`arm64`
</span>

Grammar of a line control statement

<span class="syntax-def-name">
line-control-statement
</span>
<span class="arrow">
→
</span>`#line`

<span class="syntax-def-name">
line-control-statement
</span>
<span class="arrow">
→
</span>`#line`<span class="syntactic-cat">[line-number](Statements.md#line-number)</span><span class="syntactic-cat">[file-name](Statements.md#file-name)</span>

<span class="syntax-def-name">
line-number
</span>
<span class="arrow">
→
</span><span class="text-description">A decimal integer greater than zero</span>

<span class="syntax-def-name">
file-name
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[static-string-literal](LexicalStructure.md#static-string-literal)</span>

### Generic Parameters and Arguments 

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

### Declarations 

Grammar of a declaration

<span class="syntax-def-name">
declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[import-declaration](Declarations.md#import-declaration)</span>

<span class="syntax-def-name">
declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[constant-declaration](Declarations.md#constant-declaration)</span>

<span class="syntax-def-name">
declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[variable-declaration](Declarations.md#variable-declaration)</span>

<span class="syntax-def-name">
declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[typealias-declaration](Declarations.md#typealias-declaration)</span>

<span class="syntax-def-name">
declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[function-declaration](Declarations.md#function-declaration)</span>

<span class="syntax-def-name">
declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[enum-declaration](Declarations.md#enum-declaration)</span>

<span class="syntax-def-name">
declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[struct-declaration](Declarations.md#struct-declaration)</span>

<span class="syntax-def-name">
declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[class-declaration](Declarations.md#class-declaration)</span>

<span class="syntax-def-name">
declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[protocol-declaration](Declarations.md#protocol-declaration)</span>

<span class="syntax-def-name">
declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[initializer-declaration](Declarations.md#initializer-declaration)</span>

<span class="syntax-def-name">
declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[deinitializer-declaration](Declarations.md#deinitializer-declaration)</span>

<span class="syntax-def-name">
declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[extension-declaration](Declarations.md#extension-declaration)</span>

<span class="syntax-def-name">
declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[subscript-declaration](Declarations.md#subscript-declaration)</span>

<span class="syntax-def-name">
declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[operator-declaration](Declarations.md#operator-declaration)</span>

<span class="syntax-def-name">
declarations
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[declaration](Declarations.md#declaration)</span><span class="optional"><span class="syntactic-cat">[declarations](Declarations.md#declarations)</span>~opt~</span>

Grammar of a top-level declaration

<span class="syntax-def-name">
top-level-declaration
</span>
<span class="arrow">
→
</span><span class="optional"><span class="syntactic-cat">[statements](Statements.md#statements)</span>~opt~</span>

Grammar of a code block

<span class="syntax-def-name">
code-block
</span>
<span class="arrow">
→
</span>`{`<span class="optional"><span class="syntactic-cat">[statements](Statements.md#statements)</span>~opt~</span>`}`

Grammar of an import declaration

<span class="syntax-def-name">
import-declaration
</span>
<span class="arrow">
→
</span><span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span>`import`<span class="optional"><span class="syntactic-cat">[import-kind](Declarations.md#import-kind)</span>~opt~</span><span class="syntactic-cat">[import-path](Declarations.md#import-path)</span>

<span class="syntax-def-name">
import-kind
</span>
<span class="arrow">
→
</span><span class="alternative">
`typealias`
</span><span class="alternative">
`struct`
</span><span class="alternative">
`class`
</span><span class="alternative">
`enum`
</span><span class="alternative">
`protocol`
</span><span class="alternative">
`var`
</span><span class="alternative">
`func`
</span>

<span class="syntax-def-name">
import-path
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[import-path-identifier](Declarations.md#import-path-identifier)</span>
</span><span class="alternative">
<span class="syntactic-cat">[import-path-identifier](Declarations.md#import-path-identifier)</span>`.`<span class="syntactic-cat">[import-path](Declarations.md#import-path)</span>
</span>

<span class="syntax-def-name">
import-path-identifier
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>
</span><span class="alternative">
<span class="syntactic-cat">[operator](LexicalStructure.md#operator)</span>
</span>

Grammar of a constant declaration

<span class="syntax-def-name">
constant-declaration
</span>
<span class="arrow">
→
</span><span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span class="optional"><span class="syntactic-cat">[declaration-modifiers](Declarations.md#declaration-modifiers)</span>~opt~</span>`let`<span class="syntactic-cat">[pattern-initializer-list](Declarations.md#pattern-initializer-list)</span>

<span class="syntax-def-name">
pattern-initializer-list
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[pattern-initializer](Declarations.md#pattern-initializer)</span>
</span><span class="alternative">
<span class="syntactic-cat">[pattern-initializer](Declarations.md#pattern-initializer)</span>`,`<span class="syntactic-cat">[pattern-initializer-list](Declarations.md#pattern-initializer-list)</span>
</span>

<span class="syntax-def-name">
pattern-initializer
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[pattern](Patterns.md#pattern)</span><span class="optional"><span class="syntactic-cat">[initializer](Declarations.md#initializer)</span>~opt~</span>

<span class="syntax-def-name">
initializer
</span>
<span class="arrow">
→
</span>`=`<span class="syntactic-cat">[expression](Expressions.md#expression)</span>

Grammar of a variable declaration

<span class="syntax-def-name">
variable-declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[variable-declaration-head](Declarations.md#variable-declaration-head)</span><span class="syntactic-cat">[pattern-initializer-list](Declarations.md#pattern-initializer-list)</span>

<span class="syntax-def-name">
variable-declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[variable-declaration-head](Declarations.md#variable-declaration-head)</span><span class="syntactic-cat">[variable-name](Declarations.md#variable-name)</span><span class="syntactic-cat">[type-annotation](Types.md#type-annotation)</span><span class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

<span class="syntax-def-name">
variable-declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[variable-declaration-head](Declarations.md#variable-declaration-head)</span><span class="syntactic-cat">[variable-name](Declarations.md#variable-name)</span><span class="syntactic-cat">[type-annotation](Types.md#type-annotation)</span><span class="syntactic-cat">[getter-setter-block](Declarations.md#getter-setter-block)</span>

<span class="syntax-def-name">
variable-declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[variable-declaration-head](Declarations.md#variable-declaration-head)</span><span class="syntactic-cat">[variable-name](Declarations.md#variable-name)</span><span class="syntactic-cat">[type-annotation](Types.md#type-annotation)</span><span class="syntactic-cat">[getter-setter-keyword-block](Declarations.md#getter-setter-keyword-block)</span>

<span class="syntax-def-name">
variable-declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[variable-declaration-head](Declarations.md#variable-declaration-head)</span><span class="syntactic-cat">[variable-name](Declarations.md#variable-name)</span><span class="syntactic-cat">[initializer](Declarations.md#initializer)</span><span class="syntactic-cat">[willSet-didSet-block](Declarations.md#willSet-didSet-block)</span>

<span class="syntax-def-name">
variable-declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[variable-declaration-head](Declarations.md#variable-declaration-head)</span><span class="syntactic-cat">[variable-name](Declarations.md#variable-name)</span><span class="syntactic-cat">[type-annotation](Types.md#type-annotation)</span><span class="optional"><span class="syntactic-cat">[initializer](Declarations.md#initializer)</span>~opt~</span><span class="syntactic-cat">[willSet-didSet-block](Declarations.md#willSet-didSet-block)</span>

<span class="syntax-def-name">
variable-declaration-head
</span>
<span class="arrow">
→
</span><span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span class="optional"><span class="syntactic-cat">[declaration-modifiers](Declarations.md#declaration-modifiers)</span>~opt~</span>`var`

<span class="syntax-def-name">
variable-name
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

<span class="syntax-def-name">
getter-setter-block
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

<span class="syntax-def-name">
getter-setter-block
</span>
<span class="arrow">
→
</span>`{`<span class="syntactic-cat">[getter-clause](Declarations.md#getter-clause)</span><span class="optional"><span class="syntactic-cat">[setter-clause](Declarations.md#setter-clause)</span>~opt~</span>`}`

<span class="syntax-def-name">
getter-setter-block
</span>
<span class="arrow">
→
</span>`{`<span class="syntactic-cat">[setter-clause](Declarations.md#setter-clause)</span><span class="syntactic-cat">[getter-clause](Declarations.md#getter-clause)</span>`}`

<span class="syntax-def-name">
getter-clause
</span>
<span class="arrow">
→
</span><span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span>`get`<span class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

<span class="syntax-def-name">
setter-clause
</span>
<span class="arrow">
→
</span><span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span>`set`<span class="optional"><span class="syntactic-cat">[setter-name](Declarations.md#setter-name)</span>~opt~</span><span class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

<span class="syntax-def-name">
setter-name
</span>
<span class="arrow">
→
</span>`(`<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>`)`

<span class="syntax-def-name">
getter-setter-keyword-block
</span>
<span class="arrow">
→
</span>`{`<span class="syntactic-cat">[getter-keyword-clause](Declarations.md#getter-keyword-clause)</span><span class="optional"><span class="syntactic-cat">[setter-keyword-clause](Declarations.md#setter-keyword-clause)</span>~opt~</span>`}`

<span class="syntax-def-name">
getter-setter-keyword-block
</span>
<span class="arrow">
→
</span>`{`<span class="syntactic-cat">[setter-keyword-clause](Declarations.md#setter-keyword-clause)</span><span class="syntactic-cat">[getter-keyword-clause](Declarations.md#getter-keyword-clause)</span>`}`

<span class="syntax-def-name">
getter-keyword-clause
</span>
<span class="arrow">
→
</span><span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span>`get`

<span class="syntax-def-name">
setter-keyword-clause
</span>
<span class="arrow">
→
</span><span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span>`set`

<span class="syntax-def-name">
willSet-didSet-block
</span>
<span class="arrow">
→
</span>`{`<span class="syntactic-cat">[willSet-clause](Declarations.md#willSet-clause)</span><span class="optional"><span class="syntactic-cat">[didSet-clause](Declarations.md#didSet-clause)</span>~opt~</span>`}`

<span class="syntax-def-name">
willSet-didSet-block
</span>
<span class="arrow">
→
</span>`{`<span class="syntactic-cat">[didSet-clause](Declarations.md#didSet-clause)</span><span class="optional"><span class="syntactic-cat">[willSet-clause](Declarations.md#willSet-clause)</span>~opt~</span>`}`

<span class="syntax-def-name">
willSet-clause
</span>
<span class="arrow">
→
</span><span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span>`willSet`<span class="optional"><span class="syntactic-cat">[setter-name](Declarations.md#setter-name)</span>~opt~</span><span class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

<span class="syntax-def-name">
didSet-clause
</span>
<span class="arrow">
→
</span><span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span>`didSet`<span class="optional"><span class="syntactic-cat">[setter-name](Declarations.md#setter-name)</span>~opt~</span><span class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

Grammar of a type alias declaration

<span class="syntax-def-name">
typealias-declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[typealias-head](Declarations.md#typealias-head)</span><span class="syntactic-cat">[typealias-assignment](Declarations.md#typealias-assignment)</span>

<span class="syntax-def-name">
typealias-head
</span>
<span class="arrow">
→
</span><span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span class="optional"><span class="syntactic-cat">[access-level-modifier](Declarations.md#access-level-modifier)</span>~opt~</span>`typealias`<span class="syntactic-cat">[typealias-name](Declarations.md#typealias-name)</span>

<span class="syntax-def-name">
typealias-name
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

<span class="syntax-def-name">
typealias-assignment
</span>
<span class="arrow">
→
</span>`=`<span class="syntactic-cat">[type](Types.md#type)</span>

Grammar of a function declaration

<span class="syntax-def-name">
function-declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[function-head](Declarations.md#function-head)</span><span class="syntactic-cat">[function-name](Declarations.md#function-name)</span><span class="optional"><span class="syntactic-cat">[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)</span>~opt~</span><span class="syntactic-cat">[function-signature](Declarations.md#function-signature)</span><span class="optional"><span class="syntactic-cat">[function-body](Declarations.md#function-body)</span>~opt~</span>

<span class="syntax-def-name">
function-head
</span>
<span class="arrow">
→
</span><span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span class="optional"><span class="syntactic-cat">[declaration-modifiers](Declarations.md#declaration-modifiers)</span>~opt~</span>`func`

<span class="syntax-def-name">
function-name
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>
</span><span class="alternative">
<span class="syntactic-cat">[operator](LexicalStructure.md#operator)</span>
</span>

<span class="syntax-def-name">
function-signature
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[parameter-clause](Declarations.md#parameter-clause)</span><span class="optional">`throws`~opt~</span><span class="optional"><span class="syntactic-cat">[function-result](Declarations.md#function-result)</span>~opt~</span>

<span class="syntax-def-name">
function-signature
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[parameter-clause](Declarations.md#parameter-clause)</span>`rethrows`<span class="optional"><span class="syntactic-cat">[function-result](Declarations.md#function-result)</span>~opt~</span>

<span class="syntax-def-name">
function-result
</span>
<span class="arrow">
→
</span>`->`<span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span class="syntactic-cat">[type](Types.md#type)</span>

<span class="syntax-def-name">
function-body
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

<span class="syntax-def-name">
parameter-clause
</span>
<span class="arrow">
→
</span><span class="alternative">
`(``)`
</span><span class="alternative">
`(`<span class="syntactic-cat">[parameter-list](Declarations.md#parameter-list)</span>`)`
</span>

<span class="syntax-def-name">
parameter-list
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[parameter](Declarations.md#parameter)</span>
</span><span class="alternative">
<span class="syntactic-cat">[parameter](Declarations.md#parameter)</span>`,`<span class="syntactic-cat">[parameter-list](Declarations.md#parameter-list)</span>
</span>

<span class="syntax-def-name">
parameter
</span>
<span class="arrow">
→
</span><span class="optional">`let`~opt~</span><span class="optional"><span class="syntactic-cat">[external-parameter-name](Declarations.md#external-parameter-name)</span>~opt~</span><span class="syntactic-cat">[local-parameter-name](Declarations.md#local-parameter-name)</span><span class="syntactic-cat">[type-annotation](Types.md#type-annotation)</span><span class="optional"><span class="syntactic-cat">[default-argument-clause](Declarations.md#default-argument-clause)</span>~opt~</span>

<span class="syntax-def-name">
parameter
</span>
<span class="arrow">
→
</span>`inout`<span class="optional"><span class="syntactic-cat">[external-parameter-name](Declarations.md#external-parameter-name)</span>~opt~</span><span class="syntactic-cat">[local-parameter-name](Declarations.md#local-parameter-name)</span><span class="syntactic-cat">[type-annotation](Types.md#type-annotation)</span>

<span class="syntax-def-name">
parameter
</span>
<span class="arrow">
→
</span><span class="optional"><span class="syntactic-cat">[external-parameter-name](Declarations.md#external-parameter-name)</span>~opt~</span><span class="syntactic-cat">[local-parameter-name](Declarations.md#local-parameter-name)</span><span class="syntactic-cat">[type-annotation](Types.md#type-annotation)</span>`...`

<span class="syntax-def-name">
external-parameter-name
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>
</span><span class="alternative">
`_`
</span>

<span class="syntax-def-name">
local-parameter-name
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>
</span><span class="alternative">
`_`
</span>

<span class="syntax-def-name">
default-argument-clause
</span>
<span class="arrow">
→
</span>`=`<span class="syntactic-cat">[expression](Expressions.md#expression)</span>

Grammar of an enumeration declaration

<span class="syntax-def-name">
enum-declaration
</span>
<span class="arrow">
→
</span><span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span class="optional"><span class="syntactic-cat">[access-level-modifier](Declarations.md#access-level-modifier)</span>~opt~</span><span class="syntactic-cat">[union-style-enum](Declarations.md#union-style-enum)</span>

<span class="syntax-def-name">
enum-declaration
</span>
<span class="arrow">
→
</span><span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span class="optional"><span class="syntactic-cat">[access-level-modifier](Declarations.md#access-level-modifier)</span>~opt~</span><span class="syntactic-cat">[raw-value-style-enum](Declarations.md#raw-value-style-enum)</span>

<span class="syntax-def-name">
union-style-enum
</span>
<span class="arrow">
→
</span><span class="optional">`indirect`~opt~</span>`enum`<span class="syntactic-cat">[enum-name](Declarations.md#enum-name)</span><span class="optional"><span class="syntactic-cat">[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)</span>~opt~</span><span class="optional"><span class="syntactic-cat">[type-inheritance-clause](Types.md#type-inheritance-clause)</span>~opt~</span>`{`<span class="optional"><span class="syntactic-cat">[union-style-enum-members](Declarations.md#union-style-enum-members)</span>~opt~</span>`}`

<span class="syntax-def-name">
union-style-enum-members
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[union-style-enum-member](Declarations.md#union-style-enum-member)</span><span class="optional"><span class="syntactic-cat">[union-style-enum-members](Declarations.md#union-style-enum-members)</span>~opt~</span>

<span class="syntax-def-name">
union-style-enum-member
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[declaration](Declarations.md#declaration)</span>
</span><span class="alternative">
<span class="syntactic-cat">[union-style-enum-case-clause](Declarations.md#union-style-enum-case-clause)</span>
</span>

<span class="syntax-def-name">
union-style-enum-case-clause
</span>
<span class="arrow">
→
</span><span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span class="optional">`indirect`~opt~</span>`case`<span class="syntactic-cat">[union-style-enum-case-list](Declarations.md#union-style-enum-case-list)</span>

<span class="syntax-def-name">
union-style-enum-case-list
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[union-style-enum-case](Declarations.md#union-style-enum-case)</span>
</span><span class="alternative">
<span class="syntactic-cat">[union-style-enum-case](Declarations.md#union-style-enum-case)</span>`,`<span class="syntactic-cat">[union-style-enum-case-list](Declarations.md#union-style-enum-case-list)</span>
</span>

<span class="syntax-def-name">
union-style-enum-case
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[enum-case-name](Declarations.md#enum-case-name)</span><span class="optional"><span class="syntactic-cat">[tuple-type](Types.md#tuple-type)</span>~opt~</span>

<span class="syntax-def-name">
enum-name
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

<span class="syntax-def-name">
enum-case-name
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

<span class="syntax-def-name">
raw-value-style-enum
</span>
<span class="arrow">
→
</span>`enum`<span class="syntactic-cat">[enum-name](Declarations.md#enum-name)</span><span class="optional"><span class="syntactic-cat">[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)</span>~opt~</span><span class="syntactic-cat">[type-inheritance-clause](Types.md#type-inheritance-clause)</span>`{`<span class="syntactic-cat">[raw-value-style-enum-members](Declarations.md#raw-value-style-enum-members)</span>`}`

<span class="syntax-def-name">
raw-value-style-enum-members
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[raw-value-style-enum-member](Declarations.md#raw-value-style-enum-member)</span><span class="optional"><span class="syntactic-cat">[raw-value-style-enum-members](Declarations.md#raw-value-style-enum-members)</span>~opt~</span>

<span class="syntax-def-name">
raw-value-style-enum-member
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[declaration](Declarations.md#declaration)</span>
</span><span class="alternative">
<span class="syntactic-cat">[raw-value-style-enum-case-clause](Declarations.md#raw-value-style-enum-case-clause)</span>
</span>

<span class="syntax-def-name">
raw-value-style-enum-case-clause
</span>
<span class="arrow">
→
</span><span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span>`case`<span class="syntactic-cat">[raw-value-style-enum-case-list](Declarations.md#raw-value-style-enum-case-list)</span>

<span class="syntax-def-name">
raw-value-style-enum-case-list
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[raw-value-style-enum-case](Declarations.md#raw-value-style-enum-case)</span>
</span><span class="alternative">
<span class="syntactic-cat">[raw-value-style-enum-case](Declarations.md#raw-value-style-enum-case)</span>`,`<span class="syntactic-cat">[raw-value-style-enum-case-list](Declarations.md#raw-value-style-enum-case-list)</span>
</span>

<span class="syntax-def-name">
raw-value-style-enum-case
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[enum-case-name](Declarations.md#enum-case-name)</span><span class="optional"><span class="syntactic-cat">[raw-value-assignment](Declarations.md#raw-value-assignment)</span>~opt~</span>

<span class="syntax-def-name">
raw-value-assignment
</span>
<span class="arrow">
→
</span>`=`<span class="syntactic-cat">[raw-value-literal](Declarations.md#raw-value-literal)</span>

<span class="syntax-def-name">
raw-value-literal
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[numeric-literal](LexicalStructure.md#numeric-literal)</span>
</span><span class="alternative">
<span class="syntactic-cat">[static-string-literal](LexicalStructure.md#static-string-literal)</span>
</span><span class="alternative">
<span class="syntactic-cat">[boolean-literal](LexicalStructure.md#boolean-literal)</span>
</span>

Grammar of a structure declaration

<span class="syntax-def-name">
struct-declaration
</span>
<span class="arrow">
→
</span><span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span class="optional"><span class="syntactic-cat">[access-level-modifier](Declarations.md#access-level-modifier)</span>~opt~</span>`struct`<span class="syntactic-cat">[struct-name](Declarations.md#struct-name)</span><span class="optional"><span class="syntactic-cat">[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)</span>~opt~</span><span class="optional"><span class="syntactic-cat">[type-inheritance-clause](Types.md#type-inheritance-clause)</span>~opt~</span><span class="syntactic-cat">[struct-body](Declarations.md#struct-body)</span>

<span class="syntax-def-name">
struct-name
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

<span class="syntax-def-name">
struct-body
</span>
<span class="arrow">
→
</span>`{`<span class="optional"><span class="syntactic-cat">[declarations](Declarations.md#declarations)</span>~opt~</span>`}`

Grammar of a class declaration

<span class="syntax-def-name">
class-declaration
</span>
<span class="arrow">
→
</span><span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span class="optional"><span class="syntactic-cat">[access-level-modifier](Declarations.md#access-level-modifier)</span>~opt~</span>`class`<span class="syntactic-cat">[class-name](Declarations.md#class-name)</span><span class="optional"><span class="syntactic-cat">[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)</span>~opt~</span><span class="optional"><span class="syntactic-cat">[type-inheritance-clause](Types.md#type-inheritance-clause)</span>~opt~</span><span class="syntactic-cat">[class-body](Declarations.md#class-body)</span>

<span class="syntax-def-name">
class-name
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

<span class="syntax-def-name">
class-body
</span>
<span class="arrow">
→
</span>`{`<span class="optional"><span class="syntactic-cat">[declarations](Declarations.md#declarations)</span>~opt~</span>`}`

Grammar of a protocol declaration

<span class="syntax-def-name">
protocol-declaration
</span>
<span class="arrow">
→
</span><span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span class="optional"><span class="syntactic-cat">[access-level-modifier](Declarations.md#access-level-modifier)</span>~opt~</span>`protocol`<span class="syntactic-cat">[protocol-name](Declarations.md#protocol-name)</span><span class="optional"><span class="syntactic-cat">[type-inheritance-clause](Types.md#type-inheritance-clause)</span>~opt~</span><span class="syntactic-cat">[protocol-body](Declarations.md#protocol-body)</span>

<span class="syntax-def-name">
protocol-name
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

<span class="syntax-def-name">
protocol-body
</span>
<span class="arrow">
→
</span>`{`<span class="optional"><span class="syntactic-cat">[protocol-member-declarations](Declarations.md#protocol-member-declarations)</span>~opt~</span>`}`

<span class="syntax-def-name">
protocol-member-declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[protocol-property-declaration](Declarations.md#protocol-property-declaration)</span>

<span class="syntax-def-name">
protocol-member-declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[protocol-method-declaration](Declarations.md#protocol-method-declaration)</span>

<span class="syntax-def-name">
protocol-member-declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[protocol-initializer-declaration](Declarations.md#protocol-initializer-declaration)</span>

<span class="syntax-def-name">
protocol-member-declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[protocol-subscript-declaration](Declarations.md#protocol-subscript-declaration)</span>

<span class="syntax-def-name">
protocol-member-declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[protocol-associated-type-declaration](Declarations.md#protocol-associated-type-declaration)</span>

<span class="syntax-def-name">
protocol-member-declarations
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[protocol-member-declaration](Declarations.md#protocol-member-declaration)</span><span class="optional"><span class="syntactic-cat">[protocol-member-declarations](Declarations.md#protocol-member-declarations)</span>~opt~</span>

Grammar of a protocol property declaration

<span class="syntax-def-name">
protocol-property-declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[variable-declaration-head](Declarations.md#variable-declaration-head)</span><span class="syntactic-cat">[variable-name](Declarations.md#variable-name)</span><span class="syntactic-cat">[type-annotation](Types.md#type-annotation)</span><span class="syntactic-cat">[getter-setter-keyword-block](Declarations.md#getter-setter-keyword-block)</span>

Grammar of a protocol method declaration

<span class="syntax-def-name">
protocol-method-declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[function-head](Declarations.md#function-head)</span><span class="syntactic-cat">[function-name](Declarations.md#function-name)</span><span class="optional"><span class="syntactic-cat">[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)</span>~opt~</span><span class="syntactic-cat">[function-signature](Declarations.md#function-signature)</span>

Grammar of a protocol initializer declaration

<span class="syntax-def-name">
protocol-initializer-declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[initializer-head](Declarations.md#initializer-head)</span><span class="optional"><span class="syntactic-cat">[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)</span>~opt~</span><span class="syntactic-cat">[parameter-clause](Declarations.md#parameter-clause)</span><span class="optional">`throws`~opt~</span>

<span class="syntax-def-name">
protocol-initializer-declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[initializer-head](Declarations.md#initializer-head)</span><span class="optional"><span class="syntactic-cat">[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)</span>~opt~</span><span class="syntactic-cat">[parameter-clause](Declarations.md#parameter-clause)</span>`rethrows`

Grammar of a protocol subscript declaration

<span class="syntax-def-name">
protocol-subscript-declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[subscript-head](Declarations.md#subscript-head)</span><span class="syntactic-cat">[subscript-result](Declarations.md#subscript-result)</span><span class="syntactic-cat">[getter-setter-keyword-block](Declarations.md#getter-setter-keyword-block)</span>

Grammar of a protocol associated type declaration

<span class="syntax-def-name">
protocol-associated-type-declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[typealias-head](Declarations.md#typealias-head)</span><span class="optional"><span class="syntactic-cat">[type-inheritance-clause](Types.md#type-inheritance-clause)</span>~opt~</span><span class="optional"><span class="syntactic-cat">[typealias-assignment](Declarations.md#typealias-assignment)</span>~opt~</span>

Grammar of an initializer declaration

<span class="syntax-def-name">
initializer-declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[initializer-head](Declarations.md#initializer-head)</span><span class="optional"><span class="syntactic-cat">[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)</span>~opt~</span><span class="syntactic-cat">[parameter-clause](Declarations.md#parameter-clause)</span><span class="optional">`throws`~opt~</span><span class="syntactic-cat">[initializer-body](Declarations.md#initializer-body)</span>

<span class="syntax-def-name">
initializer-declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[initializer-head](Declarations.md#initializer-head)</span><span class="optional"><span class="syntactic-cat">[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)</span>~opt~</span><span class="syntactic-cat">[parameter-clause](Declarations.md#parameter-clause)</span>`rethrows`<span class="syntactic-cat">[initializer-body](Declarations.md#initializer-body)</span>

<span class="syntax-def-name">
initializer-head
</span>
<span class="arrow">
→
</span><span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span class="optional"><span class="syntactic-cat">[declaration-modifiers](Declarations.md#declaration-modifiers)</span>~opt~</span>`init`

<span class="syntax-def-name">
initializer-head
</span>
<span class="arrow">
→
</span><span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span class="optional"><span class="syntactic-cat">[declaration-modifiers](Declarations.md#declaration-modifiers)</span>~opt~</span>`init``?`

<span class="syntax-def-name">
initializer-head
</span>
<span class="arrow">
→
</span><span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span class="optional"><span class="syntactic-cat">[declaration-modifiers](Declarations.md#declaration-modifiers)</span>~opt~</span>`init``!`

<span class="syntax-def-name">
initializer-body
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

Grammar of a deinitializer declaration

<span class="syntax-def-name">
deinitializer-declaration
</span>
<span class="arrow">
→
</span><span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span>`deinit`<span class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

Grammar of an extension declaration

<span class="syntax-def-name">
extension-declaration
</span>
<span class="arrow">
→
</span><span class="optional"><span class="syntactic-cat">[access-level-modifier](Declarations.md#access-level-modifier)</span>~opt~</span>`extension`<span class="syntactic-cat">[type-identifier](Types.md#type-identifier)</span><span class="optional"><span class="syntactic-cat">[type-inheritance-clause](Types.md#type-inheritance-clause)</span>~opt~</span><span class="syntactic-cat">[extension-body](Declarations.md#extension-body)</span>

<span class="syntax-def-name">
extension-body
</span>
<span class="arrow">
→
</span>`{`<span class="optional"><span class="syntactic-cat">[declarations](Declarations.md#declarations)</span>~opt~</span>`}`

Grammar of a subscript declaration

<span class="syntax-def-name">
subscript-declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[subscript-head](Declarations.md#subscript-head)</span><span class="syntactic-cat">[subscript-result](Declarations.md#subscript-result)</span><span class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

<span class="syntax-def-name">
subscript-declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[subscript-head](Declarations.md#subscript-head)</span><span class="syntactic-cat">[subscript-result](Declarations.md#subscript-result)</span><span class="syntactic-cat">[getter-setter-block](Declarations.md#getter-setter-block)</span>

<span class="syntax-def-name">
subscript-declaration
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[subscript-head](Declarations.md#subscript-head)</span><span class="syntactic-cat">[subscript-result](Declarations.md#subscript-result)</span><span class="syntactic-cat">[getter-setter-keyword-block](Declarations.md#getter-setter-keyword-block)</span>

<span class="syntax-def-name">
subscript-head
</span>
<span class="arrow">
→
</span><span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span class="optional"><span class="syntactic-cat">[declaration-modifiers](Declarations.md#declaration-modifiers)</span>~opt~</span>`subscript`<span class="syntactic-cat">[parameter-clause](Declarations.md#parameter-clause)</span>

<span class="syntax-def-name">
subscript-result
</span>
<span class="arrow">
→
</span>`->`<span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span class="syntactic-cat">[type](Types.md#type)</span>

Grammar of an operator declaration

<span class="syntax-def-name">
operator-declaration
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[prefix-operator-declaration](Declarations.md#prefix-operator-declaration)</span>
</span><span class="alternative">
<span class="syntactic-cat">[postfix-operator-declaration](Declarations.md#postfix-operator-declaration)</span>
</span><span class="alternative">
<span class="syntactic-cat">[infix-operator-declaration](Declarations.md#infix-operator-declaration)</span>
</span>

<span class="syntax-def-name">
prefix-operator-declaration
</span>
<span class="arrow">
→
</span>`prefix``operator`<span class="syntactic-cat">[operator](LexicalStructure.md#operator)</span>`{``}`

<span class="syntax-def-name">
postfix-operator-declaration
</span>
<span class="arrow">
→
</span>`postfix``operator`<span class="syntactic-cat">[operator](LexicalStructure.md#operator)</span>`{``}`

<span class="syntax-def-name">
infix-operator-declaration
</span>
<span class="arrow">
→
</span>`infix``operator`<span class="syntactic-cat">[operator](LexicalStructure.md#operator)</span>`{`<span class="optional"><span class="syntactic-cat">[infix-operator-attributes](Declarations.md#infix-operator-attributes)</span>~opt~</span>`}`

<span class="syntax-def-name">
infix-operator-attributes
</span>
<span class="arrow">
→
</span><span class="optional"><span class="syntactic-cat">[precedence-clause](Declarations.md#precedence-clause)</span>~opt~</span><span class="optional"><span class="syntactic-cat">[associativity-clause](Declarations.md#associativity-clause)</span>~opt~</span>

<span class="syntax-def-name">
precedence-clause
</span>
<span class="arrow">
→
</span>`precedence`<span class="syntactic-cat">[precedence-level](Declarations.md#precedence-level)</span>

<span class="syntax-def-name">
precedence-level
</span>
<span class="arrow">
→
</span><span class="text-description">A decimal integer between 0 and 255, inclusive</span>

<span class="syntax-def-name">
associativity-clause
</span>
<span class="arrow">
→
</span>`associativity`<span class="syntactic-cat">[associativity](Declarations.md#associativity)</span>

<span class="syntax-def-name">
associativity
</span>
<span class="arrow">
→
</span><span class="alternative">
`left`
</span><span class="alternative">
`right`
</span><span class="alternative">
`none`
</span>

Grammar of a declaration modifier

<span class="syntax-def-name">
declaration-modifier
</span>
<span class="arrow">
→
</span><span class="alternative">
`class`
</span><span class="alternative">
`convenience`
</span><span class="alternative">
`dynamic`
</span><span class="alternative">
`final`
</span><span class="alternative">
`infix`
</span><span class="alternative">
`lazy`
</span><span class="alternative">
`mutating`
</span><span class="alternative">
`nonmutating`
</span><span class="alternative">
`optional`
</span><span class="alternative">
`override`
</span><span class="alternative">
`postfix`
</span><span class="alternative">
`prefix`
</span><span class="alternative">
`required`
</span><span class="alternative">
`static`
</span><span class="alternative">
`unowned`
</span><span class="alternative">
`unowned``(``safe``)`
</span><span class="alternative">
`unowned``(``unsafe``)`
</span><span class="alternative">
`weak`
</span>

<span class="syntax-def-name">
declaration-modifier
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[access-level-modifier](Declarations.md#access-level-modifier)</span>

<span class="syntax-def-name">
declaration-modifiers
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[declaration-modifier](Declarations.md#declaration-modifier)</span><span class="optional"><span class="syntactic-cat">[declaration-modifiers](Declarations.md#declaration-modifiers)</span>~opt~</span>

<span class="syntax-def-name">
access-level-modifier
</span>
<span class="arrow">
→
</span><span class="alternative">
`internal`
</span><span class="alternative">
`internal``(``set``)`
</span>

<span class="syntax-def-name">
access-level-modifier
</span>
<span class="arrow">
→
</span><span class="alternative">
`private`
</span><span class="alternative">
`private``(``set``)`
</span>

<span class="syntax-def-name">
access-level-modifier
</span>
<span class="arrow">
→
</span><span class="alternative">
`public`
</span><span class="alternative">
`public``(``set``)`
</span>

### Patterns 

Grammar of a pattern

<span class="syntax-def-name">
pattern
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[wildcard-pattern](Patterns.md#wildcard-pattern)</span><span class="optional"><span class="syntactic-cat">[type-annotation](Types.md#type-annotation)</span>~opt~</span>

<span class="syntax-def-name">
pattern
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[identifier-pattern](Patterns.md#identifier-pattern)</span><span class="optional"><span class="syntactic-cat">[type-annotation](Types.md#type-annotation)</span>~opt~</span>

<span class="syntax-def-name">
pattern
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[value-binding-pattern](Patterns.md#value-binding-pattern)</span>

<span class="syntax-def-name">
pattern
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[tuple-pattern](Patterns.md#tuple-pattern)</span><span class="optional"><span class="syntactic-cat">[type-annotation](Types.md#type-annotation)</span>~opt~</span>

<span class="syntax-def-name">
pattern
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[enum-case-pattern](Patterns.md#enum-case-pattern)</span>

<span class="syntax-def-name">
pattern
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[optional-pattern](Patterns.md#optional-pattern)</span>

<span class="syntax-def-name">
pattern
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[type-casting-pattern](Patterns.md#type-casting-pattern)</span>

<span class="syntax-def-name">
pattern
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[expression-pattern](Patterns.md#expression-pattern)</span>

Grammar of a wildcard pattern

<span class="syntax-def-name">
wildcard-pattern
</span>
<span class="arrow">
→
</span>`_`

Grammar of an identifier pattern

<span class="syntax-def-name">
identifier-pattern
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

Grammar of a value-binding pattern

<span class="syntax-def-name">
value-binding-pattern
</span>
<span class="arrow">
→
</span>`let`<span class="syntactic-cat">[pattern](Patterns.md#pattern)</span>

Grammar of a tuple pattern

<span class="syntax-def-name">
tuple-pattern
</span>
<span class="arrow">
→
</span>`(`<span class="optional"><span class="syntactic-cat">[tuple-pattern-element-list](Patterns.md#tuple-pattern-element-list)</span>~opt~</span>`)`

<span class="syntax-def-name">
tuple-pattern-element-list
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[tuple-pattern-element](Patterns.md#tuple-pattern-element)</span>
</span><span class="alternative">
<span class="syntactic-cat">[tuple-pattern-element](Patterns.md#tuple-pattern-element)</span>`,`<span class="syntactic-cat">[tuple-pattern-element-list](Patterns.md#tuple-pattern-element-list)</span>
</span>

<span class="syntax-def-name">
tuple-pattern-element
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[pattern](Patterns.md#pattern)</span>

Grammar of an enumeration case pattern

<span class="syntax-def-name">
enum-case-pattern
</span>
<span class="arrow">
→
</span><span class="optional"><span class="syntactic-cat">[type-identifier](Types.md#type-identifier)</span>~opt~</span>`.`<span class="syntactic-cat">[enum-case-name](Declarations.md#enum-case-name)</span><span class="optional"><span class="syntactic-cat">[tuple-pattern](Patterns.md#tuple-pattern)</span>~opt~</span>

Grammar of an optional pattern

<span class="syntax-def-name">
optional-pattern
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[identifier-pattern](Patterns.md#identifier-pattern)</span>`?`

Grammar of a type casting pattern

<span class="syntax-def-name">
type-casting-pattern
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[is-pattern](Patterns.md#is-pattern)</span>
</span><span class="alternative">
<span class="syntactic-cat">[as-pattern](Patterns.md#as-pattern)</span>
</span>

<span class="syntax-def-name">
is-pattern
</span>
<span class="arrow">
→
</span>`is`<span class="syntactic-cat">[type](Types.md#type)</span>

<span class="syntax-def-name">
as-pattern
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[pattern](Patterns.md#pattern)</span>`as`<span class="syntactic-cat">[type](Types.md#type)</span>

Grammar of an expression pattern

<span class="syntax-def-name">
expression-pattern
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[expression](Expressions.md#expression)</span>

### Attributes 

Grammar of an attribute

<span class="syntax-def-name">
attribute
</span>
<span class="arrow">
→
</span>`@`<span class="syntactic-cat">[attribute-name](Attributes.md#attribute-name)</span><span class="optional"><span class="syntactic-cat">[attribute-argument-clause](Attributes.md#attribute-argument-clause)</span>~opt~</span>

<span class="syntax-def-name">
attribute-name
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

<span class="syntax-def-name">
attribute-argument-clause
</span>
<span class="arrow">
→
</span>`(`<span class="optional"><span class="syntactic-cat">[balanced-tokens](Attributes.md#balanced-tokens)</span>~opt~</span>`)`

<span class="syntax-def-name">
attributes
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[attribute](Attributes.md#attribute)</span><span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span>

<span class="syntax-def-name">
balanced-tokens
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[balanced-token](Attributes.md#balanced-token)</span><span class="optional"><span class="syntactic-cat">[balanced-tokens](Attributes.md#balanced-tokens)</span>~opt~</span>

<span class="syntax-def-name">
balanced-token
</span>
<span class="arrow">
→
</span>`(`<span class="optional"><span class="syntactic-cat">[balanced-tokens](Attributes.md#balanced-tokens)</span>~opt~</span>`)`

<span class="syntax-def-name">
balanced-token
</span>
<span class="arrow">
→
</span>`[`<span class="optional"><span class="syntactic-cat">[balanced-tokens](Attributes.md#balanced-tokens)</span>~opt~</span>`]`

<span class="syntax-def-name">
balanced-token
</span>
<span class="arrow">
→
</span>`{`<span class="optional"><span class="syntactic-cat">[balanced-tokens](Attributes.md#balanced-tokens)</span>~opt~</span>`}`

<span class="syntax-def-name">
balanced-token
</span>
<span class="arrow">
→
</span><span class="text-description">Any identifier, keyword, literal, or operator</span>

<span class="syntax-def-name">
balanced-token
</span>
<span class="arrow">
→
</span><span class="text-description">Any punctuation except `(`, `)`, `[`, `]`, `{`, or `}`</span>

### Expressions 

Grammar of an expression

<span class="syntax-def-name">
expression
</span>
<span class="arrow">
→
</span><span class="optional"><span class="syntactic-cat">[try-operator](Expressions.md#try-operator)</span>~opt~</span><span class="syntactic-cat">[prefix-expression](Expressions.md#prefix-expression)</span><span class="optional"><span class="syntactic-cat">[binary-expressions](Expressions.md#binary-expressions)</span>~opt~</span>

<span class="syntax-def-name">
expression-list
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[expression](Expressions.md#expression)</span>
</span><span class="alternative">
<span class="syntactic-cat">[expression](Expressions.md#expression)</span>`,`<span class="syntactic-cat">[expression-list](Expressions.md#expression-list)</span>
</span>

Grammar of a prefix expression

<span class="syntax-def-name">
prefix-expression
</span>
<span class="arrow">
→
</span><span class="optional"><span class="syntactic-cat">[prefix-operator](LexicalStructure.md#prefix-operator)</span>~opt~</span><span class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span>

<span class="syntax-def-name">
prefix-expression
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[in-out-expression](Expressions.md#in-out-expression)</span>

<span class="syntax-def-name">
in-out-expression
</span>
<span class="arrow">
→
</span>`&`<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

Grammar of a try expression

<span class="syntax-def-name">
try-operator
</span>
<span class="arrow">
→
</span><span class="alternative">
`try`
</span><span class="alternative">
`try``?`
</span><span class="alternative">
`try``!`
</span>

Grammar of a binary expression

<span class="syntax-def-name">
binary-expression
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[binary-operator](LexicalStructure.md#binary-operator)</span><span class="syntactic-cat">[prefix-expression](Expressions.md#prefix-expression)</span>

<span class="syntax-def-name">
binary-expression
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[assignment-operator](Expressions.md#assignment-operator)</span><span class="optional"><span class="syntactic-cat">[try-operator](Expressions.md#try-operator)</span>~opt~</span><span class="syntactic-cat">[prefix-expression](Expressions.md#prefix-expression)</span>

<span class="syntax-def-name">
binary-expression
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[conditional-operator](Expressions.md#conditional-operator)</span><span class="optional"><span class="syntactic-cat">[try-operator](Expressions.md#try-operator)</span>~opt~</span><span class="syntactic-cat">[prefix-expression](Expressions.md#prefix-expression)</span>

<span class="syntax-def-name">
binary-expression
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[type-casting-operator](Expressions.md#type-casting-operator)</span>

<span class="syntax-def-name">
binary-expressions
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[binary-expression](Expressions.md#binary-expression)</span><span class="optional"><span class="syntactic-cat">[binary-expressions](Expressions.md#binary-expressions)</span>~opt~</span>

Grammar of an assignment operator

<span class="syntax-def-name">
assignment-operator
</span>
<span class="arrow">
→
</span>`=`

Grammar of a conditional operator

<span class="syntax-def-name">
conditional-operator
</span>
<span class="arrow">
→
</span>`?`<span class="optional"><span class="syntactic-cat">[try-operator](Expressions.md#try-operator)</span>~opt~</span><span class="syntactic-cat">[expression](Expressions.md#expression)</span>`:`

Grammar of a type-casting operator

<span class="syntax-def-name">
type-casting-operator
</span>
<span class="arrow">
→
</span>`is`<span class="syntactic-cat">[type](Types.md#type)</span>

<span class="syntax-def-name">
type-casting-operator
</span>
<span class="arrow">
→
</span>`as`<span class="syntactic-cat">[type](Types.md#type)</span>

<span class="syntax-def-name">
type-casting-operator
</span>
<span class="arrow">
→
</span>`as``?`<span class="syntactic-cat">[type](Types.md#type)</span>

<span class="syntax-def-name">
type-casting-operator
</span>
<span class="arrow">
→
</span>`as``!`<span class="syntactic-cat">[type](Types.md#type)</span>

Grammar of a primary expression

<span class="syntax-def-name">
primary-expression
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span><span class="optional"><span class="syntactic-cat">[generic-argument-clause](GenericParametersAndArguments.md#generic-argument-clause)</span>~opt~</span>

<span class="syntax-def-name">
primary-expression
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[literal-expression](Expressions.md#literal-expression)</span>

<span class="syntax-def-name">
primary-expression
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[self-expression](Expressions.md#self-expression)</span>

<span class="syntax-def-name">
primary-expression
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[superclass-expression](Expressions.md#superclass-expression)</span>

<span class="syntax-def-name">
primary-expression
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[closure-expression](Expressions.md#closure-expression)</span>

<span class="syntax-def-name">
primary-expression
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[parenthesized-expression](Expressions.md#parenthesized-expression)</span>

<span class="syntax-def-name">
primary-expression
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[implicit-member-expression](Expressions.md#implicit-member-expression)</span>

<span class="syntax-def-name">
primary-expression
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[wildcard-expression](Expressions.md#wildcard-expression)</span>

Grammar of a literal expression

<span class="syntax-def-name">
literal-expression
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[literal](LexicalStructure.md#literal)</span>

<span class="syntax-def-name">
literal-expression
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[array-literal](Expressions.md#array-literal)</span>
</span><span class="alternative">
<span class="syntactic-cat">[dictionary-literal](Expressions.md#dictionary-literal)</span>
</span>

<span class="syntax-def-name">
literal-expression
</span>
<span class="arrow">
→
</span><span class="alternative">
`__FILE__`
</span><span class="alternative">
`__LINE__`
</span><span class="alternative">
`__COLUMN__`
</span><span class="alternative">
`__FUNCTION__`
</span>

<span class="syntax-def-name">
array-literal
</span>
<span class="arrow">
→
</span>`[`<span class="optional"><span class="syntactic-cat">[array-literal-items](Expressions.md#array-literal-items)</span>~opt~</span>`]`

<span class="syntax-def-name">
array-literal-items
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[array-literal-item](Expressions.md#array-literal-item)</span><span class="optional">`,`~opt~</span>
</span><span class="alternative">
<span class="syntactic-cat">[array-literal-item](Expressions.md#array-literal-item)</span>`,`<span class="syntactic-cat">[array-literal-items](Expressions.md#array-literal-items)</span>
</span>

<span class="syntax-def-name">
array-literal-item
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[expression](Expressions.md#expression)</span>

<span class="syntax-def-name">
dictionary-literal
</span>
<span class="arrow">
→
</span><span class="alternative">
`[`<span class="syntactic-cat">[dictionary-literal-items](Expressions.md#dictionary-literal-items)</span>`]`
</span><span class="alternative">
`[``:``]`
</span>

<span class="syntax-def-name">
dictionary-literal-items
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[dictionary-literal-item](Expressions.md#dictionary-literal-item)</span><span class="optional">`,`~opt~</span>
</span><span class="alternative">
<span class="syntactic-cat">[dictionary-literal-item](Expressions.md#dictionary-literal-item)</span>`,`<span class="syntactic-cat">[dictionary-literal-items](Expressions.md#dictionary-literal-items)</span>
</span>

<span class="syntax-def-name">
dictionary-literal-item
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[expression](Expressions.md#expression)</span>`:`<span class="syntactic-cat">[expression](Expressions.md#expression)</span>

Grammar of a self expression

<span class="syntax-def-name">
self-expression
</span>
<span class="arrow">
→
</span><span class="alternative">
`self`
</span><span class="alternative">
<span class="syntactic-cat">[self-method-expression](Expressions.md#self-method-expression)</span>
</span><span class="alternative">
<span class="syntactic-cat">[self-subscript-expression](Expressions.md#self-subscript-expression)</span>
</span><span class="alternative">
<span class="syntactic-cat">[self-initializer-expression](Expressions.md#self-initializer-expression)</span>
</span>

<span class="syntax-def-name">
self-method-expression
</span>
<span class="arrow">
→
</span>`self``.`<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

<span class="syntax-def-name">
self-subscript-expression
</span>
<span class="arrow">
→
</span>`self``[`<span class="syntactic-cat">[expression-list](Expressions.md#expression-list)</span>`]`

<span class="syntax-def-name">
self-initializer-expression
</span>
<span class="arrow">
→
</span>`self``.``init`

Grammar of a superclass expression

<span class="syntax-def-name">
superclass-expression
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[superclass-method-expression](Expressions.md#superclass-method-expression)</span>
</span><span class="alternative">
<span class="syntactic-cat">[superclass-subscript-expression](Expressions.md#superclass-subscript-expression)</span>
</span><span class="alternative">
<span class="syntactic-cat">[superclass-initializer-expression](Expressions.md#superclass-initializer-expression)</span>
</span>

<span class="syntax-def-name">
superclass-method-expression
</span>
<span class="arrow">
→
</span>`super``.`<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

<span class="syntax-def-name">
superclass-subscript-expression
</span>
<span class="arrow">
→
</span>`super``[`<span class="syntactic-cat">[expression-list](Expressions.md#expression-list)</span>`]`

<span class="syntax-def-name">
superclass-initializer-expression
</span>
<span class="arrow">
→
</span>`super``.``init`

Grammar of a closure expression

<span class="syntax-def-name">
closure-expression
</span>
<span class="arrow">
→
</span>`{`<span class="optional"><span class="syntactic-cat">[closure-signature](Expressions.md#closure-signature)</span>~opt~</span><span class="syntactic-cat">[statements](Statements.md#statements)</span>`}`

<span class="syntax-def-name">
closure-signature
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[parameter-clause](Declarations.md#parameter-clause)</span><span class="optional"><span class="syntactic-cat">[function-result](Declarations.md#function-result)</span>~opt~</span>`in`

<span class="syntax-def-name">
closure-signature
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[identifier-list](LexicalStructure.md#identifier-list)</span><span class="optional"><span class="syntactic-cat">[function-result](Declarations.md#function-result)</span>~opt~</span>`in`

<span class="syntax-def-name">
closure-signature
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[capture-list](Expressions.md#capture-list)</span><span class="syntactic-cat">[parameter-clause](Declarations.md#parameter-clause)</span><span class="optional"><span class="syntactic-cat">[function-result](Declarations.md#function-result)</span>~opt~</span>`in`

<span class="syntax-def-name">
closure-signature
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[capture-list](Expressions.md#capture-list)</span><span class="syntactic-cat">[identifier-list](LexicalStructure.md#identifier-list)</span><span class="optional"><span class="syntactic-cat">[function-result](Declarations.md#function-result)</span>~opt~</span>`in`

<span class="syntax-def-name">
closure-signature
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[capture-list](Expressions.md#capture-list)</span>`in`

<span class="syntax-def-name">
capture-list
</span>
<span class="arrow">
→
</span>`[`<span class="syntactic-cat">[capture-list-items](Expressions.md#capture-list-items)</span>`]`

<span class="syntax-def-name">
capture-list-items
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[capture-list-item](Expressions.md#capture-list-item)</span>
</span><span class="alternative">
<span class="syntactic-cat">[capture-list-item](Expressions.md#capture-list-item)</span>`,`<span class="syntactic-cat">[capture-list-items](Expressions.md#capture-list-items)</span>
</span>

<span class="syntax-def-name">
capture-list-item
</span>
<span class="arrow">
→
</span><span class="optional"><span class="syntactic-cat">[capture-specifier](Expressions.md#capture-specifier)</span>~opt~</span><span class="syntactic-cat">[expression](Expressions.md#expression)</span>

<span class="syntax-def-name">
capture-specifier
</span>
<span class="arrow">
→
</span><span class="alternative">
`weak`
</span><span class="alternative">
`unowned`
</span><span class="alternative">
`unowned(safe)`
</span><span class="alternative">
`unowned(unsafe)`
</span>

Grammar of a implicit member expression

<span class="syntax-def-name">
implicit-member-expression
</span>
<span class="arrow">
→
</span>`.`<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

Grammar of a parenthesized expression

<span class="syntax-def-name">
parenthesized-expression
</span>
<span class="arrow">
→
</span>`(`<span class="optional"><span class="syntactic-cat">[expression-element-list](Expressions.md#expression-element-list)</span>~opt~</span>`)`

<span class="syntax-def-name">
expression-element-list
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[expression-element](Expressions.md#expression-element)</span>
</span><span class="alternative">
<span class="syntactic-cat">[expression-element](Expressions.md#expression-element)</span>`,`<span class="syntactic-cat">[expression-element-list](Expressions.md#expression-element-list)</span>
</span>

<span class="syntax-def-name">
expression-element
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[expression](Expressions.md#expression)</span>
</span><span class="alternative">
<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>`:`<span class="syntactic-cat">[expression](Expressions.md#expression)</span>
</span>

Grammar of a wildcard expression

<span class="syntax-def-name">
wildcard-expression
</span>
<span class="arrow">
→
</span>`_`

Grammar of a postfix expression

<span class="syntax-def-name">
postfix-expression
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[primary-expression](Expressions.md#primary-expression)</span>

<span class="syntax-def-name">
postfix-expression
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span><span class="syntactic-cat">[postfix-operator](LexicalStructure.md#postfix-operator)</span>

<span class="syntax-def-name">
postfix-expression
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[function-call-expression](Expressions.md#function-call-expression)</span>

<span class="syntax-def-name">
postfix-expression
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[initializer-expression](Expressions.md#initializer-expression)</span>

<span class="syntax-def-name">
postfix-expression
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[explicit-member-expression](Expressions.md#explicit-member-expression)</span>

<span class="syntax-def-name">
postfix-expression
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[postfix-self-expression](Expressions.md#postfix-self-expression)</span>

<span class="syntax-def-name">
postfix-expression
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[dynamic-type-expression](Expressions.md#dynamic-type-expression)</span>

<span class="syntax-def-name">
postfix-expression
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[subscript-expression](Expressions.md#subscript-expression)</span>

<span class="syntax-def-name">
postfix-expression
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[forced-value-expression](Expressions.md#forced-value-expression)</span>

<span class="syntax-def-name">
postfix-expression
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[optional-chaining-expression](Expressions.md#optional-chaining-expression)</span>

Grammar of a function call expression

<span class="syntax-def-name">
function-call-expression
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span><span class="syntactic-cat">[parenthesized-expression](Expressions.md#parenthesized-expression)</span>

<span class="syntax-def-name">
function-call-expression
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span><span class="optional"><span class="syntactic-cat">[parenthesized-expression](Expressions.md#parenthesized-expression)</span>~opt~</span><span class="syntactic-cat">[trailing-closure](Expressions.md#trailing-closure)</span>

<span class="syntax-def-name">
trailing-closure
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[closure-expression](Expressions.md#closure-expression)</span>

Grammar of an initializer expression

<span class="syntax-def-name">
initializer-expression
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span>`.``init`

Grammar of an explicit member expression

<span class="syntax-def-name">
explicit-member-expression
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span>`.`<span class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)</span>

<span class="syntax-def-name">
explicit-member-expression
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span>`.`<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span><span class="optional"><span class="syntactic-cat">[generic-argument-clause](GenericParametersAndArguments.md#generic-argument-clause)</span>~opt~</span>

Grammar of a self expression

<span class="syntax-def-name">
postfix-self-expression
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span>`.``self`

Grammar of a dynamic type expression

<span class="syntax-def-name">
dynamic-type-expression
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span>`.``dynamicType`

Grammar of a subscript expression

<span class="syntax-def-name">
subscript-expression
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span>`[`<span class="syntactic-cat">[expression-list](Expressions.md#expression-list)</span>`]`

Grammar of a forced-value expression

<span class="syntax-def-name">
forced-value-expression
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span>`!`

Grammar of an optional-chaining expression

<span class="syntax-def-name">
optional-chaining-expression
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span>`?`

### Lexical Structure 

Grammar of an identifier

<span class="syntax-def-name">
identifier
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[identifier-head](LexicalStructure.md#identifier-head)</span><span class="optional"><span class="syntactic-cat">[identifier-characters](LexicalStructure.md#identifier-characters)</span>~opt~</span>

<span class="syntax-def-name">
identifier
</span>
<span class="arrow">
→
</span>`` ` ``<span class="syntactic-cat">[identifier-head](LexicalStructure.md#identifier-head)</span><span class="optional"><span class="syntactic-cat">[identifier-characters](LexicalStructure.md#identifier-characters)</span>~opt~</span>`` ` ``

<span class="syntax-def-name">
identifier
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[implicit-parameter-name](LexicalStructure.md#implicit-parameter-name)</span>

<span class="syntax-def-name">
identifier-list
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>
</span><span class="alternative">
<span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>`,`<span class="syntactic-cat">[identifier-list](LexicalStructure.md#identifier-list)</span>
</span>

<span class="syntax-def-name">
identifier-head
</span>
<span class="arrow">
→
</span><span class="text-description">Upper- or lowercase letter A through Z</span>

<span class="syntax-def-name">
identifier-head
</span>
<span class="arrow">
→
</span>`_`

<span class="syntax-def-name">
identifier-head
</span>
<span class="arrow">
→
</span><span class="text-description">U+00A8, U+00AA, U+00AD, U+00AF, U+00B2–U+00B5, or U+00B7–U+00BA</span>

<span class="syntax-def-name">
identifier-head
</span>
<span class="arrow">
→
</span><span class="text-description">U+00BC–U+00BE, U+00C0–U+00D6, U+00D8–U+00F6, or U+00F8–U+00FF</span>

<span class="syntax-def-name">
identifier-head
</span>
<span class="arrow">
→
</span><span class="text-description">U+0100–U+02FF, U+0370–U+167F, U+1681–U+180D, or U+180F–U+1DBF</span>

<span class="syntax-def-name">
identifier-head
</span>
<span class="arrow">
→
</span><span class="text-description">U+1E00–U+1FFF</span>

<span class="syntax-def-name">
identifier-head
</span>
<span class="arrow">
→
</span><span class="text-description">U+200B–U+200D, U+202A–U+202E, U+203F–U+2040, U+2054, or U+2060–U+206F</span>

<span class="syntax-def-name">
identifier-head
</span>
<span class="arrow">
→
</span><span class="text-description">U+2070–U+20CF, U+2100–U+218F, U+2460–U+24FF, or U+2776–U+2793</span>

<span class="syntax-def-name">
identifier-head
</span>
<span class="arrow">
→
</span><span class="text-description">U+2C00–U+2DFF or U+2E80–U+2FFF</span>

<span class="syntax-def-name">
identifier-head
</span>
<span class="arrow">
→
</span><span class="text-description">U+3004–U+3007, U+3021–U+302F, U+3031–U+303F, or U+3040–U+D7FF</span>

<span class="syntax-def-name">
identifier-head
</span>
<span class="arrow">
→
</span><span class="text-description">U+F900–U+FD3D, U+FD40–U+FDCF, U+FDF0–U+FE1F, or U+FE30–U+FE44</span>

<span class="syntax-def-name">
identifier-head
</span>
<span class="arrow">
→
</span><span class="text-description">U+FE47–U+FFFD</span>

<span class="syntax-def-name">
identifier-head
</span>
<span class="arrow">
→
</span><span class="text-description">U+10000–U+1FFFD, U+20000–U+2FFFD, U+30000–U+3FFFD, or U+40000–U+4FFFD</span>

<span class="syntax-def-name">
identifier-head
</span>
<span class="arrow">
→
</span><span class="text-description">U+50000–U+5FFFD, U+60000–U+6FFFD, U+70000–U+7FFFD, or U+80000–U+8FFFD</span>

<span class="syntax-def-name">
identifier-head
</span>
<span class="arrow">
→
</span><span class="text-description">U+90000–U+9FFFD, U+A0000–U+AFFFD, U+B0000–U+BFFFD, or U+C0000–U+CFFFD</span>

<span class="syntax-def-name">
identifier-head
</span>
<span class="arrow">
→
</span><span class="text-description">U+D0000–U+DFFFD or U+E0000–U+EFFFD</span>

<span class="syntax-def-name">
identifier-character
</span>
<span class="arrow">
→
</span><span class="text-description">Digit 0 through 9</span>

<span class="syntax-def-name">
identifier-character
</span>
<span class="arrow">
→
</span><span class="text-description">U+0300–U+036F, U+1DC0–U+1DFF, U+20D0–U+20FF, or U+FE20–U+FE2F</span>

<span class="syntax-def-name">
identifier-character
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[identifier-head](LexicalStructure.md#identifier-head)</span>

<span class="syntax-def-name">
identifier-characters
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[identifier-character](LexicalStructure.md#identifier-character)</span><span class="optional"><span class="syntactic-cat">[identifier-characters](LexicalStructure.md#identifier-characters)</span>~opt~</span>

<span class="syntax-def-name">
implicit-parameter-name
</span>
<span class="arrow">
→
</span>`$`<span class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)</span>

Grammar of a literal

<span class="syntax-def-name">
literal
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[numeric-literal](LexicalStructure.md#numeric-literal)</span>
</span><span class="alternative">
<span class="syntactic-cat">[string-literal](LexicalStructure.md#string-literal)</span>
</span><span class="alternative">
<span class="syntactic-cat">[boolean-literal](LexicalStructure.md#boolean-literal)</span>
</span><span class="alternative">
<span class="syntactic-cat">[nil-literal](LexicalStructure.md#nil-literal)</span>
</span>

<span class="syntax-def-name">
numeric-literal
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="optional">`-`~opt~</span><span class="syntactic-cat">[integer-literal](LexicalStructure.md#integer-literal)</span>
</span><span class="alternative">
<span class="optional">`-`~opt~</span><span class="syntactic-cat">[floating-point-literal](LexicalStructure.md#floating-point-literal)</span>
</span>

<span class="syntax-def-name">
boolean-literal
</span>
<span class="arrow">
→
</span><span class="alternative">
`true`
</span><span class="alternative">
`false`
</span>

<span class="syntax-def-name">
nil-literal
</span>
<span class="arrow">
→
</span>`nil`

Grammar of an integer literal

<span class="syntax-def-name">
integer-literal
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[binary-literal](LexicalStructure.md#binary-literal)</span>

<span class="syntax-def-name">
integer-literal
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[octal-literal](LexicalStructure.md#octal-literal)</span>

<span class="syntax-def-name">
integer-literal
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[decimal-literal](LexicalStructure.md#decimal-literal)</span>

<span class="syntax-def-name">
integer-literal
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[hexadecimal-literal](LexicalStructure.md#hexadecimal-literal)</span>

<span class="syntax-def-name">
binary-literal
</span>
<span class="arrow">
→
</span>`0b`<span class="syntactic-cat">[binary-digit](LexicalStructure.md#binary-digit)</span><span class="optional"><span class="syntactic-cat">[binary-literal-characters](LexicalStructure.md#binary-literal-characters)</span>~opt~</span>

<span class="syntax-def-name">
binary-digit
</span>
<span class="arrow">
→
</span><span class="text-description">Digit 0 or 1</span>

<span class="syntax-def-name">
binary-literal-character
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[binary-digit](LexicalStructure.md#binary-digit)</span>
</span><span class="alternative">
`_`
</span>

<span class="syntax-def-name">
binary-literal-characters
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[binary-literal-character](LexicalStructure.md#binary-literal-character)</span><span class="optional"><span class="syntactic-cat">[binary-literal-characters](LexicalStructure.md#binary-literal-characters)</span>~opt~</span>

<span class="syntax-def-name">
octal-literal
</span>
<span class="arrow">
→
</span>`0o`<span class="syntactic-cat">[octal-digit](LexicalStructure.md#octal-digit)</span><span class="optional"><span class="syntactic-cat">[octal-literal-characters](LexicalStructure.md#octal-literal-characters)</span>~opt~</span>

<span class="syntax-def-name">
octal-digit
</span>
<span class="arrow">
→
</span><span class="text-description">Digit 0 through 7</span>

<span class="syntax-def-name">
octal-literal-character
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[octal-digit](LexicalStructure.md#octal-digit)</span>
</span><span class="alternative">
`_`
</span>

<span class="syntax-def-name">
octal-literal-characters
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[octal-literal-character](LexicalStructure.md#octal-literal-character)</span><span class="optional"><span class="syntactic-cat">[octal-literal-characters](LexicalStructure.md#octal-literal-characters)</span>~opt~</span>

<span class="syntax-def-name">
decimal-literal
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[decimal-digit](LexicalStructure.md#decimal-digit)</span><span class="optional"><span class="syntactic-cat">[decimal-literal-characters](LexicalStructure.md#decimal-literal-characters)</span>~opt~</span>

<span class="syntax-def-name">
decimal-digit
</span>
<span class="arrow">
→
</span><span class="text-description">Digit 0 through 9</span>

<span class="syntax-def-name">
decimal-digits
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[decimal-digit](LexicalStructure.md#decimal-digit)</span><span class="optional"><span class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)</span>~opt~</span>

<span class="syntax-def-name">
decimal-literal-character
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[decimal-digit](LexicalStructure.md#decimal-digit)</span>
</span><span class="alternative">
`_`
</span>

<span class="syntax-def-name">
decimal-literal-characters
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[decimal-literal-character](LexicalStructure.md#decimal-literal-character)</span><span class="optional"><span class="syntactic-cat">[decimal-literal-characters](LexicalStructure.md#decimal-literal-characters)</span>~opt~</span>

<span class="syntax-def-name">
hexadecimal-literal
</span>
<span class="arrow">
→
</span>`0x`<span class="syntactic-cat">[hexadecimal-digit](LexicalStructure.md#hexadecimal-digit)</span><span class="optional"><span class="syntactic-cat">[hexadecimal-literal-characters](LexicalStructure.md#hexadecimal-literal-characters)</span>~opt~</span>

<span class="syntax-def-name">
hexadecimal-digit
</span>
<span class="arrow">
→
</span><span class="text-description">Digit 0 through 9, a through f, or A through F</span>

<span class="syntax-def-name">
hexadecimal-literal-character
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[hexadecimal-digit](LexicalStructure.md#hexadecimal-digit)</span>
</span><span class="alternative">
`_`
</span>

<span class="syntax-def-name">
hexadecimal-literal-characters
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[hexadecimal-literal-character](LexicalStructure.md#hexadecimal-literal-character)</span><span class="optional"><span class="syntactic-cat">[hexadecimal-literal-characters](LexicalStructure.md#hexadecimal-literal-characters)</span>~opt~</span>

Grammar of a floating-point literal

<span class="syntax-def-name">
floating-point-literal
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[decimal-literal](LexicalStructure.md#decimal-literal)</span><span class="optional"><span class="syntactic-cat">[decimal-fraction](LexicalStructure.md#decimal-fraction)</span>~opt~</span><span class="optional"><span class="syntactic-cat">[decimal-exponent](LexicalStructure.md#decimal-exponent)</span>~opt~</span>

<span class="syntax-def-name">
floating-point-literal
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[hexadecimal-literal](LexicalStructure.md#hexadecimal-literal)</span><span class="optional"><span class="syntactic-cat">[hexadecimal-fraction](LexicalStructure.md#hexadecimal-fraction)</span>~opt~</span><span class="syntactic-cat">[hexadecimal-exponent](LexicalStructure.md#hexadecimal-exponent)</span>

<span class="syntax-def-name">
decimal-fraction
</span>
<span class="arrow">
→
</span>`.`<span class="syntactic-cat">[decimal-literal](LexicalStructure.md#decimal-literal)</span>

<span class="syntax-def-name">
decimal-exponent
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[floating-point-e](LexicalStructure.md#floating-point-e)</span><span class="optional"><span class="syntactic-cat">[sign](LexicalStructure.md#sign)</span>~opt~</span><span class="syntactic-cat">[decimal-literal](LexicalStructure.md#decimal-literal)</span>

<span class="syntax-def-name">
hexadecimal-fraction
</span>
<span class="arrow">
→
</span>`.`<span class="syntactic-cat">[hexadecimal-digit](LexicalStructure.md#hexadecimal-digit)</span><span class="optional"><span class="syntactic-cat">[hexadecimal-literal-characters](LexicalStructure.md#hexadecimal-literal-characters)</span>~opt~</span>

<span class="syntax-def-name">
hexadecimal-exponent
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[floating-point-p](LexicalStructure.md#floating-point-p)</span><span class="optional"><span class="syntactic-cat">[sign](LexicalStructure.md#sign)</span>~opt~</span><span class="syntactic-cat">[decimal-literal](LexicalStructure.md#decimal-literal)</span>

<span class="syntax-def-name">
floating-point-e
</span>
<span class="arrow">
→
</span><span class="alternative">
`e`
</span><span class="alternative">
`E`
</span>

<span class="syntax-def-name">
floating-point-p
</span>
<span class="arrow">
→
</span><span class="alternative">
`p`
</span><span class="alternative">
`P`
</span>

<span class="syntax-def-name">
sign
</span>
<span class="arrow">
→
</span><span class="alternative">
`+`
</span><span class="alternative">
`-`
</span>

Grammar of a string literal

<span class="syntax-def-name">
string-literal
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[static-string-literal](LexicalStructure.md#static-string-literal)</span>
</span><span class="alternative">
<span class="syntactic-cat">[interpolated-string-literal](LexicalStructure.md#interpolated-string-literal)</span>
</span>

<span class="syntax-def-name">
static-string-literal
</span>
<span class="arrow">
→
</span>`"`<span class="optional"><span class="syntactic-cat">[quoted-text](LexicalStructure.md#quoted-text)</span>~opt~</span>`"`

<span class="syntax-def-name">
quoted-text
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[quoted-text-item](LexicalStructure.md#quoted-text-item)</span><span class="optional"><span class="syntactic-cat">[quoted-text](LexicalStructure.md#quoted-text)</span>~opt~</span>

<span class="syntax-def-name">
quoted-text-item
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[escaped-character](LexicalStructure.md#escaped-character)</span>

<span class="syntax-def-name">
quoted-text-item
</span>
<span class="arrow">
→
</span><span class="text-description">Any Unicode scalar value except `"`, `\`, U+000A, or U+000D</span>

<span class="syntax-def-name">
interpolated-string-literal
</span>
<span class="arrow">
→
</span>`"`<span class="optional"><span class="syntactic-cat">[interpolated-text](LexicalStructure.md#interpolated-text)</span>~opt~</span>`"`

<span class="syntax-def-name">
interpolated-text
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[interpolated-text-item](LexicalStructure.md#interpolated-text-item)</span><span class="optional"><span class="syntactic-cat">[interpolated-text](LexicalStructure.md#interpolated-text)</span>~opt~</span>

<span class="syntax-def-name">
interpolated-text-item
</span>
<span class="arrow">
→
</span><span class="alternative">
`\(`<span class="syntactic-cat">[expression](Expressions.md#expression)</span>`)`
</span><span class="alternative">
<span class="syntactic-cat">[quoted-text-item](LexicalStructure.md#quoted-text-item)</span>
</span>

<span class="syntax-def-name">
escaped-character
</span>
<span class="arrow">
→
</span><span class="alternative">
`\0`
</span><span class="alternative">
`\\`
</span><span class="alternative">
`\t`
</span><span class="alternative">
`\n`
</span><span class="alternative">
`\r`
</span><span class="alternative">
`\"`
</span><span class="alternative">
`\'`
</span>

<span class="syntax-def-name">
escaped-character
</span>
<span class="arrow">
→
</span>`\u``{`<span class="syntactic-cat">[unicode-scalar-digits](LexicalStructure.md#unicode-scalar-digits)</span>`}`

<span class="syntax-def-name">
unicode-scalar-digits
</span>
<span class="arrow">
→
</span><span class="text-description">Between one and eight hexadecimal digits</span>

Grammar of operators

<span class="syntax-def-name">
operator
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[operator-head](LexicalStructure.md#operator-head)</span><span class="optional"><span class="syntactic-cat">[operator-characters](LexicalStructure.md#operator-characters)</span>~opt~</span>

<span class="syntax-def-name">
operator
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[dot-operator-head](LexicalStructure.md#dot-operator-head)</span><span class="optional"><span class="syntactic-cat">[dot-operator-characters](LexicalStructure.md#dot-operator-characters)</span>~opt~</span>

<span class="syntax-def-name">
operator-head
</span>
<span class="arrow">
→
</span><span class="alternative">
`/`
</span><span class="alternative">
`=`
</span><span class="alternative">
`-`
</span><span class="alternative">
`+`
</span><span class="alternative">
`!`
</span><span class="alternative">
`*`
</span><span class="alternative">
`%`
</span><span class="alternative">
`<`
</span><span class="alternative">
`>`
</span><span class="alternative">
`&`
</span><span class="alternative">
`|`
</span><span class="alternative">
`^`
</span><span class="alternative">
`~`
</span><span class="alternative">
`?`
</span>

<span class="syntax-def-name">
operator-head
</span>
<span class="arrow">
→
</span><span class="text-description">U+00A1–U+00A7</span>

<span class="syntax-def-name">
operator-head
</span>
<span class="arrow">
→
</span><span class="text-description">U+00A9 or U+00AB</span>

<span class="syntax-def-name">
operator-head
</span>
<span class="arrow">
→
</span><span class="text-description">U+00AC or U+00AE</span>

<span class="syntax-def-name">
operator-head
</span>
<span class="arrow">
→
</span><span class="text-description">U+00B0–U+00B1, U+00B6, U+00BB, U+00BF, U+00D7, or U+00F7</span>

<span class="syntax-def-name">
operator-head
</span>
<span class="arrow">
→
</span><span class="text-description">U+2016–U+2017 or U+2020–U+2027</span>

<span class="syntax-def-name">
operator-head
</span>
<span class="arrow">
→
</span><span class="text-description">U+2030–U+203E</span>

<span class="syntax-def-name">
operator-head
</span>
<span class="arrow">
→
</span><span class="text-description">U+2041–U+2053</span>

<span class="syntax-def-name">
operator-head
</span>
<span class="arrow">
→
</span><span class="text-description">U+2055–U+205E</span>

<span class="syntax-def-name">
operator-head
</span>
<span class="arrow">
→
</span><span class="text-description">U+2190–U+23FF</span>

<span class="syntax-def-name">
operator-head
</span>
<span class="arrow">
→
</span><span class="text-description">U+2500–U+2775</span>

<span class="syntax-def-name">
operator-head
</span>
<span class="arrow">
→
</span><span class="text-description">U+2794–U+2BFF</span>

<span class="syntax-def-name">
operator-head
</span>
<span class="arrow">
→
</span><span class="text-description">U+2E00–U+2E7F</span>

<span class="syntax-def-name">
operator-head
</span>
<span class="arrow">
→
</span><span class="text-description">U+3001–U+3003</span>

<span class="syntax-def-name">
operator-head
</span>
<span class="arrow">
→
</span><span class="text-description">U+3008–U+3030</span>

<span class="syntax-def-name">
operator-character
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[operator-head](LexicalStructure.md#operator-head)</span>

<span class="syntax-def-name">
operator-character
</span>
<span class="arrow">
→
</span><span class="text-description">U+0300–U+036F</span>

<span class="syntax-def-name">
operator-character
</span>
<span class="arrow">
→
</span><span class="text-description">U+1DC0–U+1DFF</span>

<span class="syntax-def-name">
operator-character
</span>
<span class="arrow">
→
</span><span class="text-description">U+20D0–U+20FF</span>

<span class="syntax-def-name">
operator-character
</span>
<span class="arrow">
→
</span><span class="text-description">U+FE00–U+FE0F</span>

<span class="syntax-def-name">
operator-character
</span>
<span class="arrow">
→
</span><span class="text-description">U+FE20–U+FE2F</span>

<span class="syntax-def-name">
operator-character
</span>
<span class="arrow">
→
</span><span class="text-description">U+E0100–U+E01EF</span>

<span class="syntax-def-name">
operator-characters
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[operator-character](LexicalStructure.md#operator-character)</span><span class="optional"><span class="syntactic-cat">[operator-characters](LexicalStructure.md#operator-characters)</span>~opt~</span>

<span class="syntax-def-name">
dot-operator-head
</span>
<span class="arrow">
→
</span>`..`

<span class="syntax-def-name">
dot-operator-character
</span>
<span class="arrow">
→
</span><span class="alternative">
`.`
</span><span class="alternative">
<span class="syntactic-cat">[operator-character](LexicalStructure.md#operator-character)</span>
</span>

<span class="syntax-def-name">
dot-operator-characters
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[dot-operator-character](LexicalStructure.md#dot-operator-character)</span><span class="optional"><span class="syntactic-cat">[dot-operator-characters](LexicalStructure.md#dot-operator-characters)</span>~opt~</span>

<span class="syntax-def-name">
binary-operator
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[operator](LexicalStructure.md#operator)</span>

<span class="syntax-def-name">
prefix-operator
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[operator](LexicalStructure.md#operator)</span>

<span class="syntax-def-name">
postfix-operator
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[operator](LexicalStructure.md#operator)</span>

### Types 

Grammar of a type

<span class="syntax-def-name">
type
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[array-type](Types.md#array-type)</span>
</span><span class="alternative">
<span class="syntactic-cat">[dictionary-type](Types.md#dictionary-type)</span>
</span><span class="alternative">
<span class="syntactic-cat">[function-type](Types.md#function-type)</span>
</span><span class="alternative">
<span class="syntactic-cat">[type-identifier](Types.md#type-identifier)</span>
</span><span class="alternative">
<span class="syntactic-cat">[tuple-type](Types.md#tuple-type)</span>
</span><span class="alternative">
<span class="syntactic-cat">[optional-type](Types.md#optional-type)</span>
</span><span class="alternative">
<span class="syntactic-cat">[implicitly-unwrapped-optional-type](Types.md#implicitly-unwrapped-optional-type)</span>
</span><span class="alternative">
<span class="syntactic-cat">[protocol-composition-type](Types.md#protocol-composition-type)</span>
</span><span class="alternative">
<span class="syntactic-cat">[metatype-type](Types.md#metatype-type)</span>
</span>

Grammar of a type annotation

<span class="syntax-def-name">
type-annotation
</span>
<span class="arrow">
→
</span>`:`<span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span class="syntactic-cat">[type](Types.md#type)</span>

Grammar of a type identifier

<span class="syntax-def-name">
type-identifier
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[type-name](Types.md#type-name)</span><span class="optional"><span class="syntactic-cat">[generic-argument-clause](GenericParametersAndArguments.md#generic-argument-clause)</span>~opt~</span>
</span><span class="alternative">
<span class="syntactic-cat">[type-name](Types.md#type-name)</span><span class="optional"><span class="syntactic-cat">[generic-argument-clause](GenericParametersAndArguments.md#generic-argument-clause)</span>~opt~</span>`.`<span class="syntactic-cat">[type-identifier](Types.md#type-identifier)</span>
</span>

<span class="syntax-def-name">
type-name
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

Grammar of a tuple type

<span class="syntax-def-name">
tuple-type
</span>
<span class="arrow">
→
</span>`(`<span class="optional"><span class="syntactic-cat">[tuple-type-body](Types.md#tuple-type-body)</span>~opt~</span>`)`

<span class="syntax-def-name">
tuple-type-body
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[tuple-type-element-list](Types.md#tuple-type-element-list)</span><span class="optional">`...`~opt~</span>

<span class="syntax-def-name">
tuple-type-element-list
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[tuple-type-element](Types.md#tuple-type-element)</span>
</span><span class="alternative">
<span class="syntactic-cat">[tuple-type-element](Types.md#tuple-type-element)</span>`,`<span class="syntactic-cat">[tuple-type-element-list](Types.md#tuple-type-element-list)</span>
</span>

<span class="syntax-def-name">
tuple-type-element
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="optional"><span class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span class="optional">`inout`~opt~</span><span class="syntactic-cat">[type](Types.md#type)</span>
</span><span class="alternative">
<span class="optional">`inout`~opt~</span><span class="syntactic-cat">[element-name](Types.md#element-name)</span><span class="syntactic-cat">[type-annotation](Types.md#type-annotation)</span>
</span>

<span class="syntax-def-name">
element-name
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

Grammar of a function type

<span class="syntax-def-name">
function-type
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[type](Types.md#type)</span><span class="optional">`throws`~opt~</span>`->`<span class="syntactic-cat">[type](Types.md#type)</span>

<span class="syntax-def-name">
function-type
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[type](Types.md#type)</span>`rethrows``->`<span class="syntactic-cat">[type](Types.md#type)</span>

Grammar of an array type

<span class="syntax-def-name">
array-type
</span>
<span class="arrow">
→
</span>`[`<span class="syntactic-cat">[type](Types.md#type)</span>`]`

Grammar of a dictionary type

<span class="syntax-def-name">
dictionary-type
</span>
<span class="arrow">
→
</span>`[`<span class="syntactic-cat">[type](Types.md#type)</span>`:`<span class="syntactic-cat">[type](Types.md#type)</span>`]`

Grammar of an optional type

<span class="syntax-def-name">
optional-type
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[type](Types.md#type)</span>`?`

Grammar of an implicitly unwrapped optional type

<span class="syntax-def-name">
implicitly-unwrapped-optional-type
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[type](Types.md#type)</span>`!`

Grammar of a protocol composition type

<span class="syntax-def-name">
protocol-composition-type
</span>
<span class="arrow">
→
</span>`protocol``<`<span class="optional"><span class="syntactic-cat">[protocol-identifier-list](Types.md#protocol-identifier-list)</span>~opt~</span>`>`

<span class="syntax-def-name">
protocol-identifier-list
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[protocol-identifier](Types.md#protocol-identifier)</span>
</span><span class="alternative">
<span class="syntactic-cat">[protocol-identifier](Types.md#protocol-identifier)</span>`,`<span class="syntactic-cat">[protocol-identifier-list](Types.md#protocol-identifier-list)</span>
</span>

<span class="syntax-def-name">
protocol-identifier
</span>
<span class="arrow">
→
</span><span class="syntactic-cat">[type-identifier](Types.md#type-identifier)</span>

Grammar of a metatype type

<span class="syntax-def-name">
metatype-type
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[type](Types.md#type)</span>`.``Type`
</span><span class="alternative">
<span class="syntactic-cat">[type](Types.md#type)</span>`.``Protocol`
</span>

Grammar of a type inheritance clause

<span class="syntax-def-name">
type-inheritance-clause
</span>
<span class="arrow">
→
</span>`:`<span class="syntactic-cat">[class-requirement](Types.md#class-requirement)</span>`,`<span class="syntactic-cat">[type-inheritance-list](Types.md#type-inheritance-list)</span>

<span class="syntax-def-name">
type-inheritance-clause
</span>
<span class="arrow">
→
</span>`:`<span class="syntactic-cat">[class-requirement](Types.md#class-requirement)</span>

<span class="syntax-def-name">
type-inheritance-clause
</span>
<span class="arrow">
→
</span>`:`<span class="syntactic-cat">[type-inheritance-list](Types.md#type-inheritance-list)</span>

<span class="syntax-def-name">
type-inheritance-list
</span>
<span class="arrow">
→
</span><span class="alternative">
<span class="syntactic-cat">[type-identifier](Types.md#type-identifier)</span>
</span><span class="alternative">
<span class="syntactic-cat">[type-identifier](Types.md#type-identifier)</span>`,`<span class="syntactic-cat">[type-inheritance-list](Types.md#type-inheritance-list)</span>
</span>

<span class="syntax-def-name">
class-requirement
</span>
<span class="arrow">
→
</span>`class`

