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

_Eg:_
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
-----
- When we come across statements which are repetative in nature. Then we use the **Frequency Count Method** to analyse the frequency of the executing statement.

_Eg:_ 
```
Algorithm Sum(A,n)
{
  S = 0;
  i = 0;
  WHILE(i < n) {
    S = S + A[i];
    i = i + 1;
  } ENDWHILE
  return  S;
}
```
**Time analysis**
1. `S=0` and `i=0` are simple statements which take _1_ unit of time.
2. `WHILE(i<n)` condition is checked _n+1_ times
3. `S=S+A[i]` is a simple statment with _1_ unit of time. However, as it is inside _WHILE_ is it repeated _n_ times. Hence, overall frequency is _1*n_ i.e _n_ times
4. `i=i+1` is a simple statment with _1_ unit of time. However, as it is inside _WHILE_ is it repeated _n_ times. Hence, overall frequency is _1*n_ i.e _n_ times
5. `return S` is a simple statment with _1_ unit of time.
 Overall Time complexity is, `F(n) = 1 + 1 + (n+1) + n + n + 1 = 3n+3`. Since, the degree of the polynomial is 1 we consider the time complexity to be O(n) or **Order of n**

**Space analysis**
1. Array `A` of size _n_ (Collection)
2. variable `n`
3. variable S
4. variable i
 
 Overall Space complexity is, `S(n) = n + 3` or O(n)
 
The statements:
```
i=0;
WHILE(i < n) {
    i = i + 1;
} ENDWHILE
```
is as good as writing `for(i=0; i<n; i++)` in C language. Time complexity for this would be _n+1_ since out of (1, n+1, n) frequencies for respective (i=0, i<n, i++) _n+1_ comes out as the most repeated and for simplicity we will consider the most repeated statment frequency
>Note: For future references, we will consider writing for loop instead of the pseudo code for better understanding and simplicity.

_Eg:_
```
Algorithm Add(A,B,n)                                Time Complexity
{
 for(i=0; i<n; i++)                  ---->              n+1 ... for condition check
  {
    for(j=0; j<n; j++)               ---->            n*(n+1) ... for condition check for inner loop times the outer loop frequency frequency scope
    {
      C[i,j] = A[i,j] + B[i,j];      ---->            n*n ... for inner timer outer loop frequncy scope
    }
  }
}
```
**Time analysis** </br>
 Overall Time complexity is, _F(n) = 2n<sup>2</sup> + 2n + 1_. Since, the degree of the polynomial is 2 we consider the time complexity to be O(n<sup>2</sup>) or **Order of n<sup>2</sup>**

**Space analysis**
1. 2D-Array `A` of size _n*n_ (Collection)
2. 2D-Array 'B' of size _n*n_ (Collection)
3. A2D-rray 'C' of size _n*n_ (Collection)
4. variable `n`
5. variable i
6. variable j

 Overall Space complexity is, _S(n) = 3n<sup>2</sup> + 3_ or O(n<sup>2</sup>)

_Eg:_
```
Algorithm Multiply(A,B,n)                              Time Complexity
{
  for(i=0; i<n; i++)                          ---->      n+1
  {
    for(j=0; j<n; j++)                        ---->      n*(n+1)
    {
      C[i,j] = 0;                             ---->        n*n
      for(k=0; k<n; k++)                      ---->      n*n*(n+1)
      {
        C[i,j] = C[i,j] + A[i,k]*B[k,j];      ---->       n*n*n
      }
    }
  }
}
```
**Time analysis**</br>
 Overall Time complexity is, _F(n) = 2n<sup>3</sup> + 3n<sup>2</sup> + 2n + 1_. Since, the degree of the polynomial is 3 we consider the time complexity to be O(n<sup>3</sup>) or **Order of n<sup>3</sup>**

**Space analysis**
1. 2D-Array `A` of size _n*n_ (Collection)
2. 2D-Array 'B' of size _n*n_ (Collection)
3. A2D-rray 'C' of size _n*n_ (Collection)
4. variable `n`
5. variable i
6. variable j
7. variable k

 Overall Space complexity is, _S(n) = 3n<sup>2</sup> + 4_ or O(n<sup>2</sup>)
