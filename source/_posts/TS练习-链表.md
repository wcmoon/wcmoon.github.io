---
title: TS练习-链表
date: 2021-04-23 10:39:44
tags:
- TS
- 练习
categories:
- TS
---

## CODE IS EVERYTHING

```typescript
class LinkedNode<T> {
  element: T;
  next: LinkedNode<T> | null;

  constructor(e: T, next?: LinkedNode<T>) {
    this.element = e;
    this.next = next || null;
  }
}

class LinkedList<T> {
  head: LinkedNode<T> | null;
  length: number;

  constructor(head?: LinkedNode<T>, len?: number) {
    this.head = head || null;
    this.length = len || 0;
  }

  find(pos: number):LinkedNode<T> | null {
    if (pos <= 0 || pos > this.length) {
      return null
    }
    let i = 1;
    let cur = this.head;
    while (i < pos) {
      i++;
      cur = cur?.next as LinkedNode<T>;
    }
    return cur;

  }

  insert(node: LinkedNode<T>, pos: number):boolean {
    if (pos === 1) {
      node.next = this.head;
      this.head = node;
      return true;
    }
    let beforeIns:LinkedNode<T> | null = this.find(pos - 1);
    if (beforeIns) {
      node.next = beforeIns?.next || null;
      beforeIns.next = node;
      return true;
    }
    return false;
  }

  del(pos: number):LinkedNode<T> | null {
    let delElement:LinkedNode<T> | null;
    if (pos === 1) {
      delElement = this.head;
      this.head = this.head?.next || null;
      this.length--;
      return delElement;
    }
    let beforeDel = this.find(pos - 1);
    if (beforeDel) {
      delElement = beforeDel.next;
      beforeDel.next = beforeDel?.next?.next || null;
      return delElement;
    }
    return null;
  }

  display() {
    let cur = this.head;
    let output = '';
    while (cur !== null) {
      output = `${output}${cur.element} -- `;
      cur = cur.next;
    }
    console.log(output);
  }
}


let list = ['a', 'b', 'c'];
let nodeListHead = new LinkedNode(list[0]);
let cur = nodeListHead;
for (let i of list.slice(1)) {
  cur.next = new LinkedNode<string>(i);
  cur = cur.next;
}
// 构建链表
let nodeList = new LinkedList(nodeListHead, 3);
nodeList.display();
// 删除测试
nodeList.del(2);
nodeList.display();
// 插入测试
nodeList.insert(new LinkedNode('d'), 3);
nodeList.display();
```

