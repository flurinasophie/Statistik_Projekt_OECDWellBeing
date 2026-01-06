# Statistikprojekt: OECD Well-Being Indicators

## Project Overview

Unser Projekt analysiert ausgewählte **OECD Well-Being Indicators**, um Unterschiede und Zusammenhänge zwischen Ländern systematisch zu untersuchen. Ziel ist es, anhand eines realen, komplexen Datensatzes den gesamten im Kurs behandelten Statistikstoff nachvollziehbar anzuwenden – von der Datenaufbereitung über deskriptive Statistik und Inferenz bis hin zu Regressions- und Panelmodellen.

Ein zentrales Anliegen unseres Projekts ist es, die statistische Methoden nicht isoliert, sondern als aufeinander aufbauende Analyseentscheidungen zu verstehen. Deshalb sind die Notebooks bewusst sequenziell aufgebaut und eng miteinander verbunden: Ergebnisse aus früheren Schritten (z. B. Schiefe von Verteilungen oder Ausreißerproblematik) fließen explizit in die Wahl und Begründung späterer Methoden ein.

Der OECD-Well-Being-Datensatz eignet sich besonders gut, da er sowohl **Zeitreiheninformationen** als auch **Querschnittsvergleiche** ermöglicht und sozialökonomische Indikatoren aus unterschiedlichen Lebensbereichen kombiniert.

---

## Repository Structure

| Notebook | Inhalt |
|----------|--------|
| `01_Data_Preparation_and_Cleaning.ipynb` | Einlesen, Bereinigung und Strukturierung der Rohdaten. Zentrale Designentscheidung: Aufteilung in **Full Time Series** (für Zeitreihenanalysen) und **Snapshot Latest** (eine Beobachtung pro Land zur Sicherstellung unabhängiger Stichproben). |
| `02_Descriptive_Statistics_and_Distribution.ipynb` | Deskriptive Statistik und Verteilungsanalyse der Snapshot-Daten. Analyse von Lage- und Streuungsmaßen, Schiefe, Ausreißern und Implikationen für nachfolgende inferenzstatistische Methoden. |
| `03_Correlation_and_Relationships.ipynb` | Untersuchung bivariater Zusammenhänge zwischen zentralen Well-Being-Indikatoren. Wahl geeigneter Korrelationsmaße unter Berücksichtigung nicht-normalverteilter Variablen. |
| `04_Induktive_Statistik_und_Gruppenvergleiche.ipynb` | Hypothesentests und Gruppenvergleiche zwischen Ländern bzw. Ländergruppen. Begründete Auswahl parametrischer und nicht-parametrischer Tests. |
| `05_Regressionsanalyse_und_Modellierung.ipynb` | Lineare Regressionsmodelle zur Erklärung ausgewählter Indikatoren. Diskussion von Modellannahmen, Gütemaßen und Grenzen der Interpretierbarkeit. |
| `06_Zeitreihenanalyse_und_Trends.ipynb` | Zeitreihenanalysen auf Basis der Full-Time-Series-Daten. Trendanalyse und Diskussion der zeitlichen Entwicklung einzelner Indikatoren. |
| `07_Logistische_Regression.ipynb` & `07_Multiple_Regression_und_Panelmodelle.ipynb` | Erweiterte Modellierungsansätze: logistische Regression für binäre Zielgrößen sowie multiple Regression und Einführung in Panelmodelle. Diskussion der methodischen Voraussetzungen und Einschränkungen. |

Zusätzlich liegen alle Notebooks im Ordner `Project_HTML` auch als **HTML-Dateien** vor, um die vollständigen Outputs unabhängig von der Ausführungsumgebung einsehen zu können.

---

## Key Findings 
### 1. Verteilungsformen und Heterogenität der Well-Being-Indikatoren

Die deskriptive Analyse der Snapshot-Daten zeigt, dass viele OECD-Well-Being-Indikatoren keiner Normalverteilung folgen. Stattdessen treten häufig rechtsschiefe Verteilungen, ausgeprägte Ausreißer sowie eine hohe Streuung zwischen Ländern auf.

Diese Befunde haben direkte methodische Konsequenzen: Der Mittelwert erweist sich für mehrere Variablen als wenig robustes Lagemaß, während Median und Interquartilsabstand häufig eine realistischere Beschreibung der zentralen Tendenz liefern. Die beobachtete Schiefe und Heterogenität beeinflusst die Auswahl geeigneter statistischer Verfahren in den nachfolgenden Notebooks maßgeblich.

### 2. Bivariate Zusammenhänge zwischen Dimensionen des Wohlbefindens

Die Korrelationsanalysen deuten auf systematische, jedoch überwiegend moderat ausgeprägte Zusammenhänge zwischen verschiedenen Dimensionen des Wohlbefindens hin, etwa zwischen materiellen Indikatoren, subjektiven Zufriedenheitsmaßen sowie gesundheits- oder umweltbezogenen Variablen.

Auffällig ist, dass viele Zusammenhänge nicht linear sind und sensibel auf Ausreißer reagieren. Entsprechend unterscheiden sich die Ergebnisse je nach verwendetem Korrelationsmaß (z. B. Pearson vs. Spearman). Dies verdeutlicht, dass selbst scheinbar klare Zusammenhänge bei aggregierten Länderdaten methodisch vorsichtig interpretiert werden müssen.

### 3. Gruppenvergleiche und inferenzstatistische Ergebnisse

Die Gruppenvergleiche zeigen, dass sich Länder bzw. Ländergruppen in ausgewählten Well-Being-Indikatoren statistisch signifikant unterscheiden können. Die beobachtete Signifikanz hängt jedoch stark von der zugrunde liegenden Verteilung der Variablen, der Gruppengröße sowie der Wahl des Testverfahrens ab.

Insbesondere bei nicht-normalverteilten Daten bestätigen nicht-parametrische Tests häufig nur einen Teil der Effekte, die mit parametrischen Verfahren identifiziert werden. Dies unterstreicht, dass statistische Signifikanz stets im Kontext der Datenstruktur und der getroffenen Annahmen zu interpretieren ist.

### 4. Regressionsmodelle: Erklärungsbeiträge und Grenzen

Die Regressionsanalysen zeigen, dass sich einzelne Well-Being-Indikatoren durch andere Variablen teilweise erklären lassen, die Erklärungskraft der Modelle jedoch insgesamt begrenzt bleibt.

Die Modelle reagieren sensibel auf Ausreißer und Multikollinearität zwischen erklärenden Variablen, was die eindeutige Interpretation einzelner Koeffizienten einschränkt. Auch bei statistisch signifikanten Ergebnissen erlauben die Modelle keine kausalen Schlussfolgerungen, sondern dienen primär der explorativen Analyse von Zusammenhängen.

### 5. Zeitreihenanalyse: Dynamik statt statischer Vergleiche

Die Analyse der vollständigen Zeitreihen verdeutlicht, dass sich Well-Being-Indikatoren über die Zeit sehr unterschiedlich entwickeln. Während einige Länder langfristige Verbesserungen zeigen, stagnieren oder verschlechtern sich andere Indikatoren.

Diese Ergebnisse machen deutlich, dass Momentaufnahmen nur eingeschränkte Einblicke liefern und zeitliche Dynamiken für ein umfassendes Verständnis zentral sind. Gleichzeitig wird sichtbar, dass Zeitreihendaten methodisch anders zu behandeln sind als Querschnittsdaten.

### 6. Methodische Kernreflexion: Vermeidung von Pseudoreplikation

Ein zentrales methodisches Ergebnis unseres Projekts ist der bewusste Umgang mit dem Problem der Pseudoreplikation. Die OECD-Daten enthalten für jedes Land mehrere Beobachtungen über die Zeit, die innerhalb eines Landes stark voneinander abhängig sind.

Um eine Verletzung der Annahme unabhängiger Beobachtungen zu vermeiden, haben wir direkt am Anfang eine zentrale Designentscheidung getroffen: Zeitreihendaten werden ausschließlich für deskriptive Trend- und Zeitreihenanalysen verwendet, während für alle inferenzstatistischen Analysen ein Snapshot-Datensatz mit genau einer Beobachtung pro Land genutzt wird.

Diese Trennung verhindert eine künstliche Aufblähung der Stichprobengröße, vermeidet eine Unterschätzung von Standardfehlern und reduziert das Risiko fälschlich signifikanter Ergebnisse. Die Auseinandersetzung mit Pseudoreplikation prägt damit die gesamte Analysepipeline.

### 7. Gesamtfazit

Insgesamt zeigt unser Projekt, dass internationale Well-Being-Daten vielfältige analytische Möglichkeiten bieten, deren statistische Auswertung jedoch eine hohe methodische Sorgfalt erfordert.

Die zentralen Erkenntnisse liegen nicht nur in einzelnen numerischen Ergebnissen, sondern insbesondere in der reflektierten Anwendung statistischer Methoden, der bewussten Einschränkung von Interpretationen sowie der transparenten Diskussion methodischer Grenzen.

---

## Methodology & Tech Stack

**Programmiersprache**
- Python 3

**Zentrale Bibliotheken**
- `pandas`, `numpy` – Datenaufbereitung und -manipulation  
- `matplotlib`, `seaborn` – Visualisierung  
- `scipy.stats`, `statsmodels` – statistische Tests und Regressionsmodelle  

**Statistische Methoden**
- Deskriptive Statistik (Lage-, Streuungs- und Verteilungsmaße)
- Korrelationsanalyse (parametrisch und nicht-parametrisch)
- Hypothesentests und Gruppenvergleiche
- Lineare und logistische Regression
- Zeitreihenanalyse
- Einführung in Panelmodelle

Alle Methoden werden **kontextualisiert, begründet und kritisch reflektiert**, insbesondere im Hinblick auf ihre Voraussetzungen.

---

## Usage

1. Repository klonen oder herunterladen  
2. Notebooks in der angegebenen Reihenfolge öffnen  

Für eine vollständige Nachvollziehbarkeit empfehlen wir, die Notebooks **sequenziell zu lesen**, da spätere Analysen explizit auf früheren Ergebnissen aufbauen.

---
## Persönliche Reflexion

Im Verlauf dieses Projekts haben wir gelernt, Statistik nicht als eine Abfolge isolierter Rechenverfahren zu verstehen, sondern als einen zusammenhängenden analytischen Entscheidungsprozess. Besonders deutlich wurde für uns, dass statistische Methoden niemals losgelöst von der Datenstruktur, den zugrunde liegenden Annahmen und dem konkreten Erkenntnisinteresse angewendet werden können.

Ein zentraler Lernprozess bestand darin, die Bedeutung sorgfältiger Datenaufbereitung zu erkennen. Erst durch die intensive Auseinandersetzung mit der Struktur des OECD-Datensatzes wurde uns klar, welche methodischen Probleme entstehen können, wenn Zeitreihenbeobachtungen unreflektiert als unabhängige Stichproben behandelt werden. Die bewusste Trennung in Full-Time-Series-Daten und einen Snapshot-Datensatz hat unser Verständnis für Pseudoreplikation, Abhängigkeitsstrukturen und die Voraussetzungen inferenzstatistischer Verfahren nachhaltig geschärft.

Darüber hinaus hat uns das Projekt geholfen, Ergebnisse der deskriptiven Statistik kritisch zu hinterfragen. Wir haben gelernt, dass Kennzahlen wie Mittelwert oder Varianz nicht automatisch aussagekräftig sind, sondern stark von Verteilungsform und Ausreißern beeinflusst werden. Die konsequente Interpretation von Verteilungen, Schiefe und Streuung bildete die Grundlage für alle weiteren Analyseschritte und beeinflusste unsere Entscheidungen bei Korrelationen, Hypothesentests und Regressionsmodellen.

Auch im Bereich der Modellierung war das Projekt lehrreich für uns. Insbesondere die Arbeit mit Regressions- und Panelmodellen hat uns gezeigt, wie sensibel statistische Ergebnisse auf Modellannahmen reagieren und wie wichtig es ist, Erklärungskraft, Signifikanz und inhaltliche Interpretierbarkeit voneinander zu unterscheiden. Anstelle eindeutiger Antworten rückten für uns zunehmend die Grenzen statistischer Aussagen in den Fokus.

Nicht zuletzt war der gemeinsame Arbeitsprozess ein zentraler Bestandteil des Lernerfolgs. Durch das wechselseitige Überprüfen der Notebooks, die gemeinsame Diskussion methodischer Entscheidungen und die zwischenzeitliche Restrukturierung des Projekts haben wir gelernt, statistische Analysen kritisch zu reflektieren, zu begründen und transparent zu dokumentieren.

Insgesamt hat uns das Projekt dabei geholfen, Statistik als analytisches Werkzeug mit klaren Möglichkeiten, aber auch klaren Grenzen zu verstehen. Dieses Verständnis geht über einzelne Methoden hinaus und stellt für uns einen der wichtigsten Lernerträge der Veranstaltung dar.

---

## Administrative Information

**Autorinnen**
- **Annabel Morgenstern**
- **Flurina Baumbach**

**Arbeitsweise**

Nach etwa der Hälfte der Vorlesungen haben wir das Projekt **grundlegend restrukturiert**. Ursprünglich haben wir die Notebooks strikt entlang einzelner Vorlesungen aufgebaut, was sich jedoch als methodisch unübersichtlich erwies. Daraufhin haben wir die Struktur auf einen **logischen statistischen Analyseprozess** umgestellt.

Die Arbeit erfolgte stark **kollaborativ**:
- Flurina erstellte den Projektplan und übernahm die konzeptionelle Struktur.
- Annabel begann parallel mit der Überarbeitung und Vereinheitlichung der Notebooks.
- Jedes Notebook wurde nach Fertigstellung jeweils von der anderen Person überprüft (Inhalt, Logik, Konsistenz).
- Die meisten Arbeitsschritte wurden parallel und gemeinsam (am selben Ort) durchgeführt.

---

## AI Usage Declaration

Im Rahmen dieses Projekts haben wir Unterstützung von KI punktuell eingesetzt, um das Verständnis statistischer Konzepte zu vertiefen, methodische Entscheidungen zu reflektieren sowie bei der Fehlersuche und Interpretation von Analyseergebnissen zu unterstützen.  

Die Nutzung beschränkte sich auf **konzeptionelle, erklärende und technische Hilfestellung**. Die Auswahl der Methoden, die Implementierung der Analysen, die Interpretation der Ergebnisse sowie die schriftliche Ausarbeitung erfolgten eigenständig durch die Projektautorinnen.

Die folgenden Prompts geben eine **realistische und sinngemäße Auswahl** der verwendeten KI-Anfragen wieder:

| Kontext / Aufgabe | Verwendeter Prompt (sinngemäß) |
| :--- | :--- |
| **Datenstruktur & Designentscheidung** | *„Welche Probleme entstehen, wenn Zeitreihendaten fälschlich als unabhängige Beobachtungen behandelt werden, und wie lässt sich Pseudoreplikation methodisch vermeiden?“* |
| **Deskriptive Statistik (Notebook 02)** | *„Welche Konsequenzen hat eine rechtsschiefe Verteilung für die Wahl von Lagemaßen und Streuungsmaßen?“* |
| **Korrelationsanalyse (Notebook 03)** | *„Wann ist Spearman-Korrelation gegenüber Pearson-Korrelation vorzuziehen und wie unterscheidet sich die Interpretation?“* |
| **Datenaufbereitung & Debugging** | *„Warum erzeugt mein `groupby`-Befehl unerwartet Duplikate, obwohl ich pro Land nur eine Beobachtung behalten möchte?“* |
| **Gruppenvergleiche (Notebook 04)** | *„Welche Voraussetzungen müssen für parametrische Tests erfüllt sein und wann sind nicht-parametrische Alternativen angemessen?“* |
| **Hypothesentests** | *„Wie interpretiert man ein nicht-signifikantes Testergebnis korrekt, ohne daraus fälschlich ‚keinen Effekt‘ abzuleiten?“* |
| **Modell-Diagnostik** | *„Wie kann ich prüfen, ob die Residuen meines Regressionsmodells systematische Muster aufweisen?“* |
| **Regressionsanalyse (Notebook 05)** | *„Welche Annahmen liegen der linearen Regression zugrunde und wie können Verletzungen dieser Annahmen erkannt werden?“* |
| **Umgang mit Zeitreihendaten** | *„Wie kann ich in pandas sicherstellen, dass ich pro Land den aktuellsten Beobachtungszeitpunkt auswähle?“* |
| **Fehlersuche in Jupyter Notebooks** | *„Mein Plot zeigt leere Achsen, was soll ich tun?“* |
| **Projektorganisation** | *„Wie kann ich ein Jupyter-Projekt strukturieren, sodass Zwischenergebnisse reproduzierbar gespeichert und weiterverwendet werden können?“* |
| **Modellinterpretation** | *„Wie lassen sich Regressionskoeffizienten in sozialwissenschaftlichen, aggregierten Länderdaten sinnvoll interpretieren?“* |
| **Zeitreihenanalyse (Notebook 06)** | *„Welche Unterschiede bestehen zwischen Querschnitts- und Zeitreihendaten hinsichtlich statistischer Inferenz?“* |
| **Panelmodelle (Notebook 07)** | *„Welche zusätzlichen Annahmen und Einschränkungen bringen Panelmodelle im Vergleich zu einfachen Regressionsmodellen mit sich?“* |

---
