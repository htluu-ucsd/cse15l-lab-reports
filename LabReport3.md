# Lab Report: Week 5, 10/31/2023, 4-6:00 pm
# Hao Tri Luu

---
## Part 1
I am writing about the bugs for the `ArrayTests.java` implementation of the method `testReversedLongArray()`.
The JUnit test I wrote and ran are:

The first output, which is failure-inducing, is an array with elements `{1,2,3}`.
```
@Test
public void testReversedLongArray(){
  int[] arr = {1,2,3};
  int[] rra = {3,2,1};
  assertArrayEquals(rra, ArrayExamples.reversed(arr));
}
```
The result of running the debugger is `expected:<3> but was:<0>` being outputted in the terminal.

The second output, which is not failure-inducing, is an array with elements `{0}`.
```
@Test
public void testReversedLongArray(){
  int[] arr = {0};
  int[] rra = {0};
  assertArrayEquals(rra, ArrayExamples.reversed(arr));
}
```
The result of running the debugger is that no bugs are caught and the terminal just prints the runtime.

SCREENSHOT WITH SYMPTOMS

The original code is:
```
static int[] reversed(int[] arr) {
  int[] newArray = new int[arr.length];
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = newArray[arr.length - i - 1];
  }
  return arr;
}
```

The fixed code is:
```
static int[] reversed(int[] arr) {
  int[] newArray = new int[arr.length];
  for(int i = 0; i < arr.length; i += 1) {
    newArray[i] = arr[arr.length - i - 1];
  }
  return newArray;
}
```
The issue was fixed because in the code, the array `newArray` is supposed to store the reversed array but the code was not taking elements from the input `arr` and filling `newArray`. Rather, The elements of `newArray` were filling `arr`, and `arr` was being returned instead of `newArray`. Because `newArray` was initialized with only size, it was populated with `0`, so the returned array had elements of `0` instead of the correct values.

---
## Part 2
