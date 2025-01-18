# JS_notes
### JS arrays

An array is a spoecial type of object used to store multiple values in a single variable.
They are dynamic meaning they can grow and shrink in size.

creating an array- 
let array = [1,2,3,4]

accessing the element
console.log(array[0]);

modifying the element
array[1]=5;

#### Properties of array

1. length - returns number of elements in the array

```javascript
let array = [1,2,3,4];
console.log(array.length);
```

2. push - adds one or more elements to the end of the array and returns new length of the array

```javascript
let array = [1,2,3];
array.push(4);
console.log(array) // [1,2,3,4]
```

3. pop - removes the last element from the array and returns that element 

```javascript
let array = [1,2,3];
let lastElement = array.pop();
console.log(array) // [1,2]
console.log(lastElement) // 3
```

4. shift - removes the first element from the array and returns that element

```javascript
let array = [1,2,3];
let firstElement = array.shift();
console.log(array) //[2,3]
console.log(firstElement) //1
```

5. unshift - adds one or more elements to the beginning of an array and returns the new length of the array

```javascript
let array = [1,2,3];
array.unshift(0);
console.log(array) //[0,1,2,3]
```

6. splice - used to add and remove the elements from the array

```javascript
const fruits = ["banana", "orange", "apple", "mango"];
fruits.splice(2,0,"lemon", "kiwi");
console.log(fruits) //["banana", "orange","lemon", "kiwi", "apple", "mango"]
```

first param 2 defines position where the new element should be added
second param 0 defines how many elements should be removed
rest params (lemon, kiwi) defines the new elements to be added

splice returns the removed elements


7. slice - used to slice out a piece of array

```javascript
const fruits = ["banana", "orange", "apple", "mango"];
const citrus = fruits.slice(1);
console.log(citrus) //["orange"]
console.log(fruits) // ["banana", "orange", "apple", "mango"]

const fav = fruits.slice(2,3);
console.log(fav)// ["apple", "mango"]
```

8. toString - converts an array to a comma separated string 

```javascript
const fruits = ["banana", "orange", "apple", "mango"];
console.log(fruits.toString()); //Banana,Orange,Apple,Mango
```

9. join - used to join all array elements in a single string

```javascript
const fruits = ["Banana", "Orange", "Apple", "Mango"];
document.getElementById("demo").innerHTML = fruits.join(" * ");

result - Banana * Orange * Apple * Mango
```

10. concat - used to join two arrays

```javascript
const myGirls = ["Cecilie", "Lone"];
const myBoys = ["Emil", "Tobias", "Linus"];

const myChildren = myGirls.concat(myBoys); //["Cecilie", "Lone", "Emil", "Tobias", "Linus"];
```

11. flat - create a new array with sub array elements concatenated to a specific depth
``` javascript
const nestedArray = [1, [2, 3], 4, [5, [6]]];
const flattenedArray = nestedArray.flat(); // Flattens one level by default
console.log(flattenedArray); // Output: [1, 2, 3, 4, 5, [6]]

const deeperFlattenedArray = nestedArray.flat(2); // Flattens two levels
console.log(deeperFlattenedArray); // Output: [1, 2, 3, 4, 5, 6]
```

12. reduce - applies a function against an accumulator and each element in an array to reduce it to a single value.

```javascript
const numbers = [1, 2, 3, 4];
const sum = numbers.reduce((acc, num) => acc + num, 0); // Initial value (0) for accumulator
console.log(sum); // Output: 10
```

to flatten the array with use of .flat() function we can do -
```js
const flattenedArray = nestedArray.reduce((acc, val) => acc.concat(val), []);
```

13. indexOf - searches an event for element value and retruns its position, if the itemn is not found then return -1 and if more than 1 then return first occurence
```js
const fruits = ["Apple", "Orange", "Apple", "Mango"];
let position = fruits.indexOf("Apple")+1; //1
```

14. lastIndexOf - get the position of last occurence of the specified element

15. includes - check if the element is present in the array

```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];

fruits.includes("Mango"); // is true
```

16. find - returns the value of the first array element that passes a test function

```js
const numbers = [4, 9, 16, 25, 29];
let first = numbers.find(myFunction);

function myFunction(value, index, array) {
  return value > 18;
}
```

17. forEach - calls a function once for each array element

```js
const numbers = [45, 4, 9, 16, 25];
let txt = "";
numbers.forEach(myFunction);

function myFunction(value, index, array) {
  txt += value + "<br>";
}
```

18. map - creates a new array by performing a function on each array element. this method does not execute or array element without values, it does not change the original array

```js
const numbers1 = [45, 4, 9, 16, 25];
const numbers2 = numbers1.map(myFunction);

function myFunction(value, index, array) {
  return value * 2;
}
```

19. filter - creates a new array with array elements that pass a test

```js
const numbers = [45, 4, 9, 16, 25];
const over18 = numbers.filter(myFunction);

function myFunction(value, index, array) {
  return value > 18;
}
```

#### how to check if the datatype of the object is array
use the function 
Array.isArray(fruits);

#### Spread operator

Spread operator is represented by (...) used for working with arrays and objects

1. Copying array - this is creating shallow copy, first level would not be shallow but from second level it is a shallow copy

```js
let array1 = [1, 2, 3];
let array2 = [...array1];

console.log(array2); // Output: [1, 2, 3]
```

2. Combining array

```js
let array1 = [1, 2];
let array2 = [3, 4];
let combinedArray = [...array1, ...array2];

console.log(combinedArray); // Output: [1, 2, 3, 4]
```

3. Adding elements

```js
let array = [1, 2, 3];
let newArray = [0, ...array, 4, 5];

console.log(newArray); // Output: [0, 1, 2, 3, 4, 5]
```

4. Copying object - creates shallow copy

```js
let obj1 = { a: 1, b: 2 };
let obj2 = { ...obj1 };

console.log(obj2); // Output: { a: 1, b: 2 }
```

5. Merging objects

```js
let obj1 = { a: 1, b: 2 };
let obj2 = { c: 3, d: 4 };
let combinedObj = { ...obj1, ...obj2 };

console.log(combinedObj); // Output: { a: 1, b: 2, c: 3, d: 4 }
```

6. Overriding properties

```js
let obj1 = { a: 1, b: 2 };
let obj2 = { b: 3, c: 4 };
let combinedObj = { ...obj1, ...obj2 };

console.log(combinedObj); // Output: { a: 1, b: 3, c: 4 }
```

### Questions on array

#### Given an array of numbers, write a function to find the sum of all elements.

```js
const arr = [1,2,2,3];

function sumArr(arr){
  return arr.reduce((acc, num)=>acc+num, 0);
}

console.log(sumArr(arr));

```

#### Write a function to find the maximum or minimum element in an array.

```js
const arr = [3,2,2,3];

function minArr(arr){
  arr.sort((a,b)=>a-b);
  return arr[0]
}

console.log(minArr(arr));
```

#### Given an array and a target element, write a function to check if the target element exists in the array.

```js
const arr = [3,2,2,3];

function checkArr(arr, target){
  return arr.indexOf(target);
}

console.log(checkArr(arr,2));
```

#### Given an array of numbers and a target sum, find two numbers in the array that add up to the target sum. Return their indices or the numbers themselves

```js
const arr = [3,2,2,3];

function checkArr(arr, target){
  var start = 0;
  var end = arr.length -1;
  arr.sort((a,b)=>a-b);
  while(start<=end){
    let sum = arr[start]+arr[end];
    if(sum>target){
      end-=1;
    }
    else if(sum<target){
      start+=1;
    }
    else{
      return [arr[start], arr[end]]
    }
  }
}

console.log(checkArr(arr,4));

```

#### Write a function to reverse the order of elements in an array (in-place or by creating a new array).

```js
const arr = [3,2,2,4];

function reverseArr(arr){
  arr.reverse()
  return arr;
}

console.log(reverseArr(arr));
```

#### Given an array that may contain duplicates, write a function to remove duplicates and return a new array with unique elements.

```js
const arr = [3,2,2,4];

function removeDupArr(arr){
  return arr.reduce((acc, num)=>{
    if(!acc.includes(num)){
      acc.push(num);
    }
    return acc
  }, [])
}

console.log(removeDupArr(arr));

```

#### Write a function that takes an array of numbers and moves all zeros to the end of the array while maintaining the relative order of non-zero elements. (Do this in-place if possible)

```js
const arr = [0,2,0,4];

function removeDupArr(arr){
  var zeroIndex = 0;
  for(let i=0;i<arr.length;i++){
    if(arr[i]!=0){
      let temp = arr[i];
      arr[i] = arr[zeroIndex];
      arr[zeroIndex] = temp;
      zeroIndex+=1;
    }
  }
  return arr;
}

console.log(removeDupArr(arr));
```


#### Given two arrays, write a function to find the elements that are present in both arrays (the intersection).

```js
const arr = [0,2,0,4];
const arr2 = [0,3,0,5];

function intersectArr(arr1, arr2){
  let uniquiSet = new Set([...arr1]);
  let intersect = arr2.filter(num=>uniquiSet.has(num));
  return intersect;
}

console.log(intersectArr(arr, arr2));
```


