# Loops
Nim has a number of different loops, just like Ruby does too. The most commonly used ones are the for- and while-loops.

## For-loop
The for-loop is pretty straight-forward and looks as follows, wherein the ```iterable``` is any object which one can iterate through: —

```nim 
for <loopVariable> in <iterable>:
	<loop body>
```

Iterating through a range of inter numbers (or even chars) can be done quite easily — and in a similar manner to Ruby — using the ```<start> .. <finish>``` syntax as follows: —

```nim
for i in 'a' .. 'z': 
	echo i # outputs the letters 'a' through 'z'
	
for i in 1 .. 10:
	echo i # outputs the numbers 1 to 10
```

If you do not wish to include the last number or char, the ```..<``` syntax can be used.

```nim
for i in 1 ..< 10:
	echo i # outputs the numbers 1 to 9
```

Different step sizes can be defined using the ```countup``` or ```countdown``` functions as follows: —

```nim
for i in countup(0, 100, 10):
	echo i # outputs 0, 10, 20, 30 …

for i in countdown(100, 0, 10): 
	echo i #outputs 100, 90, 80, 80 …
```

As strings are iterables, they can be iterated through using a for-loop as well: —

```nim
let programming = "Nim Programming" 
for l in programming:
	echo l #outputs each letter of the string individually
``` 

One can also use _two_ iterables within one for-loop in the following way: —

```nim
let programming = "Nim Programming"
for i, l in programming:
	echo "Letter number ", i, " is: ", l
```

## While loop