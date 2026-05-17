# AI Status Menubar — DMG 배포

OpenAI, Claude, Google Gemini, NotebookLM, xAI Grok 상태를 macOS 메뉴바에서 실시간으로 확인하는 앱의 배포본입니다.

소스 코드: https://github.com/cfcf26/ai-status-menubar

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

## 라이선스 / 책임

- 비공식 배포본입니다. 본 앱은 OpenAI / Anthropic / Google / xAI와 무관합니다
- 각 서비스의 공개 상태 페이지를 polling하여 표시할 뿐, 별도의 API 키나 인증 정보를 사용하지 않습니다
- 사용 중 발생하는 문제에 대해 배포자는 책임지지 않습니다
