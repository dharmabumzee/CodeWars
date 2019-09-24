# Total Completed: 20
------------
## Student's final grade
------------
https://www.codewars.com/kata/students-final-grade

**Task overview:**
Create a function finalGrade, which calculates the final grade of a student depending on two parameters: a grade for the exam and a number of completed projects.
This function should take two arguments: exam - grade for exam (from 0 to 100); projects - number of completed projects (from 0 and above);
This function should return a number (final grade). There are four types of final grades:

- 100, if a grade for the exam is more than 90 or if a number of completed projects more than 10.
- 90, if a grade for the exam is more than 75 and if a number of completed projects is minimum 5.
- 75, if a grade for the exam is more than 50 and if a number of completed projects is minimum 2.
- 0, in other cases



```javascript
function finalGrade (exam, projects) {
  if ( exam > 90 || projects > 10) {
    return 100;
  } else if ( exam > 75 && projects >= 5) {
    return 90;
  } else if ( exam > 50 && projects >= 2) {
    return 75;
  } else {
    return 0;
    }
}
```


```javascript
const finalGrade = (exam, projects) => {
  return (
    exam > 90 || projects > 10 ? 100 :
    exam > 75 && projects >= 5 ? 90 :
    exam > 50 && projects >= 2 ? 75 : 0
  );
}
```

## Count the monkeys!
-----------
https://www.codewars.com/kata/count-the-monkeys

**Task overview:**
You take your son to the forest to see the monkeys. You know that there are a certain number there (n), but your son is too young to just appreciate the full number, he has to start counting them from 1.
As a good parent, you will sit and count with him. Given the number (n), populate an array with all numbers up to and including that number, but excluding zero.


```javascript
function monkeyCount(n) {
  var count = [];
  var i = 1;
  while (i <= n) {
    count.push(i);
    i++;
  } 
  return count;
}
```

```javascript
function monkeyCount(n) {
  for (var i = 0, monkeys = []; i < n; monkeys.push(++i));
  return monkeys;
}
```

  
## Count by X 
-----------
https://www.codewars.com/kata/5513795bd3fafb56c200049e

**Task overview:**
Create a function with two arguments that will return an array of length (n) with multiples of (x). 
Assume both the given number and the number of times to count will be positive numbers greater than 0.
Return the results as an array 


```javascript
function countBy(x, n) {
  var z = []; 
  var step = x;
  for (var i = 0; i < n; i++) {
    z.push(x);
    x += step;
  }
  return z;
}
```


```javascript
function countBy(x, n) {
  var z = [];
  while (z.length < n) z.push(x * (z.length + 1));
  return z;
}
```


## Count odd numbers below n
-----------
https://www.codewars.com/kata/59342039eb450e39970000a6 

**Task overview:**
Given a number n, return the number of positive odd numbers below n, EASY!


```javascript
function oddCount(n){
  return Math.floor(n / 2);
}
```

## Convert a boolean to a string 
-----------
https://www.codewars.com/kata/551b4501ac0447318f0009cd

**Task overview:**
In this programming exercise, you're going to learn about functions, boolean (true/false) values, strings, and the if-statement.
A function is a block of code that takes an input and produces an output. In this example, boolean_to_string is a function whose input is either true or false, and whose output is the string representation of the input, either "true"/"True" or "false"/"False" (check the sample tests about what capitalization to use in a given language).
A common idea we often want to represent in code is the concept of true and false. A variable that can either be true or false is called a boolean variable. In this example, the input to boolean_to_string (represented by the variable b) is a boolean.
Lastly, when we want to take one action if a boolean is true, and another if it is false, we use an if-statement.
For this kata, don't worry about edge cases like where unexpected input is passed to the function. You'll get to worry about these enough in later exercises.


```javascript
function booleanToString(b){
  if (b === true) {
    return "true";
  } else {
  return "false";
  }
}
```

```javascript
function booleanToString(b){
  return b.toString();
}
```
 
## Sum of positive 
-----------
https://www.codewars.com/kata/sum-of-positive

**Task overview:**
You get an array of numbers, return the sum of all of the positives ones. Example [1,-4,7,12] => 1 + 7 + 12 = 20
Note: if there is nothing to sum, the sum is default to 0.

```javascript
function positiveSum(arr) {
  var sum = 0;
  for (var i = 0; i <= arr.length; i++) {
    if (arr[i] >= 0) {
      sum += arr[i];
    } 
  }
  return sum;
}
```

```javascript
function positiveSum(arr) {
  return arr
      .filter(x => x > 0)
      .reduce((x, y) => x + y, 0);
}
```

##  Will there be enough space?
-----------
https://www.codewars.com/kata/will-there-be-enough-space

**The Story:**
Bob is working as a bus driver. However, he has become extremely popular amongst the city's residents. With so many passengers wanting to get aboard his bus, he sometimes has to face the problem of not enough space left on the bus! He wants you to write a simple program telling him if he will be able to fit all the passengers.

**Task Overview**:
You have to write a function that accepts three parameters:

- cap is the amount of people the bus can hold excluding the driver.
- on is the number of people on the bus.
- wait is the number of people waiting to get on to the bus.

If there is enough space, return 0, and if there isn't, return the number of passengers he can't take.
```javascript
function enough(cap, on, wait) {
  var sum = cap - (on + wait);
  if (sum > 0) {
    return 0;
  } else {
  return Math.abs(sum);
  }
}
```

```javascript
function enough(cap, on, wait) {
 return Math.max(wait + on - cap, 0);
}
```
 
## Surface area and volume of a box 
-----------
https://www.codewars.com/kata/surface-area-and-volume-of-a-box

**Task overview:**
Write a function that returns the total surface area and volume of a box as an array: [area, volume]

```javascript
function getSize(width, height, depth) {
  var surface = 2 * (height * width) + 2 * (height * depth) + 2 * (width * depth);
  var volume = height * width * depth;
  return [surface, volume];
}
```

```javascript
const getSize = (w, h, d) => [2*(w * h + w * d + h*d), w*h*d];
```
  
## Remove first and last character
-----------
https://www.codewars.com/kata/remove-first-and-last-character

**Task overview:**
It's pretty straightforward. Your goal is to create a function that removes the first and last characters of a string. You're given one parameter, the original string. You don't have to worry with strings with less than two characters.

```javascript
function removeChar(str){
 return str.slice(1, str.length - 1);
};
```

```javascript
function removeChar(str){
 return str.slice(1, -1);
};
```

## Get character from ASCII value 
-----------
https://www.codewars.com/kata/get-character-from-ascii-value

**Task overview:**
Write a function which takes a number and returns the corresponding ASCII char for that value.

```javascript
function getChar(c){
  return String.fromCharCode(c);
}
```

```javascript
const getChar = c => String.fromCharCode(c);
```

## Correct the mistakes of the character recognition software
-----------
https://www.codewars.com/kata/correct-the-mistakes-of-the-character-recognition-software

**Task overview:**
Character recognition software is widely used to digitise printed texts. Thus the texts can be edited, searched and stored on a computer.
When documents (especially pretty old ones written with a typewriter), are digitised character recognition softwares often make mistakes.
Your task is correct the errors in the digitised text. You only have to handle the following mistakes:

- S is misinterpreted as 5
- O is misinterpreted as 0
- I is misinterpreted as 1

The test cases contain numbers only by mistake.

```javascript
function correct(string) {
 return string.replace(/5/g, "S").replace(/0/g, "O").replace(/1/g, "I");
}
```

```javascript
const correct = string => string.replace(/5/g, "S").replace(/0/g, "O").replace(/1/g, "I");
```
  

## L1: Set Alarm 
-----------
https://www.codewars.com/kata/l1-set-alarm

**Task overview:**
Write a function named setAlarm which receives two parameters. The first parameter, employed, is true whenever you are employed and the second parameter, vacation is true whenever you are on vacation. The function should return *true* if you are employed and not on vacation (because these are the circumstances under which you need to set an alarm). It should return *false* otherwise. 

```javascript
function setAlarm(employed, vacation){
   return (employed !== false && vacation !== true) 
}
```

```javascript
function setAlarm(employed, vacation){
  return employed && !vacation;
}
```

## MakeUpperCase 
-----------
https://www.codewars.com/kata/makeuppercase/

**Task overview:**
Write function makeUpperCase.

```javascript
const makeUpperCase = str => str.replace(/[a-z]/g, s => String.fromCharCode(s.charCodeAt(0) - 32));
```

```javascript
const makeUpperCase = str => str.toUpperCase();
```
  
 ## Hex to Decimal 
 -----------
 https://www.codewars.com/kata/hex-to-decimal
 
 **Task overview:**
 Complete the function which converts hex number (given as a string) to a decimal number.
 
 ```javascript
function hexToDec(hexString){
  return parseInt(hexString, 16);
}
```

```javascript
const hexToDec = hexString => parseInt(hexString, 16);r
```

## Reduce but grow 
-----------
https://www.codewars.com/kata/beginner-reduce-but-grow/

**Task overview:**
Given a non-empty array of integers, return the result of multiplying the values together in order

 ```javascript
function grow(x){
  var sum = 1;
  for ( var i = 0; i < x.length; i++ ) {
    sum = sum * x[i];
  }
  return sum;
}
```

 ```javascript
function grow(x){
  return x.reduce((a, b) => (a * b));
}
```

## How good are you really? 
-----------
https://www.codewars.com/kata/how-good-are-you-really/

**Task overview:**
You got an array with your colleges' points. Now calculate the average to your points!
Your points are not included in the array of your classes points. 
For calculating the average point you may add your point to the given array! 


 ```javascript
function betterThanAverage(classPoints, yourPoints) {
  var average = (classPoints.reduce((a,b) => (a + b),0) + yourPoints) / (classPoints.length + 1);
  return result = (average < yourPoints) ? true : false;
}
```

 ```javascript
function betterThanAverage(classPoints, yourPoints) {
  return yourPoints > (classPoints.reduce((a,b) => (a+b)) + yourPoints) / (classPoints.length+1)
}
```

## Convert to Binary
-----------
https://www.codewars.com/kata/convert-to-binary  

**Task overview:**
Given a non-negative integer n, write a function toBinary/ToBinary which returns that number in a binary format. 
 ```javascript
const toBinary = n => parseInt(n.toString(2));
```


## Square(n) Sum
-------------
https://www.codewars.com/kata/515e271a311df0350d00000f

**Task overview:**
Complete the square sum function so that it squares each number passed into it and then sums the results together 

 ```javascript
function squareSum(numbers){
  let result = 0;
  for (let i = 0; i < numbers.length; i++) {
  result += Math.pow(numbers[i], 2);
}
  return result;
}
```

 ```javascript
function squareSum(numbers){
  return numbers.reduce((sum,num) => sum + Math.pow(num, 2), 0);
}
```
  
 ## Beginner - Lost Without a Map
 ---------------
 https://www.codewars.com/kata/57f781872e3d8ca2a000007e
  
 **Task overview:**
Given an array of integers, return a new array with each value doubled 

 ```javascript
const maps = x => x.map( x => x * 2 );
```
  
## How many lightsabers do you own?
-----------------
https://www.codewars.com/kata/51f9d93b4095e0a7200001b8

 **Task overview:**
Inspired by the development team at Vooza, write the function *howManyLightsabersDoYouOwn*/*how_many_light_sabers_do_you_own* that

- accepts the name of a programmer, and
- returns the number of lightsabers owned by that person.

The only person who owns lightsabers is Zach, by the way. He owns 18, which is an awesome number of lightsabers. Anyone else owns 0.

Note: your function should have a default parameter.
 ```javascript
const howManyLightsabersDoYouOwn = name => name === 'Zach' ? 18 : 0;
```
 