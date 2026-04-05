# Leetcode 680 - Valid Palindrome II

**HINT : Allowed to remove characters? Then follow this approach!**

## Problem Statement
Given a string s, return true if the s can be palindrome after deleting at most one character from it.

## Examples
**Example 1:**
Input: s = "aba"
Output: true

**Example 2:**
Input: s = "abca"
Output: true
Explanation: You could delete the character 'c'.

**Example 3:**
Input: s = "abc"
Output: false

## Constraints
1 <= s.length <= 105
s consists of lowercase English letters.

## Solution
```java
class Solution
{
    public boolean isPalindrome(String s, int left, int right)
    {
        while(left < right)
        {
            if(s.charAt(left) != s.charAt(right))
            {
                return false;
            }
            else
            {
                left++;
                right--;
            }
        }
        return true;
    }
    public boolean validPalindrome(String s)
    {
        int left = 0;
        int right = s.length() - 1;

        while(left < right)
        {
            if(s.charAt(left) != s.charAt(right))
            {
                return isPalindrome(s, left + 1, right) || isPalindrome(s, left, right - 1);
            }
            left++;
            right--;
        }
        return true;
    }
}
```

## Time Complexity : O(n)
The main validPalindrome() function iterates through the string once with two pointers → O(n)
When a mismatch is found, isPalindrome() is called at most twice
Each isPalindrome() call also runs in O(n) in the worst case
But since these are not nested, it's still O(n) overall

## Space Complexity : O(1)
No new strings are created
Only a few integer variables left and right are used
The recursive-looking isPalindrome() is just a regular function call, not actual recursion with a call stack growing
So memory usage is constant → O(1)
