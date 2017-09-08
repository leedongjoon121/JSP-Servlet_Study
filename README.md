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


---


# JSP특징

- 1. 자바의 모든 기능을 사용할 수 있어 발전 가능성이 무한하다.
- 2. 서블릿으로 컴파일된 후 메모리에서 처리되기 때문에 많은 사용자의 접속도 원활하게 처리할 수 있다.
- 3. JSP 또는 다른 서블릿 간의 데이터를 쉽게 공유할 수 있다.
- 4. 빈즈(Beans)라고 하는 자바컴포넌트를 사용할 수 있다.
- 5. 커스텀 태그를 만들어 사용할 수 있으며, JSTL(JSP Standard Tag Library)과 같은 태그라이브러리를 이용할 수 있다.
- 6. 스트러츠, 스프링 @MVC등 다양한 프레임워크와 결합하여 개발할 수 있다.

# Servlet특징
### 서블릿은 "컨테이너"라고 불리는 서버 소프트웨어에 의해 동작한다.
### 서블릿 컨테이너는 웹 서버와 마찬가지로 URL을 기반으로 한 요청에 따라 해당 서블릿을 실행한다.

## 서블릿 생명주기
### 1. 서블릿 초기화 : init() 메서드
> 클라이언트요청이들어오면 컨테이너는 해당 서블릿이 메모리에 있는지 확인함, 서블릿이 메모리에 없으면 init() 메서드가 호출
  init() 메서드는 초기 한번실행

### 2. 요청/응답 : service() 메서드
> init() 메서드는 초기 한번 실행되고 이후 요청은 스레드로 실행, 각각 service() 메서드를 통해 doGet()이나 doPost()로 분기
  이때 파라미터로 HttpServletRequest와 HttpServletResponse클래스 타입인 request와 response객체가 제공
  사용자 요청처리는 request로, 응답처리는 response 객체로 처리

#### GET방식
> 서버에 있는 정보를 가져오려고 설계된 방법, 최대 240Byte까지 데이터를 전달할 수있다.(Parameter)
  쿼리스트링을 통해 서버로전달 => http://www.xxx.co.kr/servlet/login?id=dj&name=dongjoon
  ? 이후의 속성값들이 '속성=값'형태로사용, &는 여러 속성값을 전달할 때 연결해주는 문장
  
#### POST방식
> 서버로 정보를 올리려고 설계된 방식(HTML Form 태그 형식)
  서버에 전달할 수있는 데이터크기에 제한이 없다
  URL에는 매개변수가 표시되지 않음
  
  
