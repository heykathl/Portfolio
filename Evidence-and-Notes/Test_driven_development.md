# Test Driven Development

### Why are tests useful?
Runs without errors
Produces the desired output
Code quality (Linters)
Understand and clarify user requirements
Opportunity to find missing requirements 
Provides confidence when making changes
Test coverage - confirm all functional code has been tested and helps find non-functional code
Documentation

### Why must we write tests first?
Only write what is necessary
Structured code to ensure the each line of the tests are met - incremental changes
Sticks to specifications
Clarify requirements
Think about the code
Efficient - catching bus before they appear
Test is the destination - planning ahead
Design tool, design incremental
Ensuring good code coverage

### TDD Process
<Insert diagram of TDD process>
The three laws of TDD:
1. You are not allowed to write any production code unless it is to make a failing unit test pass.
2. You are not allowed to write any more of a unit test than is sufficient to fail; and compilation failures are failures.
3. You are not allowed to write any more production code than is sufficient to pass the one failing unit test.

The four-phase test is a testing pattern, applicable to all programming languages and unit tests (not so much integration tests). It takes the following general form:
```
test do
  setup
  exercise - the system under test is executed
  verify - the result of the exercise is verified against the developer’s expectations
  teardown - reset to its pre-setup state
end
```

## Exercises
One of the jobs of a software engineer is turning vague half-formed ideas into working software. This exercise will involve test driving code from the outside in.

Exercise 1: [Test driving I](https://hackmd.io/NGdU2pqzSbOng3IwsDTzew)
With the use of Ruby's REPL (IRB), I wrote code in accordance with the user stories, which then converts into my tests:

```
As a student
So that I can remember people’s names
I want an IRB application that stores the names of people I meet
```
```
> store_name(“James”)
=> "Name stored!"
> show_names
=> [“James”]
> store_name(“Jimmy”)
=> "Name stored!"
> show_names
=> [“James”, “Jimmy”]
```

```
As a student
So that I can understand my recent motivation
I want an IRB application that stores my motivation ratings
And I want to see the average of my last 3 ratings
```
```
> store_motivation(1)
=> "Motivation stored!"
> store_motivation(2)
=> "Motivation stored!"
> store_motivation(2)
=> "Motivation stored!"
> show_motivation
=> [1, 2, 2]
> average_motivation.last(3)
=> 1.6
```

Step-by-step process of writing tests:
```
# The imagined example
> store_name(“James”)
=> "Name stored!"
```
```
# The expectation_
expect(store_name(“James”).to eq "Name stored!"
```
```
# The full test
describe "the store_name method" do
  it "gives us a friendly message" do
    expect(store_name(“James”)).to eq "Name stored!"
  end
end
```

Exercise 2: [TDD a single object](https://github.com/makersacademy/course/blob/main/tagging/tdd_simple.md)
The full [dice game](https://github.com/heykathl/dice-game) exercise can be found on my Github repository.

```
As a board game player,
So that I can play a game
I want to be able to roll a dice
```

```
As a board game player,
So that I know how many steps I should move
Rolling a dice should give me a number between 1 and 6
```

```
As a dice app developer,
So that I give players a good game experience
I want the dice roll to be randomly picked
```

```
As a board game player,
So that I can play many types of games
I want to be able to roll any number of dice at the same time
```

```
As a board game player,
So that I know what my score was when I rolled several dice
I want to get the result of each dice roll
```

Exercise 3: [Piggy-bank](https://github.com/heykathl/piggy-bank)