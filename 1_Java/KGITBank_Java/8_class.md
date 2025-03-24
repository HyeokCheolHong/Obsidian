
![[Pasted image 20240812133129.png|500]]



# 타 프로젝트의 Class import 
![[Pasted image 20240812133500.png|500]] 
- 프로젝트(day06) 클릭후 Alt + enter
- ModulePath 설정해줘야 export한 클래스 가져와서 사용 가능한 듯함 ^0411b1
- 같은 프로젝트에 있는 클래스 가져올 땐 설정 안해도 됨

![[Pasted image 20240812133558.png|300]]
- 클래스 가져올 프로젝트명 선택

![[Pasted image 20240812133616.png|300]]
- 자동완성 시 타 프로젝트에 존재하는 class 파일 import 가능


```java title=MemberClass
package member;

public class MemberClass {
	public String name, addr;
	public int age;
	
}

```



```java title=modul-info.java
/**
 * 
 */
/**
 * 
 */
module class_ {
	// 다른 프로젝트에서 사용할 수 있게 export
	exports member;
}
```



```java title=module-info.java
/**
 * 
 */
/**
 * 
 */
module day06_ {
	// 가져올 떈 프로젝트 이름을 적으면 됨
	requires class_;
}
```




```java title=Ex01
package method_;

import member.MemberClass;

public class Ex01 {

	public static void main(String[] args) {
		MemberClass mc = new MemberClass();
		
		mc.name = "홍길동";
		mc.age = 20;
		
		System.out.println(mc.name);
		System.out.println(mc.age);
		
	}

}

```



***



# 메소드(Method)

![[Pasted image 20240812135249.png|500]]


```java title=TestClass01
package method_;

public class TestClass01 {
	public String name;
	public int age;
}
```

```java title=MainClass01
package method_;

import java.util.Scanner;

public class QuizFunc01 {
	public String inputName() {
		Scanner input = new Scanner(System.in);
		System.out.print("이름 입력 : ");
		String name = input.next();
		
		return name;
	}
	
	public void outputName(String name) {
		System.out.println("이름 : " + name);
	}
}

```



```java title=TestClass02
package method_;

import java.util.Scanner;

public class TestClass02 {
	public int test() {
		Scanner input = new Scanner(System.in);
		int num;
		System.out.print("수 입력 : ");
		num = input.nextInt();
		
		return num;
		
	}
}

```

```java title=MainClass02
package method_;

import java.util.Scanner;

public class MainClass02 {

	public static void main(String[] args) {
		Scanner input = new Scanner(System.in);
		
//		System.out.print("수 입력 : ");
//		num = input.nextInt();
		
		TestClass02 t = new TestClass02();
		int num = t.test();

		if(num % 2 == 0) {
			System.out.println("짝");
		}else {
			System.out.println("홀");
		}
		
		
//		System.out.print("수 입력 : ");
//		num = input.nextInt();
		
		num = t.test();
		
		if(num % 3 == 0) {
			System.out.println("3의 배수");
		}else {
			System.out.println("3의 배수 아님");
		}
		
	}

}

```



```java title=TestClass03
package method_;

import java.util.Scanner;

public class TestClass03 {
	public void test() {
		System.out.println("test");
	}
	
	public void sumFunc() {
		Scanner input = new Scanner(System.in);
		
		int num = 0, sum = 0;
		System.out.println("수 입력");
		num = input.nextInt();
		
		for(int i = 1; i <= num; i++) {
			sum += i;
		}
		System.out.println("1 ~ " + num + " 까지의 합 : " + sum);
	}
}

```

```java title=MainClass03
package method_;

import java.util.Scanner;

public class MainClass03 {

	public static void main(String[] args) {
		TestClass03 t = new TestClass03();
		
		System.out.println("main시작");
		t.test();
		System.out.println("main종료");
		t.sumFunc();
		
	}

}
```



```java title=TestClass04
package method_;

public class TestClass04 {
	public void sumFunc(int num) { // 여기에서의 num은 Argument(아규먼트)라고 함
		int sum = 0;
		
		for(int i = 1; i <= num; i++) {
			sum += i;
		}
		
		System.out.println("1 ~ " + num + " 까지의 합 : " + sum);
	}
	
}
```

```java title=MainClass04
package method_;

import java.util.Scanner;

public class MainClass04 {

	public static void main(String[] args) {
		
		Scanner input = new Scanner(System.in);
		
		int num = 0, sum = 0;
		System.out.println("수 입력");
		num = input.nextInt();
		
		TestClass04 t=  new TestClass04();
		t.sumFunc(num); // 여기에서의 num : 파라미터, 인자 라고 부름
		
	}

}

```



```java title=TestClass05
package method_;

public class TestClass05 {
	
	public int sumFunc(int num) { // 여기에서의 num은 Argument(아규먼트)라고 함
		int sum = 0;
		
		for(int i = 1; i <= num; i++) {
			sum += i;
		}
		
		return sum;
	}
	
	
}

```

```java title=MainClass05
package method_;

import java.util.Scanner;

public class MainClass05 {

	public static void main(String[] args) {
		
		Scanner input = new Scanner(System.in);
		
		int num = 0, sum = 0;
		System.out.println("수 입력");
		num = input.nextInt();
		
		TestClass05 t = new TestClass05();
		sum = t.sumFunc(num); // 여기에서의 num : 파라미터, 인자 라고 부름
		
		System.out.println("1 ~ " + num + " 까지의 합 : " + sum);
		
	}

}

```



```java title=TestClass06
package method_;

import java.util.Scanner;

public class TestClass06 {
	
	public int inputData() {
		Scanner input = new Scanner(System.in);
		System.out.println("수 입력");
		int num = input.nextInt();
		
		return num;
	}
	
	public int opData(int num) {
		int sum = 0;
		
		for(int i = 1; i <= num; i++) {
			sum += i;
		}
		
		return sum;
	}
	
	public void printData(int num, int s) {
		System.out.println(num + "까지 합 : " + s);
	}
	
}

```

```java title=MainClass06
package method_;

public class MainClass06 {

	public static void main(String[] args) {
		TestClass06 t = new TestClass06();
		
		int n = t.inputData();
		int sum = t.opData(n);
		
		t.printData(n, sum);
		
	}

}

```



```java title=MainClass07
package method_;

class TestClass07 {
	public void test1() {
		int num = 1;
		
		if(num == 1) {
			System.out.println(111);
			return;
		}
		System.out.println("다음 문장실행");
	}
	
	public String test2() {
		int num = 1;
		if(num == 1) {
			return "성공";
		}
		// 첫 문자가 소문자인 자료형일 경우 return 0;
		return null;
	}
	
	/* 아래 주석처럼 사용은 불가(에러 발생) */
//	public void test3() {
//		int num = 1;
//		if(num == 1) { 
//			return 111;
//		}
//		return "문자열";
//	}
	
//	public int test4() {
//		return 10, 20, 30;
//	}
	
}

public class MainClass07 {
	public static void main(String[] args) {
		TestClass07 t = new TestClass07();
		t.test1();
	}
	
}

```



```java title=MainClass08
package method_;

import java.util.ArrayList;
import java.util.HashMap;

class TestClass08 {
	
	public int[] test1() {
		int num = 10, n = 20;
		int[] arr = { num, n };
		return arr;
	}
	
	public HashMap<String, Integer> test2(ArrayList<Integer> a) {
		System.out.println("---- test2 ----");
		System.out.println(a.size());
		System.out.println(a.get(0));
		System.out.println(a.get(1));
		
		HashMap<String, Integer> map = new HashMap<>();
		map.put("num", a.get(0) + 100);
		map.put("su", a.get(1) + 100);
		
		return map;
	}
}


public class MainClass08 {

	public static void main(String[] args) {
		TestClass08 t = new TestClass08();
		
		int[] a = t.test1();
		System.out.println(a.length);
		System.out.println(a[0]);
		System.out.println(a[1]);

		
		ArrayList<Integer> arr = new ArrayList<>();
		arr.add(10);
		arr.add(20);
		
		
		HashMap<String, Integer> map = t.test2(arr);
		System.out.println("--- main ---");
		System.out.println(map);
		
		
	}

}
```



## 메소드 Quiz
![[Pasted image 20240812172228.png|400]]


```java title=QuizFunc01
package method_;

import java.util.Scanner;

public class QuizFunc01 {
	public String inputName() {
		Scanner input = new Scanner(System.in);
		System.out.print("이름 입력 : ");
		String name = input.next();
		
		return name;
	}
	
	public void outputName(String name) {
		System.out.println("이름 : " + name);
	}
}

```

```java title=Quiz01
package method_;

public class Quiz01 {

	public static void main(String[] args) {
		QuizFunc01 qf = new QuizFunc01();
		
		String name = qf.inputName();
		qf.outputName(name);
		
	}

}

```



```java title=QuizFunc02
package method_;

import java.util.Scanner;

public class QuizFunc02 {
	public String[] InputArrayName() {
		Scanner input = new Scanner(System.in);
		String[] arrName = new String[3];
		
		System.out.print("이름 3개 입력 : ");
		for(int i = 0; i < arrName.length; i++) {
			arrName[i] = input.next();
		}
		
		return arrName;
	}
	
}

```

```java title=Quiz02
package method_;

public class Quiz02 {

	public static void main(String[] args) {
		QuizFunc02 qf = new QuizFunc02();
		
		String[] names = qf.InputArrayName();
		for(String name : names) {
			System.out.println(name);
		}
		
		
	}

}

```



```java title=QuizFunc03
package method_;

import java.util.Scanner;

public class QuizFunc03 {
	public int[] inputOfTwoNumbers() {
		Scanner input = new Scanner(System.in);
		int[] numbers = new int[2];
		
		System.out.print("두 수 입력 : ");
		for(int i = 0; i < numbers.length; i++) {
			numbers[i] = input.nextInt();
		}
		
		return numbers;
	}
	
	
	public int countBout(int[] numbers) {
		int sum = 0;
		
		for(int number : numbers) { 
			sum += number;
		}
		
		return sum;
	}
	
	
	public void printData(int sum) {
		System.out.println("두 수의 합 : " + sum);
	}
}

```

```java title=Quiz03
package method_;

public class Quiz03 {

	public static void main(String[] args) {
		QuizFunc03 qf = new QuizFunc03();
		
		int[] numbers = qf.inputOfTwoNumbers();
		int sum = qf.countBout(numbers);
		qf.printData(sum);
		
	}

}

```



```java title=QuizFunc04
package method_;

import java.util.ArrayList;
import java.util.Iterator;
import java.util.Scanner;

public class QuizFunc04 {

	public ArrayList<Integer> inputOfTwoNumbers() {
		Scanner input = new Scanner(System.in);
		ArrayList<Integer> numbers = new ArrayList<>();
		
		System.out.print("두 수 입력 : ");
		numbers.add(input.nextInt());
		numbers.add(input.nextInt());
		
		return numbers;
	}
	
	
	public int countBout(ArrayList<Integer> numbers) {
		int sum = 0;
		
		Iterator<Integer> it = numbers.iterator();
		while(it.hasNext()) {
			sum += it.next();
		}
		
		return sum;
	}
	
	
	public void printData(int sum) {
		System.out.println("두 수의 합 : " + sum);
	}
	
	
}

```

```java title=Quiz04
package method_;

import java.util.ArrayList;

public class Quiz04 {

	public static void main(String[] args) {
		
		QuizFunc04 qf = new QuizFunc04();
		
		ArrayList<Integer> numbers = qf.inputOfTwoNumbers();
		int sum = qf.countBout(numbers);
		qf.printData(sum);
		
	}

}

```



```java title=
package method_;

import java.util.HashMap;
import java.util.Iterator;
import java.util.Scanner;

public class QuizFunc05 {
	public HashMap<Integer, Integer> inputOfTwoNumbers() {
		Scanner input = new Scanner(System.in);
		HashMap<Integer, Integer> numbers = new HashMap<>();
		
		System.out.print("두 수 입력 : ");
		for(int i = 0; i < 2; i++) {
			numbers.put(i, input.nextInt());
		}
		
		return numbers;
	}
	
	
	public int countBout(HashMap<Integer, Integer> numbers) {
		int sum = 0;
		
		Iterator<Integer> it = numbers.keySet().iterator();
		while(it.hasNext()) {
			sum += numbers.get(it.next());
		}
		
		return sum;
	}
	
	public void printData(int sum) {
		System.out.println("두 수의 합 : " + sum);
	}
}

```

```java title=Quiz05
package method_;

import java.util.HashMap;

public class Quiz05 {

	public static void main(String[] args) {
		QuizFunc05 qf = new QuizFunc05();
		
		HashMap<Integer, Integer> numbers = qf.inputOfTwoNumbers();
		int sum = qf.countBout(numbers);
		qf.printData(sum);
	}

}

```



## 메소드 Quiz2
![[Pasted image 20240813124930.png|400]]


```java title=QuizFunc06
package method_;

import java.util.Scanner;

public class QuizFunc06 {
	public int[] inputLargerNumber() {
		Scanner sc = new Scanner(System.in);
		int[] nums = new int[2];
		
		System.out.print("두 수 입력 : ");
		nums[0] = sc.nextInt();
		nums[1] = sc.nextInt();
		
		return nums;
	}
	
	public int largerNumber(int[] nums) {
		return nums[0] >= nums[1] ? nums[0] : nums[1];
	}
	
	public void print(int num) {
		System.out.println("더 큰 수 : " + num);
	}
	
	
}

```

```java title=Quiz06
package method_;

public class Quiz06 {

	public static void main(String[] args) {
		QuizFunc06 qf = new QuizFunc06();
		
		int[] nums = qf.inputLargerNumber();
		int lagerNum = qf.largerNumber(nums);
		qf.print(lagerNum);
	}

}

```



```java title=QuizFunc07
package method_;

import java.util.Scanner;

public class QuizFunc07 {
	public String isOddEven() {
		Scanner sc = new Scanner(System.in);
		
		System.out.print("수 입력 : ");
		int num = sc.nextInt();
		
		return num % 2 == 0 ? "짝수" : "홀수";
	}
	
	public void print(String isOddEven) {
		System.out.println("입력한 수는 " + isOddEven);
	}
}

```

```java title=Quiz07
package method_;

public class Quiz07 {

	public static void main(String[] args) {
		QuizFunc07 qf = new QuizFunc07();
		
		String isOddEven = qf.isOddEven();
		qf.print(isOddEven);
		
	}

}

```



```java title=QuizFunc08
package method_;

import java.util.Scanner;

public class QuizFunc08 {
	public int input() {
		Scanner sc = new Scanner(System.in);
		
		System.out.print("수 입력 : ");
		int num = sc.nextInt();
		
		return num;
	}
	
	public String isThreeDrainage(int num) {
		return num % 3 == 0 ? "3의 배수" : "3의 배수 아님";
	}
	
	public void print(String result) {
		System.out.println("입력한 수는 " + result);
	}
}

```

```java title=Quiz08
package method_;

public class Quiz08 {

	public static void main(String[] args) {
		QuizFunc08 qf = new QuizFunc08();
		
		int num = qf.input();
		String result = qf.isThreeDrainage(num);
		
		qf.print(result);

	}

}

```



```java title=QuizFunc09
package method_;

import java.util.Scanner;

public class QuizFunc09 {
	public int inputCountDiscrimination() {
		Scanner sc = new Scanner(System.in);
		
		System.out.print("수 입력 : ");
		int num = sc.nextInt();
		
		return num;
	}
	
	public String countDiscrimination(int num) {
		int count = 0;
		
		for(int i = 1; i <= num; i++) {
			if(num % i == 0) {
				count++;
			}
		}
		
		return count == 2 ? "소수" : "소수 아님";
	}
	
	public void print(String msg) {
		System.out.println("입력한 수는 " + msg);
	}
}

```

```java title=Quiz09
package method_;

public class Quiz09 {

	public static void main(String[] args) {
		QuizFunc09 qf = new QuizFunc09();
		
		int num = qf.inputCountDiscrimination();
		String msg = qf.countDiscrimination(num);
		
		qf.print(msg);
		
	}

}

```



```java title=QuizFunc10
package method_;

import java.util.Scanner;

public class QuizFunc10 {
	public int inputAbsolute() {
		Scanner sc = new Scanner(System.in);
		
		System.out.print("수 입력 : ");
		int num = sc.nextInt();
		
		return num;
	}
	
	public int isAbsolute(int num) {
		return num < 0 ? -num : +num;
	}
	
	public void print(int abNum) {
		System.out.println("절대값 : " + abNum);
	}
	
}

```

```java title=Quiz10
package method_;

public class Quiz10 {

	public static void main(String[] args) {
		QuizFunc10 qf = new QuizFunc10();
		
		int num = qf.inputAbsolute();
		int abNum = qf.isAbsolute(num);
		
		qf.print(abNum);
	}

}

```



```java title=QuizFunc11
package method_;

import java.util.Scanner;

public class QuizFunc11 {
	public int input() {
		Scanner sc = new Scanner(System.in);
		
		System.out.print("수 입력 : ");
		int num = sc.nextInt();
		
		return num;
	}
	
	/* 내가 작성 코드 */
	public String upsideDown(int num) {
		int tNum = 10;
		String reNum = "";
		// 127
		// 일의 자리 : 127 % 10 = 7,
		// 십의 자리 : 127 % 100 = 27, 27 / 10 = (int)2.
		// 백의 자리 : 127 % 1000 = 127, 127 / 100 = (int)1.
		
		int result = 0;
		int temp = 0;
		
		while(true) {
			temp = num % tNum;
			
			if(result == 0) {
				result = temp;
			}else {
				result = temp / (tNum / 10);
			}
			reNum += result;
//			System.out.println("while, " + num + " "+ tNum + " " + temp + " " + result);
			
			tNum *= 10;
			if(temp == num) break;
		}
		
		return reNum;
	}
	
	public void print(String reverNum) {
		System.out.println("거꾸로 뒤집었을 때 : " + reverNum);
	}
	
	
	/* 강사님 작성 코드 */
//	public String upsideDown(int num) {
//		int su = 0, temp = 0;
//		
//		temp = su % 10;
//		System.out.println(temp + ", ");
//		su = su / 10;
//		if(su == 0) break;
//	}
	
	
	/* GPT 작성 코드*/
//	public String upsideDown(int num) {
//        StringBuilder reNum = new StringBuilder();
//        
//        while (num != 0) {
//            int digit = num % 10;
//            reNum.append(digit);
//            num /= 10;
//        }
//        
//        return reNum.toString();
//    }
	
}


```

```java title=Quiz11
package method_;

public class Quiz11 {

	public static void main(String[] args) {
		QuizFunc11 qf = new QuizFunc11();
		
		int num = qf.input();
		String reverNum = qf.upsideDown(num);
		
		qf.print(reverNum);
		
	}

}

```



***



# 오버로딩(Overloading)

![[Pasted image 20240813151104.png| 500]]


```java title=Ex01
package method_;

class TestClass01 {
	public void sumFunc() {
		System.out.println("매개변수 없는 sumFunc");
	}
	public void sumFunc(int num) {
		System.out.println(num + " : int sumFunc");
	}
	public void sumFunc(int num, int n2) {
		System.out.println(num + n2 + " : int sumFunc");
	}
	public void sumFunc(String num, int n2) {
		System.out.println(num + n2 + " : int sumFunc");
	}
}

public class Ex01 {
	public static void main(String[] args) {
		TestClass01 t = new TestClass01();
		t.sumFunc();
		t.sumFunc(2);
		t.sumFunc(123, 456);
		t.sumFunc("안녕하세요", 456);
	}
	
}

```



```java title=OverloadingTest03


/* 
 * 메서드 오버로딩의 구분 요건으로 메서드명 앞의 리턴타입을 다르게 한 오버로딩은 적용되지 않는다.
 * 일반적으로 오버로딩 구분 요건으로는 전달인자(매개변수) 개수를 다르게 하든지, 매개변수 타입을 다르게 한 오버로딩을 적용한다.
 */


class Mt03 {
	void pr(int k) {
		System.out.println(k);
	}
	
//	int pr(int k) {		// Error. 반환타입만 다르게 하면 오버로딩 구분 요건에 충족되지 않아서 Error 발생
//		return k;
//	}
	
	
} // Mt03 class



public class OverloadingTest03 {

	public static void main(String[] args) {
		Mt03 mt03 = new Mt03();
		mt03.pr(100);
		
	}

}
```



***



# 변수 종류 (class var, instance var, local var)

![[Pasted image 20240813133847.png|500]]
- 클래스 변수 : static 변수라고도 하며, 프로그램이 실행이 되면, 실행되자마자 메모리에 상주한다. 해제 시기는 프로그램 종료될 때 사라진다.
- 인스턴스 변수 : class 영역 안에 선언되며, 다른 클래스에서 객체화를 진행하게 되면 메모리에 올라간다?
	- class 영역 안에 선언된 변수는 초기화를 생략해도 java 내부에서 타입에 맞게 초기화 시켜준다.
- 지역 변수 : 메소드 내에 선언되며, 메소드가 실행될 때 58메모리에 올라가고 메소드 종료시 해제된다.


```java title=TestClass01
package variable_;

public class TestClass01 {
	// 여러 메소드에서 사용할 변수를 이곳에 선언한다.
	// 여기에 선언된 변수를 인스턴스 변수라고 한다.
	public String name = "홍길동";
	
	public void test3() {
		System.out.println("test3 : " + name);
		name = "변경";
	}
	
	public void test4() {
		System.out.println("test4 : " + name);
	}
	
	public void test1() {
		int var = 100;
		System.out.println("test1 : " + var);
		test2(var);
	}
	
	public void test2(int var) {
//		System.out.println("test2 : " + var); // Error, var 변수는 test1의 지역변수이기 때문에
		System.out.println("Test2 : " + var);
	}
	
}
```

```java title=MainClass01
package variable_;

public class MainClass01 {

	public static void main(String[] args) {
		// 지역변수 : 메소드 안에 선언된 변수들
		String name = "홍길동";
		if(true) {
			String n = "김길이";
			System.out.println(name);
			name = "김개똥";
		}
//		System.out.println(n);
		System.out.println("밖 : " + name);
		
		
		TestClass01 t = new TestClass01();
		t.test1();
		t.test3();
		t.test4();
		
		
	}

}

```



```java title=TestClass02
package variable_;

public class TestClass02 {
	public int num = 12345;
	public static int n2 = 12345;
	
}

```

```java title=MainClass02
package variable_;

class AAA {
	public static String path = "c:/test폴더/java";
	public void 저장소역할() {
		System.out.println("내용을 " + path + "에 저장합니다.");
	}
}

class BBB {
	public void 가져오기() {
//		AAA a = new AAA();
		System.out.println("내용을 " + AAA.path + " 가져옵니다.");
	}
}

public class MainClass02 {

	public static void main(String[] args) {
		// 클래스변수는 프로그램 실행될 때, 메모리에 올라간다.
		System.out.println(TestClass02.n2);
		
		AAA a = new AAA();
		a.저장소역할();
		
		BBB b = new BBB();
		b.가져오기();
		
	}

}

```



```java title=MainClass03
package variable_;

class CCC {
	public static int num;
	public static int[] arr;
	
	static {
		num = 123;
		arr = new int[3];
		for(int i = 1; i< arr.length; i++) {
			arr[i] = i;
		}
	}
	
	public final static String KOREA = "대한민국";
	
	public void test() {
		num = 456;
	}
}

public class MainClass03 {
	int num;
	public static void main(String[] args) {
//		num = 12;
	}

}

```



## 정적 메소드 or 클래스 메소드(Static Method)


```java title=StaticMethodTest08

/*
 * static 키워드로 정의된 정적메소드 내에서는 this와 인스턴스 변수를 사용할 수 없다.
 * 
 */

class St08 {
	static int a = 10;	//정적 변수
	int b = 20;	// 인스턴스 변수
	
	public static void printA() {	// static 키워드로 정의된 정적 메소드
		// 정적 메소드(클래스 메소드)는 해당 클래스명으로  직접 접근한다.
//		System.out.println(this.a);	// Error, 정적 메소드 내에서는 this를 사용하지 못한다.
//		System.out.println(this.b);	// Error
//		
//		System.out.println(b);	// 정적 메소드 내에서는 인스턴스 변수를 사용할 수 없다.
		
		System.out.println(a);	// 정적 메소드에서 클래스 변수 사용하는 것은 되는 듯, 둘 다 객체화 하지 않아도 메모리에 올라와있기 때문
		
	}
}


public class StaticMethodTest08 {

	public static void main(String[] args) {
		St08.printA();	// 호출해서 결과 출력
	}

}

```



### 정적 메소드 주의사항

```java title=StaticMethodTest08

/*
 * static 키워드로 정의된 정적메소드 내에서는 this와 인스턴스 변수를 사용할 수 없다.
 * 
 */

class St08 {
	static int a = 10;	//정적 변수
	int b = 20;	// 인스턴스 변수
	
	public static void printA() {	// static 키워드로 정의된 정적 메소드
		// 정적 메소드(클래스 메소드)는 해당 클래스명으로  직접 접근한다.
//		System.out.println(this.a);	// Error, 정적 메소드 내에서는 this를 사용하지 못한다.
//		System.out.println(this.b);	// Error
//		
//		System.out.println(b);	// 정적 메소드 내에서는 인스턴스 변수를 사용할 수 없다.
		
		System.out.println(a);	// 정적 메소드에서 클래스 변수 사용하는 것은 되는 듯, 둘 다 객체화 하지 않아도 메모리에 올라와있기 때문
		
	}
}


public class StaticMethodTest08 {

	public static void main(String[] args) {
		St08.printA();	// 호출해서 결과 출력
	}

}

```



***



# 가변 인자(Variable Arguments)

```java title=

/* 가변인자 : variable arguments
 * 전달인자 개수가 다른 메소드가 오버로딩이 된 경우는 그 개수만큼 중복해서 메소드를 정의해야 한다.
 * 이러한 불편함을 해결하기 위해서 자바 5버전에서 가변인자라는 문법이 추가되었다.
 */


class Mt04 {
	
	void prn(int a) {
		System.out.println(a);
	}
	void prn(int a, int b) {
		System.out.println(a + "\t" + b);
	}
	void prn(int a, int b, int c) {
		System.out.println(a + "\t" + b + "\t" + c);
	}
	
} // Mt04 class

class Mt05 {
	// 가변인자 문법 적용 => int ... arr
	void prn(int ... arr) {
		for(int i : arr) {
			System.out.print(i + "\t");
		}
		
	}
}


public class VariableArgumentsTest04 {

	public static void main(String[] args) {
		Mt04 mt04 = new Mt04();
		
		mt04.prn(10);
		mt04.prn(10, 20);
		mt04.prn(10, 20, 30);

		System.out.println("\n ======================> 가변인자 문법 적용");
		
		Mt05 mt05 = new Mt05();
		
		mt05.prn(10);
		mt05.prn(10, 20);
		mt05.prn(10, 20, 30);
		
	}

}
```



***



# setter, getter

```java title=Ex01
package set_get;

class Test01 {
	public int num = 12345;
	public void test() {
		int num = 10000;
		System.out.println("this : " + this.num);
		System.out.println("test : " + num);
		this.test2();
	}
	
	public void test2() {
		System.out.println("test2 실행");
	}
}

public class Ex01 {
	public static void main(String[] args) {
		Test01 t = new Test01();
		
		System.out.println(t);
		t.test();
	}
	
}

```



![[Pasted image 20240813151012.png|400]]

```java title=Ex02
package set_get;

class Test_02 {
	private int num;
	private String name;
	
	public int getNum() {
		return num;
	}
	public void setNum(int num) {
		this.num = num;
	}
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	
}


class Test02 {
	private int num = 1234;
	private String name;
	
	public void setName(String s) {
		name = s;
	}
	public String getName() {
		return name;
	}
	
	public void setting(int n) {
		num = n;
	}
	public int getter() {
		return num;
	}
	
	
}


public class Ex02 {

	public static void main(String[] args) {
		Test02 t = new Test02();
		t.setting(100);
		System.out.println(t.getter());
		
		t.setName("홍길동");
		String s = t.getName();
		System.out.println("당신 이름 : " + s);
		
		
		Test_02 t02 = new Test_02();
		t02.setNum(12345);
		System.out.println(t02.getNum());
	}
	

}


```



```java title=Quiz03
package set_get;

import java.util.Scanner;

class LoginQuiz {
	private String id, password;
	
	public void setId(String s) {
		this.id = s;
	}
	public String getId() {
		return this.id;
	}
	
	public void setPassword(String s) {
		this.password = s;
	}
	public String getPassword() { 
		return this.password;
	}
	
	public boolean isExistUser(String id, String password) {
		return id.equals(this.id) && password.equals(this.password); 
	}
	
}

public class Quiz03 {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		LoginQuiz lq = new LoginQuiz();
		
		String menuMsg = "1. 로그인\n" + "2. 회원가입\n" + "3. 종료";
		
		String id = null, password = null;
		
		boolean loginProcess = true;
		while(loginProcess) {
			System.out.println(menuMsg);
			int select = sc.nextInt();
			
			switch(select) {
				case 1: 
					if(lq.getId() == null && lq.getPassword() == null) {
						System.out.println("등록된 유저 없음.. 회원가입 우선 진행");
						continue;
					}
					
					System.out.print("ID : ");
					id = sc.next();
					System.out.print("PW : ");
					password = sc.next();
					
					String loginSuccessMsg = lq.isExistUser(id, password) ? "로그인 성공" : "로그인 실패";
					System.out.println(loginSuccessMsg);
					
					break;
				case 2: 
					while(true) {
						System.out.print("가입할 ID : ");
						id = sc.next();
						
						if(!id.equals(lq.getId())) break;
						System.out.println("이미 가입된 ID..");
					}
					System.out.print("가입할 PW : ");
					password = sc.next();
					
					lq.setId(id);
					lq.setPassword(password);
					System.out.println("가입 성공");
					
					break;
				case 3: loginProcess = false; break;
				default : System.out.println("유효하지 않은 입력..");
			}
			
		}
		
		
	}
	

}
```



# Scanner 관련

>sc.next() : 공백을 구분자로 문자열 인식
>sc.nextLine() : 공백도 문자열로 인식하며 엔터값을 구분자로 각 문자열 인식
>
>sc.nextInt() : buffer에는 사용자가 입력한 "111(enter)" 가 들어있는 상태에서 nextInt()는 정수값만 가져가서 "(enter)"값만 buffer 공간에 남게 되니 nextInt() 메소드 다음에 nextLine()을 이용해서 문자열을 입력받으려고 할 경우 buffer에 남아있는 enter값 때문에 사용자의 입력을 받지 못하고 바로 종료되어 버리기 때문에 
>nextInt() 사용 후 nextLine() 같은 문자열을 입력 받기 위해서는 buffer에 남아있는 enter값을 한 번 비워줘야 한다. 변수에 저장하지 않고 그냥 sc.nextLine(); 메소드로 버퍼 클리어
>
>스트림 : 연결통로 (입력, 출력이 있음)
>
>sc.close()는 scanner 객체화 하여 사용하다 메모리에 상주하고 있는 상태를 해제 해버림?
>scanner는 메모리에서 해제되는 시기가 중구난방이라서 메모리를 효율적으로 사용하기 위해 sc.close() 메소드로 프로그램에 끝나는 즉시 메모리에서 해제 해버리기 위함


```java title=LoginQuiz(chatGPT)
/* chatGPT 작성해준 코드 참고하면서 작성 */
package set_get;

import java.util.Scanner;

class LoginQuiz {
	private String id, password;
	
	// 회원가입
	public void setIdPwd(String id, String password) {
		this.id = id;
		this.password = password;
	}
	
	// 로그인 성공 여부
	public boolean isLogin(String id, String password) {
		return id.equals(this.id) && password.equals(this.password); 
	}
	
	// 회원가입 유저 존재 여부
	public boolean isRegisterUser(String id) {
		return this.id != null;
	}
	
	// 등록된 ID 여부
	public boolean isExistId(String id) {
		return id.equals(this.id);
	}
}

public class Quiz03 {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		LoginQuiz lq = new LoginQuiz();
		
		String menuMsg = "1. 로그인\n" + "2. 회원가입\n" + "3. 종료";
		
		String id = null, password = null;
		
		boolean loginProcess = true;
		while(loginProcess) {
			System.out.println(menuMsg);
			int select = sc.nextInt();
			sc.nextLine(); // Enter값 제거
			
			switch(select) {
				case 1: 
					if(!lq.isRegisterUser(id)) {
						System.out.println("등록된 유저 없음.. 회원가입 진행");
						continue;
					}
					
					System.out.println("ID : ");
					id = sc.next();
					System.out.println("PW : ");
					password = sc.next();
					
					if(lq.isLogin(id, password)) {
						System.out.println("로그인 성공");
					}else {
						System.out.println("로그인 실패");
					}
					
					break;
				case 2: 
					System.out.print("등록할 ID : ");
					id = sc.next();
					
					if(lq.isExistId(id)) {
						System.out.println("이미 등록된 ID.. 재입력");
					}else {
						System.out.print("등록할 PW : ");
						password = sc.next();
						
						lq.setIdPwd(id, password);
						System.out.println("회원 등록 성공");
					}
					
					break;
				case 3: loginProcess = false; break;
				default : System.out.println("유효하지 않은 입력..");
			}
			
		}
		
		sc.close(); // 프로그램 끝나면 바로 메모리에서 해제
		
	}

}
```



***



# DTO(Data Transfer Object)
- 로직을 갖고 있지 않은 순수한 데이터 객체이며, 데이터를 전달하는 용도로 사용
  ex) Main 에서 사용하는 데이터들은 MainDTO에 보관
  Main 하위에 메일 보내는 기능이 있을 경우엔 MailDTO에 데이터를 모아서 처리

![[2_JAVA/0_용어#DTO (Data Transfer Object)]]

  

```java title=LoginDTO
package day08_;

public class LoginDTO {
	// Data Transform Object? : 데이터만 저장시키는 용도
	// setter와 getter만 저장하는 파일
	private String id, pwd;

	public String getId() {
		return id;
	}

	public void setId(String id) {
		this.id = id;
	}

	public String getPwd() {
		return pwd;
	}

	public void setPwd(String pwd) {
		this.pwd = pwd;
	}
	
}
```

```java title=Login
package day08_;

import java.util.Scanner;

/* 강사님 Quiz 풀이 */
public class Login {
//	private String id, pwd;
	private LoginDTO dto = new LoginDTO();
	
	
	public int loginCheck(String inputId, String inputPwd) {
		if(inputId.equals(dto.getId())) {
			if(inputPwd.equals(dto.getPwd())) {
				return 0;
			}else {
				return 1;
			}
		}else {
			return -1;
		}
	}

	
	public void display() {
		Scanner input = new Scanner(System.in);
		String inputId = null, inputPwd = null;
		
		while(true) {
			System.out.println("1.로그인");
			System.out.println("2.가입");
			System.out.println("3.종료");
			System.out.print(">>> ");
			int num = input.nextInt();
			input.nextLine();
			
			switch(num) {
				case 1:
					System.out.println("로긴 아이디 입력");
					inputId = input.next();
					System.out.println("로긴 비번 입력");
					inputPwd = input.next();
					
					int result = loginCheck(inputId, inputPwd);
					if(result == 0) {
						System.out.println("당신은 로그인 성공 사용자 입니다.");
					}else if(result ==1){
						System.out.println("비밀번호 틀림");
					}else {
						System.out.println("아이디 없음!!");
					}
					
					break;
				case 2:
					System.out.println("가입 아이디 입력");
					inputId = input.next();
					System.out.println("가입 비번 입력");
					inputPwd = input.next();
					
					int re = loginCheck(inputId, inputPwd);
					if(re != -1) {
						System.out.println("동일한 아이디 있음");
					}else {
						dto.setId(inputId);
						dto.setPwd(inputPwd);
						
						System.out.println("가입 완료");
					}
					
					break;
				case 3:
					return;
			}
	
			input.close();
			
		}
		
	}
	
	/*
	 * public String getId() { return id; }
	 * 
	 * public void setId(String id) { this.id = id; }
	 * 
	 * public String getPassword() { return pwd; }
	 * 
	 * public void setPassword(String password) { this.pwd = password; }
	 */
	
}

```

```java title=MainClass
package day08_;

public class MainClass {
	public static void main(String[] args) {
		Login login = new Login();
		login.display();
	}
	
}

```



***


# 참조 객체(Reference)

```java title=RefTest06

/*
 * 레퍼런스에 의한 호출 방식 예제 => 값이 전달되는 것이 아니라 객체 주소가 전달된다.
 */

class MyDate06 {
	int year = 2023;
	int month = 8;
	int date = 21;
}

class RefMethod {
	void changeDate(MyDate06 t) {	// MyDate06 t = md; => t와 md 객체주소는 같다..
		t.year = 2024;
		t.month = 9;
		t.date = 10;
	}
	
}

public class RefTest06 {

	public static void main(String[] args) {
		RefMethod rm = new RefMethod();
		MyDate06 md = new MyDate06();
		
		
		System.out.println("changeDate() 메소드 호출 전 : " + md.year + "년 " + md.month + "월 " + md.date + "일");
		rm.changeDate(md); // md 객체 주소를 전달
		System.out.println("changeDate() 메소드 호출 후 : " + md.year + "년 " + md.month + "월 " +  md.date + "일");
		
		
	}

}

```



***


# Error 메시지
## NullPointerException

```java title=NullPointerExeptionTest07

/*
 * 참조변수에 null만 대입한 상태에서 사용하면 NullPointerException 예외 오류가 발생한다.
 * 이런 경우는 try~catch문으로 예외 처리해야한다.
 */

class MyDate07 {
	int year = 2024;
	int month = 8;
	int day = 21;
}

public class NullPointerExeptionTest07 {

	public static void main(String[] args) {
		MyDate07 d = null;
		try {
			System.out.println(d.year + "년 " + d.month + "월 " + d.day + "일");	// Null Pointer Exception Error, 예외가 발생하면
			// 아래 문장 실행 안됨
			System.out.println("이 문장은 실행 안됨");
		}catch(Exception e) {		// 예외처리
			System.out.println("예외 오류 메시지 : " + e.getMessage());
			e.printStackTrace();	// 예외 족적을 남김 (에러 발생한 라인도 같이 출력??)
		}
		
	}

}

```



***



# 초기화 블록 


```java title=InitialBlockTest17

/*
 * 초기화 블록
 * 1. 생성자의 주된 기능은 클래스 소속 멤버변수 중 인스턴스 변수 초기화이다.
 * 2. 초기화란 변수 정의하고 최초값을 저장하는 것을 말한다.
 * 3. 클래스 초기화 블록 특징
 * 	가. 정적변수(클래스변수)의 복잡한 초기화에 사용된다.
 *  나. 해당 클래스가 메모리에 로딩될 때 딱 한 번만 수행한다.
 * 4. 인스턴스 초기화 블록 특징
 *  가. 인스턴스 변수의 복잡한 초기화에 사용된다.
 *  나. 생성자와 같이 인스턴스(객체)를 생성할 때마다 초기화 한다.
 *  다. 생성자보다 인스턴스 초기화 블록이 먼저 수행한다.
 */

public class InitialBlockTest17 {
	
	// 클래스 초기화 블록
	static {
		System.out.println("static()");
	}
	
	// 인스턴스 초기화 블록
	{
		System.out.println("{}");
	}
	
	// 기본 생성자
	public InitialBlockTest17() {
		System.out.println("기본 생성자 InitialBlockTest17()");
	}
	
	
	public static void main(String[] args) {
		new InitialBlockTest17();
		new InitialBlockTest17();
		
	}
	
}

```



## 클래스 초기화 블록

```java title=BlockTest18

/*
 * static 키워드로 정의된 정적 배열을 클래스 초기화 블록 static{}을 사용해서
 * 배열 원소값을 초기화 하는 예제
 */

public class BlockTest18 {
	static int[] arr = new int[10];	// 배열 크기가 10인 정적 배열 arr 생성
	
	// 클래스 초기화 블록에서 정적 배열 원소값 저장
	static {
		for(int i = 0; i < arr.length; i++) {
			arr[i] = (int)(Math.random() * 10) + 1;		// Math.random()은 0.0 이상 ~ 1.0 미만 사이의 실수 난수 발생
														// random * 10하면 0.0이상 10.0미만
														// (int)로 형변환하면 소수점 이하는 버리고 0이상 ~ 10미만 사이의 정수 숫자만 구함
														// 0 ~ 10 사이의 정수에 +1 하면 1 이상 ~ 11 미만 사이의 정수숫자가 arr 배열 원소값으로 저장
		}
		
	}
	public static void main(String[] args) {
		// 자바5에서 추가된 향상된 확장 for 반복문으로 배열 원소값을 출력
		for(int k : arr) {
			System.out.print(" " + k);
		}
	}

}

```



## 인스턴스 초기화 블록

```java title=InstanceBlockTest19

/*
 * 인스턴스 초기화 블록{}을 사용해서 정적 변수와 인스턴스 변수 초기화
 */
class Product {
	static int count = 0;	// 정적 변수, 생성된 객체수를 저장할 변수(총 생산된 제품 수)
	int serialNumber = 0;	// 인스턴스 변수, 생성된 객체의 고유 번호
	
	// 인스턴스 초기화 블록을 사용해서 정적 변수와 인스턴스 변수를 함께 초기화
	{
		++count;	// 누적 카운트 => 총 생상된 제품 수
		serialNumber = count;
	}
	
	public Product() {  } // 기본 생성자 => 생략해도 묵시적 제공
}

public class InstanceBlockTest19 {

	public static void main(String[] args) {
		Product p01 = new Product();
		Product p02 = new Product();
		Product p03 = new Product();
		
		System.out.println("p01의 제품 번호(시리얼번호) : " + p01.serialNumber);
		System.out.println("p02의 제품 번호(시리얼번호) : " + p02.serialNumber);
		System.out.println("p03의 제품 번호(시리얼번호) : " + p03.serialNumber);
		System.out.println("총 생상된 제품 수는 " + Product.count);	// 클래스명.정적변수로 접근한다.
	}

}

```



***



# 싱글톤 패턴
![[2_JAVA/0_용어#싱글톤 패턴(Singleton Pattern)]]


```java title=Singleton hl=singleton
package ch06.sec15;

public class Singleton {
	// private 접근 권한을 갖는 정적 필드 선언과 초기화
	private static Singleton singleton = new Singleton();
	private int age;
	private String name;
	
	// 생성자 선언
	private Singleton() {}
	
	// Getter/Setter
	public int getAge() {
		return this.age;
	}
	
	public void setAge(int age) {
		this.age = age;
	}
	
	public String getName() {
		return this.name;
	}
	
	public void setName(String name) {
		this.name = name;
	}
	
	// public 접근 권한을 갖는 정적 메소드 선언
	public static Singleton getInstance() {
		return singleton;
	}
	
}

```

```java title=SingletonExample
package ch06.sec15;

public class SingletonExample {

	public static void main(String[] args) {
		Singleton obj1 = Singleton.getInstance();
		Singleton obj2 = Singleton.getInstance();
		
		System.out.println("obj1.getAge() : " + obj1.getAge());
		obj1.setAge(20);
		System.out.println("obj1.getAge() : " + obj1.getAge());
		System.out.println("obj2.getAge() : " + obj2.getAge());
		
		if(obj1 == obj2) {
			System.out.println("같은 Singleton 객체입니다.");
		}else {
			System.out.println("다른 Singleton 객체입니다.");
		}
		
	}

}

```

>[!success] 실행 결과
> obj1.getAge() : 0
> obj1.getAge() : 20
> obj2.getAge() : 20
> 같은 Singleton 객체입니다.



***















