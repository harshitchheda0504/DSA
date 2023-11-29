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
