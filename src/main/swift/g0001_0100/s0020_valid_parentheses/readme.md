20\. Valid Parentheses

Easy

Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:

1.  Open brackets must be closed by the same type of brackets.
2.  Open brackets must be closed in the correct order.

**Example 1:**

**Input:** s = "()"

**Output:** true 

**Example 2:**

**Input:** s = "()[]{}"

**Output:** true 

**Example 3:**

**Input:** s = "(]"

**Output:** false 

**Example 4:**

**Input:** s = "([)]"

**Output:** false 

**Example 5:**

**Input:** s = "{[]}"

**Output:** true 

**Constraints:**

*   <code>1 <= s.length <= 10<sup>4</sup></code>
*   `s` consists of parentheses only `'()[]{}'`.

To solve the Valid Parentheses problem in Swift with a `Solution` class, we'll use a stack data structure. Here are the steps:

1. Define a `Solution` class with a method named `isValid` that takes a string `s` as input and returns a boolean indicating whether the string contains valid parentheses.
2. Create a stack to store opening parentheses.
3. Iterate through each character in the input string `s`.
4. If the current character is an opening parenthesis (`'('`, `'{'`, or `'['`), push it onto the stack.
5. If the current character is a closing parenthesis (`')'`, `'}'`, or `']'`), check if the stack is empty. If it is, return `false` because there's no matching opening parenthesis for the current closing parenthesis.
6. If the stack is not empty, pop the top element from the stack and check if it matches the current closing parenthesis. If it doesn't match, return `false`.
7. After iterating through all characters in `s`, check if the stack is empty. If it's not empty, return `false` because there are unmatched opening parentheses remaining.
8. If the stack is empty after processing all characters, return `true` because all parentheses are valid.

Here's the implementation:

```swift
class Solution {
    func isValid(_ s: String) -> Bool {
        var stack = [Character]()
        
        for char in s {
            if char == "(" || char == "[" || char == "{" {
                stack.append(char)
            } else if char == ")" && !stack.isEmpty && stack.last == "(" {
                stack.popLast()
            } else if char == "}" && !stack.isEmpty && stack.last == "{" {
                stack.popLast()
            } else if char == "]" && !stack.isEmpty && stack.last == "[" {
                stack.popLast()
            } else {
                return false
            }
        }
        
        return stack.isEmpty
    }
}
```

This implementation provides a solution to the Valid Parentheses problem in Swift using a stack data structure.