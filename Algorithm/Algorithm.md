
What is algorithm? A **process** or **set of tasks** to accomplish a certain task.

Why do I need to know this?
Almost everything that you do in programming involves some kind of algorithm! It's the foundation for being a successful problem solving and developer. Also, interviews.

How do you improve?
1. **Devise** a plan for solving problems
2. **Master** common problem solving patterns

Problem Solving
1. Understand the problem
2. Explore concrete examples
3. Break it down 
4. Solve or Simplify
5. Look back and refactor

Note: Many of these stratergies are adapted from 'George Polya', whose book 'How To Solve It' is a great resource for anyone who wants to become problem solver.


**Understand the problem:**
1. Can I restate the problem in my own words?
2. What are the inputs that go into the problem?
3. What are the outputs that should come from the solution to the problem?
4. Can the outputs be determined from the inputs? In other words, do I have enough information to solve problem?
5. How should I label the important pieces of data that are a part of the problem?

Example:
Write a function which takes two numbers and returns their sum.

Q. Can I restate the problem in my own words? 
"implement addition"
Q. What are the inputs that go into the problem?
int? float? what about string for large numbers
Q. What are the outputs that should come from the solution to the problem?
int? float? string?
Q. Can the outputs be determined from the inputs? In other words, do I have enough information to solve problem?
null values? invalid value handling?
Q. How should I label the important pieces of data that are a part of the problem?
num1, num2, sum


**Explore concrete examples:**
1. Start with simple examples
2. Progress to more Complex examples
3. Explore examples with empty inputs
4. Explore examples with invalid inputs

Example:
Write a function which takes in a string and returns counts of each character in the string.

charCount("aaaa"); // {a:4}
charCount("hello"); // {h:1, e:1, l:2, o:1}

"my phone number is 182763"
"Hello hi"
charCount("")


**Break it down:**
Write a function which takes in a string and returns counts of each character in the string.

```
function charCount(str){
// do something
// return an object with keys that are lowercase alphanumeric characters in the string
} 
```

```
function charCount(str){
// make object to return at end
// loop over string, for each character...
   // if the char is a number/ letter AND is a key in object, add one to count
   // if the char is a number/ letter AND not in object, add it to object and set value to 1
   // if the char is something else (space, period, etc..) don't do anything
// return object at end
} 
```


**Refractoring Questions:**
1. Can you check the result?
2. Can you derive the result differently?
3. Can you understand it at a glance?
4. Can you use the result or method for some other problem?
5. Can you improve the performance of your solution?
6. Can you think of other ways to refactor?
7. How have other people solved this problem?


Problem Solving Patterns:
1. [[Book of Error#^690351|Frequency Counter]]
2. [[Book of Error#^2e190a|Multiple Pointers]]
3. [[Book of Error#Sliding Window|Sliding Window]]
