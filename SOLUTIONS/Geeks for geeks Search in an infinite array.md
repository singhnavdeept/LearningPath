#BinarySearch 
The thing we know 
	1. The array is sorted (means binary search can be applied )
	2. There is no specific range given so in theory its an infinite array we would not do the thing like array. Length
	3. We have to find range 
Possible solution
=
we will apply binary search then 
we will find range by doubling the size every time 

```JAVA
//function to find the range 
//assume there is abox of lenght 1 and doubled till it contains the range of entire array it will take log(n) steps so we will use this to get range
public int range(int []nums, int target){
	int s=0;
	int e=1;
	while(target<nums[end]){
		int ns=e+1;
		end=end+(end-start+1)*2;
		s=ns;
	}
}
after this all there is a binary search 

```