###  java.util 패키지

### java.util패키지는 유용한 클래스들을 많이 가지고 있는 패키지

- 날짜와 관련된 클래스인 **Date, Calendar클래스**
- 자료구조와 관련된 **컬렉션 프레임워크**와 관련된 인터페이스와 클래스
- deprecated란 더이상 지원하지 않으니 사용하지 않는 것이 좋다란 의미다.
- Date클래스는 지역화를 지원하지 않는다. 지역화란 국가별로 현재 날짜와 시간은 다를 수 있는데, 그 부분을 지원하지 못한다.
- 이런 문제를 해결하기 위하여 나온 클래스가 **Calendar클래스**. Calendar클래스는 자바 1.1에 등장하였다.
- 지역화와 관련된 클래스들은 **Locale**로 시작되는 이름을 가진 클래스들입니다. 역시 1.1 이후에 등장한다.
- **List, Set, Collection, Map**은 **자료구조** 즉 **컬렉션 프레임워크와 관련된 인터페이스**



###  컬렉션 프레임워크

java.util에는 자료를 다룰 수 있는 자료구조 클래스가 다수 존재한다.

자료구조 클래스들을 컬렉션 프레임워크라고 한다

- 자료구조란 자료를 저장할 수 있는 구조

- 책을 보관하기 위해서 책장을 이용하는 것처럼 <u>다양한 자료들을 다양한 방식으로 관리하기 위한 방법</u>이 필요한데, 

  이러한 방법을 제공하는 것을 <u>자료구조, 컬렉션 프레임워크</u>이다.

- 컬렉션 프레임워크에서 가장 기본이 되는 interface는 **Collection인터페이스**

  - Collection인터페이스는 여기에 자료가 있다라는 것을 표현.

  - 중복도 허용하고, 자료가 저장된 순서도 기억하지 못하는 것이 Collection인터페이스.

  - Collection이 가지고 있는 대표적인 메소드는 **add(), size(), iterator() 메소드**

  - <u>Collection은 저장된 순서를 기억하지 못하기 때문에</u> "첫번째 자료를 달라, 두번째 자료를 달라"와 같은 기능을 가질 수 없다. 

    * **Collection은 저장된 자료를 하나씩 하나씩 꺼낼 수 있는 Iterator라는 인터페이스를 반환한다.**

    - Iterator는 꺼낼것이 있는지 없는지 살펴보는 hasNext()메소드와 하나씩 자료를 꺼낼때 사용하는 next()메소드를 가지고 있다.

- **Set자료구조는 중복을 허용하지 않는 자료구조를 표현하는 인터페이스**

  - Collection인터페이스를 상속받는다.
  - <u>Set인터페이스가 가지고 있는 add메소드는 같은 자료가 있으면 false, 없으면 true를 반환하는 add메소드를 가지고 있다.</u>

- **List자료구조는 중복은 허용하면서 순서를 기억하는 자료구조를 표현.**

  - Set인터페이스와 마찬가지로 Collection인터페이스를 상속받고 있다.
  - <u>List는 순서를 기억하고 있기 때문에 0번째 1번째 n번째의 자료를 꺼낼 수 있는 get(int)메소드를 가지고 있다.</u>

- **Map자료구조는 Key와 Value를 가지는 자료구조이다.**

  - <u>저장할 때 put()메소드를 이용하여 key와 value를 함께 저장한다.</u>
  - <u>원하는 값을 꺼낼때는 key를 매개변수로 받아들이는 get()메소드를 이용하여 값을 꺼낸다.</u>
  - <u>Map에 저장되어 있는 모든 Key들은 중복된 값을 가지면 안된다.</u>
  - <u>Key의 이런 특징 때문에 Map은 자신이 가지고 있는 모든 Key들에 대한 정보를 읽어들일 수 있는 Set을 반환하는 keySet()메소드를 가지고 있다.</u>





###  Generic 

Box 클래스와 BoxExam 클래스가 있다

Box는 매개변수로  Object를 하나 받아들이고 Object를 반환한다

Object를 받아들일 수 있다는 것은 Object의 후손이라면 무엇이든 받아들일 수 있다는 것이다

```
public class Box {
        private Object obj;
        public void setObj(Object obj){
        this.obj = obj;
        }

        public Object getObj(){
        return obj;
        }
    }
public class BoxExam {
        public static void main(String[] args) {
            Box box = new Box();
            box.setObj(new Object());
            Object obj = box.getObj();

            box.setObj("hello");
            String str = (String)box.getObj();
            System.out.println(str);

            box.setObj(1);
            int value = (int)box.getObj();
            System.out.println(value);
        }
    }
```

java5부터 인스턴스를 만들때 사용하는 타입을 지정할 수 있는 Generic 문법이 추가되었다.

Generic을 사용함으로써의 효용은

선언할 때는 가상의 타입으로 선언하고, 사용시에는 구체적인 타입을 설정함으로써

다양한 타입의 클래스를 이용하는 클래스를 만들 수 있다

Generic을 사용하는 대표적인 클래스는 컬렉션 프레임워크과 관련된 클래스이다

```
public class Box<E> { //클래스 이름 뒤에 <E>가 제네릭을 적용한 것이다. 
					  //Box는 가상의 클래스 E를 사용한다는 의미.
        private E obj; 
        public void setObj(E obj){
            this.obj = obj;
        }
//Object를 받아들이고, 리턴하던 부분이 E로 변경. E는 실제로 존재하는 클래스는 아니다.
        public E getObj(){
            return obj;
        }
    }
```

```
public class BoxExam { // Generic을 이용하여 수정한 Box를 이용하는 BoxExam클래스
        public static void main(String[] args) {
            Box<Object> box = new Box<>(); //Object를 사용하는 Box를 인스턴스로 만들겠다는 의미
            box.setObj(new Object());
            Object obj = box.getObj();

            Box<String> box2 = new Box<>(); // String을 사용하는 Box인스턴스를 만들겠다는 의미
            box2.setObj("hello");
            String str = box2.getObj();
            System.out.println(str);

            Box<Integer> box3 = new Box<>(); // Integer를 사용하는 Box인스턴스를 만든다는 의미
            box3.setObj(1);
            int value = (int)box3.getObj();
            System.out.println(value);
        }
    }
```



###  Set

set은 중복이 없고 순서도 없는 자료구조이다

Hashset과 TreeSet이 있다

```
import java.util.HashSet;
    import java.util.Iterator;
    import java.util.Set;

    public class SetExam {
        public static void main(String[] args) {
            Set<String> set1 = new HashSet<>();

            boolean flag1 = set1.add("kim");
            boolean flag2 = set1.add("lee");
            boolean flag3 = set1.add("kim");

            System.out.println(set1.size());   //저장된 크기를 출력 
            //3개를 저장하였지만, 중복값이 있었기 때문에 2개가 출력
            System.out.println(flag1);  //true
            System.out.println(flag2);  //true
            System.out.println(flag3);  //false

            Iterator<String> iter = set1.iterator();

            while (iter.hasNext()) {   // 꺼낼 것이 있다면 true 리턴.          
                String str = iter.next(); // next()메소드는 하나를 꺼낸다. 
                //하나를 꺼내면 자동으로 다음것을 참조한다.
                System.out.println(str);
            }
        }
    }
```

###  List

list는 데이터의 중복이 있을 수 있고, 순서도 있다

```
 import java.util.ArrayList;
    import java.util.List;

    public class ListExam {

        public static void main(String[] args) {
            List<String> list = new ArrayList<>();

            // list에 3개의 문자열을 저장합니다.
            list.add("kim");
            list.add("lee");
            list.add("kim");

            System.out.println(list.size()); //list에 저장된 자료의 수를 출력 (중복을 허용하므로 3 출력) 
            for(int i = 0; i < list.size(); i++){
                String str = list.get(i);
                System.out.println(str);
            }
        }   
    }
```

###  Map

Map은 key와 value를 쌍으로 저장하는 자료구조

키는 중복될 수 없고, 값은 중복될 수 있다.

```
import java.util.HashMap;
    import java.util.Iterator;
    import java.util.Map;
    import java.util.Set;   
    public class MapExam {  
        public static void main(String[] args) {
            // Key, Value가 모두 String 타입인 HashMap인스턴스를 만든다.
            Map<String, String> map = new HashMap<>();

            // key와 value값을 put으로 저장
            map.put("001", "kim");
            map.put("002", "lee");
            map.put("003", "choi");
            // 같은 key가 2개 있을 수 없으므로 첫번째로 저장했던 001, kim은 001, kang으로 바뀐다.
            map.put("001", "kang");

            // map에 저장된 자료의 수, 3이 출력
            System.out.println(map.size());

            // 키가 001, 002, 003인 값을 꺼내 출력
            System.out.println(map.get("001"));
            System.out.println(map.get("002"));
            System.out.println(map.get("003"));

            // map에 저장된 모든 key들을 Set자료구조로 꺼낸다.
            Set<String> keys = map.keySet();
            // Set자료구조에 있는 모든 key를 꺼내기 위하여 Iterator를 구함
            Iterator<String> iter = keys.iterator();
            while (iter.hasNext()) {
                // key를 꺼냅니다.
                String key = iter.next();
                // key에 해당하는 value를 꺼낸다
                String value = map.get(key);
                // key와 value를 출력
                System.out.println(key + " : " + value);
            }
        }
    }
```