



[‌](){#TP40016643-CH8}[‌](){#TP40016643-CH8-ID105}
Collection Types {#collection-types .chapter-name}
----------------



Swift provides three primary *collection types*, known as arrays, sets, and dictionaries, for storing collections of values. Arrays are ordered collections of values. Sets are unordered collections of unique values. Dictionaries are unordered collections of key-value associations.




![image: ../Art/CollectionTypes\_intro\_2x.png](Art/CollectionTypes_intro_2x.png){width="670" height="237"}



Arrays, sets, and dictionaries in Swift are always clear about the types of values and keys that they can store. This means that you cannot insert a value of the wrong type into a collection by mistake. It also means you can be confident about the type of values you will retrieve from a collection.



Note

Swift’s array, set, and dictionary types are implemented as *generic collections*. For more on generic types and collections, see [Generics](Generics.md).







[‌](){#TP40016643-CH8-ID106}
### Mutability of Collections {#mutability-of-collections .section-name}

If you create an array, a set, or a dictionary, and assign it to a variable, the collection that is created will be *mutable*. This means that you can change (or *mutate*) the collection after it is created by adding, removing, or changing items in the collection. If you assign an array, a set, or a dictionary to a constant, that collection is *immutable*, and its size and contents cannot be changed.



Note

It is good practice to create immutable collections in all cases where the collection does not need to change. Doing so enables the Swift compiler to optimize the performance of the collections you create.







[‌](){#TP40016643-CH8-ID107}
### Arrays {#arrays .section-name}

An *array* stores values of the same type in an ordered list. The same value can appear in an array multiple times at different positions.



Note

Swift’s `Array`{.code-voice} type is bridged to Foundation’s `NSArray`{.code-voice} class.

For more information about using `Array`{.code-voice} with Foundation and Cocoa, see *Using Swift with Cocoa and Objective-C (Swift 2.1)*.





[‌](){#TP40016643-CH8-ID108}
### Array Type Shorthand Syntax {#array-type-shorthand-syntax .section-name}

The type of a Swift array is written in full as `Array`{.code-voice}, where `Element`{.code-voice} is the type of values the array is allowed to store. You can also write the type of an array in shorthand form as `[Element]`{.code-voice}. Although the two forms are functionally identical, the shorthand form is preferred and is used throughout this guide when referring to the type of an array.





[‌](){#TP40016643-CH8-ID500}
### Creating an Empty Array {#creating-an-empty-array .section-name}

You can create an empty array of a certain type using initializer syntax:







1.  `var`{.code-voice} `someInts`{.vc} = \[`Int`{.vc}\]()
2.  `print`{.code-voice}(`"someInts is of type [Int] with `{.s}\\(`someInts`{.vc}.`count`{.vc})` items."`{.s})
3.  `// prints "someInts is of type [Int] with 0 items."`{.code-voice}







Note that the type of the `someInts`{.code-voice} variable is inferred to be `[Int]`{.code-voice} from the type of the initializer.

Alternatively, if the context already provides type information, such as a function argument or an already typed variable or constant, you can create an empty array with an empty array literal, which is written as `[]`{.code-voice} (an empty pair of square brackets):







1.  `someInts`{.code-voice}.`append`{.vc}(`3`{.m})
2.  `// someInts now contains 1 value of type Int`{.code-voice}
3.  `someInts`{.code-voice} = \[\]
4.  `// someInts is now an empty array, but is still of type [Int]`{.code-voice}











[‌](){#TP40016643-CH8-ID501}
### Creating an Array with a Default Value {#creating-an-array-with-a-default-value .section-name}

Swift’s `Array`{.code-voice} type also provides an initializer for creating an array of a certain size with all of its values set to the same default value. You pass this initializer the number of items to be added to the new array (called `count`{.code-voice}) and a default value of the appropriate type (called `repeatedValue`{.code-voice}):







1.  `var`{.code-voice} `threeDoubles`{.vc} = \[`Double`{.vc}\](`count`{.vc}: `3`{.m}, `repeatedValue`{.vc}: `0.0`{.m})
2.  `// threeDoubles is of type [Double], and equals [0.0, 0.0, 0.0]`{.code-voice}











[‌](){#TP40016643-CH8-ID502}
### Creating an Array by Adding Two Arrays Together {#creating-an-array-by-adding-two-arrays-together .section-name}

You can create a new array by adding together two existing arrays with compatible types with the addition operator (`+`{.code-voice}). The new array’s type is inferred from the type of the two arrays you add together:







1.  `var`{.code-voice} `anotherThreeDoubles`{.vc} = \[`Double`{.vc}\](`count`{.vc}: `3`{.m}, `repeatedValue`{.vc}: `2.5`{.m})
2.  `// anotherThreeDoubles is of type [Double], and equals [2.5, 2.5, 2.5]`{.code-voice}
3.  ` `{.code-voice}
4.  `var`{.code-voice} `sixDoubles`{.vc} = `threeDoubles`{.vc} + `anotherThreeDoubles`{.vc}
5.  `// sixDoubles is inferred as [Double], and equals [0.0, 0.0, 0.0, 2.5, 2.5, 2.5]`{.code-voice}











[‌](){#TP40016643-CH8-ID109}
### Creating an Array with an Array Literal {#creating-an-array-with-an-array-literal .section-name}

You can also initialize an array with an *array literal*, which is a shorthand way to write one or more values as an array collection. An array literal is written as a list of values, separated by commas, surrounded by a pair of square brackets:




-   ``` {.code-voice}
    [value 1, value 2, value 3]
    ```



The example below creates an array called `shoppingList`{.code-voice} to store `String`{.code-voice} values:







1.  `var`{.code-voice} `shoppingList`{.vc}: \[`String`{.n}\] = \[`"Eggs"`{.s}, `"Milk"`{.s}\]
2.  `// shoppingList has been initialized with two initial items`{.code-voice}







The `shoppingList`{.code-voice} variable is declared as “an array of string values”, written as `[String]`{.code-voice}. Because this particular array has specified a value type of `String`{.code-voice}, it is allowed to store `String`{.code-voice} values only. Here, the `shoppingList`{.code-voice} array is initialized with two `String`{.code-voice} values (`"Eggs"`{.code-voice} and `"Milk"`{.code-voice}), written within an array literal.



Note

The `shoppingList`{.code-voice} array is declared as a variable (with the `var`{.code-voice} introducer) and not a constant (with the `let`{.code-voice} introducer) because more items are added to the shopping list in the examples below.



In this case, the array literal contains two `String`{.code-voice} values and nothing else. This matches the type of the `shoppingList`{.code-voice} variable’s declaration (an array that can only contain `String`{.code-voice} values), and so the assignment of the array literal is permitted as a way to initialize `shoppingList`{.code-voice} with two initial items.

Thanks to Swift’s type inference, you don’t have to write the type of the array if you’re initializing it with an array literal containing values of the same type. The initialization of `shoppingList`{.code-voice} could have been written in a shorter form instead:







1.  `var`{.code-voice} `shoppingList`{.vc} = \[`"Eggs"`{.s}, `"Milk"`{.s}\]







Because all values in the array literal are of the same type, Swift can infer that `[String]`{.code-voice} is the correct type to use for the `shoppingList`{.code-voice} variable.





[‌](){#TP40016643-CH8-ID110}
### Accessing and Modifying an Array {#accessing-and-modifying-an-array .section-name}

You access and modify an array through its methods and properties, or by using subscript syntax.

To find out the number of items in an array, check its read-only `count`{.code-voice} property:







1.  `print`{.code-voice}(`"The shopping list contains `{.s}\\(`shoppingList`{.vc}.`count`{.vc})` items."`{.s})
2.  `// prints "The shopping list contains 2 items."`{.code-voice}







Use the Boolean `isEmpty`{.code-voice} property as a shortcut for checking whether the `count`{.code-voice} property is equal to `0`{.code-voice}:







1.  `if`{.code-voice} `shoppingList`{.vc}.`isEmpty`{.vc} {
2.  `    print`{.code-voice}(`"The shopping list is empty."`{.s})
3.  `} else`{.code-voice} {
4.  `    print`{.code-voice}(`"The shopping list is not empty."`{.s})
5.  `}`{.code-voice}
6.  `// prints "The shopping list is not empty."`{.code-voice}







You can add a new item to the end of an array by calling the array’s `append(_:)`{.code-voice} method:







1.  `shoppingList`{.code-voice}.`append`{.vc}(`"Flour"`{.s})
2.  `// shoppingList now contains 3 items, and someone is making pancakes`{.code-voice}







Alternatively, append an array of one or more compatible items with the addition assignment operator (`+=`{.code-voice}):







1.  `shoppingList`{.code-voice} += \[`"Baking Powder"`{.s}\]
2.  `// shoppingList now contains 4 items`{.code-voice}
3.  `shoppingList`{.code-voice} += \[`"Chocolate Spread"`{.s}, `"Cheese"`{.s}, `"Butter"`{.s}\]
4.  `// shoppingList now contains 7 items`{.code-voice}







Retrieve a value from the array by using *subscript syntax*, passing the index of the value you want to retrieve within square brackets immediately after the name of the array:







1.  `var`{.code-voice} `firstItem`{.vc} = `shoppingList`{.vc}\[`0`{.m}\]
2.  `// firstItem is equal to "Eggs"`{.code-voice}









Note

The first item in the array has an index of `0`{.code-voice}, not `1`{.code-voice}. Arrays in Swift are always zero-indexed.



You can use subscript syntax to change an existing value at a given index:







1.  `shoppingList`{.code-voice}\[`0`{.m}\] = `"Six eggs"`{.s}
2.  `// the first item in the list is now equal to "Six eggs" rather than "Eggs"`{.code-voice}







You can also use subscript syntax to change a range of values at once, even if the replacement set of values has a different length than the range you are replacing. The following example replaces `"Chocolate Spread"`{.code-voice}, `"Cheese"`{.code-voice}, and `"Butter"`{.code-voice} with `"Bananas"`{.code-voice} and `"Apples"`{.code-voice}:







1.  `shoppingList`{.code-voice}\[`4`{.m}...`6`{.m}\] = \[`"Bananas"`{.s}, `"Apples"`{.s}\]
2.  `// shoppingList now contains 6 items`{.code-voice}









Note

You can’t use subscript syntax to append a new item to the end of an array.



To insert an item into the array at a specified index, call the array’s `insert(_:atIndex:)`{.code-voice} method:







1.  `shoppingList`{.code-voice}.`insert`{.vc}(`"Maple Syrup"`{.s}, `atIndex`{.vc}: `0`{.m})
2.  `// shoppingList now contains 7 items`{.code-voice}
3.  `// "Maple Syrup" is now the first item in the list`{.code-voice}







This call to the `insert(_:atIndex:)`{.code-voice} method inserts a new item with a value of `"Maple Syrup"`{.code-voice} at the very beginning of the shopping list, indicated by an index of `0`{.code-voice}.

Similarly, you remove an item from the array with the `removeAtIndex(_:)`{.code-voice} method. This method removes the item at the specified index and returns the removed item (although you can ignore the returned value if you do not need it):







1.  `let`{.code-voice} `mapleSyrup`{.vc} = `shoppingList`{.vc}.`removeAtIndex`{.vc}(`0`{.m})
2.  `// the item that was at index 0 has just been removed`{.code-voice}
3.  `// shoppingList now contains 6 items, and no Maple Syrup`{.code-voice}
4.  `// the mapleSyrup constant is now equal to the removed "Maple Syrup" string`{.code-voice}









Note

If you try to access or modify a value for an index that is outside of an array’s existing bounds, you will trigger a runtime error. You can check that an index is valid before using it by comparing it to the array’s `count`{.code-voice} property. Except when `count`{.code-voice} is `0`{.code-voice} (meaning the array is empty), the largest valid index in an array will always be `count - 1`{.code-voice}, because arrays are indexed from zero.



Any gaps in an array are closed when an item is removed, and so the value at index `0`{.code-voice} is once again equal to `"Six eggs"`{.code-voice}:







1.  `firstItem`{.code-voice} = `shoppingList`{.vc}\[`0`{.m}\]
2.  `// firstItem is now equal to "Six eggs"`{.code-voice}







If you want to remove the final item from an array, use the `removeLast()`{.code-voice} method rather than the `removeAtIndex(_:)`{.code-voice} method to avoid the need to query the array’s `count`{.code-voice} property. Like the `removeAtIndex(_:)`{.code-voice} method, `removeLast()`{.code-voice} returns the removed item:







1.  `let`{.code-voice} `apples`{.vc} = `shoppingList`{.vc}.`removeLast`{.vc}()
2.  `// the last item in the array has just been removed`{.code-voice}
3.  `// shoppingList now contains 5 items, and no apples`{.code-voice}
4.  `// the apples constant is now equal to the removed "Apples" string`{.code-voice}











[‌](){#TP40016643-CH8-ID111}
### Iterating Over an Array {#iterating-over-an-array .section-name}

You can iterate over the entire set of values in an array with the `for`{.code-voice}-`in`{.code-voice} loop:







1.  `for`{.code-voice} `item`{.vc} `in`{.kt} `shoppingList`{.vc} {
2.  `    print`{.code-voice}(`item`{.vc})
3.  `}`{.code-voice}
4.  `// Six eggs`{.code-voice}
5.  `// Milk`{.code-voice}
6.  `// Flour`{.code-voice}
7.  `// Baking Powder`{.code-voice}
8.  `// Bananas`{.code-voice}







If you need the integer index of each item as well as its value, use the `enumerate()`{.code-voice} method to iterate over the array instead. For each item in the array, the `enumerate()`{.code-voice} method returns a tuple composed of the index and the value for that item. You can decompose the tuple into temporary constants as part of the iteration:







1.  `for`{.code-voice} (`index`{.vc}, `value`{.vc}) `in`{.kt} `shoppingList`{.vc}.`enumerate`{.vc}() {
2.  `    print`{.code-voice}(`"Item `{.s}\\(`index`{.vc} + `1`{.m})`: `{.s}\\(`value`{.vc})`"`{.s})
3.  `}`{.code-voice}
4.  `// Item 1: Six eggs`{.code-voice}
5.  `// Item 2: Milk`{.code-voice}
6.  `// Item 3: Flour`{.code-voice}
7.  `// Item 4: Baking Powder`{.code-voice}
8.  `// Item 5: Bananas`{.code-voice}







For more about the `for`{.code-voice}-`in`{.code-voice} loop, see [For Loops](ControlFlow.md#TP40016643-CH9-ID121).







[‌](){#TP40016643-CH8-ID484}
### Sets {#sets .section-name}

A *set* stores distinct values of the same type in a collection with no defined ordering. You can use a set instead of an array when the order of items is not important, or when you need to ensure that an item only appears once.



Note

Swift’s `Set`{.code-voice} type is bridged to Foundation’s `NSSet`{.code-voice} class.

For more information about using `Set`{.code-voice} with Foundation and Cocoa, see *Using Swift with Cocoa and Objective-C (Swift 2.1)*.





[‌](){#TP40016643-CH8-ID493}
### Hash Values for Set Types {#hash-values-for-set-types .section-name}

A type must be *hashable* in order to be stored in a set—that is, the type must provide a way to compute a *hash value* for itself. A hash value is an `Int`{.code-voice} value that is the same for all objects that compare equally, such that if `a == b`{.code-voice}, it follows that `a.hashValue == b.hashValue`{.code-voice}.

All of Swift’s basic types (such as `String`{.code-voice}, `Int`{.code-voice}, `Double`{.code-voice}, and `Bool`{.code-voice}) are hashable by default, and can be used as set value types or dictionary key types. Enumeration case values without associated values (as described in [Enumerations](Enumerations.md)) are also hashable by default.



Note

You can use your own custom types as set value types or dictionary key types by making them conform to the `Hashable`{.code-voice} protocol from Swift’s standard library. Types that conform to the `Hashable`{.code-voice} protocol must provide a gettable `Int`{.code-voice} property called `hashValue`{.code-voice}. The value returned by a type’s `hashValue`{.code-voice} property is not required to be the same across different executions of the same program, or in different programs.

Because the `Hashable`{.code-voice} protocol conforms to `Equatable`{.code-voice}, conforming types must also provide an implementation of the “is equal” operator (`==`{.code-voice}). The `Equatable`{.code-voice} protocol requires any conforming implementation of `==`{.code-voice} to be an equivalence relation. That is, an implementation of `==`{.code-voice} must satisfy the following three conditions, for all values `a`{.code-voice}, `b`{.code-voice}, and `c`{.code-voice}:

-   `a == a`{.code-voice} (Reflexivity)

-   `a == b`{.code-voice} implies `b == a`{.code-voice} (Symmetry)

-   `a == b && b == c`{.code-voice} implies `a == c`{.code-voice} (Transitivity)

For more information about conforming to protocols, see [Protocols](Protocols.md).







[‌](){#TP40016643-CH8-ID485}
### Set Type Syntax {#set-type-syntax .section-name}

The type of a Swift set is written as `Set`{.code-voice}, where `Element`{.code-voice} is the type that the set is allowed to store. Unlike arrays, sets do not have an equivalent shorthand form.





[‌](){#TP40016643-CH8-ID503}
### Creating and Initializing an Empty Set {#creating-and-initializing-an-empty-set .section-name}

You can create an empty set of a certain type using initializer syntax:







1.  `var`{.code-voice} `letters`{.vc} = `Set`{.vc}&lt;`Character`{.n}&gt;()
2.  `print`{.code-voice}(`"letters is of type Set with `{.s}\\(`letters`{.vc}.`count`{.vc})` items."`{.s})
3.  `// prints "letters is of type Set with 0 items."`{.code-voice}









Note

The type of the `letters`{.code-voice} variable is inferred to be `Set`{.code-voice}, from the type of the initializer.



Alternatively, if the context already provides type information, such as a function argument or an already typed variable or constant, you can create an empty set with an empty array literal:







1.  `letters`{.code-voice}.`insert`{.vc}(`"a"`{.s})
2.  `// letters now contains 1 value of type Character`{.code-voice}
3.  `letters`{.code-voice} = \[\]
4.  `// letters is now an empty set, but is still of type Set`{.code-voice}











[‌](){#TP40016643-CH8-ID504}
### Creating a Set with an Array Literal {#creating-a-set-with-an-array-literal .section-name}

You can also initialize a set with an array literal, as a shorthand way to write one or more values as a set collection.

The example below creates a set called `favoriteGenres`{.code-voice} to store `String`{.code-voice} values:







1.  `var`{.code-voice} `favoriteGenres`{.vc}: `Set`{.n}&lt;`String`{.n}&gt; = \[`"Rock"`{.s}, `"Classical"`{.s}, `"Hip hop"`{.s}\]
2.  `// favoriteGenres has been initialized with three initial items`{.code-voice}







The `favoriteGenres`{.code-voice} variable is declared as “a set of `String`{.code-voice} values”, written as `Set`{.code-voice}. Because this particular set has specified a value type of `String`{.code-voice}, it is *only* allowed to store `String`{.code-voice} values. Here, the `favoriteGenres`{.code-voice} set is initialized with three `String`{.code-voice} values (`"Rock"`{.code-voice}, `"Classical"`{.code-voice}, and `"Hip hop"`{.code-voice}), written within an array literal.



Note

The `favoriteGenres`{.code-voice} set is declared as a variable (with the `var`{.code-voice} introducer) and not a constant (with the `let`{.code-voice} introducer) because items are added and removed in the examples below.



A set type cannot be inferred from an array literal alone, so the type `Set`{.code-voice} must be explicitly declared. However, because of Swift’s type inference, you don’t have to write the type of the set if you’re initializing it with an array literal containing values of the same type. The initialization of `favoriteGenres`{.code-voice} could have been written in a shorter form instead:







1.  `var`{.code-voice} `favoriteGenres`{.vc}: `Set`{.n} = \[`"Rock"`{.s}, `"Classical"`{.s}, `"Hip hop"`{.s}\]







Because all values in the array literal are of the same type, Swift can infer that `Set`{.code-voice} is the correct type to use for the `favoriteGenres`{.code-voice} variable.





[‌](){#TP40016643-CH8-ID488}
### Accessing and Modifying a Set {#accessing-and-modifying-a-set .section-name}

You access and modify a set through its methods and properties.

To find out the number of items in a set, check its read-only `count`{.code-voice} property:







1.  `print`{.code-voice}(`"I have `{.s}\\(`favoriteGenres`{.vc}.`count`{.vc})` favorite music genres."`{.s})
2.  `// prints "I have 3 favorite music genres."`{.code-voice}







Use the Boolean `isEmpty`{.code-voice} property as a shortcut for checking whether the `count`{.code-voice} property is equal to `0`{.code-voice}:







1.  `if`{.code-voice} `favoriteGenres`{.vc}.`isEmpty`{.vc} {
2.  `    print`{.code-voice}(`"As far as music goes, I'm not picky."`{.s})
3.  `} else`{.code-voice} {
4.  `    print`{.code-voice}(`"I have particular music preferences."`{.s})
5.  `}`{.code-voice}
6.  `// prints "I have particular music preferences."`{.code-voice}







You can add a new item into a set by calling the set’s `insert(_:)`{.code-voice} method:







1.  `favoriteGenres`{.code-voice}.`insert`{.vc}(`"Jazz"`{.s})
2.  `// favoriteGenres now contains 4 items`{.code-voice}







You can remove an item from a set by calling the set’s `remove(_:)`{.code-voice} method, which removes the item if it’s a member of the set, and returns the removed value, or returns `nil`{.code-voice} if the set did not contain it. Alternatively, all items in a set can be removed with its `removeAll()`{.code-voice} method.







1.  `if`{.code-voice} `let`{.kt} `removedGenre`{.vc} = `favoriteGenres`{.vc}.`remove`{.vc}(`"Rock"`{.s}) {
2.  `    print`{.code-voice}(`"`{.s}\\(`removedGenre`{.vc})`? I'm over it."`{.s})
3.  `} else`{.code-voice} {
4.  `    print`{.code-voice}(`"I never much cared for that."`{.s})
5.  `}`{.code-voice}
6.  `// prints "Rock? I'm over it."`{.code-voice}







To check whether a set contains a particular item, use the `contains(_:)`{.code-voice} method.







1.  `if`{.code-voice} `favoriteGenres`{.vc}.`contains`{.vc}(`"Funk"`{.s}) {
2.  `    print`{.code-voice}(`"I get up on the good foot."`{.s})
3.  `} else`{.code-voice} {
4.  `    print`{.code-voice}(`"It's too funky in here."`{.s})
5.  `}`{.code-voice}
6.  `// prints "It's too funky in here."`{.code-voice}











[‌](){#TP40016643-CH8-ID489}
### Iterating Over a Set {#iterating-over-a-set .section-name}

You can iterate over the values in a set with a `for`{.code-voice}-`in`{.code-voice} loop.







1.  `for`{.code-voice} `genre`{.vc} `in`{.kt} `favoriteGenres`{.vc} {
2.  `    print`{.code-voice}(`"`{.s}\\(`genre`{.vc})`"`{.s})
3.  `}`{.code-voice}
4.  `// Classical`{.code-voice}
5.  `// Jazz`{.code-voice}
6.  `// Hip hop`{.code-voice}







For more about the `for`{.code-voice}-`in`{.code-voice} loop, see [For Loops](ControlFlow.md#TP40016643-CH9-ID121).

Swift’s `Set`{.code-voice} type does not have a defined ordering. To iterate over the values of a set in a specific order, use the `sort()`{.code-voice} method, which returns the set’s elements as an array sorted using the `<`{.code-voice} operator.







1.  `for`{.code-voice} `genre`{.vc} `in`{.kt} `favoriteGenres`{.vc}.`sort`{.vc}() {
2.  `    print`{.code-voice}(`"`{.s}\\(`genre`{.vc})`"`{.s})
3.  `}`{.code-voice}
4.  `// Classical`{.code-voice}
5.  `// Hip hop`{.code-voice}
6.  `// Jazz`{.code-voice}













[‌](){#TP40016643-CH8-ID490}
### Performing Set Operations {#performing-set-operations .section-name}

You can efficiently perform fundamental set operations, such as combining two sets together, determining which values two sets have in common, or determining whether two sets contain all, some, or none of the same values.



[‌](){#TP40016643-CH8-ID505}
### Fundamental Set Operations {#fundamental-set-operations .section-name}

The illustration below depicts two sets–`a`{.code-voice} and `b`{.code-voice}– with the results of various set operations represented by the shaded regions.




![image: ../Art/setVennDiagram\_2x.png](Art/setVennDiagram_2x.png){width="561" height="425"}



-   Use the `intersect(_:)`{.code-voice} method to create a new set with only the values common to both sets.

-   Use the `exclusiveOr(_:)`{.code-voice} method to create a new set with values in either set, but not both.

-   Use the `union(_:)`{.code-voice} method to create a new set with all of the values in both sets.

-   Use the `subtract(_:)`{.code-voice} method to create a new set with values not in the specified set.







1.  `let`{.code-voice} `oddDigits`{.vc}: `Set`{.n} = \[`1`{.m}, `3`{.m}, `5`{.m}, `7`{.m}, `9`{.m}\]
2.  `let`{.code-voice} `evenDigits`{.vc}: `Set`{.n} = \[`0`{.m}, `2`{.m}, `4`{.m}, `6`{.m}, `8`{.m}\]
3.  `let`{.code-voice} `singleDigitPrimeNumbers`{.vc}: `Set`{.n} = \[`2`{.m}, `3`{.m}, `5`{.m}, `7`{.m}\]
4.  ` `{.code-voice}
5.  `oddDigits`{.code-voice}.`union`{.vc}(`evenDigits`{.vc}).`sort`{.vc}()
6.  `// [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]`{.code-voice}
7.  `oddDigits`{.code-voice}.`intersect`{.vc}(`evenDigits`{.vc}).`sort`{.vc}()
8.  `// []`{.code-voice}
9.  `oddDigits`{.code-voice}.`subtract`{.vc}(`singleDigitPrimeNumbers`{.vc}).`sort`{.vc}()
10. `// [1, 9]`{.code-voice}
11. `oddDigits`{.code-voice}.`exclusiveOr`{.vc}(`singleDigitPrimeNumbers`{.vc}).`sort`{.vc}()
12. `// [1, 2, 9]`{.code-voice}











[‌](){#TP40016643-CH8-ID506}
### Set Membership and Equality {#set-membership-and-equality .section-name}

The illustration below depicts three sets–`a`{.code-voice}, `b`{.code-voice} and `c`{.code-voice}– with overlapping regions representing elements shared among sets. Set `a`{.code-voice} is a *superset* of set `b`{.code-voice}, because `a`{.code-voice} contains all elements in `b`{.code-voice}. Conversely, set `b`{.code-voice} is a *subset* of set `a`{.code-voice}, because all elements in `b`{.code-voice} are also contained by `a`{.code-voice}. Set `b`{.code-voice} and set `c`{.code-voice} are *disjoint* with one another, because they share no elements in common.




![image: ../Art/setEulerDiagram\_2x.png](Art/setEulerDiagram_2x.png){width="551" height="323"}



-   Use the “is equal” operator (`==`{.code-voice}) to determine whether two sets contain all of the same values.

-   Use the `isSubsetOf(_:)`{.code-voice} method to determine whether all of the values of a set are contained in the specified set.

-   Use the `isSupersetOf(_:)`{.code-voice} method to determine whether a set contains all of the values in a specified set.

-   Use the `isStrictSubsetOf(_:)`{.code-voice} or `isStrictSupersetOf(_:)`{.code-voice} methods to determine whether a set is a subset or superset, but not equal to, a specified set.

-   Use the `isDisjointWith(_:)`{.code-voice} method to determine whether two sets have any values in common.







1.  `let`{.code-voice} `houseAnimals`{.vc}: `Set`{.n} = \[`"🐶"`{.s}, `"🐱"`{.s}\]
2.  `let`{.code-voice} `farmAnimals`{.vc}: `Set`{.n} = \[`"🐮"`{.s}, `"🐔"`{.s}, `"🐑"`{.s}, `"🐶"`{.s}, `"🐱"`{.s}\]
3.  `let`{.code-voice} `cityAnimals`{.vc}: `Set`{.n} = \[`"🐦"`{.s}, `"🐭"`{.s}\]
4.  ` `{.code-voice}
5.  `houseAnimals`{.code-voice}.`isSubsetOf`{.vc}(`farmAnimals`{.vc})
6.  `// true`{.code-voice}
7.  `farmAnimals`{.code-voice}.`isSupersetOf`{.vc}(`houseAnimals`{.vc})
8.  `// true`{.code-voice}
9.  `farmAnimals`{.code-voice}.`isDisjointWith`{.vc}(`cityAnimals`{.vc})
10. `// true`{.code-voice}













[‌](){#TP40016643-CH8-ID113}
### Dictionaries {#dictionaries .section-name}

A *dictionary* stores associations between keys of the same type and values of the same type in a collection with no defined ordering. Each value is associated with a unique *key*, which acts as an identifier for that value within the dictionary. Unlike items in an array, items in a dictionary do not have a specified order. You use a dictionary when you need to look up values based on their identifier, in much the same way that a real-world dictionary is used to look up the definition for a particular word.



Note

Swift’s `Dictionary`{.code-voice} type is bridged to Foundation’s `NSDictionary`{.code-voice} class.

For more information about using `Dictionary`{.code-voice} with Foundation and Cocoa, see *Using Swift with Cocoa and Objective-C (Swift 2.1)*.





[‌](){#TP40016643-CH8-ID114}
### Dictionary Type Shorthand Syntax {#dictionary-type-shorthand-syntax .section-name}

The type of a Swift dictionary is written in full as `Dictionary`{.code-voice}, where `Key`{.code-voice} is the type of value that can be used as a dictionary key, and `Value`{.code-voice} is the type of value that the dictionary stores for those keys.



Note

A dictionary `Key`{.code-voice} type must conform to the `Hashable`{.code-voice} protocol, like a set’s value type.



You can also write the type of a dictionary in shorthand form as `[Key: Value]`{.code-voice}. Although the two forms are functionally identical, the shorthand form is preferred and is used throughout this guide when referring to the type of a dictionary.





[‌](){#TP40016643-CH8-ID118}
### Creating an Empty Dictionary {#creating-an-empty-dictionary .section-name}

As with arrays, you can create an empty `Dictionary`{.code-voice} of a certain type by using initializer syntax:







1.  `var`{.code-voice} `namesOfIntegers`{.vc} = \[`Int`{.vc}: `String`{.vc}\]()
2.  `// namesOfIntegers is an empty [Int: String] dictionary`{.code-voice}







This example creates an empty dictionary of type `[Int: String]`{.code-voice} to store human-readable names of integer values. Its keys are of type `Int`{.code-voice}, and its values are of type `String`{.code-voice}.

If the context already provides type information, you can create an empty dictionary with an empty dictionary literal, which is written as `[:]`{.code-voice} (a colon inside a pair of square brackets):







1.  `namesOfIntegers`{.code-voice}\[`16`{.m}\] = `"sixteen"`{.s}
2.  `// namesOfIntegers now contains 1 key-value pair`{.code-voice}
3.  `namesOfIntegers`{.code-voice} = \[:\]
4.  `// namesOfIntegers is once again an empty dictionary of type [Int: String]`{.code-voice}











[‌](){#TP40016643-CH8-ID507}
### Creating a Dictionary with a Dictionary Literal {#creating-a-dictionary-with-a-dictionary-literal .section-name}

You can also initialize a dictionary with a *dictionary literal*, which has a similar syntax to the array literal seen earlier. A dictionary literal is a shorthand way to write one or more key-value pairs as a `Dictionary`{.code-voice} collection.

A *key-value pair* is a combination of a key and a value. In a dictionary literal, the key and value in each key-value pair are separated by a colon. The key-value pairs are written as a list, separated by commas, surrounded by a pair of square brackets:




-   ``` {.code-voice}
    [key 1: value 1, key 2: value 2, key 3: value 3]
    ```



The example below creates a dictionary to store the names of international airports. In this dictionary, the keys are three-letter International Air Transport Association codes, and the values are airport names:







1.  `var`{.code-voice} `airports`{.vc}: \[`String`{.n}: `String`{.n}\] = \[`"YYZ"`{.s}: `"Toronto Pearson"`{.s}, `"DUB"`{.s}: `"Dublin"`{.s}\]







The `airports`{.code-voice} dictionary is declared as having a type of `[String: String]`{.code-voice}, which means “a `Dictionary`{.code-voice} whose keys are of type `String`{.code-voice}, and whose values are also of type `String`{.code-voice}”.



Note

The `airports`{.code-voice} dictionary is declared as a variable (with the `var`{.code-voice} introducer), and not a constant (with the `let`{.code-voice} introducer), because more airports are added to the dictionary in the examples below.



The `airports`{.code-voice} dictionary is initialized with a dictionary literal containing two key-value pairs. The first pair has a key of `"YYZ"`{.code-voice} and a value of `"Toronto Pearson"`{.code-voice}. The second pair has a key of `"DUB"`{.code-voice} and a value of `"Dublin"`{.code-voice}.

This dictionary literal contains two `String: String`{.code-voice} pairs. This key-value type matches the type of the `airports`{.code-voice} variable declaration (a dictionary with only `String`{.code-voice} keys, and only `String`{.code-voice} values), and so the assignment of the dictionary literal is permitted as a way to initialize the `airports`{.code-voice} dictionary with two initial items.

As with arrays, you don’t have to write the type of the dictionary if you’re initializing it with a dictionary literal whose keys and values have consistent types. The initialization of `airports`{.code-voice} could have been written in a shorter form instead:







1.  `var`{.code-voice} `airports`{.vc} = \[`"YYZ"`{.s}: `"Toronto Pearson"`{.s}, `"DUB"`{.s}: `"Dublin"`{.s}\]







Because all keys in the literal are of the same type as each other, and likewise all values are of the same type as each other, Swift can infer that `[String: String]`{.code-voice} is the correct type to use for the `airports`{.code-voice} dictionary.





[‌](){#TP40016643-CH8-ID116}
### Accessing and Modifying a Dictionary {#accessing-and-modifying-a-dictionary .section-name}

You access and modify a dictionary through its methods and properties, or by using subscript syntax.

As with an array, you find out the number of items in a `Dictionary`{.code-voice} by checking its read-only `count`{.code-voice} property:







1.  `print`{.code-voice}(`"The airports dictionary contains `{.s}\\(`airports`{.vc}.`count`{.vc})` items."`{.s})
2.  `// prints "The airports dictionary contains 2 items."`{.code-voice}







Use the Boolean `isEmpty`{.code-voice} property as a shortcut for checking whether the `count`{.code-voice} property is equal to `0`{.code-voice}:







1.  `if`{.code-voice} `airports`{.vc}.`isEmpty`{.vc} {
2.  `    print`{.code-voice}(`"The airports dictionary is empty."`{.s})
3.  `} else`{.code-voice} {
4.  `    print`{.code-voice}(`"The airports dictionary is not empty."`{.s})
5.  `}`{.code-voice}
6.  `// prints "The airports dictionary is not empty."`{.code-voice}







You can add a new item to a dictionary with subscript syntax. Use a new key of the appropriate type as the subscript index, and assign a new value of the appropriate type:







1.  `airports`{.code-voice}\[`"LHR"`{.s}\] = `"London"`{.s}
2.  `// the airports dictionary now contains 3 items`{.code-voice}







You can also use subscript syntax to change the value associated with a particular key:







1.  `airports`{.code-voice}\[`"LHR"`{.s}\] = `"London Heathrow"`{.s}
2.  `// the value for "LHR" has been changed to "London Heathrow"`{.code-voice}







As an alternative to subscripting, use a dictionary’s `updateValue(_:forKey:)`{.code-voice} method to set or update the value for a particular key. Like the subscript examples above, the `updateValue(_:forKey:)`{.code-voice} method sets a value for a key if none exists, or updates the value if that key already exists. Unlike a subscript, however, the `updateValue(_:forKey:)`{.code-voice} method returns the *old* value after performing an update. This enables you to check whether or not an update took place.

The `updateValue(_:forKey:)`{.code-voice} method returns an optional value of the dictionary’s value type. For a dictionary that stores `String`{.code-voice} values, for example, the method returns a value of type `String?`{.code-voice}, or “optional `String`{.code-voice}”. This optional value contains the old value for that key if one existed before the update, or `nil`{.code-voice} if no value existed:







1.  `if`{.code-voice} `let`{.kt} `oldValue`{.vc} = `airports`{.vc}.`updateValue`{.vc}(`"Dublin Airport"`{.s}, `forKey`{.vc}: `"DUB"`{.s}) {
2.  `    print`{.code-voice}(`"The old value for DUB was `{.s}\\(`oldValue`{.vc})`."`{.s})
3.  `}`{.code-voice}
4.  `// prints "The old value for DUB was Dublin."`{.code-voice}







You can also use subscript syntax to retrieve a value from the dictionary for a particular key. Because it is possible to request a key for which no value exists, a dictionary’s subscript returns an optional value of the dictionary’s value type. If the dictionary contains a value for the requested key, the subscript returns an optional value containing the existing value for that key. Otherwise, the subscript returns `nil`{.code-voice}:







1.  `if`{.code-voice} `let`{.kt} `airportName`{.vc} = `airports`{.vc}\[`"DUB"`{.s}\] {
2.  `    print`{.code-voice}(`"The name of the airport is `{.s}\\(`airportName`{.vc})`."`{.s})
3.  `} else`{.code-voice} {
4.  `    print`{.code-voice}(`"That airport is not in the airports dictionary."`{.s})
5.  `}`{.code-voice}
6.  `// prints "The name of the airport is Dublin Airport."`{.code-voice}







You can use subscript syntax to remove a key-value pair from a dictionary by assigning a value of `nil`{.code-voice} for that key:







1.  `airports`{.code-voice}\[`"APL"`{.s}\] = `"Apple International"`{.s}
2.  `// "Apple International" is not the real airport for APL, so delete it`{.code-voice}
3.  `airports`{.code-voice}\[`"APL"`{.s}\] = `nil`{.kt}
4.  `// APL has now been removed from the dictionary`{.code-voice}







Alternatively, remove a key-value pair from a dictionary with the `removeValueForKey(_:)`{.code-voice} method. This method removes the key-value pair if it exists and returns the removed value, or returns `nil`{.code-voice} if no value existed:







1.  `if`{.code-voice} `let`{.kt} `removedValue`{.vc} = `airports`{.vc}.`removeValueForKey`{.vc}(`"DUB"`{.s}) {
2.  `    print`{.code-voice}(`"The removed airport's name is `{.s}\\(`removedValue`{.vc})`."`{.s})
3.  `} else`{.code-voice} {
4.  `    print`{.code-voice}(`"The airports dictionary does not contain a value for DUB."`{.s})
5.  `}`{.code-voice}
6.  `// prints "The removed airport's name is Dublin Airport."`{.code-voice}











[‌](){#TP40016643-CH8-ID117}
### Iterating Over a Dictionary {#iterating-over-a-dictionary .section-name}

You can iterate over the key-value pairs in a dictionary with a `for`{.code-voice}-`in`{.code-voice} loop. Each item in the dictionary is returned as a `(key, value)`{.code-voice} tuple, and you can decompose the tuple’s members into temporary constants as part of the iteration:







1.  `for`{.code-voice} (`airportCode`{.vc}, `airportName`{.vc}) `in`{.kt} `airports`{.vc} {
2.  `    print`{.code-voice}(`"`{.s}\\(`airportCode`{.vc})`: `{.s}\\(`airportName`{.vc})`"`{.s})
3.  `}`{.code-voice}
4.  `// YYZ: Toronto Pearson`{.code-voice}
5.  `// LHR: London Heathrow`{.code-voice}







For more about the `for`{.code-voice}-`in`{.code-voice} loop, see [For Loops](ControlFlow.md#TP40016643-CH9-ID121).

You can also retrieve an iterable collection of a dictionary’s keys or values by accessing its `keys`{.code-voice} and `values`{.code-voice} properties:







1.  `for`{.code-voice} `airportCode`{.vc} `in`{.kt} `airports`{.vc}.`keys`{.vc} {
2.  `    print`{.code-voice}(`"Airport code: `{.s}\\(`airportCode`{.vc})`"`{.s})
3.  `}`{.code-voice}
4.  `// Airport code: YYZ`{.code-voice}
5.  `// Airport code: LHR`{.code-voice}
6.  ` `{.code-voice}
7.  `for`{.code-voice} `airportName`{.vc} `in`{.kt} `airports`{.vc}.`values`{.vc} {
8.  `    print`{.code-voice}(`"Airport name: `{.s}\\(`airportName`{.vc})`"`{.s})
9.  `}`{.code-voice}
10. `// Airport name: Toronto Pearson`{.code-voice}
11. `// Airport name: London Heathrow`{.code-voice}







If you need to use a dictionary’s keys or values with an API that takes an `Array`{.code-voice} instance, initialize a new array with the `keys`{.code-voice} or `values`{.code-voice} property:







1.  `let`{.code-voice} `airportCodes`{.vc} = \[`String`{.vc}\](`airports`{.vc}.`keys`{.vc})
2.  `// airportCodes is ["YYZ", "LHR"]`{.code-voice}
3.  ` `{.code-voice}
4.  `let`{.code-voice} `airportNames`{.vc} = \[`String`{.vc}\](`airports`{.vc}.`values`{.vc})
5.  `// airportNames is ["Toronto Pearson", "London Heathrow"]`{.code-voice}







Swift’s `Dictionary`{.code-voice} type does not have a defined ordering. To iterate over the keys or values of a dictionary in a specific order, use the `sort()`{.code-voice} method on its `keys`{.code-voice} or `values`{.code-voice} property.








