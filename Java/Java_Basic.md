# Java 기본

## 01. 변수와 자료형

---

## 02. 연산자

---

## 03.조건문

---

## 04.반복문

---

## 05. 배열

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



---

# 연습문제

---

## 정수 자료형의 숫자를 거꾸로 변환



---

## 별 찍기

### (1)

1. 입출력 예시

```java
[입력]
3
[출력]
***
***
***
```

2. 코드


```java
for (int i = 0; i < n; i++) {
    for (int j = 0; j < n; j++) {
        System.out.print("*");
    }
    System.out.println();
}
```

3. 풀이과정


|  행  |  i   |  *   | * 공식 |
| :--: | :--: | :--: | :----: |
|  0   |  0   |  3   | n - 1  |
|  1   |  1   |  3   |        |
|  2   |  2   |  3   |        |

### (2)

1. 입출력 예시

```java
[입력]
3
[출력]
*
**
***
```

2. 코드

```java
for (int i = 0; i < n; i++) {
    for (int j = 0; j < i + 1; j++) {
        System.out.print("*");
    }
            System.out.println();
}
```

3. 풀이과정


|  행  |  i   |  *   | * 공식 |
| :--: | :--: | :--: | :----: |
|  0   |  0   |  1   | i + 1  |
|  1   |  1   |  2   |        |
|  2   |  2   |  3   |        |

### (3)

1. 입출력 예시

```java
[입력]
3
[출력]
  *
 **
***
```

2. 코드

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

3. 풀이과정

|  행  |  i   | space | space 공식 |  *   | * 공식 |
| :--: | :--: | :---: | :--------: | :--: | :----: |
|  0   |  0   |   2   | n - i - 1  |  1   | i  + 1 |
|  1   |  1   |   1   |            |  2   |        |
|  2   |  2   |   0   |            |  3   |        |

### (4)

1. 입출력 예시

```java
[입력]
3
[출력]
  *
 ***
*****
```

2. 코드


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

3. 풀이과정

|  행  |  i   | space | space 공식 |  *   |  * 공식   |
| :--: | :--: | :---: | :--------: | :--: | :-------: |
|  0   |  0   |   2   | n - i - 1  |  1   | i * 2 + 1 |
|  1   |  1   |   1   |            |  3   |           |
|  2   |  2   |   0   |            |  5   |           |

### (5)

1. 입출력 예시

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

2. 코드

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

3. 풀이과정

![KakaoTalk_20220519_221239298](https://user-images.githubusercontent.com/105831105/169312266-b44248da-98b2-4827-84a1-d26ce8027784.jpg)

4. 정답

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
                    if (j == k) {
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

---

