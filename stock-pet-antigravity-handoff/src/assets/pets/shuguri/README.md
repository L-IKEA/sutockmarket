# 슈구리 그래픽 배치 안내

각 동작 폴더에 준비된 투명 PNG 프레임을 복사하세요.

예:

```text
idle/001.png
idle/002.png
happy/001.png
happy/002.png
veryHappy/001.png
...
```

그다음 `manifest.json`에서 실제 재생 순서대로 경로를 작성하세요.

예:

```json
"happy": {
  "frames": [
    "happy/001.png",
    "happy/002.png",
    "happy/003.png",
    "happy/004.png"
  ],
  "fps": 6,
  "loop": true
}
```

폴더에 있는 파일 전체가 자동 재생되는 구조가 아닙니다. manifest에 포함된 파일만 재생합니다.
