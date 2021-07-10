###  변수의 scope와 static

####  scope

프로그램상에서 사용되는 변수들은 사용가능한 범위를 가진다. 

**scope == 범위**

**변수가 선언된 클래스 블록이 그 변수의 scope이다**

```java
 public class ValableScopeExam{

        int globalScope = 10;   // 인스턴스 변수 

        public void scopeTest(int value){   
            int localScope = 10;
            System.out.println(globalScope); //정상출력
            System.out.println(localScpe); //정상출력
            System.out.println(value); //정상출력
            // 매개변수로 선언된 int value 는 블럭 바깥에 존재하기는 하지만, 
            //메서드 선언부에 존재하므로 사용범위는 해당 메소드 블럭내이다.
        }
    }
```



```
public class VariableScopeExam { // 같은 클래스 안에 있는데 globalScope 변수를 사용 할 수 없다.
        int globalScope = 10; 
        //main은 static한 메소드이다. static한 메서드에서는 static 하지 않은 필드를 사용 할 수 없다.

        public void scopeTest(int value){
            int localScope = 20;            
            System.out.println(globalScope);
            System.out.println(localScope);
            System.out.println(value);
        }   
        public static void main(String[] args) {
            System.out.println(globalScope);  //오류
            System.out.println(localScope);   //오류
            System.out.println(value);        //오류  
        }   
    }
```

####  static

- 같은 클래스 내에 있음에도 해당 변수들을 사용할 수 없다.

- main 메소드는 static 이라는 키워드로 메소드가 정의되어 있다. 이런 메서드를 static 한 메소드 라고 한다.

- static한 필드(필드 앞에 static 키워드를 붙힘)나, static한 메소드는 Class가 인스턴스화 되지 않아도 사용할 수 있다.

  

static한 변수는 공유된다

- static하게 선언된 변수는 값을 저장할 수 있는 공간이 하나만 생성된다. 그러므로, 인스턴스가 여러개 생성되도 static한 변수는 하나다.

- ```
  public class VariableScopeExam {
          int globalScope = 10; 
          static int staticVal = 7;
  
          public void scopeTest(int value){
              int localScope = 20;        
          }
  
          public static void main(String[] args) {
              System.out.println(staticVal);      //사용가능 
              ValableScopeExam v1 = new ValableScopeExam();
              ValableScopeExam v2 = new ValableScopeExam();
              v1.golbalScope = 20;
              v2.golbalScope = 30; 
  
              System.out.println(v1.golbalScope);  //20 이 출력된다. 
              System.out.println(v2.golbalScope);  //30이 출력된다. 
  
              v1.staticVal = 10;
              v2.staticVal = 20; 
  
              System.out.println(v1.statVal);  //20 이 출력된다. 
              System.out.println(v2.statVal);  //20 이 출력된다. 
          }
  
      }
  
  ```

예제

static 메소드는 static한 필드(속성)만 사용할 수 있다.

그런데 주어진 코드는 static 메소드인 main method에서 static 하지 않은 변수, 

value를 쓰려고해 오류가 발생할 때, 

코드가 정상적으로 동작하도록 코드를 수정하려면?

public class VariableScopeExam{

​    int value = 10; //오류

​    static int  value = 10;
​    public static void main(String []args){
​        System.out.println(value);
​    }
}

**static 변수는 인스턴스가 아닌 클래스에 귀속된다. **

**따라서, 인스턴스가 여러개 생성돼도 static 변수는 딱 하나인 것이다. **

