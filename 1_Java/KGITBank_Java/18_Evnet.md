

>[!tip]
>d

```java title=EventTest01
package Event;

import java.awt.Button;
import java.awt.Frame;
import java.awt.FlowLayout;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;

// 버튼 이벤트 처리 예제 1

class FrameEx01 extends Frame{
	Button redBtn, blueBtn;
	public FrameEx01() {
		setLayout(new FlowLayout()); // 플로우 레이아웃 배치관리자 
		
		redBtn = new Button("Red Color");
		blueBtn = new Button("Blue Color");
		add(redBtn);
		add(blueBtn);// 프레임 윈도우에 버튼 추가
		
		ButtonListener handler = new ButtonListener(); // 이벤트 처리 객체 생성
		
		redBtn.addActionListener(handler);
		blueBtn.addActionListener(handler);// 각 버튼 이벤트 등록
		
		setSize(300, 200); // 프레임 윈도우 폭과 높이 지정
		setVisible(true); // 항상 보이게 하기
		
		addWindowListener(new WindowAdapter() {

			@Override
			public void windowClosing(WindowEvent e) {
				dispose(); // 자원해제, 현재 활성화된 창만 닫기
				System.exit(0); // 활성, 비활성화된 모든 창 닫기
			} // 프레임윈도우 닫기 이벤트 발생시 호출
		}); // 프레임 윈도우 이벤트 등록
	}// 생성자
}

class ButtonListener implements ActionListener {

	@Override
	public void actionPerformed(ActionEvent e) {
		System.out.println("각 버튼이 클릭한 이벤트 즉 사건이 발생했습니다.");
	}
	
}

public class EventTest01 {
	public static void main(String[] args) {
		new FrameEx01();
	}
}
```

>[!example]
>![[Pasted image 20240904163730.png]]

---

```java title=EventTest02
package Event;

import java.awt.Frame;
import java.awt.Button;
import java.awt.FlowLayout;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;
import java.awt.Color;

// 버튼 이벤트 2번째 처리소스 => 각 버튼 클릭시 Frame Window BackGroundColor 변경소스

class FrameEx02 extends Frame{
	Button redBtn, blueBtn;
	
	public FrameEx02() {
		setLayout(new FlowLayout());
		
		redBtn = new Button("Red Color");
		blueBtn = new Button("Blue Color");
		add(redBtn);
		add(blueBtn);
		
		ButtonListener2 handler = new ButtonListener2(this);
		// 생성자 인자값으로 this를 전달. 여기서 this는 내 자신 프레임윈도우창을 가리킨다.
		redBtn.addActionListener(handler);
		blueBtn.addActionListener(handler);
		
		setSize(300, 200);
		setVisible(true);
		
		addWindowListener(new WindowAdapter() {
			@Override
			public void windowClosing(WindowEvent e) {
				dispose();
				System.exit(0);
			}
		});
	} // 생성자
}

// 이벤트 처리 클래스를 따로 정의
class ButtonListener2 implements ActionListener {
	Frame frm = null;
	
	public ButtonListener2() {} // 기본생성자
	
	public ButtonListener2(Frame frm) {
		this.frm = frm;
	}
	
	@Override
	public void actionPerformed(ActionEvent e) {
		if(e.getActionCommand().equals("Red Color")) { 
		// getActionCommand()메소드는 버튼위의 캡션 문자열을 반환
			frm.setBackground(Color.RED);
			// 프레임 배경색을 빨강으로 변경
		} else {
			frm.setBackground(Color.BLUE);
		}
	}
	
}

public class EventTest02 {
	public static void main(String[] args) {
		new FrameEx02();
	}
}
```

>[!example]
>![[Pasted image 20240904163819.png]]

---

```java title=EventTest03
package Event;

import java.awt.Button;
import java.awt.Color;
import java.awt.FlowLayout;
import java.awt.Frame;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;

// Awt Frame 윈도우 API와 버튼 이벤트를 처리하는 이벤트 리스너 인터페이스를 상속과 동시에 구현해서 버튼 이벤트를 처리하는 예제

class FrameEx03 extends Frame implements ActionListener {

   Button redBtn, orangeBtn;
   
   public FrameEx03() {
      setLayout(new FlowLayout());
      
      redBtn = new Button("Red Color");
      orangeBtn = new Button("Orange Color");
      add(redBtn);
      add(orangeBtn);
      
      redBtn.addActionListener(this);
      orangeBtn.addActionListener(this);   // 각 버튼 이벤트 등록
      
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
   
   // 각 버튼 이벤트 발생시 호출
   @Override
   public void actionPerformed(ActionEvent e) {
      if(e.getSource() == redBtn) {
         this.setBackground(Color.RED);
      }else if(e.getSource() == orangeBtn) {
         this.setBackground(Color.ORANGE);
      }
   }
   
}

public class EventTest03 {
	public static void main(String[] args) {
	      new FrameEx03();
	}
}

```

>[!example]
>![[Pasted image 20240904164013.png]]

---

```java title=EventTest04
package Event;

import java.awt.Frame;
import java.awt.event.WindowEvent;
import java.awt.event.WindowListener;

// WindowListener 인터페이스에는 이벤트를 처리하는 추상메소드가 7개가 있다. 
// 여기서 현재 Frame Window Exit 했을때 호출되는 메소드 말고 불필요한 추상메소드까지 오버라이딩이 되는 예제

class FrameEx04 extends Frame implements WindowListener {

	public FrameEx04() {
		this.addWindowListener(this); // 내 자신 프레임 윈도우 이벤트 등록
		setSize(200, 200);
		setVisible(true);
	}
	
	@Override
	public void windowOpened(WindowEvent e) {
	}

	@Override
	public void windowClosing(WindowEvent e) {
		dispose();
		System.exit(0);
	}

	@Override
	public void windowClosed(WindowEvent e) {
	}

	@Override
	public void windowIconified(WindowEvent e) {
	}

	@Override
	public void windowDeiconified(WindowEvent e) {
	}

	@Override
	public void windowActivated(WindowEvent e) {
	}

	@Override
	public void windowDeactivated(WindowEvent e) {
	}
	
}


public class EventTest04 {
	public static void main(String[] args) {
		
	}
}

```

>[!example]
>출력이 따로 없음

