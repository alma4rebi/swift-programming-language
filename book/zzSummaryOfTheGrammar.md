<div class="content-wrapper">

<div id="chapter_container" class="conceptualwithtasks">

[‌](){#TP40016643-CH38}[‌](){#TP40016643-CH38-ID458}
Summary of the Grammar {#summary-of-the-grammar .chapter-name}
----------------------

<div class="section section">

[‌](){#TP40016643-CH38-ID475}
### Statements {#statements .section-name}

<div class="syntax-defs">

Grammar of a statement

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_812} <span class="syntax-def-name">
statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[expression](Expressions.md#expression)</span><span
class="optional">`;`{.literal}~opt~</span>

[‌](){#TP40016643-CH38-NoLink_813} <span class="syntax-def-name">
statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[declaration](Declarations.md#declaration)</span><span
class="optional">`;`{.literal}~opt~</span>

[‌](){#TP40016643-CH38-NoLink_814} <span class="syntax-def-name">
statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[loop-statement](Statements.md#loop-statement)</span><span
class="optional">`;`{.literal}~opt~</span>

[‌](){#TP40016643-CH38-NoLink_815} <span class="syntax-def-name">
statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[branch-statement](Statements.md#branch-statement)</span><span
class="optional">`;`{.literal}~opt~</span>

[‌](){#TP40016643-CH38-NoLink_816} <span class="syntax-def-name">
statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[labeled-statement](Statements.md#labeled-statement)</span><span
class="optional">`;`{.literal}~opt~</span>

[‌](){#TP40016643-CH38-NoLink_817} <span class="syntax-def-name">
statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[control-transfer-statement](Statements.md#control-transfer-statement)</span><span
class="optional">`;`{.literal}~opt~</span>

[‌](){#TP40016643-CH38-NoLink_818} <span class="syntax-def-name">
statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[defer-statement](Statements.md#defer-statement)</span><span
class="optional">`;`{.literal}~opt~</span>

[‌](){#TP40016643-CH38-NoLink_819} <span class="syntax-def-name">
statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[do-statement](Statements.md#do-statement)</span><span
class="optional">`:`{.literal}~opt~</span>

[‌](){#TP40016643-CH38-NoLink_820} <span class="syntax-def-name">
statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[compiler-control-statement](Statements.md#compiler-control-statement)</span>

[‌](){#TP40016643-CH38-NoLink_821} <span class="syntax-def-name">
statements </span> <span class="arrow"> → </span><span
class="syntactic-cat">[statement](Statements.md#statement)</span><span
class="optional"><span
class="syntactic-cat">[statements](Statements.md#statements)</span>~opt~</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a loop statement

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_823} <span class="syntax-def-name">
loop-statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[for-statement](Statements.md#for-statement)</span>

[‌](){#TP40016643-CH38-NoLink_824} <span class="syntax-def-name">
loop-statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[for-in-statement](Statements.md#for-in-statement)</span>

[‌](){#TP40016643-CH38-NoLink_825} <span class="syntax-def-name">
loop-statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[while-statement](Statements.md#while-statement)</span>

[‌](){#TP40016643-CH38-NoLink_826} <span class="syntax-def-name">
loop-statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[repeat-while-statement](Statements.md#repeat-while-statement)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a for statement

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_828} <span class="syntax-def-name">
for-statement </span> <span class="arrow"> → </span>`for`{.literal}<span
class="optional"><span
class="syntactic-cat">[for-init](Statements.md#for-init)</span>~opt~</span>`;`{.literal}<span
class="optional"><span
class="syntactic-cat">[expression](Expressions.md#expression)</span>~opt~</span>`;`{.literal}<span
class="optional"><span
class="syntactic-cat">[expression-list](Expressions.md#expression-list)</span>~opt~</span><span
class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

[‌](){#TP40016643-CH38-NoLink_829} <span class="syntax-def-name">
for-statement </span> <span class="arrow"> →
</span>`for`{.literal}`(`{.literal}<span class="optional"><span
class="syntactic-cat">[for-init](Statements.md#for-init)</span>~opt~</span>`;`{.literal}<span
class="optional"><span
class="syntactic-cat">[expression](Expressions.md#expression)</span>~opt~</span>`;`{.literal}<span
class="optional"><span
class="syntactic-cat">[expression-list](Expressions.md#expression-list)</span>~opt~</span>`)`{.literal}<span
class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_830} <span class="syntax-def-name">
for-init </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[variable-declaration](Declarations.md#variable-declaration)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[expression-list](Expressions.md#expression-list)</span>
</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a for-in statement

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_832} <span class="syntax-def-name">
for-in-statement </span> <span class="arrow"> →
</span>`for`{.literal}<span
class="optional">`case`{.literal}~opt~</span><span
class="syntactic-cat">[pattern](Patterns.md#pattern)</span>`in`{.literal}<span
class="syntactic-cat">[expression](Expressions.md#expression)</span><span
class="optional"><span
class="syntactic-cat">[where-clause](Statements.md#where-clause)</span>~opt~</span><span
class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a while statement

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_834} <span class="syntax-def-name">
while-statement </span> <span class="arrow"> →
</span>`while`{.literal}<span
class="syntactic-cat">[condition-clause](Statements.md#condition-clause)</span><span
class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_835} <span class="syntax-def-name">
condition-clause </span> <span class="arrow"> → </span><span
class="syntactic-cat">[expression](Expressions.md#expression)</span>

[‌](){#TP40016643-CH38-NoLink_836} <span class="syntax-def-name">
condition-clause </span> <span class="arrow"> → </span><span
class="syntactic-cat">[expression](Expressions.md#expression)</span>`,`{.literal}<span
class="syntactic-cat">[condition-list](Statements.md#condition-list)</span>

[‌](){#TP40016643-CH38-NoLink_837} <span class="syntax-def-name">
condition-clause </span> <span class="arrow"> → </span><span
class="syntactic-cat">[condition-list](Statements.md#condition-list)</span>

[‌](){#TP40016643-CH38-NoLink_838} <span class="syntax-def-name">
condition-clause </span> <span class="arrow"> → </span><span
class="syntactic-cat">[availability-condition](Statements.md#availability-condition)</span>`,`{.literal}<span
class="syntactic-cat">[expression](Expressions.md#expression)</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_839} <span class="syntax-def-name">
condition-list </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[condition](Statements.md#condition)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[condition](Statements.md#condition)</span>`,`{.literal}<span
class="syntactic-cat">[condition-list](Statements.md#condition-list)</span>
</span>

[‌](){#TP40016643-CH38-NoLink_840} <span class="syntax-def-name">
condition </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[availability-condition](Statements.md#availability-condition)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[case-condition](Statements.md#case-condition)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[optional-binding-condition](Statements.md#optional-binding-condition)</span>
</span>

[‌](){#TP40016643-CH38-NoLink_841} <span class="syntax-def-name">
case-condition </span> <span class="arrow"> →
</span>`case`{.literal}<span
class="syntactic-cat">[pattern](Patterns.md#pattern)</span><span
class="syntactic-cat">[initializer](Declarations.md#initializer)</span><span
class="optional"><span
class="syntactic-cat">[where-clause](Statements.md#where-clause)</span>~opt~</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_842} <span class="syntax-def-name">
optional-binding-condition </span> <span class="arrow"> → </span><span
class="syntactic-cat">[optional-binding-head](Statements.md#optional-binding-head)</span><span
class="optional"><span
class="syntactic-cat">[optional-binding-continuation-list](Statements.md#optional-binding-continuation-list)</span>~opt~</span><span
class="optional"><span
class="syntactic-cat">[where-clause](Statements.md#where-clause)</span>~opt~</span>

[‌](){#TP40016643-CH38-NoLink_843} <span class="syntax-def-name">
optional-binding-head </span> <span class="arrow"> →
</span>`let`{.literal}<span
class="syntactic-cat">[pattern](Patterns.md#pattern)</span><span
class="syntactic-cat">[initializer](Declarations.md#initializer)</span>

[‌](){#TP40016643-CH38-NoLink_844} <span class="syntax-def-name">
optional-binding-continuation-list </span> <span class="arrow"> →
</span><span class="alternative"> <span
class="syntactic-cat">[optional-binding-continuation](Statements.md#optional-binding-continuation)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[optional-binding-continuation](Statements.md#optional-binding-continuation)</span>`,`{.literal}<span
class="syntactic-cat">[optional-binding-continuation-list](Statements.md#optional-binding-continuation-list)</span>
</span>

[‌](){#TP40016643-CH38-NoLink_845} <span class="syntax-def-name">
optional-binding-continuation </span> <span class="arrow"> →
</span><span class="alternative"> <span
class="syntactic-cat">[pattern](Patterns.md#pattern)</span><span
class="syntactic-cat">[initializer](Declarations.md#initializer)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[optional-binding-head](Statements.md#optional-binding-head)</span>
</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a repeat-while statement

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_847} <span class="syntax-def-name">
repeat-while-statement </span> <span class="arrow"> →
</span>`repeat`{.literal}<span
class="syntactic-cat">[code-block](Declarations.md#code-block)</span>`while`{.literal}<span
class="syntactic-cat">[expression](Expressions.md#expression)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a branch statement

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_849} <span class="syntax-def-name">
branch-statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[if-statement](Statements.md#if-statement)</span>

[‌](){#TP40016643-CH38-NoLink_850} <span class="syntax-def-name">
branch-statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[guard-statement](Statements.md#guard-statement)</span>

[‌](){#TP40016643-CH38-NoLink_851} <span class="syntax-def-name">
branch-statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[switch-statement](Statements.md#switch-statement)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of an if statement

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_853} <span class="syntax-def-name">
if-statement </span> <span class="arrow"> → </span>`if`{.literal}<span
class="syntactic-cat">[condition-clause](Statements.md#condition-clause)</span><span
class="syntactic-cat">[code-block](Declarations.md#code-block)</span><span
class="optional"><span
class="syntactic-cat">[else-clause](Statements.md#else-clause)</span>~opt~</span>

[‌](){#TP40016643-CH38-NoLink_854} <span class="syntax-def-name">
else-clause </span> <span class="arrow"> → </span><span
class="alternative"> `else`{.literal}<span
class="syntactic-cat">[code-block](Declarations.md#code-block)</span>
</span><span class="alternative"> `else`{.literal}<span
class="syntactic-cat">[if-statement](Statements.md#if-statement)</span>
</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a guard statement

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_856} <span class="syntax-def-name">
guard-statement </span> <span class="arrow"> →
</span>`guard`{.literal}<span
class="syntactic-cat">[condition-clause](Statements.md#condition-clause)</span>`else`{.literal}<span
class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a switch statement

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_858} <span class="syntax-def-name">
switch-statement </span> <span class="arrow"> →
</span>`switch`{.literal}<span
class="syntactic-cat">[expression](Expressions.md#expression)</span>`{`{.literal}<span
class="optional"><span
class="syntactic-cat">[switch-cases](Statements.md#switch-cases)</span>~opt~</span>`}`{.literal}

[‌](){#TP40016643-CH38-NoLink_859} <span class="syntax-def-name">
switch-cases </span> <span class="arrow"> → </span><span
class="syntactic-cat">[switch-case](Statements.md#switch-case)</span><span
class="optional"><span
class="syntactic-cat">[switch-cases](Statements.md#switch-cases)</span>~opt~</span>

[‌](){#TP40016643-CH38-NoLink_860} <span class="syntax-def-name">
switch-case </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[case-label](Statements.md#case-label)</span><span
class="syntactic-cat">[statements](Statements.md#statements)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[default-label](Statements.md#default-label)</span><span
class="syntactic-cat">[statements](Statements.md#statements)</span>
</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_861} <span class="syntax-def-name">
case-label </span> <span class="arrow"> → </span>`case`{.literal}<span
class="syntactic-cat">[case-item-list](Statements.md#case-item-list)</span>`:`{.literal}

[‌](){#TP40016643-CH38-NoLink_862} <span class="syntax-def-name">
case-item-list </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[pattern](Patterns.md#pattern)</span><span
class="optional"><span
class="syntactic-cat">[where-clause](Statements.md#where-clause)</span>~opt~</span>
</span><span class="alternative"> <span
class="syntactic-cat">[pattern](Patterns.md#pattern)</span><span
class="optional"><span
class="syntactic-cat">[where-clause](Statements.md#where-clause)</span>~opt~</span>`,`{.literal}<span
class="syntactic-cat">[case-item-list](Statements.md#case-item-list)</span>
</span>

[‌](){#TP40016643-CH38-NoLink_863} <span class="syntax-def-name">
default-label </span> <span class="arrow"> →
</span>`default`{.literal}`:`{.literal}

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_864} <span class="syntax-def-name">
where-clause </span> <span class="arrow"> →
</span>`where`{.literal}<span
class="syntactic-cat">[where-expression](Statements.md#where-expression)</span>

[‌](){#TP40016643-CH38-NoLink_865} <span class="syntax-def-name">
where-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[expression](Expressions.md#expression)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a labeled statement

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_867} <span class="syntax-def-name">
labeled-statement </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[statement-label](Statements.md#statement-label)</span><span
class="syntactic-cat">[loop-statement](Statements.md#loop-statement)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[statement-label](Statements.md#statement-label)</span><span
class="syntactic-cat">[if-statement](Statements.md#if-statement)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[statement-label](Statements.md#statement-label)</span><span
class="syntactic-cat">[switch-statement](Statements.md#switch-statement)</span>
</span>

[‌](){#TP40016643-CH38-NoLink_868} <span class="syntax-def-name">
statement-label </span> <span class="arrow"> → </span><span
class="syntactic-cat">[label-name](Statements.md#label-name)</span>`:`{.literal}

[‌](){#TP40016643-CH38-NoLink_869} <span class="syntax-def-name">
label-name </span> <span class="arrow"> → </span><span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a control transfer statement

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_871} <span class="syntax-def-name">
control-transfer-statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[break-statement](Statements.md#break-statement)</span>

[‌](){#TP40016643-CH38-NoLink_872} <span class="syntax-def-name">
control-transfer-statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[continue-statement](Statements.md#continue-statement)</span>

[‌](){#TP40016643-CH38-NoLink_873} <span class="syntax-def-name">
control-transfer-statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[fallthrough-statement](Statements.md#fallthrough-statement)</span>

[‌](){#TP40016643-CH38-NoLink_874} <span class="syntax-def-name">
control-transfer-statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[return-statement](Statements.md#return-statement)</span>

[‌](){#TP40016643-CH38-NoLink_875} <span class="syntax-def-name">
control-transfer-statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[throw-statement](Statements.md#throw-statement)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a break statement

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_877} <span class="syntax-def-name">
break-statement </span> <span class="arrow"> →
</span>`break`{.literal}<span class="optional"><span
class="syntactic-cat">[label-name](Statements.md#label-name)</span>~opt~</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a continue statement

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_879} <span class="syntax-def-name">
continue-statement </span> <span class="arrow"> →
</span>`continue`{.literal}<span class="optional"><span
class="syntactic-cat">[label-name](Statements.md#label-name)</span>~opt~</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a fallthrough statement

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_881} <span class="syntax-def-name">
fallthrough-statement </span> <span class="arrow"> →
</span>`fallthrough`{.literal}

</div>

</div>

<div class="syntax-defs">

Grammar of a return statement

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_883} <span class="syntax-def-name">
return-statement </span> <span class="arrow"> →
</span>`return`{.literal}<span class="optional"><span
class="syntactic-cat">[expression](Expressions.md#expression)</span>~opt~</span>

</div>

</div>

<div class="syntax-defs">

Grammar of an availability condition

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_885} <span class="syntax-def-name">
availability-condition </span> <span class="arrow"> →
</span>`#available`{.literal}`(`{.literal}<span
class="syntactic-cat">[availability-arguments](Statements.md#availability-arguments)</span>`)`{.literal}

[‌](){#TP40016643-CH38-NoLink_886} <span class="syntax-def-name">
availability-arguments </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[availability-argument](Statements.md#availability-argument)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[availability-argument](Statements.md#availability-argument)</span>`,`{.literal}<span
class="syntactic-cat">[availability-arguments](Statements.md#availability-arguments)</span>
</span>

[‌](){#TP40016643-CH38-NoLink_887} <span class="syntax-def-name">
availability-argument </span> <span class="arrow"> → </span><span
class="syntactic-cat">[platform-name](Statements.md#platform-name)</span><span
class="syntactic-cat">[platform-version](Statements.md#platform-version)</span>

[‌](){#TP40016643-CH38-NoLink_888} <span class="syntax-def-name">
availability-argument </span> <span class="arrow"> →
</span>`*`{.literal}

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_889} <span class="syntax-def-name">
platform-name </span> <span class="arrow"> → </span><span
class="alternative"> `iOS`{.literal} </span><span class="alternative">
`iOSApplicationExtension`{.literal} </span>

[‌](){#TP40016643-CH38-NoLink_890} <span class="syntax-def-name">
platform-name </span> <span class="arrow"> → </span><span
class="alternative"> `OSX`{.literal} </span><span class="alternative">
`OSXApplicationExtension`{.literal} </span>

[‌](){#TP40016643-CH38-NoLink_891} <span class="syntax-def-name">
platform-name </span> <span class="arrow"> → </span>`watchOS`{.literal}

[‌](){#TP40016643-CH38-NoLink_892} <span class="syntax-def-name">
platform-version </span> <span class="arrow"> → </span><span
class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)</span>

[‌](){#TP40016643-CH38-NoLink_893} <span class="syntax-def-name">
platform-version </span> <span class="arrow"> → </span><span
class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)</span>`.`{.literal}<span
class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)</span>

[‌](){#TP40016643-CH38-NoLink_894} <span class="syntax-def-name">
platform-version </span> <span class="arrow"> → </span><span
class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)</span>`.`{.literal}<span
class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)</span>`.`{.literal}<span
class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a throw statement

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_896} <span class="syntax-def-name">
throw-statement </span> <span class="arrow"> →
</span>`throw`{.literal}<span
class="syntactic-cat">[expression](Expressions.md#expression)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a defer statement

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_898} <span class="syntax-def-name">
defer-statement </span> <span class="arrow"> →
</span>`defer`{.literal}<span
class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a do statement

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_900} <span class="syntax-def-name">
do-statement </span> <span class="arrow"> → </span>`do`{.literal}<span
class="syntactic-cat">[code-block](Declarations.md#code-block)</span><span
class="optional"><span
class="syntactic-cat">[catch-clauses](Statements.md#catch-clauses)</span>~opt~</span>

[‌](){#TP40016643-CH38-NoLink_901} <span class="syntax-def-name">
catch-clauses </span> <span class="arrow"> → </span><span
class="syntactic-cat">[catch-clause](Statements.md#catch-clause)</span><span
class="optional"><span
class="syntactic-cat">[catch-clauses](Statements.md#catch-clauses)</span>~opt~</span>

[‌](){#TP40016643-CH38-NoLink_902} <span class="syntax-def-name">
catch-clause </span> <span class="arrow"> →
</span>`catch`{.literal}<span class="optional"><span
class="syntactic-cat">[pattern](Patterns.md#pattern)</span>~opt~</span><span
class="optional"><span
class="syntactic-cat">[where-clause](Statements.md#where-clause)</span>~opt~</span><span
class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a compiler control statement

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_904} <span class="syntax-def-name">
compiler-control-statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[build-configuration-statement](Statements.md#build-configuration-statement)</span>

[‌](){#TP40016643-CH38-NoLink_905} <span class="syntax-def-name">
compiler-control-statement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[line-control-statement](Statements.md#line-control-statement)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a build configuration statement

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_907} <span class="syntax-def-name">
build-configuration-statement </span> <span class="arrow"> →
</span>`#if`{.literal}<span
class="syntactic-cat">[build-configuration](Statements.md#build-configuration)</span><span
class="optional"><span
class="syntactic-cat">[statements](Statements.md#statements)</span>~opt~</span><span
class="optional"><span
class="syntactic-cat">[build-configuration-elseif-clauses](Statements.md#build-configuration-elseif-clauses)</span>~opt~</span><span
class="optional"><span
class="syntactic-cat">[build-configuration-else-clause](Statements.md#build-configuration-else-clause)</span>~opt~</span>`#endif`{.literal}

[‌](){#TP40016643-CH38-NoLink_908} <span class="syntax-def-name">
build-configuration-elseif-clauses </span> <span class="arrow"> →
</span><span
class="syntactic-cat">[build-configuration-elseif-clause](Statements.md#build-configuration-elseif-clause)</span><span
class="optional"><span
class="syntactic-cat">[build-configuration-elseif-clauses](Statements.md#build-configuration-elseif-clauses)</span>~opt~</span>

[‌](){#TP40016643-CH38-NoLink_909} <span class="syntax-def-name">
build-configuration-elseif-clause </span> <span class="arrow"> →
</span>`#elseif`{.literal}<span
class="syntactic-cat">[build-configuration](Statements.md#build-configuration)</span><span
class="optional"><span
class="syntactic-cat">[statements](Statements.md#statements)</span>~opt~</span>

[‌](){#TP40016643-CH38-NoLink_910} <span class="syntax-def-name">
build-configuration-else-clause </span> <span class="arrow"> →
</span>`#else`{.literal}<span class="optional"><span
class="syntactic-cat">[statements](Statements.md#statements)</span>~opt~</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_911} <span class="syntax-def-name">
build-configuration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[platform-testing-function](Statements.md#platform-testing-function)</span>

[‌](){#TP40016643-CH38-NoLink_912} <span class="syntax-def-name">
build-configuration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

[‌](){#TP40016643-CH38-NoLink_913} <span class="syntax-def-name">
build-configuration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[boolean-literal](LexicalStructure.md#boolean-literal)</span>

[‌](){#TP40016643-CH38-NoLink_914} <span class="syntax-def-name">
build-configuration </span> <span class="arrow"> →
</span>`(`{.literal}<span
class="syntactic-cat">[build-configuration](Statements.md#build-configuration)</span>`)`{.literal}

[‌](){#TP40016643-CH38-NoLink_915} <span class="syntax-def-name">
build-configuration </span> <span class="arrow"> →
</span>`!`{.literal}<span
class="syntactic-cat">[build-configuration](Statements.md#build-configuration)</span>

[‌](){#TP40016643-CH38-NoLink_916} <span class="syntax-def-name">
build-configuration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[build-configuration](Statements.md#build-configuration)</span>`&&`{.literal}<span
class="syntactic-cat">[build-configuration](Statements.md#build-configuration)</span>

[‌](){#TP40016643-CH38-NoLink_917} <span class="syntax-def-name">
build-configuration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[build-configuration](Statements.md#build-configuration)</span>`||`{.literal}<span
class="syntactic-cat">[build-configuration](Statements.md#build-configuration)</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_918} <span class="syntax-def-name">
platform-testing-function </span> <span class="arrow"> →
</span>`os`{.literal}`(`{.literal}<span
class="syntactic-cat">[operating-system](Statements.md#operating-system)</span>`)`{.literal}

[‌](){#TP40016643-CH38-NoLink_919} <span class="syntax-def-name">
platform-testing-function </span> <span class="arrow"> →
</span>`arch`{.literal}`(`{.literal}<span
class="syntactic-cat">[architecture](Statements.md#architecture)</span>`)`{.literal}

[‌](){#TP40016643-CH38-NoLink_920} <span class="syntax-def-name">
operating-system </span> <span class="arrow"> → </span><span
class="alternative"> `OSX`{.literal} </span><span class="alternative">
`iOS`{.literal} </span><span class="alternative"> `watchOS`{.literal}
</span><span class="alternative"> `tvOS`{.literal} </span>

[‌](){#TP40016643-CH38-NoLink_921} <span class="syntax-def-name">
architecture </span> <span class="arrow"> → </span><span
class="alternative"> `i386`{.literal} </span><span class="alternative">
`x86_64`{.literal} </span><span class="alternative"> `arm`{.literal}
</span><span class="alternative"> `arm64`{.literal} </span>

</div>

</div>

<div class="syntax-defs">

Grammar of a line control statement

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_923} <span class="syntax-def-name">
line-control-statement </span> <span class="arrow"> →
</span>`#line`{.literal}

[‌](){#TP40016643-CH38-NoLink_924} <span class="syntax-def-name">
line-control-statement </span> <span class="arrow"> →
</span>`#line`{.literal}<span
class="syntactic-cat">[line-number](Statements.md#line-number)</span><span
class="syntactic-cat">[file-name](Statements.md#file-name)</span>

[‌](){#TP40016643-CH38-NoLink_925} <span class="syntax-def-name">
line-number </span> <span class="arrow"> → </span><span
class="text-description">A decimal integer greater than zero</span>

[‌](){#TP40016643-CH38-NoLink_926} <span class="syntax-def-name">
file-name </span> <span class="arrow"> → </span><span
class="syntactic-cat">[static-string-literal](LexicalStructure.md#static-string-literal)</span>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH38-ID476}
### Generic Parameters and Arguments {#generic-parameters-and-arguments .section-name}

<div class="syntax-defs">

Grammar of a generic parameter clause

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_928} <span class="syntax-def-name">
generic-parameter-clause </span> <span class="arrow"> →
</span>`<`{.literal}<span
class="syntactic-cat">[generic-parameter-list](GenericParametersAndArguments.md#generic-parameter-list)</span><span
class="optional"><span
class="syntactic-cat">[requirement-clause](GenericParametersAndArguments.md#requirement-clause)</span>~opt~</span>`>`{.literal}

[‌](){#TP40016643-CH38-NoLink_929} <span class="syntax-def-name">
generic-parameter-list </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[generic-parameter](GenericParametersAndArguments.md#generic-parameter)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[generic-parameter](GenericParametersAndArguments.md#generic-parameter)</span>`,`{.literal}<span
class="syntactic-cat">[generic-parameter-list](GenericParametersAndArguments.md#generic-parameter-list)</span>
</span>

[‌](){#TP40016643-CH38-NoLink_930} <span class="syntax-def-name">
generic-parameter </span> <span class="arrow"> → </span><span
class="syntactic-cat">[type-name](Types.md#type-name)</span>

[‌](){#TP40016643-CH38-NoLink_931} <span class="syntax-def-name">
generic-parameter </span> <span class="arrow"> → </span><span
class="syntactic-cat">[type-name](Types.md#type-name)</span>`:`{.literal}<span
class="syntactic-cat">[type-identifier](Types.md#type-identifier)</span>

[‌](){#TP40016643-CH38-NoLink_932} <span class="syntax-def-name">
generic-parameter </span> <span class="arrow"> → </span><span
class="syntactic-cat">[type-name](Types.md#type-name)</span>`:`{.literal}<span
class="syntactic-cat">[protocol-composition-type](Types.md#protocol-composition-type)</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_933} <span class="syntax-def-name">
requirement-clause </span> <span class="arrow"> →
</span>`where`{.literal}<span
class="syntactic-cat">[requirement-list](GenericParametersAndArguments.md#requirement-list)</span>

[‌](){#TP40016643-CH38-NoLink_934} <span class="syntax-def-name">
requirement-list </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[requirement](GenericParametersAndArguments.md#requirement)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[requirement](GenericParametersAndArguments.md#requirement)</span>`,`{.literal}<span
class="syntactic-cat">[requirement-list](GenericParametersAndArguments.md#requirement-list)</span>
</span>

[‌](){#TP40016643-CH38-NoLink_935} <span class="syntax-def-name">
requirement </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[conformance-requirement](GenericParametersAndArguments.md#conformance-requirement)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[same-type-requirement](GenericParametersAndArguments.md#same-type-requirement)</span>
</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_936} <span class="syntax-def-name">
conformance-requirement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[type-identifier](Types.md#type-identifier)</span>`:`{.literal}<span
class="syntactic-cat">[type-identifier](Types.md#type-identifier)</span>

[‌](){#TP40016643-CH38-NoLink_937} <span class="syntax-def-name">
conformance-requirement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[type-identifier](Types.md#type-identifier)</span>`:`{.literal}<span
class="syntactic-cat">[protocol-composition-type](Types.md#protocol-composition-type)</span>

[‌](){#TP40016643-CH38-NoLink_938} <span class="syntax-def-name">
same-type-requirement </span> <span class="arrow"> → </span><span
class="syntactic-cat">[type-identifier](Types.md#type-identifier)</span>`==`{.literal}<span
class="syntactic-cat">[type](Types.md#type)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a generic argument clause

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_940} <span class="syntax-def-name">
generic-argument-clause </span> <span class="arrow"> →
</span>`<`{.literal}<span
class="syntactic-cat">[generic-argument-list](GenericParametersAndArguments.md#generic-argument-list)</span>`>`{.literal}

[‌](){#TP40016643-CH38-NoLink_941} <span class="syntax-def-name">
generic-argument-list </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[generic-argument](GenericParametersAndArguments.md#generic-argument)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[generic-argument](GenericParametersAndArguments.md#generic-argument)</span>`,`{.literal}<span
class="syntactic-cat">[generic-argument-list](GenericParametersAndArguments.md#generic-argument-list)</span>
</span>

[‌](){#TP40016643-CH38-NoLink_942} <span class="syntax-def-name">
generic-argument </span> <span class="arrow"> → </span><span
class="syntactic-cat">[type](Types.md#type)</span>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH38-ID477}
### Declarations {#declarations .section-name}

<div class="syntax-defs">

Grammar of a declaration

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_944} <span class="syntax-def-name">
declaration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[import-declaration](Declarations.md#import-declaration)</span>

[‌](){#TP40016643-CH38-NoLink_945} <span class="syntax-def-name">
declaration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[constant-declaration](Declarations.md#constant-declaration)</span>

[‌](){#TP40016643-CH38-NoLink_946} <span class="syntax-def-name">
declaration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[variable-declaration](Declarations.md#variable-declaration)</span>

[‌](){#TP40016643-CH38-NoLink_947} <span class="syntax-def-name">
declaration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[typealias-declaration](Declarations.md#typealias-declaration)</span>

[‌](){#TP40016643-CH38-NoLink_948} <span class="syntax-def-name">
declaration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[function-declaration](Declarations.md#function-declaration)</span>

[‌](){#TP40016643-CH38-NoLink_949} <span class="syntax-def-name">
declaration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[enum-declaration](Declarations.md#enum-declaration)</span>

[‌](){#TP40016643-CH38-NoLink_950} <span class="syntax-def-name">
declaration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[struct-declaration](Declarations.md#struct-declaration)</span>

[‌](){#TP40016643-CH38-NoLink_951} <span class="syntax-def-name">
declaration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[class-declaration](Declarations.md#class-declaration)</span>

[‌](){#TP40016643-CH38-NoLink_952} <span class="syntax-def-name">
declaration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[protocol-declaration](Declarations.md#protocol-declaration)</span>

[‌](){#TP40016643-CH38-NoLink_953} <span class="syntax-def-name">
declaration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[initializer-declaration](Declarations.md#initializer-declaration)</span>

[‌](){#TP40016643-CH38-NoLink_954} <span class="syntax-def-name">
declaration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[deinitializer-declaration](Declarations.md#deinitializer-declaration)</span>

[‌](){#TP40016643-CH38-NoLink_955} <span class="syntax-def-name">
declaration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[extension-declaration](Declarations.md#extension-declaration)</span>

[‌](){#TP40016643-CH38-NoLink_956} <span class="syntax-def-name">
declaration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[subscript-declaration](Declarations.md#subscript-declaration)</span>

[‌](){#TP40016643-CH38-NoLink_957} <span class="syntax-def-name">
declaration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[operator-declaration](Declarations.md#operator-declaration)</span>

[‌](){#TP40016643-CH38-NoLink_958} <span class="syntax-def-name">
declarations </span> <span class="arrow"> → </span><span
class="syntactic-cat">[declaration](Declarations.md#declaration)</span><span
class="optional"><span
class="syntactic-cat">[declarations](Declarations.md#declarations)</span>~opt~</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a top-level declaration

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_960} <span class="syntax-def-name">
top-level-declaration </span> <span class="arrow"> → </span><span
class="optional"><span
class="syntactic-cat">[statements](Statements.md#statements)</span>~opt~</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a code block

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_962} <span class="syntax-def-name">
code-block </span> <span class="arrow"> → </span>`{`{.literal}<span
class="optional"><span
class="syntactic-cat">[statements](Statements.md#statements)</span>~opt~</span>`}`{.literal}

</div>

</div>

<div class="syntax-defs">

Grammar of an import declaration

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_964} <span class="syntax-def-name">
import-declaration </span> <span class="arrow"> → </span><span
class="optional"><span
class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span>`import`{.literal}<span
class="optional"><span
class="syntactic-cat">[import-kind](Declarations.md#import-kind)</span>~opt~</span><span
class="syntactic-cat">[import-path](Declarations.md#import-path)</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_965} <span class="syntax-def-name">
import-kind </span> <span class="arrow"> → </span><span
class="alternative"> `typealias`{.literal} </span><span
class="alternative"> `struct`{.literal} </span><span
class="alternative"> `class`{.literal} </span><span class="alternative">
`enum`{.literal} </span><span class="alternative"> `protocol`{.literal}
</span><span class="alternative"> `var`{.literal} </span><span
class="alternative"> `func`{.literal} </span>

[‌](){#TP40016643-CH38-NoLink_966} <span class="syntax-def-name">
import-path </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[import-path-identifier](Declarations.md#import-path-identifier)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[import-path-identifier](Declarations.md#import-path-identifier)</span>`.`{.literal}<span
class="syntactic-cat">[import-path](Declarations.md#import-path)</span>
</span>

[‌](){#TP40016643-CH38-NoLink_967} <span class="syntax-def-name">
import-path-identifier </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[operator](LexicalStructure.md#operator)</span>
</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a constant declaration

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_969} <span class="syntax-def-name">
constant-declaration </span> <span class="arrow"> → </span><span
class="optional"><span
class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span
class="optional"><span
class="syntactic-cat">[declaration-modifiers](Declarations.md#declaration-modifiers)</span>~opt~</span>`let`{.literal}<span
class="syntactic-cat">[pattern-initializer-list](Declarations.md#pattern-initializer-list)</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_970} <span class="syntax-def-name">
pattern-initializer-list </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[pattern-initializer](Declarations.md#pattern-initializer)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[pattern-initializer](Declarations.md#pattern-initializer)</span>`,`{.literal}<span
class="syntactic-cat">[pattern-initializer-list](Declarations.md#pattern-initializer-list)</span>
</span>

[‌](){#TP40016643-CH38-NoLink_971} <span class="syntax-def-name">
pattern-initializer </span> <span class="arrow"> → </span><span
class="syntactic-cat">[pattern](Patterns.md#pattern)</span><span
class="optional"><span
class="syntactic-cat">[initializer](Declarations.md#initializer)</span>~opt~</span>

[‌](){#TP40016643-CH38-NoLink_972} <span class="syntax-def-name">
initializer </span> <span class="arrow"> → </span>`=`{.literal}<span
class="syntactic-cat">[expression](Expressions.md#expression)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a variable declaration

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_974} <span class="syntax-def-name">
variable-declaration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[variable-declaration-head](Declarations.md#variable-declaration-head)</span><span
class="syntactic-cat">[pattern-initializer-list](Declarations.md#pattern-initializer-list)</span>

[‌](){#TP40016643-CH38-NoLink_975} <span class="syntax-def-name">
variable-declaration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[variable-declaration-head](Declarations.md#variable-declaration-head)</span><span
class="syntactic-cat">[variable-name](Declarations.md#variable-name)</span><span
class="syntactic-cat">[type-annotation](Types.md#type-annotation)</span><span
class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

[‌](){#TP40016643-CH38-NoLink_976} <span class="syntax-def-name">
variable-declaration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[variable-declaration-head](Declarations.md#variable-declaration-head)</span><span
class="syntactic-cat">[variable-name](Declarations.md#variable-name)</span><span
class="syntactic-cat">[type-annotation](Types.md#type-annotation)</span><span
class="syntactic-cat">[getter-setter-block](Declarations.md#getter-setter-block)</span>

[‌](){#TP40016643-CH38-NoLink_977} <span class="syntax-def-name">
variable-declaration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[variable-declaration-head](Declarations.md#variable-declaration-head)</span><span
class="syntactic-cat">[variable-name](Declarations.md#variable-name)</span><span
class="syntactic-cat">[type-annotation](Types.md#type-annotation)</span><span
class="syntactic-cat">[getter-setter-keyword-block](Declarations.md#getter-setter-keyword-block)</span>

[‌](){#TP40016643-CH38-NoLink_978} <span class="syntax-def-name">
variable-declaration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[variable-declaration-head](Declarations.md#variable-declaration-head)</span><span
class="syntactic-cat">[variable-name](Declarations.md#variable-name)</span><span
class="syntactic-cat">[initializer](Declarations.md#initializer)</span><span
class="syntactic-cat">[willSet-didSet-block](Declarations.md#willSet-didSet-block)</span>

[‌](){#TP40016643-CH38-NoLink_979} <span class="syntax-def-name">
variable-declaration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[variable-declaration-head](Declarations.md#variable-declaration-head)</span><span
class="syntactic-cat">[variable-name](Declarations.md#variable-name)</span><span
class="syntactic-cat">[type-annotation](Types.md#type-annotation)</span><span
class="optional"><span
class="syntactic-cat">[initializer](Declarations.md#initializer)</span>~opt~</span><span
class="syntactic-cat">[willSet-didSet-block](Declarations.md#willSet-didSet-block)</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_980} <span class="syntax-def-name">
variable-declaration-head </span> <span class="arrow"> → </span><span
class="optional"><span
class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span
class="optional"><span
class="syntactic-cat">[declaration-modifiers](Declarations.md#declaration-modifiers)</span>~opt~</span>`var`{.literal}

[‌](){#TP40016643-CH38-NoLink_981} <span class="syntax-def-name">
variable-name </span> <span class="arrow"> → </span><span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_982} <span class="syntax-def-name">
getter-setter-block </span> <span class="arrow"> → </span><span
class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

[‌](){#TP40016643-CH38-NoLink_983} <span class="syntax-def-name">
getter-setter-block </span> <span class="arrow"> →
</span>`{`{.literal}<span
class="syntactic-cat">[getter-clause](Declarations.md#getter-clause)</span><span
class="optional"><span
class="syntactic-cat">[setter-clause](Declarations.md#setter-clause)</span>~opt~</span>`}`{.literal}

[‌](){#TP40016643-CH38-NoLink_984} <span class="syntax-def-name">
getter-setter-block </span> <span class="arrow"> →
</span>`{`{.literal}<span
class="syntactic-cat">[setter-clause](Declarations.md#setter-clause)</span><span
class="syntactic-cat">[getter-clause](Declarations.md#getter-clause)</span>`}`{.literal}

[‌](){#TP40016643-CH38-NoLink_985} <span class="syntax-def-name">
getter-clause </span> <span class="arrow"> → </span><span
class="optional"><span
class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span>`get`{.literal}<span
class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

[‌](){#TP40016643-CH38-NoLink_986} <span class="syntax-def-name">
setter-clause </span> <span class="arrow"> → </span><span
class="optional"><span
class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span>`set`{.literal}<span
class="optional"><span
class="syntactic-cat">[setter-name](Declarations.md#setter-name)</span>~opt~</span><span
class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

[‌](){#TP40016643-CH38-NoLink_987} <span class="syntax-def-name">
setter-name </span> <span class="arrow"> → </span>`(`{.literal}<span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>`)`{.literal}

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_988} <span class="syntax-def-name">
getter-setter-keyword-block </span> <span class="arrow"> →
</span>`{`{.literal}<span
class="syntactic-cat">[getter-keyword-clause](Declarations.md#getter-keyword-clause)</span><span
class="optional"><span
class="syntactic-cat">[setter-keyword-clause](Declarations.md#setter-keyword-clause)</span>~opt~</span>`}`{.literal}

[‌](){#TP40016643-CH38-NoLink_989} <span class="syntax-def-name">
getter-setter-keyword-block </span> <span class="arrow"> →
</span>`{`{.literal}<span
class="syntactic-cat">[setter-keyword-clause](Declarations.md#setter-keyword-clause)</span><span
class="syntactic-cat">[getter-keyword-clause](Declarations.md#getter-keyword-clause)</span>`}`{.literal}

[‌](){#TP40016643-CH38-NoLink_990} <span class="syntax-def-name">
getter-keyword-clause </span> <span class="arrow"> → </span><span
class="optional"><span
class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span>`get`{.literal}

[‌](){#TP40016643-CH38-NoLink_991} <span class="syntax-def-name">
setter-keyword-clause </span> <span class="arrow"> → </span><span
class="optional"><span
class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span>`set`{.literal}

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_992} <span class="syntax-def-name">
willSet-didSet-block </span> <span class="arrow"> →
</span>`{`{.literal}<span
class="syntactic-cat">[willSet-clause](Declarations.md#willSet-clause)</span><span
class="optional"><span
class="syntactic-cat">[didSet-clause](Declarations.md#didSet-clause)</span>~opt~</span>`}`{.literal}

[‌](){#TP40016643-CH38-NoLink_993} <span class="syntax-def-name">
willSet-didSet-block </span> <span class="arrow"> →
</span>`{`{.literal}<span
class="syntactic-cat">[didSet-clause](Declarations.md#didSet-clause)</span><span
class="optional"><span
class="syntactic-cat">[willSet-clause](Declarations.md#willSet-clause)</span>~opt~</span>`}`{.literal}

[‌](){#TP40016643-CH38-NoLink_994} <span class="syntax-def-name">
willSet-clause </span> <span class="arrow"> → </span><span
class="optional"><span
class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span>`willSet`{.literal}<span
class="optional"><span
class="syntactic-cat">[setter-name](Declarations.md#setter-name)</span>~opt~</span><span
class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

[‌](){#TP40016643-CH38-NoLink_995} <span class="syntax-def-name">
didSet-clause </span> <span class="arrow"> → </span><span
class="optional"><span
class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span>`didSet`{.literal}<span
class="optional"><span
class="syntactic-cat">[setter-name](Declarations.md#setter-name)</span>~opt~</span><span
class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a type alias declaration

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_997} <span class="syntax-def-name">
typealias-declaration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[typealias-head](Declarations.md#typealias-head)</span><span
class="syntactic-cat">[typealias-assignment](Declarations.md#typealias-assignment)</span>

[‌](){#TP40016643-CH38-NoLink_998} <span class="syntax-def-name">
typealias-head </span> <span class="arrow"> → </span><span
class="optional"><span
class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span
class="optional"><span
class="syntactic-cat">[access-level-modifier](Declarations.md#access-level-modifier)</span>~opt~</span>`typealias`{.literal}<span
class="syntactic-cat">[typealias-name](Declarations.md#typealias-name)</span>

[‌](){#TP40016643-CH38-NoLink_999} <span class="syntax-def-name">
typealias-name </span> <span class="arrow"> → </span><span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

[‌](){#TP40016643-CH38-NoLink_1000} <span class="syntax-def-name">
typealias-assignment </span> <span class="arrow"> →
</span>`=`{.literal}<span
class="syntactic-cat">[type](Types.md#type)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a function declaration

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1002} <span class="syntax-def-name">
function-declaration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[function-head](Declarations.md#function-head)</span><span
class="syntactic-cat">[function-name](Declarations.md#function-name)</span><span
class="optional"><span
class="syntactic-cat">[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)</span>~opt~</span><span
class="syntactic-cat">[function-signature](Declarations.md#function-signature)</span><span
class="optional"><span
class="syntactic-cat">[function-body](Declarations.md#function-body)</span>~opt~</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1003} <span class="syntax-def-name">
function-head </span> <span class="arrow"> → </span><span
class="optional"><span
class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span
class="optional"><span
class="syntactic-cat">[declaration-modifiers](Declarations.md#declaration-modifiers)</span>~opt~</span>`func`{.literal}

[‌](){#TP40016643-CH38-NoLink_1004} <span class="syntax-def-name">
function-name </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[operator](LexicalStructure.md#operator)</span>
</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1005} <span class="syntax-def-name">
function-signature </span> <span class="arrow"> → </span><span
class="syntactic-cat">[parameter-clause](Declarations.md#parameter-clause)</span><span
class="optional">`throws`{.literal}~opt~</span><span
class="optional"><span
class="syntactic-cat">[function-result](Declarations.md#function-result)</span>~opt~</span>

[‌](){#TP40016643-CH38-NoLink_1006} <span class="syntax-def-name">
function-signature </span> <span class="arrow"> → </span><span
class="syntactic-cat">[parameter-clause](Declarations.md#parameter-clause)</span>`rethrows`{.literal}<span
class="optional"><span
class="syntactic-cat">[function-result](Declarations.md#function-result)</span>~opt~</span>

[‌](){#TP40016643-CH38-NoLink_1007} <span class="syntax-def-name">
function-result </span> <span class="arrow"> →
</span>`->`{.literal}<span class="optional"><span
class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span
class="syntactic-cat">[type](Types.md#type)</span>

[‌](){#TP40016643-CH38-NoLink_1008} <span class="syntax-def-name">
function-body </span> <span class="arrow"> → </span><span
class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1009} <span class="syntax-def-name">
parameter-clause </span> <span class="arrow"> → </span><span
class="alternative"> `(`{.literal}`)`{.literal} </span><span
class="alternative"> `(`{.literal}<span
class="syntactic-cat">[parameter-list](Declarations.md#parameter-list)</span>`)`{.literal}
</span>

[‌](){#TP40016643-CH38-NoLink_1010} <span class="syntax-def-name">
parameter-list </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[parameter](Declarations.md#parameter)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[parameter](Declarations.md#parameter)</span>`,`{.literal}<span
class="syntactic-cat">[parameter-list](Declarations.md#parameter-list)</span>
</span>

[‌](){#TP40016643-CH38-NoLink_1011} <span class="syntax-def-name">
parameter </span> <span class="arrow"> → </span><span
class="optional">`let`{.literal}~opt~</span><span class="optional"><span
class="syntactic-cat">[external-parameter-name](Declarations.md#external-parameter-name)</span>~opt~</span><span
class="syntactic-cat">[local-parameter-name](Declarations.md#local-parameter-name)</span><span
class="syntactic-cat">[type-annotation](Types.md#type-annotation)</span><span
class="optional"><span
class="syntactic-cat">[default-argument-clause](Declarations.md#default-argument-clause)</span>~opt~</span>

[‌](){#TP40016643-CH38-NoLink_1012} <span class="syntax-def-name">
parameter </span> <span class="arrow"> → </span>`inout`{.literal}<span
class="optional"><span
class="syntactic-cat">[external-parameter-name](Declarations.md#external-parameter-name)</span>~opt~</span><span
class="syntactic-cat">[local-parameter-name](Declarations.md#local-parameter-name)</span><span
class="syntactic-cat">[type-annotation](Types.md#type-annotation)</span>

[‌](){#TP40016643-CH38-NoLink_1013} <span class="syntax-def-name">
parameter </span> <span class="arrow"> → </span><span
class="optional"><span
class="syntactic-cat">[external-parameter-name](Declarations.md#external-parameter-name)</span>~opt~</span><span
class="syntactic-cat">[local-parameter-name](Declarations.md#local-parameter-name)</span><span
class="syntactic-cat">[type-annotation](Types.md#type-annotation)</span>`...`{.literal}

[‌](){#TP40016643-CH38-NoLink_1014} <span class="syntax-def-name">
external-parameter-name </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>
</span><span class="alternative"> `_`{.literal} </span>

[‌](){#TP40016643-CH38-NoLink_1015} <span class="syntax-def-name">
local-parameter-name </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>
</span><span class="alternative"> `_`{.literal} </span>

[‌](){#TP40016643-CH38-NoLink_1016} <span class="syntax-def-name">
default-argument-clause </span> <span class="arrow"> →
</span>`=`{.literal}<span
class="syntactic-cat">[expression](Expressions.md#expression)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of an enumeration declaration

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1018} <span class="syntax-def-name">
enum-declaration </span> <span class="arrow"> → </span><span
class="optional"><span
class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span
class="optional"><span
class="syntactic-cat">[access-level-modifier](Declarations.md#access-level-modifier)</span>~opt~</span><span
class="syntactic-cat">[union-style-enum](Declarations.md#union-style-enum)</span>

[‌](){#TP40016643-CH38-NoLink_1019} <span class="syntax-def-name">
enum-declaration </span> <span class="arrow"> → </span><span
class="optional"><span
class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span
class="optional"><span
class="syntactic-cat">[access-level-modifier](Declarations.md#access-level-modifier)</span>~opt~</span><span
class="syntactic-cat">[raw-value-style-enum](Declarations.md#raw-value-style-enum)</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1020} <span class="syntax-def-name">
union-style-enum </span> <span class="arrow"> → </span><span
class="optional">`indirect`{.literal}~opt~</span>`enum`{.literal}<span
class="syntactic-cat">[enum-name](Declarations.md#enum-name)</span><span
class="optional"><span
class="syntactic-cat">[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)</span>~opt~</span><span
class="optional"><span
class="syntactic-cat">[type-inheritance-clause](Types.md#type-inheritance-clause)</span>~opt~</span>`{`{.literal}<span
class="optional"><span
class="syntactic-cat">[union-style-enum-members](Declarations.md#union-style-enum-members)</span>~opt~</span>`}`{.literal}

[‌](){#TP40016643-CH38-NoLink_1021} <span class="syntax-def-name">
union-style-enum-members </span> <span class="arrow"> → </span><span
class="syntactic-cat">[union-style-enum-member](Declarations.md#union-style-enum-member)</span><span
class="optional"><span
class="syntactic-cat">[union-style-enum-members](Declarations.md#union-style-enum-members)</span>~opt~</span>

[‌](){#TP40016643-CH38-NoLink_1022} <span class="syntax-def-name">
union-style-enum-member </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[declaration](Declarations.md#declaration)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[union-style-enum-case-clause](Declarations.md#union-style-enum-case-clause)</span>
</span>

[‌](){#TP40016643-CH38-NoLink_1023} <span class="syntax-def-name">
union-style-enum-case-clause </span> <span class="arrow"> → </span><span
class="optional"><span
class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span
class="optional">`indirect`{.literal}~opt~</span>`case`{.literal}<span
class="syntactic-cat">[union-style-enum-case-list](Declarations.md#union-style-enum-case-list)</span>

[‌](){#TP40016643-CH38-NoLink_1024} <span class="syntax-def-name">
union-style-enum-case-list </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[union-style-enum-case](Declarations.md#union-style-enum-case)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[union-style-enum-case](Declarations.md#union-style-enum-case)</span>`,`{.literal}<span
class="syntactic-cat">[union-style-enum-case-list](Declarations.md#union-style-enum-case-list)</span>
</span>

[‌](){#TP40016643-CH38-NoLink_1025} <span class="syntax-def-name">
union-style-enum-case </span> <span class="arrow"> → </span><span
class="syntactic-cat">[enum-case-name](Declarations.md#enum-case-name)</span><span
class="optional"><span
class="syntactic-cat">[tuple-type](Types.md#tuple-type)</span>~opt~</span>

[‌](){#TP40016643-CH38-NoLink_1026} <span class="syntax-def-name">
enum-name </span> <span class="arrow"> → </span><span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

[‌](){#TP40016643-CH38-NoLink_1027} <span class="syntax-def-name">
enum-case-name </span> <span class="arrow"> → </span><span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1028} <span class="syntax-def-name">
raw-value-style-enum </span> <span class="arrow"> →
</span>`enum`{.literal}<span
class="syntactic-cat">[enum-name](Declarations.md#enum-name)</span><span
class="optional"><span
class="syntactic-cat">[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)</span>~opt~</span><span
class="syntactic-cat">[type-inheritance-clause](Types.md#type-inheritance-clause)</span>`{`{.literal}<span
class="syntactic-cat">[raw-value-style-enum-members](Declarations.md#raw-value-style-enum-members)</span>`}`{.literal}

[‌](){#TP40016643-CH38-NoLink_1029} <span class="syntax-def-name">
raw-value-style-enum-members </span> <span class="arrow"> → </span><span
class="syntactic-cat">[raw-value-style-enum-member](Declarations.md#raw-value-style-enum-member)</span><span
class="optional"><span
class="syntactic-cat">[raw-value-style-enum-members](Declarations.md#raw-value-style-enum-members)</span>~opt~</span>

[‌](){#TP40016643-CH38-NoLink_1030} <span class="syntax-def-name">
raw-value-style-enum-member </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[declaration](Declarations.md#declaration)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[raw-value-style-enum-case-clause](Declarations.md#raw-value-style-enum-case-clause)</span>
</span>

[‌](){#TP40016643-CH38-NoLink_1031} <span class="syntax-def-name">
raw-value-style-enum-case-clause </span> <span class="arrow"> →
</span><span class="optional"><span
class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span>`case`{.literal}<span
class="syntactic-cat">[raw-value-style-enum-case-list](Declarations.md#raw-value-style-enum-case-list)</span>

[‌](){#TP40016643-CH38-NoLink_1032} <span class="syntax-def-name">
raw-value-style-enum-case-list </span> <span class="arrow"> →
</span><span class="alternative"> <span
class="syntactic-cat">[raw-value-style-enum-case](Declarations.md#raw-value-style-enum-case)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[raw-value-style-enum-case](Declarations.md#raw-value-style-enum-case)</span>`,`{.literal}<span
class="syntactic-cat">[raw-value-style-enum-case-list](Declarations.md#raw-value-style-enum-case-list)</span>
</span>

[‌](){#TP40016643-CH38-NoLink_1033} <span class="syntax-def-name">
raw-value-style-enum-case </span> <span class="arrow"> → </span><span
class="syntactic-cat">[enum-case-name](Declarations.md#enum-case-name)</span><span
class="optional"><span
class="syntactic-cat">[raw-value-assignment](Declarations.md#raw-value-assignment)</span>~opt~</span>

[‌](){#TP40016643-CH38-NoLink_1034} <span class="syntax-def-name">
raw-value-assignment </span> <span class="arrow"> →
</span>`=`{.literal}<span
class="syntactic-cat">[raw-value-literal](Declarations.md#raw-value-literal)</span>

[‌](){#TP40016643-CH38-NoLink_1035} <span class="syntax-def-name">
raw-value-literal </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[numeric-literal](LexicalStructure.md#numeric-literal)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[static-string-literal](LexicalStructure.md#static-string-literal)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[boolean-literal](LexicalStructure.md#boolean-literal)</span>
</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a structure declaration

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1037} <span class="syntax-def-name">
struct-declaration </span> <span class="arrow"> → </span><span
class="optional"><span
class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span
class="optional"><span
class="syntactic-cat">[access-level-modifier](Declarations.md#access-level-modifier)</span>~opt~</span>`struct`{.literal}<span
class="syntactic-cat">[struct-name](Declarations.md#struct-name)</span><span
class="optional"><span
class="syntactic-cat">[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)</span>~opt~</span><span
class="optional"><span
class="syntactic-cat">[type-inheritance-clause](Types.md#type-inheritance-clause)</span>~opt~</span><span
class="syntactic-cat">[struct-body](Declarations.md#struct-body)</span>

[‌](){#TP40016643-CH38-NoLink_1038} <span class="syntax-def-name">
struct-name </span> <span class="arrow"> → </span><span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

[‌](){#TP40016643-CH38-NoLink_1039} <span class="syntax-def-name">
struct-body </span> <span class="arrow"> → </span>`{`{.literal}<span
class="optional"><span
class="syntactic-cat">[declarations](Declarations.md#declarations)</span>~opt~</span>`}`{.literal}

</div>

</div>

<div class="syntax-defs">

Grammar of a class declaration

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1041} <span class="syntax-def-name">
class-declaration </span> <span class="arrow"> → </span><span
class="optional"><span
class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span
class="optional"><span
class="syntactic-cat">[access-level-modifier](Declarations.md#access-level-modifier)</span>~opt~</span>`class`{.literal}<span
class="syntactic-cat">[class-name](Declarations.md#class-name)</span><span
class="optional"><span
class="syntactic-cat">[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)</span>~opt~</span><span
class="optional"><span
class="syntactic-cat">[type-inheritance-clause](Types.md#type-inheritance-clause)</span>~opt~</span><span
class="syntactic-cat">[class-body](Declarations.md#class-body)</span>

[‌](){#TP40016643-CH38-NoLink_1042} <span class="syntax-def-name">
class-name </span> <span class="arrow"> → </span><span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

[‌](){#TP40016643-CH38-NoLink_1043} <span class="syntax-def-name">
class-body </span> <span class="arrow"> → </span>`{`{.literal}<span
class="optional"><span
class="syntactic-cat">[declarations](Declarations.md#declarations)</span>~opt~</span>`}`{.literal}

</div>

</div>

<div class="syntax-defs">

Grammar of a protocol declaration

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1045} <span class="syntax-def-name">
protocol-declaration </span> <span class="arrow"> → </span><span
class="optional"><span
class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span
class="optional"><span
class="syntactic-cat">[access-level-modifier](Declarations.md#access-level-modifier)</span>~opt~</span>`protocol`{.literal}<span
class="syntactic-cat">[protocol-name](Declarations.md#protocol-name)</span><span
class="optional"><span
class="syntactic-cat">[type-inheritance-clause](Types.md#type-inheritance-clause)</span>~opt~</span><span
class="syntactic-cat">[protocol-body](Declarations.md#protocol-body)</span>

[‌](){#TP40016643-CH38-NoLink_1046} <span class="syntax-def-name">
protocol-name </span> <span class="arrow"> → </span><span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

[‌](){#TP40016643-CH38-NoLink_1047} <span class="syntax-def-name">
protocol-body </span> <span class="arrow"> → </span>`{`{.literal}<span
class="optional"><span
class="syntactic-cat">[protocol-member-declarations](Declarations.md#protocol-member-declarations)</span>~opt~</span>`}`{.literal}

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1048} <span class="syntax-def-name">
protocol-member-declaration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[protocol-property-declaration](Declarations.md#protocol-property-declaration)</span>

[‌](){#TP40016643-CH38-NoLink_1049} <span class="syntax-def-name">
protocol-member-declaration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[protocol-method-declaration](Declarations.md#protocol-method-declaration)</span>

[‌](){#TP40016643-CH38-NoLink_1050} <span class="syntax-def-name">
protocol-member-declaration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[protocol-initializer-declaration](Declarations.md#protocol-initializer-declaration)</span>

[‌](){#TP40016643-CH38-NoLink_1051} <span class="syntax-def-name">
protocol-member-declaration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[protocol-subscript-declaration](Declarations.md#protocol-subscript-declaration)</span>

[‌](){#TP40016643-CH38-NoLink_1052} <span class="syntax-def-name">
protocol-member-declaration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[protocol-associated-type-declaration](Declarations.md#protocol-associated-type-declaration)</span>

[‌](){#TP40016643-CH38-NoLink_1053} <span class="syntax-def-name">
protocol-member-declarations </span> <span class="arrow"> → </span><span
class="syntactic-cat">[protocol-member-declaration](Declarations.md#protocol-member-declaration)</span><span
class="optional"><span
class="syntactic-cat">[protocol-member-declarations](Declarations.md#protocol-member-declarations)</span>~opt~</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a protocol property declaration

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1055} <span class="syntax-def-name">
protocol-property-declaration </span> <span class="arrow"> →
</span><span
class="syntactic-cat">[variable-declaration-head](Declarations.md#variable-declaration-head)</span><span
class="syntactic-cat">[variable-name](Declarations.md#variable-name)</span><span
class="syntactic-cat">[type-annotation](Types.md#type-annotation)</span><span
class="syntactic-cat">[getter-setter-keyword-block](Declarations.md#getter-setter-keyword-block)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a protocol method declaration

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1057} <span class="syntax-def-name">
protocol-method-declaration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[function-head](Declarations.md#function-head)</span><span
class="syntactic-cat">[function-name](Declarations.md#function-name)</span><span
class="optional"><span
class="syntactic-cat">[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)</span>~opt~</span><span
class="syntactic-cat">[function-signature](Declarations.md#function-signature)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a protocol initializer declaration

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1059} <span class="syntax-def-name">
protocol-initializer-declaration </span> <span class="arrow"> →
</span><span
class="syntactic-cat">[initializer-head](Declarations.md#initializer-head)</span><span
class="optional"><span
class="syntactic-cat">[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)</span>~opt~</span><span
class="syntactic-cat">[parameter-clause](Declarations.md#parameter-clause)</span><span
class="optional">`throws`{.literal}~opt~</span>

[‌](){#TP40016643-CH38-NoLink_1060} <span class="syntax-def-name">
protocol-initializer-declaration </span> <span class="arrow"> →
</span><span
class="syntactic-cat">[initializer-head](Declarations.md#initializer-head)</span><span
class="optional"><span
class="syntactic-cat">[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)</span>~opt~</span><span
class="syntactic-cat">[parameter-clause](Declarations.md#parameter-clause)</span>`rethrows`{.literal}

</div>

</div>

<div class="syntax-defs">

Grammar of a protocol subscript declaration

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1062} <span class="syntax-def-name">
protocol-subscript-declaration </span> <span class="arrow"> →
</span><span
class="syntactic-cat">[subscript-head](Declarations.md#subscript-head)</span><span
class="syntactic-cat">[subscript-result](Declarations.md#subscript-result)</span><span
class="syntactic-cat">[getter-setter-keyword-block](Declarations.md#getter-setter-keyword-block)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a protocol associated type declaration

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1064} <span class="syntax-def-name">
protocol-associated-type-declaration </span> <span class="arrow"> →
</span><span
class="syntactic-cat">[typealias-head](Declarations.md#typealias-head)</span><span
class="optional"><span
class="syntactic-cat">[type-inheritance-clause](Types.md#type-inheritance-clause)</span>~opt~</span><span
class="optional"><span
class="syntactic-cat">[typealias-assignment](Declarations.md#typealias-assignment)</span>~opt~</span>

</div>

</div>

<div class="syntax-defs">

Grammar of an initializer declaration

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1066} <span class="syntax-def-name">
initializer-declaration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[initializer-head](Declarations.md#initializer-head)</span><span
class="optional"><span
class="syntactic-cat">[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)</span>~opt~</span><span
class="syntactic-cat">[parameter-clause](Declarations.md#parameter-clause)</span><span
class="optional">`throws`{.literal}~opt~</span><span
class="syntactic-cat">[initializer-body](Declarations.md#initializer-body)</span>

[‌](){#TP40016643-CH38-NoLink_1067} <span class="syntax-def-name">
initializer-declaration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[initializer-head](Declarations.md#initializer-head)</span><span
class="optional"><span
class="syntactic-cat">[generic-parameter-clause](GenericParametersAndArguments.md#generic-parameter-clause)</span>~opt~</span><span
class="syntactic-cat">[parameter-clause](Declarations.md#parameter-clause)</span>`rethrows`{.literal}<span
class="syntactic-cat">[initializer-body](Declarations.md#initializer-body)</span>

[‌](){#TP40016643-CH38-NoLink_1068} <span class="syntax-def-name">
initializer-head </span> <span class="arrow"> → </span><span
class="optional"><span
class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span
class="optional"><span
class="syntactic-cat">[declaration-modifiers](Declarations.md#declaration-modifiers)</span>~opt~</span>`init`{.literal}

[‌](){#TP40016643-CH38-NoLink_1069} <span class="syntax-def-name">
initializer-head </span> <span class="arrow"> → </span><span
class="optional"><span
class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span
class="optional"><span
class="syntactic-cat">[declaration-modifiers](Declarations.md#declaration-modifiers)</span>~opt~</span>`init`{.literal}`?`{.literal}

[‌](){#TP40016643-CH38-NoLink_1070} <span class="syntax-def-name">
initializer-head </span> <span class="arrow"> → </span><span
class="optional"><span
class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span
class="optional"><span
class="syntactic-cat">[declaration-modifiers](Declarations.md#declaration-modifiers)</span>~opt~</span>`init`{.literal}`!`{.literal}

[‌](){#TP40016643-CH38-NoLink_1071} <span class="syntax-def-name">
initializer-body </span> <span class="arrow"> → </span><span
class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a deinitializer declaration

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1073} <span class="syntax-def-name">
deinitializer-declaration </span> <span class="arrow"> → </span><span
class="optional"><span
class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span>`deinit`{.literal}<span
class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of an extension declaration

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1075} <span class="syntax-def-name">
extension-declaration </span> <span class="arrow"> → </span><span
class="optional"><span
class="syntactic-cat">[access-level-modifier](Declarations.md#access-level-modifier)</span>~opt~</span>`extension`{.literal}<span
class="syntactic-cat">[type-identifier](Types.md#type-identifier)</span><span
class="optional"><span
class="syntactic-cat">[type-inheritance-clause](Types.md#type-inheritance-clause)</span>~opt~</span><span
class="syntactic-cat">[extension-body](Declarations.md#extension-body)</span>

[‌](){#TP40016643-CH38-NoLink_1076} <span class="syntax-def-name">
extension-body </span> <span class="arrow"> → </span>`{`{.literal}<span
class="optional"><span
class="syntactic-cat">[declarations](Declarations.md#declarations)</span>~opt~</span>`}`{.literal}

</div>

</div>

<div class="syntax-defs">

Grammar of a subscript declaration

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1078} <span class="syntax-def-name">
subscript-declaration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[subscript-head](Declarations.md#subscript-head)</span><span
class="syntactic-cat">[subscript-result](Declarations.md#subscript-result)</span><span
class="syntactic-cat">[code-block](Declarations.md#code-block)</span>

[‌](){#TP40016643-CH38-NoLink_1079} <span class="syntax-def-name">
subscript-declaration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[subscript-head](Declarations.md#subscript-head)</span><span
class="syntactic-cat">[subscript-result](Declarations.md#subscript-result)</span><span
class="syntactic-cat">[getter-setter-block](Declarations.md#getter-setter-block)</span>

[‌](){#TP40016643-CH38-NoLink_1080} <span class="syntax-def-name">
subscript-declaration </span> <span class="arrow"> → </span><span
class="syntactic-cat">[subscript-head](Declarations.md#subscript-head)</span><span
class="syntactic-cat">[subscript-result](Declarations.md#subscript-result)</span><span
class="syntactic-cat">[getter-setter-keyword-block](Declarations.md#getter-setter-keyword-block)</span>

[‌](){#TP40016643-CH38-NoLink_1081} <span class="syntax-def-name">
subscript-head </span> <span class="arrow"> → </span><span
class="optional"><span
class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span
class="optional"><span
class="syntactic-cat">[declaration-modifiers](Declarations.md#declaration-modifiers)</span>~opt~</span>`subscript`{.literal}<span
class="syntactic-cat">[parameter-clause](Declarations.md#parameter-clause)</span>

[‌](){#TP40016643-CH38-NoLink_1082} <span class="syntax-def-name">
subscript-result </span> <span class="arrow"> →
</span>`->`{.literal}<span class="optional"><span
class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span
class="syntactic-cat">[type](Types.md#type)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of an operator declaration

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1084} <span class="syntax-def-name">
operator-declaration </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[prefix-operator-declaration](Declarations.md#prefix-operator-declaration)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[postfix-operator-declaration](Declarations.md#postfix-operator-declaration)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[infix-operator-declaration](Declarations.md#infix-operator-declaration)</span>
</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1085} <span class="syntax-def-name">
prefix-operator-declaration </span> <span class="arrow"> →
</span>`prefix`{.literal}`operator`{.literal}<span
class="syntactic-cat">[operator](LexicalStructure.md#operator)</span>`{`{.literal}`}`{.literal}

[‌](){#TP40016643-CH38-NoLink_1086} <span class="syntax-def-name">
postfix-operator-declaration </span> <span class="arrow"> →
</span>`postfix`{.literal}`operator`{.literal}<span
class="syntactic-cat">[operator](LexicalStructure.md#operator)</span>`{`{.literal}`}`{.literal}

[‌](){#TP40016643-CH38-NoLink_1087} <span class="syntax-def-name">
infix-operator-declaration </span> <span class="arrow"> →
</span>`infix`{.literal}`operator`{.literal}<span
class="syntactic-cat">[operator](LexicalStructure.md#operator)</span>`{`{.literal}<span
class="optional"><span
class="syntactic-cat">[infix-operator-attributes](Declarations.md#infix-operator-attributes)</span>~opt~</span>`}`{.literal}

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1088} <span class="syntax-def-name">
infix-operator-attributes </span> <span class="arrow"> → </span><span
class="optional"><span
class="syntactic-cat">[precedence-clause](Declarations.md#precedence-clause)</span>~opt~</span><span
class="optional"><span
class="syntactic-cat">[associativity-clause](Declarations.md#associativity-clause)</span>~opt~</span>

[‌](){#TP40016643-CH38-NoLink_1089} <span class="syntax-def-name">
precedence-clause </span> <span class="arrow"> →
</span>`precedence`{.literal}<span
class="syntactic-cat">[precedence-level](Declarations.md#precedence-level)</span>

[‌](){#TP40016643-CH38-NoLink_1090} <span class="syntax-def-name">
precedence-level </span> <span class="arrow"> → </span><span
class="text-description">A decimal integer between 0 and 255,
inclusive</span>

[‌](){#TP40016643-CH38-NoLink_1091} <span class="syntax-def-name">
associativity-clause </span> <span class="arrow"> →
</span>`associativity`{.literal}<span
class="syntactic-cat">[associativity](Declarations.md#associativity)</span>

[‌](){#TP40016643-CH38-NoLink_1092} <span class="syntax-def-name">
associativity </span> <span class="arrow"> → </span><span
class="alternative"> `left`{.literal} </span><span class="alternative">
`right`{.literal} </span><span class="alternative"> `none`{.literal}
</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a declaration modifier

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1094} <span class="syntax-def-name">
declaration-modifier </span> <span class="arrow"> → </span><span
class="alternative"> `class`{.literal} </span><span class="alternative">
`convenience`{.literal} </span><span class="alternative">
`dynamic`{.literal} </span><span class="alternative"> `final`{.literal}
</span><span class="alternative"> `infix`{.literal} </span><span
class="alternative"> `lazy`{.literal} </span><span class="alternative">
`mutating`{.literal} </span><span class="alternative">
`nonmutating`{.literal} </span><span class="alternative">
`optional`{.literal} </span><span class="alternative">
`override`{.literal} </span><span class="alternative">
`postfix`{.literal} </span><span class="alternative"> `prefix`{.literal}
</span><span class="alternative"> `required`{.literal} </span><span
class="alternative"> `static`{.literal} </span><span
class="alternative"> `unowned`{.literal} </span><span
class="alternative">
`unowned`{.literal}`(`{.literal}`safe`{.literal}`)`{.literal}
</span><span class="alternative">
`unowned`{.literal}`(`{.literal}`unsafe`{.literal}`)`{.literal}
</span><span class="alternative"> `weak`{.literal} </span>

[‌](){#TP40016643-CH38-NoLink_1095} <span class="syntax-def-name">
declaration-modifier </span> <span class="arrow"> → </span><span
class="syntactic-cat">[access-level-modifier](Declarations.md#access-level-modifier)</span>

[‌](){#TP40016643-CH38-NoLink_1096} <span class="syntax-def-name">
declaration-modifiers </span> <span class="arrow"> → </span><span
class="syntactic-cat">[declaration-modifier](Declarations.md#declaration-modifier)</span><span
class="optional"><span
class="syntactic-cat">[declaration-modifiers](Declarations.md#declaration-modifiers)</span>~opt~</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1097} <span class="syntax-def-name">
access-level-modifier </span> <span class="arrow"> → </span><span
class="alternative"> `internal`{.literal} </span><span
class="alternative">
`internal`{.literal}`(`{.literal}`set`{.literal}`)`{.literal} </span>

[‌](){#TP40016643-CH38-NoLink_1098} <span class="syntax-def-name">
access-level-modifier </span> <span class="arrow"> → </span><span
class="alternative"> `private`{.literal} </span><span
class="alternative">
`private`{.literal}`(`{.literal}`set`{.literal}`)`{.literal} </span>

[‌](){#TP40016643-CH38-NoLink_1099} <span class="syntax-def-name">
access-level-modifier </span> <span class="arrow"> → </span><span
class="alternative"> `public`{.literal} </span><span
class="alternative">
`public`{.literal}`(`{.literal}`set`{.literal}`)`{.literal} </span>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH38-ID478}
### Patterns {#patterns .section-name}

<div class="syntax-defs">

Grammar of a pattern

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1101} <span class="syntax-def-name">
pattern </span> <span class="arrow"> → </span><span
class="syntactic-cat">[wildcard-pattern](Patterns.md#wildcard-pattern)</span><span
class="optional"><span
class="syntactic-cat">[type-annotation](Types.md#type-annotation)</span>~opt~</span>

[‌](){#TP40016643-CH38-NoLink_1102} <span class="syntax-def-name">
pattern </span> <span class="arrow"> → </span><span
class="syntactic-cat">[identifier-pattern](Patterns.md#identifier-pattern)</span><span
class="optional"><span
class="syntactic-cat">[type-annotation](Types.md#type-annotation)</span>~opt~</span>

[‌](){#TP40016643-CH38-NoLink_1103} <span class="syntax-def-name">
pattern </span> <span class="arrow"> → </span><span
class="syntactic-cat">[value-binding-pattern](Patterns.md#value-binding-pattern)</span>

[‌](){#TP40016643-CH38-NoLink_1104} <span class="syntax-def-name">
pattern </span> <span class="arrow"> → </span><span
class="syntactic-cat">[tuple-pattern](Patterns.md#tuple-pattern)</span><span
class="optional"><span
class="syntactic-cat">[type-annotation](Types.md#type-annotation)</span>~opt~</span>

[‌](){#TP40016643-CH38-NoLink_1105} <span class="syntax-def-name">
pattern </span> <span class="arrow"> → </span><span
class="syntactic-cat">[enum-case-pattern](Patterns.md#enum-case-pattern)</span>

[‌](){#TP40016643-CH38-NoLink_1106} <span class="syntax-def-name">
pattern </span> <span class="arrow"> → </span><span
class="syntactic-cat">[optional-pattern](Patterns.md#optional-pattern)</span>

[‌](){#TP40016643-CH38-NoLink_1107} <span class="syntax-def-name">
pattern </span> <span class="arrow"> → </span><span
class="syntactic-cat">[type-casting-pattern](Patterns.md#type-casting-pattern)</span>

[‌](){#TP40016643-CH38-NoLink_1108} <span class="syntax-def-name">
pattern </span> <span class="arrow"> → </span><span
class="syntactic-cat">[expression-pattern](Patterns.md#expression-pattern)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a wildcard pattern

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1110} <span class="syntax-def-name">
wildcard-pattern </span> <span class="arrow"> → </span>`_`{.literal}

</div>

</div>

<div class="syntax-defs">

Grammar of an identifier pattern

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1112} <span class="syntax-def-name">
identifier-pattern </span> <span class="arrow"> → </span><span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a value-binding pattern

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1114} <span class="syntax-def-name">
value-binding-pattern </span> <span class="arrow"> →
</span>`let`{.literal}<span
class="syntactic-cat">[pattern](Patterns.md#pattern)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a tuple pattern

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1116} <span class="syntax-def-name">
tuple-pattern </span> <span class="arrow"> → </span>`(`{.literal}<span
class="optional"><span
class="syntactic-cat">[tuple-pattern-element-list](Patterns.md#tuple-pattern-element-list)</span>~opt~</span>`)`{.literal}

[‌](){#TP40016643-CH38-NoLink_1117} <span class="syntax-def-name">
tuple-pattern-element-list </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[tuple-pattern-element](Patterns.md#tuple-pattern-element)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[tuple-pattern-element](Patterns.md#tuple-pattern-element)</span>`,`{.literal}<span
class="syntactic-cat">[tuple-pattern-element-list](Patterns.md#tuple-pattern-element-list)</span>
</span>

[‌](){#TP40016643-CH38-NoLink_1118} <span class="syntax-def-name">
tuple-pattern-element </span> <span class="arrow"> → </span><span
class="syntactic-cat">[pattern](Patterns.md#pattern)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of an enumeration case pattern

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1120} <span class="syntax-def-name">
enum-case-pattern </span> <span class="arrow"> → </span><span
class="optional"><span
class="syntactic-cat">[type-identifier](Types.md#type-identifier)</span>~opt~</span>`.`{.literal}<span
class="syntactic-cat">[enum-case-name](Declarations.md#enum-case-name)</span><span
class="optional"><span
class="syntactic-cat">[tuple-pattern](Patterns.md#tuple-pattern)</span>~opt~</span>

</div>

</div>

<div class="syntax-defs">

Grammar of an optional pattern

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1122} <span class="syntax-def-name">
optional-pattern </span> <span class="arrow"> → </span><span
class="syntactic-cat">[identifier-pattern](Patterns.md#identifier-pattern)</span>`?`{.literal}

</div>

</div>

<div class="syntax-defs">

Grammar of a type casting pattern

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1124} <span class="syntax-def-name">
type-casting-pattern </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[is-pattern](Patterns.md#is-pattern)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[as-pattern](Patterns.md#as-pattern)</span>
</span>

[‌](){#TP40016643-CH38-NoLink_1125} <span class="syntax-def-name">
is-pattern </span> <span class="arrow"> → </span>`is`{.literal}<span
class="syntactic-cat">[type](Types.md#type)</span>

[‌](){#TP40016643-CH38-NoLink_1126} <span class="syntax-def-name">
as-pattern </span> <span class="arrow"> → </span><span
class="syntactic-cat">[pattern](Patterns.md#pattern)</span>`as`{.literal}<span
class="syntactic-cat">[type](Types.md#type)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of an expression pattern

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1128} <span class="syntax-def-name">
expression-pattern </span> <span class="arrow"> → </span><span
class="syntactic-cat">[expression](Expressions.md#expression)</span>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH38-ID479}
### Attributes {#attributes .section-name}

<div class="syntax-defs">

Grammar of an attribute

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1130} <span class="syntax-def-name">
attribute </span> <span class="arrow"> → </span>`@`{.literal}<span
class="syntactic-cat">[attribute-name](Attributes.md#attribute-name)</span><span
class="optional"><span
class="syntactic-cat">[attribute-argument-clause](Attributes.md#attribute-argument-clause)</span>~opt~</span>

[‌](){#TP40016643-CH38-NoLink_1131} <span class="syntax-def-name">
attribute-name </span> <span class="arrow"> → </span><span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

[‌](){#TP40016643-CH38-NoLink_1132} <span class="syntax-def-name">
attribute-argument-clause </span> <span class="arrow"> →
</span>`(`{.literal}<span class="optional"><span
class="syntactic-cat">[balanced-tokens](Attributes.md#balanced-tokens)</span>~opt~</span>`)`{.literal}

[‌](){#TP40016643-CH38-NoLink_1133} <span class="syntax-def-name">
attributes </span> <span class="arrow"> → </span><span
class="syntactic-cat">[attribute](Attributes.md#attribute)</span><span
class="optional"><span
class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1134} <span class="syntax-def-name">
balanced-tokens </span> <span class="arrow"> → </span><span
class="syntactic-cat">[balanced-token](Attributes.md#balanced-token)</span><span
class="optional"><span
class="syntactic-cat">[balanced-tokens](Attributes.md#balanced-tokens)</span>~opt~</span>

[‌](){#TP40016643-CH38-NoLink_1135} <span class="syntax-def-name">
balanced-token </span> <span class="arrow"> → </span>`(`{.literal}<span
class="optional"><span
class="syntactic-cat">[balanced-tokens](Attributes.md#balanced-tokens)</span>~opt~</span>`)`{.literal}

[‌](){#TP40016643-CH38-NoLink_1136} <span class="syntax-def-name">
balanced-token </span> <span class="arrow"> → </span>`[`{.literal}<span
class="optional"><span
class="syntactic-cat">[balanced-tokens](Attributes.md#balanced-tokens)</span>~opt~</span>`]`{.literal}

[‌](){#TP40016643-CH38-NoLink_1137} <span class="syntax-def-name">
balanced-token </span> <span class="arrow"> → </span>`{`{.literal}<span
class="optional"><span
class="syntactic-cat">[balanced-tokens](Attributes.md#balanced-tokens)</span>~opt~</span>`}`{.literal}

[‌](){#TP40016643-CH38-NoLink_1138} <span class="syntax-def-name">
balanced-token </span> <span class="arrow"> → </span><span
class="text-description">Any identifier, keyword, literal, or
operator</span>

[‌](){#TP40016643-CH38-NoLink_1139} <span class="syntax-def-name">
balanced-token </span> <span class="arrow"> → </span><span
class="text-description">Any punctuation except `(`{.literal},
`)`{.literal}, `[`{.literal}, `]`{.literal}, `{`{.literal}, or
`}`{.literal}</span>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH38-ID480}
### Expressions {#expressions .section-name}

<div class="syntax-defs">

Grammar of an expression

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1141} <span class="syntax-def-name">
expression </span> <span class="arrow"> → </span><span
class="optional"><span
class="syntactic-cat">[try-operator](Expressions.md#try-operator)</span>~opt~</span><span
class="syntactic-cat">[prefix-expression](Expressions.md#prefix-expression)</span><span
class="optional"><span
class="syntactic-cat">[binary-expressions](Expressions.md#binary-expressions)</span>~opt~</span>

[‌](){#TP40016643-CH38-NoLink_1142} <span class="syntax-def-name">
expression-list </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[expression](Expressions.md#expression)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[expression](Expressions.md#expression)</span>`,`{.literal}<span
class="syntactic-cat">[expression-list](Expressions.md#expression-list)</span>
</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a prefix expression

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1144} <span class="syntax-def-name">
prefix-expression </span> <span class="arrow"> → </span><span
class="optional"><span
class="syntactic-cat">[prefix-operator](LexicalStructure.md#prefix-operator)</span>~opt~</span><span
class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span>

[‌](){#TP40016643-CH38-NoLink_1145} <span class="syntax-def-name">
prefix-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[in-out-expression](Expressions.md#in-out-expression)</span>

[‌](){#TP40016643-CH38-NoLink_1146} <span class="syntax-def-name">
in-out-expression </span> <span class="arrow"> →
</span>`&`{.literal}<span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a try expression

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1148} <span class="syntax-def-name">
try-operator </span> <span class="arrow"> → </span><span
class="alternative"> `try`{.literal} </span><span class="alternative">
`try`{.literal}`?`{.literal} </span><span class="alternative">
`try`{.literal}`!`{.literal} </span>

</div>

</div>

<div class="syntax-defs">

Grammar of a binary expression

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1150} <span class="syntax-def-name">
binary-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[binary-operator](LexicalStructure.md#binary-operator)</span><span
class="syntactic-cat">[prefix-expression](Expressions.md#prefix-expression)</span>

[‌](){#TP40016643-CH38-NoLink_1151} <span class="syntax-def-name">
binary-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[assignment-operator](Expressions.md#assignment-operator)</span><span
class="optional"><span
class="syntactic-cat">[try-operator](Expressions.md#try-operator)</span>~opt~</span><span
class="syntactic-cat">[prefix-expression](Expressions.md#prefix-expression)</span>

[‌](){#TP40016643-CH38-NoLink_1152} <span class="syntax-def-name">
binary-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[conditional-operator](Expressions.md#conditional-operator)</span><span
class="optional"><span
class="syntactic-cat">[try-operator](Expressions.md#try-operator)</span>~opt~</span><span
class="syntactic-cat">[prefix-expression](Expressions.md#prefix-expression)</span>

[‌](){#TP40016643-CH38-NoLink_1153} <span class="syntax-def-name">
binary-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[type-casting-operator](Expressions.md#type-casting-operator)</span>

[‌](){#TP40016643-CH38-NoLink_1154} <span class="syntax-def-name">
binary-expressions </span> <span class="arrow"> → </span><span
class="syntactic-cat">[binary-expression](Expressions.md#binary-expression)</span><span
class="optional"><span
class="syntactic-cat">[binary-expressions](Expressions.md#binary-expressions)</span>~opt~</span>

</div>

</div>

<div class="syntax-defs">

Grammar of an assignment operator

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1156} <span class="syntax-def-name">
assignment-operator </span> <span class="arrow"> → </span>`=`{.literal}

</div>

</div>

<div class="syntax-defs">

Grammar of a conditional operator

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1158} <span class="syntax-def-name">
conditional-operator </span> <span class="arrow"> →
</span>`?`{.literal}<span class="optional"><span
class="syntactic-cat">[try-operator](Expressions.md#try-operator)</span>~opt~</span><span
class="syntactic-cat">[expression](Expressions.md#expression)</span>`:`{.literal}

</div>

</div>

<div class="syntax-defs">

Grammar of a type-casting operator

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1160} <span class="syntax-def-name">
type-casting-operator </span> <span class="arrow"> →
</span>`is`{.literal}<span
class="syntactic-cat">[type](Types.md#type)</span>

[‌](){#TP40016643-CH38-NoLink_1161} <span class="syntax-def-name">
type-casting-operator </span> <span class="arrow"> →
</span>`as`{.literal}<span
class="syntactic-cat">[type](Types.md#type)</span>

[‌](){#TP40016643-CH38-NoLink_1162} <span class="syntax-def-name">
type-casting-operator </span> <span class="arrow"> →
</span>`as`{.literal}`?`{.literal}<span
class="syntactic-cat">[type](Types.md#type)</span>

[‌](){#TP40016643-CH38-NoLink_1163} <span class="syntax-def-name">
type-casting-operator </span> <span class="arrow"> →
</span>`as`{.literal}`!`{.literal}<span
class="syntactic-cat">[type](Types.md#type)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a primary expression

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1165} <span class="syntax-def-name">
primary-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span><span
class="optional"><span
class="syntactic-cat">[generic-argument-clause](GenericParametersAndArguments.md#generic-argument-clause)</span>~opt~</span>

[‌](){#TP40016643-CH38-NoLink_1166} <span class="syntax-def-name">
primary-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[literal-expression](Expressions.md#literal-expression)</span>

[‌](){#TP40016643-CH38-NoLink_1167} <span class="syntax-def-name">
primary-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[self-expression](Expressions.md#self-expression)</span>

[‌](){#TP40016643-CH38-NoLink_1168} <span class="syntax-def-name">
primary-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[superclass-expression](Expressions.md#superclass-expression)</span>

[‌](){#TP40016643-CH38-NoLink_1169} <span class="syntax-def-name">
primary-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[closure-expression](Expressions.md#closure-expression)</span>

[‌](){#TP40016643-CH38-NoLink_1170} <span class="syntax-def-name">
primary-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[parenthesized-expression](Expressions.md#parenthesized-expression)</span>

[‌](){#TP40016643-CH38-NoLink_1171} <span class="syntax-def-name">
primary-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[implicit-member-expression](Expressions.md#implicit-member-expression)</span>

[‌](){#TP40016643-CH38-NoLink_1172} <span class="syntax-def-name">
primary-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[wildcard-expression](Expressions.md#wildcard-expression)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a literal expression

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1174} <span class="syntax-def-name">
literal-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[literal](LexicalStructure.md#literal)</span>

[‌](){#TP40016643-CH38-NoLink_1175} <span class="syntax-def-name">
literal-expression </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[array-literal](Expressions.md#array-literal)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[dictionary-literal](Expressions.md#dictionary-literal)</span>
</span>

[‌](){#TP40016643-CH38-NoLink_1176} <span class="syntax-def-name">
literal-expression </span> <span class="arrow"> → </span><span
class="alternative"> `__FILE__`{.literal} </span><span
class="alternative"> `__LINE__`{.literal} </span><span
class="alternative"> `__COLUMN__`{.literal} </span><span
class="alternative"> `__FUNCTION__`{.literal} </span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1177} <span class="syntax-def-name">
array-literal </span> <span class="arrow"> → </span>`[`{.literal}<span
class="optional"><span
class="syntactic-cat">[array-literal-items](Expressions.md#array-literal-items)</span>~opt~</span>`]`{.literal}

[‌](){#TP40016643-CH38-NoLink_1178} <span class="syntax-def-name">
array-literal-items </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[array-literal-item](Expressions.md#array-literal-item)</span><span
class="optional">`,`{.literal}~opt~</span> </span><span
class="alternative"> <span
class="syntactic-cat">[array-literal-item](Expressions.md#array-literal-item)</span>`,`{.literal}<span
class="syntactic-cat">[array-literal-items](Expressions.md#array-literal-items)</span>
</span>

[‌](){#TP40016643-CH38-NoLink_1179} <span class="syntax-def-name">
array-literal-item </span> <span class="arrow"> → </span><span
class="syntactic-cat">[expression](Expressions.md#expression)</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1180} <span class="syntax-def-name">
dictionary-literal </span> <span class="arrow"> → </span><span
class="alternative"> `[`{.literal}<span
class="syntactic-cat">[dictionary-literal-items](Expressions.md#dictionary-literal-items)</span>`]`{.literal}
</span><span class="alternative">
`[`{.literal}`:`{.literal}`]`{.literal} </span>

[‌](){#TP40016643-CH38-NoLink_1181} <span class="syntax-def-name">
dictionary-literal-items </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[dictionary-literal-item](Expressions.md#dictionary-literal-item)</span><span
class="optional">`,`{.literal}~opt~</span> </span><span
class="alternative"> <span
class="syntactic-cat">[dictionary-literal-item](Expressions.md#dictionary-literal-item)</span>`,`{.literal}<span
class="syntactic-cat">[dictionary-literal-items](Expressions.md#dictionary-literal-items)</span>
</span>

[‌](){#TP40016643-CH38-NoLink_1182} <span class="syntax-def-name">
dictionary-literal-item </span> <span class="arrow"> → </span><span
class="syntactic-cat">[expression](Expressions.md#expression)</span>`:`{.literal}<span
class="syntactic-cat">[expression](Expressions.md#expression)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a self expression

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1184} <span class="syntax-def-name">
self-expression </span> <span class="arrow"> → </span><span
class="alternative"> `self`{.literal} </span><span class="alternative">
<span
class="syntactic-cat">[self-method-expression](Expressions.md#self-method-expression)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[self-subscript-expression](Expressions.md#self-subscript-expression)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[self-initializer-expression](Expressions.md#self-initializer-expression)</span>
</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1185} <span class="syntax-def-name">
self-method-expression </span> <span class="arrow"> →
</span>`self`{.literal}`.`{.literal}<span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

[‌](){#TP40016643-CH38-NoLink_1186} <span class="syntax-def-name">
self-subscript-expression </span> <span class="arrow"> →
</span>`self`{.literal}`[`{.literal}<span
class="syntactic-cat">[expression-list](Expressions.md#expression-list)</span>`]`{.literal}

[‌](){#TP40016643-CH38-NoLink_1187} <span class="syntax-def-name">
self-initializer-expression </span> <span class="arrow"> →
</span>`self`{.literal}`.`{.literal}`init`{.literal}

</div>

</div>

<div class="syntax-defs">

Grammar of a superclass expression

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1189} <span class="syntax-def-name">
superclass-expression </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[superclass-method-expression](Expressions.md#superclass-method-expression)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[superclass-subscript-expression](Expressions.md#superclass-subscript-expression)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[superclass-initializer-expression](Expressions.md#superclass-initializer-expression)</span>
</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1190} <span class="syntax-def-name">
superclass-method-expression </span> <span class="arrow"> →
</span>`super`{.literal}`.`{.literal}<span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

[‌](){#TP40016643-CH38-NoLink_1191} <span class="syntax-def-name">
superclass-subscript-expression </span> <span class="arrow"> →
</span>`super`{.literal}`[`{.literal}<span
class="syntactic-cat">[expression-list](Expressions.md#expression-list)</span>`]`{.literal}

[‌](){#TP40016643-CH38-NoLink_1192} <span class="syntax-def-name">
superclass-initializer-expression </span> <span class="arrow"> →
</span>`super`{.literal}`.`{.literal}`init`{.literal}

</div>

</div>

<div class="syntax-defs">

Grammar of a closure expression

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1194} <span class="syntax-def-name">
closure-expression </span> <span class="arrow"> →
</span>`{`{.literal}<span class="optional"><span
class="syntactic-cat">[closure-signature](Expressions.md#closure-signature)</span>~opt~</span><span
class="syntactic-cat">[statements](Statements.md#statements)</span>`}`{.literal}

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1195} <span class="syntax-def-name">
closure-signature </span> <span class="arrow"> → </span><span
class="syntactic-cat">[parameter-clause](Declarations.md#parameter-clause)</span><span
class="optional"><span
class="syntactic-cat">[function-result](Declarations.md#function-result)</span>~opt~</span>`in`{.literal}

[‌](){#TP40016643-CH38-NoLink_1196} <span class="syntax-def-name">
closure-signature </span> <span class="arrow"> → </span><span
class="syntactic-cat">[identifier-list](LexicalStructure.md#identifier-list)</span><span
class="optional"><span
class="syntactic-cat">[function-result](Declarations.md#function-result)</span>~opt~</span>`in`{.literal}

[‌](){#TP40016643-CH38-NoLink_1197} <span class="syntax-def-name">
closure-signature </span> <span class="arrow"> → </span><span
class="syntactic-cat">[capture-list](Expressions.md#capture-list)</span><span
class="syntactic-cat">[parameter-clause](Declarations.md#parameter-clause)</span><span
class="optional"><span
class="syntactic-cat">[function-result](Declarations.md#function-result)</span>~opt~</span>`in`{.literal}

[‌](){#TP40016643-CH38-NoLink_1198} <span class="syntax-def-name">
closure-signature </span> <span class="arrow"> → </span><span
class="syntactic-cat">[capture-list](Expressions.md#capture-list)</span><span
class="syntactic-cat">[identifier-list](LexicalStructure.md#identifier-list)</span><span
class="optional"><span
class="syntactic-cat">[function-result](Declarations.md#function-result)</span>~opt~</span>`in`{.literal}

[‌](){#TP40016643-CH38-NoLink_1199} <span class="syntax-def-name">
closure-signature </span> <span class="arrow"> → </span><span
class="syntactic-cat">[capture-list](Expressions.md#capture-list)</span>`in`{.literal}

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1200} <span class="syntax-def-name">
capture-list </span> <span class="arrow"> → </span>`[`{.literal}<span
class="syntactic-cat">[capture-list-items](Expressions.md#capture-list-items)</span>`]`{.literal}

[‌](){#TP40016643-CH38-NoLink_1201} <span class="syntax-def-name">
capture-list-items </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[capture-list-item](Expressions.md#capture-list-item)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[capture-list-item](Expressions.md#capture-list-item)</span>`,`{.literal}<span
class="syntactic-cat">[capture-list-items](Expressions.md#capture-list-items)</span>
</span>

[‌](){#TP40016643-CH38-NoLink_1202} <span class="syntax-def-name">
capture-list-item </span> <span class="arrow"> → </span><span
class="optional"><span
class="syntactic-cat">[capture-specifier](Expressions.md#capture-specifier)</span>~opt~</span><span
class="syntactic-cat">[expression](Expressions.md#expression)</span>

[‌](){#TP40016643-CH38-NoLink_1203} <span class="syntax-def-name">
capture-specifier </span> <span class="arrow"> → </span><span
class="alternative"> `weak`{.literal} </span><span class="alternative">
`unowned`{.literal} </span><span class="alternative">
`unowned(safe)`{.literal} </span><span class="alternative">
`unowned(unsafe)`{.literal} </span>

</div>

</div>

<div class="syntax-defs">

Grammar of a implicit member expression

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1205} <span class="syntax-def-name">
implicit-member-expression </span> <span class="arrow"> →
</span>`.`{.literal}<span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a parenthesized expression

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1207} <span class="syntax-def-name">
parenthesized-expression </span> <span class="arrow"> →
</span>`(`{.literal}<span class="optional"><span
class="syntactic-cat">[expression-element-list](Expressions.md#expression-element-list)</span>~opt~</span>`)`{.literal}

[‌](){#TP40016643-CH38-NoLink_1208} <span class="syntax-def-name">
expression-element-list </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[expression-element](Expressions.md#expression-element)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[expression-element](Expressions.md#expression-element)</span>`,`{.literal}<span
class="syntactic-cat">[expression-element-list](Expressions.md#expression-element-list)</span>
</span>

[‌](){#TP40016643-CH38-NoLink_1209} <span class="syntax-def-name">
expression-element </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[expression](Expressions.md#expression)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>`:`{.literal}<span
class="syntactic-cat">[expression](Expressions.md#expression)</span>
</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a wildcard expression

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1211} <span class="syntax-def-name">
wildcard-expression </span> <span class="arrow"> → </span>`_`{.literal}

</div>

</div>

<div class="syntax-defs">

Grammar of a postfix expression

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1213} <span class="syntax-def-name">
postfix-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[primary-expression](Expressions.md#primary-expression)</span>

[‌](){#TP40016643-CH38-NoLink_1214} <span class="syntax-def-name">
postfix-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span><span
class="syntactic-cat">[postfix-operator](LexicalStructure.md#postfix-operator)</span>

[‌](){#TP40016643-CH38-NoLink_1215} <span class="syntax-def-name">
postfix-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[function-call-expression](Expressions.md#function-call-expression)</span>

[‌](){#TP40016643-CH38-NoLink_1216} <span class="syntax-def-name">
postfix-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[initializer-expression](Expressions.md#initializer-expression)</span>

[‌](){#TP40016643-CH38-NoLink_1217} <span class="syntax-def-name">
postfix-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[explicit-member-expression](Expressions.md#explicit-member-expression)</span>

[‌](){#TP40016643-CH38-NoLink_1218} <span class="syntax-def-name">
postfix-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[postfix-self-expression](Expressions.md#postfix-self-expression)</span>

[‌](){#TP40016643-CH38-NoLink_1219} <span class="syntax-def-name">
postfix-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[dynamic-type-expression](Expressions.md#dynamic-type-expression)</span>

[‌](){#TP40016643-CH38-NoLink_1220} <span class="syntax-def-name">
postfix-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[subscript-expression](Expressions.md#subscript-expression)</span>

[‌](){#TP40016643-CH38-NoLink_1221} <span class="syntax-def-name">
postfix-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[forced-value-expression](Expressions.md#forced-value-expression)</span>

[‌](){#TP40016643-CH38-NoLink_1222} <span class="syntax-def-name">
postfix-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[optional-chaining-expression](Expressions.md#optional-chaining-expression)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a function call expression

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1224} <span class="syntax-def-name">
function-call-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span><span
class="syntactic-cat">[parenthesized-expression](Expressions.md#parenthesized-expression)</span>

[‌](){#TP40016643-CH38-NoLink_1225} <span class="syntax-def-name">
function-call-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span><span
class="optional"><span
class="syntactic-cat">[parenthesized-expression](Expressions.md#parenthesized-expression)</span>~opt~</span><span
class="syntactic-cat">[trailing-closure](Expressions.md#trailing-closure)</span>

[‌](){#TP40016643-CH38-NoLink_1226} <span class="syntax-def-name">
trailing-closure </span> <span class="arrow"> → </span><span
class="syntactic-cat">[closure-expression](Expressions.md#closure-expression)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of an initializer expression

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1228} <span class="syntax-def-name">
initializer-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span>`.`{.literal}`init`{.literal}

</div>

</div>

<div class="syntax-defs">

Grammar of an explicit member expression

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1230} <span class="syntax-def-name">
explicit-member-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span>`.`{.literal}<span
class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)</span>

[‌](){#TP40016643-CH38-NoLink_1231} <span class="syntax-def-name">
explicit-member-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span>`.`{.literal}<span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span><span
class="optional"><span
class="syntactic-cat">[generic-argument-clause](GenericParametersAndArguments.md#generic-argument-clause)</span>~opt~</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a self expression

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1233} <span class="syntax-def-name">
postfix-self-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span>`.`{.literal}`self`{.literal}

</div>

</div>

<div class="syntax-defs">

Grammar of a dynamic type expression

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1235} <span class="syntax-def-name">
dynamic-type-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span>`.`{.literal}`dynamicType`{.literal}

</div>

</div>

<div class="syntax-defs">

Grammar of a subscript expression

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1237} <span class="syntax-def-name">
subscript-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span>`[`{.literal}<span
class="syntactic-cat">[expression-list](Expressions.md#expression-list)</span>`]`{.literal}

</div>

</div>

<div class="syntax-defs">

Grammar of a forced-value expression

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1239} <span class="syntax-def-name">
forced-value-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span>`!`{.literal}

</div>

</div>

<div class="syntax-defs">

Grammar of an optional-chaining expression

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1241} <span class="syntax-def-name">
optional-chaining-expression </span> <span class="arrow"> → </span><span
class="syntactic-cat">[postfix-expression](Expressions.md#postfix-expression)</span>`?`{.literal}

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH38-ID481}
### Lexical Structure {#lexical-structure .section-name}

<div class="syntax-defs">

Grammar of an identifier

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1243} <span class="syntax-def-name">
identifier </span> <span class="arrow"> → </span><span
class="syntactic-cat">[identifier-head](LexicalStructure.md#identifier-head)</span><span
class="optional"><span
class="syntactic-cat">[identifier-characters](LexicalStructure.md#identifier-characters)</span>~opt~</span>

[‌](){#TP40016643-CH38-NoLink_1244} <span class="syntax-def-name">
identifier </span> <span class="arrow"> → </span>`` ` ``{.literal}<span
class="syntactic-cat">[identifier-head](LexicalStructure.md#identifier-head)</span><span
class="optional"><span
class="syntactic-cat">[identifier-characters](LexicalStructure.md#identifier-characters)</span>~opt~</span>`` ` ``{.literal}

[‌](){#TP40016643-CH38-NoLink_1245} <span class="syntax-def-name">
identifier </span> <span class="arrow"> → </span><span
class="syntactic-cat">[implicit-parameter-name](LexicalStructure.md#implicit-parameter-name)</span>

[‌](){#TP40016643-CH38-NoLink_1246} <span class="syntax-def-name">
identifier-list </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>`,`{.literal}<span
class="syntactic-cat">[identifier-list](LexicalStructure.md#identifier-list)</span>
</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1247} <span class="syntax-def-name">
identifier-head </span> <span class="arrow"> → </span><span
class="text-description">Upper- or lowercase letter A through Z</span>

[‌](){#TP40016643-CH38-NoLink_1248} <span class="syntax-def-name">
identifier-head </span> <span class="arrow"> → </span>`_`{.literal}

[‌](){#TP40016643-CH38-NoLink_1249} <span class="syntax-def-name">
identifier-head </span> <span class="arrow"> → </span><span
class="text-description">U+00A8, U+00AA, U+00AD, U+00AF, U+00B2–U+00B5,
or U+00B7–U+00BA</span>

[‌](){#TP40016643-CH38-NoLink_1250} <span class="syntax-def-name">
identifier-head </span> <span class="arrow"> → </span><span
class="text-description">U+00BC–U+00BE, U+00C0–U+00D6, U+00D8–U+00F6, or
U+00F8–U+00FF</span>

[‌](){#TP40016643-CH38-NoLink_1251} <span class="syntax-def-name">
identifier-head </span> <span class="arrow"> → </span><span
class="text-description">U+0100–U+02FF, U+0370–U+167F, U+1681–U+180D, or
U+180F–U+1DBF</span>

[‌](){#TP40016643-CH38-NoLink_1252} <span class="syntax-def-name">
identifier-head </span> <span class="arrow"> → </span><span
class="text-description">U+1E00–U+1FFF</span>

[‌](){#TP40016643-CH38-NoLink_1253} <span class="syntax-def-name">
identifier-head </span> <span class="arrow"> → </span><span
class="text-description">U+200B–U+200D, U+202A–U+202E, U+203F–U+2040,
U+2054, or U+2060–U+206F</span>

[‌](){#TP40016643-CH38-NoLink_1254} <span class="syntax-def-name">
identifier-head </span> <span class="arrow"> → </span><span
class="text-description">U+2070–U+20CF, U+2100–U+218F, U+2460–U+24FF, or
U+2776–U+2793</span>

[‌](){#TP40016643-CH38-NoLink_1255} <span class="syntax-def-name">
identifier-head </span> <span class="arrow"> → </span><span
class="text-description">U+2C00–U+2DFF or U+2E80–U+2FFF</span>

[‌](){#TP40016643-CH38-NoLink_1256} <span class="syntax-def-name">
identifier-head </span> <span class="arrow"> → </span><span
class="text-description">U+3004–U+3007, U+3021–U+302F, U+3031–U+303F, or
U+3040–U+D7FF</span>

[‌](){#TP40016643-CH38-NoLink_1257} <span class="syntax-def-name">
identifier-head </span> <span class="arrow"> → </span><span
class="text-description">U+F900–U+FD3D, U+FD40–U+FDCF, U+FDF0–U+FE1F, or
U+FE30–U+FE44</span>

[‌](){#TP40016643-CH38-NoLink_1258} <span class="syntax-def-name">
identifier-head </span> <span class="arrow"> → </span><span
class="text-description">U+FE47–U+FFFD</span>

[‌](){#TP40016643-CH38-NoLink_1259} <span class="syntax-def-name">
identifier-head </span> <span class="arrow"> → </span><span
class="text-description">U+10000–U+1FFFD, U+20000–U+2FFFD,
U+30000–U+3FFFD, or U+40000–U+4FFFD</span>

[‌](){#TP40016643-CH38-NoLink_1260} <span class="syntax-def-name">
identifier-head </span> <span class="arrow"> → </span><span
class="text-description">U+50000–U+5FFFD, U+60000–U+6FFFD,
U+70000–U+7FFFD, or U+80000–U+8FFFD</span>

[‌](){#TP40016643-CH38-NoLink_1261} <span class="syntax-def-name">
identifier-head </span> <span class="arrow"> → </span><span
class="text-description">U+90000–U+9FFFD, U+A0000–U+AFFFD,
U+B0000–U+BFFFD, or U+C0000–U+CFFFD</span>

[‌](){#TP40016643-CH38-NoLink_1262} <span class="syntax-def-name">
identifier-head </span> <span class="arrow"> → </span><span
class="text-description">U+D0000–U+DFFFD or U+E0000–U+EFFFD</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1263} <span class="syntax-def-name">
identifier-character </span> <span class="arrow"> → </span><span
class="text-description">Digit 0 through 9</span>

[‌](){#TP40016643-CH38-NoLink_1264} <span class="syntax-def-name">
identifier-character </span> <span class="arrow"> → </span><span
class="text-description">U+0300–U+036F, U+1DC0–U+1DFF, U+20D0–U+20FF, or
U+FE20–U+FE2F</span>

[‌](){#TP40016643-CH38-NoLink_1265} <span class="syntax-def-name">
identifier-character </span> <span class="arrow"> → </span><span
class="syntactic-cat">[identifier-head](LexicalStructure.md#identifier-head)</span>

[‌](){#TP40016643-CH38-NoLink_1266} <span class="syntax-def-name">
identifier-characters </span> <span class="arrow"> → </span><span
class="syntactic-cat">[identifier-character](LexicalStructure.md#identifier-character)</span><span
class="optional"><span
class="syntactic-cat">[identifier-characters](LexicalStructure.md#identifier-characters)</span>~opt~</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1267} <span class="syntax-def-name">
implicit-parameter-name </span> <span class="arrow"> →
</span>`$`{.literal}<span
class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a literal

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1269} <span class="syntax-def-name">
literal </span> <span class="arrow"> → </span><span class="alternative">
<span
class="syntactic-cat">[numeric-literal](LexicalStructure.md#numeric-literal)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[string-literal](LexicalStructure.md#string-literal)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[boolean-literal](LexicalStructure.md#boolean-literal)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[nil-literal](LexicalStructure.md#nil-literal)</span>
</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1270} <span class="syntax-def-name">
numeric-literal </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="optional">`-`{.literal}~opt~</span><span
class="syntactic-cat">[integer-literal](LexicalStructure.md#integer-literal)</span>
</span><span class="alternative"> <span
class="optional">`-`{.literal}~opt~</span><span
class="syntactic-cat">[floating-point-literal](LexicalStructure.md#floating-point-literal)</span>
</span>

[‌](){#TP40016643-CH38-NoLink_1271} <span class="syntax-def-name">
boolean-literal </span> <span class="arrow"> → </span><span
class="alternative"> `true`{.literal} </span><span class="alternative">
`false`{.literal} </span>

[‌](){#TP40016643-CH38-NoLink_1272} <span class="syntax-def-name">
nil-literal </span> <span class="arrow"> → </span>`nil`{.literal}

</div>

</div>

<div class="syntax-defs">

Grammar of an integer literal

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1274} <span class="syntax-def-name">
integer-literal </span> <span class="arrow"> → </span><span
class="syntactic-cat">[binary-literal](LexicalStructure.md#binary-literal)</span>

[‌](){#TP40016643-CH38-NoLink_1275} <span class="syntax-def-name">
integer-literal </span> <span class="arrow"> → </span><span
class="syntactic-cat">[octal-literal](LexicalStructure.md#octal-literal)</span>

[‌](){#TP40016643-CH38-NoLink_1276} <span class="syntax-def-name">
integer-literal </span> <span class="arrow"> → </span><span
class="syntactic-cat">[decimal-literal](LexicalStructure.md#decimal-literal)</span>

[‌](){#TP40016643-CH38-NoLink_1277} <span class="syntax-def-name">
integer-literal </span> <span class="arrow"> → </span><span
class="syntactic-cat">[hexadecimal-literal](LexicalStructure.md#hexadecimal-literal)</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1278} <span class="syntax-def-name">
binary-literal </span> <span class="arrow"> → </span>`0b`{.literal}<span
class="syntactic-cat">[binary-digit](LexicalStructure.md#binary-digit)</span><span
class="optional"><span
class="syntactic-cat">[binary-literal-characters](LexicalStructure.md#binary-literal-characters)</span>~opt~</span>

[‌](){#TP40016643-CH38-NoLink_1279} <span class="syntax-def-name">
binary-digit </span> <span class="arrow"> → </span><span
class="text-description">Digit 0 or 1</span>

[‌](){#TP40016643-CH38-NoLink_1280} <span class="syntax-def-name">
binary-literal-character </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[binary-digit](LexicalStructure.md#binary-digit)</span>
</span><span class="alternative"> `_`{.literal} </span>

[‌](){#TP40016643-CH38-NoLink_1281} <span class="syntax-def-name">
binary-literal-characters </span> <span class="arrow"> → </span><span
class="syntactic-cat">[binary-literal-character](LexicalStructure.md#binary-literal-character)</span><span
class="optional"><span
class="syntactic-cat">[binary-literal-characters](LexicalStructure.md#binary-literal-characters)</span>~opt~</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1282} <span class="syntax-def-name">
octal-literal </span> <span class="arrow"> → </span>`0o`{.literal}<span
class="syntactic-cat">[octal-digit](LexicalStructure.md#octal-digit)</span><span
class="optional"><span
class="syntactic-cat">[octal-literal-characters](LexicalStructure.md#octal-literal-characters)</span>~opt~</span>

[‌](){#TP40016643-CH38-NoLink_1283} <span class="syntax-def-name">
octal-digit </span> <span class="arrow"> → </span><span
class="text-description">Digit 0 through 7</span>

[‌](){#TP40016643-CH38-NoLink_1284} <span class="syntax-def-name">
octal-literal-character </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[octal-digit](LexicalStructure.md#octal-digit)</span>
</span><span class="alternative"> `_`{.literal} </span>

[‌](){#TP40016643-CH38-NoLink_1285} <span class="syntax-def-name">
octal-literal-characters </span> <span class="arrow"> → </span><span
class="syntactic-cat">[octal-literal-character](LexicalStructure.md#octal-literal-character)</span><span
class="optional"><span
class="syntactic-cat">[octal-literal-characters](LexicalStructure.md#octal-literal-characters)</span>~opt~</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1286} <span class="syntax-def-name">
decimal-literal </span> <span class="arrow"> → </span><span
class="syntactic-cat">[decimal-digit](LexicalStructure.md#decimal-digit)</span><span
class="optional"><span
class="syntactic-cat">[decimal-literal-characters](LexicalStructure.md#decimal-literal-characters)</span>~opt~</span>

[‌](){#TP40016643-CH38-NoLink_1287} <span class="syntax-def-name">
decimal-digit </span> <span class="arrow"> → </span><span
class="text-description">Digit 0 through 9</span>

[‌](){#TP40016643-CH38-NoLink_1288} <span class="syntax-def-name">
decimal-digits </span> <span class="arrow"> → </span><span
class="syntactic-cat">[decimal-digit](LexicalStructure.md#decimal-digit)</span><span
class="optional"><span
class="syntactic-cat">[decimal-digits](LexicalStructure.md#decimal-digits)</span>~opt~</span>

[‌](){#TP40016643-CH38-NoLink_1289} <span class="syntax-def-name">
decimal-literal-character </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[decimal-digit](LexicalStructure.md#decimal-digit)</span>
</span><span class="alternative"> `_`{.literal} </span>

[‌](){#TP40016643-CH38-NoLink_1290} <span class="syntax-def-name">
decimal-literal-characters </span> <span class="arrow"> → </span><span
class="syntactic-cat">[decimal-literal-character](LexicalStructure.md#decimal-literal-character)</span><span
class="optional"><span
class="syntactic-cat">[decimal-literal-characters](LexicalStructure.md#decimal-literal-characters)</span>~opt~</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1291} <span class="syntax-def-name">
hexadecimal-literal </span> <span class="arrow"> →
</span>`0x`{.literal}<span
class="syntactic-cat">[hexadecimal-digit](LexicalStructure.md#hexadecimal-digit)</span><span
class="optional"><span
class="syntactic-cat">[hexadecimal-literal-characters](LexicalStructure.md#hexadecimal-literal-characters)</span>~opt~</span>

[‌](){#TP40016643-CH38-NoLink_1292} <span class="syntax-def-name">
hexadecimal-digit </span> <span class="arrow"> → </span><span
class="text-description">Digit 0 through 9, a through f, or A through
F</span>

[‌](){#TP40016643-CH38-NoLink_1293} <span class="syntax-def-name">
hexadecimal-literal-character </span> <span class="arrow"> →
</span><span class="alternative"> <span
class="syntactic-cat">[hexadecimal-digit](LexicalStructure.md#hexadecimal-digit)</span>
</span><span class="alternative"> `_`{.literal} </span>

[‌](){#TP40016643-CH38-NoLink_1294} <span class="syntax-def-name">
hexadecimal-literal-characters </span> <span class="arrow"> →
</span><span
class="syntactic-cat">[hexadecimal-literal-character](LexicalStructure.md#hexadecimal-literal-character)</span><span
class="optional"><span
class="syntactic-cat">[hexadecimal-literal-characters](LexicalStructure.md#hexadecimal-literal-characters)</span>~opt~</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a floating-point literal

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1296} <span class="syntax-def-name">
floating-point-literal </span> <span class="arrow"> → </span><span
class="syntactic-cat">[decimal-literal](LexicalStructure.md#decimal-literal)</span><span
class="optional"><span
class="syntactic-cat">[decimal-fraction](LexicalStructure.md#decimal-fraction)</span>~opt~</span><span
class="optional"><span
class="syntactic-cat">[decimal-exponent](LexicalStructure.md#decimal-exponent)</span>~opt~</span>

[‌](){#TP40016643-CH38-NoLink_1297} <span class="syntax-def-name">
floating-point-literal </span> <span class="arrow"> → </span><span
class="syntactic-cat">[hexadecimal-literal](LexicalStructure.md#hexadecimal-literal)</span><span
class="optional"><span
class="syntactic-cat">[hexadecimal-fraction](LexicalStructure.md#hexadecimal-fraction)</span>~opt~</span><span
class="syntactic-cat">[hexadecimal-exponent](LexicalStructure.md#hexadecimal-exponent)</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1298} <span class="syntax-def-name">
decimal-fraction </span> <span class="arrow"> →
</span>`.`{.literal}<span
class="syntactic-cat">[decimal-literal](LexicalStructure.md#decimal-literal)</span>

[‌](){#TP40016643-CH38-NoLink_1299} <span class="syntax-def-name">
decimal-exponent </span> <span class="arrow"> → </span><span
class="syntactic-cat">[floating-point-e](LexicalStructure.md#floating-point-e)</span><span
class="optional"><span
class="syntactic-cat">[sign](LexicalStructure.md#sign)</span>~opt~</span><span
class="syntactic-cat">[decimal-literal](LexicalStructure.md#decimal-literal)</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1300} <span class="syntax-def-name">
hexadecimal-fraction </span> <span class="arrow"> →
</span>`.`{.literal}<span
class="syntactic-cat">[hexadecimal-digit](LexicalStructure.md#hexadecimal-digit)</span><span
class="optional"><span
class="syntactic-cat">[hexadecimal-literal-characters](LexicalStructure.md#hexadecimal-literal-characters)</span>~opt~</span>

[‌](){#TP40016643-CH38-NoLink_1301} <span class="syntax-def-name">
hexadecimal-exponent </span> <span class="arrow"> → </span><span
class="syntactic-cat">[floating-point-p](LexicalStructure.md#floating-point-p)</span><span
class="optional"><span
class="syntactic-cat">[sign](LexicalStructure.md#sign)</span>~opt~</span><span
class="syntactic-cat">[decimal-literal](LexicalStructure.md#decimal-literal)</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1302} <span class="syntax-def-name">
floating-point-e </span> <span class="arrow"> → </span><span
class="alternative"> `e`{.literal} </span><span class="alternative">
`E`{.literal} </span>

[‌](){#TP40016643-CH38-NoLink_1303} <span class="syntax-def-name">
floating-point-p </span> <span class="arrow"> → </span><span
class="alternative"> `p`{.literal} </span><span class="alternative">
`P`{.literal} </span>

[‌](){#TP40016643-CH38-NoLink_1304} <span class="syntax-def-name"> sign
</span> <span class="arrow"> → </span><span class="alternative">
`+`{.literal} </span><span class="alternative"> `-`{.literal} </span>

</div>

</div>

<div class="syntax-defs">

Grammar of a string literal

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1306} <span class="syntax-def-name">
string-literal </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[static-string-literal](LexicalStructure.md#static-string-literal)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[interpolated-string-literal](LexicalStructure.md#interpolated-string-literal)</span>
</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1307} <span class="syntax-def-name">
static-string-literal </span> <span class="arrow"> →
</span>`"`{.literal}<span class="optional"><span
class="syntactic-cat">[quoted-text](LexicalStructure.md#quoted-text)</span>~opt~</span>`"`{.literal}

[‌](){#TP40016643-CH38-NoLink_1308} <span class="syntax-def-name">
quoted-text </span> <span class="arrow"> → </span><span
class="syntactic-cat">[quoted-text-item](LexicalStructure.md#quoted-text-item)</span><span
class="optional"><span
class="syntactic-cat">[quoted-text](LexicalStructure.md#quoted-text)</span>~opt~</span>

[‌](){#TP40016643-CH38-NoLink_1309} <span class="syntax-def-name">
quoted-text-item </span> <span class="arrow"> → </span><span
class="syntactic-cat">[escaped-character](LexicalStructure.md#escaped-character)</span>

[‌](){#TP40016643-CH38-NoLink_1310} <span class="syntax-def-name">
quoted-text-item </span> <span class="arrow"> → </span><span
class="text-description">Any Unicode scalar value except `"`{.literal},
`\`{.literal}, U+000A, or U+000D</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1311} <span class="syntax-def-name">
interpolated-string-literal </span> <span class="arrow"> →
</span>`"`{.literal}<span class="optional"><span
class="syntactic-cat">[interpolated-text](LexicalStructure.md#interpolated-text)</span>~opt~</span>`"`{.literal}

[‌](){#TP40016643-CH38-NoLink_1312} <span class="syntax-def-name">
interpolated-text </span> <span class="arrow"> → </span><span
class="syntactic-cat">[interpolated-text-item](LexicalStructure.md#interpolated-text-item)</span><span
class="optional"><span
class="syntactic-cat">[interpolated-text](LexicalStructure.md#interpolated-text)</span>~opt~</span>

[‌](){#TP40016643-CH38-NoLink_1313} <span class="syntax-def-name">
interpolated-text-item </span> <span class="arrow"> → </span><span
class="alternative"> `\(`{.literal}<span
class="syntactic-cat">[expression](Expressions.md#expression)</span>`)`{.literal}
</span><span class="alternative"> <span
class="syntactic-cat">[quoted-text-item](LexicalStructure.md#quoted-text-item)</span>
</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1314} <span class="syntax-def-name">
escaped-character </span> <span class="arrow"> → </span><span
class="alternative"> `\0`{.literal} </span><span class="alternative">
`\\`{.literal} </span><span class="alternative"> `\t`{.literal}
</span><span class="alternative"> `\n`{.literal} </span><span
class="alternative"> `\r`{.literal} </span><span class="alternative">
`\"`{.literal} </span><span class="alternative"> `\'`{.literal} </span>

[‌](){#TP40016643-CH38-NoLink_1315} <span class="syntax-def-name">
escaped-character </span> <span class="arrow"> →
</span>`\u`{.literal}`{`{.literal}<span
class="syntactic-cat">[unicode-scalar-digits](LexicalStructure.md#unicode-scalar-digits)</span>`}`{.literal}

[‌](){#TP40016643-CH38-NoLink_1316} <span class="syntax-def-name">
unicode-scalar-digits </span> <span class="arrow"> → </span><span
class="text-description">Between one and eight hexadecimal digits</span>

</div>

</div>

<div class="syntax-defs">

Grammar of operators

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1318} <span class="syntax-def-name">
operator </span> <span class="arrow"> → </span><span
class="syntactic-cat">[operator-head](LexicalStructure.md#operator-head)</span><span
class="optional"><span
class="syntactic-cat">[operator-characters](LexicalStructure.md#operator-characters)</span>~opt~</span>

[‌](){#TP40016643-CH38-NoLink_1319} <span class="syntax-def-name">
operator </span> <span class="arrow"> → </span><span
class="syntactic-cat">[dot-operator-head](LexicalStructure.md#dot-operator-head)</span><span
class="optional"><span
class="syntactic-cat">[dot-operator-characters](LexicalStructure.md#dot-operator-characters)</span>~opt~</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1320} <span class="syntax-def-name">
operator-head </span> <span class="arrow"> → </span><span
class="alternative"> `/`{.literal} </span><span class="alternative">
`=`{.literal} </span><span class="alternative"> `-`{.literal}
</span><span class="alternative"> `+`{.literal} </span><span
class="alternative"> `!`{.literal} </span><span class="alternative">
`*`{.literal} </span><span class="alternative"> `%`{.literal}
</span><span class="alternative"> `<`{.literal} </span><span
class="alternative"> `>`{.literal} </span><span class="alternative">
`&`{.literal} </span><span class="alternative"> `|`{.literal}
</span><span class="alternative"> `^`{.literal} </span><span
class="alternative"> `~`{.literal} </span><span class="alternative">
`?`{.literal} </span>

[‌](){#TP40016643-CH38-NoLink_1321} <span class="syntax-def-name">
operator-head </span> <span class="arrow"> → </span><span
class="text-description">U+00A1–U+00A7</span>

[‌](){#TP40016643-CH38-NoLink_1322} <span class="syntax-def-name">
operator-head </span> <span class="arrow"> → </span><span
class="text-description">U+00A9 or U+00AB</span>

[‌](){#TP40016643-CH38-NoLink_1323} <span class="syntax-def-name">
operator-head </span> <span class="arrow"> → </span><span
class="text-description">U+00AC or U+00AE</span>

[‌](){#TP40016643-CH38-NoLink_1324} <span class="syntax-def-name">
operator-head </span> <span class="arrow"> → </span><span
class="text-description">U+00B0–U+00B1, U+00B6, U+00BB, U+00BF, U+00D7,
or U+00F7</span>

[‌](){#TP40016643-CH38-NoLink_1325} <span class="syntax-def-name">
operator-head </span> <span class="arrow"> → </span><span
class="text-description">U+2016–U+2017 or U+2020–U+2027</span>

[‌](){#TP40016643-CH38-NoLink_1326} <span class="syntax-def-name">
operator-head </span> <span class="arrow"> → </span><span
class="text-description">U+2030–U+203E</span>

[‌](){#TP40016643-CH38-NoLink_1327} <span class="syntax-def-name">
operator-head </span> <span class="arrow"> → </span><span
class="text-description">U+2041–U+2053</span>

[‌](){#TP40016643-CH38-NoLink_1328} <span class="syntax-def-name">
operator-head </span> <span class="arrow"> → </span><span
class="text-description">U+2055–U+205E</span>

[‌](){#TP40016643-CH38-NoLink_1329} <span class="syntax-def-name">
operator-head </span> <span class="arrow"> → </span><span
class="text-description">U+2190–U+23FF</span>

[‌](){#TP40016643-CH38-NoLink_1330} <span class="syntax-def-name">
operator-head </span> <span class="arrow"> → </span><span
class="text-description">U+2500–U+2775</span>

[‌](){#TP40016643-CH38-NoLink_1331} <span class="syntax-def-name">
operator-head </span> <span class="arrow"> → </span><span
class="text-description">U+2794–U+2BFF</span>

[‌](){#TP40016643-CH38-NoLink_1332} <span class="syntax-def-name">
operator-head </span> <span class="arrow"> → </span><span
class="text-description">U+2E00–U+2E7F</span>

[‌](){#TP40016643-CH38-NoLink_1333} <span class="syntax-def-name">
operator-head </span> <span class="arrow"> → </span><span
class="text-description">U+3001–U+3003</span>

[‌](){#TP40016643-CH38-NoLink_1334} <span class="syntax-def-name">
operator-head </span> <span class="arrow"> → </span><span
class="text-description">U+3008–U+3030</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1335} <span class="syntax-def-name">
operator-character </span> <span class="arrow"> → </span><span
class="syntactic-cat">[operator-head](LexicalStructure.md#operator-head)</span>

[‌](){#TP40016643-CH38-NoLink_1336} <span class="syntax-def-name">
operator-character </span> <span class="arrow"> → </span><span
class="text-description">U+0300–U+036F</span>

[‌](){#TP40016643-CH38-NoLink_1337} <span class="syntax-def-name">
operator-character </span> <span class="arrow"> → </span><span
class="text-description">U+1DC0–U+1DFF</span>

[‌](){#TP40016643-CH38-NoLink_1338} <span class="syntax-def-name">
operator-character </span> <span class="arrow"> → </span><span
class="text-description">U+20D0–U+20FF</span>

[‌](){#TP40016643-CH38-NoLink_1339} <span class="syntax-def-name">
operator-character </span> <span class="arrow"> → </span><span
class="text-description">U+FE00–U+FE0F</span>

[‌](){#TP40016643-CH38-NoLink_1340} <span class="syntax-def-name">
operator-character </span> <span class="arrow"> → </span><span
class="text-description">U+FE20–U+FE2F</span>

[‌](){#TP40016643-CH38-NoLink_1341} <span class="syntax-def-name">
operator-character </span> <span class="arrow"> → </span><span
class="text-description">U+E0100–U+E01EF</span>

[‌](){#TP40016643-CH38-NoLink_1342} <span class="syntax-def-name">
operator-characters </span> <span class="arrow"> → </span><span
class="syntactic-cat">[operator-character](LexicalStructure.md#operator-character)</span><span
class="optional"><span
class="syntactic-cat">[operator-characters](LexicalStructure.md#operator-characters)</span>~opt~</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1343} <span class="syntax-def-name">
dot-operator-head </span> <span class="arrow"> → </span>`..`{.literal}

[‌](){#TP40016643-CH38-NoLink_1344} <span class="syntax-def-name">
dot-operator-character </span> <span class="arrow"> → </span><span
class="alternative"> `.`{.literal} </span><span class="alternative">
<span
class="syntactic-cat">[operator-character](LexicalStructure.md#operator-character)</span>
</span>

[‌](){#TP40016643-CH38-NoLink_1345} <span class="syntax-def-name">
dot-operator-characters </span> <span class="arrow"> → </span><span
class="syntactic-cat">[dot-operator-character](LexicalStructure.md#dot-operator-character)</span><span
class="optional"><span
class="syntactic-cat">[dot-operator-characters](LexicalStructure.md#dot-operator-characters)</span>~opt~</span>

</div>

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1346} <span class="syntax-def-name">
binary-operator </span> <span class="arrow"> → </span><span
class="syntactic-cat">[operator](LexicalStructure.md#operator)</span>

[‌](){#TP40016643-CH38-NoLink_1347} <span class="syntax-def-name">
prefix-operator </span> <span class="arrow"> → </span><span
class="syntactic-cat">[operator](LexicalStructure.md#operator)</span>

[‌](){#TP40016643-CH38-NoLink_1348} <span class="syntax-def-name">
postfix-operator </span> <span class="arrow"> → </span><span
class="syntactic-cat">[operator](LexicalStructure.md#operator)</span>

</div>

</div>

</div>

<div class="section section">

[‌](){#TP40016643-CH38-ID482}
### Types {#types .section-name}

<div class="syntax-defs">

Grammar of a type

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1350} <span class="syntax-def-name"> type
</span> <span class="arrow"> → </span><span class="alternative"> <span
class="syntactic-cat">[array-type](Types.md#array-type)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[dictionary-type](Types.md#dictionary-type)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[function-type](Types.md#function-type)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[type-identifier](Types.md#type-identifier)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[tuple-type](Types.md#tuple-type)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[optional-type](Types.md#optional-type)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[implicitly-unwrapped-optional-type](Types.md#implicitly-unwrapped-optional-type)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[protocol-composition-type](Types.md#protocol-composition-type)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[metatype-type](Types.md#metatype-type)</span>
</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a type annotation

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1352} <span class="syntax-def-name">
type-annotation </span> <span class="arrow"> → </span>`:`{.literal}<span
class="optional"><span
class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span
class="syntactic-cat">[type](Types.md#type)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a type identifier

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1354} <span class="syntax-def-name">
type-identifier </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[type-name](Types.md#type-name)</span><span
class="optional"><span
class="syntactic-cat">[generic-argument-clause](GenericParametersAndArguments.md#generic-argument-clause)</span>~opt~</span>
</span><span class="alternative"> <span
class="syntactic-cat">[type-name](Types.md#type-name)</span><span
class="optional"><span
class="syntactic-cat">[generic-argument-clause](GenericParametersAndArguments.md#generic-argument-clause)</span>~opt~</span>`.`{.literal}<span
class="syntactic-cat">[type-identifier](Types.md#type-identifier)</span>
</span>

[‌](){#TP40016643-CH38-NoLink_1355} <span class="syntax-def-name">
type-name </span> <span class="arrow"> → </span><span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a tuple type

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1357} <span class="syntax-def-name">
tuple-type </span> <span class="arrow"> → </span>`(`{.literal}<span
class="optional"><span
class="syntactic-cat">[tuple-type-body](Types.md#tuple-type-body)</span>~opt~</span>`)`{.literal}

[‌](){#TP40016643-CH38-NoLink_1358} <span class="syntax-def-name">
tuple-type-body </span> <span class="arrow"> → </span><span
class="syntactic-cat">[tuple-type-element-list](Types.md#tuple-type-element-list)</span><span
class="optional">`...`{.literal}~opt~</span>

[‌](){#TP40016643-CH38-NoLink_1359} <span class="syntax-def-name">
tuple-type-element-list </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[tuple-type-element](Types.md#tuple-type-element)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[tuple-type-element](Types.md#tuple-type-element)</span>`,`{.literal}<span
class="syntactic-cat">[tuple-type-element-list](Types.md#tuple-type-element-list)</span>
</span>

[‌](){#TP40016643-CH38-NoLink_1360} <span class="syntax-def-name">
tuple-type-element </span> <span class="arrow"> → </span><span
class="alternative"> <span class="optional"><span
class="syntactic-cat">[attributes](Attributes.md#attributes)</span>~opt~</span><span
class="optional">`inout`{.literal}~opt~</span><span
class="syntactic-cat">[type](Types.md#type)</span> </span><span
class="alternative"> <span
class="optional">`inout`{.literal}~opt~</span><span
class="syntactic-cat">[element-name](Types.md#element-name)</span><span
class="syntactic-cat">[type-annotation](Types.md#type-annotation)</span>
</span>

[‌](){#TP40016643-CH38-NoLink_1361} <span class="syntax-def-name">
element-name </span> <span class="arrow"> → </span><span
class="syntactic-cat">[identifier](LexicalStructure.md#identifier)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a function type

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1363} <span class="syntax-def-name">
function-type </span> <span class="arrow"> → </span><span
class="syntactic-cat">[type](Types.md#type)</span><span
class="optional">`throws`{.literal}~opt~</span>`->`{.literal}<span
class="syntactic-cat">[type](Types.md#type)</span>

[‌](){#TP40016643-CH38-NoLink_1364} <span class="syntax-def-name">
function-type </span> <span class="arrow"> → </span><span
class="syntactic-cat">[type](Types.md#type)</span>`rethrows`{.literal}`->`{.literal}<span
class="syntactic-cat">[type](Types.md#type)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of an array type

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1366} <span class="syntax-def-name">
array-type </span> <span class="arrow"> → </span>`[`{.literal}<span
class="syntactic-cat">[type](Types.md#type)</span>`]`{.literal}

</div>

</div>

<div class="syntax-defs">

Grammar of a dictionary type

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1368} <span class="syntax-def-name">
dictionary-type </span> <span class="arrow"> → </span>`[`{.literal}<span
class="syntactic-cat">[type](Types.md#type)</span>`:`{.literal}<span
class="syntactic-cat">[type](Types.md#type)</span>`]`{.literal}

</div>

</div>

<div class="syntax-defs">

Grammar of an optional type

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1370} <span class="syntax-def-name">
optional-type </span> <span class="arrow"> → </span><span
class="syntactic-cat">[type](Types.md#type)</span>`?`{.literal}

</div>

</div>

<div class="syntax-defs">

Grammar of an implicitly unwrapped optional type

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1372} <span class="syntax-def-name">
implicitly-unwrapped-optional-type </span> <span class="arrow"> →
</span><span
class="syntactic-cat">[type](Types.md#type)</span>`!`{.literal}

</div>

</div>

<div class="syntax-defs">

Grammar of a protocol composition type

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1374} <span class="syntax-def-name">
protocol-composition-type </span> <span class="arrow"> →
</span>`protocol`{.literal}`<`{.literal}<span class="optional"><span
class="syntactic-cat">[protocol-identifier-list](Types.md#protocol-identifier-list)</span>~opt~</span>`>`{.literal}

[‌](){#TP40016643-CH38-NoLink_1375} <span class="syntax-def-name">
protocol-identifier-list </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[protocol-identifier](Types.md#protocol-identifier)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[protocol-identifier](Types.md#protocol-identifier)</span>`,`{.literal}<span
class="syntactic-cat">[protocol-identifier-list](Types.md#protocol-identifier-list)</span>
</span>

[‌](){#TP40016643-CH38-NoLink_1376} <span class="syntax-def-name">
protocol-identifier </span> <span class="arrow"> → </span><span
class="syntactic-cat">[type-identifier](Types.md#type-identifier)</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a metatype type

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1378} <span class="syntax-def-name">
metatype-type </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[type](Types.md#type)</span>`.`{.literal}`Type`{.literal}
</span><span class="alternative"> <span
class="syntactic-cat">[type](Types.md#type)</span>`.`{.literal}`Protocol`{.literal}
</span>

</div>

</div>

<div class="syntax-defs">

Grammar of a type inheritance clause

<div class="syntax-defs-group">

[‌](){#TP40016643-CH38-NoLink_1380} <span class="syntax-def-name">
type-inheritance-clause </span> <span class="arrow"> →
</span>`:`{.literal}<span
class="syntactic-cat">[class-requirement](Types.md#class-requirement)</span>`,`{.literal}<span
class="syntactic-cat">[type-inheritance-list](Types.md#type-inheritance-list)</span>

[‌](){#TP40016643-CH38-NoLink_1381} <span class="syntax-def-name">
type-inheritance-clause </span> <span class="arrow"> →
</span>`:`{.literal}<span
class="syntactic-cat">[class-requirement](Types.md#class-requirement)</span>

[‌](){#TP40016643-CH38-NoLink_1382} <span class="syntax-def-name">
type-inheritance-clause </span> <span class="arrow"> →
</span>`:`{.literal}<span
class="syntactic-cat">[type-inheritance-list](Types.md#type-inheritance-list)</span>

[‌](){#TP40016643-CH38-NoLink_1383} <span class="syntax-def-name">
type-inheritance-list </span> <span class="arrow"> → </span><span
class="alternative"> <span
class="syntactic-cat">[type-identifier](Types.md#type-identifier)</span>
</span><span class="alternative"> <span
class="syntactic-cat">[type-identifier](Types.md#type-identifier)</span>`,`{.literal}<span
class="syntactic-cat">[type-inheritance-list](Types.md#type-inheritance-list)</span>
</span>

[‌](){#TP40016643-CH38-NoLink_1384} <span class="syntax-def-name">
class-requirement </span> <span class="arrow"> →
</span>`class`{.literal}

</div>

</div>

</div>

</div>

</div>
