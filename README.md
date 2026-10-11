# 🌐 Live Translator — EN ↔ JA

A browser extension that translates between English and Japanese **as you type**, in any text box, on any website. Fully offline after initial setup — no API keys, no subscriptions, no data sent anywhere.

---

## Setup (Two Steps)

### Step 1 — Download Transformers.js

This is a one-time step. Run the setup script to download the local ML library into the extension folder.

**macOS / Linux:**
```bash
chmod +x setup.sh
./setup.sh
```

**Windows:**
```
Double-click setup.bat
```

This downloads `transformers.min.js` (~2MB) into the `lib/` folder.

### Step 2 — Load in Chrome

1. Open Chrome and go to `chrome://extensions`
2. Enable **Developer Mode** (toggle in the top right)
3. Click **Load unpacked**
4. Select this folder (`live-translator/`)
5. The extension is now active!

---

## First Use

The extension uses two small ML models (EN→JA and JA→EN) that are downloaded the first time you translate. This is a ~100MB one-time download, after which everything works completely offline.

To trigger the download early, click the extension icon and press **"Download Models Now"**.

---

## How to Use

1. Go to any website
2. Click on any text box, search bar, or text area
3. Start typing in English or Japanese
4. A floating preview appears below the field with the translation
5. Click **⇄ Use** to swap your text with the translation, or **⎘** to copy it

The extension auto-detects the language — just type naturally.

---

## File Structure

```
live-translator/
├── manifest.json       Extension config
├── background.js       ML model runner (service worker)
├── content.js          Page listener + preview UI
├── popup.html          Extension popup
├── popup.js            Popup logic
├── setup.sh            macOS/Linux setup script
├── setup.bat           Windows setup script
├── lib/
│   └── transformers.min.js   ← created by setup script
└── icons/
    └── icon48.png
```

---

## Privacy

- All translation happens locally in your browser
- No text is ever sent to any server
- No analytics, no tracking

---

## Models Used

- **EN→JA**: `Xenova/opus-mt-en-jap` (Helsinki-NLP OPUS-MT)
- **JA→EN**: `Xenova/opus-mt-jap-en` (Helsinki-NLP OPUS-MT)

Both are open-source models from the [Helsinki-NLP](https://github.com/Helsinki-NLP/Opus-MT) project, quantized for browser use by [Xenova/Transformers.js](https://github.com/xenova/transformers.js).
