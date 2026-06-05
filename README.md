# 광탄중학교 챗봇 프렌 🌿

Microsoft Copilot Studio로 만든 학교 챗봇 **'프렌'** 을 학생들이 편하게 쓸 수 있도록 파스텔톤으로 디자인한 웹 페이지입니다. 별도의 빌드 과정 없이 `index.html` 파일 하나로 동작합니다.

> 궁금한 건 무엇이든 편하게 물어보세요 :)

---

## ✨ 주요 특징

- **단일 파일 구성** — `index.html` 하나만 있으면 됩니다. 서버나 빌드 도구가 필요 없어요.
- **파스텔톤 디자인** — 민트·하늘·복숭아·라벤더 색을 사용한 부드럽고 산뜻한 분위기.
- **둥근 한글 폰트** — Google Fonts의 `Gowun Dodum`(본문), `Jua`(제목) 적용.
- **글자 아바타** — 봇은 '프렌', 사용자는 '나'로 표시.
- **반응형** — PC와 모바일 화면 모두 자연스럽게 보입니다.
- **자동 인사말** — 대화가 시작되면 챗봇이 먼저 말을 겁니다.

---

## 🛠 기술 스택

- [Microsoft Copilot Studio](https://copilotstudio.microsoft.com/) — 챗봇 본체
- [Bot Framework Web Chat](https://github.com/microsoft/BotFramework-WebChat) — 채팅 화면(커스텀 캔버스)
- HTML / CSS / JavaScript (프레임워크 없음)
- Google Fonts (Gowun Dodum, Jua)

---

## 🚀 GitHub Pages로 배포하기

이 레포지토리를 그대로 웹사이트로 띄울 수 있습니다.

1. 레포지토리 상단의 **Settings** 클릭
2. 왼쪽 메뉴에서 **Pages** 선택
3. **Build and deployment** → **Source** 를 `Deploy from a branch` 로 설정
4. **Branch** 를 `main`(또는 사용 중인 브랜치) / `/(root)` 로 지정 후 **Save**
5. 잠시 후 표시되는 주소(`https://<사용자명>.github.io/<레포지토리명>/`)로 접속하면 챗봇이 열립니다.

> `index.html` 이 레포지토리 최상위(root)에 있어야 바로 인식됩니다.

---

## ⚙️ 설정 (토큰 엔드포인트)

챗봇이 작동하려면 Copilot Studio에서 발급한 **토큰 엔드포인트**가 필요합니다. 이미 `index.html` 안에 입력되어 있으며, 다른 챗봇으로 바꾸려면 아래 부분을 수정하세요.

```javascript
const tokenEndpoint = "여기에_토큰_엔드포인트_주소";
```

**토큰 엔드포인트 가져오는 방법**

1. Copilot Studio에서 해당 챗봇 열기
2. **설정(Settings) → 채널(Channels)** 이동
3. **모바일 앱(Mobile app)** 또는 **이메일(Email)** 선택
4. **Token Endpoint** 옆 **복사(Copy)** 클릭
5. 복사한 주소를 위 코드의 따옴표 안에 붙여넣기

> 이 토큰 엔드포인트는 짧은 수명의 접속용 토큰을 발급하는 용도라, 웹 페이지(클라이언트) 코드에 들어가는 것이 정상적인 방식입니다.

---

## 🎨 디자인 커스터마이징

### 챗봇 내부 색상

`index.html` 안의 `styleOptions` 객체에서 색상 코드(`#RRGGBB`)만 바꾸면 됩니다.

| 항목 | 변수 |
|------|------|
| 강조색 | `accent` |
| 봇 말풍선 | `bubbleBackground`, `bubbleTextColor`, `bubbleBorderColor` |
| 사용자 말풍선 | `bubbleFromUserBackground`, `bubbleFromUserTextColor` |
| 보내기 버튼 | `sendBoxButtonColor` |
| 추천 질문 버튼 | `suggestedActionBackgroundColor`, `suggestedActionBorderColor` |
| 아바타 | `botAvatarBackgroundColor`, `userAvatarBackgroundColor` |

### 페이지 헤더 / 색상 팔레트

페이지 상단 제목, 설명 문구, 전체 파스텔 팔레트는 `<style>` 영역의 `:root` 변수와 `header` 부분에서 수정합니다.

```css
:root {
  --mint:  #C5EDE0;
  --sky:   #C7E6F5;
  --peach: #FCE0CE;
  --lav:   #E5D8F4;
}
```

### 제목 / 폰트

- 제목 문구: `<h1>광탄중학교 챗봇 프렌</h1>` 수정
- 폰트: `<head>`의 Google Fonts 링크와 `primaryFont` / `font-family` 값 수정

---

## 🩺 문제 해결

| 증상 | 확인할 점 |
|------|-----------|
| 챗봇이 안 뜨고 "불러오지 못했어요" 표시 | 챗봇이 **게시(Publish)** 되었는지, 토큰 엔드포인트 주소가 정확한지 확인 |
| 빈 화면 / 응답 없음 | 브라우저 `F12` → **Console** 탭에서 빨간 에러 메시지 확인 |
| 폰트가 기본 글꼴로 보임 | 인터넷 연결 상태 확인 (Google Fonts 로딩 필요) |

---

## 📄 라이선스 및 참고

- 챗봇 연결 코드는 [Microsoft Copilot Studio 공식 문서](https://learn.microsoft.com/microsoft-copilot-studio/customize-default-canvas)의 커스텀 캔버스 샘플을 기반으로 합니다.
- 샘플 코드는 "있는 그대로(as is)" 제공되며 Copilot Studio와 함께 사용하는 용도로만 허용됩니다.
