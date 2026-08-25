# PCssak ModuSori System Requirements

[한국어](SYSTEM_REQUIREMENTS.ko.md) · [Installation](docs/INSTALLATION.md) · [Known limitations](docs/KNOWN-LIMITATIONS.md)

These are the v0.1.0 Free Early Access release boundaries, not a guarantee that every machine
meeting them has been validated. Clean Windows and hardware-matrix testing is `NOT_RUN` for this
release.

## Required platform

| Area | v0.1.0 requirement or boundary |
| --- | --- |
| Operating system | Currently serviced Windows 11 Home or Pro, x64, with current security updates is the primary target |
| CPU architecture | x86-64 (`x64`) only |
| CPU instruction set | AVX2 is mandatory; the app stops before speech processing when AVX2 is unavailable |
| Runtime | Microsoft Edge WebView2 Runtime |
| Inference backend | CPU only; no public CUDA or Vulkan build |
| Installation scope | Per current Windows user; organisation policy and WebView2 can still affect installation |

Not supported: Windows x86, Windows on ARM, Windows S mode, Windows Server, macOS, Linux, and
Wine. Windows 10 22H2 is out of Microsoft support and is only an unvalidated compatibility
observation target, not a supported platform.

## Memory

No total-system RAM minimum has completed real-device validation. The app's model catalogue gives
the following model-only guidance; Windows, WebView2, media decoding, text results, and other
applications need additional memory. A value in this table must not be read as a sufficient
whole-PC memory configuration.

| Whisper model | Download size | Model memory guidance |
| --- | ---: | ---: |
| Tiny | about 74 MiB | 1 GB |
| Base | about 141 MiB | 1 GB |
| Small | about 465 MiB | 2 GB |
| Medium | about 1.43 GiB | 5 GB |
| Large-v3 Turbo | about 1.51 GiB | 6 GB |

Close memory-intensive applications and start with a smaller model on a constrained PC. Speed,
latency, and memory use vary by CPU, model, media length, and other system load; the real-device
performance matrix is `NOT_RUN` for v0.1.0.

## Storage

- The installer size is defined only by the final GitHub Release asset and is not estimated here.
- Each chosen model is stored under the app's local data directory. Multiple installed models use
  approximately the sum of their sizes.
- A resumable `.part` model file can coexist during download. The app checks the remaining model
  bytes plus a 64 MiB safety margin before transfer when Windows can report available space.
- Allow separate room for exported SRT, WebVTT, Markdown, and TXT files and for Windows temporary
  and update files.
- Keep important audio and exported results backed up outside the application data directory.

## Audio and media

- Dictation and microphone captions require a Windows recording device the current user may access.
- System-audio captions require an active Windows output endpoint that exposes loopback capture.
- Captions use either microphone or system audio in one session, not both.
- File transcription accepts WAV, MP3, M4A, MP4, FLAC, OGG, OGA, AAC, MKA, and MKV extensions,
  but an extension alone does not guarantee that a particular codec, protected stream, or damaged
  file can be decoded.
- Free Early Access accepts at most 15 minutes per file.

Microphone, loopback, Bluetooth, USB, docking, sleep/resume, hot-plug, protected media, and codec
combinations remain `NOT_RUN` on a real device matrix.

## Network access

Network access is required for the first download of each selected Whisper model. It can also be
used for update checks and user-approved updates, WebView2 installation when Windows needs it, and
links opened by the user. Once a verified model is installed, core local recognition is designed
to continue when an update check fails, but this offline behavior has not completed the full
real-device matrix.

Corporate proxies, TLS inspection, firewalls, GitHub or Hugging Face availability, disk quotas,
and organisation policy can prevent downloads. Do not weaken network or endpoint security controls
to work around a failure.

## Languages and accessibility

The UI includes English, Korean, Japanese, German, French, Latin American Spanish, Brazilian
Portuguese, Turkish, and Russian. Whisper is multilingual, but accuracy is not guaranteed by the
presence of a language choice. Nine-language native-speaker review, Narrator, high contrast,
multi-monitor, IME, and 125–200% DPI real-device testing are `NOT_RUN` for v0.1.0.

See the [release notes](RELEASE_NOTES_v0.1.0.md) for the complete verification disclosure.
