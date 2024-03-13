# LAB REPORT 5

## Part 1 

CONVERSATION 

User: Prasham 
Hi! I am getting these errors while running these commands. Can you kindly help me out with what the potential issue might be? 

````
prashamshah@Prashams-MacBook-Pro lab3 % javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar ArrayExamples.java                               
prashamshah@Prashams-MacBook-Pro lab3 % java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ArrayExamples ArrayTests

JUnit version 4.13.2
.E.....
Time: 0.004
There was 1 failure:
1) initializationError(ArrayExamples)
org.junit.runners.model.InvalidTestClassError: Invalid test class 'ArrayExamples':
  1. No runnable methods
        at org.junit.runners.ParentRunner.validate(ParentRunner.java:525)
        at org.junit.runners.ParentRunner.<init>(ParentRunner.java:102)
        at org.junit.runners.BlockJUnit4ClassRunner.<init>(BlockJUnit4ClassRunner.java:84)
        at org.junit.runners.JUnit4.<init>(JUnit4.java:23)
        at org.junit.internal.builders.JUnit4Builder.runnerForClass(JUnit4Builder.java:10)
        at org.junit.runners.model.RunnerBuilder.safeRunnerForClass(RunnerBuilder.java:70)
        at org.junit.internal.builders.AllDefaultPossibilitiesBuilder.runnerForClass(AllDefaultPossibilitiesBuilder.java:37)
        at org.junit.runner.Computer.getRunner(Computer.java:50)
        at org.junit.runner.Computer$1.runnerForClass(Computer.java:31)
        at org.junit.runners.model.RunnerBuilder.safeRunnerForClass(RunnerBuilder.java:70)
        at org.junit.runners.model.RunnerBuilder.runners(RunnerBuilder.java:125)
        at org.junit.runners.model.RunnerBuilder.runners(RunnerBuilder.java:111)
        at org.junit.runners.Suite.<init>(Suite.java:81)
        at org.junit.runner.Computer$2.<init>(Computer.java:33)
        at org.junit.runner.Computer.getSuite(Computer.java:28)
        at org.junit.runner.Request.classes(Request.java:77)
        at org.junit.runner.JUnitCommandLineParseResult.createRequest(JUnitCommandLineParseResult.java:116)
        at org.junit.runner.JUnitCore.runMain(JUnitCore.java:77)
        at org.junit.runner.JUnitCore.main(JUnitCore.java:36)

FAILURES!!!
Tests run: 6,  Failures: 1

prashamshah@Prashams-MacBook-Pro lab3 % 
````
User: TA

Hi! I can help you out with this bug. It so seems that when you're running your command, ArrayExamples isn't a test class and shouldn't be included in your java command. Your command should instead be : `java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ArrayTests`. Kindly run this command, and let me know if it works!

User: Prasham 

Thanks for your response! I did what you recommended and the tests are now working. 

````
prashamshah@Prashams-MacBook-Pro lab3 % javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar ArrayExamples.java                                
prashamshah@Prashams-MacBook-Pro lab3 % java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ArrayTests 

JUnit version 4.13.2
.....
Time: 0.004

OK (5 tests)
````

User: TA 

Glad to help you out!

**FOLDER STRUCTURE**

````
|-- lib
|-- |-- hamcrest-core-1.3.jar
|-- |-- junit-4.13.2.jar
|-- ArrayExamples.java
|-- ArrayTests.java
````

**FILE INFO**

**Before**

`ArrayExamples.java`

````
public class ArrayExamples {

  // Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i <= arr.length/2; i += 1) {
      int oldElem = arr[i];
      arr[i] = arr[arr.length - i - 1];
      arr[arr.length - i - 1] = oldElem;
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

`ListTests.java`

````
import static org.junit.Assert.*;
import org.junit.Test;

import static org.junit.Assert.assertArrayEquals;
import static org.junit.Assert.assertEquals;

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
  public void testReverseInPlace1() { 
    int[] input1 = {1,2,3,4,5};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{5,3,2,1}, input1);
  }

  @Test
   public void testReversed1() {
    int[] input1 = {2,3,4,5};
    assertArrayEquals(new int[]{5,4,3,2}, ArrayExamples.reversed(input1));
  }

  @SuppressWarnings("deprecation")
  @Test
  public void testAverage() { 
    double[] input1 = {0};
    double[] input2 = {2,5,6,7};

    assertEquals(0.0, ArrayExamples.averageWithoutLowest(input1),0.001);
    assertEquals(6.0, ArrayExamples.averageWithoutLowest(input2), 0.001);
  }


  

}
````

Commands in terminal 

````
prashamshah@Prashams-MacBook-Pro lab3 % javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar ArrayExamples.java                               
prashamshah@Prashams-MacBook-Pro lab3 % java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ArrayExamples ArrayTests
````

**After** 

No changes to ArrayTests.java and ArrayExamples.java

Commands run in the terminal are changed to: 

````
prashamshah@Prashams-MacBook-Pro lab3 % javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar ArrayExamples.java                                
prashamshah@Prashams-MacBook-Pro lab3 % java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ArrayTests
````

## Part 2

During the second half of this quarter, I learned how to use several of Git's features effectively to streamline my workflow. Additionally, I discovered some advanced Vim shortcuts that significantly improved my editing efficiency, allowing me to navigate and edit files more fluidly. These newfound skills not only enhanced my productivity during lab sessions but also provided valuable insights into efficient coding practices for the future. 


