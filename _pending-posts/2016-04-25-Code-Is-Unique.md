How can all code be seen as equal.

First, they learn to recognize the letters (the ball or pin). Then they learn to recognize the word (the juggling pattern). However, once this basic juggling “pattern” (the word) has been learned, then the focus can shift to a higher level still (the words become a sentence).

The following is an example of two approaches to solving the same problem.

--------------------------------------------------

function imageFilter(arr) {
  //Polyfill for ends with method
  if (!String.prototype.endsWith) {
    String.prototype.endsWith = function(searchString, position) {
      var subjectString = this.toString();
      if (typeof position !== 'number' || !isFinite(position) || Math.floor(position) !== position || position > subjectString.length) {
        position = subjectString.length;
      }
      position -= searchString.length;
      var lastIndex = subjectString.indexOf(searchString, position);
      return lastIndex !== -1 && lastIndex === position;
    };
  }
  
  //Polyfill for startsWith Method
  if (!String.prototype.startsWith) {
    String.prototype.startsWith = function(searchString, position){
      position = position || 0;
      return this.substr(position, searchString.length) === searchString;
    };
  }


  //create master array
  var masterArray = [];
  
  //loop through each file in the array
  arr.forEach(function (file, index, arr) {
    //if file is an image
    if (file.endsWith(".jpg") || file.endsWith(".JPG") ||
        file.endsWith(".gif") || file.endsWith(".GIF") ||
        file.endsWith(".png") || file.endsWith(".PNG") ||
        file.endsWith(".tiff") || file.endsWith(".TIFF") ||
        file.endsWith(".svg") || file.endsWith(".SVG") ||
        file.endsWith(".bmp") || file.endsWith(".BMP")) {
      //check that file name is valid  
      if (!file.startsWith(".")) {
        //create and initialize tempArray with separated name and extension
        var tempArray = file.split('.');
        //append full filename to beginning of tempArray
        tempArray.unshift(file);
        //append tempArray to master array
        masterArray.push(tempArray);
      } else{
        //append null to master array
        masterArray.push(null);
      }
    } else {
      //append null to master array
      masterArray.push(null);
    }      
  });   
  //return master array
  return masterArray;
}

vs.

function imageFilter(arr) {
  return arr.map(file => file.match(/^(.+)\.(bmp|gif|jpg|png|tiff)$/i))
}

http://www.codewars.com/kata/56562b12044fa538b0000010/solutions/javascript

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
