# 03. 애니메이션 그래픽 규격

## 1. 핵심 원칙

그래픽은 계속 변경될 수 있다. 따라서 프레임 개수, 파일명, 재생 속도를 코드에 하드코딩하지 않는다.

단일 진실 공급원은 아래 파일이다.

```text
src/assets/pets/shuguri/manifest.json
```

## 2. 폴더

```text
src/assets/pets/shuguri/
├─ manifest.json
├─ thumbnail.png
├─ idle/
├─ happy/
├─ veryHappy/
├─ sad/
├─ shock/
├─ sleep/
└─ error/
```

준비되지 않은 애니메이션 폴더는 비어 있어도 된다. 단, `idle`은 반드시 최소 1프레임을 가져야 한다.

## 3. 프레임 규칙

- 투명 PNG
- 모든 프레임 동일 캔버스 크기
- 발 기준선과 중심점 통일
- 파일명은 `001.png`, `002.png`처럼 세 자리 권장
- 실제 재생 순서는 파일명 정렬이 아니라 manifest 배열 순서
- 원본 이미지를 코드나 빌드 스크립트가 자동 수정하지 않음

## 4. 매니페스트 예시

```json
{
  "schemaVersion": 1,
  "petId": "shuguri",
  "displayName": "슈구리",
  "canvas": {
    "width": 512,
    "height": 512
  },
  "defaultAnimation": "idle",
  "animations": {
    "idle": {
      "frames": [
        "idle/001.png"
      ],
      "fps": 3,
      "loop": true
    },
    "happy": {
      "frames": [
        "happy/001.png",
        "happy/002.png",
        "happy/003.png",
        "happy/004.png"
      ],
      "fps": 6,
      "loop": true
    },
    "shock": {
      "frames": [
        "shock/001.png",
        "shock/002.png"
      ],
      "fps": 8,
      "loop": false,
      "holdLastFrameMs": 500,
      "nextAnimation": "sad"
    }
  }
}
```

## 5. 변경 방법

### 프레임 추가

1. PNG를 해당 폴더에 추가
2. manifest의 `frames` 배열 원하는 위치에 경로 추가
3. 미리보기 화면에서 확인
4. 테스트 실행

### 프레임 제거

1. manifest의 배열에서 먼저 경로 제거
2. 미리보기 확인
3. 더 이상 사용하지 않을 때 파일 삭제

### 프레임 교체

같은 경로의 PNG를 교체하면 코드 변경은 없다. 브라우저 캐시 또는 개발 서버 캐시가 남을 경우 재시작한다.

## 6. 오류 복구

- 특정 프레임 누락: 해당 프레임 건너뛰기 및 경고
- 빈 애니메이션: `idle`로 대체
- `idle` 누락: 정적 fallback 이미지 표시
- 매니페스트 파싱 실패: 앱 종료 금지, 오류 화면과 로그 제공
- 잘못된 FPS: 기본값 3 적용 또는 검증 실패 표시

## 7. Animation Preview 필수 기능

- 애니메이션 선택
- 재생/정지
- 반복 여부 표시
- 현재 프레임/전체 프레임
- 한 프레임씩 이동
- FPS 표시
- 배경 격자 또는 밝기 전환
- 누락 파일 경고
- 상태별 전환 버튼
