How can all code be seen as equal.

The following is an example of two approaches to solving the same problem.

---------------------------------------

function unusedDigits(...args){
  return "0123456789".replace(new RegExp('['+args.join('')+']','g'), '')
}
 
-------------------------------------------

Compared to….
 
function unusedDigits(...args){
  args = typeof args[0] === 'object' && args[0].length ? args[0] : args;
  let usedDigits = args.join('').split('').map(Number).sort(),
    allDigits = [0,1,2,3,4,5,6,7,8,9];
  return arrayMinus(allDigits, usedDigits).join('');
}
 
function arrayMinus(arr1, arr2) {
  arr1 = unique(arr1.sort());
  arr2 = unique(arr2.sort());
  let i = 0, j = 0, result = [];
  while (i < arr1.length || j < arr2.length) {
    let item1 = i < arr1.length ? arr1[i] : Infinity;
    let item2 = j < arr2.length ? arr2[j] : Infinity;
    if (item1 < item2) {
      result.push(item1);
      i++;
    } else if (item1 > item2) {
      j++;
    } else {
      i++; j++;
    }
  }
  return result;
}
 
function unique(arr) {
  return arr.reduce(function(memo, v) {
      if (!memo.seen[v]) {
        memo.seen[v] = true;
        memo.result.push(v);
      }
      return memo;
    }, { result: [], seen: {} })
    .result;
}

-------------------------------------------------------------------------

function isMatching(string, str1, str2) {
  // Process the larger string:
  string = removeSpaces(string);
  string = lowerCase(string);
  var stringArray = string.split("");
  stringArray = stringArray.sort();
  
  // Process the two component strings:
  var str1and2 = str1 + str2;
  str1and2 = removeSpaces(str1and2);
  str1and2 = lowerCase(str1and2);
  var str1and2Array = str1and2.split("");
  str1and2Array = str1and2Array.sort();
  
  // Then make the comparison:
  if (arraysEqual(stringArray, str1and2Array)){
    return true;
  }else{
    return false;
  }
}

// Removes spaces from a string:
function removeSpaces(str){
  outputString = "";
  for (var i = 0; i < str.length; i++){
    if (str.slice(i, i+1) != " "){
      outputString += str.slice(i, i+1);
    }
  }
  return outputString;
}

// Converts any upper-case letters to lower-case:
function lowerCase(str){
  upperCase = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
  var outputString = "";
  for (var i = 0; i < str.length; i++){
    if (upperCase.indexOf(str.slice(i, i+1)) != -1){
      outputString += str.slice(i, i+1).toLowerCase();
    }else{
      outputString += str.slice(i, i+1);
    }
  }
  return outputString;
}

// Determines whether arrays contain exactly the same elements in the same order:
function arraysEqual(arr1, arr2){
  var equal = true;
  if (arr1.length != arr2.length){
    equal = false;
  }else{
    for (var i = 0; i < arr1.length; i++){
      if (arr1[i] != arr2[i]){
        equal = false;
      }
    }
  }
  return equal;
}


-------------------------------------------------------------------------

vs..

const isMatching = (string, str1, str2) => (normalize(str1 + str2) === normalize(string));
const normalize = (str) => sort(str.replace(/\s/g, "").toUpperCase());
const sort = (str) => str.split('').sort().join('');

-------------------------------------------------------------------------

http://www.codewars.com/kata/565ce4ab24ef4aee6a000074/solutions/javascript

Description:

isMatching checks if a string can be created by combining and rearranging the letters of two other strings (not case sensitive).

!Spaces will be ignored but special characters and numbers won't match the string and return false.

For example:
isMatching("email box", "b aIl", "Mo x e") return true
but
isMatching("bouh", "0b", "uh") return false

You need to be able to use all the caracters from the two strings so:
isMatching("kata", "kt", "aaa") return false
