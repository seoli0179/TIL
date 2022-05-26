# 자료구조와 알고리즘

## 02. 알고리즘이 중요한 까닭

### 이진 검색

```java
// 선형 검색 O(N)
// 이진 검색 O(logN)
public static int binarySearch(int[] arr, int search) {
    int lowerBound = 0;
    int upperBound = arr.length - 1;
    while (lowerBound <= upperBound) {
        int midPoint = (upperBound + lowerBound) / 2;
        int value = arr[midPoint];
        if (value == search) {
            return midPoint;
        } else if (value > search) {
            upperBound--;
        } else {
            lowerBound++;
        }
    }
    return -1;
}
```



## 04. 빅 오로 코드 속도 올리기

### 버블정렬

```java
// 순차정렬 : 
public static void buble(int[] arr) {
    int index = arr.length - 1;
    boolean sorted = false;
    while (!sorted) {
        sorted = true;
        for (int i = 0; i < index; i++) {
            if (arr[i] > arr[i + 1]) {
                int temp = arr[i + 1];
                arr[i + 1] = arr[i];
                arr[i] = temp;
                sorted = false;
            }
        }
        index--;
    }

    for (int i : arr){
        System.out.print(i + " ");
    }

}
```

### 선형 해결법

```java
// 중첩 루프 : O(N^2)
// 중첩 루프를 쓰지 않고 중복값 유무 검색하기 : O(N)
public static boolean hasDuplicateValue(int[] arr) {
    ArrayList<Boolean> arrayList = new ArrayList<Boolean>();
    for (int i = 0; i < arr.length; i++) {
        if (arrayList.size() < arr[i] + 1) {
            for (int j = arrayList.size(); j < arr[i] + 1; j++) {
                arrayList.add(false);
            }
        }
        if (arrayList.get(arr[i])) {
            return true;
        } else {
            arrayList.set(arr[i], true);
        }
    }
    return false;
}
```

