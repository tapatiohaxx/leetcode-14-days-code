<h1> Binary Search </h1>

<b> Intro:  </b>  Binary searh is one of the major algorithms you will learn in an algorithms class. It is quick and simple to create. All that you have to know about the algorithm is that you have to divide the collection of items into two sets and find the set with the numbers closest to the number you are given.

<h3> My Approach </h3>
   When I began this problem, I figured that using Java would more than suffice. With Java, we can start off with a class that looks like the following:

```
class Solution{
   public int search(int[] nums, int target) {
   } 
}
``` 
Seeing this, I managed to think of setting up myself first. I did this by initializing variables called ` first_key ` and ` last_key `  as well as ` pivot `. The logic here is that the first key will start at the front of the array and the last key will be at the end of the array. Using this logic, each time the program runs on the aray the keys will change by half of the array until the first key is greater than the last key.

That being said, if `target` is less than the middlemost value, the array will be truncated to the first half, including the center value. The reverse is true for when the `target` is greater than the middle value.

An important question you may have is how to calculate the midlemost index. Well, to do this, we initially use the algorithm

```
first + last/2
```  
In cases where the array is a truncated version of the array in ` nums `, we modify this approach a a bit. We calculate the difference between the last index and the first index and add the result to the the first index and divide that result by 2:

```
pivot = first + (last - first)/2
``` 

Tjis is all that we need to know to solve this problem! Now we can put it all together.

<h3> Our Code </h3> 

Before putting all of the code together, let me state the default returrn value in this case. LeetCode says that the default return value if the ` target ` is not in the array is ` -1 `.

With that all said and done, here is the final code.

```
class Solution {
    public int search(int[] nums, int target){
        int last_key = nums.length - 1, first_key = 0, pivot;
        while(first_key <= last_key){
            pivot = first_key + (last_key - first_key) / 2;
            if (nums[pivot] == target) return pivot;
            if(target < nums[pivot] ) last_key = pivot - 1;
            else first_key = pivot + 1;
        }
        return -1;
    }
}
```

<h3> Code Analysis </h3>

When we look at this binary search code in terms of operations done and time taken, we find two things. We first finds that it splits the list into two parts eaach time it runs and it relies on tracking to the midpoint of the array each time. This means that the algorithm is logarithmic in nature of time complexity. It is also a simple logarithmic process because nothing too complex is happening.
<h5> <i> O </i> (N) = log(N) </h5> 

The space complexity of this problem is constant since the space taken up by the things it generates does not scale up.

<h5> <i> O </i>(N) = 1
