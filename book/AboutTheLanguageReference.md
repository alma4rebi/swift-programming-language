<div class="content-wrapper">

<div id="chapter_container" class="conceptualwithtasks">

[‌](){#TP40016643-CH29}[‌](){#TP40016643-CH29-ID345}
About the Language Reference {#about-the-language-reference .chapter-name}
----------------------------

<div class="section section">

This part of the book describes the formal grammar of the Swift
programming language. The grammar described here is intended to help you
understand the language in more detail, rather than to allow you to
directly implement a parser or compiler.

The Swift language is relatively small, because many common types,
functions, and operators that appear virtually everywhere in Swift code
are actually defined in the Swift standard library. Although these
types, functions, and operators are not part of the Swift language
itself, they are used extensively in the discussions and code examples
in this part of the book.

</div>

<div class="section section">

[‌](){#TP40016643-CH29-ID346}
### How to Read the Grammar {#how-to-read-the-grammar .section-name}

The notation used to describe the formal grammar of the Swift
programming language follows a few conventions:

-   An arrow (→) is used to mark grammar productions and can be read as
    “can consist of.”

-   Syntactic categories are indicated by *italic* text and appear on
    both sides of a grammar production rule.

-   Literal words and punctuation are indicated by boldface
    `constant width`{.code-voice} text and appear only on the right-hand
    side of a grammar production rule.

-   Alternative grammar productions are separated by vertical bars (|).
    When alternative productions are too long to read easily, they are
    broken into multiple grammar production rules on new lines.

-   In a few cases, regular font text is used to describe the right-hand
    side of a grammar production rule.

-   Optional syntactic categories and literals are marked by a trailing
    subscript, *opt*.

As an example, the grammar of a getter-setter block is defined as
follows:

<div class="syntax-defs">

Grammar of a getter-setter block

<div class="syntax-defs-group">

[‌](){#TP40016643-CH29-NoLink_213} <span class="syntax-def-name">
getter-setter-block </span> <span class="arrow"> → </span><span
class="alternative"> `{`{.literal}<span
class="syntactic-cat">[getter-clause](Declarations.md#getter-clause)</span><span
class="optional"><span
class="syntactic-cat">[setter-clause](Declarations.md#setter-clause)</span>~opt~</span>`}`{.literal}
</span><span class="alternative"> `{`{.literal}<span
class="syntactic-cat">[setter-clause](Declarations.md#setter-clause)</span><span
class="syntactic-cat">[getter-clause](Declarations.md#getter-clause)</span>`}`{.literal}
</span>

</div>

</div>

This definition indicates that a getter-setter block can consist of a
getter clause followed by an optional setter clause, enclosed in braces,
*or* a setter clause followed by a getter clause, enclosed in braces.
The grammar production above is equivalent to the following two
productions, where the alternatives are spelled out explicitly:

<div class="syntax-defs">

Grammar of a getter-setter block

<div class="syntax-defs-group">

[‌](){#TP40016643-CH29-NoLink_215} <span class="syntax-def-name">
getter-setter-block </span> <span class="arrow"> →
</span>`{`{.literal}<span
class="syntactic-cat">[getter-clause](Declarations.md#getter-clause)</span><span
class="optional"><span
class="syntactic-cat">[setter-clause](Declarations.md#setter-clause)</span>~opt~</span>`}`{.literal}

[‌](){#TP40016643-CH29-NoLink_216} <span class="syntax-def-name">
getter-setter-block </span> <span class="arrow"> →
</span>`{`{.literal}<span
class="syntactic-cat">[setter-clause](Declarations.md#setter-clause)</span><span
class="syntactic-cat">[getter-clause](Declarations.md#getter-clause)</span>`}`{.literal}

</div>

</div>

</div>

</div>

</div>
