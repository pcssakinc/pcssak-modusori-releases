# Third-Party Source Availability / 제3자 원본 소스 안내

This page supplements the generated [third-party notice](../THIRD-PARTY-NOTICES.txt). The generated
notice and the SPDX SBOM attached to the exact GitHub Release determine the final package names,
versions, licences, and locked sources. This page does not turn the private PCssak ModuSori
application source into open source.

## Bundled speech engine

PCssak ModuSori uses `whisper-rs 0.16.0` and `whisper-rs-sys 0.15.0`. The latter contains the
whisper.cpp/ggml source compiled into the CPU-only Windows executable. The bindings are under the
Unlicense and the vendored whisper.cpp files retain their MIT licence.

- whisper-rs source: [Codeberg upstream](https://codeberg.org/tazz4843/whisper-rs)
- exact `whisper-rs-sys 0.15.0` crate source archive:
  [crates.io download](https://crates.io/api/v1/crates/whisper-rs-sys/0.15.0/download)
- whisper.cpp upstream: [ggml-org/whisper.cpp](https://github.com/ggml-org/whisper.cpp)
- exact licence texts and source records: [THIRD-PARTY-NOTICES.txt](../THIRD-PARTY-NOTICES.txt)

The public v0.1.1 build does not enable the Cargo CUDA or Vulkan features.

## MPL-2.0 source code form

The Windows graph contains unmodified MPL-2.0 crates. The generated notice lists the exact package
versions and the full MPL-2.0 text. Source Code Form can be obtained from the exact-version
crates.io records and archives below or from the listed upstream repository.

The v0.1.1 graph includes these groups:

- Symphonia 0.5.5 and its selected codec, format, metadata, and utility crates —
  [upstream](https://github.com/pdeljanov/Symphonia),
  [exact core package record](https://crates.io/api/v1/crates/symphonia/0.5.5), and
  [exact core crate archive](https://crates.io/api/v1/crates/symphonia/0.5.5/download)
- `cssparser 0.36.0` and `cssparser-macros 0.6.1` —
  [upstream](https://github.com/servo/rust-cssparser),
  [`cssparser` record](https://crates.io/api/v1/crates/cssparser/0.36.0) and
  [archive](https://crates.io/api/v1/crates/cssparser/0.36.0/download), and
  [`cssparser-macros` record](https://crates.io/api/v1/crates/cssparser-macros/0.6.1) and
  [archive](https://crates.io/api/v1/crates/cssparser-macros/0.6.1/download)
- `dtoa-short 0.3.5` — [upstream](https://github.com/upsuper/dtoa-short),
  [exact package record](https://crates.io/api/v1/crates/dtoa-short/0.3.5), and
  [exact archive](https://crates.io/api/v1/crates/dtoa-short/0.3.5/download)
- `option-ext 0.2.0` — [upstream](https://github.com/soc/option-ext),
  [exact package record](https://crates.io/api/v1/crates/option-ext/0.2.0), and
  [exact archive](https://crates.io/api/v1/crates/option-ext/0.2.0/download)
- `selectors 0.36.1` — [upstream](https://github.com/servo/stylo),
  [exact package record](https://crates.io/api/v1/crates/selectors/0.36.1), and
  [exact archive](https://crates.io/api/v1/crates/selectors/0.36.1/download)

For an exact archive, use `https://crates.io/api/v1/crates/<package>/<version>/download` with the
name and version in the generated notice. PCSSAK does not modify these crate source files in
v0.1.1. If a later release modifies, replaces, bundles differently, or cannot reproduce an exact
source archive, its source-availability and licence review must be updated before publication.

## Optional Whisper model weights

Model weights are not part of the installer or this GitHub Release. When the user requests one,
the app downloads one of five fixed GGML files directly from
[`ggerganov/whisper.cpp`](https://huggingface.co/ggerganov/whisper.cpp): Tiny, Base, Small, Medium,
or Large-v3 Turbo. The original Whisper project and model weights are published by OpenAI under
the MIT licence; conversion and hosting do not imply endorsement. The app contains the expected
filename, byte length, and SHA-256 and rejects a mismatch.

## External Microsoft runtime

Microsoft Edge WebView2 Runtime is not PCSSAK source code. It is governed by Microsoft's terms and
distribution guidance. The Windows installer can use Microsoft's delivery mechanism if the
runtime is absent. See [Microsoft WebView2 distribution guidance](https://learn.microsoft.com/microsoft-edge/webview2/concepts/distribution).

## Components not distributed in v0.1.1

No FFmpeg binary or codec pack, generative LLM, Ollama, llama.cpp, speaker-diarization engine,
CUDA runtime, or Vulkan runtime is bundled, mirrored, or offered for download by ModuSori 0.1.1.
Future inclusion would require a new exact binary/source inventory, licence and notice review,
security validation, and updated documentation; this page is not advance approval.

---

이 문서는 생성된 [제3자 고지](../THIRD-PARTY-NOTICES.txt)를 보충합니다. 정확한 GitHub
릴리스에 첨부한 생성 고지와 SPDX SBOM이 최종 패키지 이름·버전·라이선스·고정 원본의
기준입니다. 이 안내가 비공개 PCssak ModuSori 애플리케이션 소스를 오픈소스로 바꾸지는
않습니다.

## 동봉 음성 엔진

ModuSori는 `whisper-rs 0.16.0`과 `whisper-rs-sys 0.15.0`을 사용합니다. 후자는 CPU 전용
Windows 실행 파일에 컴파일되는 whisper.cpp/ggml 원본을 포함합니다. 바인딩은 Unlicense,
동봉 whisper.cpp 파일은 MIT 라이선스를 유지합니다. 정확한 원본·라이선스 경로는 위 영문
링크와 생성 고지를 사용하십시오. 공개 v0.1.1은 Cargo CUDA·Vulkan 기능을 켜지 않습니다.

## MPL-2.0 원본 소스 형식

Windows 그래프에는 수정하지 않은 MPL-2.0 크레이트가 있습니다. 생성 고지는 정확한 버전과
MPL-2.0 전문을 포함합니다. 위의 버전 고정 crates.io 패키지 기록·원본 압축 링크 또는 고지에
표시된 상위 저장소에서 Source Code Form을 받을 수 있습니다.

v0.1.1에는 Symphonia 0.5.5 계열, `cssparser 0.36.0`, `cssparser-macros 0.6.1`,
`dtoa-short 0.3.5`, `option-ext 0.2.0`, `selectors 0.36.1`이 포함됩니다. 정확한 압축 파일은
`https://crates.io/api/v1/crates/<패키지>/<버전>/download` 형식으로 받을 수 있습니다.
v0.1.1은 이 크레이트 원본 파일을 수정하지 않습니다. 향후 수정·교체·다른 방식 동봉 또는
정확한 원본 재현 불가가 생기면 공개 전에 원본 제공·라이선스 검토와 문서를 새로 갱신해야
합니다.

## 선택형 Whisper 모델

모델 가중치는 설치본이나 GitHub 릴리스에 포함하지 않습니다. 사용자가 요청하면 Tiny·Base·
Small·Medium·Large-v3 Turbo 중 고정 GGML 파일 하나를 `ggerganov/whisper.cpp`에서 직접
받습니다. 원본 Whisper 프로젝트·모델은 OpenAI가 MIT 라이선스로 공개했으며 변환·호스팅은
제휴나 보증을 뜻하지 않습니다. 앱은 예상 파일명·바이트 길이·SHA-256을 내장하고 불일치를
거부합니다.

## 외부 Microsoft 런타임과 미배포 구성요소

Microsoft Edge WebView2 Runtime은 PCSSAK 원본이 아니며 Microsoft 조건을 따릅니다. 없으면
Windows 설치기가 Microsoft 전달 방식을 사용할 수 있습니다. v0.1.1에는 FFmpeg·코덱 팩·
생성형 LLM·Ollama·llama.cpp·화자분리 엔진·CUDA·Vulkan 런타임을 동봉·미러링·다운로드
제공하지 않습니다. 향후 포함하려면 정확한 바이너리·원본 인벤토리, 라이선스·고지, 보안
검증과 문서를 새로 작성해야 하며 이 문서는 사전 승인이 아닙니다.
