### Scanner 클래스의 특징

1. **기본적인 데이터 타입들을 Scanner 의 메소드를 사용하여 입력받을 수 있다.**

   예로 들어 100을 입력하고자 할 때, String(문자열)로 입력받고 싶으면 next() 나 nextLine() 을, int(정수)로 입력받고 싶다면 nextInt() 를 사용하여 입력받으면 알아서 해당 타입으로 입력된다.

   

2. **Scanner 을 사용할 시 util 패키지를 경로의 Scanner 클래스를 호출해야 한다.**

   자바에서 쓰이는 대부분의 클래스는 lang 패키지가 아니라면 import 을 통해 호출해주어야 한다.
   Scanner 의 경우는 java.util 패키지에 있다.

   

   

3. **공백(띄어쓰기) 또는 개행(줄 바꿈)을 기준으로 읽는다.**

   Scanner 의 입력 메소드들은 대부분 공백과 개행(' ', '\t', '\r', '\n' 등등..)을 기준으로 읽는다. 이 덕분에 사용자의 편의에 따라 쉽게 입력을 받을 수 있다.



### Scanner 사용

1. **import 문**

```java
import java.util.Scanner
```

2. **Scanner 객체 생성**

```java
// 클래스_이름 객체_ = new 클래스_이름();
// 대체로 Scanner 의 경우 객체이름은 in, input, sc, scan 이렇게 4가지
Scanner in = new Scanner(System.in); // Scanner 객체 생성
```

3. **메소드를 이용하여 입력하기**

| in.nextByte()    | byte 형 입력 및 리턴                                    |
| ---------------- | ------------------------------------------------------- |
| in.nextShort()   | short 형 입력 및 리턴                                   |
| in.nextInt()     | int 형 입력 및 리턴                                     |
| in.next Long()   | long 형 입력 및 리턴                                    |
|                  |                                                         |
| in.nextFloat()   | float 형 입력 및 리턴                                   |
| in.nextDouble()  | double형 입력 및 리턴                                   |
|                  |                                                         |
| in.nextBoolean() | boolean 형 입력 및 리턴                                 |
|                  |                                                         |
| in.next()        | String 형 입력 및 리턴 (공백을 기준으로 한 단어를 읽음) |
| in.nextLine()    | Sting 형 입력 및 리턴 (개행을 기준으로 한 줄을 읽음)    |

```java
import java.util.Scanner;	// Scanner 클래스 호출
 
public class Main {
	public static void main(String[] args) {
 
		Scanner in = new Scanner(System.in);	// Scanner 객체 생성
 
		byte a = in.nextByte(); 		// byte 형 입력 및 리턴
		short b = in.nextShort(); 		// short 형 입력 및 리턴
		int c = in.nextInt(); 			// int 형 입력 및 리턴
		long d = in.nextLong(); 		// long 형 입력 및 리턴
 
		float e = in.nextFloat(); 		// float 형 입력 및 리턴
		double f = in.nextDouble(); 	// double 형 입력 및 리턴
 
		boolean g = in.nextBoolean(); 	// boolean 형 입력 및 리턴
 
		String h = in.next(); 			// String 형 입력 및 리턴 (공백을 기준으로 한 단어를 읽음)
		String i = in.nextLine(); 		// String 형 입력 및 리턴 (개행을 기준으로 한 줄을 읽음)
	}
 
}
```

- String을 제외하면 next + Type() 으로 조합
- nextInt(), nextDouble(), next(), nextLine() 자주 사용



#### next() 와 nextLine() 의 차이

- next()는 '한 단어' / 공백을 기준으로 문장 한 개만 읽음
- nextLine()dms '한 줄' / 한 줄에 입력된 여러 문

##### next()

```java
// next()
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        
        String str = in.next();
        
        Systme.out.println(str);
    }
}
/* 입출력
* Cat is perfect animal
* Cat
*/
```

- 공백 또는 줄바꿈까지만 읽는다.
- 4개의 문장을 모두 읽기 위해서 next() 4번 사용

```java
// 한줄로 입력
// next()
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        
        String str1 = in.next();
        String str2 = in.next();
        String str3 = in.next();
        String str4 = in.next();
        
        Systme.out.println(str1);
        Systme.out.println(str2);
        Systme.out.println(str3);
        Systme.out.println(str4);
        
    }
}
/* 입출력
* Cat is perfect animal
------------------------
* Cat
* is
* perfect
* animal
*/



// 한 문장당 한 개행씩 입력
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        
        String str1 = in.next();
        String str2 = in.next();
        String str3 = in.next();
        String str4 = in.next();
        
        Systme.out.println(str1);
        Systme.out.println(str2);
        Systme.out.println(str3);
        Systme.out.println(str4);
        
    }
}
/* 입출력
* Cat 
* is 
* perfect 
* animal
------------------------
* Cat
* is
* perfect
* animal
*/
```



##### nextLine()

> 한 줄 안에 공백 유무와 상관없이 개행(줄 바꿈)까지 읽는다.

```java
import java.util.Scanner;

public class Main {
    public static void main(Stringp[] args) {
        Scanner in = new Scanner(System.in);
        
        String str = in.nextLine();
        
        System.out.println(str);
    }
}
/* 입출력
* Cat is perfect animal
-------------------------
* Cat is perfect animal
*/
```



##### next() + nextLine()

```java
import java.util.Scanner;

public class Main {
    public static void main(Stringp[] args) {
        Scanner in = new Scanner(System.in);
        
        String str1 = in.next();
        String str2 = in.nextLine();
        
        System.out.println(str);
    }
}
/* 입출력
* Cat is perfect animal
-------------------------
* Cat
*  is perfect animal
*/
```

- 두 번째 줄에 공백이 포함
  - next()에서 공백을 입력받으면 공백 전 문자까지 읽어서 str1에 저장, 공백은 남아있는다.
  - 그 후 nextLine()을 쓰면 남아있던 공백부터 한 줄을 읽기 때문에 str2에는 공백부터 시작해서 한 줄을 읽는다.

```java
// 문제
import java.util.Scanner;

public class Main {
    public static void main(Stringp[] args) {
        Scanner in = new Scanner(System.in);
        
        String str1 = in.next();	// Cat 저장
        String str2 = in.next();	// is 저장
        String str3 = in.nextLine();	// 남아있던 공백 저장
        String str4 = in.nextLine();	// perfect 저장
        
        System.out.println(str1);
        System.out.println(str2);
        System.out.println(str3);
        System.out.println(str4);
    }
}
/* 입출력
* Cat
* is
* perfect
-------------------------
* Cat
* is
* 
* perfect
*/


// 해결
import java.util.Scanner;

public class Main{
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        
        String str1 = in.next();
        String str2 = in.next();
        in.nextLine();	// 개행이 str3 에 담기지 않도록 개행만 입력
        String str3 = in.nextLine();
        String str4 = in.nextLine();
        
        System.out.println(str1);
        System.out.println(str2);
        System.out.println(str3);
        System.out.println(str4);
    }
}
/* 입출력
* Cat
* is
* perfect
* animal
-----------------------
* Cat
* is
* perfect
* animal
```