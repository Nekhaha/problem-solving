# Leetcode 3668 - Restore Finishing Order

## Problem Statement
You are given an integer array order of length n and an integer array friends.
order contains every integer from 1 to n exactly once, representing the IDs of the participants of a race in their finishing order.
friends contains the IDs of your friends in the race sorted in strictly increasing order. Each ID in friends is guaranteed to appear in the order array.
Return an array containing your friends' IDs in their finishing order.

## Examples
**Example 1:**

Input: 

order = [3,1,2,5,4], friends = [1,3,4]

Output: 

[3,1,4]


Explanation:

The finishing order is [3, 1, 2, 5, 4]. Therefore, the finishing order of your friends is [3, 1, 4].

**Example 2:**

Input: 

order = [1,4,5,3,2], friends = [2,5]

Output: 

[5,2]


Explanation:

The finishing order is [1, 4, 5, 3, 2]. Therefore, the finishing order of your friends is [5, 2].

## Constraints
1 <= n == order.length <= 100
order contains every integer from 1 to n exactly once

1 <= friends.length <= min(8, n)
1 <= friends[i] <= n
friends is strictly increasing

## Solution
```java
class Solution 
{
    public int[] recoverOrder(int[] order, int[] friends) 
    {
        Set<Integer> friendSet = new HashSet<>();
        for(int frndId : friends)
        {
            friendSet.add(frndId);
        }
        List<Integer> res = new ArrayList<>();
        for(int i : order)
        {
            if(friendSet.contains(i))
            {
                res.add(i);
            }
        }
        int[] arr = new int[res.size()];
        for(int i = 0; i < res.size(); i++)
        {
            arr[i] = res.get(i);
        }
        return arr;
    }
}
```

## Time Complexity : O(m + n)
Building the friendSet (HashSet):
  → You loop through friends → O(m)
Checking each element in order:
  → Loop through order → O(n)
  → Each contains() in HashSet is O(1) (constant time)
Copying res list to array:
  → Loop through result → O(k) (k = number of matching elements)
Total Time Complexity:
  O(m + n + k)

Since, k ≤ n, we simplify to: O(m + n)

## Space Complexity : O(m + n)
HashSet stores all elements from friends → O(m)
res list stores matching elements → O(k)
Output array → O(k)
Since, k ≤ n, we say: O(m + n)
