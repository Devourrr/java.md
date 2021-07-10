###  Method

**메소드 == 클래스가 가지고 있는 기능**

field가 상태였다면 method는 행동, 함수와 비슷한 개념이다

입력값: Parameter매개변수, Argument인자 결과값: 리턴값

Parameter :  전달된 인자를 받아들이는 변수의미

Argument : 어떤 함수를 호출시에 전달되는 값 자체를 의미

메서드는 다양한 형태를 가지고 있다

- 매개변수도 없고 리턴하는 것도 없는 형태의 메소드(리턴값이 없을 경우 void라고 작성)

  - ```java
    public void method1(){}
    ```

- 정수를 받아들인 후, 리턴하지 않는 메서드(void)

  - ```java
    public void method2(int x){}
    ```

- 아무 것도 받아들이지 않고 정수를 반환하는 메서드

  - ```java
    public int method3(){ // 메소드 이름 앞에는 리턴하는 타입을 적어준다.
            System.out.println("method3이 실행됩니다.");
    		// 리턴타입은 하나만 사용할 수 있다. 리턴하는 타입은 어떤 타입이라도 상관없다.
            return 10; // 리턴하는 값 앞에 return 이라는 키워드를 사용한다.
        }
    ```

- 정수를 2개 매개변수로 받고 아무것도 반환하지 않는 메소드
- 정수를 한개 받아들인 후, 정수를 반환하는 메소드

메소드 사용법

- 메소드를 사용하기 위해서는 메소드가 정의된 클래스가 생성되어야 한다

- 객체를 생성할 때는 new 연산자를 이용한다.

- 메소드 사용할때는 생성된 클래스를 참조하는 레퍼런스변수.메소드명() 으로 사용할 수 있다.

  

####  String 클래스의 메소드

String str = new String("Hello");

str.length() // str문자열의 길이  5반환

str.concat("world") // "Hello world"반환 concat(연결 의미)

str.subString(1,3) or str.subString(2) // 인덱스1~3까지 자른 결과/ 인덱스 2부터 마지막까지 자른 결과 반환



