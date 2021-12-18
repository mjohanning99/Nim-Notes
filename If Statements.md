# If Statements
If statements are part of _control flow_, i. e. only executing a certain piece of code when a condition is fulfilled. If statements in Nim are written as follows: —

```nim
if <condition>: 
	<indented block of code>
```

It is, once again, important to intend the code not using tabs, but using spaces.  If statements can actually be nested, so that the following would be possible: —

```nim
var Κλεόφιλος: string = "Marv"
if Κλεόφιλος != "Marvin":
    echo "Οὐκ ἐστιν ὁ Κλεόφιλος ἀληθῶς ὁ Κλεόφιλος."
    if Κλεόφιλος & "in" == "Marvin": 
      echo "Marvin has returned."
```

## Else and Else If
There are, of course, also else and else if statements. Else statements are done as follows: —

```nim 
var hyperName: string = "Marvin"
if hyperName == "Marvin":
	echo "Truly, it is him!"
else:
	echo "Hinfort!"
```

And else if statements are done using ```elif``` in the following manner: —

```nim
var 🎄: string = "Christmas"
if 🎄 == "Christmas":
	echo "Merry Christmas!"
elif 🎄 == "Jul":
	echo "God jul till dig!"
elif 🎄 == "Weihnachten":
	echo "Fröhliche Weihnachten!"
else: 
	echo "Οὐ καταλαμβάνω τὴν γλ͂ωτταν ταύτην."
```

[[Case Statements]] are quite similar to if statements.