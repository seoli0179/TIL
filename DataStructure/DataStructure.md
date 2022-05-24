# 자료구조/알고리즘

## Ch01. 기초 수학

### 01. 집합

> 특정한 조건에 맞는 **별개의 원소들의 모임**

#### 교집합

![image](https://user-images.githubusercontent.com/105831105/169832648-f4dba573-fc24-4049-8f56-ccddcc6ac1a2.png)

![image](https://user-images.githubusercontent.com/105831105/169832931-0cc472cb-68ae-4ff9-8be0-8035c467d74b.png)

```java
HashSet a = new HashSet(Arrays.asList(1, 2, 3, 4, 5));
HashSet b = new HashSet(Arrays.asList(2, 4, 6, 8, 10));
a.retainAll(b);	// 교집합
System.out.println(a);  // [2, 4]
```

```java
// 교집합
class MySet {
    ArrayList<Integer> list;
    
    public MySet() {
        this.list = new ArrayList<Integer>();
    }
    
    public MySet(int[] arr) {
        this.list = new ArrayList<Integer>();

        for (int item : arr) {
            this.list.add(item);
        }
    }
    
    public MySet retainAll(MySet b) {
        MySet result = new MySet();
        for (int itemA : this.list) {
            for (int itemB : b.list) {
                if (itemA == itemB) {
                    result.add(itemA);
                }
            }
        }
        return result;
    }
}

public class Main {
    public static void main(String[] args) {

        MySet a = new MySet(new int[]{1,2,3,4,5});
        MySet b = new MySet(new int[]{3,4,5,6,7});
        MySet result;

        result = a.retainAll(b);
        System.out.println(result.list);	// [3, 4, 5]

    }
}
```

---

#### 합집합

![image](https://user-images.githubusercontent.com/105831105/169834573-ece87578-7a8d-4277-b941-dc2b9fe2e387.png)

![image](https://user-images.githubusercontent.com/105831105/169834620-8fa9e2b1-2486-4a0e-a41b-2a0adafb98d6.png)

```java
HashSet a = new HashSet(Arrays.asList(1, 2, 3, 4, 5));
HashSet b = new HashSet(Arrays.asList(2, 4, 6, 8, 10));
a.addAll(b);    // 합집합
System.out.println(a);  // [1, 2, 3, 4, 5, 6, 8, 10]
```

```java
// 합집합
class MySet {
    ArrayList<Integer> list;
    
    public MySet() {
        this.list = new ArrayList<Integer>();
    }
    
    public MySet(int[] arr) {
        this.list = new ArrayList<Integer>();

        for (int item : arr) {
            this.list.add(item);
        }
    }
    
    public MySet addAll(MySet b) {
        MySet result = new MySet();

        for (int itemA : this.list) {
            result.add(itemA);
        }

        for (int itemB : b.list) {
            result.add(itemB);
        }
        return result;
    }
}

public class Main {
    public static void main(String[] args) {

        MySet a = new MySet(new int[]{1,2,3,4,5});
        MySet b = new MySet(new int[]{3,4,5,6,7});
        MySet result;

        result = a.addAll(b);
        System.out.println(result.list);	// [1, 2, 3, 4, 5, 6, 7]

    }
}

```

---

#### 차집합

![image](https://user-images.githubusercontent.com/105831105/169834898-2da8e458-0d2c-45a5-96f4-566babd0e16a.png)

![image](https://user-images.githubusercontent.com/105831105/169835044-e0ab3047-e9d5-449d-a46d-4f5ff83144f2.png)

```java
HashSet a = new HashSet(Arrays.asList(1, 2, 3, 4, 5));
HashSet b = new HashSet(Arrays.asList(2, 4, 6, 8, 10));
a.retainAll(b);    // 차집합
System.out.println(a);  // [2, 4]
```

```java
// 차집합
class MySet {
    ArrayList<Integer> list;
    
    public MySet() {
        this.list = new ArrayList<Integer>();
    }
    
    public MySet(int[] arr) {
        this.list = new ArrayList<Integer>();

        for (int item : arr) {
            this.list.add(item);
        }
    }
    
    public MySet removeAll(MySet b) {
        MySet result = new MySet();

        for (int itemA : this.list) {
            boolean containFlag = false;

            for (int itemB : b.list) {
                if (itemA == itemB) {
                    containFlag = true;
                    break;
                }
            }
            if(!containFlag){
                result.add(itemA);
            }
        }
        return result;
    }
}

public class Main {
    public static void main(String[] args) {

        MySet a = new MySet(new int[]{1,2,3,4,5});
        MySet b = new MySet(new int[]{3,4,5,6,7});
        MySet result;

        result = a.retainAll(b);
        System.out.println(result.list);	// [1, 2]

    }
}
```

---

### 02. 경우의 수

#### 합의 법칙

>  사건 A와 사건 B의 합의 법칙 : **n ( A ∪ B ) = n ( A ) + n ( B ) - n ( A ∩ B )**

```java
int[] dice1 = {1, 2, 3, 4, 5, 6};
int[] dice2 = {1, 2, 3, 4, 5, 6};

int nA = 0;
int nB = 0;
int nAandB = 0;

// 두 개의 주사위를 던졌을 때 합이 3 또는 4의 배수일 경우의 수
for (int item1 : dice1) {
    for (int item2 : dice2) {
        if ((item1 + item2) % 3 == 0) {
            nA += 1;
        }
        if ((item1 + item2) % 4 == 0) {
            nB += 1;
        }
        if ((item1 + item2) % 12 == 0) {
            nAandB += 1;
        }
    }
}
System.out.println((nA + nB - nAandB)); //20
```

```java
// 두 개의 주사위를 던졌을 때 합이 3 또는 4의 배수일 경우의 수

int[] dice1 = {1, 2, 3, 4, 5, 6};
int[] dice2 = {1, 2, 3, 4, 5, 6};

HashSet<ArrayList> allCase = new HashSet<>();
for (int item1 : dice1) {
    for (int item2 : dice2) {
        if ((item1 + item2) % 3 == 0 || (item1 + item2) % 4 == 0) {
            ArrayList list = new ArrayList(Arrays.asList(item1, item2));
            allCase.add(list);
        }
    }
}
System.out.println(allCase.size());
```

#### 곱의 법칙

> 사건 A와 사건 B의 곱의 법칙 : **n ( A X B ) = n ( A ) X n ( B )**

```java
// 두 개의 주사위 a, b를 던졌을 때 a는 3의 배수, b는 4의 배수인 경우의 수
nA = 0;
nB = 0;

for (int item1:dice1){
    if(item1 % 3 == 0){
        nA++;
    }
}
for (int item1:dice2){
    if(item1 % 4 == 0){
        nB++;
    }
}

System.out.println(nA * nB);    // 2
```

#### 약수, 최소공약수, 최대공배수

````java
// 약수
public ArrayList getDivisor(int num) {
    ArrayList result = new ArrayList();

    for (int i = 1; i < num / 2; i++) {
        if (num % i == 0) {
            result.add(i);
        }
    }
    result.add(num);

    return result;
}
````

```java
// 최대 공약수
// GCD : the Greatest Common Denominator
public int getGCD(int numA, int numB) {
    int gcd = -1;

    ArrayList divisorA = this.getDivisor(numA);
    ArrayList divisorB = this.getDivisor(numB);

    for (int itemA : (ArrayList<Integer>) divisorA) {
        for (int itemB : (ArrayList<Integer>) divisorB) {
            if (itemA == itemB) {
                if (itemA > gcd) {
                    gcd = itemA;
                }
            }
        }
    }

    return gcd;
}
```

```java
// 최소 공배수
// LCM : the Lowest Common Multiple
public int getLCM(int numA, int numB){
    int lcm = -1;

    int gcd = this.getGCD(numA,numB);
    if(gcd != -1){
        lcm = numA * numB / gcd;
    }

    return lcm;
}
```







---

### 03. 순열

## Ch02. 선형 자료구조



## Ch03. 비선형 자료구조



## Ch04. 알고리즘



## Ch05. 기출 문제 풀이