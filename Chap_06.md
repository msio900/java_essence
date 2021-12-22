# Chapter 06 : 객체지향 프로그래밍[↩](../../)

## contents📑<a id='contents'></a>

* 1_객체지향언어
* 2_클래스와 객체
* 3_변수와 메서드
* 4_오버로딩(Overloading)
* 5_생성자(constructor) [👉](##5생성자(constructor)📑)
  * 5_1생성자란? [✏](#5_1)
  * 5_2 기본 생성자(default constructor) [✏](#5_2)
  * 5_3 매개변수가 있는 생성자 [✏](#5_3)
  * 5_4 생성자에서 다른 생성자 호출하기 - this(), this [✏](#5_4)
  * 5_5 생성자를 이용한 인스턴스의 복사 [✏](#5_5)

* 6_변수의 초기화

## 5_생성자(constructor)[📑](#contents)

### 5_1 생성자란?[📑](#contents)<a id='5_1'></a>

  생성자는 인스턴스가 생성될 때 호출되는 ‘인스턴스 초기화 메서드’이다. 따라서 인스턴스 변수의 초기화 작업에 주로 사용되며, 인스턴스 생성 시에 실행되어야 할 작업을 위해서 도 사용된다.

[^참고 | 인스턴스 초기화]: 인스턴스 변수들을 초기화 하는 것을 의미함.

 생성자 역시 메서드처럼 클래스 내에 선언되며, 구조도 메서드와 유사하지만 리턴값이 없다는 점이 다르다. 그렇다고 해서 생성자 앞에 리턴값이 없음을 뜻하는 키워드 `void`를 사용하지는 않고, 단지 아무 것도 적지 않는다. 생성자의 조건은 다음과 같다.

> 1. 생성자의 이름은 클래스의 이름과 같아야한다.
> 2. 생성자는 리턴 값이 없다.

[^참고]: 생성자도 메서드이기 때문에 리턴값이 없다는 의미의 `void`를 붙여야 하지만, 모든 생성자가 리턴값이 없으므로  `void`  를 생략할 수 있게 한 것이다.

#### 생성자 정의법

```java
클래스이름(타입 변수명, 타입 변수명, ...) {
    //인스턴스 생성 시 수행될 코드,
    // 주로 인스턴스 변수의 초기화 코드를 적는다.    
}
class Card {
    Card() {	//매개변수가 없는 생성자.
        ...
    }
    Card(String k, int num) {	//매개변수가 있는 생성자
        ...
    }
    ...
}
```

 연산자 `new`가 인스턴스를 생성하는 것이지 생성자가 인스턴스를 생성하는 것이 아니다. 생성자라는 용어 때문에 오해하기 쉬운데, 생성자는 단순히 인스턴스변수들의 초기화에 사용되는 조금 특별한 메서드일 뿐이다. 생성자가 갖는 몇 가지 특징만 제외하면 메서드와 다르지 않다.

#### Card클래스의 인스턴스를 생성하는 예

```java
Card c = new Card();
```

> 1. 연산자 new에 의해서 메모리(heap)에 Card클래스의 인스턴스가 생성된다.
> 2. 생성자 Card()가 호출되어 수행된다.
> 3. 연산자 new의 결과로, 생성된 Card인스턴스의 주소가 반환되어 참조변수 c에 저장된다.

 지금까지 인스턴스를 생성하기위해 사용해왔던 `클래스이름()`이 바로 생성자였던 것이다. 인스턴스를 생성할 때는 반드시 클래스 내에 정의된 생성자 중의 하나를 선택하여 지 정해주어야한다.

### 5_2 기본 생성자(default constructor)[📑](#contents)<a id='5_2'></a>

 지금까지는 생성자를 모르고도 프로그래밍을 해 왔지만, 사실 모든 클래스에는 반드시 하나 이상의 생성자가 정의되어 있어야 한다.
 그러나 지금까지 클래스에 생성자를 정의하지 않고도 인스턴스를 생성할 수 있었던 이유는 컴파일러가 제공하는 ‘기본 생성자(default constructor)’ 덕분이었다.
 컴파일 할 때, 소스파일(*.java)의 클래스에 생성자가 하나도 정의되지 않은 경우 컴파일러는 자동적으로 아래와 같은 내용의 기본 생성자를 추가하여 컴파일 한다.

```java
//클래스이름() { }
Card() { }
```

 컴파일러가 자동적으로 추가해주는 기본 생성자는 이와 같이 매개변수도 없고 아무런 내용도 없는 아주 간단한 것이다.
 그동안 우리는 인스턴스를 생성할 때 컴파일러가 제공한 기본 생성자를 사용해왔던 것이다. 특별히 인스턴스 초기화 작업이 요구되어지지 않는다면 생성자를 정의하지 않고 컴 파일러가 제공하는 기본 생성자를 사용하는 것도 좋다.

> **| 참고 |** 클래스의 ‘접근 제어자(Access Modifier)’가 public인 경우에는 기본 생성자로 'public 클래스이름( ) { }’이 추가된다.

```java
class Datal { 
    int value;
}
class Data2 { 
    int value;
    Data2(int x) { // 매개변수가있는생성자. 
        value = x;
    }
}
class ConstructorTest {
    public static void main(String[] args) {
        Datal d1 = new Data1();
        Data2 d2 = new Data2();				// compile error발생
    }
}
```

> 예제 6-23/ch6/ConstructorTest. java 

```java
ConstructorTest.java:15: cannot resolve symbol 
symbol : constructor Data2 ()
location: class Data2
    Data2 d2 = new Data2();          // compile error발생
^
1 error
```

> 실행결과

 이 예제를 컴파일 하면 위와 같은 에러메시지가 나타난다. 이것은 Data2에서 Data2()라는 생성자를 찾을 수 없다는 내용의 에러 메시지인데, Data2에 생성자 Data2()가 정의되어 있지 않기 때문에 에러가 발생한 것이다.

 Data1의 인스턴스를 생성하는 코드에는 에러가 없는데, Data2의 인스턴스를 생성하는 코드에서 에러가 발생하는 이유는 무엇일까?

그 이유는 Data1에는 정의되어 있는 생성자가 하나도 없으므로 컴파일러가 기본 생성자를 추가해주었지만,  Data2에는 이미 생성자 Data2(int x)가 정의되어 있으므로 기본 생성자가 추가되지 않았기 때문이다.

 컴파일러가 자동적으로 기본 생성자를 추가해주는 경우는 '클래스 내에 생성자가 하나도 없을 때'뿐이라는 것을 명심해야한다.

```java
Data1 d1 = new Data1();
Data2 d2 = new Data2(); // 에러
```

```java
Data1 d1 = new Data1();
Data2 d2 = new Data2(10); // OK
```

 이 예제에서 컴파일 에러가 발생하지 않도록 하기 위해서는 위의 오른쪽 코드와 같이 Data2의 인스턴스를 생성할 때 생성자 Data2(int x)를 사용하던가, 아니면 클래스 Data2에 생성자 Data2()를 추가로 정의해주면 된다.

``````
기본 생성자가 컴파일러에 의해서 추가되는 경우는 클래스에 정의된 생성자가 하나도 없을 때 뿐이다.
``````

### 5_3 매개변수가 있는 생성자[📑](#contents)<a id='5_3'></a>

 생성자도 메서드처럼 매개변수를 선언하여 호출 시 값을 넘겨받아서 인스턴스의 초기화 작업에 사용할 수 있다. 인스턴스마다 각기 다른 값으로 초기화되어야하는 경우가 많기 때문에 매개변수를 사용한 초기화는 매우 유용하다.

 아래의 코드는 자동차를 클래스로 정의한 것인데, 단순히 color, gearType, door 세 개의 인스턴스 변수와 두 개의 생성자만을 가지고 있다.

```java
class Car {
    String color;		// 색상
    String gearType;	// 변속기종류 - auto (자동) , manual (수동)
    int door;			// 문의 개수
    Car() {} // 생성자
    Car (String c, String g, int d) { // 생성자 
        color = c;
        gearType = g;
        door = d;
    }
}
```

 Car인스턴스를 생성할 때, 생성자 Car()를 사용한다면, 인스턴스를 생성한 다음에 인스턴스변수들을 따로 초기화해주어야 하지만, 매개변수가 있는 생성자 Car(String color, String gearType, int door)를 사용한다면 인스턴스를 생성하는 동시에 원하는 값으로 초기화를 할 수 있게 된다.

 인스턴스를 생성한 다음에 인스턴스변수의 값을 변경하는 것보다 매개변수를 갖는 생성자를 사용하는 것이 코드를 보다 간결하고 직관적으로 만든다.

```java
Car c = new Car ();
c.color = "white";
c.gearType = "auto";
c.door = 4;
```

```java
Car c = new Car("white","auto",4);
```

 위의 양쪽 코드 모두 같은 내용이지만, 오른쪽의 코드가 더 간결하고 직관적이다. 이처럼 클래스를 작성할 때 다양한 생성자를 제공함으로써 인스턴스 생성 후에 별도로 초기화를 하지 않아도 되도록 하는 것이 바람직하다.

```java
class Car {
    String color; 		// 색상
    String gearType;	// 변속기 종류 - auto (자동) , manual (수동)
    int door;			// 문의개수
    Car() {}
    Car(String c, String g, int d) {
        color = c;
        gearType = g;
        door = d;
    }
}
class CarTest { 
    public static void main(String[] args) {
        Car c1 = new Car (); 
        c1.color = "white"; 
        c1.gearType = "auto"; 
        c1.door = 4;
        Car c2 = new Car("white", "auto", 4);
        System.out.println("c1의 color=" + c1.color + ", gearType=" + c1.gearType+ ", door="+c1.door);
        System.out.println("c2의 color=" + c2.color + ", gearType="+ c2.gearType+ ", door="+c2.door);
    }
}           
```

> 예제 6-24/ch6/CarTest. java

```java
c1의 color=white, gearType=auto, door=4
c2의 color=white, gearType=auto, door=4
```

> 실행결과

### 5_4 생성자에서 다른 생성자 호출하기 - this(), this[📑](#contents)<a id='5_4'></a>

 같은 클래스의 멤버들 간에 서로 호출할 수 있는 것처럼 생성자 간에도 서로 호출이 가능하다. 단, 다음의 두 조건을 만족시켜야 한다.

```
- 생성자의 이름으로 클래스이름 대신 this를 사용한다.
- 한 생성자에서 다른 생성자를 호출할 때는 반드시 첫 줄에서만 호출이 가능하다
```

다음의 코드는 생성자를 작성할 때 지켜야하는 두 조건을 모두 만족시키지 못했기 때문에 에러가 발생한다.

```java
Car(String color) {
    door = 5;				// 첫 번째 줄
    Car (color, "auto", 4);	// 에러1. 생성자의두 번째 줄에서 다른 생성자 호출
} 							// 에러2. this (color, "auto", 4);로 해야함
```

 생성자 내에서 다른 생성자를 호출할 때는 클래스이름인 'Car'대신 'this'를 사용해야하는 데 그러지 않아서 에러이고, 또 다른 에러는 생성자 호출이 첫 번째 줄이 아닌 두 번째 줄 이기 때문에 에러이다.

 생성자에서 다른 생성자를 첫 줄에서만 호출이 가능하도록 한 이유는 생성자 내에서 초기화 작업도중에 다른 생성자를 호출하게 되면, 호출된 다른 생성자 내에서도 멤버변수들 의 값을 초기화를 할 것이므로 다른 생성자를 호출하기 이전의 초기화 작업이 무의미해질 수 있기 때문이다. 이에 대해서는 7장에서 좀 더 자세히 배우게 된다.

```java
class Car {
    String color;		// 색상
    String gearType;	// 변속기 종류 - auto (자동) , manual (수동)
    int door;			// 문의 개수
    Car() {
        this("white","auto", 4); //Car(String color, String gearType, int door)를 호출
    }
    Car(String color) {
        this(color, "auto", 4);
    }
	Car(String color, String gearType, int door) { 
    	this. color = color;
    	this.gearType = gearType;
    	this.door = door;
    }
    
}
class CarTest2 {
    public static void main(String[] args) {
        Car c1 = new Car ();
        Car c2 = new Car("blue");
        System.out.printin("c1의 color=" + c1.color + ", gearType="+ c1.gearType+ ", door="+c1.door);
        System.out.printin("c2의 color=" + c2.color + ", gearType="+ c2.gearType+ ", door="+c2.door);
```

> 예제 6-25/ch6/CarTest2.java

```java
c1의 color=white, gearType=auto, door=4 c2의 color=bluez gearType=autoz door=4
```

> 실행결과

 생성자 Car()에서 또 다른 생성자 Car(String color, String gearType, int door)를 호줄 하였다. 이처럼 생성자간의 호출에는 생성자의 이름 대신 this를 사용해야만 하므로 ‘Car’ 대신 ‘this’를 사용했다. 그리고 생성자 Car()의 첫째 줄에서 호출하였다는 점을 눈여겨보기 바란다.

```java
Car() {
    color = "white";
    gearType = "auto";
    door = 4;
}
```

```java
Car () {
    this("white","auto", 4);
}
```

 위 코드는 양쪽 모두 같은 일을 하지만 오른쪽의 코드는 생성자 Car(String color, String gearType, int door)를 활용해서 더 간략히 한 것이다. Car c1 = new Car()；와 같이 생성자Car()를 사용해서 Car인스턴스를 생성한 경우에, 인스턴스변수 color는 “white”, gearType은 “auto”, door는 4로 초기화 되도록 하였다.

 이것은 마치 실생활에서 자동차(Car인스턴스)를 생산할 때, 아무런 옵션도 주지 않으면, 기본적으로 흰색(white)에 자동변속기어(auto) 그리고 문의 개수가 4개인 자동차가 생산 되도록 하는 것에 비유할 수 있다.

 같은 클래스 내의 생성자들은 일반적으로 서로 관계가 깊은 경우가 많아서 이처럼 서로 호출하도록 하여 유기적으로 연결해주면 더 좋은 코드를 얻을 수 있다. 그리고 수정이 필요한 경우에도 보다 적은 코드만을 변경하면 되므로 유지보수가 쉬워진다.

```java
Car(String c, String g, int d) { 
    color = c;
    gearType = g;
    door = d;
}
```

```java
Car(String color, String gearType, int door) {
    this.color = color;
    this.gearType = gearType;
    this.door = door;
}
```

 왼쪽 코드의 `color = c;`는 생성자의 매개변수로 선언된 지역변수 c의 값을 인스턴스변수 color에 저장한다. 이 때 변수 color와 c는 이름만으로도 서로 구별되므로 아무런 문제가 없다.

 하지만, 오른쪽 코드에서처럼 생성자의 매개변수로 선언된 변수의 이름이 color로 인스 턴스변수 color와 같을 경우에는 이름만으로는 두 변수가 서로 구별이 안 된다. 이런 경우 에는 인스턴스변수 앞에 `this`를 사용하면 된다.

 이렇게 하면 this.color는 인스턴스변수이고, color는 생성자의 매개변수로 정의된 지역변수로 서로 구별이 가능하다. 만일 오른쪽코드에서 `this.color = color`대신 `color = color`와 같이하면 둘 다 지역 변수로 간주된다.

 이처럼 생성자의 매개변수로 인스턴스변수들의 초기값을 제공받는 경우가 많기 때문에 매개변수와 인스턴스변수의 이름이 일치하는 경우가 자주 있다. 이 때는 왼쪽코드와 같이 매개변수이름을 다르게 하는 것 보다 `this`를 사용해서 구별되도록 하는 것이 의미가 더 명확하고 이해하기 쉽다.

 `this`는 참조변수로 인스턴스 자신을 가리킨다. 참조변수를 통해 인스턴스의 멤버에 접근할 수 있는 것처럼, `this`로 인스턴스변수에 접근할 수 있는 것이다. 하지만, `this`를 사용할 수 있는 것은 인스턴스멤버 뿐이다. static메서드(클래스 메서드) 에서는 인스턴스 멤버들을 사용할 수 없는 것처럼, `this` 역시 사용할 수 없다. 왜냐하면, static메서드는 인스턴스를 생성하지 않고도 호출될 수 있으므로 static메서드가 호출된 시점에 인스턴스가 존재하지 않을 수도 있기 때문이다.

 사실 생성자를 포함한 모든 인스턴스메서드에는 자신이 관련된 인스턴스를 가리키는 참조변수 ‘this’가 지역 변수로 숨겨진 채로 존재한다.

 일반적으로 인스턴스메서드는 특정 인스턴스와 관련된 작업을 하기 때문에 자신과 관련 된 인스턴스의 정보가 필요하지반, static메서드는 인스턴스와 관련 없는 작업을 하므로 인스턴스에 대한 정보가 필요 없기 때문이다. 인스턴스메서드와 static메서드의 차이를 다시 한 번 되새겨 보자.

```java
this 인스턴스 자신을 가리키는 참조변수, 인스턴스의 주소가 저장되어 있다.
	 모든 인스턴스메서드에 지역변수로 숨겨진 채로 존재한다.
this(), this(매개변수) 생성자, 같은 클래스의 다른 생성자를 호출할 때 사용한다.
```

> **I 참고 I** `this`와 `this()`는 비슷하게 생겼을 뿐 완전히 다른 것이다. `this`는 ‘참조 변수’이고, `this()`는 ‘생성자’이다.

### 5_5 생성자를 이용한 인스턴스의 복사[📑](#contents)<a id='5_5'></a>

 현재 사용하고 있는 인스턴스와 같은 상태를 갖는 인스턴스를 하나 더 만들고자 할 때 생성자를 이용할 수 있다. 두 인스턴스가 같은 상태를 갖는다는 것은 두 인스턴스의 모든 인스턴스 변수(상태)가 동일한 값을 갖고 있다는 것을 뜻한다.

 하나의 클래스로부터 생성된 모든 인스턴스의 메서드와 클래스변수는 서로 동일하기 때문에 인스턴스간의 차이는, 인스턴스마다 각기 다른 값을 가질 수 있는 인스턴스변수 뿐이다.

``` java
Car(Car c) {
    color = c.color;
    gearType = c.gearType;
    door = c.door; 
}
```

 위의 코드는 Car클래스의 참조변수를 매개변수로 선언한 생성자이다. 매개변수로 넘겨진 참조변수가 가리키는 Car인스턴스의 인스턴스변수인 color, gearType, door의 값을 인 스턴스 자신으로 복사하는 것이다.

 어떤 인스턴스의 상태를 전혀 알지 못해도 똑같은 상태의 인스턴스를 추가로 생성할 수 있다. Java API의 많은 클래스들이 인스턴스의 복사를 위한 생성자를 정의해놓고 있으니 참고하기 바란다.

> **I 참고 I** Object클래스에 정의된 clone메서드를 이용하면 간단히 인스턴스를 복사할 수 있다. p.456

```java
class Car {
    String color; // 색상
    String gearType; // 변속기 종류 - auto (자동) , manual (수동)
    int door; // 문의 개수
    Car() { this("white", "auto", 4);
          }
    Car (Car c) { // 인스턴스의 복사를 위한 생성자.
        color = c.color;
        gearType = c.gearType;
        door = c.door;
    }
    Car(String color, String gearType, int door) {
        this. color = color;
        this.gearType = gearType;
        this.door = door;
    }
}
class CarTest3 {
    public static void main(String[] args) {
        Car c1 = new Car ();
        Car c2 = new Car (c1); // c1의 복사본 c2를 생성한다.
        System.out.printin("c1의 color=" + c1.color + ", gearType="
                           + c1.gearType+ ", door="+c1.door);
        System.out.printin("c2의 color=” + c2.color + ", gearType="
                           + c2.gearType+ ", door="+c2.door);
        c1.door=100; // c1의인스턴스변수 door의값을변경한다.
        System.out.printin("c1.door=100; 수행 후");
        System.out.printin("c1의 color=" + c1.color + ", gearType="
                           + c1.gearType+ ", door="+c1.door);
        System.out.printin("c2의 color=" + c2.color + "f gearType="
                                              + c2.gearType+ ", door="+c2.door);
    } 
}
```

> **예제 6-26**/ch6/CarTest3. java

```java
c1의 color=white, gearType=auto, door=4
c2의 color=white, gearType=auto, door=4
c1.door=100; 수행 후
c1의 color=white, gearType=auto, door=100
c2의 color=whitez gearType=auto, door=4
```

> 실행결과

 인스턴스 c2는 c1을 복사하여 생성된 것이므로 서로 같은 상태를 갖지만, 서로 독립적으로 메모리공간에 존재하는 별도의 인스턴스이므로 이의 값들이 변경되어도 c2는 영향을 받지 않는다.

 생성자 `Car(Car c)`는 아래와 같이 다른 생성자인 `Car(String color, String gearType, int door)`를 호출하는 것이 바람직하다. 무작정 새로 코드를 작성하는 것보다 기존의 코드를 활용할 수 없는지 고민해야한다.

```java
Car(Car c) {
    color = c.color;
    gearType = c.gearType;
    door = c.door;
}
```

```java
Car(Car c) {
// Car(String color,String gearType,int door)
    this(c.color, c.gearType, c.door);
}
```

 지금까지 생성자에 대해서 모르고도 자바프로그래밍이 가능했던 것을 생각한다면, 생성자는 그리 중요하지 않은 것으로 생각될지도 모른다. 하지만, 지금까지 본 것처럼 생성자를 잘 활용하면 보다 간결하고 직관적인, 객체지향적인 코드를 작성할 수 있을 것이다.

```💡
인스턴스를 생성할 때는 다음의 2가지 사항을 결정해야한다.
	1. 클래스 一 어떤 클래스의 인스턴스를 생성할 것인가?
	2. 생성자 - 선택한 클래스의 어떤 생성자로 인스턴스를 생성할 것인가?
```
