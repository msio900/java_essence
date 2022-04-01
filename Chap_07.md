# Chapter 07 : 객체지향 프로그래밍Ⅱ[↩](../../)

## contents📑<a id='contents'></a>

* 1_상속(inheritance)
  * 1_1 상속의정의와 장점
  * 1_2 클래스간의 관계-포함관계
  * 1_3 클래스간의관계결정하기
  * 1_4 단일상속(single inheritance)
  * 1_5 Object클래스 -모든 클래스의 조상

* 2_오버라이딩(overriding)
  * 2_1 오버라이딩이란?
  * 2_2 오버라이딩의조건
  * 2_3 오버로딩 vs. 오버라이딩
  * 2_4 super
  * 2_5 super() - 조상 클래스의 생성자

* 3_package와 import
  * 3_1 파！키시(package)
  * 3_2 패키지의 선언
  * 3_3 import문
  * 3_4 import문의 선언
  * 3_5 static import문

* 4_제어자(modifier)[👉](#4)
  * 4_1 제어자란?[✏](#4_1)
  * 4_2 static - 클래스의, 공통적인[✏](#4_2)
  * 4_3 final - 마지막의, 변경될 수 없는[✏](#4_3)
  * 4_4 abstract - 추상의, 미완성의[✏](#4_4)
  * 4_5 접근 제어자(access modifier)[✏](#4_5)
  * 4_6 제어자(modifier)의 조합[✏](#4_6)
* 5_다형성(polymorphism)
  * 5_1 다형성이란?
  * 5_2 참조변수의 형변환
  * 5_3 instanceof연산자
  * 5_4 참조변수와 인스턴스의 연결
  * 5_5 매개변수의 다형성
  * 5_6 여러 종류의 객체를 배열로 다루기

* 6_추상클래스(abstract class)[👉](#6)
  * 6_1 추상클래스란?[✏](#6_1)
  * 6_2 추상메서드(abstract method)[✏](#6_2)
  * 6_3 추상클래스의 작성[✏](#6_3)


* 7_인터페0|스(interface)
  * 7_1 인터페이스란?
  * 7_2 인터페이스의작성
  * 7_3 인터페이스의상속
  * 7_4 인터페이스의구현
  * 7_5 인터페이스를 이용한 다중상속
  * 7_6 인터페이스를이용한 다형성
  * 7_7 인터페이스의장점
  * 7_8 인터페이스의 이해
  * 7_9 디폴트 메서드와 static메서드
* 8_내부 클래스(inner class)
  * 8_1 내부클래스란?
  * 8_2 내부 클래스의종류와 특징
  * 8_3 내부 클래스의 선언
  * 8_4 내부 클래스의 제어자와 접근성
  * 8_5 익명 클래스(anonymous dass)

## 4_제어자(modifier)[📑](#contents)<a id="4"></a>

### 4_1 제어자란?[📑](#contents)<a id='4_1'></a>

제어자(modifier)는 클래스, 변수 또는 메서드의 선언부에 함께.사용되어 부가적인 의미 를 부여한다. 제어자의 종류는 크게 접근 제어자와 그 외의 제어자로 나눌 수 있다.

```
접근 제어자	  public, protected, default, private
그	   외	static, final, abstract, native, transient, synchronized, volatile, strictfp
```

 제어자는 클래스나 멤버변수와 메서드에 주로 사용되며, 하나의 대상에 대해서 여러 제어자를 조합하여 사용하는 것이 가능하다.

 단, 접근 제어자는 한 번에 네 가지 중 하나만 선택해서 사용할 수 있다. 즉, 하나의 대상에 대해서 public과 private을 함께 사용할 수 없다는 것이다.

> **I 참고 I** 제어자들 간의 순서는 관계없지만 주로 접근 제어자를 제일 왼쪽에 놓는 경향이 있다. 

### 4_2 static - 클래스의, 공통적인[📑](#contents)<a id='4_2'></a>

 static은 '클래스의'또는 '공통적인'의 의미를 가지고 있다. 인스턴스변수는 하나의 클래스로부터 생성되었더라도 각기 다른 값을 유지하지만. 클래스변수(static멤버변수)는 인스 턴스에 관계없이 같은 값을 갖는다. 그 이유는 하나의 변수를 모든 인스턴스가 공유하기 때문이다.
 static이 붙은 멤버변수와 메서드, 그리고 초기화 블럭은 인스턴스가 아닌 클래스에 관계된 것이기 때문에 인스턴스를 생성하지 않고도 사용할 수 있다.
인스턴스 메서드와 static메서드의 근본적인 차이는 메서드 내에서 인스턴스 멤버를 사용 하는가의 여부에 있다.

```
static이 사용될 수 있는 곳 - 멤버변수, 메서드, 초기화 블럭
```

#### `static`

* 멤버변수
  * 모든 인스턴스에 공통적으로 사용되는 클래스변수가 된다.
  * 클래스변수는 인스턴스를 생성하지 않고도 사용 가능하다.
  * 클래스가 메모리에 로드될 때 생성된다.
* 메서드
  * 인스턴스를 생성하지 않고도 호출이 가능한 static 메서드가 된다.
  - static메서드 내에서는 인스턴스멤버들을 직접 사용할 수 없다.

 인스턴스 멤버를 사용하지 않는 메서드는 static을 붙여서 static메서드로 선언하는 것을 고려해보도록 하자. 가능하다면 static메서드로 하는 것이 인스턴스를 생성하지 않고도 호 출이 가능해서 더 편리하고 속도도 더 빠르다.

> **I 참고 I** static초기화 블럭은 클래스가 메모리에 로드될 때 단 한번만 수행되며, 주로 클래스변수(static변수)를 초기화하는 데 주로 사용된다.

```java
class StaticTest {
    static int width = 200; // 클래스 변수（static변수)
    static int height = 120; // 클래스 변수（static변수)
    static { // 클래스초기화블럭
        // static변수의 복잡한 초기화 수행
    }
    static int max （int a, int b） { // 클래스 메서드（static메서드)
        return a > b ? a : b;
    }
}
```

### 4_3 final - 마지막의, 변경될 수 없는[📑](#contents)<a id='4_3'></a>

 final은 ‘마지막의’ 또는 ‘변경될 수 없는’의 의미를 가지고 있으며 거의 모든 대상에 사용 될 수 있다.

 변수에 사용되면 값을 변경할 수 없는 상수가 되며, 메서드에 사용되면 오버라이딩을 할 수 없게 되고 클래스에 사용되면 자신을 확장하는 자손클래스를 정의하지 못하게 된다.

```
final이 사용될 수 있는 곳 - 클래스, 메서드, 멤버변수, 지역변수
```

#### `final`

* 클래스
  * 변경될 수 없는 클래스, 확장될 수 없는 클래스가 된다. 그래서 final로 지정된 클래스는 다른 클래스의 조상이 될 수 없다.
* 메서드
  * 변경될 수 없는 메서드, final로 지정된 메서드는 오버라이딩을 통해 재정의 될 수 없다.
* 멤버변수, 지역변수
  * 변수 앞에 final이 붙으면, 값을 변경할 수 없는 상수가 된다.

> **I 참고 I** 대표적인 final클래스로는 String과 Math가 있다.

```java
final class FinalTest {				// 조상이 될 수 없는 클래스
    final int MAX_SIZE = 10;		// 값을변경할 수없는멤버변수 （상수）
    final void getMaxSize() {		// 오버라이딩할 수없는메서드 （변경불가）
        final int LV = MAX_SIZE;	// 값을변경할 수없는 지역변수 （상수
        return MAX SIZE;
    }
}
```

#### 생성자를 이용한 final멤버 변수의 초기화

 final이 붙은 변수는 상수이므로 일반적으로 선언과 초기화를 동시 에 하지만, 인스턴스변
수의 경우 생성자에서 초기화 되도록 할 수 있다.

클래스 내에 매개변수를 갖는 생성자를 선언하여, 인스턴스를 생성할 때 final이 붙은 멤
버변수를 초기화하는데 필요한 값을 생성자의 매개변수로부터 제공받는 것이다.

 이 기능을 활용하면 각 인스턴스마다 final이 붙은 멤버 변수가 다른 값을 갖도록 하는 것
이 가능하다.

 만일 이것이 불가능하다면 클래스에 선언된 final이 붙은 인스턴스변수는 모든 인스턴스
에서 같은 값을 가져야만 할 것이다.

 예를 들어 카드의 경우, 각 카드마다 다른 종류와 숫자를 갖지만, 일단 카드가 생성되면
카드의 값이 변경되어서는 안 된다. 52장의 카드 중에서 하나만 잘못 바꿔도 같은 카드가
2장이 되는 일이 생기기 때문이다. 그래서 카드의 값을 바꾸기 보다는 카드의 순서를 바
꾸는쪽이 더 안전한 방법이다.

```java
class Card {
    final int NUMBER;			// 상수지만 선언과 함께 초기화 하지 않고
    final String KIND;			// 생성자에서 단 한번만 초기화할 수 있다.
    static int width = 100;
    static int height = 250;
    Card(String kind, int num){
        KIND = kind;			//매개변수로 넘겨받은 값으로 KIND와 NUMBER를 초기화한다.
        NUMBER = num;
    }
    Card() {
        this("HEART", 1);
    }
    public String toString() {
        return KIND +" "+ NUMBER;
    }
}
class FinalCardTest {
    public static void main(String args[]) {
        Card c = new Card("HEART", 10);
        c.NUMBER = 5; 			//에러!!! cannot assign a value to final variable NUMBER
        System.out.printin(c.KIND);
        System. out.printin (c. NUMBER);
        System.out.printin(c); // System.out.printin(c.toString());
    }
}
```

> 예제 7—12/ch7/FinalCardTest. java

```java
HEART
10
HEART 10
```



### 4_4 abstract - 추상의, 미완성의[📑](#contents)<a id='4_4'></a>

 abstract는 '미완성'의 의미를 가지고 있다. 메서드의 선언부만 작성하고 실제 수행내용은 구현하지 않은 추상 메서드를 선언하는데 사용된다.
그리고 클래스에 사용되어 클래스 내에 추상메서드가 존재한다는 것을 쉽게 알 수 있게 한다. 보다 자세한 내용은 ‘추상 클래스’(p.375)에서 다룬다.

```
abstract가 사용될 수 있는 곳 - 클래스, 메서드
```

#### `abstract`

* 클래스
  * 클래스 내에 추상 메서드가 선언되어 있음을 의미한다.
* 메서드
  * 선언부만 작성하고 구현부는 작성하지 않은 추상 메서드임을 알린다.

추상 클래스는 아직 완성되지 않은 메서드가 존재하는 ‘미완성 설계도’이므로 인스턴스를 생성할수 없다.

```java
abstract class AbstractTest {		// 추상 클래스 (추상 메서드를 포함한 클래스)
    abstract void move ();			// 추상 메서드 (구현부가 없는 메서드)
}
```

 꽤 드물지만 추상 메서드가 없는 클래스, 즉 완성된 클래스도 abstract를 붙여서 추상 클래스로 만드는 경우도 있다. 예를 들어, java.awt.event.WindowAdapter는 아래와 같이 아무런 내용이 없는 메서드들만 정의되어 있다. 이런 클래스는 인스턴스를 생성해봐야 할 수 있는 것이 아무것도 없다. 그래서 인스턴스를 생성하지 못하게 클래스 앞에 제어자 `abstract`를 붙여 놓은 것이다.

```java
public abstract class WindowAdapter
    implements WindowListener, WindowStateListener, WindowFocusListener {
    public void windowOpened(WindowEvent e) {} 
    public void windowclosing(WindowEvent e) {} 
    public void windowClosed(WindowEvent e) {} 
    public void windowlconified(WindowEvent e) {}
    ...
}
```

 이 클래스 자체로는 쓸모가 없지만, 다른 클래스가 이 클래스를 상속받아서 일부의 원하 는 메서드만 오버라이딩해도 된다는 장점이 있다. 만일 이 클래스가 없다면 아무런 내용도 없는 메서드를 잔뜩 오버라이딩해야 한다. 아직 추상 클래스와 인터페이스를 배우지 않았으니 ‘이런 경우도 있구나.’라고 가볍게 참고만 하기 바란다.

> **I 참고 I** 가끔 이런 질문을 받기 패문에 참고로 적어놓은 것일 뿐이니 심각하게 고민하지 않기 바란다.

### 4_5 접근 제어자(access modifier)[📑](#contents)<a id='4_5'></a>

 접근 제어자는 멤버 또는 클래스에 사용되어, 해당하는 멤버 또는 클래스를 외부에서 접 근하지 못하도록 제한하는 여할을 한다.

 접근 제어자가 default임’ 알리기 위해 실제로 default를 붙이지는 않는다. 클래스나 멤버변수, 메서드, 생성자에 접근 제어자가 지정되어 있지 않다면, 접근 제어자가 default 임을 뜻한다.

```
접근 제어자가 사용될 수 있는 곳 - 클래스, 멤버변수, 메서드, 생성자
private		같은 클래스 내에서만 접근이 가능하다.
default		같은 패키지 내에서만 접근이 가능하다.
protected	같은 패키지 내에서, 그리고 다른 패키지의 자손클래스에서 접근이 가능하다.
public		접근 제한이 전혀 없다.
```

|   제어자    | 같은 클래스 | 같은 패키지 | 자손클래스 | 전 체 |
| :---------: | :---------: | :---------: | :--------: | :---: |
|  `public`   |      O      |      O      |     O      |   O   |
| `protected` |      O      |      O      |     O      |       |
| `(default)` |      O      |      O      |            |       |
|  `private`  |      O      |             |            |       |

접근 범위가 넓은 쪽에서 좁은 쪽의 순으로 왼쪽부터 나열하면 다음과 같다.

```
public > protected > (default) > private
```

 public은 접근 제한이 전혀 없는 것이고, private은 같은 클래스 내에서만 사용하도록 제한하는 가장 높은 제한이다. 그리고 default는 같은 패키지내의 클래스에서만 접근이 가 능하도록 하는 것이다.

 마지막으로 protected는 패키지에 관계없이 상속관계에 있는 자손클래스에서 접근할 수 있도록 하는 것이 제한목적이지만, 같은 패키지 내에서도 접근이 가능하다. 그래서 protected가 default보다 접근범위가 더 넓다.

> **I 참고 I** 접근 제어자가 default라는 것은 아무런 접근 제어자도 붙이지 않는 것을 의미한다.

| 대상     | 사용가능한 접근 제어자                |
| -------- | ------------------------------------- |
| 클래스   | public, (default)                     |
| 메서드   | public, protected, (default), private |
| 멤버변수 | public, protected, (default), private |
| 지역변수 | 없음                                  |

> **표7-1** 대상에 따라 사용할 수 있는 접근 제어자

#### 접근 제어자를 이용한 캡슐화

 클래스나 멤버, 주로 멤버에 접근 제어자를 사용하는 이유는 클래스의 내부에 선언된 데이터를 보호하기 위해서이다.

 데이터가 유효한 값을 유지하도록, 또는 비밀번호와 같은 데이터를 외부에서 함부로 변경하지 못하도록 하기 위해서는 외부로부터의 접근을 제한하는 것이 필요하다.

 이것을 데이터 감추기(data hiding)라고 하며, 객체지향개념의 캡슐화(encapsulation) 에 해당하는 내용이다.

 또 다른 이유는 클래스 내에서만 사용되는, 내부 작업을 위해 임시로 사용되는 멤버변수 나 부분작업을 처리하기 위한 메서드 등의 멤버들을 클래스 내부에 감추기 위해서이다.

외부에서 접근할 필요가 없는 멤버들을 private으로 지정하여 외부에 노출시키지 않음으 로써 복잡성을 줄일 수 있다. 이것 역시 캡슐화에 해당한다.

```
접근 제어자를 사용하는 이유
- 외부로부터 데이터를 보호하기 위해서
- 외부에는 불필요한, 내부적으로만 사용되는 부분을 감추기 위해서
```

 만일 메서드 하나를 변경해야 한다고 가정했을 때, 이 메서드의 접근 제어자가 public이라면, 메서드를 변경한 후에 오류가 없는지 테스트해야하는 범위가 넓다. 그러나 접근 제어자가 `default`라면 패키지 내부만 확인해 보면 되고, `private`이면 클래스 하나만 살펴보면 된다. 이처럼 접근 제어자 하나가 때로는 상당한 차이를 만들어낼 수 있다. 접근 제어자를 적절히 선택해서 접근 범위를 최소화하도록 노력하자. 

 이제 구체적인 예제를 통해 자세히 알아보자. 시간을 표시하기 위한 클래스 Time이 다 음과같이 정의되어 있을 때,

```java
public class Time {
    public int hour;
    public int minute;
    public int second;
}
```

 이 클래스의 인스턴스를 생성한 다음, 멤버변수에 직접 접근하여 값을 변경 할 수 있을 것이다.

```java
Time t = new Time();
t.hour =25;
```

 멤버변수 hour는 0보다는 같거나 크고 24보다는 작은 범위의 값을 가져야 하지만 위의 코드에서처럼 잘못된 값을 지정한다고 해도 이것을 막을 방법은 없다.

 이런 경우 멤버변수를 `private`이나 `protected`로 제한하고 멤버변수의 값을 읽고 변경할 수 있는 `public`메서드를 제공함으로써 간접적으로 멤버변수의 값을 다룰 수 있도록 하는 것이 바람직하다.

```java
public class Time {
    private int hour;
    private int minute;
    private int second;  //접근 제어자를 private으로 하여 외부에서 직접 접근하지 못하도록 한다.
	public int getHour() { return hour; }
    public void setHour(int hour) {
        if (hour < 0 || hour > 23) return;
        this.hour = hour;
    }
    public int getMinute() { return minute; }
    public void setMinute(int minute) {
        if (minute < 0 || minute > 59) return;
        this.minute = minute;
    }
    public int getSecond() { return second; }
    public void setSecond(int second) {
        if (second < 0 || second > 59) return;
        this.second = second;
    }
}
```

 get으로 시작하는 메서드는 단순히 멤버변수의 값을 반환하는 일을 하고, set으로 시작하 는 메서드는 매개변수에 지정된 값을 검사하여 조건에 맞는 값일 때만 멤버변수의 값을 변경하도록작성되어 있다. 

 만일 상속을 통해 확장될 것이 예상되는 클래스라면 멤버에 접근 제한을 주되 자손클래 스에서 접근하는 것이 가능하도록 하기 위해 `private`대신 `protected`를 사용한다. `private`이 붙은 멤버는 자손 클래스에서도 접근이 불가능하기 때문이다. 

 보통 멤버변수의 값을 읽는 메서드의 이름을 'get멤버변수이름'으로 하고, 멤버변수의 값을 변경하는 메서드의 이름을 'set멤버변수이름'으로 한다. 반드시 그렇게 해야 하는 것은 아니지만 암묵적인 규칙이므로 특별한 이유가 없는 한 따르도록 하자. 그리고 get으로 시작하는 메서드를 ‘겟터(getter)’, set으로 시작하는 메서드를 ‘셋터'(setter)’라고 부른다.

> 예제 7-13/ch7/TimeTest. java

```java
public class TimeTest {
    public static void main(String[] args) {
        Time t = new Time(12, 35, 30);
        System.out.println(t);
        // t.hour = 13; 에러 변수 hour의 접근제어자가 private이므로 접근할 수 없다.
        t. setHour (t.getHour () +1); // 현재시간보다 1시간 후로 변경한다.
        System.out.printin(t); // System.out.printin(t.toString());과같다.
    }
}
class Time {
    private int hour, minute, second;
    Time(int hour, int minute, int second) {
        setHour(hour);
        setMinute(minute);
        setSecond(second);
    }
    public int getHour() { return hour; }
        public void setHour(int hour) {
            if (hour < 0 || hour > 23) return;
            this.hour = hour;
        }
	public int getMinute() { return minute; }
    public void setMinute(int minute) {
        if (minute < 0 || minute > 59) return;
        this.minute = minute;
    }
	public int getSecondO { return second; }
    public void setSecond(int second) {
        if (second < 0 || second > 59) return;
        this. second = second;
    }
    public String toString() {
        return hour + ":" + minute + ":" + second;
    }
}

// 실행 결과
12:35:30
13:35:30
```

 Time클래스의 모든 멤버변수의 접근 제어자를 `private`으로 하고. 이 들을 다루기 위한 `public`메서드를 추가했다. 그래서 `t.hour = 13;`과 같이 멤버변수로의 직접적인 접근은 허가되지 않는다. 메서드를 통한 접근만이 허용될 뿐이다.

> **I 참고 I** 하나의 소스파일 (* java)에는 public클래스가 단 하나만 존재할 수 있으며. 소스파일의 이름은 반드시 public클래스 의 이름과 같아야 한다.



### 4_6 제어자(modifier)의 조합[📑](#contents)<a id='4_6'></a>

 지금까지 접근 제어자와 `static`, `final`, `abstract`에 대해서 학습했다. 이 외에도 더 많은 제어자들이 있으나 관련 내용이 현재 학습범위를 넘어선다고 판단되어 생략하였다. 이들은 앞으로 자바를 더 깊게 공부하게 되면서 자연스럽게 학습하게 될 것이다. 제어자가 사용될 수 있는 대상을 중심으로 제어자를 정리해보았다. 제어자의 기본적인 의미와 그 대상에 따른 의미 변화를 다시 한 번 되새겨 보도록 하자.

| 대 상    | 사용가능한 제어자                         |
| -------- | ----------------------------------------- |
| 클래스   | public, (default) , final, abstract       |
| 메서드   | 모든 접근 제어자, final, abstract, static |
| 멤버변수 | 모든 접근 제어자, final, static           |
| 지역변수 | final                                     |

> **표 7-2** 대상에 따라 사용할 수 있는 제어자

#### 생성자의 접근 제어자

 생성자에 접근 제어자를 사용함으로써 인스턴스의 생성을 제한할 수 있다. 보통 생성자의 접근 제어자는 클래스의 접근 제어자와 같지만, 다르게 지정할 수도 있다. 

 생성자의 접근 제어자를 `private`으로 지정하면, 외부에서 생성자에 접근할 수 없으므로 인스턴스를 생성할 수 없게 된다. 그래도 클래스 내부에서는 인스턴스를 생성할 수 있다.

```java
class Singleton {
private Singleton () {
    	...
	}
    ...
}
```

 대신 인스턴스를 생성해서 반환해주는 `public`메서드를 제공함으로써 외부에서 이 클래스의 인스턴스를 사용하도록 할 수 있다. 이 메서드는 `public`인 동시에 `static`이어야 한다.

```java
class Singleton {
    	...
    private static Singleton s = new Singleton (); // getinstance( )에서 사용될 수 있도록... 인스턴스가 미리 생성되어야 하므로 static이어야 한다.
    private Singleton () {
        ...
    }
	// 인스턴스를 생성하지 않고도 호출할 수 있어야 하므로 static이어야 한다.
	public static Singleton getlnstance() {
		return s;
    }
    ...
}
```

 이처럼 생성자를 통해 직접 인스턴스를 생성하지 못하게 하고 `public`메서드를 통해 인스턴스에 접근하게 함으로써 사용할 수 있는 인스턴스의 개수를 제한할 수 있다. 

또 한 가지, 생성자가 `private`인 클래스는 다른 클래스의 조상이 될 수 없다. 왜냐하면, 자 손클래스의 인스턴스를 생성할 때 조상클래스의 생성자를 호출해야만 하는데, 생성자의 접근 제어자가 `private`이므로 자손클래스에서 호출하는 것이 불가능하기 때문이다. 

그래서 클래스 앞에 `final`을 더 추가하여 상속할 수 없는 클래스라는 것을 알리는 것이 좋다. Math클래스는 몇 개의 상수와 `static`메서드만으로 구성되어 있기 때문에 인스턴스를 생성할 필요가 없다. 그래서 외부로부터의 불필요한 접근을 막기 위해 다음과 같이 생성자 의 접근 제어자를 `private`으로 지정하였다.

```java
public final class Math {
    private Math() {}
    ...
}
```

> 예제 7-14/ch7/SingletonTest. java

```java
final class Singleton {
    private static Singleton s = new Singleton ();
    private Singleton () {
        //...
    }
    public static Singleton getlnstance() {
        if(s==null)
            s = new Singleton();
        return s;
    }
}
class SingletonTest {
    public static void main(String args[]) {
        // Singleton s = new Singleton (); 에러! Sin이eton() has private access in Singleton
        Singleton s = Singleton.getlnstance ();
    }
}
```




## 6_추상클래스(abstract class)[📑](#contents)<a id="6"></a>

### 6_1 추상클래스란?[📑](#contents)<a id='6_1'></a>

 클래스를 설계도에 비유한다면, 추상클래스는 미완성 설계도에 비유할 수 있다. 미완성 설계도란, 단어의 뜻 그대로 완성되지 못한 채로 남겨 진 설계도를 말한다.

 클래스가 미완성이라는 것은 멤버의 개수에 관계된 것이 아니라, 단지 미완성 메서드(추상메서드)를 포함하고 있다는 의미이다.

 미완성 설계도로 완성된 제품을 만들 수 없듯이 추상클래스로 인스턴스는 생성할 수 없다. 추상클래스는 상속을 통해서 자손클래스에 의해서만 완성될 수 있다.

 추상클래스 자체로는 클래스로서의 역할을 다 못하지만, 새로운 클래스를 작성하는데 있어서 바탕이 되는 조상클래스로서 중요한 의미를 갖는다. 새로운 클래스를 작성할 때 아무것도 없는 상태에서 시작하는 것보다는 완전하지는 못하더라도 어느 정도 틀을 갖춘 상태에서 시작하는 것이 나을 것이다.

 실생활에서 예를 들자면, 같은 크기의 TV라도 기능의 차이에 따라 여러 종류의 모델이 있지만, 사실 이 들의 설계도는 아마 90% 정도는 동일할 것이다. 서로 다른 세 개의 설계도를 따로 그리는 것보다는 이들의 공통 부분만을 그린 미완성 설계도를 만들어 놓고, 이 미완성 설계도를 이용해서 각각의 설계도를 완성하는 것이 훨씬 효율적일 것이다.

 추상클래스는 키워드 `abstract`를 붙이기만 하면 된다. 이렇게 함으로써 이 클래스를 사용할 때, 클래스 선언부의 abstract를 보고 이 클래스에는 추상메서드가 있으니 상속을 통해서 구현해주어야 한다는 것을 쉽게 알 수 있을 것이다.

```java
abstract class 클래스이름 {
    ...
}
```

 추상클래스는 추상메서드를 포함하고 있다는 것을 제외하고는 일반클래스와 전혀 다르지 않다. 추상클래스에도 생성자가 있으며, 멤버변수와 메서드도 가질 수 있다.

> **I 참고 I** 추상메서드를 포함하고 있지 않은 클래스에도 키워드 `abstract` 를 붙여서 추상클래스로 지정할 수도 있다. 추상메서 드가 없는 완성된 클래스라 할지라도 추상클래스로 지정되면 클래스의 인스턴스를 생성할 수 없다.

### 6_2 추상메서드(abstract method)[📑](#contents)<a id='6_2'></a>

 메서드는 선언부와 구현부(몸통)로 구성되어 있다고 했다. 선언부만 작성하고 구현부는 작성하지 않은 채로 남겨 둔 것이 추상메서드이다. 즉, 설계만 해 놓고 실제 수행될 내용은 작성하지 않았기 때문에 미완성 메서드인 것이다.

 메서드를 이와 같이 미완성 상태로 남겨 놓는 이유는 메서드의 내용이 상속받는 클래스에 따라 달라질 수 있기 때문에 조상 클래스에서는 선언부만을 작성하고, 주석을 덧붙여 어떤 기능을 수행할 목적으로 작성되었는지 알려 주고, 실제 내용은 상속받는 클래스에서 구현하도록 비워 두는 것이다. 그래서 추상클래스를 상속받는 자손 클래스는 조상의 추상 메서드를 상황에 맞게 적절히 구현해주어야 한다.

 추상메서드 역시 키워드 `abstract`앞에 붙여 주고, 추상메서드는 구현부가 없으므로 괄호{ }대신 문장의 끝을 알리는 `;`을 적어준다. 

```java
/* 주석을 통해 어떤 기능을 수행할 목적으로 작성하였는지 설명한다. */
abstract 리턴타입 메서드이름()；
```

 추상클래스로부터 상속받는 자손클래스는 오버라이딩을 통해 조상인 추상클래스의 추상 메서드를 모두 구현해주어야 한다. 만일 조상으로부터 상속받은 추상메서드 중 하나라도 구현하지 않는다면, 자손클래스 역시 추상클래스로 지정해 주어야 한다.

```java
abstract class Player { // 추상클래스 
    abstract void play(int pos);	// 추상메서드
    abstract void stop ();			// 추상메서드
}
class AudioPlayer extends Player {
    void play (int pos) { /* 내용 생략 */ }	// 추상메서드를 구현
    void stop () {  /* 내용 생략 */ }		// 추상메서드를 구현
}
abstract class AbstractPlayer extends Player {
    void play (int pos) { /* 내용 생략 */ } // 추상메서드를 구현
}
```

 실제 작업내용인 구현부가 없는 메서드가 무슨 의미가 있을까 싶기도 하겠지만. 메서드를 작성할 때 실제 작업내용인 구현부보다 더 중요한 부분이 선언부이다.

 메서드의 이름과 메서드의 작업에 필요한 매개변수. 그리고 작업의 결과로 어떤 타입의 값을 반환할 것인가를 결정하는 것은 쉽지 않은 일이다. 선언부만 작성해도 메서드의 절반 이상이 완성된 것이라 해도 과언이 아니다.

 메서드를 사용하는 쪽에서는 메서드가 실제로 어떻게 구현되어있는지 몰라도 메서드의 이름과 매개변수, 리턴타입, 즉 선언부만 알고 있으면 되므로 내용이 없을 지라도 추상메서드를 사용하는 코드를 작성하는 것이 가능하며, 실제로는 자손클래스에 구현된 완성된 메서드가 호출되도록 할 수 있다.

### 6_3 추상클래스의 작성[📑](#contents)<a id='6_3'></a>

 여러 클래스에 공통적으로 사용될 수 있는 클래스를 바로 작성하기도 하고, 기존의 클래스의 공통적인 부분을 뽑아서 추상클래스로 만들어 상속하도록 하는 경우도 있다.

 참고로 추상의 사전적 정의는 다음과 같다.

```
추상[抽象]
낱낱의 구체적 표상(表象)이나 개념에서 공통된 성질을 뽑아 이를 일반적인 개념으로 파악하는 정신 작용
```

 상속이 자손 클래스를 만드는데 조상 클래스를 사용하는 것이라면, 이와 반대로 추상화는 기존의 클래스의 공통부분을 뽑아내서 조상 클래스를 만드는 것이라고 할 수 있다.

 추상화를 구체화와 반대되는 의미로 이해하면 보다 쉽게 이해할 수 있을 것이다. 상속계층도를 따라 내려갈수록 클래스는 점점 기능이 추가되어 구체화의 정도가 심해지며, 상속계층도를 따라 올라갈수록 클래스는 추상화의 정도가 심해진다고 할 수 있다. 즉, 상속계 층도를 따라 내려 갈수록 세분화되며, 올라갈수록 공통요소만 남게 된다.

```java
추상화	클래스간의 공통점을 찾아내서 공통의 조상을 만드는 작업 
구체화	상속을 통해 클래스를 구현, 확장하는 작업
```

 아래에 Player라는 추상클래스를 작성해 보았다. 이 클래스는 VCR이나 Audio와 같은 재생 가능한 기기(Player)를 클래스로 작성할 때, 이 들의 조상으로 사용될 수 있을 것이다.

```java
abstract class Player { 
    boolean pause;			// 일시정지 상태를 저장하기 위한 변수
    int currentPos;			// 현재 Play되고 있는 위치를 저장하기 위한 변수
    Player () { 			// 추상클래스도 생성자가 있어야 한다.
        pause = false;
        currentPos = 0; 
    } 
    /** 지정된위치 (pos) 에서재생을시작하는기능이수행하도록작성되어야 한다. */
    abstract void play (int pos);		// 추상메서드
    /** 재생을즉시멈추는기능을 수행하도록작성되어야 한다. */
    abstract void stop(); 				// 추상메서드
    void play () {
        play (currentPos);				// 추상메서드를 사용할 수 있다.
    }
    void pause () {
        if (pause) { // pause가 true일 때 (정지상태) 에서 pause가 호출되면, 
            pause = false;				// pause의 상태를 false로 바꾸고,
            play (currentPos);			// 현재의 위치에서 play를 한다.
		} else { // pause가 false일 때 (play상태) 에서 pause가 호줄되면,
            pause = true;				// pause의 상태를 true로 바꾸고
            stop(); 					// play를 멈춘다.
        }
    }
}
```

 이제 Player클래스를 조상으로 하는 CDPlayer 클래스를 만들어 보자.

```java
class CDPlayer extends Player {
    void play(int currentPos) {
        /* 조상의 추상메서드를 구현. 내용 생략 */ 
    }
    void stop() {
        /* 조상의추상메서드를구현 . 내용생략 */
    }
    // CDPlayer클래스에 추가로 정의된 멤버
    int currentTrack; // 현재 재생 중인 트랙
    void nextTrack() {
        currentTrack++;
		...
    }
    void preTrack () {
        if(currentTrack > 1) {
            currentTrack--;
        }
        ...
    }
}
```

 조상 클래스의 추상메서드를 CDPlayer클래스의 기능에 맞게 완성해주고, CDPlayer만의 새로운 기능들을 추가하였다.

 사실 Player클래스의 play(int pos)와 stop()을 추상메서드로 하는 대신, 아무 내용도 없는 메서드로 작성할 수도 있다. 아무런 내용도 없이 단지 괄호{}만 있어도, 추상메서드가 아닌 일반 메서드로 간주되기 때문이다.

```java
class Player {
    ...
    void play(int pos) {}
    void stop () {}
    ...
}
```

 어차피 자손 클래스에서 오버라이딩하여 자신의 클래스에 맞게 구현할 테니 추상메서드로 선언하는 것과 내용없는 빈 몸통만 만들어 놓는 것이나 별 차이가 없어 보인다.

 그래도 굳이 abstract를 붙여서 추상메서드로 선언하는 이유는 자손 클래스에서 추상메서드를 반드시 구현하도록 강요하기 위해서이다.

 만일 추상메서드로 정의되어 있지 않고 위와 같이 빈 몸통만 가지도록 정의되어 있다면, 상속받는 자손 클래스에서는 이 메서드들이 온전히 구현된 것으로 인식하고 오버라이딩 을 통해 자신의 클래스에 맞도록 구현하지 않을 수도 있기 때문이다.

 하지만 abstract를 사용해서 추상메서드로 정의해놓으면, 자손 클래스를 작성할 때 이들이 추상메서드이므로 내용을 구현해주어야 한다는 사실을 인식하고 자신의 클래스에 알맞게 구현할 것이다.

 이번엔 기존의 클래스로부터 공통된 부분을 뽑아내어 추상클래스를 만들어 보도록 하자.

```java
class Marine { 		// 보병
    int x, y; 		// 현재 위치
    void move (int xz int y)	{ /* 지정된 위치로 이동 */ }
    void stop() 				{ /* 현재 위치에정지 */ }
    void stimPack()				{ /* 스팀팩을사용한다. */ }
class Tank { 		// 탱크
    int x, y; 		// 현재 위치
    void move (int x, int y)	{/* 지정된위치로이동 */ }
    void stop ()				{/* 현재 위치에정지 */ }
    void changeMode()			{/* 공격모드를변환한다. */ }
class Dropship { 	// 수송선
    int x, y; 		// 현재 위치
    void move (int x, int y)	{/* 지정된위치로이동 */ }
	void stop ()				{/* 현재 위치에정지 */ }
	void load()					{/* 선택된 대상을태운다. */ }
	void unload ()				{/* 선택된 대상을내린다. */ }
}
```

 유명한 컴퓨터 게임에 나오는 유닛들을 클래스로 간단히 정의해보았다. 이 유닛들은 각자 나름대로의 기능을 가지고 있지만 공통부분을 뽑아내어 하나의 클래스로 만들고, 이 클래스로부터 상속받도록 변경해보자.

```java
abstract class Unit {
    int x, y;
    abstract void move (int xr int y);
    void stop() { /* 현재 위치에 정지 */ }
}
class Marine extends Unit {		// 보병
    void move(int x, int y)		{ /* 지정된위치로이동 */ }
              void stimPack()	{ /* 스팀팩을사용한다.*/ }
}
class Tank extends Unit {		// 탱크
    void move(int x int y)		{ /* 지정된위치로 이동 시*/ }
    void changeMode()			{ /* 공격모드를변환한다. */ }
}
class Dropship extends Unit {	// 수송선
    void move (int x, int y)	{ /* 지정된 위치로 이동 */ }
    void load()					{ /* 선택된 대상을태운다. */ }
    void unload()				{ /* 선택된 대상을 내린다. */ }
}
```

각 클래스의 공통부분을 뽑아내서 Unit클래스를 정의하고 이로부터 상속받도록 하였다. 이 Unit클래스는 다른 유닛을 위한 클래스를 작성하는데 재활용될 수 있을 것이다.

 이들 클래스에 대해서 stop메서드는 선언부와 구현부 모두 공통적이지만, Marine, Tank 는 지상유닛이고 Dropship은 공중유닛이기 때문에 이동하는 방법이 서로 달라서 move메서드의 실제 구현 내용이 다를 것이다.

 그래도 move메서드의 선언부는 같기 때문에 추상메서드로 정의할 수 있다. 최대한의 공통부분을 뽑아내기 위한 것이기도 하지만, 모든 유닛은 이동할 수 있어야 하므로 Unit클래스에는 move메서드가 반드시 필요한 것이기 때문이다.

 move메서드가 추상메서드로 선언된 것에는, 앞으로 Unit클래스를 상속받아서 작성되는 클래스는 move메서드를 자신의 클래스에 알맞게 반드시 구현해야 한다는 의미가 담겨 있는 것이기도 하다.

```java
Unit[] group = new Unit[4];
group[0] = new Marine ();
group[1]= new Tank ();
group[2]= new Marine ();
group[3]= new Dropship ();

for (int i =0; i < group.length;i++) 
    group[i].move (100, 200); // Unit배열의 모든 유닛을 좌표(100. 200)의 위치로 이동한다.
```

 위의 코드는 공통조상인 Unit클래스 타입의 참조변수 배열을 통해서 서로 다른 종류의 인 스턴스를 하나의 묶음으로 다룰 수 있다는 것을 보여 주기 위한 것이다.

 다형성에서 배웠듯이 조상 클래스타입의 참조변수로 자손 클래스의 인스턴스를 참조하 는 것이 가능하기 때문에 이처럼 조상 클래스타입의 배열에 자손 클래스의 인스턴스를 담 을 수 있는 것이다.

 만일 이들 클래스간의 공통조상이 없었다면 이처럼 하나의 배열로 다룰 수 없을 것이다. Unit클래스에 move메서드가 비록 추상메서드로 정의되어 있다 하더라도 이처럼 Unit클 래스 타입의 참조변수로 move메서드를 호출하는 것이 가능하다. 메서드는 참조변수의 타입에 관계없이 실제 인스턴스에 구현된 것이 호출되기 때문이다.

  group[i].move(100, 200)과 같이 호출하는 것이 Unit클래스의 추상메서드인 move를 호출하는 것 같이 보이지만 실제로는 이 추상메서드가 구현된 Marine, Tank, Dropship 인스턴스의 메서드가 호출되는 것이다.

 모든 클래스의 조상인 Object클래스 타입의 배열로도 서로 다른 종류의 인스턴스를 하 나의 묶음으로 다룰 수 있지만, Object클래스에는 move메서드가 정의되어 있지 않기 때문에 move메서드를 호출하는 부분에서 에러가 발생한다.

```java
Object[] group = new Object[4];
group[0] = new Marine ();
group[1] = new Tank ();
group[2] = new Marine ();
group[3] = new Dropship ();
for (int i = 0; i < group.length; i++)
    group[i].move(100, 200);//에러!!Object클래스에 move메서드가 정의되어 있지 않다.
```

