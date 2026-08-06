# Antigravity 첫 대화에 그대로 붙여넣을 프롬프트

이 프로젝트는 Windows용 주가 반응형 데스크톱 펫 앱입니다.

먼저 다음 파일을 순서대로 읽으세요.

1. `AGENTS.md`
2. `docs/01_PRODUCT_REQUIREMENTS.md`
3. `docs/02_TECH_ARCHITECTURE.md`
4. `docs/03_ANIMATION_ASSET_SPEC.md`
5. `docs/04_DEVELOPMENT_PLAN.md`
6. `docs/05_TEST_CHECKLIST.md`
7. `.agents/skills/stock-pet-development/SKILL.md`

현재는 **Phase 1만** 진행합니다. 실제 주가 API는 연결하지 마세요.

Phase 1 목표:

- Tauri 2 + React + TypeScript + Vite 프로젝트 골격
- Windows 투명 펫 창
- `manifest.json` 기반 PNG 프레임 애니메이션 플레이어
- 애니메이션 미리보기 화면
- Mock 주가 상태 버튼
- 상태별 애니메이션 전환
- 누락·빈 프레임에 대한 안전한 fallback
- Vitest 및 Rust 단위 테스트

중요 제약:

- 프레임 수와 파일명을 코드에 하드코딩하지 마세요.
- 사용자 그래픽을 수정·삭제·이름 변경하지 마세요.
- 프로젝트 폴더 밖의 파일에 접근하지 마세요.
- 삭제 명령을 실행하지 마세요.
- API 키나 토큰을 만들거나 요청하지 마세요.
- Phase 2 이상의 기능은 구현하지 마세요.
- 먼저 현재 그래픽 폴더와 manifest 상태를 검사하세요.
- 그래픽이 아직 비어 있거나 manifest가 완성되지 않았다면, 원본 파일을 만들지 말고 명확한 placeholder/fallback 구조로 진행하세요.

지금은 코드를 작성하지 말고 먼저 **Implementation Plan Artifact**를 작성해 주세요.

계획에는 반드시 다음을 포함하세요.

1. 생성·수정할 파일 목록
2. 컴포넌트 및 모듈 구조
3. manifest 로딩과 검증 방식
4. 프레임 재생 타이머 정리 방식
5. 투명 창 구현 방식
6. Mock 상태와 애니메이션 매핑
7. 오류 및 fallback 처리
8. 실행할 테스트와 빌드 명령
9. Phase 1 완료 조건
10. 이번 단계에서 구현하지 않을 항목

계획을 제시한 뒤 사용자 승인 전에는 파일을 수정하지 마세요.
