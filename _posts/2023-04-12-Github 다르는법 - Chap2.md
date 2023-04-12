---
layout: single
title: "[Github] branch / git flow 정의 및 정리"
categories: Project
tag: [back-end, project, github]
toc: true
toc_sticky: true
toc_label: index
toc_icon: "fa-solid fa-indent"
author_profile: false
# sidebar:
#     nav: "docs"
# search: false
---



<br>

본 게시글은  
[Github Repo / 칸반의 정의 및 정리](https://mins-git.github.io/project/Github-다루는법-Chap1/) 의 뒷 내용을 이어갑니다.



<br>

🐣 개발 프로젝트 제작을 위한 Github 다루는 방법.  **Chap2**

<br>

### Chapter2-1. Git branch 다루기

### Chapter2-2. 프로젝트 Git Flow 학습

<br>

<br>

## 📚 **학습 목표**

- Git으로 브랜치를 다루는 방법에 대해 이해한다.
- 브랜칭 전략 중 간소화된 Coz’ Git flow에 대해서 이해하고 적용한다.
- Pull Request와 간단한 코드 리뷰 하는 방법에 대해서 이해한다.
- Git을 다루다가 어려움에 처했을 때, 어떻게 대처하는지에 이해한다.

   

<br/>

<br/>

## Chapter2-1. Git branch 다루기

### 🎈 Git branch   

브랜칭(branching)은 기존 개발중인 메인 개발 코드를 그대로 복사하여 새로운 기능 개발을 메인 개발 코드를 건드리지 않고 할 수 있는 버전 관리 기법입니다. 처음에 GitHub Repository를 생성하면 나오는 main 브랜치에서만 작업을 하다가 새로운 기능 개발을 위해 feature 브랜치를 새로 생성하는 경우, 기존 main 브랜치에서의 작업은 유지하고 새로운 feature 브랜치에서 자유롭게 코드를 추가 및 삭제할 수 있습니다.   

<br/>

<br/>

#### ◼ 브랜치 생성하기 / 변경하기 (git switch)   

이 때, 새로운 브랜치로 Git이 바라보는 곳, HEAD를 변경하는 작업을 switch라고 부릅니다. 브랜치를 생성할 때는 생성(create)의 의미로 `-c` 를 붙여줘야 하고, 기존에 있는 브랜치로 옮길 때는 붙이지 않아도 됩니다.   

<br>

```java
// mins라는 브랜치를 새로 생성하는 경우, -c를 붙입니다.
git switch -c mins
// checkout이라는 명령어도 사용할 수 있습니다.
git checkout -b mins

// 기존에 있던 main 브랜치로 HEAD를 변경하려면, -c를 붙이지 않습니다.
git switch main
git checkout main
```

<br>

<br>

#### ◼ 브랜치 합치기 (git merge)   

기능 개발이 끝나면 브랜치를 main 브랜치와 합칠 수 있습니다.   

```java
// 기능 개발이 진행되었습니다.
git commit -m "기능1의 세부 기능1"
git commit -m "기능1의 세부 기능2"
git commit -m "기능1 개발 완료"
// 머지를 위해 main 브랜치로 전환
git switch main
// main 브랜치로 mins 브랜치를 병함
git merge mins
```

   

실제로 개발시에는 브랜치를 로컬에서 합치지 않고, GitHub의 Pull Request 기능을 이용하여 변경 내역을 충분히 확인한 후 머지하는 경우가 많다. 따라서 mins 브랜치를 push한 후 Pull Requset를 요청하면 된다.

<br>

```java
// 기능 개발이 진행되었습니다.
git commit -m "기능1의 세부 기능1"
git commit -m "기능1의 세부 기능2"
git commit -m "기능1 개발 완료"
// GitHub 리포지토리로 푸시합니다.
git push origin feat/todo
// GitHub에서 Pull Request를 합니다.
```

<br>

<br>

#### ◼ 브랜치 삭제하기 (git branch -d)   

머지된 mins 브랜치는 이미 dev 브랜치에 기록이 완벽하게 남아있기 때문에 굳이 남겨둘 이유가 없어 삭제를 권장합니다. 원격 리포지토리에서 pull request가 성공적으로 마무리되면, 깃허브에서 브랜치를 삭제하는 버튼을 눌러 쉽게 삭제할 수 있습니다.   

로컬 Repositoy의 브랜치 삭제는 `git branch -d <브랜치명>` 으로 할 수 있습니다.   

```java
git branch -d feat/todo
```

Git은 원활한 버전 관리를 위해서, 브랜치가 합쳐지지 않으면 삭제하지 못하도록 설정이 되어있습니다. 하지만 종종 다 만들지 못한 기능의 기록을 삭제하고 싶을 수 있습니다. 이 때 `-D` 옵션을 쓰면 삭제할 수 있습니다.

```java
git branch -D feat/todo
```

다만, 머지되지 않은 브랜치 삭제는 버전 기록 시스템의 사용 목적과는 잘 맞지는 않습니다. 잘 못 만들었던 기능이지만, 해당 기능으로 돌아가고 싶을 수도 있기 때문에 돌아갈 여지를 만들어두는게 좋을 수도 있습니다. 이런 경우는 팀 및 회사 정책에 따르는 것을 권장합니다.

<br>

<br>

   

#### ◼ Git 쓸만한 추가 코드

##### 🙈 Git 설정   

로컬 리포지토리와 연결할 유저 정보를 설정합니다.

```java
// 버전 히스토리를 식별할 때 사용할 이름을 설정합니다.
$ git config --global user.name "[firstname lastname]"
// 각 기록과 연결할 이메일 주소를 설정합니다.
$ git config --global user.email “[valid-email]”
```

   

<br>

##### 🙈 도움말 보기   

help 명령어를 이용하여 각 명령어 및 옵셥의 기능에 대해 살펴볼 수 있습니다.

```java
// Git에서 제공하는 모든 명령어를 볼 수 있습니다.
$ git help -all
// 특정 command에서 사용할 수 있는 모든 옵션을 볼 수 있습니다.
$ git [command] -help
```

   

<br>

##### 🙈 세팅 및 초기화   

리포지토리를 초가화하거나 존재하는 리포지토리를 클론할 수 있습니다.

```java
// 현재 디렉토리를 기준으로 Git 저장소가 생성됩니다.
$ git init
// URL을 통해 리모트 리포지토리를 로컬 리포지토리에 복제합니다.
$ git clone [url]
```

   

<br>

##### 🙈 Stage & Commit   

스테이지 영역을 이용하여 커밋할 수 있습니다.

```java
// 다음 커밋을 위해 현재 디렉토리에서 수정된 파일을 확인할 수 있습니다.
$ git status
// 다음 커밋을 위해 파일을 추가(스테이지)합니다. (stage)
$ git add [file]
// 추가한 파일을 언스테이징합니다. 변경 사항은 유지됩니다.
$ git reset [file]
// 스테이지되지 않은 변경 사항을 보여줍니다.
$ git diff
// 스테이지했지만 커밋하지 않은 변경 사항을 보여줍니다.
$ git diff --staged
// 스테이지된 콘텐츠를 메시지와 함께 커밋합니다. (스냅샷 생성)
$ git commit -m “[descriptive message]”
```

   

<br>

##### 🙈 Branch & Merge   

작업 내역을 브랜치로 분리해 컨텍스트를 변경, 통합할 수 있습니다.

```java
// 브랜치 목록을 보여줍니다. * 표시로 현재 작업중인 브랜치를 확인할 수 있습니다.
$ git branch
// 현재 커밋에서 새로운 브랜치를 생성합니다.
$ git branch [branch-name]
// 다른 브랜치로 전환합니다.
$ git switch [branch-name]
$ git checkout [branch-name]

// 새로은 브랜치를 생성하고 해당 브랜치로 전환합니다.
$ git switch -c [branch-name]
$ git checkout -b [branch-name]
// 현재 브랜치에 특정 브랜치의 히스토리를 병합합니다.
$ git merge [branch-name]
// 현재 브랜치의 모든 커밋 히스토리를 보여줍니다.
$ git log
```

   

<br>

##### 🙈 비교 및 검사   

로그 및 변경 사항을 검사할 수 있습니다.

```java
// 브랜치B에 없는 브랜치A의 모든 커밋 히스토리를 보여줍니다.
$ git log branchB..branchA
// 해당 파일의 변경 사항이 담긴 모든 커밋을 표시합니다. (파일 이름 변경도 표시)
$ git log --follow [file]
// 브랜치A에 있지만 브랜치B에 없는 것의 변경 내용(diff)을 표시합니다. (branch간 상태 비교)
$ git diff branchB...branchA
```

   

<br>

##### 🙈 공유 및 업데이트   

특정 리포지토리의 업데이트 사항을 검색하여 로컬 리포지토리를 업데이트할 수 있습니다.

```java
// url을 통해 특정 리모트 리포지토리를 별칭으로 추가합니다.
$ git remote add [alias] [url]
// 별칭으로 추가한 리모트 리포지토리에 있는 모든 브랜치 및 데이터를 로컬로 가져옵니다.
$ git fetch [alias]
// 리모트 브랜치를 현재 작업중인 브랜치와 병합하여 최신 상태로 만들 수 있습니다.
$ git merge [alias]/[branch]
// 로컬 브랜치의 커밋을 리모트 브랜치로 전송합니다.
$ git push [alias] [branch]
// 리모트 리포지토리의 정보를 가져와 자동으로 로컬 브랜치에 병합합니다.
$ git pull
```

   

<br>

##### 🙈 히스토리 수정   

브랜치 또는 커밋을 수정하거나 커밋 히스토리를 지울 수 있습니다.

```java
// 특정 브랜치의 분기 이후 커밋을 현재 작업중인 브랜치에 반영합니다.
$ git rebase [branch]
// 득정 커밋 전으로 돌아가며 스테이지된 변경 사항을 모두 지웁니다.
$ git reset --hard [commitish]
```

   

<br>

##### 🙈 임시 저장   

브랜치를 전환하기 위해 변경되었거나 추적중인 파일을 임시로 저장할 수 있습니다.

```java
// 수정하거나 스테이지된 변경사항을 스택에 임시 저장하고 현재 작업 내역에서 지웁니다.
$ git stash
// 스택에 임시 저장된 변경사항의 목록을 보여줍니다.
$ git stash list
// 스택에 임시 저장된 변경사항을 다시 현재 작업 내역에 적용합니다.
$ git stash apply
// 스택에 임시 저장된 변경사항을 다시 현재 작업 내역에 적용하고 스택에서 삭제합니다.
$ git stash pop
// 스택에 임시 저장된 변경사항을 삭제합니다.
$ git stash drop
```

   

<br>

<br>

<br>

## Chapter2-2. 프로젝트 Git Flow 학습

### Git flow

Git flow는 2010년 [incent Driessen의 블로그 글로부터 시작되었고, 이후 많은 개발자의 사랑을 받아온 Git 브랜칭 전략입니다. Git flow는 대규모 개발 프로젝트를 제작하여 하나의 소프트웨어의 릴리즈 버전을 명확하게 나누고, 다양한 버전을 배포해야 하는 당시의 개발 환경과는 적합했지만, 빠르게 제작하고 배포하고 고객의 피드백을 받는 애자일한 개발 팀에 적용하기는 다소 복잡했습니다.   

이에 “원조" Git flow에서 파생된 여러 Git flow가 있습니다.    

대표적인 Git flow는 [Github flow](https://docs.github.com/en/get-started/quickstart/github-flow), [Gitlab flow](https://docs.gitlab.com/ee/topics/gitlab_flow.html)가 있습니다. 이번 Pre project에서는 Github flow를 단순화 해서 사용해볼 생각입니다.

<br>

<br>

#### ◼ mins Git flow

main branch ->   

FE   

BE   

feature/havetodo   

제가 이번에 할 프로젝트에서는 위와같이 4개의 브렌치로 나누어, 작업할 예정입니다.  

**FEATURE 브랜치를 통해서** 기능 개발, 리펙토링, 문서 작업, 단순 오류 수정 등 다양한 작업을 기록을 할 것입니다.

개인의 로컬에 feature 브랜치를 만든 후 작업을 해서 -> BE에 합치게 될것이고 -> main으로 옮기는 방식을 채택할 예정입니다.   

<br>

💡 **Git flow tip:** Git flow는 대규모 개발 프로젝트를 제작하여 하나의 소프트웨어의 릴리즈 버전을 명확하게 나누고, 다양한 버전을 배포해야 하는 개발 환경에 적합합니다. 단순한 Git 브랜칭 전략이 필요한 경우 언제든지 다른 전략을 사용할 수 있습니다.

💡 **commit tip:** 팀원들과 작업 결과를 공유하고 피드백을 받기 위해서 자주 커밋하고 자주 push 하는 것이 좋다.

<br>

<br>

<br>

<br>

##### **🔖 용어 설명**

**dev 브랜치?**

dev 브랜치는 일반적으로 개발 작업이 진행되는 브랜치입니다. 개발자들은 dev 브랜치에서 자신이 수정한 코드를 커밋하고, 다른 개발자들과 함께 작업을 공유합니다.

<br>

<br>



##### 🧠 **오늘의 띵언:**

바퀴를 재 발명하지마라!

**Don't reinvent the wheel**

이유: 재발명된 바퀴는 기존의 바퀴보다 안정성이 떨어져 ^^(라고 맞는 말이지만 정신승리 +1) ㅋㅋㅋ 🥰

<br>

<br>
