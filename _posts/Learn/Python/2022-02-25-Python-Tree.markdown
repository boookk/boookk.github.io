---
title: "트리 자료구조"
date: 2022-02-25 00:00:00 +0300
categories: [Learn, Python]
tags: [data structure, python, learn]
---

# 📚 Tree

계층적인 구조를 표현할 때 사용하는 자료구조


### <mark style='background-color: #fff5b1'> 트리 관련 용어 </mark>

| 명칭 | 의미 |
|:----:|:----:|
| 루트 노드 (root node) | 부모가 없는 최상위 노드 |
| 단말 노드 (leaf node) | 자식이 없는 노드 |
| 크기 (size) | 트리에 포함된 모든 노드의 개수 |
| 깊이 (depth) | 루트 노드부터의 거리 |
| 높이 (height) | 깊이 중 최댓값 |
| 차수 (degree) | 각 노드의 (자식 방향) 간선 개수 |


<br><br>


# 📚 트리의 순회
- 트리 자료구조에 포함된 노드를 특정한 방법으로 한 번씩 방문하는 방법

### <mark style='background-color: #fff5b1'> 전위 순회 </mark> (Pre-order traverse)
```python
def preorderTraversal(node):
  print(node)
  if node.left: preorderTraversal(node.left)
  if node.right: preorederTraversal(node.right)
```

<br>

### <mark style='background-color: #fff5b1'> 중위 순회 </mark> (In-order traverse)
```python
def inorderTraversal(node):
  if node.left: inorderTraversal(node.left)
  print(node)
  if node.right: inorderTraversal(node.right)
```

<br>

### <mark style='background-color: #fff5b1'> 후위 순회 </mark> (Post-order traverse)
```python
def postorderTraversal(node):
  if node.left: postorderTraversal(node.left)
  if node.right: postorderTraversal(node.right)
  print(node)
```

<br><br>
