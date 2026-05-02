# Resume Match Analyser

AI-powered tool that compares your resume against any job description and delivers a detailed gap analysis with actionable improvement recommendations.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![HTML](https://img.shields.io/badge/built%20with-HTML%2FCSS%2FJS-orange)
![Claude](https://img.shields.io/badge/powered%20by-Claude%20API-blueviolet)

---

## What it does

Paste your resume and a job description, and the tool returns:

- **Overall fit score** (0–100) with a visual ring indicator
- **Match breakdown** — where your profile aligns with each requirement area
- **Gap analysis** — mandatory vs desirable gaps, colour-coded by severity
- **Improvement recommendations** — 5–8 prioritised, actionable steps (expandable)
- **Keyword analysis** — which JD terms appear or are missing from your resume
- **PDF export** — download a formatted report via the browser's print-to-PDF

## Live Demo

> `https://YOUR_USERNAME.github.io/resume-match-analyser/`

Replace `YOUR_USERNAME` with your GitHub username after enabling GitHub Pages.

## Getting Started

### Prerequisites

- A modern web browser (Chrome, Edge, Firefox, Safari)
- An [Anthropic API key](https://console.anthropic.com/) — you can get one with a free tier

### Run Locally

1. Download or clone this repository:
   ```bash
   git clone https://github.com/YOUR_USERNAME/resume-match-analyser.git
   ```
2. Open `index.html` in your browser — no server, no build step, no dependencies.
3. Enter your Anthropic API key in the top-right field.
4. Paste your resume on the left, the job description on the right.
5. Click **Analyse Match** (or press `Ctrl+Enter`).

### Deploy to GitHub Pages

1. Push `index.html` to the `main` branch of your repo.
2. Go to **Settings → Pages → Source → Deploy from a branch → main / root**.
3. Your app will be live in about a minute.

## Features

| Feature | Detail |
|---|---|
| **Zero dependencies** | Single HTML file, no npm, no build tools |
| **Offline-capable** | Only needs internet for the Claude API call |
| **Model selector** | Switch between Claude Sonnet 4, Opus 4.6, Sonnet 4.6, and Haiku 4.5 |
| **PDF export** | Browser-native print-to-PDF with formatted tables, score ring, and colour coding |
| **Privacy-first** | API key lives in memory only — never stored, never transmitted anywhere except the Anthropic API |
| **Visit counter** | Local visit counter persisted in localStorage |
| **Responsive** | Works on desktop and mobile viewports |

## How It Works

```
┌──────────────┐     ┌──────────────────┐     ┌────────────────┐
│  Your Resume │────▶│  Claude API      │────▶│  Structured    │
│  + Job Desc  │     │  (analysis prompt)│     │  JSON response │
└──────────────┘     └──────────────────┘     └───────┬────────┘
                                                      │
                                              ┌───────▼────────┐
                                              │  Rendered UI   │
                                              │  + PDF export  │
                                              └────────────────┘
```

1. Your resume and JD are sent to the Anthropic Messages API with a structured system prompt.
2. Claude returns a JSON object with scores, matches, gaps, improvements, and keywords.
3. The app renders the results as an interactive dashboard with expandable cards.
4. Click **Download as PDF** to open a print-ready formatted report.

## Project Structure

```
resume-match-analyser/
├── index.html      # The entire application (single file)
├── README.md       # This file
└── LICENSE         # MIT License
```

## Screenshots

> Add screenshots of the app here after deploying.

## Tech Stack

- **Frontend:** Vanilla HTML, CSS, JavaScript (no frameworks)
- **AI:** Anthropic Claude API (Messages endpoint)
- **Fonts:** DM Serif Display, Outfit, DM Mono (Google Fonts)
- **PDF:** Browser-native `window.print()` with `@page` CSS

## Privacy & Security

- Your API key is entered at runtime and held in browser memory only.
- No data is stored on any server — everything runs client-side.
- Resume and JD text are sent only to the Anthropic API endpoint (`api.anthropic.com`).
- The visit counter uses `localStorage` and never leaves your browser.

## Contributing

Contributions are welcome! Feel free to open an issue or submit a pull request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

## Acknowledgements

- [Anthropic Claude API](https://docs.anthropic.com/) for powering the analysis
- [Google Fonts](https://fonts.google.com/) for DM Serif Display, Outfit, and DM Mono
