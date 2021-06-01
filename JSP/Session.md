
# Session 의 개념
HTTP 프로토콜의 대표적인 특징 중 하나는 <b>상태를 유지하지 않는 것</b>으로, 클라이언트가 한 번 요청을 하고 서버에서 응답을 하면 해당 클라이언트와 서버와의 연결은 유지되지 않는다는 특징이 있다.
<pre>
클라이언트 ----> 서버 (첫 요청)
서버 -----> 클라이언트 (응답)
클라이언트 ----> 서버 (두 번째 요청)
서버 ----> 클라이언트 (새 클라이언트로 인식)
</pre>

HTTP 의 특징으로 인해 로그인, 장바구니 등 상태가 유지되어야 하는 프로그램 작성에 에로사항이 있는데, 이를 보완하기 위한 방법이 <b>세션</b> 이다.

<br>

## Session
서블릿에서 클라이언트와 서버의 상태를 유지하기 위해 제공되는 API (Application Programming Interface).
<pre>
클라이언트 ----> 서버 (첫 요청)
서버 ----> 클라이언트 (응답 + 세션 아이디 -> 쿠키에 저장)
클라이언트 ----> 서버 (두 번째 요청 + 쿠키에 저장된 세션 아이디)
서버 ----> 클라이언트 ( 쿠키에 전송된 세션 아이디 확인, 같은 클라이언트 임을 판단)
</pre>

세션 기능을 이용하면 클라이언트의 요청에 따른 응답을 할 때 서버에서 중복되지 않는 세션 아이디를 부여하여 클라이언트의 쿠키 저장소에 저장되게 하고, 클라이언트가 재 요청시 이 세션 아이디가 요청에 같이 전송된다. 서버는 해당 세션 아이디로 클라이언트가 첫 번째 요청을 한 클라이언트 인지 판별한다.

<br>

### 예제

- HttpServletRequest.getSession(true) :
해당 클라이언트에 이전 요청에 의한 세션이 생성되어 있으면 기존에 생성된 세션 객체의 레퍼런스를 반환하고, 생성되어 있지 않을 시엔 새롭게 세션 객체를 생성한다.
기본 파라미터 값은 true이다.

- HttpServletRequest.getSession(false) :
기존 클라이언트에 세션 객체가 생상되어 있으면 해당 세션의 레퍼런스를 반환하고, 생성되어 있지 않을 시엔 에러를 발생시킨다.

```java
protected void doGet(HttpServletRequest request,
HttpServletResponse response) throws ServletException, IOException {
	HttpSession session = request.getSession();
	session.setAttribute("name", "Sam"); //이름값 저장
	response.setContentType("text/html;charset = UTF-8");
	PrintWriter out = response.getWriter();
	out.println("<h1>이름저장</h1>");
}
```
<br>

```java
protected void doGet(HttpServletRequest request,
HttpServletResponse response) throws ServletException, IOException {
	HttpSession session = request.getSession();
	String name = (String)session.getAttribute("name"); //세션의 name 속성값 반환
	response.setContentType("text/html;charset = UTF-8");
	PrintWriter out = response.getWriter();
	out.println("<h1>name = "+ name +"</h1>
}
```
세션 영역에 저장되어 있는 name 속성 값을 가져와서 출력하는 서블릿

>이름저장 <br>
>name = Sam

<br>

### 실행 프로세스

 1. (클라이언트) 요청
 2. (컨테이너) `getSession(true)` 세션 영역 생성
 3. (컨테이너) `setAttribute("name", "Sam")`
 4. (컨테이너) 응답 + 세션아이디 전송
 5. (클라이언트) 쿠키에 세션아이디 저장
 6. (클라이언트) 요청 + 세션아이디 전송
 7. (컨테이너) `getSession(true)` 세션 아이디로 판별, 세션 레퍼런스 반환 - 세션 영역에 세션아이디, ("name", "Sam") 저장
 8. `getAttribute("name")`
 9. Sam 반환

<br>

### 서블릿에서 특정 페이지로 포워딩
 ***Dispatcher*** : 주소 표시줄의 주소가 변경되지 않는 포워딩 방식. 즉, 하나의 요청이며 같은 request 영역을 공유한다.

```java
DispatcherServlet.java

protected void doGet(HttpServletRequest request,
HttpServletResponse response) throws ServletException, IOException {
	RequestDispatcher dispatcher =
		request.getRequestDispatcher("dispatcher.jsp");
	request.setAttribute("request", "requestValue");
	dispatcher.forward(request, response);
}
```

<br>

```java
dispatcher.jsp

<body>
	request 속성 값 : <%=request.getAttribute("request") %>
</body>
```
request 영역에 request 라는 이름의 값을 가져와서 출력
**주소 표시줄 URL에 변경이 없으며**, **서블릿과 jsp 가 같은 request 영역을 공유**하므로 포워딩된 jsp 페이지에서 영역에 공유되어 있는 값에 접근이 가능하다.

<br>

### 서블릿에서 특정 페이지로 포워딩

 ***Redirect*** : <b>포워딩될 때 브라우저의 주소 표시줄 URL 이 변경</b>되므로 요청이 바뀌게 된다. 따라서, 포워딩된 jsp 페이지에서는 request 영역에 공유한 속성 값에 접근할 수 없다.

```java
RedirectServlet.java

protected void doGet(HttpServletRequest request,
HttpServletResponse response) throws ServletException, IOException {
	request.setAttribute("request", "requestValue");
	response.sendRedirect("redirect.jsp");
}
```
`sendRedirect(String url)` 메소드가 리다이렉트 방식으로 해당 URL 로 포워딩

<br>

```java
redirect.jsp

<body>
	request 속성 값 : <%=request.getAttribute("request") %>
</body>
```

> request 속성 값 :null

주소 표시줄 상의 URL 이 변경되고, request 영역이 공유되지 않아 jsp 페이지에서 request 영역의 속성 값을 가져올 수 없다.
