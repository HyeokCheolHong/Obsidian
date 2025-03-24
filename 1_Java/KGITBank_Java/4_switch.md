# Switch-case

![[Pasted image 20240807175316.png|500]]


## Switch 문법 1

```java title=Ex01
package switch_;

public class Ex01 {

	public static void main(String[] args) {
		/*
		 * F11 : 디버깅 시작 모드
		 * F6 : 한 줄 실행 (무조건)
		 * F5 : 한 줄 실행 (메소드 이동)
		 * F8 : 다음 브레이크 포인터 이동
		 */
		
		int select = 1;
		
		switch (select) {
			case 1: System.out.println("1입력"); break;
			case 2: System.out.println("2입력"); break;
			default: System.out.println("그 외의 값 입력"); break;
		}
		System.out.println("다음 문장들 실행!!!");
		
		
		char ch = 'a';
		
		switch (ch) {
			case 'a': // System.out.println("a입력"); break;
			case 'A': System.out.println("A입력"); break;
			default: System.out.println("그 외의 값 입력"); break;
		}
		
		
		
	}

}

```



```java title=Ex02
package switch_;

import java.util.Scanner;

public class Ex02 {

	public static void main(String[] args) {
		Scanner input = new Scanner(System.in);
		
		int num, result;
		
		System.out.print("수 입력 : ");
		num = input.nextInt();
		result = num % 2;
		
		switch (result) {
			case 0:
				System.out.println("짝");
				break;
			default:
				System.out.println("홀"); 
				break;
		}
		
		System.out.print("문자열 입력 : ");
		String str = input.next();
		
		switch (str) {
			case "안녕": System.out.println(str + " 하세요"); break;
			case "그래": System.out.println(str + " 반갑다"); break;
		}
		
		

	}

}

```



```java title=Ex03
package switch_;

import java.util.Scanner;

public class Ex03 {

	public static void main(String[] args) {
		Scanner input = new Scanner(System.in);
		String name;
		
		while(true) {
			System.out.print("문자열 입력 : ");
			name = input.next();
			System.out.println("입력받은 문자열 : " + name);
		}
	}

}

```



## Switch Quiz
![[Pasted image 20240807175610.png|500]]

![[Pasted image 20240807175628.png | 150]]

![[Pasted image 20240807175651.png | 150]]

```java title=Quiz
package switch_;

import java.util.Scanner;

public class Quiz {
	public static void main(String[] args) {
		Scanner input = new Scanner(System.in);
		
		// 날짜를 입력받아 1일이면 월요일, 2: 화요일, ... 7일: 일요일, 8일: 월요일 숫자에 맞춰 요일을 출력
		System.out.print("날짜 입력 : ");
		int day = input.nextInt();
		int week = day % 7;
	
		String weekStr = null;
		
		switch(week) {
			case 0: weekStr = "일요일"; break;
			case 1: weekStr = "월요일"; break;
			case 2: weekStr = "화요일"; break;
			case 3: weekStr = "수요일"; break;
			case 4: weekStr = "목요일"; break;
			case 5: weekStr = "금요일"; break;
			case 6: weekStr = "토요일"; break;
		}
		System.out.println(weekStr);
		
		
		//우리집, 회사 등록 후 보기
		String message = "1. 우리집 등록\n" + "2. 회사 등록\n" + "3. 등록 보기";
		String myHome = null;
		String myCom = null;
		
		while(true) {
			System.out.println(message);
			int select = input.nextInt();
			String tempStr = null;
			
			boolean isNullCheck = myHome != null && myCom != null;
			if(select == 3)	select = isNullCheck ? select : 0;
			
			switch(select) {
				case 1: 
					System.out.print("우리집 목적지 입력 : ");
					myHome = input.next();
					break;
				case 2: 
					System.out.print("회사 목적지 입력 : ");
					myCom = input.next();
					break;
				case 3: 
					System.out.println("우리집 : " + myHome);
					System.out.println("회사 : " + myCom);
					break;
				case 0:
					System.out.println("집, 회사 정보 입력");
					break;
			}
			
			if (select == 3 && isNullCheck) break;
			
		}
		
		
		/* chatGPT 코드 참고해서 작성한 것 */
		message = "1. 우리집 등록\n" + "2. 회사 등록\n" + "3. 등록 보기";
		myHome = null;
		myCom = null;
		
		while(true) {
			System.out.println(message);
			int select = input.nextInt();
			String tempStr = null;
			boolean needsInput = false;
			
			switch(select) {
				case 1: 
					tempStr = "우리집 목적지 입력 : ";
					needsInput = true;
					break;
				case 2: 
					tempStr = "회사 목적지 입력 : ";
					needsInput = true;
					break;
				case 3: 
					if (myHome != null & myCom != null) {
						tempStr = "우리집 : " + myHome + "\n" + "회사 : " + myCom + "\n";
					} else {
						tempStr = "회사 및 우리집 정보 입력\n";
					}
					break;
			}
			System.out.print(tempStr);
			// 내가 만든거
//			if(select == 1) myHome = input.next();
//			else if(select == 2) myCom = input.next();
//			else if(select == 3 && myHome != null & myCom != null) break;
			
			// GPT가 개선한거
			if(needsInput) {
				String userInput = input.next();
				
				if (select == 1) myHome = userInput;
				else if (select == 2) myCom = userInput;
				
				System.out.println("등록 성공");
			}
			
			
		}
		
	}
	
}
```



## Switch 문법 2

```java title=SwitchCharExample
package ch04.sec03;

public class SwitchCharExample {

	public static void main(String[] args) {
		char grade = 'B';
		
		switch(grade) {
			case 'A':
			case 'a': System.out.println("우수 회원입니다."); break;
			case 'B':
			case 'b': System.out.println("일반 회원입니다."); break;
			default : System.out.println("손님입니다.");
		}
	}
}

```



## Switch Expressions
- ==Java 12== 버전 이후부터는 switch 문에서 Expressions(표현식)를 사용할 수 있다.
  break 문을 없애는 대신에 화살표와 중괄호를 사용해 가독성이 좋아졌다.

```java title=
package ch04.sec03;

public class SwitchExpressionsExample {

	public static void main(String[] args) {
		char grade = 'B';
		
		// 여러 줄 일 때는 중괄호 써야함
		switch(grade) {
			case 'A', 'a' -> { 
				System.out.println("우수 회원입니다.");
				System.out.println("축하드려요!");
			}
			case 'B', 'b' -> { 
				System.out.println("일반 회원입니다."); 
				System.out.println("축하드려요!");				
			}
			default -> { 
				System.out.println("손님입니다");
				System.out.println("어서오세요!");
			}
			
		}
		
		
		// 실행문 하나일 경우에는 중괄호 생략 가능
		switch(grade) {
			case 'A', 'a' -> System.out.println("우수 회원입니다!");
			case 'B', 'b' -> System.out.println("일반 회원입니다!");
			default -> System.out.println("손님입니다!");
		}
		
	}

}

```



### 변수에 대입, yield
- Switch Expresstions를 사용하면 스위치 된 값을 변수에 바로 대입할 수도 있다.
  단일 값일 경우에는 화살표 오른쪽에 값을 기술하면 되고, 중괄호를 사용할 경우에는 ==Java 13==버전부터 사용 가능한 yield 키워드로 값을 지정하면 된다.
  단, 이 경우에는 default가 반드시 존재해야 한다.

```java title=SwitchValueExample
package ch04.sec03;

public class SwitchValueExample {

	public static void main(String[] args) {
		char grade = 'B';
		int score1 = 0;
		
		// Java 11 이전 문법
		switch(grade) {
			case 'A': score1 = 100; break;
			case 'B': 
				int result = 100 - 20;
				score1 = result;
				break;
			default : score1 = 60;
		}
		System.out.println("score1 : " + score1);
		
		
		// Java 13 이후 추가된 문법(Switch Expresstions)
		int score2 = switch(grade) {
			case 'A' -> 100;
			case 'B' -> {
				int result = 100 - 20;
				yield result;
			}
			default -> 60;
		};
		System.out.println("score2 : " + score2);
		
	}

}

```


```java title=SwitchValueExample
package ch04.sec03;

public class SwitchValueExample {

	public static void main(String[] args) {
		char grade = 'B';
		int score1 = 0;
		
		// Java 11 이전 문법
		switch(grade) {
			case 'A': score1 = 100; break;
			case 'B': 
				int result = 100 - 20;
				score1 = result;
				break;
			default : score1 = 60;
		}
		System.out.println("score1 : " + score1);
		
		
		// Java 13 이후 추가된 문법(Switch Expresstions)
		int score2 = switch(grade) {
			case 'A' -> 100;
			case 'B' -> {
				int result = 100 - 20;
				yield result;
			}
			default -> 60;
		};
		System.out.println("score2 : " + score2);
		
		
		int score3 = switch(grade) {
			case 'A', 'a', 'c' -> 100;
			case 'B', 'b' -> 200;
			default -> 0;
		};
		System.out.println("score3 : " + score3);
		
	}

}

```





















































