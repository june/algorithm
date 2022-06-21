# What is the runtime of the below code?
```
def foo(array):
  sum = 0
  product = 1
  for i in range(len(array)):
    sum += array[i]
  for i in range(len(array)):
    product *= array[i]
  print('The sum of array elements is: {}, and the product of array elements is: {}'.format(sum,product))
```

This will take `O(N)` time.
The fact that we iterate through the array twice doesn't matter.
