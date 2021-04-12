## Backgrounds
* test

## Cloud API
### Apigee: Google Cloud's API Management platform

#### Architecture of Apigee
* Apigee는 API 개발 및 관리를 위한 플랫폼입니다. Apigee는 프록시 레이어와 함께 서비스를 전면에 내세워 백엔드 서비스 API의 추상화 또는 퍼사드를 제공하고 보안, 비율 제한, 할당량, 분석 등을 제공합니다.

![apigee](https://user-images.githubusercontent.com/41291493/114328763-7f5b4200-9b78-11eb-99ac-cdde274ce7e9.png)

* Apigee 서비스: API 프록시를 생성, 관리, 배포하는 데 사용하는 서비스입니다.
* Apigee 런타임: Google이 Kubernetes 클러스터에서 유지관리하는 컨테이너화된 런타임 서비스 집합입니다. 모든 API 트래픽이 통과되어 이러한 서비스에 의해 처리됩니다.
* GCP 서비스: ID 관리, 로깅, 분석, 측정항목, 프로젝트 관리 기능을 제공합니다.
* 백엔드 서비스: 앱에서 API 프록시의 데이터에 대한 런타임 액세스를 제공하기 위해 사용합니다.




