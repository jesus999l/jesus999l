# Run and Verify Echo Locally

Echo is developed as a collection of components. Start with the smallest verified primitive instead of launching the entire ecosystem at once.

## 1. Inspect the host

```bash
hostname
uname -r
python3 --version
df -h /
free -h
```

## 2. Inspect the repository state

```bash
git status --short
git branch --show-current
git log -1 --oneline
```

A clean or understood working tree is preferred before testing a new integration.

## 3. Start a Python component

From a component directory:

```bash
python3 -m venv .venv
source .venv/bin/activate
python3 main.py
```

If the component has a documented entry point, use that entry point instead of guessing one.

## 4. Verify desktop perception

The desktop perception layer is designed to expose structured state for the Echo brain. A useful verification target is the generated perception-state file under the active runtime directory.

```bash
echo "$XDG_RUNTIME_DIR"
find "$XDG_RUNTIME_DIR" -maxdepth 3 -type f -name '*perception*' -o -name 'echo_perception_state' 2>/dev/null
```

When the state file exists and contains JSON:

```bash
jq . "$XDG_RUNTIME_DIR/driftwm/echo_perception_state"
```

The important milestone is not visual polish; it is proving that windows, titles, app IDs, focus state, or other structured desktop information can be consumed reliably.

## 5. Verify DriftWM

```bash
echo "$XDG_SESSION_TYPE"
echo "$WAYLAND_DISPLAY"
ps aux | grep '[d]riftwm'
```

Do not force-start a second compositor session over a working desktop session without understanding the session layout.

## 6. Verify local model services

For a local inference service, first inspect what is already running rather than starting duplicates:

```bash
ps aux | grep -E '[o]llama|[l]lama-server' || true
ss -ltnp 2>/dev/null | grep -E ':(11434|8080|8765)\b' || true
```

## 7. Verify voice tools

```bash
command -v python3
command -v ffmpeg
command -v tesseract
```

Vosk and Piper are normally verified inside the specific Echo component that owns them because model/runtime packaging varies.

## 8. Android / ADB verification

On the build host:

```bash
adb devices
```

Expected state:

```text
List of devices attached
DEVICE_ID    device
```

`unauthorized` means the phone has not accepted the debugging prompt. An empty list means there is no connected ADB device.

For an already-built APK:

```bash
adb install -r path/to/echocapture-debug.apk
```

Then verify application logs rather than assuming the install succeeded:

```bash
adb logcat -c
adb logcat | grep --line-buffered 'EchoCapture'
```

## 9. The Echo integration rule

The preferred progression is:

```text
primitive
   ↓
small test
   ↓
structured result
   ↓
model consumes result
   ↓
action/tool call
   ↓
perception verifies action
```

The full perception → reasoning → automation loop is still a work in progress. Documentation should describe verified behavior separately from planned behavior.
