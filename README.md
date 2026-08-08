
# OptiCrop – Crop Recommendation System

AI-powered crop recommendation using **Flask**, **Bootstrap**, and **scikit-learn Random Forest**.

## Tech Stack

| Component  | Technology                                            |
| ---------- | ----------------------------------------------------- |
| Frontend   | HTML, CSS, Bootstrap                                  |
| Backend    | Flask (Python)                                        |
| ML         | Scikit-learn                                          |
| Dataset    | Pre-trained Random Forest model (no bundled CSV)        |
| Database   | Not required (optional SQLite/MySQL for user history) |
| Model      | Random Forest (recommended)                           |
| Deployment | Render / Railway / PythonAnywhere                     |

## Quick Start

```bash
cd opticrop-flask
python -m venv venv
venv\Scripts\activate        # Windows
# source venv/bin/activate   # macOS/Linux
pip install -r requirements.txt
python train_model.py   # verifies bundled model (optional retrain with --data-path)
python app.py
```

Open [http://localhost:5000](http://localhost:5000)

## Project Structure

```
opticrop-flask/
├── app.py                 # Flask routes & API
├── train_model.py         # Verify or retrain Random Forest model
├── models/
│   ├── random_forest.pkl  # Pre-trained model
│   └── metrics.json
├── ml/
│   ├── predictor.py       # Prediction & validation
│   └── crop_info.py       # Crop metadata
├── templates/             # Bootstrap HTML pages
└── static/                # CSS & JS
```

## API

**POST** `/api/predict`

```json
{
  "N": 90,
  "P": 42,
  "K": 43,
  "temperature": 25,
  "humidity": 80,
  "ph": 6.5,
  "rainfall": 200
}
```

**GET** `/api/health` — model status and accuracy

## Deployment

### Render
1. Connect this repo and set root directory to `opticrop-flask`
2. Build command: `pip install -r requirements.txt`
3. Start command: `gunicorn app:app`

### Railway
Deploy with `railway.json` — uses the pre-trained model in `models/`.

### PythonAnywhere
Upload files, install requirements, then configure WSGI to point to `app.py`.

## Pages

- `/` — Solution dashboard with workflow, benefits, and tech stack
- `/prediction` — Input form + live Random Forest predictions
- `/about` — Project descriptions
git add README.md

