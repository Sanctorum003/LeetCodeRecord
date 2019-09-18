# 题目
给定一个未排序的整数数组，找出其中没有出现的最小的正整数。

# 题意
如题

# 解法一：
从左往右遍历一遍
1.如果nums[i] > 0,将i与nums[i]-1的数字交换，如果nums[nums[i]-1] < 0 则改为-1，并且++i。不然重新判断i
2.如果nums[i] <= 0 或者 nums[i] >= nums.size(),则改为-1，并且++i。
拿样例举例
[1,2,0] -> [1,2,-1]
[3,4,-1,1] -> [-1,4,3,1]->[-1,1,3,4]->[1,-1,3,4]
[7,8,9,11,12]->[-1,-1,-1,-1,-1]
这样再从左往右遍历,遇到的第一个-1所在的位置i,结果即为i+1。如果没有-1，则为num.size()+1

```cpp
class Solution {
public:
    int firstMissingPositive(vector<int>& nums) {
        int i = 0;
        while(i<nums.size()) 
        {
            if(nums[i] > 0 && nums[i] <= nums.size())
            {
                if(nums[i] != i+1)
                {
                    int idx = nums[i];
                    int tmp = nums[idx-1];
                    nums[idx-1] = idx;
                    if(tmp != nums[i] && tmp > 0)
                    {
                        nums[i] = tmp;
                    }
                    else
                    {
                        nums[i] = -1;
                        i++;
                    }   
                }
                else
                {
                    i++;
                    //cout<<i<<endl;
                }

            }
            else
            {
                nums[i] = -1;
                ++i;
            }
        }
        for(int j = 0; j < nums.size();++j)
            if(nums[j] == -1)
                return j+1;
        return nums.size()+1;
    }
};
```
# 解法二：
对上述进行优化
```cpp
class Solution {
public:
    int firstMissingPositive(vector<int>& nums) {
        for(int i=0; i<nums.size();++i)
        {
            //nums[i] != nums[nums[i]-1] 防止如[1,1]进入死循环
            //注意用while
            while(nums[i]>0 && nums[i] <= nums.size() && nums[i] != i+1 && nums[i] != nums[nums[i]-1])
            {
                swap(nums[i],nums[nums[i]-1]);
            }
        }
        
        for(int i = 0; i < nums.size();++i)
            if(nums[i] != i+1)
                return i+1;
        
        return nums.size()+1;
    }
};
```

