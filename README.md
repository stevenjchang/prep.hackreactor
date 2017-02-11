Hack Reactor Prep
Algorithm Questions

                            Module 1: Exercises
                      ------------------------------

****************************************
01 - countWords
****************************************

Instructions from your teacher:
Write a function called "countWords".

Given a string, "countWords" returns an object where each key is a word in the given string, with its value being how many times that word appeared in the given  string.

Notes:
* If given an empty string, it should return an empty object.

var output = countWords('ask a bunch get a bunch');
console.log(output); // --> {ask: 1, a: 2, bunch: 2, get: 1}

Starter Code :
function countWords(str) {
  // your code here
}

-------------------------------------------------------------------------------
answer
-------------------------------------------------------------------------------

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

****************************************
02 - isPersonOldEnoughToDrinkAndDrive
****************************************

Instructions from your teacher:
Write a function called "isPersonOldEnoughToDrinkAndDrive".

Given a "person" object, that contains an "age" property, "isPersonOldEnoughToDrinkAndDrive" returns whether the given person is old enough to legally drink and drive in the United States.

Notes:
* The legal drinking age in the United States is 21.
* The legal driving age in the United States is 16.
* It is always illegal to drink and drive in the United States.

var obj = {
  age: 45
};
var output = isPersonOldEnoughToDrinkAndDrive(obj);
console.log(output); // --> false

Starter Code :
function isPersonOldEnoughToDrinkAndDrive(person) {
  // your code here
}

-------------------------------------------------------------------------------
answer
-------------------------------------------------------------------------------

function isPersonOldEnoughToDrinkAndDrive(person) {
  return false;
}




****************************************
****************************************

-------------------------------------------------------------------------------
-------------------------------------------------------------------------------
