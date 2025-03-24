# 배열(Array)

![[Pasted image 20240808105029.png|500]]


```java title=Ex01
package array_;

public class Ex01 {

	public static void main(String[] args) {
		int[] arr = new int[5];
		
		System.out.println(arr[0]);
		arr[0] = 100;
		arr[1] = 200;
		System.out.println(arr[0]);
		System.out.println(arr[1]);
		System.out.println(arr[2]);
		
		double[] dos = new double[] {1.11, 2.22, 3.33};
		System.out.println(dos[0]);
		System.out.println(dos[1]);
		System.out.println(dos[2]);
		
		System.out.println("int length : " + arr.length);
		System.out.println("dos length : " + dos.length);
		
		for(int i = 0; i < dos.length; i++) {
			System.out.println(dos[i]);
		}
		
		String[] str = {"aaa", "bbb", "ccc"};
		for(int i = 0; i < str.length; i++) {
			System.out.println(str[i]);
		}

		System.out.println("----- for each -----");
		
		for(double d : dos) {
			System.out.println(d);
		}
		for(String s : str) {
			System.out.println(s);
		}
		
		
		
	}

}

```



## 배열 Quiz

![[Pasted image 20240808104952.png|450]]


```java title=Quiz01
package array_;

public class Quiz {

	public static void main(String[] args) {
		int[] arr = new int[] { 10, 54, 13, 17, 25, 30 };
		
		String message = null;
		for(int num : arr) {
			message = num % 2 == 0 ? "짝수 : " + num : "홀수 : " + num;
			System.out.println(message);
		}
		
		
	}

}

```



## 배열 Quiz2
![[Pasted image 20240808135808.png|500]]


```java title=Quiz02
package array_;

import java.util.Scanner;

public class Quiz02 {

	public static void main(String[] args) {
		Scanner input = new Scanner(System.in);
		
		int arr[] = new int[] { 10, 54, 13, 17, 25, 30 };
		String odd_even = null;
		System.out.print("짝수, 홀수 입력 : ");
		odd_even = input.next();
		
		for (int i : arr) {
			if(odd_even.equals("짝수")) {
				if(i % 2 == 0) {
					String message = "짝수 : " + i;
					System.out.println(message);
				}
			}else {
				if(i % 2 == 1) {
					String message = "홀수 : " + i;
					System.out.println(message);
				}
			}
			
		}

		
		
	}

}
```



## 배열 Quiz3

![[Pasted image 20240808135839.png|400]]


```java title=Quiz03
package array_;

import java.util.Scanner;

public class Quiz03 {

	public static void main(String[] args) {
		Scanner input = new Scanner(System.in);
		
		int arr[] = new int[] { 10, 54, 13, 17, 25, 30 };
		String odd_even = null;
		
		System.out.print("짝수, 홀수 입력 : ");
		odd_even = input.next();
		
		for (int i = 0; i < arr.length; i++) {
			if(odd_even.equals("짝수") && i % 2 == 0) {
				System.out.println(arr[i] + ",");
			}else if(odd_even.equals("홀수") && i % 2 == 1) {
				System.out.println(arr[i] + ",");
			}
		}
		
		
		
		
	}

}
```


## 배열 Quiz4

![[Pasted image 20240808135922.png|500]]

![[Pasted image 20240808145532.png|500]]


```java title=Quiz04
package array_;

import java.util.Scanner;

public class Quiz04 {

	public static void main(String[] args) {
		
		Scanner input = new Scanner(System.in);
		
		String[] id = new String[5];
		String[] pwd = new String[5];
		int userId = 0;
		
		boolean quizProcess = true;
		while(quizProcess) {
			String printMessage = "1. 로그인\n" + "2. 회원가입\n" + "3. 모든 회원 보기\n" + "4. 수정\n" + "5. 삭제\n" + "6. 나가기\n" + ">>> ";
			System.out.print(printMessage);
			int select = input.nextInt();
			
			switch(select) {
				case 1: 
					System.out.print("ID : ");
					String inputLoginId = input.next();
					System.out.print("PWD : ");
					String inputLoginPwd = input.next();
					
					int failCount = 0;
					for(int i = 0; i < id.length; i++) {
						if(inputLoginId.equals(id[i])) {
							if(inputLoginPwd.equals(pwd[i])) {
								System.out.println("인증 성공");
							}else {
								System.out.println("비밀번호 틀렸습니다.");
							}
						}else {
							failCount++;
						}

						if(failCount == id.length) {
							System.out.println("존재하지 않는 회원");
						}
						
					}
					break;
				case 2:
					System.out.print("ID : ");
					String inputJoinId = input.next();
					System.out.print("PWD : ");
					String inputJoinPwd = input.next();
					
					for(int i = 0; i < id.length; i++) {
						if(inputJoinId.equals(id[i])) {
							System.out.println("동일한 아이디가 존재합니다.");
							break;
						}
					}
					if(userId == id.length) {
						System.out.println("저장할 공간이 없습니다.");
						continue;
					}
					
					if(userId <= id.length) {
						userId++;
						id[userId - 1] = inputJoinId;
						pwd[userId - 1] = inputJoinPwd;
						System.out.println("회원가입 축하");
					}
					break;
				case 3: 
					for(int i = 0; i < id.length; i++) {
						System.out.println((i + 1) + "번째 회원ID : " + id[i]);
					}
					break;
				case 4: 
					System.out.print("수정할 ID 입력 : ");
					String inputModiId = input.next();
					
					boolean foundModiId = false;
					for (int i = 0; i < id.length; i++) {
						if (inputModiId.equals(id[i])) {
							System.out.print("수정할 ID의 패스워드 : ");
							String inputModiPwd = input.next();
							
							foundModiId = true;
							pwd[i] = inputModiPwd;
							System.out.println(id[i] + "의 패스워드 수정 완료");
							break;
						}
					}
					
					if(!foundModiId) {
						System.out.println("해당 ID는 존재하지 않습니다.");
					}
					break;
				case 5: 
					System.out.print("삭제할 ID 입력 : ");
					String inputDelId = input.next();
					
					boolean foundDelId = false;
					for(int i = 0; i < id.length; i++) {
						if (inputDelId.equals(id[i])) {
							String tempId = id[i];
							
							foundDelId = true;
							id[i] = null;
							pwd[i] = null;
							
							System.out.println(tempId + " 회원 제거 완료");
							break;
						}
					}
					
					if(!foundDelId) {
						System.out.println("해당 ID는 존재하지 않아 삭제할 수 없습니다.");
					}
					break;
				case 6: quizProcess = false; continue;
				default: System.out.println("입력이 올바르지 않음"); continue;
			}
			
		}
		
		
	}
}

```



```java title=hyeok
package array;

import java.util.Scanner;

public class Quiz4 {

   public static void main(String[] args) {
      // 배열 5개를 만들고 로그인 프로그램을 만드시오.
      // 1. 로그인시
      // - 아이디가 없다면 존재하지 않는 아이디입니다.
      // - 비밀번호가 틀리면 비밀번호가 틀렸습니다.
      // - 아이디와 비밀번호가 일치하면 인증통과
      // 2. 회원가입시
      // - 동일한 아이디가 있으면 동일한 아이디가 존재합니다.
      // - 5개의 배열 모두 사용됐으면 더 이상 저장할 공간이 없습니다.
      // - 회원가입 성공시 가입을 축하합니다.
      // 3. 모든 회원보기
      // 4. 수정
      // - 수정시 수정하고자 하는 id 입력, 저장 데이터 중 입력한 id와 일치하는 값이 존재하면 변경할 비밀번호 입력 후 비밀번호 변경
      // - 존재 하지 않는 id면 "해당 id는 존재하지 않습니다"
      // 5. 삭제
      // - 수정과 동일하게 비교하며, 일치하는 id가 있을경우 null값으로 변경
      // - 존재 하지 않는 id면 "해당 id는 삭제할 수 없습니다"

      Scanner sc = new Scanner(System.in);

      String[] saveId = new String[5];
      String[] savePwd = new String[5];
      String id = null, pwd = null, signId = null, signPwd = null, modiId = null, modiPwd = null, del = null, delch = null;;
      boolean repeat = true;
      int num = 0;

      while (repeat) {
         System.out.println("1. 로그인");
         System.out.println("2. 회원가입");
         System.out.println("3. 모든회원 보기");
         System.out.println("4. ID 수정");
         System.out.println("5. ID 삭제");         
         System.out.print(">>> ");
         num = sc.nextInt();

         switch (num) {
         case 1: {
            System.out.println("ID를 입력해 주세요");
            id = sc.next();
            System.out.println("PWSSWORD를 입력해 주세요");
            pwd = sc.next();

            for (int i = 0; i < saveId.length; i++) {
//               for (int j = 0; j < savePwd.length; j++) {
               if (id.equals(saveId[i]) && pwd.equals(savePwd[i])) {
                  // 저장되어있는 ID와 PWD가 모두 맞을때
                  System.out.println("====인증통과====");
                  break;
               } else if (id.equals(saveId[i]) && !pwd.equals(savePwd[i]) || pwd.equals(savePwd[i])) {
                  // 저장되어있는 ID는 맞으나 PWD가 틀릴때
                  System.out.println("비밀번호가 틀렸습니다.");
                  break;
               } else if (id.equals(saveId[i]) || !id.equals(saveId[i]) && pwd.equals(savePwd[i])) {
                  // 저장되어있는 ID가 틀리고 PWD는 맞을떄
                  System.out.println("아이디가 틀렸습니다.");
                  break;
               } else if (!id.equals(saveId[i]) && saveId[i] == null) {
                  // ID가 존재하지 않을때
                  System.out.println("존재하지 않는 아이디입니다.");
                  break;
//               } else if (!id.equals(saveId[i]) && !pwd.equals(savePwd[i])) {
//                  System.out.println("아이디와 비밀번호가 틀렸습니다.");
//                  break;
               }
               if (i > 5) {
                  break;
               }
            }
            break;
         }

         case 2: {
            System.out.println("사용하실 ID를 입력해 주세요");
            signId = sc.next();
            System.out.println("PWSSWORD를 입력해 주세요");
            signPwd = sc.next();
            int i = 0;

            for (i = 0; i < saveId.length; i++) {
               if (saveId[i] != null && signId.equals(saveId[i])) {
                  // index ID에 빈공간이 아니며, ID가 일치할때 저장실패
                  System.out.println("동일한 아이디가 존재합니다.");
                  break;
               } else if (saveId[i] == null && !signId.equals(saveId[i])) {
                  // index ID에 빈공간이며, ID가 일치하지 않을때 저장
                  saveId[i] = signId;
                  savePwd[i] = signPwd;
                  System.out.println("회원가입 성공");
                  break;
               }
            }
            if (i == saveId.length) {
               System.out.println("더 이상 저장할 공간이 없습니다.");
            }
            break;
         }
         case 3: {
            System.out.println("저장되어있는 ID : PW");
            for (int i = 0; i < saveId.length; i++) {
               System.out.print("ID : " + saveId[i] + "/PW : " + savePwd[i] + "\n");
            }
            break;
         }
         case 4: {
            System.out.println("수정하고자 하는 ID를 입력해주세요");
            modiId = sc.next();
            int j = 0;
            for(int i = 0; i < saveId.length; i++) {
               if(modiId.equals(saveId[i])) {
                  // index ID가 수정ID와 일치할 때
                  System.out.println(saveId[i]+" ID의 수정하실 PWD를 입력해주세요");
                  modiPwd = sc.next();
                  savePwd[i] = modiPwd;
                  // 저장 Pwd에 수정 Pwd 기입
                  System.out.println(saveId[i]+" ID의 Pwd 수정이 완료되었습니다.");
                  break;
               } else if(j == saveId.length) {
                  // index ID가 빈공간이며 수정ID가 저장아이디와 일치하지 않을때
                  System.out.println(modiId+" 해당 ID는 존재하지 않습니다.");
                  break;
               }
                  
            }
            break;
         }
         case 5: {
            System.out.println("삭제하고자 하는 ID를 입력해주세요");
            del = sc.next();
            int j = 0;
            for(int i = 0; i < saveId.length; i++) {
               if(del.equals(saveId[i])) {
                  // 지우고자 하는 ID가 저장된 ID와 일치할 때
                  System.out.println(saveId[i]+" ID를 삭제하시겠습니까? (Y/N)");
                  delch = sc.next();
                  if(delch.equals("Y") || delch.equals("y")) {
                     // Y or y를 입력 했다면?
                     System.out.println(saveId[i]+" ID와 Pwd 삭제가 완료되었습니다.");
                     saveId[i] = savePwd[i] = null;
                     // index에 저장된 ID와 PWD를 null로 초기화
                  } else if(delch.equals("N") || delch.equals("n")) {
                     // N or n을 입력 했다면?
                     System.out.println("취소되었습니다.");
                  } else {
                     System.out.println("잘못 누르셨습니다.");
                  }
                  break;
               } else if(j == saveId.length) {
                  // 저장된 아이디가 빈공간 이면서 지우고자하는 ID와 저장된 ID가 일치하지 않을때
                  System.out.println(del+" 해당 ID는 존재하지 않습니다.");
                  break;
               }
               
            }
         }
         default:

         }

      }
   }

}

```



```java title=gogu
package array;

import java.util.Scanner;

public class Quiz05 {

   public static void main(String[] args) {
      Scanner input = new Scanner(System.in);

      String[] id = new String[5];
      String[] pwd = new String[5];
      int num;
      String inputId = null, inputPwd = null;
      while (true) {
         System.out.println("1.로그인");
         System.out.println("2.회원가입");
         System.out.println("3.회원 정보");
         System.out.println("4.비번 바꿈");
         System.out.println("5.계정 삭제");
         System.out.print(">>> : ");
         num = input.nextInt();
         switch (num) {
         case 1:
            System.out.print("아이디 입력 : ");
            inputId = input.next();
            System.out.print("비밀번호 입력 : ");
            inputPwd = input.next();
            for (int i = 0;; i++) {
               if (inputId.equals(id[i]) && inputPwd.equals(pwd[i])) {
                  System.out.println("로그인 성공");
               } else {
                  System.out.println("인증 실패");
               }
               break;
            }
            break;

         case 2:
            System.out.print("아이디 입력 : ");
            inputId = input.next();
            System.out.print("비밀번호 입력 : ");
            inputPwd = input.next();
            int k = 0;
            for (k = 0; k < id.length; k++) { // k 가 0이고 ;k 가 id 배열의 개수보다 작고; k 는 더해진다
               if (id[k] == null) { // 만약 id 배열의 값이 초기화 되었을때
                  id[k] = inputId; // id 배열에 저장할 아이디를 적는다
                  pwd[k] = inputPwd; // pw 배열에 저장할 아이디를 적는다
                  System.out.println("가입 성공");
                  break;
               }
               if (id[k].equals(inputId)) { // 배열안에 같은 문장이 있을때
                  System.out.println("존재하는 id"); // 존재하는 id 라고 말해라
                  break; // 응 돌아가~
               }
            }
            if (k == id.length) { // k = id 배열 id 배열의 길이와 같을때 *0~5 != 1~5 는 다르죠?
               System.out.println("공간이 없다!!!"); // 공간이 없다고 말해라
            }
            break; // 응 돌아가~
         case 3:
            for (int h = 0; h < id.length; h++) { // i 가 0이고 ;i 가 id 배열의 개수보다 작고; i 는 더해진다
               System.out.println(id[h] + ":" + pwd[h]); // 를 조건이 만족할 때까지 반복한다.
            }break;
         case 4:
            for (int i = 0;; i++) {
               System.out.print("아이디 입력 : ");
               inputId = input.next();
               if (inputId.equals(id[i])) {
                  System.out.print("새로운 비밀번호 입력 : ");
                  pwd[i] = input.next();
               } else {
                  System.out.println("존재하지 않는 id");
               }
               break;
            }break;
         case 5:
            System.out.print("아이디 입력 : ");
            inputId = input.next();
            System.out.print("비밀번호 입력 : ");
            inputPwd = input.next();
            for (int i = 0;; i++) {
               if (inputId.equals(id[i]) && inputPwd.equals(pwd[i])) {
                  System.out.println(" 계정을 삭제하시겠습니까?\n1.예\t2.아니오");
                     num = input.nextInt();
                     id[i] = null;
                     pwd[i] = null;
                     System.out.println("계정이 삭제되었습니다.");
               }else {
               System.out.println("존재하지 않는 id");
               } break;      
            }
         }
      }
   }
}

```



```java title=Quiz04_1
package array_;

import java.util.Scanner;

public class Quiz04_1 {

	public static void main(String[] args) {
		
		Scanner input = new Scanner(System.in);
		
		String[] id = new String[5];
		String[] pwd = new String[5];
		int userId = 0;
		
		String printMessage = "1. 로그인\n" + "2. 회원가입\n" + "3. 사용자목록\n" + "4. 수정\n" + "5. 삭제\n" + "6. 종료\n" + ">>> "; 
		
		boolean process = true;
		while(process) {
			System.out.print(printMessage);
			int select = input.nextInt();
			
			if(select == 1) {
				System.out.print("로그인 ID : ");
				String inputLoginId = input.next();
				System.out.print("로그인 PW : ");
				String inputLoginPwd = input.next();
				
				boolean found = false;
				for(int i = 0 ; i < id.length ; i++) {
					if(inputLoginId.equals(id[i])) {
						found = true;
						
						if(inputLoginPwd.equals(pwd[i])) {
							System.out.println("인증통과");
						}else {
							System.out.println("패스워드 틀렸습니다.");
						}
						break;
					}
				}
				
				if(!found) {
					System.out.println("존재하지 않는 아이디");
				}
				
				
			}else if(select == 2) {
				if(userId == id.length) {
					System.out.println("저장할 공간 부족");
					continue;
				}
				
				System.out.print("ID: ");
				String inputJoinId = input.next();
				System.out.print("PW: ");
				String inputJoinPwd = input.next();
				
				for(int i = 0 ; i < id.length ; i++) {
					boolean isDupli = inputJoinId.equals(id[i]);
					if(isDupli) {
						System.out.println("동일한 ID가 존재");
						break;
					}
					
					if(id[i] == null) {
						id[i] = inputJoinId;
						pwd[i] = inputJoinPwd;
						userId++;
						
						if(id[i] != null && pwd[i] != null) {
							System.out.println("가입 완료");
						}
						break;
					}
					
				}
				
			}else if(select == 3) {
				if (userId == 0) {
					System.out.println("회원 정보가 존재하지 않음!!");
					continue;
				}
				
				for(int i = 0 ; i < id.length; i++) {
					String userInfoMessage = id[i] != null ? (i + 1) + ". id: " + id[i] + " " + "pw: " + pwd[i] : (i + 1) + ". 공석";
					System.out.println(userInfoMessage);
				}
			}else if(select == 4) {
				System.out.print("수정 ID : ");
				String inputModiId = input.next();
				
				boolean isExistId = false;
				for(int i = 0 ; i < id.length ; i++) {
					isExistId = true;
					if(inputModiId.equals(id[i])) {
						String prevPwd = pwd[i];
						
						System.out.print("수정 PW : ");
						String inputModiPwd = input.next();
						
						if(pwd[i] != prevPwd) {
							pwd[i] = inputModiPwd;
							System.out.println("비밀번호 변경 성공");
						}else {
							System.out.println("비밀번호가 전과 동일");
						}
						break;
					}
				}
				
				if(!isExistId) {
					System.out.println("해당 ID는 존재하지 않습니다.");
				}
				
				
			}else if(select == 5) {
				System.out.print("삭제할 ID : ");
				String inputDelId = input.next();
				
				boolean isExistId = false;
				for(int i = 0 ; i < id.length ; i++) {
					if(inputDelId.equals(id[i])) {
						isExistId = true;
						id[i] = null;
						
						System.out.println("삭제 성공");
						break;
					}
					
				}
				
				if(!isExistId) {
					System.out.println("해당 ID는 삭제할 수 않습니다.");
				}
			}else if(select == 6) {
				process = false;
			}else {
				System.out.println("유효하지 않은 입력");
				continue;
			}
			
			
		}
		
		
	}

}
```



***



# 2차원 배열

![[Pasted image 20240809090118.png|300]]


```java title=Ex01
package array_;

public class Ex01 {

	public static void main(String[] args) {
		int [][] arr = { 
				{ 10, 20, 30 },
				{ 40, 50, 60 }, 
				{ 70, 80, 90 }, 
				{ 100, 110, 120 }
		};
		
		System.out.println(arr.length);		
		System.out.println(arr[2].length);
		
		System.out.println("---------------------------");
		
		for(int i = 0 ; i < arr.length ; i++) {
			for(int j = 0 ; j < arr[i].length ; j++) {
				System.out.println(arr[i][j] + " ");
			}
			System.out.println();
		}
		
		
		
	}

}
```



```java title=Ex02
package array_;

public class Ex02 {

	public static void main(String[] args) {
		int [][][] arr = { 
				{ 
					{1, 2, 3}, {4, 5, 6} 
				}, 
				{ 
					{7, 8, 9}, {10, 11, 12} 
				} 
		};
		
		
	}

}
```




