## 01. String 메소드

<br>   

![image](https://github.com/last-child/STUDY_NOTE/assets/98595054/5067e682-2f7d-47b4-9b09-2acb20236a69)

<br>   

```java
String str1 = "Hello, World!";
String str2 = "hello, World!";

int length = str1.length();                      // 문자열의 길이 → 13

char character = str1.charAt(4);                 // 4번 인덱스의 문자 → 'o'

boolean result1 = str1.equals(str2);             // 두 문자열이 동일한지 비교 → false

boolean result2 = str1.equalsIgnoreCase(str2);   // 대소문자를 무시하고 두 문자열이 동일한지 비교 → true

int result3 = str1.compareTo(str2);              // 두 문자열 유니코드 순으로 비교 → 양수
```

<br>   
<br>   

![image](https://github.com/last-child/STUDY_NOTE/assets/98595054/86735af4-24c1-42dd-a869-0883b5583e7b)

<br>   

```java
String text = "Hello, World! Hello, Universe!";
        
int index1 = text.indexOf("Hello");           // 특정 단어의 처음 등장 위치 → 0

int index2 = text.indexOf("Hello", 7);        // 7번 인덱스 이후에 특정 단어의 처음 등장 위치 → 13

int index3 = text.lastIndexOf("Hello");       // 특정 단어의 마지막 등장 위치 → 13

boolean result1 = text.contains("World");     // 특정 단어를 포함하는지? → true

boolean result2 = text.startsWith("Hello");   // 특정 단어로 시작하는지? → true
        
boolean result3 = text.endsWith("Planet!");   // 특정 단어로 끝나는지? → false
```

<br>   
<br>   

![image](https://github.com/last-child/STUDY_NOTE/assets/98595054/9c99dcd3-73bf-4a8e-a0fd-80c395ef8c58)

<br>   

```java
String text = "Hello, World!";
    
String text1 = text.replace("World", "Human");   // "World"를 "Human"으로 치환한 문자열 → "Hello, Human!"

String text2 = text.substring(4);                // 4번 인덱스부터 끝까지의 부분 문자열 → "o, World!"

String text3 = text.substring(3, 8);             // 3번 인덱스부터 8번 인덱스 직전까지의 부분 문자열 → "lo, W"

String text4 = text.toLowerCase();               // 소문자로 변환한 문자열 → "hello, world!"

String text5 = text.toUpperCase();               // 대문자로 변환한 문자열 → "HELLO, WORLD!"
```

<br>   
