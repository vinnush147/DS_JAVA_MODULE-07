# Ex9 Finding the Longest Length of Nested Set in a Permutation Array
## DATE:21/11/2025
## AIM:
To write a program that finds the length of the longest set s[k] defined as s[k] = { nums[k], nums[nums[k]], nums[nums[nums[k]]], … },where the iteration stops before a duplicate element occurs.

The task is to return the maximum size among all such sets.
## Algorithm
1. For each index i, start a new chain beginning at nums[i].

2.Follow the chain by repeatedly jumping to nums[j] until a repeated value is found.

3.Keep track of visited elements in the current chain.

4.Update the maximum chain length found so far.

5.Clear the chain and repeat for all starting indices.


## Program:
```
/*
Program to find the Longest Length of Nested Set in a Permutation Array
Developed by: Vinnush Kumar L S
RegisterNumber: 212223230244
import java.util.*;
public class ArrayNestingMain {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String input = sc.nextLine().trim();
        input = input.replace("nums =", "").replace("[", "").replace("]", "").trim();
        String[] parts = input.split(",");
        int[] nums = new int[parts.length];

        for (int i = 0; i < parts.length; i++) {
            nums[i] = Integer.parseInt(parts[i].trim());
        }
        Solution sol = new Solution();
        int result = sol.arrayNesting(nums);
        System.out.println(result);
        sc.close();
    }
}
class Solution {
    public int arrayNesting(int[] nums) {
        ArrayList<Integer> com = new ArrayList<>();
        int maxlen = 0;

        for (int i = 0; i < nums.length; i++) {
            int j = nums[i];
            com.add(j);
            while (true) {
                if (!com.contains(nums[j])) {
                    com.add(nums[j]);
                    j = nums[j];
                } else {
                    break;
                }
            }
            if (com.size() > maxlen) {
                maxlen = com.size();
            }
            com.clear();
        }
        return maxlen;
    }
}


*/
```

## Output:
<img width="508" height="117" alt="image" src="https://github.com/user-attachments/assets/8d398ccf-7551-424a-b5b3-90a7954e8805" />


## Result:
The program successfully computes the longest length of the nested set s[k] for the given permutation array.
