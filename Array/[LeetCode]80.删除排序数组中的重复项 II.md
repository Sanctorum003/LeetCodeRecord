# 题目 
* 给定一个排序数组，你需要在原地删除重复出现的元素，使得每个元素最多出现两次，返回移除后数组的新长度。

# 题意
如题

# 解法一：快慢指针+标志
```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        int i =0,j=0;
        int idx = 1;
        for(i = 1; i < nums.size();++i)
        {
            if(idx < 2 && nums[i] == nums[j])
            {
                nums[++j] = nums[i];
                idx++;
            }
            else if(nums[i] != nums[j])
            {
                nums[++j] = nums[i];
                idx = 1;
            }
        }
        return nums.empty()?0:j+1;
    }
};
```