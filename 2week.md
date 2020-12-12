## 목표

##### 자바의 프리미티브 타입, 변수 그리고 배열을 사용하는 방법을 익힙니다.

## 학습할 것

- ##### 프리미티브 타입 종류와 값의 범위 그리고 기본 값

- ##### 프리미티브 타입과 레퍼런스 타입

- ##### 리터럴

- ##### 변수 선언 및 초기화하는 방법

- ##### 변수의 스코프와 라이프타임

- ##### 타입 변환, 캐스팅 그리고 타입 프로모션

- ##### 1차 및 2차 배열 선언하기

- ##### 타입 추론, var

  

### 프리미티브 타입과 레퍼런스 타입

자바의 타입은 크게 **프리미티브 타입**과 **레퍼런스 타입**으로 나뉜다.

각각의 타입으로 변수를 선언시 메모리에 공간이 할당 되는데 메모리에 직접 데이터를 담으면 프리미티브타입, 다른곳을 참조하는 주소값을 담으면 레퍼런스 타입.



### 프리미티브 타입 종류와 값의 범위 그리고 기본 값

![image](https://user-images.githubusercontent.com/57280699/101986126-5c567980-3ccf-11eb-9c99-3f7aaf837243.png)



### 리터럴

리터럴은 단지 그 자체로의 값을 의미하는 것으로 int a = 1; 에서 값1을 의미한다.



### 변수 선언 및 초기화하는 방법

변수를 사용하려면 먼저 변수를 선언해야 하는데 

![image](https://user-images.githubusercontent.com/57280699/101989678-8024ba00-3ce5-11eb-8c77-492c2995b806.png)

변수를 선언하면 메모리의 빈공간에 변수타입에 알맞은 크기의 저장 공간이 확보되고 이 저장공간은 **변수이름**을 통해서 사용 할 수 있다. 

메모리는 여러 프로그램이 공유하는 자원이므로 다른 프로그램에 의해 '**알수없는 값이**' 저장 되어 있을 수 있으므로 반드시 초기화 해야한다.



### 변수의 스코프와 라이프타임

변수의 스코프란 변수에 접근하거나 접근 할 수 있는 유효범위로 일반적으로는 변수가 선언된 블록 내에서만 접근 할 수 있다.

변수의 라이프 타임이란 변수가 **메모리에서 살아있는 기간**을 말한다.

변수의 선언위치에 따라 변수는 **클래스변수**, **인스턴스변수**, **지역변수** 가 있다.

```java
public class test { 

	int iv; 	// 인스턴스 변수
	static int cv; // 클래스 변수 
	
	public void method() {
    int lv;		 // 지역 변수 
    
    } 
}
```



![image](https://user-images.githubusercontent.com/57280699/101991362-99caff00-3cef-11eb-84f3-b1d9b0362b2d.png)



#### 인스턴스 변수

 인스턴스 변수는 인스턴스가 생성될 때 생성된다. 때문에 인스턴스 변수의 값을 읽어오거나 저장하려면 인스턴스를 먼저 생성해야 하며 인스턴스 별로 다른 값을 가질 수 있으므로, 각각의 인스턴스마다 고유의 값을 가져야할 때는 인스턴스 변수로 선언한다.



#### 클래스 변수

 클래스 변수는 인스턴스 변수에 static이 붙은 변수로 인스턴스 변수는 각각 고유한 값을 가지지만 클래스 변수는 모든 인스턴스가 같은 저장 공간을 가리킨다.      한 클래스의 모든 인스턴스들이 공통적인 값을 가져야할 때 클래스 변수로 한다. 클래스가 로딩될 때 생성되어(그러므로 메모리에 딱 한번 올라감) 종료 될 때 까지 유지되는 클래스 변수는 public 을 붙이면 같은 프로그램 내에서 어디서든 접근할 수 있는 전역 변수가 되고 또 인스턴스 변수와 다르게 인스턴스를 생성하지 않고 클래스이름.클래스변수명 을 통해서 접근할 수 있다.



#### 지역 변수

 메서드 내에서 선언되며 메서드 내에서만 사용할 수 있는 변수이다. 메서드가 실행될 때 메모리를 할당 받으며 메서드가 끝나면 소멸된다.



### 1차 및 2차 배열 선언하기

**배열**(Array)이란 선형 자료구조(Data Structure)중 하나로, **동일한 타입**의 연관된 데이터를 메모리에 **연속적으로 저장**하여 하나의 변수에 묶어서 관리하기 위한 자료 구조이다. 





### 타입 추론, var