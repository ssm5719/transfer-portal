# 코스모스 트랜스퍼 · 디자인 개선안

정적 파일만 있어서 빌드가 필요 없어요.

## 들어 있는 파일
- `index.html`: 목차
- `line-height.html`: 행간 개선 비교
- `hero.html`: 히어로 배경 정리
- `navigation.html`: 내비게이션 구조 개선
- `top-button.html`: 맨 위로 버튼
- `docs/line-height-guide.md`: 세 페이지 행간 가이드

## 배포 (GitHub → Vercel)
1. 이 폴더 내용을 새 GitHub 저장소 루트에 올려요.
   ```bash
   git init && git add . && git commit -m "design proposals"
   git branch -M main
   git remote add origin <저장소 URL>
   git push -u origin main
   ```
2. Vercel → Add New → Project에서 해당 저장소를 Import 해요.
3. 설정은 다음과 같이 해요.
   - Framework Preset: **Other**
   - Build Command: 비움
   - Output Directory: 비움
4. Deploy를 누르면 생성된 URL을 Slack에 공유하면 돼요.

## 업데이트할 때
새로 받은 파일로 덮어쓰고 push 하면 Vercel이 자동으로 다시 배포해요.
