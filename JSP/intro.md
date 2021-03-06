## 웹프로그래밍?
웹 상에서 사용자와 기업 또는 사용자들간의 연결을 가능하게 하는 <b>프로그래밍 언어<br></b>
많은 사용자들이 사용하는 사이트는 사용자들에 의해 데이터가 <b>동적</b>으로 변화하는 데, 이는 정적으로 데이터를 처리하고 웹 문서를 작성하는 **HTML** 대신 **CGI**, **ASP**, **PHP**, **JSP** 등의 프로그래밍 언어를 사용한다.

<br>

### 클라이언트 - 서버 구조

#### 클라이언트 -> request -> 서버
	사용자가 웹 서버에 결과 요청
#### 클라이언트 <- respose <- 서버
	요청을 받아들인 후 데이터 처리 결과를 사용자에게 전송

<br>

### Java Server Page
객체 지향적이며 자바를 기반으로 한 동적 웹 구현 기술인 서블릿의 낮은 접근성, 비효율적인 코드를 개선하기 위해<br>
ASP의 장점을 수용하여 만들어진 기술.&nbsp; JSP는 <b>스크립트</b> 기반으로 개발되어 서버 페이지를 쉽게 작성할 수 있으며 서블릿과 함께 구동되어<br>
서블릿의 기능을 그대로 사용할 수 있다.

> 스크립트 언어
> 
> 컴파일 없이 인터프리터에 의해 즉시 실행될 수 있는 언어, 즉 컴파일러에 의한 2진수 기계어로의 변환이 필요없다.

<br>

### JSP와 Servlet
JSP는 동적인 웹 페이지 생성을 위한 기술로, 이를 활용하면 사용자가 요청을 보낼 때마다 서버에서 바로 응답을 할 수 있다. JSP 문서는 HTML과 java가 혼합된 형식으로, 사용자가 JSP 페이지를 요청하면 웹 서버에서 HTML 코드가 아닌 부분을 분석한 뒤 JVM을 통해 자바 코드를 실행하고, 그 결과를 HTML 코드 형식으로 변환하여 만들어진 웹 페이지를 사용자 측으로 전송한다.

 1.  JSP의 특징
  - **이식성** : JSP는 자바와 마찬가지로 Java Virtual Machine을 이용한 언어 특성상 어떠한 운영체제에서도 사용할 수 있다. *(Write Once, Run Anywhere)*
  - **효율성** : 어떠한 요청이 서버에 들어오면 서버는 페이지에 대한 인스턴스를 단 한 번만 생성하고 이후 같은 요청 발생시 이미 생성된 인스턴스에 thread 단위로 요청을 전송하여 처리한다.
  - **MVC 패턴** : *Model, View, Control* 부분으로 구성되어 큰 규모의 프로젝트도 분업을 통해 훨씬 더 효율적인 개발이 가능하다.
  - **편리성** : 전체적인 틀은 HTML, 코드는 <% %> 안에 삽입하여 화면 내용을 구성하기 편리하다.

<br>
 
 2. Servlet의 특징
  - 웹 서버 상에서 실행되는 자바의 클래스 파일로, 자바의 모든 api를 사용할 수 있으며 객체지향성 등 자바의 장점을 갖고 있다.
  - 반드시 javax.servlet,Servket  인터페이스를 implements 해서 작성하여야 한다.
  - 입력과 출력을 HTTP 프로토콜의 요청(Request)과 응답(Response)의 형태로 다룬다.



<br>

### 웹 어플리케이션의 구조
웹 어플리케이션은 클라이언트의 컴퓨터에 별다른 설치를 필요로 하지 않는데, 이는 사용자와의 모든 데이터 처리를 브라우저를 통한 웹 어플리케이션 구조 때문이다.
모든 입력과 결과는 브라우저를 통해 받아들여지고 표시되며 <b>클라이언트 - 서버 구조</b>로 이루어져 웹 서버와 사용자의 요청을 실직적으로 처리하는 비즈니스 로직이 구현된 어플리케이션 구조로 이러한 웹 어플리케이션 구조를 <b>3-tier</b> 구조라고 한다.<br>

`사용자(요청) -> 웹서버(해당 요청 판단) -> 어플리케이션 서버(요청 처리) -> 웹서버(결과 수신) -> 브라우저(결과)`

사이트에 회원가입을 할 때, 사용자는 정보를 기입하고 가입 버튼을 클릭, 브라우저는 해당 데이터들을 회원 가입 요청이라는 표시와 함께 웹 서버로 전송한다. <br>
웹 서버는 요청이 회원 가입 요청임을 판단하고 가입처리를 할 수 있는 어플리케이션 서버로 데이터를 전송하고 어플리케이션 서버는<br>
받은 데이터를 데이터베이스 시스템과 연동하여 가입 처리를 한 뒤 처리완료 메세지를 웹 서버로 보낸다. 웹 서버는 해당 메세지를 사용자의 브라우저로 전송하고 사용자는 페이지에 표시된 회원가입 완료 메세지를 보며 가입이 되었다고 판단한다.
