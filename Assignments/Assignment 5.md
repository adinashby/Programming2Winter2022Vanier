# Assignment 5

## **Due Date:** 

Apr-29 23:55:00. **Late submission will directly be marked as 0**.

## **Submission:**

**Please submit a `.zip` file for this assignment that includes the following `.java` files**.

**Full Score**: 100

## **Knowledge Points**  of  This  Assignment

1. Exception Handling
2. Text I/O
3. Serialization and Deserialization

***

## Task 1

### Requirement

Define a new exception class: `InvalidNumberException`, which contains two constructors:
1. Default constructor
2. Constructor with `String` as a parameter

***

## Task 2

### Requirement

1. Create a method `Integer[][] generateRandomMatrix(int row, int col, double upperBound)` to generate some random numbers in range `[1, upperBound]`. 
   
    * If  the `upperBound` is lower than `1`, replace it by a default value of `10`. 
    * For each number in the matrix, there needs to be a `1/5` chance it will be a `null`, a `2/5` chance it will be a normal random number, and a `2/5` chance it will be a negative random number (generate a random number and then multiply it by `-1`)


2. Create a method `String[][] calcResult(Integer[][] numss)` that takes a matrix and then reads the values from the left to the right, and from the top to the bottom. This value will be stored as `num1`. Then, it should read from the right to the left, and from the bottom to the top. This value will be stored as `num2`.
   * Calculate `num1/num2` as a result, with two decimals.
   * If any value of `num1` or `num2` is negative, throw the `InvalidNumberException`.
   * The method should be able to handle `ArithmeticException`, `NullPointerException`, and `InvalidNumberException`.
   * If it is an `ArithmeticException`, put an `A` in the result. If it is a `NullPointerException`, put a `N` in the result. If it is an `InvalidNumberException`, put a `I` in the result.

*Example*

```java
// input matrix
1       2       3
null    5       0
7      -8       0

/**
Cell 1: num1 = 1, num2 = 0, result = 1 / 0 -> A 
Cell 2: num1 = 2, num2 = -8, result = 2 / -8 -> I
Cell 3: num1 = 3, num2 = 7, result = 3 / 7 -> 0.43
Cell 4: num1 = null, num2 = 0, result = null / 0 -> N
Cell 5: num1 = 5, num2 = 5, result = 5 / 5 -> 1.00
Cell 6: num1 = 0, num2 = null, result = 0 / null -> N
Cell 7: num1 = 7, num2 = 3, result = 7 / 3 -> 2.33
Cell 8: num1 = -8, num2 = 2, result = -8 / 2 -> I
Cell 9: num1 = 0, num2 = 1, result = 0 / 1 -> 0.00
*/
    
// result
A       I       0.43
N       1.00    N              
2.33    I       0.00
```

## Task 3

### Requirement

Create a class of `Animal` with

1. Data members:
   1. `String id`
   2. `String name`
   3. `String type`
   4. `String gender`
   5. `int age`
   6. `int healthStatus`: a value of {-1, 0, 1, 2,}: 0 means healthy, 1 means a little sick, 2 means very sick, -1 means un-identical
2. Methods:
   1. Default constructor
   2. Constructor with `name`, `gender` and `age`
   3. `hashCode` and `equals`
   4. `toString`
   5. getters and setters 

Create a class of `Cat` that extends from `Animal`, with 

1. Additional Data Member 
   1. `boolean longFur`
2. Additional Methods
   1. constructor with `name`, `gender`, `age` and `longFur`
   2. `hashCode` and `equals`
   3. `toString`
   4. getters and setters 

Create a class of `Dog` that extends from `Animal`, with 

1. Additional Data Member 
   1. `String suitFor`				// "apartment" or "house"
2. Additional Methods
   1. constructor with `name`, `gender`, `age` and `suitFor`
   2. `hashCode` and `equals`
   3. `toString`
   4. getters and setters 

***

## Task 4

### Requirement

Create a class of `Shelter`, which contains

1. Static variables:
    1. `List<Animal> animals`
2. Methods: 
    1. `addAnimal(Animal animal)`: to add an animal to the `animals`, it will call `serializeAnimals()` automatically to save the data
    2. `removeAnimal(Animal animal)`: to remove an animal from the `animals`, it will call `serializeAnimals()` automatically to save the data.
    3. `searchUnhealthyAnimals()`: to find all animals whose `healthStatus` is not `0`.
    4. `serializeAnimals(String path)`: to serialize the `animals` into a `.ser` file
    5. `deserializeAnimals(String path)`: to deserialize the .`ser` file into `animals`  
    6. `readAnimalFile(Strin path)`: to read a `.csv` file and returns all animals in a collection
    7. `writeAnimalFile(String path)`: to write a `.csv` file that contains all animals.
    8. `writeAnimalFile(String path, String suitFor)`: to write a `.csv` file that contains all animals, but only with the specific suit type. 
       1. If the input is `house`, then list all cats, and dogs with `house`
       2. If the input is `apartment`, then list all cats, and dogs with `apartment`

Note: Please create an initial `data.csv` file in the project folder by yourself:

```
id,name,type,gender,age,healthStatus,house/apartment,fur
1,kiki,cat,female,3,0,,long
2,tiger,dog,male,6,0,house
3,snow,cat,male,4,1,,short
4,lucky,cat,female,6,0,,short
5,angle,cat,female,2,0,,long
6,chase,dog,female,5,1,house
7,jojo,dog,male,10,2,apartment
8,lith,cat,female,0,-1,,short
9,copain,dog,male,5,0,apartment
10,charlie,dog,male,3,2,apartment
```
