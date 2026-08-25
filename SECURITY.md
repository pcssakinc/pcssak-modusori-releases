# Security Policy / 보안 정책

## Private reporting / 비공개 제보

Do not disclose a suspected vulnerability in a public issue. Use
[GitHub private vulnerability reporting](../../security/advisories/new) for this repository. If
that route is unavailable, contact support@pcssak.com with a minimal first message and do not send
an exploit, private audio, transcript, credential, or company secret until a safe exchange method
has been agreed.

의심되는 취약점을 공개 이슈에 쓰지 마십시오. 이 저장소의
[GitHub 비공개 취약점 제보](../../security/advisories/new)를 사용하십시오. 해당 경로를 사용할
수 없으면 support@pcssak.com으로 최소 정보만 먼저 보내고 안전한 전달 방법에 합의하기 전에는
공격 코드·개인 음성·전사·인증정보·회사 비밀을 보내지 마십시오.

Include:

- affected PCssak ModuSori version and official release source;
- Windows version and architecture;
- reproducible steps, impact, expected and actual behavior;
- whether user interaction, a model download, update, media file, or elevated target is required;
- the smallest non-sensitive evidence necessary to investigate.

영향받는 버전·공식 릴리스 출처, Windows 버전·아키텍처, 재현 순서·영향·기대/실제 동작,
사용자 동작·모델 다운로드·업데이트·미디어·높은 권한 대상이 필요한지, 조사에 필요한 최소
비민감 증거를 포함하십시오.

PCSSAK will acknowledge and investigate valid reports when operationally possible and coordinate
disclosure after a fix or mitigation is available. Free Early Access does not promise a fixed
response, remediation, CVE assignment, bounty, or support period.

PCSSAK은 운영상 가능한 범위에서 유효한 제보를 확인·조사하고 수정 또는 완화책이 준비된 뒤
공개를 조율합니다. 무료 얼리액세스는 고정 응답·수정 기한, CVE 발급, 보상금, 지원 기간을
약속하지 않습니다.

## Scope / 범위

Security-relevant areas include:

- Tauri updater signatures, signed release manifests, anti-rollback checks, and asset hashes;
- model-download HTTPS restrictions, fixed sizes, pinned SHA-256, resume, and atomic install;
- audio-capture indicators, consent boundaries, stopping, and Windows system-loopback capture;
- verified dictation targets, password-field refusal, integrity-level and focus checks;
- local settings, free-use counters, legal consent records, and DPAPI recovery data;
- media parsing, bounded input, export paths, atomic output, safe exit, and single-instance behavior;
- WebView CSP, Tauri capabilities, and accidental data or secret exposure in diagnostics.

주요 범위는 업데이트 서명·매니페스트·롤백 방지·해시, 모델 다운로드 출처·크기·SHA-256·
원자 설치, 녹음 표시·동의·중지·시스템 오디오, 자동 입력 대상·비밀번호 필드·권한/초점 검사,
로컬 설정·무료 사용량·법률 동의·DPAPI 복구, 미디어 파싱·입력 상한·안전 내보내기·종료·
중복 실행, WebView CSP·Tauri 권한·진단 자료의 정보 노출입니다.

## Release security boundary / 릴리스 보안 경계

- Version 0.1.0 is Windows x64 only and requires AVX2.
- The installer is not Windows Authenticode-signed. A Tauri `.sig` is not publisher identity.
- Verify the fixed official tag and `SHA256SUMS.txt`; never disable Defender, SmartScreen, Smart
  App Control, or organisation policy.
- Real-device security-product and tampered-update tests are `NOT_RUN` for v0.1.0; see the
  [release notes](RELEASE_NOTES_v0.1.0.md).
- The app has no telemetry or automatic crash upload. A public issue or email is an external
  disclosure initiated by the user.

- 0.1.0은 AVX2가 필요한 Windows x64 전용입니다.
- 설치본은 Windows Authenticode로 서명되지 않았으며 Tauri `.sig`는 게시자 신원이 아닙니다.
- 공식 고정 태그와 `SHA256SUMS.txt`를 확인하고 Defender·SmartScreen·Smart App Control·조직
  정책을 끄지 마십시오.
- 실제 장치 보안 제품·변조 업데이트 시험은 v0.1.0에서 `NOT_RUN`입니다.
- 앱에는 텔레메트리·자동 오류 업로드가 없습니다. 공개 이슈나 이메일은 사용자가 시작하는
  외부 공개입니다.

Issues entirely within GitHub, Hugging Face, Microsoft, Windows, or another upstream project should
also follow that provider's security policy. PCSSAK is not authorised to accept reports on their
behalf.

GitHub·Hugging Face·Microsoft·Windows·다른 상위 프로젝트에만 있는 문제는 해당 제공자의
보안 정책도 따르십시오. PCSSAK은 그들을 대신해 제보를 접수할 권한이 없습니다.
