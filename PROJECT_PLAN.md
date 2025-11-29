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

### 4. Hypothesentests & Inferenz (`04_Hypothesis_Testing.ipynb`)
**Ziel:** Wissenschaftliche Beantwortung unserer Forschungsfragen.
* **Inhalte (VL5 - VL9):**
    * **2 Gruppen vergleichen:** z.B. "Fühlen sich Männer sicherer als Frauen?" (t-Test oder Mann-Whitney U).
    * **Mehr als 2 Gruppen:** z.B. "Unterscheidet sich das Sicherheitsgefühl zwischen Altersgruppen (Jung/Mittel/Alt)?" (ANOVA oder Kruskal-Wallis).
    * **Post-Hoc Tests:** Wenn ANOVA signifikant, wer unterscheidet sich genau?
    * **Multiple Testing:** Korrektur der p-Werte (Bonferroni/FDR), da wir mehrere Tests machen.
* **Begründung:** Wir wollen beweisen, dass Unterschiede nicht nur Zufall sind. Hier ist die Unabhängigkeit der Beobachtungen (Snapshot-Daten) am wichtigsten!

---

##  Reminder für jedes Notebook
Die **richtige** CSV (`snapshot` für Analyse, `time_series` für Zeit-Plots) laden!!
