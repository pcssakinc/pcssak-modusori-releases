# 개인정보 처리방침

**PCssak ModuSori — 무료 얼리액세스**
제품 버전: 0.1.1 · 방침 버전: 0.1.1-2026-08-26 · 적용일: 2026-08-26
개인정보 처리·배포 운영자 표시명: **PCSSAK**
개인정보 문의: privacy@pcssak.com

언어 고지: 이 문서의 국문이 기준본입니다. 아래 영문은 편의 번역이며 별도의 현지 법률 검수를 완료했다는 뜻이 아닙니다. 이용자에게 적용되는 강행법규가 더 큰 권리를 부여하면 해당 법규가 우선합니다.

PCSSAK은 제품과 공식 배포 경로에서 사용하는 운영자 표시명이며, 이 표기만으로 등록 법인명이나 사업자 등록 상태를 단정하지 않습니다. 이번 무료 얼리액세스에서는 실제 우편 주소를 공개하지 않습니다. 현지 강행법규 또는 플랫폼이 추가 신원·주소·대리인 표시를 요구하면 충족하기 전 해당 지역의 배포·지원이 제한될 수 있습니다.

## 1. 적용 범위

이 방침은 PCssak ModuSori 0.1.1 Windows 앱이 로컬에서 다루는 데이터와 앱이 시작할 수 있는 외부 네트워크 연결을 설명합니다. PCSSAK 홈페이지, GitHub, Hugging Face, Microsoft, 이메일 제공자 등 제3자는 각자의 방침에 따라 별도로 데이터를 처리할 수 있습니다.

## 2. 앱이 PCSSAK 서버로 보내지 않는 정보

검토 대상 0.1.1 빌드는 다음 내용을 사용자 PC에서 처리하도록 설계되었습니다.

- 마이크·시스템 오디오와 사용자가 선택한 음성·영상 파일
- 음성 인식 결과, 음성 타이핑 문구와 실시간 자막
- 파일 전사, 추출식 회의록, 내보내기 결과
- 인식 언어·후처리와 로컬 모델 추론

앱에는 PCSSAK 계정, 광고, 원격 분석(텔레메트리), 사용량 분석, 추적 SDK, 온라인 프로파일링과 자동 충돌 보고 업로드가 없습니다. 위 음성·전사·결과를 PCSSAK이 운영하는 처리 서버로 업로드하지 않습니다.

## 3. 장치에 저장되는 정보

Windows와 Tauri의 실제 폴더 해석은 환경에 따라 다를 수 있으며 기본 식별자는 com.pcssak.modusori입니다.

### 설정 폴더

기본 위치: %APPDATA%\com.pcssak.modusori

- settings.json: UI·인식 언어, 모델 선택, 단축키, 스레드 수, 오디오 장치 식별자, 자막 오버레이 설정, 마지막 내보내기 폴더 등
- legal-consent.json: 스키마 버전, 사용자가 본 문서 언어, EULA·개인정보 처리방침 버전과 SHA-256, 동의 시각, 녹음 안전 고지 버전·언어·SHA-256과 확인 시각
- license.key: 오프라인 라이선스 파일이 별도로 사용되는 미래 또는 내부 구성에서만 존재할 수 있음. 0.1.1 무료 얼리액세스는 결제나 유료 라이선스를 판매하지 않음

동의 시각은 사용자 PC 시계를 기준으로 기록하며 독립된 신뢰 시각이나 참여자 동의 증명이 아닙니다. 문서 내용·버전·해시가 달라지거나 파일이 누락·손상되면 앱은 동의하지 않은 상태로 취급하고 다시 확인을 요구할 수 있습니다.

### 로컬 데이터 폴더

기본 위치: %LOCALAPPDATA%\com.pcssak.modusori

- models 폴더: 사용자가 선택해 내려받은 Whisper 모델과 다운로드 중인 부분 파일
- usage.json, usage-summary.json과 무결성 보조 파일: 무료 기능의 현지 날짜·횟수
- recovery\draft-v1.dpapi: 비정상 종료 복구용으로 제한된 편집 초안을 Windows 현재 사용자 범위 DPAPI로 전체 암호화한 파일

무료 사용량 데이터에는 음성·전사·사용자명·컴퓨터명·도메인명·Windows MachineGuid를 넣지 않습니다. 로컬 무결성 보조값은 우발적 손상·단순 변경을 찾기 위한 것이며, 장치 관리자나 같은 사용자 권한 공격자를 막는 비밀키가 아닙니다.

### 사용자가 선택한 파일

SRT, WebVTT, Markdown, TXT 등 내보낸 결과는 사용자가 저장 대화상자에서 선택한 위치에 기록됩니다. 해당 파일의 보관·공유·삭제와 클라우드 동기화 여부는 사용자가 통제합니다. 앱은 명시적 복사 버튼을 누를 때 WebView 클립보드 쓰기를 사용할 수 있으며 자동 클립보드 대체를 하지 않도록 설계되었습니다. 클립보드 내용은 Windows와 다른 앱이 접근할 수 있으므로 민감한 결과는 사용 후 지우십시오.

## 4. 비정상 종료 복구

복구 파일은 음성 원본, 입력 파일 경로·파일명과 자격증명을 구조적으로 받지 않으며, 복구에 필요한 제한된 텍스트 결과와 시간 정보만 저장하도록 설계되었습니다.

- 전체 평문 최대 4 MiB, 보호 파일 최대 5 MiB
- 실시간 자막 최대 200줄, 배치 결과 최대 32건과 별도 필드 상한
- 현재 Windows 사용자에게 묶인 DPAPI 암호화
- 최대 7일 보유; 만료·손상·알 수 없는 스키마·정책 위반 시 부분 복구 없이 전체 폐기
- 정상 종료 또는 사용자가 복구 초안을 폐기하면 삭제
- 낮은 revision이 새 초안을 덮지 못하도록 역전 방지

DPAPI는 다른 일반 Windows 계정의 단순 파일 열람 위험을 줄이지만, 같은 계정 권한의 악성코드, 관리자, 잠금 해제된 장치, 메모리 접근, 백업·동기화 도구까지 차단하지 않습니다. 복구가 필요하지 않거나 민감도가 높은 작업에서는 정상 종료하고 결과를 안전한 위치로 내보내십시오.

## 5. 네트워크 연결과 외부 수신자

### Whisper 모델 다운로드

사용자가 모델 설치를 선택할 때만 앱은 https://huggingface.co/ggerganov/whisper.cpp 와 연결된 HTTPS 저장소·CDN에 요청합니다. 고정 파일명, Range 헤더를 이용한 이어받기와 일반 요청 메타데이터가 전송될 수 있습니다. 받은 파일은 예상 크기와 고정 SHA-256을 통과해야 설치됩니다. 사용자 음성·전사·로컬 파일 경로는 이 요청에 넣지 않습니다.

### 업데이트 확인과 설치

릴리스 프로세스는 시작 상태 복구 뒤 한 번 공개 GitHub 배포 저장소의 latest.json을 확인할 수 있습니다. 새 버전 후보가 있으면 승인된 UPDATE-RELEASE.json과 그 서명을 추가로 확인해 앱이 최대 세 건의 메타데이터 요청을 시작할 수 있습니다. 사용자가 설치를 승인하면 메타데이터를 다시 확인한 뒤 설치 파일 한 건을 내려받습니다. 사용자가 누른 수동 확인은 별도 시도입니다. 리디렉션과 CDN 내부 요청은 외부 서비스가 추가로 처리할 수 있습니다.

GitHub와 연결된 CDN에는 IP 주소, 접속 시각, 사용자 에이전트, 앱 버전과 일반 HTTPS 요청 정보가 보일 수 있습니다. 업데이트 요청에는 음성·전사·파일 경로·Windows 사용자명·장치 고유 ID를 넣지 않습니다. 설치 파일은 Tauri 업데이트 서명, 승인된 배포 매니페스트와 SHA-256을 모두 검증한 뒤 적용합니다.

### Microsoft WebView2와 사용자가 연 링크

PC에 Microsoft Edge WebView2 Runtime이 없으면 Windows 설치 과정이 Microsoft 서버에서 런타임을 받을 수 있습니다. 사용자가 홈페이지·지원·피드백·이메일 링크를 열면 기본 브라우저나 메일 앱과 해당 서비스가 연결 정보를 처리합니다. 앱은 링크를 연 뒤 제3자 서비스의 처리를 통제하지 않습니다.

## 6. 홈페이지·지원·GitHub 제보

앱 자체는 PCSSAK 서버에 진단 자료를 자동 전송하지 않습니다. 사용자가 이메일, 홈페이지 또는 공개 GitHub Issues로 문의하면 사용자가 보낸 이메일 주소, 계정명, 본문, 첨부물과 기술 정보가 지원·보안 대응을 위해 처리될 수 있습니다.

공개 이슈에는 원본 음성·영상, 전사 전문, 개인 경로, 고객 자료, 자격증명, 라이선스 키, 회사 비밀과 다른 사람의 개인정보를 올리지 마십시오. 악용 가능한 보안 문제는 공개 이슈가 아니라 SECURITY.md의 비공개 경로로 보내십시오.

## 7. 목적, 보유와 삭제

- 설정·모델·사용량·동의 기록: 기능 제공, 사용자 선택 유지, 사용량 제한과 동의 버전 확인을 위해 사용자가 삭제하거나 앱을 제거한 뒤 수동 삭제할 때까지 로컬에 남을 수 있음
- 복구 초안: 정상 종료·사용자 폐기 또는 최대 7일 뒤 삭제하도록 설계
- 내보낸 결과: 사용자가 선택한 위치에서 사용자가 삭제할 때까지 보관
- 지원 문의: 문의 처리, 보안 대응, 분쟁 방어와 법적 의무에 필요한 기간만 보관하는 것을 원칙으로 하며, 정확한 기간은 사용한 이메일·GitHub 서비스와 사안에 따라 달라질 수 있음

앱 제거 프로그램이 모델·설정·사용량·복구·사용자 내보내기 파일을 모두 자동 삭제한다고 보장하지 않습니다. 삭제하려면 앱을 정상 종료한 뒤 위 APPDATA·LOCALAPPDATA 폴더와 사용자가 선택한 내보내기 위치를 확인하십시오. 필요한 모델·결과를 먼저 백업하십시오.

PCSSAK은 앱의 로컬 데이터에 접근할 수 없으므로 해당 데이터의 사본 제공·정정·삭제 요청을 원격으로 수행할 수 없습니다. 사용자가 장치에서 직접 통제해야 합니다.

## 8. 보안

앱은 HTTPS, 리디렉션의 HTTPS 제한, 모델 크기·SHA-256 검증, 원자 저장, 업데이트 전용 서명, 웹뷰 콘텐츠 보안 정책과 현재 사용자 범위 복구 암호화를 사용합니다. 그러나 어떤 소프트웨어도 완전한 보안을 보장할 수 없습니다.

Windows 보안 업데이트, 장치 잠금, 최소 권한 계정, 디스크 암호화와 신뢰할 수 있는 백업을 사용하십시오. 공유 PC, 원격 관리, 악성코드, 클라우드 동기화와 클립보드는 로컬 결과를 노출할 수 있습니다.

## 9. 아동·청소년

소프트웨어는 아동을 대상으로 설계·홍보되지 않습니다. 현지법상 계약 능력이 없는 미성년자는 법정대리인의 유효한 동의와 감독 없이 사용해서는 안 됩니다. 학교·상담·가정 통화 등 미성년자의 음성이 포함되면 사용자에게 별도의 보호자 동의, 조직 승인과 녹음·개인정보 의무가 생길 수 있습니다. 앱의 확인란은 보호자의 신원·권한을 검증하지 않습니다.

## 10. 국가별 권리와 국제 처리

앱의 핵심 콘텐츠는 로컬에만 있으므로 PCSSAK이 이를 국외 이전하지 않습니다. 모델·업데이트·WebView2·홈페이지·지원 서비스를 사용하면 GitHub, Hugging Face, Microsoft, Cloudflare, 이메일 제공자 등이 여러 국가에서 연결 정보와 사용자가 자발적으로 보낸 자료를 처리할 수 있습니다.

적용 법률에 따라 사용자는 PCSSAK이 실제 보유한 지원·홈페이지 개인정보에 대해 열람, 정정, 삭제, 처리 제한, 반대, 이동, 동의 철회 또는 감독기관 진정을 요청할 권리가 있을 수 있습니다. privacy@pcssak.com으로 요청하면 적용 법률에 따라 본인 확인과 처리 가능 범위를 안내합니다. 이 방침은 현지법이 부여하는 포기할 수 없는 권리를 제한하지 않습니다.

## 11. 변경

새로운 계정, 텔레메트리, 클라우드 전사, 광고 또는 원격 충돌 업로드를 추가한다면 데이터 흐름을 다시 검토하고 필요한 사전 고지·동의를 제공합니다. 방침이 바뀌면 버전·적용일과 주요 변경을 표시하며, 앱은 문서 해시 변경 시 다시 동의를 요청할 수 있습니다.

## 12. 연락처

- 개인정보 처리·배포 운영자 표시명: **PCSSAK**
- 개인정보 문의: privacy@pcssak.com
- 일반 지원: support@pcssak.com
- 제품 홈페이지: https://pcssak.com/modusori
- 공식 배포 저장소: https://github.com/pcssakinc/pcssak-modusori-releases

---

# Privacy Notice

**PCssak ModuSori — Free Early Access**
Product version: 0.1.1 · Notice version: 0.1.1-2026-08-26 · Effective: August 26, 2026
Privacy and distribution-operator display name: **PCSSAK**
Privacy contact: privacy@pcssak.com

## Important language and provider notice

The Korean text above governs this Notice. This English text is a convenience translation and is not represented as having been separately reviewed by local legal counsel. Mandatory law that grants you greater rights prevails.

PCSSAK is the operator display name used for the product and official distribution channels; the name alone does not assert a particular registered legal-entity or business-registration status. This Free Early Access release does not publish a physical postal address. Where mandatory law or a platform requires additional identity, address, or representative information, distribution or support there may be restricted until the requirement is satisfied.

## 1. Scope

This Notice explains data kept locally by the PCssak ModuSori 0.1.1 Windows app and external network connections the app may initiate. The PCSSAK website and third parties such as GitHub, Hugging Face, Microsoft, Cloudflare, and email providers process data separately under their own notices.

## 2. Content not sent to a PCSSAK processing server

The reviewed 0.1.1 build is designed to process on the user's PC: microphone and system audio; user-selected audio or video files; dictation, live captions, file transcripts, extractive meeting notes, exports, language processing, and local model inference.

The app contains no PCSSAK account, advertising, telemetry, usage analytics, tracking SDK, online profiling, or automatic crash-report upload. It does not upload that audio, transcript, or output to a PCSSAK-operated processing server.

## 3. Data stored on the device

Windows and Tauri may resolve folders differently by environment. The default application identifier is com.pcssak.modusori.

The default configuration directory is %APPDATA%\com.pcssak.modusori. It may contain settings.json with UI and recognition language, selected model, hotkey, thread count, audio-device identifiers, overlay preferences, and the last export directory; legal-consent.json with document locale, EULA and Privacy versions and SHA-256 hashes, consent time, and recording-safety notice version, locale, hash, and acknowledgment time; and license.key only in a future or internal offline-license configuration. Version 0.1.1 does not sell a paid license.

Consent times use the user's PC clock and are not trusted independent timestamps or proof of participant consent. Missing, corrupt, unknown, or changed document records may require consent again.

The default local-data directory is %LOCALAPPDATA%\com.pcssak.modusori. It may contain user-selected Whisper models and partial downloads; local date and count records for free limits with integrity helper files; and recovery\draft-v1.dpapi containing a limited encrypted editing draft.

Usage records do not include audio, transcripts, Windows user name, computer name, domain name, or Windows MachineGuid. Their local integrity value detects accidental damage or simple modification; it is not a secret that resists an administrator or same-user attacker.

SRT, WebVTT, Markdown, TXT, and other exported results are stored only where the user chooses in the native save dialog. The app may write text to the WebView clipboard only after the user selects an explicit Copy action; it is designed not to use automatic clipboard fallback. Windows and other apps can read clipboard content, so clear sensitive text after use.

## 4. Unexpected-exit recovery

The recovery format is designed not to accept source audio, input paths, filenames, or credentials. It stores only bounded text results and timing needed for recovery: up to 4 MiB plaintext and 5 MiB protected file size, up to 200 live-caption lines and 32 batch results with additional field limits.

The entire draft is protected with Windows current-user DPAPI. It is designed to be deleted after normal shutdown or user discard and, in all cases, rejected and deleted when older than seven days, corrupt, unknown, or outside policy. Lower revisions cannot overwrite a newer draft.

DPAPI reduces simple file access from another ordinary Windows account. It does not protect against malware running as the same user, an administrator, an unlocked device, memory access, or backup and sync tools.

## 5. Network access and external recipients

When the user chooses a Whisper model, the app requests a fixed file from https://huggingface.co/ggerganov/whisper.cpp and connected HTTPS storage or CDN services. Requests may contain the fixed filename, Range headers for resume, and ordinary network metadata. The download must match the expected size and pinned SHA-256. User audio, transcripts, and local paths are not included.

After startup-state recovery, a release process may check public GitHub Release latest.json once. If a newer candidate exists, it may additionally request the approved UPDATE-RELEASE.json and its signature, for up to three app-initiated metadata requests. If the user approves installation, the metadata is rechecked and one installer is downloaded. A manual check is a separate attempt; redirects and CDN internals may add service-side requests.

GitHub and its CDN may process IP address, time, user agent, app version, and ordinary HTTPS metadata. Update requests do not include audio, transcript text, local paths, Windows user name, or a device-unique identifier. Installation requires the Tauri updater signature, approved release manifest, and SHA-256 verification.

If Microsoft Edge WebView2 Runtime is absent, the Windows installation process may connect to Microsoft. When the user opens a website, support, feedback, or email link, the default browser or mail app and the relevant service process that connection.

## 6. Website, support, and GitHub reports

The app does not automatically send diagnostics to PCSSAK. If a user contacts PCSSAK by email, website, or public GitHub Issues, the user's email address or account name, message, attachments, and voluntarily supplied technical information may be processed for support and security response.

Do not post original media, full private transcripts, personal paths, customer data, credentials, license keys, company secrets, or another person's personal data in a public Issue. Report exploitable security details through the private route in SECURITY.md.

## 7. Purpose, retention, and deletion

Settings, models, usage, and consent records remain locally until the user deletes them or removes the app and manually removes residual data. Recovery is designed to be deleted on normal shutdown, user discard, or no later than seven days. Exports remain until the user deletes them. Support communications are retained only as reasonably needed for response, security, dispute defense, and legal obligations, with exact periods depending on the service and matter.

Uninstall may not automatically remove every setting, model, usage, recovery, or user-exported file. After closing the app normally, inspect the APPDATA and LOCALAPPDATA paths above and any export location. Back up needed results first.

PCSSAK cannot remotely access, copy, correct, or delete app-local data. The user controls it on the device.

## 8. Security

The app uses HTTPS, HTTPS-limited redirects, model size and SHA-256 checks, atomic local writes, updater signatures, a WebView content-security policy, and current-user recovery encryption. No software can guarantee complete security. Use current Windows security updates, device locking, least-privilege accounts, disk encryption, and trustworthy backups.

## 9. Children

The Software is not designed or marketed for children. A minor lacking legal capacity must not use it without valid guardian consent and supervision. A user recording a class, counseling session, family call, or other speech involving minors may have additional duties concerning guardian consent, organizational approval, recording law, and children's privacy. App checkboxes do not verify a guardian's identity or authority.

## 10. International processing and rights

Core app content remains local and is not transferred abroad by PCSSAK. GitHub, Hugging Face, Microsoft, Cloudflare, and email providers may process connection metadata and voluntarily submitted information in multiple countries.

Depending on applicable law, a user may have rights to access, correct, delete, restrict, object, port, withdraw consent, or complain concerning personal data PCSSAK actually holds through support or the website. Contact privacy@pcssak.com for identity verification and the applicable response process. This Notice does not limit non-waivable statutory rights.

## 11. Changes

Before adding an account, telemetry, cloud transcription, advertising, or remote crash upload, PCSSAK will review the data flow and provide required notice or consent. A changed Notice identifies its version, effective date, and material changes; the app may request consent again when the document hash changes.

## 12. Contact

- Privacy and distribution-operator display name: **PCSSAK**
- Privacy: privacy@pcssak.com
- Support: support@pcssak.com
- Product website: https://pcssak.com/modusori
- Official distribution repository: https://github.com/pcssakinc/pcssak-modusori-releases
