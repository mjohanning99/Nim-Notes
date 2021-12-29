```toc
style: number
```
-----
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
Uniform function call syntax allows many different ways of calling a function (from [Wikipedia](https://en.wikipedia.org/wiki/Uniform_Function_Call_Syntax)): —
> **Uniform Function Call Syntax** (**UFCS**) or **Uniform Calling Syntax** (**UCS**) or sometimes **Universal Function Call Syntax** is a [programming language](https://en.wikipedia.org/wiki/Programming_language "Programming language") feature in [D](https://en.wikipedia.org/wiki/D_(programming_language) "D (programming language)") and [Nim](https://en.wikipedia.org/wiki/Nim_(programming_language) "Nim (programming language)") that allows any [function](https://en.wikipedia.org/wiki/Function_(computer_programming) "Function (computer programming)") to be called using the syntax for method calls (as in [object-oriented programming](https://en.wikipedia.org/wiki/Object-oriented_programming "Object-oriented programming")), by using the [receiver](https://en.wikipedia.org/w/index.php?title=Receiver_(object_oriented_programming)&action=edit&redlink=1 "Receiver (object oriented programming) (page does not exist)") as the first parameter, and the given arguments as the remaining parameters.

Basically, the first argument of a procedure can be placed in front of the actual procedure name, so as to make certain calls more readable. For example: —

```nim
proc plus(num1, num2: int): int =
	return num1 + num2

echo 1.plus(5) #Output: 6
```

## Result variable
When the end of a procedure has been reached, its last value is automatically assigned as the procedure's return value if no `return` statement has been added. An example of this is as follow: —

```nim
proc findBiggest(a: seq[int]): int =  
  for number in a:
    if number > result:
      result = number
  # the end of proc                   

let d = @[3, -5, 11, 33, 7, -15
echo findBiggest(d) #Output: 33
```

In this example, as the `return` type of the procedures is an integer, the `result` variable has been automatically assigned the value of `0`. The for loop then iterates through each of the sequence's numbers and changes the `result` variable's value to said number if it was bigger than the number.

In the following example, which shows a procedure which will only keep the odd numbers of a sequenced passed to it, the `return` type has been defined as a `seq`; therefore, the `result` variable has been automatically declared as an empty sequence and values can be added onto it: —

```nim
proc keepOdds(nums: seq[int]): seq[int] =
	for number in nums:
		if number mod 2 == 1:
			result.add(number)


let f = @[1, 6, 4, 43, 57, 34, 98]
echo keepOdds(f)```
````

## Forward Declaration
Procedures must be declared before they are called, hence why the following will throw an error: —

```nim
echo 5.plus(1)

proc plus(num1, num2: int): int =
	return num1 + num2
```

To solve this, one must first tell Nim that, at some point in the code, there will be a procedure titled `plus`. This is done as follows: —

```nim
proc plus(num1, num2: int): int

echo 5.plus(1)

proc plus(num1, num2: int): int =
	return num1 + num2
```
<div style="page-break-after: always;"></div>