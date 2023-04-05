# 5. 참조타입

### 5.1 데이터 타입 분류

> 객체란?
>
> 객체는 데이터와 메소드로 구성된 덩어리
>
> `객체 - 데이터(필드) + 메소드`

| 기본 타입                                                    | 참조 타입  |
| ------------------------------------------------------------ | ---------- |
| 정수 타입<br />    byte<br />    char<br />    short<br />    int<br />    long | 배열타입   |
| 실수 타입<br />    float<br />    double                     | 열거타입   |
| 논리타입<br />    boolean                                    | 클래스     |
|                                                              | 인터페이스 |

- 기본 타입 : 값 자체를 저장
- 참조 타입 : 객체가 생성된 메모리 번지를 저장

```
[기본 타입 변수]
int age = 25;
double price = 100.5

[참조 타입 변수]
String name = "신용권";
String hobby = "독서";
```

- 변수들은 모두 스택이라는 메모리 영역에 생성



### 5.2 메모리 사용 영역

##### 메소드 영역

- 바이트코드 파일을 읽은 내용이 저장되는 영역
- 클래스 별로 상수, 정적 필드, 메소드 코드, 생성자 코드 등 저장



##### 힙 영역

- 객체가 생성되는 영역
- 객체의 번지는 메소드 영역과 스택 영역의 상수와 변수에서 참조



##### 스택 영역

- 메소드를 호출할 때마다 생성되는 프레임이 저장되는 영역
- 메소드 호출이 끝나면 프레임이 자동 제거



### 5.3 참조 타입 변수의 ==, !=

- ==, != 연산자는 변수의 값이 같은지, 아닌지 조사
- 참조 타입 변수의 값은 객체의 번지이므로 ==, != 연산자는 번지를 비교하는 것



### 5.4 null과 NullPointerException

##### null

- 아직 변수를 저장하고 있지 않다.
- null도 초기값으로 사용 가능
- null로 초기화된 참조 변수는 스택 영역에 생성

```
String refVar1 = "자바";
String refVar2 = null;

refVar1 == null	// 결과: false
refVar1 != null // 결과: true

refvar2 == null // 결과: true
refcar2 != null // 결과: false
```



##### NullPointerException

- 변수가 null인 상태에서 객체의 데이터나 메소드를 사용하려 할 때 발생

```
int[] intArray = null;
intArray[0] = 10;	// NullPointerException : intArray가 참조하는 배열 객체가 없다.

String str = null;
System.out.println("총 문자 수: " + str.length()) 
// NullPointerException : str변수가 참조하는 String 객체가 없다.
```



- 변수에 null을 대입하면 번지를 잃게 되므로 더 이상 객체를 사용 불가

```
String hobby = "여행";
hobby = null;
```

- 어떤 변수에서도 객체를 참조하지 않으면 해당 객체는 프로그램에서 사용할 수 없는 객체
- 힙 메모리에는 있지만, 위치 정보를 모르기 때문에 사용할 수 없다.
- 자바에서 자동으로 GC을 실행시켜 제거
- 객체를 제거하는 방법은 객체의 모든 참조를 없애는 것



### 5.5 문자열 타입

##### 문자열 비교(equals())

```
String name1 = "홍길동";
String name2 = "홍길동";
String new name3 = new String("홍길동");

name1 == name2	// true
name1 == name3	// false

boolean result = name1.equals(name3);	// 문자열이 같은지 검사(대소문자 구분)
boolean result = ! name1.equlas(name3);	// 문자열이 다른지 검사
```



##### 문자 추출(charAt())

- 문자열에서 특정 위치의 문자를 얻을 때 사용
- 매개값으로 주어진 인덱스의 문자를 리턴

```
String subject = "자바 프로그래밍"
char charValue = subject.charAt(3);	// 프
```



##### 문자열 길이(length())

- 문자열의 개수를 얻을 때 사용

```
String subject = "자바 프로그래밍";
int length = subject.length();
```



##### 문자열 대체(replace())

- 특정 문자열을 다른 문자열로 대체하고 싶을 때 사용
- 기존 문자열을 그대로 두고, 대체한 새로운 문자열을 리턴

```
String oldStr = "자바 프로그래밍";
String newStr = oldStr.replace("자바", "Java");	// Java 프로그래밍
```



##### 문자열 잘라내기(substring())

- 특정 위치의 문자열을 잘라내어 가져올 때 사용

| 메소드                                  | 설명                                    |
| --------------------------------------- | --------------------------------------- |
| substring(int beginIndex)               | beginIndex에서 끝까지 잘라내기          |
| substring(int beginIndex, int endIndex) | beginIndex에서 endIndex 앞까지 잘라내기 |

```
String ssn = "880815-1234567";
String firstNum = ssn.substring(0, 6);	//880815
String lastNum = ss.substring(7);	//1234567

firstNum은 880815 문자열 참조
lastNum은 1234567 문자열 참조
```



##### 문자열 찾기(indexOf())

- 특정 문자열의 위치를 찾을 때 사용
- 주어진 문자열이 시작되는 인덱스 리턴
- 주어진 문자열이 포함되어 있지 않으면 -1 리턴

```
String subject = "자바 프로그래밍";
int index = subject.indexOf("프로그래밍");	// 3

"자바 프로그래밍"에서 "프로그래밍" 문자열의 인덱스 위치가 3번이기 때문에 3	
```

- 단순히 포함되어 있는지만 알고 싶으면 `contain()` 사용
- 포함되어 있으면 true, 아니면 false

```
boolean result - subject.contain("프로그래밍");	// 1
```



##### 문자열 분리(split(정규표현식regex))

> 정규표현식regex : 특정 규칙을 갖는 문자열

- 구분자를 사용하여 여러 개의 문자열로 구성되어 있을 경우, 따로 분리할 때 사용

```
String board = "번호,제목,내용,성명";
String[] arr = board.split(",");	// ["번호", "제목", "내용", "성명"]
```



### 5.6 배열 타입

- 연속된 공간에 값을 나열시키고, 각 값에 인덱스를 부여해 놓은 자료구조
- 인덱스는 대괄호 []와 함께 사용하여 각 항목을 읽거나 저장하는데 사용

```
int sum = 0;
for(int i = 0; i < 30; i++) {
	sum += score[i];
}
int avg = sum / 30;
```

- 배열은 같은 타입의 값만 관리한다.
- 배열의 길이는 늘리거나 줄일 수 없다.



##### 배열 선언 변수

```
타입[] 변수;
타입 변수[];
```

- 배열도 객체이므로 힙 영역에 생성, 배열 변수에는 힙 영역의 배열 주소 저장



##### 값 목록으로 배열 생성

```
타입[] 배열 = { 값0, 값1, 값2, 값3, ... }

// 배열의 값을 바꾸고 싶으면 대입 연산자 사용
배열[i] = 값i

// 배열 변수를 미리 선언한 후에는 값 목록을 변수에 대입할 수 없다.
타입[] = 변수
변수 = { 값0, 값1, 값2, 값3, ... };	// 컴파일 에러

// 선언 시점과 대입 시접이 다르면 new 타입[] 사용
변수 = new 타입[] { 값0, 값1, 값2, 값3, ... };
```



##### new 연산자로 배열 생성

- 향후 값들을 저장할 목적으로 배열을 미리 생성
- 길이는 배열이 저장할 수 있는 항목의 수를 의미

```
타입[] 변수 = new 타입[길이];

타입[] 변수 = null;
변수 = new 타입[길이];
// new 연산자로 배열을 처음 생성하면 배열 항목은 기본값으로 초기화
// 기본 타입 : 0
// 참조 타입 : null

// 새로운 값으로 변경
변수[인덱스] = 값;
```



##### 배열 길이(.length)

- 배열에 저장할 수 있는 항목 수 의미

```
배열변수.length;
```

