# PCssak ModuSori — Official Windows Downloads

[한국어](README.ko.md) · [Product website](https://pcssak.com/modusori) · [Install guide](docs/INSTALLATION.md) · [v0.1.0 release](https://github.com/pcssakinc/pcssak-modusori-releases/releases/tag/v0.1.0)

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

## Free Early Access 0.1.0

Version 0.1.0 begins real-user compatibility, accuracy, and usability validation. It does not
claim that every device, language, or jurisdiction has already been validated.

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
English translation are not included.** No paid plan, payment, or paid licence is offered for
this release.

### Free 0.1.x limits

| Function | Limit |
| --- | --- |
| Users and seats | No limit |
| Whisper models | All five registered models |
| File transcription | Up to 15 minutes per file |
| Dictation | 15 uses per local calendar day |
| Live captions | Five minutes per session; a new session may be started |
| Meeting notes | Three summaries per local calendar day |
| English translation | Not available |

## Platform boundary

- Release target: Windows x64 with an AVX2-capable CPU
- Primary target: a currently serviced Windows 11 Home or Pro x64 installation
- CPU-only build; public CUDA and Vulkan builds are not provided
- Microsoft Edge WebView2 Runtime is required
- Not supported: Windows x86, Windows on ARM, Windows S mode, Windows Server, macOS, Linux, or Wine
- Windows 10 22H2 is out of Microsoft support and is only an unvalidated compatibility
  observation target, not a supported platform

Clean Windows, device, long-duration, native-language, security-product, updater, and launch-region
legal testing remains explicitly `NOT_RUN` for v0.1.0. Read the
[release notes](RELEASE_NOTES_v0.1.0.md), [known limitations](docs/KNOWN-LIMITATIONS.md), and
[system requirements](SYSTEM_REQUIREMENTS.md) before installation.

## Download and integrity

Download only from the [fixed official v0.1.0 release](https://github.com/pcssakinc/pcssak-modusori-releases/releases/tag/v0.1.0)
or the official PCSSAK download page.

1. Confirm that the release tag is exactly `v0.1.0` and that it is not a source archive, mirror,
   repack, portable build, MSI, x86 build, or ARM build.
2. Read `RELEASE-NOTES.md` and `BUILD-PROVENANCE.json` from the same release.
3. Calculate the downloaded installer's SHA-256 and compare it with the installer's entry in
   `SHA256SUMS.txt` from that same fixed release.
4. Keep Microsoft Defender, SmartScreen, Smart App Control, and organisation policy enabled.
5. Stop if a filename, digest, version, source commit, or required release asset does not agree.

No installer digest or size is hard-coded in these repository documents. The exact values are
created from the final release bytes and published only in the fixed release assets.

> **v0.1.0 release-note records:**
> [`RELEASE_NOTES_v0.1.0.md` at the immutable tag](https://github.com/pcssakinc/pcssak-modusori-releases/blob/v0.1.0/RELEASE_NOTES_v0.1.0.md)
> is the version-controlled base note. The fixed Release asset
> [`RELEASE-NOTES.md`](https://github.com/pcssakinc/pcssak-modusori-releases/releases/download/v0.1.0/RELEASE-NOTES.md)
> is the distribution copy and adds final-build and security-verification details; its file digest
> is listed in [`SHA256SUMS.txt`](https://github.com/pcssakinc/pcssak-modusori-releases/releases/download/v0.1.0/SHA256SUMS.txt).
> [`latest.json`](https://github.com/pcssakinc/pcssak-modusori-releases/releases/download/v0.1.0/latest.json)
> and [`UPDATE-RELEASE.json`](https://github.com/pcssakinc/pcssak-modusori-releases/releases/download/v0.1.0/UPDATE-RELEASE.json)
> embed updater-facing `notes`. `UPDATE-RELEASE.json`'s `notes_sha256` hashes exactly that UTF-8
> `notes` value, not either Markdown file.

> [!WARNING]
> The v0.1.0 installer and application are not Windows Authenticode-signed. Windows may show
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
- [Release notes](RELEASE_NOTES_v0.1.0.md)
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
