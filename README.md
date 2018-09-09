TDD Session
---

- [TDD Session](#tdd-session)
- [JS Requirements](#js-requirements)
- [C# Requirements](#c-requirements)
- [Summary](#summary)
- [Day 1](#day-1)
- [Day 2](#day-2)
- [Day 3](#day-3)
- [Exercises & Information](#exercises--information)
    - [TDD Habits 1.0: Red, Green, Refactor](#tdd-habits-10-red-green-refactor)
    - [TDD Habits 2.0: Assertion First](#tdd-habits-20-assertion-first)
    - [TDD Habits 3.0: TPP](#tdd-habits-30-tpp)
    - [Fake it, Obvious Implementation, and Triangulation](#fake-it-obvious-implementation-and-triangulation)
    - [Leap Year Exercise](#leap-year-exercise)
    - [FizzBuzz Exercise](#fizzbuzz-exercise)
    - [String Calculator](#string-calculator)
    - [Roman Numerals Exercise](#roman-numerals-exercise)
    - [Copier Exercise](#copier-exercise)
    - [Test Doubles](#test-doubles)
---
## JS Requirements
- Git
- VS Code
- Jest Extension
- Path Intellisense extension
- VSTS account
- NPM installed


[Back to top](#tdd-session)

---
## C# Requirements
- Git
- Visual Studio 2017    
- Resharper extension
- dotnet core 2.*


[Back to top](#tdd-session)

---
## Summary

- 9 hours over 3 days
- Friday 1.5 hour / Monday 3 hours / Tuesday 4.5 hours
- Day 1: Intro and Demonstration
- Day 2: 2 x Class Exercises (FizzBuzz, String Calculator) with a 15 minute Retro for each
- Day 3: Intro to Tranformation Priority Premise (TPP), Roman Numeral Exercise, Test doubles
- Sessions based on [Coaching Program](https://asoscom.atlassian.net/wiki/spaces/OM/pages/753730337/Coaching+Program)


[Back to top](#tdd-session)

---

## Day 1

- Icebreaker
- 1 hour
- Introduce Classic TDD **15 mins**
  - TDD Habits: Red, Green, Refactor
- Do demo of LeapYear **45 mins**

**Learning Objective**: Students understand the TDD cycle (Red, Green, Refactor).

[Back to top](#tdd-session)

---

## Day 2
- Icebreaker
- 3 hours total
- Fizzbuzz Exercise **45 mins**
- Fizz Buzz Retro **15 mins**
- Introduce TDD Habits 2.0 **20 mins**
- String Calculator Exercise **45 - 75 mins**
- String Calculator Retro **15 mins**

**Learning Objective**: Student can use the TDD cycle (Red, Green, Refactor) to drive the code. Just solving the code does not count.

[Back to top](#tdd-session)

---
## Day 3
- Icebreaker
- 4 hours total
- Introduce TPP **30 mins**
- Roman Numeral Exercise TDD & TPP **120 mins**
- TPP Retro **15 mins**
- Introduction to Test Doubles **95 mins**

**Learning Objective**: Students should apply the TDD habits Principles, Red habits, Green habits and Refactor habits


[Back to top](#tdd-session)

---
___
Exercises & Information
---


### TDD Habits 1.0: Red, Green, Refactor

- General rules
    - Tests should test one thing only and have one assertion
    - Don't refactor with failing test (don’t refactor on red)
    - Organize your unit tests to reflect your production code (similar project structure)
    - Keep your tests and production code separate
    - Test behaviours not technical implementation (not properties etc)
    - Test names are business oriented
        - Don't leak implementation details into test names
- Red
    - Create more specific tests to drive a more generic solution (Triangulate)
    - See the test fail for the right reason
    - Ensure you have meaningful feedback from failing tests
    - Organize your test in Arrange, Act and Assert blocks
        - Arrange (aka Given) – all necessary preconditions and inputs.
        - Act (aka When) – on the object or method under test.
        - Assert (aka Then) – that the expected results have occurred.
- To Green
    - Write the simplest code to pass the test
    - Don't worry about writing efficient code, this is cleaned up in the Refactor stage

- Green -> Refactor
    - Test code must also be clean and refactored
    - Use the Rule of 3 to tackle duplication
        - Code can be copied once, but that when the same code is used three times, it should be abstracted. Or if you need something once, build it. If you need something twice, pay attention. If you need it a third time, abstract it.
        - Keep in mind that duplication is cheaper than the wrong abstractions

[Back to top](#tdd-session)

---

### TDD Habits 2.0: Assertion First


**Organize your test in Arrange, Act and Assert blocks***

Tests are about assertions (ASSERT). For an assertion to be possible you need to take an action on the code you are asserting (ACT). Sometimes to take an action you need to create some context to enable the action (Arrange).

- General rules
    - Tests should test one thing only and have one assertion
    - Don't refactor with failing test (don’t refactor on red)
    - Organize your unit tests to reflect your production code (similar project structure)
    - Keep your tests and production code separate
    - Test behaviours not technical implementation (not properties etc)
    - Test names are business oriented
        - Don't leak implementation details into test names
- Red
    - Create more specific tests to drive a more generic solution (Triangulate)
    - See the test fail for the right reason
    - Ensure you have meaningful feedback from failing tests
    - **NEW HABIT** Write the assertion first and work backwards
    - Organize your test in Arrange, Act and Assert blocks
        - Arrange (aka Given) – all necessary preconditions and inputs.
        - Act (aka When) – on the object or method under test.
        - Assert (aka Then) – that the expected results have occurred.
- To Green
    - Write the simplest code to pass the test
    - Don't worry about writing efficient code, this is cleaned up in the Refactor stage

- Green -> Refactor
    - Test code must also be clean and refactored
    - Use the Rule of 3 to tackle duplication
        - Code can be copied once, but that when the same code is used three times, it should be abstracted. Or if you need something once, build it. If you need something twice, pay attention. If you need it a third time, abstract it.
        - Keep in mind that duplication is cheaper than the wrong abstractions

**Example of Assertion First:**
```csharp
// In Order of writing:
assert fizzBuzzed == "1"
var fizzBuzzed = fizzBuzzer.FizzBuzz(1)
var fizzBuzzer = new FizzBuzzer()

// Final code
var fizzBuzzer = new FizzBuzzer() 
var fizzBuzzed = fizzBuzzer.FizzBuzz(1) 
assert fizzBuzzed == "1" 
```

[Back to top](#tdd-session)

---

### TDD Habits 3.0: TPP

If we go back to how we evolve code in TDD, we have these methods:

- **Fake it** is where you just return the exact value you need. If your test expects a zero from a method, use a “return 0;” statement. Usually you use this when you cannot tell how to implement certain functionality, or your previous steps were too large and you cannot figure out what went wrong. Something that works is better than something that doesn’t work!
- Use **obvious implementation** when you are pretty sure of the code you need to write, so write it and see if the test passes. The majority of the time you will use this method to move forward with TDD quickly.
- **Triangulation** is where you want to generalize certain behaviour, but are not sure how to do it. So you start with fake it and add additional tests that force the code to be more generic along a certain dimension.
- “Use **obvious implementation**” is ambiguous, what does “obvious implementation” mean? It may mean something for you and something else for another developer. The transformations on the following table are a way to clarify ambiguity the “obvious implementation”.

| #   | Transormation                | Start Code             | End Code                                        |
| --- | ---------------------------- | ---------------------- | ----------------------------------------------- |
| 1   | {} -> nil                    | {}                     | [return] nil                                    |
| 2   | Nil -> constant              | [return] nil           | [return] “1”                                  |
| 3   | Constant -> constant+        | [return] “1”         | [return] “1” + “2”                          |
| 4   | Constant -> scalar           | [return] “1” + “2” | [return] argument                               |
| 5   | Statement -> statements      | [return] argument      | [return] min(max(0, argument), 10)              |
| 6   | Unconditional -> conditional | [return] argument      | if(condition) [return] argument else [return] 0 |
| 7   | Scalar -> array              | dog                    | [dog, cat]                                      |
| 8   | Array -> container           | [dog, cat]             | {dog=”DOG”, cat=”CAT”}                      |
| 9   | Statement -> tail recursion  | a + b                  | a + recursion                                   |
| 10  | If -> loop                   | if(condition)          | loop(condition)                                 |
| 11  | Statement -> recursion       | a + recursion          | recursion                                       |
| 12  | Expression -> function       | today – birth          | CalculateBirthDate()                            |
| 13  | Variable -> mutation         | day                    | var Day = 10; Day = 11;                         |
| 14  | Case/Switch                  |                        |


Notes:
- Help with if's to recursion
- Help with if's to loop

Why:
- If statements vs Dictionary, memory vs cpu trade off (dictionary is more memory)
- Delay 12, expression to function, so you can spot patterns and still refactor
- Delay 13, variable to mutation, as mutation is unwanted behaviour and easily leads to bugs
- Delay 14, case/switch, as it is a code smell and is the most complicated structure making it hard to refactor and understand

*Transformations on the top of the list should be preferred to those that are lower. It is better (or simpler) to change a constant into a variable than it is to add an if statement. So when making a test pass, you try to do so with transformations that are simpler (higher on the list) than those that are more complex. Please do not take this table literally. This is a starting point. Adapt this table to your language and environment.*

- General rules
    - Tests should test one thing only
    - Test one logical assertion
    - Don't refactor with failing test (don’t refactor on red)
    - Organize your unit tests to reflect your production code (similar project structure)
    - Keep your tests and production code separate
    - Test behaviours not technical implementation (not properties etc)
    - GivenWhenThen names that are business oriented
        - Don't leak implementation details into test names
- Red
    - Create more specific tests to drive a more generic solution (Triangulate)
    - Give your test meaningful names (behaviour / goal-oriented) - that reflects your business domain
    - See the test fail for the right reason
    - Ensure you have meaningful feedback from failing tests
    - Write the assertion first and work backwards
    - Organize your test in Arrange, Act and Assert blocks
        - Arrange (aka Given) – all necessary preconditions and inputs.
        - Act (aka When) – on the object or method under test.
        - Assert (aka Then) – that the expected results have occurred.
        - Structure the code in tests to reflect these concepts.
- To Green
    - Write the simplest code to pass the test
    - Write any code that makes you get to the refactor phase quicker
    - It is okay to write any code that you might improve at a later stage
    - **NEW HABIT** Consider using Transformation Priority Premise
- Green -> Refactor
    - Treat tests as first-class code
    - Use the Rule of 3 to tackle duplication
        - Code can be copied once, but that when the same code is used three times, it should be abstracted. Or if you need something once, build it. If you need something twice, pay attention. If you need it a third time, abstract it.
        - Keep in mind that duplication is cheaper than the wrong abstractions


[Back to top](#tdd-session)

---

### Fake it, Obvious Implementation, and Triangulation

- **Fake it** is where you just return the exact value you need. If your test expects a zero from a method, use a “return 0;” statement. Usually you use this when you cannot tell how to implement certain functionality, or your previous steps were too large and you cannot figure out what went wrong. Something that works is better than something that doesn’t work!
- Use **obvious implementation** when you are pretty sure of the code you need to write, so write it and see if the test passes. The majority of the time you will use this method to move forward with TDD quickly.
- **Triangulation** is where you want to generalize certain behaviour, but are not sure how to do it. So you start with fake it and add additional tests that force the code to be more generic along a certain dimension.
- “Use **obvious implementation**” is ambiguous, what does “obvious implementation” mean? It may mean something for you and something else for another developer. This ambiguity will be clarified in the 3rd session with TPP. For now, just write what you find the most obvious and simple to you.

[Back to top](#tdd-session)

---
### Leap Year Exercise

- Write a function that returns true or false depending on whether its input integer is a leap year or not.
- A year will be a leap year if it is divisible by 4 but not by 100. If a year is divisible by 4 and by 100, it is not a leap year unless it is also divisible by 400.
- For example, years such as 1996, 1992, 1988 and so on are leap years because they are divisible by 4 but not by 100. For century years, the 400 rule is important. Thus, century years 1900, 1800 and 1700 while all still divisible by 4 are also exactly divisible by 100. As they are not further divisible by 400, they are not leap years


[Online Leap Year Calculator](http://www.onlineconversion.com/leapyear.htm)

**Starting Point**:
```csharp

// Start with bad naming on test, variables, methods
// Quiz students and refactor to more appropriate names

public static bool IsLeapYear(int year)
{
    // code
}

public class LeapYearCalculatorShould(){

    [Test]
    public void MarkYearOneAsANonLeapYear()
    {
        // Arrange
        var input = 1; 
        var expected = false;

        // Act
        var actual = IsLeapYear(input);

        // Assert
        Assert.That(actual, Is.EqualTo(expected));
    }
}

```

[Back to top](#tdd-session)

---
### FizzBuzz Exercise

- Write a program that prints the numbers from 1 to 100. 
- For for multiples of 3 print "Fizz" instead of the number
- For the multiples of 5 print "Buzz"
- For numbers which are multiples of both 3 and 5 print "FizzBuzz"


**Sample output:**
```
1
2
Fizz
4
Buzz
Fizz
7
8
Fizz
Buzz
11
Fizz
13
14
FizzBuzz
16
17
Fizz
19
Buzz
... etc up to 100
```

[Back to top](#tdd-session)

---
### String Calculator

- Create a simple String Calculator with a method `public int Add(string numbers)`
    - The method can take 0, 1 or 2 numbers, and will return their sum (for an empty string it will return 0) for example “” or “1” or “1,2”
    - Start with the simplest test case of an empty string and move to 1 and two numbers
- Allow the Add method to handle an unknown amount of numbers
- Allow the Add method to handle new lines between numbers (instead of commas).
    - The following input is ok: “1\n2,3” (will equal 6)
    - The following input is NOT ok: “1,\n” (not need to prove it - just clarifying)
- Support different delimiters (except for '-')
    - To change a delimiter, the beginning of the string will contain a separate line that looks like this: “//[delimiter]\n[numbers…]” for example “//;\n1;2” should return three where the default delimiter is ‘;’ .
    - The first line is optional. all existing scenarios should still be supported
- Calling Add with a negative number will throw an exception “negatives not allowed” - and the negative that was passed.if there are multiple negatives, show all of them in the exception message
- Numbers bigger than 1000 should be ignored, so adding 2 + 1001 = 2
- Delimiters can be of any length with the following format: “//[delimiter]\n” for example: “//[***]\n1***2***3” should return 6 (include the square brackets)
- Allow multiple delimiters like this: “//[delim1][delim2]\n” for example “//[*][%]\n12%3” should return 6.
- Make sure you can also handle multiple delimiters with length longer than one char

[Back to top](#tdd-session)

---
### Roman Numerals Exercise

- Given a positive integer number (eg 42) determine its Roman numeral representation as a String (eg "XLII").
- You cannot write numerals like IM for 999. Wikipedia states "Modern Roman numerals are written by expressing each digit separately starting with the leftmost digit and skipping any digit with a value of zero."

[Online Roman Numeral Calculator](https://www.thecalculatorsite.com/misc/romannumerals.php)

Examples:

```
1 -> "I" | 10 -> "X" | 100 -> "C" | 1000 -> "M"
2 -> "II" | 20 -> "XX" | 200 -> "CC" | 2000 -> "MM"
3 -> "III" | 30 -> "XXX" | 300 -> "CCC" | 3000 -> "MMM"
4 -> "IV" | 40 -> "XL" | 400 -> "CD" | 4000 -> "MMMM"
5 -> "V" | 50 -> "L" | 500 -> "D" |
6 -> "VI" | 60 -> "LX" | 600 -> "DC" |
7 -> "VII" | 70 -> "LXX" | 700 -> "DCC" |
8 -> "VIII" | 80 -> "LXXX" | 800 -> "DCCC" |
9 -> "IX" | 90 -> "XC" | 900 -> "CM" |

1990 -> "MCMXC" (1000 -> "M" + 900 -> "CM" + 90 -> "XC")
2008 -> "MMVIII" (2000 -> "MM" + 8 -> "VIII")
99 -> "XCIX" (90 -> "XC" + 9 -> "IX")
47 -> "XLVII" (40 -> "XL" + 7 -> "VII")
```

[Back to top](#tdd-session)

---
### Copier Exercise

- The character copier is a simple class that reads characters from a source and copies them to a destination one character at a time.
- When the method Copy is called on the copier then it should read characters from the source and copy them to the destination until the source returns a newline (‘\n’). 
- The exercise is to implement the character copier using test doubles for the source and the destination. Try using mocks written with a mocking framework.

Start with these definitions:
```
public class Copier
{
	public Copier(…) {}
	public void Copy() {}
}

public interface ISource
{
	char GetChar();
}

public interface IDestination
{
	void SetChar(char character);
}
```

[Back to top](#tdd-session)

---
### Test Doubles

**Summary:**
- Introduction to Test Doubles terminology
    - Mocks
    - Stubs
    - Best practices
    
Test doubles is an extension to Test-Driven Development that supports good Object-Oriented design by guiding the discovery of a coherent system of types within a code base. It turns out to be less interesting as a technique for isolating tests from third-party libraries than is widely thought.

**Different types of test doubles**
- Dummy objects are passed around but never actually used. Usually, they are just used to fill parameter lists.
- Stubs provide canned answers to calls made during the test, usually not responding at all to anything outside what's programmed in for the test. Stubs may also record information about calls, such as an email gateway stub that remembers the messages it 'sent', or maybe only how many messages it 'sent'.
- Fake objects actually have working implementations, but usually take some shortcut which makes them not suitable for production (an in-memory database is a good example).
- Mocks are pre-programmed with expectations which form a specification of the calls they are expected to receive. They can throw an exception if they receive a call they don't expect and are checked during verification to ensure they got all the calls they were expecting.
- Spies are stubs that also record some information based on how they were called. One form of this might be an email service that records how many messages it was sent.


**Principles**

*Allow/Setup Queries; Expect/Verify Commands*

- Use Mocks for Commands
    - Commands are all about side effects, and Mocks are all about Behaviour Verification: that is, that side effects occurred
- Use Stubs for Queries
    - Stubs mainly exist to 'make happy noises', and one of the ways they have to do that is to return data from dependencies when return data is required.

*Only mock/stub classes you own*

> Mock Objects is a design technique so programmers should only write mocks for types that they can change. Otherwise, they cannot change the design to respond to requirements that arise from the process. Programmers should not write mocks for fixed types, such as those defined by the runtime or external libraries. Instead, they should write thin wrappers to implement the application abstractions in terms of the underlying infrastructure. Those wrappers will have been defined as part of a need-driven test. We have found this to be a powerful insight to help programmers understand the technique. It restores the pre-eminence of the design in the use of Mock Objects, which has often been overshadowed by its use for testing interactions with third-party libraries.

*Specify as little as possible in a test*

> When testing with Mock Objects it is important to find the right balance between an accurate specification of a unit's required behaviour and a flexible test that allows easy evolution of the code base. One of the risks with TDD is that tests become “brittle”, that is they fail when a programmer makes unrelated changes to the application code. They have been over-specified to check features that are an artefact of the implementation, not an expression of some requirement in the object. A test suite that contains a lot of brittle tests will slow down development and inhibit refactoring. The solution is to re-examine the code and see if either the specification should be weakened, or the object structure is wrong and should be changed. Following Einstein, a specification should be as precise as possible, but not more precise.

*Don’t use mocks/stubs to test boundary/isolated objects*

> If an object has no relationships to other objects in the system, it does not need to be tested with mock objects. A test for such an object only needs to make assertions about values returned from its methods. Typically, these objects store data, perform independent calculations or represent atomic values. While this may seem an obvious thing to say, we have encountered people trying to use mock objects where they don’t actually need to.

*Don’t add behaviour*

> Mock objects are still stubs and should not add any additional complexity to the test environment, their behaviour should be obvious [10]. We find that an urge to start adding real behaviour to a mock object is usually a symptom of misplaced responsibilities. A common example of this is when one mock has to interpret its input to return another mock, perhaps by parsing an event message. This introduces a risk of testing the test infrastructure rather than the target code. For example:
> ```csharp
> mock.expect(once()) .method("retrieve").with(eq(KEY1)) .willReturn(VALUE1);
> mock.expect(once()) .method("retrieve").with(eq(KEY2)) .willReturn(VALUE2);
> ```

*Only mock/stub your immediate neighbours*

> An object that has to navigate a network of objects in its implementation is likely to be brittle because it has too many dependencies. One symptom of this is tests that are complex to set up and difficult to read because they have to construct a similar network of mock objects. Unit tests work best when they focus on testing one thing at a time and only setting expectations on objects that are nearest neighbours. The solution might be to check that you are testing the right object, or to introduce a role to bridge between the object and its surroundings.

*Too Many Mocks/Stubs*

> A similar problem arises when a test has to pass too many mock objects to the target code, even if they are all immediate neighbours. Again, the tests is likely to be complex to set up and hard to read. Again the solution might be to change misaligned responsibilities or to introduce an intermediate role. Alternatively, it is possible that the object under test is too large and should be broken up into smaller objects that will be more focussed and easier to test.

[Back to top](#tdd-session)

---
