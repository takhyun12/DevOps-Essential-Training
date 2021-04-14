## HTTP Session

### Session 이란?
* 클라이언트(사용자)가 서버에 접속을 하면 그 클라이언트만의 저장공간에 서버에 생성이 되는데 이 공간이 바로 Session입니다.
* Session은 접속한 클라어언트만의 고유공간이기 때문에, 서버에 접속한 클라이언트 숫자만큼 Session이 생성됩니다.
* Session은 클라이언트의 브라우저 단위로 생성됩니다.

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
* Apigee는 API 개발 및 관리를 위한 플랫폼입니다. Apigee는 프록시 레이어와 함께 서비스를 전면에 내세워 백엔드 서비스 API의 추상화 또는 퍼사드를 제공하고 보안, 비율 제한, 할당량, 분석 등을 제공합니다.
