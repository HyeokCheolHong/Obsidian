2024-08-26

```java title=EqualsTest01
package BuiltInAPI;

// 자바에서 equals()메소드와 ==(같다)연산의 차이점
// 1. 정수 숫자 기본타입값을 같다등을 비교할 때는 ==연산을 사용한다.
// 2. String 문자열 참조타입 값을 같다 비교할 때는 String 내장 API클래스에 오버라이딩 된 equals()메소드를 사용해서 문자열 내용값만 비교해야 한다.
//    만약에 ==을 비교하면 객체주소를 비교한다.

public class EqualsTest01 {

	public static void main(String[] args) {
		
		// 기본타입 값 비교
		int a = 10, b = 10;
		if(a == b) {
			System.out.println("같다");
		}
		
		String pwd01 = new String("56789");
		String pwd02 = new String("56789");
		// pwd01 과 pwd02는 값은 같을수 있으나 객체주소가 다르다.
		
		if(pwd01 == pwd02) {
		// pwd01과 pwd02는 객체주소가 달라서 false
			System.out.println("같다");
		} else {
			System.out.println("다르다");
		}
		
		String pwd03 = new String("77777");
		String pwd04 = pwd03;
		// pwd03과 pwd04는 값과 객체주소가 같다.
		if(pwd03 == pwd04) {
		// pwd03 과 pwd04는 객체주소가 같으므로 True
			System.out.println("같다");
		} else {
			System.out.println("다르다");
		}
		
		if(pwd01.equals(pwd02) ) {
		// equals()메소드로 문자열 값만 비교	
		// pwd01과 pwd02는 값이 같기에 True
			System.out.println("비번이 같다");
		} else {
			System.out.println("비번이 다르다");
		}
		
		if(pwd03.equals(pwd04) ) {
			System.out.println("비번이 같다");
		} else {
			System.out.println("비번이 다르다");
		}
	}

}
```



```java title=EqualsTest02
package BuiltInAPI;

// Object의 equals()메소드를 오버라이딩을 하지 않고 상속받아서 같다를 비교하는 예제

class Point02 extends Object{
	int a;
	int b;
	
	public Point02() {}
	
	public Point02(int a, int b) {
		this.a = a;
		this.b = b;
	} // 매개변수가 개수가 다른 생성자 오버로딩
}

public class EqualsTest02 {

	public static void main(String[] args) {
		
		Point02 pt01 = new Point02(10, 20);
		// 오버로딩 된 생성자 호출
		Point02 pt02 = new Point02(10, 20);
		
		// 상속만 진행했기에 자손(Point02)에서 받은 값을 서로 비교할 수 없다
		if(pt01.equals(pt02)) {
			// 값 비교
			System.out.println("같다");
		} else {
			System.out.println("다르다");
		}
		
		System.out.println("====구분선====");
		
		// 오버라이딩을 하지 않아 pt01 과 pt02의 객체주소는 다르다.
		if(pt01 == pt02) {
			// 객체주소 비교
			System.out.println("같다");
		} else {
			System.out.println("다르다");
		}
	}
}

```

