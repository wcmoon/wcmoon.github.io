---
title: leetcode-cn 1.两数之和
date: 2020-08-14 08:32:21
tags:
- leetcode
- hashmap
categories:
- 算法
img: https://blog-cdn.wcmoon.com/algorithm.jpg
---

## 题目描述

给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。
你可以假设每种输入只会对应一个答案。但是，数组中同一个元素不能使用两遍

## 示例

给定 nums = [2, 7, 11, 15], target = 9
因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]

## 解题思路
暴力两层嵌套循环是最容易想到的办法，但这样的解法时间复杂度至少为 O(n^2)
优化思路主要两个方向
1. 加快检索速度
由于我们最终需要输出的是下标，加快检索速度的话，可以用 hashmap 来存储已经访问过的节点，将数组项的值当作 map 的 key，将下标作为 value
2. 减少重复计算
在使用 hashmap 来存储已经访问过的节点的基础上，减少重复计算变得很好实现。我们只需要一遍遍历 nums，设下标为 i，计算 target - nums[i] 是否是 hashmap 的一个 key 值，如果不是，就将当前节点存储在 hashmap，如果是，问题就解完了。

## 代码
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        dct = {}
        for index, num in enumerate(nums):
            if target - num in dct:
                return [dct[target - num], index]
            dct[num] = index
```

## PS
本系列博客所有题目出自 https://leetcode-cn.com/
