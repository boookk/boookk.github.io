---
title: "Async-Nonblocking"
date: 2022-04-11 00:00:00 +0300
categories: [MSA]
tags: [msa]
---

## 📚 Synchronous
특정 함수를 호출한 뒤 해당 함수의 리턴 값을 확인하며 응답을 받기 전까지 동작을 멈춘다.

<br>

## 📚 Asynchronous
요청을 보낸 후 응답과는 상관없이 다음 동작을 실행한다.

<br>

## 📊 Sync&Async Comparison
![image](https://user-images.githubusercontent.com/76933244/162745605-b22463c2-2ca7-4e7a-b0c1-533c54350fd8.png)

> 요청자와 처리자가 서로의 시간을 공유하는지 여부에 따라 동기, 비동기로 구분된다.
{: .prompt-tip }

<br>

## 📚 Non-Blocking
함수 A가 함수 B를 호출해도 함수 A가 제어권을 가진다.
> 제어권 : 함수 자신의 코드를 실행할 권리를 의미
{: .prompt-tip }

<br>

## 📊 Blocking and Non-Blocking Comparison
![image](https://user-images.githubusercontent.com/76933244/162746960-8642bb8f-d2ea-451a-9f66-3e5a6086b652.png)

<br>
