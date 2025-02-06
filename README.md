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



## JS Promise, Async/Await 

Imagine you are a top singer, and fans ask day and night for your upcoming songs
So you give fans a list they can fill their email in it and once the song is released you can mail the subscribed parties instantly and if something goes wrong then you can inform that you won't be publishing song

You can apply this for the concept of promises in js
1. A "producing code" that does something and takes time is like a singer for producing songs.
2. A "consuming code" that wants the songs or the produced code just like fans who want the songs.
3. A promise is just the connection link between producing code and consuming code like the email list for songs

```javascript
let promise = new Promise(function(resolve, reject) {
  // executor (the producing code, "singer")
});
```

the executor is the producing code which produces the result. Like a singer
resolve and reject are callback functions
- resolve(value) - if the job is finished successfully, with result value.
- reject(error) - if an error occurred, error is an object.

The promise object retruned by the new Promise constructor has these internal properties:
- state : intitially is is "pending", then changes to "fulfilled" when resolve is called or "rejected" when reject is called.
- result : initially undefined, then changes to value when resolve(value) is called or error when reject(error) is called.

```javascript
let promise = new Promise(function(resolve, reject) {
  // the function is executed automatically when the promise is constructed

  // after 1 second signal that the job is done with the result "done"
  setTimeout(() => resolve("done"), 1000);
});
```

There can be only a single result or an error
The executor should call only one resolve or one reject. Any state change is final.

All further calls of resolve and reject are ignored:

```javascript
let promise = new Promise(function(resolve, reject) {
  resolve("done");

  reject(new Error("…")); // ignored
  setTimeout(() => resolve("…")); // ignored
});
```

The idea is that a job done by the executor may have only one result or an error.

Also, resolve/reject expect only one argument (or none) and will ignore additional arguments.

Consumer - the consuming function will recieve the result or error. Consuming functions can be registered using methods .then and .catch.

- then : 

```javascript
promise.then(
  function(result) { /* handle a successful result */ },
  function(error) { /* handle an error */ }
);
```

the first argument of .then is a function that runs when the promise is resolved and recieves the result.
the second argument of .then is a function that runs when the promise is rejected and recieves the error.

```javascript
let promise = new Promise(function(resolve, reject) {
  setTimeout(() => resolve("done!"), 1000);
});

// resolve runs the first function in .then
promise.then(
  result => alert(result), // shows "done!" after 1 second
  error => alert(error) // doesn't run
);
```

The first function was executed.

And in the case of a rejection, the second one:

```javascript
let promise = new Promise(function(resolve, reject) {
  setTimeout(() => reject(new Error("Whoops!")), 1000);
});

// reject runs the second function in .then
promise.then(
  result => alert(result), // doesn't run
  error => alert(error) // shows "Error: Whoops!" after 1 second
);
```


### Using promise to fetch the data

```javascript
function fetchWeather(city) {
  const apiKey = 'your_api_key_here';
  const apiUrl = `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${apiKey}`;

  // Fetch weather data using a promise
  return fetch(apiUrl)
    .then((response) => {
      if (!response.ok) {
        throw new Error('City not found');
      }
      return response.json(); // Parse the JSON from the response
    })
    .then((data) => {
      // Use the fetched data
      console.log(`Weather in ${city}: ${data.weather[0].description}`);
      return data;
    })
    .catch((error) => {
      // Handle any errors
      console.error(`Error fetching weather data: ${error.message}`);
    });
}

// Example usage
fetchWeather('New York')
  .then((weatherData) => {
    if (weatherData) {
      console.log(`Temperature: ${weatherData.main.temp}K`);
    }
  });
```

Output :
```plaintext
Weather in New York: clear sky
Temperature: 280.32K
```

fetch is built in function in most browsers for making the API calls it returns a Promise 
Due to chaining of promises first the fetchWeather function promise is resolved first inside the fetchWeather function first .then callback function we are converting the respose in the json then feeding it to the next .then callback fucntion which logs the message and returns the data then it returns the response to the calling function and then that function is resolved

call fetchWeather => fetch() => convert to json => log the message and return the data => .then callback of the calling function


### Chaining of promises

```javascript
// Create the first promise
const firstPromise = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve('First promise resolved');
    }, 1000);
});

// Chain the second promise
const secondPromise = firstPromise.then((message) => {
    console.log(message); // Log the message from the first promise
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve('Second promise resolved');
        }, 1000);
    });
});

// Chain the third promise
secondPromise.then((message) => {
    console.log(message); // Log the message from the second promise
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve('Third promise resolved');
        }, 1000);
    });
}).then((message) => {
    console.log(message); // Log the message from the third promise
});
```

Output - 
```
First promise resolved
Second promise resolved
Third promise resolved
```


### Handling of errors

```javascript
// Create a promise that simulates an error
const errorPromise = new Promise((resolve, reject) => {
    setTimeout(() => {
        reject('An error occurred');
    }, 1000);
});

// Handle the error using .catch() method
errorPromise
    .then((message) => {
        console.log(message); // This won't be executed
    })
    .catch((error) => {
        console.error('Error caught:', error); // Log the error message
    });
    
// Another way to handle errors using .then() second parameter
errorPromise
    .then((message) => {
        console.log(message); // This won't be executed
    }, (error) => {
        console.error('Error caught using then second parameter:', error); // Log the error message
    });
```

### Promise.all

Used for running multiple promises in parallel, useful when we want to wait for several asynchronous operations to complete

```javascript
// Create three promises that resolve after different times
const promise1 = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve('First promise resolved after 1 second');
    }, 1000);
});

const promise2 = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve('Second promise resolved after 2 seconds');
    }, 2000);
});

const promise3 = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve('Third promise resolved after 3 seconds');
    }, 3000);
});

// Use Promise.all to run the promises in parallel
Promise.all([promise1, promise2, promise3])
    .then((messages) => {
        console.log('All promises resolved:');
        messages.forEach((message, index) => {
            console.log(`Promise ${index + 1}: ${message}`);
        });
    })
    .catch((error) => {
        console.error('One of the promises rejected:', error);
    });
```

### Async await 

async await provides more readable way for handling promises instead of using .then() and .catch(). With async/await, you can write asynchronous code that looks similar to synchronous code and it uses promises under the hood.

Async keyword is used to declare an asynchronous function.
Await keyword is used to wait for a promise to be resolved before continuing with execution of the function

```js
// Function that returns a promise that resolves after a given time
function delayPromise(message, delay) {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve(message);
        }, delay);
    });
}

// Async function to handle promises using async/await
async function executeAsync() {
    try {
        const result1 = await delayPromise('First promise resolved', 1000);
        console.log(result1);

        const result2 = await delayPromise('Second promise resolved', 2000);
        console.log(result2);

        const result3 = await delayPromise('Third promise resolved', 3000);
        console.log(result3);
    } catch (error) {
        console.error('Error:', error);
    }
}

// Run the async function
executeAsync();
```

### Questions on promises

1. 
```js
console.log('start');

const promise1 = new Promise((resolve, reject)=>{
  console.log(1);
})

console.log('end');
```

output - 
start
1
end

2. 
```js
console.log('start');

const promise1 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("hello");
  }, 1000);
});

console.log('end');
```

output - 
start
end

3. 
```js
console.log('start');

const promise1 = new Promise((resolve, reject) => {
  setTimeout(() => {
    console.log("hello");
  }, 1000);
});

console.log('end');
```

output - 
start
end
hello


4. 
```js
console.log('start');

const promise1 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("hello");
  }, 1000);
});

console.log('end');

promise1.then((value) => {
  console.log(value); // Logs "hello" after 1 second
});
```

output - 
start
end
hello

5. 
```js
console.log('start');

const promise1 = new Promise((resolve, reject) => {
  setTimeout(() => {
    console.log("hello");
    resolve(); 
  }, 1000);
});

promise1.then(() => {
  console.log("Promise resolved!");
});

console.log('end');
```

output -
start
end
hello
Promise resolved

6. 
```js
function performTask(){
  return new Promise(function(resolve, reject){
    reject();
  })
}

let taskPromise = performTask();

taskPromise.then(function(){
  console.log('Success1');
})
.then(function(){
  console.log('Success2');
})
.then(function(){
  console.log('Success3');
})
.catch(function(){
  console.log('Error1');
})
.then(function(){
  console.log('Success4');
})
```
output -
Error1
Success4

7. 
```js
const promise = new Promise((resolve) => {
  resolve(1);
});

promise.then((value) => {
  console.log(value);
  return value + 1;
}).then((value) => {
  console.log(value);
  throw new Error('Something went wrong');
}).catch((error) => {
  console.error(error.message);
});
```
output -
1
2
Something went wrong



### Difference between Promises and async/await

async/await is an extension of promise and uses async/await only internally it basically provides a better more readable way for handling asyncronous functions.

```js
async function executeAsync() {
    try {
        const result1 = await delayPromise('First promise resolved', 1000);
        console.log(result1);
    } catch (error) {
        console.error('Error:', error);
    }
}
```

In the above example console.log(result1) will not execute till the const result1 does not get the value because await is applied on that function

if we have to execute the same with promises only that would be something like

```js

const delayPromise = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('First promise resolved'); 
  }, 1000);
});

function executeAsync() {
    try {
        const result1 = delayPromise().then((response)=>{
          console.log(response)
        });
    } catch (error) {
        console.error('Error:', error);
    }
}
```

So clearly with async/await it is easier to understand flow of the code and implementation of asyncronous functions