# 题目
给定一个排序数组，你需要在原地删除重复出现的元素，使得每个元素只出现一次，返回移除后数组的新长度。

# 题意
如题

# 方法一：快慢指针
## 我的写法
```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {        
        if(nums.size() == 0 ) return nums.size();
        
        int i = 1;
        int j = 1;
        
        int pre  = nums[0];
        for(i = 1; i < nums.size();++i)
        {
            if(pre != nums[i])
            {
                nums[j] = nums[i];
                j++;
               
            }
            
            pre = nums[i];
        }
        
        return j;
    }
};
```
## 优雅写法
```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        int i =0, j = 0;
        for(i = 0; i < nums.size();++i)
        {
            if(nums[i] != nums[j]) 
            {
                nums[++j] = nums[i];
            }
        }
        //注意vector位空的情况
        return nums.empty()?0:j+1;
    }
};
```
