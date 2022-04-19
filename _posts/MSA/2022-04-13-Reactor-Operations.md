---
title: "Reactor Operations"
date: 2022-04-13 23:00:00 +0900
categories: [MSA]
tags: [msa, spring, reactor, reactive]
---

## 🧶 생성

### <mark style='background-color: #f1f8ff'> Create </mark>

![image](https://user-images.githubusercontent.com/76933244/163540036-dcc17a9a-3a3c-425b-a0ce-e0214d02d57a.png){: w="500"}
_https://reactivex.io/_

- Observable 생성

### <mark style='background-color: #f1f8ff'> Just </mark>

![image](https://reactivex.io/documentation/operators/images/just.c.png){: w="500"}
_https://reactivex.io/documentation/operators/just.html_

- 하나의 item만 방출(emit)하는 observable 생성

### <mark style='background-color: #f1f8ff'> From </mark>

![image](https://reactivex.io/documentation/operators/images/from.c.png){: w="500"}
_https://reactivex.io/documentation/operators/from.html_

- 다양한 객체와 데이터 유형을 observable로 변환
- e.g. 리스트를 Flux로 변환

### <mark style='background-color: #f1f8ff'> Empty </mark>

![image](https://reactivex.io/documentation/operators/images/empty.c.png){: w="500"}
_https://reactivex.io/documentation/operators/empty-never-throw.html_

- 빈 observable 생성

### <mark style='background-color: #f1f8ff'> Defer </mark>

![image](https://reactivex.io/documentation/operators/images/defer.c.png){: w="500"}
_https://reactivex.io/documentation/operators/defer.html_

- observer가 구독할 때까지 observable을 생성하지 않고, 각 observer에 대해 새로운 observable 생성

<br>

## 🔮 변환

### <mark style='background-color: #f1f8ff'> flatMap </mark>

![image](https://reactivex.io/documentation/operators/images/flatMap.c.png){: w="500"}
_https://reactivex.io/_

> 비동기 처리
{: .prompt-tip }

### <mark style='background-color: #f1f8ff'> groupBy </mark>

![image](https://reactivex.io/documentation/operators/images/groupBy.c.png){: w="500"}
_https://reactivex.io/_

- Obsevable을 기준에 따라 그룹으로 obsevable 방출

### <mark style='background-color: #f1f8ff'> map </mark>

![image](https://user-images.githubusercontent.com/76933244/163541362-d3e5610f-5969-4d2c-9342-2ae444d20331.png){: w="500"}
_https://reactivex.io/_

> 동기 처리
{: .prompt-tip }

> 입력과 리턴 값은 `Mono<T>`
{: .prompt-warning }

<br>

## 🔊 필터

### <mark style='background-color: #f1f8ff'> distinct </mark>
- 중복을 없앤 observable 반환

### <mark style='background-color: #f1f8ff'> filter </mark>
- 조건에 만족하는 항목만 방출

### <mark style='background-color: #f1f8ff'> elementAt </mark>

![image](https://user-images.githubusercontent.com/76933244/163542099-ed60f277-90bd-4758-9d94-9f65af4ab3a4.png){: w="500"}
_https://reactivex.io/_

- Flux에서 i번째 요소를 Mono로 반환

### <mark style='background-color: #f1f8ff'> ignoreElements </mark>

![image](https://reactivex.io/documentation/operators/images/ignoreElements.c.png){: w="500"}
_https://reactivex.io/_

- Observable의 항목을 내보내지 않고 종료 알림 발생
- Observable을 사용하지 않고 종료할 때 이용
- onNext 핸들러가 호출되지 않는다.

### <mark style='background-color: #f1f8ff'> take </mark>

![image](https://user-images.githubusercontent.com/76933244/163542783-c04373dc-52c8-45a4-968b-bfe6f5c22728.png){: w="500"}
_https://reactivex.io/_

- 앞에서 n개의 요소 방출

<br>

## 🧩 결합

### <mark style='background-color: #f1f8ff'> merge </mark>

![image](https://user-images.githubusercontent.com/76933244/163543629-f8aefccf-a26b-4b5d-b19b-7677ce44eb21.png){: w="500"}
_https://reactivex.io/_

- 여러 observable을 합쳐서 하나의 observable 반환

### <mark style='background-color: #f1f8ff'> startWith </mark>

![image](https://user-images.githubusercontent.com/76933244/163543514-8ffaaed0-f632-4222-8f3c-702b3d305041.png){: w="500"}
_https://reactivex.io/_

- Observable의 항목을 방출하기 전에 지정된 항목을 추가

### <mark style='background-color: #f1f8ff'> zip </mark>

![image](https://user-images.githubusercontent.com/76933244/163543582-3d74a050-c646-4fcc-8afb-03ac28aa6a01.png){: w="500"}
_https://reactivex.io/_

- 여러 observable의 방출을 결합하여 하나의 observable로 방출

<br>

## 📍 오류 처리

### <mark style='background-color: #f1f8ff'> onErrorResume </mark>

![image](https://reactivex.io/documentation/operators/images/Catch.png){: w="500"}
_https://reactivex.io/_

- error 신호 처리

> try-catch 문에서 catch와 유사
{: .prompt-tip }

### <mark style='background-color: #f1f8ff'> retry </mark>

![image](https://reactivex.io/documentation/operators/images/retry.C.png){: w="500"}
_https://reactivex.io/_

- error 신호가 발생하면 다시 실행

<br>

## 🎮 유틸리티

### <mark style='background-color: #f1f8ff'> delay </mark>
- Observable에서 방출 시점을 특정 시간만큼 앞으로 이동

### <mark style='background-color: #f1f8ff'> do </mark>

![image](https://reactivex.io/documentation/operators/images/do.c.png){: w="500"}
_https://reactivex.io/_

- 원본 시퀀스에 영향을 주지 않고 처리 로직 추가
- 주로 시퀀스의 신호를 잡아서 사용
- e.g. doOnNext, doOnComplete, doOnError 등

### <mark style='background-color: #f1f8ff'> serialize </marK>

![image](https://reactivex.io/documentation/operators/images/serialize.c.png){: w="500"}
_https://reactivex.io/_

- Observable이 직렬화된 호출을 수행하고 올바르게 작동하도록 강제

### <mark style='background-color: #f1f8ff'> subscribe </mark>
- Observable 방출 및 알림에 따라 작동
- e.g. onNext, onError, onComplete

> 구독하지 않은 Observable은 처리되지 않는다.
{: .prompt-warning }

### <mark style='background-color: #f1f8ff'> timestamp </mark>

![image](https://reactivex.io/documentation/operators/images/timestamp.c.png){: w="500"}
_https://reactivex.io/_

- 각 항목에 타임스탬프 추가

<br>

## 🔎 조건

### <mark style='background-color: #f1f8ff'> all </mark>

![image](https://user-images.githubusercontent.com/76933244/163544748-2a3ada34-5720-455c-a84c-18313b852410.png){: w="500"}
_https://reactivex.io/_

- Observable이 내보낸 모든 항목이 조건을 만족하는지 여부 반환

### <mark style='background-color: #f1f8ff'> contains </mark>

![image](https://user-images.githubusercontent.com/76933244/163544940-88b59655-82c9-419c-9c00-15f60e3c22bc.png){: w="500"}
_https://reactivex.io/_

- Observable이 특정 항목을 방출하는지 여부 반환

### <mark style='background-color: #f1f8ff'> defaultIfEmpty </mark>

![image](https://reactivex.io/documentation/operators/images/defaultIfEmpty.c.png){: w="500"}
_https://reactivex.io/_

- Observable이 아무것도 방출하지 않을 때 특정 항목 반환

### <mark style='background-color: #f1f8ff'> skipWhile </mark>

![image](https://reactivex.io/documentation/operators/images/skipWhile.c.png){: w="500"}
_https://reactivex.io/_

- 조건을 만족하지 않을 때까지 방출된 항목 무시

### <mark style='background-color: #f1f8ff'> takeWhile </mark>

![image](https://reactivex.io/documentation/operators/images/takeWhile.c.png){: w="500"}
_https://reactivex.io/_

- 조건을 만족하지 않은 후 observable이 내보낸 항목 무시

<br>

## 📝 집계

### <mark style='background-color: #f1f8ff'> average </mark>
- 뒤에 자료형을 붙여서 사용
- 평균을 Mono로 반환

### <mark style='background-color: #f1f8ff'> count </mark>
- 조건을 만족하는 item의 개수를 카운팅하여 Mono로 반환

### <mark style='background-color: #f1f8ff'> max </mark>
- 최댓값

### <mark style='background-color: #f1f8ff'> min </mark>
- 최솟값

### <mark style='background-color: #f1f8ff'> sum </mark>
- 합

### <mark style='background-color: #f1f8ff'> reduce </mark>

![image](https://user-images.githubusercontent.com/76933244/163546012-c3bef04f-761b-4828-b5ee-1aab36302c79.png){: w="500"}
_https://reactivex.io/_

- 시퀀스의 각 item에 함수를 순차적으로 적용하고 최종 값 반환

<br>
