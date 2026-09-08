# Quality and Safety — PCssak ModuSori

[한국어](QUALITY-AND-SAFETY.ko.md) · [Known limitations](KNOWN-LIMITATIONS.md) · [Security](../SECURITY.md)

This document explains the engineering boundaries and evidence expected for the v0.1.7 Free Version release. It is not a certificate that the app is error-free, accurate for every language,
legally suitable in every jurisdiction, or approved by a security product.

## Local, user-controlled workflow

1. The user chooses a microphone, Windows system-audio source, or supported media file.
2. The app requires the applicable legal and recording-safety confirmations.
3. A locally installed, hash-verified Whisper model produces text on the PC.
4. The user reviews the transcript, captions, or extractive meeting notes.
5. Only an explicit save or copy action sends results to a user-chosen destination.

Free Version limits each live-caption session to 30 minutes and allows another session after
the limit. This product limit is not evidence that a real 30-minute microphone/session/UI path has
passed.

The app has no PCSSAK account, telemetry, advertising, usage analytics, tracking SDK, or automatic
crash upload. User audio and text are not sent to a PCSSAK processing server. Model, update,
WebView2, user-opened link, email, and GitHub traffic remains subject to each external provider's
network metadata processing. Public reports are not local or private.

## Recording and consent safety

- First use requires active acceptance of the complete EULA and Privacy Notice. A changed document
  version or hash requires renewed acceptance.
- Before each recording confirmation, the app checks the selected source without capturing audio.
  The first recording shows the full safety notice with exactly one unchecked confirmation; later
  sessions also require one unchecked confirmation. Missing devices stop the flow before that dialog.
- The UI and caption overlay identify active capture and provide a stop path.
- Microphone and system-audio recording can capture other people, notifications, copyrighted
  content, confidential discussion, or regulated information. The user must obtain every required
  permission and stop when consent is withdrawn.
- These controls remind and inform. They do not verify identity, age, authority, participant
  consent, workplace policy, or legal compliance.

## Dictation target safety

Global-hotkey dictation stores only an opaque backend target token. Before automatic input it
rechecks the target window and process, focus, password-field status, integrity level, input
desktop, and modifier-key state. If the verified target is unavailable or changed, it refuses
automatic input and returns control to ModuSori. This reduces accidental disclosure but cannot
make every third-party application or IME compatible.

## Result and exit safety

- Transcription and extractive notes can be wrong. Important results require comparison with the
  original audio and human review.
- Supported export formats are rendered by the backend and saved through a native dialog with a
  fixed extension and atomic replacement boundary.
- Recording, transcription, model changes, exports, summary work, and update installation share
  backend work gates to reduce races.
- Recording, stopping, and processing are separate user-visible states. Recording duration freezes
  when capture ends; processing reports elapsed time and measured backlog without inventing an
  estimated completion time.
- Duplicate stop requests are suppressed. Dictation's separate cancel-remaining action keeps text already
  recognized, closes delivery of later session output, and cooperatively cancels pending inference.
- Unsaved frontend results and unacknowledged backend output participate in close and update
  protection. Discarding results requires an explicit choice.
- Single-instance handling returns a second launch to the existing app instead of starting a
  second audio engine.

These controls reduce common loss and concurrency risks; they do not replace a separate backup.

## 0.1.7 speech-processing boundary

- Session language is reused after a final result contains at least six alphabetic characters,
  or two consecutive valid final results containing letters identify the same language. Numbers-only
  output and interim hypotheses cannot lock the language. This reduces dependence on one short
  first utterance; character count and agreement are not a language-confidence guarantee.
- Dictation submits pending audio after one second of silence following the final utterance's tail
  padding, while keeping an eight-second upper bound from utterance start. Stopping immediately
  after a brief click no longer extends the earlier utterance; resumed speech is retained.
  Submission timing is not total recognition latency.
- Normal stopping checks inference progress and actual computation in the same session. After
  60 seconds without activity or a 15-minute absolute limit, Dictation requests cooperative
  cancellation and preserves partial results. Live Captions keeps a failed session so the user can
  stop again. Live Captions has no direct cancel control during stopping; ending remaining work
  uses the app-exit confirmation flow, which can lose unfinalized output. Only Dictation's
  explicit-cancel path retains a five-second
  wait budget, not a promise that all computation physically ends within five seconds.
- A live-recognition noise filter uses silence evidence for phrase, credit, and repetition rules.
  Number, time, and amount text is preserved during normalization, and number-containing output is
  not shortened as repetition. Genuine emphasis and credit mentions have regression coverage.
  The filter does not apply to file transcription and can still make mistakes on real audio.
- CPU build settings are fixed independently of the build PC and shell environment. AVX2, FMA,
  and F16C are required and checked before speech processing. Build-setting checks do not prove
  a complete executable instruction audit or compatibility on every processor.

## Layout and accessibility safety

- The application shell has finite width and height boundaries matching the main WebView.
- Interface scaling uses the Tauri/WebView2 native page-zoom API rather than CSS `zoom`, keeping
  layout viewport, responsive breakpoints, and viewport-sized dialogs on one scale boundary.
- All four feature tabs stay inside one finite, vertically scrollable main-content region. The
  region can receive keyboard focus, shows a focus ring, and has an accessible name in all nine
  UI languages.
- Automated viewport, scale, keyboard, dialog, and rendered-layout contracts are regression
  evidence only. Real WebView2 DPI 100–200%, multi-monitor, window-resize, touchpad, touch, IME,
  and assistive-technology testing remains `NOT_RUN`.

## Unexpected-exit recovery

Recovery stores bounded edit text and timing without source audio, source paths, or filenames.
The complete file is protected with current-user Windows DPAPI, revision-checked, limited to
policy bounds, and expired after at most seven days. Corrupt, expired, unknown, or oversized data
is rejected as a whole. Normal exit and explicit discard remove the draft.

Recovery is not a complete project save and DPAPI is not protection against an administrator,
same-user malware, unlocked-device access, memory inspection, backups, or synchronisation tools.

## Model and update supply chain

- Models are optional and are downloaded only after user action from the fixed
  `ggerganov/whisper.cpp` Hugging Face source.
- Each model has a fixed filename, exact size, and pinned SHA-256. Partial downloads resume, but a
  final mismatch is rejected instead of installed.
- Model-download HTTPS uses Windows platform certificate verification and supported Windows
  system-proxy settings. Certificate and hostname checks stay enabled; there is no invalid-
  certificate bypass, HTTP fallback, or automatic certificate-authority installation.
- Update discovery uses this public release repository. Installation requires user approval and
  is blocked while protected work or unsaved output exists.
- The app verifies a Tauri installer signature, a separately signed release manifest, version,
  canonical URL, release-note digest, and installer SHA-256. Replay of an older or substituted
  candidate is rejected.
- A fixed release publishes hashes, source/build/signing provenance, legal documents, exact
  third-party notices, and an SPDX SBOM. Publication permits only the release process's exact
  asset allowlist.

The Tauri signature is not Windows Authenticode publisher identity. The v0.1.7 installer remains
unsigned to Windows and can be warned about or blocked.

## Automated validation layer

Before publication, the exact candidate is required to record successful results for:

- frontend contract tests and rendered DOM, keyboard, focus, accessibility, viewport, and scale
  interaction tests;
- TypeScript checking and production Vite build;
- Rust unit and integration tests, formatting, Clippy with warnings denied, and release build;
- single-instance, close, update, model, consent, recovery, quota, export, and concurrency contracts;
- nine-UI-language key, message-argument, locale-number, and error-catalogue consistency;
- dependency advisory, licence, source-policy, npm audit, secret-hygiene, and workflow static checks;
- legal Free Version gate and bundled-document equality;
- NSIS architecture/configuration, updater-signature, signed-manifest, SBOM, exact-asset, and
  SHA-256 verification.

The fixed release assets, release notes, and build provenance are the evidence for the published
candidate. A source-level pass does not prove a clean Windows installation, driver compatibility,
speech accuracy, long-duration behavior, native translation quality, security-product reputation,
or legal suitability.

Historical evidence from before 0.1.7, not a repeat measurement of this build: on one development PC, the deterministic 30-minute live-final test passed only the automatic
functional-completion, queue-drain, result-consistency, and inference-throughput gate. It completed
146/146 chunks without processing failures and measured 2.569096× realtime inference with standard
RTF 0.389242. Memory had no automatic pass threshold; working set/private increased by
19,968,000/18,616,320 bytes from the first full chunk to the end, but one manual observation
neither proves nor disproves a long-duration leak. The 36-slot product queue configuration was
used, but maximum observed depth was one, so saturation and backpressure were not exercised. This
evidence does not cover an actual microphone, resampling, VAD, application session events, UI,
stop, or cancellation for 30 minutes.

## Human and real-device validation layer

For v0.1.7, clean Windows 11 Home/Pro, Windows 10 observation, Intel/AMD and audio-device matrices,
actual 30-minute microphone/VAD/session/UI/stop/cancel operation, actual long-meeting and
nine-language owned benchmarks, nine-language native-speaker review, WebView2 DPI 100–200%,
multi-monitor, window-resize, touchpad, touch, IME and assistive-technology checks,
security-product behavior, separate-machine public v0.1.3 → v0.1.7 updater testing, and
launch-region legal review are all `NOT_RUN`. The exact matrix is in
[Known limitations](KNOWN-LIMITATIONS.md) and the
[fixed v0.1.7 release](https://github.com/pcssakinc/pcssak-modusori-releases/releases/tag/v0.1.7).

An earlier user report confirmed successful model download on the PC that reported `UnknownIssuer`.
That observation does not complete the exact 0.1.7 install → Tiny/Base download → model load → restart
path, which remains `NOT_RUN`. Do not disable certificate or hostname verification, antivirus TLS
inspection, or Windows and organisation security controls to work around a failure.

Real-user evidence complements the automated checks. A user report is
not automatically a pass or benchmark result; reproduction method, non-sensitive sample, device
context, expected output, and actual output are needed.

## Safe feedback

Use the public issue forms only for non-sensitive reproducible information. Never attach original
audio, private transcripts, customer data, credentials, personal paths, or company secrets. Report
exploitable vulnerabilities through [private security reporting](../SECURITY.md).
