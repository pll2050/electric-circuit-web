# Electric Circuit Web

웹 기반 전기회로 설계 및 시뮬레이터

## 프로젝트 개요

Eplan 수준의 전기회로 설계가 가능하고 설계 시 AI 기반의 오류 검출 및 수정 제안을 제공하는 웹 애플리케이션입니다.

## 프로젝트 구조 (서브모듈 방식)

이 프로젝트는 다음과 같은 구조로 구성되어 있습니다:

- **메인 저장소**: 프로젝트 전체 관리 및 문서
- **클라이언트 서브모듈**: Nuxt.js + Vue.js + TypeScript 프론트엔드
- **서버 서브모듈**: Go + Gin 백엔드

### 서브모듈 설정

#### 초기 클론

```bash
# 메인 저장소 클론 (서브모듈 포함)
git clone --recursive [main-repo-url]

# 또는 기본 클론 후 서브모듈 초기화
git clone [main-repo-url]
cd electric_circuit_web
git submodule init
git submodule update
```

#### 서브모듈 업데이트

```bash
# 모든 서브모듈을 최신 커밋으로 업데이트
git submodule update --remote

# 특정 서브모듈만 업데이트
git submodule update --remote client
git submodule update --remote server
```

#### 서브모듈에서 작업하기

```bash
# 클라이언트 폴더로 이동하여 작업
cd client
git checkout main  # 또는 작업할 브랜치
# 작업 수행 후
git add .
git commit -m "클라이언트 변경사항"
git push origin main

# 메인 저장소로 돌아가서 서브모듈 참조 업데이트
cd ..
git add client
git commit -m "클라이언트 서브모듈 업데이트"
git push
```

## 기술 스택

### 프론트엔드
- **Nuxt 3** - Vue.js 기반 풀스택 프레임워크
- **TypeScript** - 타입 안정성
- **Tailwind CSS** - 유틸리티 우선 CSS 프레임워크
- **@joint/plus** - 인터랙티브 다이어그램 및 회로도 구현 (프리미엄 기능 포함)
  > **⚠️ 중요**: @joint/core를 직접 사용하지 말고 항상 @joint/plus를 사용할 것
- **Babylon.js** - 3D 그래픽 렌더링 및 판넬 보드 시각화
- **Pinia** - 상태 관리

### 백엔드
- **Go (Golang)** - 고성능 백엔드 서버
- **PostgreSQL** - 데이터베이스

## 시작하기

### 필요 환경

- Node.js 18.x 이상
- Go 1.21 이상
- Docker (데이터베이스용)

### 데이터베이스 설정

```bash
docker run --name electric-circuit-db -e POSTGRES_PASSWORD=q1w2e3r4 -p 5432:5432 -d postgres
```

데이터베이스 생성:
```bash
docker exec -it electric-circuit-db psql -U postgres -c "CREATE DATABASE electric_circuit;"
```

### 프론트엔드 실행

```bash
cd client
npm install
npm run dev
```

프론트엔드는 http://localhost:3000 에서 실행됩니다.

### 백엔드 실행

```bash
cd server
go mod download
go run cmd/app/main.go
```

백엔드는 http://localhost:8080 에서 실행됩니다.

## 프로젝트 구조

```
electric_circuit_web/
├── client/              # Nuxt 프론트엔드
│   ├── app/
│   │   ├── assets/      # CSS, 이미지 등
│   │   ├── components/  # Vue 컴포넌트
│   │   ├── composables/ # Composition API 함수
│   │   ├── layouts/     # 레이아웃
│   │   └── pages/       # 페이지 라우트
│   ├── middleware/      # 라우트 미들웨어
│   ├── plugins/         # Vue 플러그인
│   ├── public/          # 정적 파일
│   ├── store/           # Pinia 스토어
│   └── utils/           # 유틸리티 함수
│
├── server/              # Go 백엔드
│   ├── cmd/app/         # 애플리케이션 진입점
│   ├── internal/
│   │   ├── handlers/    # HTTP 핸들러
│   │   ├── models/      # 데이터 모델
│   │   └── services/    # 비즈니스 로직
│   └── pkg/
│       ├── config/      # 설정 관리
│       └── database/    # 데이터베이스 연결
│
├── CLAUDE.md            # Claude AI 컨텍스트 문서
└── README.md            # 프로젝트 문서
```

## 주요 기능

- 배전반 설계를 위한 전기회로도 작성 도구
- 4:3 및 16:9 도면 레이아웃 지원
- 드래그 앤 드롭 인터페이스
- 회로 시뮬레이션 및 결과 표시
- AI 기반 오류 검출 및 수정 제안
- 실시간 협업 기능
- BOM(자재 명세서) 자동 생성
- 판넬 보드 3D 시각화
- KEC, IEC, UL 표준 준수

## 코딩 컨벤션

- **컴포넌트**: PascalCase (예: `MyComponent.vue`)
- **변수/함수**: camelCase (예: `calculateVoltage`)
- **커밋 메시지**: Conventional Commits (예: `feat: Add resistor component`)
- **포맷팅**: Prettier를 사용하여 코드 스타일 통일

## 라이선스

이 프로젝트는 비공개 프로젝트입니다.

## 문의

프로젝트 관련 문의사항이 있으시면 이슈를 생성해주세요.


## 향후 계획
- 도면 탬플릿 생성 및 관리 기능
- vjs 기반 실시간 협업 기능
