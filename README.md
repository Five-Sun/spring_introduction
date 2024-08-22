### 스프링 입문
---
스프링 입문 - 코드로 배우는 스프링 부트, 웹 MVC, DB 접근 기술
프로젝트 목표: 간단한 웹 애플리케이션 개발
1. 스프링 프로젝트 생성
2. 스프링 부트로 웹 서버 실행
3. 회원 도메인 개발
4. 웹 MVC 개발
5. DB 연동 - JDBC > JPA > 스프링 데이터 JPA
6. 테스트 케이스 작성
---
스프링 학습의 제대로 된 첫 길잡이 역할
**동작 환경**
![image](https://github.com/user-attachments/assets/78ea2e57-4495-4869-a74c-a037c334f3b3)

viewResolver가 화면을 찾아서 처리한다.

**참고: spring-boot-devtools 라이브러리를 추가하면, html 파일을 컴파일만 해주면 서버 재시작 없이 View 파일 변경이 가능하다**

---
빌드하고 실행하기(콘솔 이용)
1. ./gradlew build
2. cd build/libs
3. java -jar hello-spring-0.0.1-SNAPSHOT.jar
4. 실행 확인

---
웹 개발 방식
* 정적 컨텐츠
![image](https://github.com/user-attachments/assets/e1a561fa-01f0-4e57-9966-26561891bf3b)

* MVC와 템플릿 엔진
![image](https://github.com/user-attachments/assets/eccbfa38-3bf5-4ca3-8f53-2e5ce6361829)

* API 방식
![image](https://github.com/user-attachments/assets/36af28c0-63c6-4a28-88cc-71a24fac0384)
* @ResponseBody를 사용하면 뷰 리졸버( viewResolver )를 사용하지 않음
