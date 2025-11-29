# Statistik_Projekt_OECDWellBeing

Dieses Repository enthält unsere Statistik-Projektarbeit mit Datenanalyse und statistischen Auswertungen auf dem Datensatz der OECD Well-Being Indicators.

Bei der 
## Voraussetzungen
Python 3.8 oder höher

## Setup-Anleitung (.venv)

### 1. Repository klonen
```bash
git clone https://github.com/DEIN-USERNAME/statistik-projekt.git
cd statistik-projekt
```

### 2. Virtuelle Umgebung erstellen

**Windows:**
```bash
python -m venv .venv
.venv\Scripts\activate
```

**macOS/Linux:**
```bash
python3 -m venv .venv
source .venv/bin/activate
```

-> Du solltest jetzt `(.venv)` am Anfang deiner Terminal-Zeile sehen.

### 3. Pakete installieren
```bash
pip install --upgrade pip
pip install -r requirements.txt
```

### 4. Jupyter Notebook starten
```bash
jupyter notebook
```

Der Browser öffnet sich automatisch. Navigiere zum `notebooks/` Ordner und öffne die Notebooks.

## Projektstruktur
```
statistik-projekt/
├── data/                   # Datensätze (CSV, Excel, etc.)
├── notebooks/              # Jupyter Notebooks für Analysen
├── requirements.txt        # Python-Abhängigkeiten
└── README.md              # Diese Datei
```

## Wichtige Hinweise

- **Virtuelle Umgebung aktivieren:** Denke daran, die venv vor jeder Arbeit zu aktivieren!
- **Neue Pakete:** Falls du neue Pakete installierst, aktualisiere die `requirements.txt`:
```bash
  pip freeze > requirements.txt
```
- **Git Workflow:**
```bash
  git pull
  git add .
  git commit -m "Beschreibung"
  git push
```

## Verwendete Bibliotheken

- **pandas**: Datenmanipulation und -analyse
- **numpy**: Numerische Berechnungen
- **matplotlib & seaborn**: Datenvisualisierung
- **scipy**: Statistische Tests
- **statsmodels**: Erweiterte statistische Modelle
- **scikit-learn**: Machine Learning
- **jupyter**: Interactive Notebooks

## Team

- Annabel Morgenstern
- Flurina Baumbach
