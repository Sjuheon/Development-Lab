# Get
서버에 존재하는 페이지를 요청하거나 목차에서 해당 페이지에 대한 목록 출력을 요청할 때 페이지 번호 등과 같은 간단한 파라미터를 전송하는 경우 사용
 
 <h3>클라이언트 페이지 생성</h3>
 
```html
<h1>Log In</h1>
<form action = "login" method = "get">
<label id = "id"> ID :</label>
<input type = "text" name = "id" id = "id"><br>
<label id = "passwd"> Password :</label>
<input type = "password" name = "passwd" id = "passwd"><br><br>
<input type = "submit" value = "Log In">
</form>
```


`<form action = "login" method = "get">`
서버로 요청을 보내는 <form> 태그 영역으로, action 값을
"login" 으로 지정하여 "login" URL 로 요청을 전송하고 method 값이 "get" 이기에 get 방식으로 요청

```
<label id = "id"> ID :</label>
<input type = "text" name = "id" id = "id">
```
<label> 태그에 id 속성값을 "id" 로 지정하여 HTML 에서 "ID" 레이블을 클릭 시, 아이디를 입력하는 text 상자로 이동한다. <label> 부분과 <input> 영역은 id 속성값으로 연결된다.


<h3>Servlet 생성</h3>

```java
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		String id = request.getParameter("id");
		String passwd = request.getParameter("passwd");
		response.setContentType("text/html;charset=euc-kr");
		PrintWriter out = response.getWriter();
		out.println("ID = " + id + "<br>");
		out.println("Password = " + passwd + "<br>");
```

`String id = request.getParameter("id");` <br>
`String passwd = request.getParameter("passwd");` <br>
클라이언트에서 전송되는 id 와 passwd 라는 이름의 파라미터 값을 수신

`response.setContentType("text/html;charset=euc-kr");`
응답하는 데이터 타입이 HTML 이고 응답되는 데이터들의 한글처리

`PrintWriter out = response.getWriter();`
문자열 단위로 reponse 객체에 내용을 출력하는 스트림 생성


<h3>결과</h3>

>ID = Samjuheon  
>Password = juheonSung

<br>

# Post
Get 방식과 유사하지만 서블릿 쪽에서 요청 처리를 수행 시, doGet 이 아닌 doPost 메소드에서 요청이 처리된다.

<h3>클라이언트 페이지 생성</h3>

```html
<h1>Sign in</h1>
<form action = "memReg" method = "post">
	Name : <input type = "text" name = "name"><br>
	Address : <input type = "text" name = "addr"><br>
	Tel : <input type = "text" name = "tel"><br>
	Hobby : <input type = "text" name = "hobby"><br>
	<input type = "submit" value = "Sign in">
</form>
```

`<form action = "memReg" method = "post">`
form 태그의 요청 방식을 post로 지정

<h3>Servlet 생성</h3>

```html
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		request.setCharacterEncoding("euc-kr");
		response.setContentType("text/html;charset=euc-kr");
		PrintWriter out = response.getWriter();
		String name = request.getParameter("name");
		String addr = request.getParameter("addr");
		String tel = request.getParameter("tel");
		String hobby = request.getParameter("hobby");
		out.println("Name = " + name + "<br>");
		out.println("Address = " + addr + "<br>");
		out.println("Tel = " + tel + "<br>");
		out.println("Hobby = " + hobby + "<br>");
	}

```

`request.setCharacterEncoding("euc-kr");`
Post 방식으로 전송된 한글 파라미터 값 처리

<h3>결과</h3>


Name = Samjuheon  
Address = 101-3 nipperstreet  
Tel = 010-7127-2666  
Hobby = Piano
