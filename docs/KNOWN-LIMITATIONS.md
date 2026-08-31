# Known Limitations — PCssak ModuSori v0.1.5

[한국어](KNOWN-LIMITATIONS.ko.md) · [v0.1.5 release](https://github.com/pcssakinc/pcssak-modusori-releases/releases/tag/v0.1.5) · [System requirements](../SYSTEM_REQUIREMENTS.md)

This document describes the Free Early Access boundary. It prevents an untested or absent feature
from being mistaken for a supported promise.

> [!CAUTION]
> The owner approved publishing the free v0.1.5 Early Access build before repeating the original
> `UnknownIssuer` scenario on the same clean Windows PC that reported it. That installed
> candidate → Tiny/Base download → model load → app restart path is therefore `NOT_RUN`, not a
> pass. It must be tested immediately after publication, and any required correction will use a
> higher version without replacing the fixed v0.1.5 assets.

## Platform and installer

- Only a Windows x64 CPU build is provided. AVX2 is mandatory.
- The primary target is a currently serviced Windows 11 Home or Pro x64 installation, but the
  clean-install matrix remains `NOT_RUN`.
- Windows x86, Windows on ARM, Windows S mode, Windows Server, macOS, Linux, and Wine are not
  supported and no installer is provided for them.
- Windows 10 22H2 is out of Microsoft support. Compatibility observation is `NOT_RUN`; it is not
  a supported platform.
- CUDA and Vulkan are not included. Large models can be slow on CPU-only hardware.
- The installer and app are not Windows Authenticode-signed. SmartScreen, Smart App Control,
  Defender, another security product, or organisation policy can warn or block execution.
- Current-user install, repair, update, uninstall, and WebView2 behavior has not completed a clean
  Home/Pro device matrix.

## 0.1.5 cumulative processing and compatibility changes

- Main-interface scaling uses Tauri/WebView2 native page zoom and can be set to 100%, 110%, 125%,
  or 150%. The app shell and shared main-content region now have finite WebView boundaries and the
  main region is vertically scrollable and keyboard-focusable.
- The live-caption overlay keeps its separate text-size setting. The automated layout contracts
  do not replace the `NOT_RUN` real WebView2 DPI 100–200%, multi-monitor, window-resize, touchpad,
  touch, IME, assistive-technology, and nine-language native-speaker matrix.
- Recording length freezes when capture ends. Stopping and processing are separate states, and
  processing shows elapsed time and measured recognition backlog rather than a completion estimate.
- Live final utterances use one-candidate greedy decoding for CPU responsiveness. Batch file
  transcription retains an accuracy-focused beam size of five; neither path guarantees correct
  output for a specific speaker or recording.
- Duplicate stop requests are suppressed. Cancelling remaining transcription keeps text already
  recognized and closes delivery of later results for that session, but actual 30-minute
  microphone/session/UI/stop/cancel real-device testing remains `NOT_RUN`.
- Dictation recording, input cleanup, remaining conversion, cancellation, and failure have separate
  states and actions. Final work is scoped to its owning session, but this does not turn automated
  ownership and cancellation tests into a real microphone or long-meeting pass.
- Model-download HTTPS now follows the Windows platform certificate chain and supported Windows
  system-proxy settings. This replaces the former copied-root/WebPKI path that could report
  `invalid peer certificate: UnknownIssuer` even when Windows and the browser trusted the server.

## Speech recognition and models

- Whisper output can omit, substitute, duplicate, or mis-segment words, names, numbers, accents,
  and punctuation. It is not a certified record or professional advice.
- Tiny, Base, Small, Medium, and Large-v3 Turbo are all selectable without payment, but no model is
  guaranteed to be accurate or fast for a particular language, speaker, microphone, noise level,
  or CPU.
- A deterministic 30-minute real-time-paced live-final test on one development PC passed only the
  automatic functional-completion, queue-drain, result-consistency, and inference-throughput gate:
  146/146 chunks completed without processing failures, at 2.569096× realtime inference and
  standard RTF 0.389242. Memory had no automatic pass threshold; working set/private increased by
  19,968,000/18,616,320 bytes from the first full chunk to the end, but one manual observation
  neither proves nor disproves a long-duration leak. The 36-slot configuration was used, but
  maximum observed depth was one, so saturation and backpressure were not exercised. It did not
  exercise an actual microphone, resampling, VAD, application session events, UI, stop, or
  cancellation. Actual long-duration meetings and owned nine-language WER/CER,
  latency, real-time factor, and memory benchmarks remain `NOT_RUN` for v0.1.5.
- Models are not bundled. First use needs a Hugging Face download, storage, and successful pinned
  size and SHA-256 verification.
- Certificate and hostname verification remain mandatory. There is no invalid-certificate bypass,
  HTTP fallback, plaintext redirect, or automatic certificate-authority installation. Never turn off
  certificate verification, Windows security, organisation certificate policy, or antivirus TLS
  inspection to make a model download succeed. Record the complete non-sensitive error and stop.
- Supported system-proxy settings do not guarantee every enterprise network. PAC/WPAD-only,
  WinHTTP-only, integrated-authentication, TLS-inspection, and unusual per-scheme proxy environments
  still need separate validation. A trusted enterprise root must be deployed by the responsible
  administrator through normal Windows policy, not installed or accepted by the app.
- The release is CPU-only. Model memory guidance is not a validated total-system RAM minimum.

## Features not included

- **No speaker diarization.** Transcript segments do not identify who spoke. A stereo or two-channel
  signal is not converted into reliable multi-speaker labels.
- **No local or remote generative LLM.** Meeting notes are deterministic and extractive. They can
  miss context or choose unhelpful lines and still require human review.
- **No English translation.** The Free Early Access UI blocks translation even when an underlying
  model can technically perform an X-to-English Whisper task.
- No cloud account, team administration, collaboration workspace, cloud sync, online transcription,
  paid plan, payment, or paid licence is offered.

## Dictation

- Free Early Access allows 15 dictation uses per local calendar day.
- Automatic text input is limited to a verified Windows target. Password fields, an invalid or
  changed target, mismatched integrity level, residual modifier keys, or inaccessible focus are
  refused rather than guessed.
- Elevated applications, browsers, Office applications, Korean and Japanese IME, multiple
  monitors, minimised windows, and rapid start/stop combinations remain `NOT_RUN` on a real matrix.
- Voice commands do not create a general-purpose remote-control or automation interface.

## Live captions and audio devices

- One session uses either microphone or Windows system audio, not both.
- Free Early Access stops a caption session after 30 minutes; the user may start another session.
- Loopback capture depends on a compatible active Windows output endpoint. Protected streams,
  exclusive-mode devices, Bluetooth profiles, docks, virtual devices, sleep/resume, and hot-plug
  behavior can differ.
- Caption history is bounded. Important text should be reviewed and exported; it is not a permanent
  legal transcript.
- Recording and system-audio law, participant consent, workplace policy, and content rights remain
  the user's responsibility.

## File transcription and export

- Free Early Access accepts at most 15 minutes per file.
- Supported extensions are WAV, MP3, M4A, MP4, FLAC, OGG, OGA, AAC, MKA, and MKV. A recognised
  extension does not guarantee support for every codec, damaged container, encrypted stream, or
  unusual metadata layout.
- SRT, WebVTT, Markdown, and TXT export is available. There is no subtitle timeline editor, video
  burn-in, FFmpeg integration, or speaker track.
- Save cancellation, permissions, full disks, file locks, path policy, and external modification
  can prevent export. Review the final file in its destination application.

## Meeting notes

- Free Early Access allows three summaries per local calendar day.
- Notes select and organise source lines using deterministic rules. They are not generative and do
  not understand every decision, owner, deadline, negation, joke, or domain term.
- The source transcript must be checked against the audio first. A transcription error can be
  preserved or emphasised in the notes.
- No speaker attribution, cloud model, Ollama, llama.cpp, or other local LLM is included.

## Recovery, privacy, and data

- Unexpected-exit recovery contains bounded text and timing, not source audio, source paths, or
  filenames. It is not a complete project backup.
- Recovery uses current-user Windows DPAPI, expires after at most seven days, and rejects the whole
  file if it is corrupt, expired, unknown, or outside policy. Normal exit or user discard removes
  the draft.
- DPAPI does not protect against an administrator, malware running as the same Windows user,
  unlocked-device access, memory inspection, backup software, or cloud synchronisation.
- The app has no telemetry or automatic crash upload. Model, update, WebView2, external-link,
  email, and public GitHub requests can expose ordinary network metadata to those providers.
- Public issue attachments are not local or private. Never upload real audio, transcripts, paths,
  credentials, customer data, or company secrets.

## Updates

- Startup makes one automatic check attempt; manual checks are separate attempts. Network or GitHub
  failure must not be interpreted as proof that no update exists.
- The user approves download and installation. Active work or unsaved results can block it.
- Tauri updater signatures protect update bytes but are not Authenticode publisher identity.
- Separate installed-machine public v0.1.3 → v0.1.5 success, restart race, rollback, replay, and
  tampered-update tests are `NOT_RUN` for v0.1.5.

## Verification disclosure

The following real-device work is not represented as passed:

| Validation | v0.1.5 status |
| --- | --- |
| Deterministic 30-minute live-final test on one development PC | Functional completion, queue drain, result consistency, and throughput gate PASS; memory manually observed without a pass threshold; 36-slot configuration used but saturation/backpressure not exercised; actual microphone/session/UI path excluded |
| Original `UnknownIssuer` clean PC: install v0.1.5 candidate → Tiny download → Base download → model load → app restart | `NOT_RUN` — owner-approved post-publication validation for free Early Access; this is not evidence that the original PC is fixed |
| Development-PC Windows platform TLS initialization, untrusted local-certificate rejection, Hugging Face one-byte Range, and full Tiny pinned-size/SHA-256 download | PASS within those automated/development-PC boundaries only |
| Manual system proxy, trusted TLS-inspection CA, untrusted CA, PAC/WPAD, and authenticated proxy | NOT_RUN |
| Clean Windows 11 Home x64 install, launch, core work, uninstall | NOT_RUN |
| Clean Windows 11 Pro x64 install, launch, core work, uninstall | NOT_RUN |
| Windows 10 22H2 compatibility observation | NOT_RUN; Windows 10 is out of Microsoft support |
| Intel and AMD device matrix, microphones, loopback, sleep, device removal | NOT_RUN |
| WebView2 DPI 100–200%, multi-monitor, window resize, touchpad, touch, IME, and assistive technology | NOT_RUN |
| Tray, duplicate launch, and update-restart races | NOT_RUN |
| Actual 30-minute microphone/VAD/session/UI/stop/cancel flow | NOT_RUN |
| Actual long-meeting and nine-language owned benchmark audio | NOT_RUN |
| Nine-language native-speaker review of every screen and error | NOT_RUN |
| Defender, SmartScreen, Smart App Control, and third-party security-product behavior | NOT_RUN |
| Normal and tampered in-app update on a separate installed machine | NOT_RUN |
| Launch-jurisdiction legal counsel and localized legal translation review | NOT_RUN |

See [Quality and safety](QUALITY-AND-SAFETY.md) for the automated and human validation layers.
