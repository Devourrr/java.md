

###  Date

날짜와 시간을 구하기 위한 Date 클래스

- Date클래스는 JDK 1.0때 만들어졌고, Calendar클래스는 JDK1.1에 만들어졌다.
- Date는 지역화에 대한 부분이 고려되지 않았다.
  - 지역화 : 지역에 따라서 시간, 통화(원, 달러, 엔 등) 언어등에 대하여 고려하는 프로그래밍
- Date클래스를 보면 대부분의 생성자와 메소드가 Deprecated되어 있다.
  - Deprecated된 것은 앞으로 지원을 안하거나 문제가 있을 수 있으니 사용하지 말라는 의미
- 기본 생성자를 이용한 Date클래스 생성
  - 기본 생성자로 Date인스턴스를 만들게 되면 현재 시간과 날짜 정보를 Date인스턴스가 가지게 된다

```
Date date = new Date();
System.out.println(date.toString()); // toString()메소드로 현재 시간 문자열로 출력
```

java.util.SimpleDateFormat 클래스를 이용해서 원하는 형태로 출력하는 방법

- yyyy는 년, MM은 월, dd는 일을 표현한다.
- hh는 시간, mm은 분, ss는 초를 표현하며 a는 오전/오후 를 표현한다.
- zzz는 TimeZone을 나타낸다. 한국의 경우 한국표준시 KST가 TimeZone에 해당하는 값이다.

```
SimpleDateFormat ft =  new SimpleDateFormat ("yyyy.MM.dd 'at' hh:mm:ss a zzz");     
    System.out.println(ft.format(date));
```

현재 시간을 Long값으로 구하는 방법

```
System.out.println(date.getTime());
    // System이 가지고 있는 currentTimeMillis()메소드를 이용
    long today = System.currentTimeMillis();
    System.out.println(today);
```



###  Calendar

#### Date의 단점을 해결하고 등장한 것이 Calendar클래스

- Calendar 클래스 생t성 방법
  - Calendar클래스는 추상클래스이다.
  - Calendar클래스에 대한 인스턴스를 생성하려면 Calendar가 가지고 있는 클래스 메소드 getInstnace()를 사용해야 한다.
  - getInstance()메소드를 호출하면 내부적으로 java.util.GregorianCalendar 인스턴스를 만들어서리턴한다.
  - GregorianCalendar는 Calendar의 자식 클래스이다

- Calendar 클래스를 이용해서 현재 날짜와 시간에 대한 정보를 알아내는 방법
  - Calendar는 현재 날짜와 시간에 대한 정보를 가진다.
  - Calendar가 가지고 있는 get메소드에 Calendar의 상수를 어떤 것을 넣어주느냐에 따라서 다른 값이 나오게 된다

```
Calendar cal = Calendar.getInstance();

 int yyyy = cal.get(Calendar.YEAR);
        int month = cal.get(Calendar.MONTH) + 1; // 월은 0부터 시작합니다.
        int date = cal.get(Calendar.DATE);
        int hour = cal.get(Calendar.HOUR_OF_DAY);
        int minute = cal.get(Calendar.MINUTE);
        // Calendar가 가지고 있는 add메소드를 이용하면 쉽게 다음 날짜나 이전 날짜를 구할 수 있다
        cal.add(Calendar.HOUR, 5); // 현재 캘린더에 5시간 후를 더함, -5로 수정시 5시간 전 구할 수 있음

```



오늘부터 100일뒤의 날짜를 문자열로 만들어 return하려면 어떻게 해야하는지 실습해보자
    
    import java.util.*;
    
    public class CalendarExam{
        public String hundredDaysAfter(){
            Calendar cal = Calendar.getInstance();
            cal.add(Calendar.DATE, 100);
            
            int year = cal.get(Calendar.YEAR);
            int month = cal.get(Calendar.MONTH);
            int date = cal.get(Calendar.DATE);
            
            String cals = year + "년" + month + "월" + date + "일";
            return cals;
            
        }
    public static void main(String[] args){
        CalendarExam c = new CalendarExam();
        System.out.println(c.hundredDaysAfter());
    	}
    }
#### 

###  java.time 패키지



#### Java에서 제공하는 Date, Time API는 부족한 기능 지원을 포함한 여러가지 문제점을 가지고 있었다. JDK 코어에서 이런 문제점들을 해결하고 더 좋고 직관적인 API들을 제공하기 위해 새롭게 재 디자인한 Date, Time API를 Java SE 8부터 제공한다.

- 새로운 API의 핵심 클래스는 오브젝트를 생성하기 위해 다양한 factory 메서드를 사용한다.

- 오브젝트 자기 자신의 특정 요소를 가지고 오브젝트를 생성할 경우 of 메서드를 호출하면 되고, 다른 타입으로 변경할 경우에는 from 메서드를 호출하면 된다.

- LocalDateTime 클래스를 이용해서 현재 시간 time객체 만드는 방법

  - now는 현재 시간을 구한다.

  - ```
    LocalDateTime timePoint = LocalDateTime.now(); // 현재의 날짜와 시간
    ```

- 원하는 시간으로 time객체 생성하는 방법

```
 // 2012년 12월 12일의 시간에 대한 정보를 가지는 LocalDate객체를 만드는 방법  
    LocalDate ld1 = LocalDate.of(2012, Month.DECEMBER, 12); // 2012-12-12 from values

        // 17시 18분에 대한 LocalTime객체를 구한다.
    LocalTime lt1 = LocalTime.of(17, 18); // 17:18 (17시 18분)the train I took home today

    // 10시 15분 30초라는 문자열에 대한 LocalTime객체를 구한다.
    LocalTime lt2 = LocalTime.parse("10:15:30"); // From a String
```

- 현재와 날짜와 시간정보를 getter메소드를 이용하여 구하는 방법

```
LocalDate theDate = timePoint.toLocalDate();
    Month month = timePoint.getMonth();
    int day = timePoint.getDayOfMonth();
    int hour = timePoint.getHour();
    int minute = timePoint.getMinute();
    int second = timePoint.getSecond();
    // 달을 숫자로 출력한다 1월도 1부터 시작하는 것을 알 수 있다. 
    System.out.println(month.getValue() + "/" + day + "  " + hour + ":" + minute + ":" + second);
```

