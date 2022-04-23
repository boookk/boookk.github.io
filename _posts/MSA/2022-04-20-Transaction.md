---
title: "Transaction"
date: 2022-04-20 23:00:00 +0900
categories: [MSA]
tags: [msa, spring]
---

## 💨 Monoliths ↔ MSA 전환

> Application Logic layer부터 순차적으로 분해
{: .prompt-tip }

1. `Router` 구축
2. Monoliths가 router를 통해 요청 받게 하기
3. API로 통신 가능한 작은 규모의 서비스를 분리하여 microservice 1개 구축
4. 구축된 서비스만 proxy 전환
5. DB 또는 schema 분리
6. 분리된 서비스를 위한 `Data Migration`
7. 검증 및 확장

<br>

## 🏃 데이터 이관 전략

- Downtime 갖고 한 번에 `ETL` (Extract, Transform, Load)
- 구DB와 새 DB 둘 다 사용하지만, Monoliths에서는 `ReadOnly`
- `CDC`를 이용하여 변경되는 데이터만 새 DB에 반영

> 오늘날에는 AWS Snowball 등 클라우드 서비스를 통해 데이터베이스 마이그레이션 간편화
{: .prompt-tip }

### 🧐 Change Data Capture
> DB의 로그 파일을 분석해 변경된 데이터를 추출하는 기술
{: .prompt-info }

<br>

## 🏗 MSA에서의 DB 설계

### 🙂 이상
- 분리된 서비스 당 독립된 데이터베이스 소유
- 다른 서비스에서 관리하는 데이터는 API를 통해서만 참조

### 🙃 현실
- 서로 다른 서비스가 같은 데이터를 동시에 `CUD` 하지 않도록 설계
- 반드시 물리적으로 데이터베이스 분리 불필요

<br>

## 🌉 분산 DB 설계

- 서비스 당 1개 DB
- 서비스 당 1개 DB + 필요한 DB Link View
- 하나의 DB를 하나의 서비스만 `CUD` 권한을 가지고, 나머지는 `ReadOnly`
- 1개 DB 내에서 TableSpace만 구분
- 1개 DB 내에서 Schema만 구분
- 공통 서비스에 대한 Shared Data 구축

<br>

## ❓ Transaction

> 데이터베이스의 상태를 변경시키기 위해 수행하는 작업 단위
{: .prompt-tip }

- Create, Delete, Update, Insert 모음
- 동시성 제어와 `Recovery` 기본 단위

<br>

## ❓ SAGA

> 분산 트랜잭션 시나리오에서 마이크로 서비스에서 데이터 일관성을 관리하는 방법
{: .prompt-tip }

### Orchestration SAGA
- 중앙 집중식 컨트롤러가 각 서비스에게 실행할 트랜잭션 알려주는 방법

#### 🧐 하나의 서비스에서라도 트랜잭션이 실패한다면?
> 성공한 트랜잭션 `rollback` 로직을 수행하여 일관성 유지

### Choreography
- 중앙 집중식 제어 없이 `Message Queue`를 이용하여 비동기로 트랜잭션 로직 요청
- 서비스 간 event `Publish`하고 `Subscribe`
- 시스템 복잡도 증가

#### 🧐 하나의 서비스에서 트랜잭션이 실패한다면?
> 약속된 `Fallback`을 수행하거나, `Retry`

<br>

## CQRS
> Command and Query Responsibility Segregation

> Command와 Query의 책임을 분리하는 패턴
{: .prompt-tip }

### 수준 1. 서비스 수준에서 CUD와 R 역할 구분

### 수준 2. read-replica 사용

### 수준 3. CUD DB와 R DB를 분리하고 동기화
- 보통 RDB와 NoSQL 기반의 DB를 사용하는 경우
- `Event Broker`를 통해 변경사항을 동기화

### 수준 4. EventSourcing
![image](https://docs.microsoft.com/ko-KR/azure/architecture/patterns/_images/event-sourcing-overview.png)
_https://docs.microsoft.com/ko-kr/azure/architecture/patterns/event-sourcing_
- 모든 트랜잭션을 `Event`로 `streaming`
- Event Broker 없이 EventStream 저장용 Data Storage 관리
- 데이터의 상태 변경 이력 관리 가능

<br>
<br>

### 출처
- [SAGA](https://docs.microsoft.com/ko-kr/azure/architecture/reference-architectures/saga/saga)
- [EventSourcing](https://docs.microsoft.com/ko-kr/azure/architecture/patterns/event-sourcing)
