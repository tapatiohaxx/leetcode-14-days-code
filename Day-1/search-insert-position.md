
<h1> Search Insert Position  </h1>
<b> Intro:  </b> In this problem, we are asked to simply make a procedure that finds a target value in an array. An additional codition to this problem is that the algorithm must have the condtraint of being ``O(log(N))`` time complexity.

<h3> My Approach </h3>
The approach I took to this problem is very simple. Since they asked for a `O(log(n))` complexityI decided to utilize the binaary search algorithm. I did make one modification from the original problem at the beginning of today: the default return statement. Instead of returning `-1`, I was forced to return the incremented right value of the array `(right + 1)` because the default condition returns a key of `(1 + right value)` when the value is not in the array
```
EXAMPLE:
Input: nums = [1,3,5,6], target = 7
Output: 4
```  

<h3> The Code </h3> 

```
class Solution {
    public int searchInsert(int[] nums, int target) {
        int last_key = nums.length - 1, first_key = 0, pivot;
        while(first_key <= last_key){
            pivot = first_key + (last_key - first_key) / 2;
            if (nums[pivot] == target) return pivot;
            if(target < nums[pivot] ) last_key = pivot - 1;
            else first_key = pivot + 1;
        }
        return last_key+1;
    }
}
```

<h6> THE TIME AND SPACE COMPLEXITIES ARE THE SAME AS THAT OF BINARY SEARCH SINCE THAT WAS SPECIFIED </h6>
