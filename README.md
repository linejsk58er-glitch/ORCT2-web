# ORCT2-web (한글 폰트 수정 + GitHub Actions)

포크 후 Actions 탭에서 `Build ORCT2-web`이 돌면:
- 이미지: `ghcr.io/<내계정>/<레포>:latest`
  `docker run -p 8080:8080 ghcr.io/<내계정>/<레포>:latest`
- 정적 파일: 실행 결과의 `orct2-web-www` artifact

주의: wasm 스레드 때문에 `Cross-Origin-Opener-Policy: same-origin`,
`Cross-Origin-Embedder-Policy: require-corp` 헤더가 필요해서 GitHub Pages에는 그대로 못 올림
(nginx 이미지나 `tools/server.py`로 서빙).
