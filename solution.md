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
???
```

(b) Tail-recursive implementation

```scala
???
```

Execution trace:

```
???
```