
# 상속

## 상속 예제1

```java title=ExtendsTest09

/*
 * 클래스 상속 문법 특징
 * 1. class 자손 클래스 extends 부모 클래스 { } 로 상속 받는다.
 * 2. 클래스 상속은 하나의 부모로부터 단일 상속만 가능하다.
 * 3. 명시적인 상속을 받지 않으면 자바의 모든 클래스는 묵시적으로 자바 최상위 부모 클래스 Object를 상속 받는다.
 * 
 */

class Parent09 {
	public void p09() {
		System.out.println("부모 클래스에서 정의된 p09() 메소드");
	}
	
}


class Child09 extends Parent09 {		// class 자손클래스 extends 부모클래스 { }. 즉, extends 키워드로 부모 클래스 상속
	public void c09() {
		System.out.println("자손 클래스에서 정의된 c09() 메소드");
	}
}


public class ExtendsTest09 {

	public static void main(String[] args) {
		Child09 ch = new Child09();
		ch.p09();	// 부모클래스로부터 상속 받아서 호출
		ch.c09();	// 자식클래스에서 정의된 메서드 호출
		System.out.println();
		
		
		Parent09 p = new Parent09();
		p.p09();
//		p.c09();	// Error. 부모입장에서 자손에서 정의한 메소드는 호출이 불가능하다.
		
	}

}

```



## 상속 예제2

```java title=ExtendsTest10

// 상속코드에서 코드의 재활용
class Point2D extends Object {	// extends Object는 묵시적 생략 가능함
	private int x;
	private int y;
	
	// 매개변수(전달인자)가 없는 기본 생성자 묵시적 제공
	// 
	
	
	public int getX() {
		return x;
	}
	public void setX(int x) {
		this.x = x;
	}
	public int getY() {
		return y;
	}
	public void setY(int y) {
		this.y = y;
	}
	
} // 부모 클래스 Point2D


class Point3D extends Point2D {
	private int z;

	
	public int getZ() {
		return z;
	}

	public void setZ(int z) {
		this.z = z;
	}
	
} // 자손 클래스 Point3D


public class ExtendsTest10 {
	public static void main(String[] args) {
		Point3D pt = new Point3D();
		
		pt.setX(100); pt.setY(200); // 상속받아서 호출
		pt.setZ(300);
		
		System.out.println(String.format("x좌표값 : %d, y좌표값 : %d, z좌표값 : %d", pt.getX(), pt.getY(), pt.getZ()));
	}
	
}


```



***



# 상속 관련 문제

## 문제 1

 - 접근 권한이 다음과 같이 지정되어 있을 경우, 문제가 발생하는 문장 찾기
   ( [] 안에 숫자가 기술되어 있다. [] 몇 번 문장이 잘못된 것인지 번호를 기술)


```java title=Ex16_2.java
package 문제;

/*
 * 16장. 상속.pdf 강의교안의 20쪽 1번 문제
 */

class Parent {
	private int a;
	int b;
	protected int c;
	public int d;
	
} // Parent 부모 클래스

class Child extends Parent {
	public Child(int a, int b, int c, int d) {
//		this.a = a; // [1]이 잘못됨. a 멤버변수가 private 접근제어자로 정의되어 있어서 외부(자손) 클래스에스 접근하지 못함
		this.b = b; // [2]
		this.c = c; // [3]
		this.d = d; // [4]
	}
	
	void func() {
//		System.out.println(a);	// [5]번 잘못됨
		System.out.println(b); // [6]번
		System.out.println(c); // [7]번
		System.out.println(d); // [8]번
	}
	
} // child 자손 클래스

public class Ex16_02 {

	public static void main(String[] args) {
		Child one = new Child(1, 2, 3, 4);
		one.func();
	}

}

```



## 문제 2

- 다음과 같은 상속 구조에서 생성자의 호출 순서를 알아보기 위한 문제입니다.
- 실행 결과를 유추해봅시다.


```java title=Ex16_03
package 문제;

/*
 * 16장.상속.pdf 강의교안의 21쪽 2번 문제
 */

class Parent3 { 
	protected int a, b, c; 
	
	public Parent3( ){
		super(); // 부모 Object 클래스 기본 생성자를 호출
		System.out.println("Parnet3() 생성자 호출"); 
	} 
	
	public Parent3(int a, int b, int c){ 
		this.a = a; this.b = b; this.c = c; 
		System.out.println("Parnet3() 오버로딩 된 생성자 호출"); 
	} 
}


class Child3 extends Parent3 { 
	public Child3( ){ 
		// super()이 생략됨
		System.out.println("Child3() 생성자 호출"); 
	} 
	
	public Child3(int a, int b, int c){ 
		super(a, b, c); 
		System.out.println("Child3() 오버로딩 된 생성자 호출"); 
	}
	
	public String print() {
//		String result = String.format("a : %d, b : %d, c : %d", a, b, c);
		String result = "a : " + a + ", b : " + b +  ", c : " + c;
		
		return result;
	}
} 


public class Ex16_03 {

	public static void main(String[] args) {
		new Child3( ); 
		Child3 three = new Child3(100, 200, 300);
		
		/*
		 * 문제) 메소드 리턴 타입이 String 형으로 된 print() 메소드를 정의한 
		 * 다음 a, b, c 멤버 변수 정수값을 문자열변수 result에 저장한 다음 반환해서 출력하는 코드를 만들어보자.
		 */
		
		String result = three.print();
		System.out.println(result);
	}

}


```



## 문제 3

- 동물(Animal)과 개(Dog)와 사람(Human)이란 클래스를 서로 상속이란 개념을 도입해서 설계
- 슈퍼클래스는 동물(Animal)을 두고, 멤버변수로 무슨 종인지 구분하기 위한 kind, 다리의 개수를 저장하기 위한 leg 선언
- 멤버 메소드는 getKind()와 walk()를 선언, getKind는 어떤 동물인지를 알려주는 메소드, walk는 어떻게 걷는지 알려주는 메소드
- 아래의 UML 클래스 다이어그램대로 설계하여, 각 메소드에서 is~else 분기문을 사용하세요.


![[Pasted image 20240822235152.png|450]]


```java title=
package 문제;

/*
 * 16장.상속.pdf 강의교안의 23쪽 3번 문제
 */

class Animal {
	protected String kind;		// 동물종이 저장될 변수
	protected int leg;			// 다리 개수
	
	// 기본 생성자
	Animal() {}
	
	// 생성자 오버로딩
	Animal(String kind, int leg) {
		this.kind = kind;
		this.leg = leg;
	}
	
	public void getKind() {
		String division = null;
		
		if(leg == 4) {
			division = "동물";
		}
		
		if(leg == 2) {
			division = "사람";
		}
		
		System.out.println(kind + division + "이다.");
		
		
		/* 강사님코드 */
		if(kind.equals("소녀")) {	// 문자열 값 같다 비교는 equals() 메소드를 사용한다.
			System.out.println(kind + "는 사람이다.");
		}else {
			System.out.println(kind + "는 동물이다.");
		}
	}
	
	public void walk() {
		String division = null;
		
		if(leg == 4) {
			division = "동물";
		}
		
		if(leg == 2) {
			division = "사람";
		}
		
		System.out.println(division + "은 " + leg + "발로 걷는다.");
		
		
		/* 강사님 코드 */
		if(leg == 2) {
			System.out.println("사람은 " + leg + "발로 걷는다.");
		}else {
			System.out.println("동물은 " + leg + "발로 걷는다.");
		}
	}
	
}

// 첫번째 자손 클래스 Human 정의
class Human extends Animal {
	Human() {}
	Human(String kind, int leg) {
		super(kind, leg);	// 부모클래스 오버로딩 된 생성자 호출
	}
}


// 두번째 자손 클래스 Dog
class Dog extends Animal {
	Dog() {}
	Dog(String kind, int leg) {
		super(kind, leg);
	}
}


public class Ex16_04 {
	public static void main(String[] args) {
		Dog dog = new Dog("강아지", 4);
		Human human = new Human("소녀", 2);
		
		dog.getKind();
		dog.walk();
		human.getKind();
		human.walk();
		
	}

}

```



## 문제 4

- 다음과 같은 상속 관계를 갖는 두 개의 클래스를 설계하시오.
- 설계된 클래스로 다음과 같이 객체 생성하여 메소드를 호출하면 실행결과와 같이 출력되도록 합시다.

```java
class Ex16_05 {
	public static void main(String[] args) {
		DicaPhone dp = new DicaPhone("갤럭시", "010", "1024");
		dp.prnDicaPhone();
	}
	// 실행결과 : 모델명 : 갤럭시  번호 : 010  화소수 : 1024
}
```

![[Pasted image 20240823000302.png|400]]


```java title=Ex16_05
package 문제;

/*
 * 16장.상속.pdf 강의교안의 26쪽 4번 문제
 */

class HandPhone {
	protected String model;
	protected String number;
	
	public HandPhone() {}
	
	public HandPhone(String model, String number) {
		this.model = model;
		this.number = number;
	}
	
	public String getModel() {
		return model;
	}
	
	public String getNumber() {
		return number;
	}
}


class DicaPhone extends HandPhone {
	protected String pixel;
	
	public DicaPhone() {}
	
	public DicaPhone(String model, String number, String pixel) {
		super(model, number);
		this.pixel = pixel;
	}
	
	public void prnDicaPhone() {
		boolean isExistVal = model == null && number == null && pixel == null;
		if(isExistVal) {
			System.out.println("값 전부 입력 후 사용");
			return;
		}
		
		System.out.println("모델명 : " + model + "  번호 : " + number + "  화소수 : " + pixel);
	}
	
}


public class Ex16_05 {
	
	public static void main(String[] args) {
		DicaPhone dp = new DicaPhone("갤럭시", "010", "1024");
		
		dp.prnDicaPhone();
	}

}


```



## 문제 5

- 다음 프로그램의 실행 결과를 유추하시오.


```java title=Ex16_06 error=18,24
package 문제;

/*
 * 부모클래스 생성자가 오버로딩이 되면, 매개변수가 없는 기본생성자를 묵시적으로 제공하지 않는다.
 * 이런 경우에서 부모의 기본생성자를 호출하여 에러 발생
 */
/*
 * 16장.상속.pdf 강의교안의 28쪽 5번 문제
 */

class TestSuper extends Object {
	TestSuper(int i) { 
		//super();	가 생략되었다. 부모의 Object 클래스 기본 생성자를 호출
	}
}


class TestSub extends TestSuper { }


public class Ex16_06 {

	public static void main(String[] args) {
		new TestSub();
	}

}

```



## 문제 6

- 다음 프로그램의 실행 결과를 유추하시오.


```java title=Ex16_07
package 문제;

/*
 * 16장.상속.pdf 강의교안의 29쪽 6번 문제
 * 
 * new 클래스명();에 의해서 호출되는 생성자 관련 소스
 */

class Base extends Object {
	Base() {
		super();
		System.out.print("Base");
	}
	
} // Base 부모클래스

class Alpha extends Base {
	// 묵시적 기본 생성자 생략
}


public class Ex16_07 {
	public static void main(String[] args) {
		new Alpha();
		new Base();
		
	}
	
}

```



## 문제 8

- 다음 프로그램의 실행 결과를 유추하시오.


```java title=Ex16_09
package 문제;

/*
 * 16장.상속.pdf 강의교안의 31쪽 8번 문제
 */

class A {
	public A() {
		System.out.println("hello from a");
	}
}

class B extends A {
	public B() {
		System.out.println("hello from b");
//		super();	// Error, 부모 생성자는 자식 생성자의 첫 줄에 들어가야하기 때문에 
	}
}


public class Ex16_09 {

	public static void main(String[] args) {
		new B();
	}

}

```



## 문제 9

- 다음 프로그램의 실행 결과를 유추하시오.


```java title=SubEx09
package 문제;

/*
* 16장.상속.pdf 강의교안의 32쪽 9번 문제
* 상속관계에서 메소드 오버라이딩과 super.메소드()에 관한 소스
*/

class A2 {
	public String toString() { return "4"; }
} // A2 class


class B2 extends A2 {
	public String toString() { return super.toString() + "3"; }	// 메소드 오버라이딩	
} // B2 class


public class SubEx09 {

	public static void main(String[] args) {
		
		System.out.println(new B2());	// new B2().toString().	즉, toString() 메소드가 생략됨
	}

}
```



***



# 다형성
![[2_JAVA/0_용어#다형성(Polymorphism)]]


## 필드 다형성 예제

```java title=Tire
package ch07.sec08.exam01;

public class Tire {
	// 메소드 선언 
	public void roll() {
		System.out.println("회전합니다.");
	}
}

```

```java title=HankookTire
package ch07.sec08.exam01;

public class HankookTire extends Tire {
	// 메소드 재정의 (오버라이딩)
	@Override
	public void roll() {
		System.out.println("한국 타이어가 회전합니다.");
	}
}

```

```java title=KumhoTire
package ch07.sec08.exam01;

public class KumhoTire extends Tire {
	// 메소드 재정의
	@Override
	public void roll() {
		System.out.println("금호 타이거가 회전합니다.");
	}
}

```

```java title=Car
package ch07.sec08.exam01;

public class Car {
	// 필드 선언
	public Tire tire;
	
	// 메소드 선언
	public void run() {
		// tire 필드에 대입된 객체의 roll() 메소드 호출
		tire.roll();
	}
}

```

```java title=CarExample
package ch07.sec08.exam01;

public class CarExample {
	public static void main(String[] args) {
		// Car 객체 생성
		Car myCar = new Car();
		
		// Tire 객체 장착
		myCar.tire = new Tire();
		myCar.run();
		
		// HankookTire 객체 장착
		myCar.tire = new HankookTire();
		myCar.run();
		
		// KumhoTire 객체 저장
		myCar.tire = new KumhoTire();
		myCar.run();
		
		
	}
}

```

> [!success] 실행 결과
> 회전합니다.
> 한국 타이어가 회전합니다.
> 금호 타이어가 회전합니다.



## 매개변수 다형성 예제

```java title=Vehicle
package ch07.sec08.exam02;

public class Vehicle {
	// 메소드 선언
	public void run() {
		System.out.println("차량이 달립니다.");
	}
}

```

```java title=Bus
package ch07.sec08.exam02;

public class Bus extends Vehicle {
	// 메소드 재정의(오버라이딩)
	@Override
	public void run() {
		System.out.println("버스가 달립니다.");
	}
	
}

```

```java title=Taxi
package ch07.sec08.exam02;

public class Taxi extends Vehicle {
	// 메소드 재정의(오버라이딩)
	@Override
	public void run() {
		System.out.println("택시가 달립니다.");
	}
}

```

```java title=Driver
package ch07.sec08.exam02;

public class Driver {
	// 메소드 선언(클래스 타입의 매개변수를 가지고 있음)
	public void drive(Vehicle vehicle) {
		vehicle.run();
	}
}

```

```java title=DriverExample
package ch07.sec08.exam02;

public class DriverExample {

	public static void main(String[] args) {
		// Driver 객체 생성
		Driver driver = new Driver();
		
		// 매개값으로 Bus 객체를 제공하고 driver() 메소드 호출
		Bus bus = new Bus();
		driver.drive(bus);
		
		// 매개값으로 Taxi 객체를 제공하고 driver() 메소드 호출
		Taxi taxi = new Taxi();
		driver.drive(taxi);
		
		
	}

}

```

>[!success] 실행 결과
> 버스가 달립니다.
> 택시가 달립니다.


## 매개변수 다형성 예제 (객체 타입 확인)

```java title=Person
package ch07.sec09;

public class Person {
	// 필드 선언
	public String name;
	
	// 생성자 선언
	public Person(String name) {
		this.name = name;
	}
	
	// 메소드 선언
	public void walk() {
		System.out.println("걷습니다.");
	}
}

```

```java title=Student
package ch07.sec09;

public class Student extends Person {
	// 필드 선언 
	public int studentNo;
	
	// 생성자 선언
	public Student(String name, int studentNo) {
		super(name);
		this.studentNo = studentNo;
	}
	
	// 메소드 선언
	public void study() {
		System.out.println("공부를 합니다.");
	}
}

```

```java title=InstanceofExample
package ch07.sec09;

public class InstanceofExample {
	// main() 메소드에서 바로 호출하기 위해 정적 메소드 선언
	public static void personInfo(Person person) {
		System.out.println("name : " + person.name);
		person.walk();
		
		/* 기존 사용 방식 */
		// person이 참조하는 객체가 Student 타입인지 확인
		if(person instanceof Student) {
			// Student 객체일 경우 강제 타입 변환
			Student student = (Student)person;
			// Student 객체만 가지고 있는 필드 및 메소드 사용
			System.out.println("studentNo : " + student.studentNo);
			student.study();
		}
		
		/* Java 12버전부터 사용 가능 */
		// person이 참조하는 객체가 Student 타입일 경우
		// student 변수에 대입(타입 변환 발생)
		if (person instanceof Student student) {
			System.out.println("studentNo : " + student.studentNo);
			student.study();
		}
	}
	
	
	public static void main(String[] args) {
		// Person 객체를 매개값으로 제공하고 personInfo() 메소드 호출
		Person p1 = new Person("홍길동");
		personInfo(p1);
		
		System.out.println();
		
		// Student 객체를 매개값으로 제공하고 personInfo() 메소드 호출
		Person p2 = new Student("김길동", 10);
		personInfo(p2);
		
	}
	
}

```

>[!success] 실행 결과
> name : 홍길동
> 걷습니다.
> 
> name : 김길동걷습니다.
> studentNo : 10
> 공부를 합니다.
> studentNo : 10
> 공부를 합니다.



***



# Casting
## UpCasting

```java title=UpCast01
package casting;

/*
 * 업캐스팅이란?
 * 1. 상속 관계에서 자손타입 참조변수가 부모타입의 참조변수로 변환하는 것을 말한다. 자손 클래스가 부모 클래스로 형변환이 이루어지는 것을 말한다.
 * 2. 업캐스팅은 자바 컴파일러에 의해서 자동 형변환을 해준다.
 */

class Parent01 extends Object {
	void parentPrn() {
		System.out.println("부모 클래스 메소드 parentPrn()");
	}
}


class Child01 extends Parent01 {
	void childPrn() {
		System.out.println("자식 클래스 메소드 childPrn()");
	}
}


public class UpCast01 {

	public static void main(String[] args) {
		Parent01 p = new Child01();	// 업캐스팅, 자동 형변환
		p.parentPrn();
//		p.childPrn();	// Error.
		
		
	}

}

```



## DownCasting

```java title=DownCast02
package casting;

/*
 * 다운캐스팅이란
 * 1. 다운 캐스팅이란 상속 관계에서 부모타입의 참조변수가 자손타입의 참조변수로 변환하는 것을 말한다. 부모 클래스가 자손 클래스로 형변환 이루어지는 것을 말한다.
 * 2. 참조타입 간의 다운 캐스팅의 전제 조건
 * 	2-1. 사전에 상속 관계를 만들어야 한다.
 *  2-2. 자바 컴파일러에서 자동 형변환을 해주지 않는다. 그러므로 캐스팅(형변환) 연산자를 사용해서 명시적인 다운 캐스팅을 해야한다.
 *  2-3. 사전에 반드시 업캐스팅을 해야한다. 그래야만 다운 캐스팅을 허용한다.
 */

class Parent02 {
	void pr02() {
		System.out.println("부모 클래스 메소드 pr02()");
	}
}


class Child02 extends Parent02 {
	void ch02() {
		System.out.println("자식 클래스 메소드 ch02()");
	}
}


public class DownCast02 {

	public static void main(String[] args) {
		Parent02 p = new Child02();	// 업캐스팅
		p.pr02();
		
		Child02 ch = (Child02)p;		// 명시적인 다운캐스팅
		ch.pr02();						// 상속받아서 호출
		ch.ch02();						// 자식 클래스에서 정의된 메소드 호출
		
	}

}

```



```java title=DownCastFail03 error=26
package casting;

/*
 * 명시적인 캐스팅 연산자인 (Son03)을 사용하지 않아서 발생하는 컴파일 에러 예제이다. 
 */

class Parent03 {
	void p03() {
		System.out.println("부모 클래스 메소드 p03()");
	}
}


class Son03 extends Parent03 {
	void s03() {
		System.out.println("자손 클래스 메소드 s03");
	}
}


public class DownCastFail03 {

	public static void main(String[] args) {
		Parent03 p = new Son03();	// 업캐스팅
		
		Son03 s = p;	// 명시적인 캐스팅 연산자인 (Son03)을 사용하지 않아서 발생하는 컴파일 에러
		
	}

}

```



```java title=DownCastError04 error=27
package casting;

/*
 * 레퍼런스 타입 간의 형변환 중 다운캐스팅은 반드시 사전에 업캐스팅을 하고 다운캐스팅을 해야 하는데 사전에 업캐스팅을 하지 않고 명시적인 다운캐스팅을 하면
 * 정상적인 컴파일은 되지만 실행시 캐스팅 예외 오류가 발생한다. 이 오류가 가장 많이 발생한다.
 */

class Father04 {
	void f04() {
		System.out.println("부모 클래스 메소드 f04()");
	}
}


class Son04 extends Father04 {
	void s04() {
		System.out.println("자손 클래스 메소드 s04()");
	}
}


public class DownCastError04 {

	public static void main(String[] args) {
		Father04 f = new Father04();	// 사전에 업캐스팅을 하지 않고 부모 클래스 객체 f만 생성
		
		Son04 s = (Son04)f;	// 명시적인 다운캐스팅	=> 사전에 업캐스팅을 하지 않고, 
								// 다운캐스팅을 하여 java.lang.ClassCastException: 캐스트 연산 예외 오류가 발생한다.
								// 정상적인 컴파일이 된 바이트코드(.class) 파일을 자바 가상 머신이 java 명령으로 실행 시 예외 오류가 발생한다.
		s.f04();
		s.s04();
		
	}

}

```



## with InstanceOf

```java title=InstanceOf05
package casting;

/*
 * instanceof 는 형변환 유무 판단 연산자이다.
 */

class HandPhone {
	String model; // 폰 모델
	String number; // 폰 번호
	
	public HandPhone() {}

	public HandPhone(String model, String number) {
		this.model = model;
		this.number = number;
	} // 생성자 오버로딩
} // HandPhone class


class DicaPhone extends HandPhone {
	String pixel;	// 화소 수
	
	public DicaPhone() {}
	
	public DicaPhone(String model, String number, String pixel) {
		super(model, number);
		this.pixel = pixel;
	}
	
	public void prnDicaPhone() {
		System.out.println("폰모델 : " + model + ", 폰번호 : " + number + ", 화소 수 : " + pixel);
	}
	
} // DicaPhone 자손 클래스

public class InstanceOf05 {

	public static void main(String[] args) {
		DicaPhone dp = new DicaPhone("갤럭시 24", "010-7777-7777", "1024");
		dp.prnDicaPhone();
		
		if(dp instanceof DicaPhone) { // dp 객체가 DicaPhone 객체 타입인가?
			System.out.println("dp는 DicaPhone이다.");
		}
		if(dp instanceof HandPhone) {	// 업캐스팅이 가능한가?
			HandPhone hp = dp;	// 업캐스팅
			System.out.println("업캐스팅이 가능하다.");
		}
		
		
		HandPhone hp2 = new HandPhone();	// 사전에 업캐스팅 안 함 => 다운캐스팅 허용 안 함
		
		if(hp2 instanceof DicaPhone) {	// hp2가 다운캐스팅이 가능한가? 사전에 업캐스팅을 하지 않아서 불가능(false)
			DicaPhone dp2 = (DicaPhone)hp2;	// 명시적인 다운캐스팅
			System.out.println("다운캐스팅이 가능하다.");
		}else {
			System.out.println("다운캐스팅이 불가능하다.");
		}
		
	}
}
```



## UpCasting With Override

```java title=UpCastOverride06
package casting;

/*
 * 업캐스팅 이후 오버라이딩 한 메소드 호출
 */

class Mother06 {
	void m06() {
		System.out.println("부모 클래스 메소드 m06()");
	}
}


class Son06 extends Mother06 {
	@Override
	void m06() {
		System.out.println("오버라이딩 메소드 m06()");
	}
}


public class UpCastOverride06 {

	public static void main(String[] args) {
		Mother06 m = new Son06();
		m.m06();	// 업캐스팅 후 오버라이딩 한 메소드 호출
	}

}

```



```java title=
package casting;


/*
 * 업캐스팅 이후 오버라이딩 한 메소드 호출에 관한 소스이다.
 */

class Parent09 {
	int x = 100;
	
	void method() {
		System.out.println("부모 클래스에서 정의한 인스턴스 변수 x = " + x);
	}
}


class Son09 extends Parent09 {

	@Override
	void method() {
		System.out.println("오버라이딩 한 메소드");
	}
	
	void test() {
		System.out.println("test");
	}
	
}


public class UPcastOverride09 {

	public static void main(String[] args) {
		Parent09 p = new Son09();
	
		/*
		 * 메소드가 오버라이딩이 된 경우에 업캐스팅 한 p가 실제 호출되는 메소드는 p가 가리키고 있는 객체 타입에 의해서 호출되는 메소드가 결정된다.
		 * 결국 업캐스팅 이후 오버라이딩 한 메소드를 호출한다.
		 */
		p.method();	// 사용빈도가 높다. 중요하다.
		
	}

}

```


## UpCasting & DownCasting

```java title=UpcastDowncast07
package casting;

class Car {
	String color;
	int door;
	
	void drive() {
		System.out.println("차가 드라이브 한다.");
	}
	
	void stop() {
		System.out.println("차가 멈춘다.");
	}
	
} // 부모 Car class


class FireEngine extends Car {
	void water() {
		System.out.println("소방차가 물을 뿌린다.");
	}
} // 자손 클래스 


public class UpcastDowncast07 {

	public static void main(String[] args) {
		FireEngine fe = new FireEngine();
		Car car = fe;	// 업캐스팅
		
		car.drive();
		car.stop();
		
		
		FireEngine fe2 = (FireEngine)car;	// 명시적인 다운캐스팅
		
		fe2.water();
		
	}
}

```

```java title=InstanceOfCar08
package casting;

/*
 * UpcastDowncast07 클래스에 정의된 Car 부모 클래스와 FireEngine 자손 클래스를 활용한 instanceof 형변환 유무 판단 연산자의 관한 실습
 */

public class InstanceOfCar08 {

	public static void main(String[] args) {
		FireEngine fe = new FireEngine();
		
		boolean isFire = fe instanceof FireEngine;
		if(isFire) {
			System.out.println("fe가 FireEngine이다.");
		}
		
		boolean isCar = fe instanceof Car;
		if(isCar) {
			System.out.println("업캐스팅 가능하다.");
		}
		
		if(fe instanceof Object) {	// fe가 Object 타입으로 업캐스팅이 가능한가
			System.out.println("fe가 Object 타입으로 업캐스팅 가능하다.");
		}
		
		System.out.println(fe.getClass().getName());	// fe 타입 패키지명.클래스명을 출력한다.
	}

}

```



## UpCasting & DownCasting 문제

- 다음 수행 결과 유추

```java title=Ex17_01
package 문제;

/*
 * 17장.레퍼런스 형 변환.pdf 19쪽 2번 문제
 */

class SubClass {	// extends Object
	private int i = 3;
	
	void print() {
		System.out.println("i : " + i);
	}
	
}	// SunClass

public class Ex17_01 {

	public static void main(String[] args) {
		Object obj = new SubClass();
		
		/*
		 * 문제) 형변환 유무 판단 연산자와 if 조건문을 사용해서 다운캐스팅이 가능할 때만 다운캐스팅 진행하는 코드 작성
		 * SubClass에 사용자 정의 메소드 void print() {}를 정의해서 i 멤버변수 값을 출력해보자.
		 */
		
		if(obj instanceof SubClass) {	// 다운캐스팅이 가능한가?
			SubClass sub = (SubClass)obj;	// 명시적인 다운캐스팅
			sub.print();
		}
		
		
	}

}

```



- 다음 프로그램 결과 유추

```java title=Ex17_02
package 문제;

/*
 * 17장.레퍼런스 형 변환.pdf 20쪽 3번 문제
 * 업캐스팅 이후 오버라이딩 메소드 호출하는 문제
 */

class Super {
	public int getNumber(int k) {
		return k + 1;
	}
}

class CastingEx03 extends Super {
	@Override
	public int getNumber(int k) {
		return k + 2;
	}
}

public class Ex17_02 {

	public static void main(String[] args) {
		Super s = new CastingEx03();	//업캐스팅
		System.out.println(s.getNumber(1));	// 3 => 업캐스팅 이후 오버라이딩 메소드를 호출한다.
		
		
	}

}

```

