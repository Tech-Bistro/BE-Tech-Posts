# Lambda & Stream (Libienz) 


# 람다란❔
- 람다 함수는 프로그래밍 언어에서 사용되는 개념으로 **익명 함수**를 지칭하는 용어  
- 쉬운 말로 표현하면  **메서드를 하나의 식**으로 표현한 것 
- 바로 예시를  보자  
```java
public int addOperation(int a, int b) {
	return a + b;
}
```
- 위의 메서드는 정수 두개를 파라미터로 받아서 더하는 간단한 메서드. 
- 람다식으로 바꾸면 아래처럼 표현이 가능해짐   
```java
(int a, int b) -> a + b
```
- 이전보다 훨씬 간단하다! 
- 이렇게 간단하게 표현된 람다식은  [일급 객체](https://velog.io/@reveloper-1311/%EC%9D%BC%EA%B8%89-%EA%B0%9D%EC%B2%B4First-Class-Object%EB%9E%80)로써 다양하게 활용될 수 있음.    

- 우리가 Person의 컬렉션에서 나이 속성이 24살 이상인 사람들을 따로 모으고 싶다고 가정해보자.
-  람다를 사용하지 않는다면 다음과 같은 메서드를 만들어야 함      
```java
	public List<Person> collectAgeOver24(List<Person> people) {
		List<Person> res = new ArrayList<>();
		for (Person p : people) {
			if (p.getAge() > 24) {
				res.add(p);
			}
		}
		return res;
	}
```
- 람다를 사용하여 일급 객체로써 이용하면 위의 과정을 한줄로 바꿀 수 있다.     
```java
//어떤 방식으로 filtering할지 외부에서 지정!
//나이가 24살 초과만 필터링
personList.stream().filter(person -> person.getAge() > 24) 
```
- 람다는 일급 객체이기 때문에 파라미터로 전달이 가능하고 그 결과 함수의 동작을 외부에서 지정 가능.
- 위의 코드에서도 데이터의 흐름을 필터링을 할 것인데 어떤 조건으로 필터링할 지를 람다식으로 넘겨주고 있는 모습이다. 
- 개발자의 의도가 정확히 드러나면서 코드도 훨씬 간결해지고 번거롭게 클래스와 메서드를 생성할 필요가 없어짐

# 람다의 정체!
- 람다의 정체는 메서드..? 
- 메서드라기엔 함수형 언어가 아닌 자바에서 파라미터로 전달도 가능하고 return대상도 될 수 있고 변수도 될 수 있음..  
- 역시 람다는 메서드가 아니라 객체..? 
- 직접 한번 람다식을 변수로 추출해보자.    
- 우선 인텔리제이를 키고 다음의 람다식을 작성   
```java
() -> System.out.println();
```
- 그 다음에 ctrl + alt + v를 통해 어떤 타입이었는지 추출해보자    
- **Runnable이라는 함수형 인테페이스**가 람다의 정체.       

## 함수형 인터페이스
- 함수형 인터페이스는 추상 메서드가 딱 1개만 있는 인터페이스 
- 인터페이스를 implement하는 클래스가 있어야 동작을 할텐데 우리는 구현체를 만들어준 적이 없는데..?    
- 바로 람다식이 인스턴스를 만들어주고 있었던 것이다! 
- 원래 같았으면 추상 메서드를 구현하는 클래스와 메서드를 작성해야 했을 텐데 람다는 이것을 한방에 처리할 수 있게 해주는 문법을 제공해 주는 것
- 결과적으로 식으로써 함수를 이용할 수 있게 되었다.   

## 람다식은 함수형 인터페이스를 구현한 인스턴스!
- 우리는 람다식이 함수형 인터페이스의 구현체임을 알게 되었다. 
- 그런데 함수형 인터페이스는 추상 메서드가 한 개인데 매번 함수형 인터페이스를 정의해서 람다식이랑 1:1 매핑시켜 사용해야 하는 것일까?
- 그렇지 않다 미리 만들어진 함수형 인터페이스를 이용하면 된다. 
- 애초에 생각해보면 위에서 테스트 해봤던 Runnable도 우리가 만든 적 없다. 미리 정의된 인터페이스일 뿐     
### 잘 만들어진 함수형 인터페이스를 사용하자!
 - 함수형 인터페이스는 이미 매개변수가 있는지, 반환값이 있는지 등등을 기준으로 [java.util.function](https://docs.oracle.com/javase/8/docs/api/java/util/function/package-summary.html)패키지에 많은 함수형 인터페이스들이 이미 만들어져 있음. 
 - 람다식을 사용하고자 할때에는 FunctionalInterface를 만들어서 쓰기 보다는 잘 골라서 쓰면 되겠다   

|함수형 인터페이스|매개 변수  | 메서드 | 반환값 | 
|--|--|--|--|
|  Runnable| X | void run() | X |
|  Supplier<T>| X | T get() | O(T) |
|  Consumer<T>| O(T) | void accept(T t) | X |
|  Predicate<T>| O(T) | boolean test(T t) | O(boolean) |

 위에서 직접 인텔리제이에 작성해보았던 ```() -> System.out.println()```은 매개변수도 없고 반환값도 없었기에 Runnable 함수형 인터페이스로 추출된 것도 이제는 알 수 있겠네요   

## 람다식 정리
- 람다식의 도입으로 자바는 함수형 언어의 특징도 챙기게 되었다.   
- 결과적으로 코드를 간결하게 만들 수 있으며 함수를 만들기 위해 클래스를 생성하고 메서드를 정의하는 등의 동작이 필요 없어졌기에 생산성 또한 높아짐
-  람다식이 Functional Interface의 구현체라는 것과 여러 Functional Interface가 미리 정의 되어 있다는 것을 다시 한번 기억하자 
# Stream
- 스트림은 개울, 시내 물줄기 등의 뜻을 가짐
- 그 의미와 연결해서 Modern Java in Action이라는 책에서는 **데이터 처리 연산을 지원하도록 소스에서 추출된 연속된 요소**라고 설명하고 있음
- 스트림은 Java 8부터 다량의 데이터 처리 작업을 돕기 위해서 추가되었고 데이터 소스가 다르더라도 일단 스트림을 생성하기만 한다면 과거에 그 데이터의 형태가 무엇이었던 간에 같은 방식으로 다룰 수 있게 된다
- 이로써 코드의 재사용성이 높아진다라는 장점을 가진다
- 배열이든 컬렉션이든 파일이든 Stream을 만들어내기만 하면 동일하게 처리할 수 있게 되는 것!

## Stream 사용 방법
- 스트림은 사용하기 위해서 다음 3단계를 알아야 한다
### 스트림 생성 
- 데이터 소스로 부터 스트림을 생성
### 중간 연산
- 원하는 형태로 데이터를 가공
### 최종 연산 
- 원하는 형태로 반환

예시
```java
List<String> names = people.stream() // 생성
						.filter(person -> people.getAge().equals(24)) //중간 연산
						.map(Person::getName)//중간 연산
						.limit(10) //중간 연산
						.collect(toList()); //최종 연산
```
- 자 이제 각 단계별로 한번 살펴보자  
 
 ## Stream 생성
- 컬렉션, 배열, 숫자, 람다식으로부터 Stream을 생성하는 법을 알아보자
  
 ### 컬렉션으로 부터 스트림 생성하기!
 
 - 컬렉션은 이미 스트림을 생성할 수 있는 메서드 stream()을 제공하고 있음.
 - 이를 사용하면 스트림을 생성할 수 있다
```java
private final List<Card> cards;

private boolean hasAce() {
	return cards.stream().anyMatch(Card::isAce); // 스트림 생성 부분 
}
```

### 배열로 부터 스트림 생성하기!
- 배열 역시 정의되어있는 static method를 사용함으로써 스트림을 생성할 수 있음
```java
	Arrays.stream(arr)....
```
### 숫자로부터 스트림 생성하기!
- 임의의 수를 다음처럼 생성할 수 있다.
```java
IntStream intStream = new Random().ints();
```
- 특정 범위의 연속된 정수를 다음 처럼 생성할 수 있다.
```java
IntStream intStream1 = IntStream.range(1,5); //1,2,3,4
IntStream intStream2 = IntStream.rangeClosed(1,5); //1,2,3,4,5
```
- 특정 범위의 난수를 다음과 같이 생성할 수 있다.
```java
IntStream limitedStream = new Random().ints(10,1,10); //10사이즈의 스트림 begin 1, end 10
IntStream unlimitedIntStream = new Random.ints(1,10); //begin1, end 10 사이즈 특정 안함
```
### 람다식으로부터 스트림 생성하기
- 람다식으로부터 스트림을 생성하기 위해서는 ```iterate``` 메서드나 ```generate```메서드를 사용해야 함.
-  iterate먼저 살펴보자
- iterate은 파라미터로 시드 값과 람다 식을 받는다. 
- 시드 값은 람다식에 파라미터로 들어가는 제일 첫번째 값으로 그렇게 반환된 결과는 다시 람다식의 입력으로 들어가기를 반복하게 된다. 
```java
Stream.iterate(0, n->n+2)
	.limit(4)
	.forEach(System.out::println); // 0,2,4,6
```
- generate는 시드 값 없이 람다식의 계산값으로만 스트림을 생성한다.
```java
Stream<Double> randomStream = Stream.generate(Math::random); 
Stream<Integer> oneStream = Stream.generate(()->1); // 1, 1, 1, 1 ...
```

## 중간 연산

- 중간 연산으로 제공되는 여러 메서드를 살펴보자!
- distinct() : 스트림에서 중복되는 데이터를 제거
- filter(Predicate<T> predicate) : 조건을 만족하는 데이터만 남기고 나머지를 제외
- sorted(Comparator<T> comparator) : 정렬 기준으로 정렬 (정렬 기준 없다면 기본 정렬 기준)
- map(Function<T,R> mapper) : 원하는 필드만 뽑아내거나, 특정 형태로 변환

## 최종 연산
- 최종 연산을 사용함으로써 스트림을 닫을 수 있다. 
- 최종 연산으로써 제공되는 여러 메서드들을 살펴보자.
- forEach(Consumer<? super T> action) : 스트림의 데이터를 소모하며 주로 출력하는 용도로 사용 
	- 예시```.forEach(System.out::println)```
- allMatch(Predicate<? super T> predicate) : 모든 요소가 일치하면 true
- anyMatch(Predicate<? super T> predicate) : 하나의 요소도 일치하면 true
- noneMatch(Predicate<? super T> predicate) : 모든 요소가 불일치하면 true
- findFirst() : 조건에 일치하는 첫 번째 요소를 반환
- findAny(): 조건에 일치하는 요소를 하나 반환
- collect(Collector collector) : 스트림의 요소를 수집해 원하는 형태로 반환.
	- Collector는 인터페이스인데 수많은 추상 메서드를 정의해야 collect()의 파라미터로 사용할 수 있음.
	- 하지만 수많은 추상 메서드를 일일이 정의할 수는 없다.
	-  그래서 static 메서드로 많은 것을 미리 정의해준 Collectors를 주로 이용함.
	- 예시 ```.collect(Collectors.toList());``` 데이터를 수집해서 리스트 형태로 반환
	- 예시 ```.collect(Collectors.groupingBy(person -> person.getCountry()));``` person의 country별로 그룹화 하여 맵으로 반환 

## 스트림 정리
- 지금까지 스트림이 3가지 연산을 통해서 사용될 수 있음을 알아보았고 단계별로 스트림을 생성하는 법, 스트림에 중간 연산자를 먹여서 내가 원하는 데이터로 가공하는 법, 최종 연산을 통해 내가 원하는 형태로 받아오는 법을 배웠다.

## 끝
- 스트림과 람다가 내게는 아직 어색하게 느껴진다.  
- 많이 써보고 테스트도 여러번 해보아서 완전히 자기것으로 만들자.
