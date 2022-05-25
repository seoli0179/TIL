# Java 기본

## 01. 변수와 자료형

> ⭐ **변수란**
>
> 하나의 값을 저장할 수 있는 메모리 공간

> ⭐ **리터럴(literal)이란**
>
> 소스 코드 내에서 직접 입력된 값, 상수와 구분한다.

```java
int a = 30; // '30'은 정수 리터럴이다.
```

> ⭐ **상수란**
>
> 값을 한번 저장하면 변경할 수 없는 변수

```java
final int a = 30;	// a는 상수이다.
```



![image](https://user-images.githubusercontent.com/105831105/169700247-32941c51-09e2-4985-bae2-ff901ad92d52.png)

### 기본 타입

> **⚠ String과 배열은 참조형 타입이다.**

- Max값

```java
// int MAX 값
int intMaxValue = Integer.MAX_VALUE;
```

- 연산식 자동 타입 변환

```java
int result1 = 정수리터럴(long 제와) + 정수리터럴(long 제와)	// int로 자동 변환 후 계산

long result2 = 정수리터럴 + 정수리터럴; // long로 자동 변환 후 계산

double result3 = 실수리터럴 + 정수리터럴; // double로 자동 변환 후 계산
result3 = 1.0 * 정수리터럴 + 정수리터럴; // double로 자동 변환 후 계산
result3 = (double)정수리터럴 + 정수리터럴; // 강제 형변환 후 계산
```

- 2진수, 8진수, 16진수

```java
System.out.println("0b" + Integer.toBinaryString(0b1111));	// 2진수
System.out.println("0" + Integer.toOctalString(014));		// 8진수
System.out.println("0x" + Integer.toHexString(0x1a));		// 16진수
```
### 참조 타입

![image](https://user-images.githubusercontent.com/105831105/169726238-cb70c585-dffa-4405-bf91-b6a8764819fe.png)

#### 배열

- 일반 초기화

```java
int[] intArr1 = {1, 3, 5, 7, 9};
System.out.println(intArr1.length);

int[] intArr2 = new int[]{2, 4, 6};    // 초기화 필요!

int[][] intArr3 = {{1}, {2, 3}, {4, 5, 6}};

int[][] intArr4 = new int[3][];
intArr4[0] = new int[]{1};
intArr4[1] = new int[]{2, 3};
intArr4[2] = new int[]{4, 5, 6};
```

- 배열 복사

```java
int[] oldArr = {1, 2, 3};
int[] newArr = new int[5];

System.arraycopy(oldArr, 0, newArr, 0, oldArr.length);    // 단순한 배열 복사
int[] newArr2 = Arrays.copyOf(oldArr, oldArr.length);	// Arrays 클래스

int[] newArr3 = oldArr.clone();
```

#### String  타입

```java
String[] strArr = new String[3];

strArr[0] = "java";
strArr[1] = "java";
strArr[2] = new String("java");

System.out.println(strArr[0] == strArr[1]);			// true
System.out.println(strArr[1] == strArr[2]);			// false (문자열 == 는 객체 번지 비교)
System.out.println(strArr[1].equals(strArr[2]));	// true (문자열 비교는 equals을 사용)
```

#### 열거 타입

> **상수집합 / 열거란**
>
> Enum은 서로 관련이 있는 여러 개의 상수 집합을 정의할 때 사용하는 자료형
>
> 매직넘버(1과 같은 숫자 상수값)를 사용할 때보다 코드가 명확해 진다.
>
> - 프로그래밍에서 상수로 선언하지 않은 숫자를 매직넘버라고 한다.
>

> **열거타입을 사용하는 이유?**
>
> 잘못된 값을 사용함으로 인해 발생할수 있는 위험성이 사라진다.

```java
public enum CoffeeType {
        AMERICANO,
        ICE_AMERICANO,
        CAFE_LATTE
    };

public class Sample {

    public static void main(String[] args) {
        System.out.println(CoffeeType.AMERICANO);  // AMERICANO 출력
        System.out.println(CoffeeType.ICE_AMERICANO);  // ICE_AMERICANO 출력
        System.out.println(CoffeeType.CAFE_LATTE);  // CAFE_LATTE 출력
        
        for(CoffeeType type: CoffeeType.values()) {
            System.out.println(type);  // 순서대로 AMERICANO, ICE_AMERICANO, CAFE_LATTE 출력
        }
    }
}
```

```java
public enum Week {
    MONDAY,
    TUESDAY,
    WEDNESDAY,
    THURSDAY,
    FRIDAY,
    SATURDAY,
    SUNDAY
}

public class Main {
    public static void main(String[] args) {
        Week day1 = Week.MONDAY;
        Week day2 = Week.WEDNESDAY;
        Week day3 = Week.valueOf("THURSDAY");
        Week[] days = Week.values();

        if (day1 == Week.MONDAY) {
            System.out.println("일주일의 시작");    // 출력 안됨
        }

        System.out.println(day2.ordinal());    // 2
        System.out.println(day1.compareTo(day2));   // -2
        System.out.println(day2.compareTo(day1));   // 2
        System.out.println(day3.name());    //THURSDAY

        for (Week day : days){
            System.out.println(day);	// 전체 출력
        }
    }
}
```
---

## 02.제어문

### 2. switch 문

```java
int input = 2;
switch (input) {
    case 1:
        System.out.println(1);
        break;
    case 2:
        System.out.println(2);
        break;
    default:
        System.out.println("default");
}
```

### 3. while 문

```java
Outer:
while (true) {
    break Outer;
}
```

### 4. for 문

#### 1. 기본 for문

```java
for (int i = 0; i < 5; i++) {
    System.out.println(i);
}
```

#### 2. 향상된 for문

```java
int[] intArr = {1, 2, 3};
for (int i : intArr) {
    System.out.println(i);
}
```




---

## 04. 객체 지향

### 클래스

```java
public class Worker {
    private String JoominNo, name;

    public Worker(String joominNo, String name) {
        JoominNo = joominNo;
        this.name = name;
    }

    @Override
    public String toString() {
        return "주민번호 : " + JoominNo + '\n' +
                "성명 : " + name + '\n';
    }
}

public class PartTime extends Worker {

    private int hours, uniPrice;

    public PartTime(String joominNo, String name, int hours, int uniPrice) {
        super(joominNo, name);
        this.hours = hours;
        this.uniPrice = uniPrice;
    }

    public int calculatePay(){
        return uniPrice * hours;
    }

    @Override
    public String toString() {
        return super.toString() +
                "시급 : " + uniPrice + " 원\n" +
                "근무시간 : " + hours + " 시간\n" +
                "총지불액 : " + calculatePay() + " 원\n";
    }
}

public class WorkerPartTimeMain {
    public static void main(String[] args) {
        PartTime pt = new PartTime("990101-1034567", "홍길동", 60, 6000);
        System.out.println(pt); // == System.out.println(pt.toString());
    }
}
```

---

### 접근 제한자

![image](https://user-images.githubusercontent.com/105831105/169733857-5519ee84-8c8f-4ebf-9172-a50501495267.png)

![image](https://user-images.githubusercontent.com/105831105/169733923-14cad5f6-eff2-42bc-995f-9010eeaffbd4.png)

---

### 상속

> **상속이란?**
>
> 자식 클래스가 부모 클래스의 기능을 그대로 물려받을 수 있는 기능
>
> private 필드와 메소드 제외, 다른 패키지면 default 필드와 메소드도 제외
>
> 자바는 다중 상속을 지원하지 않는다.

```java
class Animal {
    String name;

    void setName(String name) {
        this.name = name;
    }
}

class Dog extends Animal {
}

public class Sample {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.setName("poppy");
        System.out.println(dog.name);  // poppy 출력
    }
}
```

- 기능 확장
  - 메소드 추가 / 필드 추가

```java
class Animal {
    String name;

    void setName(String name) {
        this.name = name;
    }
}

class Dog extends Animal {
    String old;	// 필드 추가
    
    void sleep() {
        System.out.println(this.name+" zzz");	// 메소드 추가
    }
}

public class Sample {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.setName("poppy");
        System.out.println(dog.name);  // poppy 출력
        dog.sleep();  // poppy zzz 출력
    }
}
```

- 생성자
  - 생성자 호출은 **맨 첫줄**에 와야함


![image](https://user-images.githubusercontent.com/105831105/169724098-23ca7603-7cf8-4cb3-8fee-aa485e330c53.png)

- IS-A Vs HAS-A 관계

> "Dog `is a` Animal" 과 같이 말할 수 있는 관계를 **IS-A 관계**라고 한다. (상속)
>
> - **상속을 코드 재사용의 개념으로 이해하면 안된다.** 
>
> "Computer has a CPU" 와 같이 말할 수 있는 관계룰 **HAS-A 관계**라고 한다. (인터페이스)

```java
Animal dog = new Dog();  // Dog is a Animal
Dog dog = new Animal();  // 컴파일 오류: 부모 클래스로 만든 객체는 자식 클래스의 자료형으로 사용할 수 없다.
```

![IS-A](https://user-images.githubusercontent.com/105831105/169725208-aa3b9194-44f5-4c44-8980-dd7f1764354a.png)

![image](https://user-images.githubusercontent.com/105831105/169725236-4107230b-81ce-4cc6-bde3-97bd4991048d.png)

- 메소드 오버라이딩 (Method overriding)과 오버로딩

```java
class Animal {
    String name;

    void setName(String name) {
        this.name = name;
    }
}

class Dog extends Animal {
    @Override
    void sleep() {
        System.out.println(this.name + " zzz");
    }
}

class HouseDog extends Dog {
    // 메소드 오버라이딩
    @Override
    void sleep() {
        System.out.println(this.name + " zzz in house");
    }
    
    // 메소드 오버로딩(method overloading) : 동일한 이름 / 다른 입력
    void sleep(int hour) {
        System.out.println(this.name + " zzz in house for " + hour + " hours");
    }
}

public class Sample {
    public static void main(String[] args) {
        HouseDog houseDog = new HouseDog();
        houseDog.setName("happy");
        houseDog.sleep();  // happy zzz in house 출력
    }
}
```

- 자동/강제 형변환

```java
Parent p = new Child(); // 자동
Child c = (Child)p;		// 강제
//Child c1 = (Child)new Parent(); //에러!
```



---

### 인터페이스

> **인터페이스란**
>
> 동일한 목적 하에 동일한 기능을 수행하게끔 강제하는 것

> **상속과 인터페이스**
>
> **상속**은 자식 클래스가 부모 클래스의 메소드를 오버라이딩하지 않고 사용할 수 있다.
>
> **인터페이스**는 인터페이스의 메소드를 반드시 구현해야 하는 **강제성**을 갖는다

> ⚠ **클래스와 인터페이스는 .java 파일을 따로 만드는 것이 일반적이다.**

![image](https://user-images.githubusercontent.com/105831105/170155503-87d02392-9df5-49d9-a726-8ca14502ffe9.png)

![image](https://user-images.githubusercontent.com/105831105/170155560-b3286df3-f226-4888-a5c9-7443e0ae7950.png)

![image](https://user-images.githubusercontent.com/105831105/170155597-7d0471c0-5510-4fbe-92fa-dffd2301d715.png)

```java
interface Tire {
    
    int finalValue = 0;	// public, static, final 생략 가능
    void roll();	// public, static, final 생략 가능, 필수 Overridding
    
    //default 메소드 : 실행블럭 가질 수 있음, Override 필수 아님
    default void run(){	
        System.out.println("Hello World!");
    }
    
}

class ATire implements Tire {
    // 반드시 Override 해야함!
    @Override
    public void roll() {
        System.out.println("ATire.roll()");
    }
}

public class main  {
    public static void main(String[] args) {
        ATire b = new ATire();
        b.roll();
        b.run();
        System.out.println(Tire.finalValue);
    }
}
```

---

### 다형성(Polymorphism)

> **다형성 이란?**
>
> 하나의 객체가 여러개의 자료형 타입을 가질 수 있는 것

```java
interface Tire {
    public void roll();
}

class ATire implements Tire {
    @Override
    public void roll() {
        System.out.println("ATire.roll()");
    }
}

class BTire implements Tire {
    @Override
    public void roll() {
        System.out.println("BTire.roll()");
    }
}

class Car {
    Tire[] tires = {
            new ATire(),
            new ATire(),
            new BTire(),
            new BTire()
    };

    public void run() {
        for (Tire i : tires) {
            i.roll();
        }
    }
}

public class test {

    public static void main(String[] args) {

        Car car = new Car();
        car.run();

    }
}
```

```java
// 자동 형변환
public interface Vehicle {
    void run();
}
public class Bus implements Vehicle{
    @Override
    public void run() {
        System.out.println("버스가 달립니다.");
    }
}
public class Taxi implements Vehicle{
    @Override
    public void run() {
        System.out.println("택시가 달립니다.");
    }
}
public class Driver {
    void drive(Vehicle vehicle){
        vehicle.run();
    }
}
public class DriverEx {
    public static void main(String[] args) {
        Driver driver = new Driver();
        Bus bus = new Bus();
        Taxi taxi = new Taxi();

        driver.drive(bus);	// 자동 타입 변환
        driver.drive(taxi);	// 자동 타입 변환

    }
}

```

```java
// 강제 형변환
public interface Vehicle {
    void run();
}
public class Driver {
    public void drive(Vehicle vehicle){
        if(vehicle instanceof Bus){
            Bus bus = (Bus)vehicle;
            bus.check();
        }
    }
}
public class Bus implements Vehicle{
    @Override
    public void run() {
        System.out.println("버스가 달립니다.");
    }
    public void check() {
        
    }
}
public class DriverEx {
    public static void main(String[] args) {
        Vehicle vehicle = new Bus();	// 자동 타입 변환
        Driver driver = new Driver();
        
        vehicle.run();
//        vehicle.check(); 에러! Vehicle 인터페이스에는 check() 없음

        Bus bus = (Bus)vehicle;	// 강제 타입 변환
        
        bus.run();
        bus.check();
        
        driver(vehicle);	// 객체 타입 확인 후 강제변환
        
        Vehicle v = new Vehicle() {	// 익명 구형 객체 (일회성)
            @Override
            public void run() {
                
            }
        };

    }
}

```



---

### 추상 클래스

> **추상클래스(Abstract Class)란?**
>
> 인터페이스의 역할도 하면서 클래스의 기능도 가지고 있는 자바의 돌연변이 같은 클래스
>
> 일반 클래스와는 달리 단독으로 객체를 생성할 수 없고, 반드시 추상 클래스를 상속한 실제 클래스를 통해서만 객체를 생성할 수 있다.
>
> **필드와 메서드 이름을 통일하여 유지보수성을 높이고 통일성을 유지**할 수 있다.

> **인터페이스와 추상 클래스의 차이**
>
> 인터페이스와는 달리 일반 클래스처럼 객체변수, 생성자, private 메서드 등을 가질 수 있다.

![image](https://user-images.githubusercontent.com/105831105/169930041-2bf69970-0d8b-41bc-9682-e18d0294c7a1.png)

```java
public abstract class Bird{
    public abstract void sing();

    public void fly(){
        System.out.println("날다.");
    }
}

public class Duck extends Bird{
    @Override
    public void sing() {
        System.out.println("꽥꽥!!");
    }
}

public class DuckExam { 
    public static void main(String[] args) {
        Duck duck = new Duck();
        duck.sing();
        duck.fly();

        //Bird b = new Bird(); 객체 생성 불가!
    }   
}
```



---

### 내부 클래스(중첩 클래스)

- Class in Class
- Method in Class
- 매개변수 in Class 

```java
class OutClass {
    class InClass { //내부 인스턴스 멤버 클래스
        InClass() {}
        int filed1;
        //        static int filed2; 정적 필드 X
        void method1() {
            class LocalClass{ // 로컬 클래스
                int filed3;
//                static int filed4; 정적 필드 X
                void methode3(){}
//                static void method4(){} 정적 메소드 X
            }
            LocalClass localClass = new LocalClass();
            localClass.filed3 = 1;
            localClass.methode3();
        }
//        static void method2(){} 정적 메소드 X
    }

    static class InClassStatic { // 내부 정적 멤버 클래스
        InClassStatic() {}
        int filed1;
        static int filed2;
        void method1() {}
        static void method2() {}
    }

    interface Ininterface { // 중첩 인터페이스
        public void onClick();
    }
    
}

public class Main {
    public static void main(String[] args) {
        OutClass outClass = new OutClass();
        OutClass.InClass inClass = outClass.new InClass();
//        OutClass.InClass = new OutClass.InClass(); 에러!
        OutClass.InClassStatic inClassStatic = new OutClass.InClassStatic();
        OutClass.Ininterface ininterface = new OutClass.Ininterface() {
            @Override
            public void onClick() {}
        };

        inClass.filed1 = 1;
        inClass.method1();

        inClassStatic.filed1 = 2;
        OutClass.InClassStatic.filed2 = 3;
        inClass.method1();
        OutClass.InClassStatic.method2();
    }
}

```

```java
class OutClass {

    int field1;
    void method1(){}
    static int field2;
    static void method2(){}
    class InClass{
        void method(){
            field1 = 1;
            method1();
            
            field2 = 1;
            method2();
        }
    }
    static class InStaticClass{
        void method(){
//            field1 = 1;
//            method1();
            field2 = 1;
            method2();
        }
    }

}
```

```java
class OutClass {
    void method(final int arg1, int arg2){
        final int var1 = 1;
        int var2 = 2;
        class LocalClass{ 
// 로컬 클래스에서 "사용된" 매개변수와 로컬변수는 final의 특성을 갖는다.
// 매개변수나 로컬변수가 수정되어 값이 변경되면, 
// 로컬클래스에 복사해 둔 값과 달라지는 문제를 해결하기 위해서이다.
            int method(){
//                var2 = 1;	
//                arg2 = 1;	
                return arg1 + arg2 + var1 + var2;
            }
        }
//        var2 = 3;
//        arg2 = 2;
    }
}
```

```java
class OutClass {
    int a = 1;
    void method(){
        System.out.println("OutClass");
    };
    class InClass{
        int a = 0;
        void method(){
            System.out.println("InClass");
        };
        void print(){
            int a = 1;
            
            a = 2;				 	//InClass.print() a / print안에 생성 안했다면 Inclass.a
            this.a = 2; 			//Inclass.a
            OutClass.this.a = 2;   	 //OutClass.a

            method();				//InClass.method()
            this.method();			//InClass.method()
            OutClass.this.method();	 //OutClass.method()
        }
    }
    
    class A {}
    static class B {}
    
    A a = new A();
    B b = new B();
//    static A c = new A(); 에러!
    static B d = new B();
    
    void method1(){
        A a = new A();
        B b = new B();
    }
    static void method2(){
//        A a = new A(); 에러!
        B b = new B();
    }
    
}

public class Test {
    public static void main(String[] args) {
        OutClass outClass = new OutClass();
        OutClass.InClass inClass = outClass.new InClass();
        inClass.print();
    }
}

```

```java

// 익명 자식 객체 만들기
interface Person { //class도 가능
    public void wake();
}
class A {
    Person filed = new Person() {
        @Override
        public void wake() {
            System.out.println("6시에 일어납니다.");
            work();
        }
        public void work() {
            System.out.println("출근합니다.");
        }
    };
    void method1() {
        Person localVar = new Person() {
            @Override
            public void wake() {
                System.out.println("7시에 일어납니다.");
                walk();
            }
            public void walk() {
                System.out.println("산책합니다.");
            }
        };
        localVar.wake();
    }
    void method2(Person person) {
        person.wake();
    }
}
public class Test {
    public static void main(String[] args) {
        A a = new A();
        a.filed.wake();
        a.method1();
        a.method2(new Person() {
            @Override
            public void wake() {
                System.out.println("8시에 일어납니다.");
                study();
            }
            public void study() {
                System.out.println("공부합니다.");
            }
        });
    }
}

```





---

## 05. 기본 API

### String

- String

> String 자료형은 한번 값이 생성되면 그 값을 변경할 수가 없다.
>
> 이렇게 값을 변경할 수 없는 것을 immutable 하다고 한다.

```java
String result = "";
result += "hello";	// +연산 할 때 마다 객체 생성
result += " ";
result += "jump to java";
System.out.println(result);
```

- StringBuffer

>StringBuffer는 값을 변경할 수 있다(mutable 하다).
>
>StringBuffer 자료형은 String 자료형보다 무거운 편에 속한다. 

```java
StringBuffer sb = new StringBuffer();  // 최초 한 번만 객체 생성
sb.append("hello");
sb.append(" ");
sb.append("jump to java");
sb.insert(0, "hello ");
System.out.println(sb.toString());	// hello jump to java
System.out.println(sb.substring(0, 4));	// hell
```

- StringBuilder

> StringBuffer는 멀티 스레드 환경에서 안전하다는 장점이 있고, 
>
> StringBuilder는 StringBuffer보다 성능이 우수한 장점이 있다. 
>
> 따라서 동기화를 고려할 필요가 없는 상황에서는 StringBuffer 보다는 StringBuilder를 사용하는 것이 유리하다.

```java
StringBuilder sb = new StringBuilder();
sb.append("hello");
sb.append(" ");
sb.append("jump to java");
String result = sb.toString();
System.out.println(result);
```

----

## 12. 입출력

---

## 13. 예외 처리

---

## 14. 컬렉션 프레임워크

---

## 15. 람다식

---

## 16. 스트림

### 1. HashSet

- 중복값을 허용하지 않는다.

### 2. TreeSet

- 순서를 보장한다.
