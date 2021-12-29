# Exercises
```toc
style: number
```
----

## Collatz conjecture
> First pick a number. If it is odd, multiply it by three and add one; if it is even, divide it by two. Repeat this procedure until you arrive at one. E.g. 5 → odd → 3*5 + 1 = 16 → even → 16 / 2 = 8 → even → 4 → 2 → 1 → end

```nim
# Collatz Conjecture

var number: int = 123

while number != 1:
    echo number
    if number mod 2 == 0:
        number = int(number / 2)
    else:
        number = number * 3 + 1
```

## Fizz Buzz
> We count numbers from one upwards. If a number is divisible by 3 replace it with _fizz_, if it is divisible by 5 replace it with _buzz_, and if a number is divisible by 15 (both 3 and 5) replace it with _fizzbuzz_. First few rounds would look like this: 1, 2, fizz, 4, buzz, fizz, 7, …​. Create a program which will print first 30 rounds of Fizz buzz.

```nim
# Fizz Buzz

for i in 1..30:
    if i mod 15 == 0:
        echo "fizzbuzz"
    elif i mod 3 == 0:
        echo "fizz"
    elif i mod 5 == 0:
        echo "buzz"
    else:
        echo i
```

### Output
```
1 2 fizz 4 buzz fizz 7 8 fizz buzz 11 fizz 13 14 fizzbuzz 16 17 fizz 19 buzz fizz 22 23 fizz buzz 26 fizz 28 29 fizzbuzz
```

## Vowels Only
> Create an immutable variable containing your full name. Write a for-loop which will iterate through that string and print only the vowels.

```nim
let name: string = "Marvin Johanning"

for l in name:
	case l
	of 'a', 'e', 'i', 'o', 'u':
		echo l
	else:
		discard
```

### Output
```
aioai
```

## Collatz Conjecture — Revisted
> Re-do the [Collatz conjecture exercise](https://narimiran.github.io/nim-basics/#_exercises_2), but this time instead of printing each step, add it to a sequence: Create a sequence whose only member is that starting number; using the same logic as before, keep adding elements to the sequence until you reach 1; print the length of the sequence, and the sequence itself
    
```nim
# Collatz Conjecture Revisted
var numbers: seq[int] = @[9]
    
while numbers[^1] != 1:
    if numbers[^1] mod 2 == 0: 
        numbers.add(int(numbers[^1] / 2))
    else:
        numbers.add(numbers[^1] * 3 + 1)

echo "The following numbers were found: ", numbers
echo "In total, there were ", numbers.len, " numbers found"
```

### Output
```
The following numbers were found: @[9, 28, 14, 7, 22, 11, 34, 17, 52, 26, 13, 40, 20, 10, 5, 16, 8, 4, 2, 1]
In total, there were 20 numbers found
```

## Hyper Collatz
> Find the number in a range from 2 to 100 which will produce the longest Collatz sequence: For each number in the given range calculate its Collatz sequence; if the length of current sequence is longer than the previous record, save the current length and the starting number as a new record; print the starting number which gives the longest sequence, and its length

```nim
# Hyper Collatz
var bigCollatz = (longestLength: 0, startingNumber: 0)
var bigCandidate: seq[int]

for numberCandidate in 2 .. 100:
    bigCandidate = @[numberCandidate]

    while bigCandidate[^1] != 1:
        if bigCandidate[^1] mod 2 == 0:
            bigCandidate.add(int(bigCandidate[^1] / 2))
        else:
            bigCandidate.add(bigCandidate[^1] * 3 + 1)
        if bigCandidate.len > bigCollatz.longestLength:
            bigCollatz.longestLength = bigCandidate.len
            bigCollatz.startingNumber = numberCandidate
    

echo "The longest Collatz sequence is ", bigCollatz.longestLength , " numbers long."
echo "The number starting number for this sequence was: ", bigCollatz.startingNumber
```

### Output
```
The longest Collatz sequence is 119 numbers long.
The number starting number for this sequence was: 97
```

## Array stuff
> Create an empty array which can contain ten integers: Fill that array with numbers 10, 20, …​, 100; -   Print only the elements of that array that are on odd indices (values 20, 40, …​); multiply elements on even indices by 5. Print the modified array.
 
```nim
# Array Stuff
var hyperSeq: seq[int]

for num in countup(10, 100, 10): 
    hyperSeq.add(num)

for i in 0 .. (hyperSeq.len - 1):
    if i mod 2 == 1:
        echo hyperSeq[i]
    else:
        hyperSeq[i] = hyperSeq[i] * 5

echo hyperSeq
```

### Output
```
20
40
60
80
100
@[50, 20, 150, 40, 250, 60, 350, 80, 450, 100]
```

# findMax3
> Create a procedure `findMax3` which will return the largest of three values.

```nim
proc findMax3(num1, num2, num3: int): int = 
  let nums: seq[int] = @[num1, num2, num2]

  for num in nums: 
    if num > result:
      result = num

echo findMax3(243, 123095, 1923)
```

## Output
```
123095
```

# 2D points
> Points in 2D plane can be represented as `tuple[x, y: float]`. Write a procedure which will receive two points and return a new point which is a sum of those two points (add x’s and y’s separately).

```nim
proc addTwoPoints(p1, p2: tuple): tuple =
  var result: tuple = (x: 0, y: 0)

  result.x = p1.x + p2.x
  result.y = p1.y + p2.y

  return result

let point1 = (x: 12, y: 15)
let point2 = (x: 42, y: 123)

echo addTwoPoints(point1, point2)
```

## Output
```
(x: 54, y: 138)
```

# Tick Tock
> Create two procedures `tick` and `tock` which echo out the words "tick" and "tock". Have a global variable to keep track of how many times they have run, and run one from the other until the counter reaches 20. The expected output is to get lines with "tick" and "tock" alternating 20 times. (Hint: use forward declarations.)

```nim
proc tick
proc tock

var counter: int = 0

proc tick() =
  echo "tick"

proc tock =
  echo "tock"

for i in 1..20:
  if counter mod 2 == 0:
    tick()
    counter += 1
  else:
    tock()
    counter += 1
```

## Output
```
tick tock tick tock tick tock tick tock tick tock tick tock tick tock tick tock tick tock tick tock 
```