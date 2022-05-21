# 제로베이스 기본연습문제

---

## 정수 거꾸로 변환



---

## 별찍기 1

### 1. 입출력 예시

```java
[입력]
3
[출력]
***
***
***
```

### 2. 코드


```java
for (int i = 0; i < n; i++) {
    for (int j = 0; j < n; j++) {
        System.out.print("*");
    }
    System.out.println();
}
```

### 3. 풀이과정


|  행  |  i   |  *   | * 공식 |
| :--: | :--: | :--: | :----: |
|  0   |  0   |  3   | n - 1  |
|  1   |  1   |  3   |        |
|  2   |  2   |  3   |        |

## 별찍기 2

### 1. 입출력 예시

```java
[입력]
3
[출력]
*
**
***
```

### 2. 코드

```java
for (int i = 0; i < n; i++) {
    for (int j = 0; j < i + 1; j++) {
        System.out.print("*");
    }
            System.out.println();
}
```

### 3. 풀이과정


|  행  |  i   |  *   | * 공식 |
| :--: | :--: | :--: | :----: |
|  0   |  0   |  1   | i + 1  |
|  1   |  1   |  2   |        |
|  2   |  2   |  3   |        |

## 별찍기 3

### 1. 입출력 예시

```java
[입력]
3
[출력]
  *
 **
***
```

### 2. 코드

```java
// 첫번째 방법
for (int i = 0; i < n; i++) {
    for (int j = 0; j < n; j++) {
        if (j < n - i - 1) {
            System.out.print(" ");
        } else {
            System.out.print("*");
        }
    }
    System.out.println();
}   
// 두번째 방법
for (int i = 0; i < n; i++) {
    for (int j = n - 1; j >= 0; j--) {
        if (j > i)
            System.out.print(" ");
        else
            System.out.print("*");
    }
    System.out.println();
}
```

### 3. 풀이과정

|  행  |  i   | space | space 공식 |  *   | * 공식 |
| :--: | :--: | :---: | :--------: | :--: | :----: |
|  0   |  0   |   2   | n - i - 1  |  1   | i  + 1 |
|  1   |  1   |   1   |            |  2   |        |
|  2   |  2   |   0   |            |  3   |        |

## 별찍기 4

### 1. 입출력 예시

```java
[입력]
3
[출력]
  *
 ***
*****
```

### 2. 코드


```java
for (int i = 0; i < n; i++) {
    for (int j = 0; j < n - i - 1; j++) {
        System.out.print(" ");
    }
    for (int j = 0; j < i * 2 + 1; j++) {
        System.out.print("*");
    }
    System.out.println();
}
```

### 3. 풀이과정

|  행  |  i   | space | space 공식 |  *   |  * 공식   |
| :--: | :--: | :---: | :--------: | :--: | :-------: |
|  0   |  0   |   2   | n - i - 1  |  1   | i * 2 + 1 |
|  1   |  1   |   1   |            |  3   |           |
|  2   |  2   |   0   |            |  5   |           |

## 별찍기 5

### 1. 입출력 예시

```java
[입력]
5
[출력]
  *
 ***
*****
 ***
  *
```

### 2. 코드

```java
//상단부
for (int i = 0; i <= n / 2; i++) {
    for (int j = 0; j < n / 2 - i; j++) {
        System.out.print(" ");
    }
    for (int j = 0; j < i * 2 + 1; j++) {
        System.out.print("*");
    }
    System.out.println();
}
//하단부
for (int i = 0; i < n / 2; i++) {
    for (int j = 0; j < i + 1; j++) {
        System.out.print(" ");
    }
    for (int j = 0; j <n - (i * 2 + 2); j++) {
        System.out.print("*");
    }
    System.out.println();
}
```

### 3. 풀이과정

![KakaoTalk_20220519_221239298](https://user-images.githubusercontent.com/105831105/169312266-b44248da-98b2-4827-84a1-d26ce8027784.jpg)

### 4. 정답

```java
// 상단
for (int i = 0; i <= n / 2; i++) {
    for (int j = 0; j < n / 2 - i; j++) {
        System.out.print(" ");
    }

    for (int j = 0; j < i * 2 + 1; j++) {
        System.out.print("*");
    }
    System.out.println();
}
// 하단
for (int i = n / 2; i > 0; i--) {
    for (int j = 0; j < n / 2 + 1 - i; j++) {
        System.out.print(" ");
    }

    for (int j = 0; j < i * 2 -1; j++) {
        System.out.print("*");
    }
    System.out.println();
}
```



---

## 가장 많은 물 담기

### 1. 문제

n개의 데이터 height 배열(벽의 높이), 벽의 위치는 고정

어떤 두 벽을 고르면 가장 많은 물을 담을 수 있는지 확인하고 출력

### 2. 입출력 예시

```java
입력 : 1, 8, 6, 2, 5, 4, 8, 3, 7
출력 : 49
    
입력 : 5, 3, 9, 2, 1, 1, 1, 1, 1, 1, 1, 1, 1, 2
출력 : 49
```

### 3. 코드

```java
public static int solution(int[] height) {        
        int range = 0, rangeMax = 0;

        for (int i = 0; i < height.length; i++) {
            for (int j = 0; j < height.length - 1; j++) {
                
                if (i == j) {
                    // 붙은 벽은 Pass
                    continue;
                }
                
                int wallMin = Math.min(height[i], height[j]);
                int width = 0;
                
                if (i > j){
                    width = i - j;
                }else{
                    width = j - i;
                }
                
                range = wallMin * width;
                rangeMax = Math.max(rangeMax, range);
            }

        }

        return rangeMax;
    }
```

### 4. 풀이과정

![KakaoTalk_20220519_225235995](https://user-images.githubusercontent.com/105831105/169312459-d075fa31-cb24-42d7-9bae-e1e9b4030651.jpg)

### 5. 정답

```java
public static int solution(int[] height) {
    int left = 0;
    int right = height.length - 1;
    int maxArea = 0;

    while (left < right) {
        // # 1
        int x = (right - left);
        int y = height[left] < height[right] ? height[left] : height[right];
        int curArea = x * y;
        maxArea = maxArea > curArea ? maxArea : curArea;

        // # 2
        // curArea = (right - left) * Math.min(height[left], height[right]);
        // maxArea = Math.max(maxArea, curArea);

        if (height[left] < height[right]) {
            left++;
        } else {
            right--;
        }
    }

    return maxArea;
}
```

---

## 로마자를 정수형으로 변환

> [답안](https://github.com/seoli0179/ZeroBaseJava/blob/master/JavaBasic/src/Practice/Java_18_2/src/Practice1.java)
>
> [정답](https://github.com/seoli0179/ZeroBaseJava/blob/master/JavaBasic/src/Solution/Java_18_2/src/Practice1.java)

### 1. 문제

로마 숫자 표기를 정수형으로 변환하는 프로그램을 작성하세요.

로마 숫자 표기법은 I, V, X, L, C, D, M 으로 이루어져있다.

|로마 숫자|정수형|
|---|---|
|I|1|
|V|5|
|X|10|
|L|50|
|C|100|
|D|500|
|M|1000|


로마 숫자 표기 방식
* 큰 기호에서 작은 기호 방향으로 작성 (XI, VI, II, ...)
* 다음의 경우 작은 기호가 큰 기호 앞에 올 수 있다.
  * I 는 V 와 X 의 앞에 올 수 있다. (IV: 4, IX: 9)
  * X 는 L 과 C 의 앞에 올 수 있다. (XL: 40, XC: 90)
  * C 는 D 와 M 의 앞에 올 수 있다. (CD: 400, CM: 900)
  
    

입출력 예시

|입력|출력|
|---|---|
|"III"|3|
|"IV"|4|
|"VI"|6|
|"XIII"|13|
|"XXVI"|26|
|"MCMXCIV"|1994|

### 2. 풀이



---

## 정수형을 로마자로 변환

> [답안](https://github.com/seoli0179/ZeroBaseJava/blob/master/JavaBasic/src/Practice/Java_18_2/src/Practice2.java)
>
> [정답](https://github.com/seoli0179/ZeroBaseJava/blob/master/JavaBasic/src/Solution/Java_18_2/src/Practice1.java)

### 1. 문제

정수형 숫자를 로마 숫자 표기로 변환하는 프로그램을 작성하세요.

로마 숫자 표기법은 I, V, X, L, C, D, M 으로 이루어져있다.

|로마 숫자|정수형|
|---|---|
|I|1|
|V|5|
|X|10|
|L|50|
|C|100|
|D|500|
|M|1000|


로마 숫자 표기 방식
* 큰 기호에서 작은 기호 방향으로 작성 (XI, VI, II, ...)
* 다음의 경우 작은 기호가 큰 기호 앞에 올 수 있다.
    * I 는 V 와 X 의 앞에 올 수 있다. (IV: 4, IX: 9)
    * X 는 L 과 C 의 앞에 올 수 있다. (XL: 40, XC: 90)
    * C 는 D 와 M 의 앞에 올 수 있다. (CD: 400, CM: 900)

**입출력 예시**

|입력|출력|
|---|---|
|3|"III"|
|4|"IV"|
|6|"VI"|
|13|"XIII"|
|26|"XXVI"|
|1994|"MCMXCIV"|

### 2. 풀이



---

## 간단한 편집기

> [답안](https://github.com/seoli0179/ZeroBaseJava/blob/master/JavaBasic/src/Practice/Java_18_2/src/Practice3.java)
>
> [정답](https://github.com/seoli0179/ZeroBaseJava/blob/master/JavaBasic/src/Solution/Java_18_2/src/Practice3.java)

### 1. 문제

간단한 편집기를 구현하려고 한다.

편집기에는 문자열과 편집 명령어가 주어지는데, 명령어의 동작은 다음과 같다.
- L : 커서를 왼쪽으로 한 칸 옮김 (커서가 문장의 맨 앞이면 무시)
- D	: 커서를 오른쪽으로 한 칸 옮김 (커서가 문장의 맨 뒤이면 무시)
- B	: 커서 왼쪽에 있는 문자를 삭제 (커서가 문장의 맨 앞이면 무시)
- P x : x라는 문자를 커서 왼쪽에 추가

여기서 커서는 문자열에서 편집이 시작되는 기준 위치로,  
문장의 맨 앞, 맨 뒤, 중간에 위치할 수 있다.

편집기에 문자열과 명령어들이 주어졌을 때,  
편집을 완료한 후의 문자열을 출력하는 프로그램을 작성하시오.  
(초기 커서의 위치는 문장의 맨 뒤에서 시작한다.)  
(문자열은 소문자만 입력 가능하다.)

**입출력 예시**

|초기 문자열|명령어|결과 출력|
|---|---|---|
|"aba"|"L B"|"aa"|
|"abcd"|"P x L P y"|"abcdyx"|
|"abc"|"L L L P x L B P y"|"yxabc"|
|"a"|"B B L L D D P a P b P c"|"abc"|

### 2. 풀이



---

# 제로베이스 미니과제

## 로또 당첨 프로그램

### 1. 문제

- 로또를 구매하고 당첨번호랑 비교하여 일치 여부 판단하기

### 2. 입출력 예시

```java
[로또 당첨 프로그램]

로또 개수를 입력해 주세요.(숫자 1 ~ 10) : 2
A	13, 28, 31, 35, 40, 44
B	00, 01, 09, 20, 39, 43

[로또 발표]
	01, 02, 12, 13, 21, 35

[내 로또 결과]
A	13, 28, 31, 35, 40, 44 => 2개 일치
B	00, 01, 09, 20, 39, 43 => 1개 일치
```

### 3. 코드

```java
package Quest07;

import java.util.*;

public class Quest07 {

    public static Scanner sc = new Scanner(System.in);

    public static Integer[] lottoGenerate() {

        // HashSet은 중복값 허용하지 않는다.
        HashSet set = new HashSet();

        for (int i = 0; set.size() < 6; i++) {
            int num = (int) (Math.random() * 45) * 1;
            set.add(num);
        }

        // 오른차순 정렬
        LinkedList list = new LinkedList(set);
        Collections.sort(list);

        // Integer 배열로 변환
        return (Integer[]) list.toArray(new Integer[0]);

    }

    public static void lottoDisplay() {

        System.out.println("[로또 당첨 프로그램]\n");
        System.out.print("로또 개수를 입력해 주세요.(숫자 1 ~ 10) : ");

        int num = sc.nextInt();
        Integer[][] lottoUserArray = new Integer[num][6];
        Integer[] lottoComputer = lottoGenerate();

        for (int i = 0; i < num; i++) {
            lottoUserArray[i] = lottoGenerate();
            System.out.printf("%c\t%02d, %02d, %02d, %02d, %02d, %02d\n", (char) i + 'A', lottoUserArray[i][0], lottoUserArray[i][1], lottoUserArray[i][2], lottoUserArray[i][3], lottoUserArray[i][4], lottoUserArray[i][5]);
        }

        System.out.println("\n[로또 발표]");
        System.out.printf("\t%02d, %02d, %02d, %02d, %02d, %02d\n", lottoComputer[0], lottoComputer[1], lottoComputer[2], lottoComputer[3], lottoComputer[4], lottoComputer[5]);

        System.out.println("\n[내 로또 결과]");

        for (int i = 0; i < lottoUserArray.length; i++) {
            int count = 0;
            for (Integer j : lottoUserArray[i]) {
                for (Integer k : lottoComputer) {
                    if (Objects.equals(j, k)) {
                        count++;
                    }
                }
            }
            System.out.printf("%c\t%02d, %02d, %02d, %02d, %02d, %02d => %d개 일치\n", (char) i + 'A', lottoUserArray[i][0], lottoUserArray[i][1], lottoUserArray[i][2], lottoUserArray[i][3], lottoUserArray[i][4], lottoUserArray[i][5], count);
            count = 0;
        }
    }


    public static void main(String[] args) {
        lottoDisplay();
    }
}

```

### 4. 풀이과정

> ❓ **HashSet 스트림을 사용한 이유**
>
> HashSet은 중복된 값을 허용하지 않기 때문에 중복값이 있으면 안되는 로또 번호 생성에 적합하다고 생각했다.
>
> ❓ **LinkedList를 사용한 이유**
>
> HashSet은 순서를 보장하지 않기 때문에 값을 정렬하기 위해서 사용했다.
>
> ❓ **Integer 배열을 사용한 이유**
>
> LinkedList에서 get으로 값을 받아 쓰는것보다 Integer 배열이 공용으로 쓰기에 적합하다고 생각해 사용했다.

---

## 과세금액 계산 프로그램

### 0. 코드

```java
package Quest08;

import java.util.Scanner;

public class Quest08 {

    static Scanner sc = new Scanner(System.in);

    // 누진공제
    static final long[] progressiveTaxData = {0, 1080000, 5220000, 14900000, 19400000, 25400000, 35400000, 65400000};

    // 과세 표준
    static final long[] TaxData1 = {0, 12000000, 46000000, 88000000, 150000000, 300000000, 500000000, 1000000000};
    static final long[] TaxData2 = {0, 12000000, 34000000, 42000000, 62000000, 150000000, 200000000, 500000000, 1000000000};

    // 세율
    static final double[] TaxRateData = {0.06, 0.15, 0.24, 0.35, 0.38, 0.4, 0.42, 0.45};

    public static void taxCalculatorDisplay() {

        System.out.println("[과세금액 계산 프로그램]");
        System.out.print("연소득을 입력해 주세요 : ");

        // 연소득 금액
        long salaryAnnual = sc.nextLong();
        long salaryAnnualTemp = salaryAnnual;

        long tax;                   // 각 세율의 세금 계산
        long tax_sum = 0;           // 총 세금 계산
        long ProgressiveTax = 0;    // 누진 공세

        for (int i = 0; i < TaxData1.length; i++) {
            if (salaryAnnual > TaxData1[i] || (i == 0 && salaryAnnual >= 0)) {

                salaryAnnualTemp -= TaxData2[i];

                // 세율계산
                tax = (i == TaxData1.length - 1) ? (long) (salaryAnnualTemp * TaxRateData[i]) : (long) ((Math.min(salaryAnnualTemp, TaxData2[i + 1])) * TaxRateData[i]);
                tax_sum += tax;

                // 누진공제계산
                ProgressiveTax = (i == 0) ? 0L : (long) ((salaryAnnual * TaxRateData[i]) - progressiveTaxData[i]);

                System.out.printf("%10d * %2d%% = \t%10d\n", (i == TaxData1.length - 1) ? salaryAnnualTemp : Math.min(salaryAnnualTemp, TaxData2[i + 1]), (int) (TaxRateData[i] * 100), tax);
            }
        }


        System.out.printf("\n[세율에 위한 세금] : \t\t\t%10d\n", tax_sum);
        System.out.printf("[누진공제 계산에 의한 세금] : \t%10d", ProgressiveTax);

    }

    public static void main(String[] args) {

        taxCalculatorDisplay();
        sc.close();
    }
}
```