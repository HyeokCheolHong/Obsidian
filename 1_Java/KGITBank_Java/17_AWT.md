
- Java에서 Drawing 하는 방법은 Swing과 AWT가 있다

>[!tip] Swing과 AWT 장/단점
>### AWT(Abstract Window Toolkit)
>**장점:**
>
>1. **플랫폼 독립성:** AWT는 Java의 표준 라이브러리로, Java와 함께 기본적으로 제공되며, 다양한 플랫폼에서 동일하게 동작하도록 설계되었습니다.
>2. **경량:** AWT는 상대적으로 간단한 컴포넌트를 제공하므로 메모리 사용량이 적고, 시스템 리소스를 적게 사용합니다.
>3. **Native Components 사용:** AWT는 기본적으로 운영체제의 네이티브 GUI 컴포넌트를 사용하므로, 각 운영체제의 룩앤필(Look and Feel)을 잘 따릅니다.
>   
>**단점:**
>
>1. **제한된 기능:** AWT는 기본적인 GUI 컴포넌트만 제공하며, 복잡한 UI를 구현하기에는 기능이 제한적입니다.
>2. **플랫폼 종속성 문제:** 운영체제의 네이티브 컴포넌트를 사용하기 때문에, 운영체제에 따라 UI의 동작이나 모양이 다를 수 있습니다.
>3. **확장성 부족:** 복잡한 커스텀 컴포넌트나 고급 UI를 구현하기 어렵습니다.
>   
>### Swing
>**장점:**
>
>1. **풍부한 컴포넌트:** Swing은 AWT에 비해 훨씬 더 많은 컴포넌트(테이블, 트리, 탭 등)를 제공하며, 더 복잡한 UI를 쉽게 구현할 수 있습니다.
>2. **플랫폼 독립적 룩앤필:** Swing은 Java로 구현된 컴포넌트를 사용하므로, 운영체제에 관계없이 동일한 UI를 유지할 수 있습니다. 또한, 룩앤필을 변경할 수 있어, 원하는 스타일을 적용할 수 있습니다.
>3. **더 나은 확장성:** 커스텀 컴포넌트 제작이 쉬우며, 다양한 UI 디자인을 적용할 수 있습니다.
>4. **MVC 패턴 지원:** Swing 컴포넌트는 MVC(Model-View-Controller) 패턴을 따르므로, 데이터와 UI의 분리가 용이하여 구조적인 프로그램을 작성할 수 있습니다.
>   
>**단점:**
>
>1. **성능 문제:** Swing은 운영체제의 네이티브 컴포넌트를 사용하지 않기 때문에, 복잡한 UI를 구현할 때 AWT에 비해 성능이 떨어질 수 있습니다.
>2. **상대적으로 높은 메모리 사용:** AWT에 비해 더 많은 메모리를 사용하며, 시스템 리소스를 더 많이 요구할 수 있습니다.
>3. **학습 곡선:** Swing은 AWT보다 더 복잡한 구조를 가지고 있어, 처음 배우는 개발자에게는 다소 어려울 수 있습니다.
>   
>### 결론
>- **AWT**는 단순하고 경량의 GUI 애플리케이션을 빠르게 만들 때 적합하며, 시스템 리소스의 사용이 적습니다.
>- **Swing**은 복잡한 UI를 구현할 때 더 나은 선택이며, 다양한 기능과 커스터마이징을 제공합니다. 그러나 성능과 메모리 사용에 있어서는 AWT에 비해 다소 무거울 수 있습니다.


---

```java title=AwtTEst01
package awt;

import java.awt.Frame;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;

// java.awt 패키지의 그림그리는 API인 AWT로 Frame Window를 만든 후 내부 무명클래스인 익명클래스 문법으로 만들어진 해당 AWT Frame Window를 종료하는 예제

class FrameEvent01 extends Frame{
	public FrameEvent01() {
		// 생성자 메소드 선언
		super("Frame Window"); 
		// 부모클래스 생성자를 호출하면서 Frame Window 제목을 설정한다.
		setSize(300, 200);
		// Frame Width, Height 지정
		setVisible(true);
		// 항상 보이게 한다.
		
		// add+WindowEventLister 인터페이스이름() 으로 된 내장 메서드로 프레임 윈도우 닫기 이벤트를 처리한다.
		addWindowListener(new WindowAdapter() {

			@Override
			public void windowClosing(WindowEvent e) {
				dispose();
				// 자원 해제하면서 현재 호출되고 활성화 된 창을 닫는다. 백단에 비활성화 된 창은 닫지 못한다.
				System.exit(0);
				// 현재 호출되고 활성화 된 창뿐만 아니라 비활성된 창까지 모두 종료한다.
			} // 현재 열려진 Frame Window 닫기 했을 때 호출
		}); // 익명클래스 문법으로 Window 닫기 이벤트 처리 =? 내부무명클래스(외부클래스명$번호.class => FrameEvent01$1.class)
	} // 생성자 정의
}

public class AwtTest01 {
	public static void main(String[] args) {
		new FrameEvent01();
		// 생성자 호출
	}
}

```

``` java title = AwtTest01_설명
addWindowListener(new WindowAdapter() {} 
				  
// addWindowListener : 사용자가 행하는 Window(화면) 행동을 받아들인다
// WindowAdapter() : WindowListener 인터페이스의 하위 메소드로 여러 메소드중 특정 메소드만 오버라이딩이 되도록 함
//   그로인해 public void windowClosing(WindowEvent e) {} 만 오버라이딩만 해도 Error가 미발생한다.

// WindowListener의 메소드 종류 :
	// windowOpened(WindowEvent e): 창이 열릴 때 호출
	// windowClosing(WindowEvent e): 창을 닫으려고 할 때 호출
	// windowClosed(WindowEvent e): 창이 닫힌 후 호출
	// windowIconified(WindowEvent e): 창이 최소화될 때 호출
	// windowDeiconified(WindowEvent e): 창이 최소화 해제될 때 호출
	// windowActivated(WindowEvent e): 창이 활성화될 때 호출
	// windowDeactivated(WindowEvent e): 창이 비활성화될 때 호출
	
dispose() : // Debugging후 활성화된 창 하나만 닫는다

System.exit(0) : // Debugging 후 활성화된 창 전체를 닫는다.

```
---
>[!Debugging 결과]
![[Pasted image 20240830161455.png]]

---

```java title=AwtTest02
package awt;

import java.awt.Button;
import java.awt.FlowLayout;
import java.awt.Frame;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;

// Flow Layout 배치관리자를 지정해서 FrameWindow에 각 Button 개체가 추가될 때 방향(위에서 아래, 왼쪽에서 오른쪽으로)이 자연스럽게 배치

class FrameEvent02 extends Frame{
	public FrameEvent02() {
		setLayout(new FlowLayout());
		// FlowLayout 배치관리자 지정
		
		add(new Button("Button 01"));
		// FrameWindow에 버튼추가
		// Frame 내부에 Button을 추가 (글자 : Button 01)
		add(new Button("Button 02"));
		add(new Button("Button 03"));
		add(new Button("Button 04"));
		add(new Button("Button 05"));
		
		setSize(300, 200);
		// Frame Width, Height를 지정
		setVisible(true);
		// 항상 보이게
		
		addWindowListener(new WindowAdapter() {
			// Window Event 등록
			@Override
			public void windowClosing(WindowEvent e) {
				// 현재 FrameWindow에서 닫기 했을 때 호출
				
				dispose();
				// 자원해제, 현재 호출되어서 활성화된 창 닫기
			}
		});
	}
}

public class AwtTest02 {
	public static void main(String[] args) {
		new FrameEvent02();
		// 기본생성자(default 생성자) 호출
	}
}

```

>[!Debugging 결과]
![[Pasted image 20240830164644.png]]

---

```java title=BorderLayout03
package awt;

import java.awt.BorderLayout;
import java.awt.Button;
import java.awt.Frame;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;

// BorderLayout 배치관리자

class FrameEx03 extends Frame {
	public FrameEx03() {
		setLayout(new BorderLayout());
		// BorderLayout 배치 관리자 설정 : 
		
		add(new Button("Button 01"), "North");
		// FrameWindow 북쪽에 첫번째 버튼을 추가
		add(new Button("Button 02"), "West");
		add(new Button("Button 03"), "Center");
		add(new Button("Button 04"), "East");
		add(new Button("Button 05"), "South");
		
		
		setSize(300, 200);
		setVisible(true);
		
		addWindowListener(new WindowAdapter() {
			@Override
			public void windowClosing(WindowEvent e) {
				dispose();
				System.exit(0);
			}
		});
	}
}

public class BorderLayout03 {
	public static void main(String[] args) {
		new FrameEx03();
		// 생성자 호출
	}
}

```

```java title=borderLayout03_설명
add(new Button("Button 01"), "North");
//"North" 문자열로 인수를 전달하는데 위치가 정해지는 이유 : 
// **"North"**는 BorderLayout이 제공하는 예약어로, 프레임의 상단(북쪽)에 해당 컴포넌트를 배치하도록 지정하는 역할을 합니다.
// add 메서드의 두 번째 인수로 "North"를 전달하면, BorderLayout은 이를 프레임의 북쪽에 해당 컴포넌트를 배치하라는 지시로 이해합니다.
```

>[!Debugging 결과]
![[Pasted image 20240830172109.png]]

---

```java title=GridLayout04
package awt;

import java.awt.Button;
import java.awt.Frame;
import java.awt.GridLayout;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;

class FrameEx04 extends Frame{
	public FrameEx04() {
		setLayout(new GridLayout(3, 2));
		// 3행 * 2열의 그리드 레이아웃 배치관리자 설정
		
		add(new Button("Button 01"));
		add(new Button("Button 02"));
		add(new Button("Button 03"));
		add(new Button("Button 04"));
		add(new Button("Button 05"));
		add(new Button("Button 06"));
		
		setSize(300, 200);
		setVisible(true);
		
		addWindowListener(new WindowAdapter() {
			@Override
			public void windowClosing(WindowEvent e) {
				dispose();
				System.exit(0);
			}
		});
	}
}

public class GridLayout04 {
	public static void main(String[] args) {
		new FrameEx04();
	}
}
```

>[!Debugging 결과]
![[Pasted image 20240830172222.png]]

---

```java title=Panel05
package awt;

import java.awt.BorderLayout;
import java.awt.Button;
import java.awt.Color;
import java.awt.Frame;
import java.awt.Panel;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;

// 패널(Panel)은 여러개의 컴포넌트를 그룹화 시켜서 FrameWindow에 효율적으로 배치하는 컨테이너(레이아웃)이다.
// 즉 패널단위로 배치하면 효율적으로 배치할 수 있다.

class FrameEx05 extends Frame{
	Panel pan01, pan02, pan03;
	
	public FrameEx05() {
		// 3개의 패널 객체 생성
		pan01 = new Panel();
		pan02 = new Panel();
		pan03 = new Panel();
		
		// 3개의 각 패널에 배경색 설정
		// Color.소문자 : 소문자로 된 필드 이름을 사용하는 표현
//		pan01.setBackground(Color.orange);
//		pan02.setBackground(Color.blue);
//		pan03.setBackground(Color.green);
		// Color.대문자 : 상수 필드에 대한 자바 코딩 컨벤션을 따르는 표기
		pan01.setBackground(Color.ORANGE);
		pan02.setBackground(Color.BLUE);
		pan03.setBackground(Color.GREEN);
		// 표준적으로 대문자 표기를 사용
		
		// 각 패널을 보더레이아웃으로 배치
		add(BorderLayout.NORTH,pan01);
		// 첫번째 패널을 FrameWindow 북쪽에 배치
		add(BorderLayout.CENTER,pan02);
		add(BorderLayout.SOUTH,pan03);
		
		// 첫번째 패널에 2개의 버튼 추가
		pan01.add(new Button("Button 01"));
		pan01.add(new Button("Button 02"));
		
		// 두번째 패널에 1개의 버튼 추가
		pan02.add(new Button("Button 03"));
		
		// 세번째 패널에 2개의 버튼 추가
		pan03.add(new Button("Button 04"));
		pan03.add(new Button("Button 05"));
		
		setSize(300, 130);
		setVisible(true);
		
		addWindowListener(new WindowAdapter() {
			@Override
			public void windowClosing(WindowEvent e) {
				dispose();
				System.exit(0);
			}
		});
	}
}

public class Panel05 {
	public static void main(String[] args) {
		new FrameEx05();
	}
}
```

>[!Debugging 결과]
>![[Pasted image 20240830173622.png]]