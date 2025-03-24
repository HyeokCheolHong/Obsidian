
# 추상 클래스(abstract)

![[0_용어#추상 클래스(abstract)]]



## 추상 클래스 예제 1

```java title=Phone
package ch07.sec10.exam01;

public abstract class Phone {
	// 필드 선언
	String owner;
	
	// 생성자 선언
	Phone(String owner) {
		this.owner = owner;
	}
	
	// 메소드 선언
	void turnOn() {
		System.out.println("폰 전원을 켭니다.");
	}
	void turnOff() {
		System.out.println("폰 전원을 끕니다.");
	}
	
}

```

```java title=SmartPhone
package ch07.sec10.exam01;

public class SmartPhone extends Phone {
	// 생성자 선언
	SmartPhone(String owner) {
		// Phone 생성자 호출
		super(owner);
	}
	
	// 메소드 선언
	void internetSearch() {
		System.out.println("인터넷 검색을 합니다.");
	}
	
}

```

```java title=PhoneExample error:"new Phone("홍길동");"
package ch07.sec10.exam01;

public class PhoneExample {

	public static void main(String[] args) {
		// 추상 클래스 인스턴스는 직접 생성 불가
		// Phone phone  = new Phone("홍길동");
		
		// 추상 클래스의 자식 클래스는 new 연산자로 객체 생성이 가능하고, 
		// Phone 추상 클래스로부터 물려받은 turnOn(), turnOff() 메소드를 호출할 수 있다.
		SmartPhone smartPhone = new SmartPhone("홍길동");
		
		smartPhone.turnOn();
		smartPhone.internetSearch();
		smartPhone.turnOff();
	}

}

```

>[!success] 실행 결과
>폰 전원을 켭니다.
>인터넷 검색을 합니다.
>폰 전원을 끕니다.



# 추상 메소드와 오버라이딩
![[2_JAVA/0_용어#추상 메소드]]

## 추상 메소드 예제 1

```java title=Animal
package ch07.sec10.exam02;

public abstract class Animal {
	// 메소드 선언
	public void breathe() {
		System.out.println("숨을 쉽니다.");
	}
	
	// 추상 메소드 선언
	public abstract void sound();
	
}

```

```java title=Dog
package ch07.sec10.exam02;

public class Dog extends Animal {
	// 추상 메소드 재정의
	@Override
	public void sound() {
		System.out.println("멍멍");
	}
	
}

```

```java title=Cat
package ch07.sec10.exam02;

public class Cat extends Animal {
	// 추상 메소드 재정의 
	@Override
	public void sound() {
		System.out.println("야옹");
	}
	
}

```

```java title=AbstractMethodExample
package ch07.sec10.exam02;

public class AbstractMethodExample {
	// 매개변수로 받은 값이 자식 객체라면 자동적으로 업캐스팅 진행
	public static void animalSound(Animal animal) {
		animal.sound();
	}
	
	public static void main(String[] args) {
		Dog dog = new Dog();
		dog.sound();
		
		Cat cat = new Cat();
		cat.sound();
		
		
		// 매개변수의 다형성
		if(dog instanceof Animal) {
			animalSound(dog);
		}
		
		if(cat instanceof Animal) {
			animalSound(cat);
		}
		
	}

}

```

>[!success] 실행 결과
> 멍멍
> 야옹
> 멍멍
> 야옹



***



# 학원 추상 클래스 예제
```java title=AbsTest10
package abst;

/*
 * 추상클래스 특징)
 * 1. abstract class 키워드로 추상클래스를 정의한다.
 * 2. 추상클래스는 new 키워드로 객체 생성을 할 수 없다.
 * 3. 일반클래스는 추상메소드가 올 수 없다. 추상 메소드는 abstract 키워드로 정의하고 {}가 없고, 실행 문장이 없다. 호출 불가능하다.
 */

abstract class AbsClass10 {	// 추상 클래스 정의
	abstract void pr();	// pr() 추상 메소드 정의
}

//class AbsClass02 { // 일반 클래스 정의
//	abstract void print();	// 일반 클래스는 추상 메소드 정의할 수 없음
//}


public class AbsTest10 {

	public static void main(String[] args) {

	}

}

```



```java title=AbsTest11
package abst;

/*
 * 추상 클래스를 상속받은 일반 자손 클래스에서는 반드시 부모 추상클래스의 추상메소드를 오버라이딩을 해야한다.
 */

abstract class Father11 {
	abstract void m01(); // 추상 메소드 정의
	
	void m02() {
		System.out.println("일반메소드 m02");
	}
}

class Son11 extends Father11 {
	@Override
	void m01() {
		System.out.println("m01() 추상 메소드 오버라이딩");
	}
	
}

public class AbsTest11 {
	public static void main(String[] args) {
		Father11 f = new Son11();	// 업캐스팅
		f.m01();	// 업캐스팅 이후 오버라이딩 한 메소드 호출
		
		Son11 s = new Son11();
		s.m01();
		s.m02();	// 상속 받아서 호출
	}
}

```



```java title=AbsTest12
package abst;

/*
 * 중간에 MiddleClass 추상 클래스를 끼워놓은 다음 이를 상속받은 자손 클래스에서 그 부모인 AbsClass12에 있는 추상 메소드를 오버라이딩 한 예다.
 */

abstract class AbsClass12 {
	abstract void method01();
	
	void method02() {
		System.out.println("method02() 일반 메소드");
	}
} // 첫번째 부모 AbsClass12 추상 클래스


abstract class MiddleClass extends AbsClass12 {
	void method03() {
		System.out.println("method03() 일반 메소드");
	}
} // 두번째 부모 MiddleClass 중간 추상 클래스 


class ChildClass12 extends MiddleClass {
	@Override
	void method01() {
		System.out.println("추상 메소드 오버라이딩 method01()");
	}
} // 일반 클래스


public class AbsTest12 {

	public static void main(String[] args) {
		ChildClass12 cc = new ChildClass12();
		
		cc.method01();	// 추상 클래스로부터 상속받은 추상 메소드 오버라이딩
		cc.method03();	// 상속 받아서 호출
		cc.method02();
		
	}
}
```



```java title=AirCon
package net.daum.model01;

public abstract class AirCon {
	public abstract void goods_in();
}

```

```java title=AirModel01
package net.daum.model02;

import net.daum.model01.AirCon;

public class AirModel01 extends AirCon {
	
	@Override
	public void goods_in() {
		System.out.println("AirModel01 에어콘 모델이 입고");
	}

}

```

```java title=AirModel02
package net.daum.model02;

import net.daum.model01.AirCon;

public class AirModel02 extends AirCon {

	@Override
	public void goods_in() {
		System.out.println("AirModel02 에어컨 모델이 입고됨");
	}

}

```

```java title=AirModel03
package net.daum.model02;

import net.daum.model01.AirCon;

public class AirModel03 extends AirCon {

	@Override
	public void goods_in() {
		System.out.println("AirModel03 에어컨 입고");
	}

}

```

```java title=AirConMain
package net.daum.controller;

import net.daum.model01.AirCon;
import net.daum.model02.AirModel01;
import net.daum.model02.AirModel02;
import net.daum.model02.AirModel03;

public class AirConMain {

	public static void main(String[] args) {
		AirModel01 air01 = new AirModel01();
		AirModel02 air02 = new AirModel02();
		AirModel03 air03 = new AirModel03();
		
		air01.goods_in();
		air02.goods_in();
		air03.goods_in();
		System.out.println("=====================>");
		
		
		// 업캐스팅
		AirCon air;	// 부모 추상클래스 타입으로 참조 변수를 선언
		
		air = new AirModel01();
		air.goods_in();
		
		air = new AirModel02();
		air.goods_in();
		
		air = new AirModel03();
		air.goods_in();
		System.out.println("=====================>");
		
		
		// 배열에 담고 출력
		AirCon[] arr = new AirCon[3];	// 배열 크기 3인 AirCon 타입의 배열 생성
		
//		arr[0] = new AirModel01();		// 업캐스팅
//		arr[1] = new AirModel02();
//		arr[2] = new AirModel03();
		
		
		for(int i = 0; i < arr.length; i++) {
			arr[i].goods_in();	// 업캐스팅 이후 오버라이딩 한 메소드를 호출
		}
		System.out.println("=====================>");
		
	}

}

```

```java title=AirConMain02
package net.daum.controller;

import net.daum.model01.AirCon;
import net.daum.model02.AirModel01;
import net.daum.model02.AirModel02;
import net.daum.model02.AirModel03;

/*
 * 하나는 매개변수 다형성 문법이 적용되지 않은 것
 * 또 하나는 매개변수 다형성 문법이 적용된 것에 대한 예제
 * 
 * 매개변수 다형성 문법을 적용할려면 상속, 업캐스팅 등(메소드 오버라이딩, ...)이 적용되어야 한다.
 */

public class AirConMain02 {
	/*
	 * 매개변수 다형성 문법을 적용하지 않으면 자손클래스 개수만큼 메소드를 오버로딩 해야한다.
	 * 그만큼 불필요한 코드라인이 추가된다.
	 */
	static void inCome(AirModel01 air) {
		air.goods_in();
	}
	static void inCome(AirModel02 air) {
		air.goods_in();
	}
	static void inCome(AirModel03 air) {
		air.goods_in();
	}

	
	// 매개변수 타입이 부모 타입인 AirCon이어서 업캐스팅이 적용되며, 모든 자손 타입을 받을 수 있다. => 매개변수 다형성 문법 이라고 부른다.
	static void inCome2(AirCon air) {
		air.goods_in();	// 업캐스팅 이후 오버라이딩 한 메소드 호출
	}
	
	public static void main(String[] args) {
		inCome(new AirModel01());
		inCome(new AirModel02());
		inCome(new AirModel03());
		System.out.println("================");
		
		
		inCome2(new AirModel01());
		inCome2(new AirModel02());
		inCome2(new AirModel03());
		System.out.println("================");
		
	}
	
}

```



# final
- 변수를 final로 정의하면 수정할 수 없는 변수 즉 상수가 된다. 
- 클래스를 final 로선언하면 더 이상 상속을 허락하지 않는다. 
- 메서드를 final 로선언하면 더 이상 오버라이딩을 허락하지 않는다.

```java title=FinalVariable13
package 파이널;

/*
 * 변수를 final로 선언할 경우 수정할 수 없는 상수가 된다.
 * 상수명은 관례적으로 영문 대문자로 작성한다.
 */

class FinalMember {
	final int ABC = 100;
	
	public void setAbc(int abc) {
//		ABC = abc;	// ABC 멤버 변수는 final 이기 때문에 값 변조 불가능
	}
	
	public void pr() {
		System.out.println("ABC 상수값 : " + ABC);
	}
	
}


public class FinalVariable13 {

	public static void main(String[] args) {
		FinalMember fm = new FinalMember();
		fm.setAbc(1000);
		fm.pr();
		
	}

}

```



```java title=FinalMethod14
package 파이널;


/*
 * 메소드를 final로 선언하면 더 이상 자손에서 오버라이딩을 허락하지 않는다. 
 */

class FinalMethodTest {
	public final void pr() {
		System.out.println("파이널 메소드이다.");
	}
}

class Son14 extends FinalMethodTest {
//	@Override
//	public void pr() {
//		System.out.println("pr() 메소드는 final 이라서 오버라이딩 안된다.");
//	}
	
}

public class FinalMethod14 {

	public static void main(String[] args) {
		FinalMethodTest fm = new Son14();
		fm.pr();	// 업캐스팅 이후 오버라이딩 된 메소드 호출, 하지만 pr() 메소드가 final이라서 자식 클래스에서 오버라이딩 안되어있음
		
	}

}

```



```java title=FinalClass15
package 파이널;


/*
 * 클래스를 final로 선언하면 더 이상 상속을 허락하지 않는다.
 */

final class FinalClassTest {
	int k = 10;
	
	public void setK(int k) {
		this.k = k;
	}
	
	public void print() {
		System.out.println("k : " + k);
	}
}

//class FinalSon15 extends FinalClassTest {		// 상속 안됨!
//	int b = 20;
//	
//	public FinalSon15() {
//		this.b = 200;
//	}
//	
//	public void pr() {
//		System.out.println("b : " + b);
//	}
//}

public class FinalClass15 {

	public static void main(String[] args) {
//		FinalClassTest fc = new FinalSon15();
	}

}

```



***



# 추상 클래스 문제

## 문제 1

```java title=
package 문제;

/*
 * 18장. 추상 클래스와 final.pdf No. 20쪽의 1번 문제
 * 추상 클래스를 상속받은 자손 클래스에서 반드시 부모의 추상 메소드를 오버라이딩을 해야한다.
 */

abstract class Abs1 {
	// 필드 선언
	int a = 10;
	String str = "Test";
	
	// 추상 메소드 선언
	public abstract int getA();
	
	// 일반 메소드 선언
	public String getStr() {
		return str;
	}
}

abstract class Abs2 extends Abs1 {
	// 필드 선언 
	int b = 100;
	
	// 추상 메소드 선언
	public abstract int getB();
	
}

class AbsMain extends Abs2 {
	// 추상 메소드 오버라이딩
	@Override
	public int getA() {
		return a;
	}
	@Override
	public int getB() {
		return b;
	}
	
}

public class Ex18_01 {

	public static void main(String[] args) {
		// AbsMain 객체 생성
		AbsMain am = new AbsMain();
		
		// 추상 메소드 호출
		System.out.println(am.getA());
		System.out.println(am.getB());
		
		// 추상 클래스로부터 상속받은 getStr() 일반 메소드 호출
		System.out.println(am.getStr());
		
		
	}

}
```



## 문제 2

```java title=Ex18_02
package 문제;

/*
 * 18장. 추상 클래스와 final.pdf No.21쪽의 2번 문제
 * final로 선언된 메소드는 자손에서 오버라이딩을 할 수 없다.
 */

class A02 extends Object {
	public final int method01() {
		return 0;
	}
}

class B02 extends A02 {
//	@Override
//	public int method01() {
//		return 10;
//	}
}

public class Ex18_02 {

	public static void main(String[] args) {
		B02 b = new B02();
		
		System.out.println(b.method01());
	}

}

```








