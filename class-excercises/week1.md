# Class Exercises - Week 1: JavaScript Fundamentals

## Topics Covered: Variables, Data Types, Arrays, Operators, Expressions, Conditional Statements (if, else, else if)

### **Exercise Set 1: Variables & Basic Operations**

#### Exercise 1.1: Personal Information Card

**Task:** Create a program that stores your name, age, city, and favorite color in variables, then displays them in a formatted message.

**Example Output:**

```
Name: John Doe
Age: 25
City: Toronto
Favorite Color: Blue
```

---

#### Exercise 1.2: Simple Calculator

**Task:** Create variables for two numbers, then calculate and display:

- Sum
- Difference
- Product
- Quotient
- Remainder (modulo)

**Example:**

```javascript
let num1 = 15;
let num2 = 4;
// Calculate and display all operations
```

---

#### Exercise 1.3: Temperature Converter

**Task:** Convert a temperature from Celsius to Fahrenheit using the formula: `F = (C * 9/5) + 32`

**Test Cases:**

- 0°C = 32°F
- 100°C = 212°F
- 25°C = 77°F

---

#### Exercise 1.4: Balance Checker (Introduction to Conditionals)

**Task:** Create a program that checks if a user has enough balance to purchase an item. Use the example from the course material:

- Set `balance = 500` and `itemPrice = 100`
- Use an `if` statement to check if `itemPrice <= balance`
- Display "You have enough money to purchase the item!" if true
- Display "You do not have enough money." if false

**Extension:** Try different values for balance and itemPrice to test both conditions.

---

### **Exercise Set 2: Data Types & Type Coercion**

#### Exercise 2.1: Type Detective

**Task:** Create variables of different types (Number, String, Boolean, undefined, null) and use `typeof` to identify each type. Display the type of each variable.

**Example:**

```javascript
let value1 = 42;
let value2 = "42";
let value3 = true;
let value4;
let value5 = null;
// Display typeof for each
```

---

#### Exercise 2.2: String vs Number Operations

**Task:** Demonstrate the difference between:

- `"5" + 3` vs `5 + 3`
- `"5" - 3` vs `5 - 3`
- `"5" * 2` vs `5 * 2`
- `"10" / 2` vs `10 / 2`

Explain why each produces different results.

---

#### Exercise 2.3: BigInt Calculator

**Task:** Create a program that calculates very large numbers using BigInt. Calculate:

- `9007199254740991n + 1n` (Number.MAX_SAFE_INTEGER + 1)
- Compare with regular Number operations

---

### **Exercise Set 3: Arrays**

#### Exercise 3.1: Shopping List

**Task:** Create an array of grocery items. Display:

- The first item
- The last item
- The total number of items
- All items in a formatted list

**Example:**

```javascript
let groceries = ["milk", "bread", "eggs", "cheese"];
// Display formatted output
```

---

#### Exercise 3.5: Array Validation with Conditionals

**Task:** Create an array and use conditionals to validate:

1. Check if the array is empty (length === 0)
2. Check if the first element exists
3. Check if the array has more than 5 elements
4. Display appropriate messages for each condition

**Example:**

```javascript
let items = ["apple", "banana", "cherry"];
// Use if statements to check array conditions
```

---

#### Exercise 3.4: Array Manipulation

**Task:**

1. Create an empty array
2. Add elements at specific indices (e.g., index 0, 3, 5)
3. Display the array length
4. Access elements at different indices
5. Explain what happens with "holes" in the array

---

### **Exercise Set 4: Operators**

#### Exercise 4.1: Operator Practice

**Task:** Create examples demonstrating:

- Arithmetic operators (+, -, \*, /, %)
- Assignment operators (++, --, +=, -=, \*=, /=)
- Comparison operators (==, ===, !=, !==, <, >, <=, >=)
- Logical operators (&&, ||, !)
- Ternary operator

**Challenge:** Create a single program that uses all operator types meaningfully.

---

#### Exercise 4.2: Comparison Detective

**Task:** Create a comparison table showing:

```javascript
1 == "1"; // true or false?
1 === "1"; // true or false?
0 == false; // true or false?
0 === false; // true or false?
null == undefined; // true or false?
null === undefined; // true or false?
```

Explain why each comparison produces its result.

---

#### Exercise 4.3: Increment/Decrement Puzzle

**Task:** Predict and verify the output:

```javascript
let a = 5;
let b = a++;
let c = ++a;
let d = a--;
let e = --a;
// What are the values of a, b, c, d, e?
```

---

### **Exercise Set 5: Expressions & Calculations**

#### Exercise 5.1: Expression Evaluator

**Task:** Evaluate and display results of:

- `(10 + 5) * 2 - 8 / 4`
- `"Hello" + " " + "World" + "!"`
- `!(true && false) || true`
- `(5 > 3) && (10 < 20)`

---

#### Exercise 5.2: Area Calculator

**Task:** Calculate and display:

- Area of a rectangle: `length * width` (use 10 and 6)
- Area of a triangle: `(base * height) / 2` (use 8 and 12)

---

#### Exercise 5.3: String Expression Builder

**Task:** Build a formatted message using template literals (if covered) or concatenation:

- Create variables for: firstName, lastName, age, city
- Build: "Hello, I'm [firstName] [lastName], I'm [age] years old, and I live in [city]."

---

### **Exercise Set 6: Conditional Statements** (Week 1 Core Topic)

#### Exercise 6.1: Age Checker (Basic if)

**Task:** Check if a person is old enough to vote (18+). Display appropriate messages.

**Example:**

```javascript
let age = 20;
// Display "You can vote!" or "You cannot vote yet."
```

---

#### Exercise 6.1b: Age-Based Welcome Message (if-else if-else)

**Task:** Create a program similar to the week1.md example that displays different messages based on user age:

- If age is between 18 and 29: "Welcome! You're eligible for our special offer."
- If age is between 30 and 39: "Hello! Enjoy exploring our products."
- Otherwise: "Welcome! We hope you enjoy browsing our site."

**Test Cases:** 25, 35, 15, 45

**Example:**

```javascript
let userAge = 25;
// Use if, else if, and else statements
```

---

#### Exercise 6.2: Grade Assigner (if-else if-else)

**Task:** Convert a numeric grade to a letter grade using else if statements:

- 90-100: A
- 80-89: B
- 70-79: C
- 60-69: D
- Below 60: F

**Important:** Remember there is no `elseif` in JavaScript - always use `else if` (two words).

**Test Cases:** 95, 87, 72, 65, 45

**Example:**

```javascript
let grade = 87;
if (grade >= 90) {
  // A
} else if (grade >= 80) {
  // B
} // ... continue pattern
```

---

#### Exercise 6.3: Login Simulator (Multiple Conditions)

**Task:** Check username and password using nested conditionals. Display:

- "Login successful" if both are correct
- "Invalid username" if username is wrong (but password might be correct)
- "Invalid password" if password is wrong (but username is correct)
- "Both are incorrect" if both are wrong

**Example:**

```javascript
let storedUsername = "admin";
let storedPassword = "secret123";
let username = "admin";
let password = "secret123";

// Use if-else if-else structure
if (username === storedUsername && password === storedPassword) {
  // Login successful
} else if (username !== storedUsername && password === storedPassword) {
  // Invalid username
} // ... continue
```

---

#### Exercise 6.3b: Simple Login (Using Logical Operators)

**Task:** Create a simpler version that checks:

- If username is correct AND password is correct: "Login successful"
- Otherwise: "Login failed"

**Then extend it to check:**

- If username OR password is empty: "Please enter both username and password"
- Otherwise, check if both match

---

#### Exercise 6.4: Number Classifier (Complex Conditionals)

**Task:** Classify a number using if-else if-else structure:

- Positive even (number > 0 AND number % 2 === 0)
- Positive odd (number > 0 AND number % 2 !== 0)
- Negative even (number < 0 AND number % 2 === 0)
- Negative odd (number < 0 AND number % 2 !== 0)
- Zero (number === 0)

**Test Cases:** 4, 7, -8, -3, 0

**Hint:** Use the modulo operator (%) to check if a number is even or odd.

---

#### Exercise 6.4b: Number Range Classifier

**Task:** Classify a number into ranges:

- "Very small" if number < -10
- "Small" if number >= -10 and < 0
- "Zero" if number === 0
- "Small positive" if number > 0 and <= 10
- "Medium" if number > 10 and <= 50
- "Large" if number > 50

**Test Cases:** -15, -5, 0, 5, 25, 75

---

#### Exercise 6.5: Discount Calculator (else if chain)

**Task:** Calculate final price with discount using if-else if-else:

- If purchase > $100: 10% discount
- Else if purchase > $50: 5% discount
- Else: no discount

Display original price, discount percentage, discount amount, and final price.

**Example Output:**

```
Original Price: $120.00
Discount: 10%
Discount Amount: $12.00
Final Price: $108.00
```

**Test Cases:** $25, $75, $150

---

#### Exercise 6.5b: Discount Calculator with Ternary (Optional)

**Task:** Rewrite Exercise 6.5 using ternary operator for the discount percentage:

```javascript
let discount = purchase > 100 ? 0.1 : purchase > 50 ? 0.05 : 0;
```

---

#### Exercise 6.6: Leap Year Checker (Complex Logical Conditions)

**Task:** Determine if a year is a leap year using if-else if-else:

- If divisible by 400: leap year
- Else if divisible by 100: NOT a leap year
- Else if divisible by 4: leap year
- Else: NOT a leap year

**Important:** Check conditions in the correct order! Once a condition is true, the rest are ignored.

**Test Cases:** 2020 (leap), 2021 (not), 1900 (not), 2000 (leap), 2024 (leap)

**Example:**

```javascript
let year = 2020;
if (year % 400 === 0) {
  // Leap year
} else if (year % 100 === 0) {
  // Not leap year
} else if (year % 4 === 0) {
  // Leap year
} else {
  // Not leap year
}
```

---

#### Exercise 6.7: BMI Calculator (Multiple Conditionals)

**Task:** Calculate BMI and classify using if-else if-else:

- BMI = weight (kg) / height (m)²
- Underweight: BMI < 18.5
- Normal: BMI >= 18.5 AND BMI < 25
- Overweight: BMI >= 25 AND BMI < 30
- Obese: BMI >= 30

**Test Cases:**

- Weight: 70kg, Height: 1.75m (BMI ≈ 22.9, Normal)
- Weight: 50kg, Height: 1.60m (BMI ≈ 19.5, Normal)
- Weight: 45kg, Height: 1.70m (BMI ≈ 15.6, Underweight)
- Weight: 90kg, Height: 1.75m (BMI ≈ 29.4, Overweight)

---

#### Exercise 6.8: Temperature Alert System

**Task:** Create a temperature monitoring system:

- If temperature < 0: "Freezing! Bundle up!"
- Else if temperature < 10: "Very cold! Wear a jacket."
- Else if temperature < 20: "Cool weather."
- Else if temperature < 30: "Pleasant temperature."
- Else: "Hot! Stay hydrated."

**Test Cases:** -5, 5, 15, 25, 35

---

### **Exercise Set 7: Debugging & Problem Solving**

#### Exercise 7.1: Fix the Code

**Task:** Students are given buggy code and must fix it:

```javascript
// Buggy Code:
let name = "John";
let age = 25;
let message = "Hello" + name + "you are" + age + "years old";
console.log(message);

// Expected: "Hello John, you are 25 years old."
```

---

#### Exercise 7.2: Type Conversion Challenge

**Task:** Predict and verify outputs, then explain:

```javascript
let a = "5";
let b = 3;
console.log(a + b); // What is this?
console.log(a - b); // What is this?
console.log(a * b); // What is this?
console.log(a / b); // What is this?
```
