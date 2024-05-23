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
Command chosen: **find** \
**-exec** \
Example 1: 
```
$ find /Users/adityamathur/docsearch/technical/biomed -name "*-2.txt" -exec mv {} /Users/adityamathur/docsearch/technical \; \

```
Explanation: -exec executes a specific command for each file found by the find criteria. In this example, we are moving the files \
found in the first directory into the second directory. There is no output. \
 \
Example 2: 
```
$ find /Users/adityamathur/docsearch/technical/biomed -name "*-3.txt" -exec head {} \;
Background
        Common variable immunodeficiency (CVID) and selective
        immunoglobulin G subclass deficiency (IgGSD) are
        characterized by subnormal serum concentrations of total
        IgG, or by normal serum total IgG concentrations with
        deficiency of one or more IgG subclasses, respectively; in

        Background
        CFEOM1 is an autosomal dominant disorder that has been
        linked to the pericentromere of chromosome 12, flanked by
        marker D12S1584 on the p arm and D12S1668 on the q arm [ 1,
        2]. The clinical phenotype consists of congenital,
        bilateral ptosis and external ophthalmoplegia, with the

        Background
        The increasing research in Complementary and Alternative
        Medicine (CAM) and the importance placed on practicing
        evidence-based CAM require ready access to the CAM
        scientific literature. The optimal retrieval of a
        literature search in biomedicine depends on the appropriate
```
Explanation: -exec executes a specific command for each file found by the find criteria. Here we are finding files given \
the criteria and `head` prints the first few lines of file and -exec applies to that command to every file found.
 \
 
**-name** \
Example 1:
```
$ find /Users/adityamathur/docsearch/technical/government/Post_Rate_Comm -name "*Delivery.txt"
/Users/adityamathur/docsearch/technical/government/Post_Rate_Comm/Cohenetal_RuralDelivery.txt
```
Explanation: `find -name` allows to search for files and directories that match the specified name pattern. Here \
we see that we're finding any file in the given directory that ends in "Delivery.txt" and see that the file \
Cohenetal_RuralDelivery.txt is returned. \
 \
Example 2:
```
$ find /Users/adityamathur/docsearch/technical/plos -name "*68.txt"
/Users/adityamathur/docsearch/technical/plos/journal.pbio.0020068.txt
/Users/adityamathur/docsearch/technical/plos/pmed.0010068.txt
/Users/adityamathur/docsearch/technical/plos/pmed.0020268.txt
/Users/adityamathur/docsearch/technical/plos/pmed.0020068.txt
```
Explanation: `find -name` allows to search for files and directories that match the specified name pattern. Similar \
to last example, here we are finding texts that end in "68.txt" and see that multiple files are returned \
within the directory. \
 \
**-type** \
Example 1:
```
$ find /Users/adityamathur/docsearch/technical/plos -type d
/Users/adityamathur/docsearch/technical/plos
```
Explanation: `find -type` allows to search for a specific type of file. the `d` is used here to find all the \
directories within the given directory and the return value signifies there are no further directories. \
 \
Example 2:
```
$ find /Users/adityamathur/docsearch/technical -type f
/Users/adityamathur/docsearch/technical/plos/pmed.0020007.txt
/Users/adityamathur/docsearch/technical/plos/journal.pbio.0030050.txt
.
.
. (thousands of files)
```
Explanation: `find -type` allows to search for a specific type of file. The `f` is used here to find all the \
regular files within the specified directory. As shown here, not only is the file name shown but also the directory \
within the specified directory it is located in. \
 \
**-mtime** \
Example 1:
```
$ find /Users/adityamathur/docsearch/technical/biomed -mtime 7

```
Explanation: `find -mtime [n]` allows to search for a file based on when it was modified. Here we are searching \
for files within a specific directory modified exactly 7 days ago and see nothing is returned. \
 \
Example 2:
```
$ find /Users/adityamathur/docsearch/technical/biomed -mtime +90

```
Explanation: `find -mtime [n]` allows to search for a file based on when it was modified. This example is different \
from last because the `+` is an additional modification that allows to search for files more than [n] days ago. \
 \


   
