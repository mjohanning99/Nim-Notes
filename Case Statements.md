# Case Statements 
Case statements work quite similarly to those found in Ruby. Their syntax differs somewhat, however: —

```nim
var 🎄: string = "Christmas"
case 🎄
of "Christmas":
	echo "Merry Christmas!"
of "Weihnachten":
	echo "Fröhliche Weihnachten!"
else: echo "Det här språket kan jag inte förstå."
``` 

Unlike [[If Statements|if statements]] (and unlike Ruby’s case statements), case statements _must cover all possible cases_; therefore, when nothing is supposed to happen in the ```else``` portion of the case statement, the following must be written:  — 

```nim
var 🎄: string = "Christmas"
case 🎄
of "Christmas":
	echo "Merry Christmas!"
of "Weihnachten":
	echo "Fröhliche Weihnachten!"
else: discard
``` 

Several values can be added to one branch of a case statement by separating each value with a comma: —

```nim
var 🎄: string = "Christmas"
case 🎄
of "Christmas", "Yule":
	echo "Merry Christmas!"
```