---
title: "Queue"
date: 2022-02-27 00:00:00 +0300
categories: [Learn, Python]
tags: [data structure, python, learn]
---

# 📚 Queue 구현


### <mark style='background-color: #fff5b1'> 기능 </mark>

| Event | Description |
|:----:|:----:|
| enqueue(data) | 맨 뒤에 데이터 추가하기 |
| dequeue() | 맨 앞의 데이터 뽑기 |
| peek() | 맨 앞의 데이터 보기 |
| isEmpty() | 큐의 사용 여부 반환 |

> FIFO
{: .prompt-tip }


<br>

### <mark style='background-color: #fff5b1'> 구현 </mark>
```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None


class Queue:
    def __init__(self):
        self.head = None
        self.tail = None

    def enqueue(self, data):
        new_node = Node(data)
        if self.isEmpty():
            self.head = new_node
            self.tail = new_node
            return
        self.tail.next = new_node
        self.tail = new_node

    def dequeue(self):
        if self.isEmpty():
            return "Queue is Empty"
        node = self.head
        self.head = self.head.next
        return node.data

    def peek(self):
        if self.isEmpty():
            return "Queue is Empty"
        return self.head.data

    def isEmpty(self):
        return self.head is None
```

<br><br>
