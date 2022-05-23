---
title: "Netflixed"
date: 2022-04-20 23:00:00 +0900
categories: [MSA]
tags: [msa, netflix, cloud]
---

## 🧐 Netflixed

> 미국 실리콘밸리에서 기존 비즈니스 모델이 붕괴되었을 때를 일컫는 말
{: .prompt-tip}

<br>

## ✨ Netflix OpenSource Software

> 기존 Legacy 시스템을 클라우드 환경의 MSA로 전환하기 위해 사용한 기술을 공개한 것
{: .prompt-tip}

### 🏃 Netflix는 MSA의 선구자

<br>

## 🧶 Eureka
> Client와 Application server 사이에서 로드 밸런싱 및 장애 조치를 위해 AWS 클라우드에서 주로 사용되는 RESTful 서비스 
{: .prompt-tip }

- 클라우드 기반의 MSA 서비스의 `IP`와 `port`는 일정하지 않고 지속적으로 변화
- Eureka는 클라우드 환경에서 연결 정보 등록 및 해지를 도와주는 역할
- `Eureka Server`와 `Eureka Client`로 구성

### 🧐 Eureka Client
- 서비스마다 `Eureka client` 설치
- Spring에서 annotation만 추가하면 사용 가능
- Eureka Client는 스스로 Eureka server에 등록
- 연결 정보 `Meta Data`를 Eureka 서버에 등록

### 🧐 Eureka Server
- Eureka server가 `Registry`에 Eureak client 등록
- Registry에 Eureka client의 Meta data 등록
- Client의 상태 확인 

### 🧐 Registry
> 서비스의 연결 정보를 등록하는 것

### 🧐 Discovery
> 다른 서비스의 정보를 찾는 것

<br>

## 👮 Zuul

- API Gateway 구현체
- 라우팅 역할
- Endpoint 관리 통합
- Reverse proxy
- 인증 및 접근 제어

<br>

## 💊 Hystrix

> 분산 서비스 간의 상호 작용을 제어하는 데 도움을 주는 라이브러리
{: .prompt-tip }

- 종속성으로 인한 지연 및 장애로부터 보호하고 제어하는 기능
- 실패 서비스 액세스 격리
- 빠르게 실패하고 빠르게 복구 가능
- 실시간에 가까운 모니터링, 경고 및 운영 제어 가능

<br>
<br>

### 출처
- [Netflix OSS](https://netflix.github.io/)
