[215. Kth Largest Element in an Array](https://leetcode-cn.com/problems/kth-largest-element-in-an-array/)

```cpp
class Solution {
public:
	int findKthLargest(vector<int>& nums, int k) {
		int len = nums.size();
		int low = 0, high = len - 1,index;
		while (true) {
            index=partition(nums,low,high);
            if (index == len - k) {
			    return nums[index];
		    }
            else if(index>len-k){
                high=index-1;
            }
            else{
                low=index+1;
            }
		}
	}

	int partition(vector<int>&nums, int l, int r) {
		int i = l, j = r, temp = nums[l];
		while (i < j) {
			while (i < j&&nums[j] >= temp) { j--; }
			if (i<j) {
				nums[i] = nums[j];
			}
			while (i < j&&nums[i] <= temp) { i++; }
			if (i<j) {
				nums[j] = nums[i];
			}
		}
        nums[i] = temp;
        return i;
	}
};
```
