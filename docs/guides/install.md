# Echo Installation Guide

This repository is the public map and documentation layer for Echo. The profile repo does not install the entire Echo stack by itself; individual components live in their own repositories or local workspaces.

## 1. Host prerequisites

Recommended baseline for the current Linux development environment:

- Linux
- Git
- Python 3
- Rust / Cargo for DriftWM
- FFmpeg for media pipelines
- Tesseract for OCR experiments
- Docker for supporting services

Check the basic toolchain:

```bash
git --version
python3 --version
cargo --version
ffmpeg -version | head -n 1
tesseract --version | head -n 1
docker --version
```

## 2. Clone the public Echo repositories

```bash
mkdir -p ~/Echo/Repositories
cd ~/Echo/Repositories

git clone https://github.com/jesus999l/echo-vision.git
```

Additional experimental repositories can be added separately. Do not clone everything blindly onto a nearly-full disk; check available storage first:

```bash
df -h /
```

## 3. Python environment

For Python components that require dependencies, create an isolated environment inside the component rather than installing project packages globally:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
```

Use the project's own dependency file when one exists:

```bash
[ -f requirements.txt ] && python -m pip install -r requirements.txt
```

## 4. Local AI stack

Echo experiments use local inference components such as llama.cpp. Model files are intentionally not bundled into this documentation repository.

Keep large GGUF/model files outside the profile repository and verify free space before downloading:

```bash
df -h /
du -sh ~/Echo 2>/dev/null || true
```

## 5. Voice components

The current research stack uses Vosk for offline speech recognition and Piper for local text-to-speech. Installation details depend on the selected model/runtime, so model downloads should be documented with the exact version used by the active Echo build rather than hard-coded here.

## 6. DriftWM

DriftWM is a separate Rust/Wayland project. Its public source and build instructions are the authoritative source for compositor dependencies.

```bash
git clone https://github.com/malbiruk/driftwm.git
cd driftwm
cargo build --release
```

Do not replace a working compositor binary without a backup and a tested rollback path.

## 7. Android / EchoCapture

EchoCapture is an experimental Android proof-of-capture component. Its build environment is currently intended for the ThinkPad rather than Termux.

For Android builds, verify the Android/Buildozer toolchain in the component workspace before starting a build. A successful APK build is not the same thing as a successful device connection; ADB must separately report a connected device.

## 8. Verify before integrating

The preferred Echo workflow is:

1. Build one primitive.
2. Run a small test.
3. Record the result.
4. Back up the previous working state.
5. Only then connect it to another subsystem.

This prevents a broken experimental component from taking down the larger environment.

## Rollback rule

Before modifying an existing working project:

```bash
git status --short
git branch --show-current
git log -1 --oneline
```

Create a backup or commit before destructive changes. Never treat a generated build artifact as the only backup.
