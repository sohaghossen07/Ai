# English Buddy AI — Android starter project

This is a **voice-first offline practice prototype**, not a finished full generative-AI tutor.

## Included
- Android app with a voice-only practice screen (no chat transcript or text-entry interface).
- English speech recognition request with `EXTRA_PREFER_OFFLINE`.
- Spoken English responses using Android Text-to-Speech.
- 30-minute session timer.
- A small local rule-based teacher for a few common beginner mistakes.
- Local session practice count stored on the device.
- GitHub Actions workflow to build a debug APK.

## Important offline limitations
Android's `SpeechRecognizer` may use an online recognition service depending on the phone, installed language pack, Android version and recognition provider. `EXTRA_PREFER_OFFLINE` is only a preference; it does not guarantee offline recognition. Install an English offline speech/language pack and an offline English TTS voice in Android settings, then test with mobile data and Wi-Fi turned off.

The response engine in this starter is rule-based. It is **not** a bundled local LLM and cannot freely understand every answer or create truly open-ended conversations. A full offline AI tutor requires selecting and bundling/downloading a compatible quantized language model plus a reliable offline speech-to-text and text-to-speech engine. Model files are intentionally not included because they are large and device compatibility varies.

No online AI API or cloud sync is wired in this starter. Those require a chosen provider, account/API configuration, privacy design and explicit implementation. The local session count is stored on-device.

## Build with GitHub Actions
1. Create a GitHub repository.
2. Extract this ZIP on your phone or computer.
3. Upload the **contents** of this folder to the repository root (not the ZIP as a single file).
4. Open the repository's **Actions** tab.
5. Select **Build Android APK** and run it, or push a commit to `main`.
6. Open the completed workflow run and download the `EnglishBuddyAI-debug-apk` artifact.
7. Extract the downloaded artifact and install the APK on your Android phone. Allow installation from that source if Android asks.

## Build locally
Requires JDK 17, Android SDK platform 35 and Gradle 8.9:
```bash
gradle assembleDebug
```
APK output:
`app/build/outputs/apk/debug/app-debug.apk`

## Suggested next development steps
- Replace Android's recognition service with a bundled offline STT engine.
- Add a quantized local LLM and prompt/response management.
- Store structured learner profile, vocabulary, recurring errors and conversation topics in Room.
- Add opt-in encrypted online sync and downloadable conversation/model packs.
- Add tests for grammar feedback, session timing, permissions and offline behavior.
