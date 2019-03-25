---
layout:  resource
name:    posts
title:   "Midterm Review"
---
## Concepts

- array name vs. memory address
- array size declaration explicit, implicit
- multi dim arrays as arguments
- code snippet with array indexes ("what will this code display")
- advantage of linear search
- binary search algorithm
- pointer variable declaration syntax
- pointers vs. array names
- comparing pointers
- memory address vs. variable content ("what will this code display")
- `*` and `&` in context of addresses and pointers
- code snippets - arrays and pointers
- isdigit
- strcpy arguments
- strstr
- atol
- C-string dimensions
- strncpy
- structures - assignments to members syntax
- primitive data types
- passing a structure to function
- structure - dereferencing
- enum
- parts of structure - tag, members

## TO DO

Creating a study guide is more useful than having one! By going through each
item in the list of concepts above and writing notes that pertain to that topic,
you are cementing those concepts in your mind. You'll also naturally focus on
areas where your knowledge is more shaky.

What I have prepared for you in this document is a starting point. The topics
that are more difficult from a conceptual level are briefly explained, but the
practice is left up to you. Below is a list of things you can do to practice
each topic. Most of these things will 

### array name vs. memory address
- refer to the pointers.cpp file
  - before you execute the file, ask yourself what the results of certain
    lines will be
  - look at lines where the memory address is printed to the console
  - will that memory address be the same or different than other addresses
    printed at various points in the code?
- in a new c++ test file
  - create an array, populate it with varibles
  - print each item in the array
  - print the memory address of array
  - print the memory address of each element in the array

### array size declaration explicit, implicit
- how can you declare an array and initialize it without explicityly stating
  how many items are in the array?
- you do this in `a1main.cpp`

### multi dim arrays as arguments
- a multi dimensional array is an array of arrays
  - this is the simplest definition
  - it can also be an array of arrays of arrays of arrays... 
- create a multi dimensional array, pass it as an argument to a function that
  will do something to it
  - printing out each element in a readable manner would be a fine thing to do
    to the array

### code snippet with array indexes ("what will this code display")
- remember that arrays start at index `0`

### advantage of linear search
- binary search is faster than linear search
- binary search requires the array being searched to be sorted
- therefore, linear search is better if your list is not sorted or if keeping
  your list sorted would be too much work

### binary search algorithm
- see section "Binary Search"

### pointer variable declaration syntax
- look over your homework assignments for examples of proper syntax
- practice by making pointers, make to match every `new` with a `delete`
  - do this in a file called `pointerPractice.cpp`
    - I will reference this in subsequent bullet points
  - make arrays with pointers
  - make primitive data types with pointers
  - make a struct and instantiate some variables typed to that struct with
    pointers
      - this would also double as practice with struct syntax
- working with C-strings would be good practice for this
  - Get two birds with one stone!

### pointers vs. array names
- see bullet points under previous concept

### comparing pointers
- using the `pointerPractice.cpp` file, write some comparisons that
  - use the dereference operator `*` to compare pointer values
  - compare the memory address that a pointer holds
  - compare the memory address that a points is located at
  - make sure that you can correctly identify what the code will output for
    each of the above bullet points
    - Practice with one "this should be false" and one "this should be true"
      example for each!

### memory address vs. variable content ("what will this code display")
- see the previous concept "comparing pointers"

### * and & in context of addresses and pointers
- see the previous concept "comparing pointers"
- use both the dereference operator (`*`) and the address operator (`&`)
  - Don't know when to use them? Sprinkle them across all those test
    comparisons you made! Ask yourself what the output will be after you
    change some code but before you run it.

### code snippets - arrays and pointers
- make arrays with and without the use of pointers

### isdigit
- see this [link](http://www.cplusplus.com/reference/cctype/isdigit/)
  - note that this example uses `atoi`
  - modify this to use `atol` to practice with that concept
- make a program that asks the user for a number
- use `cin` to get the number, but store it as a character array
- convert the value you got from cin to a number (`int` or something)
- do some math to that number (whatever you want)
- output the result

### strcpy arguments
- See the "C-Strings" section

### strstr
- See the "C-Strings" section

### atol
- see this [link](http://www.cplusplus.com/reference/cstdlib/atol/)
- refer to the "isdigit" concept above

### C-string dimensions
- See the "C-Strings" section

### strncpy
- See the "C-Strings" section

### structures - assignments to members syntax
- refer to the "pointer variable declaration syntax" concept above

### primitive data types
- check out this [explanation](https://www.geeksforgeeks.org/c-data-types/)
- what are the primitive data types?
- what is the difference between a primitive data type and an object?
- write some code that declares and instantiates several primitive data types
- write some code that declares and instantiates several objects

### passing a structure to function
- look at your `a4main.cpp` file for an example of this
- practice by making some functions in the `pointerPractice.cpp` file

### structure - dereferencing
- see the "memory address vs. variable content" concept above
  - use a structure where you were using another type to practice this

### enum
- enums are basically just constant (`const`) variables
- the explanation from [this useful but initimidatingly informative site](https://en.cppreference.com/w/cpp/language/enum)
  is "an enumeration is a distinct type whose value is restricted to a range
  of values, which may include several explicitly named constants
  ("enumerators"). The values of the constants are values of an integral type
  known as the underlying type of the enumeration. "
- Enums would be useful for `a4main.cpp` - can you figure out where?

### parts of structure - tag, members
- this [stackoverflow post](https://stackoverflow.com/questions/44180120/what-is-the-use-of-struct-tag-name-in-c-programming) explains it all
- practice by
  - creating some structs with a tag
  - creating some structs without a tag
  - creating a struct and then modifying the members

## C-Strings

These four concepts above relate to C Strings
- `strcpy` arguments
  - copies a char array (c-string) from one place to another
  - see [this link](http://www.cplusplus.com/reference/cstring/strcpy/)
- `strstr`
  - search a c-string for the occurrence of another c-string
  - see [this link](http://www.cplusplus.com/reference/cstring/strstr/)
- C-String dimensions
  - covered section under "Primary differences between C-Strings and string"
- strncpy
  - same as `strcpy` but there's a maximum number of `char`s that it will copy
  - see [this link](http://www.cplusplus.com/reference/cstring/strncpy/)

### What is a C-String?
A C-String is just an array of characters, also called a "char array." In C
there is no `string` object, so all representations of a string of characters
had to be represented with an array of `char`s. We call this a C-String because
it was all you had in the way of strings when coding in C.

### Primary differences between C-Strings and string
#### C-Strings
- an array of primitive data types (`char`s)
- number of characters (aka "size" or "length") must be calculated
  - [sizeof](https://www.tutorialspoint.com/cplusplus/cpp_sizeof_operator.htm)
  - [strlen and sizeof](https://www.geeksforgeeks.org/difference-strlen-sizeof-string-c-reviewed/)

#### strings
- object (NOT a primitive data type)
- number of characters (aka "size" or "length") is a public member function
  - [size](http://www.cplusplus.com/reference/string/string/size/)
  - [length](http://www.cplusplus.com/reference/string/string/length/)

### What can I do to practice these?

- Make a program that
  - keeps asking the user for text input (until the user says stop)
  - take that text input and put it on a c string
  - at the end of the program, output the size of the c string
    - give the user the size in bytes as well as the number of characters
  - do this once with a string, then again with a c string
    - it will make you appreciate how much easier strings are than c strings
- Make a program that
  - has a c string with a lot of text in it
  - prints the c string to the user
  - asks the user for something to find within that c string, and somethign to
    replace it with
  - finds the phrase and replaces it with what the user specified
  - at the end of the program, output the size of the c string
    - give the user the size in bytes as well as the number of characters
  - do this once with a string, then again with a c string
    - it will make you appreciate how much easier strings are than c strings


## Binary Search

```
// C++ program to implement recursive Binary Search
#include <iostream>
using namespace std;

// A iterative binary search function. It returns
// location of x in given array arr[l..r] if present,
// otherwise -1
int binarySearch(int arr[], int l, int r, int x)
{
	while (l <= r) {
		int m = l + (r - l) / 2;

		// Check if x is present at mid
		if (arr[m] == x)
			return m;

		// If x greater, ignore left half
		if (arr[m] < x)
			l = m + 1;

		// If x is smaller, ignore right half
		else
			r = m - 1;
	}

	// if we reach here, then element was
	// not present
	return -1;
}

int main(void)
{
	int arr[] = { 2, 3, 4, 10, 40 };
	int x = 10;
	int n = sizeof(arr) / sizeof(arr[0]);
	int result = binarySearch(arr, 0, n - 1, x);
	(result == -1) ? cout << "Element is not present in array"
				: cout << "Element is present at index " << result;
	return 0;
}
```

[source](https://www.geeksforgeeks.org/binary-search/)

- NOTES
  - `l` is for "left" - its the left most index that we care about
  - `r` is for "right" - its the right most index that we care about
  - `m` is for "middle" - it is directly between `l` and `r`
- ASSUMPTIONS
  - the list we are looking through is sorted
    - binary search will not work if the list being searched is unsorted
- PROGRAM FLOW
  - loop through the list until `l` is no longer less than `r`
  - calculate the mid-point between `l` and `r` - call this value `m`
  - if the item at index `m` is what we are looking for, return that value
    - this breaks out of the while loop and the search function
  - if the value of the array at index `m` is less than what we're searching for
    (`x`) then...
    - we know that `x`, if present in the list, must be at an index greater than
      index `l`
    - we know this because the array is sorted
  - if the value of the array at index `m` is less than than the value that we
    are searching for (`x`) then...
    - we know that `x`, if present in the list, must be at an index greater than
      index `m`
    - we know this because the array is sorted
  - otherwise (read: `else`)...
    - the value of the array at index `m` is less than the value that we are
      searching for (`x`)
    - `x`, if present in the list, must be at an index less than index `m`
    - we know this because the array is sorted and the previous two if
      statements did not result to true
  - return -1 if we are outside of the loop
    - we return the value from within the `while` loop if we find it
    - so if we are outside of the loop, we did not find `x` in the list because
      it's not in the list!


### Links
- [Primitive Data Types](https://www.geeksforgeeks.org/c-data-types/)
- [Binary Search Algorithm](https://www.geeksforgeeks.org/binary-search/)

