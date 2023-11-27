안녕하세요! 리비엔즈입니다 🤗

오늘은 트랜잭션 관련해서 정리를 해보려고 해요! 

# 트랜잭션 (Transaction)
트랜잭션에 대해서 많은 설명이 있습니다
- 여러 쿼리를 논리적으로 하나의 작업 단위로 묶는 것
- 더 이상 나눌 수 없는 가장 작은 하나의 단위
- 데이터베이스의 상태를 변화시키기 위해 수행하는 작업 단위

조금씩 다른 말들이지만 공통되는 부분도 찾아볼 수 있죠 🤔
**'하나의 작업 단위로 수행된다'**가 공통적으로 나오는 얘기인 것 같네요 😊

결과적으로 트랜잭션은 _**<span style="color:olivedrab">데이터베이스에서 수행되는 여러 작업을 하나의 논리적 단위로 수행하는 것</span>**_이라고 이해할 수 있겠습니다.
# 트랜잭션 예시

트랜잭션 관련해서 간단한 예시를 보고 갑시다
보통 트랜잭션을 설명할 때 많이 사용하는 예시인 은행 계좌 예시를 들어볼게요 💸


> 사용자 A의 계좌 잔액: $100
사용자 B의 계좌 잔액: $0

A 계좌에서 $100을 B 계좌로 이체하려고 합니다 🤔
이체는 다음의 두 단계를 거쳐야 하겠죠!

> 1. A 계좌에서 $100 차감
2. B 계좌에 $100 추가

두 단계를 거친 후에 A계좌와 B계좌의 상태는 다음과 같을 것입니다 😊


> A 계좌 잔액: $0
B 계좌 잔액: $100


여기서 중요한 것은 A 계좌에서 돈을 차감하고 B 계좌에 추가하는 두 단계가 하나의 작업 단위로써 모두 성공하거나 실패해야 한다는 것입니다.

만약 A 계좌에서 돈을 차감하는 단계는 성공했지만 B 계좌에 돈을 추가하는 과정에서 실패가 발생한다면 계좌 상태는 다음과 같이 변경될 것입니다
> A 계좌 잔액: $0
B 계좌 잔액: $0

돈이 사라져버렸습니다 😱 

이러한 현상을 방지하기 위해서 위의 송금을 위한 두 단계는 하나의 작업 단위로써 모두 성공하거나 모두 실패해야 합니다 😊

_**트랜잭션**_으로 관리되어야 하는 작업인 것입니다!


# 트랜잭션의 연산 
저는 바로 앞에서 송금을 위한 두 단계는 모두 성공하거나 모두 실패하는 하나의 트랜잭션으로 묶여야 함을 말씀드렸습니다.

그렇기에 트랜잭션은 성공하였을 경우 결과를 반영하는 연산과 실패할 경우 모두 실패하도록 유도하는 연산 두가지를 가집니다. 각각 ```commit```과 ```rollback```인데요 관련해서 설명 드릴게요 👍


> ### 트랜잭션의 연산 - Commit(커밋)
커밋은 트랜잭션이 성공적으로 완료되었고, 그 결과를 데이터베이스에 영구적으로 적용하는 것을 의미합니다. 트랜잭션의 모든 단계가 성공적으로 수행되면, 해당 트랜잭션은 커밋되어 데이터베이스의 상태가 변경됩니다.

> ### 트랜잭션의 연산 - Rollback(롤백)
롤백은 트랜잭션이 실패하거나 중단되었을 때, 해당 트랜잭션이 시작된 시점 이전의 상태로 되돌리는 것을 의미합니다. 실패할 경우 모두가 실패하도록 하는 연산이라고 이해하시면 되겠습니다. 다만 명시적으로 롤백 명령을 생성하여 롤백을 할 수도 있습니다


# 트랜잭션의 성질 ACID

트랜잭션 관련한 두가지 연산 소개드렸습니다 🤗
이어서는 트랜잭션의 성질에 대해서 설명드릴게요!

트랜잭션은 안전하게 수행되기 위해서 ACID 성질을 가집니다.
ACID는 단어들의 앞글자를 따서 모은 말인데요 각각 어떤 것을 의미하는지 먼저 확인해봅시다 🤗

- Atomicity 원자성
- Consistency 일관성
- Isolation 고립성 
- Durability 지속성

자 이제는 ACID의 성질 하나씩 설명드릴게요 👍

## ACID - Atomicity (원자성)
원자적이다라는 말은 컴퓨터과학을 공부하면 숱하게 나오는 단어인 것 같아요

더 이상 나눌 수 없는 원자적 상태를 지님을 의미하는데요 트랜잭션의 Atomicity 역시 트랜잭션이 쪼개질 수 없는 작업임을 의미하는 것이라고 보시면 되겠습니다

물론 트랜잭션은 여러 연산으로 이루어질 수 있습니다. 저희가 위에서 보고 온 송금 예시처럼요!
하지만 그 실행 여부는 모두가 성공하거나 모두가 실패해야 함을 말씀드렸었습니다. 원자성을 그와 같은 의미로 받아들이시면 좋을 것 같아요 👍 ```All Or Nothing```으로 이해하셔도 좋을 것 같습니다 🤗


이전에 트랜잭션 연산에서 설명드린 ```rollback```연산이 이 원자성과 관련이 있습니다!
트랜잭션이 롤백되면 어떤 변경 사항도 데이터베이스에 적용되지 않으며, 데이터베이스는 이전의 일관된 상태를 유지하는 점에서 연관이 있다고 볼 수 있는 것이죠!

## ACID - Consistency
일관성입니다

트랜잭션이 실행되기 전과 실행이 완료된 후에도 데이터 베이스가 항상 일관된 상태에 있어야 함을 이야기하는 것이 일관성이에요 🤗

트랜잭션의 결과가 데이터베이스에서 정의한 모든 규칙과 제약조건을 어겨서는 안 됨을 의미합니다.

데이터베이스 무결성 제약 조건을 만족해야 한다고 간단히 이야기할 수도 있겠네요 😊

> #### 데이터베이스 무결정 제약조건
데이터베이스 무결성 제약조건은 데이터베이스 내의 데이터가 정확하고 일관성 있게 유지되도록 하는 규칙이나 조건을 말합니다. 이러한 제약조건은 데이터베이스 설계 및 관리 단계에서 정의되며, 데이터의 무결성을 유지하고 부정확한 데이터가 데이터베이스에 저장되지 않도록 하는 역할을 합니다.



## ACID - Isolation
고립성입니다 

어떤 트랜잭션에서 지정된 연산이 수행되고 있다면 다른 트랜잭션에 영향을 주거나 받아서는 안된다는 성질입니다.

A 계좌에서 B계좌로 $100를 이체하는 트랜잭션이 진행되고 있는 도중에 B계좌에서 A계좌로 $100을 이체하려고 한다면 일관성을 깨트릴 수 있겠죠! 

A 계좌에서 B계좌로 $100를 이체하는 트랜잭션이 끝난 후에 B계좌에 대한 트랜잭션이 실행되는 것이 바람직해 보입니다 🤗

<span style="color:slateblue">_**하지만! 트랜잭션이 끝날 때 까지 마냥 기다리는 것은 성능 상 좋지 않을 수도 있어요**_</span>

예를 들어서 다음의 상황을 생각해볼까요?
> $10,000,000를 가지고 있는 A계좌에서 천만명에게 1달러씩 송금

A계좌는 천만 명에게 모두 송금이 끝날 때 까지 하나의 트랜잭션 차지가 될 것입니다.
완전 고립 정책을 유지한 상태로 다른 트랜잭션에서 A 계좌에 접근하려면 많은 시간이 걸리겠죠 🤔

대부분의 서비스에서는 다수의 트랜잭션이 동시에 실행되는 경우가 많습니다. 마냥 기다리게 설계할 경우 성능 문제가 있을 수 있으니 이를 위해서 무조건적인 트랜잭션 격리가 아닌 다양한 트랜잭션 격리 수준이 존재한답니다

이어서는 트랜잭션 격리 수준 4가지를 설명드릴게요 🤗

### ACID - Isolation 격리 수준
말씀드린 것처럼 트랜잭션은 다양한 격리 수준으로 관리될 수 있습니다
격리 수준은 크게 다음 4가지로 볼 수 있습니다
- Read Uncommitted(커밋되지 않은 읽기)
- Read Committed(커밋된 읽기)
- Repeatable Read(반복 가능한 읽기)
- Serializable(직렬화)

위에 위치한 격리 수준일 수록 속도는 빠르지만 데이터의 일관성을 잘 보장하지 못하고 아래에 위치한 격리 수준일 수록 속도는 느리지만 데이터의 일관성을 보장할 수 있게 된답니다 😊

각 격리 수준이 어떠한 방식으로 적용되는지 간단한 설명 첨부드립니다 🚀
자세한 예시를 참고하시고 싶은 분은 해당 포스팅 시리즈의 [다음 글](https://velog.io/@libienz/%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-%EA%B2%A9%EB%A6%AC-%EC%88%98%EC%A4%80%EC%9D%84-%EC%98%88%EC%8B%9C%EB%A1%9C-%EC%95%8C%EC%95%84%EB%B3%B4%EC%9E%90)참고 부탁드려요

> #### Read Uncommitted(커밋되지 않은 읽기)
 가장 낮은 격리 수준으로, 한 트랜잭션이 다른 트랜잭션에서 아직 커밋되지 않은 데이터를 읽을 수 있습니다. 이는 다른 트랜잭션이 변경 중인 데이터를 읽을 수 있어 문제가 발생할 수 있습니다.

> #### Read Committed(커밋된 읽기)
 트랜잭션이 커밋된 데이터만 읽을 수 있습니다. 따라서 한 트랜잭션이 다른 트랜잭션에서 수정 중인 데이터를 읽는 것은 허용되지 않습니다.

> #### Repeatable Read(반복 가능한 읽기)
 트랜잭션이 읽은 데이터는 트랜잭션이 완료될 때까지 다른 트랜잭션에 의해 수정되지 않습니다. 이로 인해 같은 쿼리를 여러 번 실행해도 동일한 결과가 나타납니다.

> #### Serializable(직렬화)
 가장 높은 격리 수준으로, 동시에 실행되는 여러 트랜잭션 간에도 결과가 일관성 있게 유지됩니다. 이는 동시에 여러 트랜잭션이 실행되어도 마치 순차적으로 실행되는 것처럼 보이도록 보장합니다.

## ACID - Durability
마지막 지속성입니다 🤗

트랜잭션이 성공적으로 수행되면 영구적으로 데이터 베이스에 반영이 되어야 함을 의미합니다.  다시 말해, 트랜잭션이 성공하면 해당 트랜잭션에 의해 변경된 데이터는 시스템에서 영원히 보존되어야 함을 의미하죠 👍

커밋이 지속성과 관련있다고 말씀드렸었습니다! 즉, 트랜잭션이 커밋되면 해당 트랜잭션에 의한 변경 사항은 영구적으로 데이터베이스에 저장되며, 장애나 시스템 다운 시에도 손실되지 않음을 다시 한번 말씀드릴 수 있겠네요 👍

# 정리
지금까지 트랜잭션이 작업의 논리적 단위라는 것과 트랜잭션에는 commit과 rollback이라는 연산이 있으며 트랜잭션은 ACID 성질을 가진다는 것에 대해서 설명 드렸습니다 🤗

찾아주시고 제 글로 공부해주신 분들 모두 감사드립니다 🙇‍♂️

# Reference

https://www.youtube.com/watch?v=taUeIi6a6hk
https://gyoogle.dev/blog/computer-science/data-base/Transaction.html
https://iingang.github.io/posts/DB-Integrity-constraint/