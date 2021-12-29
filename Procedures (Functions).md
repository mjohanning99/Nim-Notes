# Procedures (Functions)
Procedure are basically the Nim equivalent of what's known as "functions" in other programming languages. Apparently, this is the proper name for functions in programming languages, as they differ from mathematical functions: —

>As mentioned in the beginning of this section, procedures are often called functions in other languages. This is actually a bit of a misnomer if we consider the mathematical definition of a function. Mathematical functions take a set of arguments (like `f(x, y)`, where `f` is a function, and `x` and `y` are its arguments) and _always_ return the same answer for the same input.
> Programmatic procedures on the other hand don’t always return the same output for a given input. Sometimes they don’t return anything at all

## Declaring a procedure
The declaration of a procedure is pretty straightforward and similar to how functions are declared in a lot of other programming languages. It is declared as follows, wherein `<px>` is a parameter of the function and `<typex>` is its type: —

```nim
proc <name>(<p1>: <type1>, <p2>: <type2>, ...): <return type> =
```

It is also important to note that, unlike in Ruby, a function's (or rather procedure's) return value must be implicitly declared. 
To declare a procedures that takes two numbers (of the `int` type) as its input and returns the number which is the largest of the two, one one write it as follows: —

```nim
proc largerOfTwo(num1: int, num2: int): int =
	if num1 > num2:
		return num1
	else:
		return num2

echo largerOfTwo(100, 20) #Output: 100
```

If a procedures has no `return` statement — and hence no return value —, the return type can be omitted: —

```nim
proc greet(name: string) =
	echo "Hello there, " & name

greet("Marvin") #Output: Hello there, Marvin
```

By default, the parameters of a procedures are immutable and, therefore, the following would result in an error: —

```nim
proc hyperError(num1: int) =
	num += 1

hyperError(10)
```

To make the above example compile and run properly, one would have to explicitly declare the parameters are a `var`. Additionally, all the arguments passed _to_ the procedure must also be declared as a variable, hence why the following example will still throw an error: —

```nim
proc addFive(var num1: int) =
	num1 += 5

echo addFive(100)
```

To make the above example _actually_ run, the following would have to be written: —

```nim
proc addFive(var num1: int) =
	num1 += 5

var hyperNumber: int = 100
addFive(hyperNumber)
echo hyperNumber #Output: 105
```

## Uniform Function Call Syntax
