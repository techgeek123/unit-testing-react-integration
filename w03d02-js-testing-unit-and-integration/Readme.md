# JavaScript-Testing-Unit vs Integration, Mocha_and_Chai

## Learning Competencies

By the end of this chapter, you should be able to:

- Understand what is unit testing
- Understand what is integration testing
- Unit vs Integration Testing
- Generating coverage report
- Know how to run tests
- Write unit tests with Mocha and Chai
- Understand how Test Driven Development works


## Overview of Testing Unit vs Integration

### Wiki Says
#### [Unit Testing](https://en.wikipedia.org/wiki/Unit_testing)
> In computer programming, unit testing is a software testing method by which individual units of source code, sets of one or more computer program modules together with associated control data, usage procedures, and operating procedures, are tested to determine whether they are fit for use.

#### [Integration Testing](https://en.wikipedia.org/wiki/Integration_testing)
> Integration testing is the phase in software testing in which individual software modules are combined and tested as a group. It occurs after unit testing and before validation testing. Integration testing takes as its input modules that have been unit tested, groups them in larger aggregates, applies tests defined in an integration test plan to those aggregates, and delivers as its output the integrated system ready for system testing.


Testing is a very important part of writing code. Without it, bugs sneak into the wild where they are more difficult and costly to fix. Think about fixing and debugging a code of thousands and millions of lines after being executed for a business. It will delay user's process and thus a high loss for the company. To avoid such issues, we use automatic testing frameworks. They significantly increase test coverage as well as reduce long-term costs.

In some teams, this falls to the developers but it can also fall to testers to create automated tests. These automated tests can be unit tests (concise tests that target very small pieces of functionality) or larger, integration-level tests.

In Integration Testing, individual software modules are integrated logically and tested as a group.A typical software project consists of multiple software modules, coded by different programmers.Integration testing focuses on checking data communication amongst these modules.


## Overview of Mocha_and_Chai

### Wiki Says
> Mocha is a JavaScript test framework running on node.js, featuring browser support, asynchronous testing, test coverage reports, and use of any assertion library.


As you begin writing more complicated functions and larger applications, you're bound to make mistakes. Everyone does it, even professional programmers. When your programs grow they can become more difficult to reason about, and as hard as you may try it's impossible to predict every bug in your program. Fixing bugs also has a cost, as it can be quite easy for one fix to introduce bugs in other parts of your application.

Is there any way to avoid our programs becoming more brittle and difficult to maintain as they grow in complexity? Yes! The solution to this problem lies in **testing** our code as thoroughly as possible. In this chapter, you'll learn how to write tests in JavaScript that you can run automatically to verify that the code you're writing does what you expect. This makes it easier to protect against bugs, and to ensure that you don't introduce new bugs in your code as you add new features or rewrite old ones.

It might be difficult to appreciate the value of writing tests now, but it's a critical skill to have when you're working in a large codebase with a team of other developers. Are you down with **TDD** (Test Driven Development)? By the end of this chapter, hopefully you will be.

`mocha` - this is our test runner and we will be using it to run all of our tests. A **test runner** is a tool that is responsible for running tests that you write and logging the results of the tests for you to see.

`chai` - this is our expectation/assertion library. `chai` provides additional ways for you to write tests; in particular, it lets you write tests so that they are quite straightforward to read. This isn't a necessary tool to use if you're writing tests with `mocha`, but you'll very often see them paired together. For now, you can simply think of chai as a way to enhance your tests and make them more readable. 

When we write our tests, there are a few functions that we'll be using quite frequently. Here are three of the most important ones:

`describe` - this function is given to us by `mocha` and it is what we use to organize our tests. You can think of a `describe` function like talking to someone and telling them "let me describe ____ to you." Very often when you're writing unit tests, you'll have one `describe` block per function you're testing (this will make more sense once you've seen some examples).

`it` - this function lives inside of describe functions. Inside of these `it` functions we make our expectations. Each `it` function corresponds to a test; if one of our expectations inside of the `it` function isn't met, the test fails.

`expect` - this is a function given to us by `chai`. `chai` has a few different styles (`expect`/`should`/`assert`); all let you write readable tests, so which style you use is up to you.

## **T**est **D**riven **D**evelopment (**TDD**)

### Why?

_Project(s) without tests_ often end up looking like they are stuck together with _**duct tape**_ ...

![duct tape car fail](http://i.imgur.com/9cNriGK.jpg)

Change _one_ part and the _other_ stops working? "_Fixing_" one bug, creates another?

Wouldn't you *prefer* if everything was
***consistent*** and beautifully integrated? <br />
What if _everyone_ on your team worked _like **clock-work**_ in a disciplined order... like a _**Formula 1 Crew**_ ...

![formula 1 pit stop](http://i.imgur.com/0NDbaam.jpg)

Test Driven Development (TDD) makes your team a well-oiled machine which means you can go _**faster**_.

Once you have a ***suite*** of tests that run on every change, you will
begin to develop a whole other level of ***confidence*** in your codebase
and will discover a new freedom to be ***creative*** without fear of
"*breaking*" anything else; truly *game-changing*.


### What?

This tutorial will help you get started with
**T**est **D**riven **D**evelopment (**TDD**) *today*! <br />
In the next ***30 minutes*** you will learn _everything_<sup>1</sup> you need to know to write tests for your web project!


#### What is Software Testing?
> Software testing is the process of evaluation a software item to detect differences between given input and expected output. Testing assesses the quality of the product. Software testing is a process that should be done during the development process. In other words software testing is a verification and validation process.


#### What is TDD?

> Test-driven development (TDD) is an evolutionary approach to development which combines test-first development where you write a test before you write just enough production code to fulfill that test and refactoring. In other words, it’s one way to think through your requirements or design before your write your functional code.

*From [Introduction to Test Driven Development (TDD)](http://agiledata.org/essays/tdd.html)*


### How?

The *first* thing you need to *understand* is that writing code following TDD (*discipline*) is a (*slightly*) different approach from simply diving into solving the problem (*without a test*).

When reading about TDD you will see the expression: "***Red, Green, Refactor***":

![TDD Cycle: Red, Green, Refactor](http://i.imgur.com/RQe2NQT.jpg)

What this means is that there's a **3-step process**:

1. ***Write*** a **Failing Test** - Understand the (user) requirements/story well enough to write a test for what you expect. (_the test should **fail** initially - hence it being "Red"_) <br />

2. ***Make*** the (*failing*) **Test Pass** - Write (*only*) the code you need
to make the (*failing*) test pass, while ensuring your existing/previous tests
all still pass (*no regressions*).

3. ***Refactor*** the code *you* wrote - if you have time to tidy up the code
*you* wrote to make it simpler (*for your future self or colleagues to understand*) before you need to ship the current feature, do it.

To develop the *habit(s)* you will need to be successful with TDD (*and software engineering in general*)
we need to ***write*** a ***test first*** (*and watch it fail*) and *then* write the code required to make the test pass.

Writing a _**failing test**_, before writing the code may seem *counter-intuitive*, *time consuming* or even "*tedious*" at _**first**_. But we _urge_ you to think of it this way:

> The ***test*** is the ***question*** you are asking <br />
> your code is the ***answer*** to the question. <br />
> By having a _clear_ question, you can always check
> that your code is working, <br />
> because it _**consistently**_
> gives you the same answer(s) ... _no surprises_, even when you're working with a large, inter-dependent code base!


## Resources

### Unit vs Integration

- An article on "Introduction to JS Unit Testing" by Zorn Zafferer. Read [here](https://www.smashingmagazine.com/2012/06/introduction-to-javascript-unit-testing/) 
- Read "Why do we need framework for test automation?" [here](http://www.softwaretestinghelp.com/why-do-we-need-test-automation-framework/)
- Check out [this](http://www.guru99.com/unit-testing-guide.html) beautiful tutorial on Unit Testing
- For code coverage read the Wikipedia article [here](https://en.wikipedia.org/wiki/Code_coverage)

### Mocha and Chai

- You can read more about `mocha` [here](https://mochajs.org/).
- You can read more about `chai` [here](http://chaijs.com/).
- You can read more about `except` [here](http://chaijs.com/guide/styles/#expect)
- Check out this excellent [website](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-unit-testing-with-mocha-and-chai) on **Testing with Mocha & Chai**
- Read [this](https://www.sitepoint.com/unit-test-javascript-mocha-chai/) article on **Unit Test Your JavaScript Using Mocha and Chai** by *Jani Hartikainen*

### Testing and Test Driven Development
- [Software Testing](http://en.wikipedia.org/wiki/Software_testing)
- ["What is Software Testing" video (from 5:56 onwards)](https://youtu.be/UZy1Dj9JIg4?t=356)
- [Video intro to Software Development Lifecycle (from 0:52 onwards)](https://youtu.be/qMkV_TDdDeA?t=52)
- [How to Write Clean, Testable Code](http://youtu.be/XcT4yYu_TTs) (ignore the Java code focus on the general principals)
+ [What is software testing?](http://www.codeproject.com/Tips/351122/What-is-software-testing-What-are-the-different-ty) by _Rehman Zafar_
- [Practical Full-Stack JavaScript WebApplication Test Driven Development](https://github.com/nelsonic/practical-js-tdd)

