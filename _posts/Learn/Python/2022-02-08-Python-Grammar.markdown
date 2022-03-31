---
title: "Python 문법"
date: 2022-02-08 00:00:00 +0300
categories : [Learn, Python]
tags: [python, learn]
---

# 📚 리스트

### <mark style='background-color: #fff5b1'> 컴프리헨션 </mark>
대괄호 안에 조건문과 반복문을 적용하여 리스트를 초기화하는 방법
```python
a = [i for i in range(5)]
```

<br>

### <mark style='background-color: #fff5b1'> 리스트에서 특정 값을 가지는 원소를 모두 제거하기 </mark>
```python
arr = [1, 1, 2, 2, 3]
search = {1, 2}

# arr에 1, 2를 제외한 값만 저장
res = [a for a in arr if a not in search]
```

<br>

### <mark style='background-color: #fff5b1'> 리스트 관련 메서드의 시간 복잡도 </mark>

| 함수명 | 시간 복잡도 |
|:----:|:----:|
| append() | O(1) |
| sort() | O(NlogN) |
| reverse() | O(N) |
| insert() | O(N) |
| count() | O(N) |
| remove() | O(N) |

<br><br>


# 📚 튜플
### <mark style='background-color: #fff5b1'> 특징 </mark>
- 튜플은 한 번 선언된 값을 변경할 수 없다.
- 튜플은 리스트에 비해 상대적으로 공간 효율적이다.
- 튜플을 비롯하여 리스트는 순서가 존재한다.

<br>

### <mark style='background-color: #fff5b1'> 튜플은 사용하면 좋은 경우 </mark>
- 서로 다른 성질의 데이터를 묶어서 관리해야 하는 경우
- 메모리를 효율적으로 사용해야 하는 경우

<br><br>


# 📚 집합
### <mark style='background-color: #fff5b1'> set() </mark>
- 중복을 허용하지 않는다.
- 순서가 존재하지 않는다.
- 사전 자료형과 집합 자료형은 순서가 없기 때문에 검색할 때 O(1)의 시간 복잡도를 가진다.

<br>

### <mark style='background-color: #fff5b1'> 집합 자료형 연산 </mark>
```python
s1 = {1, 2, 3}
s2 = {3, 4}

# 합집합
print(s1 | s2)
print(s2.union(s1))

# 교집합
print(s1 & s2)
print(s1.intersection(s2))

# 합집합
print(s1 - s2)
print(s1.difference(s2))
```

<br><br>


# 📚 함수
### <mark style='background-color: #fff5b1'> eval() </mark>
```python
# 문자열 형태의 식을 계산해주는 함수
print(eval("2+3"))
```
<mark style='background-color: #ffdce0'> 만약, 피연산자 앞에 0이 붙어 있는 경우, 오류가 발생한다. </mark> (Ex. 1+01)

<br><br>


# 📚 라이브러리

### <mark style='background-color: #fff5b1'> itertools </mark>
```python
# 순열 : 서로 다른 n개에서 서로 다른 r개를 선택하여 나열
from itertools import permutations

# 조합 : 서로 다른 n개에서 순서와 상관 없이 서로 다른 r개 선택
from itertools import combinations

# 중복 순열 : 중복 가능한 n개에서 r개를 선택하여 나열
from itertools import product

# 중복 조합 : 중복 가능한 n개에서 순서와 상관 없이 r개 선택
from itertools import combinationswith_replacement
```

<br>

### <mark style='background-color: #fff5b1'> collections </mark>
```python
# 카운팅
from collections import Counter

a = ['apple', 'banana', 'apple']
counter = Counter(a)

# 업데이트
counter.update(a)

# 가장 빈도가 높은 순으로 n개 출력
print(counter.most_common(n))
```

```python
# 큐 구현
# 리스트를 사용하는 경우보다 효율성이 높다.
from collections import deque

queue = deque()

queue.append(1)
queue.popleft()
```
