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
is as good as writing `for(i=0; i<n; i++)` in C language. Frequency-count for this would be _n+1_ since out of (1, n+1, n) frequencies for respective (i=0, i<n, i++) _n+1_ comes out as the most repeated and for simplicity we will consider the most repeated statment frequency
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

#### FOR-LOOP Time Complexity analysis
_Eg:_
```
  for(i=0; i<n; i++)         ----> n+1
  {
    stmt;                    ----> n
  }
```
**Time Complexity:**  O(n)

_Eg:_
```
  for(i=n; i>0; i--)         ----> n+1
  {
    stmt;                    ----> n
  }
```
**Time Complexity:**  O(n)

_Eg:_
```
  for(i=1; i<n; i=i+2)         ----> n/2 + 1
  {
    stmt;                     ----> n/2
  }
```
**Time Complexity:**  O(n)

_Eg:_
```
  for(i=1; i<=n; i=i+20)         ----> n/20 + 1
  {
    stmt;                       -----> n/20
  }
```
**Time Complexity:**  O(n)
> Note: If FOR-LOOP counter increments by say, _i+a_ times; the frequency for it can be generalized as _n/a_. However, the time complexity for all such scenarios will always remain O(n).

_Eg:_
```
  for(i=0; i<n; i++)         ----> n+1
  {
    for(j=0; j<n; j++)       ----> n*(n+1)
  {
    stmt;                   -----> n*n
  }
  }
```
**Time Complexity:**  O(n<sup>2</sup>)

_Eg:_
```
  for(i=0; i<n; i++)         
  {
    for(j=0; j<i; j++)       
    {
      stmt;                   -----> n*n
    }
  }
```
| i | j | count |
|---|---|---|
| 0 | 0 ❌ | 0 |
| 1 |  0 ✔️</br> 1 ❌ | 1 |
| 2 | 0 ✔️</br> 1 ✔️</br> 2 ❌ | 2 |
| 3 | 0 ✔️</br> 1 ✔️</br> 2 ✔️</br> 3 ❌ | 3 |
| ... | ... | ...|
| n | 0 ✔️</br> 1 ✔️</br> 2 ✔️</br> 3 ✔️</br> .</br> .</br> n ❌ | n |

F(n) = 0 + 1 + 2 + 3 + .... + n = $`\frac{n*(n+1)}{2}`$ = $`\frac{n^2 + 1}{2}`$


**Time Complexity:**  O($`n^2`$)

_Eg:_
```
  p = 0;
  for(i=1; p<=n; i++)         
  {
    p = p + i;
  }
```
| i | p |
|---|---|
| 1 |  0+1 = 1 |
| 2 |  1+2 = 3 |
| 3 | 3+3 = 6 |
| 4 | 6+4 = 10 |
| ... | ... |
| k | 1+2+3+4+...+k = $`\frac{k*(k+1)}{2}`$ |

The loop doesn't jump n times but exits at `i=k` as evident from the fact that before `i` even reached `n`, `p` will already exceed it </br>
The loop exits when: `p > n` </br>
since, p = $`\frac{k*(k+1)}{2}`$ </br>
Therefore, $`\frac{k*(k+1)}{2}`$ > n   &rarr;   $`k^2`$ > n   &rarr;   k > $`\sqrt{n}`$


**Time Complexity:**  O($`\sqrt{n}`$)

_Eg:_
```
  for(i=1; i<n; i=i*2)         
  {
    stmt;
  }
```
| i  |
|--- |
| 1 |
| 1*2 = 2 |
| 2*2 = $`2^2`$ |
| $`2^2`$*2 = $`2^3`$ |
| ...|
| $`2^k`$ |

The loop doesn't jump n times but exits at $`i = 2^k`$ as evident from the fact that before `i` even reached `n`, $`2^k`$ will already exceed it </br>
The loop exits when: `i >= n` </br>
since, i = $`2^k`$ </br>
Therefore, $`2^k`$ >= n   &rarr;     k >= $`log_2 n`$

If you observe, value of $`log_2 n`$ can be decimal. However, when coming to frequency, it should be a whole value. For this example:</br>
When n=8
| i  |
|--- |
| 1 ✔️ |
| 1*2 = 2 ✔️ |
| 2*2 = $`2^2`$ = 4 ✔️ |
| $`2^2`$*2 = $`2^3`$ = 8 ❌ |

So, overall, loop ran for 3 times and also $`log_2 8 = 3`$.</br></br>
Now, consider n=10
| i  |
|--- |
| 1 ✔️ |
| 1*2 = 2 ✔️ |
| 2*2 = $`2^2`$ = 4 ✔️ |
| $`2^2`$*2 = $`2^3`$ = 8 ✔️ |
| $`2^3`$*2 = $`2^4`$ = 16 ❌ |

So, overall the loop ran for 4 times. However, $`3 > log_2 10 > 4`$. So, we consider **ceil** value for this time complexity.

**Time Complexity:**  O($`\lceil log_2 n \rceil`$)

_Eg:_
```
  for(i=n; i>=1; i=i/2)         
  {
    stmt;
  }
```
| i |
|---|
| n |
| $`\frac n2`$ |
| $`\frac {n}{2^2}`$ |
| $`\frac {n}{2^3}`$ |
| ...|
| $`\frac {n}{2^k}`$|

The loop doesn't jump n times but exits at $`i = \frac {n}{2^k}`$ as evident from the fact that before `i` even reached `1`, $`\frac {n}{2^k}`$ will already be less that it </br>
The loop exits when: `i < 1` </br>
since, i = $`\frac {n}{2^k}`$ </br>
Therefore, $`\frac {n}{2^k}`$ < 1   &rarr;    n  < $`2^k`$ &rarr; k > $`log_2 n`$

If you observe, value of $`log_2 n`$ can be decimal. However, when coming to frequency, it should be a whole value. For this example:</br>
When n=8
| i  |
|--- |
| 8 ✔️ |
| $`\frac 82`$ = 4 ✔️ |
| $`\frac 42`$ = 2 ✔️ |
| $`\frac 22`$ = 1 ✔️ |
| $`\frac 12`$ = 0.5 ❌ |

So, overall, loop ran for 4 times. However, $`log_2 8 = 3`$.</br></br>
Now, consider n=10
| i  |
|--- |
| 10 ✔️ |
| $`\frac {10}2`$ = 5 ✔️ |
| $`\frac {5}2`$ = 2.5 ✔️ |
| $`\frac {2.5}2`$ = 1.25 ✔️ |
| $`\frac {1.25}2`$ = 0.75 ❌ |

So, overall the loop ran for 4 times. However, $`3 > log_2 10 > 4`$. So, we consider **ceil** value for this time complexity.

**Time Complexity:**  O($`\lceil log_2 n \rceil`$)

_Eg:_
```
  for(i=0; i*i <= n; i++)         
  {
    stmt;
  }
```
| i |
|---|
| 0|
| 1*1 = 1 |
| 2*2 = 4 |
| 3*3 = 9 |
| ... |
| k*k = $`k^2`$

The loop doesn't jump n times but exits at `i = k` as evident from the fact that before `i` even reached `n`, $`k^2`$ will already exceed it</br>
The loop exits when: `i*i > n` </br>
since, i = k</br>
Therefore, $`k^2`$ > n   &rarr;    k > $`\sqrt n`$

**Time Complexity:**  O($`\sqrt n`$)

_Eg:_
```
// These are two independent loops
  for(i=0; i<n; i++)                  ---->              n+1 ... for condition check
  {
    stmt;                             ---->              n
  }
  for(j=0; j<n; j++)                  ---->            n*(n+1) ... for condition check
  {
    stmt;                             ---->            n
  }
```
**Time analysis** </br>
 Overall Time complexity is, _F(n) = n + n = 2n_. Since, the degree of the polynomial is 1 we consider the time complexity to be O(n) or **Order of n**

_Eg:_
```
  p = 0;
  for(i=1; i < n; i=i*2)         
  {
    p++;
  }
  for(j=1; j < p; j=j*2)         
  {
    stmt;
  }
```
From the previous examples, we know that, for the first loop
```
  for(i=1; i < n; i=i*2)         
  {
    p++;
  }
```
the frequency is $`\lceil log_2 n \rceil`$. Meaning, p= $`\lceil log_2 n \rceil`$ as p's value and the loop count go hand in hand.</br>

For the second loop
```
  for(j=1; j < p; j=j*2)         
  {
    stmt;
  }
```
the frequency is $`\lceil log_2 p \rceil`$. However,  p= $`\lceil log_2 n \rceil`$.

**Time Complexity:**  O($`\lceil log_2 (\lceil log_2 n \rceil) \rceil`$)

_Eg:_
```
  for(i=0; i < n; i++)                         ---->          n+1
  {
      for(j=1; j < n; j=j*2)                   ---->          n*(logn)
	  {
	    stmt;                                    ---->          n*(logn)
	  }
  }
  
```
F(n) = $`2nlog_2 n + n`$

**Time Complexity:**  O($`nlog_2 n`$)

**CheatSheet**
| loop | Frequecy-count | time-complexity |
|---|---|---|
| for(i=0; i<n; i++) | n | O(n) |  |
| for(i=0; i<n; i=i+2) | $`\frac n2`$ | O(n) | 
| for(i=0; i<n; i=i+3) | $`\frac n3`$ | O(n) | 
| for(i=0; i<n; i=i+200) | $`\frac {n}200`$ | O(n) |
| for(i=n; i>1; i--) | n | O(n) |
| for(i=n; i>1; i=i-2) | $`\frac n2`$ | O(n) |
| for(i=n; i>1; i=i-3) | $`\frac n3`$ | O(n) |
| for(i=n; i>1; i=i-200) | $`\frac {n}200`$ | O(n) |

For linear increment/decrement, the time complexity will be O(n).

| loop | Frequecy-count | time-complexity |
|---|---|---|
| for(i=1; i<n; i=i*2) | $`\lceil log_2 n \rceil`$ | O($`\lceil log_2 n \rceil`$) |
| for(i=1; i<n; i=i*3) | $`\lceil log_3 n \rceil`$ | O($`\lceil log_3 n \rceil`$) |
| for(i=n; i>1; i=i/2) | $`\lceil log_2 n \rceil`$ | O($`\lceil log_2 n \rceil`$) |
| for(i=n; i>1; i=i/3) | $`\lceil log_3 n \rceil`$ | O($`\lceil log_3 n \rceil`$) |

For power based increment/decrement, the time complexity will be O($`\lceil log_k n \rceil`$), where k is the power.
