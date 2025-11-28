# EX 3E Generate Permutations using Backtracking Approach.

## AIM:

To write a Java program to for given constraints.
Given an array nums of distinct integers, return all the possible Permutation. You can return the answer in any order.
Example 1:
Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]

## Algorithm

1. Initialize a list to store all permutations.
2. Use a backtracking function that takes the current path and a boolean array `used` to track elements.
3. For each unused element, add it to the current path and mark it as used.
4. Recursively continue building the permutation until the path length equals the array length.
5. After recursion, remove the last element (backtrack) and mark it as unused to explore other possibilities.

#### Developed By: Vidhiya lakshmi S

#### Register Number: 212223230238

## Program:

### to implement all possible permutations

```java
import java.util.*;

public class Main {

    public static List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> result = new ArrayList<>();
        boolean[] used = new boolean[nums.length];
        backtrack(nums, new ArrayList<>(), used, result);
        return result;
    }

    private static void backtrack(int[] nums, List<Integer> path, boolean[] used, List<List<Integer>> result) {
        if (path.size() == nums.length) {
            result.add(new ArrayList<>(path));
            return;
        }

        for (int i = 0; i < nums.length; i++) {
            if (!used[i]) {
                used[i] = true;
                path.add(nums[i]);
                backtrack(nums, path, used, result);
                path.remove(path.size() - 1); // backtrack
                used[i] = false;
            }
        }
    }

    public static void main(String[] args) {
        int[] nums = {1, 2, 3};
        List<List<Integer>> permutations = permute(nums);
        System.out.println(permutations);
    }
}
```

## Output:

```
[[1, 2, 3], [1, 3, 2], [2, 1, 3], [2, 3, 1], [3, 1, 2], [3, 2, 1]]
```

## Result:

The program successfully implemented and the expected output is verified.
