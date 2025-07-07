20 min a day and you will be goated:
https://www.edclub.com/

## Event Loop and promises

- watch this [video](https://www.youtube.com/watch?v=8aGhZQkoFbQ)
- solve the following questions:

```typescript
const noam = ();
```

	- read the following section: https://javascript.info/async
```typescript
const noam2 = {};
```
rewrite the following code sections from let to const


what will happened when the following code runs?:
```typescript
console.log('first');

setTimeout(() => {
console.log("inside");
},3000);

console.log('second');
```

what will happened when the following code runs?:
```typescript
console.log('first');

setTimeout(() => {
console.log("inside");
},0);

console.log('second');
```

what will happened when the following code runs?:

```typescript
console.log("first");

setTimeout(() => {
console.log("timeout");
})

Promise.resolve("Promise").then(res => console.log(res));

console.log("end")

```

### Hands-On Exercise: What the Heck IS the Event Loop, Anyway?

# Hands-On Exercise: What the Heck IS the Event Loop, Anyway?


---

## Part 1: The Synchronous World - The Call Stack

First, let's see how JavaScript runs code when there's no asynchronicity involved. This is all about the **Call Stack**.

**Instructions:**

- Create a new HTML file and give it the basic structure, including html, head, body, and an empty script tag inside the body.
- Inside the script tag, create a function named third. It should log the message "Third function called!" to the console.
- Create another function named second. Inside it, first log "Second function is calling third...", then call your third function, and finally log "Second function finished.".
- Create a function named first. It should log "First function is calling second...", then call the second function, and then log "First function finished.".
- In the main part of your script (after the function definitions), log "Script starting...".
- On the next line, call your first function.
- On the last line, log "Script finished.".
- Open the file in your browser and check the **Console** in your Developer Tools. Notice the order of the messages.

> [!QUESTION] Think About It  
> Why did the messages appear in that specific order? This demonstrates the "Last-In, First-Out" (LIFO) nature of the Call Stack.

---

## Part 2: Asynchronous Code - Web APIs & the Callback Queue

Now, let's introduce an asynchronous Web API. setTimeout is a function provided by the browser, not by the JavaScript engine itself.

**Instructions:**

- Clear the inside of your script tag.
- First, log the word Start to the console.
- Next, call the setTimeout function. It takes two arguments: a callback function to run later, and a delay in milliseconds.
- For the first argument, provide a new function. Inside this function, log the message "Fired from the timeout!".
- For the second argument, provide the number 2000, which represents a 2-second delay.
- Finally, as the last line of your script, log the word End to the console. 
- Save and refresh the page. Watch the console closely.

> [!QUESTION] Think About It  
> Why did 'End' appear before "Fired from the timeout!"? What was happening during those two seconds? This shows the browser's Web API handling the timer while your main script finishes.

---

## Part 3: The setTimeout(0) "Trick"

What happens if we tell the browser to wait for 0 milliseconds? It should be instant, right?

**Instructions:**

- Go back to the code you wrote in Part 2.
- Find your setTimeout call and change the delay from 2000 to 0.
- Save and refresh the page. Observe the order of the logs in the console.

> [!QUESTION] Think About It  
> The output order is the same! Why? This proves a critical concept: setTimeout(0) does not mean "run this now." It means "add this to the Callback Queue immediately, to be run after the current Call Stack is empty."

---

## Part 4: Blocking the Event Loop

Since JavaScript is single-threaded, a long-running synchronous task can cause major problems. Let's create one and see what happens.

**Instructions:**

- In the body of your HTML file, before the script tag, add a button element. Give it an ID of "myButton" and the text "Click me... if you can!".
- Now, clear the inside of your script tag again.
- Get a reference to the button using document.getElementById('myButton') and store it in a constant.
- Add a click event listener to the button. The callback function for this listener should simply log "Button clicked!" to the console.
- After setting up the listener, log the message "Starting a long, blocking task...".
- To simulate a long task, create a while loop. Before the loop, store the current time in a constant using Date.now(). The loop's condition should check if the new current time minus the start time is less than 5000 (5 seconds). Leave the body of the loop empty. This will effectively pause your script for 5 seconds.
- After the while loop, log the message "Long task finished!".
- Save and refresh. As soon as the page loads, immediately start clicking the button repeatedly. Try to select text on the page as well.  

> [!QUESTION] Think About It  
> Notice how the entire page was frozen? The button didn't react, and your clicks weren't processed until after the long task finished. This is **blocking**. The long synchronous loop was on the Call Stack, preventing the Event Loop from processing anything else, including your clicks and the browser's own rendering updates.


## React Under The Hood:
- read the following article demystifing hooks
- https://react.dev/learn/choosing-the-state-structure
- complete the challenges at the end of the article above
-  [`key` prop](https://www.youtube.com/watch?v=A8AxHueElo0)
- 

 JS Objects And Cloning With React Integration:
	- Read the following [article](https://javascript.info/object-copy)
	- [`React.memo`](https://react.dev/reference/react/memo)
	- immer - useImmer (there's official React docs on that)

> [!question]- Answer questions after reading
> What will be the output of the following code:
> 
> ```typescript
> const person = {
>   name: "ofek",
>   birthdate: new Date(2003, 2, 31), // 🎂
>   favoriteColor: Color.RED,
> };
> 
> const newPerson = 
> ```

what will happened when the following block of code run:
```javascript
const car = { brand: "Toyota" };
car = { brand: "Honda" };
```

what will be printed from the following block of code:
```javascript
const user = { name: "Alice" };
user.name = "Bob";
console.log(user.name);
```

What will be printed?:
```javascript
const settings = Object.freeze({ theme: "dark" });
settings.theme = "light";
console.log(settings.theme);
```

Is this allowed with `const`? What will be printed?:
```javascript
const numbers = [1, 2, 3];
numbers.push(4);
console.log(numbers);
```

Is this allowed? What will be printed?:
```javascript
const app = { config: { debug: true } };
app.config.debug = false;
console.log(app.config.debug);
```

- Why can we push items into a `const` array but cannot reassign the array itself?
- How do `Object.freeze()` and `const` differ in protecting object data?
- why can we edit an object even when it's declared with const?

// add react.memo()
hands on section:
####  **Part 1: `const` and Object Behavior**
##### Step 1: Reassignment Block
- Declare an object with `const`.
- Try to reassign it to a completely new object.
- Observe the error.
##### Step 2: Mutate a Property
- Change a property of that `const` object.
- Log the result and see what happens.
---

#### **Part 2: Object.freeze Limitations**

##### Step 3: Freeze the Object
- Use `Object.freeze` on a flat object.
- Try changing a property.
- Check if the change was applied or not.
##### Step 4: Freeze Only Top Level
- Create a nested object.
- Freeze only the top-level object.
- Try changing a deeply nested property.
- Observe whether the change succeeded and why.
---
#### **Part 3: Array and Reference Behavior**
####  Step 5: Mutate a `const` Array
- Create an array using `const`.
- Push a new item into it.
- Log the result and confirm if it worked.
#### Step 6: Shared Reference Pitfall
- Create an object.
- Assign it to another variable.
- Change a property using the second variable.
- Check if the original object also changed.    
---
####  **Part 4: Intro to Immer.js**
> Make sure to install Immer with `npm install immer`.
#####  Step 7: Immutable Update
- Use Immer’s `produce` to modify a property of an object.
- Compare the original and the new object.
####  Step 8: Add New Property
- Use Immer to add a new property to an existing object.
- Confirm that only the draft copy was affected.
#### Step 9: Modify an Array Immutably
- Use Immer to add a new element to an array.
- Verify that the original array remains unchanged.
####  Step 10: Deep Immutable Updates
- Use Immer to update a deeply nested value in an object.
- Check both the base and the updated object to confirm immutability.
---

#### **Part 5: Deep Copying with `structuredClone`**
#####  Step 11: Shallow vs Deep Copy
- Create a nested object.
- Make a shallow copy using spread syntax or `Object.assign`.
- Mutate a deeply nested property in the copy.
- Check if the original object was affected.
#### Step 12: Use `structuredClone`
- Use `structuredClone()` on the same nested object to create a deep copy.
- Mutate a deeply nested property in the clone.
- Confirm that the original object did **not** change.


## JS

- [Nullish coalescing operator '??'](https://javascript.info/nullish-coalescing-operator)
- [Optional chaining](https://javascript.info/optional-chaining)
- 
## CSS - Logical properties
- intro question: card example todo(ofek)
- read the following [article](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_logical_properties_and_values)
- continue reading the [guides section](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_logical_properties_and_values#guides)
- answer the following questions: 
	1. explain in simple words what does inline represents in css and what does block.
	2. now that you know about logical properties how would you rewrite the code of the card in the intro question?
	3. are physical properties still useful after the introduction of logical properties? explain. 
	4. [screenshot-square-with-rouded-corners] : given the writing direction is `vertical-rtl`, what will be the css rules to mimic the following square.
		

## Advanced TS

What will be the type of the variable `DEFAULT_LOCALE`?

```typescript
type Locale = "en" | "he";

const DEFAULT_LOCALE: Locale = "en";
```

> [!tip]- Answer
> The type will be `Locale` but why?


- `satisfies`, `as const`, `: T`
- Enums considered harmful YouTube video
- `as const` - most underrated TS feature
- 


5. Team conventions and code quality - linters and formatters

- Exercise fix faulty code to follow conventions
5. Working with browser debugger (right throught VSCode noam?)
6. Working with React DevTools - profiling and components tree
## TailwindCSS

Read the introduction of [TailwindCSS](https://tailwindcss.com/docs/styling-with-utility-classes)

In your own words what's the rationale behind TailwindCSS?

Convert the code from execrise #4 in Logical properties todo(ofek, "add link") to TailwindCSS

`data-[state=""]:`

- cn rationale

Creating custom components that have default class names - how to override?

Implement the following screenshot (Figma design - Tools Eligibility - implement in your own)

## Writing a Node.js BE Express/fastapi + JWT

### Building the BE - Express


### Zod schemas

Exercise add schemas to endpointsl

Good [YouTube video about JWT]()

## TanStack Query (half a day each day)

6. TanStack Query + devtools