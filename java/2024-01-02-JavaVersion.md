안녕하세요 사한입니다.😎
오늘은 자바 버전에 관한 간단한 이야기를 해보려 합니다!😁

# 자바 버전의 역사

![](https://velog.velcdn.com/images/ks0927/post/0b7f6ae5-db57-49bb-8293-44d374d9c49e/image.png)

자바는 95년 처음으로 릴리즈된 뒤 1,2 년 간격으로 안정적인 버전을 출시하였습니다.

사진만 봐도 오밀조밀한게 보이시죠? 🤣

하지만 **자바 6** 버전 이후 이러한 흐름이 끊기게 됩니다. 😭

![](https://velog.velcdn.com/images/ks0927/post/35da80b1-e0c6-4faa-8c11-f8ecc09de88f/image.png)

자바 6버전 이후 **자바 7 **버전이 나오기 까지 약 5년이 걸리게 됩니다.

그 이유로는 Sun Microsystems가 오라클에 인수되고 OpenJdk를 구성하는 등 여러 가지 일이 있었기 때문입니다.

오랜 시간이 걸렸음에도 기대했던 기능들을 모두 반영하지 못한채로 7버전을 출시하게 됩니다.

자바 8과 9에서의 변화는 프로그래밍 생태계의 변화와도 연관이 있습니다.
핵심적인 부분만 가볍게 살펴 보면

> **자바 8**에서는 빅데이터가 떠오르면서 병렬처리에 대한 관심이 높아지면서 Stream API가 추가되었습니다.
>
> **자바 9**에서는 개발자가 라이브러리와 대규모 응용 프로그램을 쉽게 구성하고 관리할 수 있도록 모듈화를 지원하게됩니다.

자바 10이 출시된 후 이제부턴 주기적으로 버전을 출시하겠다고 선언합니다. 😤

![](https://velog.velcdn.com/images/ks0927/post/39f344b8-b956-4ff0-a583-9ae7fe11030e/image.png)

**6개월마다 메이저 버전**을 출시 하고, **3년을 주기로 Long Term Support(LTS) 버전**을 출시하기로 합니다!

>**LTS**는 기존 버전과 다르게 새로운 버전이 나와도 지속적으로 지원을 해주는 버전을 의미합니다.

하지만 자바 17버전 이후 LTS버전을 **2년 주기**로 출시하기로 변경합니다. 😅

![](https://velog.velcdn.com/images/ks0927/post/8beafa9b-61f2-4157-a2b8-24d027ef53e0/image.png)

2024년 새해를 맞은 현 1월 1일 기점으로 자바는 21버전까지 출시되었습니다.

# 자바 LTS 버전 현황

포스팅 사진들을 자세히 보신분들이면 알아차렸겠지만 색칠된 **자바8** ,**자바11**, **자바17**, **자바21** 버전이 자바 LTS 버전입니다!😎

Oracle JDK 기준 지원기간을 확인해봅시다.

![](https://velog.velcdn.com/images/ks0927/post/aa435474-4e1e-4815-9a0c-0cd99debbe81/image.png)

LTS 버전은 약 8번간 보안 업데이트와 수정이 지원됩니다.

자바 8 버전은 사용자도 많고 인기도 많아서 30년까지 연장하게 되었습니다.

자바 11 버전은 26년, 자바 17 버전은 29년, 자바 21 버전은 31년 까지 유료지원을 받을 수 있습니다!


# 자바 버전 사용현황

jetbrains의 2021, 2022, 2023년 설문조사를 살펴봅시다!

![](https://velog.velcdn.com/images/ks0927/post/4ce3cd0b-1b22-4ddd-9a77-a34a0badab2f/image.png)

이중에서 사용률이 높은 버전들을 살펴보면 자바8, 자바11, 자바17 버전이 보이는데요 공통점은 lts 버전입니다 ㅎㅎ

해당 세가지 버전만 따로 사용률을 확인해보면

![](https://velog.velcdn.com/images/ks0927/post/315039fb-b5e5-4886-b7b1-ef6d9f41a0c6/image.png)

- 자바 8버전은 **하락**하는 추세
- 자바 11버전은 22년도에 사용률이 상승했지만 23년도에는 하락하는 **미묘**한 모습
- 자바 17버전은 **상승**하는 추세

jetbrains의 설문조사로만 판단하기엔 아쉽죠? 조금 더 인사이트를 드리면

**여기어때 개발팀**에서는 자바 8 버전에서 ```자바 17버전```을 22년도에 도입하였고

우아한형제들에서 주최하는 **우아한테크코스 6기**의 선발 과정 미션에서도 ```자바 17버전```을 사용하기 시작했습니다. (지원했었습니다ㅎㅎ)

# 그래서 무슨 버전을 써야해요? 🤔

사실 회사를 다니고 있거나, 프로젝트를 진행하고 계시다면 이전부터 써오던 관습도 있을것이고 어떤 서비스를 개발하느냐에 따라서도 자바 버전 선택은 여러가지가 될 수 있다고 생각합니다.

**그.래.서.** 저는 사용률이 높은 자바 8 버전까지의 특징, 자바 9부터 11버전까지의 특징, 자바 12부터 17버전까지의 특징을 알려드릴테니 여러분들이 판단해보시는 것도 좋은 공부가 될 것이라고 생각 됩니다 ㅎㅎ

![](https://velog.velcdn.com/images/ks0927/post/11e10a6a-15b7-4b6b-b48e-17eabcb167f6/image.png)

# ~ 자바 8


### lambda

**람다식**은 ```익명 함수```를 생성하기 위한 식을 지칭하는 용어입니다.

쉬운 말로 표현하면 ```메서드를 하나의 식 으로 축약 표현한 것``` 이라고 생각하면 좋을 것 같습니다.

예시를 보면
```java
    public int addOperation(int x, int y) {
        return x + y;
    }
```
해당 메서드를 람다식으로 표현하면
```java
	(int x, int y) -> x + y;
```
간단하게 표현할 수 있죠?

```java
	List<Integer> numList = Arrays.asList(0, 1, 2);

    // 1. 반복문 - Iterator
    for(Integer num: numList) {
        System.out.println(num);
    }
    
    // 2. 람다식 사용
    numList.forEach(x -> System.out.println(x));
```
외부에서 forEach라는 메서드에 람다식을 파라미터로 전달할 수 도 있습니다.

### method references(메서드 참조)

**메서드 참조**는 람다 표현식의 한 형태로, 이미 정의된 메서드를 재사용하기 위한 방법입니다. 

메서드 참조는 특정 객체 또는 클래스의 메서드를 참조하는 데 사용되며, 이를 사용하면 코드를 더욱 간결하게 만들 수 있습니다.

메서드 참조는 다음과 같은 형태를 띄고 있습니다.
- ```클래스 이름::메소드 이름```
- ```생성자::new```

사용 예시를 보여드리겠습니다.
```java
	List<String> list = Arrays.asList("Apple", "Banana", "Cherry");
    // 메서드 참조 사용
	list.forEach(System.out::println);
```

```java
	Stream<User> stream = list.stream().map(User::new);
```

### stream

**스트림**은 ```데이터 처리 연산을 지원하도록 소스에서 추출된 연속된 요소``` 입니다.

스트림은 복잡하고 큰 데이터 처리 작업을 몇 줄의 코드로 처리할 수 있으며, 람다식을 파라미터로 사용하는 경우가 많습니다.

스트림에 대해서는 지난 비스트로에서 **리비엔즈**님께서 작성하신 [포스팅](https://velog.io/@libienz/Java%EC%9D%98-Stream)이 있으니 참고하시면 좋을 것 같습니다! 😁

간단한 사용예시를 보여드리면 다음과 같습니다.
```java
	List<String> list = Arrays.asList("Apple", "Banana", "Cherry");
	list.stream()  // 스트림 생성
    	.filter(s -> s.startsWith("A"))  // 'A'로 시작하는 요소 필터링
    	.forEach(System.out::println);  // 남은 요소 출력
```

### optional

**Optional** 클래스는 ```null 값을 가질 수 있는 객체를 감싸는 래퍼``` 클래스입니다. 

optional을 통해서 NullPointerException을 방지하고, null을 반환할 수 있는 메서드를 보다 안전하게 사용할 수 있습니다. 😍

간단한 사용예시를 보여드리면 다음과 같습니다.

```java
	// null일 수 있는 getString() 메서드 반환값을 Optional로 감쌈
	Optional<String> optional = Optional.ofNullable(getString()); 

	// 값이 존재하면 출력
	optional.ifPresent(System.out::println);
```
### 인터페이스 default, static method

자바 8 이전에는 인터페이스에 정의된 모든 메서드를 구현해야 했기에 메서드가 추가되면 인터페이스를 구현하는 클래스에도 구현을 해야만 하는 불편함이 있었습니다.

하지만 default method는 인터페이스에서 메서드 내용을 정의하고, 그대로 재사용할 수 있게 해줍니다.

```java
    public interface Printer {

        String getName();

		// 디폴트 메서드 추가
        default void printHelp() {
            System.out.println("Help");
        }

    }

    public class HelloPrinter implements Printer {

        @Override
        public String getName() {
            return "Hello";
        }
    ]
    
```

인터페이스 Printer를 구현하는 다른 클래스인 ByePrinter가 생성되어도 getName() 메서드만 구현할 뿐 디폴트 메서드인 printHelp()는 구현하지 않아도 됩니다.

또한 기존의 구현 클래스를 변경하지 않고도 인터페이스인 Printer에 새 메서드를 추가할 수 있어, 소스 코드의 호환성을 유지하면서 계속해서 인터페이스를 업데이트할 수 있습니다.

그리고 자바 8부터는 인터페이스에서도 static method를 정의할 수 있게 됩니다.

```java
    public interface Printer {
    	...
        
		//스태틱 메서드 추가
        static void printHello() {
            System.out.println("hello");
        }

    }
    
    public static void main(String[] args) {
    	//스태틱 메서드 사용
    	Printer.printHello();
	}
```
# ~ 자바 11

### 모듈화

모듈에 대한 내용은 방대하기 때문에 간략하게 이야기 드리겠습니다. 😅

패키지는 클래스들의 묶음이고 **모듈**은 ```패키지의 묶음``` 이라고 생각하면 간단할 것 같습니다.

기존의 자바는 모듈의 패키지속 클래스를 외부에 숨길수 없었습니다.

하지만 자바8 이후 모듈을 만들기 위해 ```Jigsaw 모듈 시스템``` 이라는 기능을 제공하기 시작합니다.

이 기능을 사용하면 캡슐화를 통해 각 모듈이 제공하는 기능만을 외부에 공개하고, 모듈의 내부 동작은 숨길 수 있습니다. 

이렇게 하면 모듈의 내부 구조를 자유롭게 바꿀 수 있으며, 다른 사람이 모듈을 사용할 때도 그저 제공하는 기능만을 알면 됩니다.

### var

**var**은 자바 10에서 도입되었으며, 지역 변수의 타입을 컴파일러가 자동으로 추론하게 하는 기능입니다.

var는 인스턴스 변수로 사용이 불가능하고 반드시 초기화를 해야 합니다.

간단한 사용예시를 보여드리면 다음과 같습니다.

```java
    var list = new ArrayList<String>();  // ArrayList<String> 타입 추론
    var stream = list.stream();  // Stream<String> 타입 추론
    
    for (var data : list) {
       ...
    }
```
### gc 개선

자바 9부터 11까지의 버전은 가비지 컬렉터의 성능 향상에 중점을 두었습니다. 

제가 이전에 비스트로에서 발표한😁 GC 알고리즘인 **G1**(Garbage First)이 기본 가비지 컬렉터로 설정되었고, **ZGC**(Z Garbage Collector)와 같은 가비지 컬렉터가 실험적으로 도입되었습니다.

### Collection Factory Method 기능 강화

Set, List, Map 인터페이스에 불변(Immutable) 속성을 지닌채로 생성할 수 있는 메서드 of가 추가 되었습니다.

사용 예시를 바로 보시죠.

```java
    List<String> list = List.of("Apple", "Banana", "Cherry");  // 불변 리스트 생성
    Set<String> set = Set.of("Apple", "Banana", "Cherry");  // 불변 셋 생성
    Map<String, Integer> map = Map.of("Apple", 1, "Banana", 2, "Cherry", 3);  // 불변 맵 생성
```

> 불변 속성 관련 복사,반환 신규메서드 
>
>  **copyOf()**
> 
> - List.copyOf();
> - Set.copyOf();
> - Map.copyOf();
>
> **toUnmodifiable()**
> 
> - toUnmodifiableList();
> - toUnmodifiableSet();
> - toUnmodifiableMap();

### 문자열 Method 추가

**isBlank**: 문자열이 비어있거나 공백이면 True 반환
```java
String str1 = "";
System.out.println(str1.isBlank());  // true 출력

String str2 = " ";
System.out.println(str2.isBlank());  // true 출력

String str3 = "Hello";
System.out.println(str3.isBlank());  // false 출력
```

**lines**: 줄 단위로 나뉘어 있는 문자를 스트림으로 반환
```java
String str = "Hello\nWorld\n!";
str.lines().forEach(System.out::println);
// 출력:
// Hello
// World
// !
```

**strip**: 문자열 양쪽의 공백 제거
```java
String str = " Hello, World! ";
System.out.println(str.strip());  // "Hello, World!" 출력
```

**stripLeading**: 문자열 앞의 공백 제거
```java
String str = " Hello, World!";
System.out.println(str.stripLeading());  // "Hello, World!" 출력
```

**stripTrailing**: 문자열 뒤의 공백 제거
```java
String str = "Hello, World! ";
System.out.println(str.stripTrailing());  // "Hello, World!" 출력
```

**repeat**: 문자열을 파라미터로 주어진 수 만큼 반복
```java
String str = "Hello";
System.out.println(str.repeat(3));  // "HelloHelloHello" 출력
```

# ~ 자바 17

### Record Data 클래스
**Record**는 자바 14에서 프리뷰 기능으로 처음 소개되었고, 자바 16에서 정식 기능으로 확정되었습니다. 

Record는 ```불변의 데이터 컨테이너```로서, 간결한 문법을 통해 클래스를 정의할 수 있습니다. 

기존에 getter, setter, equals, hashCode 등을 명시적으로 작성해야 했던 부분을 자동으로 구현해주며, 모든 인스턴스 필드를 초기화해주는 생성자가 생성됩니다.

다만 Record Class는 상속이 불가능합니다. (모든 필드는 “private final ...”로 선언이 되기때문입니다.)

DTO의 상태가 변경되지 않아야 하는 경우에는 클래스대신 Record를 사용하면 편리할 수 있겠네요! 

사용 예시는 코드로 확인해 봅시다! 😎
```java
    public record Point(int x, int y, String name) {
    }

    public static void main(String[] args) {
        Point userPoint = new Point(10, 20, "kim");

        // kim 출력
        System.out.println(userPoint.name());

        // 10 출력
        System.out.println(userPoint.x());

        // 20 출력
        System.out.println(userPoint.y());

        // false 출력
        System.out.println(userPoint.equals(new Point(10, 90, "kim")));

        // Point[x=10, y=20, name=kim] 출력
        System.out.println(userPoint);
    }
```
### 텍스트 블록

**텍스트 블록**은 자바 13에서 프리뷰 기능으로 처음 소개되었고, 자바 15에서 정식 기능으로 확정되었습니다. 

텍스트 블록은 ```여러 줄에 걸쳐 문자열을 쉽고 가독성 있게 작성할 수 있도록 도와주는 문법```입니다.

```""" { String 문자열 } """``` 형식을 취하고 있습니다.

간단한 예시로 확인해봅시다.
```java
String text = """
              Hello,
              World!
              """;
// 출력:
// Hello,
// World!
System.out.println(text);
```

### Sealed Class

**Sealed** 클래스는 자바 15에서 프리뷰 기능으로 처음 소개되었고, 자바 17에서 정식 기능으로 확정되었습니다. 

Sealed 클래스는 ```상속을 제한할 수 있는 기능```이며, 어떤 클래스가 상속받을 수 있는지 명시적으로 지정할 수 있습니다.

예시를 통해서 알아봅시다!

```java
    sealed abstract class Shape permits Circle, Rectangle { }

    final class Circle extends Shape { }
    final class Rectangle extends Shape { }
    final class Triangle extends Shape { }  // 오류 발생
```
Shape는 sealed로 선언되어 있고 permits을 통해 Circle과 Rectangle 두 클래스만이 Shape를 상속받을 수 있습니다.

하지만 Triangle 클래스는 Shape의 permits 키워드에 명시되어 있지 않기 때문에 Shape를 상속받을 수 없습니다. 

sealed 클래스를 더 알아보면 하위 클래스로 final, sealed, 또는 non-sealed로 선언될 수 있습니다.

- final: 더 이상의 하위 클래스를 가질 수 없음을 의미합니다.
- sealed: 하위 클래스를 가질 수 있지만, 그것들은 permits 키워드로 명시해야 합니다.
- non-sealed: 하위 클래스를 가질 수 있으며, 어떤 클래스든지 상속받을 수 있음을 의미합니다.

이번에도 예시를 통해 알아봅시다!

```java
    sealed abstract class Shape permits Circle, Rectangle, Polygon { }

    final class Circle extends Shape { }  // 더 이상의 하위 클래스를 가질 수 없습니다.

	// 다른 하위 클래스를 가질 수 있지만, 그것들은 `permits`로 명시해야 합니다.
    sealed class Rectangle extends Shape permits Square, NonSquare { }

    final class Square extends Rectangle { }
    final class NonSquare extends Rectangle { }

    non-sealed class Polygon extends Shape { }  // 어떤 클래스든지 상속받을 수 있습니다.
    class Triangle extends Polygon { }
```

# 📚 정리

지금까지 자바 버전에 대한 이야기를 들으시느라 고생하셨습니다! 😀

마지막으로 자바 8버전을 선택한 경우, 자바 11버전을 선택한 경우, 자바 17 버전을 선택한 경우를 한번에 정리해드리겠습니다.

> 1. 자바 8 버전을 선택한 경우
> - 첫 번째 LTS(Long Term Support) 버전으로, 지원 기간이 30년이라는 긴 기간 동안 안정적인 운영이 가능합니다.
> - 국내에서 개발된 프로젝트 중 많은 부분이 자바 8 버전을 사용하고 있어, 호환성 유지를 위해 선택하는 경우가 많습니다.
> - lambda, stream API, optional 클래스, 메서드 참조, 인터페이스의 default/static 메서드 등의 새로운 특징이 도입되었습니다.

> 2. 자바 11 버전을 선택한 경우
> - 모듈화, 'var' 키워드, 가비지 컬렉터(GC)의 개선, 컬렉션 팩토리 메서드의 기능 강화, 새로운 문자열 메서드 등의 새로운 특징이 추가되었습니다.
> - 여전히 광범위하게 사용되고 있는 LTS 버전입니다.

> 3. 자바 17 버전을 선택한 경우
> - 스프링 부트 3.0 이상 버전에서는 자바 17 이상을 지원하며, 지원 기간이 길어 안정적인 운영이 가능합니다.
> - 가비지 컬렉터(GC)의 성능이 8, 11 버전보다 향상되었습니다.
> - 애플의 M1 및 이후 프로세서 탑재 제품군에 대한 정식 지원이 이루어졌습니다.
> - record 데이터 클래스, 텍스트 블록, sealed 클래스 등의 새로운 특징이 도입되었습니다.

# 더 알아보면 좋을 내용

해당 포스트에서는 자바 21 버전에 대한 내용은 다루지 않았습니다. 😥

다만 여러 기업들의 기술 블로그를 살펴보았을때 자바 21 버전에 추가되는 ```Virtual Thread```라는 개념에 주목하고 있는 것 같습니다.

링크를 2개 첨부하니 확인해보세요! 

https://tech.kakao.com/2023/12/22/techmeet-virtualthread/

https://techblog.woowahan.com/15398/

# 참고

https://techblog.gccompany.co.kr/%EC%9A%B0%EB%A6%AC%ED%8C%80%EC%9D%B4-jdk-17%EC%9D%84-%EB%8F%84%EC%9E%85%ED%95%9C-%EC%9D%B4%EC%9C%A0-ced2b754cd7

https://velog.io/@skyepodium/%EC%9E%90%EB%B0%94-Java-8-%EB%B2%84%EC%A0%84-%ED%8A%B9%EC%A7%95

https://www.baeldung.com/java-8-new-features

https://www.jetbrains.com/ko-kr/lp/devecosystem-2023/java/

https://www.youtube.com/watch?v=LcIyHlE2NlA&t=134s

https://kstefanj.github.io/2021/11/24/gc-progress-8-17.html

