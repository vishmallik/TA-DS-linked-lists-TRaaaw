## Solve the list of given problems:

For the given problems below write a function to solve the problem and write two test/example testing your solution.

1. Write Algorithms to Check if Two String are Anagram. An anagram is something where length and character matches but not the order like `listen` and `silent`, both have the same number of characters.

```js
function isAnagram(str1, str2) {
  if (str1.length === str2.length) {
    if (str1.split("").sort().join("") === str2.split("").sort().join("")) {
      return true;
    }
    return false;
  }
  return false;
}

//test

console.log(isAnagram("hackatoon", "achcthkon")); //false
console.log(isAnagram("listen", "silent")); //true
```

2. Given two non-empty array of numbers, write a function to find whether the second array is a subsequence of the first array or not.

A subsequence is a sequence that can be derived from an array by deleting some or no elements without changing the order of the remaining elements. For example, [3,6,2,7] is a subsequence of the array [0,3,1,6,2,2,7].

Example 1:

First array is `[1, 5, 23, 32, -42, 100]` and second array is `[23, 32, -42]`. In this example the second array is a subsequence of the first array.

Example 2:

First array is `[1, 5, 23, 32, -42, 100]` and second array is `[200, 23, 32, -42]`. In this example the second array is not a subsequence of the first array.

```js
function isSubsequenceArray(arr1, arr2) {
  let index1 = 0,
    index2 = 0;
  while (index1 < arr1.length && index2 < arr2.length) {
    if (arr1[index1] === arr2[index2]) {
      index1++;
      index2++;
    } else {
      index1++;
    }
  }
  return index2 === arr2.length;
}
console.log(isSubsequenceArray([1, 5, 23, 32, -42, 100], [23, 32, -42]));
console.log(isSubsequenceArray([1, 5, 23, 32, -42, 100], [100, 23, 32, -42]));
```

3. Hamming Distance

the Hamming distance between two strings of equal length is the number of positions at which the corresponding symbols are different. In other words, it measures the minimum number of substitutions required to change one string into the other, or the minimum number of errors that could have transformed one string into the other. In a more general context, the Hamming distance is one of several string metrics for measuring the edit distance between two sequences.

Examples:

Input: `karolin` and `kathrin`
Output: 3

Input: `karolin` and `kerstin`
Output: 3

Input: `1011101` and `1001001`
Output: 2

```js
function getHammingDistance(str1, str2) {
  let count = 0;
  if (str1.length === str2.length) {
    let arr1 = str1.split("");
    let arr2 = str2.split("");

    arr1.forEach((elm, i) => {
      if (elm !== arr2[i]) {
        count++;
      }
    });
    return count;
  }
  return console.log("String lengths are not equal.");
}
```

4. For a given number, find all the prime numbers in an array from zero to that number.

```js
function checkPrimeNumbers(num) {
  for (let i = 2; i < num; i++) {
    if (num % i === 0) {
      return false;
    }
  }
  return true;
}
function getAllPrimeNumbers(num) {
  let finalArr = [];
  for (let i = 2; i <= num; i++) {
    if (checkPrimeNumbers(i)) {
      if (!finalArr.includes(i)) {
        finalArr.push(i);
      }
    }
  }
  return finalArr;
}
// Test
let primeNumbers = getAllPrimeNumbers(100); // [2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47, 53, 59, 61, 67, 71, 73, 79, 83, 89, 97]
let primeNumbers = getAllPrimeNumbers(200); // let primeNumbers = getAllPrimeNumbers(100); // [2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47, 53, 59, 61, 67, 71, 73, 79, 83, 89, 97]
```

5. Given a phrase, reverse the order of the characters of each word.

Example:

"I love JavaScript!" will become "I evol !tpircSavaJ"

```js
function reverseWords(str) {
  return str
    .split(" ")
    .map((elm) => elm.split("").reverse().join(""))
    .join(" ");
}
// Test
reverseWords("I love JavaScript!"); // "I evol !tpircSavaJ"
reverseWords("React is best frontend library!"); // "tcaeR si tseb dnetnorf !yrarbil"
```
