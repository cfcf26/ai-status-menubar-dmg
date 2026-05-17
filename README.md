# AI Status Menubar — DMG 배포

OpenAI, Claude, Google Gemini, NotebookLM, xAI Grok 상태를 macOS 메뉴바에서 실시간으로 확인하는 앱의 배포본입니다.

소스 코드: https://github.com/cfcf26/ai-status-menubar

> ## ⚠️ 알파(Alpha) 버전 안내
>
> 이 앱은 **알파 단계**입니다. 핵심 기능은 동작하지만:
>
> - 일부 상태 페이지의 응답 포맷이 바뀌면 일시적으로 회색(확인 불가)으로 표시될 수 있습니다
> - 메뉴바 아이콘, 환경설정 UI, 알림 동작 등은 피드백을 받아 자주 바뀝니다
> - 공식 서명(Developer ID) 및 공증(Notarization)이 적용되지 않아 첫 실행 시 Gatekeeper를 수동으로 우회해야 합니다
> - 자동 업데이트 기능이 없습니다 — 새 버전은 이 레포에서 직접 다운로드하셔야 합니다
>
> 사용 중 문제가 생기면 아래 [버그 / 개선 제안 남기기](#버그--개선-제안-남기기) 섹션을 참고해 GitHub Issue로 알려주세요.

---

## 다운로드

[**AIStatusMenubar.dmg**](./AIStatusMenubar.dmg) (약 500 KB)

또는 터미널에서:

```bash
curl -L -o AIStatusMenubar.dmg https://github.com/cfcf26/ai-status-menubar-dmg/raw/main/AIStatusMenubar.dmg
```

---

## 시스템 요구사항

| 항목 | 요구사항 |
|---|---|
| CPU | **Apple Silicon (arm64)** — M1/M2/M3/M4 |
| macOS | **13 Ventura 이상** (15 Sequoia 권장) |
| 네트워크 | statuspage.io, google.com, x.ai 접근 가능 |

> Intel Mac은 지원하지 않습니다.

---

## 설치 방법

### 1. DMG 마운트 후 앱 복사

1. `AIStatusMenubar.dmg` 더블클릭으로 마운트
2. `AIStatusMenubar.app`을 `/Applications` 폴더로 드래그
3. DMG 언마운트

### 2. 첫 실행 — Gatekeeper 우회

이 앱은 **ad-hoc 서명**이라 처음 실행 시 macOS가 한 번 막습니다. 우회 방법:

#### macOS 15 Sequoia
1. `/Applications/AIStatusMenubar.app` 더블클릭 → "확인되지 않은 개발자" 알림 닫기
2. **시스템 설정 → 개인정보 보호 및 보안** 열기
3. 아래로 스크롤 → "**AIStatusMenubar.app이 차단되었습니다**" 옆 **"확인 없이 열기"** 클릭
4. 다시 한 번 확인 다이얼로그에서 **"열기"**

#### macOS 13–14
1. Finder에서 `AIStatusMenubar.app`을 **우클릭 → 열기**
2. 경고 다이얼로그에서 **"열기"** 클릭

### 3. 알림 권한 허용

- 환경설정에서 "상태 변경 시 알림" 토글 켜면 권한 다이얼로그가 뜹니다 → **"허용"**
- 거부했다면 시스템 설정 → 알림 → AIStatusMenubar에서 직접 허용

### 4. 로그인 시 자동 시작 (선택)

환경설정 → 일반 → "로그인 시 자동 시작" 토글

---

## 사용법

설치 후 메뉴바 우측 상단에 컬러 캡슐(초록/노랑/주황/빨강)이 나타납니다.

- **메뉴바 아이콘 클릭** → 5개 서비스 상태 팝오버
- **각 서비스 행 클릭** → 해당 공식 상태 페이지를 브라우저에서 열기
- **환경설정**에서 폴링 주기, 서비스 순서, 상세 모드(component 단위 표시), 알림 등을 조정할 수 있습니다

### 색상 의미

| 색 | 상태 |
|---|---|
| 🟢 초록 | 정상 |
| 🟡 노랑 | 일부 저하 |
| 🟠 주황 | 주요 장애 |
| 🔴 빨강 | 심각한 장애 |
| ⚪ 회색 | 점검 중 / 확인 불가 |

---

## 문제 해결

| 증상 | 해결 |
|---|---|
| "손상되었습니다" 표시 | 터미널에서 `xattr -dr com.apple.quarantine /Applications/AIStatusMenubar.app` 실행 |
| 메뉴바 아이콘 안 보임 | 메뉴바 공간 부족 — Bartender 등 메뉴바 관리 앱에서 확인 |
| 모두 회색 (확인 불가) | 네트워크 / 방화벽 확인. 환경설정에서 "새로고침" |
| 알림이 안 옴 | 시스템 설정 → 알림 → AIStatusMenubar 허용 확인 |

---

## 버그 / 개선 제안 남기기

알파 단계이므로 **사용자 피드백이 가장 중요합니다.** 버그를 발견했거나 개선 아이디어가 있다면 GitHub Issue로 남겨주세요.

### 이슈 등록 페이지

👉 **https://github.com/cfcf26/ai-status-menubar/issues/new**

(앱 소스 레포의 이슈 트래커입니다. 이 DMG 레포가 아니라 **`ai-status-menubar`** 레포로 들어가는 점에 유의하세요.)

### 등록 방법

1. 위 링크 클릭 → GitHub 로그인 (계정 없으면 무료 가입)
2. **Title** — 한 줄 요약 (예: "메뉴바 아이콘이 초록인데 OpenAI는 장애 상태")
3. **Write 탭** 본문에 아래 템플릿을 복사해 채워주세요:

````markdown
## 증상
무엇이 잘못되었는지 한두 문장으로 설명

## 재현 방법
1. ...
2. ...
3. ...

## 예상한 동작
이렇게 되어야 한다고 생각했는데...

## 실제 동작
실제로는 이렇게 되었습니다...

## 환경
- macOS 버전: (예: 15.7.4 Sequoia)
- CPU: (예: Apple Silicon M2)
- 앱 버전 / 다운로드 시점: (예: 2026-05-17 다운로드)

## 스크린샷 / 로그 (있으면)
이미지를 본문에 드래그&드롭하면 자동으로 첨부됩니다.
````

4. **Submit new issue** 클릭

### 좋은 이슈를 작성하는 팁

- **재현 가능한 절차**가 가장 큰 도움이 됩니다 ("뭘 클릭하니 뭐가 일어났다" 순서대로)
- 화면 상태가 이상하다면 **스크린샷**을 첨부해주세요 (`Cmd+Shift+4`로 영역 캡처 후 본문에 드래그)
- 메뉴바 아이콘을 클릭한 팝오버에 보이는 **각 서비스의 메시지**도 같이 적어주시면 좋습니다
- 콘솔 로그가 필요한 경우: 터미널에서 `log show --predicate 'subsystem == "AIStatusMenubar"' --last 1h` 실행 후 결과 첨부

### 보안 / 민감 이슈

공개 이슈로 올리기 어려운 보안 관련 제보는 이슈 대신 이메일(소스 레포 README 참고)로 부탁드립니다.

---

## 라이선스 / 책임

- 비공식 배포본입니다. 본 앱은 OpenAI / Anthropic / Google / xAI와 무관합니다
- 각 서비스의 공개 상태 페이지를 polling하여 표시할 뿐, 별도의 API 키나 인증 정보를 사용하지 않습니다
- 사용 중 발생하는 문제에 대해 배포자는 책임지지 않습니다
