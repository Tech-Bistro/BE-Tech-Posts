
> 본 포스팅은 AOP의 개념적인 개론과 Spring AOP의 특성만을 다루며 코드를 활용한 사용 예시는 다루지 않습니다.
> AOP의 개념에 접근하시고자 하는 분들이 읽으시면 좋을 것 같아요. 

# ✨ AOP
AOP는 _**Aspect Oriented Programming**_의 약자로 _**관점 지향 프로그래밍 패러다임**_을 말합니다.
AOP는 **관심사의 분리를 허용함으로써 모듈성을 증가**시키는 것이 목적입니다.

이해를 돕기 위해 예시를 드릴게요!
제가 참고했던 자료가 재밌게 예시를 들어서 기억에 남는데 그 예시로 한번 가보겠습니다.

## 🧐 AOP 이해를 위한 예시
주니어 개발자인 Libienz가 회원가입 서비스를 만들었습니다. 메서드를 다음과 같이 구현했어요
![](https://velog.velcdn.com/images/libienz/post/56896d9c-0dea-4a28-87c6-46f4d15736a0/image.png)

그런데 팀장님이 찾아와서 다음과 같이 요청합니다.
> **팀장: 유저가 회원가입에 얼마나 시간을 소비하는지 로그로 남기는 기능을 추가해주세요**

그래서 주니어 개발자 리비엔즈는 다음과 같이 기능을 완성시켰어요

![](https://velog.velcdn.com/images/libienz/post/837b71df-8d6c-463d-903c-bf1c36cac7fc/image.png)

객체지향 개발자 답게 ```stopWatch```라는 객체를 생성하고 이용하여 로그로 남기도록 했죠 

결과적으로 다음과 같이 로그가 잘 남는 모습을 확인할 수 있었습니다.
![](https://velog.velcdn.com/images/libienz/post/314c813e-b7f2-4505-b07c-1dbc326efaf6/image.png)

그런데 팀장님이 나타나서 다음과 같이 말합니다.
> **팀장: 리비엔즈! 너무 좋아요 이제 회원가입 뿐만 아니라 모든 service에 다 같은 형식으로 남겨주세요! **

리비엔즈는 퇴사를 고민합니다.. 왜냐 하면 서비스 메서드가 1억개였거든요.
메서드 하나하나마다 위와 같은 코드를 복붙하기가 너무 힘들었던 것이죠.

그래도 퇴사를 하기 힘들었던 리비엔즈는 자리로 돌아와서 다른 서비스 메서드들에도 스탑와치 기능을 복붙하기 시작합니다.

그런데 리비엔즈는 여기에서 이상한 점을 발견하게 됩니다.
![](https://velog.velcdn.com/images/libienz/post/9c89a61e-ee65-4429-9f4b-ad584ef0d4f7/image.png)


> - **스탑 와치라는 시간을 재는 기능을 구현하기는 했는데 서비스에 이 기능이 들어가는 것이 맞을까..? **
> - **우리가 필요한 핵심 로직이랑 동떨어져 있는 기능 아닌가..?**
> - **이럴 경우 SRP를 위배하는 코드가 되는 것 아닌가?**

## 🛠 부가 기능 
서비스에서 핵짐적인 비즈니스 로직 외에 
- 시간 측정
- 권한 체크
- 로깅

등등의 부가적인 기능을 부가기능이라고 하고 인프라 로직으로도 부릅니다. 
위 예시의 시간 측정도 인프라 로직 중 하나겠네요 🤔

이런 인프라 로직들은 다음의 특성을 가집니다.
- 어플리케이션의 전 영역에서 나타날 수 있다 
- 중복 코드를 만들어낼 가능성 떄문에 유지보수를 힘들게 한다
- 비즈니스 로직과 함께 있을 경우 비즈니스 로직을 이해하기 어렵게 한다.

그리고 이런 인프라 로직은 기능마다 등장하면서 기능들을 횡단하기에 **횡단 관심사 (Cross Cutting Concern)** 라고도 불립니다.
![](https://velog.velcdn.com/images/libienz/post/f0b4e0d7-3d87-48fb-97dd-835d7dd373a4/image.png)

AOP는 이런 인프라 로직을 비즈니스 로직과 섞이게 하지 않고 **분리함으로써 객체지향적 특성을 살리고 모듈성을 증가**시키는 것이 목적입니다.

이제 앞에서 말씀드렸던 두 문장이 어떤 말을 하는지 이해가실 것 같아요 🤗
>
AOP는 _**Aspect Oriented Programming**_의 약자로 _**관점 지향 프로그래밍 패러다임**_을 말합니다.
AOP는 **관심사의 분리를 허용함으로써 모듈성을 증가**시키는 것이 목적입니다.


# 📃 AOP 용어
Aop는 프로그래밍 패러다임인 만큼 여러 언어, 진영마다 구현체를 가집니다. 자바에서는 ```AspectJ``` 이고 스프링은 AspectJ를 이용한 ```Spring AOP```를 제공하죠. 

이어 설명드리는 AOP 용어들은 진영에 종속적인 용어가 아니라 AOP라는 개념 그 자체에서 범용적으로 사용되는 용어들입니다. 자바와 스프링에서도 용어가 많이 등장하니 익혀두시면 좋을 것 같습니다 😊

- Advice
   - 실질적인 부가 기능 로직을 정의하는 곳
- Join Point
   - 추상적인 개념으로 ```advice```가 적용될 수 있는 모든 위치
   - AOP를 적용할 수 있는 메서드의 실행 시점, 생성자 호출 시점, 필드 값 접근 시점 등등...
   - 스프링 AOP는 프록시 방식을 사용함으로 조인 포인트는 항상 메서드 실행 지점이 되게 됨
- Point Cut
   - 조인 포인트 중에서 ```advice```가 적용될 위치를 선별하는 기능
   - 스프링 AOP는 프록시 기반이기 때무에 조인 포인트가 메서드 실행 시점 뿐, 포인트 컷도 메서드 실행 시점만 가능
- Target
   - advice의 대상이 되는 객체
   - 포인트 컷으로 결정된다.
- Aspect
   - advice + point cut을 모듈화 한 것 

> 예시> **JoinPoint**들 중 ```AuthServiceImpl```의 메서드를 **Point cut**으로 지정하여 Around **advice**가 적용되도록 하고 있는 스프링에서의 AOP 예시
> ![](https://velog.velcdn.com/images/libienz/post/ca1abc76-f474-4fe3-b804-6b00bae33d21/image.png)

> cf> 스프링에서는 **커스텀 어노테이션**으로 포인트 컷 지정을 단순화할 수도 있습니다
![](https://velog.velcdn.com/images/libienz/post/58efd383-90b8-44c9-9759-9a8c36d68344/image.png)

# 🔎 AOP의 구현 방법 

이러한 AOP를 구현하는 방법은 크게 다음 3가지 입니다.

- 컴파일 시점에 AOP 봉합
   - 컴파일 하는 시점에 AOP 기능을 Target에 Weaving합니다.
   - 자바의 AOP 구현체 AspectJ에서 사용합니다. 
- 클래스 로드 시점에 AOP 봉합
   - 컴파일 후 클래스 로더가 메모리에 로드 하는 시점에 AOP 기능을 Target에 Weaving합니다.
   - 자바의 AOP 구현체 AspectJ에서 사용합니다. 
- 프록시 패턴 사용 AOP 봉합
   - 타겟 클래스를 프록시로 감싸서 부가적인 기능을 봉합하는 형태입니다. (Decorate)
   - 스프링 AOP가 프록시 기반으로 동작합니다.

> 스프링 예시> ```AuthService```에 Spring AOP를 적용했을 때 ```AuthService```가 CGLIB 프록시로 감싸지는 모습
![](https://velog.velcdn.com/images/libienz/post/a4ee0d51-531d-494e-b9d6-25ba33b669d0/image.png)

# 🔨 스프링에서의 AOP 특징 정리
아주 개론적으로 AOP의 개념에 대해서 말씀 드렸습니다.
앞서 조금씩 말씀드렸는데요 추가적인 내용과 함께 스프링에서의 AOP의 특징을 정리해보겠습니다.

스프링 AOP는 다음의 특성을 가집니다.
- 프록시로 AOP가 구현되었다. (DI, IoC 환경과 잘 맞음)
- 프록시로 구현되었기에 AOP 기능이 봉합되는 weaving이 Run time 시에만 가능하다.
- AOP를 적용할 Join Point는 메서드만 가능하다. (객체 접근 등등의 조인 포인트 불가능)
- Advice로 Before, AfterReturning, AfterThrowing, After, Around가 제공된다.
- AspectJ의 기능을 이용함으로써 구현되었다.

AspectJ와의 차이점은 다음과 같이 정리할 수 있겠네요

![](https://velog.velcdn.com/images/libienz/post/0c1d2519-de62-49a6-ab48-dd88605a9847/image.png)



# 참고

https://velog.io/@backtony/Spring-AOP-%EC%B4%9D%EC%A0%95%EB%A6%AC  

https://www.youtube.com/watch?v=Hm0w_9ngDpM  

https://www.youtube.com/watch?v=hjDSKhyYK14  

https://ittrue.tistory.com/232
