---
tags:
  - git
  - github
  - education
---
> [!abstract] 빠른 이동
> [[#1. Git Flow]]
[[#2. Github flow]]
[[#3. GitLab flow]]
[[#4. Trunk-Based Development(TBD)]]
[[#5. Scaled Trunk-Based Development(Enterprise형 TBD)]]

>[!quote]
> _“Build software better, together.”_
>  

# Branch 전략

> branch 전략이란?
> 
> 소프트웨어 개발 프로젝트에서 버전 관리를 효율적으로 하기 위해 사용하는 [[워크플로우]]

> [!abstract] branch 전략교육 목적
>  
> 간단한 프로젝트에서 사용하지 않지만 우리는 회사에 들어가 큰 프로젝트를 맡을 사람들이다 따라서 회사에서 사용하는 branch 전략에 대해서 알아보자

> [!note] branch 전략 종류
>
>1. Git Flow
>   1. Github Flow
>   2. GitLab Flow
>   3. Trunk-Based Development(TBD)
>   4. Scaled Trunk-Based Development(Enterprise형 TBD)

## 1. Git Flow

>Git Flow란?
>
>**Git을 사용해 소스 코드를 관리하고 출시하기 위한 브랜치 관리 전략**

### 구성 브랜치

![[image.png]]

> **1. main/master**
> 
>   - 먼저 배포했거나 배포준비가 된 코드를 관리하는 브랜치
>   - 원격 저장소에서는 `origin/master`에 두고 관리한다.
 
> **2. develop**
>    
>   - 다음 배포를 위해 개발 중인 코드를 관리하는 **브랜치**
>   - 개발자들이 함께 작업하는 가장 역동적인 **브랜치**
>   - 코드가 안정화되고 배포 준비가 완료되면 master로 병합 후버전 태그 추가

> **3. feature**
>    
>    - 새로운 기능을 개발할 때 사용하는 **브랜치**
>    - **develop**에서 분기하여 작업하고, 완료 . 후 다시 **develop**으로 병합

> **4. release**
> 
>    - 배포 전 안정화를 위한 브랜치
>    - **develop**에서 분기하여 **QA** 및 최종 테스트 진행
>    - 안정화 후 **master**에 병합하고 버전 태그 추가
   
> **5. hotfix**
>    
>    - 배포된 코드에서 발생한 긴급 버그를 수정하는 브랜치
>    - **master**에서 분기하여 수정후, **master**와 **develop**에 병합

### 장점과 단점

> [! check] 장점
> 
> 1. 브랜치 관리의 명확성
> 2. 배포 안정성
> 3. 협업 효율성
> 4. 버전 관리와 롤백
> 5. 유지 보수에 용이

> [! fail] 단점
> 
> 1. 복잡성
> 2. 다소 높은 진입장벽
> 3. 느린 릴리스
> 4. 팀 규모에 대한 제한
> 5. 유연성의 한계
## 2. Github flow

>Github Flow? 
>
>Github Flow는 깃허브(GitHub)를 기반으로 한 간단하고 유연한 개발 워크플로우로 주요 목표는 신속한 배포와 효율적인 협업을 지원하는 것이다. Github Flow는 Git Flow와 달리 단일 브랜치를 사용하여 개발하는데, 이는 하나의 버전이 만들어지면 바로 배포될 수 있다는 의미이다.

### 브랜치 종류

![[image (1).png]]

1. master/main
2. feature branch
### Github Flow의 사용 방법

1. Branch 생성
2. Commit 작성
3. Pull Request
4. 리뷰 및 피드백
5. 병합
6. 배포
### 장점/단점

>[!success] 장점
> 1. 간단하고 직관적인 구조
> 2. 유연성과 빠른 피드백
> 3. 충돌 최소화
> 4. 지속적인 배포

>[!fail] 단점
> 1. 대규모 프로젝트에 제한적
> 2. 배포 위험성
> 3. 배포 관리의 어려움
## 3. GitLab Flow

>GItLab Flow란?
>
> [[GitLab]]을 사용하는 브랜치 전략으로 간단하면서도 효과적인 개발 프로세스를 지향하며, 다양한 기능들을 통합하여 사용할 수 있다.

### GitLab Flow 브랜치 구조

![[Pasted image 20250311125824.png]]

> 1. Master 브랜치
>    
>    - gitlab flow의 master 브랜치 역활은 git flow의 develop브랜치와 동일하다
>    - master 브랜치는 feature 브랜치에서 병합된 기능에 대해 테스트를 진행
>    - 전체적인 테스트가 진행되어 기능에 대한 보장이 되었다면 production 브랜치로 머지한다
>    - 만약 staging단계를 원한다면 pre-production 브랜치로 머지를 진행한다.

> 2. Feature 브랜치
>    
>    - 특정한 기능(단위 기능)을 구현하는 브랜치이다.
>    - 기능 구현이 완료되면, master 브랜치로 PR(Pull Request)을 날린다. merge 되면 브랜치는 삭제된다

> 3. production 브랜치
>    
>    - gitlab flow의 production 브랜치 역활은 git flow의 master 브랜치와 동일 하다
>    - 테스트가 끝난 기능에 대해 배포를 하기 위한 브랜치이다.

> 4. pre-production 브랜치
>    
>    - 배포 전에 제품을 테스트(QA, 품질검사) 하는 브랜치이다
>    - 테스트가 정상적으로 완료되면, production과 master에 각각 PR(Pull Request)을 날린다.

### 장점/ 단점

> [!success] 장점
> 1. GitLab Flow는 간단하고 직관적인 워크플로우를 제공한다. 주요 브랜치와 명시적인 브랜치 종류를 사용하여 개발 프로세스를 이해하기 쉽게 만든다
> 2. GitLab은 내장된 CI/CD 파이프라인을 제공하므로 빌드, 테스트, 배포 등을 자동화할 수 있다. 이를 통해 안정적인 배포와 빠른 피드백을 얻을 수 있다.

> [!fail] 단점
> 
> 1. GitLab Flow는 비교적 간단한 프로세스를 제공하므로, 대규모 프로젝트에서는 팀 간의 협업과 관리가 어려울 . 수있다.
> 2. GitLab Flow는 특히 지속적인 배포가 강조되는 환경에서 효과적이지만, 프로젝트의 특성에 따라 다른 브랜치 전략이 더 적합할 수 있다.
## 4. Trunk-Based Development(TBD)

> Trunk-Based Development(TBD)란
> 
> 직역: 트렁크 기반 개발
> **개발자가 잦은 소규모 업데이트를 핵심 “트렁크”나 메인 브랜치에 병합하는 버전 제어 관리 방식**

> [!note] 중요!
> 규칙을 잘지키는 것이 중요하다
### 그라운드 룰

1. Trunk 브랜치는 항상 배포 가능한 상태여야 한다.
2. 가능한 짧고 자주 커밋해야 한다.
3. 코드 병합 전에 자동화된 테스트를 거쳐야 한다
4. 코드 리뷰를 수행한다.
5. 긴 기능 개발은 [[피처 플래그]]를 사용한다.
6. 배포는 trunk에서 직접 이루어진다.
7. [[CI]]를 적극 사용한다. 

### 장점 / 단점

> [!check] 장점
> 
> 1. 빠른 피드백
> 2. 지식 공유
> 3. 간결한 작업 흐름

> [! fail] 단점
> 
> 1. 코드 품질
> 2. 팀과 프로젝트 적합성
> 3. [[피처 플래그]] 관리

## 5. Scaled Trunk-Based Development(Enterprise형 TBD)








