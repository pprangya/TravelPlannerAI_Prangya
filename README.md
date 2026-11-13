# 🇮🇳 Travel Planner AI 

An AI-powered conversational travel assistant for Indian destinations, built with OpenAI Function Calling via SAP AI Core and an interactive ipywidgets chat UI.

---

## Features

| Tool | What it does |
|---|---|
| `find_best_hotels` | Recommends hotels filtered by destination, budget range, and star rating |
| `get_top_attractions` | Lists things to do, filterable by category (food, cultural, nature, …) |
| `create_itinerary` | Builds a day-by-day morning/afternoon/evening plan |
| `get_weather_info` | Returns seasonal conditions, temperatures, and packing advice |
| `get_travel_tips` | Shares 8 practical local tips per destination |
| `estimate_trip_budget` | Calculates daily and total costs across budget / moderate / luxury tiers |

**Supported destinations:** Mumbai · Delhi · Goa · Jaipur · Kerala · Varanasi

---

## Architecture

```
User Input
    │
    ▼
TravelPlannerAI (conversation memory + function calling loop)
    │
    ▼
Function Dispatcher (execute_function)
    │
    ▼
6 Python Functions  ←──  travel_data.py (30 hotels, 48 attractions, 6 destinations)
```

---

## Setup

### Prerequisites

- Python 3.9+
- Access to SAP AI Core with a GPT-4o deployment (or any OpenAI-compatible endpoint)
- Jupyter Notebook / VS Code with Jupyter extension

### Install dependencies

```bash
python3 -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

### Configure credentials

Copy `.env.example` to `.env` and fill in your SAP AI Core values:

```bash
cp .env.example .env
```

```
AICORE_CLIENT_ID=...
AICORE_CLIENT_SECRET=...
AICORE_AUTH_URL=https://...authentication.sap.hana.ondemand.com
AICORE_BASE_URL=https://api.ai.prod.eu-central-1.aws.ml.hana.ondemand.com
AICORE_DEPLOYMENT_ID=...
AICORE_MODEL=gpt-4o
```

---

## Running the notebook

1. Open `travel_planner.ipynb` in VS Code or Jupyter
2. Select the **Travel Planner (Python 3.12)** kernel (or your venv kernel)
3. **Run All Cells** — cells must run in order (Section 2 → 3 → 4 → 5 → 6 → 7 → 8)
4. The interactive chat UI appears at the end of Section 8

---

## File structure

```
TravelPlannerAI/
├── travel_planner.ipynb   # Main notebook — all sections, demos, and chat UI
├── travel_data.py         # Curated travel database (hotels, attractions, weather, tips, budgets)
├── requirements.txt       # Python dependencies
├── .env.example           # Credential template (copy to .env)
└── Project_Report.docx    # Standalone project report
```

---

## Notebook sections

| Section | Contents |
|---|---|
| 1 | Project overview, architecture diagram, rubric alignment |
| 2 | Setup — SAP AI Core OAuth token + OpenAI client |
| 3 | Data layer — import and preview `travel_data.py` |
| 4 | Tool definitions — 6 OpenAI function schemas |
| 5 | Function implementations |
| 6 | Function dispatcher |
| 7 | `TravelPlannerAI` class (conversation loop) |
| 8 | Interactive chat UI (ipywidgets) |
| 9 | Demo conversations — 4 scripted examples with real outputs |
| 10 | Project documentation |
