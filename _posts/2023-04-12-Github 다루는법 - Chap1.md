---
layout: single
title: "[Github] Repo / 칸반의 정의 및 정리"
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

🐣 개발 프로젝트 제작을 위한 Github 다루는 방법.  **Chap1**

<br>

### Chapter1-1. GitHub Repository

### Chapter1-2. GitHub Project Kanban

<br>

<br>

## 📚 **학습 목표**

- 개발 프로젝트 GitHub Repository에 꼭 필요한 요소를 이해한다.
- 칸반이 무엇인지 이해한다.
- 칸반 원칙과 실천 방안에 대해서 이해한다.
- Github Project, 이슈, 마일스톤 기능을 이용하여 칸반 보드를 제작할 수 있다.
- 칸반 보드로 업무 시각화를 할 수 있다.

<br>

<br>



## Chapter1-1. GitHub Repository

### 🎈 GitHub Repository에 꼭 필요한 파일  

  

#### ◼ README.md  

기본 마크다운 문법을 활용해 간단한 소개 페이지를 제작할 수 있다.  

어떻게 하면 해당 오픈소스를 활용할 수 있는지에 대한 상세한 정보를 작성하면 된다.  



Pre-Project GitHub Repository README.md 파일은 아래 정보를 꼭 포함하면 좋다.  

- 프로젝트 이름
- 프로젝트 핵심 기능 소개
- 팀원 소개

​    

<br>

#### ◼ .gitignore  

**gitignore dotfile은 git으로 관리하지 않는 파일 모음이다.** 여기에는 개인이 따로 관리해야 하는 중요한 secret token이나, 다른 동료와 공유할 필요가 없는 설정 파일, 그 외 공유할 필요 없는 파일을 기록하면 git이 이를 파악하지 않고, push 할 때도 GitHub Repository에 push되지 않는다.   

<br>

#### ◼ LICENSE  

해당 코드의 라이센스를 표기한다. GitHub에 public하게 공개된 리포지토리도 라이센스에 따라서 사용을 할 수도 있고, 하지 못 할 수도 있으니 사용할 때 라이센스를 잘 보고 사용해야 한다. 회사에서 사용하는 코드는 private으로 관리하고, 외부에 공개하지 않아 라이센스 정보를 따로 표기하지 않기도 한다. 하지만 모종의 이유로 회사에서 작성하는 코드가 public으로 공개된다면, LICENSE를 명확하게 표기해야 한다.   

보통 제약이 적은 MIT 라이센스나 Apache License를 적용하여 많은 개발자가 쉽게 코드를 사용하고 기여할 수 있도록 한다.

<br>

<br>



### 🎈 프로젝트 관리에 활용할 수 있는 GitHub 기능

#### ◼ Issue   

GitHub Issue는 말 그대로 프로젝트에 새로운 기능을 제안하거나, 버그를 찾아 제보하는 등 프로젝트의 이슈를 의미한다.

Pre-Project에서는 GitHub Issue를 하나의 칸반 티켓처럼 사용 할 것이다.   

<br>

#### ◼ Milestone   

GitHub Milestone은 이정표 역할을 하며, 태스크 카드(Issue)를 그룹화하는 데 사용한다. GitHub Milestone에 연결된 태스크 카드(Issue)가 종료되면 GitHub Milestone마다 진행 상황이 업데이트되는 것을 볼 수 있다. 이 GitHub Milestone 기능을 통해 연관된 이슈의 추적과 진행 상황을 한눈에 파악할 수 있는 장점이 있다.

Pre-Project에서는 Bare Minimum, Advanced Challenge, Nightmare를 표시하기 위해 사용할 것이다.   

<br>

#### ◼ Pull Request   

Pull Request는 내가 작업한 내용을 중요 Git branch에 합칠 수 있는지 확인하는 요청이다. GitHub에서는 Pull Request에서 커밋한 코드를 따로 선택하여 해당 부분에 코멘트를 달 수 있다. 현장에서도 Pull Request를 보고 코멘트를 남기면서 코드 리뷰를 진행하기 때문에 Pull Request 과정에 익숙해지는 것이 중요하다.   

<br>

#### ◼ Project   

GitHub Project는 GitHub 내에서 업무 관리를 해줄 수 있게 돕는 새로운 기능이다.   

Pre-Project에서는 GitHub Project 기능을 이용하여 칸반 보드를 생성하고, 칸반으로 Pre-Project의 업무 흐름을 관리한다.   

<br>

<br>

<br>



## **Chapter1-2. GitHub Project Kanban**

### 🎈 칸반이란?

칸반(Kanban)은 Lean 소프트웨어 개발 방법론 중 하나로, 일의 흐름을 시각적으로 표현하여 생산성과 효율성을 높이는 방법입니다. 칸반은 일의 상태를 카드 또는 게시판 등에 시각적으로 표현하여 각 단계에서의 작업의 수량과 진행 상태를 파악하고, 그에 따라 업무의 우선순위를 조절하며 작업을 진행합니다. 이러한 방법은 개발 작업뿐만 아니라 다양한 업무에 적용될 수 있습니다.   

<br/>

<br/>

### 🎈 칸반 보드   

|            백로그             |            To-do(할일)            | In Progress(진행중) <br />WIP:3 | Done(완료) |
| :---------------------------: | :-------------------------------: | :-----------------------------: | :--------: |
| 랜딩페이지<br />로딩속도 개선 |        Todo 푸시 기능 추가        |     Todo 컴포넌트 리펙토링      |            |
|                               | 변경 디자인 시안에 맞도록 CSS수정 |                                 |            |

칸반 보드는 일반적으로 3개의 열(To-do, In Progress, Done)로 구성된 보드를 사용합니다. 각각의 열은 일의 진행 상태를 나타냅니다. 예를 들어, To-do 열은 아직 시작하지 않은 작업을 나타내고, In Progress 열은 현재 진행 중인 작업을 나타내며, Done 열은 이미 완료된 작업을 나타냅니다.

칸반 보드는 일의 상태를 나타내는 열 외에도, 각각의 작업을 나타내는 카드(Card)를 사용합니다. 각각의 카드는 작업에 대한 정보를 담고 있으며, 예를 들어 작업 제목, 작업자, 우선순위 등을 포함할 수 있습니다. 각각의 카드는 해당 작업이 현재 어느 상태에 있는지, 즉 어느 열에 위치하는지 나타내는 레이블을 가지고 있습니다.

칸반 보드를 사용하면, 작업의 진행 상태와 현재 상황을 한 눈에 파악할 수 있기 때문에, 업무의 흐름을 더욱 투명하게 파악하고, 팀 내의 협업과 커뮤니케이션을 원활하게 할 수 있습니다.   

<br>

**In Progress의 특징:**   

WIP:3  :  Work In Progress = WIP 는 현재 진행하고 있는 작업을 의미합니다. 각 업무 단계에 WIP 제한 WIP limit을 둘 수 있는데 WIP제한이 3개라면 세개 이상의 카드가 해당 열에 위치할 수 없게 됩니다.   

WIP를 두는 이유는 업무가 과도하게 쌓이지 않는 원활한 업무 흐름을 위해서입니다.   

WIP 제한을 두는 이유는 한 번에 처리하는 업무의 양을 최소화하여 팀원이 한 번에 여러 업무를 동시에 진행해서 생기는 맥락 전환의 문제를 방지할 수 있고, 업무 흐름을 적당하게 유지시켜 업무가 차근차근 처리될 수 있도록 합니다.   

<br/>

<br/>

#### ◼ 명확한 팀 정책 설정   

칸반을 잘 활용하기 위해서는 정책을 설정해야 합니다.   

프로젝트가 본격적으로 시작하기 전에 정하면 좋을 정책은 아래와 같습니다.   

1. 칸반의 열을 정의하고, WIP limit을 결정.

2. 회의 시간 및 해당 회의에서 논의할 내용

3. 팀원 간 소통 원칙

4. 칸반 티켓을 언제, 어떻게, 누가 추가할지

   

<br/>

#### ◼ 회의와 리뷰를 통해 함께 업무를 개선합니다.   

보통 칸반을 사용하는 경우, 데일리 칸반 회의와 주간 보충 회의를 진행합니다.

**데일리 칸반 회의(Daily Kanban Meeting)는 일일 회의로**, 팀원들이 하루의 시작 전에 진행 상황과 문제점 등을 공유하는 회의입니다. 일반적으로 15분 정도 소요되며, 팀원들이 서로 자신이 담당하는 작업을 소개하고, 그 작업의 진행 상황과 문제점을 공유합니다. 이를 통해 팀 내에서 작업의 우선순위를 조정하고, 작업을 보다 효율적으로 진행할 수 있습니다. 예를 들어, 개발팀에서는 다음과 같은 내용을 공유할 수 있습니다.

- A 개발자: 어제 완료된 작업들 확인하고, 오늘 작업 예정인 task #1234 시작할 예정입니다.
- B 개발자: 현재 작업중인 task #5678의 문제점 발견, 진행을 잠시 중단하고 원인 파악 중입니다.
- C 개발자: 오늘 예정된 작업 외에 급한 이슈 #9101 발생, 우선 처리 예정입니다.

**주간 보충회의(Weekly Kanban Review)는 주간 회의로,** 전 주의 작업 진행 상황과 문제점 등을 공유하는 회의입니다. 일반적으로 30분에서 1시간 정도 소요되며, 팀원들이 전 주의 작업 진행 상황, 완료된 작업의 수, 진행 중인 작업의 문제점과 개선 방안 등을 공유합니다. 이를 통해 팀 내에서 작업의 전반적인 상황을 파악하고, 문제점을 해결하기 위한 계획을 수립할 수 있습니다. 예를 들어, 마케팅팀에서는 다음과 같은 내용을 공유할 수 있습니다.

- 지난 주 마케팅 캠페인 결과 공유 및 피드백
- 현재 진행 중인 프로젝트의 문제점 발견 및 해결 방안 논의
- 다음 주 예정된 작업 계획 및 우선순위 조정   

   

격주 혹은 월간 KPT회고를 진행해도 좋다.

<br>

#### ◼ 칸반의 실천법   

- 업무 시각화
- 진행 중인 업무 제한
- 흐름 관리
- 명확한 프로세스 정책
- 피드백 루프 구현
- 협력적인 개선, 실험적인 발전

<br/>

#### 💡 무엇보다 가장 중요한건 직위에 관계 없이 리더쉽을 발휘해야 업무 효율이 높아진다.   

칸반은 팀장만 관리하는 것은 아닙니다. 각 팀원도 칸반을 보고 WIP 제한을 늘리거나 줄이는 것을 제안할 수 있고, 새로운 업무 티켓을 발행하거나 기존 업무 티켓의 진행을 도울 수 있습니다. Pre-Project에서도 팀원 모두가 합심해서 리더십을 발휘해야 합니다. 아쉽게도 프론트엔드 개발자와 백엔드 개발자가 개발 단계에서는 직무 간 도움을 주기는 쉽지 않습니다. 다만 API 설계나 요구사항 명세서를 적는 기획 단계에서는 서로 어떤 기능을 더 구현하고 덜 구현할지 충분히 제안하고 의견을 나눌 수 있습니다.

현장에서도 신입 개발자에게 시키는 것을 잘하기를 기대하지만, 또한 작은 리더십을 발휘하여 현재 업무 흐름을 개선하기를 기대하기도 합니다. Pre-Project의 작은 리더십이 쌓여서 큰 리더십을 발휘할 수 있게 성장하기를 기원합니다.

   

**-> GitHub는 칸반과 같이 가볍게 사용하기 위해서 GitHub Issue, GitHub Milestone이 있다.**   

   

#### 🔑 GitHub Issue, GitHub Milestone 공부 링크

[깃허브 이슈 공부 링크](https://docs.github.com/en/issues/tracking-your-work-with-issues/about-issues)

[깃허브 이슈 템플릿 링크](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/configuring-issue-templates-for-your-repository)

[깃허브 마일스톤 공부 링크](https://docs.github.com/en/issues/using-labels-and-milestones-to-track-work/about-milestones)

<br/>

<br/>

😚 오늘 학습 내용:

GitHub의 Repository, 칸반의 정의와 보드 읽는법, Github Issue, GitHub Milesone사용법과 정의.

오늘도 배움 +1 해간당 ♥💯미민💯

<br/>

<br/>

