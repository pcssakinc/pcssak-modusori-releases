# Third-Party Notices / 제3자 고지

The authoritative v0.1.5 component inventory, locked sources, notices, and complete collected
licence texts are in [THIRD-PARTY-NOTICES.txt](THIRD-PARTY-NOTICES.txt). That file is generated
from the exact Windows x64 Cargo dependency graph and runtime npm graph used by the release
workspace. The fixed GitHub Release also publishes the corresponding SPDX SBOM.

PCssak ModuSori's proprietary application portions remain governed by [LICENSE](LICENSE) and the
[EULA](EULA.md). Every third-party component remains governed by its own licence; neither the
proprietary licence nor this summary removes rights granted by a third-party licence.

## Distribution boundary

- The Windows executable includes Tauri/Rust/React runtime components, whisper.cpp through
  `whisper-rs-sys`, and the Symphonia media-decoding family. Exact package names, versions,
  source locations, and notice-text hashes are in the generated text notice.
- Tiny, Base, Small, Medium, and Large-v3 Turbo model weights are **not bundled**. The user chooses
  whether to download a fixed model directly from
  [`ggerganov/whisper.cpp` on Hugging Face](https://huggingface.co/ggerganov/whisper.cpp). The app
  checks its pinned byte length and SHA-256 before use.
- Microsoft Edge WebView2 Runtime is an external Microsoft component required for the UI and can
  be obtained by the Windows installation process when absent.
- v0.1.5 does not bundle or download FFmpeg, a generative LLM, Ollama, llama.cpp, a speaker-
  diarization engine, CUDA, or Vulkan runtime components.

See [Third-party source availability](docs/THIRD-PARTY-SOURCE.md) for the exact upstream and
corresponding-source routes relevant to the distributed components.

Third-party names identify technology and provenance only. PCSSAK is not affiliated with or
endorsed by OpenAI, Hugging Face, Microsoft, GitHub, or the upstream projects.

---

v0.1.5의 정확한 구성요소 목록·고정 원본·고지·수집한 라이선스 전문은
[THIRD-PARTY-NOTICES.txt](THIRD-PARTY-NOTICES.txt)에 있습니다. 이 파일은 릴리스 작업공간의
정확한 Windows x64 Cargo 의존성 그래프와 런타임 npm 그래프에서 생성합니다. 고정 GitHub
릴리스에는 이에 대응하는 SPDX SBOM도 게시합니다.

PCssak ModuSori의 독점 부분은 [LICENSE](LICENSE)와 [EULA](EULA.md)를 따릅니다. 제3자
구성요소는 각자의 라이선스를 계속 따르며 독점 라이선스나 이 요약이 제3자 라이선스의 권리를
제한하지 않습니다.

## 배포 경계

- Windows 실행 파일은 Tauri/Rust/React 런타임 구성요소, `whisper-rs-sys`를 통한
  whisper.cpp, Symphonia 미디어 디코딩 계열을 포함합니다. 정확한 이름·버전·원본 위치·고지
  해시는 생성된 텍스트 고지에 있습니다.
- Tiny·Base·Small·Medium·Large-v3 Turbo 모델 가중치는 **동봉하지 않습니다.** 사용자가
  [`ggerganov/whisper.cpp` Hugging Face 저장소](https://huggingface.co/ggerganov/whisper.cpp)에서
  고정 모델을 받을지 선택하며 앱이 고정 바이트 길이·SHA-256을 확인합니다.
- Microsoft Edge WebView2 Runtime은 UI에 필요한 외부 Microsoft 구성요소이며 없으면 Windows
  설치 과정이 받을 수 있습니다.
- v0.1.5는 FFmpeg·생성형 LLM·Ollama·llama.cpp·화자분리 엔진·CUDA·Vulkan 런타임을
  동봉하거나 내려받지 않습니다.

배포 구성요소의 상위 원본과 대응 원본 경로는
[제3자 원본 소스 안내](docs/THIRD-PARTY-SOURCE.md)를 확인하십시오.

제3자 이름은 기술·출처 식별용입니다. PCSSAK은 OpenAI·Hugging Face·Microsoft·GitHub 또는
상위 프로젝트와 제휴하거나 보증받지 않았습니다.
