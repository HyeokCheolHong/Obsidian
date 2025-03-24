
![[2_JAVA/0_용어#JAVA]]

![[2_JAVA/0_용어#변수(Variable)]]



# 출력(println, print)

```java title="Test01"
package day01;

public class Test01 {

	// main : 프로그램의 시작점
	public static void main(String[] args) {
		/*
		*
		*/
		
		//System.out.println(1000);
		System.out.println("문자열");
		
		System.out.print("문자열");
		System.out.print("문자열");
		System.out.print("문자열");
		
	}

}
```



## 출력 Quiz

![[2_JAVA/Attachments/Pasted image 20240805161255.png|450]]


```java title="Test02"
package day01;
   
   public class Test02 {
   
   	public static void main(String[] args) {
   		System.out.println("안\n녕\n하\n");
   		// \t는 윈도우의 space 8칸에 해당함.
   		System.out.println("1\t1234567\t12345678\t1"); // 1~7까지의 공간 차지 후 마지막 1칸만 space가 차지, 1~8은 8칸 다 차지하여 새롭게 8칸 추가됨
   		System.out.println("이름\t나이");
   		System.out.println("홍길동\t20살");
   		
   		System.out.println("  \" \\ ");
   		System.out.println("\"C:\\0.공유자료\\내가 만든 폴더\"");
   		
   		System.out.println("===================");
   		System.out.println(100 + 100);
   		System.out.println("100" + "100");
   		System.out.println("백" + 100 + 100);
   		System.out.println("백" + (100 + 100));
   		
   
   		/* ◈ 숫자들은 숫자로 사용하시오.
   		 *  =======================================
   			이름	나이	전화번호		회비
   			=======================================
   			홍길동	"15"	3672-1234	\20000
   			고길동	"15"	2238-1234	\30000
   			김말이	"15"	1234-1234	\50000
   			---------------------------------------
   			총합계				\100000
   			---------------------------------------
   		 */
   
   		System.out.println("=======================================");
   		System.out.println("이름" + "\t" + "나이" + "\t" + "전화번호" + "\t\t" + "회비");
   		System.out.println("=======================================");
   		System.out.println("홍길동" + "\t\"" + 15 + "\"\t" + 3672 + "-" + 1234 + "\t\\" + 20000);
   		System.out.println("고길동" + "\t\"" + 15 + "\"\t" + 2238 + "-" + 1234 + "\t\\" + 30000);
   		System.out.println("김말이" + "\t\"" + 15 + "\"\t" + 1234 + "-" + 1234 + "\t\\" + 50000);
   		System.out.println("---------------------------------------");
   		System.out.println("총합계" + "\t\t\t\t\\" + 100000);
   		System.out.println("---------------------------------------");
   		
   		
   	}
   
}
   
```



***



# 변수(Variable)

![[2_JAVA/Attachments/Pasted image 20240805140150.png|550]]

```java title="Test01"
package variable;

public class Test01 {

	public static void main(String[] args) {
		int age = 30;
		double weight = 55.0, height = 100.123;
//		double height = 100.123;
		
		System.out.println("나의 나이는 " + age + "살 입니다.");
		System.out.println("나의 몸무게 " + weight + "kg");
		
		age = 123;
		System.out.println("변경 후 " + age + "살 입니다.");
		
		int number = 123;
		System.out.println("변경 전 : " + number);
		number = 100;
		System.out.println("변경 후 : " + number);
		number = number + 300;
		System.out.println("변경 후 : " + number);
		
	}

}

```



```java title="Test02"
package variable;

public class Test02 {

	public static void main(String[] args) {
		// char : 2byte 크기의 문자 하나 저장
		// char는 작은 따옴표로 묶어야 한다.
		char ch = 'A';
		String str = "A";
		int num = 5;
		System.out.println(ch);
		System.out.println(str);
		System.out.println(num);
		
		int result = 0;
		System.out.println(result + 10);
		
		result = ch + num;
		System.out.println("연산 후 : " + result);
		
		
		
		
	}

}

```

==**옵시디언 Code Block 실행시 한글 깨짐 해결**== : ![[JAVA Code Block 실행시 한글 깨짐]]



```java title=Test03
package variable;

public class Test03 {

	public static void main(String[] args) {
		/*
		 * 형변환 (type casting)
		 * - 강제 형변환 : 강제로 자료형을 변경
		 * - 자동 형변환 : 프로그램에서 자동으로 자료형 변경
		 */
		int num = 0;
		char ch = 'A';
		System.out.println("변경 전 num : " + num);
		
		num = ch; // 자동형 변환
		System.out.println("변경 후 num : " + num);
		
//		ch = num; // error
		char ch2 = (char)num;
		System.out.println("ch2 : " + ch2);
		System.out.println("ch2 : " + (int)ch2);
		
		double dou = 1.123;
		float fl = (float)1.234;
		float fl2 = 1.234F;
		
		
		final String KOREA = "대한민국";
		System.out.println("변경 전 : " + KOREA);
		// korea = "미국";
		System.out.println("변경 후 : " + KOREA);

		
	}

}

```



***



# 입력(Scanner)

```java title=Test01
package scanner;

import java.util.Scanner;

public class Test01 {

	public static void main(String[] args) {
		Scanner input = new Scanner(System.in);
		System.out.println("문자열 입력 : ");
		String str = input.next();
		System.out.println("입력 받은 값 : " + str);
		
		int num;
		System.out.print("수 입력 : ");
		num = input.nextInt();
		System.out.println("입력 수 : " + num);
		
		System.out.print("실수 입력 : ");
		double dou = input.nextDouble();
		System.out.println("입력 수 : " + dou);
	}

}

```



## 입력 Quiz

![[2_JAVA/Attachments/Pasted image 20240805163013.png|450]]


```java title=Quiz01
package scanner;

import java.util.Scanner;

public class Quiz01 {

	public static void main(String[] args) {
		Scanner input = new Scanner(System.in);
		
		
		System.out.print("당신의 이름은 무엇입니까? ");
		String name = input.next();
		System.out.print(name + " 님의 국어 점수 : ");
		int kor = input.nextInt();
		System.out.print(name + " 님의 영어 점수 : ");
		int eng = input.nextInt();
		System.out.print(name + " 님의 수학 점수 : ");
		int ma = input.nextInt();
		
		String bar = "===============";
		System.out.println(bar);
		System.out.println("이 름 : " + name.charAt(0) + " " + name.charAt(1) + " " + name.charAt(2));
		System.out.println(bar);
		System.out.println("국 어 : " + kor);
		System.out.println("영 어 : " + eng);
		System.out.println("수 학 : " + ma);
		System.out.println(bar);
		System.out.println("합 계 : " + (kor + eng + ma));
		System.out.println(bar);
		
		
		
	}

}

```




