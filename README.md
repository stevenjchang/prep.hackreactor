# Hack Reactor Prep - Module 1: Exercises [with Answers]

this prep course is available for free at [prep.hackreactor.com](http://prep.hackreactor.com/).

> to find/skip to a specific question, use the Find function on your browser, but clicking 'cmd-f' (on Mac) and 'ctrl-f' (on Windows).

## #1 - countWords

>Instructions from your teacher:
Write a function called "countWords".

>Given a string, "countWords" returns an object where each key is a word in the given string, with its value being how many times that word appeared in the given  string.

>Notes:
* If given an empty string, it should return an empty object.

> ```javascript
var output = countWords('ask a bunch get a bunch');
console.log(output);
// --> {ask: 1, a: 2, bunch: 2, get: 1}

>Starter Code :
function countWords(str) {
  // your code here
}
```

### Answer:

```javascript
var output = countWords('ask a bunch get a bunch');
console.log(output); // --> {ask: 1, a: 2, bunch: 2, get: 1}

// input will be a string
// output will be an object, with multiple key:value pairings

//pseudocode
  // create empty obj
  // if str.length === 0, return empty object
  // split input str into words
    // for each word, key (at word) will equal += 1
    // return obj

function countWords(str) {
  // create empty obj
  var newObj = {};
  // if str.length === 0, return empty object
  if (str.length === 0) {
    return newObj;
  } else {
    // split input str into words
    str.split(' ').forEach(function(word){
      // for each word, key (at word) will equal += 1// return obj
      if (newObj[word] === undefined) {
        newObj[word] = 1;
      } else {
        newObj[word] += 1;
      }
    });
  return newObj;
  }
}
```
---

## #2 - isPersonOldEnoughToDrinkAndDrive


> Instructions from your teacher:
> Write a function called "isPersonOldEnoughToDrinkAndDrive".
>
> Given a "person" object, that contains an "age" property, "isPersonOldEnoughToDrinkAndDrive" returns whether the given person is old enough to legally drink and drive in the United States.
>
> Notes:
> * The legal drinking age in the United States is 21.
> * The legal driving age in the United States is 16.
> * It is always illegal to drink and drive in the United States.
>
> ```javascript
> var obj = {
  > age: 45
> };
> var output = isPersonOldEnoughToDrinkAndDrive(obj);
> console.log(output); // --> false
>
> Starter Code :
> function isPersonOldEnoughToDrinkAndDrive(person) {
  > // your code here
> }
> ```

### Answer:

```javascript
function isPersonOldEnoughToDrinkAndDrive(person) {
  return false;
}
```
---

## #3 - extend

> Instructions from your teacher:
> Write a function called "extend".
>
> Given two objects, "extend" adds properties from the 2nd object to the 1st object.
>
> Notes:
> * Add any keys that are not in the 1st object.
> * If the 1st object already has a given key, ignore it (do not overwrite the property value).
> * Do not modify the 2nd object at all.
>
> ```javascript
> var obj1 = {
  > a: 1,
  > b: 2
> };
> var obj2 = {
  > b: 4,
  > c: 3
> };
>
> extend(obj1, obj2);
>
> console.log(obj1); // --> {a: 1, b: 2, c: 3}
> console.log(obj2); // --> {b: 4, c: 3}
>
> Starter Code :
> function extend(obj1, obj2) {
  > // your code here
> }
> ```

### Answer:

```javascript
function extend(obj1, obj2) {
  //iterate through obj2's keys
  for (var key in obj2) {
    //at each key, evaulate if obj2 at key exists in obj1
    if (obj1[key] === undefined) { //the keyword "key" on this line refers to obj2
      //if it doesn't exist, set it
      obj1[key] = obj2[key];
    } else {
      //else do nothing
    }
  }
  return obj1;
}
```
---


## #5 - select

> Instructions from your teacher:
> Write a function called "select".
>
> Given an array and an object, "select" returns a new object whose properties are those in the given object AND whose keys are present in the given array.
>
> Notes:
> * If keys are present in the given array, but are not in the given object, it should ignore them.
> * It does not modify the passed in object.
>
> ```javascript
> var arr = ['a', 'c', 'e'];
> var obj = {
  > a: 1,
  > b: 2,
  > c: 3,
  > d: 4
> };
> var output = select(arr, obj);
> console.log(output); // --> { a: 1, c: 3 }
>
>
> Starter Code:
> function select(arr, obj) {
  > // your code here
> }
> ```

### Answer:

#### Two ways to solve, iterating through array or object 

**iterating through ARRAY**

```javascript

function select(arr, obj) {
  //initialize new object
  var newObj = {};
  //iterate through each index of array
  arr.forEach(function(element){
    //if object has a key identical to array index, (if it exists)
    if (obj[element]){
      newObj[element] = obj[element];
    } else {
      //do nothing
    }
  });
  return newObj;
}

```

**iterating through OBJECT**
> TIPS:
> * look up Object.keys(obj).forEach()

```javascript

function select(arr, obj) {
  //initialize new object
  var newObj = {};

  //iterate through each key
  Object.keys(obj).forEach(function(key){
    //if key exists in the array
    if (arr.indexOf(key) !== -1){
      //add to newObj
      newObj[key] = obj[key];
    } else {

    }
  });
  return newObj;
}

```



















## #10 - getOddLengthWordsAtProperty


> Instructions from your teacher:
> Write a function called "getOddLengthWordsAtProperty".
>
> Given an object and a key, "getOddLengthWordsAtProperty" returns an array containing all the odd length word elements of the array located at the given key.

> Notes:
> * If the array is empty, it should return an empty array.
> * If it contains no odd length elements, it should return an empty array.
> * If the property at the given key is not an array, it should return an empty array.
> * If there is no property at the given key, it should return an empty array.
>
> ```
> var obj = {
  > key: ['It', 'has', 'some', 'words']
> };
> var output = getOddLengthWordsAtProperty(obj, 'key');
> console.log(output); // --> ['has', 'words']
>
> Starter Code :
> function getOddLengthWordsAtProperty(obj, key) {
  > // your code here
> }
> ```

### Answer:

> TIPS:
  > - look up Array.isArray(), which checks the typeof of an Array (which is a Javascript Object)

```javascript
function getOddLengthWordsAtProperty(obj, key) {
  //initiate new array
  var newArr = [];

  //use Array.isArray() instead of "typeof" to check if input in an array
  if (obj[key] === undefined || !(Array.isArray(obj[key]))){
    return newArr;
  }

  //iterate array inside obj[key]
  for (var i = 0; i < obj[key].length; i++) {
    var word = obj[key][i];
    var wordLength = word.length;  

    if (wordLength % 2 !== 0) {
      newArr.push(word);
    } else {
      //do nothing
    }
  }
  return newArr;
}
```











****************************************
****************************************

-------------------------------------------------------------------------------
-------------------------------------------------------------------------------
