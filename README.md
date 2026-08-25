# PCssak ModuSori - Official Windows Downloads

[한국어](README.ko.md) · [PCSSAK](https://pcssak.com) · [Latest release](https://github.com/pcssakinc/pcssak-modusori-releases/releases/latest)

> **Current status: no public installer has been released.** The application is still completing
> local quality, legal, compatibility, and brand-rights checks. Do not download a file claiming
> to be PCssak ModuSori from another location.

**Turn speech into text on your own Windows PC.** PCssak ModuSori is a local-first dictation,
live-caption, media-transcription, and extractive meeting-notes application powered by
downloadable Whisper models.

> **Repository scope:** This is the official public binary distribution, update, documentation,
> and issue-tracking repository. The PCssak ModuSori application source is private and
> proprietary; this public repository is not an open-source code release.

## Planned Free Early Access

- Windows 11 Home/Pro x64 is the primary validation target.
- Tiny, Base, Small, Medium, and Large v3 Turbo models can be selected without a paid model tier.
- Models are downloaded only when requested and are not bundled into the installer.
- The current `0.1.x` evaluation limits are 15-minute files, 15 dictation sessions per local day,
  5 minutes per live-caption session, and 3 meeting summaries per local day. English translation
  is not included in the free Early Access build. No paid plan is currently sold.
- Dictation, live subtitles, file transcription, and extractive meeting-note assistance run on
  the device after a model is installed.
- There is no PCSSAK account, advertising, analytics, tracking, or automatic crash upload in the
  planned Early Access build.
- A release build checks this repository once after startup for a signed update. Download and
  installation require user approval and are postponed while audio capture or file transcription
  is active.

The current feature set, language quality, legal terms, and compatibility claims remain under
validation. A release will appear here only after the published installer, checksums, updater
metadata, notices, and safety documents agree with the tested build.

## Download safety

When the first approved build is published, download it only from the
[latest official release](https://github.com/pcssakinc/pcssak-modusori-releases/releases/latest)
or the official PCSSAK product page.

- Compare the installer SHA-256 with `SHA256SUMS.txt` in the same release.
- Published release tags and assets are protected by GitHub immutable releases; a new version is
  issued instead of silently replacing an approved installer.
- The initial Early Access installer may not yet have a Windows Authenticode publisher
  signature. If so, Windows can show **Unknown publisher** or a SmartScreen warning.
- Never disable Microsoft Defender or SmartScreen to install the application.
- The in-app Tauri updater signature is mandatory but is separate from an Authenticode
  publisher signature.

## Privacy boundary

Speech, media contents, transcripts, subtitles, and meeting-note text are intended to stay on
the device. Network exceptions are model downloads from the official whisper.cpp model
repository and one update check per application launch against this repository. Those requests
can expose ordinary network metadata, such as IP address, time, requested file, and transfer
information, to the relevant hosting provider. Exact release behavior will be documented and
verified before publication.

## Help improve the beta

- Use the [bug report form](../../issues/new?template=bug-report.yml) for a reproducible defect.
- Use the [feature request form](../../issues/new?template=feature-request.yml) to explain the
  user problem and expected outcome.
- Read [Support](SUPPORT.md) before attaching logs, screenshots, transcripts, or media details.
- Report exploitable security issues privately under [Security](SECURITY.md).

Never post private audio, full transcripts, customer data, credentials, licence keys, personal
file paths, or confidential documents in a public issue.

PCssak ModuSori binaries will be licensed under the approved PCssak ModuSori EULA. Third-party
open-source components and Whisper model weights remain under their own licences and notices.
PCSSAK is not affiliated with or endorsed by OpenAI, Hugging Face, or GitHub.
