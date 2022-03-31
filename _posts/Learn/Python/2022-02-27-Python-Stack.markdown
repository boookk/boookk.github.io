---
title: "Stack"
date: 2022-02-27 00:00:00 +0300
categories: [Learn, Python]
tags: [data structure, python, learn]
---

# 📚 Stack 구현


### <mark style='background-color: #fff5b1'> 기능 </mark>

| Event | Description |
|:----:|:----:|
| push(data) | 맨 앞에 데이터 넣기 |
| pop() | 맨 앞의 데이터 뽑기 |
| peek() | 맨 앞의 데이터 보기 |
| isEmpty() | 스택의 사용 여부 반환 |

> LIFO


<br>

### <mark style='background-color: #fff5b1'> 구현 </mark>
```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None


class Stack:
    def __init__(self):
        self.head = None

    def push(self, item):
        new_head = Node(item)
        new_head.next = self.head
        self.head = new_head

    def pop(self):
        if self.isEmpty():
            return "Stack is Empty"
        item = self.head
        self.head = self.head.next
        return item

    def peek(self):
        if self.isEmpty():
            return "Stack is Empty"
        return self.head.data

    def isEmpty(self):
        return self.head is None
```

<br><br>
