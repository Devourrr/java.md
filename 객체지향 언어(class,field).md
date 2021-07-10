###  객체지향 언어

**"프로그램을 구성하는 요소는 객체이며 이것이 상호작용하도록 프로그래밍 한다."**

자바는 객체를 만들기 위해서 반드시 클래스(frame)를 먼저 만들어야 한다



###  클래스 선언 형식

pulic class 클래스명{

​		public static void main(String[] args){ // 메인 메서드

​			객체타입 변수명 = new  객체타입(); // 지정한 객체타입과 이름으로 객체가 생성됨

​													//new 연산자는 new뒤에 생성자를 이용해서 메모리에 객체를 만들라는 명령지시

​													//메모리에 만들어진 객체 = 인스턴스

​		Ex) Car c1 = new Car();

​		}

}										

###  참조형 변수



자바는 변수를 선언하려면 반드시 변수의 타입을 정해줘야 하는데

기본형과 참조형 타입이 있다

기본형 - boolean, char, byte, short, int, long, float, double..

참조형 타입은 기본형 타입을 제외한 모든 타입이다 ex) 배열, 클래스 ..

기본형 ex) int i=4;  // 기본형 정수 i변수에 4라는 값 저장

참조형 ex) String str = new String("hello"); // String 이라는 클래스 사용해서 참조형 변수 str선언

기본형이 아닌 String클래스 변수명 =  new연산자 생성자(값); // new = 클래스를 메모리에 추가할 것이라는 뜻(인스턴스)

![](C:\Users\CJH\Downloads\참조형.jpg)

**str변수는 String 인스턴스(메모리에 추가된 String클래스)를 참조한다**

<u>**기본형 타입과 참조 타입의 차이는 메소드 호출에서 확인할 수 있다**</u>



###  String 클래스

**"String클래스는 자바에서 문자열을 표현하기 위해 가장 많이 사용하는 클래스이다"**

또한 String클래스는 new 연산자를 이용하지 않고도 인스턴스를 만들 수 있다(모든 클래스는 new사용해야 인스턴스 만들 수 있음)

ex) String str2 = "hello"; //상수 저장 영역 메모리에 저장됨(중복x 최초 선언 값의 인스턴스를 가리킴)

String str3 = new String("hello"); // 상수영역이 아닌 무조건 hip 영역에 저장(중복값도 새로 생성, 다른 인스턴스를 참조)

사람의 입장에선 같은 값을 가진 변수라고 생각할 수 있지만 자바 입장에선 서로 다르다고 생각한다



###  Field

자동차에 차종, 번호판, 기능이 있는 것처럼 클래스에도 속성이 있다 이 것을 Field(상태)라고 한다

public class Car{

​	String name;

​	int number;

​	public static void main(String[] args){

​	Car c1 = new Car();

​	Car c2 = new Car(); // Car라는 인스턴스가 메모리에 2개 만들어져서 객체별 각 name/number 속성을 가진다



​	c1.name = "소방차";

​	c1.number = 1234;

​	c2.name = "구급차";

​	c2.number = 1004



​	System.out.println(c1.name); // c1이 참조하는 객체의 name을 출력

​	System.out.println(c1.number);



​	String name = c2.name; c2가 참조하는 객체의 name을 String 타입 변수 name도 참조하도록 선언

}

}









