# Practices for Backtracking

## Count Sorted Vowel Strings

**Example**

```
Input: n = 2
Output: 15
Explanation: The 15 sorted strings that consist of vowels only are
["aa","ae","ai","ao","au","ee","ei","eo","eu","ii","io","iu","oo","ou","uu"].
Note that "ea" is not a valid string since 'e' comes after 'a' in the alphabet.
```

**Explained**



**Solution.java**

```java
/**
 * Count Sorted Vowel Strings
 */
class Solution {

    private static String vowelString = "aeiou";
    private static char[] vowels = vowelString.toCharArray();
    private int result = 0;

    public int countVowelStrings(int n) {
        // Corner case
        // 1 <= n <= 50
        if (n == 1) return vowels.length;
        backtracking(n, new ArrayList<Character>(), 0);
        return result;
    }

    public void backtracking(int n, List<Character> runningChoices, int start) {

        // We have made all decisions
        if (n == runningChoices.size()) {
            result++;
            return;
        }

        // Decision tree traversal
        for (int i = start; i < vowels.length; i++) {

            // 1. Make decision
            runningChoices.add(vowels[i]);
            // 2. Jump into the next level of decision tree
            backtracking(n, runningChoices, i);
            // 3. Undo current decision
            runningChoices.remove(runningChoices.size() - 1);

        }
    }
}
```