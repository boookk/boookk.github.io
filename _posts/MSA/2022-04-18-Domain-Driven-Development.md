---
title: "Domain Driven"
date: 2022-04-18 23:00:00 +0900
categories: [MSA]
tags: [msa, ddd]
---

## 🍃 기존의 개발
- 관계형 데이터 모델에 종속
- 최초 설계 데이터의 모델링의 변경과 확장하기 어려움
- 모델링과 실제 개발의 불일치 누적

<br>

## 🎨 Domain Driven Design

- 데이터를 기능과 분리해서 식별하지 않고, 별도의 도메인 모델로 정의
- 용어 사전을 기반으로 도메인 설계
- 도메인 별로 설계와 구현 가능

### 🧐 용어 사전 (Ubiquitous Language)

> 사용자와 설계자, 구현자가 모두 의미에 동의할 수 있는 용어의 모음
{: .prompt-tip }

<br>

## ✨ Domain

- 소프트웨어로 해결하고자 하는 문제 영역
- 개발하려는 서비스의 비즈니스 로직과 연관

<br>

## ❓ Domain model

> 요구사항으로부터 Domain과 이하 entity를 정의하고 그 관계를 경계와 함께 추상화한 모식도
{: .prompt-tip }

<br>

## 📊 Domain-driven and Object-oriented Comperison

### Object
- 추상화하거나 구체화할 수 있는 대상
- e.g. 상품, 주문, 쿠폰

### Domain
- 요구사항에서 표현하는 모든 것
- e.g. Object + 주문하다, 결제하다, 정산하다 등

<br>

## 📌 Domain Driven Design Step

1. 요구사항 정리
2. 핵심 도메인 로직 파악
3. `용어 사전` 정리
4. 도메인을 작은 단위로 분리
5. `Bounded context` 설정하고 관계 정의
6. 세부 동작 설계
7. Context 별 bounds 침범 여부 확인
8. 변경 사항 발생 시 반복

<br>

## 📋 Domain Driven Design 기본 요소

### Domain model pattern
- Entity
- Value Object
- Service
- Aggregate
- Repository

### Bounded Context
- 서로 독립적인 업무로 분할될 수 있는 모델 영역
- MSA를 나누느 단위로 사용 가능

<br>

## 🎄 Domain Driven Architecture

### Client
- Presentation layer에 `HTTP Request` 전달

### Presentation layer
- Client의 요청을 받고 Application layer로 전달받은 결과를 client에게 전달

### Application layer
- Client에게 제공할 결과를 Domain layer에 요청하여 조합

### Domain layer
- `Domain model`을 구현
- 하나의 대표되는 도메인이 다른 도메인의 처리 결과를 조합하는 경우가 많다고 한다.

### Infrastructure layer
- DB, 외부 시스템 등 연동 처리

<br>

