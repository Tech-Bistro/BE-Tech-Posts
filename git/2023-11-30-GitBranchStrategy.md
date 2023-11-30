안녕하세요 리비엔즈입니다 😊

최근에 저는 새로운 프로젝트를 진행하기 위해서 이것 저것 준비 중이랍니다 😉

현재 준비 중인 프로젝트가 개인적으로 하고 싶었던 프로젝트이기 때문에 더욱 열심히 준비하게 되는 것 같아요 😄

저는 다음 프로젝트를 위해서 특히 최근 진행했던 프로젝트의 회고를 진행하고 있어요. 이전에 실패했던 부분 만큼은 새로운 프로젝트에서 발전된 모습으로 적용시키고 싶어서 열심히 회고를 진행해보았답니다 😋

회고 중 역시 여러가지 문제점을 발견할 수 있었는데요 이 중에는 Git Branch 전략 관련 문제점도 있었습니다.

이에 오늘 Git Branch 전략 관련해서 정리하면서 다음 프로젝트 대비 내공을 좀 쌓아보려고 합니다 😎

찾아와 주신 분들 감사하고 같이 Git Branch 전략에 대해서 공부해봅시다 👀

# 📂 Git과 브랜치 전략
저희는 개발할 때 Git을 사용하죠!

Git은 버전 관리 시스템(VCS, Version Control System) 중 하나로, 소스 코드나 파일의 변경 이력을 효과적으로 관리하는 도구입니다. Git을 사용하면 여러 사람이 협업하면서 발생하는 코드의 수정, 추가, 삭제 등의 작업을 추적하고 관리할 수 있게 된답니다.

보통 협업을 하는 상황에서는 모두가 같은 작업을 하지 않는 것이 일반적입니다 🤔 누군가는 A기능을 개발하고 누군가는 B기능을 개발하고 있고 누군가는 배포 중인 버전의 오류를 수정하고 있는 상황 처럼 병렬적으로 작업이 이루어지는 것이 일반적인 상황이지요.

따라서 Git에서는 협업을 위한 핵심기능으로써 브랜치와 병합 기능을 제공한답니다. 독립적인 브랜치에서 각 브랜치에 맞는 작업을 수행하고 병합함으로써 효율적인 병렬 작업을 극대화 할 수 있죠!

이러한 브랜치를 관리하는 전략은 여러가지가 있습니다.
# 📂 나의 브랜치 전략..
우선 저는 최근에 진행했던 프로젝트에서 브랜치를 다음과 같이 관리했어요

각 팀원이 이용할 브랜치를 팀원의 이름으로 하나씩 만들어서 기능 단위 구현이 끝날 때마다 main을 향한 PR을 만드는 방식이었습니다. 🤔

팀 규모도 크지 않고 해서 이렇게 naive하게 진행하는 것도 그럭저럭 굴러갈 정도는 되었어요. 오히려 번거로운 절차가 없어서 빠르게 배포하는데에 도움이 되기도 했죠.

하지만 개발이 진행됨에 따라서 작업이 점점 병렬적으로 진행되고 형상 변화를 추적해야 할 때에는 이러한 브랜치 전략이 불편하게 느껴졌던 적이 있습니다.

지속적 운영을 위해서는 잘 정제된 브랜치 전략이 필요하다고 느낀 순간이었습니다 🙂

# 📂 다양한 Git branch 전략들
저처럼 마구잡이로 브랜치를 관리할 수도 있고 그것이 틀린것만은 아닙니다. 팀 단위의 선택일 뿐이죠. 하지만 브랜치를 효율적으로 운용할 수 있는 가이드라인 같은 여러 전략들이 정의되어 있습니다.

그리고 많은 기업들이 팀의 규모와 배포 주기에 맞추어 프로젝트에 맞는 브랜치 전략을 운용하고 있죠.

대표적으로 가장 많이 사용되는 전략은 다음과 같습니다

- GitHub flow
- Git flow

하나는 간단한 관리 방법, 나머지 하나는 체계를 갖춘 꼼꼼하고 복잡한 관리방법인데요 오늘은 이 두가지 전략에 대해서 소개드릴게요 🤗

# 📂 GitHub flow

![](https://velog.velcdn.com/images/libienz/post/2dbf7f29-9485-452e-82cc-67bae14492aa/image.png)

먼저 GitHub flow 입니다!

Github flow는 Github에서 만든 단순한 구조의 브랜치 전략입니다.

Master 브랜치를 중심으로 운영되며 기능 개발, 버그 수정 등의 작업용 <span style="color:indianred">브랜치를 구분하지 않는 단순한 구조입니다.</span>

까다로운 조건 없이 작업할 브랜치를 열고 작업을 완료한 후 PR을 생성하여 merge하는 간단한 전략이죠

단순한 구조이기에 수시로 배포가 일어나는 프로젝트에 유용하다고 합니다 🧐

실제로 우아한 형제들의 안드로이드 모바일 팀도 3주의 주기로 배포를 할 때 즈음 이러한 전략을 사용했다고 하네요 🙂

GitHub flow는 다음의 흐름으로 협업이 진행됩니다.
- 브랜치 생성
- 개발, 커밋, 푸쉬
- PR 생성
- 리뷰, 토의
- 테스트
- Merge

각 단계 하나씩 살펴보시겠습니다 😎

## GitHub flow 단계 1 - 브랜치 생성
![](https://velog.velcdn.com/images/libienz/post/16ce550b-096c-4e00-a445-b5e5abbd9014/image.png)

> 새로운 브랜치를 생성합니다.
새로운 브랜치는 항상 master 브랜치에서 만들어지며 새로 생성된 브랜치는 분류 체계를 갖추지 않습니다.

## GitHub flow 단계 2 - 개발, 커밋, 푸쉬

![](https://velog.velcdn.com/images/libienz/post/eb1c2e5d-95ee-4076-8ab3-2b21221d862e/image.png)

> 생성한 브랜치에서 개발, 커밋 푸쉬를 진행하며 작업합니다 😄

## GitHub flow 단계 3 - PR 생성
![](https://velog.velcdn.com/images/libienz/post/9805f4b6-6b87-4b12-8d76-cdc7cffbfd32/image.png)

> 작업이 완료된 후 PR을 생성합니다.

## GitHub flow 단계 4 - 리뷰, 토의

![](https://velog.velcdn.com/images/libienz/post/c6ce1023-69ae-4396-9018-0d90110d101b/image.png)

> 생성된 PR이 merge 되기 이전 리뷰와 토의가 이루어집니다.

## GitHub flow 단계 5 - 테스트

![](https://velog.velcdn.com/images/libienz/post/3eb2c3ee-77c8-4216-815d-da45ba452011/image.png)

> 리뷰와 토의가 끝난 상태에서 해당 작업 내용을 테스트해봅니다.
배포 시 문제가 발생할 여지가 있다면 추가 작업을 진행합니다.

## GitHub flow 단계 6 - Merge
![](https://velog.velcdn.com/images/libienz/post/3753b3d8-6578-4770-bfe2-ee43a411f0d8/image.png)

> 배포시 문제가 발견되지 않았다면 master 브랜치에 푸시합니다.

# 📂 GitHub flow - 요약
GitHub flow는 위처럼 어떠한 작업이든 Main 브랜치에서 분기하는 브랜치를 새로 만들어 작업 후 다시 메인브랜치로 머지하는 과정을 거칩니다.

기본적으로 master branch에 대한 규칙만 정확하게 정립되어 있다면 나머지 가지들에 대해서는 특별한 관여를 하지 않죠. 흐름이 단순함으로 규칙이 단순해졌다고도 볼 수 있겠습니다.

# 📂 Git flow
![](https://velog.velcdn.com/images/libienz/post/9a569c55-e2ff-4348-a11c-a24c47c9784a/image.png)

이어서 볼 전략은 Git flow 입니다! <span style="color:indianred"> GitHub flow와 다르게 크게 5개의 브랜치를 운영</span>하며 브랜치에 체계화된 규칙을 적용하여 관리합니다

더욱 체계화 시켜 관리하는 형태이기에 배포 주기가 길고 팀의 크기가 클수록 적합한 전략이라고 볼 수 있겠습니다.

그렇기에 현재는 많은 기업에서 표준으로 사용되고 있다고 해요 😊

우선은 5개의 브랜치 각각이 어떤 역할을 수행하는지 먼저 알아봅시다.

## Git flow - 메인 브랜치들
![](https://velog.velcdn.com/images/libienz/post/d3b2e04e-fcba-4018-928a-b5ecc084d90c/image.png)

먼저 메인 브랜치인 ```Master branch```와 ```Develop branch``` 입니다
두개의 브랜치는 삭제되지 않고 항상 남아있다는 특징을 가집니다.
>
#### Master Branch
- 제품으로 배포할 수 있는 버전을 관리하는 브랜치
#### Develop Branch
- 개발자들이 개발 하며 개발 내역을 쌓아가는 브랜치

## Git flow - 보조 브랜치들

![](https://velog.velcdn.com/images/libienz/post/93e4de78-46e1-4ceb-afad-8efa34df9e1c/image.png)

이어서 보조 브랜치인 ```Hotfix Brnach```, ```Release Branch```, ```Feature Branch```입니다.

보조 브랜치들은 메인 브랜치와 다르게 사용을 마치면 삭제된다는 특징이 있습니다!



>
#### feature branch
- develop으로 부터 분기하여 새로운 기능을 생성하는 브랜치
- 기능 구현이 끝나면 develop으로 merge
#### Release branch
- develop으로 부터 분기하여 개발이 완료된 버전의 출시를 위해 QA를 진행하는 브랜치
- 테스트에서 발견된 버그 수정 및 버전 번호, 빌드 날짜와 같은 메타데이터를 준비하는 브랜치
- 기능 개발은 하지 않는다.
#### Hotfix branch
- 배포 중인 master 브랜치로부터 분기하여 버그를 긴급하게 수정하는 브랜치
- 수정이 완료되면 메인 브랜치로 merge
- 여기서 수정하는 버그는 develop과 release에서 거르지 못한 버그임으로 수정이 완료되었을 경우 develop으로 추가 merge

## Git flow - 예시

자 Git flow 전략에서 운용되는 브랜치들을 설명드렸습니다.

다음으로는 제가 만든 예시로 Git flow 전략이 어떻게 적용되는지 확인해볼게요 😊

> #### 리그 오브 레전즈 1.0.0 버전이 현재 서비스 중입니다.
![](https://velog.velcdn.com/images/libienz/post/94edc667-8b8e-40c3-a13b-668f92398e78/image.png)


> #### 1.1 업데이트는 신규 챔피언 두개가 추가됩니다. 해당 개발을 위해서 develop 브랜치에서 feature 브랜치로 분기합니다.
![](https://velog.velcdn.com/images/libienz/post/a006f787-508b-47ed-91d5-f3ef1cbccdcf/image.png)


> #### 1.1버전을 업데이트 하는 와중에 배포 중인 1.0 버전에 오류가 발생했습니다. 핫픽스 브랜치에서 수정을 시작합니다.
![](https://velog.velcdn.com/images/libienz/post/562f09b2-84fc-46de-b5d2-c53fd9cbc7f5/image.png)


> #### 1.0 버전의 버그가 핫픽스로 수정되었습니다. 새로운 버전 1.0.1이 master 브랜치로 올라가 배포되고 develop 브랜치에도 핫픽스를 반영합니다.
![](https://velog.velcdn.com/images/libienz/post/9139e709-d5dd-45d5-8597-e172f18ad9f2/image.png)


> #### 신규 챔피언 개발이 끝나서 순차적으로 develop 브랜치에 merge 됩니다.
![](https://velog.velcdn.com/images/libienz/post/dadf0dbe-26f6-4cd3-a2f0-e22d960fc362/image.png)


> #### develop 브랜치에서 Release Branch로 merge 해서 qa를 진행합니다.
![](https://velog.velcdn.com/images/libienz/post/20bd702e-69a3-429d-a1a1-343254bae759/image.png)



> #### 문제가 없다면 Master 브랜치와 Develop 브랜치로 merge합니다
![](https://velog.velcdn.com/images/libienz/post/ea08d853-2dd9-482a-8245-da853863a4ff/image.png)

# 📂 마무리
지금까지 Git 브랜치 전략 두가지를 정리해보았습니다.

단순한 흐름으로 서비스를 지속적으로 테스트하고 배포하는데에 유리한 GitHub flow와 체계를 엄격히 갖춘 흐름으로 더 높은 수준의 형상 추적을 가능하게 하고 다양한 시나리오에 대비할 수 있는 Git flow를 살펴보았네요 🤗

저는 이후 진행할 프로젝트에선 Git flow를 적용해서 체계를 갖춘 개발을 처음으로 진행해보려고 합니다. 기회가 된다면 이전에 마구잡이로 하던때와 어떤 장점들을 얻을 수 있었는지 후기도 작성해보겠습니다 😄

# 참조
https://hudi.blog/git-branch-strategy/

https://sungjk.github.io/2023/02/20/branch-strategy.html

https://techblog.woowahan.com/2553/

