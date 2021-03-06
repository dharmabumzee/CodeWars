# Total completed: 20
## Sums of Parts
https://www.codewars.com/kata/sums-of-parts/

Let us consider this example (array written in general format):

```ls = [0, 1, 3, 6, 10]```

Its following parts:

```ls = [0, 1, 3, 6, 10]```
```ls = [1, 3, 6, 10]```
```ls = [3, 6, 10]```
```ls = [6, 10]```
```ls = [10]```
```ls = []```

The corresponding sums are (put together in a list): ```[20, 20, 19, 16, 10, 0]```

The function ```parts_sums``` (or its variants in other languages) will take as parameter a list ```ls``` and return a list of the sums of its parts as defined above.

###### Other Examples:

```ls = [1, 2, 3, 4, 5, 6] ```
```parts_sums(ls) -> [21, 20, 18, 15, 11, 6, 0]```

```ls = [744125, 935, 407, 454, 430, 90, 144, 6710213, 889, 810, 2579358]```
```parts_sums(ls) -> [10037855, 9293730, 9292795, 9292388, 9291934, 9291504, 9291414, 9291270, 2581057, 2580168, 2579358, 0]```
###### Notes:
Some lists can be long.
Please ask before translating: some translations are already written and published when/if the kata is approved.

```javascript
function partsSums(ls) {
    let sum = ls.reduce((a,b) => a + b, 0);
    return [sum, ...ls.map(x => sum -= x)];
}
```

## Give me a Diamond
https://www.codewars.com/kata/give-me-a-diamond/

Jamie is a programmer, and James' girlfriend. She likes diamonds, and wants a diamond string from James. Since James doesn't know how to make this happen, he needs your help.

###### Task
You need to return a string that looks like a diamond shape when printed on the screen, using asterisk (```*```) characters. Trailing spaces should be removed, and every line must be terminated with a newline character (```\n```).

Return ```null/nil/None/...``` if the input is an even number or negative, as it is not possible to print a diamond of even or negative size.

###### Examples
A size 3 diamond:
```
 *
***
 *
 ```
...which would appear as a string of ```" *\n***\n *\n"```

A size 5 diamond:
```
  *
 ***
*****
 ***
  *
  ```
...that is: ```" *\n ***\n*****\n ***\n *\n"```


```javascript
function diamond(n){
  if (n < 1 || n % 2 == 0) return null;
  return Array.apply(null, {length: n})
    .map((e, i) => {
      const spaces = Math.abs(i - (Math.floor(n / 2)));
      const draw = n - spaces * 2;
      return Array(spaces + 1).join(' ') + Array(draw + 1).join('*');
    })
    .join('\n') + '\n';
  }
```



## Equal Sides Of An Array
https://www.codewars.com/kata/equal-sides-of-an-array/

You are going to be given an array of integers. Your job is to take that array and find an index N where the sum of the integers to the left of N is equal to the sum of the integers to the right of N. If there is no index that would make this happen, return -1.

###### For example:

Let's say you are given the array {1,2,3,4,3,2,1}:
Your function will return the index 3, because at the 3rd position of the array, the sum of left side of the index ({1,2,3}) and the sum of the right side of the index ({3,2,1}) both equal 6.

###### Let's look at another one.
You are given the array {1,100,50,-51,1,1}:
Your function will return the index 1, because at the 1st position of the array, the sum of left side of the index ({1}) and the sum of the right side of the index ({50,-51,1,1}) both equal 1.

###### Last one:
You are given the array {20,10,-80,10,10,15,35}
At index 0 the left side is {}
The right side is {10,-80,10,10,15,35}
They both are equal to 0 when added. (Empty arrays are equal to 0 in this problem)
Index 0 is the place where the left side and right side are equal.

###### Note: Please remember that in most programming/scripting languages the index of an array starts at 0.

###### Input:
An integer array of length 0 < arr < 1000. The numbers in the array can be any integer positive or negative.

###### Output:
The lowest index N where the side to the left of N is equal to the side to the right of N. If you do not find an index that fits these rules, then you will return -1.

###### Note:
If you are given an array with multiple answers, return the lowest correct index.

```javascript
function findEvenIndex(arr) {

 let rightSum = 0, leftSum = 0;
 
 arr.forEach(i => rightSum += i);

 for (let i = 0; i < arr.length; i++) {
    rightSum -= arr[i];

    if (leftSum === rightSum) {
      return i;
    }

    leftSum += arr[i];
  }

  return -1;
 }
```


## Find the odd int
https://www.codewars.com/kata/find-the-odd-int

Given an array, find the integer that appears an odd number of times.

There will always be only one integer that appears an odd number of times.

```javascript
function findOdd(A) {
  let count = 0;
  for(let i = 0; i < A.length; i++) {
    for(let j = 0; j < A.length; j++) {
          if(A[i] == A[j]) {
            count++;
          }
        }
    if (count % 2 !== 0) {
        return A[i];
    }
  }
  count = 0;
}
```

```javascript
 const findOdd = A => A.reduce((a, b) => a ^ b);
```


## Encrypt this!
https://www.codewars.com/kata/encrypt-this/

###### Description:

You want to create secret messages which can be deciphered by the Decipher this! kata. Here are the conditions:

Your message is a string containing space separated words.
You need to encrypt each word in the message using the following rules:
The first letter needs to be converted to its ASCII code.
The second letter needs to be switched with the last letter
Keepin' it simple: There are no special characters in input.
###### Examples:
encryptThis("Hello") === "72olle"
encryptThis("good") === "103doo"
encryptThis("hello world") === "104olle 119drlo"

```javascript
const encryptThis = text => text.replace(/\b\w(\w?)(\w*?)(\w?)\b/g, (word, second, mid, last) => word.charCodeAt(0) + last + mid + second);

```

## Format a string of names like 'Bart, Lisa & Maggie'.
https://www.codewars.com/kata/format-a-string-of-names-like-bart-lisa-and-maggie/

Given: an array containing hashes of names

Return: a string formatted as a list of names separated by commas except for the last two names, which should be separated by an ampersand.

###### Example:

list([ {name: 'Bart'}, {name: 'Lisa'}, {name: 'Maggie'} ])
// returns 'Bart, Lisa & Maggie'

list([ {name: 'Bart'}, {name: 'Lisa'} ])
// returns 'Bart & Lisa'

list([ {name: 'Bart'} ])
// returns 'Bart'

list([])
// returns ''

Note: all the hashes are pre-validated and will only contain A-Z, a-z, '-' and '.'.


```javascript
const list = names => names.map(x => x.name).join(", ").replace(/,(?!.*,)/gmi, " &");
```

## Prefill an Array
https://www.codewars.com/kata/prefill-an-array/

Create the function prefill that returns an array of n elements that all have the same value v. See if you can do this without using a loop.

You have to validate input:

v can be anything (primitive or otherwise)
if v is ommited, fill the array with undefined
if n is 0, return an empty array
if n is anything other than an integer or integer-formatted string (e.g. '123') that is >=0, throw a TypeError
When throwing a TypeError, the message should be n is invalid, where you replace n for the actual value passed to the function.

Code Examples

    prefill(3,1) --> [1,1,1]

    prefill(2,"abc") --> ['abc','abc']

    prefill("1", 1) --> [1]

    prefill(3, prefill(2,'2d'))
      --> [['2d','2d'],['2d','2d'],['2d','2d']]

    prefill("xyz", 1)
      --> throws TypeError with message "xyz is invalid"

```javascript
function throwTypeError(n) {
   throw new TypeError(`${n} is invalid`);
}

const prefill = (n, v) => (n === 0 || n === '0') ? [] : 
    typeof n === 'boolean' || 
    !Number.isInteger(Number(n)) || 
    Number(n) < 0 ? 
    throwTypeError(n) : new Array(n).fill(v);
```

## Highest Rank Number in an Array
https://www.codewars.com/kata/highest-rank-number-in-an-array

Complete the method which returns the number which is most frequent in the given input array. If there is a tie for most frequent number, return the largest number among them.

Note: no empty arrays will be given.

Examples
[12, 10, 8, 12, 7, 6, 4, 10, 12]              -->  12
[12, 10, 8, 12, 7, 6, 4, 10, 12, 10]          -->  12
[12, 10, 8, 8, 3, 3, 3, 3, 2, 4, 10, 12, 10]  -->   3

```javascript
const highestRank = arr => arr.sort( (x, y) => arr.filter(i => i === y).length - arr.filter(i => i === x).length)[0];
```

## IPv4 to int32
https://www.codewars.com/kata/ipv4-to-int32/

Take the following IPv4 address: 128.32.10.1 This address has 4 octets where each octet is a single byte (or 8 bits).

1st octet 128 has the binary representation: 10000000
2nd octet 32 has the binary representation: 00100000
3rd octet 10 has the binary representation: 00001010
4th octet 1 has the binary representation: 00000001
So 128.32.10.1 == 10000000.00100000.00001010.00000001

Because the above IP address has 32 bits, we can represent it as the 32 bit number: 2149583361.

Write a function ip_to_int32(ip) ( JS: ipToInt32(ip) ) that takes an IPv4 address and returns a 32 bit number.

  ipToInt32("128.32.10.1") => 2149583361
  
  ```javascript
  const ipToInt32 = ip => ip.split('.').reduce( ( int, v ) => 256 * int + Number(v), 0);
  ```
  
## Reverse every other word in the string
https://www.codewars.com/kata/reverse-every-other-word-in-the-string
  
Reverse every other word in a given string, then return the string. 
Throw away any leading or trailing whitespace, while ensuring there is exactly one space between each word. 
Punctuation marks should be treated as if they are apart of the word in this kata.
  
```javascript
const reverse = str => str.trim().split(' ').map( (word, index) =>  index % 2 == 0 ? word : word.split('').reverse().join('')).join(' ');
```
  
## Title Case
https://www.codewars.com/kata/title-case

A string is considered to be in title case if each word in the string is either (a) capitalised (that is, only the first letter of the word is in upper case) or (b) considered to be an exception and put entirely into lower case unless it is the first word, which is always capitalised.

Write a function that will convert a string into title case, given an optional list of exceptions (minor words). The list of minor words will be given as a string with each word separated by a space. Your function should ignore the case of the minor words string -- it should behave in the same way even if the case of the minor word string is changed.

###Arguments (Haskell)

First argument: space-delimited list of minor words that must always be lowercase except for the first word in the string.
Second argument: the original string to be converted.
###Arguments (Other languages)

First argument (required): the original string to be converted.
Second argument (optional): space-delimited list of minor words that must always be lowercase except for the first word in the string. The JavaScript/CoffeeScript tests will pass undefined when this argument is unused.
###Example

titleCase('a clash of KINGS', 'a an the of') // should return: 'A Clash of Kings'
titleCase('THE WIND IN THE WILLOWS', 'The In') // should return: 'The Wind in the Willows'
titleCase('the quick brown fox') // should return: 'The Quick Brown Fox'


```javascript
const titleCase = (title, minorWords) => {
  
  if (title.length === 0) {
    return '';
  }
  
  let minorArr;
  
  minorWords ? minorArr = minorWords.toLowerCase().split(' ') : minorArr = [];
  
  let titleArr = title.toLowerCase().split(' ');
  
  titleArr[0] = capitalize(titleArr[0]);
  
  for (let i = 0; i < titleArr.length; i++) {
    if (minorArr.indexOf(titleArr[i]) === -1) {
      titleArr[i] = capitalize(titleArr[i]);
    }
  }
  
  return titleArr.join(' ');
}

let capitalize = str => str[0].toUpperCase() + str.slice(1);
```

```javascript
String.prototype.capitalize = function() {
    return this.charAt(0).toUpperCase() + this.slice(1).toLowerCase();
}

function titleCase(title, minorWords) {
   let titleArr = title.toLowerCase().split(' '), minorWordsArr = minorWords ? minorWords.toLowerCase().split(' ') : [];
   return titleArr.map( (a, b) => minorWordsArr.indexOf(a) === -1 || b === 0 ? a.capitalize() : a ).join(' ');
}
```

## Row of the odd triangle
https://www.codewars.com/kata/row-of-the-odd-triangle/

Given a triangle of consecutive odd numbers:

             1
          3     5
       7     9    11
   13    15    17    19
21    23    25    27    29
...
find the triangle's row knowing its index (the rows are 1-indexed), e.g.:

odd_row(1)  ==  [1]
odd_row(2)  ==  [3, 5]
odd_row(3)  ==  [7, 9, 11]
Note: your code should be optimized to handle big inputs.



```javascript
const oddRow = n => Array(n).fill(0).map( (e, i) => Math.pow(n, 2) - n + 1 + i * 2 );
```

## Your order, please
https://www.codewars.com/kata/your-order-please

Your task is to sort a given string. Each word in the string will contain a single number. This number is the position the word should have in the result.

Note: Numbers can be from 1 to 9. So 1 will be the first word (not 0).

If the input string is empty, return an empty string. The words in the input String will only contain valid consecutive numbers.

Examples
"is2 Thi1s T4est 3a"  -->  "Thi1s is2 3a T4est"
"4of Fo1r pe6ople g3ood th5e the2"  -->  "Fo1r the2 g3ood 4of th5e pe6ople"
""  -->  ""

```javscript
const order = words => words.split(' ').sort((a, b) => a.match(/\d/) - b.match(/\d/)).join(' ');
```

## English beggars
https://www.codewars.com/kata/english-beggars

Born a misinterpretation of this kata, your task here is pretty simple: given an array of values and an amount of beggars, you are supposed to return an array with the sum of what each beggar brings home, assuming they all take regular turns, from the first to the last.

For example: [1,2,3,4,5] for 2 beggars will return a result of [9,6], as the first one takes [1,3,5], the second collects [2,4].

The same array with 3 beggars would have in turn have produced a better out come for the second beggar: [5,7,3], as they will respectively take [1,4], [2,5] and [3].

Also note that not all beggars have to take the same amount of "offers", meaning that the length of the array is not necessarily a multiple of n; length can be even shorter, in which case the last beggers will of course take nothing (0).

Note: in case you don't get why this kata is about English beggars, then you are not familiar on how religiously queues are taken in the kingdom ;)

```javascript
const beggars = (values, n) => values.reduce( (result, val, i) => { result[i % n] += val; return result; }, Array(n).fill(0));
```

## Data Reverse
https://www.codewars.com/kata/data-reverse

A stream of data is received and needs to be reversed.

Each segment is 8 bits long, meaning the order of these segments needs to be reversed, for example:

11111111  00000000  00001111  10101010
 (byte1)   (byte2)   (byte3)   (byte4)
should become:

10101010  00001111  00000000  11111111
 (byte4)   (byte3)   (byte2)   (byte1)
The total number of bits will always be a multiple of 8.

The data is given in an array as such:

[1,1,1,1,1,1,1,1,0,0,0,0,0,0,0,0,0,0,0,0,1,1,1,1,1,0,1,0,1,0,1,0]

```javascript
const dataReverse = data => data.join('').match(/.{8}/g).reverse().join('').split('').map(x => x * 1) || []
```

## Take a Ten Minute Walk
https://www.codewars.com/kata/take-a-ten-minute-walk/

You live in the city of Cartesia where all roads are laid out in a perfect grid. 
You arrived ten minutes too early to an appointment, so you decided to take the opportunity to go for a short walk. 
The city provides its citizens with a Walk Generating App on their phones -- 
everytime you press the button it sends you an array of one-letter strings representing directions to walk 
(eg. ['n', 's', 'w', 'e']). 
You always walk only a single block in a direction and you know it takes you one minute to traverse one city block, 
so create a function that will return true if the walk the app gives you will take you exactly ten minutes 
(you don't want to be early or late!) and will, of course, return you to your starting point. Return false otherwise.

Note: you will always receive a valid array containing a random assortment of direction letters 
('n', 's', 'e', or 'w' only). It will never give you an empty array (that's not a walk, that's standing still!).

```javascript
const count = (walk, dir) => walk.filter(direction => direction === dir).length

const isValidWalk = walk =>
  walk.length === 10 &&
  count(walk, 'n') === count(walk, 's') &&
  count(walk, 'w') === count(walk, 'e')
```

## Linked Lists - Length & Count
https://www.codewars.com/kata/linked-lists-length-and-count/

Implement Length() to count the number of nodes in a linked list.

length(null) => 0
length(1 -> 2 -> 3 -> null) => 3
Implement Count() to count the occurrences of an integer in a linked list.

count(null, 1) => 0
count(1 -> 2 -> 3 -> null, 1) => 1
count(1 -> 1 -> 1 -> 2 -> 2 -> 2 -> 2 -> 3 -> 3 -> null, 2) => 4

Inspired by Stanford Professor Nick Parlante's excellent - http://cslibrary.stanford.edu/103/LinkedListBasics.pdf

```javascript
function Node(data) {
  this.data = data
  this.next = null
}

const length = head => head ? 1 + length(head.next) : 0

const count = (head, data) => !head ? 0 : (head.data === data ? 1 : 0) + count(head.next, data)
```

## Salesman's Travel
https://www.codewars.com/kata/salesmans-travel

A traveling salesman has to visit clients. He got each client's address e.g. "432 Main Long Road St. Louisville OH 43071" as a list.

The basic zipcode format usually consists of two capital letters followed by a white space and five digits. The list of clients to visit was given as a string of all addresses, each separated from the others by a comma, e.g. :

"123 Main Street St. Louisville OH 43071,432 Main Long Road St. Louisville OH 43071,786 High Street Pollocksville NY 56432".

To ease his travel he wants to group the list by zipcode.

Task
The function travel will take two parameters r (addresses' list of all clients' as a string) and zipcode and returns a string in the following format:

zipcode:street and town,street and town,.../house number,house number,...

The street numbers must be in the same order as the streets where they belong.

If a given zipcode doesn't exist in the list of clients' addresses return "zipcode:/"

Examples
r = "123 Main Street St. Louisville OH 43071,432 Main Long Road St. Louisville OH 43071,786 High Street Pollocksville NY 56432"

travel(r, "OH 43071") --> "OH 43071:Main Street St. Louisville,Main Long Road St. Louisville/123,432"

travel(r, "NY 56432") --> "NY 56432:High Street Pollocksville/786"

travel(r, "NY 5643") --> "NY 5643:/"
Note for Elixir:
In Elixir the empty addresses' input is an empty list, not an empty string.

Note:
You can see a few addresses and zipcodes in the test cases.

```javascript
function travel(r, zipcode) {
 
  let regex = RegExp('(\\d+)\\s+(.+)\\s+' + zipcode + '$');

  let address = r.split(',').map(r => r.match(regex)).filter(r => r);

  return `${zipcode}:${address.map(r => r[2])}/${address.map(r => r[1])}`;
}
```

## Playing on a chessboard
https://www.codewars.com/kata/playing-on-a-chessboard/


With a friend we used to play the following game on a chessboard (8, rows, 8 columns). On the first row at the bottom we put numbers:

1/2, 2/3, 3/4, 4/5, 5/6, 6/7, 7/8, 8/9

On row 2 (2nd row from the bottom) we have:

1/3, 2/4, 3/5, 4/6, 5/7, 6/8, 7/9, 8/10

On row 3:

1/4, 2/5, 3/6, 4/7, 5/8, 6/9, 7/10, 8/11

until last row:

1/9, 2/10, 3/11, 4/12, 5/13, 6/14, 7/15, 8/16

When all numbers are on the chessboard each in turn we toss a coin. The one who get "head" wins and the other gives him, in dollars, the sum of the numbers on the chessboard. We play for fun, the dollars come from a monopoly game!

Task
How much can I (or my friend) win or loses for each game if the chessboard has n rows and n columns? Add all of the fractional values on an n by n sized board and give the answer as a simplified fraction.

Ruby, Python, JS, Coffee, Clojure, PHP, Elixir, Crystal, Typescript, Go:
The function called 'game' with parameter n (integer >= 0) returns as result an irreducible fraction written as an array of integers: [numerator, denominator]. If the denominator is 1 return [numerator].

Haskell:
'game' returns either a "Left Integer" if denominator is 1 otherwise "Right (Integer, Integer)"

Prolog: 'game' returns an irreducible fraction written as an array of integers: [numerator, denominator]. If the denominator is 1 return [numerator, 1].

Java, C#, C++, F#, Swift, Reason, Kotlin:

'game' returns a string that mimicks the array returned in Ruby, Python, JS, etc...

Fortran, Bash: 'game' returns a string
Forth: return on the stack the numerator and the denominator (even if the denominator is 1)
In Fortran - as in any other language - the returned string is not permitted to contain any redundant trailing whitespace: you can use dynamically allocated character strings.

```javascript
const game = n => n % 2 ? [Math.pow(n, 2), 2] : [Math.pow(n, 2) / 2];
```

## Create Phone Number
https://www.codewars.com/kata/create-phone-number

Write a function that accepts an array of 10 integers (between 0 and 9), that returns a string of those numbers in the form of a phone number.

Example:
createPhoneNumber([1, 2, 3, 4, 5, 6, 7, 8, 9, 0]) // => returns "(123) 456-7890"
The returned format must be correct in order to complete this challenge.
Don't forget the space after the closing parentheses!

```javascript
const createPhoneNumber = numbers => '(###) ###-####'.replace(/#/g, () => numbers.shift());
```
