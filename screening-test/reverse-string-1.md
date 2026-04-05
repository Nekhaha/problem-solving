# Leetcode 344 - Reverse String

**HINT : Reverse in-place, Two pointers + Swap**

## Problem Statement
Write a function that reverses a string. The input string is given as an array of characters s.
You must do this by modifying the input array in-place with O(1) extra memory.

## Examples
**Example 1:**
Input: s = ["h","e","l","l","o"]
Output: ["o","l","l","e","h"]

**Example 2:**
Input: s = ["H","a","n","n","a","h"]
Output: ["h","a","n","n","a","H"]

## Constraints
1 <= s.length <= 105
s[i] is a printable ascii character.

## Solution
```java
class Solution 
{
    public void reverseString(char[] s) 
    {
        int left = 0;
        int right = s.length - 1;
        
        while(left < right)
        {
            char temp = s[left];
            s[left] = s[right];
            s[right] = temp;

            left++;
            right--;
        }
    }
}
```

## Time Complexity : O(n)
n = length of the array
Two pointers left and right move towards each other
Each element is visited at most once
Total work done is proportional to the length → O(n)

## Space Complexity : O(1)
No new array or string is created
The reversal is done in-place on the original array
Only one extra variable temp is used → O(1)
