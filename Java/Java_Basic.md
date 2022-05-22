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

---

## 02.제어문

### 1. if 문



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

## 03. 참조 타입

### 배열

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

### String  타입

```java
String[] strArr = new String[3];

strArr[0] = "java";
strArr[1] = "java";
strArr[2] = new String("java");

System.out.println(strArr[0] == strArr[1]);			// true
System.out.println(strArr[1] == strArr[2]);			// false (문자열 == 는 객체 번지 비교)
System.out.println(strArr[1].equals(strArr[2]));	// true (문자열 비교는 equals을 사용)
```

### 열거 타입

> **상수집합 / 열거란**
>
> Enum은 서로 관련이 있는 여러 개의 상수 집합을 정의할 때 사용하는 자료형
>
> 매직넘버(1과 같은 숫자 상수값)를 사용할 때보다 코드가 명확해 진다.
>
> - 프로그래밍에서 상수로 선언하지 않은 숫자를 매직넘버라고 한다.
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

## 05. 기본 API

### String 



### StringBuffer

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

## 

---

## 06. 클래스

---

## 07. 상속

---

## 08. 다형성

---

## 09. 추상 클래스

---

## 10. 인터페이스

---

## 11. 내부 클래스

---

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
