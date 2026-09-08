# Install and Update PCssak ModuSori

[한국어](INSTALLATION.ko.md) · [System requirements](../SYSTEM_REQUIREMENTS.md) · [Known limitations](KNOWN-LIMITATIONS.md)

This guide applies to v0.1.7 Free Version for Windows x64. Download only from the
[official fixed v0.1.7 release](https://github.com/pcssakinc/pcssak-modusori-releases/releases/tag/v0.1.7)
or the official [PCSSAK product page](https://pcssak.com/modusori).

## Before installation

1. Confirm that the PC runs a currently serviced Windows 11 Home or Pro x64 installation and that
   its CPU supports AVX2/FMA/F16C. Other platforms are outside the supported boundary.
2. Back up important audio, transcripts, notes, and exported files.
3. Open the fixed `v0.1.7` release and download its Windows x64 NSIS installer and
   `SHA256SUMS.txt`. Do not use GitHub's automatically generated source archives.
4. In PowerShell, calculate the installer digest:

   ```powershell
   Get-FileHash -Algorithm SHA256 -LiteralPath (Read-Host 'Full installer path')
   ```

5. Compare all 64 hexadecimal characters with the installer entry in `SHA256SUMS.txt` from the
   same release. Stop on any mismatch. The release page, not this guide, is the source of the
   final filename, digest, and size.
6. Keep Microsoft Defender, SmartScreen, Smart App Control, and organisation policy enabled.

The v0.1.7 installer is not Windows Authenticode-signed. Windows can show **Unknown publisher** or
a reputation warning even when its SHA-256 matches. The hash verifies byte equality with the
published asset; it is not publisher identity or a malware guarantee. If security policy blocks
the installer, stop and use an authorised test PC or wait for a signed release. Do not disable a
security control.

## First installation

The NSIS installer is configured for the current Windows user and offers English, Korean,
Japanese, German, French, International Spanish, Brazilian Portuguese, Turkish, and Russian.
Choose a language, read the bundled EULA, and continue only if you agree. Current-user installation
is the intended configuration, but clean-device privilege and policy behavior is `NOT_RUN` for
v0.1.7.

Microsoft Edge WebView2 Runtime is required for the interface. If it is absent, the installation
process can connect to Microsoft's WebView2 distribution service. Proxy, offline, organisation,
and security-product behavior has not completed the real-device matrix.

On first launch, ModuSori shows the complete EULA and Privacy Notice again. Both checkboxes are
cleared by default, and both must be actively selected before the app can be used. Before microphone
or system-audio recording, the app checks the chosen device without capturing audio, then requires one
unchecked confirmation per session. The first recording includes the full safety notice in that
same confirmation. The initial legal-document checkboxes are separate from recording confirmation.
Free Version limits each live-caption session to 30 minutes; the user may start another
session after the limit.

## Install a Whisper model

Model weights are not bundled. Open the model manager and choose Tiny, Base, Small, Medium, or
Large-v3 Turbo. The app downloads the fixed file directly from the
[`ggerganov/whisper.cpp` Hugging Face repository](https://huggingface.co/ggerganov/whisper.cpp),
supports resuming a partial download, and accepts the model only after its exact byte length and
pinned SHA-256 match.

Start with a smaller model on a constrained PC. See [system requirements](../SYSTEM_REQUIREMENTS.md)
for model sizes and memory guidance. Do not copy an unverified model into the application data
folder or substitute another download URL.

v0.1.7 model-download HTTPS uses Windows platform certificate verification and supported Windows
system-proxy settings. Certificate and hostname checks, HTTPS-only redirects, the fixed model byte
length, and pinned SHA-256 remain mandatory. If `UnknownIssuer` or another TLS error appears, do not
disable certificate verification, Defender, SmartScreen, Smart App Control, organisation policy,
or antivirus TLS inspection. Do not switch to HTTP or an untrusted mirror. Record only the smallest
non-sensitive technical detail and contact the responsible network administrator or support.

An earlier user report confirmed successful model download on the PC that reported `UnknownIssuer`.
That observation does not complete the exact 0.1.7 install → Tiny/Base download → model load → restart
path, which remains `NOT_RUN`. Do not disable certificate or hostname verification, antivirus TLS
inspection, or Windows and organisation security controls to work around a failure.

## Short utterances and stopping

Choose the recognition language explicitly if automatic detection is wrong. Try a short,
non-sensitive sample and compare numbers, times, amounts, and omissions with the original audio.
Normal stopping waits for remaining transcription activity. If its time limit is reached,
Dictation requests cooperative cancellation and preserves partial output; Live Captions keeps a
failed session that can be stopped again. Live Captions has no direct cancel control while waiting
for stopping; ending remaining work uses the app-exit confirmation flow and can lose unfinalized output.
Do not treat an error state
as completed transcription or immediately discard results by reinstalling. Larger models can take
longer; there is no fixed completion-time guarantee.

## Update

- The updater supports direct signed updates from v0.1.0–v0.1.6; intermediate patches are not
  required. Identity, update endpoint, public key, and install-scope contracts match. Actual installed
  direct-update tests to the public 0.1.7 release remain `NOT_RUN`.
- A release build makes at most one automatic update-check attempt after startup. The user can
  also start a manual check.
- The app displays a candidate and release notes before download. Download and installation need
  user approval; there is no silent update installation.
- Recording, transcription, unsaved results, model work, or another protected operation can defer
  or block installation.
- The updater verifies the mandatory Tauri installer signature, the separately signed release
  manifest, expected version and URL, and SHA-256 before applying an update.
- A Tauri updater signature is not Windows Authenticode. It protects update bytes but does not
  turn an unsigned installer into a known Windows publisher.
- Only an approved version greater than the installed version can be offered. A separate-PC
  installed public v0.1.3 → v0.1.7 normal and tampered update test remains `NOT_RUN`.

If an update check fails, keep using the installed version after a model is available or visit the
fixed official release page. Never bypass a signature error, replace metadata, or install a mirror
or repackaged copy. Separate-machine normal and tampered update tests are `NOT_RUN` for v0.1.7.

## Repair or reinstall

Re-download from the fixed official tag and repeat the SHA-256 comparison. Close ModuSori normally
before running an installer. Back up or export results first. Preservation of every setting,
recovery state, model, and pending output across repair or reinstall has not completed the clean-PC
matrix, so do not use reinstall as a substitute for a backup.

## Uninstall and local data

Use Windows **Settings → Apps → Installed apps** to uninstall PCssak ModuSori. Close the app and
export important results first. Uninstalling the executable does not promise deletion of every
model, setting, recovery file, exported result, partial download, browser download, backup, or
cloud-synchronised copy.

If you intentionally want to remove remaining local app data after uninstalling and backing up,
review only these exact per-user locations:

- `%APPDATA%\com.pcssak.modusori`
- `%LOCALAPPDATA%\com.pcssak.modusori`

Do not delete a parent folder, a similarly named folder, or an exported file location. Windows
Recycle Bin, backup, security software, and cloud-sync retention are controlled separately.

See [Support](../SUPPORT.md) for safe troubleshooting and [Security](../SECURITY.md) for private
vulnerability reporting.
