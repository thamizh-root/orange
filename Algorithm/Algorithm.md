
What is algorithm? A **process** or **set of tasks** to accomplish a certain task.

Why do I need to know this?
Almost everything that you do in programming involves some kind of algorithm! It's the foundation for being a successful problem solving and developer. Also, interviews.

How do you improve?
1. **Devise** a plan for solving problems
2. **Master** common problem solving patterns

##### Problem Solving
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


##### Problem Solving Patterns:
1. [[Book of Error#Frequency Counter|Frequency Counter]]
2. [[Book of Error#Multiple Pointers|Multiple Pointers]]
3. [[Book of Error#Sliding Window|Sliding Window]]
4. Divide And Conquer
##### Recursive:

Once upon a time... Martin and Dragon.

- Define what recursion is and how it can be used.
- Understand the two essential components of a recursive function.
- Visualize the call stack to better debug and understand recursive functions.
- Use helper method recursion and pure recursion to solve more difficult problems.

What is recursion? A process (a function in our case) that calls itself.

Why do I need to know this? It's everywhere. 
- JSON.parse / JSON.stringify
- document.getElementById and DOM traversal algorithms
- Object traversal
- We will see it with more complex data structures
- It's sometimes a cleaner alternative to iteration

The call stack
- It's a **stack** data structure - we'll talk about that later!
- Any time a function is invoked it is placed (**pushed**) on the top of the call stack.
- When JavaScript sees the **return** keyword or when the function ends, the compiler will remove (**pop**).

```
function takeShower(){
    return "Showering!"
}

function eatBreakfast(){
    let meal = cookFood()
    return `Eating ${meal}`
}

function cookFood(){
    let items = ["Oatmeal", "Eggs", "Protein Shake"]
    return items[Math.floor(Math.random()*items.length)];
}

function wakeUp() {
    takeShower()
    eatBreakfast()
    console.log("Ok ready to go to work!")
}

wakeUp()
```

Why do I care?
- You're used to functions being pushed on the call stack and popped off when they are done.
- When we write recursive functions, we keep pushing new functions onto the call stack.

**Our first recursive function:**
How recursive functions work? Invoke the same function with a different input until you reach your base case. What's base case? The condition when the recursive ends. So, **base case** and **different input** are two essential parts of recursive function.

```
function countDown(num){
    if(num <= 0) {
        console.log("All done!");
        return;
    }
    console.log(num);
    num--;
    countDown(num);
}

countDown(3)
```

**Our second recursive function:**
Can you spot the base case?
Do you notice the different input?
What would happen if we didn't return?

```
function sumRange(num){
   if(num === 1) return 1;
   return num + sumRange(num-1);
}

sumRange(4)
```

```
function factorial(num){
    if(num === 1) return 1;
    return num * factorial(num-1);
}
factorial(5)
```

Helper method recursion:
```
function collectOddValues(arr){
    let result = [];
    function helper(helperInput){
        if(helperInput.length === 0) {
            return;
        }
        if(helperInput[0] % 2 !== 0){
            result.push(helperInput[0])
        }
        helper(helperInput.slice(1))
    }
    helper(arr)
    return result;
}

collectOddValues([1,2,3,4,5,6,7,8,9])
```

Pure recursion:
```
function collectOddValues(arr){
    let newArr = [];
    if(arr.length === 0) {
        return newArr;
    }

    if(arr[0] % 2 !== 0){
        newArr.push(arr[0]);
    }
    newArr = newArr.concat(collectOddValues(arr.slice(1))); // difference between splice(1) and slice(1)
    return newArr;
}

collectOddValues([1,2,3,4,5])
```

- For arrays, use methods like slice, spread operators and concat that make copies of arrays so you don't not mutate them.
- Remember that strings are immutable so you will need to use methods like slice, substr or substring to make copies of strings.
- To make copies of objects use Object.assign or spread operator.

Practice Recursive:
1. **Power Calculation**: Write a recursive function that takes in two integers, `base` and `exponent`, and returns the result of raising the base to the exponent (i.e., `base^exponent`).
2. **Factorial**: Write a recursive function to calculate the factorial of a number `n`, where `factorial(n)` is `n * (n-1) * ... * 1`, and `factorial(0)` is `1`.
3. **Product of Array**: Write a recursive function that takes an array of numbers and returns the product of all the numbers in the array.
4. **Recursive Range**: Write a recursive function that calculates the sum of all numbers from `0` up to a given number `n`.
5. **Fibonacci**: Write a recursive function that returns the nth number in the Fibonacci sequence, where the first two numbers are 1 and 1, and each subsequent number is the sum of the previous two.
6. **Reverse**: Write a recursive function that takes a string and returns the string reversed.
7. **Is Palindrome**: Write a recursive function that checks if a given string is a palindrome (a word that reads the same forwards and backwards).
8. **Some Recursive**: Write a recursive function that takes an array and a callback, and returns `true` if any value in the array returns `true` when passed to the callback.
9. **Flatten**: Write a recursive function that flattens an array of arrays into a single array.
10. **Capitalize First**: Write a recursive function that takes an array of strings and capitalizes the first letter of each string.
11. **Nested Even Sum**: Write a recursive function that takes an object and returns the sum of all the even numbers in the object, which may contain nested objects.
12. **Capitalize Words**: Write a recursive function that capitalizes all words in an array.
13. **Stringify Numbers**: Write a recursive function that takes an object and finds all of the values that are numbers and converts them to strings.
14. **Collect Strings**: Write a recursive function that takes an object and returns an array of all the string values present inside the object.


**Power Calculation**: Write a recursive function that takes in two integers, `base` and `exponent`, and returns the result of raising the base to the exponent (i.e., `base^exponent`).

Wrong Solution
```
// **Power Calculation**: Write a recursive function that takes in two integers, `base` and `exponent`, and returns the result of raising the base to the exponent (i.e., `base^exponent`).

// find base ^ exponent using recursive
// input - two integers - base and exponent
// base ^ exponent
// variables we might need base, exponent

// base case - if 1 return 1;
// different input - n - 1

// findExpo(base, exponent)
// if 1 return 1;
// return 1 ^ findExpo(base, exponent - 1)
// 
// 

function findExpo(base, exponent) {
    //base case 
    if (exponent == 1) {
        return 1;           // this is bad base case
    }
    return base ^ findExpo(base, exponent - 1);   // should be using *, not ^
}

let result = findExpo(2, 3);
console.log(" --- result --- ", result);
```

There are two issues with above code:
1. **Incorrect base case**: The base case `if (exponent == 1)` is wrong. In an exponentiation function, when the exponent reaches `0`, the result should be `1`, not when it reaches `1`. For example, `2^0 = 1`, and `2^1 = 2`.
2. **Incorrect operator**: The operator `^` in JavaScript is a bitwise XOR, not exponentiation. For exponentiation, you should use `*` to multiply the base recursively, or use the `**` operator for direct exponentiation.

Good Solution
```
function findExpo(base, exponent) {
     if (exponent === 0) {
        return 1;
    }
    return base * findExpo(base, exponent - 1);
}
let result = findExpo(2, 3);
```


**Product of Array**: Write a recursive function that takes an array of numbers and returns the product of all the numbers in the array.

```
function multiply(arr) {
    if (arr.length == 0) {
        return 1;
    }
    return arr[0] * multiply(arr.slice(1));
}
let x = multiply([1, 2, 1, 2]);
console.log('Product of all the elements in the given array:', x);
```

```
1 * multiply([2, 1, 2])
    2 * multiply([1, 2])
        1 * multiply([2])
            2 * multiply([])
                return 1
```

**Recursive Range**: Write a recursive function that calculates the sum of all numbers from `0` up to a given number `n`.

```
function addEverything(num) {
    if (num === 0) {
        return 0; // base case: when num is 0, return 0
    }
    
    return num + addEverything(num - 1); // recursive call
}

let x = addEverything(5);
console.log('Added all the numbers from 0 to the given num: ', x);
```