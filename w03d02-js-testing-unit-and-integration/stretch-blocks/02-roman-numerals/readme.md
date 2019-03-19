# Roman Numerals

##Summary

We're going to write a WebApp that converts an integer to its Roman numeral equivalent. In other words, if we give our method the Arabic number 476, our method will return the Roman numeral CDLXXVI.

What we want at the end of this challenge is a web page which takes an Arabic numeral as an input and when you click on the Convert to Roman button, returns the Roman version of the number on the screen.

Determining how to take any number (e.g., 1, 58, 1948, etc.) and convert it into its Roman numeral equivalent is our main focus.  But, in solving this problem, we'll have the opportunity to practice developing with a test-first approach.  And, as always, we should pay attention to the quality of the code that we write.  Are we writing methods that do only one thing?  Is our code DRY—as in *don't repeat yourself*? Are we giving our variables descriptive names?  We need to be very deliberate with our code to make it as easy to read as possible; make intentional decisions.

### Test-first Approach
Before we write code, we're going to write tests that will tell us if the code we do write is operating the way that we expect it to.  

With this approach, we start simple.  The first test we have for converting an Arabic number to a Roman numeral is converting 1 to I.  Then we make things a little harder; we'll convert 4.  From there, maybe we'll move on to converting 5.  We'll continue with this step-by-step approach until we can convert any Arabic number to its Roman numeral equivalent.

### Refactoring
Undoubtedly, as we code, we'll see opportunities to refactor.  Are we beginning to repeat ourselves?  Is there a bit of logic that could exist in its own method so that each method is responsible for only one thing?  When we refactor code, we can accidentally break already working code. How do we know if we break our code?  Our tests can help us.  We'll want to get into the habit of refactoring only when all of our tests are passing.  Passing tests tell us that our code works.  If our tests continue to pass during and after refactoring, we can be sure that we haven't broken anything.

### Roman Numerals as Representation
Has anyone ever seen a 5? Not a symbol we write on a piece of paper or print to a screen, but an actual, honest-to-goodness 5?  Of course not. You've seen things that somehow embody five: five apples, five fingers, five weekdays on the calendar, a scrap of paper with *5* written on it, and so forth.

Think of all the ways to represent the integer 5.  Symbols like *5*, *five*, *V*, and *IIIII* all ways to represent 5. If we asked a three-year-old, they might hold up the five fingers on their hand or pull out five pennies from their pocket. Computers encode numbers their own way, as a sequence of 0s and 1s called [binary](http://en.wikipedia.org/wiki/Binary_number).  [The map is not the territory](http://en.wikipedia.org/wiki/Map%E2%80%93territory_relation), as they say.


##Releases

###Release 0 : Old Roman Numerals

| Arabic Number  | Roman Numeral |
| -------------- | ------------- |
| 1              | I             |
| 5              | V             |
| 10             | X             |
| 50             | L             |
| 100            | C             |
| 500            | D             |
| 1000           | M             |

*Table 1*. Arabic number and their old Roman numeral equivalents.


In the early days of Roman numerals, the Romans built their numerals from the individual characters in Table 1 (e.g., I, V, X, etc.) written largest value to smallest from left to right.  To determine the value of any numeral, they used straight addition.  I is equivalent to 1.  II is equivalent to 1 + 1, or 2.  VIIII is equivalent to 5 + 1 + 1 + 1 + 1, or 9.

We are going to begin writing a method `convert_to_roman`.  When passed an integer between 1 and 3000, this method returns a string containing the proper old Roman numeral.  In other words, `convert_to_roman(4)` should return the string `'IIII'`.  Don't worry about checking whether or not the number passed to the method is between 1 and 3000; it's just that at some point, Roman numerals become unwieldy.

We'll need to test that our code works. Write the necessary tests in the file `test.js`.  Think of the cases you would like to cover to effectively test your code.

Run the test suite.  The tests should fail since we haven't done any work yet.

Let's start simple and make the test for converting 1 pass.  To do so, write the least amount of code as possible—maybe your method just returns a hard-coded string.

After the test for converting 1 is passing, let's pass the test for converting 4.  Again, write the least amount of code as possible.

### Release 1: Write New Tests

Can our method convert 5, 6, 10, etc.?  We'll need to write and pass tests that confirm our method is working as intended.

Update the test file with a new test for converting the number 5.  Then, make this new test pass.  Once the test passes, write the next test.  Which Arabic number would be a good candidate to check next?

Repeat the cycle of writing and passing tests until we're confident that our method will convert any number from 1 to 3000.

*Hint*: It might be useful to use the integer division `/` and modulus `%` methods.

### Release 2: Options for Modern Roman Numerals

| Arabic Number | Roman Numeral |
| ------------- | ------------- |
| 4             | IV            |
| 9             | IX            |
| 14            | XIV           |
| 44            | XLIV          |
| 99            | XCIX          |
| 400           | CD            |
| 944           | CMXLIV        |



## Conclusion
This challenge is a useful exercise in understanding the relationship between how we represent our data and the actions we want to perform on it—a dynamic you'll see at play in almost every piece of software you write.  How did we decide to represent the relationship between a Roman numeral and its Arabic number equivalent (e.g., X to 10)?  Was it easy to map from one to the other?  Were all the mappings organized together?  Did our representation of the relationship make it easier or harder when it came time to switch to modern Roman numerals?

### More on Data Representations
Reflect on the pros and cons of Arabic numbers and Roman numerals. Imagine we're engineers building a system for people to manipulate numbers and we have two proposals: use Roman numerals or use [Arabic numbers](http://en.wikipedia.org/wiki/Arabic_numerals). How do we decide and why?

What benefits do Arabic numerals have over Roman numerals as a way to represent numbers? For example, with Arabic numerals we have an obvious way to represent 0. Arabic numerals also typically require fewer characters to represent the same number (e.g., "3111" vs "MMMCXI"). What else? 

For example, if we're counting people as they walk into a room by marking something on a piece of paper, Arabic numerals are a terrible representation. That'd be like trying to go for a hike and using a political map as a guide.  Would Roman numerals be any better?  An option more appropriate for the task might be [tally marks](http://en.wikipedia.org/wiki/Tally_marks).