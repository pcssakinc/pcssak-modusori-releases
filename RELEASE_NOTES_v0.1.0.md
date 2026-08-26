# PCssak ModuSori v0.1.0 — Free Early Access

PCssak ModuSori turns speech into text locally on a Windows PC. This first public Early Access
release is intended to begin real-user compatibility, quality, and usability validation. It is
not a claim that every device, language, or legal jurisdiction has already been validated.

> **Published-record roles:** This main-branch clarification does not alter the immutable v0.1.0
> tag or Release assets. The [file at the fixed tag](https://github.com/pcssakinc/pcssak-modusori-releases/blob/v0.1.0/RELEASE_NOTES_v0.1.0.md)
> is the version-controlled base note. The fixed Release asset
> [`RELEASE-NOTES.md`](https://github.com/pcssakinc/pcssak-modusori-releases/releases/download/v0.1.0/RELEASE-NOTES.md)
> is the distribution copy with final-build and security-verification details. Updater manifests
> embed their own `notes`; `UPDATE-RELEASE.json`'s `notes_sha256` hashes exactly that UTF-8 inline
> value, while the Markdown asset's file digest is listed separately in `SHA256SUMS.txt`.

## Included in v0.1.0

- Dictation into a verified Windows target using a configurable global hotkey
- Live captions from either a microphone or Windows system audio
- Batch transcription of supported audio and video files with SRT, WebVTT, Markdown, and TXT export
- Deterministic extractive meeting notes with decisions and action-item assistance
- All five registered Whisper models: Tiny, Base, Small, Medium, and Large-v3 Turbo
- User-approved signed update flow with one automatic check attempt after startup
- Single-instance protection, safe-exit coordination, and encrypted unexpected-exit draft recovery
- English, Korean, Japanese, German, French, Latin American Spanish, Brazilian Portuguese,
  Turkish, and Russian user interfaces

Meeting notes are rule-based and extractive. Speaker diarization and a local generative LLM are
not included. English translation is not available in this Free Early Access release.

## Free 0.1.x limits

| Function | Limit |
| --- | --- |
| Users and seats | No limit |
| Whisper models | All five registered models |
| File transcription | Up to 15 minutes per file |
| Dictation | 15 uses per local calendar day |
| Live captions | Five minutes per session; a new session may be started |
| Meeting notes | Three summaries per local calendar day |
| English translation | Not available |

No paid plan, payment, or paid license is currently offered.

## Privacy and network boundary

Speech recognition, transcripts, captions, and extractive notes run on the user's device. The
app has no PCSSAK account, advertising, telemetry, usage analytics, tracking SDK, or automatic
crash upload. User audio and transcripts are not sent to a PCSSAK processing server.

Network access occurs only for a user-requested model download from the fixed whisper.cpp
Hugging Face repository, a public GitHub Release update check, a user-approved update download,
Microsoft WebView2 installation when Windows requires it, or a link the user opens. Those
providers may process ordinary HTTPS metadata such as IP address, time, and requested asset.

Unexpected-exit recovery stores only bounded editing text and timing, excludes source paths and
filenames by structure, encrypts the whole file with current-user Windows DPAPI, and rejects
expired or corrupt data. It is not protection against an administrator or malware running as
the same Windows user.

## Platform and security boundary

- Release target: Windows x64 with an AVX2-capable CPU
- Primary target: a currently serviced Windows 11 Home or Pro x64 installation
- Not provided: x86, Windows on ARM, Windows S mode, Windows Server, macOS, Linux, or Wine builds
- CPU-only release; Vulkan and CUDA are not included in the public installer
- The installer and app are not Windows Authenticode-signed
- Windows may show Unknown publisher, SmartScreen, or Smart App Control warnings or blocks
- Do not disable Microsoft Defender, SmartScreen, Smart App Control, or organization policy
- Verify the fixed v0.1.0 GitHub Release, exact filename, and SHA256SUMS.txt before installation

The Tauri updater signatures protect the in-app update path but are not an Authenticode publisher
identity. The release also publishes the signed update manifest, SPDX SBOM, provenance, legal
documents, third-party notices, and hashes.

## Verification disclosure

Source-level frontend, rendered interaction, Rust, formatting, lint, production-build,
dependency-license, source-policy, secret-hygiene, installer static-contract, updater-signature,
SBOM, and asset-hash checks are run before publication and recorded in the release assets.

The following real-device work is deliberately deferred to public Early Access feedback and is
not represented as passed:

| Validation | v0.1.0 status |
| --- | --- |
| Clean Windows 11 Home x64 install, launch, core work, uninstall | NOT_RUN |
| Clean Windows 11 Pro x64 install, launch, core work, uninstall | NOT_RUN |
| Windows 10 22H2 compatibility observation | NOT_RUN; Windows 10 is out of Microsoft support |
| Intel and AMD device matrix, microphones, loopback, sleep, device removal | NOT_RUN |
| Multi-monitor, DPI, IME, tray, duplicate launch, update-restart races | NOT_RUN |
| Long-duration and nine-language owned benchmark audio | NOT_RUN |
| Nine-language native-speaker review of every screen and error | NOT_RUN |
| Defender, SmartScreen, Smart App Control, and third-party security-product behavior | NOT_RUN |
| Normal and tampered in-app update on a separate installed machine | NOT_RUN |
| Launch-jurisdiction legal counsel and localized legal translation review | NOT_RUN |

By publishing Free Early Access, PCSSAK accepts these disclosed early-stage risks without
claiming compatibility, legal certification, native-language review, or security-product
approval that was not performed. Important audio and results must be backed up and reviewed by
a person.

## Feedback

Report reproducible defects through the official GitHub bug form and recurring user needs through
the feature-request form. Do not post original audio, private transcripts, personal paths,
customer data, credentials, or company secrets in a public issue. Use the private security
reporting route for exploitable vulnerabilities.

---

# PCssak ModuSori v0.1.0 — 무료 얼리액세스

이번 버전은 Windows PC에서 음성을 로컬로 문자화하는 첫 공개 얼리액세스입니다. 실제
사용자의 호환성·정확도·편의성 검증을 시작하기 위한 버전이며 모든 장치·언어·국가의
검증이 이미 끝났다는 뜻이 아닙니다.

> **공개 기록의 역할:** 이 main 브랜치 설명은 고정된 v0.1.0 태그·릴리스 자산을 바꾸지
> 않습니다. [고정 태그의 파일](https://github.com/pcssakinc/pcssak-modusori-releases/blob/v0.1.0/RELEASE_NOTES_v0.1.0.md)은
> 형상관리 기본 노트이고, 고정 릴리스 자산
> [`RELEASE-NOTES.md`](https://github.com/pcssakinc/pcssak-modusori-releases/releases/download/v0.1.0/RELEASE-NOTES.md)는
> 최종 빌드·보안 확인 정보를 덧붙인 배포용 사본입니다. 업데이트 매니페스트는 자체 인라인
> `notes`를 담으며, `UPDATE-RELEASE.json`의 `notes_sha256`은 그 UTF-8 값 자체를 해시합니다.
> Markdown 자산 파일 해시는 `SHA256SUMS.txt`가 별도로 정합니다.

음성 타이핑, 마이크 또는 시스템 오디오 실시간 자막, 파일 일괄 전사와 네 가지 형식
내보내기, 추출식 회의록, 다섯 Whisper 모델, 실행 후 한 번의 사용자 승인 업데이트,
중복 실행 방지, 안전 종료와 현재 Windows 사용자 DPAPI 암호화 복구를 포함합니다.
화자분리·생성형 로컬 LLM·영어 번역은 포함하지 않습니다.

무료 0.1.x는 사용자·좌석 제한이 없고 다섯 모델을 모두 제공합니다. 파일당 15분,
받아쓰기 하루 15회, 실시간 자막 세션당 5분, 회의록 하루 3회의 기능 제한이 있습니다.
현재 유료 플랜·결제·유료 라이선스 판매는 없습니다.

음성·전사·자막·회의록은 PCSSAK 처리 서버로 보내지 않으며 계정·광고·텔레메트리·사용
분석·자동 오류 업로드가 없습니다. 사용자가 시작한 Hugging Face 모델 다운로드,
GitHub 업데이트 확인·승인 다운로드, 필요한 WebView2 설치와 사용자가 연 외부 링크만
네트워크를 사용할 수 있습니다.

공개 설치본은 AVX2를 지원하는 Windows x64용 CPU 빌드이며 Authenticode로 서명되지
않았습니다. Defender·SmartScreen을 끄지 말고 공식 v0.1.0 고정 릴리스의 정확한 파일명과
SHA256SUMS.txt를 확인하십시오.

별도 깨끗한 Windows PC 설치, Intel·AMD와 여러 오디오 장치, 장시간·9개 언어 정답 음원,
원어민 전체 UI, 보안 제품, 설치된 앱의 정상·변조 업데이트와 출시국 법률 검토는 모두
NOT_RUN입니다. PCSSAK은 실행하지 않은 검사를 통과했다고 주장하지 않고 공개
얼리액세스에서 이 범위를 투명하게 검증·개선합니다.
