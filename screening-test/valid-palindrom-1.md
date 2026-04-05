# Leetcode 125 - Valid Palindrome

## Problem Statement
A phrase is a palindrome if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. 
Alphanumeric characters include letters and numbers.
Given a string s, return true if it is a palindrome, or false otherwise.

## Examples
**Example 1:**
Input: s = "A man, a plan, a canal: Panama"
Output: true
Explanation: "amanaplanacanalpanama" is a palindrome.

**Example 2:**
Input: s = "race a car"
Output: false
Explanation: "raceacar" is not a palindrome.

**Example 3:**
Input: s = " "
Output: true
Explanation: s is an empty string "" after removing non-alphanumeric characters.
Since an empty string reads the same forward and backward, it is a palindrome.

## Constraints
1 <= s.length <= 2 * 105
s consists only of printable ASCII characters.

## Solution
```java
class Solution {
    public boolean isPalindrome(String s)
    {
        String str = s.trim();
        str = str.toLowerCase();
        int i = 0;
        int j = str.length() - 1;
        while(i < j)
        {
            while(i < j && !Character.isLetterOrDigit(str.charAt(i)))
            {
                i++;
            }
            while(i < j && !Character.isLetterOrDigit(str.charAt(j)))
            {
                j--;
            }
            if(str.charAt(i) != str.charAt(j))
            {
                return false;
            }
            i++;
            j--;
        }
        return true;
    }
}
```

## Time Complexity : O(n)
n = length of the string
The two pointers i and j start from both ends and move towards each other
Each character is visited at most once
So the total work done is proportional to the length of the string → O(n)

## Space Complexity : O(n)
Created a new string str using s.trim() and str.toLowerCase()
This creates a copy of the original string in memory
That copy takes up n space → O(n)
