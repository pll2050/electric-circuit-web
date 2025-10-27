# Gemini 프로젝트 컨텍스트

이 파일은 Gemini가 `electric_circuit_web` 프로젝트의 맥락을 이해하는 데 도움을 주기 위해 작성되었습니다.

## 1. 프로젝트 개요

- **프로젝트명:** 웹 기반 전기회로 설계 및 시뮬레이터
- **목표:** Eplan 수준의 전기회로 설계가 가능하고 설계 시 AI 기반의 오류 검출 및 수정 제안을 제공하는 웹 애플리케이션 개발
- **주요 기능:**
    - 배전반 설계를 위한 전기회로도 작성 도구 제공
    - 4:3 및 16:9 도면 레이아웃 지원
    - JointJS를 활용한 인터랙티브 회로도 캔버스 구현
    - 캔버스는 확대/축소 기능 제공
    - 회로 구성 요소(저항, 전원, 스위치 등) 드래그 앤 드롭 인터페이스
    - 구성 요소 간 연결 및 회로 구성
    - 회로 시뮬레이션 및 결과 값 표시
    - AI 기반 오류 검출 및 수정 제안
    - 사용자 계정 관리 및 프로젝트 저장 기능
    - 도면 레이아웃 선택 및 사용자 정의 레이아웃 저장 및 출력
    - 다국어 지원 (한국어, 영어 등)
    - 반응형 디자인으로 다양한 기기에서 사용 가능
    - 협업 기능 (실시간 공동 작업, 버전 관리 등)
    - 협업 시 마우스 커서 표시 기능
    - 접근성 준수 (WCAG 가이드라인 따름)
    - KEC 표준 부품 라이브러리 통합
    - IEC 표준 준수 (IEC6113 등)
    - 클라우드 저장소 연동 (예: AWS S3, Google Drive 등)
    - 오프라인 모드 지원 (서비스 워커 활용)
    - 플러그인 아키텍처 도입 (사용자 정의 기능 추가 가능)
    - 고급 검색 및 필터링 기능
    - 통계 및 보고서 생성 기능
    - BOM(자재 명세서) 자동 생성 기능
    - 판넬 보드 설계 기능
    - 부품 XML 내보내기 및 가져오기 기능
    - 부품 XML 편집기 내장
    - AI 기반 부품 추천 시스템
    - 사용자 피드백 수집 및 분석 도구 통합
    - 전기용량 계산기 내장
    - UL 표준 준수

## 2. 기술 스택

- **프론트엔드:** Nuxt, TypeScript, Vite, JointJS
- **백엔드:** Go (Golang)
- **스타일링:** CSS Modules, Tailwind CSS

## 3. 주요 명령어

- **의존성 설치:** `npm install`
- **개발 서버 실행:** `npm run dev`
- **빌드:** `npm run build`
- **테스트:** `npm run test`

## 4. 코딩 컨벤션

- **포맷팅:** Prettier를 사용하여 코드 스타일을 통일합니다.
- **네이밍:**
    - 컴포넌트: PascalCase (`MyComponent.vue`)
    - 변수/함수: camelCase (`calculateVoltage`)
- **커밋 메시지:** Conventional Commits 규칙을 따릅니다. (예: `feat: Add resistor component`)

## 5. 디렉토리 구조

프로젝트는 프론트엔드와 백엔드가 분리된 모노레포 구조를 가정합니다.

### 📁 client (프론트엔드 - Nuxt)

- `client/app/assets`: 빌드 도구(Vite)에 의해 처리될 자산 (CSS, SASS, 글꼴 등)
- `client/app/components`: 자동 임포트되는 Vue 컴포넌트
- `client/app/composables`: 자동 임포트되는 Vue 컴포저블 (Composition API 함수)
- `client/app/layouts`: 페이지의 전체적인 구조를 정의하는 레이아웃
- `client/app/pages`: 파일 기반 라우팅을 위한 페이지 컴포넌트
- `client/middleware`: 페이지 렌더링 전 실행되는 라우트 미들웨어
- `client/plugins`: Vue 앱 초기화 시 실행되는 플러그인
- `client/public`: 빌드 과정 없이 서버 루트에 직접 제공되는 정적 파일
- `client/server/api`: 서버 사이드 API 라우트 (Nuxt 서버 엔진)
- `client/store`: 전역 상태 관리를 위한 Pinia 스토어
- `client/utils`: 자동 임포트되는 유틸리티 함수

### 📁 server (백엔드 - Go)

- `server/cmd/app`: 애플리케이션의 진입점 (main 함수)
- `server/internal/handlers`: HTTP 요청 핸들러
- `server/internal/models`: 데이터베이스 모델 또는 비즈니스 로직에서 사용되는 구조체
- `server/internal/services`: 비즈니스 로직
- `server/pkg/config`: 설정 관리
- `server/pkg/database`: 데이터베이스 연결
- `go.mod`: 의존성 관리 파일

## 6. 기타 선호사항

- 코드 변경 전에는 항상 변경 사항에 대해 한국어로 설명해주세요.
- 새로운 기능 추가 시에는 관련 테스트 코드를 함께 작성해주세요.

## 7. 개발 환경 설정

### 데이터베이스 (Docker)

이 프로젝트는 개발 환경에서 Docker를 사용하여 데이터베이스를 실행합니다. 기술 스택에 명시된 PostgreSQL을 기준으로 합니다.

- **실행 명령어:**
  ```bash
  docker run --name electric-circuit-db -e POSTGRES_PASSWORD=q1w2e3r4 -p 5432:5432 -d postgres
  ```
- **Root 비밀번호:** `q1w2e3r4`

**주의:** 이 설정은 로컬 개발용입니다. 프로덕션 환경에서는 반드시 더 안전한 비밀번호와 설정을 사용해야 합니다.
