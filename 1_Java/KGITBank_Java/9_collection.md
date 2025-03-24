
# List

![[Pasted image 20240809123358.png|400]]

![[Pasted image 20240809123416.png|300]]

![[Pasted image 20240809123437.png|400]]


```java title=Ex01
package list_;

import java.util.ArrayList;

public class Ex01 {

	public static void main(String[] args) {
		int num = 10;
		System.out.println(num);
		
		Integer num2 = 100;
		System.out.println(num2);
		
		ArrayList<Integer> arr = new ArrayList<>();
		// arr[0] = 100;
		arr.add(100);
		arr.add(200);
		System.out.println(arr.get(0));
		System.out.println(arr.get(1));
		System.out.println(arr.size());
		
		int[] arr2 = new int[3];
		System.out.println(arr2.length);
		
		
		ArrayList<String> arr3 = new ArrayList<>();
		arr3.add("aaa");
		arr3.add("bbb");
		
		System.out.println(arr3);
		for(int i = 0 ; i < arr3.size() ; i++) {
			System.out.println(arr3.get(i));
		}
		
		System.out.println("------- foreach -------");
		
		for(String s : arr3) {
			System.out.println(s);
		}
		
	}

}
```



```java title=Ex02
package list_;

import java.util.ArrayList;
import java.util.Scanner;

public class Ex02 {

	public static void main(String[] args) {
		ArrayList<String> arr = new ArrayList<>();
		
		System.out.println(arr.add("1111"));
		System.out.println(arr.get(0));
		
		boolean bool = arr.add("1111");
		String s = arr.get(0);
		s += "수정";
		System.out.println(s);
		
		arr.add("111");
		arr.add("222");
		arr.add("333");
		
		System.out.println(arr.contains("222"));
		System.out.println(arr.contains("없는 값"));
		
		boolean b = arr.contains("특정 값");
		if(b) {
			System.out.println("존재합니다.");
		}else {
			System.out.println("존재하지 않습니다.");
		}
		
		System.out.println("삭제 전 : " + arr);
		System.out.println(arr.remove(0));
		System.out.println("삭제 후 : " + arr);
		System.out.println(arr.size());
		
		if(arr.size() > 5) {
			System.out.println(arr.remove(5));
		}
		
		System.out.println("-----------------");
		System.out.println(arr.remove("222"));
		System.out.println(arr.remove("없는 값"));
		
		
	}

}
```



```java title=Ex03
package list_;

import java.util.ArrayList;
import java.util.Scanner;

public class Ex03 {

	public static void main(String[] args) {
		Scanner input = new Scanner(System.in);
		ArrayList<String> arr = new ArrayList<>();
		
		for(int i = 0 ; i < 3 ; i++) {
			System.out.print((i + 1) + "번째 값 입력 : ");
			String n = input.next();
			arr.add(n);
		}
		System.out.println("기본 : " + arr);
		System.out.println("찾는 값 입력");
		String search = input.next();
		System.out.println(arr.indexOf(search)); // 인덱스 위치 반환
		System.out.println(arr.contains(search));
		
//		int index = input.nextInt();
//		String msg = input.next();
//		arr.set(index, msg);
		
		arr.set(1, "다른값");
		System.out.println(arr);
		
	}

}

```



# List Quiz
![[Pasted image 20240809123619.png|600]]


```java title=Quiz
package list_;

import java.util.ArrayList;
import java.util.Scanner;

public class Quiz {

	public static void main(String[] args) {
		
		Scanner input = new Scanner(System.in);
		
		ArrayList<String> name = new ArrayList<>();
		ArrayList<String> phoneNum = new ArrayList<>();
		
		String printMsg = "1.연락처 등록\n" + "2.연락처 보기\n" + "3.연락처 삭제\n" + "4.모든 연락처 보기\n" + "5.종료\n" + ">>> ";

		boolean savePhoneNumProcess = true;
		while(savePhoneNumProcess) {
			System.out.print(printMsg);
			int select = input.nextInt();
			
			if(select == 1) {
				System.out.print("이름 : ");
				String addName = input.next();
				System.out.print("연락처 : ");
				String addPhoneNum = input.next();
				
				boolean isNameDupl = name.contains(addName);
				boolean isPhoneNumDupl = phoneNum.contains(addPhoneNum);
				if(!isNameDupl && !isPhoneNumDupl) {
					if (name.add(addName) && phoneNum.add(addPhoneNum)) {
						System.out.println("등록 완료");
					}
				}else {
					System.out.println("이름 or 전화번호 중복.. 다시 입력");
					continue;
				}
				
				
			}else if(select == 2) {
				if(phoneNum.size() == 0 && name.size() == 0) {
					System.out.println("등록된 연락처가 없음..");
					continue;
				}
				
				System.out.print("확인할 연락처 : ");
				String searchPhoneNum = input.next();
				
				boolean isExistPhoneNum = phoneNum.contains(searchPhoneNum);
				if(isExistPhoneNum) {
					int searchIndex = phoneNum.indexOf(searchPhoneNum);
					
					System.out.println("찾은 연락처의 주인 이름 : " + name.get(searchIndex) + ", " + "연락처 : " + phoneNum.get(searchIndex));
				}else {
					System.out.println("존재하지 않는 연락처..");
					continue;
				}
				
				
			}else if(select == 3) {
				System.out.print("삭제할 연락처 : ");
				String delPhoneNum = input.next();
				
				boolean isExistDelPhoneNum = phoneNum.contains(delPhoneNum);
				if(!isExistDelPhoneNum) {
					System.out.println("목록에 없는 연락처.. 다시 입력");
					continue;
				}
				
				int searchIndex = phoneNum.indexOf(delPhoneNum);
				if(phoneNum.remove(delPhoneNum)) {
					name.remove(searchIndex);
					System.out.println(delPhoneNum + " 삭제 완료");
				}else {
					System.out.println("예기치 못하게 삭제 실패?");
				}
				
				
			}else if(select == 4) {
				if(phoneNum.size() == 0 && name.size() == 0) {
					System.out.println("등록된 정보 없음..");
					continue;
				}
				
				for(int i = 0 ; i < name.size() ; i++) {
					System.out.println("[ 이름 : " + name.get(i) + ", " + "연락처 : " + phoneNum.get(i) + " ]");
				}
				
				
			}else if(select == 5) {
				savePhoneNumProcess = false;
				
				
			}else {
				System.out.println("유효하지 않은 입력..");
			}
			
		}
		
		
	}

}
```



```java title="Quiz 강사님코드"
/* 강사님 코드*/
		
		ArrayList<String> nameArr = new ArrayList<>();
		ArrayList<String> phoneArr = new ArrayList<>();
		
		int num;
		String name, phoneNum;
		
		while(true) {
			System.out.println("1.연락처 등록");
			System.out.println("2.검색");
			System.out.println("3.삭제");
			System.out.println("4.모두 보기");
			System.out.println("5.종료");
			System.out.print(">>> : ");
			num = input.nextInt();
			switch(num) {
				case 1:
					// 이름 중복 확인
					System.out.println("이름 입력");
					name = input.next();
					System.out.println("전화번호 입력");
					phoneNum = input.next();
					
					if(!nameArr.contains(name)) {
						nameArr.add(name);
						phoneArr.add(phoneNum);
					}else {
						System.out.println("동일한 값");
					}
					
					break;
				case 2:
					System.out.println("검색 이름 입력");
					name = input.next();
					int re = nameArr.indexOf(name);
					
					if(re == -1) {
						System.out.println("없음");
					}else {
						System.out.println(nameArr.get(re));
						System.out.println(phoneArr.get(re));
					}
					
					break;
				case 3:
					System.out.println("삭제 이름 입력");
					name = input.next();
					int index = nameArr.indexOf(name);
					
					if(index == -1) {
						System.out.println("삭제 없음");
					}else {
						nameArr.remove(index);
						phoneArr.remove(index);
					}
					break;
					
				case 4:
//					System.out.println(nameArr);
//					System.out.println(phoneArr);
					System.out.println("이름\t전화번호");
					System.out.println("==============================");
					for(int i = 0 ; i < nameArr.size() ; i++) {
						System.out.println(nameArr.get(i) + "\t " + phoneArr.get(i));
					}
				case 5: break;
			}
			
		}
```



***



# Set

![[Pasted image 20240809144328.png|400]]


```java title=Ex01
package set_;

import java.util.ArrayList;
import java.util.HashSet;

public class Ex01 {

	public static void main(String[] args) {
		HashSet<String> set = new HashSet<>();
		ArrayList<String> list = new ArrayList<>();
		
		set.add("라면");
		set.add("순대");
		set.add("김밥");
		set.add("라면");
		
		list.add("라면");
		list.add("순대");
		list.add("김밥");
		list.add("라면");
		
		System.out.println(set);
		System.out.println(list);
		
		
		System.out.println(set.contains("라면"));
		
		
//		System.out.println(set.remove("순대"));
		System.out.println(set.remove(1));
		System.out.println(set);
	}

}
```


## 반복자(Iterator)
![[Pasted image 20240809144431.png|300]]
- bof : 반복자의 시작 의미
- eof : 반복자의 끝 의미

```java title=Ex02
package set_;

import java.util.ArrayList;
import java.util.HashSet;
import java.util.Iterator;

public class Ex02 {

	public static void main(String[] args) {
////		ArrayList에 타입 안 적었을 때
////		장점 : 똑같이 기능 쓸 수 있으며, 아무 값이나 저장 가능 (출력하고 저장할 때는 좋음..)
////		많이 저장되어 있을수록 어느 공간에 무슨 값이 저장되어있는지 확인하기 힘듦
//		ArrayList arr = new ArrayList();
//		arr.add(111);
//		arr.add(111.111);
//		arr.add("문자열");
//		arr.add(111);
//		arr.add(111.111);
//		arr.add("문자열");
//		arr.add(111);
//		arr.add(111.111);
//		arr.add("문자열");
//		System.out.println(arr);
//		
//		// 무슨 값이 있는지와 타입을 알면 형변환하여 가져올 수 있긴 함
//		// 결국 저장은 편하나 가져와서 쓰는게 힘드니 별로 안 쓴다고 하시는 듯
//		int i = (int)arr.get(5);
		
		ArrayList<String> arr = new ArrayList<>();
		
		arr.add("111");
		arr.add("222");
		arr.add("333");
		System.out.println(arr);
		
		// iterator : 반복자
		// bof : 반복자의 시작
		// eof : 반복자의 끝
		Iterator<String> it = arr.iterator();
		
		/*
		 * // hasNext() : 다음 위치에 값이 있는지 여부 System.out.println(it.hasNext());
		 * 
		 * // next() : 다음 위치에 값이 있는걸 확인했으니 next()로 가져오기(String) // 다음 위치로 이동을 한 뒤, 현재
		 * 위치의 값을 가져온다. -> it : bof | "111" | "222" | "333" | eof
		 * System.out.println(it.next()); // "111"
		 * 
		 * System.out.println(it.hasNext()); System.out.println(it.next());
		 * 
		 * System.out.println(it.hasNext()); System.out.println(it.next());
		 * 
		 * // 다음 위치엔 eof를 만나서 hasNext()의 결과값이 false를 반환
		 * System.out.println(it.hasNext()); // System.out.println(it.next());
		 */		
		

		// 반복문 이용한 전체 값 가져오기
		while(it.hasNext()) {
			String n = it.next();
			System.out.println(n);
		}
		
		
		// HashSet은 데이터를 1개씩 밖에 못 가져옴...?
		HashSet<Integer> set = new HashSet<>();
		
		set.add(111);
		set.add(222);
		set.add(333);
		
		System.out.println(set);
		Iterator<Integer> s = set.iterator();
		
		while(s.hasNext()) {
			int num = s.next();
			System.out.println(num);
		}
		
		
		
		
	}

}
```



***



# Random
## Random class
```java title=Ex01
package random_;

import java.util.Random;

public class Ex01 {

	public static void main(String[] args) {
		Random ran = new Random();
		
		int num = ran.nextInt(3); // 0 ~ 2
		System.out.println(num);
		
		for(int i = 0; i < 5; i++) {
			num = ran.nextInt(3);
			System.out.println(num + 10);
		}
		
		
		for(int i = 0; i < 5; i++) {
			double d = Math.random();
			// (0.00000 ~ 0.99999) * 3 = 0.000 ~ 2.999 사이값이 나온다. 이 값을 int로 형변환하면 실수값을 버리기 때문에 0~2까지 출력
			System.out.println((int)(d * 3));
		}
		
		
		
	}

}

```


## Math.random()
```java title=Quiz
package random_;

import java.util.ArrayList;
import java.util.HashSet;

public class Quiz {

	public static void main(String[] args) {
		// 로또 프로그램 : 1 ~ 45의 랜덤 숫자, 각각 ArrayList, HashSet 으로 만들어보기! 중복되지 않은 숫자들을 넣도록
		
		/* ArrayList */
		ArrayList<Integer> lottoListArr = new ArrayList<>();
		
		int repeat = 45;
		for(int i = 0; i < repeat; i++) {
			double ranDouble = Math.random();
			int randInt = (int)(ranDouble * repeat) + 1;
			
			if(!lottoListArr.contains(randInt)) {
				lottoListArr.add(randInt);
			}else {
				i--;
			}
		}
		System.out.println(lottoListArr);
		
		
		/* HashSet */
		HashSet<Integer> lottoHashArr = new HashSet<>();
		
		repeat = 45;
		for(int i = 0; i < repeat; i++) {
			int hashInt = (int)(Math.random() * repeat) + 1;
			
			if(!lottoHashArr.add(hashInt)) {
				i--;
			}
		}
		System.out.println(lottoHashArr);
		
		
		
	}

}

```


```java title="강사님 Quiz 풀이"
package random_;

import java.util.ArrayList;
import java.util.HashSet;

public class Quiz {
	public static void main(String[] args) {
		ArrayList<Integer> arr = new ArrayList<>();
		int ran = 0 ;
		while( arr.size()<6 ){
			ran = (int)(Math.random()*6)+1;
			if(arr.contains(ran)==false)  
				arr.add(ran);
		}
		System.out.println("=== ArrayList Lotto ===");
		System.out.println( arr );
		Random rand = new Random();
		HashSet<String> hs = new HashSet<>();
		while(hs.size()<6){
			ran = rand.nextInt(45)+1;  
			hs.add(ran+""); 
		}
		System.out.println("=== HashSet Lotto ===");
		System.out.println( hs );
		
		
		
	}

}
```



***



# Map

![[Pasted image 20240812090853.png|450]]


```java title=Ex01
package map_;

import java.util.HashMap;

public class Ex01 {

	public static void main(String[] args) {
		HashMap<String, String> map = new HashMap<>();
		
		map.put("num", "100");
		map.put("name", "홍길동");
		
		System.out.println(map);
		System.out.println(map.get("num"));
		System.out.println(map.get("name"));		
		System.out.println(map.get("없는 키"));
		
		
		HashMap<String, Integer> map2 = new HashMap<>();
		map2.put("age", 20);
		map2.put("num", 12345);
		
		int num = map2.get("num");
		System.out.println("num : " + num);
		System.out.println("get : " + map2.get("num"));
		
		int age = map2.get("age");
		age -= 1;
		System.out.println("age : " + age);
		System.out.println("get age : " + map2.get("age"));
		
		System.out.println(map2.containsKey("age"));
		System.out.println(map2.containsValue(1111));
		
		System.out.println("변경 전 : " + map2);
		map2.put("age", 5555);
		map2.put("a", 20);
		System.out.println("변경 후 : " + map2);
		
		map2.remove("age");
		System.out.println("삭제 후 : " + map2);
		
		

	}

	
}
```



```java title=Ex02
package map_;

import java.util.HashMap;
import java.util.Iterator;
import java.util.Set;

public class Ex02 {

	public static void main(String[] args) {
		int num = 100;
		String str = num + ""; // 자동 형변환
		
		// 정수를 문자열로 변환
		str = Integer.toString(num);
		// 문자열을 정수로 변환
		int a = Integer.parseInt(str);
		
		HashMap<String, String> map = new HashMap<>();
		
		map.put("이름", "홍길동");
		map.put("나이", "20");
		
		String age = map.get("나이");
		
		int age2 = Integer.parseInt(age) - 1;
		age = Integer.parseInt(age) - 1 + "";
		
		System.out.println("age2 : " + age2);
		System.out.println("age : " + age);
		
		System.out.println("map : " + map);
		// map에 존재하는 키값만 set 변수에 저장
		Set<String> set = map.keySet(); 
		// 위의 set 변수에 저장하는 과정에서 "빈공간 | 이름 | 빈공간 | 빈공간 | 나이 | 빈공간 ..."이런식으로 비효율적으로 저장이 되니
		// 반복자로 변환해서 "bof | 이름 | 나이 | eof" 로 데이터를 효율적으로 가져오기 위해? 사용하는 듯
		Iterator<String> it = set.iterator(); 
		
		while(it.hasNext()) {
//			System.out.println(it.next());
			String key = it.next();
			
			System.out.println(key + " : " + map.get(key));
		}
		
		
	}

}
```



## Map Quiz
![[Pasted image 20240812102459.png|300]]

![[Pasted image 20240812102509.png|300]]


```java title=Quiz
package map_;

import java.util.HashMap;
import java.util.Iterator;
import java.util.Scanner;
import java.util.Set;

public class Quiz {

	public static void main(String[] args) {
		Scanner input = new Scanner(System.in);
		
		HashMap<String, String> menu = new HashMap<>();
		
		String printMsg = "1. 메뉴 등록\n" + "2. 메뉴별 가격 보기\n" + "3. 종료\n" + ">>> ";
		String menuName, menuPrice;
		
		boolean menuProcess = true;
		while(menuProcess) {
			Set<String> menuKey = menu.keySet();
			Iterator<String> menuIterList = menuKey.iterator(); 
			
			System.out.print(printMsg);
			int select = input.nextInt();
			
			switch(select) {
				case 1: 
					System.out.print("메뉴 이름 등록 : ");
					menuName = input.next();
					System.out.print("메뉴 가격 등록 : ");
					menuPrice = input.next();
					
					if(menu.containsKey(menuName)) {
						System.out.print("기존에 등록된 메뉴인데 덮어쓰기 (Y/N) : ");
						String isYorN = input.next();
						
						switch(isYorN) {
							case "Y": break;
							case "N": continue;
							default: System.out.println("Y or N 만 입력"); break;
						}
					}
					menu.put(menuName, menuPrice);
					System.out.println("등록 완료");
					
					break;
				case 2: 
					if(menu.size() > 0) {
						boolean menuPrintProcess = true;
						while(menuPrintProcess) {
							String menuPrint = "";
							while(menuIterList.hasNext()) {
								String key = menuIterList.next();
								
								menuPrint += "- " + key + " : " + menu.get(key) + "\n";
							}
							menuPrint += "1. 수정 " + "2. 삭제 " + "3. 나가기 \n" + ">>> ";
							System.out.print(menuPrint);
							int choice = input.nextInt();
							
							switch(choice) {
								case 1: 
									System.out.print("수정할 메뉴 : ");
									menuName = input.next();
									System.out.print("수정할 가격 : ");
									menuPrice = input.next();
									
									if(!menu.containsKey(menuName)) {
										System.out.println("기존에 없는 메뉴인데.. 다시 입력");
										continue;
									}
									
									menu.put(menuName, menuPrice);
									System.out.println(menuName + "의 기존 가격 : " + beforePrice + "원 -> " + menuPrice + "원 으로 변경됨");
									
									break;
								case 2: 
									System.out.print("삭제할 메뉴 : ");
									menuName = input.next();
									
									if(!menu.containsKey(menuName)) {
										System.out.println("기존에 없는 메뉴인데.. 다시 입력");
										continue;
									}
									
									menu.remove(menuName);
									System.out.println("메뉴 삭제 완료");
									
									break;
								case 3: menuPrintProcess = false; break;
							} // choice switch
							
						} // menuPrintProcess while
						
					}else { // menu.size() if
						System.out.println("등록된 메뉴가 없으므로 메뉴 등록 먼저");
					}
					
					break;
				case 3: menuProcess = false; break;
			} // select switch
			
		} // menuProcess while 
		
	} // main
	

} // class
```



```java title="강사님 Quiz 풀이"
package map_;

import java.util.HashMap;
import java.util.Iterator;
import java.util.Scanner;
import java.util.Set;

public class Quiz02 {
   public static void main(String[] args) {
      Scanner input = new Scanner(System.in);
      HashMap<String, String> map = new HashMap<>();
      int num;
      String menu =null, money=null;
      while(true) {
         System.out.println("1.메뉴 등록");
         System.out.println("2.가격 보기");
         System.out.println("3.종료");
         System.out.print(">>> : ");
         num = input.nextInt();
         switch (num) {
         case 1:
            while(true) {
               System.out.println("메뉴 입력");
               menu = input.next();
               if( map.containsKey(menu) ) {
                  System.out.println("존재하는 메뉴.. 다시 입력..");
                  continue;
               }
               break;
            }
            System.out.println("가격 입력");
            money = input.next();
            map.put(menu, money);
            break;
         case 2:
            //System.out.println( map );
            //Set<String> set = map.keySet();
            //Iterator<String> it = set.iterator();
            Iterator<String> it = map.keySet().iterator();
            //while( it.hasNext() ) {
            for( int i=1 ; it.hasNext() ; i++) {
               String key = it.next();
               System.out.println(i+"."+key+" : "+map.get(key) );
            }
            System.out.println("---------------");
            boolean bool = true;
            while( bool ) {
               System.out.println("1.수정 2.삭제 3.나가기");
               num = input.nextInt();
               switch (num) {
               case 1:   
                  System.out.println("수정 메뉴 입력");
                  menu = input.next();
                  if( map.containsKey(menu) ) {
                     System.out.println("변경 가능 메뉴");
                     System.out.println("변경 가격 입력");
                     money = input.next();
                     System.out.println(map.get(menu)+" => "+money);
                     map.put(menu, money);
                  }else {
                     System.out.println("메뉴 없음!!!");
                  }
                  break;
               case 2:   
                  System.out.println("삭제 메뉴 입력");
                  menu = input.next();
                  if( map.containsKey(menu) ) {
                     System.out.println("삭제 가능 메뉴");
                     map.remove(menu);
                  }else {
                     System.out.println("메뉴 없음!!!");
                  }
                  break;
               //if( num == 3 ) break;
               case 3:   
                  System.out.println("나가기");
                  bool = false;
                  break;
               }
            }
            
         }
      }
   }
}

```








