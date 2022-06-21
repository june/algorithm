# What is the runtime of the below code?

```
def PairPrints(array):
  for i in range(len(array)):
    for j in range(len(array)):
      print('{}, {}'.format(array[i],array[j]))
```

The inner `for loop` has O(N) iterations and it is called N times. Therefore, the runtime is O(N<sup>2</sup>).

Another way we can see this is by inspecting what the `meaning` of the code is. It is printing all pairs (two element sequences). There are O(N<sup>2</sup>) pairs; therefore, the runtimes is O(N<sup>2</sup>)
