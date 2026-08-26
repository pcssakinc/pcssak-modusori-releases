# PCssak ModuSori 0.1.1 — Free Early Access

PCssak ModuSori 0.1.1 is an urgent usability and transcription-responsiveness update based on
the first installed-build dictation test. It makes recording and processing states explicit,
adds a real cancellation path for remaining transcription, and improves readability without
changing the Free Early Access limits or privacy boundary.

The EULA and Privacy Notice identify this build as 0.1.1 with document version
`0.1.1-2026-08-26`. Existing installations must review them again because the embedded document
version and hash changed; this version alignment does not add a paid plan or change the data flow.

## What changed in 0.1.1

- Interface scaling at **100%, 110%, 125%, or 150%**, saved for the next launch
- Separate recording length, processing time, and measured recognition backlog without an
  invented completion estimate
- Faster live dictation finalization on CPU while batch transcription keeps its
  accuracy-focused decoding path
- Duplicate-stop protection and an explicit option to cancel remaining transcription while
  keeping text that was already recognized

The capture banner now distinguishes recording, stopping, and processing. The microphone meter
stops when audio collection has ended, and the processing screen cannot be mistaken for a second
recording session. Closing the app no longer waits behind the long live-transcription drain lock;
capture and worker cleanup use bounded waits after an immediate cooperative Whisper cancel.

## Performance disclosure

Live final utterances now use greedy decoding with one candidate. Batch file transcription keeps
beam search with a beam size of five because that path prioritizes accuracy over live response.

On this development PC, one 12.347-second Korean synthetic sample with the Small CPU model and six
threads measured:

| Mode | Inference | Total | Engine speed | Recognized text |
| --- | ---: | ---: | ---: | --- |
| Batch accuracy path | 7,769 ms | 9,200 ms | 1.589× realtime | Same |
| Live final path | 7,083 ms | 8,853 ms | 1.743× realtime | Same |

The deterministic 30-minute, real-time-paced live-final core-and-queue stress test also passed on
this PC. The clean release-mode CPU source was
`c5f497899637036e85942873c8fe42894ed652e1` (`git_dirty=false`, duration override disabled). It
submitted and completed 146/146 chunks representing exactly 1,800,000 ms of audio. Submit,
inference, and empty-result failures were zero; 144 comparable full-chunk results had zero
mismatches. Maximum/final queue depth was 1/0, maximum/final outstanding chunks was 1/0, FIFO
drain took 3,552 ms, and 700,635 ms of inference measured 2.569096× realtime with standard RTF
0.389242. From the first full chunk to the end, working set/private memory increased by
19,968,000/18,616,320 bytes; observed stress peaks were 526,520,320/522,047,488 bytes. The
automatic functional, queue, result-consistency, and throughput gate passed with no failure
reasons. Memory has no automatic pass threshold in this test: the figures are manual observations,
and this single run neither proves nor disproves a long-duration leak.

This paced test used the live-final Whisper core and the same 36-slot queue configuration as the
product (33 data plus three control slots), but the maximum observed queue depth was only one.
Queue saturation and backpressure boundaries were therefore not exercised. It does **not**
exercise an actual microphone, resampling,
VAD, application session events, UI, stop, or cancellation for 30 minutes; that end-to-end
real-device test remains `NOT_RUN`. These are local regression measurements, not a claim about
every computer, microphone, language, accent, or recording. A rights-cleared nine-language
accuracy corpus, WER/CER baseline, actual long-meeting test, and wider Intel/AMD device matrix
also remain `NOT_RUN`.

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
Download only from the fixed official v0.1.1 GitHub Release and verify `SHA256SUMS.txt`. The Tauri
updater signature protects the in-app update path but is not an Authenticode publisher identity.

## Update behavior

A release build makes one non-blocking automatic update-check attempt after startup. If v0.1.1 is
available, the app verifies the signed release manifest before showing the update. The installer
is downloaded only after user approval, and installation is blocked while capture, conversion,
downloads, or unsaved results remain. The installer signature and signed manifest SHA-256 must
both match before the update is applied.

## Verification disclosure

The release candidate is subjected to frontend contract tests, rendered keyboard and dialog
flows, TypeScript and Vite production build, Rust tests, formatting, strict Clippy, dependency
licence/source/advisory checks, secret-hygiene checks, installer contracts, updater signatures,
SBOM generation, provenance, and exact asset hashes before publication.

The following real-device work is deliberately deferred to Free Early Access feedback and is not
represented as passed:

| Validation | v0.1.1 status |
| --- | --- |
| Clean Windows 11 Home/Pro install, core work, update, and uninstall | NOT_RUN |
| Installed v0.1.0 → v0.1.1 normal and tampered update on a separate PC | NOT_RUN |
| Intel/AMD devices, microphones, loopback, sleep, and device removal | NOT_RUN |
| Actual 30-minute microphone/VAD/session/UI/stop/cancel flow and nine-language owned audio | NOT_RUN |
| Nine-language native-speaker review of every screen and error | NOT_RUN |
| Multi-monitor, DPI 100–200%, IME, tray, and duplicate-launch races | NOT_RUN |
| Defender, SmartScreen, Smart App Control, and other security products | NOT_RUN |
| Launch-jurisdiction legal counsel and localized legal review | NOT_RUN |

Important audio and results must be backed up and reviewed by a person.

## Feedback

Report reproducible defects through the official GitHub bug form and recurring user needs through
the feature-request form. Do not post original audio, private transcripts, personal paths,
customer data, credentials, or company secrets in a public issue. Use the private security
reporting route for exploitable vulnerabilities.

---

# PCssak ModuSori 0.1.1 — 무료 얼리액세스

0.1.1은 첫 설치본 받아쓰기 시험에서 확인한 변환 지연·상태 혼동·취소·종료 문제를 우선
개선한 긴급 사용성 업데이트입니다. 무료 한도, 다섯 모델, 로컬 처리, 네트워크 경계와
미서명 설치기 고지는 바뀌지 않습니다. EULA·개인정보 처리방침은 0.1.1 적용 범위를
명확히 하도록 문서 버전을 `0.1.1-2026-08-26`으로 맞췄으며, 내장 문서 버전·해시가
달라졌으므로 기존 설치에서도 다시 확인해야 합니다.

## 핵심 변경 네 가지

- 다음 실행에도 유지되는 **100%·110%·125%·150% 화면 배율**
- 가짜 예상 시간 없이 녹음 길이·처리 경과·실측 인식 대기량을 분리 표시
- 파일 일괄 전사의 정확도 중심 경로는 유지하면서 CPU 실시간 받아쓰기 마무리 속도 개선
- 중복 중지 방지와 이미 인식된 텍스트를 유지하는 남은 변환 취소 기능

상단 배너는 녹음·중지·처리를 구분하며 녹음이 끝나면 마이크 레벨 표시도 멈춥니다. 남은
변환 취소는 해당 세션의 늦은 결과와 외부 자동 입력 대상을 닫고 짧은 제한시간으로 정리합니다.
앱 종료는 더 이상 받아쓰기·자막의 최장 60초 변환 잠금 뒤에서 기다리지 않습니다.

이 PC의 12.347초 한국어 합성 음원·Small CPU·6스레드 1회 측정에서 실시간 확정 경로는
순수 추론 7,083ms·전체 8,853ms, 배치 정확도 경로는 순수 추론 7,769ms·전체 9,200ms였고
인식문은 같았습니다.

같은 PC에서 결정론적 30분 실제시간 페이싱 live-final 코어·제품 큐 본시험도 통과했습니다.
깨끗한 release CPU 소스는 `c5f497899637036e85942873c8fe42894ed652e1`이며
`git_dirty=false`, 시험시간 override=false였습니다. 정확히 1,800,000ms를 146/146 청크로
제출·완료했고 제출·추론·빈 결과 실패는 0, 비교 가능한 전체 청크 144개의 결과 불일치도
0이었습니다. 최대/최종 큐는 1/0, 최대/최종 미완료 청크는 1/0, FIFO drain은 3,552ms,
순수 추론은 700,635ms·2.569096배 실시간·표준 RTF 0.389242였습니다. 첫 전체 청크부터
종료까지 working set/private 메모리는 19,968,000/18,616,320바이트 증가했고 관찰 스트레스
peak는 526,520,320/522,047,488바이트였습니다. 기능·큐·결과 일관성·처리량 자동 gate의
실패 사유는 없었습니다. 메모리에는 자동 합격 임계값을 적용하지 않았으므로 위 수치는 수동
관찰값이며, 단일 실행만으로 장시간 누수 여부를 확정하지 않습니다.

이 결과는 데이터 33칸·제어 예약 3칸인 36칸 제품 큐 구성과 live-final Whisper 코어를
실제시간으로 페이싱한 검증이지만, 관찰된 최대 큐 깊이는 1이었습니다. 따라서 큐 포화·역압
경계는 이 시험에서 실기로 검증하지 않았습니다. 실제 마이크·리샘플링·VAD·앱 세션 이벤트·
UI·중지·취소를 30분 동안
실행한 종단 실기는 아니며 계속 `NOT_RUN`입니다. 한 환경의 회귀 기준일 뿐 모든 PC·언어·억양의
성능을 보장하지 않습니다. 9개 언어 정답 음원, WER/CER, 실제 장시간 회의와 여러 Intel·AMD PC
실기도 `NOT_RUN`입니다.

무료 0.1.x는 사용자·좌석 제한이 없고 Tiny·Base·Small·Medium·Large-v3 Turbo를 모두
제공합니다. 파일당 15분, 받아쓰기 하루 15회, 실시간 자막 세션당 5분, 회의록 하루
3회의 기능 제한이 있으며 영어 번역은 제공하지 않습니다. 유료 플랜·결제·유료 라이선스
판매도 아직 없습니다.

음성·전사·자막·추출식 회의록은 사용자 PC에서 처리되며 PCSSAK 처리 서버로 보내지
않습니다. 계정·광고·텔레메트리·사용 분석·추적 SDK·자동 오류 업로드가 없습니다.

공개 설치본은 AVX2를 지원하는 Windows x64용 CPU 빌드이며 Windows Authenticode로
서명되지 않았습니다. Defender·SmartScreen·Smart App Control을 끄지 말고 공식 v0.1.1
고정 GitHub 릴리스와 `SHA256SUMS.txt`를 확인하십시오. Tauri 업데이터 서명은 앱 내
업데이트 무결성을 보호하지만 Windows 게시자 신원을 뜻하지 않습니다.

깨끗한 별도 Windows 11 Home/Pro 설치, 설치된 0.1.0→0.1.1 정상·변조 업데이트, 실제 마이크·
VAD·세션·UI·중지·취소 30분 종단 실기, 9개 언어 정답 음원, 여러 오디오 장치, DPI·IME·
다중 모니터, 원어민 UI, 보안 제품과 출시국 법률 검토는 모두 `NOT_RUN`입니다. PCSSAK은
실행하지 않은 검사를 통과했다고 주장하지 않고 무료 얼리액세스에서 투명하게 검증·개선합니다.
