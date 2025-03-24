
>[!tip]

```java title=SwingGUI01
package Swing;

import java.awt.FlowLayout;

import javax.swing.JButton;
import javax.swing.JFrame;

// 스윙 프레임 윈도우안에 스윙버튼을 배치

class MyFrame01 extends JFrame {
	public MyFrame01() {
		setSize(300, 200);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		// 스윙 프레임윈도우 닫기
		
		setTitle("스윙 프레임 윈도우 열기");
		// 스윙 프레임 윈도우 제목 설정
		
		setLayout(new FlowLayout());
		// 배치관리자 설정
		
		JButton button = new JButton("스윙버튼");
		this.add(button);
		setVisible(true);
	}// 생성자 정의
}

public class SwingGui01 {
	public static void main(String[] args) {
		new MyFrame01();
	}
}
```

>[!example]
>![[Pasted image 20240904164728.png]]

>[!note]
>Swing 버튼 구현

---

```java title=SwingGui02
package Swing;

import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JPanel;
import javax.swing.JTextField;

// javax.swing패키지의 JTextField() 컴포넌트는 한줄 입력필드를 만든다.

public class SwingGui02 {
	public static void main(String[] args) {
		JFrame f = new JFrame();
		JPanel panel = new JPanel();
		f.add(panel);
		
		JLabel labelName = new JLabel("이름:");
		JLabel labelAddr = new JLabel("주소:");
		JTextField nameText = new JTextField(16);
		JTextField addrText = new JTextField(26);
		
		panel.add(labelName);
		panel.add(nameText);
		panel.add(labelAddr);
		panel.add(addrText);
		
		f.setSize(600, 100);
		f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		// Swing 닫기버튼 눌렀을때 행동
		f.setTitle("스윙 텍스트 입력필드");
		f.setVisible(true);
	}
}

```

>[!example]
>![[Pasted image 20240904164813.png]]

>[!note]
>Swing 라벨과 입력공간 구현

---

```java title=SwingGui03
package Swing;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JPanel;
import javax.swing.JTextField;

// Swing으로 피자 주문 화면 작성

class MyFrame03 extends JFrame{
	public MyFrame03() {
		setSize(600, 150);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		setTitle("Java Pizza Store");
		
		JPanel panel = new JPanel();
		JPanel panelA = new JPanel();
		JPanel panelB = new JPanel();
		
		JLabel label01 = new JLabel("자바 피자에 오신 것을 환영합니다! 피자의 종류를 선택하시오.");
		panelA.add(label01);
		
		JButton button01 = new JButton("콤보피자");
		JButton button02 = new JButton("포테이토자");
		JButton button03 = new JButton("하와이안피자");
		
		panelB.add(button01);
		panelB.add(button02);
		panelB.add(button03);
		
		JLabel label02 = new JLabel("개수");
		JTextField field01 = new JTextField(10);
		panelB.add(label02);
		panelB.add(field01);
		
		panel.add(panelA);
		panel.add(panelB);
		
		add(panel);
		// panel을 window에 추가한다.
		setVisible(true);
	} // 생성자 정의
}

public class SwingGUI03 {
	public static void main(String[] args) {
		new MyFrame03();
		// 생성자 호출
	}
}
```

>[!example]
>![[Pasted image 20240904164849.png]]

>[!note]
>Swing 다중 버튼과 라벨 및 입력공간 구현

---

```java title=SwingGui04
package Swing;

import java.awt.GridLayout;

import javax.swing.JButton;
import javax.swing.JFrame;

// 그리드 레이아웃 배치관리자를 설정하는데 행의개수는 정하지 않고 열의개수만 지정한다.

class MyFrame04 extends JFrame{
	public MyFrame04() {
		setTitle("그리드 레이아웃 연습"); // 스윙 프레임 윈도우 제목 설정
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE); // 스윙 프레임 윈도우 닫기
		
		setLayout(new GridLayout(0, 3)); // 3개의 열을 가지고 있으며, 필요한 만큼의 행의 개수를 가지는 그리드 레이아웃 배치관리자 설정
		
		add(new JButton("Button01"));
		add(new JButton("Button02"));
		add(new JButton("Button03"));
		add(new JButton("Button04"));
		add(new JButton("Button05"));
		
		pack(); // 프레임 윈도우에 소속된 컴포넌트들의 크기에 맞게 조절
		setVisible(true);
	}
}

public class SwingGUI04 {
	public static void main(String[] args) {
		new MyFrame04(); // 생성자 호출
	}
}

```

>[!example]
>![[Pasted image 20240904164933.png]]

>[!note]
>Swing 그리드 레이아웃 구현

---

```java title=SwingGui05
package Swing;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JPanel;

// 배치관리자 설정없이 임의의 위치를 지정해서 컴포넌트를 배치하는 절대위치로 배치하기

class MyFrame05 extends JFrame{
	JButton btn01;
	private JButton btn02, btn03;
	
	public MyFrame05() {
		setTitle("절대 배치 연습");
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		setSize(400, 200);
		
		JPanel p = new JPanel();
		p.setLayout(null); // 인자값을 null할당하여 레이아웃 설정 안함
		
		btn01 = new JButton("Button #01");
		p.add(btn01); // 패널에 첫번째 버튼 추가
		btn02 = new JButton("Button #02");
		p.add(btn02);
		btn03 = new JButton("Button #03");
		p.add(btn03);
		
		btn01.setBounds(20, 5, 95, 30); // 첫번째 버튼 X좌표 위치가 20, y좌표가 5, 버튼 너비가 95, 높이가 30
		// 첫번째 버튼에 임의의 위치를 지정해서 절대 배치
		btn02.setBounds(55, 45, 105, 70);
		btn03.setBounds(180, 15, 105, 90);
		
		add(p);
		setVisible(true);
		
	} // 생성자 정의
}

public class SwingGUI05 {
	public static void main(String[] args) {
		new MyFrame05(); // 생성자 호출
	}
}

```

>[!example]
>![[Pasted image 20240904165012.png]]

>[!note]
>Swing Layout 미적용시 배치에 관한 예제

---

```java title=SwingGui06
package Swing;

import java.awt.FlowLayout;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JPanel;

// 10개의 스윙 버튼을 for반복문으로 배치하는 실습 예제

class MyFrame06 extends JFrame{
	JPanel jp;
	
	public MyFrame06() {
		setSize(450, 200);
		setTitle("반복문으로 버튼배치");
		jp=new JPanel();
		jp.setLayout(new FlowLayout());// 패널에 플로우 레이아웃 배치관리자 설정
		
		for(int i = 1; i<= 10; i++) {
			jp.add(new JButton("Button"+i));
		}
		add(jp);//스윙 프레임 윈도우에 패널추가
		setVisible(true);
	}// 생성자 정의
	
}

public class SwingGUI06 {
	public static void main(String[] args) {
		new MyFrame06();
	}
}
```

>[!example]
>![[Pasted image 20240904165046.png]]

>[!note]
>Swing 반복문을 통한 버튼 배치

---

```java title=SwingGui07
package Swing;

import java.awt.GridLayout;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JPanel;

// SwingGUI06.java소스를 참조해서 그리드 레이아웃을 사용해서 행의 크기는 지정하지 않고 열의 크기만 3으로 지정해서
// 추가된 10개의 버튼개수만큼 만들어 지게 하는 스윙윈도우를 만들어 보자. 격자 간격을 3으로 지정(그리드 레이아웃 객체 생성할 때 지정하면 된다.)

class MyFrame07 extends JFrame{
	JPanel jp;
	
	public MyFrame07() {
		setSize(450, 200);
		setTitle("??");
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		jp = new JPanel();
		jp.setLayout(new GridLayout(0, 3, 3, 3));
		
		for(int i = 1; i <= 10; i++) {
			jp.add(new JButton("Button"+i));
		}
		add(jp);
		setVisible(true);
		
	}
}

public class SwingGUI07 {
	public static void main(String[] args) {
		new MyFrame07();
	}
}

```

>[!example]
>![[Pasted image 20240904165123.png]]

>[!note]
>Swing 그리드 레이아웃과 

```java title=SwingGui08
package Swing;

import java.awt.BorderLayout;
import java.awt.Color;
import java.awt.GridBagLayout;
import java.awt.GridLayout;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JPanel;
import javax.swing.JTextField;

// 자바 스윙으로 계산기 만들기

class Calculator08 extends JFrame{
	
	private JPanel panel;
	private JTextField tField;
	private JButton[] buttons;
	private String[] labels = {
			"Backspace","","","CE","C",
			"7","8","9","/","sqrt",
			"4","5","6","x","%",
			"1","2","3","-","1/x",
			"0","+/-",".","+","="
	};
	
	public Calculator08() {
		super("스윙으로 만든 계산기");
		// 제목설정
		tField = new JTextField(35);
		panel = new JPanel();
		tField.setText("0."); // 텍스트 필드의 기본문자열 지정
		tField.setEnabled(false); // 비활성화 편집불가
		
		panel.setLayout(new GridLayout(0, 5, 3, 3));
		buttons = new JButton[25];
		int index = 0;
		
		for(int rows=0; rows<5; rows++) {
			for(int cols=0; cols<5; cols++) {
				buttons[index] = new JButton(labels[index]);
				// 버튼위에 출력되는 캡션 문자열 지정
				if(cols>=3) {
					buttons[index].setForeground(Color.RED);// 4번째와 5번째 버튼위 캡션문자열 전경색을 빨강
				} else {
					buttons[index].setForeground(Color.BLUE); // 첫번째부터 세번째까지 버튼위 캡션문자열 전경색을 블루
				}
				buttons[index].setBackground(Color.YELLOW); // 25개 버튼 배경색을 노랑으로 설정
				panel.add(buttons[index]); // panel에 25개 버튼추가
				index++;
				
			}
		}
		this.add(tField, BorderLayout.NORTH); // 프레임 북쪽에 텍스트 필드 추가
		add(panel, BorderLayout.CENTER); // 프레임 중앙에 25개 버튼이 추가된 패널 추가
		setVisible(true);
		pack();
		
	}// 생성자 정의
}

public class SwingGUI08 {
	public static void main(String[] args) {
		new Calculator08();
	}
}

```

>[!example]
>![[Pasted image 20240904165156.png]]

---

```java title=SwingGui09
package Swing;

import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JPanel;

// 내부클래스 문법으로 이벤트 처리 => 내부클래스명은 외부클래스명$내부클래스명.class

class MyFrame09 extends JFrame{
	private JButton button;
	private JLabel label;
	
	public MyFrame09() {
		this.setSize(300, 200);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		setTitle("내부클래스로 이벤트처리");
		JPanel panel = new JPanel();
		button = new JButton("버튼을 누르시오.");
		label = new JLabel("아직 버튼이 클릭되지 않았다.");
		button.addActionListener(new MyListener08());
		// button이 동작했을때 MyListener08() 클래스를 동작하는 이벤트를 등록한다.
		panel.add(button);
		panel.add(label);
		add(panel);
		setVisible(true);
		
	}
	
	// 내부클래스를 정의해서 버튼 이벤트를 처리
	private class MyListener08 implements ActionListener{

		@Override
		public void actionPerformed(ActionEvent e) {
			if(e.getSource() == button) {
				// event Source 객체를 Button과 비교한다.
				label.setText("마침내 버튼이 클릭되었습니다");
			}
		}
	} // MyFrame09$MyListener08.class
}

public class SwingGUI09 {
	public static void main(String[] args) {
		new MyFrame09();
	}
}

```

>[!example]
>![[Pasted image 20240904165227.png]] ![[Pasted image 20240904165329.png]]

---

```java title=SwingGui10
package Swing;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JPanel;

// java version8에서 추가된 수학 함수형 언어인 람다식을 사용한 버튼 이벤트 처리

class MyFrame10 extends JFrame{
	private JButton button;
	private JLabel label;
	
	public MyFrame10() {
		setSize(300, 200);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		setTitle("람다식 이벤트");
		
		JPanel panel = new JPanel();
		button = new JButton("버튼을 클릭하세요!");
		
		label = new JLabel("아직 버튼이 클릭되지 않았다");
		button.addActionListener(e -> {
			label.setText("드디어 버튼이 클릭되었다.");
		});
		
		panel.add(button);
		panel.add(label);
		add(panel);
		setVisible(true);
		
	}
}

public class SwingGUI10 {
	public static void main(String[] args) {
		new MyFrame10();
	}
}

```

>[!example]
>![[Pasted image 20240904165311.png]] ![[Pasted image 20240904165324.png]]

>[!note]
>람다식 이벤트로 버튼 동작 이벤트 구현

---

```java title=SwingGui11
package Swing;

import java.awt.BorderLayout;
import java.awt.Button;
import java.awt.Dimension;
import java.awt.GridLayout;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JPanel;
import javax.swing.JTextField;

// 키패드 버튼 만들기

public class SwingGUI11 extends JFrame implements ActionListener{
	private JTextField txtInput;
	private JPanel panel;
	
	private JLabel label;
	private JButton button;
	private JButton[] buttons;
	private String[] labels = {
			"7", "8", "9,",
			"4", "5", "6", 
			"1", "2", "3"
	};
	
	public SwingGUI11() {
		setTitle("키패드 버튼 만들기");
		txtInput = new JTextField(20);
		add(txtInput, BorderLayout.NORTH);
		panel = new JPanel();
		panel.setLayout(new GridLayout(3, 3, 2, 2));
		// 격자 간격이 2인 3행*3열의 그리드레이아웃 배치관리자 설정
		add(panel, BorderLayout.CENTER);
		
		// 문제
		// 일반 for 반복문을 사용해서 버튼너비가 100, 높이가 100인 1부터 9까지 버튼위의 캡션문자열이 표시되는 9개의 숫자 키패드 버튼 Swing UI를 만들자
		// panel컨테이너에 9개 버튼 키패드가 추가되어야 한다.
		buttons = new JButton[9];
		
		for(int i=1; i<=9; i++) {
			JButton btn = new JButton(""+i);
			btn.addActionListener(this);//버튼이벤트등록
			btn.setPreferredSize(new Dimension(100, 100)); // 버튼 너비100, 높이 100
			panel.add(btn);
		}	
//		for(int i=0; i<9; i++) {
//			buttons[i] = new JButton("Button "+labels[i]);
//			button = buttons[i];
//			// 버튼위에 출력되는 캡션 문자열 지정
//			button.addActionListener(this);//버튼이벤트등록
//			button.setPreferredSize(new Dimension(100, 100)); // 버튼 너비100, 높이 100
//			panel.add(button);
//		}
		
		pack();
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		setVisible(true);
	}
	
	@Override
	public void actionPerformed(ActionEvent e) {
		// 문제
		// 9개의 키패드 버튼을 클릭하면 버튼위의 캡션문자열 숫자가 텍스트 필드에 기존값을 유지한채 누적해서 표시되게 만들어 보자
		
		String captionTitle = e.getActionCommand();
		txtInput.setText(txtInput.getText() + captionTitle);
		
//		txtInput.setText(txtInput.getText() + e.getActionCommand()); 
		
	}
	
	public static void main(String[] args) {
		new SwingGUI11();
	}
}

```

>[!example]
>![[Pasted image 20240904170525.png]]

>[!note]
>캡션문자열 숫자가 텍스트 필드에 기존값을 유지한채 누적해서 표시

---

```java title=SwingGui12
package Swing;

import java.awt.Graphics;
import java.awt.event.KeyAdapter;
import java.awt.event.KeyEvent;
import java.awt.image.BufferedImage;
import java.io.File;
import java.io.IOException;

import javax.imageio.ImageIO;
import javax.swing.JFrame;
import javax.swing.JPanel;

// 방향키를 누르면 자동차 이미지가 상,하,좌,우로 이동하는 예제 소스.
// 방향키를 눌렀을때(key down) 이벤트를 처리한다.

class MyPanel12 extends JPanel{
	BufferedImage img = null;
	int img_x = 100, img_y = 100; // 이미지 x, y좌표 위치
	
	public MyPanel12() {
		try {
			img = ImageIO.read(new File("./src/image/car_image_converted_down.jpg"));
			// 이클립스에서 인식하는 기본 경로는 프로젝트 경로이다.
			// ./는 현재 경로를 뜻하고 그것이 바로 기본경로인 프로젝트 경로(Day0903)이다
		} catch(IOException ie) { // 예외처리
			System.out.println("자동차 이미지가 해당경로에 없다.");
			System.exit(1); // 문제가 있어서 비정상적인 종료
		}
		
		// 키보드 이벤트 등록
		addKeyListener(new KeyAdapter() {

			@Override
			public void keyPressed(KeyEvent e) {
				int keycode = e.getKeyCode();
						
				switch (keycode) {
				case KeyEvent.VK_UP: img_y -= 10; break;// 위 방향키일때 y좌표가 줄어듬
				case KeyEvent.VK_DOWN: img_y += 10; break;// 아래 방향키일때 y좌표가 늘어남
				case KeyEvent.VK_LEFT: img_x -= 10; break;
				case KeyEvent.VK_RIGHT: img_x += 10; break;
				}
				
				repaint(); // 다시 그리고자 repaint()메소드를 호출
			}
		});// 익명클래스 즉 내부 무명클래스(외부클래스$번호.class => MyPanel12$1.class)로 키보드 이벤트 처리
		
		this.requestFocus();// 패널에 키보드 포커스 요청
		setFocusable(true); // 스윙 패널은 기본값으로 키보드 포커스를 받을 수 없다.
		// 그래서 해당 코드는 스윙 패널이 포커스를 받을 수 있게 함.
	} // 생성자
	// 

	@Override
	protected void paintComponent(Graphics g) { // 무엇을 그리고자 호출되는 메소드
		super.paintComponent(g);
		g.drawImage(img, img_x, img_y, null); // x, y좌표에 자동차 이미지를 그린다
	}
}

public class SwingGUI12 extends JFrame{
	
	public SwingGUI12() {
		setSize(500,500);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE); // 스윙 프레임 윈도우 닫기
		add(new MyPanel12()); // 프레임윈도우에 패널 컨테이너(레이아웃) 추가
		setVisible(true);
	} // 생성자
	
	public static void main(String[] args) {
		new SwingGUI12();
	}
}

```

>[!example]
>![[Pasted image 20240904170816.png]]

>[!note]
>키보드 방향키에 따른 image 이동

---

```java title=MouseEvent01
package SwingGUI;

import java.awt.Graphics;
import java.awt.event.MouseAdapter;
import java.awt.event.MouseEvent;
import java.awt.image.BufferedImage;
import java.io.File;
import java.io.IOException;

import javax.imageio.ImageIO;
import javax.swing.JFrame;
import javax.swing.JPanel;

// 마우스를 아래로 눌렀을 때 발생하는 이벤트로 x, y좌표값을 구해서 자동차 이미지를 이동시키는 예제

class MyPanel01 extends JPanel{
	BufferedImage img = null;
	// 불러올 이미지는 초기값 null
	int img_x =0, img_y=0;
	// 이미지의 초기값 지정
	
	public MyPanel01() {
		try {
			img = ImageIO.read(new File("./src/image/car_image_converted_down.jpg"));
			// img에 ImageIO.read()읽어올 이미지를 할당
		}catch(IOException ie) {
			System.out.println("no image");
			System.exit(1);
			// 비정상일경우 exit(1) / 정상일경우 exit(0)
		}// 예외처리 : 이미지를 못불러온다면?
		
		addMouseListener(new MouseAdapter() {
			// 마우스 이벤트가 발생시
			@Override
			public void mousePressed(MouseEvent e) {
				// 마우스이벤트 중 왼쪽마우스 선택 이벤트 발생시
				img_x = e.getX();
				// img_x 값에 마우스가 클릭된 위치의 x값을 할당
				img_y = e.getY();
				repaint();
				// 이미지를 다시 그림
			}
			
		});
	} // 생성자

	@Override
	protected void paintComponent(Graphics g) {
		super.paintComponent(g);
		g.drawImage(img, img_x, img_y, null);
	}// g.drawImage(그리고자할 대상, 좌표x값, 좌표y값, 관찰자)

	
}

public class MouseEvent01 extends JFrame{
	public MouseEvent01() {
		add(new MyPanel01());
		setSize(1000, 1000);
		setVisible(true);
	}
	
	public static void main(String[] args) {
		new MouseEvent01();
	}
}
```

>[!example]
>![[Pasted image 20240904164330.png]]

---

```java title=CounterTest02
package SwingGUI;

import java.awt.Font;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JPanel;

// 카운터 증가 버튼을 클릭하면 증가된 카운터 숫자가 라벨에 표시되는 예제

class Counter02 extends JFrame implements ActionListener{
	private JLabel label, label01;
	private JButton button, button01;
	private int count = 0;
	
	public Counter02() {
		JPanel panel = new JPanel();
		label = new JLabel("Counter");
		panel.add(label);
		
		label01 = new JLabel(" "+count);
		// JLabel(" "+count) : " " 가 들어가는 이유는 숫자를 문자열에 넣는것이 불가능하기에 " "+숫자를 넣음으로써 숫자를 문자열로 인식하게함
		label01.setFont(new Font("Serif", Font.BOLD|Font.ITALIC, 100));
		// Font() 메소드는 (글꼴, 글꼴스타일(BOLD:굵게/ITALIC:기울기), 글자크기)로 지정한다.
		panel.add(label01);
		
		button = new JButton("카운터 증가");
		button01 = new JButton("카운터 감소");
		panel.add(button);
		panel.add(button01);
		System.out.println(button);
		button.addActionListener(this);
		button01.addActionListener(this);
		// button의 이벤트할 인자값으로 this(자기자신)을 지정
		
		add(panel);
		// new Counter02로 생성된 객체에 add함
		setSize(300, 200);
		setTitle("카운터 증가");
		setVisible(true);
		
	}

	@Override
	public void actionPerformed(ActionEvent e) {
//		System.out.println(e);
		// 이벤트가 발생한 소스내용 + @이벤트가 발생한 대상의 객체의 전체 소스내용을 담음)
//		System.out.println(button);
		// 객체의 전체 소스내용
//		System.out.println(e.getSource());
		// getSource() 이벤트가 발생한 대상 객체의 전체 소스내용을 담음
//		System.out.println(e.getActionCommand());
		// getActionCommand() 이벤트가 발생한 대상 객체의 Command(text)만 담음
		if(e.getSource() == button || e.getActionCommand() == "카운터 증가") {
			count++;
		}
		if(e.getSource() == button01 || e.getActionCommand() == "카운터 감소") {
			count--;
		}
		// 카운터 증가
		label01.setText(" "+count);
		// count(숫자)를 문자열로 기록 되게끔 " "를 추가해줌
	}
}

public class CounterTEst02 {
	public static void main(String[] args) {
		new Counter02();
	}
}

```

>[!example]
>![[Pasted image 20240904164423.png]]

---

```java title=ImageLabel03
package SwingGUI;

import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

import javax.swing.ImageIcon;
import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JPanel;

// 스윙컴포넌트에 이미지를 표시할려면 ImageIcon api를 사용하면 쉽게 이미지를 추가할 수 있다.

public class ImageLabel03 extends JFrame implements ActionListener {

	private JPanel panel;
	private JLabel label;
	private JButton button;
	
	public ImageLabel03() {
		setTitle("이미지 레이블");
		setSize(1000, 750);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		
		panel = new JPanel();
		label = new JLabel("이미지를 보려면 아래 버튼을 클릭하세요.");
		
		button = new JButton("이미지 레이블");
		ImageIcon icon = new ImageIcon("./src/image/Green_grapes.jpg");
		// ImageIcon API 사용
		button.setIcon(icon);
		// 버튼위 이미지(icon) 배치
		
		button.addActionListener(this);
		// button의 이벤트를 등록함(자기자신)
		
		panel.add(label);
		panel.add(button);
		add(panel);
		setVisible(true);
		pack();
	}// 생성자 정의
	
	@Override
	public void actionPerformed(ActionEvent e) {
		ImageIcon catImage = new ImageIcon("./src/image/cat.jpg");
		label.setIcon(catImage);
		// 라벨에 고양이 이미지 배치
		label.setText(null);
		pack();
		// 라벨위 문자는 초기화
		
	}

	public static void main(String[] args) {
		new ImageLabel03();
	}
}

```

>[!example]
>![[Pasted image 20240904164546.png]]

---

```java title=CheckBox04
package SwingGUI;

import java.awt.GridLayout;
import java.awt.event.ItemEvent;
import java.awt.event.ItemListener;

import javax.swing.ImageIcon;
import javax.swing.JCheckBox;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JPanel;

// 스윙 체크박스 컴포넌트에 관한 실습 예제

public class CheckBox04 extends JPanel implements ItemListener {
	
	// 멤버 변수 작성
	JCheckBox[] buttons = new JCheckBox[3];
	// buttons는 배열크기가 3인 객체
	String[] fruits = {"apple", "grape","orange"};
	JLabel[] pictureLabel = new JLabel[3];
	ImageIcon[] icon = new ImageIcon[3];
	String frutsMemory = null;
	
	public CheckBox04() {
		super(new GridLayout(0, 4));
		// 부모클래스로 오버로딩 된 생성자를 호출하면서 열의 개수가4, 정해지지 않은 행의개수를 가진 그리드 레이아웃 배치관리자 설정
		
		for(int i = 0 ; i < buttons.length; i++) {
			buttons[i] = new JCheckBox(fruits[i]);
			// buttons 체크박스 각 인덱스에 새로운 객체로 fruits 배열에 있는 값들을 할당함
			buttons[i].addItemListener(this);
			// 각 체크박스 항목 이벤트 등록
			
			pictureLabel[i] = new JLabel(fruits[i]);
			// pictureLabel 라벨 각 인덱스에 새로운 객체로 fruits배열+.jpg 를 할당함
			
			icon[i] = new ImageIcon("./src/image/"+fruits[i]+".jpg");
		}

		JPanel checkPanel = new JPanel(new GridLayout(0, 1));
		for(int i=0; i<3; i++)
			checkPanel.add(buttons[i]);
		// 그리드 방식으로 buttons(CheckBox)를 하나씩 세로정렬한다
		
		add(checkPanel);
		add(pictureLabel[0]);
		add(pictureLabel[1]);
		add(pictureLabel[2]);
	}
	
	@Override
	public void itemStateChanged(ItemEvent e) {
	// 이벤트가 발생시 해당 메소드 전체가 동작
		Object source = e.getItemSelectable();
		// 선택된 체크박스를 구함
		for(int i = 0; i < 3; i++) {
			if(source == buttons[i]) {
				if(e.getStateChange() == ItemEvent.DESELECTED) {
					// 체크박스가 선택 안된 경우
					pictureLabel[i].setIcon(null);
					pictureLabel[i].setText(fruits[i]);
					// 라벨위 과일 이미지 제거
					
				} else {
					// 체크박스가 선택 된 경우
					
					pictureLabel[i].setIcon(icon[i]);
					// 라벨위 과일 이미지 추가
					
					pictureLabel[i].setText(null);
				}
				
				// 민중이가한 fruits배열을 사용하지 않고 text 나타내기
				// 문제 발생! : 체크박스 2개이상 선택후 해제시 마지막 선택된 temp(문자)로 나머지가 출력됨
//				if(e.getStateChange() == ItemEvent.DESELECTED) {
//					// 체크박스가 선택 안된 경우
//					pictureLabel[i].setText(frutsMemory);
//					pictureLabel[i].setIcon(null);
//					// 라벨위 과일 이미지 제거
//					
//				} else {
//					// 체크박스가 선택 된 경우
//					pictureLabel[i].setIcon(icon[i]);
//					// 라벨위 과일 이미지 추가
//					frutsMemory = pictureLabel[i].getText();
//					pictureLabel[i].setText(null);
//				}
			}
		}
	}

	public static void main(String[] args) {
		// CheckBox04는 JFrame내부 JPaenl을 상속받았기에 JFrame객체를 생성 해야함
		JFrame frame = new JFrame();
		
		frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE); // 스윙 프레임 윈도우 닫기
		CheckBox04 panel = new CheckBox04();
		panel.setOpaque(true);
		// 스윙 패널을 불투명하게 설정
		
		frame.add(panel);
		// 프레임에 패널 추가
		frame.setSize(500, 200);
		// 프레임 사이즈 지정(가로, 높이)
		frame.setVisible(true);
		// frame이 항상 보이게 설정
	}
}

```

>[!example]
>![[Pasted image 20240904164650.png]]

