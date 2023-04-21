# Lab 8 : Unit Testing with JUnit

## Student Name : Jay Shukla

## Student ID: 202001440

1. Create a JAVA project in Eclipse named "Lab8" and create a package inside it with name **"mypackage"**

![image](https://user-images.githubusercontent.com/123619898/233591384-5536c65c-1588-476e-9887-8c3d0a9047c4.png)

2.Then create a class with name Boa and then add the given code inside it.

![image](https://user-images.githubusercontent.com/123619898/233591563-1158775a-7b0e-4f33-bb20-baf58873548c.png)


3.Then create a JUnit test file for the Boa Class with name **"BoaTest"**
```
import org.junit.Assert;
import org.junit.Test;
public class BoaTest {
  @Test
  public void testIsHealthy() {
    Boa healthyBoa = new Boa("Lucy", 8, "granola bars");
    Assert.assertTrue(healthyBoa.isHealthy());
    Boa sickBoa = new Boa("Sneaky", 6, "mice");
    Assert.assertFalse(sickBoa.isHealthy());
  }
  @Test
  public void testFitsInCage() {
    Boa smallBoa = new Boa("Tiny", 2, "rats");
    Assert.assertTrue(smallBoa.fitsInCage(5));
    Assert.assertFalse(smallBoa.fitsInCage(1));
    Boa largeBoa = new Boa("Goliath", 20, "chicken");
    Assert.assertTrue(largeBoa.fitsInCage(25));
    Assert.assertFalse(largeBoa.fitsInCage(10));
  }
}
```
![image](https://user-images.githubusercontent.com/123619898/233591778-ada1dfc3-4e78-422f-a855-3f490f128e2c.png)


4.Then modify the setUp method to initialize the variables.
```
public class BoaTest {
    private Boa jen;
    private Boa ken;
    
    @Before
    public void setUp() throws Exception {
        jen = new Boa("Jennifer", 2, "grapes");
        ken = new Boa("Kenneth", 3, "granola bars");
    }
    
    // write test methods here
}
```
5.Then implement tests for the given two functions testIsHealthy() and testFitsInCage(). ![image](https://user-images.githubusercontent.com/123619898/233591871-9349ab7a-0446-4c8b-a5ea-66583017e868.png)

For testing the fitsInCage() function, there is no need to write tests for both jen and ken objects as the function is same for both and the output of test cases depends only whether the given lenght is greater than,less than or equal to actual length of object.The behaviour will be similar in both cases.

6.Then run the Junit test file and see that all the tests are passed. There are no red bars in the output. ![image](https://user-images.githubusercontent.com/123619898/233591928-4c57eb2d-9509-4be0-adc1-34fe5fa8e68b.png)

It can be seen that 2 out of 2 test cases have been passed.

7.Then add a new method to the Boa class with name lenghtInInches() to get the length in inches.
```
public class Boa {
    private String name;
    private int length; // the length of the boa, in feet
    private String favoriteFood;
    public Boa(String name, int length, String favoriteFood) {
        this.name = name;
        this.length = length;
        this.favoriteFood = favoriteFood;
    }
    // returns true if this boa constrictor is healthy
    public boolean isHealthy() {
        return this.favoriteFood.equals("granola bars");
    }
    // returns true if the length of this boa constrictor is
    // less than the given cage length
    public boolean fitsInCage(int cageLength) {
        return this.length < cageLength;
    }
    // produces the length of the Boa in inches
    public int lengthInInches() {
        return this.length * 12;
    }
}
```
![image](https://user-images.githubusercontent.com/123619898/233592021-d1982768-49b2-41a2-9ac3-c0ec5d9eea1d.png)

As the length of the Boa is given in feet, to convert it into inches, multiply length with 12 and return the value.

8.Then I wrote another test case for this new method and ran the 3 test cases together. ![image](https://user-images.githubusercontent.com/123619898/233592378-36e73f16-d23b-4ac2-bc24-4aaaaa9b948b.png)

Thus, test cases have been written for the given Boa class and all the three methods have been tested with required Junit test cases.

Here's an example of a new test case in the BoaTest class that tests the lengthInInches() method:
```
import static org.junit.Assert.assertEquals;
import org.junit.Before;
import org.junit.Test;
public class BoaTest {
    private Boa jen;
    private Boa ken;
    @Before
    public void setUp() throws Exception {
        jen = new Boa("Jennifer", 2, "grapes");
        ken = new Boa("Kenneth", 3, "granola bars");
    }
    @Test
    public void testLengthInInches() {
        assertEquals(24, jen.lengthInInches());
        assertEquals(36, ken.lengthInInches());
    }
}
```
This new test case checks that the lengthInInches() method returns the expected value when called on each of the Boa objects created in the setUp() method. It uses the assertEquals() method to compare the expected value to the actual value returned by the lengthInInches() method. The @Test annotation indicates that this is a test method that should be run by JUnit.
