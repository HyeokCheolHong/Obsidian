
# 조건문(if)

![[Pasted image 20240806140151.png|500]]


```java title=Ex01
package if_;

import java.util.Scanner;

public class Ex01 {

	public static void main(String[] args) {
		Scanner input = new Scanner(System.in);
		
		int num;
		System.out.println("1. 쉬운 게임");
		System.out.println("2. 어려운 게임");
		System.out.println("3. 종료");
		System.out.print(">>> : ");
		num = input.nextInt();
		
		if(num == 1) System.out.println("쉬운 게임 시작합니다");
		if(num == 2) System.out.println("어려운 게임 시작합니다");
		if(num == 3) System.out.println("게임 종료합니다");		

		
	}

}

```



```java title=Ex02
package if_;

import java.util.Scanner;

public class Ex02 {
	public static void main(String[] args) {
		Scanner input = new Scanner(System.in);
		
		int num;
		System.out.print("수 입력 : ");
		num = input.nextInt();
		
		if(num > 10) {
			System.out.println("1. 10보다 크다");
			System.out.println("2. 10보다 크다");
			System.out.println("3. 10보다 크다");
		}
		
		System.out.println("다음 문장들 실행");
		System.out.println("다음 문장들 실행");
		
		if (num % 2 != 0) {
			System.out.println("입력값은 홀수");
		}
		if (num % 2 == 0) {
			System.out.println("짝수....");
		}
		
		
		/*
		 * 1. 두 수 입력받고, 큰 수 출력
		 * 2. 세 수 입력받고, 가장 큰 수 출력
		 * 3. 두 수 입력받고, 합이 짝수이고 3의 배수 출력
		 */
		System.out.print("두 수 입력 : ");
		int num1 = input.nextInt();
		int num2 = input.nextInt();
		int result = 0;
		
		if(num1 >= num2) {
			result = num1;
		}
		if(num1 <= num2) {
			result = num2;
		}
		
		System.out.println("더 큰 수 : " + result);
		
		
		
		System.out.print("세 수 입력 : ");
		int num3 = input.nextInt();
		int num4 = input.nextInt();
		int num5 = input.nextInt();
		int result2 = num3;
		
		if(num4 > result) {
			result2 = num4;
		}
		if(num5 > result) {
			result2 = num5;
		}
		
		System.out.println("가장 큰 수 : " + result);
		
		
		
		System.out.print("두 수 입력 : ");
		int num6 = input.nextInt();
		int num7 = input.nextInt();
		int sum = num6 + num7;
	
		
		if(sum % 2 == 0 && sum % 3 == 0) {
			System.out.println("합이 짝, 3의 배수임");
		}
		
		
	}
	
}
```



***



# 조건문(if - else)

![[Pasted image 20240806140133.png|550]]


```java title=Ex03
package if_;

public class Ex03 {

	public static void main(String[] args) {
		int num = 10;
		if(num == 10) {
			System.out.println("if 실행");
		} else {
			System.out.println("else");
		}
		System.out.println("다음 문장들 실행");
		
		
		int n1, n2 = 10;
		if(n2 > 100) 
			n1 = 100;
		else
			n1 = 1234;
		System.out.println(n1);
		
		/* 초기화 */
		// 첫번째 문자가 소문자면 0으로 초기화 진행
		int i = 0;
		double d = 0;
		char ch = 0;
		
		// 첫번째 문자가 대문자면 null로 초기화 진행
		String s = null; 
		
		
		int n = 10;
		if(n % 2 == 0 && n % 3 == 0) {
			System.out.println("짝 3배수");
		}else {
			System.out.println("아님");
		}
		
		if(n % 2 == 0) {
			System.out.println("짝수다");
			if(n % 3 == 0) {
				System.out.println("3의 배수");
			}else {
				System.out.println("배수 아님");
			}
		}else {
			System.out.println("짝수가 아니다");
		}
		
		
	}

}
```



***



# 조건문(if - else if)

![[Pasted image 20240806143055.png|550]]


```java title=Ex04
package if_;

public class Ex04 {

	public static void main(String[] args) {
		int num = 150;
		if(num > 100) {
			System.out.println("100보다 크다");
		}else if(num > 80) {
			System.out.println("80보다 크다");
		}else if(num > 50) {
			System.out.println("50보다 크다");
		}else {
			System.out.println("그 외의 값");
		}
		System.out.println("다음 문장들 실행!!!!");
	}

}

```



# 조건문 Quiz

![[Pasted image 20240806143201.png|600]]

![[Pasted image 20240806143207.png|600]]


```java title=Quiz
package if_;

import java.util.Scanner;

public class Quiz {

	public static void main(String[] args) {
		Scanner input = new Scanner(System.in);
		
		// 커피의 개당 가격은 2000원이다. 10개 초과하면 초과하는 양에 대해서만 개당 1500원씩 받는다.
		// 커피의 개수를 입력받아 금액을 출력하시오.
		System.out.print("커피 몇 잔 : ");
		int coffee = input.nextInt();
		
		// 할인시작개수나 가격 수정될 거 생각한 풀이?
		int coffeeDefaultPrice = 2000;
		int coffeeHalPrice = 1500;
		int halCount = 10;
		int sumPrice = 0;
		
		int defaultCoffee = coffee <= halCount ? coffeeDefaultPrice * coffee : coffeeDefaultPrice * halCount;
		int halCoffee = coffee > halCount ? (coffee - halCount) * coffeeHalPrice : 0;
		
		sumPrice = defaultCoffee + halCoffee;
		System.out.println("총 금액 : " + sumPrice);
		
		// 처음 풀이
//		if (coffee > 10) {
//			price = (10 * 2000) + (coffee - 10) * 1500;
//		}else {
//			price = coffee * 2000;
//		}
		
//		System.out.println("총 금액 : " + price);
		
		
		
		// 정수를 입력받아 아래와 같이 출력하시오.
		/*
		 * 1) 3의 배수이면서, 4의 배수에도 해당합니다.
		 * 2) 3의 배수에만 해당합니다.
		 * 3) 4의 배수에만 해당합니다.
		 * 4) 3의 배수도, 4의 배수도 해당 안됩니다.
		 * 5) 0은 잘못 입력했습니다.
		 */
		System.out.print("정수 입력 : ");
		int num = input.nextInt();
		String message = null;
		
		if(num == 0) {
			message = "0은 잘못 입력했습니다.";
		}else if(num % 3 == 0 && num % 4 == 0) {
			message = "3의 배수이면서, 4의 배수에도 해당합니다.";
		}else if(num % 3 == 0) {
			message = "3의 배수에만 해당합니다.";
		}else if(num % 4 == 0) {
			message = "4의 배수에만 해당합니다.";
		}else {
			message = "3의 배수도, 4의 배수도 해당 안됩니다.";
		}
		System.out.println(message);
		
		
		
		
		/*
		 * usb 1개에 5000원 한다.
		 * 그런데 한 번에 10개 이상을 사면 전체 금액의 10%를 할인하여 준다.
		 * 그리고 100개 이상을 사면 전체 금액의 12%를 할인하여 준다. X개의 usb를 사려면 얼마가 있어야 하는가?
		 */
		int x = 10;
		int usb = 5000;
		int price = 0;
		double totalPrice = usb * x;
		
		if (x >= 100) {
			price = (int)totalPrice - (int)(totalPrice * 0.12);
		}else if(x >= 10) {
			price = (int)totalPrice - (int)(totalPrice * 0.1);
		}
		System.out.println("가격 : " + price);
		
		
		
		
		/*
		 * 국, 영, 수학 점수를 입력받아 평균 60점 이상이고 각 점수가 40점 이상이면 합격, 아니면 평균 불합격인지,
		 * 과목 불합격인지 사유를 출력하고, 평균이 90이상이면 'A', 80이상 'B', 70이상 'C', 60이상 'D', 60미만이면 'F'
		 * 를 출력하시오 (출력: 불합격 또는 합격, 국, 영, 수, 합계, 평균, 등급) 
		 */
		System.out.print("국 영 수 점수 입력: ");
		int kor = input.nextInt();
		int eng = input.nextInt();
		int ma = input.nextInt();
		
		int sum = kor + eng + ma;
		int avg = (int)(sum / 3);
		char grade = 0;
		
		boolean isEachScore = kor >= 40 && eng >= 40 && ma >= 40;
		boolean isAcceptance = avg >= 60 && isEachScore;
		
		String acceptanceMessage = isAcceptance ? "합격" : "불합격";
		
		if (avg >= 90) {
			grade = 'A';
		}else if (avg >= 80) {
			grade = 'B';
		}else if (avg >= 70) {
			grade = 'C';
		}else if (avg >= 60) {
			grade = 'D';
		}else {
			grade = 'F';
		}
		System.out.println(acceptanceMessage + " " + kor + " " + eng + " " + ma + " " + sum + " " + avg + " " + grade);
		
		
		
		/*
		 * 비행기를 타는데 30분 거리까지의 기본 요금은 30000원이며, 10분 단위로 추가 요금 5000원씩 부가된다.
		 * 비행기 탈 시간을 입력하여 요금 계산기를 만드시오.
		 */
		System.out.print("비행기 시간 : ");
		int minute = input.nextInt();
//		int time = input.nextInt();
//		int minute = time >= 60 ? time / 60 : time * 60;
		
		int referMinute = 30;
		int intervalMinute = 10;
		int referMinutePrice = 30000;
		int addPrice = 5000;
		
		int resultPrice = 0;
		
		if(minute > referMinute) {
			resultPrice = (minute - referMinute) / intervalMinute * addPrice + referMinutePrice;
		}else {
			resultPrice = referMinutePrice;
		}
		
		if(minute == 0) {
			resultPrice = 0;
		}
		System.out.println("총 요금 : " + resultPrice);
		
		
	}

}

```





