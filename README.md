# JSP & Servlet
JSP & Servlet 핵심 기능 & 개념 정리 => 추후 응용 단계까지 업로드 예정

### name :  Dongjoonlee 
### nation : south korea
### date of birth : 1993.04.06
### univ : gachon university
### email : ehdwns46@naver.com

<hr/>
<br/>

## 목차

* [1. JSP 특징](#JSP특징)
* [2. Servlet 특징](#Servlet특징)
* [3. HttpServlet클래스](#HttpServlet클래스)
* [4. 지시어](#지시어)
* [5. 액션](#액션)

---

<br/>

# JSP특징

- 1. 자바의 모든 기능을 사용할 수 있어 발전 가능성이 무한하다.
- 2. 서블릿으로 컴파일된 후 메모리에서 처리되기 때문에 많은 사용자의 접속도 원활하게 처리할 수 있다.
- 3. JSP 또는 다른 서블릿 간의 데이터를 쉽게 공유할 수 있다.
- 4. 빈즈(Beans)라고 하는 자바컴포넌트를 사용할 수 있다.
- 5. 커스텀 태그를 만들어 사용할 수 있으며, JSTL(JSP Standard Tag Library)과 같은 태그라이브러리를 이용할 수 있다.
- 6. 스트러츠, 스프링 @MVC등 다양한 프레임워크와 결합하여 개발할 수 있다.

<br/>

# Servlet특징
### 서블릿은 "컨테이너"라고 불리는 서버 소프트웨어에 의해 동작한다.
### 서블릿 컨테이너는 웹 서버와 마찬가지로 URL을 기반으로 한 요청에 따라 해당 서블릿을 실행한다.
### 서블릿은 javax.servlet.GenericServlet을 상속받는 javax.servlet.HttpServlet 클래스를 상속받아 구현할 수 있다.

<br/>

## 서블릿 생명주기
### 1. 서블릿 초기화 : init() 메서드
> 클라이언트요청이들어오면 컨테이너는 해당 서블릿이 메모리에 있는지 확인함, 서블릿이 메모리에 없으면 init() 메서드가 호출
  init() 메서드는 초기 한번실행

### 2. 요청/응답 : service() 메서드
> init() 메서드는 초기 한번 실행되고 이후 요청은 스레드로 실행, 각각 service() 메서드를 통해 doGet()이나 doPost()로 분기
  이때 파라미터로 HttpServletRequest와 HttpServletResponse클래스 타입인 request와 response객체가 제공
  사용자 요청처리는 request로, 응답처리는 response 객체로 처리

### 3. 서블릿 종료 : destroy() 메서드
> 컨테이너로부터 서블릿 종료 요청이 있을 때 destroy()메서드 호출

<br/>

#### GET방식
> 서버에 있는 정보를 가져오려고 설계된 방법, 최대 240Byte까지 데이터를 전달할 수있다.(Parameter)
  쿼리스트링을 통해 서버로전달 => http://www.xxx.co.kr/servlet/login?id=dj&name=dongjoon
  ? 이후의 속성값들이 '속성=값'형태로사용, &는 여러 속성값을 전달할 때 연결해주는 문장
  
#### POST방식
> 서버로 정보를 올리려고 설계된 방식(HTML Form 태그 형식)
  서버에 전달할 수있는 데이터크기에 제한이 없다
  URL에는 매개변수가 표시되지 않음
  
 <br/>
 
 # HttpServlet클래스
 ## doGet메서드, doPost메서드
 > HttpServlet 클래스에서 사용자 요청을 처리하는 doGet/doPost 메서드는 모두 HttpServletRequest와 HttpServletResponse 객체를 매개변수로 가지고있음

```swift
  public void doGet(HttpServletRequest request, HttpServletResponse response)
  public void doPost(HttpServletRequest request, HttpServletResponse response)
```

## HttpServletRequest 클래스의 주요 메서드

메서드|설명
----|----
getParameter(name)|문자열 name과 같은 이름을 가진 매개변수 값을 가져온다
getParameterValues(name)|문자열 name과 같은 이름을 가진 매개변수 값을 배열 형태로 가져온다
getMethod()|현재 요청이 Get인지, Post인지 파악해서 가져옴
getSession()|현재 세션을 가져옴

<br/>

## HttpServletResponse 클래스의 주요 메서드

메서드|설명
----|----
setContentType(type)|문자열 형태의 type에 지정된 MIME Type으로 ContentType을 설정
sendRedirect(url)|클라이언트 요청을 다른 페이지로 보낸다.

<br/>

# 지시어
> 지시어(Directives)는 해당하는 jsp 파일의 속성을 기술하는 곳으로 크게 page, include, taglib으로 나눌수 있음

## page 지시어
> page 지시어는 현재의 JSP 페이지를 컨테이너에서 처리 하는데 필요한 각종 속성을 기술하는 부분으로, 대개 소스코드 맨앞에서 볼수있음

```swift
   <%@page 속성1="값" 속성2="값" ... %>
   
   <%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8" 
       import = "java.util.*" errorPage="error.jsp"%>    
```

### page 지시어 속성

속성|설명|기본 설정 값
----|----|----
import|JSP 내에서 사용할 외부 자바 패키지나 클래스의 불러오기를 정함|-
session|세션의 사용유무를 정함|true
errorPage|현재 페이지에서 오류가 발생할 경우 호출될 페이지를 지정|-
isErrorPage|오류만을 처리하는 페이지로 지정|false
contentType|MIME 형식 지정 및 캐릭터셋을 설정 |text/html
pageEncoding|contentType과 동일한 기능을 한다|ISO-8859-1

<br/>

## include지시어
> include 지시어는 현재 JSP파일에 다른 HTML이나 JSP문서를 포함하기 위한 기능을 제공, 여러 페이지에 공통으로 들어갈 내용을 관리할 때 유용함
 
```swift
  <%@ include file = "포함될 파일 이름" %>
  <%@ include file = "news.jsp" %>
```

<br/>

## taglib지시어
> taglib지시어는 JSP기능을 확장 하기위해 만들어진 커스텀 태그 라이브러리를 JSP파일에서 사용하기 위한 지시어(사용자가 만드는 지시어)
> uri와 prefix로 구성, uri는 TLD파일을 지정하는데 사용, 커스텀태그의 구조를 정의한 파일로 XML형식으로 미리 만들어져 있어야함
  prefix는 JSP파일에서 커스텀 태그를 사용하기 위한 이름 일종의 접두어 역할
```swift
   <%@ taglib uri="/META-INF/mytag.tld" prefix="mytag" %>
   <body>
      <mytag:GetInfo name="user1"/>
   </body>
```

<br/>

# 액션
