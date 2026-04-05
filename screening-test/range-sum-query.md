# Range Sum Queries

**HINT : Prefix Sum**

## Problem Statement
Given an integer array nums, answer multiple queries of the following type:

--> Find the sum of elements from index left to index right, both inclusive


## I/O Format
**Input Format:**

Integer n - size of array

Array elements

Number of queries q

q lines each containing 2 space-seperated integers left and right representing the query range.

**Output Format:**

For each query, print the sum of elements, from index left to index right in a new line.

## I/O Sample
**Sample Input:**

6

-2 0 3 -5 2 -1

3

0 2

2 5

0 5

**Sample Output:**

1

-1

-3

## Explanation
Array: [-2, 0, 3, -5, 2, -1]

Query: (0, 2) --> (-2) + (0) + (3) = 1

## Solution
```java
import java.util.*;
public class Main
{
    public static void main(String[] args)
    {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] nums = new int[n];
        
        for(int i = 0; i < n; i++)
        {
            nums[i] = sc.nextInt();
        }
        
        int[] prefix = new int[n];
        prefix[0] = nums[0];
        for(int i = 1; i < n; i++)
        {
            prefix[i] = prefix[i - 1] + nums[i];
        }
            
        int q = sc.nextInt();
        for(int i = 0; i < q; i++)
        {
            int left = sc.nextInt();
            int right = sc.nextInt();
            int sum;
                
            if(left == 0)
            {
                sum = prefix[right];
            }
            else
            {
                sum = prefix[right] - prefix[left - 1];
            }
            System.out.println(sum);
        }
            sc.close();
    }
}
```

## Time Complexity : O(n + q)
Building the prefix array → loops through n elements once → O(n)
Answering each query → each query is answered in O(1) because you're just doing a subtraction prefix[right] - prefix[left-1]
For q queries → O(q) total
Combined → O(n + q)

## Space Complexity : O(n)
The prefix[] array stores n elements → O(n)
No other major data structures used
Input array nums[] also takes O(n) but that's required to store input
