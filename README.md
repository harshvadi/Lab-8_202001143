# Lab-8_202001143

### Name: Harsh Vadi
### ID: 202001143

## 1. Create a new Eclipse project, and within the project create a package.

![image](https://user-images.githubusercontent.com/75617265/233312509-84580fb9-2703-4f8f-87ad-111c2776056e.png)

## 2. Create a class for a Boa.

![image](https://user-images.githubusercontent.com/75617265/233312219-a93ff6d8-cac4-4ba7-b5ac-d13b6da23470.png)

## 3. Creating a test case for the class Boa.

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
![image](https://user-images.githubusercontent.com/75617265/233316831-6807a31a-5d04-4c19-b595-73dce79f32bf.png)

## 4. Modify the setUp() method

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
![image](https://user-images.githubusercontent.com/75617265/233317442-1662aeea-4296-45be-ada9-a3f3da36da43.png)

## 5.

### 5.1 Modify the testIsHealthy() method so that it checks the results of activating the isHealthy() method on the two Boa objects you created in setup().

```
@Test
public void testIsHealthy() {
    // check that jen is not healthy
    assertFalse(jen.isHealthy());
    
    // check that ken is healthy
    assertTrue(ken.isHealthy());
}
```

### 5.2 Modify the testFitsInCage() method to test the results of that method.

```
@Test
public void testFitsInCage() {
    // Test for jen
    assertFalse(jen.fitsInCage(1)); // cage length is less than length of boa
    assertTrue(jen.fitsInCage(2)); // cage length is equal to length of boa
    assertTrue(jen.fitsInCage(3)); // cage length is greater than length of boa

    // Test for ken
    assertFalse(ken.fitsInCage(2)); // cage length is less than length of boa
    assertTrue(ken.fitsInCage(3)); // cage length is equal to length of boa
    assertTrue(ken.fitsInCage(4)); // cage length is greater than length of boa
}
```

## 6. Run the testcases

![image](https://user-images.githubusercontent.com/75617265/233320065-405673e9-c331-473f-9c08-d26ecaed4b84.png)

## 7. 

### 7.1 Add a new method to the Boa class

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

### 7.2 Add a new test case to the BoaTest class that tests the lengthInInches() method.

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
