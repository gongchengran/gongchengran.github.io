# Leetcode

### Date：12.1

#### 121.买卖股票的最佳时期

Ori: 暴力法会超时

```
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int pro = 0;
        int n = prices.size();
        for(int i = 0; i < n; i++)
        {
            for(int j = i+1; j < n; j++)
            {
                    pro = max(pro, prices[j]-prices[i]);
            }
        }
        return pro;
    }
};
```

动态规划：遍历一遍即可

```
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int maxpro = 0;
        int minpri = int(1e9);
        for(auto price:prices)
        {
            maxpro = max(maxpro,price-minpri);
            minpri = min(minpri, price);
        }
        return maxpro;
    }
};
```



#### 169.多数元素

方法1：Hashtable

```
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        int n = nums.size()/2;
        int res = 0;
        unordered_map<int,int> hash;
        for(auto num:nums)
        {
            ++hash[num];
            if(hash[num]>n)
            {
                res = num;
            }
        }
        return res;
    }
};
```

方法2：排序

```
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        sort(nums.begin(),nums.end());
        return nums[nums.size()/2];
    }
};
```



#### 283.移动零

```
class Solution {
public:
    void moveZeroes(vector<int>& nums) {
		for(int i=0,j=0;i!=nums.size();++i) 
		if(nums[i]) swap(nums[i],nums[j++]);
    }
};
```

