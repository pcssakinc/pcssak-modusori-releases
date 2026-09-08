# PCssak ModuSori — 공식 Windows 다운로드

[English](README.md) · [제품 홈페이지](https://pcssak.co.kr/modusori) · [설치 안내](docs/INSTALLATION.ko.md) · [v0.1.7 릴리스](https://github.com/pcssakinc/pcssak-modusori-releases/releases/tag/v0.1.7)

**말한 내용을 자신의 Windows PC에서 문자로 바꿉니다.** PCssak ModuSori는 사용자가
선택해 내려받는 다섯 Whisper 모델로 동작하는 로컬 우선 음성 타이핑·실시간 자막·미디어
전사·추출식 회의록 프로그램입니다.

> **저장소 범위:** 이곳은 공식 설치 파일 배포·업데이트·문서·문제 제보용 공개
> 저장소입니다. 애플리케이션 소스는 비공개 독점 소프트웨어이며 이 저장소가 공개되어
> 있다는 이유로 소스 코드가 오픈소스가 되는 것은 아닙니다.

> **공개 승인 기준:** 정확한 태그의 고정 GitHub 릴리스가 보이고, 무결성·서명·출처·법률·
> 고지·SBOM·릴리스 노트 자산이 모두 있어야 공식 설치본입니다. 릴리스 페이지나 필수
> 자산이 없으면 승인된 공개 PCssak ModuSori 빌드가 아닙니다.

## 무료 버전 0.1.7

0.1.7은 짧은 발화·언어 재사용·정상 중지·인식문 보존을 다듬은 누적 패치입니다. 0.1.6의
녹음 전 비캡처 장치 점검과 세션당 확인 1회 흐름, 이전 Windows 모델 다운로드 신뢰·결과 복구
수정도 포함합니다. 이 문서의 버전 안내만으로 위 공개 승인 기준을 충족한 것은 아닙니다.

### 0.1.7 핵심 변경

- 최종 결과에서 숫자·문장부호를 제외한 문자가 6개 이상이거나 문자가 있는 유효 최종 결과가
  연속 두 번 같은 언어를 감지하면 세션 언어를 고정해 재사용합니다. 숫자뿐인 결과와 중간 가설은
  고정 근거로 쓰지 않습니다. 짧은 첫 발화 한 번의 영향을 줄이는 규칙이며 문자 수·결과 일치가
  언어 감지 정확도를 보장하지는 않습니다.
- 받아쓰기는 마지막 발화의 꼬리 패딩 뒤 침묵이 1초 이어지면 대기 음성을 제출하고 발화 시작
  기준 8초 상한도 유지합니다. 짧은 클릭 직후 중지해도 이전 발화 끝을 늘리지 않으며 실제
  재개한 발화는 보존합니다. 제출 시점은 전체 인식 완료 시간이 아닙니다.
- 정상 중지는 인식 진행과 같은 세션의 실제 계산 활동을 확인합니다. 무활동 60초 또는 절대
  상한 15분 뒤 받아쓰기는 협력 취소와 부분 결과 보존을 진행합니다. 자막은 실패 상태에서
  세션을 유지해 다시 중지할 수 있습니다. 자막 중지 대기에는 직접 취소 버튼이 없으며 남은
  작업을 강제 중단하려면 앱 종료 확인 경로를 사용하며 미확정 결과가 유실될 수 있습니다.
  받아쓰기 직접 취소의 5초는 대기
  예산이며 모든 계산이 물리적으로 5초 안에 종료된다는 보장이 아닙니다.
- 실시간 인식의 잡음 필터는 문구·크레딧·반복 규칙에 무음 근거를 함께 요구합니다. 정규화 중
  숫자·시각·금액을 보존하고 숫자가 포함된 결과는 반복으로 축약하지 않습니다. 정상 강조·
  크레딧 언급도 회귀시험으로 보강했습니다. 파일 변환에는 적용하지 않으며 실제 음원에서
  잘못 거르거나 놓칠 가능성은 남아 있습니다.
- 빌드 PC·외부 환경변수와 무관하게 CPU 빌드 정책을 고정했습니다. AVX2·FMA·F16C가 모두
  필요하며 음성 처리 전에 확인합니다. 빌드 설정 검사를 실행 파일 전체 명령 검사나 모든
  CPU의 실제 호환성 검증으로 확대하지 않습니다.

첫 실행에서는 인식 언어를 직접 지정하지 않은 경우 선택한 UI 언어를 인식 언어 기본값으로
연결하며 기존 설치의 설정과 명시적 선택은 보존합니다.

실제 마이크·장시간 세션·자동/고정 언어 속도 비교·9개 언어 정확도와 오탐·구버전 설치본의
직접 업데이트는 `NOT_RUN`입니다. 과거 `UnknownIssuer` PC에서 모델 다운로드가 현재 정상이라는
사용자 확인은 정확한 0.1.7의 모델 로드·앱 재시작 검증 완료를 뜻하지 않습니다.
[알려진 제한](docs/KNOWN-LIMITATIONS.ko.md)을 확인하십시오.

### 포함 기능

- 설정 가능한 전역 단축키와 검증된 Windows 입력 대상을 이용한 음성 타이핑
- 마이크 또는 Windows 시스템 오디오 중 한 소스의 실시간 자막
- WAV, MP3, M4A, MP4, FLAC, OGG, OGA, AAC, MKA, MKV 미디어 일괄 전사
- SRT, WebVTT, Markdown, 일반 텍스트 내보내기
- 결정·할 일 정리를 돕는 결정론적 추출식 회의록
- 사용자가 요청할 때만 내려받는 Tiny, Base, Small, Medium, Large-v3 Turbo 모델
- 시작 후 자동 업데이트 확인 한 번과 사용자가 요청한 수동 확인
- 중복 실행 방지, 안전 종료 조정, 비정상 종료 초안 암호화 복구
- 영어·한국어·일본어·독일어·프랑스어·중남미 스페인어·브라질 포르투갈어·튀르키예어·
  러시아어 UI

회의록은 규칙 기반 추출식 기능입니다. **화자분리, 생성형 로컬 LLM, 영어 번역은 포함하지
않습니다.**

### 무료 0.1.x 기능 제한

| 기능 | 제한 |
| --- | --- |
| 사용자·좌석 | 제한 없음 |
| Whisper 모델 | 등록된 다섯 모델 모두 |
| 파일 전사 | 파일당 최대 15분 |
| 음성 타이핑 | 현지 날짜 기준 하루 15회 |
| 실시간 자막 | 세션당 30분, 새 세션 시작 가능 |
| 회의록 | 현지 날짜 기준 하루 3회 |
| 영어 번역 | 제공하지 않음 |

## 플랫폼 경계

- 배포 대상: AVX2·FMA·F16C를 지원하는 Windows x64 CPU
- 우선 대상: 현재 Microsoft 지원을 받는 Windows 11 Home 또는 Pro x64
- CPU 전용 빌드이며 공개 CUDA·Vulkan 빌드는 제공하지 않음
- Microsoft Edge WebView2 Runtime 필요
- 미지원: Windows x86, Windows on ARM, Windows S 모드, Windows Server, macOS, Linux, Wine
- Windows 10 22H2는 미검증 호환성 관찰 대상일 뿐 지원 플랫폼이 아님

깨끗한 Windows·실제 마이크 장시간·여러 장치·원어민 언어·보안 제품·업데이터·출시 지역
법률 실기는 v0.1.7에서 명시적으로 `NOT_RUN`입니다. 설치 전에 [v0.1.7 릴리스](https://github.com/pcssakinc/pcssak-modusori-releases/releases/tag/v0.1.7),
[알려진 제한](docs/KNOWN-LIMITATIONS.ko.md), [시스템 요구사항](SYSTEM_REQUIREMENTS.ko.md)을
읽으십시오.

## 다운로드와 무결성 확인

[공식 고정 v0.1.7 릴리스](https://github.com/pcssakinc/pcssak-modusori-releases/releases/tag/v0.1.7)
또는 PCSSAK 공식 다운로드 페이지만 사용하십시오.

1. 릴리스 태그가 정확히 `v0.1.7`인지 확인하고 소스 압축 파일·미러·재패키지·포터블·MSI·
   x86·ARM 빌드를 사용하지 마십시오.
2. 같은 릴리스의 `RELEASE-NOTES.md`와 `BUILD-PROVENANCE.json`을 읽으십시오.
3. 설치 파일의 SHA-256을 계산해 같은 고정 릴리스의 `SHA256SUMS.txt` 설치본 항목과
   비교하십시오.
4. Microsoft Defender·SmartScreen·Smart App Control·조직 정책을 켜 두십시오.
5. 파일명·해시·버전·소스 커밋·필수 릴리스 자산이 하나라도 다르면 중단하십시오.

아직 생성하지 않은 설치본 해시나 크기를 저장소 문서에 미리 적지 않습니다. 정확한 값은
최종 릴리스 바이트에서 만든 뒤 고정 릴리스 자산에만 공개합니다.

> **v0.1.7 릴리스 노트 기록의 역할:**
> 고정 릴리스 자산
> [`RELEASE-NOTES.md`](https://github.com/pcssakinc/pcssak-modusori-releases/releases/download/v0.1.7/RELEASE-NOTES.md)는
> 최종 빌드·검증 경계·보안 정보를 포함한 배포 노트이며 파일 해시는
> [`SHA256SUMS.txt`](https://github.com/pcssakinc/pcssak-modusori-releases/releases/download/v0.1.7/SHA256SUMS.txt)가
> 기준입니다. [`latest.json`](https://github.com/pcssakinc/pcssak-modusori-releases/releases/download/v0.1.7/latest.json)과
> [`UPDATE-RELEASE.json`](https://github.com/pcssakinc/pcssak-modusori-releases/releases/download/v0.1.7/UPDATE-RELEASE.json)은
> 업데이터용 `notes`를 내부에 담습니다. `UPDATE-RELEASE.json`의 `notes_sha256`은 두 Markdown
> 파일이 아니라 UTF-8 인라인 `notes` 값 자체의 해시입니다.

> [!WARNING]
> v0.1.7 설치본과 앱은 Windows Authenticode로 서명되지 않습니다. Windows가 **알 수 없는
> 게시자**, **Windows의 PC 보호**를 표시하거나 Smart App Control·조직 정책이 실행을 막을
> 수 있습니다. 필수 Tauri 업데이트 `.sig`는 앱 내부 업데이트 파일을 보호하지만
> Authenticode 게시자 신원은 아닙니다. 설치를 위해 Windows 보안 기능을 끄지 마십시오.

## 개인정보와 네트워크

음성 인식·음성 타이핑·자막·파일 전사·추출식 회의록은 사용자 장치에서 동작합니다. 앱에는
PCSSAK 계정·광고·텔레메트리·사용 분석·추적 SDK·자동 오류 업로드가 없고 음성·전사를
PCSSAK 처리 서버로 보내지 않습니다.

사용자가 고정 `ggerganov/whisper.cpp` Hugging Face 저장소에서 모델을 요청할 때, 공개
GitHub 릴리스 업데이트 확인·사용자 승인 업데이트 다운로드, Windows의 WebView2 설치,
사용자가 외부 링크를 열 때만 네트워크를 사용할 수 있습니다. 해당 제공자는 IP 주소·시각·
사용자 에이전트·요청 자산 같은 일반 HTTPS 메타데이터를 처리할 수 있습니다. 자세한 내용은
[개인정보 처리방침](PRIVACY.md)을 확인하십시오.

모델 다운로드 HTTPS는 Windows 플랫폼 신뢰와 지원 범위의 시스템 프록시를 따릅니다. 오류를
우회하려고 인증서·호스트명 검증, Windows 보안, 조직 인증서 정책 또는 백신 TLS 검사를 끄지
말고 HTTP 폴백·미신뢰 미러도 사용하지 마십시오. PAC/WPAD 전용·WinHTTP 전용·통합 인증·
TLS 검사 등 기업 프록시 조합은 별도 실기가 남아 있습니다.

비정상 종료 복구는 원본 경로·파일명 없이 제한된 편집 문자와 시간 정보만 저장하고 현재
Windows 사용자 DPAPI로 파일을 암호화하며 만료·손상 자료를 거부합니다. 관리자나 같은
Windows 사용자 권한으로 실행되는 악성코드까지 막는 경계는 아닙니다.

## ModuSori 개선 참여

- 직접 재현한 결함은 [버그 제보 양식](../../issues/new?template=bug-report.yml)을 사용하십시오.
- 반복되는 사용자 문제와 기대 결과는 [기능 요청 양식](../../issues/new?template=feature-request.yml)에 적으십시오.
- 화면이나 기술 정보를 공유하기 전에 [지원 안내](SUPPORT.md)를 읽으십시오.
- 악용 가능한 보안 문제는 [보안 정책](SECURITY.md)에 따라 비공개로 제보하십시오.

원본 음성·개인 전사·고객 자료·인증정보·개인 경로·라이선스 키·기밀 업무를 공개 이슈에
올리지 마십시오. AI 도움으로 작성한 제보도 제출자가 직접 재현하고 확인해야 합니다.

## 문서

- [영문 소개](README.md)
- [v0.1.7 릴리스와 릴리스 노트](https://github.com/pcssakinc/pcssak-modusori-releases/releases/tag/v0.1.7)
- [시스템 요구사항](SYSTEM_REQUIREMENTS.ko.md)
- [설치와 업데이트](docs/INSTALLATION.ko.md)
- [알려진 제한](docs/KNOWN-LIMITATIONS.ko.md)
- [품질과 안전](docs/QUALITY-AND-SAFETY.ko.md)
- [EULA](EULA.md)와 [개인정보 처리방침](PRIVACY.md)
- [제3자 고지](THIRD-PARTY-NOTICES.md)와 [원본 소스 안내](docs/THIRD-PARTY-SOURCE.md)
- [지원](SUPPORT.md), [보안](SECURITY.md), [이슈 작성 기준](CONTRIBUTING.md)

PCssak ModuSori 실행 파일은 판매가 아니라 동봉 EULA에 따른 사용권으로 제공됩니다.
`PCSSAK`은 게시자·소프트웨어 브랜드 표시명이며 이 표현만으로 특정 등록 법인 형태를
주장하지 않습니다. 제3자 구성요소는 각자의 라이선스를 따릅니다. PCSSAK은 OpenAI,
Hugging Face, GitHub, Microsoft 또는 상위 프로젝트와 제휴하거나 보증받지 않았습니다.
