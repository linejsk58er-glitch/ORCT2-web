# ORCT2-web (한글 폰트 수정 + GitHub Actions)

포크 후 Actions 탭에서 `Build ORCT2-web`이 돌면:
- 이미지: `ghcr.io/<내계정>/<레포>:latest`
  `docker run -p 8080:8080 ghcr.io/<내계정>/<레포>:latest`
- 정적 파일: 실행 결과의 `orct2-web-www` artifact

주의: wasm 스레드 때문에 `Cross-Origin-Opener-Policy: same-origin`,
`Cross-Origin-Embedder-Policy: require-corp` 헤더가 필요해서 GitHub Pages에는 그대로 못 올림
(nginx 이미지나 `tools/server.py`로 서빙).

## RCT2 파일을 zip 하나로 올리기 (아이패드 등 폴더 선택이 안 되는 기기용)

첫 화면에 폴더 선택 외에 **".zip 선택"** 칸이 추가됐어요.

1. PC에서 RCT2 폴더(또는 `Data`, `ObjData`, `Scenarios`, `Tracks` 폴더들)를 우클릭 → 압축해서 zip 하나로 만들기
   - 압축 파일 안에 폴더가 통째로 들어 있어도 되고, 내용물만 있어도 돼요 (`Data/ch.dat`만 찾을 수 있으면 OK)
2. zip을 기기로 옮기기 (아이패드는 에어드롭/iCloud 등으로 "파일" 앱에 넣기)
3. 사이트에서 ".zip 선택" → 파일 고르기. 한 파일씩 풀어서 바로 저장하니까 zip 전체가 메모리에 올라가지 않아요.

지원 안 하는 것: 비밀번호 걸린 zip, 4GB가 넘는 zip(zip64).

이미 배포한 서버는 `resources/index.html`과 `resources/fflate.min.js` 두 파일만 덮어쓰면 돼요(재빌드 불필요).
