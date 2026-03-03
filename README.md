# TriageRedTeam

**AI Health Triage Evaluation Framework** — a prompt generator for red-teaming AI health triage systems, based on the methodology from Ramaswamy (2026).

Generates structured clinical vignettes with configurable bias probes (race, gender, anchoring, access barriers) across 4 acuity levels, using a 2x2x2x2 factorial design.

![Node.js](https://img.shields.io/badge/Node.js-18%2B-green)
![License](https://img.shields.io/badge/license-MIT-blue)

## Features

- **8 built-in clinical scenarios** across 4 triage levels (A–D)
- **AI-generated vignettes** via Claude API — create unlimited custom scenarios
- **Factorial bias probes** — race, gender, anchoring statements, access barriers
- **Two prompt variants** — with or without objective clinical data (vitals, labs, exam)
- **Copy-ready prompts** — paste directly into any AI health system for testing
- **Bring your own API key** — enter it in the UI, nothing stored server-side

## Quick Start

### 1. Clone and install

```bash
git clone https://github.com/health-ai-redteam/health-ai-redteam.git
cd health-ai-redteam
npm install
```

### 2. Configure (optional)

If you want a server-side default API key:

```bash
cp .env.example .env
# Edit .env and add your Anthropic API key
```

Otherwise, users can enter their own key directly in the UI.

### 3. Run

```bash
npm start
```

Open **http://localhost:3000** in your browser.

## How It Works

1. **Select a triage level** (A–D) and clinical scenario
2. **Configure patient demographics** — age, gender, race
3. **Toggle bias probes** — anchoring statements, access barriers
4. **Build the prompt** — generates a structured patient message
5. **Copy and paste** into any AI health triage system to evaluate its response

Optionally, click **AI-Generate Vignette** to have Claude create a new clinical scenario on the fly.

## Study Methodology

Based on a 2x2x2x2 factorial design:

| Factor | Levels |
|---|---|
| Race | White (unmarked) / Black (stated) |
| Gender | Man / Woman |
| Anchoring | With / without prior clinician reassurance |
| Access Barrier | With / without healthcare access constraint |

Two prompt variants per condition:
- **Prompt 1**: Symptoms + vitals + exam + labs
- **Prompt 2**: Symptoms + history only

Gold standards from 39 clinical scenarios across 4 acuity levels, adjudicated by 3 physicians (Fleiss' kappa = 0.90).

## Tech Stack

- **Backend**: Node.js + Express (serves static files + proxies Claude API)
- **Frontend**: Vanilla HTML, CSS, JavaScript (no frameworks, no build step)
- **AI**: Claude API (Anthropic) for vignette generation

## Project Structure

```
triage-redteam/
├── server.js          # Express server + Claude API proxy
├── package.json
├── .env.example       # Environment variable template
└── public/
    ├── index.html     # Page structure
    ├── style.css      # All styles
    └── app.js         # Application logic
```

## API Key

You need an Anthropic API key for the AI vignette generation feature. Get one at [console.anthropic.com](https://console.anthropic.com).

The prompt builder works without an API key — only the "AI-Generate Vignette" button requires one.

## License

MIT
