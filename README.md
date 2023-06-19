# 객체지향 프로그래밍 1

## 1. 객체지향언어
* 객체지향언어의 특징
    * 코드의 재사용성이 높다.
    * 코드의 관리가 용이하다.
    * 신뢰성이 높은 프로그래밍을 가능하게 한다.

## 2. 클래스와 객체

### 2.1 클래스와 객체의 정의와 용도
* 클래스: 객체를 정의해 놓은 것
* 객체: 실제로 존재하는 것. 사물 또는 개념
* 비유하면 TV 설계도가 클래스이고, TV 설계도를 바탕으로 만들어진 TV가 객체이다.

### 2.2 객체와 인스턴스
* 인스턴스: 클래스로부터 만들어진 객체
* 객체는 모든 인스턴스를 대표하는 포괄적인 의미를 갖고 인스턴스는 어떤 클래스로부터 만들어진 것인지를 강조하는 보다 구체적인 의미를 갖는다.
* 책상은 인스턴스다 -> 책상은 객체다, 책상은 책상 클래스의 객체이다 -> 책상은 책상 클래스의 인스턴스이다.

### 2.3 속성과 기능
* 객체는 속성과 기능의 집합이다.
* 그 속성과 기능을 객체의 멤버라고 한다.
* 속성: 멤버변수, 특성, 필드, 상태
* 기능: 메서드, 함수, 행위

### 2.4 인스턴스의 생성과 사용
```java
public static void main(String[] args) {
        Tv t;
        t = new Tv();
        t.channel = 7;
        t.channelDown();
        System.out.println("현재 채널은 " + t.channel + " 입니다.");
    }
```
* Tv t;
    * 참조변수 t를 선언
    * 메모리에 참조변수 t를 위한 공간이 마련된다.
    * 아직 인스턴스가 생성되지 않았으므로 참조변수로 아무것도 할 수 없다.
* t = new Tv();
    * new에 의해 인스턴스가 메모리의 빈 공간에 생성
    * 주소 0x100에 생성되었다고 가정
    * 멤버변수는 각 자료형에 해당하는 기본값으로 초기화
    * 대입 연산자에 의해 생성된 객체의 주소값이 참조변수 t에 저장된다.
    * 이제는 참조변수 t를 통해 Tv 인스턴스에 접근할 수 있다.
    * 인스턴스를 다루기 위해선 참조변수가 반드시 필요하다.
* t.channel = 7;
    * 참조변수 t에 저장된 주소에 있는 인스턴스의 멤버변수 channel에 7을 저장한다.

> 인스턴스는 참조변수를 통해서만 다룰 수 있으며, 참조변수의 타입은 인스턴스의 타입과 일치해야 한다.

```java
public static void main(String[] args) {
        Tv t1 = new Tv();
        Tv t2 = new Tv();
        System.out.println("t1의 channel 값은 " + t1.channel + "입니다.");
        System.out.println("t2의 channel 값은 " + t2.channel + "입니다.");
        t2 = t1;
        t1.channel = 7;
        System.out.println("t1의 channel 값을 7로 변경하였습니다.");
        System.out.println("t1의 channel 값은 " + t1.channel + "입니다.");
        System.out.println("t2의 channel 값은 " + t2.channel + "입니다.");
        
    }
```
* t2 = t1;
    * t1은 참조변수이므로, 인스턴스의 주소를 저장하고 있다.
    * t2에 t1의 값을 저장하면, t2도 t1과 같은 인스턴스를 참조하게 된다.
    * t2가 원래 참조하고 있던 인스턴스는 더 이상 사용할 수 없다.

> 둘 이상의 참조변수가 하나의 인스턴스를 가리키는 것은 가능하지만 하나의 참조변수로 여러 개의 인스턴스를 가리키는 것은 불가능하다.

### 2.5 객체 배열
* 객체 배열에는 객체가 저장되는 것은 아니고, 객체의 주소가 저장된다.
```java
Tv[] tvArr = new Tv[3];
```
* 길이가 3인 Tv객체 배열이 생성된다.
* 각 요소는 참조변수의 기본값인 null로 초기화된다.
* 객체를 다루기 위한 참조변수들이 만들어진 것일뿐, 객체가 저장되지 않았다.

### 2.6 클래스의 또 다른 정의
* 프로그래밍적인 관점에서 클래스의 정의와 의미
1. 클래스: 데이터와 함수의 결합
    * 서로 관계가 깊은 변수와 함수들을 다룬다.
    * 자바에서 문자열을 클래스로 정의한 이유는 문자열과 문자열을 다루는 함수들을 함께 묶어서 다루기 위해서이다.
2. 클래스: 사용자정의 타입
    * 사용자정의 타입: 프로그래머가 서로 관계가 있는 변수들을 묶어서 하나의 타입으로 새로 추가하는 것
    * 자바 같은 객체지향언어에서는 클래스가 곧 사용자 정의 타입이다. 

## 3. 변수와 메서드

### 3.1 선언 위치에 따른 변수의 종류
* 인스턴스 변수
    * 클래스 영역에 선언되며, 클래스의 인스턴스를 생성할 때 만들어진다.
    * 인스턴스 변수의 값을 읽어 오거나 저장하기 위해서는 먼저 인스턴스를 생성해야 한다.
    * 인스턴스는 독립적인 저장공간을 가지므로 서로 다른 값을 가질 수 있다.
* 클래스 변수
    * 인스턴스 변수 앞에 static을 붙이면 된다.
    * 클래스 변수는 모든 인스턴스가 공통된 저장공간을 공유한다.
    * 인스턴스를 생성하지 않고 바로 사용할 수 있다.
    * 클래스가 메모리에 로딩될 때 생성되어 프로그램이 종료될 때 까지 유지된다.

### 3.2 클래스 변수와 인스턴스 변수
* 클래스 변수를 사용할 때는 '클래스이름.클래스변수'의 형태로 하는 것이 좋다.
> 인스턴스 변수는 인스턴스가 생성될 때 마다 생성되므로 인스턴스마다 다른 겂을 유지할 수 있지만, 클래스 변수는 모든 인스턴스가 하나의 저장공간을 공유하므로 항상 공통된 값을 갖는다.

### 3.3 JVM 메모리 구조
* 응용프로그램이 실행되면 JVM은 시스템으로부터 메모리를 할당받는다.
* 이 메모리를 용도에 따라 여러 영역으로 나눌 수 있다. 그 중 메서드 영역, 힙 영역, 호출스택 영역이 있다.
* 메서드 영역
    * 프로그램 실행 중 어떤 클래스가 사용되면, JVM은 해당 클래스의 클래스 파일(*.class)을 읽어서 분석하여 클래스에 대한 정보를 이곳에 저장한다.
    * 클래스 변수도 이 영역에 함께 생성된다.
* 힙 영역
    * 인스턴스가 생성되는 공간이다.
    * 인스턴스변수들이 생성되는 공간이다.
* 호출스택 영역
    * 메서드가 호출되면, 호출스택에 호출된 메서드를 위한 메모리가 할당된다.
    * 이 메모리는 메서드가 작업을 수행하는 동안 지역변수들과 연산의 중간결과 등을 저장하는데 사용된다.
    * 메서드가 호출되면 수행에 필요한 만큼의 메모리를 스택에 할당받는다.
    * 메서드가 수행을 마치고나면 사용했던 메모리를 반환하고 스택에서 제거된다.
    * 호출스택의 제일 위에 있는 메서드가 현재 실행 중인 메서드이다.
    * 아래에 있는 메서드가 바로 위의 메서드를 호출한 메서드이다.

### 3.4 기본형 매개변수와 참조형 매개변수
* 기본형 매개변수: 변수의 값을 읽기만 할 수 있다.
* 참조형 매개변수: 변수의 값을 읽고 변경할 수 있다.

### 3.5 클래스 메서드(static 메서드)와 인스턴스 메서드
* 변수와 마찬가지로 클래스 메서드는 객체를 생성하지 않고도 호출할 수 있다.
1. 클래스를 설계할 때, 멤버 변수 중 모든 인스턴스에서 공통으로 사용하는 것에 static을 붙인다.
2. 클래스 변수는 인스턴스를 생성하지 않아도 사용할 수 있다.
3. 클래스 메서드는 인스턴스 변수를 사용할 수 없다.
    * 인스턴스 변수는 인스턴스가 반드시 존재해야만 사용할 수 있지만 클래스 메서드가 호출되었을 때 인스턴스가 존재하지 않을 수도 있다.
4. 메서드 내에서 인스턴스 변수를 사용하지 않는다면, static을 붙이는 것을 고려한다.
    * 메서드 호출 시간이 짧아지므로 효율이 높아진다.

## 4. 오버로딩

### 4.1 오버로딩이란?
* 한 클래스 내에 같은 이름의 메서드를 여러 개 정의하는 것을 메서드 오버로딩이라고 한다.

### 4.2 오버로딩의 조건
* 메서드 이름이 같아야 한다.
* 매개변수의 개수 또는 타입이 달라야 한다.
* 반환 타입은 오버로딩을 구현하는데 아무런 영향을 주지 못한다.
* 즉, 메서드를 호출하였을 때 어떤 메서드가 호출된 것인지 결정할 수 있어야 한다.

### 4.3 오버로딩의 장점
* 같은 기능을 하는 메서드들의 이름을 통일할 수 있다.

### 4.4 가변인자와 오버로딩
* 가변인자는 메서드의 매개변수를 동적으로 지정할 수 있다.
* '타입... 변수명' 형태로 선언한다.
* 가변인자 외에도 매개변수가 있으면 가변인자를 맨 마지막에 배치해야 한다.
```java
String concatenate(String... str) { ... }
System.out.println(concatenate());
System.out.println(concatenate("a"));
System.out.println(concatenate("a", "b"));
System.out.println(concatenate(new String[] {"a", "b"}));
```
* 가변인자는 내부적으로 배열을 이용하는 것이다.
* 가변인자가 선언된 메서드를 호출할 때마다 배열이 새로 생성된다.
* 가능하면 가변인자를 사용한 메서드는 오버로딩하지 않는 것이 좋다.

## 5. 생성자

### 5.1 생성자란?
* 인스턴스가 생성될 때마다 호출되는 '인스턴스 초기화 메서드'
* 생성자의 이름은 클래스의 이름과 같아야 한다.
* 생성자는 리턴 값이 없다.
* 연산자 new가 인스턴스를 생성하는 것이지 생성자가 인스턴스를 생성하는 것은 아니다.
```
Card c = new Card();
```
* 연산자 new에 의해서 heap에 card 클래스의 인스턴스가 생성된다.
* 생성자 Card()가 호출되어 수행된다.
* 연산자 new의 결과로, 생성된 Card 인스턴스의 주소가 반환되어 참조변수 c에 저장된다.
* 인스턴스를 생성하기 위해 사용해왔던 '클래스이름()'이 바로 생성자이다.

### 5.2 기본 생성자
* 모든 클래스에는 반드시 하난 이상의 생성자가 정의되어 있어야 한다.
* 클래스에 생성자가 하나도 없으면 컴파일러가 기본 생성자를 추가한다.

### 5.3 매개변수가 있는 생성자
* 매개변수가 있는 생성자를 통해 인스턴스 생성 전에 초기화 작업을 진행할 수 있다.

### 5.4 생성자에서 다른 생성자 호출하기 - this(), this
* 생성자의 이름으로 클래스이름 대신 this를 사용한다.
* 한 생성자에서 다른 생성자를 호출할 때는 반드시 첫 줄에서만 호출이 가능하다.
```java
Car(String color) {
    door = 5;
    Car(color, "auto", 4);
}
```
* Car 대신 this를 사용하지 않아서 에러 발생한다.
* 생성자 호출이 첫 번째 줄이 아닌 두 번째 줄이라서 에러 발생한다.
    * 생성자 내에서 초기화 작업 도중 다른 생성자를 호출하면
    * 호출된 다른 생성자 내에서도 멤버변수들의 값을 초괴화할 것이므로 다른 생성자를 호출하기 이전의 초기화 작업이 무의미해질 수 있기 때문이다.
```
Car(String color, String gearType, int door) {
    this.color = color;
    this.gearType = gearType;
    this.door = door;
}
```
* this는 참조변수로 인스턴스 자신을 가리킨다.
* 참조변수를 통해 인스턴스의 멤버에 접근할 수 있는 것처럼, this로 인스턴스변수에 접근할 수 있다.
* 하지만, this를 사용할 수 있는 것은 인스턴스 멤버뿐이다.
* static 메서드에서는 인스턴스 멤버들을 사용할 수 없으므로 this를 사용할 수 없다.
> 일반적으로 인스턴스메서드는 특정 인스턴스와 관련된 작업을 하기 때문에 자신과 관련된 인스턴스의 정보가 필요하지만, static 메서드는 인스턴스와 관련 없는 작업을 하기 때문에 인스턴스에 대한 정보가 필요 없다.

### 5.5 생성자를 이용한 인스턴스의 복사
```java
Car(Car c) {
    color = c.color;
    gearType = c.gearType;
    door = c.door;
}
```
* Car 클래스의 참조변수를 매개변수로 선언한 생성자이다.
* 매개변수로 넘겨진 참조변수가 가리키는 Car 인스턴스의 인스턴스 변수를 복사한다.

## 6. 변수의 초기화

### 6.1 변수의 초기화
* 멤버변수는 초기화하지 않아도 자동으로 변수의 자료형에 맞는 기본값으로 초기화가 이루어진다.
* 지역변수는 사용하기 전에 반드시 초기화해야 한다.
* 멤버변수의 초기화 방법
    * 명시적 초기화
    * 생성자
    * 초기화 블럭

### 6.2 명시적 초기화
* 변수의 선언과 동시에 초기화를 수행하는 것

### 6.3 초기화 블럭
* 복잡한 초기화에 사용된다.
* 단순히 클래스 내에 블럭{}을 만들고 그 안에 코드를 작성하기만 하면 된다.
* 클래스 초기화 블럭과 인스턴스 초기화 블럭으로 나뉘는데 클래스 초기화 블럭은 블럭 앞에 static만 붙여주면 된다.
* 클래스 초기화 블럭은 클래스가 메모리에 처음 로딩될 때 한 번만 수행된다.
* 인스턴스 초기화 블럭은 생성자와 같이 인스턴스를 생성할 때 마다 수행된다. 그리고 인스턴스 초기화 블럭이 생성자보다 먼저 수행된다.
* 인스턴스 변수의 초기화는 생성자를 이용하고, 인스턴스 초기화 블럭은 모든 생성자에서 공통으로 수행해야 하는 코드를 넣는데 사용한다.
> 코드의 중복을 제거하는 것은 코드의 신뢰성을 높여주고, 오류의 발생가능성을 줄여준다. 즉, 재사용성을 높이고 중복을 제거하는 것. 이것이 객체지향 프로그래밍이 추구하는 궁극적인 목표이다.

# 객체지향프로그래밍 2

## 1. 상속

### 1.1 상속의 정의와 장점
* 상속: 기존의 클래스를 재사용하여 새로운 클래스를 작성하는 것
* 코드의 재사용성을 높이고 코드의 중복을 제거하여 프로그램의 생산성과 유지보수에 크게 기여한다.
* 자손 클래스는 조상 클래스의 모든 멤버를 상속받는다. 
* 자손 클래스가 변경되는 것은 조상 클래스에 아무런 영향을 주지 못한다.
* 상속에 상속을 거듭할수록 상속받는 클래스의 멤버 개수는 점점 늘어나게 된다. 따라서 상속 받는다는 것은 조상 클래스를 확장(extend)한다는 의미로 해석할 수 있다.
* 생성자와 초기화 블럭은 상속되지 않는다.
* 자손 클래스의 인스턴스를 생성하면 조상 클래스의 멤버와 자손 클래스의 멤버가 합쳐진 하나의 인스턴스로 생성된다.

### 1.2 클래스간의 관계 - 포함관계
* 한 클래스의 멤버변수로 다른 클래스의 타입의 참조변수를 선언하는 것이다.
```java
class Circle {
    int x;
    int y;
    int r;
}
class Point {
    int x;
    int y;
}
```

```java
class Circle {
    Point c = new Point();
    int r;
}
```
* 이와 같이 하나의 거대한 클래스를 작성하는 것보다 단위별로 여러 개의 클래스를 작성한 다음, 포함관계로 재사용하면 보다 간결하고 손쉽게 클래스를 작성할 수 있다.

### 1.3 클래스간의 관계 결정하기
* 상속관계: ~은 ~이다(is-a)
* 포함관계: ~은 ~을 가지고 있다(has-a)

### 1.4 단일 상속
* C++와 다르게 자바는 단일 상속만을 허용한다.

### 1.5 Object 클래스 - 모든 클래스의 조상
* 모든 상속계층도의 최상위에는 Object 클래스가 위치한다.

## 2. 오버라이딩과

### 2.1 오버라이딩이란?
* 조상 클래스로부터 상속받은 메서드의 내용을 변경하는 것

### 2.2 오버라이딩의 조건
* 자손 클래스에서 오버라이딩하는 메서드는 조상 클래스의 메서드와
    * 이름이 같아야 한다.
    * 매개변수가 같아야 한다.
    * 반환타입이 같아야 한다.
* 접근 제어자는 조상 클래스의 메서드보다 좁은 범위로 변경할 수 없다.
    * public, protected, (default), private 순서로 범위가 좁아진다.
* 예외는 조상 클래스의 메서드보다 많이 선언할 수 없다.
* 인스턴스 메서드를 static으로 또는 그 반대로 변경할 수 없다.

### 2.3 오버로딩 vs 오버라이딩
* 오버로딩: 기존에 없는 새로운 메서드를 정의하는 것
* 오버라이딩: 상속받은 메서드의 내용을 변경하는 것

### 2.4 super
* 조상 클래스로부터 상속받은 멤버를 참조하는데 사용되는 참조변수이다.
* 멤버변수와 지역변수의 이름이 같을 때 this를 붙여서 구별했듯이
* 상속받은 멤버와 자신의 클래스에 정의된 멤버의 이름이 같을 때는 super를 붙여서 구별할 수 있다.
* 조상의 멤버와 자신의 멤버를 구별하는데 사용된다는 점을 제외하고는 this와 근본적으로 같다.
* 메서드 역시 super를 써서 호출할 수 있다. 특히 오버라이딩한 경우에 super를 사용한다.

### 2.5 super() - 조상 클래스의 생성자
* this()와 마찬가지로 super() 역시 생성자 호출이다.
* Object 클래스를 제외한 모든 클래스의 생성자 첫 줄에서 생성자 this() or super()를 호출해야 한다.
* 그렇지 않으면 컴파일러가 자동으로 super();를 생성자의 첫 줄에 삽입한다.

## 3. package와 import

### 3.1 패키지(package)
* 모든 클래스는 반드시 하나의 패키지에 속해야 한다.
* 패키지는 점을 구분자로 하여 계층구조를 구성할 수 있다.
* 패키지는 물리적으로 클래스 파일을 포함하는 하나의 디렉토리이다.

### 3.2 패키지의 선언
* 클래스나 인터페이스의 소스파일에 'package 패키지명;'을 첫 줄에 선언한다.
* 패키지명은 대소문자를 모두 허용하지만, 클래스명과 구별하기 위해서 소문자로 하는 것이 관례이다.

### 3.3 import문
* 다른 패키지의 클래스를 사용하려면 패키지명이 포함된 클래스 이름을 사용해야 한다.
* import문으로 사용하고자 하는 클래스의 패키지를 미리 명시해주면 클래스 이름만으로 참조할 수 있다.

### 3.4 import문의 선언
* import문은 package문 다음에 선언한다.

### 3.5 static import문
* static 멤버를 호출할 때 클래스 이름을 생략할 수 있다.
```java
import static java.lang.Integer.*;
import static java.lang.Math.random;
import static java.lang.System.out;
```
* 이와 같이 선언하였다면
* System.out.println(Math.random());을
* out.println(random());으로 사용할 수 있다.
