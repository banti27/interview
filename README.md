# interview

## Permutations

### Given a set of distinct numbers, find all of its permutations.

Permutation is defined as the re-arranging of the elements of the set. For example, {1, 2, 3} has the following six permutations:

1. {1, 2, 3}
1. {1, 3, 2}
1. {2, 1, 3}
1. {2, 3, 1}
1. {3, 1, 2}
1. {3, 2, 1}

If a set has ‘n’ distinct elements it will have n! permutations.

#### Example 1: 

```
Input: [1,3,5]
Output: [1,3,5], [1,5,3], [3,1,5], [3,5,1], [5,1,3], [5,3,1]
```

#### Solve:

```
import java.util.*;

class Permutations {

  public static List<List<Integer>> findPermutations(int[] nums) {
    List<List<Integer>> result = new ArrayList<>();
    // TODO: Write your code here
    return result;
  }

  public static void main(String[] args) {
    List<List<Integer>> result = Permutations.findPermutations(new int[] { 1, 3, 5 });
    System.out.print("Here are all the permutations: " + result);
  }
}
```
***


## Triplet Sum to Zero 

### Given an array of unsorted numbers, find all unique triplets in it that add up to zero.

#### Example 1: 

```
Input: [-3, 0, 1, 2, -1, 1, -2]
Output: [-3, 1, 2], [-2, 0, 2], [-2, 1, 1], [-1, 0, 1]
Explanation: There are four unique triplets whose sum is equal to zero.
```

#### Example 2: 

```
Input: [-5, 2, -1, -2, 3]
Output: [[-5, 2, 3], [-2, -1, 3]]
Explanation: There are two unique triplets whose sum is equal to zero.
```

#### Solve:

```
import java.util.*;

class TripletSumToZero {

  public static List<List<Integer>> searchTriplets(int[] arr) {
    List<List<Integer>> triplets = new ArrayList<>();
    // TODO: Write your code here
    return triplets;
  }
}
```
***


## Permutation in a String

### Given a string and a pattern, find out if the string contains any permutation of the pattern.

Permutation is defined as the re-arranging of the characters of the string. For example, “abc” has the following six permutations:

1. abc
1. acb
1. bac
1. bca
1. cab
1. cba

If a string has ‘n’ distinct characters, it will have n! permutations.

#### Example 1: 
```
Input: String="oidbcaf", Pattern="abc"
Output: true
Explanation: The string contains "bca" which is a permutation of the given pattern.
```

#### Example 2: 
```
Input: String="odicf", Pattern="dc"
Output: false
Explanation: No permutation of the pattern is present in the given string as a substring.
```


#### Example 3: 
```
Input: String="bcdxabcdy", Pattern="bcdyabcdx"
Output: true
Explanation: Both the string and the pattern are a permutation of each other.
```


#### Example 2: 
```
Input: String="aaacb", Pattern="abc"
Output: true
Explanation: The string contains "acb" which is a permutation of the given pattern.
```



#### Solve:
```
import java.util.*;

class StringPermutation {
  public static boolean findPermutation(String str, String pattern) {
    // TODO: Write your code here
    return false;
  }
}

```






