<h1> First Bad Version </h1> 

<h6> Intro: </h6> In this problem we are asked to make a procedure script that uses an API to check for the first bad version of a product. All that we are given is that there are ` n ` versions of the product and that the latest version is bad. 

<h3> My Approach </h3> 
I struggled to find an approach at first, but I realized one thing as I thought about it. I realized that n will be the amount of versions and that some version within that may be the first. TO achieve this, along with using API calls, we could use a modified version of binary search from the previous problem. You may refer to the previous ` binary-search.md ` for an explanation of that algorithm. As for this use of the concept, we declare the beginning of the array (` first `) to 1 and the end (` last `) to ` n `. In the spirit of binary search we make the same initial mid value too. 
` mid = first + (last - first) /2
`
Using this initial value, we can safely say that if the middle value is bad we can go less than that and if not we have to go higher. 

```java
if (isBadVersion(mid))
   last = mid;
else
   first = mid + 1;
```

We will find at the end that the leftmost value of the final array will be the value we want.

<h3> The Code: </h3>

```java
public class Solution extends VersionControl {
    public int firstBadVersion(int n) {
        int firstt = 1, last = n;
    	while (left < right) {
        	int mid = first + (last - first) / 2;
        	if (isBadVersion(mid))
        	    last = mid;
        	else 
            		firstt = mid + 1;
       
    	}
    	return first;
    }
} 
``` 

<h3> Time and Space Complexity </h3> 
Just as we saw for the binary search algorithm, the time and space complexities for this algorithm will be <h6> <i> O </i>(N) = O(log(N) </h6> and <h6> O(N) = O(1) </h6> respectively. 
