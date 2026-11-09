# 🎙️ spectromood - Hear What Your Voice Really Feels

[![Download spectromood](https://img.shields.io/badge/Download-spectromood-8A2BE2?style=for-the-badge&logo=github&logoColor=white)](https://github.com/kailas-design/spectromood/releases)

spectromood listens to a short recording of your voice and shows you the emotion hiding inside it. It turns your speech into a colorful picture called a spectrogram, measures the small details of how you speak, compares everything against your own personal baseline, and then lets a decision model make the final call. Everything runs privately on your own computer inside Docker, and the results appear live on a dashboard in your browser.

You do not need to know anything about programming, audio engineering, or machine learning to use it. If you can click a download button and open a web page, you can use spectromood.

## ✨ What You Get

- **A live dashboard** that updates while you speak, so you can watch your voice being analyzed in real time.
- **Spectrogram plots** that turn sound into an easy-to-read picture, with color showing how much energy sits in each frequency range over time.
- **Voice features** pulled out of every clip, including pitch, loudness, pace, and the pauses between words.
- **Your own baseline** built from your normal speaking voice, so results reflect how *you* sound rather than how a stranger sounds.
- **A decision model** that weighs the evidence and returns a clear emotion label with a confidence level.
- **Voice activity detection (VAD)** that automatically ignores silence and background noise, so you never have to trim a recording by hand.
- **A private, offline-style workflow.** The dashboard runs on your machine, and your recordings stay on your machine.

## 🚀 Getting Started on Windows

Visit this link to download the application:

**[https://github.com/kailas-design/spectromood/releases](https://github.com/kailas-design/spectromood/releases)**

The page that opens lists the available versions, with the newest one at the top. Download the file offered for that newest version and wait for the download to finish. Once it is complete, open the downloaded file to start setting up spectromood.

Before you do that, complete the Docker step below, because spectromood is a Docker-only application and needs Docker running on your computer first.

## 🐳 Installing Docker Desktop

spectromood is delivered as a Docker application. Docker is a free tool that packages software so it runs the same way on every computer. Think of it as a sealed lunchbox that contains spectromood and everything it needs, so nothing else on your PC gets touched.

1. Open the official Docker website in your browser and download **Docker Desktop for Windows**.
2. Run the installer and accept the default options as they appear.
3. When the installer finishes, restart your computer if it asks you to.
4. Open **Docker Desktop** from your Start menu and leave it running. You will see a small whale icon in the system tray near the clock when it is ready.
5. If Docker Desktop asks you to sign in, you can skip or close that window. A free account is not required to run spectromood.

Docker Desktop must be open and running every time you use spectromood. If the whale icon is not visible, start Docker Desktop first and give it a minute to wake up.

## 🎛️ Your First Session, Step by Step

1. Make sure Docker Desktop is running.
2. Open the spectromood application you downloaded. A small window may appear while it starts up. The first launch takes longer than later ones because Docker is preparing the container.
3. When startup finishes, your browser opens the spectromood dashboard automatically. If it does not, the startup window shows a local address you can paste into your browser.
4. Allow microphone access when your browser asks. Without it, spectromood cannot hear you.
5. Pick a quiet moment and read a sentence out loud in your normal voice for about ten seconds. The dashboard begins drawing immediately.
6. Watch the spectrogram appear, the voice feature panel fill in, and the decision model return its first emotion label.

## 📈 Reading Your Dashboard

The dashboard is split into panels, each answering a different question.

**The waveform panel** shows the raw shape of your voice, so you can confirm the microphone is picking you up.

**The spectrogram panel** is the star of the show. Time runs left to right, pitch runs bottom to top, and brighter colors mean more energy. Steady horizontal bands usually mean a calm, even tone, while scattered bright patches suggest a more animated delivery.

**The voice features panel** translates those pictures into numbers: how high or low your pitch sits, how much it moves, how loud you are, how quickly you speak, and how long your pauses last.

**The voice activity panel** confirms which parts of your recording counted as speech, so silent gaps are ignored rather than analyzed.

**The decision panel** shows the final emotion label, a confidence score, and a short breakdown of which signals pushed the decision in that direction.

## 🎚️ Why Your Own Baseline Matters

Most emotion detectors compare you to a generic average of thousands of strangers. That is why they often get it wrong, especially for quieter speakers, deeper voices, or anyone with an accent.

spectromood does something different. During a short calibration session, you speak a few neutral sentences. spectromood records how your voice behaves when you are not feeling anything in particular, and saves that as your baseline. From then on, every result is measured as a change from *your* normal. A shift in pitch or a drop in pace means something real about you, not about a statistical average.

You can rebuild your baseline at any time from the dashboard, which is useful after a cold, a long trip, or a new microphone.

## 🔍 What the Decision Model Adds

Voice features alone are just numbers. The decision model is what turns those numbers into a verdict.

spectromood sends the combined evidence, meaning the spectrogram patterns and the voice features compared against your baseline, to a decision model running on Cloudflare Clef with Workers AI. The model weighs all the signals together, the way a person would listen to tone, energy, and rhythm at the same time, and returns an emotion label with a confidence score.

Only the extracted measurements travel to the model. It is looking at shapes and numbers, not listening to your raw audio.

## 🎤 Tips for a Clean Recording

- Record in a room with soft furnishings rather than a bare, echoey space.
- Keep the microphone at a steady distance, roughly a hand's width from your mouth.
- Speak at your natural volume. Whispering and shouting both stretch the analysis.
- Avoid background music, fans, or open windows facing traffic.
- Aim for ten to twenty seconds of speech. Longer clips give the decision model more to work with.
- Do your calibration baseline when you are relaxed and feeling neutral.

## 🧰 Troubleshooting

**The dashboard does not open.** Confirm Docker Desktop is running before launching spectromood, then try again and allow up to two minutes on the first run.

**No sound is detected.** Check the microphone permission in your browser settings and confirm the correct microphone is selected in your Windows sound settings.

**Results look random.** Rebuild your baseline. A baseline recorded while you were tired or distracted will skew every later comparison.

**Docker shows an error about resources.** Close other heavy applications to free memory, then restart Docker Desktop from its tray menu.

**The browser tab was closed by accident.** Reopen the local address shown in the spectromood startup window.

## 🔐 Privacy

Your audio is processed on your own computer. The dashboard, the spectrogram generation, the voice feature extraction, and the baseline storage all live inside the Docker container on your machine. What leaves your computer is limited to the numeric measurements needed for the decision step.

## 💬 Getting Help

If something does not work, open an issue on the repository and describe what you saw. Screenshots of the dashboard and the exact wording of any error message make problems much faster to solve.

Keywords: cloudflare, decision-model, docker, emotion-detection, fastapi, prosody, spectrogram, speech-emotion-recognition, voice-activity-detection, workers-ai