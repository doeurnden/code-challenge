# Reverse Parenthesis

## 📘 Description

This project solves the **Reverse Parenthesis** problem.

You are given a string containing **properly nested and balanced parentheses**.
Your task is to return the **decoded string** by applying these rules:

1. **Reverse all characters** inside each pair of parentheses.
2. **Remove all parentheses** in the final result.
3. If parentheses are **nested**, decode the **innermost pair first** and apply reversing outward.

---

## 🔍 Examples

### Example 1

**Input:**

```
(f(b(dc)e)a)
```

**Output:**

```
abcdef
```

### Example 2

**Input:**

```
((is?)(a(t d)h)e(n y( uo)r)aC)
```

**Output:**

```
Can you read this?
```

### Example 3

**Input:**

```
freeCodeCamp
```

---

## 🧠 How It Works

The key idea is to decode from the **innermost parenthese first**.

Example:
`(f(b(dc)e)a)`

- Decode `(dc)` → `"cd"`
- Replace inside: `(f(b(cd)e)a)`
- Decode `(b(cd)e)` from inside → reverse entire content
- Continue until no parentheses remain

To efficiently decode nested parentheses, a **stack** is used.

---

## 🚀 Algorithm (Stack Approach)

1. Create an empty stack.
2. Loop through each character in the string:
   - If the character is **not `)`**, push it onto the stack.
   - If the character is `)`:
     - Pop characters until encountering `(`.
     - Reverse the popped substring.
     - Push the reversed characters back to the stack.
3. After processing the entire string, join all characters remaining in the stack.

---

## 🧩 Pseudocode

```text
function decode(s):
    stack = []

    for char in s:
        if char != ')':
            stack.push(char)
        else:
            temp = []
            while stack.top() != '(':
                temp.append(stack.pop())
            stack.pop()  // remove '('

            reversed_temp = reverse(temp)
            push each char of reversed_temp back to stack

    return join(stack)
```

---

## ⏱️ Time Complexity

- **O(n)** — each character is pushed and popped at most once.
- Efficient for long or deeply nested strings.

---

## 📦 Languages

If you'd like, I can provide implementations in:

- JavaScript
- Python
- Java
- C++
