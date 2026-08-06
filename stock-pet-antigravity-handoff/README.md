# Stock Pet / 슈구리 주가 반응형 데스크톱 펫

이 저장소는 회사 주가 변화에 따라 캐릭터 애니메이션이 달라지는 Windows 데스크톱 펫 앱을 개발하기 위한 프로젝트입니다.

## 가장 중요한 원칙

1. 애니메이션 프레임 수와 파일명을 코드에 하드코딩하지 않습니다.
2. 모든 애니메이션은 `manifest.json`의 실제 프레임 목록을 기준으로 재생합니다.
3. 실제 주가 API보다 Mock 데이터와 애니메이션 플레이어를 먼저 완성합니다.
4. API 키·토큰·계좌정보를 저장소에 커밋하지 않습니다.
5. 한 번에 전체 앱을 만들지 않고 문서의 단계별 개발 계획을 따릅니다.
6. 기존 그래픽 파일을 임의로 수정·삭제·이름 변경하지 않습니다.
7. 계획, 구현, 테스트 결과를 각 단계 종료 시 문서화합니다.

## 먼저 읽을 문서

1. `AGENTS.md`
2. `docs/01_PRODUCT_REQUIREMENTS.md`
3. `docs/02_TECH_ARCHITECTURE.md`
4. `docs/03_ANIMATION_ASSET_SPEC.md`
5. `docs/04_DEVELOPMENT_PLAN.md`
6. `docs/05_TEST_CHECKLIST.md`

## 그래픽 넣는 위치

준비한 투명 PNG 프레임을 다음 폴더에 넣습니다.

```text
src/assets/pets/shuguri/
├─ idle/
├─ happy/
├─ veryHappy/
├─ sad/
├─ shock/
├─ sleep/
└─ error/
```

각 폴더에 프레임을 넣은 뒤 `src/assets/pets/shuguri/manifest.json`의 `frames` 배열에 실제 경로와 순서를 작성합니다.

## 첫 개발 범위

Phase 1에서는 다음만 구현합니다.

- Tauri 2 + React + TypeScript + Vite 프로젝트
- Windows용 투명 데스크톱 펫 창
- 매니페스트 기반 PNG 프레임 애니메이션 플레이어
- 애니메이션 미리보기 화면
- Mock 주가 상태 버튼
- 상태별 애니메이션 전환
- 프레임 누락 시 안전한 대체 처리
- 관련 단위 테스트

실제 증권 API 연동은 Phase 5 전에는 진행하지 않습니다.
