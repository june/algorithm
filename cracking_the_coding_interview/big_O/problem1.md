# What is the runtime of the below code?
```
void foo(int[] array) {
  int sum = 0;
  int product = 1;
  for (inti= 0; i < array.length; i++) {
    sum =+ array[i);
  }
  for (int i= 0; i < array.length; i++) {
    product*= array[i];
  }
  System.out.println(sum + ", " + product);
}
```

This will take `O(N)` time.
The fact that we iterate through the array twice doesn't matter.
