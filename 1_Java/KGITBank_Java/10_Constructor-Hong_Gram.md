

# 오버라이딩

```java title=OverRidingTest11

/*
 * 메소드 오버라이딩이란?
 * 1. 상속 관계에서 부모클래스 메소드 이름 앞의 리턴타입, 매개변수(전달인자) 타입과 개수 모두 동일한 원형을 그대로 자손으로 상속받은 상태에서 
 * {} 중괄호 내의 본문 실행문장을 자손에 맞게 변경 수정하는 것을 메소드 오버라이딩이라고 한다.
 * 
 * 2. 오버라이딩을 하기 위해서는 사전에 반드시 상속관계를 만들어야한다.
 *  
 */

class Parent11 {
	void p11() {
		System.out.println("부모클래스 메소드 p11()");
	}
} // 부모 클래스


class Child11 extends Parent11 {

	@Override
	void p11() {
		System.out.println("자손에 맞게 오버라이딩 한 메소드 p11()");
	}
	
}


public class OverRidingTest11 {

	public static void main(String[] args) {
		
		Child11 child = new Child11();
		child.p11();	// 오버라이딩 한 메소드 호출
		
		Parent11 parent = new Parent11();
		parent.p11();
	}

}

```



```java title=SuperTest12

/*
 * 자손클래스에서 메소드가 오버라이딩 된 경우에서 부모클래스 메소드를 호출할려면 super.메소드()를 사용한다.
 */

class Father12 {
	public void f12() {
		System.out.println("부모클래스 메소드 f12()");
	}
	
} // 부모 클래스 Father12


class Child12 extends Father12 {

	@Override
	public void f12() {
		super.f12();	// 부모클래스 메소드 호출
		System.out.println("오버라이딩 한 메소드 f12()");
	}
	
	public void ch12() {
		System.out.println("자손클래스에서 정의한 메소드 ch12()");
	}
	
} // 자손 클래스 Child12


public class SuperTest12 {

	public static void main(String[] args) {
		
		Child12 ch12 = new Child12();
		
		ch12.f12();	// 오버라이딩 한 메소드 호출
		ch12.ch12(); // 자손에서 정의한 메소드 호출
		
	}

}


```



```java title=SuperTest13


/*
 * 부모 클래스에서 정의한 멤버변수명과 자손 클래스에서 정의한 멤버변수명이 동일한 경우
 * 부모로부터 상속받은 멤버변수명에 접근할 때는 super.멤버변수명으로 접근한다. 
 */

class Mother13 {
	protected int a = 10;
	protected int b = 20;
}


class Child13 extends Mother13 {
	protected int a = 40;
	protected int b = 50;
	protected int c = 30;
	
	public void pr01() {
		System.out.println("a : " + this.a + ", b : " + b + ", c : " + c);	// 40, 50, 30
	}
	
	public void pr02() {
		System.out.println("super.a : " + super.a + ", super.b : " + super.b + ", this.c : " + this.c);	// 10, 20, 30
	}
	
}


public class SuperTest13 {

	public static void main(String[] args) {
		Child13 ch13 = new Child13();
		
		ch13.pr01();
		ch13.pr02();
		
	}

}



```



***



# 상속 생성자

```java title=SuperConstructorTest14

/*
 * 상속에서 생성자 호출에 관한 부분
 */


class Mother14 extends Object {
	protected int x = 10;
	protected int y = 20;
	
	// 생성자명은 클래스명과 같게 만든다.
	public Mother14() { // 매개변수가 없는 기본 생성자	 
		super();		 // 최상위 부모클래스 Object의 기본생성자를 먼저 호출한다. (생략 가능)
		System.out.println("부모클래스 Mother14() 기본 생성자 호출");
	}

}


class Son14 extends Mother14 {
	protected int z = 30;
	
	public Son14() {
		// super();가 생략됨 => 부모의 기본 생성자를 먼저 호출
		System.out.println("자손 클래스 Son14() 기본생성자 호출");
	}
	
	public void pr() {
		System.out.println("x : " + x + ", y : " + y + ", z : " + z);
	}
	
}


public class SuperConstructorTest14 {

	public static void main(String[] args) {
		
		new Son14().pr();	// new Son14()에 의해서 기본 생성자를 호출
		
	}

}

```



```java title=SuperConstructorTest15


/*
 * 부모 클래스 생성자가 오버로딩이 된 경우, 묵시적으로 제공되던 기본 생성자가 제공되지 않는다.
 * 이때, 자손에서 부모의 기본생성자를 호출할 때 에러가 발생한다.
 * 
 */


class Mother15 {
	protected int a = 100;
	protected int b = 200;
	
	// 기본 생성자
	public Mother15() { ; }
	
	// 오버로딩 생성자
	public Mother15(int a, int b) {
		this.a = a;
		this.b = b;
	}
	
}


class Son15 extends Mother15 {
	protected int c = 300;
	
	public Son15() {
		System.out.println("자손의 Son15() 기본 생성자 호출");
	}
	
	
	/*
	 * 문제) 합리적인 생성자 오버로딩 추가 코드를 해보자.
	 * 참고로 a, b, c 멤버변수값이 1000, 2000, 3000으로 변경되는 코드이다.
	 */
	
	public Son15(int a, int b, int c) {
		super(a, b);	// 부모 클래스의 전달인자 2개짜리 오버로딩 된 생성자를 호출
		this.c = c;
	}
	
	public void print() {
		System.out.println(String.format("a : %d, b : %d, this.c : %d", a, b, c));
	}
	
}


public class SuperConstructorTest15 {

	public static void main(String[] args) {
		Son15 s15 = new Son15();	// new Son15();에 의해서 Son15() 기본 생성자 호출
		s15.print();
		
		
		new Son15(1000, 2000, 3000).print();
		
		
		Son15 s16 = new Son15(1000, 2000, 3000);
		s16.print();
		
	}

}


```



```java title=ExtendsConstructorTest16

/*
 * 상속관계에서 부모클래스 생성자가 오버로딩이 된 경우 자손에서 생성자 호출에 관한 소스
 */

class Mother16 {
	protected int a = 10;
	protected int b = 20;
	
	// 생성자가 오버로딩이 되면, 묵시적인 기본 생성자를 제공하지 않는다.
	
	public Mother16(int a, int b) {
		// super();	코드가 생략됨. 최상위 부모클래스 Object의 기본 생성자를 호출한다.
		this.a = a;
		this.b = b;
	}
} // Mother16 class 


class Son16 extends Mother16 {
	protected int c = 30;
	
	
	public Son16() {
		super(100, 200);	// 부모 클래스 전달인자 2개짜리 오버로딩 된 생성자를 호출한다.
		this.c = 300;
	}
	
	public Son16(int a, int b, int c) {
		super(a, b);
		this.c = c;
	} // 전달인자 3개짜리 오버로딩 된 생성자
	
	public void pr() {
		System.out.println(String.format("a : %d, b : %d, c : %d", a, b, c));
	}
	
}


public class ExtendsConstructorTest16 {

	public static void main(String[] args) {
		Son16 s16 = new Son16();
		s16.pr();
		
		Son16 s17 = new Son16(1000, 2000, 3000);
		s17.pr();
	}
	

}

```



***



# this

```java title=ThisConstructTest20

/*
 * this()는 같은 클래스 내의 오버로딩 된 다른 생성자를 호출한다.
 * this()는 상속과 관련이 없다.
 * 
 * 인스턴스 초기화 블록{}과 클래스 초기화 블록 static{}을 사용하지 않고 생성자를 통한 초기화를 한다.
 */

class Document {
	static int count;
	String name;	// 문서명
	
	{
		++count;
		System.out.println("인스턴스 초기화 블록 실행!!");
		System.out.println(count);
	}
	
	Document() {
		this("제목없음" + count);	// 같은 클래스 내의 다른 생성자 호출
		System.out.println(count);
	}
	
	Document(String name) {
		this.name = name;
		System.out.println("문서 " + this.name + "이 생성되었습니다.");
	}
	
	
}


public class ThisConstructTest20 {

	public static void main(String[] args) {
		Document d01 = new Document();
		System.out.println("총카운터 수="+  Document.count);
				
		Document d02 = new Document("java.txt");
		
	}

}

```

- [ ]  오류 해결 여부
      인스턴스 초기화 블록으로 객체가 생성 될 때마다 count 값 증가하도록 했다.
      `Document d01 = new Document();` 코드가 실행되면서 Document 기본 생성자가 실행.
      `this("제목없음" + count)` 가 실행될 때 count가 1이 아닌 0이 넘겨지는 것 같다....
      그래서 최초 객체 실행되었을 때 출력되는 문구는 "제목없음1" 문구가 아닌 "제목없음0" 문구가 출력된다.
      왜 그러는지 이해나 해결되면 체크박스 체크하기



# super

```java title=SuperThisTest21

/*
 * this()는 같은 클래스 내의 오버로딩 된 다른 생성자를 호출한다. 상속과 관련 없다.
 * super()는 부모클래스 생성자를 호출한다. 상속과 관련 있다.
 */

class Point {	// extends Object이 생략됨.
	int x = 10;
	int y = 20;
	
	Point(int x, int y) {
		super(); // 부모 Object 클래스의 기본생성자를 호출. 생략 가능함
		this.x = x;
		this.y = y;
	}
} // Point class

class Point3D extends Point {
	int z = 30;
	
	Point3D() {
		this(100, 200, 300);	//같은 클래스 내의 오버로딩 된 생성자 호출
	}
	
	Point3D(int x, int y, int z) {
		super(x, y);	// 부모클래스 오버로딩 된 생성자를 호출
		this.z = z;
	}
	
	void pr() {
		System.out.println("x : " + x + ", y : " + y + ", z : " + z);
		System.out.println();
	}
}

public class SuperThisTest21 {

	public static void main(String[] args) {
		Point3D pt = new Point3D();
		pt.pr();
		
		Point3D pt2 = new Point3D(1000, 2000, 3000);
		pt2.pr();
		
	}

}

```



***



# static import

```java title=Static_import
package 정적임포트_staticimport중요안함;

/*
 * static import문을 사용하면 static 멤버(정적 변수)를 호출할 때 생략 가능하다. 코드가 간결
 * 많이 사용하지 않음
 */

import static java.lang.System.out;
import static java.lang.Math.*;


public class Static_import {

	public static void main(String[] args) {
		
		// 기존 사용 : println() 메소드
		System.out.println(Math.random());
		// 정적 임포트 사용
		out.println(random());
		
		
		// 기존 사용 : Math.PI 멤버 변수
		System.out.println("원주율 값 : " + Math.PI);
		// 정적 임포트 사용
		out.println("원주율  값 : " + PI);
		
	}

}

```



***
















































