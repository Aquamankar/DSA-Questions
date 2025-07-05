### Java Interview Questions and Programs

---

#### **1. What is the output of the following code?**

```java
class Main {
    public static void main(String args[]) {
        int[] arr = {10, 20};
        swap(arr);
        System.out.println(Arrays.toString(arr));
    }

    public static void swap(int[] arr) {
        int temp = arr[0];
        arr[0] = arr[1];
        arr[1] = temp;
    }
}
```

**Answer:** `[20, 10]`

---

#### **2. What will be the output of the below program?**

```java
public class Test {
    public static void main(String args[]) {
        double[] myList = {1, 5, 5, 5, 5, 1};
        double max = myList[0];
        int indexOfMax = 0;
        for(int i = 1; i < myList.length; i++) {
            if(myList[i] > max){
                max = myList[i];
                indexOfMax = i;
            }
        }
        System.out.println(indexOfMax);
    }
}
```

**Answer:** `1`

---

#### **3. Count and print number of occurrences of each consonant in "I live in India"**

```java
public class Main {
    public static void main(String[] args) {
        String s = "I live in India".toLowerCase();
        Map<Character, Integer> map = new HashMap<>();
        for(char c : s.toCharArray()) {
            if(Character.isLetter(c) && "aeiou".indexOf(c) == -1) {
                map.put(c, map.getOrDefault(c, 0) + 1);
            }
        }
        for(Map.Entry<Character, Integer> entry : map.entrySet()) {
            System.out.println(entry.getKey() + " = " + entry.getValue());
        }
    }
}
```

**Sample Output:**

```
l = 1
v = 1
n = 2
d = 1
```

---

#### **4. Check if a list contains only odd numbers**

```java
List<Integer> list = Arrays.asList(3, 5, 7, 9, 11);
boolean allOdd = list.stream().allMatch(i -> i % 2 != 0);
System.out.println(allOdd);
```

**Answer:** `true`

---

#### **5. Factorial using Recursion**

```java
public class Main {
    public static void main(String[] args) {
        int num = 4;
        System.out.println(factorial(num));
    }

    public static int factorial(int num) {
        if(num == 0 || num == 1) return 1;
        return num * factorial(num - 1);
    }
}
```

**Output:** `24`

---

#### **6. Print all Prime Numbers between n1 and n2 in reverse order**

```java
public class Main {
    public static void main(String[] args) {
        int n1 = 3, n2 = 13;
        for (int i = n2; i >= n1; i--) {
            if (isPrime(i)) {
                System.out.println(i);
            }
        }
    }

    public static boolean isPrime(int n) {
        if (n <= 1) return false;
        for (int i = 2; i <= Math.sqrt(n); i++) {
            if (n % i == 0) return false;
        }
        return true;
    }
}
```

---

#### **7. Reverse each word in a string**

```java
public class Main {
    public static void main(String[] args) {
        String s = "I live in India";
        StringBuilder sb = new StringBuilder();
        String[] arr = s.trim().split(" ");

        for (String word : arr) {
            sb.append(new StringBuilder(word).reverse()).append(" ");
        }

        System.out.println(sb.toString().trim());
    }
}
```

**Output:** `I evil ni aidnI`

---

#### **8. Find the maximum number from an array**

```java
List<Integer> list = Arrays.asList(1, 3, 9, 7, 5);
Optional<Integer> ans = list.stream().max(Integer::compare);
System.out.println(ans.orElse(0));
```

**Output:** `9`

---

#### **9. Check if two strings are Anagrams**

```java
String s1 = "eat", s2 = "ate";
char[] c1 = s1.toCharArray();
char[] c2 = s2.toCharArray();
Arrays.sort(c1);
Arrays.sort(c2);

if (Arrays.equals(c1, c2)) {
    System.out.println("Anagrams");
} else {
    System.out.println("Not Anagrams");
}
```

**Output:** `Anagrams`

---

#### **10. Output and Explanation**

```java
public class Main {
    public static void main(String[] args) {
        int a = 1;
        A aObj = new A(1);
        modify(a, aObj);
        System.out.println(a);
        System.out.println(aObj.getA());
    }

    private static void modify(int a, A aObj) {
        a = 2;
        aObj.setA(2);
    }
}

class A {
    int a;
    public A(int a) { this.a = a; }
    public void setA(int a) { this.a = a; }
    public int getA() { return a; }
}
```

**Answer:**

```
1
2
```

**Explanation:**

* `int a` is passed by value, so changes to `a` inside `modify` do not affect original `a`.
* `A aObj` is an object reference. `aObj.setA(2)` modifies the original object.

---
