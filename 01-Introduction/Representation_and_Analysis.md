## Representation

### Few key points to remember while representing an algorithm
- We never mention the datatype while describing an algorithm as it is ususally done during program creation

Different Ways to represent
```
Algorithm swap(a,b)
{
  temp = a;
  a = b;
  b = temp;
}
```

Another way is to use `BEGIN` AND `END` instead of the curly craces`{}`
```
Algorithm swap(a,b)
BEGIN
  temp = a;
  a = b;
  b = temp;
END
```

Another way can be to use `:=` instead of equalto (`=`) sign
```
Algorithm swap(a,b)
{
  temp := a;
  a := b;
  b := temp;
}
```

We can also use left assigment arrow (&larr;)
```
Algorithm swap(a,b)
{
  temp <-- a;
  a <-- b;
  b <-- temp;
}
```

## How to Analyse an algorithm
### Major criteria
#### Time
The algorithm should be efficent in terms of time. WE analyse the efficiency in terms of **time as a function** and not in terms of watch time.

#### Space
As the algorithm is going to get converted into a program and run on a machine, we need to know the memory space it will consume.

### Other criteria's
#### Data transfer/ Network consumition
As in recent time many applications are cloud driven, Data transfer speed or network consumption becomes a very critical criteria to analyse whether the packet size can be compressed or does the data reduction can be acheived.
#### Power consumption
There days along with computers many handheld devices are revolutionizing the ecosystem. Hence, power consumption by various devices is another criteria to be taken into consideration.

### Few key points to remember while analyzing an algorithm
- Every simple statement is considered to be consuming 1 unit of time
- If an algorithm depends on another algorithm to reach the outcome, then analyzing the external algorithm is important to decide on the complexity
- For space complexity, we should consider the number of storage containers/variables we are utilizing if its a simple container else if its a collection like list/arrays then we consider the number of items that collection can hold to reach the outome

```
Algorithm swap(a,b)    |    Time complexity  |    Space Complexity
{                      |                     |          
  temp = a;         ---|---->  1             |           temp
  a = b;            ---|---->  1             |             a
  b = temp;         ---|---->  1             |             b
}                      |                     |
-----------------------------------------------------------------------
                       |  F(n) = 3 or O(1)   |        S(n) = 3
```
