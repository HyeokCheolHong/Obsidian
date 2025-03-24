
>[!tip]
>MariaDB는 오픈 소스의 관계형 데이터베이스 관리 시스텝(RDBMS)

>[!note]
>MySQL과 동일한 소스 코드를 기반으로 하며 GPS v2 라이선스를 따른다.


## Oracle

Oracle - 다운로드
![[Pasted image 20240905153343.png]]
![[Pasted image 20240905154025.png]]


>[!tip]
>알집 풀고 (OracleXE112_Win32) - DISK1 - setup.exe 실행
![[Pasted image 20240905160455.png]]

>[!tip]
>![[Pasted image 20240905160505.png]]

>[!tip]
>![[Pasted image 20240905160523.png]]
>[!note]
>check Status 항목 3개가 Succeeded 여야 한다.
>만약 false가 있다면 이미 설치된 파일이 있기에 제거를 선행해야한다.


>[!tip]
>![[Pasted image 20240905162515.png]]

>[!note]
>파일 경로(Destination Folder) 설정


>[!tip]
![[Pasted image 20240905162551.png]]

>[!note]
>Enter Password : 123456

>[!tip]
>![[Pasted image 20240905162621.png]]

>[!note]
>Oracle Database Listener : 1521
>Oracle services for Microsoft Transaction Server : 2030
>Oracle HTTP Listener : 8080


>[!tip]
>![[Pasted image 20240905162735.png]]

>[!note]
>설치 진행중...

>[!error]
>The installer is unable to instantiate the file.. 뜨면 Error 아니라고함.. 그냥 넘어가자
>![[Pasted image 20240905162859.png]]


>[!tip]
>설치 완료후 cmd 들어가서 (sqlplus system/123456) 입력
>![[Pasted image 20240905163240.png]]
>위와 같은 화면이 나오면 성공적으로 설치 완료


## DB생성


>[!tip]
>사용자 계정 만들때 주의사항
>18c 이전버전까지는 사용가능한 명령어
>CREATE USER aaaa(아이디) IDENTIFIED BY bbbb(비번)으로 설정
>
>18c 이후버전
>CREATE USER C##aaaa(아이디) IDENTIFIED BY bbbb(비번)설정

>[!note]
>alter session set "_ORACLE_SCRIPT"=true;
>위의 cmd(관리자계정)에서 붙여넣기 실행

>[!note]
>SQL> select tablespace_name, bytes, file_name FROM dba_data_files;
>저장된 곳을 확인했으면 그곳에 200M 정도의 oraclejava 테이블 스페이스를 만든다
>
>SQL> create tablespace fintech
>      datafile 'C:경로' size 200M; (C:\app\mun51\product\21c\oradata\XE\fintech.dbf' size 200M;)
>      
>      참고)
>      18c C:\\KGITBank\app\mun51\product\oradata\XE\fintech.dbf' size 200M;
>      11g C:\\KGITBank\Oracles\app\oracle\oradata\XE\fintech.dbf' size 200M;
>      10g C:\\KGITBank\Oracles\oradata\XE\fintech.dbf' size 200M;



>[!note]
>![[Pasted image 20240905171459.png]]
>![[Pasted image 20240905171515.png]]
>로 FINTECH.DBF 파일이 생성된다


>[!note] 계정생성
>SQL> create user fintech // 계정생성
>identified by 56789 // 패스워드 생성
>default tablespace fintech // 위에서 생성한 테이블스페이스 명
>quota UNLIMITED ON fintech; // 테이블 스페이스의 제한량 무한대
>![[Pasted image 20240905172005.png]]
>
>성공하면
>![[Pasted image 20240905172025.png]]
>User created 라는 문구가 나온다.


>[!note] 권한 부여
>접속과 기타 기능을 사용할 수 있도록 GRANT 를 이용해 할당한다.
>권한은 root 개념으로 관리하는데 connect, resource 롤을 할당한다. 이것으로 왠만한 기능은 다된다.
>// 롤이란 여러개의 집합을 묶음 처리 한것. (connect : 오라클 연결 권한 / resource : 오라클 사용 권한)
>SQL> GRANT connect, resource TO fintech;
>![[Pasted image 20240905172318.png]]
>
>성공하면
>![[Pasted image 20240905172339.png]]
>Grant succeeded.문구가 나온다


>[!note] 관리자 권한 접속
>SQL> connect ID/PW 입력
>SQL> connect fintech/56789
>![[Pasted image 20240905172458.png]]
>

>[!note] 현재 사용자명 확인
>SQL> show user
>![[Pasted image 20240905172458.png]]

---

## SQL - 다운로드
![[Pasted image 20240905153920.png]]

![[Pasted image 20240905154009.png]]

>[!note] 설치
>sqldeveloper-19.2.1.247.2212-x64 - sqldeveloper - sqldeveloper.exe 실행
>![[Pasted image 20240905172646.png]]
>
>해당 창이 뜨는데 (강의교안 Oracle 18... 보면 11Page) 아니요 입력
>![[Pasted image 20240905172709.png]]
>
>정상적으로 설치가 완료된다
>![[Pasted image 20240905173021.png]]

>[!note]
>파일 - 새로만들기 - General - 접속 - 데이터베이스 접속
>![[Pasted image 20240905173058.png]]
>
>Name : fintech / 사용자 이름 : fintech / 비밀번호 : 56789 / 비밀번호 저장
>![[Pasted image 20240905173154.png]]


>[!note] 네트워크 연결이 안되는경우
>C:\KGITBank\Oracles\app\oracle\product\11.2.0\server\network\ADMIN 로 들어간 후 listener.ora를 메모장으로 열어서
>
>![[Pasted image 20240905173403.png]]
>Hong_Gram이 PC 사용자 계정이 아닌 유동IP일수도 있다.
>


>[!note]
하단에 text실행 후 상태 : 성공으로 나와야 한다
![[Pasted image 20240905173540.png]]
접속 실행


>[!note]
>좌측에 fintech로 생성되었다면 성공이다
>![[Pasted image 20240905173643.png]]



