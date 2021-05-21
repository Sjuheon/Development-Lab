```jsp
<%@ page language="java" contentType="text/html; charset=EUC-KR"
    pageEncoding="EUC-KR"%>
    
<!DOCTYPE html>
<%@page import="java.util.Calendar"%>
<html>

<head>
<%
Calendar c = Calendar.getInstance();
int hour = c.get(Calendar.HOUR_OF_DAY);
int minute = c.get(Calendar.MINUTE);
int second = c.get(Calendar.SECOND);
%>
<meta charset="EUC-KR">
<title>Time</title>
</head>

<body>
Current Time <%=hour%>h, <%=minute%>m, <%=second%>s
</body>
</html>
```

> <b>Current Time 16h, 5m, 46s</b>
