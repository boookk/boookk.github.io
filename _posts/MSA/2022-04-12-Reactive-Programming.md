---
title: "Reactive Programming"
date: 2022-04-12 23:00:00 +0900
categories: [MSA]
tags: [msa]
---

## ❓ Reactive System
> 응답이 잘 되고, 탄력적이며 유연하고 메시지 기반으로 동작하는 시스템
{: .prompt-tip }

<br>

## 📜 리액티브 선언문
- 유연하고, 느슨한 결합을 가지며, 확장성이 있다.
- 이로 인해 개발 및 변경 사항을 적용하기 쉽다.
- 장애가 발생하더라도, 간단한 방식으로 해결한다.
- 높은 응답성을 가지며, 사용자에게 효과적인 상호적 피드백을 제공한다.

<br>

## 🔎 Reactive System 특징

### <mark style='background-color: #f1f8ff'> Responsive </mark> (응답성)
- 요청에 대해 시스템은 가능한 즉각적으로 응답해야 한다.

### <mark style='background-color: #f1f8ff'> Resilient </mark> (탄력성)
- 장애가 발생하더라도 응답성을 유지한다.

### <mark style='background-color: #f1f8ff'> Elastic </mark> (유연성)
- 사용량의 변화에 대해 유연하게 대응한다.

### <mark style='background-color: #f1f8ff'> Message Driven </mark> (메시지 구동)
- 탄력성을 유지하기 위해 비동기 메시지 전달에 의존하여 구성 요소 사이에서 경계 형성

<br>

## ❓ Reactive Programming
> 데이터의 흐름과 변화의 전파에 중점을 둔 프로그래밍 패러다임
{: .prompt-tip }

- 기존의 명령형 프로그래밍은 작성한 코드의 순서대로 진행된다.
- 리액티브 프로그래밍은 데이터의 흐름을 정의하면 데이터의변화 혹은 작업의 종료에 따라 반응하여 진행된다.
- 데이터 흐름을 따라 하위 로직에 자동으로 변화를 전파할 수 있어야 한다.

<br>

## 📋 Reactive Programming 주요 요소

![image](https://user-images.githubusercontent.com/76933244/163134897-af6dfb51-4f54-4855-9015-9f0dfba7d696.png)
_https://reactivex.io/_

### <mark style='background-color: #f1f8ff'> Observable </mark>
- `데이터 스트림`
- 데이터 압축, 방출하는 역할

### <mark style='background-color: #f1f8ff'> Observers </mark>
- Observable을 구독하고 방출된 데이터 스트림을 받아서 처리하는 역할

### <mark style='background-color: #f1f8ff'> Schedulers </mark>
- 비동기 프로그래밍을 위한 요소
- Observable과 Observers에게 실행되어야 할 스레드를 알려주는 역할

<br>

## 📊 Marble Diagram

![image](https://user-images.githubusercontent.com/76933244/163000202-b90f7613-688c-4d8a-99f5-6a3aad05b333.png)
_https://reactivex.io/_

> Reactive Programming을 통해 발생하는 비동기적인 데이터 흐름을 시간에 따라 시각화한 다이어그램
{: .prompt-tip }

<br>

## ❓ Reactive Stream
> Nonblocking [Backrpessure](https://www.reactivemanifesto.org/ko/glossary#Back-Pressure)를 이용한 비동기 스트림 처리의 표준
{: .prompt-tip }

### 🧐 BackPressure
- 기존 옵저버 패턴은 `Push` 방식으로, Publisher가 데이터가 변경될 때마다 데이터 생성
- BackPressure은 `Pull` 방식으로, Subscriber가 필요한 만큼만 요청

<br>

## 📱 Reactive Stream을 구성하는 인터페이스

### <mark style='background-color: #f1f8ff'> Processor </mark>
- 오퍼레이터 모음

### <mark style='background-color: #f1f8ff'> Publisher </mark>
- 데이터를 생성하는 역할

### <mark style='background-color: #f1f8ff'> Subscriber </mark>
- 데이터를 구독하고 처리하는 역할

### <mark style='background-color: #f1f8ff'> Subscription </mark>
- Subscriber와 Publisher 사이의 데이터가 교환될 수 있도록 연결하는 역할
- 전달 받을 데이터의 개수를 요청하거나, 구독을 해지 할 수 있다.

<br>

## ❓ Reactor

- 스프링 리액티브 개발에 사용되는 Reactive Stream의 구현체 중 하나

<br>

## 🎁 Publisher의 구현체

### <mark style='background-color: #f1f8ff'> Flux </mark>

![image](https://user-images.githubusercontent.com/76933244/163008833-4e849cac-36ae-474d-915c-1910627af32a.png){: w="700"}
_https://projectreactor.io/docs/core/release/reference/#flux_

- 비동기 sequence
- 0 ~ N개의 아이템을 가진다.

### <mark style='background-color: #f1f8ff'> Mono </mark>
![image](https://user-images.githubusercontent.com/76933244/163009169-bb899b13-9b84-4d77-a0cf-7675e82d3a9c.png){: w="700"}
_https://projectreactor.io/docs/core/release/reference/#mono_

- 비동기 item
- 0 또는 1개의 아이템을 가진다.

<br>

## 🍃 Sequence
> 변화 가능한 데이터의 흐름
{: .prompt-tip }

- Publisher에 의해 publish 되고 Subscriber에 의해 subscription

<br>

## 👮 Schedulers
> 오퍼레이터를 처리할 쓰레드를 지정한다.
{: .prompt-tip }

- Reactor는 비동기 실행을 강제하지 않기 때문에 스케줄러를 사용하여 쓰레드를 지정한다.
- 스케줄러를 설정하지 않으면, 메인 쓰레드에서 동기적으로 실행

### <mark style='background-color: #f1f8ff'> publishOn() </mark>
- 신호 처리 스케줄링
- next, complete, error 신호 처리 쓰레드 설정
- 다음 publishOn을 만날 때까지 같은 쓰레드에서 동작

### <mark style='background-color: #f1f8ff'> subscribeOn() </mark>
- 구독 처리 스케줄링
- 시퀀스를 실행할 쓰레드 결정
- publishOn을 만날 때까지 같은 쓰레드에서 동작
- publishOn이 신호를 처리할 쓰레드를 지정하므로, publishOn 뒤에 오는 subscribeOn은 무시된다.

<br>

## 📊 publishOn() and subscribeOn() Comparison

### 공통점
> 스케줄러를 통해 쓰레드를 분리한다
{: .prompt-tip }

### 차이점

#### publishOn()
```java
Flux.fromIterable(listOf(1, 2, 3, 4))
    .map { i -> i * 10 }
    .publishOn(Schedulers.Elastic())
```
- publishOn()을 통해 오퍼레이터가 메인 쓰레드가 아닌, 별도의 쓰레드에서 동작한다.
- 메인 쓰레드 외 1개의 쓰레드 생성

#### subscribeOn()
```java
Flux.fromIterable(listOf(1, 2, 3, 4))
    .map { i -> i * 10 }
    .subscribeOn(Schedulers.Elastic())
```
- subscribeOn()은 오퍼레이터를 실행할 때마다 새로운 쓰레드에서 실행된다.
- 위의 코드에서는 하나의 시퀀스에 4개의 데이터가 있기 때문에 4개의 쓰레드가 생성된다.

<br>

## 📒 Schedulers 종류

### <mark style='background-color: #f1f8ff'> Immediate </mark>
- 지금 실행 중인 쓰레드에서 실행

### <mark style='background-color: #f1f8ff'> Single </mark>
- Runnable Executor 실행

### <mark style='background-color: #f1f8ff'> Parallel </mark>
- Core 개수만큼의 쓰레드 생성
- 주로 CPU를 많이 사용하지만 생명주기가 짧은 작업 실행

### <mark style='background-color: #f1f8ff'> Elastic </mark>
- 쓰레드 무한정 생성

### <mark style='background-color: #f1f8ff'> BoundedElastic </mark>
- Default로 Core * 10 만큼의 쓰레드 생성

<br>

## ✨ Reactive Programming 장점

### 1. <mark style='background-color: #f1f8ff'> 장애가 전파되지 않는다. </mark>
- 장애가 발생한 처리자는 구독한 데이터를 처리할 수 없다.
- 시퀀스에서 처리되지 않은 데이터는 그대로 흘러간다.

### 2. <mark style='background-color: #f1f8ff'> 비동기 처리 </mark>
- 스케줄러를 이용하여 쓰레드를 쉽게 사용할 수 있다.

### 3. <mark style='background-color: #f1f8ff'> 리소스의 효율적인 사용 </mark>
- 요청자는 처리자가 작업을 완료하기 전까지 다른 작업을 하거나 리소스를 반납한다.
- 쓰레드를 점유하지 않는다.

<br>


