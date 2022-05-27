

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

### java.lang 패키지

| 클래스                              | 용도                                              |
| ----------------------------------- | ------------------------------------------------- |
| Object                              | 자바 클래스의 최상의 클래스                       |
| System                              | 입출력, JVM 종료, 가비지 수집기                   |
| Class                               | 클래스를 메모리로 로딩                            |
| Math                                | 수학 함수                                         |
| Wraper(Byte, Integer, Boolean...)   | 기본 타입을 객체, 문자열을 기본 타입, 입력값 검사 |
| String, StringBuffer, StringBuilder |                                                   |

---

### java.util 패키지

| 클래스           | 용도                                |
| ---------------- | ----------------------------------- |
| Arrays           | 배열을 조작(비교, 복사, 정렬, 찾기) |
| Calender         | 운영체제의 날짜와 시간              |
| Date             | 날짜와 시간 정보를 저장             |
| Objects          | 객체 비교, null 여부 조사           |
| String Tokenizer | 특정 문자로 구분된 문자열 추출      |
| Random           | 난수                                |

---

### Object  클래스

#### equals()

```java
class Member{
    private String id;
    public Member(String id) {
        this.id = id;
    }
    @Override
    public boolean equals(Object obj) {
        if(obj instanceof Member){
            Member m = (Member) obj;
            return id.equals(m.id);
        }
        return false;
    }
    
    @Override
    public int hashCode() {
        return id.hashCode();
    }
}
public class MemberEx {
    public static void main(String[] args) {
        Member m1 = new Member("A");
        Member m2 = new Member("A");
        Member m3 = new Member("B");

        System.out.println(m1.equals(m2));
        System.out.println(m1.equals(m3));
    }
}
```

---

#### hashCode()

> 객체를 식별할 하나의 정수 값

```java
package ch11.sec01;

import java.util.HashMap;
import java.util.HashSet;

class Key {
    public int num;

    public Key(int num) {
        this.num = num;
    }

    @Override
    public boolean equals(Object obj) {
        if (obj instanceof Key) {
            Key key = (Key) obj;
            return num == key.num;
        }
        return false;
    }

    @Override
    public int hashCode() {
        return num;
    }
}

public class KeyEx {
    public static void main(String[] args) {
        HashMap<Key, String> hashMap = new HashMap<Key, String>();

        hashMap.put(new Key(1),"홍길동");

        String value = hashMap.get(new Key(1));
        System.out.println(value);
    }
}

```

---

#### toString()

```java
bject obj = new Object();
Date date = new Date();
String str = new String("홍길동");

System.out.println(obj.toString());	//java.lang.Object@34ce8af7
System.out.println(date.toString());	//Thu May 26 16:10:04 KST 2022
System.out.println(date.toGMTString());	//26 May 2022 07:10:04 GMT
System.out.println(date.toLocaleString());	//2022. 5. 26. 오후 4:10:04
System.out.println(str.toString());	//홍길동
```

---

#### clone()

> 얕은 복제 : 필드가 참조 타입일 경우 번지가 복사된다.
>
> 깊은 복제 : 필드가 참조 타입 이여도 별도의 객체를 생성하여 값을 복제한다.

```java
package ch11.sec02;

import java.util.Arrays;

class Car{
    public String name;

    public Car(String name) {
        this.name = name;
    }

    @Override
    public String toString() {
        return "Car{" +
                "name='" + name + '\'' +
                '}';
    }
}

class Member implements Cloneable{	//implements Cloneable 반드시 필요!
    public String name;
    public int age;
    public int[] scores;
    public Car car;

    public Member(String name, int age, int[] scores, Car car) {
        this.name = name;
        this.age = age;
        this.scores = scores;
        this.car = car;
    }

    public void setMember(String name, int age, int[] scores, Car car) {
        this.name = name;
        this.age = age;
        this.scores = scores;
        this.car = car;
    }

    @Override
    protected Object clone() throws CloneNotSupportedException {
        Member m = (Member) super.clone();
        //m.name = new String(this.name); 안해도 됨!
        m.scores = Arrays.copyOf(this.scores,this.scores.length);   //객체 번지수 변경
        m.car = new Car(this.car.name);    //객체 번지수 변경
        return m;
    }

    @Override
    public String toString() {
        return "Member{" +
                "name='" + name + '\'' +
                ", age=" + age +
                ", scores=" + Arrays.toString(scores) +
                ", car=" + car +
                '}';
    }

    public Member getMember(){
        Member m = null;
        try {
            m = (Member) clone();
        } catch (CloneNotSupportedException e) {
            e.printStackTrace();
        }
        return m;
    }
}
public class CloneEx {
    public static void main(String[] args) {
        Member oldM = new Member("a", 1, new int[]{80, 80}, new Car("소나타"));
        Member newM = oldM.getMember();

        oldM.scores[0] = 1;
        oldM.car.name = "bb";

        System.out.println(oldM.toString());
        System.out.println(newM.toString());
    }
}
```

---

#### finalize()

> **종료자 메소드는 사용을 권장하지 않는다. **
>
> 자바 가상머신(JVM : java virtual machine)이 더 이상 사용하지 않는 자원에 대한 정리 작업을 진행하기 위해 호출되는 종료자 메소드이다.
>
> 가비지 컬렉션의 실행 시점이 불분명하기 때문에 finalize 메소드를 사용하더라도 실행을 보장하지 않는다. 

```java
class Counter{
    private int no;
    public Counter(int no) {
        this.no = no;
    }
    
    // 사용을 권장하지 않는다! 보통 JVM이 자동으로 해준다.
    @Override
    protected void finalize() throws Throwable {
        System.out.println(no+"번 객체의 finalize()가 실행됨");
    }
}
public class FinalizeEx {
    public static void main(String[] args) {
        Counter counter = null;
        for (int i = 0; i < 50; i++) {
            counter = new Counter(i);
            counter = null;
            System.gc();	
        }
    }
}
```

---

### System 클래스

#### exit()

> 강제로 JVM 종료

```java
System.exit(0);
```

#### gc()

> 가비지 수집기(쓰레기 수집기)
>
> **사용을 권장하지 않음**

```java
System.gc();
```

#### 현재 시간 읽기

```java
System.out.println(System.currentTimeMills());
System.out.println(System.nanoTime());
```

#### 시스템 프로퍼티

| 키(key)        | 설명               | 값(Value)                     |
| -------------- | ------------------ | ----------------------------- |
| java.version   | 자바 버전          | 1.8.0_20                      |
| java.home      | JRE 경로           | <jdk 설치경로>\jre            |
| os.name        | OS이름             | Windows 11                    |
| file.separator | \                  | \                             |
| user.name      | 사용자 이름        | 사용자계정                    |
| user.home      | 사용자 홈 디렉토리 | C:\Users\사용자계정           |
| user.dir       | 디렉토리 경로      | C;\Users\사용자계정\Workspace |

#### 환경변수 읽기

````java
System.out.println(System.getenv("JAVA_HOME"));
````

---

### Class 클래스



---

### String 클래스

#### String

```java
// 바이트 변환
byte[] bytes = {72, 101, 108, 108, 111, 32, 74, 97, 118, 97};
byte[] inputBytes = new byte[100];

int readByteNo = System.in.read(inputBytes);

String str = new String(bytes);
byte[] bytes1 = str.getBytes();	//String -> byte
byte[] bytes2 = str.getBytes(StandardCharsets.UTF_8);
String str2 = new String(bytes2, StandardCharsets.UTF_8);	//byte -> String

System.out.println(new String(bytes));	// Hello Java
System.out.println(new String(inputBytes, 0, readByteNo - 1));	// '\n' 넘김
System.out.println(Arrays.toString(bytes1));
System.out.println(Arrays.toString(bytes2));

// int 변환
String str3 = "123";
int intValue = Integer.parseInt(str3);
String str4 = Integer.toString(intValue);
```

```java

String str = "Hello World!";
char[] chars = str.toCharArray(); // String -> char
char c1 = str.charAt(3);
String str2 = String.valueOf(chars);	// char -> String
String str3 = new String(chars);	// char -> String

System.out.println(Arrays.toString(chars));
System.out.println(c1); // l
System.out.println(str2);
System.out.println(str3);
```

```java
String str1 = "홍길동";
String str2 = new String("홍길동");
System.out.println(str1.equals(str2));
```

```java
String email = "abc@gmail.com";
System.out.println(email.indexOf("gmail"));
System.out.println(email.contains("@"));
email = email.replace("gmail","naver");
System.out.println(email);
System.out.println(email.substring(email.indexOf("@") + 1,email.length()));
System.out.println(email.substring(0,email.indexOf("@")).toUpperCase());
email = "   " + email + "    ";
email = email.trim();
System.out.println(email);
System.out.println(String.valueOf(10.5));
String[] value = email.split("@");
System.out.println(Arrays.toString(value));

```

#### StringTokenizer

```java
String name = "홍길동/이수홍/박연수";
StringTokenizer st = new StringTokenizer(name,"/");
int a = st.countTokens();
for (int i = 0; i < a; i++) {
    System.out.println(st.nextToken());
}

st = new StringTokenizer(name,"/");
while (st.hasMoreTokens()){
    System.out.println(st.nextToken());
}
```



#### StringBuffer

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

#### StringBuilder

> StringBuffer는 **멀티 스레드 환경**에서 안전하다는 장점이 있고, 
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

---

#### 정규 표현식

| 기호  | 설명                                                         |
| ----- | ------------------------------------------------------------ |
| []    | 1개의 문자 / [abc] a,b,c중 1개 / [&#94;abc] a,b,c이외의 1개 / [a-zA-Z] a~z, A~Z중에 1개 |
| \d    | 1개의 숫자, [0-9]와 동일                                     |
| \s    | 공백                                                         |
| \w    | 1개의 알파벳 또는 한 개의 숫자, [a-zA-Z_0-9]와 동일          |
| ?     | 없음 또는 1개                                                |
| *     | 없음 또는 1개 이상                                           |
| +     | 1개 이상                                                     |
| {n}   | 정확히 n개                                                   |
| {n,}  | 최소한 n개                                                   |
| {n,m} | n개 ~ m개까지                                                |
| ()    | 그룹핑                                                       |

```java
String phone = "010-2846-9777";
System.out.println(Pattern.matches("(02|010)-\\d{3,4}-\\d{4}",phone));

String email = "abc@gamil.com";
System.out.println(Pattern.matches("\\w+@\\w+\\.\\w+(\\.\\w+)?",email));
```

---

### Arrays 클래스

#### 배열 복사

```java
int[] a = {1, 2, 3, 4};
int[] b = Arrays.copyOf(a, a.length - 1);
int[] c = Arrays.copyOfRange(a, 1, a.length);
int[] d = new int[a.length];
System.arraycopy(a, 0, d, 0, a.length);

a[0] = 9;

System.out.println(Arrays.toString(a));
System.out.println(Arrays.toString(b));
System.out.println(Arrays.toString(c));
System.out.println(Arrays.toString(d));

//얕은 복사
int[][] e = {{1, 2}, {3, 4}};
int[][] f = Arrays.copyOf(e, e.length);

System.out.println(e.equals(f));    // 배열 번지 : false
System.out.println(Arrays.equals(e, f));    // 1차 배열 번지 비교 : true
System.out.println(Arrays.deepEquals(e, f));    //중첩 배열 항목값 비교 : true

e[0][0] = 9;

System.out.println(Arrays.toString(e[0]));
System.out.println(Arrays.toString(f[0]));

// 깊은 복사
int[][] f2 = Arrays.copyOf(e,e.length);
f2[0] = Arrays.copyOf(e[0],e[0].length);
f2[1] = Arrays.copyOf(e[1],e[1].length);

System.out.println(e.equals(f2));    // 배열 번지 : false
System.out.println(Arrays.equals(e, f2));    // 1차 배열 번지 비교 : false
System.out.println(Arrays.deepEquals(e, f2));    //중첩 배열 항목값 비교 : true
```

---

#### 배열 정렬

```java
int[] a = {3, 5, 7, 1};
Arrays.sort(a);	// 오른차순

Integer[] b = Arrays.stream(a).boxed().toArray(Integer[]::new);
Arrays.sort(b, Collections.reverseOrder());	// 내림차순

System.out.println(Arrays.toString(a));
System.out.println(Arrays.toString(b));
```

---

#### 배열 검색

```java
class Member implements Comparable<Member> {
    private String name;

    public Member(String name) {
        this.name = name;
    }

    @Override
    public int compareTo(Member o) {
        return name.compareTo(o.name);
    }
}

public class ArrayEx {
    public static void main(String[] args) {

        int[] a = {3, 5, 7, 1};
        System.out.println(Arrays.binarySearch(a, 7));

        String[] b = {"aaa", "bbb", "ccc"};
        System.out.println(Arrays.binarySearch(b, "bbb"));

        Member m1 = new Member("ddd");
        Member m2 = new Member("eee");
        Member m3 = new Member("fff");

        Member[] members = {m1, m2, m3};
        System.out.println(Arrays.binarySearch(members, m2));

    }
}
```

---

### Wrapper(포장) 클래스

```java
Integer integer1 = Integer.valueOf("1000");
Integer integer2 = 100;   // 자동 박싱

int a = integer1;   // 자동 언박싱
integer1 = 100;

int b = Integer.parseInt("1000");	// String -> int
String str = Integer.toString(b);	// int -> String

System.out.println(integer1.equals(integer2));
```

### Math 클래스

| 메소드   | 설명                 |
| -------- | -------------------- |
| abs      | 절대값               |
| ceil     | 올림값               |
| floor    | 내림값               |
| max      | 최대값               |
| min      | 최소값               |
| random() | 랜덤값               |
| rint     | 가까운 정수의 실수값 |
| round    | 반올림값             |

`0.0 <= Math.random() < 1.0`

### Random 클래스

| Math.random()                    | Random                                                |
| -------------------------------- | ----------------------------------------------------- |
| 0 <= n < 1 double 난수           | boolean, int, long, float, double 난수를 얻을 수 있음 |
| 종자값(seed)이 현재시간으로 고정 | 종자값(seed)을 설정할 수 있음 / 설정하지 않으면 랜덤  |

```java
int a = (int) (Math.random() * 6) + 1;
int b = new Random().nextInt(6) + 1;
```

---

### Format 클래스

| 기호   | 의미                              | 패턴 예 | 1234567.89</br>변환 결과 |
| ------ | --------------------------------- | ------- | --------- |
| 0      | 10진수(빈자리는 0으로 채움)       | 0 </br>0.0</br>0000000000.00000 | 1234568</br>1234567.9</br>0001234567.89000 |
| #      | 10진수                            | &#35;</br>&#35;.&#35;</br>&#35;&#35;&#35;&#35;&#35;&#35;&#35;&#35;&#35;&#35;.&#35;&#35;&#35;&#35;&#35; | 1234568</br>1234567.9</br>1234567.89 |
| .      | 소수점                            | &#35;.0 | 1234567.9 |
| -      | 음수 기호                         | &#43;&#35;.0</br>&#45;&#35;.0 | &#43;1234567.9</br>&#45;1234567.9 |
| ,      | 단위 구분                         | &#35;,&#35;&#35;&#35;.0 | 1,234,567.9 |
| E      | 지수 문자                         | 0.0E0 | 1.2E6 |
| ;      | 양수와 음수 모두 기술할 때 구분자 | &#43;&#35;,&#35;&#35;&#35; ; &#45;&#35;,&#35;&#35;&#35; | &#43;1234567.9(양수일 때)</br>&#45;1234567.9(음수일 때) |
| %      | 100을 곱한 후 % 문자를 붙임       | &#35;,&#35; % | 123456789% |
| \u00A4 | 통화기호                          | \u00A4 &#35;,&#35;&#35;&#35; | &#8361; 1,234,568 |

```java
double num = 1234567.89;

System.out.println(new DecimalFormat("0").format(num)); // 1234568
System.out.println(new DecimalFormat("0.0").format(num)); // 1234567.9
System.out.println(new DecimalFormat("0000000000.00000").format(num)); // 0001234567.89000
System.out.println(new DecimalFormat("#").format(num)); // 1234568
System.out.println(new DecimalFormat("#.#").format(num)); // 1234567.9
System.out.println(new DecimalFormat("##########.#####").format(num)); // 1234567.89
System.out.println(new DecimalFormat("#.0").format(num)); // 1234567.9
System.out.println(new DecimalFormat("+#.0").format(num)); // +1234567.9
System.out.println(new DecimalFormat("-#.0").format(num)); // -1234567.9
System.out.println(new DecimalFormat("#,###.0").format(num)); // 1,234,567.9
System.out.println(new DecimalFormat("0.0E0").format(num)); //1.2E6
System.out.println(new DecimalFormat("+#,### ; -#,###").format(num)); // +1,234,568 
System.out.println(new DecimalFormat("#.# %").format(num)); // 123456789 %
System.out.println(new DecimalFormat("\u00A4 #,###").format(num)); // ₩ 1,234,568
```



---

### 날짜 형식 클래스

#### SimpleDateFormat

| 패턴 문자 | 의미                     | 패턴 문자 | 의미                 |
| --------- | ------------------------ | --------- | -------------------- |
| y         | 년                       | H         | 시(0~23)             |
| M         | 월                       | h         | 시(1~12)             |
| d         | 일                       | K         | 시(0~11)             |
| D         | 월 구분이 없는 일(1~365) | k         | 시(1~24)             |
| E         | 요일                     | m         | 분                   |
| a         | 오전/오후                | s         | 초                   |
| w         | 년의 몇 번째 주          | S         | 밀리세컨드(1/1000초) |
| W         | 월의 몇 번째 주          |           |                      |

```java
System.out.println(new Date());	// Fri May 27 16:10:00 KST 2022
System.out.println(new SimpleDateFormat("yyyy년 MM월 dd일 E요일 w주 HH:mm:ss").format(new Date()));	// 2022년 05월 27일 금요일 22주 16:19:47
```

#### Calendar

| 상수                     | 사용방법               | 설명                           |
| ------------------------ | ---------------------- | ------------------------------ |
| static int YEAR          | Calendar.YEAR          | 현재 년도                      |
| static int MONTH         | Calendar.MONTH         | 현재 월 (1월: 0)               |
| static int DATE          | Calendar.DATE          | 현재 월의 날짜                 |
| static int WEEK_OF_YEAR  | Calendar.WEEK_OF_YEAR  | 현재 년도의 몇째 주            |
| static int WEEK_OF_MONTH | Calendar.WEEK_OF_MONTH | 현재 월의 몇째 주              |
| static int DAY_OF_YEAR   | Calendar.DAY_OF_YEAR   | 현재 년도의 날짜               |
| static int DAY_OF_MONTH  | Calendar.DAY_OF_MONTH  | 현재 월의 날짜                 |
| static int DAY_OF_WEEK   | Calendar.DAY_OF_WEEK   | 현재 요일(일요일:1 ,토요일: 7) |
| static int HOUR          | Calendar.HOUR          | 현재 시간 (12시간제)           |
| static int HOUR_OF_DAY   | Calendar.HOUR_OF_DAY   | 현재 시간 (24시간제)           |
| static int MINUTE        | Calendar.MINUTE        | 현재 분                        |
| static int SECOND        | Calendar.SECOND        | 현재 초                        |

```java
Calendar today = Calendar.getInstance();
int year = today.get(Calendar.YEAR);
int month = today.get(Calendar.MONTH);
int date = today.get(Calendar.DATE);

int woy = today.get(Calendar.WEEK_OF_YEAR);	// 현재 년도의 몇째 주
int wom = today.get(Calendar.WEEK_OF_MONTH);	// 현재 월의 몇째 주

int doy = today.get(Calendar.DAY_OF_YEAR);	//0~365
int dom = today.get(Calendar.DAY_OF_MONTH);	//0~52
int dow = today.get(Calendar.DAY_OF_WEEK);	//요일

int hour12 = today.get(Calendar.HOUR);	//12시제
int hour24 = today.get(Calendar.HOUR_OF_DAY);	//24시제
int minute = today.get(Calendar.MINUTE);
int second = today.get(Calendar.SECOND);

int milliSecond = today.get(Calendar.MILLISECOND);
int timeZone = today.get(Calendar.ZONE_OFFSET);	// 표준시
int lastDate = today.getActualMaximum(Calendar.DATE);

System.out.println("오늘은 " + year + "년 " + month + 1 + "월" + date + "일");
System.out.println("오늘은 올해의 " + woy + "째주, 이번달의 " + wom + "째주. " + date + "일");
System.out.println("오늘은 이번 해의 " + doy + "일이자, 이번 달의 " + dom + "일. 요일은 " + dow + "일 (1:일요일)");
System.out.println("현재 시각은 " + hour12 + ":" + minute + ":" + second + ", 24시간으로 표현하면 " + hour24 + ":" + minute + ":" + second);
System.out.println("오늘은 " + year + "년 " + month + 1 + "월" + date + "일");
System.out.println("이 달의 마지막 날: " + lastDate);
```

#### LocalDate

```java
// 달력 출력 프로그램
Scanner sc = new Scanner(System.in);
int year, month;

System.out.println("[달력 출력 프로그램]");
System.out.print("달력의 년도를 입력해 주세요. (yyyy) : ");
year = sc.nextInt();
System.out.print("달력의 월을 입력해 주세요. (mm) : ");
month = sc.nextInt();

LocalDate ld = LocalDate.of(year, month, 1);

System.out.printf("\n\n\n[%d년 %02d월]\n", year, month);
System.out.println("일\t월\t화\t수\t목\t금\t토");

int cnt = 0;
for (int i = 0; i < ld.getDayOfWeek().getValue() % 7; i++) {
    System.out.print("\t");
    cnt++;
}
for (int i = 1; i <= ld.lengthOfMonth(); i++) {
    if (cnt > 6) {
        System.out.println();
        cnt = 0;
    }
    System.out.printf("%02d\t", i);
    cnt++;
}

sc.close();
```

---

### 문자열 형식 클래스(MessageFormat)

```java
tring id = "java", name = "홍길동", tel = "010-1234-5678";
System.out.println(MessageFormat.format("회원 ID : {0} \n회원 이름 : {1}\n회원 전화 : {2}", id, name, tel));

Object[] arguments = {"'python'", "'이몽룡'", "'010-1111-2222'"};
System.out.println(MessageFormat.format("insert into member values({0},{1},{2})", arguments));
```



----

## 12. 입출력

---

## 13. 예외 처리

### NullPointerException

````java
String data = null;
try{
    System.out.println(data.toString());
}catch (NullPointerException e){
    System.out.println("NullPointerException");
}finally {	// 생략 가능
    System.out.println("finally");
}
````

### ArrayIndexOutOfBoundsException

```java
int[] value = {1, 2};
try {
    for (int i = 0; i <= value.length; i++) {
        System.out.println(value[i]);
    }
}catch (ArrayIndexOutOfBoundsException e){
    System.out.println("ArrayIndexOutOfBoundsException");
}
```

### NumberFormatException

```java
String a = "100";
String b = "a100";  // 숫자로 변환 불가!
try {
    int result = Integer.parseInt(a) + Integer.parseInt(b);
}catch (java.lang.NumberFormatException e){
    System.out.println("NumberFormatException");
}
```

### ClassCastException

```java
class Animal {}
class Dog extends Animal {}
class Cat extends Animal {}

public class ClassCastExceptionEx {
    public static void main(String[] args) {
        Animal animal = new Animal();
        Dog dog = new Dog();
        Cat cat = new Cat();

        changeDog(dog);
        changeDog(cat); //에러! Cat은 Dog로 형변환 불가!
    }
    public static void changeDog(Animal animal) {
        if(animal instanceof Dog){
            Dog dog = (Dog) animal;
        }
        try {
            Dog dog = (Dog) animal;
        }catch (ClassCastException e){
            System.out.println("ClassCastException");
        }
    }
}
```

### ClassNotFoundException

````java
try {
    Class clazz = Class.forName("java.lang.String2");
}catch (ClassNotFoundException e){
    System.out.println("ClassNotFoundException");
}
````



### 예외 떠넘기기

```java
public static void method1(){
    try {
        method2();
    }catch (NumberFormatException e){
        System.out.println("NumberFormatException");
    }
}

public static void method2() throws NumberFormatException{
    System.out.println(Integer.parseInt("a123"));
}
```

### 예외 정보얻기

```java
public class BalanceInsufficientException extends Exception {

    public BalanceInsufficientException() {
    }

    public BalanceInsufficientException(String message) {
        super(message);
    }
}

public class Account {
    private int balance;

    public Account() {}

    public int getBalance() {
        return balance;
    }

    public void deposit(int money) {
        balance += money;
    }

    public void withdraw(int money) throws BalanceInsufficientException {
        if (balance < money) {
            throw new RuntimeException("잔고부족 : " + (money - balance) + " 모자람");
        }
        balance -= money;
    }
}

public class AccountMain {
    public static void main(String[] args) {
        Account account = new Account();
        account.deposit(10000);
        System.out.println(account.getBalance());
        try {
            account.withdraw(30000);
        }catch (BalanceInsufficientException e){
            System.out.println(e.getMessage());
            e.printStackTrace();
        }
    }
}
```



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
