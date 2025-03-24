2024-08-28

```java title=ObjectTest01
package BuiltInAPI;

// Object 최고 조상 내장 API 클래스 하위에 equals()메소드를 자손에서 오버라이딩을 해서 비교하는 예제

class Point01 extends Object {
	int x, y;
	
	public Point01() {}
	
	public Point01(int x, int y) {
		this.x = x;
		this.y = y;
	}
	
	@Override
	public boolean equals(Object obj) {
	// equalss 메소드 호출하여(Obejct obj)로 업캐스팅 완료
		Point01 ptTmp = (Point01)obj;
		// 명시적인 다운 캐스팅
		
		if((x == ptTmp.x) && (y == ptTmp.y)) {
			return true;
		} else {
			return false;
		}
	}
}

public class ObjectTest01 {

	public static void main(String[] args) {
		
		Point01 pt01 = new Point01();
		Point01 pt02 = new Point01();
		
		if(pt01.equals(pt02)) {
			System.out.println("같다");
		} else {
			System.out.println("다르다");
		}
	}

}

```

---

```java title=AutoTest02
package BuiltInAPI;

// java 5버전이후에 추가된 오토박싱과 오토언박싱에 관한 소스
// 1. 오토박싱 : 자바 기본타입이 래퍼 참조타입으로 자동형변환이 되는 것을 말한다.
// 2. 오토언박싱 : 래퍼 참조타입이 기본타입으로 형변환이 되는 것을 말한다. 

public class AutoTest02 {

	public static void main(String[] args) {
		
		int n01 = 10;
		// 기본 타입
		int n02;
		Integer num01;
		// 래퍼 참조타입
		Integer num02 = new Integer(20);
		
		num01 = n01;
		// 오토박싱 : 래퍼 참조타입에 기본타입을 할당
		
		n02 = num02;
		// 오토언박싱 : 기본타입에 래퍼 참조타입을 할당
		
		System.out.println("오토박싱 된 값"+num01);
		System.out.println("오토언박싱 된 값"+n02);
	}

}

```

---

```java title=StringTest03
package BuiltInAPI;

// java.lang 기본패키지에 있는 문자열을 다루는 내장클래스 String하위의 내장메소드에 관한 소스

public class StringTest03 {

	public static void main(String[] args) {
		
		String str01 = "Java Programming";
		System.out.println("영문대문자:"+str01.toUpperCase()); // 영문대문자:JAVA PROGRAMMING
		System.out.println("str01 :"+str01); // str01 :Java Programming
		
		String result = str01.toUpperCase();
		System.out.println("result :"+result); // result :JAVA PROGRAMMING
		
		System.out.println("====구분선====");
		
		String str02 = "Java";
		String str03 = new String(" Programming");
		System.out.println("\'Java\'의 문자길이는?"+str02.length()); // 'Java'의 문자길이는?4
		System.out.println("문자결합="+str02.concat(str03)); // 문자결합=JavaProgramming
		System.out.println("\'Java\'에서 3번째 단일문자 :"+str02.charAt(2));
		// charAt() 메소드는 첫문자를 0부터 시작해서 해당위치의 단일문자를 구함
		
		System.out.println("\' Programming\'에서 r이 몇번째 저장되었는가?" + (str03.indexOf('r')+1)); // ' Programming'에서 r이 몇번째 저장되었는가?3
		// indexof() 내장메소드는 인수값에 해당하는 첫번째 문자가 왼쪽부터 몇번째 위치되어 있는 위치번호를 말한다. (첫문자는 0부터 시작한다)
		
		// 문제)str03변수에 저장된 문자열값에서 'r'을 맨오른쪽부터 찾아서 가장먼저 나오는 해당문자 위치번호를 구한다음 +1을 해보는 코드를 완성해보자
		System.out.println("\' Programming\'에서 r을 오른쪽에서 몇번째 저장되었는가?" + (str03.lastIndexOf('r')+1)); // ' Programming'에서 r을 오른쪽에서 몇번째 저장되었는가?6
	}
}

```

---

```java title=StringBuffer04
package BuiltInAPI;

import java.util.StringTokenizer;

// java.lang기본패키지 내장 API클래스 중 String과 StringBuffer의 차이점
// 1. String class : 내 자신 객체값을 변경 못함
// 2. StringBuffer class : 내 자신 객체값을 변경 가능

public class StringBuffer04 {

	public static void main(String[] args) {
		StringBuffer str01 = new StringBuffer();
		
		str01.append("Java");
		// append() 메소드로 문자열 추가
		System.out.println("추가된 str01 :" + str01.toString()); // 추가된 str01 :Java
		// toString() 메소드로 str01 객체 문자열로 반환
		
		str01.append(" Programming");
		// 기존값 Java를 유지한채 문자열 추가
		System.out.println("수정된 str01 :" + str01.toString()); // 수정된 str01 :Java Programming
		
		str01.replace(0, 4, "Jsp");
		// replace() 메소드로 문자 "Java" 주소번호 0이상 4미만 사이의 문자를 Jsp로 변경
		System.out.println("수정된 str01 :" + str01.toString()); // 수정된 str01 :Jsp Programming
		
		String str02 = str01.substring(3);
		//substring() 메소드는 첫문자를 인수부터 시작해서 인수이후 부터 마지막 문자까지 구함.
		System.out.println("str02 :" + str02.toString()); // str02 : Programming
		
		str01.deleteCharAt(0);
		// 인덱스주소 0번째 삭제
		System.out.println("첫문자 삭제후 str01 :" + str01.toString()); // 첫문자 삭제후 str01 :sp Programming
		
		str01.reverse();
		// 문자를 역순으로 뒤집는다.
		System.out.println("str01 :" + str01.toString());

		
		StringTokenizer st = new StringTokenizer("this is a test");
	     while (st.hasMoreTokens()) {
	         System.out.println(st.nextToken());
	     }
		
		String[] result = "this is a test".split("\\s");
	     for (int x=0; x<result.length; x++)
	         System.out.println(result[x]);
	}
}

```

---

```java title=StringToken05
package BuiltInAPI;

import java.util.StringTokenizer;

// 회원정부 수정폼 등에서 많이 응용하는 특수문자를 기준으로 
// 문자열을 파싱할 때 주로 String클래스 하위에 split()메소드나,
// java.util패키지의 StringTokenizer클래스를 활용한다.
// 이때 분리된 문자부분을 token이라고 한다.

public class StringToken05 {

	public static void main(String[] args) {
		
		String phoneNumber = "010-7777-9999";
		StringTokenizer token = new StringTokenizer(phoneNumber, "-");
		// -을 기준으로 폰번호를 분리한다.
		
		while(token.hasMoreElements() ) {
			// 분리된 문자 요소가 있다면 참
			System.out.println(token.nextToken()); // 010\n7777\n9999
			// nextToken()메소드는 다음 분리된 문자 요소를 가져온다.
		}
		
		System.out.println("====구분선====");
		
		String[] tokenArr = phoneNumber.split("-");
		// -을 기준으로 문자열을 분리해서 분리된 토큰문자가 배열원소값으로 저장된다.
		System.out.println("분리된 폰문자 개수 :" + tokenArr.length); // 분리된 폰문자 개수 :3
		
		for(int i = 0; i < tokenArr.length; i++) {
			System.out.println(tokenArr[i]); // 010\n7777\n9999
		}
				
	}
}

```

---

```java title=calendar06
package BuiltInAPI;

import java.util.Calendar;

// java.util 패키지의 Calendar 추상클래스는 날짜와 시간에 관한 정보를 제공한다.

public class calender06 {

	public static void main(String[] args) {
		
		Calendar cal = Calendar.getInstance();
		
		int year = cal.get(Calendar.YEAR); // 년도값
		int month = cal.get(Calendar.MONTH)+1; // 월값 (시작이 0이기에 맞추기 위해서 +1이 필요함)
		int date = cal.get(Calendar.DATE); // 일값
		int hour = cal.get(Calendar.HOUR_OF_DAY);; // 24시간값
		int minute = cal.get(Calendar.MINUTE); // 분값
		int second = cal.get(Calendar.SECOND); // 초값
		
		System.out.println(year + "년 "+ month + "월 " + date + "일 " + hour + "시 " + minute + "분 " + second + "초");
		// 출력 : 2024년 8월 28일 13시 46분 0초(호출한 당시의 컴퓨터 시간)
	}
}

```

---

```java title=ObjectTest07
package BuiltInAPI;

// Object의 equals()메소드를 상속받아서 사용한다.

class Value07 {
	int value;
	
	// 생성자를 오버로딩 하면 매개변수가 없는 디폴트 기본생성자를 묵시적으로 제공하지 않는다.
	
	Value07(int value) {
		this.value = value;
	}// 생성자 오버로딩
}

public class ObjectTest07 {
	public static void main(String[] args) {
		Value07 v01 = new Value07(100); // 오버로딩 된 생성자를 호출
		Value07 v02 = new Value07(100);
		
		// v01과 v02는 객체주소가 다르다.
		if(v01.equals(v02)) {
			System.out.println("같다");
		} else {
			System.out.println("다르다");
		}
		
		v02 = v01;
		// v01객체주소를 v02에 대입함
		// v01과 v02의 객체 주소가 같아짐
		if(v01.equals(v02)) {
			System.out.println("같다");
		} else {
			System.out.println("다르다");
		}
	}
}

```

---

```java title=ObjectTest08
package BuiltInAPI;

// java.lang 기본패키지 경로는 자바 코드에서 생략가능하다.
// 이 패키지에 있는 Object 최고 조상크래스 하위의 equals()메소드를 
//   자손에서 오버라이딩을 해서 활용하는 실습 예제이다.

class Person{
	long id;
	
	Person(long id) {
		this.id = id;
	} // Person 메소드 생성자 오버로딩

	@Override
	public boolean equals(Object obj) {
		if(obj != null && obj instanceof Person) {
			// obj instanceof Person은 obj가 다운캐스팅이 가능한가>
			// 사전에 업캐스팅을 했다면 True
			return id==((Person)obj).id;
			// 명시적 다운캐스팅
			
		} else {
			return false;
		}// if else
	} // equals()
} // Person Class

public class ObjectTest08 {

	public static void main(String[] args) {
		Person p01 = new Person(92082847777777L);
		Person p02 = new Person(92082847777777L);
		
		if (p01 == p02) {
			// 값을 비교하는 것이 아니라 객체주소를 비교한다.
			System.out.println("같다");
		} else {
			System.out.println("다르다");
		}
		
		if (p01.equals(p02)) {
			// 값만 비교
			System.out.println("같다");
		} else {
			System.out.println("다르다");
		}
		
	}
}

```

---

```java title=EqualsTest09
package BuiltInAPI;

// String 문자열 타입 값 같다 비교는 equals()메소드를 사용해야 한다.

public class EqualsTest09 {

	public static void main(String[] args) {
		
		String pwd01 = "56789";
		String pwd02 = "56789";
		// pwd01과 pwd02는 같은 주소를 가리킨다.
		
		System.out.println("pwd01 == pwd02 ?" + (pwd01 == pwd02));
		// true, String 문자열을 ==로 비교하면 주소값을 비교한다.
		System.out.println("pwd01.equals(pwd02)?" + pwd01.equals(pwd02));
		// true, 문자열을 equals()로 비교하면 문자열의 '값'만 비교한다.
		
		String pwd03 = new String("12345");
		String pwd04 = new String("12345");
		// pwd03과 pwd04는 다른 주소를 가진다.
		
		System.out.println("pwd03 == pwdo4 ?" + (pwd03 == pwd04));
		// false, ==로 비교하면 주소값을 비교한다.
		System.out.println("pwd03.equals(pwd04)" + pwd03.equals(pwd04));
		// true, 실직적은 객체의 '값' 은 같다
		
	}
}

```

---

```java title=StringMethod10
package BuiltInAPI;

// String 내장 API클래스 하위의 내장메소드에 관한 소스

public class StringMethod10 {
	public static void main(String[] args) {
		
		String cityName = "Seoul";
		char result = cityName.charAt(1);
		// charAt()은 첫문자를 주소 0부터 시작해서 인수+1번째 단일문자를 구함
		System.out.println(result); // e
		
		boolean re = cityName.equals("seoul");
		// equals()메소드는 영문 대/소문자를 구분하면서 같다를 비교한다.
		System.out.println(re); // false
		
		// 대소문자를 구문하지 않고 비교
		re = cityName.equalsIgnoreCase("seoul");
		// equalsIgnoreCase() 메소드는 영문 대소문자를 무시하고 같다를 비교한다.
		System.out.println(re); // true
		
		int indexNumber = cityName.indexOf('e');
		// 'e'에 해당하는 문자를 맨왼쪽에서 부터 찾아서 가장 먼저 나오는 해당 단일문자 위치번호를 구함.
		System.out.println(indexNumber+1); // 2
		// +1을 하는 이유 : indexOf는 0자리부터 시작하기 때문에 x번째 라고 찾기위해선 +1값을 더해야 함
		
		indexNumber=cityName.indexOf('n');
		// 해당 단일문자가 존재하지 않으면 -1 반환
		System.out.println(indexNumber); // -1
		
		System.out.println("/'Seoul/'의 문자길이 =" + cityName.length()); // 5
		// length()메소드는 문자길이를 반환하고 첫문자를 1부터 카운트
		
		//문자변경
		String s = "Hello";
		String s01 = s.replace("H", "c");
		// Hello문자에서 H를 C로 변경
		System.out.println(s01); // Cello
		
		// ,구분자 기호를 기준으로 문자를 파싱한다.
		// 분리된 문자를 토큰 문자라고 한다.
		String animals = "cat,dog,bear";
		// 문제) ,를 기준으로 문자를 파싱해서 토큰문자를 만들어서 
		//   배열원소값으로 저장한 다음 일반for와 향상된 확장for를 사용해서 토큰문자 즉 파싱된 문자를 출력
		String[] animalsArr = animals.split(",");
		
		// 일반 for
		for(int i = 0; i < animalsArr.length; i++) {
			System.out.println(animalsArr[i]); // cat\ndog\nbear
		}
		System.out.println("====구분선====");
		// 확장 for
		for(String animal : animalsArr) {
			System.out.println(animal); // cat\ndog\nbear
		}
		
		System.out.println("====구분선====");
		String obj = "java.lang.Object";
		
		// 문제1 : obj변수 문자열값에서 첫문자를 0부터 카운터 해서 
		//    10이후 마지막 문자 즉 "Object"가 나오게 만드는 코드를 완성하자.
		// 문제2 : obj변수 문자열값에서 첫문자를 0부터 시작해서 
		//    5이상 9미만 사이의 문자 "lang"을 구하는 코드를 만들어 보자
		
		String result01 = obj.substring(10);
		// obj변수의 문자열에 인수부터 마지막까지 저장
		System.out.println("\'java.lang.Object\'에서 10이후 부터 마지막 문자 =" + result01);
		
		result01 = obj.substring(5, 9);
		System.out.println("\'java.lang.Object\'에서 5이상 10미만의 문자 =" + result01);
		
		obj = "OBJect";
		System.out.println("\'OBJect\' 영문대문자를 소문자로 변경 =" + obj.toLowerCase());
		
		String objTrim = " Busan ";
		System.out.println("\' Busan \' 양쪽 공백을 제거 =" + objTrim.trim());
	}
}

```

---

```java title=StringMethod11
package Example;

// String 문자열 클래스 하위의 내장메소드를 활용해서 자료실을 만들때 
//   즉 첨부파일에서 확장자를 뺀 파일명과 파일명을 뺀 확장자만 구하는 소스이다.

// 문제
// 위의 타이틀 소스 제목을 참조하고 String 클래스의 
// 내장메소드 indexOf(), subString(), length()를 활용하여 원하는 파일명과 확장자를 구하는 코드 작성

public class StringMethod11 {
	public static void main(String[] args) {
		
		String fileName = "Hello.java";
		// 첨부 파일명
		
		int fileName_index = fileName.indexOf(".");
		String fileName_Name = fileName.substring(0, fileName_index);
		String fileName_Extension = fileName.substring(fileName_index+1);
		
		System.out.println("파일명 : " + fileName_Name);
		System.out.println("확장자 : " + fileName_Extension);
		System.out.printf("확장자 : %s%n" ,fileName_Extension);
		// %s는 문자열 출력형태, %n은 줄바꿈
	}
}

```

---

```java title=StringBuffer12
package Example;

// StringBuffer 내장 API클래스 하위에는 부모 Object 메소드 중 
//   equals()메소드를 오버라이딩 하지 않았으므로 제대로된 문자열 값 비교를 못한다.
// String 내장 클래스에는 오버라이딩 된 equals()메소드가 존재한다.
// StringBuffer를 String으로 변환해야 한다.

public class StringBuffer12 {

	public static void main(String[] args) {
		StringBuffer pwd01 = new StringBuffer("56789");
		StringBuffer pwd02 = new StringBuffer("56789");
		
		System.out.println("pwd01 == pwd02 : "+ (pwd01 == pwd02)); // pwd01 == pwd02 : false
		System.out.println("pwd.equals(pwd02) : " + pwd01.equals(pwd02)); // pwd.equals(pwd02) : false
		
		// 문제
		// 문자열 참조타입 값 '같다' 비교를 ==로 하면 객체주소를 비교한다.
		// equals() 메소드로 문자열 값만 비교해도 false 이다.
		// 위의 결과물을 참조해서 문자열 값만 비교하게 해서 True가 나오게 하자
		System.out.println("pwd01.toString().equals(pwd02.toString()) : " + pwd01.toString().equals(pwd02.toString())); // pwd.equals(pwd02) : True
		System.out.println("pwd01.substring(0).equals(pwd02.substring(0)) : " + pwd01.substring(0).equals(pwd02.substring(0))); // pwd.equals(pwd02) : True
		
		// 강사님
		System.out.println("pwd01.toString().equals(pwd02.toString()) : " + 
		 pwd01.toString().equals(pwd02.toString())); // True
		// pwd01.toString().equals()를 메소드 체이닝 방법이라고 함.
		// 메소드 체이닝 방법은 두줄이상을 코드를 해야하며 
		//   dot(.)으로 구분해서 한줄로 나열해서 코드를 간략하게 하는 방법
		
		// 메소드 체이닝 안쓸경우
		String result01 = pwd01.toString();
		String result02 = pwd02.toString();
		System.out.println("result01.equals(result02)=" + result01.equals(result02)); // True
	}

}

```

---

2024-08-29

```java title=listEx01
package Collection;

import java.util.ArrayList;
import java.util.List;

// java.util패키지의 Collection List Interface 자료구조 특징
// 1. 중복원소값을 허용한다.
// 2. 순서있게 저장된다.

public class ListEx01 {
	public static void main(String[] args) {
		List list = new ArrayList();
		
		list.add(100);
		list.add(100.9);
		list.add(100);
		list.add("홍길동");
		list.add(true);
		
		System.out.println("원소개수 : "+ list.size()); // 5
		
		// 일반 for로 컬렉션 원소 값 출력
		for(int i = 0; i < list.size(); i++) {
			System.out.println("원소 : " + list.get(i));
		}
	}
}

```

---

``` java Title=IteratorEx02
package Collection;

import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;

// java.util패키지의 Iterator 인터페이스 특징
// 1. jdk1.2에서 추가되었기 때문에 같은 버전에서 추가된 Collection API에 
//    저장된 복수개의 요소값을 쉽게 읽어오는 용도로 사용된다.
// 2. 한번 사용하면 재 사용못한다. 다시 사용할려면 새롭게 생성해서 사용해야 한다.

public class IteratorEx02 {
	public static void main(String[] args) {
		List list = new ArrayList();
		
		list.add(7);
		list.add(10.3);
		list.add(7);
		list.add("서울시");
		list.add("부산시");
		list.add(false);
		
		Iterator elements = list.iterator();
		while(elements.hasNext()) {
			// 읽어온 다음 요소값이 있다면 참
			System.out.print(" " + elements.next());
			// next() 메소드로 다음 요소값을 가져온다.
		}
		
		// 재사용 불가
		while(elements.hasNext()) {
			System.out.print(" " + elements.next());
		}
	}
}

```

---

```java title=EnumerationEx03
package Collection;

import java.util.Enumeration;
import java.util.Vector;

// java.util패키지의 Enumeration 인터페이스 특징
// 1. jdk1.0에서 추가되었고, 같은 버전에서 추가된 Collection API에 
//    저장된 복수개의 원소값을 읽어오는 용도로 사용된다.
// 2. 한번 사용하면 재사용 불가한다.

public class EnumerationEx03 {
	public static void main(String[] args) {
		
		Vector vec = new Vector();
		for(int i = 1; i <= 5; i++) {
			vec.add(new Integer(i * 10));
		} // for
		
		Enumeration enu = vec.elements();
		while(enu.hasMoreElements()) {
			// vec값에 원소값이 있다면 참
			System.out.println(enu.nextElement());
			// nexElement() 메소드로 다음요소값을 가져온다
		} // while
		
		System.out.println("===구분선====");
		// 일반 for로 컬렉션 원소값 읽어오기
		for(int i = 0; i < vec.size(); i++) {
			System.out.println("\t" + vec.get(i));
		} // for
	}
}

```

---

```java title=VectorEx04
package Collection;

import java.util.Vector;

// java.util패키지의 Vector Collection 클래스에 관한 Search and Delete 예제
// 1. jdk 1.0에서 추가됨

public class VectorEx04 {
	public static void main(String[] args) {
		
		Vector vec = new Vector();
		double[] arr = {38.6, 9.2, 45.3, 6.1, 4.7, 1.6};
		
		for(int i = 0; i < arr.length; i++) {
			vec.add(arr[i]);
			// vec에 배열 요소값 추가
		}
		
		System.out.println("\n >> vec 요소값 출력 <<");
		for(int i = 0; i < vec.size(); i++) {
			System.out.print(" " + vec.get(i));
		}
		System.out.println(); // 줄바꿈
		
		double searchData = 6.1;
		int index = vec.indexOf(searchData);
		// index변수에 vec배열요소에서 searchData값의 주소값 할당
		
		if(index != -1) {
			System.out.println("\n 검색 성공" + index);
		} else {
			System.out.println("\n 검색 실패" + index);
		}
		
		double delData = 45.3;
		if(vec.contains(delData)) {
			// delData(45.3)이 vec 배열 요소값에 포함되어 있다면 참
			// contains() 메소드는 인수값의 데이터가 배열에 있는지 확인
			vec.remove(delData); // 해당 배열요소값 삭제
			System.out.println("\n 삭제 완료");
		}
		
		System.out.println("\n >> 삭제후 전체 벡터 요소값 출력<<");
		for(int i = 0; i < vec.size(); i++) {
			System.out.println("vec 요소 값은 : " + vec.get(i));
		}
	}
}

```

---

```java title=StackEx05
package Collection;

import java.util.Stack;

// java.util패키지의 Stack Collection Class 특징
// 1. jdk.10에서 추가됨
// 2. 입구와 출구가 같다. 가장 먼저 입력된것이 가장 나중에 출력된다 (First Input Last Output:FILO)
// 3. 가장 나중에 입력 된것이 가장 먼저 출력된다.

public class StackEx05 {
	public static void main(String[] args) {
		
		Stack myStack = new Stack();
		myStack.push("1-Java");
		// push()메소드로 Stack에 요소값 입력
		myStack.push("2-Linux");
		myStack.push("3-Oracle");
		
		while(!myStack.isEmpty()) {// myStack이 비어있지 않다면
			// isEmpty() 메소드는 : 요소가 비어있다면 참
			System.out.println(myStack.pop());
			// pop()메소드로 스택의 맨위의 원소값을 제거하면서 출력한다.
		}
	}
}

```

---

```java title=LikedQueEx06
package Collection;

import java.util.LinkedList;

// javautil 패키지의 Queue Collection Interface를 구현 상속한 LinkedList Collection 특징
// 1. Linked Collection 자료구조는 입구와 출구가 다르다.
// 2. 먼저 입력된 것이 먼저 나가는 구조이다(First Input First Output: FIFO)

public class LinkedQueEx06 {
	public static void main(String[] args) {
		
		LinkedList myQue = new LinkedList();
		myQue.offer("1-Java");
		// offer() 메소드를 활용해 요소값 추가
		myQue.offer("2-Oracle");
		myQue.offer("3-HTML");
		
		while(myQue.peek() != null) { 
			// peek() 메소드는 myQue의 요소가 있는지 확인
			System.out.println(myQue.poll());
			// poll() 메소드는 myQue로 부터 데이터를 꺼낸다.
		}
	}
}

```

---

```java title=Collection07
package Collection;

import java.util.Enumeration;
import java.util.Hashtable;

// java.util패키지의 Map Collection Interface를 구현 상속한 Hashtable Collection Class 특징
// 1. Hashtable Collection Class는 JDK1.0에서 추가됨
// 2. 해당 Collection은 키, 값 쌍으로 저장하는 영어 사전적인 자료구조
// 3. 키를 통해서 값을 검색하기 때문에 검색속도가 빠르다.

public class HashTable07 {
	public static void main(String[] args) {
		Hashtable ht = new Hashtable();
		
		ht.put("apple", "사과");
		// key : apple / value : 사과 저장
		ht.put("grape", "포도");
		ht.put("peach", "복숭아");
		ht.put("banana", "바나나");
		ht.put("watermelon", "수박");
		// key, value 쌍으로 저장될 때 Java 최상위 Object type으로 업캐스팅 하면서 추가
		
		if(ht.get("peach") instanceof String) {
			// 다운캐스팅이 가능한가?
			String val = (String)ht.get("peach");
			// peach key에 대한 value을 구함. (명시적인 다운캐스팅)
			if(val != null) {
				System.out.println("peach => " + val);
			}
		}
		
		Enumeration enum2 = ht.keys();
		while(enum2.hasMoreElements()) {
			 Object K = enum2.nextElement(); 
			// 키값을 구함
			
//			String K= "";
//			if(enum2.nextElement() instanceof String) {
//				// 다운캐스팅이 가능한가?
//				K = (String)enum2.nextElement();
//			}
			
//			Object v = ht.get(K);
			// key에 대한 value를 구함
			
			String v = "";
			if(ht.get(K) instanceof String) {
				// 다운캐스팅이 가능한가?
				v = (String)ht.get(K);
			}
			
			System.out.println(K + " : " + v);
		}
	}
}

```

---

```java title=ListTieratorEx08
package Collection;

import java.util.ArrayList;
import java.util.ListIterator;

// java.util 패키지의 ListIterator 인터페이스 특징
// 1. jdk 1.2에서 추가되었고, Iterator Interface를 구현 상속했음
// 2. Iterator Interface는 단방향 즉 다음방향으로만 이동하지만 ListIterator Interface는 양방향 이동이 가능하다.
// 3. ListIterator Interface는 List Collection Interfece를 구현 상속한 
//    자손 Collection Class에서만 주로 사용이 되어지며
// 4. Collection Elements값을 양방향으로 읽어오는 용도로 사용한다.

public class ListiteratorEx08 {
	public static void main(String[] args) {
		
		ArrayList list = new ArrayList();
		list.add("1");
		// Java 최상위 클래스 Object 타입으로 업캐스팅 하면서 저장
		list.add("2");
		list.add("3");
		list.add("4");
		list.add("5");
		
		ListIterator it = list.listIterator();
		// 양방향 조회
		
		// 단방향 조회
		while(it.hasNext()) { // 다음 요소값이 존재한다면 참
			System.out.print(" " + it.next()); // 1 2 3 4 5
			// next() 메소드로 다음 원소값을 가져온다.
		}
		System.out.println("\n ===========================>");
		
		// 역방향 조회
		while(it.hasPrevious()) { // 이전 요소값이 존재한다면 참
			System.out.print(" " + it.previous()); // 5 4 3 2 1
			// previous()메소드는 이전 요소값을 가져온다.
		}
		System.out.println("\n ===========================>");
	}
}

```

---

```java title=HashMapEx09
package Collection;

import java.util.HashMap;
import java.util.Scanner;

// java.util패키지의 Map Collection Interface를 구현 상송받은 HashMap Collection Class 특징
// 1. jdk 1.2버전에서 추가됨
// 2. key, value쌍으로 저장되는 영어 사전적인 자료구조이다.
// 3. key를 통해서 값을 검색하기 때문에 검색속도가 빠르다.
// 4. 저장되는 순서를 보장하지 않는다.

public class HashMapEx09 {
	public static void main(String[] args) {
		HashMap map = new HashMap();
		map.put("myid", "1234");
		// key, value 쌍으로 저장. key 는 id이고 value는 password
		map.put("asdf", "56789");
		
		Scanner scan = new Scanner(System.in);
		
		while(true) {
			System.out.println("아이디와 비번을 입력해주세요!");
			System.out.println("ID >>");
			String ID = scan.nextLine().trim();
			// trim() 메소드로 scan.nexLine()으로 입력되는 '문자열'에 양쪽 공백을 제거
			
			System.out.println("Password >>");
			String Password = scan.nextLine().trim();
			System.out.println();
			
			if(!map.containsKey(ID)) {
				// map Class내 ID(사용자 입력값)가 없다면 참
				System.out.println("입력하신 ID가 존재하지 않습니다!");
				System.out.println("다시 ID를 입력해주세요!");
				continue;
				// continue : 아래문장을 실행하지 않고 다음 반복을 위해 반복문 처음(while)으로 돌아간다.
			} else if (!map.get(ID).equals(Password)){
				// get() 메소드는 인수의 값과 같은 map class key값의 해당하는 value값을 가져온다.
				// map Class내 에서 key값의 해당하는 value값과 Password(사용자입력값)이 맞지않다면 참
				System.out.println("비번이 일치하지 않습니다.");
				System.out.println("다시 입력해주세요!");
			} else {
				System.out.println("아이디와 비번이 일치합니다!");
				break;
				// 반복문(while) 종료
			}
		}
	}
}

```

---

```java title=GenericList10
package CollectionGeneric;

import java.util.ArrayList;
import java.util.List;

// jdk 1.5(자바 5버전)에서 추가된 Collection Generic 특징
// 1. <String>Generic Type을 지정하면 해당 Collection에는 문자열 값만 저장가능하다.
// 2. Generic Type으로 기본타입은 안되고 reference Type만 가능하다.

public class GenericList10 {
	public static void main(String[] args) {
		List<String> nameList = new ArrayList<String>();
		// Collection nameList에는 문자열만 저장가능하다.
		
		nameList.add("gil dong Hong");
		nameList.add("sun shin Lee");
		nameList.add("sot got Kim");
		
		// 일반 for반복문으로 영문대문자로 변경해서 출력
		for(int i = 0; i < nameList.size(); i++) {
			System.out.println("영문소문자 이름을 영문대문자로 변경하여 출력 : " + nameList.get(i).toUpperCase());
			// get(i) 메소드로 해당 요소값을 가져옴.
			// toUpperCase()메소드로 영문대문자로 변경.
		}
		
		// 문제 <Integer>Generic(Generics) Type으로 ListCollection Type 객체 numberList를 생성하고 
		// 수학점수로 100, 90, 100, 80 4개의 점수를 저장한 다음
		// 향상된 확장for 반복문을 사용해서 점수 총합을 구해서 
		// 총합과 평균을 출력하는 알고리즘 프로그램코드를 해보자
		
		List<Integer> numberList = new ArrayList<Integer>();
		
		numberList.add(100);
		numberList.add(95);
		numberList.add(92);
		numberList.add(24);
		
		int Total = 0;
		double avg = 0;
		for(int result : numberList) {
			// numberList(참조형 wrapper) => result(기본형) 변경됨으로 autoUnBoxing
			Total += result;
		}
		avg = Total / (double)numberList.size();
		// 자동산술법 : 실수 숫자를 나눗셈하면 몫과 나머지를 구하며, 정수 숫자끼리 나눗셈하면 몫만 구하게된다.
		System.out.println("점수 총합 : " + Total);
		System.out.println("평균 : " + avg);
	}
}

```

---

```java title=GenericHashtable11
package CollectionGeneric;

import java.util.Enumeration;
import java.util.Hashtable;

// java.util의 Hashtable Collection Class에 Generic type을 지정한다.

public class GenericHashtable11 {
	public static void main(String[] args) {
		Hashtable<String, String> ht = new Hashtable<String, String>();
		// 문자열타입 key, value 쌍으로 저장 가능한 Collection Generic ht 생성
		
		ht.put("grape", "포도");
		ht.put("strawberry", "딸기");
		ht.put("pear", "배");
		ht.put("apple", "사과");
		
		String value = ht.get("apple");
		// 'apple' key에 대한 value를 구함
		
		if(value != null) {
			System.out.println("apple => " + value); // apple => 사과
		}
		
		Enumeration<String> enu2 = ht.keys();
		// ht의 key를 읽어오기 위함
		
		while(enu2.hasMoreElements()) {
			// enu2의 요소가 있다면
			String key = enu2.nextElement();
			// enu2의 다음 요소를 구함
			String val = ht.get(key);
			// get()메소드로 ht에 key에 해당하는 value값을 val에 저장함
			System.out.println(key + " : " + val); 
			// apple : 사과\npear : 배\nstrawberry : 딸기\ngrape : 포도
		}
	}
}

```

---

```java title=GenericHashMap12
package CollectionGeneric;

import java.util.HashMap;
import java.util.Map;

// java.util 패키지의 Collection Map Interface를 구현상속한 Collection Class HashMap 특징
// 1. jdk1.2(java2) 버전에서 추가됨
// 2. key, value 쌍으로 저장하는 여영어 사전적인 자료구조이다.
// 3. key를 통해서 값을 검색하기 때문에 검색 속도가 빠르다.

public class GenericHashMap12 {
	public static void main(String[] args) {
		
		Map<String, Integer> map = new HashMap<>();
		// 뒷부분 Generic Type은 생략가능함(jdk 1.7(자바 7버전)에서 추가됨)
		
		String[] sample = {"to", "be", "or", "not", "to", "be", "is", "a", "problem"};
		
		// 향상된 확장 for반복문
		for(String key: sample) {
			Integer freq = map.get(key);
			// Collection Map으로 부터 key에 대한 value를 구함.
			map.put(key, (freq==null)? 1: freq+1);
			
			System.out.println(map.size() + "단어가 있습니다.");
			System.out.println(map.containsKey("to"));
			// 'to' key가 Map Collection에 포험되어 있다면 참
			System.out.println(map);
		}
	}
}

```

---

```java title=GenericClass13
package CollectionGeneric;

// Generic Class 설계에 관한 실습 예제

class GenericClass<T> {
	// Generic <T>타입 Class 정의
	private T member;

	public T getMember() {
		return member;
	} // 값 반환 메소드 => getter() 메소드

	public void setMember(T member) {
		this.member = member;
	} // 값 저장 메소드 => setter() 메소드
}

public class GenericClass13 {
	public static void main(String[] args) {
		
		GenericClass<Double> obj01 = new GenericClass<Double>();
		// 뒷부분 Generic Type은 생략가능 (java 7버전에서 추가)
		
		obj01.setMember(100.37);
		System.out.println("반환값 = " + obj01.getMember());
		
		GenericClass<Integer> obj02 = new GenericClass<>();
		obj02.setMember(100);
		System.out.println("되돌리는 값 = " + obj02.getMember());
		
		GenericClass<String> obj03 = new GenericClass<>();
		obj03.setMember("홍길동");
		System.out.println("반환 이름 : " + obj03.getMember());
	}
}

```

---

```java title=GenericType14
package CollectionGeneric;

import java.util.ArrayList;
import java.util.List;

// Generic Type으로는 기본타입은 안되고 참조 타입만 가능하다.
// 1. Generic Type reference 간의 형변환은 원래 허용하지 않는다.

public class GenericType14 {
	public static void main(String[] args) {
		
		List<String> list = new ArrayList<String>();
		list.add("Seoul");
		list.add("Busan");
		list.add("Incheon");
		list.add("Daegu");
		
		List<Object> objlist;
//		objlist = list;
//		// Error... Type mismatch: cannot convert from List<String> to List<Object>
		
//		for(Object obj: objlist) {
//			String cityName = (String)obj;
//			// 명시적인 다운캐스팅
//		}
	}
}

```

---

```java title=GenericTitle15
package CollectionGeneric;

import java.util.ArrayList;
import java.util.List;

// 원래 자바문법에서 Generic Type reference간의 형변환은 허용하지 않지만 
// Generic WildeCard 문법을 사용하면 일부분 Generic Type reference 간의 형변환을 허용한다.
// 상한제한 와일드 카드 문법:
//   <? extends Object> 은 Object을 상속받은 자손에 한해서만 Generic Type 간의 reference 간의 형변환을 일정부분 허용한다.

public class GenericType15 {
	public static void main(String[] args) {
		
		List<String> citylist = new ArrayList<>();
		citylist.add("Seoul");
		citylist.add("Busan");
		
		List<? extends Object> objlist;
		// Object를 상속받고 있다면 형변환을 인정한다.
		objlist = citylist;
		// Generic Type 간의 형변환 허용
		
		for(Object obj: objlist) {
			if(obj instanceof String) {
				// obj는 String의 인스턴스 인가?
				String cityName = (String)obj;
				// 명시적인 다운캐스팅
				System.out.println(cityName.toUpperCase());
				// 영문대문자로 변경해서 출력
			}
		}
	}
}

```