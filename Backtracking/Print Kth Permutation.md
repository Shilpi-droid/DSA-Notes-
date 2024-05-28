[[Print All Permutations]]
Given two ****integers N and K****, find the Kth permutation sequence of numbers from 1 to N without using STL function.  
__Note: Assume that the inputs are such that Kth permutation of N number is always possible.__

****Examples:**** 

> ****Input:**** N = 3, K = 4   
> ****Output:**** 231   
> ****Explanation:****   
> The ordered list of permutation sequence from integer 1 to 3 is : 123, 132, 213, 231, 312, 321. So, the 4th permutation sequence is “231”.
> 
> ****Input:**** N = 2, K = 1   
> ****Output:**** 12   
> Explanation:   
> For n = 2, only 2 permutations are possible 12 21. So, the 1st permutation sequence is “12”.
### Code

```java
// Java program to Find the kth Permutation
// Sequence of first n natural numbers
import java.util.*;

class GFG {
	// Driver code
	public static void main(String[] args)
	{
		int n = 3, k = 4;
		String kth_perm_seq = findKthPermutation(n, k);

		// function call
		System.out.println(kth_perm_seq);
	}

	static char[] swap(String s, int i, int j)
	{
		char[] ch = s.toCharArray();
		char temp = ch[i];
		ch[i] = ch[j];
		ch[j] = temp;
		return ch;
	}

	// recursive function to generate all
	// possible permutations of a string
	static void generate_permutations(String str, int idx,
									List<String> result)
	{
		// base case
		if (idx == str.length()) {
			result.add(str);
			return;
		}

		// traverse string from idx to end
		for (int i = idx; i < str.length(); i++) {
			str = new String(swap(str, i, idx));
			generate_permutations(str, idx + 1, result);
			str = new String(swap(str, i, idx));
		}
	}

	// Function to find the
	// kth permutation of n numbers
	static String findKthPermutation(int n, int k)
	{
		String str = "";
		List<String> result = new ArrayList<String>();

		// Insert all natural number
		// upto n in string
		for (int i = 1; i <= n; i++) {
			str += i;
		}
		generate_permutations(str, 0, result);

		// sort the generated permutations
		Collections.sort(result);

		// make k 0-based indexed to point to kth sequence
		return result.get(k - 1);
	}
}

// This code is contributed by Tapesh(tapeshdua420)

```
