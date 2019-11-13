# Total completed: 21
## Is this a triangle? 
https://www.codewars.com/kata/students-final-grade

Implement a method that accepts 3 integer values ```a```, ```b```, ```c```. The method should return ```true``` if a triangle can be built with the sides of given length and ```false``` in any other case. In this case, all triangles must have surface ```greater than 0``` to be accepted.

```javascript
function isTriangle(a,b,c) {
    if ((a + b > c) && (a + c > b) && (b + c > a)) {
      return true;
    } else {
     return false;
  }
}
```

```javascript
function isTriangle(a,b,c) {
   return a + b > c && a + c > b && b + c > a;
}
```


## Friend or Foe?
https://www.codewars.com/kata/friend-or-foe/

Make a program that filters a list of strings and returns a list with only your friends name in it. If a name has exactly 4 letters in it, you can be sure that it has to be a friend of yours! Otherwise, you can be sure he's not...

```javascript
function friend(friends){
  var realFriends = [];
  for (var i = 0; i < friends.length; i++ ) {
    if (friends[i].length == 4) {
      realFriends.push(friends[i]);
    } 
  }
  return realFriends;
}
``` 

```javascript
function friend(friends){
  return friends.filter(n => n.length === 4);
}
```

## Reverse words
https://www.codewars.com/kata/reverse-words/

Complete the function that accepts a string parameter, and reverses each word in the string. All spaces in the string should be retained.

```javascript
function reverseWords(str) {
 return str.split("").reverse().join("").split(/\s/g).reverse().join(" ");
}
```

```javascript
function reverseWords(str) {
  return str.split(" ").map(str => str.split("").reverse().join("")).join(" ");
}
```
   
## Descending order 
https://www.codewars.com/kata/descending-order/

Your task is to make a function that can take any non-negative integer as a argument and return it with its digits in descending order. Essentially, rearrange the digits to create the highest possible number.

###### Examples:
* Input: ```21445```        Output: ```54421```
* Input: ```145263```       Output: ```654321```
* Input: ```1254859723```   Output: ```9875543221```


```javascript
function descendingOrder(n){
  return parseInt(Array.from(String(n), Number).sort((a,b) => b - a).join(""));
}
```
   
    
## Club Doorman 
https://www.codewars.com/kata/club-doorman

###### INTRODUCTION

The Club Doorman will give you a word. To enter the Club you need to provide the right number according to provided the word. Every given word has a doubled letter, like ```'tt'``` in lettuce. To answer the right number you need to find the doubled letter's position of the given word in the alphabet and multiply this number per ```3```. It will be given only words with one doubled letter.

###### EXAMPLE
```Lettuce``` is the given word. ```'t'``` is the doubled letter and it's position is ```20``` in the alphabet. The answer to the Club Doorman is ```20 * 3 = 60```

###### TASK
The function ```passTheDoorMan``` with a given string word shall return the right number.
 
 ```javascript
 function passTheDoorMan (word){
  var doubleLetter;
  for (var i = 0; i < word.length-1; i++) 
    if (word[i] == word[i+1]) {
      doubleLetter = word[i];
      break;
    }
  return (doubleLetter.charCodeAt()-96)*3;
}
```

```javascript
const passTheDoorMan = word => ((word.match(/(.)\1/)[1]).charCodeAt(0) - 96) * 3;
```

## Simple Fun #152: Invite More Women?
https://www.codewars.com/kata/simple-fun-number-152-invite-more-women/

King Arthur and his knights are having a New Years party. Last year Lancelot was jealous of Arthur, because Arthur had a date and Lancelot did not, and they started a duel. To prevent this from happening again, Arthur wants to make sure that there are at least as many women as men at this year's party. He gave you a list of integers of all the party goers. Arthur needs you to return true if he needs to invite more women or false if he is all set.

```javascript
function inviteMoreWomen(L) {
  var men = 0;
  var women = 0;
  for (var i = 0; i < L.length; i++) {
    if ( L[i] > 0 ) {
      men += 1;
    } else {
      women += 1;
    }
  }
  
  if (men > women) {
    return true;
  } else {
    return false;
  }
}
```

```javascript
const inviteMoreWomen = L => L.reduce((a,b) => a+b) > 0;
```


## Disemvowel Trolls
https://www.codewars.com/kata/disemvowel-trolls

Trolls are attacking your comment section! A common way to deal with this situation is to remove all of the vowels from the trolls' comments, neutralizing the threat. Your task is to write a function that takes a string and return a new string with all vowels removed. For example, the string ```"This website is for losers LOL!"``` would become ```"Ths wbst s fr lsrs LL!"```. 
```Note:``` for this kata ```y``` isn't considered a vowel.

```javascript
const disemvowel = str => str.replace(/[aeiou]/gi, '');
```
   
 ## Return the first M multiples of N
 https://www.codewars.com/kata/return-the-first-m-multiples-of-n/
 
Implement a function, ```multiples(m, n)```, which returns an array of the first ```m``` multiples of the real number ```n```. Assume that ```m``` is a positive integer.

###### Example:
```multiples(3, 5)``` should return ```vec![5, 10, 15]```

```javascript  
 function multiples(m, n){
    let result = [];
    for (let i = 1; i <= m; i++) {
        result.push(i*n);
 }
    return result;
}
```

```javascript
const multiples = (m, n) => Array.from(Array(m), (_, i) => n* i + n);
```


## Complementary DNA
https://www.codewars.com/kata/complementary-dna

Deoxyribonucleic acid ```(DNA)``` is a chemical found in the nucleus of cells and carries the "instructions" for the development and functioning of living organisms. In DNA strings, symbols ```"A"``` and ```"T"``` are complements of each other, as ```"C"``` and ```"G"```. You have function with one side of the DNA you need to get the other complementary side. DNA strand is never empty or there is no DNA at all.

###### Example: 
* DNAStrand ("ATTGC") // return "TAACG"
* DNAStrand ("GTAT") // return "CATA" 



```javascript
function DNAStrand(dna){
  let complementDNA = '';
  for(let i = 0; i < dna.length; i++){
    if(dna[i] === 'T'){
      complementDNA += 'A';
    }
    if(dna[i] === 'A'){
      complementDNA += 'T';
    }
    if(dna[i] === 'C'){
      complementDNA += 'G';
    }
    if(dna[i] === 'G'){
      complementDNA += 'C';
    }
  }
  return complementDNA;
}
```


```javscript
const DNAStrand = dna => dna.replace(/./g, x => "ATCG"["TAGC".indexOf(x)]);
```
   
    
## Sum of odd numbers
https://www.codewars.com/kata/sum-of-odd-numbers/

Given the triangle of consecutive odd numbers:
```
             1
          3     5
       7     9    11
   13    15    17    19
21    23    25    27    29
...
```
Calculate the row sums of this triangle from the row index (starting at index ```1```) 

###### Example: 

* rowSumOddNumbers(1); // 1
* rowSumOddNumbers(2); // 3 + 5 = 8


```javascript
const rowSumOddNumbers = n => Math.pow(n, 3);
```
  
 ## Alphabetical Addition
 https://www.codewars.com/kata/alphabetical-addition/
 
Your task is to add up letters to one letter. The function will be given a variable amount of arguments, each one being a letter to add.

###### Notes:
* Letters will always be lowercase.
* Letters can overflow (see second to last example of the description)
* If no letters are given, the function should return ```'z'```

```javascript
const addLetters = (...letters) => String.fromCharCode((letters.reduce((sum, x) => sum + x.charCodeAt() - 96, 0) % 26 || 26) + 96);
```

## Drying Potatoes
https://www.codewars.com/kata/drying-potatoes/

All we eat is water and dry matter. John bought potatoes: their weight is ```100``` kilograms. Potatoes contain water and dry matter. The water content is ```99 percent``` of the total weight. He thinks they are too wet and puts them in an oven - at low temperature - for them to lose some water. At the output the water content is only ```98%```. What is the total weight in kilograms (water content plus dry matter) coming out of the oven? He finds ```50 kilograms``` and he thinks he made a mistake: "So much weight lost for such a small change in water content! Can you help him?

Write function ```potatoes``` with
* int parameter ```p0``` - initial percent of water
* int parameter ```w0``` - initial weight 
* int parameter ```p1``` - final percent of water 

```potatoes``` should return the final weight coming out of the oven ```w1``` truncated as an int.

 ###### Example:
 * ```potatoes(99, 100, 98) --> 50```
 

```javascript
const potatoes = (p0, w0, p1) => Math.floor(w0 * (100 - p0) / (100 - p1));
```

    

## Growth of a Population
https://www.codewars.com/kata/growth-of-a-population/


In a small town the population is ```p0 = 1000``` at the beginning of a year. The population regularly increases by ```2``` percent per year and moreover ```50``` new inhabitants per year come to live in the town. How many years does the town need to see its population greater or equal to ```p = 1200``` inhabitants? 

* At the end of the first year there will be: 1000 + 1000 * 0.02 + 50 => 1070 inhabitants
* At the end of the 2nd year there will be: 1070 + 1070 * 0.02 + 50 => 1141 inhabitants (number of inhabitants is an integer)
* At the end of the 3rd year there will be: 1141 + 1141 * 0.02 + 50 => 1213
* It will need 3 entire years.

 More generally given parameters:
 ```p0, percent, aug (inhabitants coming or leaving each year), p (population to surpass)```
 the function ```nb_year``` should return ```n``` number of entire years needed to get a population greater or equal to ```p```.
 aug is an integer, percent a positive or null number, p0 and p are positive integers (> 0)

###### Examples:
* nb_year(1500, 5, 100, 5000) -> 15
* nb_year(1500000, 2.5, 10000, 2000000) -> 10
* ```Note```: Don't forget to convert the percent parameter as a percentage in the body of your function: if the parameter percent is 2 you have to convert it to 0.02.

```javascript
function nbYear(p0, percent, aug, p) {
    let count = 0;
    while ( p0 < p ) {
      p0 = p0 + ((p0 * percent) / 100) + aug;
      count++;
    }
  return count;
}
```
  


## Binary Addition
https://www.codewars.com/kata/binary-addition/


Implement a function that adds two numbers together and returns their sum in binary. The conversion can be done before, or after the addition. The binary number returned should be a string.

```javascript
const addBinary= (a,b) => (a + b).toString(2);
```

    

## Spacify
https://www.codewars.com/kata/spacify

Modify the spacify function so that it returns the given string with spaces insertedbetween each character:  ```spacify("hello world") // returns "h e l l o   w o r l d"```

```javascript
const spacify = str => str.split("").join(" ");
```

  

## The Poet And The Pendulum
https://www.codewars.com/kata/the-poet-and-the-pendulum

###### Task
Given an array/list [] of ```n``` integers, arrange them in a way similar to the to-and-fro movement of a Pendulum. The smallest element of the list of integers, must come in center position of array/list. The higher than smallest, goes to the right. The next higher number goes to the left of minimum number and so on, in a to-and-fro manner similar to that of a Pendulum.

###### Notes
Array/list size is at least ```3```.
 In even array size , The minimum element should be moved to ```(n-1)/2``` index (considering that indexes start from ```0```)
Repetition of numbers in the array/list could occur , So (duplications are included when arranging).
 
###### Input >> Output Examples:
```pendulum ([6, 6, 8 ,5 ,10]) ==> [10, 6, 5, 6, 8]```

###### Explanation:
 Since, 5 is the the smallest element of the list of integers, came in the center position of array/list
 The higher than smallest is 6 goes to the right of 5 .
 The next higher number goes to the left of minimum number and so on .
 Remember, duplications are included when arranging, don't delete them .
 ```pendulum ([-9, -2, -10, -6]) ==> [-6, -10, -9, -2]```

###### Explanation:
 Since , -10 is the The Smallest element of the list of integers , came in The center position of array/list
 The Higher than smallest is -9 goes to the right of it .
 The Next higher number goes to the left of -10 , and So on .
 Remember , in even array size , The minimum element moved to (n-1)/2 index (considering that indexes start from 0) .
 ```pendulum ([11, -16, -18, 13, -11, -12, 3, 18 ]) ==> [13, 3, -12, -18, -16, -11, 11, 18]```

###### Explanation:
 Since , -18 is the The Smallest element of the list of integers , came in The center position of array/list
 The Higher than smallest is -16 goes to the right of it .
 The Next higher number goes to the left of -18 , and So on .
 Remember , in even array size , The minimum element moved to (n-1)/2 index (considering that indexes start from 0) .

```javascript
function pendulum(values) {
  let arr = [];
  let result = [];
  values.sort((x, y) => x - y).forEach((y, x) => (x % 2 ? arr : result).push(y));
  return result.reverse().concat(arr)
}
```
    
      
## Thinking & Testing: A and B?
https://www.codewars.com/kata/thinking-and-testing-a-and-b/

No Description. Only by Thinking and Testing. Look at the results of the testcases, and guess the code!

```Test.assertSimilar(testit([0,0,0,0]), 0, "")```
    ```Test.assertSimilar(testit([0,0,0,1]), 0, "")```
    ```Test.assertSimilar(testit([0,0,1,1]), 0, "")```
    ```Test.assertSimilar(testit([0,1,0,1]), 0, "")```
    ```Test.assertSimilar(testit([0,1,1,0]), 1, "")```
    ```Test.assertSimilar(testit([1,0,0,1]), 1, "")```
    ```Test.assertSimilar(testit([9,2,7,0]), 14, "")```
    ```Test.assertSimilar(testit([8,2,6,4)), 44, "")```
    ```Test.assertSimilar(testit([9,5,9,5]), 90, "")```
    ```Test.assertSimilar(testit([4,4,1,9]), 40, "")```


```javascript
function testit(arr){
  let a = arr[0] * arr[3];
  let b = arr[1] * arr[2];
  return a + b;
}
```

```javascript
const  testit = ([a, b, c, d]) => b * c + a * d;
```
    
## String ends with?
https://www.codewars.com/kata/string-ends-with/

 Complete the solution so that it returns true if the first argument(string) passed in ends with the 2nd argument (also a string).

```javascript
const solution = (str, ending) => str.includes(ending, [str.length - ending.length]);
```

```javascript
const solution = (str, ending) => str.endsWith(ending);
```
   

## Password Hashes
https://www.codewars.com/kata/password-hashes/

When you sign up for an account somewhere, some websites do not actually store your password in their databases. Instead, they will transform your password into something else using a cryptographic hashing algorithm. After the password is transformed, it is then called a password hash. Whenever you try to login, the website will transform the password you tried using the same hashing algorithm and simply see if the password hashes are the same. Create the function that converts a given string into an ```md5``` hash. The return value should be encoded in hexadecimal.

```javascript
const passHash = str => require('crypto').createHash('md5').update(str).digest('hex');
```
   



## Ten Green Bottles
https://www.codewars.com/kata/ten-green-bottles/

###### Lyrics:  

 
```
 Ten green bottles hanging on the wall,
 Ten green bottles hanging on the wall,
 And if one green bottle should accidentally fall,
 There'll be nine green bottles hanging on the wall.

 Nine green bottles hanging on the wall,
 Nine green bottles hanging on the wall,
 And if one green bottle should accidentally fall,
There'll be eight green bottles hanging on the wall. 

 Eight green bottles hanging on the wall...
 Seven green bottles hanging on the wall...
...

 One green bottle hanging on the wall,
 One green bottle hanging on the wall,
 If that one green bottle should accidentally fall,
 There'll be no green bottles hanging on the wall.
 ```
 ###### Task
 Write some amazing code to reproduce the above lyrics starting from ```n``` green bottles!

 parameter ```n``` is ```1``` to ```10```
 newline terminates every line (including the last)
 don't forget the blank lines between the verses

```javascript
function tenGreenBottles(n) {
    
    let result = [];
    const convert = {
      10 : "ten",
       9 : "nine",
       8 : "eight",
       7 : "seven",
       6 : "six",
       5 : "five",
       4 : "four",
       3 : "three",
       2 : "two",
       1 : "one",
       0 : "no"
    }
    
    const line1 = () => `${convert[n].replace(/^[a-z]/, x => x.toUpperCase())} green bottle${n !== 1 ? 's' : ''} hanging on the wall,`,
          line3 = () => `${n > 1 ? 'And if' : 'If that'} one green bottle should accidentally fall,`,
          line4 = () => `There'll be ${convert[n - 1]} green bottle${n - 1 !== 1 ? 's' : ''} hanging on the wall.`;
        
                
    while ( n > 0 ) {
      result.push(line1(), line1(), line3(), line4(), '');
      n--;
    }
    return result.join('\n');
}  
```

## Odder Than the Rest
https://www.codewars.com/kata/odder-than-the-rest/

Create a method that takes an array/list as an input, and outputs the index at which the sole odd number is located. This method should work with arrays with negative numbers. If there are no odd numbers in the array, then the method should output ```-1```

```javascript
const oddOne = arr => arr.findIndex(x => x % 2 !== 0);
```
 