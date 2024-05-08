# Lab 3 Report
## Part 1
**Buggy Program** 
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```
There are 2 bugs in this program: 
1.  `arr[i] = newArray[arr.length - i - 1];` assigns values of the \
   original array to the new array. It should the opposite. The correct \
code would be `newArray[i] = arr[arr.length - i - 1];`. 
2. `return arr;` returns the original array, not the reversed array. The \
   correct code should be `return newArray;`.
\
\
**Failure-inducing input as a JUnit Test:** 
```
@Test 
  public void testReversedFailure() {
    int[] input1 = {0, 1};
    int[] expected = {1, 0};
    assertArrayEquals(expected, ArrayExamples.reversed(input1));
  }
```
\
**Input that doesn't induce a failure as a JUnit Test:** 
```
@Test
  public void testReversed() {
    int[] input1 = { };
    assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
  }
```
**Symptom of Running the Tests:**
![Image](symptom.png)
\
**Buggy Program:** 
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```
**Fixed Program:**
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
        newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
}
```
This fix addresses the issue because now we're iterating through the ORIGINAL array \
and putting its elements in reverse order into a NEW array. Then the program is \
returning the new array. This fixes the original bug which inserted the elements \
in reverse order from the new, empty array into the original array and returning \
that original array (which will always be empty). 

---

## Part 2

   
