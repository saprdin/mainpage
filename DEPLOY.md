# 배포 메모 — SIA.SYS backrooms hub

- **호스트**: Cloudflare Pages
- **프로젝트**: `sia-backrooms`
- **계정**: Akarollsdev@gmail.com (Account ID `346927369cbc71bc61da7809b3c2524f`)
- **URL**: https://sia-backrooms.pages.dev/
  - 루트 `/` = `index.html` = **3D 백룸 워킹 갤러리 (메인)**
  - `/arcade.html` = 아케이드 GAME SELECT 허브 (보관)
- **GitHub**: https://github.com/saprdin/mainpage (private)

## 재배포 방법
1. 인증 (둘 중 하나 — **토큰을 코드/메모리에 평문 저장하지 말 것**):
   - `npx wrangler login` ← 1회 브라우저 로그인, 이후 토큰 재입력 불필요 (권장)
   - 또는 셸 환경변수로 `CLOUDFLARE_API_TOKEN` 지정
2. 배포:
   ```
   cd Homepage
   npx wrangler pages deploy . --project-name sia-backrooms --branch main
   ```
   - `.assetsignore` 가 `.git` / `.claude` / `*.md` 등을 업로드에서 제외함.

## 알려진 이슈 (배포 환경)
- `arcade.html` 의 `../Game_1`, `../Game_2` 상대경로 → 배포본엔 해당 폴더가 없어 404.
- `index.html`(backrooms) 사진 라이트박스의 `게임 열기`(`../../../Project/DeepHero/...`) → 404.
- 외부 링크(타로 `sia-tarot…workers.dev`, 대시 `sia-backroom-dash.pages.dev`, 소셜)는 정상.
- → 깨지는 상대경로는 배포 주소로 교체하면 됨.
