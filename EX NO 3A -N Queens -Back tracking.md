
# EX 3A N Queens Problem - Backtracking Approach.

## AIM:

To Write a Java program for N queens using backtracking approach.
You are given an integer N. For a given N x N chessboard, find a way to place 'N' queens such that no queen can attack any other queen on the chessboard.
A queen can be attacked when it lies in the same row, column, or the same diagonal as any of the other queens. You have to print one such configuration.
Chess Board
<img width="241" height="209" alt="image" src="https://github.com/user-attachments/assets/96aacb61-4f34-423f-b324-5e34454e42b8" />

Note :

Get the input from the user for N . The value of N must be from 1 to 4

If solution exists Print a binary matrix as output that has 1s for the cells where queens are placed

If there is no solution to the problem print "Solution does not exist"

## Algorithm

1. Start with an empty `N × N` board filled with 0s.
2. Try placing a queen in each row of the current column.
3. Before placing, check safety: no other queen in the same row or diagonals.
4. If safe, place the queen (set to 1) and recursively place queens in the next column.
5. If no row works, backtrack by removing the queen and return false.

#### Developed By: Vidhiya lakshmi S

#### Register Number: 212223230238

## Program:

### to implement NQueens

```java
public class Main {

    public static boolean isSafe(int[][] board, int row, int col, int n) {
        // Check row on left
        for (int i = 0; i < col; i++)
            if (board[row][i] == 1) return false;

        // Upper diagonal
        for (int i = row, j = col; i >= 0 && j >= 0; i--, j--)
            if (board[i][j] == 1) return false;

        // Lower diagonal
        for (int i = row, j = col; i < n && j >= 0; i++, j--)
            if (board[i][j] == 1) return false;

        return true;
    }

    public static boolean solveNQueens(int[][] board, int col, int n) {
        if (col >= n) return true;

        for (int row = 0; row < n; row++) {
            if (isSafe(board, row, col, n)) {
                board[row][col] = 1;   // place queen

                if (solveNQueens(board, col + 1, n))
                    return true;

                board[row][col] = 0;   // backtrack
            }
        }

        return false;
    }

    public static void printBoard(int[][] board, int n) {
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                System.out.print(board[i][j] + " ");
            }
            System.out.println();
        }
    }

    public static void main(String[] args) {
        int n = 4;
        int[][] board = new int[n][n];

        if (solveNQueens(board, 0, n)) {
            printBoard(board, n);
        } else {
            System.out.println("No solution exists.");
        }
    }
}
```

## Output:

```
0 1 0 0
0 0 0 1
1 0 0 0
0 0 1 0
```

## Result:

The program successfully implemented and the ouput is verified.
