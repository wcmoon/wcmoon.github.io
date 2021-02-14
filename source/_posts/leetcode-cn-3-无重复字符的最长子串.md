---
title: leetcode-cn 3.无重复字符的最长子串
date: 2020-08-19 00:04:24
tags:
- leetcode
- 双指针
categories:
- 算法
img: https://blog-cdn.wcmoon.com/algorithm.jpg
---

## 题目描述
给定一个字符串，请你找出其中不含有重复字符的 最长子串 的长度。
## 示例
示例 1:

输入: "abcabcbb"
输出: 3 
解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。
示例 2:

输入: "bbbbb"
输出: 1
解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。
示例 3:

输入: "pwwkew"
输出: 3
解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。
     请注意，你的答案必须是 子串 的长度，"pwke" 是一个子序列，不是子串。

## 解题思路
用到一个滑动窗口的概念，也可以理解为两个指针的遍历。
设置一个窗口，窗口起始指针 left 和窗口结束指针 right 都从字符串最左侧开始。
设置一个集合来存储当前窗口中的值
遍历开始，right 指针向右遍历，每次遍历的时候，判断当前 right 指针指向的值是否在集合中，若在，则 left 指针向右移动，并更新集合，直到 right 指针指向的值不在集合中，将此时的值放入集合。
每次 right 指针移动完成，判断集合长度，如果大于之前已找到的最大长度，则更新最大长度

## 代码
```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        left = 0
        content = set()
        max_length = 0
        for index, item in enumerate(s):
            while item in content:
                content.remove(s[left])
                left += 1
            content.add(item)
            if index - left + 1 > max_length:
                max_length = index - left + 1
        return max_length
```
