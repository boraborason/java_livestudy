# 목표

자바의 인터페이스에 대해 학습하세요.

# 학습할 것 (필수)

- 인터페이스 정의하는 방법
- 인터페이스 구현하는 방법
- 인터페이스 레퍼런스를 통해 구현체를 사용하는 방법
- 인터페이스 상속
- 인터페이스의 기본 메소드 (Default Method), 자바 8
- 인터페이스의 static 메소드, 자바 8
- 인터페이스의 private 메소드, 자바 9

## 인터페이스 정의하는 방법

**인터페이스란?**

오직 추상메서드와 상수만을 멤버로 가질 수 있는 클래스이다.

구현된 것은 아무것도 없는 밑그림, 설계도. 



**작성방법**

- class대신 interface라는 키워드를 사용하다.
- 접근제어자로 public, default를 사용할 수 있다.

```java
interface 인터페이스이름 (){
	public static final 타입 상수이름 = 값;
	public abstract 메서드이름(매개변수목록);
}
```

**인터페이스 멤버들의 제약사항**

모든 멤버변수는 `public static final` 이어야 하며 생략가능

모든 메서드는 `public abstract` 이어야 하며 생략가능

`static`메서드, `defualt`메서드는 제외(JDK1.8부터 변경)



**인터페이스 vs 추상클래스**

- 추상클래스 :  부분적으로 완성된 "미완성 설계도"
- 인터페이스 : 구현된 것이 하나도 없이 밑그림만 있는 "기본 설계도"



## 인터페이스 구현하는 방법

구현된 것이 아무것도 없는 밑그림인 인터페이스의 추상메서드를 구현한 클래스를 구현클래스라고 한다.

구현 클래스 - 구현 클래스는 클래스 선언부에 **implements** 키워드를 추가하고 인터페이스 명을 명시해야한다.

```java
public class 구현클래스명 implements 인터페이스명(){
	@Override
    //인터페이스에 선언된 추상메서드 구현
}
```



**구현시 주의점**

- 인터페이스의 모든 메서드는 `public`이기 때문에 더 낮은 접근 제한자 작성불가

- 인터페이스의 모든 메서드를 구현클래스에서 작성 하지 않았다면 구현클래스는 자동으로 추상 클래스가 되기 때문에 `abstract`추가 해야함

  

## 인터페이스 레퍼런스를 통해 구현체를 사용하는 방법

인터페이스 타입의 reference variable을 선언할 수 있다. (인터페이스를 구현하는 클래스만 가능)

```java
interface Vehicle {
    void move();
}

class car implements Vehicle {
    @Override
    public void move(){
        System.out.println("앞으로 전진");
    }
    
    public void method1(){
        System.out.println("method1");
    }
}

static public void main(String[] args){
    Vehicle car = new car(); //인터페이스 타입 레퍼런스변수 선언!
    
    car.move();
    //car.method1(); 불가
   						 /*인스턴스 레퍼런스는 해당 인터페이스를 구현한 클래스 인스턴스를 가리킬 수 있고 																해당 인터페이스에 선언된 메서드만 호출 할 수 있다.*/
}
```



구현한 클래스의 레퍼런스는 인터페이스와 본인이 가지고있는 메서드 둘다 호출가능





## 인터페이스 상속

인터페이스는 인터페이스로부터만 상속 받을 수있으며 

자바에서 다중상속은 불가능하지만, 인터페이스는 예외로 다중 상속이 가능하다.

```java
public class 구현클래스명 implements 인터페이스A, 인터페이스B {

	//인터페이스 A에 선언된 추상 메소드의 실체 메소드 선언

	//인터페이스 B에 선언된 추상 메소드의 실체 메소드 선언

}
```





-클래스에서 클래스 상속받을 때 -> extends

-인터페이스에서 인터페이스를 상속받을 때 -> extends

-클래스에서 인터페이스를 상속받을 때 -> implements

## 인터페이스의 Default메서드 와 Static 메서드(자바8)



**바뀐점**

자바8 버전 이상부터는 인터페이스에서 `default` 접근 제어자를 사용하여 **인터페이스 내에서 직접 메서드를 구현** 할수 있게 되었다.

구현한 구체 클래스는 오버라이딩없이 이 default 메서드를 사용할 수 있고, 물론 오버라이딩 하여 재정의 할 수 있다.



**이유**

인터페이스는 라이브러리나 프레임워크에서 매우 자주 사용되는데 라이브러리를 업데이트할 때 인터페이스에 추가된 기능이 있다면 이를 구현한 클래스 역시 추가해주어야 한다. 

하지만 이 라이브러리를 사용하는 사용자가 해당 인터페이스를 구현한 클래스가 있다면 이를 구현하지 않아 컴파일 에러가 발생할 것이다. 이러한 심각한 불편함을 해소하기 위해 `default` 라는 키워드를 만들었다고 한다.

```JAVA
public interface Calculator { 
    
    default int plus(int a, int b){ //default메서드
        return a + b; } 
    
    static int minus(int a, int b){ //static메서드
        return a - b; } 
}
```

```java

public class CalculatorImpl implements Calculator {
                                     
}

```

```java
public class InterfaceEx { 
	public static void main(String[] args) {
	
        Calculator cal = new CalculatorImpl();

	int resultPlus = cal.Plus(3, 9); 
		System.out.println("dafault method 호출 결과 : " + resultPlus); 
	
	int resultMinus = Calculator.minus(9, 3); 		
        System.out.println("static method 호출 결과 : " + resultMinus);
	}
}
```



- interface의 **default** 메소드

\- interface에서도 메소드 구현이 가능하다.

\- 참조 변수로 함수를 호출할 수 있다.

\- implements한 클래스에서 재정의가 가능하다.



- interface의 **static** 메소드 

\- interface에서 메소드 구현이 가능하다.

\- 반드시 클래스 명으로 메소드를 호출해야 한다.

\- 재정의 불가능!

## 인터페이스의 private 메소드, 자바 9

java9 에서는 추가로  **private method** 와 **private static method** 가 추가되었다.

구현부가 존재하며 private 접근 제어자의 특성으로 상속과 구현에 반영안된다.

```java
public interface Animal{

    static void showAnimal(){
        showCat();
    }

    private static void showCat(){
        System.out.println("고양이");
    }
   

}

public static void main(String[] args) {

        Animal.cat(); //고양이
}
```



