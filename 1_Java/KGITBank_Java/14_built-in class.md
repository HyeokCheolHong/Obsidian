
# Object

```java title=ObjectTest10
package 내장클래스;

/*
 * 자바 최상위 내장 부모클래스 Object 내장 메소드 toString()을 자손에서 오버라이딩을 활용하는 소스이다.
 */

class Point10 extends Object {
	int x, y;
	
	public Point10() {}	// 생성자가 오버로딩이 되면 매개변수가 없는 기본 생성자를 묵시적 제공 안 함
	public Point10(int x, int y) {
		this.x = x;
		this.y = y;
	} // 매개변수 개수가 다른 생성자 오버로딩
	
	@Override
	public String toString() {	// Object 클래스의 toString() 메소드 오버라이딩
		return "(x 좌표 : " + x + ", y 좌표 : " + y + ")";
	}
}


public class ObjectTest10 {
	public static void main(String[] args) {
		Point10 pt = new Point10(10, 20);	// 오버라이딩 된 생성자 호출
		System.out.println(pt.toString());	
		System.out.println(pt); // .toString() 메소드는 생략 가능
		
	}

}

```

>[!success] 실행 결과
>(x 좌표 : 10, y 좌표 : 20)
>(x 좌표 : 10, y 좌표 : 20)


