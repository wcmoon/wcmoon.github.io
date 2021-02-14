---
title: leetcode-cn 2.两数相加
date: 2020-08-16 20:49:26
tags:
- leetcode
- 链表
categories:
- 算法
img: https://blog-cdn.wcmoon.com/algorithm.jpg
---

## 题目描述
给出两个 非空 的链表用来表示两个非负的整数。其中，它们各自的位数是按照 逆序 的方式存储的，并且它们的每个节点只能存储 一位 数字。
如果，我们将这两个数相加起来，则会返回一个新的链表来表示它们的和。
您可以假设除了数字 0 之外，这两个数都不会以 0 开头。

## 示例
输入：(2 -> 4 -> 3) + (5 -> 6 -> 4)
输出：7 -> 0 -> 8
原因：342 + 465 = 807

## 解题思路
这道题基本没有什么花里胡哨的解法，直接一遍遍历两个链表，复杂度为O(n)，注意实际编码的时候可以写干净一点

### 代码
```python
class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
        new_head = ListNode(-1)
        node = new_head
        carry = 0
        while l1 or l2:
            x = l1.val if l1 else 0
            y = l2.val if l2 else 0
            val = x + y + carry
            carry = val // 10
            node.next = ListNode(val % 10)
            if l1:
                l1 = l1.next
            if l2:
                l2 = l2.next
            node = node.next
        if carry:
            node.next = ListNode(1)
        return new_head.next
```

### PS
本系列博客所有题目出自 https://leetcode-cn.com/
