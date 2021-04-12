## Backgrounds
* API(Application Programming Interface) : 응용 프로그램에서 사용할 수 있도록, 운영 체제나 프로그래밍 언어가 제공하는 기능을 제어할 수 있도록 만든 인터페이스를 뜻한다. 

## Cloud API
### Apigee: Google Cloud's API Management platform

#### Apigee 아키텍처
* Apigee는 API 개발 및 관리를 위한 플랫폼입니다. Apigee는 프록시 레이어와 함께 서비스를 전면에 내세워 백엔드 서비스 API의 추상화 또는 퍼사드를 제공하고 보안, 비율 제한, 할당량, 분석 등을 제공합니다.

![apigee](https://user-images.githubusercontent.com/41291493/114328763-7f5b4200-9b78-11eb-99ac-cdde274ce7e9.png)

* Apigee 서비스: API 프록시를 생성, 관리, 배포하는 데 사용하는 서비스입니다.
* Apigee 런타임: Google이 Kubernetes 클러스터에서 유지관리하는 컨테이너화된 런타임 서비스 집합입니다. 모든 API 트래픽이 통과되어 이러한 서비스에 의해 처리됩니다.
* GCP 서비스: ID 관리, 로깅, 분석, 측정항목, 프로젝트 관리 기능을 제공합니다.
* 백엔드 서비스: 앱에서 API 프록시의 데이터에 대한 런타임 액세스를 제공하기 위해 사용합니다.

#### Apigee 유형

* Apigee: Apigee가 환경을 유지관리하는 호스팅된 SaaS 버전으로, 서비스를 빌드하고 해당 서비스에 API를 정의하는 데 집중할 수 있습니다.
* Apigee Hybrid: 온프레미스 또는 선택한 클라우드 제공업체에 설치된 런타임 영역과, Apigee 클라우드에서 실행되는 관리 영역으로 구성된 하이브리드 버전입니다. 이 모델에서는 사용자의 자체 기업 승인을 받은 경계 내에서 API 트래픽 및 데이터가 제한됩니다.

#### Apigee Lifecycle
* Apigee는 API Lifecycle의 전반적인 모든 영역을 관리한다.

![api lifecycle](https://user-images.githubusercontent.com/41291493/114329299-ee856600-9b79-11eb-88e5-5a3d1ffd6e50.png)

## RESTful API Design
