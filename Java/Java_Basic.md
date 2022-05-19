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

![](C:\Users\yeoub\Documents\카카오톡 받은 파일\KakaoTalk_20220519_221239298.jpg)

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

![](C:\Users\yeoub\Documents\카카오톡 받은 파일\KakaoTalk_20220519_225235995.jpg)

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



