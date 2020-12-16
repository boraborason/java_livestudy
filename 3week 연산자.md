## 목표

##### 자바가 제공하는 다양한 연산자를 학습하세요.

## 학습할 것

- ##### 산술 연산자

- ##### 비트 연산자

- ##### 관계 연산자

- ##### 논리 연산자

- ##### instanceof

- ##### assignment(=) operator

- ##### 화살표(->) 연산자

- ##### 3항 연산자

- ##### 연산자 우선 순위

- ##### (optional) Java 13. switch 연산자



### 산술 연산자

산술 연산자에는 사칙연산(+ ,- ,* ,/)와 나머지 연산자가 있다



**사칙연산**

사칙 연산은 이미 알고 있는 것처럼 곱셉(*), 나눗셈(/), 나머지(%) 연산자가 덧셈(+), 뺄셈(-)연산자보다 우선순위가 높으므로 먼저 처리된다. 그리고 나눗셈 연산자에서 피연산자가 정수형일 경우 0으로 나눌 수 없다.

덧셈(+)연산자는 문자열과 문자열을 결합할 때도 사용된다.

사칙 연산시 타입에 따라 저장 할 수 있는 값이 다르므로 값 손실에 주의해야 한다. 



**나머지연산자**

나머지 연산자는 왼쪽의 피연산자를 오른쪽 피연산자로 나누고 난 나머지 값이 결과이다. 나머지 연산의 용도는 다양하지만 주로 짝수, 홀수 또는 배수 검사 등에 사용된다.



**문자의 사칙연산**

사칙연산은 숫자뿐만 아니라 문자도 가능하다. 문자는 실제로 컴퓨터 내부에서 아스키코드나 유니코드로 바뀌어 저장되므로 정수간의 연산과 동일취급 된다.

```java
public class Operator {
 
    public static void main(String[] args) {
        
        char zero = '0';
        char seven= '7';
        
        int number = seven - zero;
        //[1]int number = '7' - '0';
        //[2]int number = 55 - 48;
        //[3]int number = 7;
                
        System.out.println(number);      
        //결과 -> 7
 
    }
 
}
```



문자의 연산이 가능한 이유는 말했듯이 문자형은 컴퓨터 내부에 아스키 코드나 유니코드로 저장된다.

 숫자형식으로 된 문자'7'에서 문자 '0'을 빼면 실제 숫자값을 얻을수가 있다.



### 비트 연산자

비트 연산자는 피 연산자를 2진수로 표현하여 비트단위로 연산한다. 

또한, 비트 단위로 전체 비트를 왼쪽이나 오른쪽으로 이동시킬 때도 사용한다.

![image](https://user-images.githubusercontent.com/57280699/102361586-bcfaf480-3ff6-11eb-822f-7d1b4b5ac647.png)

 **AND 연산자(&)**

AND 연산자는 대응되는 두 비트가 모두 1일 때만 1을 반환하며, 다른 경우는 모두 0을 반환한다.

![image](https://user-images.githubusercontent.com/57280699/102363102-73130e00-3ff8-11eb-9ddc-88b892a2cda7.png)



**OR 연산자(|)**

OR 연산자는 대응되는 두 비트 중 하나라도 1이면 1을 반환하며, 두 비트가 모두 0일 때만 0을 반환한다.

![image](https://user-images.githubusercontent.com/57280699/102364084-6e028e80-3ff9-11eb-8456-5e8c2b531742.png)

**XOR 연산자(^)**

 XOR 연산자는 대응되는 두 비트가 서로 다르면 1을 반환하고, 서로 같으면 0을 반환한다.

![image](https://user-images.githubusercontent.com/57280699/102364132-7bb81400-3ff9-11eb-8951-71208411c353.png)

**NOT 연산자(~)**

NOT 연산자는 해당 비트가 1이면 0을 반환하고, 0이면 1을 반환한다.

![image-20201216235046268](C:\Users\82103\AppData\Roaming\Typora\typora-user-images\image-20201216235046268.png)



### 관계 연산자

비교 연산자라고도 하며 우리가 수학시간에 배웠던 부등호를 생각하면 된다. 

관계연산자의 결과는 true 혹은 false 값인 boolean 자료형으로 반환이 된다.

![image](https://user-images.githubusercontent.com/57280699/102367434-1f56f380-3ffd-11eb-82bf-035d3200cbb8.png)



### 논리 연산자

논리 연산자는 AND(&&), OR(||), NOT(!) 세가지의 연산자가 있으며 관계연산자와 같이 사용 되는 경우가 많다.

논리 연산자 역시 연산의 결과가 true 혹은 false로 반환 된다.

![image](https://user-images.githubusercontent.com/57280699/102367693-67761600-3ffd-11eb-9f02-f56079a9664d.png)

**단락회로 평가**

단락회로 평가는 논리 연산자를 사용할 때 고려해야 할 사항으로 두항 중 앞의 항에서 결과값이 정해지는 경우 뒤의 값이 참인지 거짓인지 평가하지 않는 것을 단락회로평가라고 한다. 

단락회로 평가를 사용하고 싶지 않으면 &&, || 대신 &, | 를 사용하면 된다. 



### instanceof

참조변수가 참조하고 있는 인스턴스의 실제 타입을 알아보기 위해 instanceof 연산자를 사용합니다. 주로 조건문에 사용되며, instanceof의 왼쪽에는 참조변수를 오른쪽에는 타입(클래스명)이 피연산자로 위치합니다. 그리고 연산의 결과로 boolean값인 true, false 중의 하나를 반환 합니다.



instanceof를 이용한 연산결과로 true를 얻었다는 것은 참조변수가 검사한 타입으로 형변환이 가능하다는 것을 뜻합니다.

주로 상속 관계에서 부모객체인지 자식객체인지 확인하는데 사용한다.

```java
class A{ } 
class B extends A{ }


public class InstanceofExam { public static void main(String[] args) {4
    A a = new A(); 
    B b = new B(); 
                                                                      
    //객체 a는 자기 자신의 객체이기 때문에 형변환 가능. 
    System.out.println(a instanceof A); //true 출력
                                                                       
   	//객체 b는 A의 자식객체이기 때문에 A로 형변환 가능. 
    System.out.println(b instanceof A); //true 출력 
                                                                      
   //객체 a는 B의 부모객체이기때문에 형변환 불가능. 
    System.out.println(a instanceof B); //false 출력 
    
   //객체 b는 자기 자신의 객체이기때문에 형변환 가능. 
    System.out.println(b instanceof B); //true 출력 
                                                                      
	}
}
```



### assignment(=) operator

대입 연산자는 변수에 값을 대입할 때 사용하는 연산자이며, 피연산자들의 결합 방향은 오른쪽에서 왼쪽이다.

![image](https://user-images.githubusercontent.com/57280699/102371544-9ee6c180-4001-11eb-939f-4ddaf8498870.png)



### 화살표(->) 연산자

자바에서는 화살표(->) 기호를 사용하여 람다 표현식을 작성할 수 있다.

**람다 표현식(lambda expression)이란?**     람다 표현식이란 간단히 말해 메소드를 하나의 식으로 표현한 것

실제로는 이름없는 클래스와 이름없는 메소드를 만드는 코드

```java
int min(int x, int y) {		//메서드
    return x < y ? x : y;
}
 
(x, y) -> x < y ? x : y; 	//람다 표현식
```

람다 표현식을 사용하면, 기존의 불필요한 코드를 줄여주고, 작성된 코드의 가독성을 높여준다.

Java SE 8부터는 이러한 람다 표현식을 사용하여 자바에서도 함수형 프로그래밍을 할 수 있게 되었다.



**람다의 표현식**

\1. 람다는 매개변수 화살표(->) 함수몸체로 이용하여 사용 할 수 있습니다.    		**(매개변수) -> {함수몸체}**

\2. 매개변수가 하나일 경우 매개변수를 생략 할 수 있습니다.						 		  **() -> {함수몸체)**

\3. 함수몸체가 단일 실행문이면 괄호{}를 생략 할 수 있습니다.					 		   **(매개변수) -> 함수몸체**

\4. 함수몸체가 return문으로만 구성되어 있는 경우 괄호{}를 생략 할 수 없습니다.	**(매개변수) -> {return 0;}**



##### 예제

```java
public interface Good{ //인터페이스
	public void doSome();
}
```

보통 기존 자바에서는 인터페이스를 이용해 다형성을 제공하기 위해 인터페이스를 만들고 class를 작성 뒤 인터페이스 타입의 참조변수변수에 작성한  클래스의 객체를 생성하여 사용했었다.

또는 main에서 아래와 같이 **익명객체**를 만들어 사용

```java
public Main { 
	public static void main(String[] args) {
		Good good = new Good() { 
			public void dosome(){
				System.out.println("good");
			}
		};
		good.doSome();
	}
}
```

 하지만 good을 구현한 객체가 자주 사용되어야 한다면 위 코드를 계속 반복 해야한다.

##### 람다식사용

```java
public Main { 
	public static void main(String[] args) {
		Good good = () -> System.out.println("good");
        good.doSome();
	}
}
```

인터페이스 참조변수에 람다식을 대입하여 사용하면 아주 간결하게 표현 가능



추가 참고 https://galid1.tistory.com/509

### 3항 연산자

조건식 ? 피연산자1 : 피연산자2

- 조건식의 연산결과가 true 이면, 결과는 피연산자 1이고, 조건식의 연산결과가 false 이면 결과는 피연산자2

```java
int b1 = (5>4) ? 50 : 40;
        //조건식이 true이므로 b1은 50이 된다. 
```



### 연산자 우선 순위

1. 산술 > 비교 > 대입

2. 단항 > 이항 > 삼항

   

   -단항 연산자와 대입 연산자를 제외한 모든 연산의 진행방향은 왼쪽에서 오른쪽이다.

### (optional) Java 13. switch 연산자

Java12부터 switch 연산자가 추가 되었다. (기존에 switch문 변경x !!  switch 연산자가 추가 됨)

**화살표 연산자**

`case:` 대신 `case->` 를 사용할수있다.



**yield**

yield 기능을 이용해 값을 리턴 할 수 있다.

yield는 예약어이지만 변수명으로 사용가능하다. int yield = 3; 