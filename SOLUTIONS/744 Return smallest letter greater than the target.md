arr=["] a character array sorted in a  non decreasing order
the root concept of this is similar to ceil 
just return the start 
as we know we dont need the equal parts so we dont need the == condition 
```java

public char nextGreatestLetter(char[] letters, char target){
	int s=0;
	int e=letters.length-1;
	while(s<=e){
		int mid= s+(e-s)/2;
		if(target<letters[mid]){
		end=mid-1;
		}
		else{start =mid+1;}
	}
	return letters[start%letters.length];
}

```