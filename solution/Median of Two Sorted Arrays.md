### Median of Two Sorted Arrays

Given two sorted arrays `nums1` and `nums2` of size `m` and `n` respectively, return **the median** of the two sorted arrays.

The overall run time complexity should be `O(log (m+n))`.

 

**Example 1:**

```
Input: nums1 = [1,3], nums2 = [2]
Output: 2.00000
Explanation: merged array = [1,2,3] and median is 2.
```

**Example 2:**

```
Input: nums1 = [1,2], nums2 = [3,4]
Output: 2.50000
Explanation: merged array = [1,2,3,4] and median is (2 + 3) / 2 = 2.5.
```

**Example 3:**

```
Input: nums1 = [0,0], nums2 = [0,0]
Output: 0.00000
```

**Example 4:**

```
Input: nums1 = [], nums2 = [1]
Output: 1.00000
```

**Example 5:**

```
Input: nums1 = [2], nums2 = []
Output: 2.00000
```

 

**Constraints:**

- `nums1.length == m`
- `nums2.length == n`
- `0 <= m <= 1000`
- `0 <= n <= 1000`
- `1 <= m + n <= 2000`
- `-106 <= nums1[i], nums2[i] <= 106`

**solution:**

```javascript
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number}
 */
var findMedianSortedArrays = function(nums1, nums2) {
    let a = nums1.length;
    let b = nums2.length;
    let minArr = a> b ? nums2: nums1;
    let maxArr = a> b ? nums1: nums2;
    let odd = (a+b) %2 != 0 ;
    let middle = (a+b)>>1;
    let newArr = [];
    let index =0;
    let j = 0;
    let k = 0 ;
    let needRange = 1;
    if(a==0){
		newArr = nums2;
        needRange = 0;
	}
	if(b==0){
		newArr = nums1;
         needRange = 0;
	}
    if (needRange) {
        while (index <  middle && newArr.length < (middle+1) ) {
            if(j>=minArr.length){
                for(let l=k;l<middle+1;l++){
                    newArr[newArr.length]=maxArr[l];
                }
                break;
            }
            index = binarySearch(index, maxArr, minArr[j ]);
            if(index==0){
               newArr[newArr.length]=minArr[j];
            }else{
                for(let l=k;l<index;l++){
                    newArr[newArr.length]=maxArr[l];
                }
                newArr[newArr.length]=minArr[j];
                k = index;
            }
            j++;
        }
        
    }
    let ret = odd ? newArr[middle] : (newArr[middle]+newArr[middle-1])/2;
    return ret;
};


function binarySearch( index,  nums,   target) {
    let left = index; 
    let right = nums.length - 1; // 注意
		
    while(left <= right) { // 注意

        let mid =  (right + left) >>1 ;

        if(nums[mid] == target){
            return mid; 
        }else if (nums[mid] < target){
            left = mid + 1;  
        }else if (nums[mid] > target){
            right = mid - 1; // 注意
        }

    }
    return right+1;
}
```

