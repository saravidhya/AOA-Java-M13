# EX 3B Rat in Maze- Backtracking

## AIM:

To write a Java program to for given constraints.
here is a ball in a maze with empty spaces (represented as 0) and walls (represented as 1). The ball can go through the empty spaces by rolling up, down, left or right, but it won't stop rolling until hitting a wall. When the ball stops, it could choose the next direction.

Given the m x n maze, the ball's start position and the destination, where start = [startrow, startcol] and destination = [destinationrow, destinationcol], return true if the ball can stop at the destination, otherwise return false.

You may assume that the borders of the maze are all walls (see examples).
<img width="573" height="573" alt="image" src="https://github.com/user-attachments/assets/d6f1c054-cdc2-4bb3-9c55-512fb2cf0fb7" />
Input: maze = [[0,0,1,0,0],[0,0,0,0,0],[0,0,0,1,0],[1,1,0,1,1],[0,0,0,0,0]], start = [0,4], destination = [4,4]
Output: true
Explanation: One possible way is : left -> down -> left -> down -> right -> down -> right.

## Algorithm

1. Use DFS or BFS starting from the ball’s initial position.
2. From each position, roll the ball **continuously** in all four directions until it hits a wall.
3. Once it stops (just before a wall), treat that stop-position as a new node.
4. If a stop-position has not been visited before, continue exploring from it.
5. If the destination is reached as a _stop-position_, return true; otherwise return false.

#### Developed By: Vidhiya lakshmi S

#### Register Number: 212223230238

## Program:

### to implement rat in the maze

```java
import java.util.*;

public class Main {

    public static boolean hasPath(int[][] maze, int[] start, int[] destination) {
        int m = maze.length;
        int n = maze[0].length;

        boolean[][] visited = new boolean[m][n];
        return dfs(maze, start[0], start[1], destination, visited);
    }

    private static boolean dfs(int[][] maze, int row, int col, int[] dest, boolean[][] visited) {
        if (visited[row][col]) return false;
        if (row == dest[0] && col == dest[1]) return true;

        visited[row][col] = true;

        int[][] dirs = {{1,0}, {-1,0}, {0,1}, {0,-1}};

        for (int[] d : dirs) {
            int r = row;
            int c = col;

            // Roll until hitting a wall
            while (r + d[0] >= 0 && r + d[0] < maze.length &&
                   c + d[1] >= 0 && c + d[1] < maze[0].length &&
                   maze[r + d[0]][c + d[1]] == 0)
            {
                r += d[0];
                c += d[1];
            }

            if (dfs(maze, r, c, dest, visited)) return true;
        }

        return false;
    }

    public static void main(String[] args) {
        int[][] maze = {
            {0, 0, 1, 0, 0},
            {0, 0, 0, 0, 0},
            {0, 0, 0, 1, 0},
            {1, 1, 0, 1, 1},
            {0, 0, 0, 0, 0}
        };

        int[] start = {0, 4};
        int[] dest = {4, 4};

        System.out.println("Can the ball reach the destination? " + hasPath(maze, start, dest));
    }
}
```

## Output:

```
Can the ball reach the destination? true
```

## Result:

The program successfully implemented and the expected output is verified.
