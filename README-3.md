# Resume Match Analyser

A single-file, browser-based tool that uses AI to compare your resume against any job description — then tells you exactly where you match, where the gaps are, and how to fix them.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Zero Dependencies](https://img.shields.io/badge/dependencies-zero-brightgreen)
![Free AI](https://img.shields.io/badge/AI-free%20tier%20available-blueviolet)

---

## Why this exists

Tailoring a resume to a specific job posting is tedious. You read the JD, scan your resume, try to guess what's missing — and still end up uncertain. This tool automates that entire process in under 30 seconds, giving you a scored breakdown, gap analysis, keyword audit, and prioritised action plan.

## What you get

- **Fit score** (0–100) with a visual ring chart
- **Match breakdown** — which requirements your profile already covers
- **Gap analysis** — mandatory vs desirable gaps, colour-coded by severity
- **Improvement plan** — 5–8 prioritised, expandable action items with specific rewrite advice
- **Keyword audit** — JD terms present in or missing from your resume
- **PDF export** — download a formatted, print-ready report
- **Visit counter** — tracks how many times you've used the tool (stored locally)

## Quick start

1. **Download** `index.html` (just one file — that's the whole app)
2. **Open** it in Chrome, Edge, Firefox, or Safari
3. **Get a free API key** from [Groq](https://console.groq.com/keys) (takes 30 seconds, no credit card)
4. **Paste** your resume on the left, the job description on the right
5. **Click Analyse Match** or press `Ctrl+Enter`

Results appear in ~10–20 seconds depending on the model.

## Supported AI providers

The app ships with three providers. Switch between them using the dropdown — the model list, API key field, and "Get key" link update automatically.

| Provider | Cost | Rate limit | Models | Key signup |
|---|---|---|---|---|
| **Groq** (default) | Free | 14,400 req/day | Llama 3.3 70B, Llama 4 Scout 17B | [console.groq.com/keys](https://console.groq.com/keys) |
| **Google Gemini** | Free | 1,500 req/day | Gemini 2.5 Flash, Gemini 2.5 Pro | [aistudio.google.com/apikey](https://aistudio.google.com/apikey) |
| **Anthropic Claude** | Paid | Per usage | Sonnet 4, Opus 4.6, Sonnet 4.6, Haiku 4.5 | [console.anthropic.com](https://console.anthropic.com) |

> **Note on Gemini:** Google's API may block browser requests when opened via `file://`. If you hit a "Load failed" error with Gemini, serve the file through a local HTTP server instead:
> ```bash
> python3 -m http.server 8000
> # then open http://localhost:8000
> ```
> Groq and Anthropic work fine when opened directly as a local file.

## PDF export

After running an analysis, click **Download as PDF**. A new window opens with a formatted report and your browser's print dialog appears automatically — select **Save as PDF** as the destination. No external libraries required.

The exported PDF includes the score ring, colour-coded tables, improvement recommendations, and keyword analysis — all print-optimised with `@page` CSS.

## Deploy to GitHub Pages

```bash
# 1. Create a repo and push
git init
git add index.html README.md LICENSE
git commit -m "Initial commit"
git remote add origin https://github.com/YOUR_USERNAME/resume-match-analyser.git
git push -u origin main

# 2. Enable Pages
# Settings → Pages → Source: Deploy from branch → main / root → Save
```

Your app will be live at `https://YOUR_USERNAME.github.io/resume-match-analyser/` within a minute.

## Project structure

```
resume-match-analyser/
├── index.html    # The entire application (single file, ~1000 lines)
├── README.md     # This file
└── LICENSE       # MIT
```

## Privacy

- Your API key is held in browser memory only — never saved to disk, never sent anywhere except the chosen AI provider's API endpoint.
- Resume and JD text are sent only to the provider you select (Groq, Google, or Anthropic). Nothing is stored server-side.
- The visit counter uses `localStorage` and never leaves your browser.
- No analytics, no tracking, no cookies.

## Tech stack

- **Frontend:** Vanilla HTML + CSS + JavaScript — no frameworks, no build step, no `node_modules`
- **AI:** Groq API (OpenAI-compatible) / Google Gemini API / Anthropic Claude API
- **Fonts:** DM Serif Display, Outfit, DM Mono via Google Fonts
- **PDF:** Browser-native `window.print()` with `@page` CSS rules

## Contributing

1. Fork the repo
2. Create a feature branch (`git checkout -b feature/your-idea`)
3. Commit your changes
4. Push and open a Pull Request

Bug reports and feature suggestions are welcome as issues.

## License

[MIT](LICENSE)
