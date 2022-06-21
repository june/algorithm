# What is the runtime of the below code?

```
def PairPrints(array):
  for i in range(len(array)):
    for j in range(i+1, len(array)):
      print('{}, {}'.format(array[i],array[j]))
```

This is very similar code to the `problem2`, but now the inner `for loop` starts at i+1.

We can drive the runtime several ways.

<b>Deep Comprehension is important!</b>

The number of steps total is:
(N-1) + (N-2) + (N-3) + ... + 2 + 1
= sum of 1 through N-1
= N(N-1)/2

So, the runtime will be O(N<sup>2</sup>).
