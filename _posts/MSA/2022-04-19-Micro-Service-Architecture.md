---
title: "Micro Service Architecture"
date: 2022-04-19 23:00:00 +0900
categories: [MSA]
tags: [msa, spring]
---

## ❓ Monoliths

> 전통적인 시스템 구조로 하나의 단위로 개발하는 단일 서비스 개발 방식
{: .prompt-tip }

<br>

## 📍 Monolith 단점

- 긴 빌드 시간 및 테스트 시간
- 특정 개발 언어, DB에 종속
- 선택적으로 확장 불가능
- 서비스 간 높은 의존성

<br>

## ❓ Software 모듈화
> 큰 문제를 해결하기 위해 작은 단위로 나누어 개발하는 방법
{: .prompt-tip }

- 마이크로 서비스를 만들기 위한 첫 과정
- 서비스 기능의 확장, 수정, 테스트, 재사용 편리

<br>

## 💡 모듈 설계 조건

- 모듈마다 다른 모듈과 구분되는 독립적인 기능 수행
- 독립적인 컴파일 가능
- 한 모듈에서 다른 모듈 호출 가능

<br>

## 🔎 모듈화의 특징

### 캡슐화
- 모듈 내 동작 방식, 데이터 구조를 다른 모듈에게 은폐

### 추상화
- 다른 모듈은 추상화 된 기능으로만 모듈에 접근

### 독립성
- 서로 다른 모듈끼리 낮은 결합도
- 한 모듈 내부에서는 높은 응집도

<br>

## 💡 분산 컴퓨팅 환경의 소프트웨어 요구 조건
- 개발 언어에 상관없이 동일한 서비스 동작
- 컴포넌트가 특정 플랫폼에 비종속적
- 서비스 유지보수 용이

<br>

## ❓ SOA
> Service Oriented Architecture

>  컴포넌트를 모아 비즈니스적으로 의미 있고 완결적인 서비스 단위로 모듈화하는 방법론
{: .prompt-tip }

<br>

## 🔎 SOA 특징
- 특정 플랫폼에 비종속
- 서비스 간 낮은 결합도
- 서비스 위치 투명성
- 하나의 DB를 공유하기 때문에 독립적으로 사용 불가능
- MSA와 비슷한 개념이지만, 추상적이며 성공을 증명하지 못함

<br>

## ❓ MicroService

> 여러 개의 작은 서비스 집합으로 개발하는 접근 방법
{: .prompt-tip }

- 서비스는 비즈니스 단위로 구분되어 별개의 인스턴스로 작동
- 여러 서비스가 모여 하나의 비즈니스 애플리케이션 구성
- `Polyglot` 방식으로 서로 다른 언어와 DB 사용 가능
- 서비스는 서로 내부 API를 호출하여 통신
- 독립적인 확장 및 배포 가능

<br>

## 📍 MicroService 단점

- 각 서비스가 독립적이기 때문에 통신을 위한 수많은 내부 service call 발생
- Transaction 관리 난이도 상승
- 데이터 무결성 보장 난이도 상승
- 시스템 복잡도 상승

<br>

## ❓ MSA
> MicroService Architecture

> 마이크로서비스 기반으로 시스템을 개발하는 아키텍처 및 개발 방식
{: .prompt-tip }

<br>

## 💡 MicroService 조건

### 1. 업무 조직 성격의 변화
- 역할별 팀 구성 ➡ 목적별 팀 구성
- 팀마다 관리하는 서비스는 느슨한 연결로 구성

### 2. 관리체계의 변화
- 목적팀 별 서비스 목표에 따라 방법론, 도구를 취사 선택

### 3. 개발 생명 주기의 변화: 프로젝트 ➡ 제품 중식
- Waterfall ➡ Agile
- 하나의 서비스를 개발하고 변경, 폐기하는 과정 용이

### 4.개발 환경의 변화: 인프라 자동화
- `인프라 자동화`는 개발 환경, 개발지원 환경을 자동화 하는 것을 의미
- 클라우드 인프라를 활용하여 쉽고 빠르게 개발 환경 구축
- `Infrastructure as Code`를 통해 인프라 구성 및 애플리케이션 빌드 및 배포 등의 자동화를 코드로 처리

### 5. 저장소의 변화: 통합 저장소 ➡ 분권 데이터 관리
- 서비스별 데이터베이스 사용
- 다른 서비스의 저장소를 직접 호출할 수 없고 오로지 API를 통해서 접근

### 6. 실패를 고려한 설계
- 다양한 실패에 대비한 완벽한 테스트 환경 마련
- 시스템 실패를 감지하고 대응하기 위해 실시간 모니터링 체계 구축
- `Circuit breaker` 패턴으로 긴급 장애 상황에 빠르고 유연하고 탄력적으로 대응

#### 🧐 Circuit breaker
> 각 서비스를 모니터링하고 있다가 한 서비스에서 장애가 발생하면 이를 호출하는 서비스의 연계를 차단하고 적절하게 대응하는 것을 의미
{: .prompt-tip }

<br>

## 📚 MSA 설계 원칙

### 단일 책임 원칙
- 명확한 모듈 경계 설정 필요

### MicroService는 자율적
- 독립적 배포
- 독립적 실행
- 독립적 확장, 축소

<br>

## 📍 MSA 설계 시 고려사항
- 서비스 간 호출량
- 내부 service call에 동기적 의존 관계 존재 여부
- 서비스 간 순환 의존 관계 존재 여부
- Transaction 범위
- 하나의 service의 배포 크기
- 분리 시 유의미한 resource 사용량이 발생하는 기능

<br>

## 📋 MSA 구성 요소

### API Gateway pattern
- 여러 MS App에서 공통적으로 필요한 기능 분리
- e.g. 사용자 정보, 인증, 로깅 등
- Routing 기능 수행

### RESTful
- 통신 인터페이스

<br>

## 🎨 HATEOAS
> Hypermedia As The Engine Of Application State

> REST API를 통해 클라이언트가 서버와 동적인 상호작용하기 위한 매커니즘
{: .prompt-tip}

- REST API의 단점을 보완하기 위해 HATEOAS 사용
> 단점 1. 엔드 포인트 URL을 변경하면 모든 클라이언트의 URL 변경 <br>
> 단점 2. 자원의 상태를 고려하지 않기 때문에 클라이언트에서 처리 필요

- 링크에 사용 가능한 URL을 리소스로 전달하여 클라이언트가 참고하도록 하여 극복

### HAL
> Hypertext Application Language

> API의 리소스들 사이에 쉽고 일관적인 하이퍼링크를 제공하는 방식
{: .prompt-tip }

- 응답에 참조 가능한 정보들을 요청 메시지에 포함
- Context type은 `application/hal+json`

```json
{
  "_links": {
    "self": {"href": "/user/login"}
  }
}
```

<br>

## 📍 MSA Monitoring 문제

- 분산된 각각의 서비스의 Health check 문제
- 클라우드 환경에서 로그 보관의 어려움
- 컨테이너의 짧은 수명
- 각 서비스 별로 분산되어 있는 로그

> 중앙 집중형 Monitoring Service 구축 필요
{: .prompt-tip }
```
- 서비스의 모든 로그 메시지 수집
- 트랜잭션 연결 추적 가능
- 로그 장기 보관 가능
```

<br>

## 💊 장애 대응

### 1. 장애 전파 차단
- `Circuit breaker`로 장애 서비스 격리
- `Fallback`으로 장애 서비스 대체

### 2. 분산 저장 / 운영
- Public Cloud를 사용하는 경우 다중 리전 사용

### 3. Canary 배포
- 조금씩 사용자의 범위 확장
- 일부 트래픽을 새 버전의 서버로 분산하여 오류 여부 판단
- 빠르게 장애 감지 가능
- 장애를 감지하면 `Rollback`

### 4. 장애 시나리오
- `Chaos Engineering`

<br>

## 🧶 Anti Pattern

### Microliths
- Monoliths 분해 실패
- 분해된 서비스끼리 강한 의존성

### Death Star
- 밀접하게 결합하고 뒤섞인 마이크로서비스

<br>

## 🧵 보완 설계 패턴

### Service Mesh

> MicroService가 서로 데이터를 공유하는 방식을 제어하는 방법
{: .pompt-tip }

- 가벼운 프록시를 `Sidecar` 패턴으로 배치
- Sidecar는 모니터링, 로깅, 프록시 등의 동작 수행

### Istio
- Service Mesh 구현체
- kubernetes 지원
- MS contaier에 sidecar를 붙여서 배포
- Logging, security, routing, discovery 등 cliend-side 역할 담당
- 각 MS는 서로 proxy를 통해 통신

### Serverless Computing
- Cold Start 이슈

<br>
<br>

### 출처
- [Martin Fowler](https://martinfowler.com/articles/microservices.html)
