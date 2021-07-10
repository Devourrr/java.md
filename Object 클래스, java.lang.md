### Object 클래스

모든 클래스의 최상위 클래스이다

- Object클래스는 모든 클래스의 최상위 클래스
- 아무것도 상속받지 않으면 자동으로 Object를 상속
- Object가 가지고 있는 메소드는 모든 클래스에서 다 사용할 수 있다는 것을 의미

오브젝트가 가지고 있는 메서드 중 가장 많이 사용되는 메서드는

- equals(in String 클래스) - 객체가 가진 값 비교 (오브젝트 클래스의 메서드를 오버라이딩한 메서드)
- toString - 객체가 가진 값을 문자열로 반환
- hashcode - 객체의 해시코드 값 반환(자료구조에서 많이 사용됨)
- 모두 사용 시 반드시 오버라이딩 해야 한다



name과 number필드를 가지는 Car클래스를 toString 메소드 오버라이딩으로 리턴해보자

public class Car{
    String name;
    int number;
    

    public class Car{
        String name;
        int number;
        
    @Override
    public String toString(){
        return "name: " + name + ", number: " + number;
    }


​    

number는 int형이지만 toString메서드 사용으로 name과 함께 문자열로 반환되었다

###  java.lang패키지 / 오토박싱

java.lang패키지는 자바가 지원하는 다양한 기본적 패키지 중에 가장 중요한 패키지이다

- Java.lang패키지의 클래스는 import를 하지 않고도 사용할 수 있다.
- java.lang패키지에는 기본형타입을 객체로 변환시킬때 사용하는**<u>Wrapper</u>**클래스가 있다.
  - Boolean, Byte, Short, Integer, Long, Float, Double 클래스
- 모든 클래스의 최상위 클래스인 Object도 java.lang패키지
- 문자열과 관련된 String, StringBuffer, StringBuilder도 모두 java.lang패키지
- 화면에 값을 출력할때 사용했던 System클래스도 java.lang패키지
- 수학과 관련된 Math클래스도 java.lang패키지
- Thread와 관련된 중요 클래스들이 java.lang패키지
- 이외에도 다양한 클래스와 인터페이스가 java.lang패키지에 속해 있다.



**오토박싱**

오토박싱, 오토 언박싱은 java5부터 지원한다. 이 때 내부적으로 Wrapper클래스들이 사용된다

설명 : Integer는 int의 wrapper클래스이다. 따라서 속성과 메소드를 가지는데

Integer타입인 경우 필드와 메소드를 사용할 수 있지만,

기본형 타입 int의 경우 필드와 method를 사용할 수 없다

- Integer i3 = 5; 숫자 5는 원래 기본형이지만 자동으로 Integer 형태로 변환된다
- int i5 = i2;  Integer객체타입의 값을 기본형 int로 자동 변환되어 값을 할당한다

```
public class WrapperExam {
        public static void main(String[] args) {
            int i = 5; 
            Integer i2 = new Integer(5);
            Integer i3 = 5;     //오토박싱
            int i4 = i2.intValue();
            int i5 = i2;       //오토언박싱
        }
    }
```



###  스트링버퍼

아무 값도 가지지않은 StringBuffer객체를 생성

```
 StringBuffer sb = new StringBuffer();
    // 해당 스트링 버퍼에 "hello", 공백, "world"를 차례대로 추가

    sb.append("hello");
    sb.append(" ");
    sb.append("world");
    // StringBuffer에 추가된 값을 toString()메소드를 이용하여 반환

    String str = sb.toString();
```

#### StringBuffer가 가지고 있는 메소드들은 대부분 자기 자신, this를 반환

```
    StringBuffer sb2 = new StringBuffer();
    StringBuffer sb3 = sb2.append("hello");
    if(sb2 == sb3){
        System.out.println("sb2 == sb3");
    }
```

- 자기 자신의 메소드를 호출하여 자기 자신의 값을 바꿔나가는 것을 메소드체이닝 이라고 한다.
- StringBuffer클래스는 메소드 체인 방식으로 사용할 수 있도록 만들어져 있다.

```
        String str2 = 
        new StringBuffer().append("hello").append("").append("world").toString();
        System.out.println(str2);
```

- 앞에서 5줄로 작성했던 코드를 위와 같이 한 줄로 수정할 수 있다.
- StringBuffer는 append메소드 외에도 길이를 구하거나, 자르거나 등의 다양한 메소드들을 가지고 있다.



###  스트링클래스의 문제점

String클래스는 문자열을 다룰 때 사용하는 클래스

#### String클래스는 불변클래스 이다.

```
        String str1 = "hello world";
        String str2 = str1.substring(5);
        System.out.println(str1);
        System.out.println(str2);
```

- 실행결과

```
    hello world
     world
```

- 기존의 str1은 전혀 변화 없다.
- substring메소드는 5번째 부터 문자열을 잘라서 새로운 문자열을 반환하는 메소드
- str1자체는 전혀 변화가 없다.

String클래스를 사용할 때 가장 문제가 발생하는 경우는 다음과 같은 코드를 사용할 때 입니다.

```
    String str3 = str1 + str2;
    System.out.println(str3);
```

- 실행결과

```
    hello world world
```

#### 문자열과 문자열을 더하게 되면 내부적으로는 다음과 같은 코드가 실행

```
    String str4 = new StringBuffer().append(str1).append(str2).toString();
    System.out.println(str4);
```

+연산 사용시 .append().toString()이 내부적으로 실행된다

반복문안에서 내부적으로 String 객체를 만들어내면 매번 new연산자를 사용해야하기 때문에 

그만큼 속도가 느려진다

#### 문자열을 반복문 안에서 더하는 것은 성능상 문제가 생길 수 있으니 반드시 피하도록 하자

###  Math

수학계산을 위한 클래스

**코사인, 사인, 탄젠트, 절대값, 랜덤값을 구할 수 있는 클래스**

- Math클래스는 생성자가 private으로 되어 있기 때문에 new 연산자를 이용하여 객체를 생성할 수 없다.
- 객체를 생성할 수는 없지만 모든 메소드와 속성이 static으로 정의되어 있기 때문에 객체를 생성하지 않고도 사용할 수 있다.

```
public class MathExam {
        public static void main(String[] args) {
            int value1 = Math.max(5, 20); // 5~20최댓값
            int value2 = Math.min(5, -5); //-5~5 최솟값
            int value3 = Math.abs(-10); // 인자에 대한 절대값 10반환
            double value4 = Math.random(); // 랜덤
            double value5 = Math.sqrt(25);  //인자의 제곱근 5 반환
        }
    }
```

