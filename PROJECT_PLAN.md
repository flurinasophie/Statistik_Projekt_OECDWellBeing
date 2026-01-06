# Projektplan & Analyse-Struktur

## Daten-Struktur (Input & Output)

Damit wir sauber arbeiten, unterscheiden wir zwischen **Rohdaten** und **prozessierten Daten**.

1.  **Input (Rohdaten):**
    * `data/OECD.WISE.WDP...csv`: Der unveränderte Original-Datensatz.
2.  **Output (Bereinigt aus Notebook 01):**
    * **`data/oecd_full_time_series.csv`**: Enthält alle Jahre. Nutzen wir **NUR** für Verlaufs-Grafiken (Liniendiagramme).
    * **`data/oecd_snapshot_latest.csv`**: Enthält nur das aktuellste Jahr pro Land. Nutzen wir für **ALLE statistischen Tests und Vergleiche**, um die Unabhängigkeit der Daten zu wahren (Vermeidung von Pseudoreplikation).

---

Unser Projekt ist in mehrere Jupyter Notebooks gegliedert, die sich an einem klaren statistischen Analyseprozess orientieren. Die Notebooks bauen logisch aufeinander auf und greifen Inhalte aus verschiedenen Vorlesungen auf. Ziel ist es, die im Kurs behandelten Methoden nicht isoliert, sondern im Zusammenhang anzuwenden.

---

### Notebook 01 — Data Preparation and Cleaning  
**Datei:** `01_Data_Preparation_and_Cleaning.ipynb`  
**Ziel:** Herstellung einer sauberen, konsistenten Datenbasis als Voraussetzung für alle weiteren Analysen.

**Inhaltlicher Fokus:**
- Einlesen der OECD Well-Being Rohdaten
- Entfernen redundanter Spalten und Korrektur von Datentypen
- Identifikation und Behandlung von Duplikaten
- Zentrale Designentscheidung: Aufteilung der Daten in  
  - **Full Time Series** (alle Jahre pro Land) und  
  - **Snapshot Latest** (eine Beobachtung pro Land)

**Bezug zu Vorlesungen:**  
VL 1 (Einführung, Datentypen), VL 4 (Datenstruktur, Abhängigkeiten)

Dieses Notebook legt die methodische Grundlage des gesamten Projekts, insbesondere zur Vermeidung von Pseudoreplikation.

---

### Notebook 02 — Descriptive Statistics and Distribution  
**Datei:** `02_Descriptive_Statistics_and_Distribution.ipynb`  
**Ziel:** Exploratives Verständnis der Daten und ihrer Verteilungen.

**Inhaltlicher Fokus:**
- Deskriptive Statistiken (Mittelwert, Median, Varianz, IQR)
- Visualisierung von Verteilungen (Histogramme, Boxplots)
- Identifikation von Schiefe und Ausreißern
- Erste Einschätzung, ob parametrische Verfahren sinnvoll sind

**Datengrundlage:**  
`oecd_snapshot_latest.csv`

**Bezug zu Vorlesungen:**  
VL 2 (Deskriptive Statistik), VL 3 (Verteilungen)

Die Ergebnisse dieses Notebooks bestimmen maßgeblich die Wahl der statistischen Verfahren in den folgenden Schritten.

---

### Notebook 03 — Correlation and Relationships  
**Datei:** `03_Correlation_and_Relationships.ipynb`  
**Ziel:** Untersuchung von Zusammenhängen zwischen zentralen Well-Being-Indikatoren.

**Inhaltlicher Fokus:**
- Visualisierung bivariater Zusammenhänge (Scatterplots)
- Berechnung von Korrelationskoeffizienten
- Begründete Wahl zwischen Pearson- und Spearman-Korrelation
- Diskussion möglicher Scheinkorrelationen

**Datengrundlage:**  
`oecd_snapshot_latest.csv`

**Bezug zu Vorlesungen:**  
VL 4 (Zusammenhänge, Korrelation)

Dieses Notebook dient als Brücke zwischen deskriptiver Analyse und inferenzstatistischen Fragestellungen.

---

### Notebook 04 — Induktive Statistik und Gruppenvergleiche  
**Datei:** `04_Induktive_Statistik_und_Gruppenvergleiche.ipynb`  
**Ziel:** Formale Überprüfung, ob beobachtete Unterschiede statistisch signifikant sind.

**Inhaltlicher Fokus:**
- Prüfung von Verteilungsannahmen (z. B. Normalverteilung)
- Konfidenzintervalle und Punktschätzungen
- Hypothesentests und Gruppenvergleiche
- Parametrische vs. nicht-parametrische Tests

**Datengrundlage:**  
`oecd_snapshot_latest.csv`

**Bezug zu Vorlesungen:**  
VL 5–9 (Inferenzstatistik, Hypothesentests, Gruppenvergleiche)

Hier wird der Übergang von explorativer zu inferenzstatistischer Analyse vollzogen.

---

### Notebook 05 — Regressionsanalyse und Modellierung  
**Datei:** `05_Regressionsanalyse_und_Modellierung.ipynb`  
**Ziel:** Multivariate Analyse und Modellierung von Zusammenhängen.

**Inhaltlicher Fokus:**
- Einfache und multiple lineare Regression
- Interpretation von Regressionskoeffizienten und R²
- Überprüfung von Modellannahmen (Residuenanalyse)
- Diskussion der Grenzen kausaler Interpretation

**Datengrundlage:**  
`oecd_snapshot_latest.csv`

**Bezug zu Vorlesungen:**  
VL 10 (Regression und Modellierung)

Dieses Notebook erweitert die bisherigen bivariaten Analysen um einen multivariaten Ansatz.

---

### Notebook 06 — Zeitreihenanalyse und Trends  
**Datei:** `06_Zeitreihenanalyse_und_Trends.ipynb`  
**Ziel:** Analyse der zeitlichen Entwicklung von Well-Being-Indikatoren.

**Inhaltlicher Fokus:**
- Visualisierung von Zeitverläufen für ausgewählte Länder
- Identifikation von Trends über mehrere Jahre
- Vergleich von Ländern und Regionen im Zeitverlauf

**Datengrundlage:**  
`oecd_full_time_series.csv`

**Bezug zu Vorlesungen:**  
VL 2 (Visualisierung), VL 10 (Regression in zeitlichem Kontext)

Dieses Notebook ergänzt die Querschnittsanalysen um eine dynamische Perspektive.

---

### Notebook 07 — Multiple Regression und Panelmodelle  
**Datei:** `07_Multiple_Regression_und_Panelmodelle.ipynb`  
**Ziel:** Abschließende Modellierung unter Berücksichtigung der Panelstruktur der Daten.

**Inhaltlicher Fokus:**
- Erweiterung auf multiple Regressionsmodelle
- Einführung panelbasierter Denkweisen
- Diskussion von Fixed Effects und unbeobachteter Heterogenität
- Reflexion zusätzlicher Annahmen und Limitationen

**Datengrundlage:**  
Primär `oecd_full_time_series.csv`

**Bezug zu Vorlesungen:**  
VL 10 (fortgeschrittene Modellierung, Panelansätze)

Dieses Notebook bildet den methodischen Abschluss des Projekts.


##  Reminder für jedes Notebook
Die **richtige** CSV (`snapshot` für Analyse, `time_series` für Zeit-Plots) laden!!

