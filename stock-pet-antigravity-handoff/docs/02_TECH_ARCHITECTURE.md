# 02. 기술 아키텍처

## 1. 기술 스택

| 영역 | 기술 |
|---|---|
| 데스크톱 프레임워크 | Tauri 2 |
| UI | React + TypeScript |
| 프런트 빌드 | Vite |
| 네이티브 계층 | Rust |
| HTTP | reqwest |
| 직렬화 | Serde / serde_json |
| 일반 설정 | Tauri Store |
| 비밀정보 | Tauri Stronghold 또는 OS 보안 저장소 |
| 창 상태 | Tauri Window State |
| 자동 실행 | Tauri Autostart |
| 프런트 테스트 | Vitest |
| Rust 테스트 | cargo test |

프로젝트 생성 시 안정 버전을 사용하고 `package-lock.json`과 `Cargo.lock`을 커밋한다.

## 2. 구조

```text
StockProvider
  ├─ MockStockProvider
  └─ RealStockProvider
          ↓
StockSnapshot
          ↓
PetStateMachine
          ↓
PetState / PetEvent
          ↓
Animation Mapping
          ↓
Manifest-based AnimationPlayer
          ↓
Transparent Tauri Window
```

## 3. 역할

### React

- 프레임 애니메이션 재생
- 펫 화면
- 설정 화면
- 애니메이션 미리보기
- Mock 제어판

### Rust

- Tauri 창과 트레이
- 실제 API 통신
- 인증정보 보호
- 설정 파일 처리
- 데이터 제공자 구현
- 네이티브 오류 처리

### 상태 머신

- 등락률을 기본 상태로 변환
- 직전 데이터와 비교해 순간 이벤트 생성
- 우선순위 처리
- 이벤트 종료 후 기본 상태 복귀

## 4. 데이터 제공자 인터페이스

실제 API에 앱 전체가 결합되지 않도록 한다.

```rust
pub trait StockProvider {
    async fn get_quote(
        &self,
        symbol: &str,
    ) -> Result<StockSnapshot, StockError>;
}
```

Mock과 실제 제공자는 동일한 `StockSnapshot`을 반환한다.

## 5. 설정 구조 예시

```ts
export type AppSettings = {
  schemaVersion: number;
  stock: {
    market: "KR";
    symbol: string;
    companyName: string;
  };
  reaction: {
    strongDown: number;
    down: number;
    up: number;
    strongUp: number;
    suddenChangeRate: number;
    eventDurationSeconds: number;
  };
  pet: {
    petId: string;
    scale: number;
    animationSpeedMultiplier: number;
    speechBubbleEnabled: boolean;
    soundEnabled: boolean;
  };
  window: {
    alwaysOnTop: boolean;
    clickThrough: boolean;
    opacity: number;
    positionX: number;
    positionY: number;
  };
  data: {
    refreshIntervalSeconds: 30 | 60 | 180 | 300;
    provider: "mock" | "real";
  };
};
```

## 6. 보안

- `.env`, 인증 파일, 토큰 파일을 Git에서 제외한다.
- API 키를 React 번들에 포함하지 않는다.
- 로그에 토큰과 키를 출력하지 않는다.
- 실제 주문 API를 사용하지 않는다.
- 프로젝트 루트 밖 파일 접근을 요구하지 않는다.

## 7. 성능 목표

- 앱 실행 후 펫 표시 5초 이내
- 대기 CPU 평균 5% 이하
- 메모리 300MB 이하
- API 요청 중 프레임 재생 중단 없음
