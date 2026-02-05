## Solution to Problem 1

(a)
The use at line 4 is bound at line 3 because it is within the scope of the circumference function.
The use at line 7 is bound at line 1 because pi is not redefined within the scope of the area function.

(b)
The use at line 3 is bound at line 2 because it is within f and x is an argument to the function f.
The use at lines 6 and 10 is bound at line 5 because "case x" creates a new variable called x.
The use at line 11 is bound at line 1 because it is outside the scope of the function f.

## Solution to Problem 2

(a) Execution trace:

```
pow(2,3)
-> if 3 > 0 then 2 * pow(2, 3-1) else 1
-> if true then 2 * pow(2, 3-1) else 1
-> 2 * pow(2, 3-1)
-> 2 * pow(2, 2)
-> 2 * (if 2 > 0 then 2 * pow(2, 2-1) else 1)
-> 2 * (if true then 2 * pow(2, 2-1) else 1)
-> 2 * (2 * pow(2, 2-1))
-> 2 * (2 * pow(2, 1))
-> 2 * (2 * (if 1 > 0 then 2 * pow(2, 1-1) else 1))
-> 2 * (2 * (if true then 2 * pow(2, 1-1) else 1))
-> 2 * (2 * (2 * pow(2, 1-1)))
-> 2 * (2 * (2 * pow(2, 0)))
-> 2 * (2 * (2 * (if 0 > 0 then 2 * pow(2, 0-1) else 1)))
-> 2 * (2 * (2 * (if false then 2 * pow(2, 0-1) else 1)))
-> 2 * (2 * (2 * 1))
-> 2 * (2 * 2)
-> 2 * 4
-> 8
```

(b) Tail-recursive implementation

```scala
def powTailHelper(x: Int, n: Int, acc: Int): Int =
    if n > 0 then powTailHelper(x, n-1, acc*x) else acc

def powTail(x: Int, n: Int): Int =
    powTailHelper(x, n, 1)
```

Execution trace:

```
powTail(2,3)
-> powTailHelper(2, 3, 1)
-> if 3 > 0 then powTailHelper(2, 3-1, 1*2) else 1
-> if true then powTailHelper(2, 3-1, 1*2) else 1
-> powTailHelper(2, 3-1, 1*2)
-> powTailHelper(2, 2, 1*2)
-> powTailHelper(2, 2, 2)
-> if 2 > 0 then powTailHelper(2, 2-1, 2*2) else 2
-> if true then powTailHelper(2, 2-1, 2*2) else 2
-> powTailHelper(2, 2-1, 2*2)
-> powTailHelper(2, 1, 2*2)
-> powTailHelper(2, 1, 4)
-> if 1 > 0 then powTailHelper(2, 1-1, 4*2) else 4
-> if true then powTailHelper(2, 1-1, 4*2) else 4
-> powTailHelper(2, 1-1, 4*2)
-> powTailHelper(2, 0, 4*2)
-> powTailHelper(2, 0, 8)
-> if 0 > 0 then powTailHelper(2, 0-1, 8*2) else 8
-> if false then powTailHelper(2, 0-1, 8*2) else 8
-> 8
```