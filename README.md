# 6주차 4단계 질문에 대한 답

## 질문 1. SPA 페이지를 정적 배포를 하려고 할 때 Vercel을 사용하지 않고 한다면 어떻게 할 수 있을까요?

SPA(Single Page Application)는 클라이언트 측에서 동적으로 업데이트되는 웹 애플리케이션이다. Vercel을 사용하지 않고 배포하는 방법은 다음과 같다.

### 1.1 GitHub Pages
- **설명**: GitHub 저장소에서 무료로 정적 사이트를 배포할 수 있다.
- **방법**:
  1. SPA 빌드 파일(예: `dist`)을 커밋한다.
  2. GitHub 저장소의 **Settings** > **Pages**에서 배포 소스를 설정한다.

### 1.2 Netlify
- **설명**: 빠르고 쉽게 정적 사이트를 배포할 수 있는 서비스이다.
- **방법**:
  1. Netlify에 가입하고 GitHub 저장소를 연결한다.
  2. 빌드 명령과 배포 디렉토리를 설정한다.

### 1.3 AWS S3 + CloudFront
- **설명**: AWS S3 버킷을 이용해 정적 파일을 저장하고 CloudFront로 배포한다.
- **방법**:
  1. S3 버킷에 빌드 파일을 업로드한다.
  2. CloudFront 배포를 설정하여 S3를 원본으로 지정한다.

### 1.4 Firebase Hosting
- **설명**: Firebase의 정적 웹 호스팅 서비스이다.
- **방법**:
  1. Firebase CLI 설치 및 프로젝트를 설정한다.
  2. `firebase deploy` 명령어로 배포한다.

## 질문 2. CSRF나 XSS 공격을 막는 방법은 무엇일까요?

### 2.1 CSRF 공격 방지
1. **CSRF 토큰 사용**: 서버에서 고유한 토큰을 생성하고 요청 시 검증한다.
2. **SameSite 쿠키 사용**: `SameSite` 속성을 `Strict` 또는 `Lax`로 설정한다.
3. **Referer 및 Origin 헤더 검사**: 유효한 도메인에서 온 요청인지 확인한다.

### 2.2 XSS 공격 방지
1. **출력 인코딩**: 사용자 입력을 HTML에 출력하기 전 인코딩한다.
2. **콘텐츠 보안 정책(CSP) 설정**: 외부 스크립트 출처를 제한한다.
3. **입력 검증 및 정규화**: 사용자 입력의 유효성을 검사한다.
4. **HTTP 보안 헤더 사용**: `X-XSS-Protection` 헤더를 설정한다.

## 질문 3. 브라우저 렌더링 원리에대해 설명해주세요.

### 3.1 렌더링 과정
1. **HTML 파싱 및 DOM 트리 생성**: HTML 문서를 파싱하여 DOM을 만든다.
2. **CSS 파싱 및 CSSOM 생성**: CSS 파일을 파싱하여 스타일 정보를 만든다.
3. **렌더 트리 생성**: DOM과 CSSOM을 결합하여 화면에 표시될 요소를 구성한다.
4. **레이아웃 계산**: 각 요소의 크기와 위치를 계산한다.
5. **페인팅(Painting)**: 요소의 스타일을 적용하여 픽셀을 그린다.
6. **컴포지팅(Compositing)**: 여러 레이어를 조합하여 최종 화면을 출력한다.

### 3.2 최적화 고려 사항
- **레이아웃 변경 최소화**: 불필요한 레이아웃 계산을 줄인다.
- **비동기 로딩 사용**: 리소스를 비동기로 로드하여 초기 렌더링을 빠르게 한다.
- **렌더링 차단 리소스 최소화**: CSS와 JavaScript 로드를 최적화한다.