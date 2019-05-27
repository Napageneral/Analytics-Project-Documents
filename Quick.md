# Quick and Dirty Style Guide

## Meaningful Names
- Avoid **disinformation**.
  - Don’t call a variable an `accountList` if the type is not part of the `List` class.
  - `accountList As Queue` **is bad**.
  - `accountList As List` **is fine**.
  - `accounts` is better.
- Use **intention-revealing** names.
  - `Dim daysPassed As Integer` compared to `Dim d As Integer`.
- **Don’t use similar looking names** like `methodThatCallsUserAccount` and `methodThatCallsUserAccountInfo`.
- Use pronounceable names.
- Use searchable names.
- Class names should be nouns like Customer, Account, etc. not a verb.
- Don’t hesitate to rename items in an existing code base.

## Methods
- Methods should be small, **about 20 lines is ideal** (although not a strict rule).
- Code within an if, else, while, etc. block should **ideally be one line long** - a method call.
  - Methods should not hold nested structures.
- **Methods should only do one task**, if they do more, split them.
- Use **descriptive and lengthy names**.
  - `downloadPagesForTestingHTML` vs `downloadHTML`.
- The ideal number of method arguments is zero, one, or two (in that order).
- If a method transforms an input argument, the transformation should be returned by the method.
- Flag arguments (passing a boolean) in a method is bad practice.
  - Instead of a method called `render(true)` that contains both conditions, it should be split into two functions.
  - Example: `renderForSuite()` and `renderForSingleTest()`.
- When a method takes too many arguments, they can likely be **wrapped into another class**.
  - `Method makeCircle(ByVal x As Double, ByVal y As Double, ByVal radius As Double) As Circle` vs `Method makeCircle(ByVal center As Point, ByVal radius As Double) As Circle`.
- **Avoid ByRef arguments**.
  - `Public sub appendFooter(ByRef report As String)` vs `report.appendFooter()`.
- A method should either **change the state** or **return some information** of an object, not both.
  - `Sub set(ByVal attribute As String, ByVal value As String)` would be called as `set(“username”, “bob”)`.
  - `if(set(“username”, “bob”))` **is bad**.
  - Can be improved by splitting up into `Method attributeExists(String attribute) as Boolean` and `Sub setAttribute(String attribute, String value)`.
  - `If attributeExists(“username”) Then setAttribute(“username”, “bob”)` **is good**.
- Methods **can be messy and complicated at first**, as long as they are **refined afterwards**.

## Comments
- The use of comments **compensates for failure** to express ourselves in code.
- Old comments possibly become irrelevant over time.
- Programmers should be able to update/maintain comments, but that energy **should go toward making code clear and expressive**.
  - `If employee.flags And employee.age > 65 ‘Checks employee benefits eligibility` **<-bad comment**.
  - `If employee.isEligibleForFullBenefits()` **<- no comment needed**.
- **Good types of comments**.
  - Legal, lawful, or regulatory comments.
  - Informative comments that discuss formatting.
  - Explanation of intent, why the implementation was done in a certain way.
  - Clarification of something obscure that cannot be changed.
  - Warnings.
  - To-do comments that serve as reminders.
  - Stressing the importance of an item.
- **Bad types of comments**.
  - Comments written for every single variable and method.
  - Change log comments.
  - Restating the obvious and redundancy.
  - Commented-out code.
  - Too much information.

## Formatting
- Make liberal use of the **#Region functionality** 
  - #Regions that can be reasonably expected in most every class: #Globals, #Constructors, #Public Methods, #Private Methods
  - Other common #Regions: #BO Calls, #Overrides, interface implementations...
- Closely related functions and variables should be **vertically close** to each other.
  - Non-member variables should be declared immediately before their first usage.

## Objects and Data Structures
- We don’t want to expose the implementation of data structures.
  - Use abstractions to hide implementation. Consider the following:
  - ```vbnet
	Public Interface Vehicle
		Method getFuelTankCapacityInGallons() As Double
		Method getGallonsOfGasoline() As Double
    ```
  - ```vbnet
	Public Interface Vehicle
		Method getPercentFuelRemaining() As Double    
    ```
  - The first option uses concrete cases that are merely accessors of variables.
  - The second option hides the form of the data using the percentage.
  - The second option is preferable because the details of the data are hidden.
- **Objects hide their data behind abstractions** and expose functions to operate on that data.
  - **Object-oriented code** allows new classes to be added without changing existing functions.
    - OOP makes it hard to add new functions because all classes must change.
    - If you want to add new data types rather than functions, use OOP.
- **Data structures expose their data** and have no meaningful functions.
  - **Procedural code** allows ne functions to be added without changing the existing data structures.
    - Hard to add new data structures because all functions must change.
    - If you want to add new functions rather than data types, use procedural code.
- A module **should not know** about the inner workings of the objects being manipulated.	
  - A method should not invoke methods on objects returned by other functions.
  - `Dim output As String = text.getValue().getDirectory()` <- calls getDirectory() on the return value of. getValue(), **BAD**
- **A Data Transfer Object (DTO)** is a class with **public variables and no functions**.
  - Useful for communicating with databases or providing a large number of variables to a method at once.
- Objects **expose behavior and hide data**.
  - It’s easy to add new objects without changing existing behaviors.
  - It’s hard to add new behaviors to existing objects.
- Data structures **expose data but have no significant behavior**.
  - It’s easy to add new behaviours to existing data structures.
  - It’s hard to add new data structures to existing functions.

## Boundaries
- Create accessors so that the data **cannot be directly manipulated**.
  - Instead of passing an object around, **create a getter method**.
  - The object would be private, while the getter method is public.
  - This way the data in the object can be accessed, but not cleared.

## Classes
- Classes should be **small**, with a low number of instance variables.
- **Single Responsibility Principle (SRP)**, class should have one responsibility.
- Organize system such that **new changes minimize the risk** that the entire system won’t method.
  - Consider splitting into many classes, **even if they only have one method each**.
  - **Avoid** classes that directly depend on others.
- Concrete classes contain implementation details.
- Abstract classes represent concepts only.

## Concurrency
- Concurrency ***can*** **increase performance when there is a lot of wait time**.
  - Not all forms of concurrency are equal: there is a lot of wait time to grab data from a database, but doing so concurrently may reduce performance compared to other means.
- Your design changes when writing concurrent programs.
  - Concurrency is **complex**, even for simple problems.
  - It requires a **fundamental change in design** strategy.	 

## Environment
- Your development environment settings should be set to the strictest possible settings.
  - **My Project > Compile > Option Explicit: On, Option Strict: On, Option Infer: Off, Warning Configurations should have all Notifications set to Error**.
