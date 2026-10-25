# Little English 🌈

A lightweight, open-source, iPad-friendly English listen-and-repeat web app for young learners.

一个面向儿童英语启蒙的开源跟读网页应用，无需后端即可体验范读与浏览器语音识别。

## Features / 功能

- Large, touch-friendly landscape layout for iPad / iPad 横屏触屏布局
- English speech synthesis (TTS) / 英文范读
- Automatically attempts to start speech recognition after the model voice finishes / 范读后自动尝试监听
- Word-by-word green highlighting for ASR matches / 逐词绿色反馈
- Three stars for exact sentence match; two stars if at least one target word matches / 完全匹配三星，部分匹配二星
- Spoken encouragement: “Excellent!” or “Good job!”
- Editable text and local image selection via settings / 可修改句子并选择本地配图

## Demo

After GitHub Pages is enabled: https://zhengxilong.github.io/little-english/

## Run locally / 本地运行

```bash
python3 -m http.server 8000
```

Open http://localhost:8000/ .

## GitHub Pages / 部署

Repository → **Settings → Pages → Deploy from a branch → main → /(root)**.

HTTPS is important for microphone-related browser APIs. Browser speech recognition support varies by browser, operating-system version and recognition service. In particular, **automatic ASR startup after TTS may be blocked by Safari**, so the large green button and retry control allow explicit user action.

## Learning logic / 判定逻辑

1. Tap the green button to hear the example.
2. At the end of TTS, the app attempts to start speech recognition.
3. Recognized matching words turn green.
4. An exact normalized sentence match earns ⭐⭐⭐ and “Excellent!”.
5. A non-exact sentence with at least one matching word earns ⭐⭐ and “Good job!”.
6. No matched words: a gentle retry prompt, without a star rating.

Punctuation and capitalization are ignored. This is a **recognition-based encouragement rule, not a pronunciation assessment**. Misrecognition, network availability, browser permissions, and accents can affect results.

## Structure

- `index.html`: complete working prototype.
- `data/lessons.example.json`: sample data schema for a future lesson library. **Not connected to the UI yet.**
- `LICENSE`: MIT License.

The current image selected in settings uses a temporary object URL and is not uploaded or saved. This prototype does not intentionally store or transmit recordings; browser-provided speech recognition may use vendor-hosted services. Review browser privacy behavior before real-world use with children.

## License

MIT. See [LICENSE](LICENSE).
