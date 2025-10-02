# ☁️ Daily Compass (Azure 기반 개인 맞춤형 대시보드)

## 📌 프로젝트 소개

**Daily Compass**는 바쁜 현대인들이 하루를 체계적으로 계획하고 관리할 수 있도록 돕는 **개인 맞춤형 데일리 대시보드**입니다. 이 프로젝트는 단순한 기능 구현을 넘어, Microsoft Azure의 클라우드 네이티브 기술을 기반으로 **높은 수준의 가용성(99.95%+)과 확장성, 그리고 강력한 보안**을 갖춘 서비스를 구축하는 데 목표를 두었습니다.

-----

## ✨ 주요 기능 및 특징

  * **마음 우체통 (AI 명언 추천)**
      * 사용자의 감정(좋음/나쁨)에 따라 맞춤형 명언을 추천합니다. 
      * **Azure AI Speech Service**를 연동하여 추천된 명언을 음성으로 들려주는 기능을 제공합니다.
  * **My Diary (일정 관리)**
      * **TODO 리스트**와 **캘린더(Calendar)** 뷰를 통해 사용자가 개인의 할 일과 일정을 직관적으로 관리할 수 있습니다. 
  * **실시간 뉴스 피드**
      * 서버에서 **웹 크롤링**을 통해 네이버의 최신 뉴스를 수집하고, 사용자에게 실시간으로 제공합니다.
  * **보안 및 인증**
      * 회원가입 및 로그인 기능을 통해 사용자별 데이터를 안전하게 관리합니다.

-----

## 🏛️ 주요 아키텍처 및 데이터 흐름

이 서비스는 Frontend, Backend, Database가 명확히 분리된 **클라우드 네이티브 아키텍처**를 기반으로 설계되었습니다.

  * **사용자 요청**: `Client (React UI)` → `Azure Static Web Apps`
  * **API 처리**: `Azure Functions (Serverless)` → `Cosmos DB` / `AI Service` / `External API`
  * **보안**: 모든 주요 리소스(DB, Storage)는 **Private Endpoint**를 통해 외부 접근을 원천 차단하고, 격리된 가상 네트워크(VNet) 내에서만 통신하여 데이터 유출 위험을 최소화했습니다.

-----

## 🛠 기술 스택

| 구분 | 기술 |
| --- | --- |
| **Cloud & Infra** | Azure Functions, Azure Cosmos DB (MongoDB API), Azure Static Web Apps, Azure AI Speech Service, VMSS, Private Endpoint, VNet, NSG, Application Insights  |
| **Backend** | Node.js, Azure Functions, Cheerio, Axios  |
| **Frontend** | React, CSS, JavaScript  |
| **Database** | Azure Cosmos DB (MongoDB API)  |
| **DevOps** | GitHub Actions (CI/CD)  |

-----

## 📂 프로젝트 구조

```yaml
📦 DAILY-COMPASS
┣ 📂 .github/workflows # CI/CD 파이프라인 (GitHub Actions)
┣ 📂 api # Backend (Azure Functions)
┃ ┣ 📂 GetRandomMessage
┃ ┣ 📂 Login
┃ ┣ 📂 News # 뉴스 크롤링 API
┃ ┣ 📂 Signup
┃ ┣ 📂 TextToSpeech
┃ ┗ 📂 todos
┣ 📂 frontend # Frontend (React)
┃ ┣ 📂 public
┃ ┗ 📂 src
┗ 📜 README.md # 프로젝트 설명 문서
```

-----

## 📸 실행 화면

| 로그인 / 회원가입 | 메인 대시보드 (기능 통합) |
| --- | --- |
|  |  |
| **마음 우체통 (AI 명언/음성)** | **실시간 뉴스 및 TODO 관리** |
|  |  |

*(위 이미지는 예시이며, 실제 이미지 경로로 수정해주세요.)*

-----

## 💡 제가 기여한 부분과 학습 포인트

[cite\_start]저는 이 팀 프로젝트에서 **전체 아키텍처 설계와 실시간 뉴스 웹 크롤링 API 개발**을 주도적으로 담당했습니다. 

  * **클라우드 아키텍처 설계 역량 강화**
      * 안정성, 보안, 확장성을 모두 고려하여 **Azure 클라우드 네이티브 시스템을 처음부터 끝까지 설계**한 경험을 쌓았습니다. 
      * Private Endpoint, VNet, NSG를 적용하여 **기업 수준의 보안 인프라를 직접 구성**하고 데이터 흐름을 통제했습니다. 
  * **서버리스 기반 백엔드 API 개발**
      * Node.js와 Cheerio 라이브러리를 활용하여 **뉴스 웹 크롤링 모듈을 개발**하고, 이를 **Azure Functions 기반의 서버리스 API로 구현**하여 비용 효율성과 확장성을 확보했습니다. 
  * **문서화와 커뮤니케이션**
      * 팀원들이 아키텍처를 명확히 이해하고 개발에 참여할 수 있도록 **데이터 흐름도, DB 스키마, UI/UX 와이어프레임 등 상세한 설계 문서를 작성**했습니다. 

-----

## 🚀 향후 개선 아이디어

  * 📱 **인증 강화**: Azure AD B2C를 도입하여 **소셜 로그인 기능**을 추가하고 보안성을 높일 계획입니다. 
  * 🔎 **서비스 고도화**: Azure Machine Learning을 활용하여 사용자 활동 패턴을 분석하고, **개인 맞춤형 뉴스를 추천**하는 기능을 개발하고 싶습니다. 
  * 🐳 **컨테이너화**: 일부 서비스를 컨테이너(ACI/AKS) 환경으로 전환하여 **MSA(Microservices Architecture) 구조로의 발전 가능성을 모색**하고 이식성을 증대시킬 것입니다. 

-----

### 👤 Author

  - **이름**: 김태영
  - **역할**: 클라우드 아키텍트 & 개발자
  - **Contact**: katiekim412@gmail.com | [LinkedIn](http://www.linkedin.com/in/katiekim412)
