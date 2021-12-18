# Immutable Values and Declarations
[[Variables]], as the name would already suggest, are _variable_; their values can change over the course of the program. At times, however, this is not intended and a static value is, instead, required. There are two ways of declaring these immutable, static values: ```const``` and ```let```.

### Const

Constants, which are defined by ```const```, must be declared and known at compile time. Thus, a constant cannot be dependent on the output of, for example, a function. Therefore, the following declaration would result in a compilation error: —

```nim
var five: int = -5
const hyper: int = five + 5
```

Here, the value of ```hyper``` will be known only after the program has been run, but it will not be known during compilation — hence the error. The following declarations will, however, work without any issues because their values will be known at the time of compilation: —

```nim
const developerName: string = "Marvin"
const pi: float = 3.141592653589793
```

## Let
The other method of defining an immutable value is by using the ```let``` keyword. The main difference between ```const``` and ```let``` is the fact that the value of a constant declared by ```let``` does _not_ need to be known at compile time. Thus, the above-example can be rewritten using ```let``` to make it work: —

```nim
var five: int = -5
let hyper: int = five + 5
```

[[Data Types]]