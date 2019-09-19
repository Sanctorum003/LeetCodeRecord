# 题目
题目:给定一个数组 nums 和一个值 val，你需要原地移除所有数值等于 val 的元素，返回移除后数组的新长度。
不要使用额外的数组空间，你必须在原地修改输入数组并在使用 O(1) 额外空间的条件下完成。
元素的顺序可以改变。你不需要考虑数组中超出新长度后面的元素。

# 题意
如题

# 方法一:头尾指针
设置两个指针i,j分别指向头和尾.从前向后遍历,如果遇到待删元素,swap(a[i],a[j])并且--J,不然就++i,直到i>j时。
```cpp
class Solution {
public:
    void swap(int &a,int &b)
    {
        int t = a;
        a = b;
        b = t;
    }
    
    int removeElement(vector<int>& nums, int val) {
        int i =0,j = nums.size()-1;
        while(i<=j)
        {
            if(nums[i] == val)
            {
                swap(nums[i],nums[j]);
                --j;
            }
            else
            {
                ++i;
            }
        }
        return i;
    }
};
```

# 方法二:快慢指针
设置两个指针i,j,对i进行循环,遇到不删除的元素复制到nums[i]。
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        int i = 0;
        int j = 0;
        for(j = 0; j < nums.size();++j)
        {
            if(nums[j] != val)
            {
                nums[i] = nums[j];
                i++;
            }
        }
        return i;
    }
};
