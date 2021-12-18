# Data Types
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