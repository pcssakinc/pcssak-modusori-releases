# PCssak ModuSori Support / 지원 안내

PCssak ModuSori 0.1.0 is Free Early Access. Support is best-effort and has no guaranteed response
or resolution time. This repository handles public download documentation, reproducible defects,
and product feedback; it is not a source-code support repository.

PCssak ModuSori 0.1.0은 무료 얼리액세스입니다. 지원은 가능한 범위에서 제공하며 응답·해결
시간을 보장하지 않습니다. 이 저장소는 공개 다운로드 문서·재현 가능한 결함·제품 의견을
다루며 소스 코드 지원 저장소가 아닙니다.

## Before reporting / 제보 전 확인

1. Confirm the version shown in the app footer and use only an official fixed GitHub Release.
2. Read the [release notes](RELEASE_NOTES_v0.1.0.md),
   [system requirements](SYSTEM_REQUIREMENTS.md), and
   [known limitations](docs/KNOWN-LIMITATIONS.md).
3. Restart the application normally. Do not reinstall or delete recovery data until you have
   recorded whether the issue is repeatable.
4. Search existing issues. Report one reproducible problem or one user need per issue.

1. 앱 하단 버전을 확인하고 공식 고정 GitHub 릴리스만 사용하십시오.
2. [릴리스 노트](RELEASE_NOTES_v0.1.0.md), [시스템 요구사항](SYSTEM_REQUIREMENTS.ko.md),
   [알려진 제한](docs/KNOWN-LIMITATIONS.ko.md)을 확인하십시오.
3. 앱을 정상적으로 다시 시작하십시오. 반복 여부를 기록하기 전에 재설치하거나 복구 자료를
   지우지 마십시오.
4. 기존 이슈를 검색하고 이슈 하나에는 재현 가능한 문제나 사용자 요구 하나만 적으십시오.

## Bug report / 버그 제보

Use the [bug report form](../../issues/new?template=bug-report.yml) and include only non-sensitive
information:

- exact PCssak ModuSori version and whether it came from the fixed official release;
- Windows edition, version, architecture, and update level;
- CPU model, whether AVX2 is available, installed memory, and selected Whisper model;
- microphone, output/loopback device, or media container and codec without private content;
- exact steps, expected behavior, actual behavior, and repeat frequency;
- whether the problem survives a normal restart and whether another capture or update was active;
- a synthetic test file or redacted screenshot only when needed and lawful to share.

[버그 제보 양식](../../issues/new?template=bug-report.yml)에 다음 비민감 정보만 적으십시오.

- 정확한 ModuSori 버전과 공식 고정 릴리스에서 받았는지 여부
- Windows 에디션·버전·아키텍처·업데이트 수준
- CPU 모델·AVX2 지원 여부·설치 메모리·선택한 Whisper 모델
- 개인 내용이 없는 마이크·출력/루프백 장치 또는 미디어 컨테이너·코덱 정보
- 정확한 재현 순서·기대 결과·실제 결과·반복 빈도
- 정상 재시작 뒤에도 반복되는지와 다른 캡처·업데이트가 실행 중이었는지
- 필요하고 공유 권한이 있을 때만 합성 시험 파일 또는 비식별 화면

## Feature request / 기능 요청

Use the [feature request form](../../issues/new?template=feature-request.yml). Describe the
recurring user problem, current workaround, expected outcome, target language or workflow, and why
the request matters. A request is not a promise of implementation, schedule, pricing, or support.

[기능 요청 양식](../../issues/new?template=feature-request.yml)에 반복되는 사용자 문제·현재
우회 방법·기대 결과·대상 언어 또는 업무 흐름·필요한 이유를 적으십시오. 요청 등록은 구현·
일정·가격·지원 약속이 아닙니다.

## Never post publicly / 공개 금지 자료

Do not post original audio or video, full transcripts or meeting notes, customer or employee data,
names, email addresses, credentials, licence or signing keys, private URLs, full local paths,
company secrets, crash dumps containing content, or files you do not have the right to share.
Create a small synthetic sample instead. Public GitHub issues and attachments are not local or
private processing.

원본 음성·영상, 전체 전사·회의록, 고객·직원 자료, 이름·이메일, 인증정보, 라이선스·서명 키,
비공개 URL, 전체 로컬 경로, 회사 비밀, 내용이 포함된 덤프, 공유 권한이 없는 파일을 공개하지
마십시오. 대신 작은 합성 자료를 만드십시오. 공개 GitHub 이슈와 첨부는 로컬·비공개 처리가
아닙니다.

For an exploitable vulnerability, use [private security reporting](SECURITY.md), not a public issue.
General support contact: support@pcssak.com. Privacy questions: privacy@pcssak.com.

악용 가능한 취약점은 공개 이슈가 아니라 [비공개 보안 제보](SECURITY.md)를 사용하십시오.
일반 지원: support@pcssak.com · 개인정보 문의: privacy@pcssak.com
