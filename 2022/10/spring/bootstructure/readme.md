# spring boot 시작하기

# spring boot의 동작 구조

![sprintboot1.png](/2022/10/spring/bootstructure/boot/sprintboot1.png)

Spring boot 프로젝트는 mvc 구조 기반으로 동작한다. Servlet은 client의 요청을 처리하고 결과를 반환한다. Servlet을 관리하는 servlet container는 servlet 인스턴스를 생성하고 관리하는 역할을 한다. Tomcat은 WAS의 역할과 servlet container의 역할을 수행하는 컨테이너다. Servlet container는 아래와 같은 특징을 갖는다.

-   servlet 객체를 생성, 초기화, 호출, 종료하는 생명 주기를 관리
-   servlet 객체는 싱글톤 패턴으로 관리
-   멀티 스레딩 지원

Spring에서는 DispatcherServlet이 servlet의 역할을 수행한다. DispatcherServlet의 동작은 아래와 같다

1. DispatcherServlet으로 요청이 들어오면 handler mapping을 통해 controller에서 매핑된 경로를 탐색한다
2. Handler adapter로 controller를 호출한다
3. Handler adapter에 controller의 응답이 오면 ModelAndView로 응답을 반환한다
4. View 형식으로 반환하는 controller를 사용할 때 view resolver를 통해 view를 받아 반환한다

# Layerd Architecture

레이어드 아키텍처는 어플리케이션의 컴포넌트를 유사 관심사 기준으로 레이어로 묶어 수평적으로 구성한 구조이다. 일반적인 레이어드 아키텍처는 3계층이나 4계층 구성을 의미한다. 데이터베이스 레이어이 추가 유무이다.

## spring에서의 layerd architecture

### presentation layer

-   상황에 따라 UI 계층이라고 한다
-   client와 접점이 된다
-   client로 데이터와 함께 요청을 받고 처리 결과를 응답으로 전달한다

### busizness layer

-   service 계층이라고 한다
-   핵심 비즈니스 로직을 구현하는 영역이다
-   트랜잭션 처리나 유효성 검사 등의 작업을 수행한다

### data access layer

-   persistance 계층이라고 한다
-   데이터베이스에 접근해야 하는 작업을 수행한다
-   Spring Data JPA에서는 DAO 역할을 repository가 수행하기 때문에 repository로 대체할 수 있다
