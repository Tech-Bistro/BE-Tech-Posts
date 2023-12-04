안녕하세요 사한입니다!

오늘은 함수나 메서드를 호출할 때 인자를 전달하는 방식인 

**Call by Value** 와 **Call by Reference** 

두가지 방식을 자바에서 어떻게 사용하고있는지 알아 보겠습니다.😁

 ## Call by Value

- Call by Value는 실제 값(Value)을 복사하여 함수, 메서드에 전달합니다. Pass by Value 라고도 부릅니다.
- 따라서 메서드를 호출하는 호출자(Caller)의 변수와 수신자(Callee)의 파라미터는 복사된 서로 다른변수입니다.
- 값만을 전달하기 때문에 수신자의 파라미터를 수정해도 호출자의 변수에는 아무런 영향이 없습니다.
- 이렇듯 안전한 방식이지만 큰 데이터를 복사하는 데에는 많은 시간과 메모리가 필요하므로 비효율적일 수 있습니다.

## Call by Reference

- Call by Reference 는 변수의 참조(주소)를 직접 함수에 전달합니다. Pass by Reference 라고도 부릅니다.
- 참조를 직접 넘기기 때문에 호출자의 변수와 수신자의 파라미터는 완전히 동일한 변수입니다.
- 따라서 메서드 내에서 파라미터를 수정하면 그대로 원본 변수에도 반영됩니다.
- 이는 메모리와 시간을 절약할 수 있는 효율적인 방식이지만, 실수로 원래 변수의 값을 변경하는 위험이 있습니다.

## 자바에서는?
지금까지 Call by Value 와 Call by Reference에 대해 알아보았는데 그렇다면 Java 에서는 어떤 방법을 사용할까요?

Java는 Call by Reference 라고 오해하시기 쉽지만 Java 는 오직 **Call by Value** 로만 동작합니다.

## Jvm 메모리
자바의 Call by Value 동작을 이해하기전에 런타임중 변수 생성 시 메모리에 어떤 식으로 저장되는 지 알아야 합니다.

![](https://velog.velcdn.com/images/ks0927/post/5ba94c40-1241-46b9-989a-7acef758239a/image.png)

위 사진은 이전 제 포스트 [Jvm과 가비지 컬렉션(GC)](https://velog.io/@ks0927/Jvm%EA%B3%BC-%EA%B0%80%EB%B9%84%EC%A7%80-%EC%BB%AC%EB%A0%89%EC%85%98GC#jvm%EC%9D%B4%EB%9E%80)을 보셨다면 익숙하실수도 있겠네요😁😁

Jvm과 GC에 대해 설명하면서 보여드린 실행 중 프로그램의 정보가 올라가 있는 Jvm Memory 사진입니다.

우리가 Java 에서 변수를 선언하게 되면 위 사진의 Stack 영역에 할당됩니다.

원시 데이터 타입 (Primitive Data Type) 은 Stack 영역에 변수와 함께 저장되고

참조 데이터 타입 (Reference Data Type) 객체는 Heap 영역에 저장되고, Stack 영역에 있는 변수가 객체의 주소값을 갖고 있습니다.

>### 원시 데이터 타입과 참조 데이터 타입?
>**원시 데이터 타입**
>
>자바에서의 원시 데이터 타입에는 byte, short, int, long, float, double, char, boolean 등이 있습니다.
>
>이들은 스택 메모리에 직접 저장됩니다.
>
>스택 메모리는 컴파일 시간에 메모리 크기가 결정되며, 함수 호출이 끝나면 자동으로 해제되는 특징이 있습니다.
>
>**참조 데이터 타입**
>
>자바에서의 참조 데이터 타입은 배열, 클래스, 인터페이스 등이 있으며, 이들은 힙 메모리에 저장됩니다.
>
>힙 메모리는 런타임에 동적으로 할당되며, 가비지 컬렉터에 의해 관리됩니다.
>
>참조 데이터 타입의 변수는 스택 메모리에 저장되고, 힙 영역에 생성된 객체를 참조하는 주소값입니다.

이를 그림으로 단순하게 표현하면 다음과 같습니다.

![](https://velog.velcdn.com/images/ks0927/post/985a8727-b0b3-4298-9fd7-845d7b9d77bb/image.png)

## 원시 데이터 타입 (Primitive Data Type)의 전달 방식

원시 데이터 타입은 Stack 영역에 변수와 함께 저장된다고 했었죠?

코드와 그림을 통해 자바의 동작 방식을 보여드리겠습니다~ 👨‍🏫


```
public class PrimitivesUnitTest {

    @Test
    public void test() {

		// ( 1 )
        int x = 1;
        int y = 2;
        
        // Before
        assertEquals(x, 1);
        assertEquals(y, 2);
        
		// ( 2 )
        modify(x, y);
		
        // After
        assertEquals(x, 1);
        assertEquals(y, 2);
    }

    public static void modify(int x, int y) {
    	// ( 3 )
        x += 1;
        y -= 1;
    }
}
```
 

위 코드를 살펴보면 test메서드에 원시 데이터 타입인 int의 변수 x, y 가 modify 메서드 호출 이후 값의 변화를 테스트 하고 있습니다.

실제 과정을 그림을 통해 순차적으로 살펴보겠습니다. 

![](https://velog.velcdn.com/images/ks0927/post/a3dc6b7a-dad7-4e6d-9059-87908af2eaff/image.png)


그림의 상황이 발생한 곳을 코드에 주석으로 달아두었으니 확인해보세요!😎

Stack 내부에 test() 와  test()의 변수 x,y가 복사되어 modify() 스택 프레임의 x,y로 따로 들어가게 됩니다.

따라서 modify() 영역의 값이 바뀌어도 test() 영역의 변수는 당연히 변화가 없습니다.

이와 같이 자바에서 원시 데이터 타입의 전달은 값만 전달하는 Call by Value 로 동작합니다.

## 참조 데이터 타입 (Reference Data Type)의 전달 방식

참조 데이터 타입은 원시 데이터 타입과 다르다는 것은 이미 언급드렸었죠?

변수 자체는 Stack 영역에 생성되지만 실제 객체는 Heap 영역에 위치합니다.

그리고 Stack 에 생성된 변수가 Heap 에 위치한 객체를 바라보고 있는 형태라고 생각하면 좋을 것 같습니다.

마찬가지로 코드와 그림을 통해 알아보겠습니다! 😎

```
public class PrimitivesUnitTest {

    @Test
    public void test() {
    	// ( 1 )
        Money x = new Money(100);
        Money y = new Money(200);

        // Before
        assertEquals(x.num, 100);
        assertEquals(y.num, 200);

		// ( 2 )
        modify(x, y);
        
        // After
        assertEquals(x.num, 200);
        assertEquals(y.num, 200);
    }

    public static void modify(Money x, Money y) {
    	// ( 3 )
        x.num += 100;

		// ( 4 )
        y = new Money(300);
        // ( 5 )
        y.num += 100;
    }
}

class Money {
    public int num;

    public Money(int num) {
        this.num = num;
    }
}

```

위 코드를 살펴보면 test메서드에 참조 데이터 타입인 클래스 Money 의 변수 x, y 가 modify 메서드 호출 이후 값의 변화를 테스트 하고 있습니다.

실제 과정을 그림을 통해 순차적으로 살펴보겠습니다. 

![](https://velog.velcdn.com/images/ks0927/post/c0c909cc-2ea5-4e9d-a981-7441f77f31c0/image.png)

원시 타입과는 다르게 변수 x, y만 Stack 영역에 생성되고 실제 객체는 Heap 영역에 생성됩니다.

각 변수는 Heap 영역에 있는 객체를 바라보고 있습니다.

![](https://velog.velcdn.com/images/ks0927/post/52fe22da-adc9-4664-849b-b47c541251dc/image.png)

modify 메서드는 넘겨받은 파라미터 x,y를 Stack 영역에 생성하고 주소값을 똑같이 바라봅니다.

![](https://velog.velcdn.com/images/ks0927/post/094d74a7-2663-469b-b334-29799bdd7d93/image.png)

test() 영역과 modify() 영역에 존재하는 x 변수들은 같은 객체인 ```Money “x”(x.num=100)``` 을 바라보고 있기 때문에 객체를 공유합니다.
따라서 modify() 메서드에서 ```x.num += 100;```를 행하면 값이 변경됩니다.

![](https://velog.velcdn.com/images/ks0927/post/3f0ced11-3d50-4123-ab96-326842229e96/image.png)

test() 영역과 modify() 영역에 존재하는 y 변수들은 서로 같은 객체인 ```Money “y”(y.num=200)``` 를 바라보고 있었지만

modify() 매서드에서 ```y = new Money(300);```를 통해 새로운 객체를 생성해서 할당했기 때문에

```Money “y”(y.num=300)``` 이라는 객체를 바라봅니다.

![](https://velog.velcdn.com/images/ks0927/post/9271fdce-bbe2-4f0e-8221-f626fff7aa43/image.png)

따라서 ```Money “y”(y.num=300)``` 의 num 값을 ```y.num += 100;```을 통해 변경해도 test() 에 있는 y 에는 아무런 변화가 없습니다.

## 결론
Java 는 참조 데이터 타입이든 원시 데이터 타입이든 **Call by Value** 로만 동작한다! 

## 더 알아보면 좋을 내용

해당 포스트에서는 조금 생략하였지만 실제로 Jvm의 Stack의 내부는 조금 더 복잡합니다!

Stack에 stack frame 단위로 추가되는데 stack frame은 ```Local Variables Array``` ,```Operand Stack```,```frame data```  로 구성되어 있습니다!

더 정확한 실행 구조는 여러분이 학습해 보면 좋을것 같습니다! 😁😁

## 참고 자료

https://www.baeldung.com/java-pass-by-value-or-pass-by-reference

https://youtu.be/Vd1C3-wHc4Y?si=5rnmtu60pJbhcXWg

https://bcp0109.tistory.com/360![](https://velog.velcdn.com/images/ks0927/post/a96ff9ea-a238-4ad5-9350-26556268fc40/image.png)
