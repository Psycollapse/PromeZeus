# NanoLab Toolkit

A lightweight toolkit for experimenting with nanotechnology- and quantum-inspired calculations, combined with a daily arXiv harvester and a search API.  
Features include:
- **Element data** via [APIVerve Periodic Table API](https://apiverve.com).
- **Simple calculators** for thin films, SEM interaction ranges, quantum wells, and alloy mixtures.
- **ArXiv harvester** for categories like `cond-mat.mtrl-sci`, `quant-ph`, `app-ph`, etc.
- **Search API** (FastAPI) to query harvested papers by keyword (and later, semantic embeddings).

---

## Getting Started

### 1. Clone the repository
```bash
git clone https://github.com/yourusername/nanolab-toolkit.git
cd nanolab-toolkit
```

### 2. Create a virtual environment
On Windows:
```bash
python -m venv .venv
```

### 3. Activate the environment
PowerShell:
```powershell
.venv\Scripts\Activate.ps1
```

Command Prompt:
```bat
.venv\Scripts\Activate.bat
```

On Linux/Mac:
```bash
source .venv/bin/activate
```

### 4. Install dependencies
```bash
pip install -r requirements.txt
```

---

## Usage

### APIVerve client
Fetch element properties:
```bash
python -m nanolab.apiverve_client
```

### ArXiv harvester
Run the script to fetch the newest 50 papers in each category into `data/arxiv_nano.db`:
```bash
python -m nanolab.arxiv_harvest
```

### Run the API
Launch the FastAPI service:
```bash
uvicorn api.search_api:app --reload --port 8010
```

Open docs in browser:
- Swagger UI: http://127.0.0.1:8010/docs  
- ReDoc: http://127.0.0.1:8010/redoc

### Example query
```bash
curl "http://127.0.0.1:8010/search?q=TiO2+thin+film&limit=5"
```

---

## Project Structure
```
.
├─ nanolab/             # Core calculators and harvesters
├─ api/                 # FastAPI service
├─ data/                # Local database (SQLite by default)
├─ workflows/           # n8n workflows (JSON exports)
├─ requirements.txt     # Dependencies
└─ README.md
```

---

## Next Steps
- Add thin-film transfer-matrix module with optical constants.
- Add Pinecone (or FAISS) embeddings for semantic paper search.
- Connect to n8n workflow for automated daily harvest.
