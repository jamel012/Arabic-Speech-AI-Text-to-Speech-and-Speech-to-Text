## EdgeTTS Arabic TTS Demo — Text‑to‑Speech without API Keys
A minimal project that converts Arabic text to natural‑sounding speech using Microsoft Edge TTS via the edge-tts Python library.
Works without any API keys and runs in Jupyter/Colab or as a stand‑alone Python script.

## ✨ Features
🔊 Convert Arabic text to MP3 using neural voices (e.g., ar-SA-ZariyahNeural, ar-SA-HamedNeural).

🧪 Works in notebooks (top‑level await) and regular Python scripts (asyncio.run).


🗣️ Example text included: “This is my first text‑to‑speech project…” in Arabic.

## 🧰 Tech Stack
Python 3.9+

edge-tts (Microsoft Edge Text‑to‑Speech)

Optional for notebooks: IPython.display to preview audio

## ⚙️ Requirements
bash
Copy
Edit
pip install edge-tts
If you’re on Google Colab, just run the command above in a cell.

## 🚀 Quick Start
A) Jupyter / Google Colab (recommended)
python
Copy
Edit
# !pip install edge-tts

import edge_tts
from IPython.display import Audio

async def tts_ar(text, out="voice.mp3", voice="ar-SA-ZariyahNeural"):
    tts = edge_tts.Communicate(text, voice=voice)
    await tts.save(out)

# Use top-level await in notebooks
text = "هذا هو أول مشروع لي في تحويل النص إلى كلام. تجربة رائعة وأتطلع لتطوير المزيد!"
await tts_ar(text, out="voice.mp3")

# Play inside the notebook
Audio("voice.mp3", autoplay=True)
B) Python Script (main.py)
python
Copy
Edit
import asyncio
import edge_tts

async def tts_ar(text, out="voice.mp3", voice="ar-SA-ZariyahNeural"):
    tts = edge_tts.Communicate(text, voice=voice)
    await tts.save(out)

if __name__ == "__main__":
    text = "هذا هو أول مشروع لي في تحويل النص إلى كلام. تجربة رائعة وأتطلع لتطوير المزيد!"
    asyncio.run(tts_ar(text, out="voice.mp3"))
    print("Saved voice.mp3")
Run:

bash
Copy
Edit
python main.py
## 🗣️ Choose a Voice
Common Arabic voices:

ar-SA-ZariyahNeural

ar-SA-HamedNeural

Tip: You can try other locales/voices by changing the voice parameter.

## 🧩 Useful Snippets
Your “first project” message (Arabic):

python
Copy
Edit
text = (
    "هذا هو أول مشروع لي في تحويل النص إلى كلام باستخدام الذكاء الاصطناعي. "
    "تجربة رائعة وأتطلع لتطوير المزيد من المشاريع المشابهة في المستقبل!"
)
Save to a different file name:

python
Copy
Edit
await tts_ar(text, out="my-first-tts.mp3")
## 🛠️ Troubleshooting
RuntimeError: asyncio.run() cannot be called from a running event loop
You’re in a notebook—use await instead of asyncio.run(...).

No audio or empty file
Re‑run the cell, check that text isn’t empty, and make sure the environment has internet access (Edge TTS needs connectivity).

Unicode issues
Save your script as UTF‑8 and put the text string directly in your code (Python 3 handles Arabic well).

<img width="1103" height="350" alt="image" src="https://github.com/user-attachments/assets/c89551e1-d0a5-4560-8bad-7b66337d3cfc" />
