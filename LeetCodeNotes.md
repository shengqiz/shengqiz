# LeetCode Problems

## 205. Isomorphic Strings 

1.0 First success (1 hr)
Creat hash tables to memorize each corresponding letter for both strings.


```python
class Solution:
    def isIsomorphic(self, s: str, t: str) -> bool:
        s2 = s
        t2 = t
        d = {}
        for i in range(len(s)):
            if s[i] not in d:
                d[s[i]] = t[i]
            s = s[:i] + d[s[i]] + s[i+1:]
        d2= {}
        for i in range(len(s)):
            if t2[i] not in d2:
                d2[t2[i]] = s2[i]

            t2 = t2[:i] + d2[t2[i]] + t2[i+1:]
        return s == t and s2 == t2
```

2.0 Second Try


## 205. Isomorphic Strings

1.0 First success (10 mins)
Use two cursors to go through each strings and see if the cursor for the string can reach the end.
```python
class Solution:
    def isSubsequence(self, s: str, t: str) -> bool:
        cur_s = 0
        cur_t = 0
        
        while cur_s < len(s) and cur_t < len(t):
            if s[cur_s] == t[cur_t]:
                cur_s += 1
                cur_t += 1
            else:
                cur_t += 1
        return cur_s == len(s)
```
2.0 Second Try


## 1. Two Sum
Use hash table to store seen numbers. Using two for loops increases runtime exponentially.
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        seen = {}
        
        for i, num in enumerate(nums):
            remaining = target - num
            
            if remaining in seen:
                return [i, seen[remaining]]
            else:
                seen[num] = i
```

## 88. Merge Sorted Array

1.0 First Try
Simply combine two arrays together from the end and using the built-in sort function.

```python
class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
        """
        Do not return anything, modify nums1 in-place instead.
        """
     
        cur1 = m + n - 1
        cur2 = n - 1
        while cur2 > -1:
            nums1[cur1] = nums2[cur2]
            cur1 -= 1
            cur2 -= 1
        nums1.sort()
        return nums1
```


