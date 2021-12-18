# Data Types
```toc
style: number
```
----
As with most other programming languages, there are a number of data types that can be defined when declaring a [[Variables|variable]] or [[Immutable Values and Declarations|constant]]. The following is a list of these data types.

## Numbers
The first type of data we will be looking at is numbers. There are a couple of different data types concerning numbers.

### Integers
Integers can be declared using the previously-discussed ```int``` declaration. An underscore can be used as a thousands separator to make larger numbers more easily readable as follows: —

```nim
let monthlyIncome: int = 10_000
```

### Floats
Floats work as one would expect and can be declared using ```float```. Scientific notation for larger floats is also possible, such as ```4e7```. 

#### Conversion Between Floats and Integers
If one tries to add a float to an integer as in the example below, an error would occur: —
```nim
let
	monthlyIncome = 10_000
	monthlyTax    = 2_300.5142

echo monthlyIncome - monthlyTax
```
The following error would be thrown: —
```nim
proc `-`(x, y: int): int
first type mismatch at position: 2
required type for y: int
but expression 'monthlyTax' is of type: float64
```

Therefore, one must either the float to an integer or — more logically in this instance — the integer to a float. This can be achieved by using the aptly named ```integer``` and ```float``` functions within Nim as follows: —

```nim
let
	monthlyIncome = 10_000
	monthlyTax 	  = 2_300.5142

echo float(monthlyIncome) - monthlyTax # Output: 7699.4858
```

## Characters and Strings
A different type of frequently used data types are characters and strings. They are used for displaying either single characters (or a small amount thereof) or larger pieces of text.

### Characters
The ```char``` type can only be used for single ASCII characters (no Unicode here, οὖν πάνυ ἀθυμῶ εἰμὶ ἔγωγε). They always have to be placed within single quotation marks as follows: —

```nim
let hyperChar: char = 'c'
```

### Strings
Strings are usually the much more frequently used and can be declared using ```string``` (as we have previously seen). Their content is placed in-between double quotes as follows: —

```nim
let καλώδιον: string = "Οὕτός ἐστιν καλώδιόν τί."
```

#### Special Characters
There are also a handful of _special characters_ that can be used, such as ```\n``` for a new line, ```\t``` for a tab and, because ```\``` is used as the escape character, ```\\``` must be used when one wishes to write a backslash. The latter problem can be mitigated by using so-called _raw strings_: —

```nim
echo "Hello \\ there" # Output: Hello \ there
echo r"Hello \ there" # Output: Hello \ there
echo "Hello \ there"  # Error: invalid character constant
```

#### Concatenation
Strings in Nim are mutable and can, therefore, be modified — as long as they are defined as a variable and not ```const``` or ```let```. Appending a character or a different string to a string can be done using the ```add``` function, and simply concatenating different strings together — without altering their values — can be done with ```&```. The following examples illustrate this: —

```nim
var 
	hyperString = "I am testing."
	καλώδιον	= "Hello there, my friend."
	hallå		= "Låt oss programmera."
	
hyperString.add(" " & καλώδιον)
echo hyperString # Output: I am testing. Hello there, my friend.
```

### Booleans
Booleans are declared using ```bool```. The relational operators are basically the same as in Ruby, i. e. ```==``` to compare to values, ```=``` to define a value etc. Strings can be compared using the same operators. 

#### Logical Operators
The logical operators are basically the same as in Ruby, though there do not appear to be “shortcuts” as in Ruby, such as ```||``` for ```or```. 


## Containers 

Containers are iterable data types such as arrays or tuples. As they are iterable, [[Loops|loops]] can be used to iterate through their values. The simplest of these containers is the array.

### Array
An important aspect to know about arrays in Nim is that an array’s elements must _all_ be of the same data type; mixing different data types within the same array will result in an error. Additionally, an array’s size must be known at compile time; their size is, therefore, immutable (unlike in Ruby). 

Arrays are declared using ```array[<length>, <type>]```. If the length and the type can be inferred from the elements passed to the array, the declaration can be omitted. An array’s elements are enclosed inside square brackets, as in Ruby. Here are a few examples: —

```nim
var
	years: array[5, int] 	 = [2021, 2020, 2019, 2005, 1999]
	names: array[3, string]  = ["Ἡρόδοτος", "Marvin", "Πλάτων"]
	💕: array = ["💜", "💓", "💗", "💘", "💝"]
```

### Sequences
Sequences, unlike arrays, have neither an immutable length nor does their length need to be known at compile-time. Sequences are defined by using ```seq[<data type>]``` and its elements are placed inside square brackets prepended with an @ sign as follows: ```@[<values>]```.  The following is an example of such a sequence: —

```nim
var
	hyperSequence: seq[string] = @["Jag", "dricker", "kaffe"]
	inferredSequence = @[1, 2, 3]
```

#### Adding to a Sequence
Elements can be added (appended) onto a sequence using the same ```add``` function that was used to append a string to another string. The sequence must be mutable (i. e. declared using ```var```) and and data type of the element being added must be the same as the data type of the sequence: —

```nim
name: seq[string] = @["M", "a", "r", "v", "i"]
name.add("n")
echo name # Output: @["M", "a", "r", "v", "i", "n"]
```

#### Finding out a Sequence’s Length
Finding out a sequence’s length can be achieved by using the rather aptly named ```len``` function as follows: —

```nim
name: seq[string] = @["M", "a", "r", "v", "i", "n"]
echo name.len # Output: 6
```

### Slicing and Indexing
Slicing and indexing can be used to get a specific values — or series of values — from a container. Indexing, as with virtually all other programming languages (except for Lua, as far as I know), starts at 0.

#### Indexing
The syntax here is identical to Ruby, i. e. ```<container>[<index>]```.  A caret can be prepended to the index to index “from the back” (i. e. the last element becomes the first). The last element has index ```^1```.  Below a short example: —

```nim
var john: array[5, string] = ["ἐν", "ἀρχῇ", "ἦν", "ὁ", "λόγος"]

echo john[0] # Output: ἐν
echo john[^1] # Output: λόγος
```

#### Slicing
Slicing is basically the same as indexing, just that it allows one to get a series of elements using one statement. The ```start ... stop``` syntax can be used here as well: —

```nim
var 
	john: array[5, string] = ["ἐν", "ἀρχῇ", "ἦν", "ὁ", "λόγος"]
	name: seq[string] = @["M", "a", "r", "v", "i", "n"]

echo john[1..2] # Output: @["ἀρχῇ", "ἦν"]
echo name[0..5] # Output: @["M", "a", "r", "v", "i", "n"]
```

#### Assigning New Values
Both slicing and indexing can be used to assign a new value to a sequence or array — or to change an element: —

```nim
var
	name: seq[string] = @["G", "u", "ð", "m", "u", "n", "d"]
	years: array[3, int] = [2019, 2020, 2021]
	hyperYears: array[3, int]
	
for i in 0 .. 2:
	hyperYears[i] = years[i] * 2

name[0] = "K"

echo hyperYears # Output: [4038, 4040, 4042]
echo name # Output: @["K", "u", "ð", "m", "u", "n", "d"]
```

### Tuples
Tuples contain heterogeneous data, i. e. elements of a tuple can be of different data types. Like arrays, they have a fixed size. A tuple’s elements are enclosed within parentheses: —

```nim
let hyperTuple = ("Marvin", 1999, 'M')
```

It is also possible to assign a name to each of the fields of a tuple to distinguish them more easily: —

```nim
let hyperTuple = (name: "Marvin", year: 1999, gender: 'M')

echo hyperTuple.name # Output: Marvin
```

<div style="page-break-after: always;"></div>