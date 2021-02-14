---
title: leetcode-cn 109.有序链表转换二叉搜索树
date: 2020-08-19 19:17:14
tags:
- leetcode
- 平衡二叉树
categories:
- 算法
img: https://blog-cdn.wcmoon.com/algorithm.jpg
---

## 题目描述
给定一个单链表，其中的元素按升序排序，将其转换为高度平衡的二叉搜索树。
本题中，一个高度平衡二叉树是指一个二叉树每个节点 的左右两个子树的高度差的绝对值不超过 1。

## 示例
给定的有序链表： [-10, -3, 0, 5, 9],

一个可能的答案是：[0, -3, 9, -10, null, 5], 它可以表示下面这个高度平衡二叉搜索树：
```
      0
     / \
   -3   9
   /   /
 -10  5
```

## 解题思路
这题思路还是很明确的，要保证平衡二叉树，最方便的方式就是保持根节点左右两侧节点数量相同或者相差不超过 1，以此规律递归处理
所以问题就转化成了，找到链表的中位节点，然后将两边的节点做重复处理

## 代码
```python
class Solution:
    def sortedListToBST(self, head: ListNode) -> TreeNode:
        def find_mid(left, right):
            slow = fast = left
            while fast != right and fast.next != right:
                slow = slow.next
                fast = fast.next.next
            return slow

        def build_tree(left, right):
            if left == right:
                return None
            mid = find_mid(left, right)
            root = TreeNode(mid.val)
            root.left = build_tree(left, mid)
            root.right = build_tree(mid.next, right)
            return root

        return build_tree(head, None)
```
