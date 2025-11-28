# EX 3C Tug of War problem - Backtracking.

## AIM:

To write a Java program to for given constraints.
Given an integer array nums, return true if you can partition the array into two subsets such that the sum of the elements in both subsets is equal or false otherwise.
Example 1:
Input: Enter the number of elements: 4
Enter the elements of the array:
1 5 11 5
Output: true
Explanation: The array can be partitioned as [1, 5, 5] and [11].

Constraints:

1 <= nums.length <= 200
1 <= nums[i] <= 100

## Algorithm

1. Compute the total sum of the array; if it's odd, the split is impossible — return false.
2. Target = sum / 2. We only need to check whether a subset sums to this target.
3. Use a DP boolean array `dp[target + 1]`, where `dp[x]` means "a subset with sum x is possible."
4. For each number in the array, update the dp array **from right to left**.
5. After processing all numbers, return `dp[target]`.

#### Developed By: Vidhiya lakshmi S

#### Register Number: 212223230238

## Program:

### to implement tug-of-war

```java
import java.util.Scanner;

public class Main {

    public static boolean canPartition(int[] nums) {
        int sum = 0;
        for (int x : nums) sum += x;

        if (sum % 2 != 0) return false; // odd sum cannot be split equally

        int target = sum / 2;
        boolean[] dp = new boolean[target + 1];
        dp[0] = true; // sum 0 is always possible

        for (int num : nums) {
            for (int j = target; j >= num; j--) {
                dp[j] = dp[j] || dp[j - num];
            }
        }

        return dp[target];
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter the number of elements: ");
        int n = sc.nextInt();

        int[] nums = new int[n];
        System.out.println("Enter the elements of the array:");
        for (int i = 0; i < n; i++) {
            nums[i] = sc.nextInt();
        }

        System.out.println(canPartition(nums));
        sc.close();
    }
}
```

## Output:

```
Enter the number of elements: 4
Enter the elements of the array:
1 5 11 5
true
```

## Result:

The program successfully implemented and the expected output is verified.
