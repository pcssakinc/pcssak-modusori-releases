# PCssak ModuSori — Official Windows Downloads

[한국어](README.ko.md) · [Product website](https://pcssak.com/modusori) · [Install guide](docs/INSTALLATION.md) · [v0.1.7 release](https://github.com/pcssakinc/pcssak-modusori-releases/releases/tag/v0.1.7)

**Turn speech into text on your own Windows PC.** PCssak ModuSori is a local-first dictation,
live-caption, media-transcription, and extractive meeting-notes application powered by five
optional Whisper models.

> **Repository scope:** This is the official public binary-distribution, update, documentation,
> and issue-tracking repository. The application source is private and proprietary; this public
> repository is not an open-source source-code release.

> **Publication gate:** A public installer is approved only when the fixed GitHub Release for its
> exact tag is visible and includes its integrity, signature, provenance, legal, notice, SBOM, and
> release-note assets. If the release page or those required assets are absent, there is no
> approved public PCssak ModuSori build.

## Free Version 0.1.7

Version 0.1.7 is a cumulative patch for short utterances, language reuse, stopping, and preservation
of recognized text. It also includes 0.1.6's non-capturing device preflight and one confirmation per
recording session, plus earlier Windows model-download trust and result-recovery corrections.
A document describing this version does not open the publication gate above.

### What changed in 0.1.7

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

On first launch, the chosen UI language supplies a recognition-language default only when the user
has not selected one explicitly. Existing installations and explicit choices are preserved.

Actual microphones, long sessions, automatic-versus-fixed-language timing, nine-language accuracy
and false positives, and installed direct updates remain `NOT_RUN`. Earlier user confirmation that
model download works on the PC that reported `UnknownIssuer` does not complete the exact 0.1.7
model-load and app-restart test. See [Known limitations](docs/KNOWN-LIMITATIONS.md).

### Included features

- Dictation into a verified Windows input target with a configurable global hotkey
- Live captions from either a microphone or Windows system audio
- Batch transcription of WAV, MP3, M4A, MP4, FLAC, OGG, OGA, AAC, MKA, and MKV media
- SRT, WebVTT, Markdown, and plain-text export
- Deterministic extractive meeting notes with decisions and action-item assistance
- Tiny, Base, Small, Medium, and Large-v3 Turbo Whisper models, downloaded only when requested
- One automatic update-check attempt after startup, plus user-requested manual checks
- Single-instance protection, coordinated safe exit, and encrypted unexpected-exit draft recovery
- English, Korean, Japanese, German, French, Latin American Spanish, Brazilian Portuguese,
  Turkish, and Russian user interfaces

Meeting notes are rule-based and extractive. **Speaker diarization, a local generative LLM, and
English translation are not included.**

### Free 0.1.x limits

| Function | Limit |
| --- | --- |
| Users and seats | No limit |
| Whisper models | All five registered models |
| File transcription | Up to 15 minutes per file |
| Dictation | 15 uses per local calendar day |
| Live captions | 30 minutes per session; a new session may be started |
| Meeting notes | Three summaries per local calendar day |
| English translation | Not available |

## Platform boundary

- Release target: Windows x64 with an AVX2/FMA/F16C-capable CPU
- Primary target: a currently serviced Windows 11 Home or Pro x64 installation
- CPU-only build; public CUDA and Vulkan builds are not provided
- Microsoft Edge WebView2 Runtime is required
- Not supported: Windows x86, Windows on ARM, Windows S mode, Windows Server, macOS, Linux, or Wine
- Windows 10 22H2 is only an unvalidated compatibility observation target, not a supported platform

Clean Windows, actual-microphone long-duration, device-matrix, native-language, security-product,
updater, and launch-region legal testing remains explicitly `NOT_RUN` for v0.1.7. Read the
[v0.1.7 release](https://github.com/pcssakinc/pcssak-modusori-releases/releases/tag/v0.1.7), [known limitations](docs/KNOWN-LIMITATIONS.md), and
[system requirements](SYSTEM_REQUIREMENTS.md) before installation.

## Download and integrity

Download only from the [fixed official v0.1.7 release](https://github.com/pcssakinc/pcssak-modusori-releases/releases/tag/v0.1.7)
or the official PCSSAK download page.

1. Confirm that the release tag is exactly `v0.1.7` and that it is not a source archive, mirror,
   repack, portable build, MSI, x86 build, or ARM build.
2. Read `RELEASE-NOTES.md` and `BUILD-PROVENANCE.json` from the same release.
3. Calculate the downloaded installer's SHA-256 and compare it with the installer's entry in
   `SHA256SUMS.txt` from that same fixed release.
4. Keep Microsoft Defender, SmartScreen, Smart App Control, and organisation policy enabled.
5. Stop if a filename, digest, version, source commit, or required release asset does not agree.

No installer digest or size is hard-coded in these repository documents. The exact values are
created from the final release bytes and published only in the fixed release assets.

> **v0.1.7 release-note records:**
> The fixed Release asset
> [`RELEASE-NOTES.md`](https://github.com/pcssakinc/pcssak-modusori-releases/releases/download/v0.1.7/RELEASE-NOTES.md)
> is the distribution note and includes final-build, verification-boundary, and security details;
> its file digest is listed in
> [`SHA256SUMS.txt`](https://github.com/pcssakinc/pcssak-modusori-releases/releases/download/v0.1.7/SHA256SUMS.txt).
> [`latest.json`](https://github.com/pcssakinc/pcssak-modusori-releases/releases/download/v0.1.7/latest.json)
> and [`UPDATE-RELEASE.json`](https://github.com/pcssakinc/pcssak-modusori-releases/releases/download/v0.1.7/UPDATE-RELEASE.json)
> embed updater-facing `notes`. `UPDATE-RELEASE.json`'s `notes_sha256` hashes exactly that UTF-8
> `notes` value, not either Markdown file.

> [!WARNING]
> The v0.1.7 installer and application are not Windows Authenticode-signed. Windows may show
> **Unknown publisher**, **Windows protected your PC**, or block execution under Smart App
> Control or organisation policy. The mandatory Tauri updater `.sig` protects the in-app update
> bytes but is not an Authenticode publisher identity. Do not disable Windows security controls
> to install the application.

## Privacy and network use

Speech recognition, dictation, captions, file transcription, and extractive notes run on the
user's device. The app has no PCSSAK account, advertising, telemetry, usage analytics, tracking
SDK, or automatic crash upload. Audio and transcripts are not sent to a PCSSAK processing server.

Network access can occur only when the user requests a model from the fixed
`ggerganov/whisper.cpp` Hugging Face repository, for a public GitHub Release update check or a
user-approved update download, when Windows needs WebView2, or when the user opens an external
link. Those providers can process ordinary HTTPS metadata such as IP address, time, user agent,
and requested asset. See the complete [Privacy Notice](PRIVACY.md).

Model-download HTTPS follows Windows platform trust and supported system-proxy settings. Do not
disable certificate or hostname verification, Windows security, organisation certificate policy,
or antivirus TLS inspection to work around a download error. Do not use an HTTP fallback or an
untrusted mirror. PAC/WPAD-only, WinHTTP-only, integrated-authentication, TLS-inspection, and other
enterprise proxy combinations remain separately unvalidated.

Unexpected-exit recovery stores bounded editing text and timing without source paths or filenames,
encrypts the file with current-user Windows DPAPI, and rejects expired or corrupt data. This does
not protect against an administrator or malware running as the same Windows user.

## Help improve ModuSori

- Use the [bug report form](../../issues/new?template=bug-report.yml) for a defect you reproduced.
- Use the [feature request form](../../issues/new?template=feature-request.yml) for a recurring
  user problem and desired outcome.
- Read [Support](SUPPORT.md) before sharing screenshots or technical details.
- Report exploitable security issues privately under [Security](SECURITY.md).

Never post original audio, private transcripts, customer data, credentials, personal paths,
licence keys, or confidential work in a public issue. AI-assisted reports must still be reproduced
and checked by the submitter.

## Documentation

- [Korean introduction](README.ko.md)
- [v0.1.7 release and release notes](https://github.com/pcssakinc/pcssak-modusori-releases/releases/tag/v0.1.7)
- [System requirements](SYSTEM_REQUIREMENTS.md)
- [Installation and update](docs/INSTALLATION.md)
- [Known limitations](docs/KNOWN-LIMITATIONS.md)
- [Quality and safety](docs/QUALITY-AND-SAFETY.md)
- [EULA](EULA.md) and [Privacy Notice](PRIVACY.md)
- [Third-party notices](THIRD-PARTY-NOTICES.md) and [source availability](docs/THIRD-PARTY-SOURCE.md)
- [Support](SUPPORT.md), [Security](SECURITY.md), and [issue guidelines](CONTRIBUTING.md)

PCssak ModuSori binaries are licensed, not sold, under the bundled EULA. `PCSSAK` is the
publisher and software-brand display name; that wording does not by itself assert a registered
legal-entity form. Third-party components remain under their own licences. PCSSAK is not
affiliated with or endorsed by OpenAI, Hugging Face, GitHub, Microsoft, or the upstream projects.
