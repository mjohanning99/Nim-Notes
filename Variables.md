# Variables
Nim is statically typed, hence the type of a declaration must be provided when defining a variable (much like Java and unlike Ruby). A variable can be defined as follows: —

```nim
# If value is unknown
var <name>: <type>

# If value is known
var <name>: <type> = <value>
```

Nim can, however, infer the type of a declaration, so that the following line of code is also valid: —

```nim
var <name> = <value>
```

It is, however, strongly recommended to always define the type of a declaration. The following are a handful of examples of variable declaration: —

```nim
var a: int  
var b = 7 
var a = 10
```

Nim developers typically use camel case for variable names; it is, however, rather important to note that Nim is both underscore- and case-insensitive, meaning that the following variables would all be viewed as having the same name in Nim: —

```nim
hello_world: int
helloWorld: int
hello_World: int
# etc.
```

Nim variables can, however, contain virtually any UTF-8 characters, including emojis; thus, the following examples would compile and run without any issues: —

```nim
var Κλεόφιλος: int = 100
echo Κλεόφιλος # Output: 100

var 💖: string = "<3"
echo 💖 # Output: <3
```

Several variables (which can be of different types) can be defined inside one ```var``` block as follows: —

```nim
var
	c = -11
	d = "Hello"
	e = '!'
```

The indentation here is vital, as Nim uses spaces to delimit the scope of a declaration, much like Python (but quite unlike Ruby); indentation can, thus, be seen as a replacement for curly brackets in programming languages such as PHP or Rust or the ```end``` placed after a declaration (such as a ```def```).  The only type of indentation that can, however, be used is __spaces__. The editor must, thus, convert tabs into any number of spaces (like two or four). 

There are two other ways of defining values, ```let``` and ```const```. These are under [[Immutable Values and Declarations]].