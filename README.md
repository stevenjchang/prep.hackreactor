# Hack Reactor Prep - Module 1: Exercises [with Answers]

this prep course is available for free at [prep.hackreactor.com](http://prep.hackreactor.com/).


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
---


## #6 - getElementsLessThan100AtProperty

> Instructions from your teacher:
> Write a function called "getElementsLessThan100AtProperty".
>
> Given an object and a key, "getElementsLessThan100AtProperty" returns an array containing all the elements of the array located at the given key that are less than 100.
>
> Notes:
> * If the array is empty, it should return an empty array.
> * If the array contains no elements less than 100, it should return an empty array.
> * If the property at the given key is not an array, it should return an empty array.
> * If there is no property at the key, it should return an empty array.
>
> ```javascript
> var obj = {
  > key: [1000, 20, 50, 500]
> };
> var output = getElementsLessThan100AtProperty(obj, 'key');
> console.log(output); // --> [20, 50]
>
> Starter Code :
> function getElementsLessThan100AtProperty(obj, key) {
  > // your code here
> }
> ```

### Answer:
//objective: iterate through array inside of object, directly

> TIPS:
> - look up Array.isArray(), which checks the typeof of an Array (which is a Javascript Object)

```javascript

function getElementsLessThan100AtProperty(obj, key) {
  var newArr = [];
  var arrayInsideObject = obj[key];

  //if array is empty, or if input not an array, or if no property at key, return newArr immediately
  if (obj === undefined || arrayInsideObject === undefined || !(Array.isArray(arrayInsideObject)) ){
    return newArr;
  }

  //iterate through array at "key" inside object
  arrayInsideObject.forEach(function(elem){
    if (elem < 100){
      newArr.push(elem);
    }
  });
  return newArr;  
}

```
---


## #7 - countAllCharacters

> Instructions from your teacher:
> Write a function called "countAllCharacters".
>
> Given a string, "countAllCharacters" returns an object where each key is a character in the given string. The value of each key should be how many times each character appeared in the given string.
>
> Notes:
> * If given an empty string, countAllCharacters should return an empty object.
>
> ```javascript
> var output = countAllCharacters('banana');
> console.log(output); // --> {b: 1, a: 3, n: 2}
>
> Starter Code :
> function countAllCharacters(str) {
  > // your code here
> }
> ```

### Answer:

```javascript

function countAllCharacters(str) {
  //initialize empty new object
  var newObj = {};

  //iterate through each char of string
  for (i = 0; i < str.length; i++){
    var char = str[i];
    //if char exist in new object
    if (newObj[char]){
      //add 1
      newObj[char] += 1;
    } else {
      //create key:value pair, set value to 1
      newObj[char] = 1;
    }
  }
  return newObj;
}

```
---


## #8 - getElementsGreaterThan10AtProperty

> Instructions from your teacher:
> Write a function called "getElementsGreaterThan10AtProperty".
>
> Given an object and a key, "getElementsGreaterThan10AtProperty" returns an array containing the elements within the array, located at the given key, that are greater than 10.
>
> Notes:
> * If the array is empty, it should return an empty array.
> * If the array contains no elements greater than 10, it should return an empty array.
> * If the property at the given key is not an array, it should return an empty array.
> * If there is no property at the key, it should return an empty array.
>
> ```javascript
> var obj = {
  > key: [1, 20, 30]
> };
> var output = getElementsGreaterThan10AtProperty(obj, 'key');
> console.log(output); // --> [20, 30]
>
> Starter Code :
> function getElementsGreaterThan10AtProperty(obj, key) {
  > // your code here
> }
> ```

### Answer:

> TIPS:
> * Syntax of .forEach()
  >> array.forEach(function(currentValue, index, arr), thisValue)

```javascript

function getElementsGreaterThan10AtProperty(obj, key) {
  //initialize empty new array
  var newArr = [];

  //if property at given key is not an array, or if there is no property, immediately return new array
  if (!(Array.isArray(obj[key])) || obj[key] === undefined) {
    return newArr;
  }

  //create variable arrayInsideObject
  var arrayInsideObject = obj[key];

  //iterate through "key" parameter
  arrayInsideObject.forEach(function(value, index){
    //if value greater than 10 => add to empty array
    if (value > 10){
      newArr.push(value);
    } else {
      //do nothing
    }
  });
  return newArr;
}

```

## #9 - getAverageOfElementsAtProperty

> Write a function called "getAverageOfElementsAtProperty".
>
> Given an object and a key, "getAverageOfElementsAtProperty" returns the average of all the elements in the array located at the given key.
>
> Notes:
> * If the array at the given key is empty, it should return 0.
> * If the property at the given key is not an array, it should return 0.
> * If there is no property at the given key, it should return 0.
>
> ```javascript
> var obj = {
  > key: [1, 2, 3]
> };
> var output = getAverageOfElementsAtProperty(obj, 'key');
> console.log(output); // --> 2
>
> Starter Code :
> function getAverageOfElementsAtProperty(obj, key) {
  > // your code here
> }
> ```

### Answer:

```javascript

function getAverageOfElementsAtProperty(obj, key) {
  //initiate sumOfElements to 0
  var total = 0;
  var arrayInsideObject = obj[key];
  //if array is empty, or property is not array, or no property at key, immediately return 0
  //NOTE: test did not pass unless I put === undefined first
  if (arrayInsideObject === undefined || arrayInsideObject.length < 1 || !(Array.isArray(arrayInsideObject)) ) {
    return total;
  }

  //iterate through array
  arrayInsideObject.forEach(function(value){
    // add number at each index to the total
    total += value;
  });
  //return the total divided by number of index in array
  return total / arrayInsideObject.length;
}


```
---

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
---


## #11 - getEvenLengthWordsAtProperty

> Write a function called "getEvenLengthWordsAtProperty".
>
> Given an object and a key, "getEvenLengthWordsAtProperty" returns an array containing all the even length word elements of the array located at the given key.
>
> Notes:
> * If the array is empty, it should return an empty array.
> * If it contains no even length elements, it should return an empty array.
> * If the property at the given key is not an array, it should return an empty array.
> * If there is no property at the key, it should return an empty array.
>
> ```javascript
> var obj = {
  > key: ['a', 'long', 'game']
> };
> var output = getEvenLengthWordsAtProperty(obj, 'key');
> console.log(output); // --> ['long', 'game']
>
> Starter Code :
> function getEvenLengthWordsAtProperty(obj, key) {
  > // your code here
> }
> ```

### Answers:

```javascript
function getEvenLengthWordsAtProperty(obj, key) {
  //initialize empty new array
  var newArr = [];
  //set array inside given key to a variable
  var arrayInsideObject = obj[key];

  //if input is an empty array, or no even length elements, or property at given key is not an array, or their is no property at key, it should return an empty array
  if (arrayInsideObject === undefined || !(Array.isArray(arrayInsideObject)) || arrayInsideObject.length < 1){
    return newArr;
  }
  //iterate through array
  arrayInsideObject.forEach(function(value, index){
    //if element length at index is even
    if (value.length % 2 === 0){
      //add to new array
      newArr.push(value);
    } else {
      //do nothing
    }
  });
  return newArr;  
}
```
---


## #12 - getSquaredElementsAtProperty

> Write a function called "getSquaredElementsAtProperty".
>
> Given an object and a key, "getSquaredElementsAtProperty" returns an array containing all the squared elements of the array located at the given key.
>
> Notes:
> * If the array is empty, it should return an empty array.
> * If the property at the given key is not an array, it should return an empty array.
> * If there is no property at the key, it should return an empty array.
>
> ```javascript
> var obj = {
  > key: [2, 1, 5]
> };
> var output = getSquaredElementsAtProperty(obj, 'key');
> console.log(output); // --> [4, 1, 25]
>
> Starter Code :
> function getSquaredElementsAtProperty(obj, key) {
  > // your code here
> }
> ```

### Answer:

```javascript
function getSquaredElementsAtProperty(obj, key) {
  //initialize empty new array
  var newArr = [];
  //set array inside given key to a variable
  var arrayInsideObject = obj[key];
  //if array is empty, or property at given key not an array, or no property at key
  if (arrayInsideObject === undefined || !(Array.isArray(arrayInsideObject)) || arrayInsideObject.length < 1){
    return newArr;
  }

  //iterate through array inside object at given key
  arrayInsideObject.forEach(function(value, index){
    newArr.push(value * value);
  })
  return newArr;
}
```
---


## #13 - getOddElementsAtProperty

> Write a function called "getOddElementsAtProperty".
>
> Given an object and a key, "getOddElementsAtProperty" returns an array containing all the odd elements of the array located at the given key.
>
> Notes:
> * If the array is empty, it should return an empty array.
> * If it contains no odd elements, it should return an empty array.
> * If the property at the given key is not an array, it should return an empty array.
> * If there is no property at the key, it should return an empty array.
>
> ```javascript
> var obj = {
  > key: [1, 2, 3, 4, 5]
> };
> var output = getOddElementsAtProperty(obj, 'key');
> console.log(output); // --> [1, 3, 5]
>
> Starter Code :
> function getOddElementsAtProperty(obj, key) {
  > // your code here
> }
> ```

### Answer:

```javascript
function getOddElementsAtProperty(obj, key) {
  //initialize empty new array
  var newArr = [];
  //set array inside given key to a variable
  var arrayInsideObject = obj[key];
  //if array is empty, or property at given key not an array, or no property at key
  if (arrayInsideObject === undefined || !(Array.isArray(arrayInsideObject)) || arrayInsideObject.length < 1){
    return newArr;  
  }
  //iterate through array
  arrayInsideObject.forEach(function(value, index){
    //if element at index is odd
    if (value % 2 !== 0){
      //add to new array
      newArr.push(value);
    } else {
      //do nothing
    }
  });
  return newArr;  
}
```


## #14 - getEvenElementsAtProperty

> Write a function called "getEvenElementsAtProperty".
>
> Given an object and a key, "getEvenElementsAtProperty" returns an array containing all the even elements of the array located at the given key.
>
> Notes:
> * If the array is empty, it should return an empty array.
> * If the array contains no even elements, it should return an empty array.
> * If the property at the given key is not an array, it should return an empty array.
> * If there is no property at the given key, it should return an empty array.
>
> ```javascript
> var obj = {
  > key: [1000, 11, 50, 17]
> };
> var output = getEvenElementsAtProperty(obj, 'key');
> console.log(output); // --> [1000, 50]
>
> Starter Code :
> function getEvenElementsAtProperty(obj, key) {
  > // your code here
> }
> ```

### Answer:

```javascript
function getEvenElementsAtProperty(obj, key) {
  //initialize empty new array
  var newArr = [];
  //set array inside given key to a variable
  var arrayInsideObject = obj[key];
  //if array is empty, or property at given key not an array, or no property at key
  if (arrayInsideObject === undefined || !(Array.isArray(arrayInsideObject)) || arrayInsideObject.length < 1){
    return newArr;  
  }
  //iterate through array
  arrayInsideObject.forEach(function(value, index){
    //if element at index is even
    if (value % 2 === 0){
      //add to new array
      newArr.push(value);
    } else {
      //do nothing
    }
  });
  return newArr;  
}
```

## #15 - getSmallestElementAtProperty

> Write a function called "getSmallestElementAtProperty".
>
> Given an object and a key, "getSmallestElementAtProperty" returns the smallest element in the array located at the given key.
>
> Notes:
> * If the array is empty, it should return undefined.
> * If the property at the given key is not an array, it should return undefined.
> * If there is no property at the key, it should return undefined.
>
> ```javascript
> var obj = {
  > key: [2, 1, 5]
> };
> var output = getSmallestElementAtProperty(obj, 'key');
> console.log(output); // --> 1
>
> Starter Code :
> function getSmallestElementAtProperty(obj, key) {
  > // your code here
> }
> ```

### Answer:

> TIPS: two ways to find the min value
> * `Math.min.apply(Math, array)`
  >>  (because Math.min() does not work on arrays)
  >>  e.g. `Math.min.apply(null, arrayInsideObject)`
> * `Math.min( ...arr )`  //this only works in ES6
  >>  e.g. `Math.min(...arrayInsideObject)`

```javascript
function getSmallestElementAtProperty(obj, key) {
  //set array inside given key to a variable
  var arrayInsideObject = obj[key];

  //if array is empty, or property at given key not an array, or no property at key
  if (arrayInsideObject === undefined || !(Array.isArray(arrayInsideObject)) || arrayInsideObject.length < 1){
    return undefined;  
  }

  //return the smallest element at property (array at given key)
  //method 1:
  return Math.min.apply(null, arrayInsideObject);
  //or method 2: (only in ES6)
  // return Math.min(...arrayInsideObject);
}
```
---


## #16 - getLargestElementAtProperty

> Write a function called "getLargestElementAtProperty".
>
> Given an object and a key, "getLargestElementAtProperty" returns the largest element in the array located at the given key.
>
> Notes:
> * If the array is empty, it should return undefined.
> * If the property at the given key is not an array, it should return undefined.
> * If there is no property at the key, it should return undefined.
>
> ```javascript
> var obj = {
  > key: [1, 2, 4]
> };
> var output = getLargestElementAtProperty(obj, 'key');
> console.log(output); // --> 4
>
> Starter Code :
> function getLargestElementAtProperty(obj, key) {
  > // your code here
> }
> ```

### Answer:

> TIPS: two ways to find the max value
> * `Math.max.apply(Math, array)`
  >>  (because Math.max() does not work on arrays)
  >>  e.g. `Math.max.apply(null, arrayInsideObject)`
> * `Math.max( ...arr )`  //this only works in ES6
  >>  e.g. `Math.max(...arrayInsideObject)`

```javascript
function getLargestElementAtProperty(obj, key) {
  //set array inside given key to a variable
  var arrayInsideObject = obj[key];

  //if array is empty, or property at given key not an array, or no property at key
  if (arrayInsideObject === undefined || !(Array.isArray(arrayInsideObject)) || arrayInsideObject.length < 1){
    return undefined;  
  }

  //return the smallest element at property (array at given key)
  //method 1:
  return Math.max.apply(null, arrayInsideObject);
  //or method 2: (only in ES6)
  // return Math.max(...arrayInsideObject);
}
```
---


## #17 - getProductOfAllElementsAtProperty

> Write a function called "getProductOfAllElementsAtProperty".
>
> Given an object and a key, "getProductOfAllElementsAtProperty" returns the product of all the elements in the array located at the given key.
>
> Notes:
> * If the array is empty, it should return 0.
> * If the property at the given key is not an array, it should return 0.
> * If there is no property at the given key, it should return 0.
>
> ```javascript
> var obj = {
  > key: [1, 2, 3, 4]
> };
> var output = getProductOfAllElementsAtProperty(obj, 'key');
> console.log(output); // --> 24
>
> Starter Code :
> function getProductOfAllElementsAtProperty(obj, key) {
  > // your code here
> }
> ```

### Answer:

#### Method 1
```javascript
function getProductOfAllElementsAtProperty(obj, key) {
  //initialize productOfAllElements to 1;
  var productOfAllElements = 1;
  //set array at given key to variable
  var arrayInsideObject = obj[key];

  //if array is empty, or property at given key is not an array, or no property at given key, immediately return 0
  if (arrayInsideObject === undefined || arrayInsideObject.length < 1 || !(Array.isArray(arrayInsideObject)) ){
    return 0;
  }

  arrayInsideObject.forEach(function(value, index){
    productOfAllElements = productOfAllElements * value;
  })
  return productOfAllElements;
}
```

#### Method 2: using .reduce()

> TIPS:
> * reduce syntax
>> array.reduce(function(accumulator, currentValue, currentIndex, arr), initialValue)

```javascript
function getProductOfAllElementsAtProperty(obj, key) {
  //initialize productOfAllElements to 0;
  var productOfAllElements = 0;
  //set array at given key to variable
  var arrayInsideObject = obj[key];

  //if array is empty, or property at given key is not an array, or no property at given key, immediately return productOfAllElements
  if (arrayInsideObject === undefined || arrayInsideObject.length < 1 || !(Array.isArray(arrayInsideObject)) ){
    return productOfAllElements;
  }

  //set productOfAllElements to
  //the iterated result of multiplying each value at given key, with an initial value of 1
  productOfAllElements = arrayInsideObject.reduce(function(acc, value, index){
    return acc * value;
  }, 1);
  return productOfAllElements;
}
```
---


## #18 - getSumOfAllElementsAtProperty

> Write a function called "getSumOfAllElementsAtProperty".
>
> Given an object and a key, "getSumOfAllElementsAtProperty" returns the sum of all the elements in the array located at the given key.
>
> Notes:
> * If the array is empty, it should return 0.
> * If the property at the given key is not an array, it should return 0.
> * If there is no property at the key, it should return 0.
>
> ```javascript
> var obj = {
  > key: [4, 1, 8]
> };
> var output = getSumOfAllElementsAtProperty(obj, 'key');
> console.log(output); // --> 13
>
> Starter Code :
> function getSumOfAllElementsAtProperty(obj, key) {
  > // your code here
> }
> ```

### Answer:

```javascript
function getSumOfAllElementsAtProperty(obj, key) {
  //initialize sumOfAllElements to 0;
  var sumOfAllElements = 0;
  //set array at given key to variable
  var arrayInsideObject = obj[key];

  //if array is empty, or property at given key is not an array, or no property at given key, immediately return sumOfAllElements
  if (arrayInsideObject === undefined || arrayInsideObject.length < 1 || !(Array.isArray(arrayInsideObject)) ){
    return sumOfAllElements;
  }

  //iterate through array at given key, add value at each index to sumOfAllElements
  arrayInsideObject.forEach(function(value, index){
    sumOfAllElements += value;
  });
  return sumOfAllElements;
}
```
