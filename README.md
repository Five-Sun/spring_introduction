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

참고: spring-boot-devtools 라이브러리를 추가하면, html 파일을 컴파일만 해주면 서버 재시작 없이 View 파일 변경이 가능하다

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
@ResponseBody를 사용하면 뷰 리졸버( viewResolver )를 사용하지 않음

---
* 일반적인 웹 애플리케이션 계층 구조

![image](https://github.com/user-attachments/assets/4f9b3509-48f4-459d-a68e-7a46ff771982)

---
개발한 기능을 실행해서 테스트 할 때 자바의 main 메서드를 통해서 실행하거나, 웹 애플리케이션의 컨트롤러를 통해서 해당 기능을 실행한다. 하지만 이러한 방법은 준비하고 실행하는데 오래 걸린다.
자바는 JUnit이라는 프레임워크로 테스트를 수행하곤 한다.
**테스트는 각각 독립적으로 실행되어야 하고 테스트 순서에 의존관계가 있는 것은 좋은 테스트가 아니다.**

---

스프링이 연관된 객체를 스프링 컨테이너에서 찾아서 넣어주는데 이렇게 객체 의존관계를 외부에서 넣어주는 것을 **DI(의존성 주입)** 이라고 한다.

스프링 빈을 등록하는 2가지 방법
1. 컴포넌트 스캔과 자동 의존관계 설정 -> @Component을 사용
2. 자바 코드로 직접 스프링 빈 등록하기 -> @Configuration을 사용

생성자에 `@Autowired`를 사용하면 객체 생성 시점에 스프링 컨테이너에서 해당 스프링 빈을 찾아서 주입한다. 생성자가 1개인 경우 생략할 수 있다.
DI에는 필드 주입, setter 주입, 생성자 주입 3가지 방식이 있다. 의존관계가 실행중에 동적으로 변하는 경우는 거의 없으므로 생성자 주입을 권장한다.
실무에서는 주로 정형화된 컨트롤러, 서비스, 리포지토리 같은 코드는 컴포넌트 스캔을 사용한다.

---
스프링 통합 테스트
@SpringBootTest : 스프링 컨테이너와 테스트를 함께 실행한다.
@Transactional : 테스트 케이스에 이 애노테이션이 있으면, 테스트 시작 전에 트랜잭션을 시작하고, 테스트 완료 후에 항상 롤백한다. 이렇게 하면 DB에 데이터가 남지 않으므로 다음 테스트에 영향을 주지 않는다.

---
**순수 Jdbc**
->
**스프링 JdbcTemplate:** 
스프링 JdbcTemplate과 MyBatis 같은 라이브러리는 JDBC API에서 본 반복 코드를 대부분 제거해준다. 하지만 SQL은 직접 작성해야 한다.
->
**JPA:**
JPA는 기존의 반복 코드는 물론이고, 기본적인 SQL도 JPA가 직접 만들어서 실행해준다.
JPA를 사용하면, SQL과 데이터 중심의 설계에서 객체 중심의 설계로 패러다임을 전환을 할 수 있다.
JPA를 사용하면 개발 생산성을 크게 높일 수 있다.
show-sql: JPA가 생성하는 SQL을 출력한다.
ddl-auto: JPA는 테이블을 자동으로 생성하는 기능을 제공하는데 none을 사용하면 해당 기능을 끈다
->
**스프링 데이터 JPA:**
스프링 부트와 JPA만 사용해도 개발 생산성이 정말 많이 증가하고, 개발해야할 코드도 확연히 줄어듭니다. 
여기에 스프링 데이터 JPA를 사용하면, 기존의 한계를 넘어 마치 마법처럼, 리포지토리에 구현 클래스 없이 인터페이스 만으로 개발을 완료할 수 있습니다. 
그리고 반복 개발해온 기본 CRUD 기능도 스프링 데이터 JPA가 모두 제공합니다.
스프링 데이터 JPA가 SpringDataJpaMemberRepository를 스프링 빈으로 자동 등록해준다.

![image](https://github.com/user-attachments/assets/09b1094e-2b2c-4587-ab8c-d4e0b1463a92)

---

**AOP**
 AOP가 필요한 상황: 공통 관심 사항! 추후에 강의를 통해 자세하게 학습할 예정
