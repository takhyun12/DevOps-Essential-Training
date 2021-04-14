## HTTP Session

### Session 이란?
* 클라이언트(사용자)가 서버에 접속을 하면 그 클라이언트만의 저장공간에 서버에 생성이 되는데 이 공간이 바로 Session입니다.
* Session은 접속한 클라어언트만의 고유공간이기 때문에, 서버에 접속한 클라이언트 숫자만큼 Session이 생성됩니다.
* Session은 클라이언트의 브라우저 단위로 생성됩니다.

### Session의 원리
* 웹 클라이언트가 서버에게 요청을 보내면 서버는 클라이언트를 식별하는 session id를 생성한다.
* 서버는 session id로 key와 value를 저장하는 HttpSession을 생성하고, session id를 저장하고 있는 쿠키를 생성하여 클라이언트에게 전송한다.
* 클라이언트는 서버 측에 요청을 보낼 때, session id를 가지고 있는 쿠키를 전송한다.
* 서버는 쿠키의 session id로 HttpSession을 찾는다.

### Session 만들기

```javascript
session.setAttribute(String name, Object value);
```

* name이 바로 세션에 저장된 특정 값을 찾아오기 위한 키로 사용된다.
* name과 value는 1:1 대응이다.
* name은 String type이며 value는 Object type이이어야만 한다.
* int, doublic, char등의 primitive type은 사용할 수 없다.
* 동일한 이름으로 세션에 저장하게 되면 항상 덮어씌우게 된다.

### Session에 저장된 값 가져오기

```javascript
Object getAttribute(String name);
String valeu = (String)session.getAttribute("name"); // 형변환
```

* 세션 객체 안에 지정한 name에 해당되는 속성이 없으면 getAttribute가 null 값을 되돌린다.
* 반환되는 값이 Object형이기 때문에 반드시 적절한 형변환을 해야한다.
* 세션에 저장된 값을 String 형태로 얻어오려면 cast 연산자로 형 변환을 해야한다.

### Session 생성여부 확인

```javascript
HttpSession session = request.getSession();
HttpSession session = request.getSession(true);
HttpSession session = request.getSession(false);
```

* 서버에 생성된 세션이 있다면 세션을 반환하고, 없다면 새 세션을 생성하여 반환한다.(default: true)
* 파라미터로 false를 전달하면 이미 생성된 세션이 있을 때 그 세션을 반환하고 없으면 null을 반환한다.

### Session 값 삭제

```javascript
removeAttribute(String name);
invalidate();
```

* removeAttribute 메서드로 name 값에 해당하는 세션 정보를 삭제할 수 있다.
* invalidate로 모든 세션 정보를 한 번에 삭제할 수 있다.

### Session 유지시간 설정

```javascript
<session-config>
  <session-timeout>30</session-timeout>
</session-config>
```

* web.xml 파일의 `<session-timeout>`을 수정하면 된다.


