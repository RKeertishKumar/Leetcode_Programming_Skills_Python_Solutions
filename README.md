# Leetcode Programming Skills Python Solutions

The repo has a well-commented markdown file for the programming skills section of Leetcode problems for quick review.

## Question 1

**1768. Merge Strings Alternately**

You are given two strings `word1` and `word2`. Merge the strings by adding letters in alternating order, starting with `word1`. If a string is longer than the other, append the additional letters onto the end of the merged string.

Return the merged string.

### Example 1

**Input:** `word1 = "abc"`, `word2 = "pqr"`  
**Output:** `"apbqcr"`  
**Explanation:** The merged string will be merged as so:
```
word1:  a   b   c
word2:    p   q   r
merged: a p b q c r
```

### Solution

```python
class Solution:
    def mergeAlternately(self, word1: str, word2: str) -> str:
        # Let's have an empty string to store the new string
        new_string = ""

        # Find the minimum length of both the strings so we know until which index the loop has to run so that we don't get an out of index error
        minlen = min(len(word1), len(word2))

        # Let's go through both the strings and add the character to the new array
        for i in range(minlen):
            new_string += word1[i]
            new_string += word2[i]

        # Use the slice function to add the remaining characters. If there are no remaining characters, it doesn't add anything
        # Notice we start the slicing form the minimum length, thus only the word with the greater length of the variable will be added.
        new_string += word1[minlen:]
        new_string += word2[minlen:]

        return new_string
