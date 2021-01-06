# 목표

자바의 패키지에 대해 학습하세요.

# 학습할 것 (필수)

- package 키워드
- import 키워드
- 클래스패스
- CLASSPATH 환경변수
- -classpath 옵션
- 접근지시자

## package 키워드

패키지란 클래스의 묶음으로 클래스끼리 단위로 묶어 놓음으로써 클래스를 효율적으로 관리할 수 있다.

**패키지** **선언**

```java
package 패키지명;
```



## import 키워드

코드를 작성할 때 다른 패키지의 클래스를 사용하려면 패키지명이 포함된 클래스의 이름을 사용해야 한다. 하지만 매번 패키지명을 붙여서 작성해야하는 것은 매우 불편하다.

클래스 코드를 작성하기 전에 한번만**import**문을 선언하면 소스코드에 사용되는 클래스의 패키지명은 생략할 수 있다. 



**import문 선언**

```java
import 패지키명.크래스명;
또는
import 패키지명.*
```

지금까지 System과 String 같은 java.lang패키지의 클래스들을 패키지명 없이 쓸 수 있었던 이유는 모든 소스파일에 

​	`import java.lang.*;`

가 선언되어 있었기 때문이다.



**static import문**

static import문을 사용하면 static멤버를 호출할 때 클래스 이름을 생략 할 수 있다.

특정 클래스의 static멤버를 사용할 때 편리하다. 

```java
import static java.lang.Math.random;
import static java.lang.System.out;

//System.out.println(Math.random());

  out.println(random());

```



## 클래스패스

자바에서 사용하는 path로 os환경에서 필요한 path와 비슷한 개념이지만 자바의 class 파일들을 위한 환경변수이다.

**모든 컴파일된 클래스와 자원들은 classpath하단에 생성되는데 .class 파일에 포함된 명령을 실행하려면, 먼저 이 파일을 찾을 수 있어야 한다.** 

컴파일된 .class 파일을 실행하기 위해 JVM이 시작될 때 JVM의 클래스 로더는 classpath를 호출하고 환경 변수에 설정되어 있는 디렉토리가 호출되면 그 디렉토리에 있는 클래스들을 먼저 JVM에 로드한다. 



## CLASSPATH 환경변수

**classPath를 사용하는 첫번째 방법은 classpath환경변수를 사용하는 방법이다.**

CLASSPATH 환경 변수에는 필수 클래스들이 위치한 디렉토리를 등록하도록 해야한다.

![image](https://user-images.githubusercontent.com/57280699/103733783-dc050900-502d-11eb-8972-9aebf06cc453.png)

CLASSPATH속성이 있는경우 ; 구분후 경로를 설정해 주면된다.



## -classpath 옵션

 **classPath를 사용하는 두번째 방법은 -classpath 옵션 사용하는 방법이다.**

.java 파일을 컴파일 하기전에 해당 파일이 필요로 하는 클래스들을 찾기 위하 사용하는 옵션으로 

-classpath뒤에 Drirectory  Path를 작성하면 해당 Directory를 탐색하게 된다.

`jacac -classpath C:\java/ex ex.java`



## 접근지시자

접근제어자는 멤버 또는 클래스에 사용되어 해당하는 멤버 또는 클래스를 외부에서 접근하지 못하도록 제한하는 역할을 한다.



**접근 제어자가 사용될 수 있는 곳 - 클래스, 멤버변수, 메서드, 생성자**

private 같은 클래스 내에서만 접근가능

default 같은 패키지

protected 같은 패키지, 다른 패키지의 자손클래스에서 접근가능

public 접근 제한이 전혀없음



**접근제어자를 사용하는 이유**

-외부로 부터 데이터 보호

-외부에는 불필요한 내부적으로 사용되는 부분을 감추기 위해서