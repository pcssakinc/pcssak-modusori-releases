# PCssak ModuSori 0.1.2 — Free Early Access

PCssak ModuSori 0.1.2 is an urgent layout patch for the application-wide vertical scrolling
failure reported after 0.1.1. At enlarged interface scales, content below the visible window
could be clipped while the shared Dictation, Live Subtitles, File Transcription, and Meeting
Notes area had no usable vertical scrollbar.

This patch does not change speech recognition, Free 0.1.x limits, the model catalogue, supported
platforms, network behavior, or the unsigned-installer disclosure. The EULA and Privacy Notice
identify the reviewed build as 0.1.2 with document version `0.1.2-2026-08-27`; their policy terms
are unchanged. Existing installations must review the embedded documents again because their
version and hash changed.

## What changed in 0.1.2

- The application root now has an explicit finite width and height matching the WebView.
- Interface scaling now uses Tauri/WebView2 native page zoom instead of CSS `zoom`, so the layout
  viewport, responsive breakpoints, and viewport-sized dialogs change together.
- Conflicting full-screen height utilities were removed from the scaled boot, legal-consent, and
  ready application shells.
- All four feature tabs remain inside one finite, vertically scrollable main-content region.
- The main-content region is keyboard-focusable, has a visible focus ring, and has an accessible
  name in all nine UI languages.
- Boot content follows the finite scaled parent height instead of requesting a second full
  viewport height.

The default interface scale remains 110%, with 100%, 125%, and 150% still available in Settings.
The independent Live Subtitles overlay font-size control is not changed by this patch.

## Why the failure occurred

CSS `zoom` enlarged the visual interface while the scaled root used a percentage-based height.
Because its ancestor height was not explicitly finite, that percentage could resolve as an
automatic content height. The root then grew below the WebView instead of making the inner
`main` element overflow. It also left CSS media queries on the unscaled viewport and enlarged
`vh`-sized dialogs a second time. The outer page intentionally hides overflow, so lower controls
could be clipped with no usable page scrollbar.

Version 0.1.2 gives the shell a finite height and delegates interface scaling to the native
WebView zoom API rather than adding separate scrollbars to each feature tab. This keeps
navigation, responsive layouts, active-capture banners, dialogs, and footer behavior consistent
across the application. The zoom permission is restricted to the main WebView; the independent
Live Subtitles overlay remains unchanged.

## Free 0.1.x limits

| Function | Limit |
| --- | --- |
| Users and seats | No limit |
| Whisper models | Tiny, Base, Small, Medium, and Large-v3 Turbo |
| File transcription | Up to 15 minutes per file |
| Dictation | 15 uses per local calendar day |
| Live captions | Five minutes per session; a new session may be started |
| Meeting notes | Three summaries per local calendar day |
| English translation | Not available |

No paid plan, payment, or paid licence is currently offered. Speaker diarization and a local
generative LLM are not included; meeting notes remain deterministic and extractive.

## Privacy and network boundary

Speech recognition, transcripts, captions, and extractive notes run on the user's device. The
application has no PCSSAK account, advertising, telemetry, usage analytics, tracking SDK, or
automatic crash upload. User audio and transcripts are not sent to a PCSSAK processing server.

Network access is limited to a user-requested model download from the fixed whisper.cpp Hugging
Face repository, a public GitHub Release update check, a user-approved update download, Microsoft
WebView2 installation when Windows requires it, or a link the user opens. Those providers may
process ordinary HTTPS metadata such as IP address, time, and requested asset.

## Platform and installation safety

- Release target: Windows x64 with an AVX2-capable CPU
- Primary target: a currently serviced Windows 11 Home or Pro x64 installation
- Not provided: x86, Windows on ARM, Windows S mode, Windows Server, macOS, Linux, or Wine builds
- CPU-only public installer; Vulkan and CUDA are not included
- The installer and application are **not Windows Authenticode-signed**
- Windows may show Unknown publisher, SmartScreen, or Smart App Control warnings or blocks

Do not disable Microsoft Defender, SmartScreen, Smart App Control, or an organization policy.
Download only from the fixed official v0.1.2 GitHub Release and verify `SHA256SUMS.txt`. The Tauri
updater signature protects the in-app update path but is not an Authenticode publisher identity.

## Update behavior

A release build makes one non-blocking automatic update-check attempt after startup. When v0.1.2
is available, the app verifies the signed release manifest before showing the update. The
installer is downloaded only after user approval, and installation is blocked while capture,
conversion, downloads, or unsaved results remain. The installer signature and signed-manifest
SHA-256 must both match before the update is applied.

## Verification disclosure

The release candidate is subjected to frontend contract tests, rendered keyboard and dialog
flows, automated viewport and scale contracts, TypeScript and Vite production build, Rust tests,
formatting, strict Clippy, dependency licence/source/advisory checks, secret-hygiene checks,
installer contracts, updater signatures, SBOM generation, provenance, and exact asset hashes
before publication.

The following real-device work is deliberately not represented as passed:

| Validation | v0.1.2 status |
| --- | --- |
| Clean Windows 11 Home/Pro install, core work, update, and uninstall | NOT_RUN |
| Installed v0.1.1 → v0.1.2 normal and tampered update on a separate PC | NOT_RUN |
| Windows WebView2 at OS DPI 100–200%, multi-monitor, and window-resize combinations | NOT_RUN |
| Touchpad, touch, IME, and assistive-technology review on real devices | NOT_RUN |
| Intel/AMD devices, microphones, loopback, sleep, and device removal | NOT_RUN |
| Actual 30-minute microphone/VAD/session/UI/stop/cancel flow and nine-language owned audio | NOT_RUN |
| Nine-language native-speaker review of every screen and error | NOT_RUN |
| Defender, SmartScreen, Smart App Control, and other security products | NOT_RUN |
| Launch-jurisdiction legal counsel and localized legal review | NOT_RUN |

Important audio and results must be backed up and reviewed by a person.

## Feedback

Report reproducible defects through the official GitHub bug form and recurring user needs through
the feature-request form. Include the selected interface scale, Windows display scaling, window
size, active tab, and whether mouse wheel, touchpad, scrollbar drag, or keyboard scrolling failed.
Do not post original audio, private transcripts, personal paths, customer data, credentials, or
company secrets in a public issue. Use the private security reporting route for exploitable
vulnerabilities.

---

# PCssak ModuSori 0.1.2 — 무료 얼리액세스

0.1.2는 0.1.1 설치 뒤 제보된 앱 전체 세로 스크롤 불능을 우선 수정한 긴급 화면 패치입니다.
화면 배율을 확대하면 현재 창 아래의 내용이 잘리면서 받아쓰기·실시간 자막·파일 변환·회의록이
공유하는 주 기능 영역에 사용할 수 있는 세로 스크롤이 생기지 않을 수 있었습니다.

이번 패치는 음성 인식, 무료 0.1.x 기능 한도, 모델 목록, 지원 플랫폼, 네트워크 동작과 미서명
설치기 고지를 바꾸지 않습니다. EULA·개인정보 처리방침은 검토 대상 빌드를 0.1.2로 명확히 하고
문서 버전을 `0.1.2-2026-08-27`로 맞췄습니다. 정책 내용은 바뀌지 않았지만 내장 문서 버전과
해시가 달라지므로 기존 설치에서도 다시 확인해야 합니다.

## 0.1.2 핵심 변경

- 앱 루트의 너비와 높이를 실제 WebView 크기의 유한 경계로 고정
- CSS `zoom` 대신 Tauri/WebView2 네이티브 페이지 확대를 사용해 레이아웃 뷰포트·
  반응형 기준·뷰포트 단위 모달 높이를 함께 조정
- 부팅·법률 동의·정상 화면의 배율 컨테이너와 충돌하던 별도 전체 화면 높이 제거
- 네 기능 탭을 하나의 유한한 공통 세로 스크롤 영역 안에 유지
- 공통 영역에 키보드 초점, 보이는 포커스 표시와 9개 UI 언어 접근성 이름 추가
- 부팅 화면이 별도 전체 뷰포트가 아니라 배율 보정 부모 높이를 따르도록 수정

기본 화면 배율은 계속 110%이며 설정에서 100%·125%·150%를 선택할 수 있습니다. 독립 실시간
자막 오버레이의 글자 크기 설정은 이번 패치의 영향을 받지 않습니다.

## 원인과 수정 경계

CSS `zoom`은 화면을 확대했지만 확대 루트는 백분율 높이를 사용했습니다. 조상 높이가 명시적인
유한값이 아니어서 이 백분율이 콘텐츠 높이처럼 풀릴 수 있었고, 내부 `main`에 넘침이 생기는 대신
앱 루트가 WebView 아래로 늘어났습니다. 또한 반응형 미디어 쿼리는 확대 전 창 폭을 기준으로
남고 `vh` 기반 대화상자는 다시 확대될 수 있었습니다. 바깥 페이지는 의도적으로 넘침을 숨기므로
하단이 잘리고 사용할 수 있는 페이지 스크롤바도 나타나지 않았습니다.

0.1.2는 공통 앱 셸에 유한 높이를 부여하고 화면 배율을 네이티브 WebView 확대에 맡겼습니다.
기능 탭마다 별도 스크롤을 덧붙이지 않아 탐색 메뉴, 반응형 레이아웃, 활성 녹음 배너,
대화상자와 하단 버전 표시가 같은 기준으로 동작합니다. 확대 권한은 메인 WebView에만 제한되며
독립 실시간 자막 오버레이에는 적용하지 않습니다.

## 무료 0.1.x 기준

| 항목 | 한도 |
| --- | --- |
| 사용자·좌석 | 제한 없음 |
| Whisper 모델 | Tiny·Base·Small·Medium·Large-v3 Turbo 모두 제공 |
| 파일 변환 | 파일당 최대 15분 |
| 받아쓰기 | 현지 날짜 기준 하루 15회 |
| 실시간 자막 | 세션당 5분, 새 세션 다시 시작 가능 |
| 회의록 정리 | 현지 날짜 기준 하루 3회 |
| 영어 번역 | 제공하지 않음 |

현재 유료 플랜·결제·유료 라이선스 판매는 없습니다. 화자분리와 로컬 생성형 LLM도 포함하지 않으며
회의록은 결정론적 추출식 정리입니다.

음성·전사·자막·추출식 회의록은 사용자 PC에서 처리되며 PCSSAK 처리 서버로 보내지 않습니다.
계정·광고·텔레메트리·사용 분석·추적 SDK·자동 오류 업로드가 없습니다.

공개 설치본은 AVX2를 지원하는 Windows x64용 CPU 빌드이며 Windows Authenticode로 서명되지
않았습니다. Defender·SmartScreen·Smart App Control을 끄지 말고 공식 v0.1.2 고정 GitHub
릴리스와 `SHA256SUMS.txt`를 확인하십시오. Tauri 업데이터 서명은 앱 내 업데이트 무결성을
보호하지만 Windows 게시자 신원을 뜻하지 않습니다.

## 검증 범위 공개

공개 후보 생성 전 프런트 계약, 실제 렌더 키보드·대화상자 흐름, 자동 뷰포트·배율 계약 검사,
TypeScript/Vite 운영 빌드, Rust 시험, 형식·Clippy·의존성·비밀정보·설치기·업데이터 서명·
SBOM·출처·자산 해시 검사를 수행합니다.

깨끗한 별도 Windows 11 Home/Pro 설치, 설치된 0.1.1→0.1.2 정상·변조 업데이트, 실제 WebView2의
OS DPI 100–200%·다중 모니터·창 크기 조합, 터치패드·터치·IME·보조 기술, 여러 장치, 실제
30분 마이크 종단 흐름, 9개 언어 원어민 UI와 정답 음원, 보안 제품, 출시국 법률 검토는 모두
`NOT_RUN`이며 통과했다고 주장하지 않습니다.

스크롤 문제가 재현되면 선택한 앱 화면 배율, Windows 디스플레이 배율, 창 크기, 기능 탭과
실패한 입력 방식(휠·터치패드·스크롤바 끌기·키보드)을 함께 제보해 주십시오. 공개 이슈에는
원본 음성·전사 전문·개인 경로·고객 자료·자격증명·회사 비밀을 올리지 마십시오.
