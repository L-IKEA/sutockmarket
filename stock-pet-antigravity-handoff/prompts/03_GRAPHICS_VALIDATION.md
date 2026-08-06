# 그래픽을 넣은 뒤 사용할 점검 프롬프트

`src/assets/pets/shuguri/`에 테스트 그래픽과 `manifest.json`을 추가했습니다.

그래픽 파일을 수정하거나 이름을 변경하지 말고 다음만 수행하세요.

1. manifest에 선언된 모든 프레임 경로가 실제로 존재하는지 검사
2. 빈 애니메이션과 누락 프레임 보고
3. 프레임별 이미지 크기 불일치 여부 검사
4. 모든 애니메이션을 Animation Preview에서 재생
5. loop, fps, holdLastFrameMs, nextAnimation 동작 확인
6. idle, happy, veryHappy, sad, shock 상태 전환 확인
7. 문제를 발견하면 원본 그래픽이 아니라 코드 또는 manifest 수정안을 먼저 제안

검사 결과와 수정이 필요한 항목을 표로 정리하고, 사용자 승인 전에는 그래픽이나 manifest를 수정하지 마세요.
