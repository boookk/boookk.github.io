---
title: "Even Driven"
date: 2022-04-11 23:00:00 +0300
categories: [MSA]
tags: [msa]
---

## ❓ Event Driven
MSA가 적용된 시스템에서 이벤트 발생시 해당 `이벤트 로그`를 보관하고 

이를 기반으로 동작하며, `비동기 통신`을 통해 시스템 내 통합을 수행하는 아키텍처다.

<br>

## 📋 Event Driven 주요 요소

### 1. <mark style='background-color: #f1f8ff'> Event </mark>
프로그램에 의해 감지되고 처리될 수 있는 동작이나 사건

관찰의 대상이 되는 사건 정보를 담고 있다.

```json
{
  "id": "해싱된 키",
  "message": "처리할 사건",
  "createdAt": "timestamp"
}
```

### 2. <mark style='background-color: #f1f8ff'> Producer </mark>
이벤트 감지와 생성

### 3. <mark style='background-color: #f1f8ff'> Consumer </mark>
이벤트를 구독하고, 관심있는 이벤트가 발생하면 처리

### 4. <mark style='background-color: #f1f8ff'> Event Bus </mark>
Producer에서 Consumer로 이벤트 전달

<br>

## 🔒 Event Driven 제약 사항
- 이벤트는 발생한 사건에 대해 약속된 형식 사용
- 불변 (과거의 메시지를 변경할 수 없다.)
- 발생한 사건에 대한 결과 상태 전달
- 생성자는 이벤트 처리 상태에 관여하지 않는다.
- 소비자는 이벤트 생성자에 관심 갖지 않는다.

<br>

## 🔎 Event Driven Architecture 동작 방식

### 1. Message 생성 (Publish/Subscribe)
- 이벤트가 생성되면 `Subcriber`에게 전달된다.
- 반복되어 전달되지 않으며, 수신자는 송신자의 정보를 알 필요가 없다.

### 2. Event Source
- `Event Processor`에게 이벤트를 전달하는 역할
- Event Source는 1개 이상일 수 있고, 1개 이상의 Event Processor에게 전달한다.

### 3. Event Processor
- 수신된 이벤트에 대한 여러 Action을 수행하는 역할

### 4. Event Consumer
- 이벤트에 대한 처리를 한다.

<br>

## 🧐 Event Driven Architecture 설계 시 고려 사항

### 1. <mark style='background-color: #f1f8ff'> Loosely coupling </mark>

### 2. <mark style='background-color: #f1f8ff'> Removing dependencies </mark>
> 시스템 간 의존성은 감소하나, `Message Broker`에 대한 의존성 발생
{: .prompt-warning }

### 3. <mark style='background-color: #f1f8ff'> Nonblocking transaction </mark>
- 트랜잭션 간에 영향을 주지 않도록 설계해야 한다.

### 4. <mark style='background-color: #f1f8ff'> Asynchronized callback </mark>

### 5. <mark style='background-color: #f1f8ff'> Fallback / Retry </mark>
- 작업을 실패한 경우, 이전 작업까지 fallback을 하고 Retry할 수 있도록 설계해야 한다.

### 6. <mark style='background-color: #f1f8ff'> Event logging </mark>


<br>

## 🎨 Event Driven Architecture Pattern

### 1. <mark style='background-color: #f1f8ff'> Single Producer - Single Consumer </mark>
- 가장 단순한 형태

### 2. <mark style='background-color: #f1f8ff'> Single Producer - Multi Consumer </mark>
- 이벤트 처리 비용이 이벤트 생성 비용보다 높을 경우

### 3. <mark style='background-color: #f1f8ff'> Dead Letter Queue </mark>
#### 이벤트를 처리하는 데 실패했을 때 어떻게 할 것인가?
- Retry로 이벤트를 다시 큐로 되돌릴 수 있다.
- 설정한 Retry limitation 동안 이벤트 처리되지 않을 경우 main queue에서 제거하고 사후 분석을 위해 DLQ로 이동

### 4. <mark style='background-color: #f1f8ff'> Time To Live </mark>
- 처리되지 않은 이벤트의 생명 주기를 제한하여 만료되면 이벤트 폐기

### 5. <mark style='background-color: #f1f8ff'> Asynchronous request-response </mark>
- Polling

### 6. <mark style='background-color: #f1f8ff'> Event splitting </mark>
- 한 Event에 대해 여러 로직의 처리가 필요할 경우 사용
- 단일 책임의 원칙을 벗어나는 경우 이벤트를 나눠서 처리한다.

<br>

## ✨ Event Driven Architecture 특장점

### 1. <mark style='background-color: #f1f8ff'> Service 간 호출이 많은 MSA에 적합 </mark>
- 비동기적으로 다수의 컨슈머가 이벤트 버스를 통해 다수의 이벤트를 처리하는 형식
- Service간 호출이 많은 MicroService Architecture에 적합하다.

### 2. <mark style='background-color: #f1f8ff'> Infra Structure의 유연한 사용</mark>
> 하드웨어 인프라에서는 불가능
{: .prompt-warning }

### 3. <mark style='background-color: #f1f8ff'> Polyglot </mark>
- 모듈별로 여러 언어를 사용하여 구사하는 것이 가능하다.

### 4. <mark style='background-color: #f1f8ff'> 가용성, 응답성 개선</mark>
- 효율성과 성능의 향상 기대

### 5. <mark style='background-color: #f1f8ff'> Fault Isolation </mark>
- 하나의 서버에 장애가 발생하더라도, 시스템 전체에 영향을 미치지 않는다.
- 단, 서버의 장애가 지속되면 시스템 전체에도 영향을 미친다.

<br>

## 📍 Event Driven Architecture 단점

### 1. <mark style='background-color: #f1f8ff'> 설계 복잡도 증가 </mark>

### 2. <mark style='background-color: #f1f8ff'> Message Broker 의존성 증가 </mark>
- Message Broker를 보호하는 아키텍처를 만든다.

### 3. <mark style='background-color: #f1f8ff'> 코드 가독성 하락 </mark>

### 4. <mark style='background-color: #f1f8ff'> 디버깅 난이도 상승 </mark>

### 5. <mark style='background-color: #f1f8ff'> log를 통한 system flow 가독성 하락 </mark>

<br>

## 💻 Event Driven Programming

> 이벤트 발생에 의해 프로그램 흐름이 결정되는 프로그래밍 패러다임
{: .prompt-tip }

<br>

## 🔎 Even Driven Programming 특징

### <mark style='background-color: #f1f8ff'> Consumer ↔ Producer는 Broker 통해 소통 </mark>

### <mark style='background-color: #f1f8ff'> Message 생성 후 소비 전까지 Queue에 저장 </mark>

<br>

## ✨ Consumer ↔ Producer의 분리로 인한 이점
- N개의 consumer, producer 동시 처리
- 실패한 작업 재시도 및 logging 로직 단순화
- Consumer Scale out으로 컴퓨팅 리소스 확장

<br>


