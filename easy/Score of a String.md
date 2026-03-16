# 📝 Score of a String

| Difficulty | Topics |
| Easy | String, Iteration |

## 📖 Problem Description
You are given a string s. The score of a string is defined as the sum of the absolute difference between the ASCII values of adjacent characters.

Return the score of s.

---

## 💡 Initial Thoughts & Evolution
Initially, I misread the problem as summing all ASCII values. I quickly adjusted to calculate the difference between neighbors once I re-read the prompt.

> Key Insight: In Java, subtracting two char types results in an implicit cast to their ASCII integer values. 
> Example: 'B' - 'A' evaluates to 66 - 65 = 1.

### ❌ Initial Attempt (Summing values)
    public int scoreOfString(String s) {
        int result = 0;
        for(int i = 0; i < s.length(); i++) {
            result += s.charAt(i); 
        } 
        return result;
    }

---

## 🚀 Final Solution
By starting the loop at index 1, we can compare the current character with the one immediately preceding it.

    class Solution {
        public int scoreOfString(String s) {
            int result = 0;
            
            for (int i = 1; i < s.length(); i++) {
                // Calculate absolute difference between adjacent characters
                // Implicit casting handles the ASCII conversion
                result += Math.abs(s.charAt(i) - s.charAt(i - 1));

                // Example with explicit casting
                // result += Math.abs((int) s.charAt(i) - (int) s.charAt(i - 1));
            }
            
            return result;
        }
    }

---

## 🛠️ Algorithm
1. Iterate: Loop through the string starting from the second character (index 1).
2. Subtract: Find the difference between s.charAt(i) and s.charAt(i-1).
3. Absolute Value: Use Math.abs() to ensure the difference is non-negative.
4. Accumulate: Add the result to the result variable.
5. Return: Send back the final sum after the loop finishes.

---

## 📊 Complexity Analysis
* Time Complexity: O(n) — We traverse the string exactly once.
* Space Complexity: O(1) — We only use a single integer variable regardless of input size.

## 📝 Code Notes
* ASCII Trick: Casting a char to an int (or performing math on it) automatically uses its ASCII value.
* Boundary Check: Always start the loop at i = 1 to avoid an IndexOutOfBoundsException when looking back at i - 1.

---

## Pattern found
* Sliding Window (Size 2)