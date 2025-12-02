# Projektplan & Analyse-Struktur

## Daten-Struktur (Input & Output)

Damit wir sauber arbeiten, unterscheiden wir zwischen **Rohdaten** und **prozessierten Daten**.

1.  **Input (Rohdaten):**
    * `data/OECD.WISE.WDP...csv`: Der unveränderte Original-Datensatz.
2.  **Output (Bereinigt aus Notebook 01):**
    * **`data/oecd_full_time_series.csv`**: Enthält alle Jahre. Nutzen wir **NUR** für Verlaufs-Grafiken (Liniendiagramme).
    * **`data/oecd_snapshot_latest.csv`**: Enthält nur das aktuellste Jahr pro Land. Nutzen wir für **ALLE statistischen Tests und Vergleiche**, um die Unabhängigkeit der Daten zu wahren (Vermeidung von Pseudoreplikation).

---

## Notebook-Struktur

Wir teilen die Analyse in 4 logische Schritte (Notebooks) auf:

### 1. Data Preparation (`01_Data_Preparation.ipynb`)
**Ziel:** Vom "Raw Data" zum "Clean Data".
* **Inhalte (VL1 & VL4):**
    * Daten laden und redundante Spalten (Codes vs. Labels) entfernen.
    * Datentypen korrigieren (String zu Float).
    * **Kritische Entscheidung:** Split in Zeitreihe vs. Snapshot (siehe oben).
    * Missing Values behandeln (Löschen von Zeilen ohne Zielvariable).
* **Begründung:** Ohne saubere Daten sind alle p-Werte später falsch. Wir müssen sicherstellen, dass wir keine abhängigen Messungen (gleiches Land 10x) in Hypothesentests stecken.

### 2. Deskriptive Statistik (`02_Descriptive_Statistics.ipynb`)
**Ziel:** Ein Gefühl für die Daten bekommen (Lage, Streuung, Verteilung).
* **Inhalte (VL2 & VL3):**
    * **Verteilung prüfen:** Histogramme & KDE Plots für unsere Hauptvariablen (z.B. "Feeling safe"). Sind sie normalverteilt?
    * **Lage & Streuung:** Mittelwert vs. Median (Begründung anhand von Schiefe/Outliern).
    * **Ausreißer:** Boxplots erstellen und Tukey-Fences prüfen.
    * **Zeitverlauf:** Liniendiagramme (mit `oecd_full_time_series.csv`) um Trends zu sehen.
* **Begründung:** Bevor wir testen, müssen wir wissen, ob die Daten normalverteilt sind (Voraussetzung für t-Test/ANOVA) oder schief (dann brauchen wir Mann-Whitney/Kruskal).

### 3. Korrelationen (`03_Correlation.ipynb`)
**Ziel:** Zusammenhänge zwischen metrischen Variablen prüfen.
* **Inhalte (VL4):**
    * Scatterplots erstellen.
    * Korrelationskoeffizienten berechnen: Pearson (wenn linear/normal) oder Spearman (wenn nicht-linear/Ausreißer).
    * Scheinkorrelationen diskutieren (Simpson-Paradox checken).
* **Wichtig:** Wir nutzen hier nur `oecd_snapshot_latest.csv`.
* **Begründung:** Wir wollen wissen, ob Länder mit höherem BIP auch sicherer sind (Querschnittsanalyse).

### 4. Induktive Statistik & Gruppenvergleiche (04_Inference_and_Groups.ipynb)
**Ziel:** Wir prüfen, ob die beobachteten Unterschiede in den Daten statistisch signifikant sind oder auf Zufall beruhen.
* **Inhalte (VL5 - VL9):**
    * Verteilungs-Check (VL5): Formale Prüfung auf Normalverteilung (Shapiro-Wilk Test), da dies die Voraussetzung für viele Tests ist.
    * Punktschätzung & Intervalle (VL6): Berechnung von Konfidenzintervallen (z.B. 95%) für Mittelwerte. Interpretation: "Wo liegt der wahre Wert der Population?"
    * Gruppenvergleiche (VL7-9): Durchführung von Hypothesentests.
        * 2 Gruppen: t-Test (parametrisch) oder Mann-Whitney U (nicht-parametrisch).
        * Mehr als 2 Gruppen: ANOVA oder Kruskal-Wallis Test.
* **Wichtig:** Wir nutzen hier strikt oecd_snapshot_latest.csv.
* **Begründung:** Bevor wir komplexe Modelle bauen, müssen wir sicherstellen, dass Gruppenunterschiede (z.B. "Europa vs. Rest der Welt") nicht zufällig zustande kamen. Die Unabhängigkeit der Beobachtungen (Snapshot) ist hier zwingend erforderlich.

### 5. Regressionsanalyse & Modellierung (05_Regression_and_Modelling.ipynb)
**Ziel:** Wir analysieren die Stärke von Zusammenhängen und versuchen, Variablen durch andere zu erklären (Ursache-Wirkung-Modellierung).
* **Inhalte (VL10):**
    * Einfache Lineare Regression: Wie stark beeinflusst eine unabhängige Variable (z.B. GDP) die abhängige Variable (z.B. Life Satisfaction)? Interpretation von R^2 und Koeffizienten.
    * Multiple Regression: Hinzufügen weiterer Prädiktoren, um die Erklärungskraft des Modells zu verbessern.
    * Residuenanalyse: Überprüfung der Modellannahmen (Homoskedastizität, Normalverteilung der Fehler), um die Güte des Modells zu beurteilen.
* **Wichtig:** Wir nutzen hier oecd_snapshot_latest.csv, um strukturelle Zusammenhänge im Querschnitt zu finden.
* **Begründung:** Korrelation (aus NB 03) ist keine Kausalität. Die Regression erlaubt es uns, den Einfluss von Faktoren zu quantifizieren und Vorhersagen zu treffen.

### 6. Zeitreihenanalyse & Trends (06_Time_Series_Analysis.ipynb)
**Ziel:** Analyse der zeitlichen Entwicklung der Indikatoren.
* **Inhalte (VL2 & VL10):**
    * Visualisierung: Liniendiagramme für ausgewählte Länder/Gruppen über alle verfügbaren Jahre.
    * Trend-Berechnung: Nutzung der Regression mit der "Zeit" (Jahr) als unabhängige Variable, um Steigungen (Trends) zu berechnen.
    * Vergleich: Welche Länder haben sich positiv/negativ entwickelt?

* **Wichtig:** Hier (und nur hier) nutzen wir oecd_full_time_series.csv!
* **Begründung:** Die bisherigen Analysen waren Momentaufnahmen. Da Wohlbefinden dynamisch ist, müssen wir prüfen, ob sich die Zustände verbessern oder verschlechtern.


---

##  Reminder für jedes Notebook
Die **richtige** CSV (`snapshot` für Analyse, `time_series` für Zeit-Plots) laden!!

