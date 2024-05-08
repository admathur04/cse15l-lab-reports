# Lab 5 Report
## Part 1
**Buggy Program** \
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```
There are 2 bugs in this program: \
1.  `arr[i] = newArray[arr.length - i - 1];` assigns values of the \
   original array to the new array. It should the opposite. The correct \
code would be `newArray[i] = arr[arr.length - i - 1];`. 
2. `return arr;` returns the original array, not the reversed array. The \
   correct code should be `return newArray;`.
\
**Failure-inducing input as a JUnit Test:** \
```
@Test 
  public void testReversedFailure() {
    int[] input1 = {0, 1};
    int[] expected = {1, 0};
    assertArrayEquals(expected, ArrayExamples.reversed(input1));
  }
```
\
**Input that doesn't induce a failure as a JUnit Test:** \
```
@Test
  public void testReversed() {
    int[] input1 = { };
    assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
  }
```
\

   
