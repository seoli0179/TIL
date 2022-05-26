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

#### 팩토리얼

> 1에서 n까지의 모든 자연수의 곱 (n!)

![image](https://user-images.githubusercontent.com/105831105/170264466-3307f04e-7535-4fa3-a69f-50b62ef542b4.png)

```java
// 팩토리얼
int n = 5;
int result = 1;
for (int i = 1; i <= n; i++) {
    result *= i;
}
System.out.println(result);
```

```java
System.out.println(IntStream.range(2, 6).reduce(1, (x, y) -> (x * y)));
```

#### 순열

> 서로 다른 n개 중에서 r개를 선택하는 경우의 수 (순서O, 중복X)
>
> 예시) 5명을 3줄로 세우는 방법
>
> 예시) 서로 다른 4명 중 반장, 부반장 뽑는 방법

![image](https://user-images.githubusercontent.com/105831105/170264374-1bc7d415-6bbe-4afa-83e1-3731ef07cdc1.png)

```java
int n = 5;
int r = 3;
int result = 1;

for (int i = n; i >= n - r + 1; i--) {
    result *= i;
}
System.out.println(result);
```



#### 중복 순열

> 서로 다른 n개 중에 r개를 선택하는 경우의 수 (순서O, 중복O)
>
> 예시) 서로 다른 4개의 수 중 2개를 뽑는 방법 (중복 허용)
>
> 예시) 후보 2명, 유권자 3명일 때 기명 투표 방법

![image](https://user-images.githubusercontent.com/105831105/170265236-27e32e3e-a4b5-42dc-ba10-27b1c4209dcf.png)

```java
int n = 4;
int r = 2;
int result = 1;
for (int i = 0; i < r; i++) {
    result *= n;
}
System.out.println(result);
```

```java
System.out.println(Math.pow(n, r));
```

#### 원 순열

> 원 모양의 테이블에 n개의 원소를 나열하는 경우의 수
>
> 예시) 원 모양의 테이블에 3명을 앉히는 경우

![image](https://user-images.githubusercontent.com/105831105/170265521-bb3b641c-8d92-4f70-82e4-2a2175363e89.png)

![원 순열 공식](https://blog.kakaocdn.net/dn/qQxR9/btqHBRtzmpx/J1LyLclK1SafprzJm77QHk/img.png)

```java
int n = 3;
int result = 1;

for (int i = 1; i < n; i++) {
    result *= i;
}
System.out.println(result);
```

#### 연습

````java
//1,2,3,4를 이용해여 세자리 자연수 만드는 방법 (순서O, 중복X)
public void permutation1(int[] arr, int depth, int n, int r) {

    if (depth == r) {
        for (int i = 0; i < r; i++) {
            System.out.print(arr[i] + " ");
        }
        System.out.println();
        return;
    }

    for (int i = depth; i < n; i++) {
        swap(arr, depth, i);
        permutation1(arr, depth + 1, n, r);
        swap(arr, depth, i);
    }

}
void swap(int[] arr, int depth, int idx) {
    int tmp = arr[depth];
    arr[depth] = arr[idx];
    arr[idx] = tmp;
}
void permutation2(int[] arr, int depth, int n, int r, boolean[] visited, int[] out) {

    if (depth == r) {
        System.out.println(Arrays.toString(out));
        return;
    }

    for (int i = 0; i < n; i++) {
        if (visited[i] != true) {
            visited[i] = true;
            out[depth] = arr[i];
            permutation2(arr, depth + 1, n, r, visited, out);
            visited[i] = false;
        }
    }
    
    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4};
        boolean[] visited = new boolean[4];
        int[] out = new int[3];

        Solution solution = new Solution();
        solution.permutation1(arr, 0, 4, 3);
        solution.permutation2(arr, 0, 4, 3, visited, out);

    }

}
````



### 조합

```java
public int combination(int n, int r) {
    if (n == r || r == 0)
        return 1;
    else
        return combination(n - 1, r - 1) + combination(n - 1, r);
}
```





---

## Ch02. 선형 자료구조



## Ch03. 비선형 자료구조



## Ch04. 알고리즘



## Ch05. 기출 문제 풀이