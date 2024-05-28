[[Matrix Based Problems]]
Given a 2D matrix of dimension ****m✕n,**** the task is to print all the possible paths from the ****top left**** corner to the ****bottom right**** corner in a 2D matrix with the constraints that from each cell you can either move to right or down only.

## Code:
```java
import java.util.ArrayList;
import java.util.List;

public class MatrixPaths {
	// To store the matrix dimensions
	static int M, N;

	// Function to print the path taken to reach the destination
	static void printPath(List<Integer> path) {
		for (int i : path) {
			System.out.print(i + ", ");
		}
		System.out.println();
	}

	// Function to find all possible paths in the matrix from the top-left cell to the bottom-right cell
	static void findPaths(int[][] arr, List<Integer> path, int i, int j) {
		// If it's the bottom-right cell, print the path
		if (i == M - 1 && j == N - 1) {
			path.add(arr[i][j]);
			printPath(path);
			path.remove(path.size() - 1);
			return;
		}

		// Boundary cases: Check if we are out of the matrix
		if (i < 0 || i >= M || j < 0 || j >= N) {
			return;
		}

		// Include the current cell in the path
		path.add(arr[i][j]);

		// Move right in the matrix
		if (j + 1 < N) {
			findPaths(arr, path, i, j + 1);
		}

		// Move down in the matrix
		if (i + 1 < M) {
			findPaths(arr, path, i + 1, j);
		}

		// Backtrack: Remove the current cell from the current path
		path.remove(path.size() - 1);
	}
}

```