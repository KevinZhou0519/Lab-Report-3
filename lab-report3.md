**Part 1**-------------------------------------------------------------------------------------------------------------------------------------------------------------


**Code Before**
````md
public class ArrayExamples {

  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }

  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }

  static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      if(num != lowest) { sum += num; }
    }
    return sum / (arr.length - 1);
  }
}
````

**Success**
````md
import static org.junit.Assert.*;
import org.junit.*;

public class ArrayTests {
	@Test 
	public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
	}


  @Test
  public void testReversed() {
    int[] input1 = { };
    assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
  }

  @Test 
	public void testReverseInPlace2() {
    int[] input1 = { 5,5 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{5,5}, input1);
	}


  
  @Test
  public void testaverageWithoutLowest() {
    double[] input1 = {3.0};
    
    assertEquals(0.0, ArrayExamples.averageWithoutLowest(input1),0.000001);
  }

  @Test
  public void testaverageWithoutLowest1() {
    double[] input1 = {};
    
    assertEquals(0.0, ArrayExamples.averageWithoutLowest(input1),0.000001);
  }

  @Test
  public void testaverageWithoutLowest2() {
    double[] input1 = {3.0,4.0};
    
    assertEquals(4.0, ArrayExamples.averageWithoutLowest(input1),0.000001);
  }

PS C:\Users\KIDKV\OneDrive\Desktop\UCSD\2023 Fall\cse 15L\lab3-main> javac -cp ".;lib/hamcrest-core-1.3.jar;lib/junit-4.13.2.jar" *.java
>>
PS C:\Users\KIDKV\OneDrive\Desktop\UCSD\2023 Fall\cse 15L\lab3-main> java -cp ".;lib/junit-4.13.2.jar;lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore ArrayTests
JUnit version 4.13.2
......
Time: 0.018

OK (6 tests)
````
![suc](lab-report3-suc.png)


**Failure**
````md

  @Test
  public void testReversed1() {
    int[] input1 = {3,4,5};
    assertArrayEquals(new int[]{5,4,3}, ArrayExamples.reversed(input1));
  }

  @Test
  public void testReverseInPlace1() {
    int[] input1 = {3,4,5};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{5,4,3}, input1);
  }

  

  @Test
  public void testaverageWithoutLowest3() {
    double[] input1 = {3.0,3.0,4.0,5.0};
    
    assertEquals(4.5, ArrayExamples.averageWithoutLowest(input1),0.000001);
  }

PS C:\Users\KIDKV\OneDrive\Desktop\UCSD\2023 Fall\cse 15L\lab3-main> javac -cp ".;lib/hamcrest-core-1.3.jar;lib/junit-4.13.2.jar" *.java
>>
PS C:\Users\KIDKV\OneDrive\Desktop\UCSD\2023 Fall\cse 15L\lab3-main> java -cp ".;lib/junit-4.13.2.jar;lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore ArrayTests
JUnit version 4.13.2
.E.E.E
Time: 0.009
There were 3 failures:
1) testReverseInPlace1(ArrayTests)
arrays first differed at element [2]; expected:<3> but was:<5>
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:78)
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:28)
        at org.junit.Assert.internalArrayEquals(Assert.java:534)
        at org.junit.Assert.assertArrayEquals(Assert.java:418)
        at org.junit.Assert.assertArrayEquals(Assert.java:429)
        at ArrayTests.testReverseInPlace1(ArrayTests.java:59)
        ... 32 trimmed
Caused by: java.lang.AssertionError: expected:<3> but was:<5>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at org.junit.internal.ExactComparisonCriteria.assertElementsEqual(ExactComparisonCriteria.java:8)
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:76)
        ... 38 more
2) testReversed1(ArrayTests)
arrays first differed at element [0]; expected:<5> but was:<0>
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:78)
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:28)
        at org.junit.Assert.internalArrayEquals(Assert.java:534)
        at org.junit.Assert.assertArrayEquals(Assert.java:418)
        at org.junit.Assert.assertArrayEquals(Assert.java:429)
        at ArrayTests.testReversed1(ArrayTests.java:52)
        ... 32 trimmed
Caused by: java.lang.AssertionError: expected:<5> but was:<0>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at org.junit.internal.ExactComparisonCriteria.assertElementsEqual(ExactComparisonCriteria.java:8)
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:76)
        ... 38 more
3) testaverageWithoutLowest3(ArrayTests)
java.lang.AssertionError: expected:<4.5> but was:<3.0>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:555)
        at org.junit.Assert.assertEquals(Assert.java:685)
        at ArrayTests.testaverageWithoutLowest3(ArrayTests.java:68)

FAILURES!!!
Tests run: 3,  Failures: 3
````
![fail](lab-report2-fail.png)

**After change**
````md
public class ArrayExamples {

  // Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    for(int i = 0;i<newArray.length;i++){
        arr[i] = newArray[i];
    }
    
  }

  // Returns a *new* array with all the elements of the input array in reversed
  // order
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }

  // Averages the numbers in the array (takes the mean), but leaves out the
  // lowest number when calculating. Returns 0 if there are no elements or just
  // 1 element in the array
  static double averageWithoutLowest(double[] arr) {
    int count = 0;
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      if(num != lowest) { 
        sum += num; 
        count++;
      }
    }
    return sum / (count);
  }


} 

````
**reverseInPlace**: This method changes it's element in the first place to last place, the second to last-1 place. When it get to the second half of the array, it will have the same element as before because the first half has already been changed. One solution is to store the reversed array in another array and let the original array equal to the reversed array.

**reversed**: This method let empty array as every element of the original array therefore, we will return an empty array. One solution is to assign the empty array equal to the original array from the back to get the reversed array.

**averageWithoutLowest**: If there are two lowest number, then the array need to minus 2 at the end. However, it only minus1, which assume there are one lowest number everytime. Therefore, we can count how many lowest number in the for loop and divide sum by that instead of array length-1

**Part 2**-------------------------------------------------------------------------------------------------------------------------------------------------------------






