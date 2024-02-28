# Lab Report 3
>Daniel Bravo
>
>CSE 15l

## Part 1 - Bugs
### Chosen bug: Code for the method `reverseInPlace` in `ArrayExamples.java`
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```

* A failure-inducing input for the buggy program, as a JUnit test and any associated code:
```
@Test 
	public void testReverseInPlaceFailure() {
    int[] input2 = {1, 2, 3, 4};
    ArrayExamples.reverseInPlace(input2);
    assertArrayEquals(new int[]{4, 3, 2, 1}, input2);
	}
```

* An input that doesn't induce a failure, as a JUnit test and any associated code:
```
@Test 
	public void testReverseInPlaceOk() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);

	}
```

* The symptom, as the output of running the tests:
<img width="1068" alt="image" src="https://github.com/dbrvo/cse15l-lab-reports/assets/87788227/77d2a655-dd47-4c68-9360-ca31035a8746">


* The bug, as the before-and-after code change required to fix it:

Before:
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```

After:
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length/2; i += 1) {
      int temp = arr[i];
      arr[i] = arr[arr.length - i - 1];
      arr[arr.length - i - 1] = temp;
    }
  }
```

* Briefly describe why the fix addresses the issue:

For reverseInPlace I changed the for loop to be bound by i<arr.length/2 because we are swapping elements, so going through half of them will swap the first half and second half. I added an int called temp to hold the value of arr at index i, so we can swap elements without losing the data in an index that was changed. Lastly I added another line of code to make the value of arr.length - i - 1 to be that of temp, so the reverse swap can finish by using the saved temp element.

<br />

## Part 2 - Researching Commands

### Chosen command: `find`
1. `find -name «pattern»`
   * ```
     % find . -name preface.txt
       ./911report/preface.txt
     ```
   * The `-name` with a file name found a file that has a specific name. It is useful when you want to know the specific location of a file when you know its name.
   * ```
     % find . -name About_LSC
       ./government/About_LSC
     ```
   * The `-name` with a directory name found a directory that has a specific name. It is useful when you want to know the specific location of a directory when you know its name.

2. `find -type «type»`
   * ```
     % find . -type d
       .
       ./government
       ./government/About_LSC
       ./government/Env_Prot_Agen
       ./government/Alcohol_Problems
       ./government/Gen_Account_Office
       ./government/Post_Rate_Comm
       ./government/Media
       ./plos
       ./biomed
       ./911report
     ```
   * The `-type` followed by a `d` searches for files of type directory. It is useful when you want to specify if what your looking for is a file or directory
   * ```
     % find . -type f -name "chapter-10.txt"
       ./911report/chapter-10.txt
     ```
   * The `-type` followed by a `f` searches for files of type file. It is useful when you want to specify if what your looking for is a file or directory

3. `find -size «n»`
   * ```
     % find . -size +590
       ./government/Gen_Account_Office/Statements_Feb28-1997_volume.txt
     ```
   * The `-size` followed by a plus and number n looks for flies that take up more than n units of space. It is useful when you want to find and potentially use a file that uses up more space than others.
   * ```
     % find . -size -2
       .
       ./government
       ./government/Env_Prot_Agen
       ./government/Alcohol_Problems
       ./government/Post_Rate_Comm
     ```
   * The `-size` followed by a plus and number n looks for flies that take up less than n units of space. It is useful when you want to find and potentially use a file that uses up less space than others.

4. `find -mindepth «levels»`
   * ```
     % find . -mindepth 3
       ./government/About_LSC/LegalServCorp_v_VelazquezSyllabus.txt
       ./government/About_LSC/Progress_report.txt
       ./government/About_LSC/Strategic_report.txt
       ./government/About_LSC/Comments_on_semiannual.txt
       ./government/About_LSC/Special_report_to_congress.txt
       ./government/About_LSC/CONFIG_STANDARDS.txt
       ... lots of lines! ...
     ```
   * The `-mindepth` option specifies the minimum directory depth for the search. It can be useful when you want to find a file or directory that has a certain depth, for example helping with organization.
   * ```
     % find . -type d -mindepth 2
       ./government/About_LSC
       ./government/Env_Prot_Agen
       ./government/Alcohol_Problems
       ./government/Gen_Account_Office
       ./government/Post_Rate_Comm
       ./government/Media
     ```
   * The `-mindepth` option can also be paired up with other options like `-type` to be even more specific. It can be useful when you want to find a file or directory that has a certain depth and file type.
  

<br />

Sources used:
* [man7.org](https://man7.org/linux/man-pages/man1/find.1.html)
* [geeksforgeeks.org](https://www.geeksforgeeks.org/find-command-in-linux-with-examples/)





