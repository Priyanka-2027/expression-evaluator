# Expression Converter - Understanding Notation Conversions

The Expression Converter transforms mathematical expressions between three different notations: **Infix**, **Prefix**, and **Postfix**. Think of it as a translator for how we write math!

---

## The Three Notations

### Infix (Standard)
This is how we normally write math in school.

**Example:** `A + B * C`

- Operators sit **between** operands.
- We read left-to-right.
- Requires parentheses for clarity: `(A + B) * C`

### Prefix (Polish Notation)
Operators come **before** their operands.

**Example:** `+ A * B C`

- Read from right-to-left
- No parentheses needed!
- `+ A * B C` means: "Add A to the result of (B times C)"

### Postfix (Reverse Polish Notation)
Operators come **after** their operands.

**Example:** `A B C * +`

- Read left-to-right
- No parentheses needed
- `A B C * +` means: "Take A, then add it to (B times C)"

---

## Why These Conversions Matter

Different notations are useful in different situations:

| Notation | Best For |
|----------|----------|
| **Infix** | Human reading and writing |
| **Prefix** | Function calls in programming |
| **Postfix** | Computer evaluation (calculators, processors) |

---

## Why Use Stacks? (The Secret Ingredient!)

A **stack** is like a stack of plates:
- You add items to the **top**
- You remove items from the **top** only
- First item added = Last item removed (LIFO)

**Why are stacks perfect for expression conversion?**

1. **Operator precedence:** Stacks remember which operators came first
2. **Parentheses handling:** Stacks track when to process groups
3. **Efficient:** O(1) time to add/remove items

**Example - Converting `A + B * C` to Postfix:**
```
Step 1: Read 'A' → Output: A, Stack: [ ]
Step 2: Read '+' → Output: A, Stack: [ + ]
Step 3: Read 'B' → Output: A B, Stack: [ + ]
Step 4: Read '*' → Has higher precedence, Stack: [ + * ]
Step 5: Read 'C' → Output: A B C, Stack: [ + * ]
Step 6: End → Pop all, Output: A B C * +
```

Result: `A B C * +` (multiply B and C first, then add A)

---

## Algorithm Overview

### Converting Infix to Postfix

The **Shunting Yard Algorithm** (created by Dijkstra) works like this:

1. **Read** each character left-to-right
2. **If it's a number:** Output it immediately
3. **If it's an operator:**
   - Check stack top operator
   - If stack operator has higher/equal precedence → pop it to output
   - Push current operator to stack
4. **If it's `(`:** Push to stack
5. **If it's `)`:** Pop until we find `(`
6. **At the end:** Pop all remaining operators to output

**Key insight:** By using a stack, we respect operator precedence automatically!

### Other Conversions

- **Infix → Prefix:** Reverse the expression, swap `(` and `)`, convert to postfix, reverse result
- **Prefix/Postfix → Infix:** Use a stack, pop operands and combine with operators

---

## Time Complexity

All conversions have the same complexity:

| Operation | Complexity |
|-----------|-----------|
| **Time** | O(n) - where n = length of expression |
| **Space** | O(n) - for the stack storage |

**Why O(n)?**
- We visit each character exactly once
- Stack operations (push/pop) take O(1)
- Total: n characters × O(1) per character = O(n)

This is **optimal** - we can't do better than reading each character!

---

## Real-World Applications

### 1. **Calculators**
Most calculators convert infix to postfix, then evaluate using a stack:
```
Display: 3 + 4 * 2
Convert: 3 4 2 * +
Evaluate: 3 + (4×2) = 11
```

### 2. **Compilers**
When your code compiles, expressions are often converted to postfix for efficient execution.

### 3. **Databases**
Query engines convert SQL expressions to efficient internal representations.

### 4. **Spreadsheets**
Excel/Google Sheets use similar algorithms to evaluate formula expressions.

### 5. **Graphics & Games**
Physics engines evaluate complex expressions (like collision detection) using these techniques.

---

## Quick Memory Tips

**Remember the differences:**
- **Infix:** What you're used to (A + B)
- **Prefix:** Function-like (+ A B)
- **Postfix:** Stack-friendly (A B +)

**Remember why stacks work:**
- They naturally handle **precedence** (higher ops stay longer in stack)
- They naturally handle **grouping** (parentheses push/pop groups)
- They're **efficient** (O(1) per operation)

---

## Try It Out!

Use the Expression Converter to:
1. Type `A + B * C` in Infix
2. Convert to Postfix → See: `A B C * +`
3. Convert to Prefix → See: `+ A * B C`
4. Enable visualization to watch each step!

This interactive exploration is the best way to truly understand these concepts.

---

##Output Screenshots
<img width="1600" height="749" alt="image" src="https://github.com/user-attachments/assets/4e327f27-0945-4d55-9ab0-fa8ea488b399" />
<img width="1600" height="746" alt="image" src="https://github.com/user-attachments/assets/cc8e8849-515f-4695-ac5a-389e77b87d37" />



## Learn More

These concepts are fundamental to:
- Data Structures courses
- Compiler design
- Algorithm optimization
- Computer architecture

Understanding stacks and notation conversions opens doors to understanding how computers actually evaluate expressions under the hood!
