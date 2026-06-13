# 마운로그 💉

마운자로(터제파타이드) 투약과 체중 감량을 기록하는 개인용 다이어리.
**서버 없이** 브라우저 안(IndexedDB)에 데이터를 저장합니다.

## 기능
- 💉 **주사 기록** — 용량(2.5/5/10mg) 선택, 정확한 투약 일시, 메모. 주간 일정 설정 시 다음 주사일 표시
- ⚖️ **몸무게** — 아침/저녁 따로 기록
- 🏃 **운동** — 운동 여부 + 종류 선택(편집 가능)
- 🍽️ **식사** — 아침/점심/저녁 사진 + 시간 (사진 자동 압축, ~720px/품질 0.55로 작게 저장)
- 🤢 **부작용** — 체크 + 메모
- 📈 **그래프** — 아침/저녁 체중 추이, 기간별 변화·최저 기록
- 📔 **오늘의 일기**
- 💾 **백업/복원** — JSON 파일로 내보내기·불러오기

## 로컬에서 바로 쓰기
`index.html`을 더블클릭하면 브라우저에서 바로 열립니다.
(파일 직접 열기에서는 PWA 설치/오프라인 캐시만 비활성화되고, 나머지 기능은 모두 동작합니다.)

## GitHub Pages에 올리기 (폰에서 앱처럼 쓰기)
1. GitHub에서 새 저장소(repository) 생성 — 예: `mounjaro-diary`
2. 이 폴더의 파일들을 푸시:
   ```bash
   cd mounjaro-diary
   git init
   git add .
   git commit -m "마운로그 v1"
   git branch -M main
   git remote add origin https://github.com/<your-id>/mounjaro-diary.git
   git push -u origin main
   ```
3. 저장소 **Settings → Pages → Branch: `main` / `/ (root)`** 선택 후 저장
4. 1~2분 뒤 `https://<your-id>.github.io/mounjaro-diary/` 접속
5. 폰 브라우저에서 열고 **"홈 화면에 추가"** → 앱 아이콘으로 실행 (오프라인에서도 동작)

> ⚠️ 데이터는 **접속한 그 브라우저 안에만** 저장됩니다. 기기/브라우저를 바꾸면 보이지 않으며,
> 브라우저 데이터를 지우면 기록도 사라집니다. **설정 → 백업**으로 가끔 파일을 받아두세요.

## 데이터 저장 방식
- 기록/주사: IndexedDB `entries`, `shots` 스토어
- 식사 사진: IndexedDB `photos` 스토어 (압축된 JPEG data URL)
- 설정(주사 일정·운동 종류): localStorage
