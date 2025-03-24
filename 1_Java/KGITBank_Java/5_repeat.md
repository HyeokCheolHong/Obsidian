# 반복문(for, while)

![[Pasted image 20240807175718.png|500]]

![[Pasted image 20240807175940.png|500]]


```java title=Ex01
package repeat_;

public class Ex01 {

	public static void main(String[] args) {
		int sum = 0;
		int i = 1;
		
		for(i = 1; i <= 10; i++) {
			System.out.println(i);
			sum = sum + i;
		}
		System.out.println("i : " + i);
		
		
		int j = 1, sum2 = 0;
		while(j <= 10) {
			System.out.println(j);
			sum2 = sum2 + j;
			j++;
		}
		System.out.println("sum2 : " + sum2);
		
		
		// 1 ~ 10까지의 총합, 홀합, 짝합을 구하세요
		int totalSum = 0;
		int oddSum = 0;
		int evenSum = 0;
		
		i = 1;
		
		for (i = 1 ; i <= 10 ; i++) {
			if(i % 2 == 0) {
				evenSum += i;
			} else {
				oddSum += i;
			}
			totalSum += i;
		}
		System.out.println("totalSum : " + totalSum + ", " + "evenSum : " + evenSum + ", " + "oddSum : " + oddSum);
		
		
		
	}

}

```



```java title=Ex02
package repeat_;

public class Ex02 {

	public static void main(String[] args) {
		int i = 1;
		for (i = 1 ; i <= 10 ; i++) {
			if(i % 2 == 0) {
				System.out.println(i + " : 짝");
			} else {
				System.out.println(i + " : 홀");
			}
		}
		
		System.out.println("=======================");
		
		i = 1;
		while(i <= 10) {
			if(i % 2 == 0) {
				System.out.println(i + " : 짝");
			} else {
				System.out.println(i + " : 홀");
			}
			i++;
		}
		
	}

}

```



## 반복문 Quiz

![[Pasted image 20240807180008.png]]


```java title=Ex03
package repeat_;

public class Ex03 {

	public static void main(String[] args) {
//		while(true) {
//		for( ; ; ) {
//			System.out.println("while");
//		}
		
		
		
		for(int k = 0 ; k < 3 ; k++) {
			System.out.println("for : " + k);
		}
		
		int i = 0;
		while(i < 3) {
			System.out.println("for : " + i);
			i++;
		}
		
		String line = "";
		
		for (i = 1; i <= 25; i++) {
//			System.out.print(i + "\t");
//			
//			if(i % 5 == 0) System.out.println();
			
			line += i % 5 != 0 ? i + "\t" : i + "\n";
		}
		System.out.println(line);
		
		
		
	}

}
```



***



# 반복문 제어(break, continue)

![[Pasted image 20240807180021.png|400]]


```java title=Ex04
package repeat_;

public class Ex04 {

	public static void main(String[] args) {
		boolean bool = true;
		int i = 0;
		
		for( ; bool ; ) {
			i++;
			System.out.println(11);
			
			if( i > 3) bool = false;
		}
		
		i = 0;
		while(true) {
			i++;
			System.out.println(i);
			if(i > 3) break;
		}
		
		System.out.println("-------------------------");
		
		i = 0;
		for ( ; i < 5 ; ) { 
			i++;
			if(i == 3) {
				System.out.println(33333);
				continue;
			}
			System.out.println("i : " + i);
		}
		
		
		
	}

}
```



```java title=Ex05
package repeat_;

import java.util.Scanner;

public class Ex05 {

	public static void main(String[] args) {
		Scanner input = new Scanner(System.in);
		
		int i, sum = 0;
		while(true) {
			System.out.print("1 ~ 10 사이 수 입력 : ");
			i = input.nextInt();
			
			if (i <= 0 || i > 10) {
				System.out.println("다시 입력...");
				continue;
			}
			break;
		}
		
		for (int k = 0 ; k <= i ; k++) {
			sum += k;
		}
		System.out.println("1 ~ " + i + " 까지의 합 : " + sum);
		
		
		
	}

}

```



```java title=Ex06
package repeat_;

import java.util.Scanner;

public class Ex06 {

	public static void main(String[] args) {
		
		Scanner input = new Scanner(System.in);
		
		// 문자열 비교
		String n1, n2;
		System.out.println("문자열 입력");
		n1 = input.next();
		
		System.out.println("문자열 입력");
		n2 = input.next();
		
		System.out.println("n1 == n2 : " + (n1 == n2));
		System.out.println("n1.equals(n2) : " + n1.equals(n2));
		
		if(n2.equals(n1)) {
			System.out.println("두 이름 같다.");
		}else {
			System.out.println("두 이름 다르다.");
		}
		
		
		String name1 = null, name2 = "test";
		System.out.println(name2.equals(name1));
		
		if(name1 == null) {
			System.out.println("name1은 null");
		}
		
		
	}

}
```



## 반복문 제어 Quiz
![[Pasted image 20240807180041.png|500]]

![[Pasted image 20240807180054.png|300]]

![[Pasted image 20240807180107.png|500]]


```java title=Quiz
package repeat_;

import java.util.Scanner;

public class Quiz {

	public static void main(String[] args) {
		
		Scanner input = new Scanner(System.in);
		
		/* 로그인 회원가입 */
		boolean loginProcess = true;
		String id = null;
		String pass = null;
		
		while(loginProcess) {
			String menu = "1. 로그인" + "\n" + "2. 회원가입" + "\n" + "3. 나가기" + "\n" + ">>> ";
			
			System.out.print(menu);
			int select = input.nextInt();
			
			String tempId = null;
			String tempPass = null;
			
			switch(select) {
			case 1:
				if(id == null && pass == null) {
					System.out.println("회원가입 먼저 진행");
					continue;
				}
				
				boolean isLogin = false;
				String loginMessage = null;
				
				System.out.print("ID : ");
				tempId = input.next();
				System.out.print("Pass : ");
				tempPass = input.next();
				
				isLogin = tempId.equals(id) && tempPass.equals(pass);
				if(isLogin) {
					loginMessage = "로그인 성공";
				} else {
					loginMessage = "로그인 실패";
				}
				System.out.println(loginMessage);
				
				break;
			case 2:
				String prevId = id;
				String joinMessage = null;
				boolean isJoin = false;
		
				System.out.print("가입할 ID : ");
				tempId = input.next();
				System.out.print("가입할 Pass : ");
				tempPass = input.next();
				
				if(!tempId.equals(prevId)) {
					id = tempId;
					pass = tempPass;
					isJoin = true;
				}
				
				if(isJoin) {
					joinMessage = "가입 성공";
				}else {
					joinMessage = "가입 실패";
				}
				System.out.println(joinMessage);
				
				break;
			case 3: 
				loginProcess = false;
				continue;
			default: System.out.println("test");
				break;
			}
			
		}
		
		
		
		/* 자판기 */
		int money = 0;
		while(true) {
			System.out.print("요금 투입 : ");
			money = input.nextInt();
			
			if (money != 0 && money > 0) break;
		}
		
		boolean vendProcess = true;
		while(vendProcess) {
			int coffee = 200;
			int coco = 250;
			boolean approv = false;
			int selector = 0;
			
			String message = "==== 커피 자판기 ====" + "\n\n" + "1. 커피(" + coffee + ")\t" + "2. 코코아(" + coco + ")\t" + "3. 반환\t" + "4. 종료\n" + "메뉴 선택 >>> ";
			System.out.print(message);
			int select = input.nextInt();
			
			switch(select) {
				case 1: 
					selector = coffee;
					break;
				case 2: 
					selector = coco;
					break;
				case 3: 
					if(money != 0 && money > 0) {
						System.out.println("거스름돈 : " + money);
						money = 0;
					} else {
						System.out.println("반환할 돈이 없음");
					}
					continue;
				case 4:
					vendProcess = false;
					continue;
			}
			approv = money >= selector;
			if (approv) {
				money -= selector;
				System.out.println("맛있게 드세요");
			}else {
				System.out.println("요금부족");
				continue;
			}
			
		}
		
		
	}

}
```



***



# 이름 붙은 for문
```java title=Test01
		// 이름 붙은 for문
		test_for:
		for(int i = 0; i < 5; i++) {
			System.out.println("i : " + i);
			for(int j = 0; j < 5; j++) {
				if(j >= 3) break test_for;
				System.out.println("j : " + j);
			}
		}
		
```
- break 뒤에 for문의 이름을 적어두면 j for문만 빠져나가는게 아닌 최상위 for문까지 빠져나간다.



```java title=BreakTest01

public class BreakTest01 {

	public static void main(String[] args) {
		
		int i, j;	// 반복문 제어 변수
		
		for(i = 1; i <= 5; i++) {
			for(j = 1; j <= 5; j++) {
				if(i % 3 == 0) break;	// 가장 가까운 맨 안쪽 반복문만 중단한다.
				System.out.print(" j -> " + j);
			} // inner for
			System.out.println("\n i -> " + i);
		} // outer for
		System.out.println("======================>");
		
		
		// 바깥쪽 반복문과 안쪽 반복문 모두 중단
		break_for:
			for(int a = 1; a <= 5; a++) {
				for(int b = 1; b <= 5; b++) {
					if(b % 3 == 0) break break_for;
					System.out.println(" b -> " + b);
				}
				System.out.println(" \n a - > " + a);
			}
		System.out.println("======================>");
		
		
		
	}

}

```



```java title=BreakTest02


// 다중 반복문을 모두 강제 종료하기 위해서 이름 붙는 반복문을 응용한 메뉴 선택 계산 예제

import java.util.Scanner;

public class BreakTest02 {

	public static void main(String[] args) {
		
		int menu = 0;
		int num = 0;
		
		Scanner sc = new Scanner(System.in);
		
		String printMenu = "1. 물냉면\n" + "2. 비빔냉면\n" + "3. 삼겹살\n" + "0. 종료\n" + "원하는 메뉴 (1 ~ 3)를 선택 : ";
		
		exit_for:
			while(true) { // 무한 루프문
				System.out.print(printMenu);
				String resultMenu = sc.nextLine().trim();	// 메뉴 입력
				menu = Integer.parseInt(resultMenu);		// 입력받은 문자열 숫자를 정수로 변경해서 저장
				
				if(menu == 0) {
					System.out.println("메뉴 선택을 종료합니다.");
					break;	// 무한 루프 while 종료
				}else if(!(menu >= 1 && menu <= 3)) {
					System.out.println("메뉴를 잘못 선택했습니다.");
					continue;	// 아래 문장 실행하지 않고 반복문 처음으로 돌아가서 다음 반복 계속 
				}
				
				
				for(;;) {	// for 반복문 무한루프 
					System.out.print("메뉴 계산할 값을 입력 (계산 종료: 0, 전체 종료: 99)");
					num = Integer.parseInt(sc.nextLine().trim());
					
					if(num == 0) break;	// 무한루프 for 반복문 종료
					if(num == 99) break exit_for;	// 전체 종료 => for 반복문 종료하고
					
					switch(menu) {
						case 1: System.out.println("물냉면 가격 : " + num + "원"); break;
						case 2: System.out.println("비빔냉면 가격 : " + num + "원"); break;
						case 3: System.out.println("삼겹살 가격 : " + num + "원"); break;
					}
					
				} // for
				
				
			} // while
		
		
	}

}

```



***



# 반복문(do while)

![[Pasted image 20240808105059.png|450]]

```java title=Ex01
package repeat_;

public class Ex01 {

	public static void main(String[] args) {
		int i = 0, sum = 0;
		
		do {
			sum += ++i;
			System.out.println("do while " + i);
		} while(i < 10);
		System.out.println("sum1 : " + sum);
		
		System.out.println("---------------------");
		
		i = sum = 0;
		
		 while(i < 10) {
			sum += ++i;
			System.out.println("while " + i);
		};
		System.out.println("sum2 : " + sum);
	}

}



```


```java title=Ex02

package repeat_;

public class Ex02 {

	public static void main(String[] args) {
		for(int k = 0 ; k < 3 ; k++) {
			System.out.println("===상위 반복문");
			
			for(int i = 0 ; i < 3 ; i++) {
				System.out.println(i + " for");
				break;
			}
			System.out.println("상위 반복문 끝===");
			break;
		}
		System.out.println("다음 문장들");
		
		
		for(int k = 2 ; k < 10 ; k++) {
			for(int i = 1 ; i < 10 ; i++) {
				System.out.println(k + " * " + i + " = " + k*i);
			}
		}
		
		int k = 2;
		
		while(k < 10) {
			int i = 1;
			
			while(i < 10) {
				System.out.println(k + " * " + i + " = " + k*i);
				i++;
			}
			
			k++;
		}
		
		System.out.println("---------------");
		
		String print = "";
		int sum = 0;
		for (int j = 0; j < 5; j++) {
			for (int i = 0; i < 5; i++) {
				print += ++sum + "\t";
			}
			print += "\n";
		}
		System.out.println(print);
		
		
		
	}

}

```







