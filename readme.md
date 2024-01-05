Source : https://www.freecodecamp.org/news/javascript-one-liners-to-use-in-every-project

# JavaScript is a powerful language that can do a lot with very little code.

In some cases, the amount of code you need to write doesn't exceed more than a single line, which is why they are known as one-liners.

Let's go through 10 essential one liners worth using in virtually every JavaScript project you create.

## 1. How to Capitalize Text
```js
const capitalize = (str) => `${str.charAt(0).toUpperCase()}${str.slice(1)}`;
```
Capitalizing strings is not a built-in feature of JavaScript.

To fix this, we can make a capitalize function which accepts some text and makes the first letter uppercase, then appends the rest of the string.

This one-liner is useful for just about every kind of text you want to capitalize. I use it most frequently with displaying users' names.

```js
const name = "robert";

capitalize(name) // "Robert";
```

## 2. How to Calculate Percent

```js
const calculatePercent = (value, total) => Math.round((value / total) * 100)
```
Calculating a percent is pretty easy and just involves some simple math. It is an essential task if you want to display user progress, for example in incrementing a progress bar.

`calculatePercent` accepts a certain amount, divides it by the total amount, then multiplies it by 100. Finally, we use `Math.round()` to round the result up to the nearest whole number.
```js
const questionsCorrect = 6;
const questionTotal = 11;

calculatePercent(questionsCorrect, questionsTotal); // 55
```

## 3. How to Get a Random Element

```js
const getRandomItem = (items) =>  items[Math.floor(Math.random() * items.length)];
```
Getting a random element and array is really nice when you want to make things unique for your user.

For example, you might want to show your users a congratulations message based on some action. But you probably don't want to show them the same one every time, because that would get repetitive and boring.

`getRandomItem` uses the `Math.random()` function, which returns a decimal between 0 and 1. This is multiplied by the length of the array to select a random index, which can be used to select a random element.

```js
const items = ["Nicely done!", "Good job!", "Good work!", "Correct!"];

getRandomItem(items); // "Good job!"
```

## 4. How to Remove Duplicate Elements

```js
const removeDuplicates = (arr) => [...new Set(arr)];
```

Removing duplicate values in an array is an essential task in JavaScript.

For example, you might be adding one user to another user's friends list, but you don't want that user to be added or displayed twice.

This `removeDuplicates` function leverages the `Set` constructor in JavaScript, which removes any duplicate (primitive) values by default. After that, we use the spread operator `...` to spread its values into a new array.

```js
const friendList = ["Jeff", "Jane", "Jane", "Rob"];

removeDuplicates(friendList); // ['Jeff', 'Jane', 'Rob']`
```

## 5. How to Sort Elements By Certain Property

```js
const sortBy = (arr, key) => arr.sort((a, b) => a[key] > b[key] ? 1 : a[key] < b[key] ? -1 : 0);
```
A common task when displaying data in JavaScript is to sort it based on some property.

This `sortBy` function uses the native sort method, compares the elements in the array based off of the provided key, and sorts the array in ascending order.

Where would this be helpful? If you're fetching data that is supposed to be in a certain position based off of a position key, `sortBy` will make sure that those elements are placed in the proper order.

```js
const lessons = [{ position: 1, name: "Intro" }, { position: 0, name: "Basics" }];

sortBy(lessons, 'position'); 

// {position: 0, name: 'Basics'},
// {position: 1, name: 'Intro'}
```

## 6. How to Check if Arrays/Objects are Equal

```js
const isEqual = (a, b) => JSON.stringify(a) === JSON.stringify(b);
```
It's easy to check for equality with JavaScript primitives, like numbers and strings.

Checking for equality between arrays and objects is a bit harder, however. Fortunately, there's a neat trick you can use with `JSON.stringify` to convert arrays or objects into a JSON string. If all the elements match, `isEqual` will return a value of true.

This is very handy when you expect multiple inputs from a user, for example if they're answering a question and you want to compare it to the correct solution.

```js
isEqual([1, '2'], [1, 2]); // false
isEqual([1, 2], [1, 2]); // true
```

## 7. How to Count Number of Occurrences

```js
const countOccurrences = (arr, value) => arr.reduce((a, v) => (v === value ? a + 1 : a), 0);
```
Another helpful array-based one liner is to count the number of occurrences of an element in an array. It uses the `.reduce()` function. If the value is found in the array, it increments a counter by one.

One useful example might be a poll to determine what most people voted for.

```js
const pollResponses = ["Yes", "Yes", "No"];
const response = "Yes";

countOccurrences(pollResponses, response); // 2
```

## 8. How to Wait for a Certain Amount of Time

```js
const wait = async (milliseconds) => new Promise((resolve) => setTimeout(resolve, milliseconds));
```
In your application, you might want to wait for a certain period of time. For example, if you want to delay an animation or are waiting for an important operation for finish.

You can provide the `wait` function a certain amount of time to wait in milliseconds. Because it uses a promise, you can use the `then` callback or the `await` keyword to make sure it has finished.

```js
wait(2000).then(() => goToSignupPage());
```

## 9. How to Use the Pluck Property from Array of Objects

```js
const pluck = (objs, key) => objs.map((obj) => obj[key]);
```
If you need to extract data from an array of objects and are not interested in getting all the data that is returned, use the `pluck` function.

It takes an array of objects and a property that each of the objects contains. The function maps over this array and returns an array with only the values of the property that we specified.

For example, if we have an array of user data, but we want to convert it just to an array of their names, `pluck` can do this.

```js
const users = [{ name: "Abe", age: 45 }, { name: "Jennifer", age: 27 }];

pluck(users, 'name'); // ['Abe', 'Jennifer']
```


## 10. How to Insert an Element at a Certain Position

```js
const insert = (arr, index, newItem) => [...arr.slice(0, index), newItem, ...arr.slice(index)];
```
If we want to put an element in a precise location in an array, we can use this special `insert` function.

To use it, we just need to pass to `insert` the array we want to transform, the index where we want the element insert, and the element to insert.

This is a great function to use instead of `.splice()` because it does not mutate the original array. It creates a new array with the help of the slice method, by slicing the array into two parts around the specified index and then creates a new one.

```js
const items = [1, 2, 4, 5];

// insert the number 3 at index 2:

insert(items, 2, 3); // [1, 2, 3, 4, 5]
```