---
title: "Git 사용 방법"
date: 2021-07-03 00:00:00 +0300
categories: [Git]
tags: [git]
---

## 📚 Git

- 소스 코드의 버전 관리 프로그램
- 여러 개발자와의 협업 가능
- GitHub, GitLab은 Git 기반의 저장소 서비스


<br>


## 📚 저장소의 프로젝트를 Local 저장소로 복제
```shell
git clone <url>
```
{: .nolineno }


<br>


## 📚 내 컴퓨터에서 디렉토리를 만들어 시작하는 경우
```shell
cd ./디렉토리
git init

# 저장소의 내용을 가져온다
git remote add <저장소> <url>
```
{: .nolineno }


<br>


## 📚 git 저장소마다 다른 계정으로 설정 가능
```shell
git config user.name "name"
git config user.email "@"
```
{: .nolineno }


<br>


## 📚 git commit log 확인
```shell
git log
```
{: .nolineno }
<mark style='background-color: #ffdce0'> git log 명령어를 통해 commit id 확인 가능 </mark>


<br>


## 📚 전체 commit log 확인
```shell
git log --all --graph
```
{: .nolineno }


<br>


## 📚 HEAD가 가리켰던 커밋 기록을 모두 확인
```shell
git reflog
```
{: .nolineno }
<mark style='background-color: #ffdce0'> reference log 숫자가 낮을수록 최근기록 </mark>


<br>


## 📚 git commit 내용 비교
```shell
git diff <commit_id> <commit_id>
```
{: .nolineno }
<mark style='background-color: #ffdce0'> commit id를 다 적지 않고 구분 가능한 정도만 적어주어도 된다. </mark>


<br>


## 📚 원하는 commit 시점으로 변경
```shell
git reset --option <commit_id>
```
{: .nolineno }

### 📍 옵션
--hard : Working Directory 내용 변경
--mixed : Working Directory 변경하지 않고 Staging Area를 해당 커밋처럼 변경
--soft : Working Directory, Staging Area 변경하지 않고 HEAD가 가리키는 커밋만 변경


<br>


## 📚 git의 현재상태
```shell
git status
```
{: .nolineno }


<br>


## 📚 git branch 생성
```shell
git branch <branch_name>
```
{: .nolineno }


<br>


## 📚 git branch 변경
```shell
git checkout <branch_name>
```
{: .nolineno }


<br>


## 📚 HEAD가 가리키는 branch에 target_branch 병합
```shell
git merge <target_branch_name>
```
{: .nolineno }
<mark style='background-color: #ffdce0'> merge 과정에서 충돌이 발생할 경우, 충돌이 발생한 파일을 직접 수정하고 add와 commit을 하면 된다. </mark>



<br>


## 📚 원격 저장소에 변경 사항 업로드
```shell
git push -u origin master
```
{: .nolineno }


### 📍 옵션
-u 옵션 : --set-upstream : 내 컴퓨터의 master 브랜치가 저장소 서버의 master 브랜치를 가르키도록
-u 옵션을 사용할 경우 뒤에 저장소와 branch를 명시하지 않아도 된다.
--force : 강제 업로드


<br>


## 📚 fork
- 원본 프로젝트와 동일한 복제 프로젝트 만들기
- 복제 프로젝트로 작업 후 원본 프로젝트로 merge request 보내기

