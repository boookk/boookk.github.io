---
title: LinkedList
date: 2022-02-27 00:00:00 +0300
categories: [Learn, Python]
tags: [data structure, python, learn]
---

# 📚 Array와 LinkedList


### <mark style='background-color: #fff5b1'> 차이점 </mark>

| Event | Array | LinkedList|
|:----:|:----:|:----:|
| 특정 원소 조회 | O(1) | O(N) |
| 중간에 원소 삽입 / 삭제 | O(N) | O(1) |
| 정리 | 데이터 접근이 빈번한 경우 사용 | 데이터 변경이 빈번한 경우 사용 |

> Array는 인덱스로 접근이 가능하기 때문에 조회할 때 상수 시간 소요


<br><br>


# 📚 LinkedList 구현
```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None


class LinkedList:
    def __init__(self, value):
        self.head = Node(value)
        self.next = None

    def append(self, value):
        cur = self.head
        while cur.next is not None:
            cur = cur.next
        cur.next = Node(value)

    def all_print(self):
        cur = self.head
        while cur is not None:
            print(cur.data)
            cur = cur.next

    def get_node(self, index):
        node = self.head
        for i in range(1, index):
            node = node.next
        return node

    def add_node(self, index, value):
        new_node = Node(value)
        if index == 0:
            new_node.next = self.head
            self.head = new_node
            return

        node = self.get_node(index - 1)
        next_node = node.next
        node.next = new_node
        new_node.next = next_node

    def delete_node(self, index):
        if index == 0:
            self.head = self.head.next
            return
        node = self.get_node(index - 1)
        node.next = node.next.next
```

<br><br>
