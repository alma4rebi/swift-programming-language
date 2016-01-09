



[‌](){#TP40016643-CH38}[‌](){#TP40016643-CH38-ID458}
Summary of the Grammar {#summary-of-the-grammar .chapter-name}
----------------------



[‌](){#TP40016643-CH38-ID475}
### Statements {#statements .section-name}



Grammar of a statement



[‌](){#TP40016643-CH38-NoLink_812}

statement


→
[expression](Expressions.md#expression)`;`{.literal}~opt~

[‌](){#TP40016643-CH38-NoLink_813}

statement


→
[declaration](Declarations.md#declaration)`;`{.literal}~opt~

[‌](){#TP40016643-CH38-NoLink_814}

statement


→
[loop-statement](Statements.md#loop-statement)`;`{.literal}~opt~

[‌](){#TP40016643-CH38-NoLink_815}

statement


→
[branch-statement](Statements.md#branch-statement)`;`{.literal}~opt~

[‌](){#TP40016643-CH38-NoLink_816}

statement


→
[labeled-statement](Statements.md#labeled-statement)`;`{.literal}~opt~

[‌](){#TP40016643-CH38-NoLink_817}

statement


→
[control-transfer-statement](Statements.md#control-transfer-statement)`;`{.literal}~opt~

[‌](){#TP40016643-CH38-NoLink_818}

statement


→
[defer-statement](Statements.md#defer-statement)`;`{.literal}~opt~

[‌](){#TP40016643-CH38-NoLink_819}

statement


→
[do-statement](Statements.md#do-statement)`:`{.literal}~opt~

[‌](){#TP40016643-CH38-NoLink_820}

statement


→
[compiler-control-statement](Statements.md#compiler-control-statement)

[‌](){#TP40016643-CH38-NoLink_821}

statements


→
[statement](Statements.md#statement)[statements](Statements.md#statements)~opt~







Grammar of a loop statement



[‌](){#TP40016643-CH38-NoLink_823}

loop-statement


→
[for-statement](Statements.md#for-statement)

[‌](){#TP40016643-CH38-NoLink_824}

loop-statement


→
[for-in-statement](Statements.md#for-in-statement)

[‌](){#TP40016643-CH38-NoLink_825}

loop-statement


→
[while-statement](Statements.md#while-statement)

[‌](){#TP40016643-CH38-NoLink_826}

loop-statement


→
[repeat-while-statement](Statements.md#repeat-while-statement)







Grammar of a for statement



[‌](){#TP40016643-CH38-NoLink_828}

for-statement


→
`for`{.literal}[for-init](Statements.md#for-init)~opt~`;`{.literal}[expression](Expressions.md#expression)~opt~`;`{.literal}[expression-list](Expressions.md#expression-list)~opt~[code-block](Declarations.md#code-block)

[‌](){#TP40016643-CH38-NoLink_829}

for-statement


→
`for`{.literal}`(`{.literal}[for-init](Statements.md#for-init)~opt~`;`{.literal}[expression](Expressions.md#expression)~opt~`;`{.literal}[expression-list](Expressions.md#expression-list)~opt~`)`{.literal}[code-block](Declarations.md#code-block)





[‌](){#TP40016643-CH38-NoLink_830}

for-init


→

[variable-declaration](Declarations.md#variable-declaration)

[expression-list](Expressions.md#expression-list)








Grammar of a for-in statement



[‌](){#TP40016643-CH38-NoLink_832}

for-in-statement


→
`for`{.literal}`case`{.literal}~opt~[pattern](Patterns.md#pattern)`in`{.literal}[expression](Expressions.md#expression)[where-clause](Statements.md#where-clause)~opt~[code-block](Declarations.md#code-block)







Grammar of a while statement



[‌](){#TP40016643-CH38-NoLink_834}

while-statement


→
`while`{.literal}[condition-clause](Statements.md#condition-clause)[code-block](Declarations.md#code-block)





[‌](){#TP40016643-CH38-NoLink_835}

condition-clause


→
[expression](Expressions.md#expression)

[‌](){#TP40016643-CH38-NoLink_836}

condition-clause


→
[expression](Expressions.md#expression)`,`{.literal}[condition-list](Statements.md#condition-list)

[‌](){#TP40016643-CH38-NoLink_837}

condition-clause


→
[condition-list](Statements.md#condition-list)

[‌](){#TP40016643-CH38-NoLink_838}

condition-clause


→
[availability-condition](Statements.md#availability-condition)`,`{.literal}[expression](Expressions.md#expression)





[‌](){#TP40016643-CH38-NoLink_839}

condition-list


→

[condition](Statements.md#condition)

[condition](Statements.md#condition)`,`{.literal}[condition-list](Statements.md#condition-list)


[‌](){#TP40016643-CH38-NoLink_840}

condition


→

[availability-condition](Statements.md#availability-condition)

[case-condition](Statements.md#case-condition)

[optional-binding-condition](Statements.md#optional-binding-condition)


[‌](){#TP40016643-CH38-NoLink_841}

case-condition


→
`case`{.literal}[pattern](Patterns.md#pattern)[initializer](Declarations.md#initializer)[where-clause](Statements.md#where-clause)~opt~





[‌](){#TP40016643-CH38-NoLink_842}

optional-binding-condition


→
[optional-binding-head](Statements.md#optional-binding-head)[optional-binding-continuation-list](Statements.md#optional-binding-continuation-list)~opt~[where-clause](Statements.md#where-clause)~opt~

[‌](){#TP40016643-CH38-NoLink_843}

optional-binding-head


→
`let`{.literal}[pattern](Patterns.md#pattern)[initializer](Declarations.md#initializer)

[‌](){#TP40016643-CH38-NoLink_844}

optional-binding-continuation-list


→

[optional-binding-continuation](Statements.md#optional-binding-continuation)

[optional-binding-continuation](Statements.md#optional-binding-continuation)`,`{.literal}[optional-binding-continuation-list](Statements.md#optional-binding-continuation-list)


[‌](){#TP40016643-CH38-NoLink_845}

optional-binding-continuation


→

[pattern](Patterns.md#pattern)[initializer](Declarations.md#initializer)

[optional-binding-head](Statements.md#optional-binding-head)








Grammar of a repeat-while statement



[‌](){#TP40016643-CH38-NoLink_847}

repeat-while-statement


→
`repeat`{.literal}[code-block](Declarations.md#code-block)`while`{.literal}[expression](Expressions.md#expression)







Grammar of a branch statement



[‌](){#TP40016643-CH38-NoLink_849}

branch-statement


→
[if-statement](Statements.md#if-statement)

[‌](){#TP40016643-CH38-NoLink_850}

branch-statement


→
[guard-statement](Statements.md#guard-statement)

[‌](){#TP40016643-CH38-NoLink_851}

branch-statement


→
[switch-statement](Statements.md#switch-statement)







Grammar of an if statement



[‌](){#TP40016643-CH38-NoLink_853}

if-statement


→
`if`{.literal}[condition-clause](Statements.md#condition-clause)[code-block](Declarations.md#code-block)[else-clause](Statements.md#else-clause)~opt~

[‌](){#TP40016643-CH38-NoLink_854}

else-clause


→

`else`{.literal}[code-block](Declarations.md#code-block)

`else`{.literal}[if-statement](Statements.md#if-statement)








Grammar of a guard statement



[‌](){#TP40016643-CH38-NoLink_856}

guard-statement


→
`guard`{.literal}[condition-clause](Statements.md#condition-clause)`else`{.literal}[code-block](Declarations.md#code-block)







Grammar of a switch statement



[‌](){#TP40016643-CH38-NoLink_858}

switch-statement


→
`switch`{.literal}[expression](Expressions.md#expression)`{`{.literal}[switch-cases](Statements.md#switch-cases)~opt~`}`{.literal}

[‌](){#TP40016643-CH38-NoLink_859}

switch-cases


→
[switch-case](Statements.md#switch-case)[switch-cases](Statements.md#switch-cases)~opt~

[‌](){#TP40016643-CH38-NoLink_860}

switch-case


→

[case-label](Statements.md#case-label)[statements](Statements.md#statements)

[default-label](Statements.md#default-label)[statements](Statements.md#statements)






[‌](){#TP40016643-CH38-NoLink_861}

case-label


→
`case`{.literal}[case-item-list](Statements.md#case-item-list)`:`{.literal}

[‌](){#TP40016643-CH38-NoLink_862}

case-item-list


→

[pattern](Patterns.md#pattern)[where-clause](Statements.md#where-clause)~opt~

[pattern](Patterns.md#pattern)[where-clause](Statements.md#where-clause)~opt~`,`{.literal}[case-item-list](Statements.md#case-item-list)


[‌](){#TP40016643-CH38-NoLink_863}

default-label


→
`default`{.literal}`:`{.literal}





[‌](){#TP40016643-CH38-NoLink_864}

where-clause


→
`where`{.literal}[where-expression](Statements.md#where-expression)

[‌](){#TP40016643-CH38-NoLink_865}

where-expression


→
[expression](Expressions.md#expression)







Grammar of a labeled statement



[‌](){#TP40016643-CH38-NoLink_867}

labeled-statement


→

[statement-label](Statements.md#statement-label)[loop-statement](Statements.md#loop-statement)

[statement-label](Statements.md#statement-label)[if-statement](Statements.md#if-statement)

[statement-label](Statements.md#statement-label)[switch-statement](Statements.md#switch-statement)


[‌](){#TP40016643-CH38-NoLink_868}

statement-label


→
[label-name](Statements.md#label-name)`:`{.literal}

[‌](){#TP40016643-CH38-NoLink_869}

label-name


→
[identifier](LexicalStructure.md#identifier)







Grammar of a control transfer statement



[‌](){#TP40016643-CH38-NoLink_871}

control-transfer-statement


→
[break-statement](Statements.md#break-statement)

[‌](){#TP40016643-CH38-NoLink_872}

control-transfer-statement


→
[continue-statement](Statements.md#continue-statement)

[‌](){#TP40016643-CH38-NoLink_873}

control-transfer-statement


→
[fallthrough-statement](Statements.md#fallthrough-statement)

[‌](){#TP40016643-CH38-NoLink_874}

control-transfer-statement


→
[return-statement](Statements.md#return-statement)

[‌](){#TP40016643-CH38-NoLink_875}

control-transfer-statement


→
[throw-statement](Statements.md#throw-statement)







Grammar of a break statement



[‌](){#TP40016643-CH38-NoLink_877}

break-statement


→
`break`{.literal}[label-name](Statements.md#label-name)~opt~







Grammar of a continue statement



[‌](){#TP40016643-CH38-NoLink_879}

continue-statement


→
`continue`{.literal}[label-name](Statements.md#label-name)~opt~







Grammar of a fallthrough statement



[‌](){#TP40016643-CH38-NoLink_881}

fallthrough-statement


→
`fallthrough`{.literal}







Grammar of a return statement



[‌](){#TP40016643-CH38-NoLink_883}

return-statement


→
`return`{.literal}[expression](Expressions.md#expression)~opt~







Grammar of an availability condition



[‌](){#TP40016643-CH38-NoLink_885}

availability-condition


→
`#available`{.literal}`(`{.literal}[availability-arguments](Statements.md#availability-arguments)`)`{.literal}

[‌](){#TP40016643-CH38-NoLink_886}

availability-arguments


→

[availability-argument](Statements.md#availability-argument)

[availability-argument](Statements.md#availability-argument)`,`{.literal}[availability-arguments](Statements.md#availability-arguments)


[‌](){#TP40016643-CH38-NoLink_887}

availability-argument


→
[platform-name](Statements.md#platform-name)[platform-version](Statements.md#platform-version)

[‌](){#TP40016643-CH38-NoLink_888}

availability-argument


→
`*`{.literal}





[‌](){#TP40016643-CH38-NoLink_889}

platform-name


→

`iOS`{.literal}

`iOSApplicationExtension`{.literal}


[‌](){#TP40016643-CH38-NoLink_890}

platform-name


→

`OSX`{.literal}

`OSXApplicationExtension`{.literal}


[‌](){#TP40016643-CH38-NoLink_891}

platform-name


→
`watchOS`{.literal}

[‌](){#TP40016643-CH38-NoLink_892}

platform-version


→
[decimal-digits](LexicalStructure.md#decimal-digits)

[‌](){#TP40016643-CH38-NoLink_893}

platform-version


→
[decimal-digits](LexicalStructure.md#decimal-digits)`.`{.literal}[decimal-digits](LexicalStructure.md#decimal-digits)

[‌](){#TP40016643-CH38-NoLink_894}

platform-version


→
[decimal-digits](LexicalStructure.md#decimal-digits)`.`{.literal}[decimal-digits](LexicalStructure.md#decimal-digits)`.`{.literal}[decimal-digits](LexicalStructure.md#decimal-digits)







Grammar of a throw statement



[‌](){#TP40016643-CH38-NoLink_896}

throw-statement


→
`throw`{.literal}[expression](Expressions.md#expression)







Grammar of a defer statement



[‌](){#TP40016643-CH38-NoLink_898}

defer-statement


→
`defer`{.literal}[code-block](Declarations.md#code-block)







Grammar of a do statement



[‌](){#TP40016643-CH38-NoLink_900}

do-statement


→
`do`{.literal}[code-block](Declarations.md#code-block)[catch-clauses](Statements.md#catch-clauses)~opt~

[‌](){#TP40016643-CH38-NoLink_901}

catch-clauses


→
[catch-clause](Statements.md#catch-clause)[catch-clauses](Statements.md#catch-clauses)~opt~

[‌](){#TP40016643-CH38-NoLink_902}

catch-clause


→
`catch`{.literal}[pattern](Patterns.md#pattern)~opt~[where-clause](Statements.md#where-clause)~opt~[code-block](Declarations.md#code-block)







Grammar of a compiler control statement



[‌](){#TP40016643-CH38-NoLink_904}

compiler-control-statement


→
[build-configuration-statement](Statements.md#build-configuration-statement)

[‌](){#TP40016643-CH38-NoLink_905}

compiler-control-statement


→
[line-control-statement](Statements.md#line-control-statement)







Grammar of a build configuration statement



[‌](){#TP40016643-CH38-NoLink_907}

build-configuration-statement


→
`#if`{.literal}[build-configuration](Statements.md#build-configuration)[statements](Statements.md#statements)~opt~[build-configuration-elseif-clauses](Statements.md#build-configuration-elseif-clauses)~opt~[build-configuration-else-clause](Statements.md#build-configuration-else-clause)~opt~`#endif`{.literal}

[‌](){#TP40016643-CH38-NoLink_908}

build-configuration-elseif-clauses


→
[build-configuration-elseif-clause](Statements.md#build-configuration-elseif-clause)[build-configuration-elseif-clauses](Statements.md#build-configuration-elseif-clauses)~opt~

[‌](){#TP40016643-CH38-NoLink_909}

build-configuration-elseif-clause


→
`#elseif`{.literal}[build-configuration](Statements.md#build-configuration)[statements](Statements.md#statements)~opt~

[‌](){#TP40016643-CH38-NoLink_910}

build-configuration-else-clause


→
`#else`{.literal}[statements](Statements.md#statements)~opt~





[‌](){#TP40016643-CH38-NoLink_911}

build-configuration


→
[platform-testing-function](Statements.md#platform-testing-function)

[‌](){#TP40016643-CH38-NoLink_912}

build-configuration


→
[identifier](LexicalStructure.md#identifier)

[‌](){#TP40016643-CH38-NoLink_913}

build-configuration


→
[boolean-literal](LexicalStructure.md#boolean-literal)

[‌](){#TP40016643-CH38-NoLink_914}

build-configuration


→
`(`{.literal}[build-configuration](Statements.md#build-configuration)`)`{.literal}

[‌](){#TP40016643-CH38-NoLink_915}

build-configuration


→
`!`{.literal}[build-configuration](Statements.md#build-configuration)

[‌](){#TP40016643-CH38-NoLink_916}

build-configuration


→
[build-configuration](Statements.md#build-configuration)`&&`{.literal}[build-configuration](Statements.md#build-configuration)

[‌](){#TP40016643-CH38-NoLink_917}

build-configuration


→
[build-configuration](Statements.md#build-configuration)`||`{.literal}[build-configuration](Statements.md#build-configuration)





[‌](){#TP40016643-CH38-NoLink_918}

platform-testing-function


→
`os`{.literal}`(`{.literal}[operating-system](Statements.md#operating-system)`)`{.literal}

[‌](){#TP40016643-CH38-NoLink_919}

platform-testing-function


→
`arch`{.literal}`(`{.literal}[architecture](Statements.md#architecture)`)`{.literal}

[‌](){#TP40016643-CH38-NoLink_920}

operating-system


→

`OSX`{.literal}

`iOS`{.literal}

`watchOS`{.literal}

`tvOS`{.literal}


[‌](){#TP40016643-CH38-NoLink_921}

architecture


→

`i386`{.literal}

`x86_64`{.literal}

`arm`{.literal}

`arm64`{.literal}








Grammar of a line control statement



[‌](){#TP40016643-CH38-NoLink_923}

line-control-statement


→
`#line`{.literal}

[‌](){#TP40016643-CH38-NoLink_924}

line-control-statement


→
`#line`{.literal}[line-number](Statements.md#line-number)[file-name](Statements.md#file-name)

[‌](){#TP40016643-CH38-NoLink_925}

line-number


→
A decimal integer greater than zero

[‌](){#TP40016643-CH38-NoLink_926}

file-name


→
[static-string-literal](LexicalStructure.md#static-string-literal)









[‌](){#TP40016643-CH38-ID476}
### Generic Parameters and Arguments {#generic-parameters-and-arguments .section-name}



Grammar of a generic parameter clause



[‌](){#TP40016643-CH38-NoLink_928}

generic-parameter-clause


→
`[generic-parameter-list](GenericParametersAndArguments.md#generic-parameter-list)[requirement-clause](GenericParametersAndArguments.md#requirement-clause)~opt~`>`{.literal}

[‌](){#TP40016643-CH38-NoLink_929}

generic-parameter-list


→

[generic-parameter](GenericParametersAndArguments.md#generic-parameter)

[generic-parameter](GenericParametersAndArguments.md#generic-parameter)`,`{.literal}[generic-parameter-list](GenericParametersAndArguments.md#generic-parameter-list)


[‌](){#TP40016643-CH38-NoLink_930}

generic-parameter


→
[type-name](Types.md#type-name)

[‌](){#TP40016643-CH38-NoLink_931}

generic-parameter


→
[type-name](Types.md#type-name)`:`{.literal}[type-identifier](Types.md#type-identifier)

[‌](){#TP40016643-CH38-NoLink_932}

generic-parameter


→
[type-name](Types.md#type-name)`:`{.literal}[protocol-composition-type](Types.md#protocol-composition-type)





[‌](){#TP40016643-CH38-NoLink_933}

requirement-clause


→
`where`{.literal}[requirement-list](GenericParametersAndArguments.md#requirement-list)

[‌](){#TP40016643-CH38-NoLink_934}

requirement-list


→

[requirement](GenericParametersAndArguments.md#requirement)

[requirement](GenericParametersAndArguments.md#requirement)`,`{.literal}[requirement-list](GenericParametersAndArguments.md#requirement-list)


[‌](){#TP40016643-CH38-NoLink_935}

requirement


→

[conformance-requirement](GenericParametersAndArguments.md#conformance-requirement)

[same-type-requirement](GenericParametersAndArguments.md#same-type-requirement)






[‌](){#TP40016643-CH38-NoLink_936}

conformance-requirement


→
[type-identifier](Types.md#type-identifier)`:`{.literal}[type-identifier](Types.md#type-identifier)

[‌](){#TP40016643-CH38-NoLink_937}

conformance-requirement


→
[type-identifier](Types.md#type-identifier)`:`{.literal}[protocol-composition-type](Types.md#protocol-composition-type)

[‌](){#TP40016643-CH38-NoLink_938}

same-type-requirement


→
[type-identifier](Types.md#type-identifier)`==`{.literal}[type](Types.md#type)







Grammar of a generic argument clause



[‌](){#TP40016643-CH38-NoLink_940}

generic-argument-clause


→
`[generic-argument-list](GenericParametersAndArguments.md#generic-argument-list)`>`{.literal}

[‌](){#TP40016643-CH38-NoLink_941}

generic-argument-list


→

[generic-argument](GenericParametersAndArguments.md#generic-argument)

[generic-argument](GenericParametersAndArguments.md#generic-argument)`,`{.literal}[generic-argument-list](GenericParametersAndArguments.md#generic-argument-list)


[‌](){#TP40016643-CH38-NoLink_942}

generic-argument


→
[type](Types.md#type)









[‌](){#TP40016643-CH38-ID477}
### Declarations {#declarations .section-name}



Grammar of a declaration



[‌](){#TP40016643-CH38-NoLink_944}

declaration


→
[import-declaration](Declarations.md#import-declaration)

[‌](){#TP40016643-CH38-NoLink_945}

declaration


→
[constant-declaration](Declarations.md#constant-declaration)

[‌](){#TP40016643-CH38-NoLink_946}

declaration


→
[variable-declaration](Declarations.md#variable-declaration)

[‌](){#TP40016643-CH38-NoLink_947}

declaration


→
[typealias-declaration](Declarations.md#typealias-declaration)

[‌](){#TP40016643-CH38-NoLink_948}

declaration


→
[function-declaration](Declarations.md#function-declaration)

[‌](){#TP40016643-CH38-NoLink_949}

declaration


→
[enum-declaration](Declarations.md#enum-declaration)

[‌](){#TP40016643-CH38-NoLink_950}

declaration


→
[struct-declaration](Declarations.md#struct-declaration)

[‌](){#TP40016643-CH38-NoLink_951}

declaration


→
[class-declaration](Declarations.md#class-declaration)

[‌](){#TP40016643-CH38-NoLink_952}

declaration


→
[protocol-declaration](Declarations.md#protocol-declaration)

[‌](){#TP40016643-CH38-NoLink_953}

declaration


→
[initializer-declaration](Declarations.md#initializer-declaration)

[‌](){#TP40016643-CH38-NoLink_954}

declaration


→
[deinitializer-declaration](Declarations.md#deinitializer-declaration)

[‌](){#TP40016643-CH38-NoLink_955}

declaration


→
[extension-declaration](Declarations.md#extension-declaration)

[‌](){#TP40016643-CH38-NoLink_956}

declaration


→
[subscript-declaration](Declarations.md#subscript-declaration)

[‌](){#TP40016643-CH38-NoLink_957}

declaration


→
[operator-declaration](Declarations.md#operator-declaration)

[‌](){#TP40016643-CH38-NoLink_958}

declarations


→
[declaration](Declarations.md#declaration)[declarations](Declarations.md#declarations)~opt~







Grammar of a top-level declaration



[‌](){#TP40016643-CH38-NoLink_960}

top-level-declaration


→
[statements](Statements.md#statements)~opt~







Grammar of a code block



[‌](){#TP40016643-CH38-NoLink_962}

code-block


→
`{`{.literal}[statements](Statements.md#statements)~opt~`}`{.literal}







Grammar of an import declaration



[‌](){#TP40016643-CH38-NoLink_964}

import-declaration


→
[attributes](Attributes.md#attributes)~opt~`import`{.literal}[import-kind](Declarations.md#import-kind)~opt~[import-path](Declarations.md#import-path)





[‌](){#TP40016643-CH38-NoLink_965}

import-kind


→

`typealias`{.literal}

`struct`{.literal}

`class`{.literal}

`enum`{.literal}

`protocol`{.literal}

`var`{.literal}

`func`{.literal}


[‌](){#TP40016643-CH38-NoLink_966}

import-path


→

[import-path-identifier](Declarations.md#import-path-identifier)

[import-path-identifier](Declarations.md#import-path-identifier)`.`{.literal}[import-path](Declarations.md#import-path)


[‌](){#TP40016643-CH38-NoLink_967}

import-path-identifier


→

[identifier](LexicalStructure.md#identifier)

[operator](LexicalStructure.md#operator)








Grammar of a constant declaration



[‌](){#TP40016643-CH38-NoLink_969}

constant-declaration


→
[attributes](Attributes.md#attributes)~opt~[declaration-modifiers](Declarations.md#declaration-modifiers)~opt~`let`{.literal}[pattern-initializer-list](Declarations.md#pattern-initializer-list)





[‌](){#TP40016643-CH38-NoLink_970}

pattern-initializer-list


→

[pattern-initializer](Declarations.md#pattern-initializer)

[pattern-initializer](Declarations.md#pattern-initializer)`,`{.literal}[pattern-initializer-list](Declarations.md#pattern-initializer-list)


[‌](){#TP40016643-CH38-NoLink_971}

pattern-initializer


→
[pattern](Patterns.md#pattern)[initializer](Declarations.md#initializer)~opt~

[‌](){#TP40016643-CH38-NoLink_972}

initializer


→
`=`{.literal}[expression](Expressions.md#expression)







Grammar of a variable declaration



[‌](){#TP40016643-CH38-NoLink_974}

variable-declaration


→
[variable-declaration-head](Declarations.md#variable-declaration-head)[pattern-initializer-list](Declarations.md#pattern-initializer-list)

[‌](){#TP40016643-CH38-NoLink_975}

variable-declaration


→
[variable-declaration-head](Declarations.md#variable-declaration-head)[variable-name](Declarations.md#variable-name)[type-annotation](Types.md#type-annotation)[code-block](Declarations.md#code-block)

[‌](){#TP40016643-CH38-NoLink_976}

variable-declaration


→
[variable-declaration-head](Declarations.md#variable-declaration-head)[variable-name](Declarations.md#variable-name)[type-annotation](Types.md#type-annotation)[getter-setter-block](Declarations.md#getter-setter-block)

[‌](){#TP40016643-CH38-NoLink_977}

variable-declaration


→
[variable-declaration-head](Declarations.md#variable-declaration-head)[variable-name](Declarations.md#variable-name)[type-annotation](Types.md#type-annotation)[getter-setter-keyword-block](Declarations.md#getter-setter-keyword-block)

[‌](){#TP40016643-CH38-NoLink_978}

variable-declaration


→
[variable-declaration-head](Declarations.md#variable-declaration-head)[variable-name](Declarations.md#variable-name)[initializer](Declarations.md#initializer)[willSet-didSet-block](Declarations.md#willSet-didSet-block)

[‌](){#TP40016643-CH38-NoLink_979}

variable-declaration


→
[variable-declaration-head](Declarations.md#variable-declaration-head)[variable-name](Declarations.md#variable-name)[type-annotation](Types.md#type-annotation)[initializer](Declarations.md#initializer)~opt~[willSet-didSet-block](Declarations.md#willSet-didSet-block)





[‌](){#TP40016643-CH38-NoLink_980}

variable-declaration-head


→
[attributes](Attributes.md#attributes)~opt~[declaration-modifiers](Declarations.md#declaration-modifiers)~opt~`var`{.literal}

[‌](){#TP40016643-CH38-NoLink_981}

variable-name


→
[identifier](LexicalStructure.md#identifier)





[‌](){#TP40016643-CH38-NoLink_982}

getter-setter-block


→
[code-block](Declarations.md#code-block)

[‌](){#TP40016643-CH38-NoLink_983}

getter-setter-block


→
`{`{.literal}[getter-clause](Declarations.md#getter-clause)[setter-clause](Declarations.md#setter-clause)~opt~`}`{.literal}

[‌](){#TP40016643-CH38-NoLink_984}

getter-setter-block


→
`{`{.literal}[setter-clause](Declarations.md#setter-clause)[getter-clause](Declarations.md#getter-clause)`}`{.literal}

[‌](){#TP40016643-CH38-NoLink_985}

getter-clause


→
[attributes](Attributes.md#attributes)~opt~`get`{.literal}[code-block](Declarations.md#code-block)

[‌](){#TP40016643-CH38-NoLink_986}

setter-clause


→
[attributes](Attributes.md#attributes)~opt~`set`{.literal}[setter-name](Declarations.md#setter-name)~opt~[code-block](Declarations.md#code-block)

[‌](){#TP40016643-CH38-NoLink_987}

setter-name


→
`(`{.literal}[identifier](LexicalStructure.md#identifier)`)`{.literal}





[‌](){#TP40016643-CH38-NoLink_988}

getter-setter-keyword-block


→
`{`{.literal}[getter-keyword-clause](Declarations.md#getter-keyword-clause)[setter-keyword-clause](Declarations.md#setter-keyword-clause)~opt~`}`{.literal}

[‌](){#TP40016643-CH38-NoLink_989}

getter-setter-keyword-block


→
`{`{.literal}[setter-keyword-clause](Declarations.md#setter-keyword-clause)[getter-keyword-clause](Declarations.md#getter-keyword-clause)`}`{.literal}

[‌](){#TP40016643-CH38-NoLink_990}

getter-keyword-clause


→
[attributes](Attributes.md#attributes)~opt~`get`{.literal}

[‌](){#TP40016643-CH38-NoLink_991}

setter-keyword-clause


→
[attributes](Attributes.md#attributes)~opt~`set`{.literal}





[‌](){#TP40016643-CH38-NoLink_992}

willSet-didSet-block


→
`{`{.literal}[willSet-clause](Declarations.md#willSet-clause)[didSet-clause](Declarations.md#didSet-clause)~opt~`}`{.literal}

[‌](){#TP40016643-CH38-NoLink_993}

willSet-didSet-block


→
`{`{.literal}[didSet-clause](Declarations.md#didSet-clause)[willSet-clause](Declarations.md#willSet-clause)~opt~`}`{.literal}

[‌](){#TP40016643-CH38-NoLink_994}

willSet-clause


→
[attributes](Attributes.md#attributes)~opt~`willSet`{.literal}[setter-name](Declarations.md#setter-name)~opt~[code-block](Declarations.md#code-block)

[‌](){#TP40016643-CH38-NoLink_995}

didSet-clause


→
[attributes](Attributes.md#attributes)~opt~`didSet`{.literal}[setter-name](Declarations.md#setter-name)~opt~[code-block](Declarations.md#code-block)







Grammar of a type alias declaration



[‌](){#TP40016643-CH38-NoLink_997}

typealias-declaration


→
[typealias-head](Declarations.md#typealias-head)[typealias-assignment](Declarations.md#typealias-assignment)

[‌](){#TP40016643-CH38-NoLink_998}

typealias-head


→
[attributes](Attributes.md#attributes)~opt~[access-level-modifier](Declarations.md#access-level-modifier)~opt~`typealias`{.literal}[typealias-name](Declarations.md#typealias-name)

[‌](){#TP40016643-CH38-NoLink_999}

typealias-name


→
[identifier](LexicalStructure.md#identifier)

[‌](){#TP40016643-CH38-NoLink_1000}

typealias-assignment


→
`=`{.literal}[type](Types.md#type)







Grammar of a function declaration



[‌](){#TP40016643-CH38-NoLink_1002}

function-declaration


→
[function-head](Declarations.md#function-head)[function-name](Declarations.md#function-name)[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)~opt~[function-signature](Declarations.md#function-signature)[function-body](Declarations.md#function-body)~opt~





[‌](){#TP40016643-CH38-NoLink_1003}

function-head


→
[attributes](Attributes.md#attributes)~opt~[declaration-modifiers](Declarations.md#declaration-modifiers)~opt~`func`{.literal}

[‌](){#TP40016643-CH38-NoLink_1004}

function-name


→

[identifier](LexicalStructure.md#identifier)

[operator](LexicalStructure.md#operator)






[‌](){#TP40016643-CH38-NoLink_1005}

function-signature


→
[parameter-clause](Declarations.md#parameter-clause)`throws`{.literal}~opt~[function-result](Declarations.md#function-result)~opt~

[‌](){#TP40016643-CH38-NoLink_1006}

function-signature


→
[parameter-clause](Declarations.md#parameter-clause)`rethrows`{.literal}[function-result](Declarations.md#function-result)~opt~

[‌](){#TP40016643-CH38-NoLink_1007}

function-result


→
`->`{.literal}[attributes](Attributes.md#attributes)~opt~[type](Types.md#type)

[‌](){#TP40016643-CH38-NoLink_1008}

function-body


→
[code-block](Declarations.md#code-block)





[‌](){#TP40016643-CH38-NoLink_1009}

parameter-clause


→

`(`{.literal}`)`{.literal}

`(`{.literal}[parameter-list](Declarations.md#parameter-list)`)`{.literal}


[‌](){#TP40016643-CH38-NoLink_1010}

parameter-list


→

[parameter](Declarations.md#parameter)

[parameter](Declarations.md#parameter)`,`{.literal}[parameter-list](Declarations.md#parameter-list)


[‌](){#TP40016643-CH38-NoLink_1011}

parameter


→
`let`{.literal}~opt~[external-parameter-name](Declarations.md#external-parameter-name)~opt~[local-parameter-name](Declarations.md#local-parameter-name)[type-annotation](Types.md#type-annotation)[default-argument-clause](Declarations.md#default-argument-clause)~opt~

[‌](){#TP40016643-CH38-NoLink_1012}

parameter


→
`inout`{.literal}[external-parameter-name](Declarations.md#external-parameter-name)~opt~[local-parameter-name](Declarations.md#local-parameter-name)[type-annotation](Types.md#type-annotation)

[‌](){#TP40016643-CH38-NoLink_1013}

parameter


→
[external-parameter-name](Declarations.md#external-parameter-name)~opt~[local-parameter-name](Declarations.md#local-parameter-name)[type-annotation](Types.md#type-annotation)`...`{.literal}

[‌](){#TP40016643-CH38-NoLink_1014}

external-parameter-name


→

[identifier](LexicalStructure.md#identifier)

`_`{.literal}


[‌](){#TP40016643-CH38-NoLink_1015}

local-parameter-name


→

[identifier](LexicalStructure.md#identifier)

`_`{.literal}


[‌](){#TP40016643-CH38-NoLink_1016}

default-argument-clause


→
`=`{.literal}[expression](Expressions.md#expression)







Grammar of an enumeration declaration



[‌](){#TP40016643-CH38-NoLink_1018}

enum-declaration


→
[attributes](Attributes.md#attributes)~opt~[access-level-modifier](Declarations.md#access-level-modifier)~opt~[union-style-enum](Declarations.md#union-style-enum)

[‌](){#TP40016643-CH38-NoLink_1019}

enum-declaration


→
[attributes](Attributes.md#attributes)~opt~[access-level-modifier](Declarations.md#access-level-modifier)~opt~[raw-value-style-enum](Declarations.md#raw-value-style-enum)





[‌](){#TP40016643-CH38-NoLink_1020}

union-style-enum


→
`indirect`{.literal}~opt~`enum`{.literal}[enum-name](Declarations.md#enum-name)[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)~opt~[type-inheritance-clause](Types.md#type-inheritance-clause)~opt~`{`{.literal}[union-style-enum-members](Declarations.md#union-style-enum-members)~opt~`}`{.literal}

[‌](){#TP40016643-CH38-NoLink_1021}

union-style-enum-members


→
[union-style-enum-member](Declarations.md#union-style-enum-member)[union-style-enum-members](Declarations.md#union-style-enum-members)~opt~

[‌](){#TP40016643-CH38-NoLink_1022}

union-style-enum-member


→

[declaration](Declarations.md#declaration)

[union-style-enum-case-clause](Declarations.md#union-style-enum-case-clause)


[‌](){#TP40016643-CH38-NoLink_1023}

union-style-enum-case-clause


→
[attributes](Attributes.md#attributes)~opt~`indirect`{.literal}~opt~`case`{.literal}[union-style-enum-case-list](Declarations.md#union-style-enum-case-list)

[‌](){#TP40016643-CH38-NoLink_1024}

union-style-enum-case-list


→

[union-style-enum-case](Declarations.md#union-style-enum-case)

[union-style-enum-case](Declarations.md#union-style-enum-case)`,`{.literal}[union-style-enum-case-list](Declarations.md#union-style-enum-case-list)


[‌](){#TP40016643-CH38-NoLink_1025}

union-style-enum-case


→
[enum-case-name](Declarations.md#enum-case-name)[tuple-type](Types.md#tuple-type)~opt~

[‌](){#TP40016643-CH38-NoLink_1026}

enum-name


→
[identifier](LexicalStructure.md#identifier)

[‌](){#TP40016643-CH38-NoLink_1027}

enum-case-name


→
[identifier](LexicalStructure.md#identifier)





[‌](){#TP40016643-CH38-NoLink_1028}

raw-value-style-enum


→
`enum`{.literal}[enum-name](Declarations.md#enum-name)[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)~opt~[type-inheritance-clause](Types.md#type-inheritance-clause)`{`{.literal}[raw-value-style-enum-members](Declarations.md#raw-value-style-enum-members)`}`{.literal}

[‌](){#TP40016643-CH38-NoLink_1029}

raw-value-style-enum-members


→
[raw-value-style-enum-member](Declarations.md#raw-value-style-enum-member)[raw-value-style-enum-members](Declarations.md#raw-value-style-enum-members)~opt~

[‌](){#TP40016643-CH38-NoLink_1030}

raw-value-style-enum-member


→

[declaration](Declarations.md#declaration)

[raw-value-style-enum-case-clause](Declarations.md#raw-value-style-enum-case-clause)


[‌](){#TP40016643-CH38-NoLink_1031}

raw-value-style-enum-case-clause


→
[attributes](Attributes.md#attributes)~opt~`case`{.literal}[raw-value-style-enum-case-list](Declarations.md#raw-value-style-enum-case-list)

[‌](){#TP40016643-CH38-NoLink_1032}

raw-value-style-enum-case-list


→

[raw-value-style-enum-case](Declarations.md#raw-value-style-enum-case)

[raw-value-style-enum-case](Declarations.md#raw-value-style-enum-case)`,`{.literal}[raw-value-style-enum-case-list](Declarations.md#raw-value-style-enum-case-list)


[‌](){#TP40016643-CH38-NoLink_1033}

raw-value-style-enum-case


→
[enum-case-name](Declarations.md#enum-case-name)[raw-value-assignment](Declarations.md#raw-value-assignment)~opt~

[‌](){#TP40016643-CH38-NoLink_1034}

raw-value-assignment


→
`=`{.literal}[raw-value-literal](Declarations.md#raw-value-literal)

[‌](){#TP40016643-CH38-NoLink_1035}

raw-value-literal


→

[numeric-literal](LexicalStructure.md#numeric-literal)

[static-string-literal](LexicalStructure.md#static-string-literal)

[boolean-literal](LexicalStructure.md#boolean-literal)








Grammar of a structure declaration



[‌](){#TP40016643-CH38-NoLink_1037}

struct-declaration


→
[attributes](Attributes.md#attributes)~opt~[access-level-modifier](Declarations.md#access-level-modifier)~opt~`struct`{.literal}[struct-name](Declarations.md#struct-name)[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)~opt~[type-inheritance-clause](Types.md#type-inheritance-clause)~opt~[struct-body](Declarations.md#struct-body)

[‌](){#TP40016643-CH38-NoLink_1038}

struct-name


→
[identifier](LexicalStructure.md#identifier)

[‌](){#TP40016643-CH38-NoLink_1039}

struct-body


→
`{`{.literal}[declarations](Declarations.md#declarations)~opt~`}`{.literal}







Grammar of a class declaration



[‌](){#TP40016643-CH38-NoLink_1041}

class-declaration


→
[attributes](Attributes.md#attributes)~opt~[access-level-modifier](Declarations.md#access-level-modifier)~opt~`class`{.literal}[class-name](Declarations.md#class-name)[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)~opt~[type-inheritance-clause](Types.md#type-inheritance-clause)~opt~[class-body](Declarations.md#class-body)

[‌](){#TP40016643-CH38-NoLink_1042}

class-name


→
[identifier](LexicalStructure.md#identifier)

[‌](){#TP40016643-CH38-NoLink_1043}

class-body


→
`{`{.literal}[declarations](Declarations.md#declarations)~opt~`}`{.literal}







Grammar of a protocol declaration



[‌](){#TP40016643-CH38-NoLink_1045}

protocol-declaration


→
[attributes](Attributes.md#attributes)~opt~[access-level-modifier](Declarations.md#access-level-modifier)~opt~`protocol`{.literal}[protocol-name](Declarations.md#protocol-name)[type-inheritance-clause](Types.md#type-inheritance-clause)~opt~[protocol-body](Declarations.md#protocol-body)

[‌](){#TP40016643-CH38-NoLink_1046}

protocol-name


→
[identifier](LexicalStructure.md#identifier)

[‌](){#TP40016643-CH38-NoLink_1047}

protocol-body


→
`{`{.literal}[protocol-member-declarations](Declarations.md#protocol-member-declarations)~opt~`}`{.literal}





[‌](){#TP40016643-CH38-NoLink_1048}

protocol-member-declaration


→
[protocol-property-declaration](Declarations.md#protocol-property-declaration)

[‌](){#TP40016643-CH38-NoLink_1049}

protocol-member-declaration


→
[protocol-method-declaration](Declarations.md#protocol-method-declaration)

[‌](){#TP40016643-CH38-NoLink_1050}

protocol-member-declaration


→
[protocol-initializer-declaration](Declarations.md#protocol-initializer-declaration)

[‌](){#TP40016643-CH38-NoLink_1051}

protocol-member-declaration


→
[protocol-subscript-declaration](Declarations.md#protocol-subscript-declaration)

[‌](){#TP40016643-CH38-NoLink_1052}

protocol-member-declaration


→
[protocol-associated-type-declaration](Declarations.md#protocol-associated-type-declaration)

[‌](){#TP40016643-CH38-NoLink_1053}

protocol-member-declarations


→
[protocol-member-declaration](Declarations.md#protocol-member-declaration)[protocol-member-declarations](Declarations.md#protocol-member-declarations)~opt~







Grammar of a protocol property declaration



[‌](){#TP40016643-CH38-NoLink_1055}

protocol-property-declaration


→
[variable-declaration-head](Declarations.md#variable-declaration-head)[variable-name](Declarations.md#variable-name)[type-annotation](Types.md#type-annotation)[getter-setter-keyword-block](Declarations.md#getter-setter-keyword-block)







Grammar of a protocol method declaration



[‌](){#TP40016643-CH38-NoLink_1057}

protocol-method-declaration


→
[function-head](Declarations.md#function-head)[function-name](Declarations.md#function-name)[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)~opt~[function-signature](Declarations.md#function-signature)







Grammar of a protocol initializer declaration



[‌](){#TP40016643-CH38-NoLink_1059}

protocol-initializer-declaration


→
[initializer-head](Declarations.md#initializer-head)[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)~opt~[parameter-clause](Declarations.md#parameter-clause)`throws`{.literal}~opt~

[‌](){#TP40016643-CH38-NoLink_1060}

protocol-initializer-declaration


→
[initializer-head](Declarations.md#initializer-head)[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)~opt~[parameter-clause](Declarations.md#parameter-clause)`rethrows`{.literal}







Grammar of a protocol subscript declaration



[‌](){#TP40016643-CH38-NoLink_1062}

protocol-subscript-declaration


→
[subscript-head](Declarations.md#subscript-head)[subscript-result](Declarations.md#subscript-result)[getter-setter-keyword-block](Declarations.md#getter-setter-keyword-block)







Grammar of a protocol associated type declaration



[‌](){#TP40016643-CH38-NoLink_1064}

protocol-associated-type-declaration


→
[typealias-head](Declarations.md#typealias-head)[type-inheritance-clause](Types.md#type-inheritance-clause)~opt~[typealias-assignment](Declarations.md#typealias-assignment)~opt~







Grammar of an initializer declaration



[‌](){#TP40016643-CH38-NoLink_1066}

initializer-declaration


→
[initializer-head](Declarations.md#initializer-head)[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)~opt~[parameter-clause](Declarations.md#parameter-clause)`throws`{.literal}~opt~[initializer-body](Declarations.md#initializer-body)

[‌](){#TP40016643-CH38-NoLink_1067}

initializer-declaration


→
[initializer-head](Declarations.md#initializer-head)[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)~opt~[parameter-clause](Declarations.md#parameter-clause)`rethrows`{.literal}[initializer-body](Declarations.md#initializer-body)

[‌](){#TP40016643-CH38-NoLink_1068}

initializer-head


→
[attributes](Attributes.md#attributes)~opt~[declaration-modifiers](Declarations.md#declaration-modifiers)~opt~`init`{.literal}

[‌](){#TP40016643-CH38-NoLink_1069}

initializer-head


→
[attributes](Attributes.md#attributes)~opt~[declaration-modifiers](Declarations.md#declaration-modifiers)~opt~`init`{.literal}`?`{.literal}

[‌](){#TP40016643-CH38-NoLink_1070}

initializer-head


→
[attributes](Attributes.md#attributes)~opt~[declaration-modifiers](Declarations.md#declaration-modifiers)~opt~`init`{.literal}`!`{.literal}

[‌](){#TP40016643-CH38-NoLink_1071}

initializer-body


→
[code-block](Declarations.md#code-block)







Grammar of a deinitializer declaration



[‌](){#TP40016643-CH38-NoLink_1073}

deinitializer-declaration


→
[attributes](Attributes.md#attributes)~opt~`deinit`{.literal}[code-block](Declarations.md#code-block)







Grammar of an extension declaration



[‌](){#TP40016643-CH38-NoLink_1075}

extension-declaration


→
[access-level-modifier](Declarations.md#access-level-modifier)~opt~`extension`{.literal}[type-identifier](Types.md#type-identifier)[type-inheritance-clause](Types.md#type-inheritance-clause)~opt~[extension-body](Declarations.md#extension-body)

[‌](){#TP40016643-CH38-NoLink_1076}

extension-body


→
`{`{.literal}[declarations](Declarations.md#declarations)~opt~`}`{.literal}







Grammar of a subscript declaration



[‌](){#TP40016643-CH38-NoLink_1078}

subscript-declaration


→
[subscript-head](Declarations.md#subscript-head)[subscript-result](Declarations.md#subscript-result)[code-block](Declarations.md#code-block)

[‌](){#TP40016643-CH38-NoLink_1079}

subscript-declaration


→
[subscript-head](Declarations.md#subscript-head)[subscript-result](Declarations.md#subscript-result)[getter-setter-block](Declarations.md#getter-setter-block)

[‌](){#TP40016643-CH38-NoLink_1080}

subscript-declaration


→
[subscript-head](Declarations.md#subscript-head)[subscript-result](Declarations.md#subscript-result)[getter-setter-keyword-block](Declarations.md#getter-setter-keyword-block)

[‌](){#TP40016643-CH38-NoLink_1081}

subscript-head


→
[attributes](Attributes.md#attributes)~opt~[declaration-modifiers](Declarations.md#declaration-modifiers)~opt~`subscript`{.literal}[parameter-clause](Declarations.md#parameter-clause)

[‌](){#TP40016643-CH38-NoLink_1082}

subscript-result


→
`->`{.literal}[attributes](Attributes.md#attributes)~opt~[type](Types.md#type)







Grammar of an operator declaration



[‌](){#TP40016643-CH38-NoLink_1084}

operator-declaration


→

[prefix-operator-declaration](Declarations.md#prefix-operator-declaration)

[postfix-operator-declaration](Declarations.md#postfix-operator-declaration)

[infix-operator-declaration](Declarations.md#infix-operator-declaration)






[‌](){#TP40016643-CH38-NoLink_1085}

prefix-operator-declaration


→
`prefix`{.literal}`operator`{.literal}[operator](LexicalStructure.md#operator)`{`{.literal}`}`{.literal}

[‌](){#TP40016643-CH38-NoLink_1086}

postfix-operator-declaration


→
`postfix`{.literal}`operator`{.literal}[operator](LexicalStructure.md#operator)`{`{.literal}`}`{.literal}

[‌](){#TP40016643-CH38-NoLink_1087}

infix-operator-declaration


→
`infix`{.literal}`operator`{.literal}[operator](LexicalStructure.md#operator)`{`{.literal}[infix-operator-attributes](Declarations.md#infix-operator-attributes)~opt~`}`{.literal}





[‌](){#TP40016643-CH38-NoLink_1088}

infix-operator-attributes


→
[precedence-clause](Declarations.md#precedence-clause)~opt~[associativity-clause](Declarations.md#associativity-clause)~opt~

[‌](){#TP40016643-CH38-NoLink_1089}

precedence-clause


→
`precedence`{.literal}[precedence-level](Declarations.md#precedence-level)

[‌](){#TP40016643-CH38-NoLink_1090}

precedence-level


→
A decimal integer between 0 and 255, inclusive

[‌](){#TP40016643-CH38-NoLink_1091}

associativity-clause


→
`associativity`{.literal}[associativity](Declarations.md#associativity)

[‌](){#TP40016643-CH38-NoLink_1092}

associativity


→

`left`{.literal}

`right`{.literal}

`none`{.literal}








Grammar of a declaration modifier



[‌](){#TP40016643-CH38-NoLink_1094}

declaration-modifier


→

`class`{.literal}

`convenience`{.literal}

`dynamic`{.literal}

`final`{.literal}

`infix`{.literal}

`lazy`{.literal}

`mutating`{.literal}

`nonmutating`{.literal}

`optional`{.literal}

`override`{.literal}

`postfix`{.literal}

`prefix`{.literal}

`required`{.literal}

`static`{.literal}

`unowned`{.literal}

`unowned`{.literal}`(`{.literal}`safe`{.literal}`)`{.literal}

`unowned`{.literal}`(`{.literal}`unsafe`{.literal}`)`{.literal}

`weak`{.literal}


[‌](){#TP40016643-CH38-NoLink_1095}

declaration-modifier


→
[access-level-modifier](Declarations.md#access-level-modifier)

[‌](){#TP40016643-CH38-NoLink_1096}

declaration-modifiers


→
[declaration-modifier](Declarations.md#declaration-modifier)[declaration-modifiers](Declarations.md#declaration-modifiers)~opt~





[‌](){#TP40016643-CH38-NoLink_1097}

access-level-modifier


→

`internal`{.literal}

`internal`{.literal}`(`{.literal}`set`{.literal}`)`{.literal}


[‌](){#TP40016643-CH38-NoLink_1098}

access-level-modifier


→

`private`{.literal}

`private`{.literal}`(`{.literal}`set`{.literal}`)`{.literal}


[‌](){#TP40016643-CH38-NoLink_1099}

access-level-modifier


→

`public`{.literal}

`public`{.literal}`(`{.literal}`set`{.literal}`)`{.literal}










[‌](){#TP40016643-CH38-ID478}
### Patterns {#patterns .section-name}



Grammar of a pattern



[‌](){#TP40016643-CH38-NoLink_1101}

pattern


→
[wildcard-pattern](Patterns.md#wildcard-pattern)[type-annotation](Types.md#type-annotation)~opt~

[‌](){#TP40016643-CH38-NoLink_1102}

pattern


→
[identifier-pattern](Patterns.md#identifier-pattern)[type-annotation](Types.md#type-annotation)~opt~

[‌](){#TP40016643-CH38-NoLink_1103}

pattern


→
[value-binding-pattern](Patterns.md#value-binding-pattern)

[‌](){#TP40016643-CH38-NoLink_1104}

pattern


→
[tuple-pattern](Patterns.md#tuple-pattern)[type-annotation](Types.md#type-annotation)~opt~

[‌](){#TP40016643-CH38-NoLink_1105}

pattern


→
[enum-case-pattern](Patterns.md#enum-case-pattern)

[‌](){#TP40016643-CH38-NoLink_1106}

pattern


→
[optional-pattern](Patterns.md#optional-pattern)

[‌](){#TP40016643-CH38-NoLink_1107}

pattern


→
[type-casting-pattern](Patterns.md#type-casting-pattern)

[‌](){#TP40016643-CH38-NoLink_1108}

pattern


→
[expression-pattern](Patterns.md#expression-pattern)







Grammar of a wildcard pattern



[‌](){#TP40016643-CH38-NoLink_1110}

wildcard-pattern


→
`_`{.literal}







Grammar of an identifier pattern



[‌](){#TP40016643-CH38-NoLink_1112}

identifier-pattern


→
[identifier](LexicalStructure.md#identifier)







Grammar of a value-binding pattern



[‌](){#TP40016643-CH38-NoLink_1114}

value-binding-pattern


→
`let`{.literal}[pattern](Patterns.md#pattern)







Grammar of a tuple pattern



[‌](){#TP40016643-CH38-NoLink_1116}

tuple-pattern


→
`(`{.literal}[tuple-pattern-element-list](Patterns.md#tuple-pattern-element-list)~opt~`)`{.literal}

[‌](){#TP40016643-CH38-NoLink_1117}

tuple-pattern-element-list


→

[tuple-pattern-element](Patterns.md#tuple-pattern-element)

[tuple-pattern-element](Patterns.md#tuple-pattern-element)`,`{.literal}[tuple-pattern-element-list](Patterns.md#tuple-pattern-element-list)


[‌](){#TP40016643-CH38-NoLink_1118}

tuple-pattern-element


→
[pattern](Patterns.md#pattern)







Grammar of an enumeration case pattern



[‌](){#TP40016643-CH38-NoLink_1120}

enum-case-pattern


→
[type-identifier](Types.md#type-identifier)~opt~`.`{.literal}[enum-case-name](Declarations.md#enum-case-name)[tuple-pattern](Patterns.md#tuple-pattern)~opt~







Grammar of an optional pattern



[‌](){#TP40016643-CH38-NoLink_1122}

optional-pattern


→
[identifier-pattern](Patterns.md#identifier-pattern)`?`{.literal}







Grammar of a type casting pattern



[‌](){#TP40016643-CH38-NoLink_1124}

type-casting-pattern


→

[is-pattern](Patterns.md#is-pattern)

[as-pattern](Patterns.md#as-pattern)


[‌](){#TP40016643-CH38-NoLink_1125}

is-pattern


→
`is`{.literal}[type](Types.md#type)

[‌](){#TP40016643-CH38-NoLink_1126}

as-pattern


→
[pattern](Patterns.md#pattern)`as`{.literal}[type](Types.md#type)







Grammar of an expression pattern



[‌](){#TP40016643-CH38-NoLink_1128}

expression-pattern


→
[expression](Expressions.md#expression)









[‌](){#TP40016643-CH38-ID479}
### Attributes {#attributes .section-name}



Grammar of an attribute



[‌](){#TP40016643-CH38-NoLink_1130}

attribute


→
`@`{.literal}[attribute-name](Attributes.md#attribute-name)[attribute-argument-clause](Attributes.md#attribute-argument-clause)~opt~

[‌](){#TP40016643-CH38-NoLink_1131}

attribute-name


→
[identifier](LexicalStructure.md#identifier)

[‌](){#TP40016643-CH38-NoLink_1132}

attribute-argument-clause


→
`(`{.literal}[balanced-tokens](Attributes.md#balanced-tokens)~opt~`)`{.literal}

[‌](){#TP40016643-CH38-NoLink_1133}

attributes


→
[attribute](Attributes.md#attribute)[attributes](Attributes.md#attributes)~opt~





[‌](){#TP40016643-CH38-NoLink_1134}

balanced-tokens


→
[balanced-token](Attributes.md#balanced-token)[balanced-tokens](Attributes.md#balanced-tokens)~opt~

[‌](){#TP40016643-CH38-NoLink_1135}

balanced-token


→
`(`{.literal}[balanced-tokens](Attributes.md#balanced-tokens)~opt~`)`{.literal}

[‌](){#TP40016643-CH38-NoLink_1136}

balanced-token


→
`[`{.literal}[balanced-tokens](Attributes.md#balanced-tokens)~opt~`]`{.literal}

[‌](){#TP40016643-CH38-NoLink_1137}

balanced-token


→
`{`{.literal}[balanced-tokens](Attributes.md#balanced-tokens)~opt~`}`{.literal}

[‌](){#TP40016643-CH38-NoLink_1138}

balanced-token


→
Any identifier, keyword, literal, or operator

[‌](){#TP40016643-CH38-NoLink_1139}

balanced-token


→
Any punctuation except `(`{.literal}, `)`{.literal}, `[`{.literal}, `]`{.literal}, `{`{.literal}, or `}`{.literal}









[‌](){#TP40016643-CH38-ID480}
### Expressions {#expressions .section-name}



Grammar of an expression



[‌](){#TP40016643-CH38-NoLink_1141}

expression


→
[try-operator](Expressions.md#try-operator)~opt~[prefix-expression](Expressions.md#prefix-expression)[binary-expressions](Expressions.md#binary-expressions)~opt~

[‌](){#TP40016643-CH38-NoLink_1142}

expression-list


→

[expression](Expressions.md#expression)

[expression](Expressions.md#expression)`,`{.literal}[expression-list](Expressions.md#expression-list)








Grammar of a prefix expression



[‌](){#TP40016643-CH38-NoLink_1144}

prefix-expression


→
[prefix-operator](LexicalStructure.md#prefix-operator)~opt~[postfix-expression](Expressions.md#postfix-expression)

[‌](){#TP40016643-CH38-NoLink_1145}

prefix-expression


→
[in-out-expression](Expressions.md#in-out-expression)

[‌](){#TP40016643-CH38-NoLink_1146}

in-out-expression


→
`&`{.literal}[identifier](LexicalStructure.md#identifier)







Grammar of a try expression



[‌](){#TP40016643-CH38-NoLink_1148}

try-operator


→

`try`{.literal}

`try`{.literal}`?`{.literal}

`try`{.literal}`!`{.literal}








Grammar of a binary expression



[‌](){#TP40016643-CH38-NoLink_1150}

binary-expression


→
[binary-operator](LexicalStructure.md#binary-operator)[prefix-expression](Expressions.md#prefix-expression)

[‌](){#TP40016643-CH38-NoLink_1151}

binary-expression


→
[assignment-operator](Expressions.md#assignment-operator)[try-operator](Expressions.md#try-operator)~opt~[prefix-expression](Expressions.md#prefix-expression)

[‌](){#TP40016643-CH38-NoLink_1152}

binary-expression


→
[conditional-operator](Expressions.md#conditional-operator)[try-operator](Expressions.md#try-operator)~opt~[prefix-expression](Expressions.md#prefix-expression)

[‌](){#TP40016643-CH38-NoLink_1153}

binary-expression


→
[type-casting-operator](Expressions.md#type-casting-operator)

[‌](){#TP40016643-CH38-NoLink_1154}

binary-expressions


→
[binary-expression](Expressions.md#binary-expression)[binary-expressions](Expressions.md#binary-expressions)~opt~







Grammar of an assignment operator



[‌](){#TP40016643-CH38-NoLink_1156}

assignment-operator


→
`=`{.literal}







Grammar of a conditional operator



[‌](){#TP40016643-CH38-NoLink_1158}

conditional-operator


→
`?`{.literal}[try-operator](Expressions.md#try-operator)~opt~[expression](Expressions.md#expression)`:`{.literal}







Grammar of a type-casting operator



[‌](){#TP40016643-CH38-NoLink_1160}

type-casting-operator


→
`is`{.literal}[type](Types.md#type)

[‌](){#TP40016643-CH38-NoLink_1161}

type-casting-operator


→
`as`{.literal}[type](Types.md#type)

[‌](){#TP40016643-CH38-NoLink_1162}

type-casting-operator


→
`as`{.literal}`?`{.literal}[type](Types.md#type)

[‌](){#TP40016643-CH38-NoLink_1163}

type-casting-operator


→
`as`{.literal}`!`{.literal}[type](Types.md#type)







Grammar of a primary expression



[‌](){#TP40016643-CH38-NoLink_1165}

primary-expression


→
[identifier](LexicalStructure.md#identifier)[generic-argument-clause](GenericParametersAndArguments.md#generic-argument-clause)~opt~

[‌](){#TP40016643-CH38-NoLink_1166}

primary-expression


→
[literal-expression](Expressions.md#literal-expression)

[‌](){#TP40016643-CH38-NoLink_1167}

primary-expression


→
[self-expression](Expressions.md#self-expression)

[‌](){#TP40016643-CH38-NoLink_1168}

primary-expression


→
[superclass-expression](Expressions.md#superclass-expression)

[‌](){#TP40016643-CH38-NoLink_1169}

primary-expression


→
[closure-expression](Expressions.md#closure-expression)

[‌](){#TP40016643-CH38-NoLink_1170}

primary-expression


→
[parenthesized-expression](Expressions.md#parenthesized-expression)

[‌](){#TP40016643-CH38-NoLink_1171}

primary-expression


→
[implicit-member-expression](Expressions.md#implicit-member-expression)

[‌](){#TP40016643-CH38-NoLink_1172}

primary-expression


→
[wildcard-expression](Expressions.md#wildcard-expression)







Grammar of a literal expression



[‌](){#TP40016643-CH38-NoLink_1174}

literal-expression


→
[literal](LexicalStructure.md#literal)

[‌](){#TP40016643-CH38-NoLink_1175}

literal-expression


→

[array-literal](Expressions.md#array-literal)

[dictionary-literal](Expressions.md#dictionary-literal)


[‌](){#TP40016643-CH38-NoLink_1176}

literal-expression


→

`__FILE__`{.literal}

`__LINE__`{.literal}

`__COLUMN__`{.literal}

`__FUNCTION__`{.literal}






[‌](){#TP40016643-CH38-NoLink_1177}

array-literal


→
`[`{.literal}[array-literal-items](Expressions.md#array-literal-items)~opt~`]`{.literal}

[‌](){#TP40016643-CH38-NoLink_1178}

array-literal-items


→

[array-literal-item](Expressions.md#array-literal-item)`,`{.literal}~opt~

[array-literal-item](Expressions.md#array-literal-item)`,`{.literal}[array-literal-items](Expressions.md#array-literal-items)


[‌](){#TP40016643-CH38-NoLink_1179}

array-literal-item


→
[expression](Expressions.md#expression)





[‌](){#TP40016643-CH38-NoLink_1180}

dictionary-literal


→

`[`{.literal}[dictionary-literal-items](Expressions.md#dictionary-literal-items)`]`{.literal}

`[`{.literal}`:`{.literal}`]`{.literal}


[‌](){#TP40016643-CH38-NoLink_1181}

dictionary-literal-items


→

[dictionary-literal-item](Expressions.md#dictionary-literal-item)`,`{.literal}~opt~

[dictionary-literal-item](Expressions.md#dictionary-literal-item)`,`{.literal}[dictionary-literal-items](Expressions.md#dictionary-literal-items)


[‌](){#TP40016643-CH38-NoLink_1182}

dictionary-literal-item


→
[expression](Expressions.md#expression)`:`{.literal}[expression](Expressions.md#expression)







Grammar of a self expression



[‌](){#TP40016643-CH38-NoLink_1184}

self-expression


→

`self`{.literal}

[self-method-expression](Expressions.md#self-method-expression)

[self-subscript-expression](Expressions.md#self-subscript-expression)

[self-initializer-expression](Expressions.md#self-initializer-expression)






[‌](){#TP40016643-CH38-NoLink_1185}

self-method-expression


→
`self`{.literal}`.`{.literal}[identifier](LexicalStructure.md#identifier)

[‌](){#TP40016643-CH38-NoLink_1186}

self-subscript-expression


→
`self`{.literal}`[`{.literal}[expression-list](Expressions.md#expression-list)`]`{.literal}

[‌](){#TP40016643-CH38-NoLink_1187}

self-initializer-expression


→
`self`{.literal}`.`{.literal}`init`{.literal}







Grammar of a superclass expression



[‌](){#TP40016643-CH38-NoLink_1189}

superclass-expression


→

[superclass-method-expression](Expressions.md#superclass-method-expression)

[superclass-subscript-expression](Expressions.md#superclass-subscript-expression)

[superclass-initializer-expression](Expressions.md#superclass-initializer-expression)






[‌](){#TP40016643-CH38-NoLink_1190}

superclass-method-expression


→
`super`{.literal}`.`{.literal}[identifier](LexicalStructure.md#identifier)

[‌](){#TP40016643-CH38-NoLink_1191}

superclass-subscript-expression


→
`super`{.literal}`[`{.literal}[expression-list](Expressions.md#expression-list)`]`{.literal}

[‌](){#TP40016643-CH38-NoLink_1192}

superclass-initializer-expression


→
`super`{.literal}`.`{.literal}`init`{.literal}







Grammar of a closure expression



[‌](){#TP40016643-CH38-NoLink_1194}

closure-expression


→
`{`{.literal}[closure-signature](Expressions.md#closure-signature)~opt~[statements](Statements.md#statements)`}`{.literal}





[‌](){#TP40016643-CH38-NoLink_1195}

closure-signature


→
[parameter-clause](Declarations.md#parameter-clause)[function-result](Declarations.md#function-result)~opt~`in`{.literal}

[‌](){#TP40016643-CH38-NoLink_1196}

closure-signature


→
[identifier-list](LexicalStructure.md#identifier-list)[function-result](Declarations.md#function-result)~opt~`in`{.literal}

[‌](){#TP40016643-CH38-NoLink_1197}

closure-signature


→
[capture-list](Expressions.md#capture-list)[parameter-clause](Declarations.md#parameter-clause)[function-result](Declarations.md#function-result)~opt~`in`{.literal}

[‌](){#TP40016643-CH38-NoLink_1198}

closure-signature


→
[capture-list](Expressions.md#capture-list)[identifier-list](LexicalStructure.md#identifier-list)[function-result](Declarations.md#function-result)~opt~`in`{.literal}

[‌](){#TP40016643-CH38-NoLink_1199}

closure-signature


→
[capture-list](Expressions.md#capture-list)`in`{.literal}





[‌](){#TP40016643-CH38-NoLink_1200}

capture-list


→
`[`{.literal}[capture-list-items](Expressions.md#capture-list-items)`]`{.literal}

[‌](){#TP40016643-CH38-NoLink_1201}

capture-list-items


→

[capture-list-item](Expressions.md#capture-list-item)

[capture-list-item](Expressions.md#capture-list-item)`,`{.literal}[capture-list-items](Expressions.md#capture-list-items)


[‌](){#TP40016643-CH38-NoLink_1202}

capture-list-item


→
[capture-specifier](Expressions.md#capture-specifier)~opt~[expression](Expressions.md#expression)

[‌](){#TP40016643-CH38-NoLink_1203}

capture-specifier


→

`weak`{.literal}

`unowned`{.literal}

`unowned(safe)`{.literal}

`unowned(unsafe)`{.literal}








Grammar of a implicit member expression



[‌](){#TP40016643-CH38-NoLink_1205}

implicit-member-expression


→
`.`{.literal}[identifier](LexicalStructure.md#identifier)







Grammar of a parenthesized expression



[‌](){#TP40016643-CH38-NoLink_1207}

parenthesized-expression


→
`(`{.literal}[expression-element-list](Expressions.md#expression-element-list)~opt~`)`{.literal}

[‌](){#TP40016643-CH38-NoLink_1208}

expression-element-list


→

[expression-element](Expressions.md#expression-element)

[expression-element](Expressions.md#expression-element)`,`{.literal}[expression-element-list](Expressions.md#expression-element-list)


[‌](){#TP40016643-CH38-NoLink_1209}

expression-element


→

[expression](Expressions.md#expression)

[identifier](LexicalStructure.md#identifier)`:`{.literal}[expression](Expressions.md#expression)








Grammar of a wildcard expression



[‌](){#TP40016643-CH38-NoLink_1211}

wildcard-expression


→
`_`{.literal}







Grammar of a postfix expression



[‌](){#TP40016643-CH38-NoLink_1213}

postfix-expression


→
[primary-expression](Expressions.md#primary-expression)

[‌](){#TP40016643-CH38-NoLink_1214}

postfix-expression


→
[postfix-expression](Expressions.md#postfix-expression)[postfix-operator](LexicalStructure.md#postfix-operator)

[‌](){#TP40016643-CH38-NoLink_1215}

postfix-expression


→
[function-call-expression](Expressions.md#function-call-expression)

[‌](){#TP40016643-CH38-NoLink_1216}

postfix-expression


→
[initializer-expression](Expressions.md#initializer-expression)

[‌](){#TP40016643-CH38-NoLink_1217}

postfix-expression


→
[explicit-member-expression](Expressions.md#explicit-member-expression)

[‌](){#TP40016643-CH38-NoLink_1218}

postfix-expression


→
[postfix-self-expression](Expressions.md#postfix-self-expression)

[‌](){#TP40016643-CH38-NoLink_1219}

postfix-expression


→
[dynamic-type-expression](Expressions.md#dynamic-type-expression)

[‌](){#TP40016643-CH38-NoLink_1220}

postfix-expression


→
[subscript-expression](Expressions.md#subscript-expression)

[‌](){#TP40016643-CH38-NoLink_1221}

postfix-expression


→
[forced-value-expression](Expressions.md#forced-value-expression)

[‌](){#TP40016643-CH38-NoLink_1222}

postfix-expression


→
[optional-chaining-expression](Expressions.md#optional-chaining-expression)







Grammar of a function call expression



[‌](){#TP40016643-CH38-NoLink_1224}

function-call-expression


→
[postfix-expression](Expressions.md#postfix-expression)[parenthesized-expression](Expressions.md#parenthesized-expression)

[‌](){#TP40016643-CH38-NoLink_1225}

function-call-expression


→
[postfix-expression](Expressions.md#postfix-expression)[parenthesized-expression](Expressions.md#parenthesized-expression)~opt~[trailing-closure](Expressions.md#trailing-closure)

[‌](){#TP40016643-CH38-NoLink_1226}

trailing-closure


→
[closure-expression](Expressions.md#closure-expression)







Grammar of an initializer expression



[‌](){#TP40016643-CH38-NoLink_1228}

initializer-expression


→
[postfix-expression](Expressions.md#postfix-expression)`.`{.literal}`init`{.literal}







Grammar of an explicit member expression



[‌](){#TP40016643-CH38-NoLink_1230}

explicit-member-expression


→
[postfix-expression](Expressions.md#postfix-expression)`.`{.literal}[decimal-digits](LexicalStructure.md#decimal-digits)

[‌](){#TP40016643-CH38-NoLink_1231}

explicit-member-expression


→
[postfix-expression](Expressions.md#postfix-expression)`.`{.literal}[identifier](LexicalStructure.md#identifier)[generic-argument-clause](GenericParametersAndArguments.md#generic-argument-clause)~opt~







Grammar of a self expression



[‌](){#TP40016643-CH38-NoLink_1233}

postfix-self-expression


→
[postfix-expression](Expressions.md#postfix-expression)`.`{.literal}`self`{.literal}







Grammar of a dynamic type expression



[‌](){#TP40016643-CH38-NoLink_1235}

dynamic-type-expression


→
[postfix-expression](Expressions.md#postfix-expression)`.`{.literal}`dynamicType`{.literal}







Grammar of a subscript expression



[‌](){#TP40016643-CH38-NoLink_1237}

subscript-expression


→
[postfix-expression](Expressions.md#postfix-expression)`[`{.literal}[expression-list](Expressions.md#expression-list)`]`{.literal}







Grammar of a forced-value expression



[‌](){#TP40016643-CH38-NoLink_1239}

forced-value-expression


→
[postfix-expression](Expressions.md#postfix-expression)`!`{.literal}







Grammar of an optional-chaining expression



[‌](){#TP40016643-CH38-NoLink_1241}

optional-chaining-expression


→
[postfix-expression](Expressions.md#postfix-expression)`?`{.literal}









[‌](){#TP40016643-CH38-ID481}
### Lexical Structure {#lexical-structure .section-name}



Grammar of an identifier



[‌](){#TP40016643-CH38-NoLink_1243}

identifier


→
[identifier-head](LexicalStructure.md#identifier-head)[identifier-characters](LexicalStructure.md#identifier-characters)~opt~

[‌](){#TP40016643-CH38-NoLink_1244}

identifier


→
`` ` ``{.literal}[identifier-head](LexicalStructure.md#identifier-head)[identifier-characters](LexicalStructure.md#identifier-characters)~opt~`` ` ``{.literal}

[‌](){#TP40016643-CH38-NoLink_1245}

identifier


→
[implicit-parameter-name](LexicalStructure.md#implicit-parameter-name)

[‌](){#TP40016643-CH38-NoLink_1246}

identifier-list


→

[identifier](LexicalStructure.md#identifier)

[identifier](LexicalStructure.md#identifier)`,`{.literal}[identifier-list](LexicalStructure.md#identifier-list)






[‌](){#TP40016643-CH38-NoLink_1247}

identifier-head


→
Upper- or lowercase letter A through Z

[‌](){#TP40016643-CH38-NoLink_1248}

identifier-head


→
`_`{.literal}

[‌](){#TP40016643-CH38-NoLink_1249}

identifier-head


→
U+00A8, U+00AA, U+00AD, U+00AF, U+00B2–U+00B5, or U+00B7–U+00BA

[‌](){#TP40016643-CH38-NoLink_1250}

identifier-head


→
U+00BC–U+00BE, U+00C0–U+00D6, U+00D8–U+00F6, or U+00F8–U+00FF

[‌](){#TP40016643-CH38-NoLink_1251}

identifier-head


→
U+0100–U+02FF, U+0370–U+167F, U+1681–U+180D, or U+180F–U+1DBF

[‌](){#TP40016643-CH38-NoLink_1252}

identifier-head


→
U+1E00–U+1FFF

[‌](){#TP40016643-CH38-NoLink_1253}

identifier-head


→
U+200B–U+200D, U+202A–U+202E, U+203F–U+2040, U+2054, or U+2060–U+206F

[‌](){#TP40016643-CH38-NoLink_1254}

identifier-head


→
U+2070–U+20CF, U+2100–U+218F, U+2460–U+24FF, or U+2776–U+2793

[‌](){#TP40016643-CH38-NoLink_1255}

identifier-head


→
U+2C00–U+2DFF or U+2E80–U+2FFF

[‌](){#TP40016643-CH38-NoLink_1256}

identifier-head


→
U+3004–U+3007, U+3021–U+302F, U+3031–U+303F, or U+3040–U+D7FF

[‌](){#TP40016643-CH38-NoLink_1257}

identifier-head


→
U+F900–U+FD3D, U+FD40–U+FDCF, U+FDF0–U+FE1F, or U+FE30–U+FE44

[‌](){#TP40016643-CH38-NoLink_1258}

identifier-head


→
U+FE47–U+FFFD

[‌](){#TP40016643-CH38-NoLink_1259}

identifier-head


→
U+10000–U+1FFFD, U+20000–U+2FFFD, U+30000–U+3FFFD, or U+40000–U+4FFFD

[‌](){#TP40016643-CH38-NoLink_1260}

identifier-head


→
U+50000–U+5FFFD, U+60000–U+6FFFD, U+70000–U+7FFFD, or U+80000–U+8FFFD

[‌](){#TP40016643-CH38-NoLink_1261}

identifier-head


→
U+90000–U+9FFFD, U+A0000–U+AFFFD, U+B0000–U+BFFFD, or U+C0000–U+CFFFD

[‌](){#TP40016643-CH38-NoLink_1262}

identifier-head


→
U+D0000–U+DFFFD or U+E0000–U+EFFFD





[‌](){#TP40016643-CH38-NoLink_1263}

identifier-character


→
Digit 0 through 9

[‌](){#TP40016643-CH38-NoLink_1264}

identifier-character


→
U+0300–U+036F, U+1DC0–U+1DFF, U+20D0–U+20FF, or U+FE20–U+FE2F

[‌](){#TP40016643-CH38-NoLink_1265}

identifier-character


→
[identifier-head](LexicalStructure.md#identifier-head)

[‌](){#TP40016643-CH38-NoLink_1266}

identifier-characters


→
[identifier-character](LexicalStructure.md#identifier-character)[identifier-characters](LexicalStructure.md#identifier-characters)~opt~





[‌](){#TP40016643-CH38-NoLink_1267}

implicit-parameter-name


→
`$`{.literal}[decimal-digits](LexicalStructure.md#decimal-digits)







Grammar of a literal



[‌](){#TP40016643-CH38-NoLink_1269}

literal


→

[numeric-literal](LexicalStructure.md#numeric-literal)

[string-literal](LexicalStructure.md#string-literal)

[boolean-literal](LexicalStructure.md#boolean-literal)

[nil-literal](LexicalStructure.md#nil-literal)






[‌](){#TP40016643-CH38-NoLink_1270}

numeric-literal


→

`-`{.literal}~opt~[integer-literal](LexicalStructure.md#integer-literal)

`-`{.literal}~opt~[floating-point-literal](LexicalStructure.md#floating-point-literal)


[‌](){#TP40016643-CH38-NoLink_1271}

boolean-literal


→

`true`{.literal}

`false`{.literal}


[‌](){#TP40016643-CH38-NoLink_1272}

nil-literal


→
`nil`{.literal}







Grammar of an integer literal



[‌](){#TP40016643-CH38-NoLink_1274}

integer-literal


→
[binary-literal](LexicalStructure.md#binary-literal)

[‌](){#TP40016643-CH38-NoLink_1275}

integer-literal


→
[octal-literal](LexicalStructure.md#octal-literal)

[‌](){#TP40016643-CH38-NoLink_1276}

integer-literal


→
[decimal-literal](LexicalStructure.md#decimal-literal)

[‌](){#TP40016643-CH38-NoLink_1277}

integer-literal


→
[hexadecimal-literal](LexicalStructure.md#hexadecimal-literal)





[‌](){#TP40016643-CH38-NoLink_1278}

binary-literal


→
`0b`{.literal}[binary-digit](LexicalStructure.md#binary-digit)[binary-literal-characters](LexicalStructure.md#binary-literal-characters)~opt~

[‌](){#TP40016643-CH38-NoLink_1279}

binary-digit


→
Digit 0 or 1

[‌](){#TP40016643-CH38-NoLink_1280}

binary-literal-character


→

[binary-digit](LexicalStructure.md#binary-digit)

`_`{.literal}


[‌](){#TP40016643-CH38-NoLink_1281}

binary-literal-characters


→
[binary-literal-character](LexicalStructure.md#binary-literal-character)[binary-literal-characters](LexicalStructure.md#binary-literal-characters)~opt~





[‌](){#TP40016643-CH38-NoLink_1282}

octal-literal


→
`0o`{.literal}[octal-digit](LexicalStructure.md#octal-digit)[octal-literal-characters](LexicalStructure.md#octal-literal-characters)~opt~

[‌](){#TP40016643-CH38-NoLink_1283}

octal-digit


→
Digit 0 through 7

[‌](){#TP40016643-CH38-NoLink_1284}

octal-literal-character


→

[octal-digit](LexicalStructure.md#octal-digit)

`_`{.literal}


[‌](){#TP40016643-CH38-NoLink_1285}

octal-literal-characters


→
[octal-literal-character](LexicalStructure.md#octal-literal-character)[octal-literal-characters](LexicalStructure.md#octal-literal-characters)~opt~





[‌](){#TP40016643-CH38-NoLink_1286}

decimal-literal


→
[decimal-digit](LexicalStructure.md#decimal-digit)[decimal-literal-characters](LexicalStructure.md#decimal-literal-characters)~opt~

[‌](){#TP40016643-CH38-NoLink_1287}

decimal-digit


→
Digit 0 through 9

[‌](){#TP40016643-CH38-NoLink_1288}

decimal-digits


→
[decimal-digit](LexicalStructure.md#decimal-digit)[decimal-digits](LexicalStructure.md#decimal-digits)~opt~

[‌](){#TP40016643-CH38-NoLink_1289}

decimal-literal-character


→

[decimal-digit](LexicalStructure.md#decimal-digit)

`_`{.literal}


[‌](){#TP40016643-CH38-NoLink_1290}

decimal-literal-characters


→
[decimal-literal-character](LexicalStructure.md#decimal-literal-character)[decimal-literal-characters](LexicalStructure.md#decimal-literal-characters)~opt~





[‌](){#TP40016643-CH38-NoLink_1291}

hexadecimal-literal


→
`0x`{.literal}[hexadecimal-digit](LexicalStructure.md#hexadecimal-digit)[hexadecimal-literal-characters](LexicalStructure.md#hexadecimal-literal-characters)~opt~

[‌](){#TP40016643-CH38-NoLink_1292}

hexadecimal-digit


→
Digit 0 through 9, a through f, or A through F

[‌](){#TP40016643-CH38-NoLink_1293}

hexadecimal-literal-character


→

[hexadecimal-digit](LexicalStructure.md#hexadecimal-digit)

`_`{.literal}


[‌](){#TP40016643-CH38-NoLink_1294}

hexadecimal-literal-characters


→
[hexadecimal-literal-character](LexicalStructure.md#hexadecimal-literal-character)[hexadecimal-literal-characters](LexicalStructure.md#hexadecimal-literal-characters)~opt~







Grammar of a floating-point literal



[‌](){#TP40016643-CH38-NoLink_1296}

floating-point-literal


→
[decimal-literal](LexicalStructure.md#decimal-literal)[decimal-fraction](LexicalStructure.md#decimal-fraction)~opt~[decimal-exponent](LexicalStructure.md#decimal-exponent)~opt~

[‌](){#TP40016643-CH38-NoLink_1297}

floating-point-literal


→
[hexadecimal-literal](LexicalStructure.md#hexadecimal-literal)[hexadecimal-fraction](LexicalStructure.md#hexadecimal-fraction)~opt~[hexadecimal-exponent](LexicalStructure.md#hexadecimal-exponent)





[‌](){#TP40016643-CH38-NoLink_1298}

decimal-fraction


→
`.`{.literal}[decimal-literal](LexicalStructure.md#decimal-literal)

[‌](){#TP40016643-CH38-NoLink_1299}

decimal-exponent


→
[floating-point-e](LexicalStructure.md#floating-point-e)[sign](LexicalStructure.md#sign)~opt~[decimal-literal](LexicalStructure.md#decimal-literal)





[‌](){#TP40016643-CH38-NoLink_1300}

hexadecimal-fraction


→
`.`{.literal}[hexadecimal-digit](LexicalStructure.md#hexadecimal-digit)[hexadecimal-literal-characters](LexicalStructure.md#hexadecimal-literal-characters)~opt~

[‌](){#TP40016643-CH38-NoLink_1301}

hexadecimal-exponent


→
[floating-point-p](LexicalStructure.md#floating-point-p)[sign](LexicalStructure.md#sign)~opt~[decimal-literal](LexicalStructure.md#decimal-literal)





[‌](){#TP40016643-CH38-NoLink_1302}

floating-point-e


→

`e`{.literal}

`E`{.literal}


[‌](){#TP40016643-CH38-NoLink_1303}

floating-point-p


→

`p`{.literal}

`P`{.literal}


[‌](){#TP40016643-CH38-NoLink_1304}

sign


→

`+`{.literal}

`-`{.literal}








Grammar of a string literal



[‌](){#TP40016643-CH38-NoLink_1306}

string-literal


→

[static-string-literal](LexicalStructure.md#static-string-literal)

[interpolated-string-literal](LexicalStructure.md#interpolated-string-literal)






[‌](){#TP40016643-CH38-NoLink_1307}

static-string-literal


→
`"`{.literal}[quoted-text](LexicalStructure.md#quoted-text)~opt~`"`{.literal}

[‌](){#TP40016643-CH38-NoLink_1308}

quoted-text


→
[quoted-text-item](LexicalStructure.md#quoted-text-item)[quoted-text](LexicalStructure.md#quoted-text)~opt~

[‌](){#TP40016643-CH38-NoLink_1309}

quoted-text-item


→
[escaped-character](LexicalStructure.md#escaped-character)

[‌](){#TP40016643-CH38-NoLink_1310}

quoted-text-item


→
Any Unicode scalar value except `"`{.literal}, `\`{.literal}, U+000A, or U+000D





[‌](){#TP40016643-CH38-NoLink_1311}

interpolated-string-literal


→
`"`{.literal}[interpolated-text](LexicalStructure.md#interpolated-text)~opt~`"`{.literal}

[‌](){#TP40016643-CH38-NoLink_1312}

interpolated-text


→
[interpolated-text-item](LexicalStructure.md#interpolated-text-item)[interpolated-text](LexicalStructure.md#interpolated-text)~opt~

[‌](){#TP40016643-CH38-NoLink_1313}

interpolated-text-item


→

`\(`{.literal}[expression](Expressions.md#expression)`)`{.literal}

[quoted-text-item](LexicalStructure.md#quoted-text-item)






[‌](){#TP40016643-CH38-NoLink_1314}

escaped-character


→

`\0`{.literal}

`\\`{.literal}

`\t`{.literal}

`\n`{.literal}

`\r`{.literal}

`\"`{.literal}

`\'`{.literal}


[‌](){#TP40016643-CH38-NoLink_1315}

escaped-character


→
`\u`{.literal}`{`{.literal}[unicode-scalar-digits](LexicalStructure.md#unicode-scalar-digits)`}`{.literal}

[‌](){#TP40016643-CH38-NoLink_1316}

unicode-scalar-digits


→
Between one and eight hexadecimal digits







Grammar of operators



[‌](){#TP40016643-CH38-NoLink_1318}

operator


→
[operator-head](LexicalStructure.md#operator-head)[operator-characters](LexicalStructure.md#operator-characters)~opt~

[‌](){#TP40016643-CH38-NoLink_1319}

operator


→
[dot-operator-head](LexicalStructure.md#dot-operator-head)[dot-operator-characters](LexicalStructure.md#dot-operator-characters)~opt~





[‌](){#TP40016643-CH38-NoLink_1320}

operator-head


→

`/`{.literal}

`=`{.literal}

`-`{.literal}

`+`{.literal}

`!`{.literal}

`*`{.literal}

`%`{.literal}

`<`{.literal}

`>`{.literal}

`&`{.literal}

`|`{.literal}

`^`{.literal}

`~`{.literal}

`?`{.literal}


[‌](){#TP40016643-CH38-NoLink_1321}

operator-head


→
U+00A1–U+00A7

[‌](){#TP40016643-CH38-NoLink_1322}

operator-head


→
U+00A9 or U+00AB

[‌](){#TP40016643-CH38-NoLink_1323}

operator-head


→
U+00AC or U+00AE

[‌](){#TP40016643-CH38-NoLink_1324}

operator-head


→
U+00B0–U+00B1, U+00B6, U+00BB, U+00BF, U+00D7, or U+00F7

[‌](){#TP40016643-CH38-NoLink_1325}

operator-head


→
U+2016–U+2017 or U+2020–U+2027

[‌](){#TP40016643-CH38-NoLink_1326}

operator-head


→
U+2030–U+203E

[‌](){#TP40016643-CH38-NoLink_1327}

operator-head


→
U+2041–U+2053

[‌](){#TP40016643-CH38-NoLink_1328}

operator-head


→
U+2055–U+205E

[‌](){#TP40016643-CH38-NoLink_1329}

operator-head


→
U+2190–U+23FF

[‌](){#TP40016643-CH38-NoLink_1330}

operator-head


→
U+2500–U+2775

[‌](){#TP40016643-CH38-NoLink_1331}

operator-head


→
U+2794–U+2BFF

[‌](){#TP40016643-CH38-NoLink_1332}

operator-head


→
U+2E00–U+2E7F

[‌](){#TP40016643-CH38-NoLink_1333}

operator-head


→
U+3001–U+3003

[‌](){#TP40016643-CH38-NoLink_1334}

operator-head


→
U+3008–U+3030





[‌](){#TP40016643-CH38-NoLink_1335}

operator-character


→
[operator-head](LexicalStructure.md#operator-head)

[‌](){#TP40016643-CH38-NoLink_1336}

operator-character


→
U+0300–U+036F

[‌](){#TP40016643-CH38-NoLink_1337}

operator-character


→
U+1DC0–U+1DFF

[‌](){#TP40016643-CH38-NoLink_1338}

operator-character


→
U+20D0–U+20FF

[‌](){#TP40016643-CH38-NoLink_1339}

operator-character


→
U+FE00–U+FE0F

[‌](){#TP40016643-CH38-NoLink_1340}

operator-character


→
U+FE20–U+FE2F

[‌](){#TP40016643-CH38-NoLink_1341}

operator-character


→
U+E0100–U+E01EF

[‌](){#TP40016643-CH38-NoLink_1342}

operator-characters


→
[operator-character](LexicalStructure.md#operator-character)[operator-characters](LexicalStructure.md#operator-characters)~opt~





[‌](){#TP40016643-CH38-NoLink_1343}

dot-operator-head


→
`..`{.literal}

[‌](){#TP40016643-CH38-NoLink_1344}

dot-operator-character


→

`.`{.literal}

[operator-character](LexicalStructure.md#operator-character)


[‌](){#TP40016643-CH38-NoLink_1345}

dot-operator-characters


→
[dot-operator-character](LexicalStructure.md#dot-operator-character)[dot-operator-characters](LexicalStructure.md#dot-operator-characters)~opt~





[‌](){#TP40016643-CH38-NoLink_1346}

binary-operator


→
[operator](LexicalStructure.md#operator)

[‌](){#TP40016643-CH38-NoLink_1347}

prefix-operator


→
[operator](LexicalStructure.md#operator)

[‌](){#TP40016643-CH38-NoLink_1348}

postfix-operator


→
[operator](LexicalStructure.md#operator)









[‌](){#TP40016643-CH38-ID482}
### Types {#types .section-name}



Grammar of a type



[‌](){#TP40016643-CH38-NoLink_1350}

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



[‌](){#TP40016643-CH38-NoLink_1352}

type-annotation


→
`:`{.literal}[attributes](Attributes.md#attributes)~opt~[type](Types.md#type)







Grammar of a type identifier



[‌](){#TP40016643-CH38-NoLink_1354}

type-identifier


→

[type-name](Types.md#type-name)[generic-argument-clause](GenericParametersAndArguments.md#generic-argument-clause)~opt~

[type-name](Types.md#type-name)[generic-argument-clause](GenericParametersAndArguments.md#generic-argument-clause)~opt~`.`{.literal}[type-identifier](Types.md#type-identifier)


[‌](){#TP40016643-CH38-NoLink_1355}

type-name


→
[identifier](LexicalStructure.md#identifier)







Grammar of a tuple type



[‌](){#TP40016643-CH38-NoLink_1357}

tuple-type


→
`(`{.literal}[tuple-type-body](Types.md#tuple-type-body)~opt~`)`{.literal}

[‌](){#TP40016643-CH38-NoLink_1358}

tuple-type-body


→
[tuple-type-element-list](Types.md#tuple-type-element-list)`...`{.literal}~opt~

[‌](){#TP40016643-CH38-NoLink_1359}

tuple-type-element-list


→

[tuple-type-element](Types.md#tuple-type-element)

[tuple-type-element](Types.md#tuple-type-element)`,`{.literal}[tuple-type-element-list](Types.md#tuple-type-element-list)


[‌](){#TP40016643-CH38-NoLink_1360}

tuple-type-element


→

[attributes](Attributes.md#attributes)~opt~`inout`{.literal}~opt~[type](Types.md#type)

`inout`{.literal}~opt~[element-name](Types.md#element-name)[type-annotation](Types.md#type-annotation)


[‌](){#TP40016643-CH38-NoLink_1361}

element-name


→
[identifier](LexicalStructure.md#identifier)







Grammar of a function type



[‌](){#TP40016643-CH38-NoLink_1363}

function-type


→
[type](Types.md#type)`throws`{.literal}~opt~`->`{.literal}[type](Types.md#type)

[‌](){#TP40016643-CH38-NoLink_1364}

function-type


→
[type](Types.md#type)`rethrows`{.literal}`->`{.literal}[type](Types.md#type)







Grammar of an array type



[‌](){#TP40016643-CH38-NoLink_1366}

array-type


→
`[`{.literal}[type](Types.md#type)`]`{.literal}







Grammar of a dictionary type



[‌](){#TP40016643-CH38-NoLink_1368}

dictionary-type


→
`[`{.literal}[type](Types.md#type)`:`{.literal}[type](Types.md#type)`]`{.literal}







Grammar of an optional type



[‌](){#TP40016643-CH38-NoLink_1370}

optional-type


→
[type](Types.md#type)`?`{.literal}







Grammar of an implicitly unwrapped optional type



[‌](){#TP40016643-CH38-NoLink_1372}

implicitly-unwrapped-optional-type


→
[type](Types.md#type)`!`{.literal}







Grammar of a protocol composition type



[‌](){#TP40016643-CH38-NoLink_1374}

protocol-composition-type


→
`protocol`{.literal}`[protocol-identifier-list](Types.md#protocol-identifier-list)~opt~`>`{.literal}

[‌](){#TP40016643-CH38-NoLink_1375}

protocol-identifier-list


→

[protocol-identifier](Types.md#protocol-identifier)

[protocol-identifier](Types.md#protocol-identifier)`,`{.literal}[protocol-identifier-list](Types.md#protocol-identifier-list)


[‌](){#TP40016643-CH38-NoLink_1376}

protocol-identifier


→
[type-identifier](Types.md#type-identifier)







Grammar of a metatype type



[‌](){#TP40016643-CH38-NoLink_1378}

metatype-type


→

[type](Types.md#type)`.`{.literal}`Type`{.literal}

[type](Types.md#type)`.`{.literal}`Protocol`{.literal}








Grammar of a type inheritance clause



[‌](){#TP40016643-CH38-NoLink_1380}

type-inheritance-clause


→
`:`{.literal}[class-requirement](Types.md#class-requirement)`,`{.literal}[type-inheritance-list](Types.md#type-inheritance-list)

[‌](){#TP40016643-CH38-NoLink_1381}

type-inheritance-clause


→
`:`{.literal}[class-requirement](Types.md#class-requirement)

[‌](){#TP40016643-CH38-NoLink_1382}

type-inheritance-clause


→
`:`{.literal}[type-inheritance-list](Types.md#type-inheritance-list)

[‌](){#TP40016643-CH38-NoLink_1383}

type-inheritance-list


→

[type-identifier](Types.md#type-identifier)

[type-identifier](Types.md#type-identifier)`,`{.literal}[type-inheritance-list](Types.md#type-inheritance-list)


[‌](){#TP40016643-CH38-NoLink_1384}

class-requirement


→
`class`{.literal}










