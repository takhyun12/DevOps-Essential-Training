## Backgrounds
* API(Application Programming Interface) : 응용 프로그램에서 사용할 수 있도록, 운영 체제나 프로그래밍 언어가 제공하는 기능을 제어할 수 있도록 만든 인터페이스를 뜻한다. 

## Cloud API
### Apigee: Google Cloud's API Management platform

#### Apigee 아키텍처
* Apigee는 API 개발 및 관리를 위한 플랫폼입니다. Apigee는 프록시 레이어와 함께 서비스를 전면에 내세워 백엔드 서비스 API의 추상화 또는 퍼사드를 제공하고 보안, 비율 제한, 할당량, 분석 등을 제공합니다.

![apigee](https://user-images.githubusercontent.com/41291493/114328763-7f5b4200-9b78-11eb-99ac-cdde274ce7e9.png)

* `Apigee 서비스`: API 프록시를 생성, 관리, 배포하는 데 사용하는 서비스입니다.
* `Apigee 런타임`: Google이 Kubernetes 클러스터에서 유지관리하는 컨테이너화된 런타임 서비스 집합입니다. 모든 API 트래픽이 통과되어 이러한 서비스에 의해 처리됩니다.
* `GCP 서비스`: ID 관리, 로깅, 분석, 측정항목, 프로젝트 관리 기능을 제공합니다.
* `백엔드 서비스`: 앱에서 API 프록시의 데이터에 대한 런타임 액세스를 제공하기 위해 사용합니다.

#### Apigee 유형

* `Apigee`: Apigee가 환경을 유지관리하는 호스팅된 SaaS 버전으로, 서비스를 빌드하고 해당 서비스에 API를 정의하는 데 집중할 수 있습니다.
* `Apigee Hybrid`: 온프레미스 또는 선택한 클라우드 제공업체에 설치된 런타임 영역과, Apigee 클라우드에서 실행되는 관리 영역으로 구성된 하이브리드 버전입니다. 이 모델에서는 사용자의 자체 기업 승인을 받은 경계 내에서 API 트래픽 및 데이터가 제한됩니다.

#### Apigee Lifecycle
* Apigee는 `API Lifecycle`의 전반적인 모든 영역을 관리한다.

![api lifecycle](https://user-images.githubusercontent.com/41291493/114329299-ee856600-9b79-11eb-88e5-5a3d1ffd6e50.png)

---

## RESTful API Design

### 관련용어
* `Resource`: 연관된 데이터를 갖고 있는 오브젝트나 어떤 표현이며, 동작하는 메소드를 가질 수 있다. 
* e.g. Animals, schools, employees는 각각 하나의 resource이며, delete, add, update가 이것들과 동작하는 operation이다.
* `Collections`: resource들의 집합이다.
* e.g. Companies는 Company resource의 collection이다.
* `URL(Uniform Resource Locator)`: resource가 어떤 action에 연결되거나, 그 action을 동작 하게 하는 경로이다.

### API Design
* 다음은 Companies에 관한 API 디자인 예시이며, 이는 좋지 못한 API 디자인의 표본이다.

```
/addNewEmployee
/updateEmployee
/deleteEmployee
/deleteAllEmployees
/promoteEmployee
/promoteAllEmployee
```

* URL은 동사나 `action`이 아닌 `resource(명사)`만을 포함해야 한다. /addNewEmployee라는 API 경로는 Employee라는 resource에 addNew라는 `action`을 포함하고 있다.
* HTTP methods(GET, POST, DELETE, PUT)의 CRUD를 이용하여 디자인한다.
* Resource는 API endpoint에서 항상 복수 단위어야 하고, resource의 instance에 접근 하고 싶다면, URL에 id를 포함시켜야 한다.

1) `GET`: resource의 데이터를 서버에 요청
2) `POST`: resource의 생성을 서버에 요청
3) `PUT`: 서버에 resource가 있다면 update를, 없다면 create를 하도록 요청
4) `DELETE`: 어떤 resource나 instance의 삭제를 서버에 요청한다.

```
method GET, path /companies는 모든 companies의 리스트를 받는다.
method GET, path /companies/34는 company 34의 상세 정보를 받는다.
method DELETE, path /companies/34는 company 34를 삭제한다.
GET /companies/3/employees는 company3에 있는 모든 employee의 리스트를 받는다.
GET /companies/3/employees/45는 company3의 45번 employee의 상세 정보를 받는다.
DELETE /companies/3/employees/45는 company3의 45번 employee를 삭제한다.
POST /companies는 새 company를 만들고, 만들어진 company의 상세 정보를 리턴한다.
```

### HTTP response status codes
* API를 통해 서버에 요청을 보낼 때, 클라이언트는 그 요청이 실패했는지, 통과했는지, 요청이 잘못됐는지에 대해 알아야 한다. HTTP status code는 다양한 상황에 각각 대응되는 표준 코드가 존재하고, 서버는 항상 알맞는 status code를 리턴해야 한다.

* 2xx (Success)

```
200 Ok – GET, PUT, POST의 성공을 의미하는 표준 HTTP response.
201 Created – 새로운 instance가 생성되었을 때 리턴되야하는 status code.
204 No Content – 요청이 성공적이었지만, 다른 데이터를 리턴 하지 않았을 경우. ex) DELETE
```

* 3xx (Redirection)

```
304 Not Modified – 클라이언트가 해당 response를 cache에 가지고 있어서 같은 데이터를 여러번 보낼 필요가 없을 경우.
```

* 4xx (Client Error)

```
400 Bad Request – 서버가 클라이언트의 요청을 해석 할 수 없을 경우.
401 Unauthorized – 클라이언트가 리소스에 접근 권한이 없음을 말하며, 권한을 인증 받을 수 있는 값과 함께 재 요청을 해야 하는 경우.
403 Forbidden – 요청은 성공적이었지만, 어떤 이유에서 페이지나 리소스에 접근 권한이 없을 경우. ex) 클라이언트에서 서버 디렉토리에 접근이 불가능 한 경우.
404 Not Found – 요청된 리소스가 현재 존재하지 않는 경우.
410 Gone – 요청된 리소스가 내부적으로 이동이 있어서 현재 해당 방법으로 접근이 불가능한 경우.
```
* GET method가 URI를 너무 길게 만든다면, 서버는 HTTP status로 414 URI Too Long를 리턴 할 수 있다. 
* 그런 경우에는, POST method를 이용해서 request body에 param을 보내는 방법이 있다.

### Searching, sorting, filtering and pagination
* `Sorting`: 클라이언트가 정렬된 companies 리스트를 받고 싶을 때, GET /company endpoint는 쿼리에 들어갈 sort param들을 받아야 할 것이다.

```
GET /companies?sort=rank_asc
```

* `Filtering`: 데이터 셋을 필터링 하기 위해서 다수의 query parm을 보내야 할 것이다.

```
GET/companies?category=banking&location=india
```

* `Searching`: company의 이름으로 검색 하기 위한 API endpoint는 다음과 같을 것이다

```
GET /companies?search=Digital Mckinsey
```

* `Pagination`: 데이터 셋의 규모가 커지면, 퍼포먼스를 향상시고 response를 쉽게 다루기 위해 해당 데이터 셋을 나누게 될 것이다

```
GET /companies?page=23
```

### Versioning
* API의 업데이트를 고려하여 버전 정보를 포함하는것이 좋다

```
http://api.yourservice.com/v1/companies/34/employees
```

---

## API Key 인증 방식
* REST API를 요청(Request)할 때 HTTP 헤더에 Authorization 정보를 추가하여 인증수행

```
// syntax
Authorization: <AuthenticationMethod> apiKey=<API Key>, date=<Date Time>, salt=<Salt>, signature=<Signature>
```

```
// sample
curl -X GET https://api.solapi.com/messages/v4/list --header "Authorization: HMAC-SHA256 apiKey=NCSAYU7YDBXYORXC, date=2019-07-01T00:41:48Z, salt=jqsba2jxjnrjor, signature=1779eac71a24cbeeadfa7263cb84b7ea0af1714f5c0270aa30ffd34600e363b4"
```

* 메시지의 무결성 검증(인증)을 위한 용도로 Signature 생성 및 검증에 Hash기반의 MAC 알고리즘을 사용
* Signature는 중복사용이 불가하며 15분 안에 전송되는 요청(Request)의 Signature 값은 항상 다름
* Salt는 매번 요청때마다 다른 문자열로 변경하여 요청 시간대가 같아도 항상 Signature가 다른 값으로 생성되도록 함
* HTTP Stauts code 기반의 예외처리

```
403 InvalidAPIKey - 유효한 API Key가 아님
403 SignatureDoesNotMatch - 생성한 Signature가 일치하지 않음
403 RequestTimeTooSkewed - 시간 값이 서버 시간을 15분 이상 벗어남
403 DuplicatedSignature - 15분 안에 동일한 signature 값
```

---

## OAuth2 API
* OAuth 인증 방식은 위에서 언급한 대로 인증의 과정을 '타 서비스에게 위임' 하는 인증 방식이다
* 사용자가 '구글 로그인' 기능을 통해 전송한 구글 계정 정보가 유효한지를 확인한 후,
* 유효하다면 해당하는 구글 유저 정보 중 일부(유저 이름 등)를 내 웹 사이트에 제공해주는 '인증' 과정만을 처리해준다
* Google APIs 등에서 OAuth 서비스 생성방법

```
1. 프로젝트 - 사용자 인증정보 만들기 - OAuth Client ID - 서비스 유형/이름/URL 입력
2. 클라이언트 ID/비밀번호를 발급받음
```

* 구글에게 인증을 요청한다

```
GET https://api.google.com/oauth2/v1/authorize
```

* 구글로부터 리다이렉션된 데이터는 code 혹은 token이 된다

```
// rseponse_type이 code일 경우
{
    code: 'ADFKVJCK19JDFKL2KFJLS3388',
    state: '사용자가 보내왔던 state값'
}

// rseponse_type이 token일 경우
{
    access_token: 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.ZwUymzWAUiTxQ...',
    refresh_token: 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.ZwUymzWAUiTxQ...'
}
```

* response type이 코드인 경우 Access Token을 추가로 발급받는다
* POST body에 code와 cliend_id 등을 포함한다

```
POST https://api.google.com/oauth2/v1/access_token
```

* Access Token을 통해 API를 사용한다
* GET/POST header에 Access Token을 포함한다


```
curl -X (GET|POST) https://api.google.com/<접근하려는 API url>
-H 'Authorization: bearer <Access Token>'
```

* 권한(Scope) 에러처리 : 어플리케이션에서 요구하는 권한과 실제로 사용자가 인가한 권한이 다른경우
* 액세스 토큰을 사용간에 권한에 대한 오류가 발생할 수 있어 예외처리를 수행해야 함

---
