
# 인터페이스

![[0_용어#인터페이스(Interface)]]


```java title=InterfaceTest01
package interface1;

/*
 * 인터페이스의 특징
 * 1. 인터페이스는 interface 예약어로 정의한다.
 * 2. 인터페이스에는 public abstract 로 인식하는 추상메소드가 올 수 있다. (public abstract는 생략할 수 있다.)
 * 3. 인터페이스를 상속받은 일반 자손 클래스에서 부모 인터페이스의 추상메소드를 반드시 오버라이딩을 해야한다. 그리고, 부모 인터페이스를 implements 키워드로 구현 상속 받는다. 
 */

interface IHello01 {
	void sayHello(String name);	// public abstract가 생략된 추상 메소드 정의
}

class Hello01 implements IHello01 {
	@Override
	public void sayHello(String name) {
		System.out.println(name + "씨 안녕하세요!");
	}
	
}

public class InterfaceTest01 {

	public static void main(String[] args) {
		IHello01 ih;	// 부모 인터페이스 참조변수 ih 선언
		ih = new Hello01();	// 업캐스팅
		
		ih.sayHello("홍길동");	// 업캐스팅 이후 오버라이딩 된 메소드를 호출한다.
	}

}

```

>[!success] 실행 결과
> 홍길동씨 안녕하세요!



## 클래스 다중 상속 불가

```java title=InterfaceTest02 error:15
package interface1;

/*
 * 일반 클래스나 추상 클래스는 하나 이상의 부모로부터 다중 상속을 받을 수 없다.
 */

abstract class Hello02 {
	public abstract void sayHello(String name);
}

abstract class GoodBye02 {
	public abstract void sayGoodBye(String name);
}

//class ChildClass02 extends Hello02, GoodBye02 {	// class는 다중 상속 불가
//	public void sayHello(String name) {
//		System.out.println(name + " 안녕");
//	}
//}

public class InterfaceTest02 {

	public static void main(String[] args) {
		
	}

}

```

>[!error] Error
> 클래스는 다중 상속 불가능



## 인터페이스 다중 상속 예제

```java title=InterfaceTest03
package interface1;

/*
 * 하나 이상의 부모로부터 다중 상속을 받으려면 인터페이스를 사용해야 한다.
 */

interface IHello03 {
	public abstract void sayHello(String name);
}


interface IGoodBye03 {
	void sayGoodBye(String name);
}


class Child03 implements IHello03, IGoodBye03 {

	@Override
	public void sayGoodBye(String name) {
		System.out.println(name + " 안녕히 가세요");
	}

	@Override
	public void sayHello(String name) {
		System.out.println(name + " 안녕하세요.");
	}
	
}


public class InterfaceTest03 {
	public static void main(String[] args) {
		Child03 child = new Child03();
		
		child.sayHello("홍길동");
		child.sayGoodBye("이순신");
		
	}

}
```

>[!success] 실행 결과
> 홍길동 안녕하세요.
> 이순신 안녕히 가세요


## 클래스와 인터페이스 혼합 상속

```java title=InterfaceTest04
package interface1;

/*
 * 부모 클래스와 인터페이스를 혼합으로 상속받는 법
 */

interface IHello04 {
	void sayHello(String name);	// public abstract 생략됨
}


abstract class GoodBye04 {
	public abstract void sayGoodBye(String name);	// 추상 클래스에서 추상 메소드를 정의할 때는 abstract 생략 불가
}


class Child04 extends GoodBye04 implements IHello04 {

	@Override
	public void sayHello(String name) {
		System.out.println(name + " 안녕하세요.");
	}

	@Override
	public void sayGoodBye(String name) {
		System.out.println(name + " 안녕히 가세요.");
	}
	
}


public class InterfaceTest04 {
	public static void main(String[] args) {
		Child04 child = new Child04();
		
		child.sayHello("세종대왕님");
		child.sayGoodBye("이율곡님");
	}

}

```

>[!success] 실행 결과
> 세종대왕님 안녕하세요.
> 이율곡님 안녕히 가세요.



## 인터페이스끼리의 상속 (extends 키워드)

```java title=InterfaceTest05
package interface1;

/*
 * 인터페이스에서 인터페이스 상속은 extends 키워드를 사용한다.
 */

interface IHello05 {
	void hello(String name);	// public abstract 이 생략됨.
}


interface IGoodBye05 {
	public abstract void bye(String name);	// public abstract 생략 가능 
}


interface ITotal05 extends IHello05, IGoodBye05 {
	void greeting(String name);
}


class Child05 implements ITotal05 {

	@Override
	public void hello(String name) {
		System.out.println(name + " 안녕");
	}

	@Override
	public void bye(String name) {
		System.out.println(name + " 잘가세요.");
	}

	@Override
	public void greeting(String name) {
		System.out.println(name + "씨 반가워요.");
	}
	
}


public class InterfaceTest05 {
	public static void main(String[] args) {
		Child05 child = new Child05();
		
		child.hello("홍길동");
		child.greeting("이순신");
		child.bye("강감찬");
		
	}
	
}

```

>[!success] 실행 결과
> 홍길동 안녕
> 이순신 잘가세요.
> 강감찬 반가워요.



## 인터페이스 내 멤버 변수는 정적 상수

```java title=InterfaceTest06
package interface1;

/*
 * 인터페이스에 오는 모든 변수는 public static final로 인식되는 정적 상수이다.
 * 예) int a; -> public stsatic int a; 로 인식됨
 */

interface IColor06 {
	int RED=1;	// public static final이 생략된 정적 상수
	public static final int GREEN = 2;
	public static final int BLUE = 3;
	
	void setColor(int c);	// 추상 메소드, public abstract 생략되어 있음
	public abstract int getColor();
}

abstract class AbsColor06 implements IColor06 {
	int color = GREEN;	// 추상 클래스에 오는 color는 일반 변수
	
	@Override
	public void setColor(int c) {
		color = c;
	}
}

class SubClass06 extends AbsColor06 {
	@Override
	public int getColor() {
		return color;
	}
}

public class InterfaceTest06 {
	public static void main(String[] args) {
		SubClass06 sub = new SubClass06();
		
		sub.setColor(IColor06.BLUE);
		System.out.println(sub.getColor());
	}

}

```

>[!success] 실행 결과
> 3



## 클래스에서 인터페이스를 통해 간접으로 클래스 연결

```java title=InterfaceTest07
package interface1;

/*
 * 클래스와 클래스 간 직접 연결하는 방식,
 * 클래스에서 인터페이스를 통해서 간접으로 클래스 연결(이 소스는 여기에 해당)
 */

interface I07 {
	public abstract void play();	// 추상 메소드
}

class B07 implements I07 {
	@Override
	public void play() {
		System.out.println("play in B07 Class");
	}
} // 첫번째 자손 클래스 B07

class C07 implements I07 {
	@Override
	public void play() {
		System.out.println("play in C07 Class");
	}
} // 두번째 자손 클래스 C07

class A07 {
	void autoPlay(I07 i) {
		i.play();
		/*
		 * 이론 문제) 적용된 중요한 자바 문법 2가지만 적어보세요.
		 * 1. A07 객체의 autoPlay 메소드의 매개변수로 B07, C07 자손 클래스 타입의 데이터를 전달하면 I07 타입의 i 참조변수로 업캐스팅 발생
		 * 2. 실행문 내 play() 호출 시 컴파일러가 I07 인터페이스 내에 play() 추상 메소드가 존재하는지 확인 및 참조변수 i가 가리키는 실제 객체 타입을 확인.
		 *    런타임에 실제 객체 타입인 B07, C07 타입에 play() 메소드가 오버라이딩 된 것을 확인하여 i.play(); Java의 다형성에 의해 B07과 C07 클래스의 play() 메소드 결과가 출력
		 */
		
		/*
		 * 선생닙 답
		 * 1. 매개변수 다형성(업캐스팅 + 상속)
		 * 2. 업캐스팅 이후 오버라이딩 메소드 호출
		 */
	}
}

public class InterfaceTest07 {
	public static void main(String[] args) {
		A07 a = new A07();
		
		a.autoPlay(new B07());
		a.autoPlay(new C07());
	}

}

```

>[!success] 실행 결과
> play in B07 Class
> play in C07 Class



## 다양한 자바 문법 활용 예제

```java title=InterfaceTest08
package interface1;

/*
 * 다양한 자바 문법 활용 예제
 */

interface I08 {
	void methodB();	// public abstract 생략된 추상 메소드, 인터페이스는 추상 메소드, 정적 상수만 정의할 수 있기 때문!
}

class B08 extends Object implements I08 {	// extends Object 생략 가능
	@Override
	public void methodB() {
		System.out.println("methodB in B08 Class");
	}
	
	@Override
	public String toString() {
		return "class B08";
	}
}	// B08 class


class InstanceManager {
	public static I08 getInstance() {
		return new B08();
	}
}	// InstanceManager

class A08 {
	void methodA() {
		I08 i = InstanceManager.getInstance();	// 업캐스팅
		i.methodB();// 업캐스팅 이후 오버라이딩 된 메소드 호출
		System.out.println(i.toString());
	}
}	// A08 class


public class InterfaceTest08 {
	public static void main(String[] args) {
		A08 a = new A08();
		
		a.methodA();
	}

}

```

>[!success] 실행 결과
> methodB in B08 Class
> class B08



## 디폴트 메소드(Default Method)

```java title=InterfaceTest09
package interface1;

/*
 * 자바8(JDK 1.8) 버전 이후에는 인터페이스에도 디폴트 메소드와 정적메소드(static 메소드)가 올 수 있다.
 * 부모 인터페이스에 새로운 추상메소드가 추가되면 이 인터페이스를 상속받은 모든 자손 클래스에서는 사용하지 않는 부모의 추상 메소드를 강제 오버라이딩을 해야하는 불편함이 있다.
 * 
 * 이러한 불편함을 해결하기 위해 나온 것이 디폴트 메소드이다.
 * 결국 부모 인터페이스에 새로운 디폴트 메소드가 추가되었다 해도 자손에서 필요치 않으면 굳이 오버라이딩 하지 않아도 된다.
 * 
 * 참고) 1. 부모 인터페이스에 동일한 디폴트 메소드가 중복된 경우는 자손클래스에서 부모의 디폴트 메소드를 무조건 오버라이딩을 해야 한다.
 *       2. 부모 인터페이스의 디폴트 메소드와 부모 클래스의 일반 메소드가 중복된 경우는 자손에서 디폴트 메소드는 무시하고 부모클래스의 일반 메소드가 상속된다.
 */


interface MyInterface {
	default void method1() {
		System.out.println("method1() in MyInterface");
	} // 디폴트 메소드
	
	default void method2() {
		System.out.println("method2() in MyInterface");
	}
	
	static void staticMethod() {
		System.out.println("static Method in MyInterface");
	} // 정적 메소드
	
} // MyInterface


interface MyInterface2 {
	default void method1() {
		System.out.println("method1() in MyInterface2");
	}
	static void staticMethod() {
		System.out.println("staticMethod() in MyInterface2");
	}
} // MyInterface2


class Parent {
	public void method2() {
		System.out.println("method2() in Parent");
	}
}


class Child09 extends Parent implements MyInterface, MyInterface2 {
	@Override
	public void method1() {
		System.out.println("method1() in Child09");
	}
}


public class InterfaceTest09 {
	public static void main(String[] args) {
		Child09 child = new Child09();
		
		child.method1();	// 오버라이딩 메소드
		child.method2();	// 인터페이스의 디폴트 메소드와 부모 클래스의 일반 메소드가 중복되는 경우, 부모 클래스로부터 상속받은 메소드가 호출됨
		
		MyInterface.staticMethod();
		MyInterface2.staticMethod();
	}

}

```

>[!success] 실행 결과
>method1() in Child09
>method2() in Parent
>static Method in MyInterface
>staticMethod() in MyInterface2



# 인터페이스 문제

```java title=Ex18_01
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

>[!success] 실행 결과
>10
>100
>Test



```java title=Ex18_02 hl:9, error:16
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

>[!fail] 실행 결과
> final 메소드는 오버라이딩 되지 않기 때문에 Error



```java title=IShapeClass
package com.naver.model01;

public interface IShapeClass {
	void draw();
}

```

```java title=Circ
package com.naver.model02;

import com.naver.model01.IShapeClass;

public class Circ implements IShapeClass {
	@Override
	public void draw() {
		System.out.println("타원을 그린다.");
	}
	
}

```

```java title=Rect
package com.naver.model02;

import com.naver.model01.IShapeClass;

public class Rect implements IShapeClass {
	@Override
	public void draw() {
		System.out.println("사각형을 그린다.");
	}
	
}

```

```java title=Tria
package com.naver.model02;

import com.naver.model01.IShapeClass;

public class Tria implements IShapeClass {
	@Override
	public void draw() {
		System.out.println("삼각형을 그린다.");
	}
	
}

```

```java title=IShapMain
package com.naver.model03;

import com.naver.model01.IShapeClass;

public class IShapMain {
	public static void printArr(IShapeClass ref) {
		ref.draw();
	}
}

```

```java title=Ex19_01
package 문제;

import com.naver.model01.IShapeClass;
import com.naver.model02.Circ;
import com.naver.model02.Rect;
import com.naver.model02.Tria;
import com.naver.model03.IShapMain;

/*
 * 19장.인터페이스.pdf No.16쪽 1번 문제
 * 
 * 추가 문제)
 * 1. com.naver.model01 패키지에 부모 인터페이스 IShapeClass를 정의하고 추상 메소드를 void draw();를 정의한다.
 * 2. com.naver.model02 패키지에서 IShapeClass 인터페이스를 구현 상속받은 자손 클래스 Circ, Rect, Tria를 만들고, 
 *    draw() 추상 메소드를 오버라이딩 한 다음 실행 문장으로 "타원을 그린다.", "사각형을 그린다.", "삼각형을 그린다."가 출력되도록 작성한다.
 */

public class Ex19_01 {

	public static void main(String[] args) {
		IShapeClass ref; // 부모 인터페이스로 참조 변수 선언
		
		ref = new Circ(); // 업캐스팅
		ref.draw(); // 업캐스팅 후 오버라이딩 된 메소드 호출
		
		ref = new Rect();
		ref.draw();
		
		ref = new Tria();
		ref.draw();
		System.out.println("\n=============================>");
		
		/*
		 * 추가문제 2) 배열 크기가 3인 객체 배열 refArr을 생성하고 3개의 배열원소 값은 Circ, Rect, Tria 객체 주소를 업캐스팅해서 저장한 다음 
		 * 일반 for 반복문을 활용해서 업캐스팅 후 각 배열 원소값으로 오바라이딩 한 메소드를 호출하는 코드를 작성해보세요.
		 */
		IShapeClass[] refArr = { new Circ(), new Rect(), new Tria() };
		
		for(int i = 0; i < refArr.length; i++) {
			refArr[i].draw();
		}
		System.out.println("\n=============================>");
		
		/*
		 * 추가문제 3) com.naver.model03 패키지에 IShapeMain 클래스를 정의한 다음 매개변수 다형성 문법이 적용되게 리턴타잆이 없는 void 형으로 printArr() 메소드를 정의하고, 
		 * 해당 메소드 매개변수 타입을 IShapeClass ref로 선언한 다음 메소드 실행 문장으로 ref.draw(), 즉 업캐스팅 이후 오버라이딩한 메소드를 호출해서 동일 출력 결과물이 나오게 만들어보자.
		 */
		for(IShapeClass ref1 : refArr) {
			IShapMain.printArr(ref1);
		}
		
		
	}

}

```

>[!success] 실행 결과
> 타원을 그린다.
> 사각형을 그린다.
> 삼각형을 그린다.
> 
> =============================>
> 타원을 그린다.
> 사각형을 그린다.
> 삼각형을 그린다.
> 
> =============================>
> 타원을 그린다.
> 사각형을 그린다.
> 삼각형을 그린다.









