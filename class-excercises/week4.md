# Class Exercises - Week 4: Callbacks, Promises & Async/Await

## Topics Covered: Asynchronous Programming, Callbacks, Promises, Async/Await

### **Exercise Set 1: Understanding Asynchronous Code**

#### Exercise 1.1: setTimeout Basics

**Task:** Create a program that demonstrates asynchronous behavior using `setTimeout`.

**Instructions:**
1. Output "Start" to the console
2. Use `setTimeout` to output "Middle" after 1 second (1000 milliseconds)
3. Output "End" to the console immediately after the setTimeout call

**Expected Output:**
```
Start
End
Middle  (appears 1 second later)
```

**Hint:** Remember that `setTimeout` takes two parameters: a callback function and a delay in milliseconds.

**Question:** Why does "End" appear before "Middle" even though it's written after the setTimeout call?

---

#### Exercise 1.2: Multiple setTimeout Calls

**Task:** Create three `setTimeout` calls that output "First", "Second", and "Third" after random delays (between 500ms and 2000ms each).

**Instructions:**
- Use `Math.random()` to generate random delays
- Run the code multiple times and observe the output order
- Notice that the order is unpredictable

**Hint:** 
- Use `Math.random()` to generate a number between 0 and 1
- Multiply by the range (1500) to get 0-1500
- Add the minimum (500) to get 500-2000
- Use `Math.floor()` to get an integer
- Create three separate `setTimeout` calls with different variable names

---

### **Exercise Set 2: Callbacks**

#### Exercise 2.1: Simple Callback Function

**Task:** Create a function called `greetUser` that takes a name and a callback function as parameters. The function should output a greeting, then call the callback function.

**Instructions:**
1. Create `greetUser(name, callback)` function
2. Inside the function, output: `"Hello, ${name}!"`
3. Call the callback function
4. Create a callback function that outputs "Greeting complete!"
5. Call `greetUser` with your name and the callback

**Hint:**
- A callback is just a function parameter
- Call the callback using `callback()` syntax
- You can pass a function name or define an inline function

**Expected Output:**
```
Hello, Alice!
Greeting complete!
```

---

#### Exercise 2.2: Callback with Parameters

**Task:** Create a function `processData` that simulates processing data (using setTimeout) and calls a callback with the processed result.

**Instructions:**
1. Create `processData(data, callback)` function
2. Use `setTimeout` to simulate processing (delay of 1 second)
3. After the delay, call the callback with the processed data (e.g., `data.toUpperCase()` for strings)
4. Create a callback function that receives and displays the processed data
5. Test with different data values

**Hint:**
- The callback function should receive the processed data as a parameter
- When calling the callback, pass the processed data: `callback(processedData)`
- The callback function you create should accept one parameter to receive the result

---

#### Exercise 2.3: Sequential Callbacks (Callback Hell Preview)

**Task:** Create three functions that must execute in order: `step1`, `step2`, and `step3`. Each function should take a callback and call it after a random delay.

**Instructions:**
1. Create `step1(callback)` that outputs "Step 1 complete" after a delay, then calls the callback
2. Create `step2(callback)` that outputs "Step 2 complete" after a delay, then calls the callback
3. Create `step3(callback)` that outputs "Step 3 complete" after a delay, then calls the callback
4. Chain them together so they execute in order: step1 → step2 → step3

**Hint:**
- Each function should accept a callback parameter
- After the delay and console.log, call the callback
- To chain them, pass the next function as the callback: `step1(() => { step2(...) })`
- This creates nested callbacks - notice how it gets harder to read!

**Question:** What happens if you need to add a `step4`? How does the code become harder to read?

---

### **Exercise Set 3: Promises**

#### Exercise 3.1: Creating Your First Promise

**Task:** Create a function `waitForSeconds` that returns a Promise. The promise should resolve after a specified number of seconds.

**Instructions:**
1. Create `waitForSeconds(seconds)` function that returns a new Promise
2. Use `setTimeout` inside the Promise
3. Resolve the promise after the specified time
4. Use `.then()` to handle the resolved promise
5. Output a message when the promise resolves

**Hint:**
- A Promise is created with `new Promise((resolve, reject) => { ... })`
- Call `resolve()` when the operation completes successfully
- The function should `return` the Promise
- Use `.then()` on the returned promise to handle the result
- Remember: `seconds * 1000` converts seconds to milliseconds

---

#### Exercise 3.2: Promise with Data

**Task:** Create a function `fetchUserData` that returns a Promise resolving with user information.

**Instructions:**
1. Create `fetchUserData(userId)` that returns a Promise
2. Simulate a delay (1 second) before resolving
3. Resolve with an object containing user data: `{ id: userId, name: "John Doe", email: "john@example.com" }`
4. Use `.then()` to receive and display the user data

**Hint:**
- Pass data to `resolve()` as a parameter: `resolve(dataObject)`
- The data passed to `resolve()` becomes available in the `.then()` callback
- The parameter in `.then((user) => ...)` receives whatever was passed to `resolve()`

---

#### Exercise 3.3: Promise Rejection and Error Handling

**Task:** Create a function `checkAge` that returns a Promise. If age is 18 or older, resolve with "Access granted". If age is less than 18, reject with "Access denied: too young".

**Instructions:**
1. Create `checkAge(age)` that returns a Promise
2. Use `setTimeout` to simulate a delay (500ms)
3. Check if age >= 18, resolve if true, reject if false
4. Use `.then()` for success and `.catch()` for error handling

**Hint:**
- Use `if/else` to check the condition
- Call `resolve()` for success, `reject()` for failure
- Chain `.catch()` after `.then()` to handle rejections
- The error message passed to `reject()` becomes available in `.catch()`
- Test with both valid (>= 18) and invalid (< 18) ages

---

#### Exercise 3.4: Chaining Promises

**Task:** Create three functions that return Promises: `getUser()`, `getUserPosts(userId)`, and `getPostComments(postId)`. Chain them together to get user → posts → comments.

**Instructions:**
1. `getUser()` resolves with `{ id: 1, name: "Alice" }` after 500ms
2. `getUserPosts(userId)` resolves with `[{ id: 101, title: "Post 1" }]` after 500ms
3. `getPostComments(postId)` resolves with `["Great post!", "Thanks!"]` after 500ms
4. Chain them using `.then()` to execute in order

**Hint:**
- Each `.then()` should return the next promise: `return getUserPosts(user.id)`
- The returned promise becomes available in the next `.then()`
- Use data from previous promises: `user.id`, `posts[0].id`
- This is called "promise chaining" - each step waits for the previous one

---

### **Exercise Set 4: Async/Await**

#### Exercise 4.1: Converting Promises to Async/Await

**Task:** Convert the `waitForSeconds` function from Exercise 3.1 to use async/await syntax.

**Instructions:**
1. Create an `async` function called `waitAndLog`
2. Use `await` to wait for `waitForSeconds(2)`
3. Log the result

**Hint:**
- Mark the function with `async` keyword: `async function waitAndLog()`
- Use `await` before the promise-returning function: `await waitForSeconds(2)`
- The `await` keyword "pauses" execution until the promise resolves
- Wrap in `try/catch` to handle potential errors
- The resolved value is directly available (no need for `.then()`)

---

#### Exercise 4.2: Async/Await with Error Handling

**Task:** Convert the `checkAge` function from Exercise 3.3 to use async/await with try/catch.

**Instructions:**
1. Create an `async` function `verifyAccess`
2. Use `await` to call `checkAge(age)`
3. Use `try/catch` to handle both success and error cases
4. Test with both valid (20) and invalid (15) ages

**Hint:**
- Use the same `checkAge` function from Exercise 3.3
- `await` will throw an error if the promise rejects
- `try/catch` handles both success (resolve) and failure (reject)
- If `checkAge` rejects, execution jumps to the `catch` block
- Test with both valid and invalid ages to see both paths

---

#### Exercise 4.3: Sequential Async/Await

**Task:** Convert the chained promises from Exercise 3.4 to use async/await syntax.

**Instructions:**
1. Create an `async` function `loadUserData`
2. Use `await` for each step: getUser → getUserPosts → getPostComments
3. Log each result as it's received
4. Compare the readability with the promise chaining version

**Hint:**
- Use the same functions from Exercise 3.4
- Each `await` waits for the previous one to complete
- You can use the result directly: `const user = await getUser()`
- Then use that result in the next call: `await getUserPosts(user.id)`
- Compare this code structure to the promise chaining version - which is easier to read?

**Question:** How does this compare to the promise chaining version? Which do you find easier to read?

---

#### Exercise 4.4: Multiple Async Operations

**Task:** Create an async function that fetches data from three different "sources" simultaneously and waits for all of them.

**Instructions:**
1. Create three functions: `fetchData1()`, `fetchData2()`, `fetchData3()` that return Promises
2. Each should resolve with different data after random delays (500-1500ms)
3. Use `Promise.all()` to wait for all three to complete
4. Display all results together

**Hint:**
- `Promise.all()` takes an array of promises
- It waits for ALL promises to resolve (or any to reject)
- Use `await Promise.all([...])` to wait for all results
- The results array will be in the same order as the input promises
- All three functions execute simultaneously, not sequentially!

---

### **Exercise Set 5: Practical Application**

#### Exercise 5.1: Simulated File Reading

**Task:** Create a function `readFile` that simulates reading a file asynchronously. Use it to read three files in sequence and display their contents.

**Instructions:**
1. Create `readFile(filename)` that returns a Promise
2. It should resolve with file content after a delay (simulating file I/O)
3. Create an async function that reads three files: "file1.txt", "file2.txt", "file3.txt"
4. Display each file's content as it's read

**Hint:**
- `readFile` should return a Promise that resolves with file content
- Use `await` to read each file sequentially
- Each file waits for the previous one to complete
- The resolved value is the file content string
- What would happen if you used `Promise.all()` instead? (Try it!)

---

#### Exercise 5.2: User Authentication Flow

**Task:** Create a simulated user authentication flow using async/await.

**Instructions:**
1. Create `validateUsername(username)` - resolves if username length > 3, rejects otherwise
2. Create `validatePassword(password)` - resolves if password length > 6, rejects otherwise
3. Create `loginUser(username, password)` - resolves with user object if both validations pass
4. Create an async function `authenticate` that performs all steps
5. Handle errors appropriately

**Hint:**
- Each validation function should check a condition and resolve/reject accordingly
- Use `string.length` to check string length
- Call validations sequentially with `await`
- If any validation fails (rejects), the `catch` block will execute
- Only call `loginUser` if both validations pass
- Test with invalid username, invalid password, and valid credentials

---

### **Challenge Exercise**

#### Challenge: Promise Race

**Task:** Create three functions that return Promises with different delays. Use `Promise.race()` to see which one completes first.

**Instructions:**
1. Create three functions: `fastTask()`, `mediumTask()`, `slowTask()`
2. Each should have different delays (e.g., 500ms, 1000ms, 2000ms)
3. Use `Promise.race()` to execute all three and see which completes first
4. Display the winner

**Hint:**
- `Promise.race()` takes an array of promises
- It returns as soon as the FIRST promise resolves or rejects
- The other promises continue running, but their results are ignored
- Use different delays to see which one wins
- Run it multiple times - the winner should always be the same (fastest one)

---

## Notes for Students:

- **Callbacks** are functions passed as arguments to be executed later
- **Promises** provide a cleaner way to handle asynchronous operations than callbacks
- **Async/Await** makes promise-based code look more like synchronous code
- Always use `try/catch` with async/await to handle errors
- `Promise.all()` waits for all promises to resolve
- `Promise.race()` returns the first promise that resolves or rejects
