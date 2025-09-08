### Einführung in die Regelungstheorie

- **Klassische und moderne Regelungstheorie**: Rückkopplungsstrategien, um Systeme stabil und leistungsfähig zu machen.
- **Klassische Regelungstheorie**: Basierend auf Übertragungsfunktionen; analysiert Ein-zu-Ein-Ausgangssysteme (SISO) im Zeit- und Frequenzbereich. Werkzeuge: Bode-Diagramme, Nyquist-Kurven und Wurzelortskurven. Diese analysieren Stabilität und Dynamik, geben aber eigentlich dieselbe Information.
- **Moderne Regelungstheorie**: Verwendet Zustandsraumdarstellung für Mehrgrößensysteme (MIMO). Konzepte: Steuerbarkeit und Beobachtbarkeit. Nutzt fortgeschrittene Methoden wie optimale und robuste Regelung für komplexe Leistungsanforderungen. Ein Mehrgrößenregler kann auf den Entwurf mehrerer Eingrößenregler zurückgeführt werden, wenn das System statisch oder dynamisch entkoppelt werden kann. Entkopplung: Das Ziel ist, die Eingangs- und Ausgangskanäle so zu transformieren, dass jede Eingangsgröße nur eine einzige Ausgangsgröße beeinflusst.

### Grundbegriffe

- **Nullstellen**: Wurzeln des Zählerpolynoms der Übertragungsfunktion.
- **Pole**: Wurzeln des Nennerpolynoms der Übertragungsfunktion.
- **Eigenwerte**: Wurzeln des charakteristischen Polynoms der Systemmatrix A in der Zustandsraumdarstellung.
- **Relativer Grad**: Differenz zwischen der Anzahl der Pole und der Anzahl der Nullstellen; zeigt, wie stark hochfrequente Signale gedämpft werden.
- **Zeitkonstanten (Grenzfrequenz)**: Bestimmen die Geschwindigkeit des Systems bei der Antwort auf eine Eingabe. Sie sind das Negative des Realteils der komplexen Pole.
- **E/A-Verhalten (Eingabe-Ausgabe-Verhalten)**: Beeinflusst durch Nullstellen, relativen Grad und Grenzfrequenz.
- **Eigenbewegung (Freie Bewegung)**: Beeinflusst durch Pole (entsprechen den Eigenwerten), Eigenwerte und Zeitkonstanten.

### Stabilitätsdefinitionen

- **Zustandsstabilität (Lyapunov-Stabilität)**: Ein System ist zustandsstabil, wenn für jeden beliebigen Anfangszustand die nachfolgenden Zustände beschränkt bleiben. Das bedeutet, das System schwingt nicht unendlich auf. Es kann aber sein, dass das System nicht zu seinem Gleichgewichtszustand zurückkehrt.
- **Innere Stabilität (Asymptotische Stabilität)**: Die stärkste Form der Stabilität; ein System ist intern stabil, wenn es zustandsstabil ist und zusätzlich nach einer Störung in seinen Gleichgewichtszustand zurückkehrt. Bei LTI-Systemen kehrt es zu seinem ursprünglichen Zustand zurück.
- **Integrität eines Regelkreises**: Bezeichnet die Fähigkeit, auch beim Ausfall eines Teilsystems (z. B. eines Sensors) stabil zu bleiben. Es ist eine Eigenschaft der Robustheit gegenüber Ausfällen. Ein Regelkreis, der nach einem Sensorausfall instabil wird, hat keine Integrität.
- **Beobachtbarkeit**: Ein System ist strukturell beobachtbar, wenn es möglich ist, alle internen Zustände durch die Messung der Ausgaben zu rekonstruieren. Der Rang der Beobachtbarkeitsmatrix ist n.

### Modelle und Stabilitätskriterien

- **Zeitbereichsmodelle**: Zustandsraumdarstellung, Differentialgleichungen.
  - **Zustandsraumdarstellung**: Ein lineares, zeitinvariantes (LTI) System ist stabil, wenn die Eigenwerte der Systemmatrix (A) einen negativen Realteil haben.
  - **Stabilitätskriterien für Regelstrecke (offene Kreis – kein Feedback)**: Die Eigenwerte der Systemmatrix (A) haben negativen Realteil, dann ist die Regelstrecke stabil.
- **Frequenzbereichsmodelle**: Übertragungsfunktion, Frequenzgang.
  - **Übertragungsfunktion**: Ein System ist BIBO-stabil, wenn alle Pole der Übertragungsfunktion einen negativen Realteil haben.
  - **Stabilitätskriterien für Regelkreis (geschlossener Kreis – mit Feedback)**:
    - **Hurwitz-Kriterium**: Alle Wurzeln des Nennerpolynoms der geschlossenen Schleife haben negativen Realteil.
    - **Wurzelortskurve**: Das System ist stabil, solange die Wurzelortskurve nicht in die rechte Hälfte der s-Ebene eindringt.
    - **Nyquist-Diagramm**: Stellt den Frequenzgang (Betrag und Phase) in der komplexen Ebene dar. Nyquist-Kriterium: Das System ist stabil, wenn die Nyquist-Kurve den kritischen Punkt (−1, j0) nicht umschließt.
    - **Bode-Kriterium**: Ein System ist stabil, wenn der Amplitudengang bei der Phasenverschiebung von −180° kleiner als 1 ist und die Phase bei dem Amplitudengang 1 über −180° liegt.

### Kenngrößen im Regelkreis

- **Führungsübertragungsfunktion**: Beschreibt das Verhältnis von Ausgang Y(s) zu Sollwert W(s).
- **Störübertragungsfunktion**: Beschreibt das Verhältnis von Ausgang Y(s) zu einer Störung Z(s).
- **Bleibende Regelabweichung**: Der stationäre Fehler, wenn der Sollwert eine Sprungfunktion ist (1/s) und Störungen null sind. Kann mit dem Endwertsatz berechnet werden.
- **Kreisverstärkung**: Die Verstärkung der offenen Kette bei Gleichstrom; Stabilitätsrand (Amplituden- und Phasenrand): Diese Kenngrößen geben an, wie weit das System von der Stabilitätsgrenze entfernt ist.
- **Pole**: Die Pole des geschlossenen Regelkreises sind die Wurzeln des charakteristischen Polynoms.
- **Empfindlichkeit**: Beschreibt, wie empfindlich die Führungsübertragungsfunktion auf Änderungen der Übertragungsfunktion der Regelstrecke reagiert.

### Regeln und Reglerauswahl

- **Stabilisierung instabiler Regelstrecken**: Eine instabile Regelstrecke kann durch einen geeigneten linearen Regler stabilisiert werden, wenn sie steuerbar ist. Das bedeutet, dass alle instabilen Pole der Strecke durch eine geeignete Eingabe beeinflusst und in die linke Halbebene verschoben werden können. Der Rang der Steuerbarkeitsmatrix muss gleich der Systemordnung n sein.
- **Zustandsrückführungen**: Haben große Bedeutung, obwohl technisch selten direkt umsetzbar. Sie ermöglichen die Polplatzierung (Pole des geschlossenen Regelkreises an jede beliebige Position in der stabilen linken Halbebene verschieben), vorausgesetzt, das System ist vollständig steuerbar. Dienen als Grundlage für praktische Regler.
- **Wahl des Reglers**: Ein Kompromiss zwischen Stabilität, Nachführgenauigkeit, Rauschunterdrückung und Robustheit. Reglerstruktur (meist PID) basierend auf: Stabilität, Sollwertfolge, Messrauschunterdrückung, Robustheit, Dynamik (Führungs- und Störverhalten).
- **Klassifizierung von Regelungsaufgaben**:
   (Klasse 1: I/PI für Genauigkeit; Klasse 2: PID für Dynamik; Klasse 3: P/PI für Robustheit).
  - **Klasse 1**: Hohe Genauigkeit im stationären Zustand (bleibende Regelabweichung null). Regler: I- oder PI-Regler. Beispiel: Temperaturregelung in einem Ofen.
  - **Klasse 2**: Hohe Dynamik (kurze Anstiegszeit, minimale Überschwingung). Regler: PID-Regler (D-Anteil beschleunigt und reduziert Überschwingen). Beispiel: Servomotor-Positionsregelung.
  - **Klasse 3**: Hohe Robustheit (System muss unter allen Umständen stabil bleiben). Regler: P-Regler (bei PT2-Strecken) oder PI-Regler (bei PT1-Strecken) mit kleiner Verstärkung; D-Anteil vermeiden. Beispiel: Regelung in der chemischen Industrie mit unvorhersehbaren Einflüssen.
- **I-Regler**: Fügt einen Pol bei s=0 hinzu; eliminiert stationären Fehler durch Integration des Fehlers. Vorteil: Ausgang folgt Sollwert auch bei konstanter Störung.

### Übertragungsglieder

- **P-Glied (Proportionalglied)**: Ausgang proportional zur Eingabe; keine Dynamik. Beispiele: Potentiometer, Verstärker ohne Filter.
- **I-Glied (Integrationsglied)**: Ausgang ist Integral der Eingabe; steigt/fällt konstant bei konstanter Eingabe ≠ 0. Beispiele: Motor ohne Last, Füllstand eines Tanks.
- **D-Glied (Differenzialglied)**: Ausgang proportional zur Änderungsrate der Eingabe; reagiert auf Änderungen. Beispiele: Tachogenerator, induktive Sensoren.
- **PT1-Glied**: Proportional-Verzögerung 1. Ordnung; verzögert mit Zeitkonstante. Beispiele: Thermometer, RC-Glied.
- **PT2-Glied**: Proportional-Verzögerung 2. Ordnung; verzögert und oft schwingend. Beispiele: Feder-Masse-Dämpfer-System, LCR-Schwingkreis.
- **PD-Glied**: Kombination aus proportional und differenzierend; reagiert schnell auf Änderungen.
- **T-Glied (Totzeitglied)**: Ausgang ist verzögerte Kopie der Eingabe (konstante Verzögerung). Beispiele: Transportband, chemische Reaktionen mit Transportzeit.

### Theorem und Verfahren

- **Gleichgewichtstheorem (Regelungsnormalform)**: Dynamische Eigenschaften von Führungs- und Störübertragungsfunktion können nicht unabhängig eingestellt werden. Für gute Störunterdrückung bei niedrigen Frequenzen muss S(s) klein sein (hohe Kreisverstärkung). Für Robustheit bei hohen Frequenzen muss S(s) klein sein (geringe Kreisverstärkung).
- **Wurzelortskurve**: Darstellung der Eigenwerte (Pole) in der s-Ebene. System stabil, wenn alle Pole in linker Halbebene. Zeigt Bewegung der Pole bei Variation von K (0 bis ∞). Optimierung: Wahl von K für gewünschte Dämpfung/Dynamik.
  - **Verfahren (Iterationsschleife)**:
    - Schritt 1: Zeichnen der Wurzelortskurve der offenen Kette mit variablen Parameter.
    - Schritt 2: Auswahl eines gewünschten Pols (z. B. für Dämpfung).
    - Schritt 3: Ablesen der Reglerverstärkung K.
    - **Iteration**: Wenn Pol nicht auf Kurve liegt, Regler umgestalten (z. B. PD/PID hinzufügen), Schritte wiederholen.
- **Bode-Diagramm**: Besteht aus Betragsdiagramm (Verstärkung bei sinusförmigen Signalen) und Phasendiagramm (Phasenverschiebung). System stabil, wenn Reserven positiv.
  - **Verfahren (Iterationsschleife)**:
    - Schritt 1: Zeichnen des Bode-Diagramms der offenen Kette ohne Regler.
    - Schritt 2: Auswahl einer Reglerstruktur (z. B. PI/PID).
    - Schritt 3: Schätzung der Parameter für gewünschte Stabilitätsränder.
    - **Iteration**: Wenn Ränder/Dynamik unzureichend, Parameter anpassen (z. B. I-Anteil für Phase bei niedrigen Frequenzen, D-Anteil für höhere Frequenzen), Schritte wiederholen.

### Anpassungen bei Schwingen (PID-Regler)

- Schwingen deutet auf Instabilität oder geringe Dämpfung hin. Um zu beseitigen:
  - **Verringern von k_p (Proportionalanteil)**: Senkt Kreisverstärkung; erhöht Amplitudenrand, verschiebt Schnittfrequenz; Pole wandern in linke Halbebene.
  - **Erhöhen von T_I (Integralzeit)**: Verringert I-Anteil; verschiebt Phasenabfall zu höheren Frequenzen; größerer Phasenrand; Kurvenverlauf flacher.
  - **Erhöhen von T_D (Differenzialzeit)**: Erhöht D-Anteil; fügt Phasenreserve hinzu; Pole weg von imaginärer Achse; erhöht Dämpfung durch Nullstelle in linker Halbebene.

 ---

 ### Ergänzungen zu deinen Grundkenntnissen in der Regelungstechnik

Deine Notizen sind bereits eine starke Basis und decken die Kernkonzepte der klassischen und modernen Regelungstechnik umfassend ab. Basierend auf Standard-Lehrbüchern und Skripten (z. B. aus Universitätsquellen wie TU Braunschweig oder Uni Siegen), hier einige sinnvolle Ergänzungen, die oft als grundlegend gelten, aber in deinen Notizen entweder fehlen oder nur implizit erwähnt sind. Ich habe sie thematisch gruppiert und priorisiere Essentials, die das Verständnis vertiefen, ohne zu weit in fortgeschrittene Themen abzudriften. Jede Ergänzung enthält eine kurze Erklärung, warum sie wichtig ist, und Beispiele.

#### Mathematische Grundlagen
- **Laplace-Transformation**: Dies ist die mathematische Basis für Übertragungsfunktionen und Frequenzbereichsanalysen (z. B. Bode-Diagramme). Sie wandelt Differentialgleichungen in algebraische Gleichungen um. Ergänzung: Lerne, wie man eine Übertragungsfunktion G(s) aus einer Differentialgleichung ableitet, z. B. für ein PT1-Glied: Aus y' + a y = b u folgt G(s) = b / (s + a). Warum? Ohne das kannst du Modelle nicht selbst aufbauen.
- **Blockdiagramme und Signalflussgraphen**: Visuelle Darstellungen von Regelkreisen (z. B. Serien-, Parallel- und Rückkopplungsschaltungen). Ergänzung: Regeln zur Vereinfachung, wie Mason's Gain Formula für komplexe Schleifen. Warum? Hilft, Systeme zu modellieren und zu analysieren, bevor du zu Wurzelortskurven oder Bode gehst.

#### Erweiterte Stabilitäts- und Analysewerkzeuge
- **Routh-Hurwitz-Kriterium (Erweiterung zum Hurwitz)**: Ein Verfahren, um Stabilität ohne Wurzelberechnung zu prüfen, indem man eine Tabelle aus Koeffizienten des charakteristischen Polynoms aufbaut. Ergänzung: Es zeigt nicht nur Stabilität, sondern auch, wie viele Pole in der rechten Halbebene liegen. Warum? Praktisch für höhergradige Systeme, wo Hurwitz allein zu aufwendig ist.
- **Phasen- und Amplitudenrand (Gain/Phase Margin)**: Du hast sie kurz erwähnt, aber ergänze: Phase Margin ist der Abstand zur -180°-Linie bei Gain=1; Gain Margin der Abstand zu Gain=1 bei Phase=-180°. Typische Werte: Phase Margin > 45° für gute Dämpfung. Warum? Quantifiziert Robustheit und hilft beim Tuning.

#### Reglerdesign und Tuning
- **PID-Tuning-Methoden**: Deine Notizen decken PID-Strukturen ab, aber ergänze praktische Tuning-Verfahren wie Ziegler-Nichols (offene oder geschlossene Schleife: Bringe System zum Schwingen, berechne K_p, T_I, T_D aus Periodendauer). Oder Chien-Hrones-Reswick für bessere Überschwingungskontrolle. Warum? Theorie allein reicht nicht; Tuning macht Regler anwendbar.
- **Zustandsbeobachter (Observer)**: Ergänzung zu Beobachtbarkeit: Ein Luenberger-Observer schätzt unmessbare Zustände aus Ausgängen. Formel: \hat{x}' = A \hat{x} + B u + L (y - C \hat{x}). Warum? In der Praxis sind nicht alle Zustände messbar; essenziell für Zustandsrückführung.

#### Digitale und Praktische Aspekte
- **Diskrete Regelung (Z-Transformation)**: Ergänzung zur kontinuierlichen Regelung: Für digitale Systeme (z. B. Mikrocontroller) wandelt man s in z um (z = e^{s T}, T=Abtastzeit). Stabilität: Pole innerhalb des Einheitskreises. Warum? Die meisten modernen Systeme sind digital; ignoriere das nicht.
- **Nichtlineare Systeme (Grundlagen)**: Lineare Annäherung (Linearisierung um Arbeitspunkt via Taylor-Reihe). Ergänzung: Konzepte wie Limit Cycles oder Bifurkationen. Warum? Reale Systeme sind oft nichtlinear (z. B. Sättigung); Grundkenntnisse helfen, Grenzen der linearen Theorie zu verstehen.

#### Anwendungen und Tools
- **Praktische Beispiele**: Ergänze reale Anwendungen, z. B. Cruise Control (Geschwindigkeitsregelung im Auto: PT1-Strecke mit PI-Regler) oder Inverted Pendulum (instabile Strecke, stabilisiert via Zustandsrückführung). Warum? Verknüpft Theorie mit Praxis und motiviert.
- **Simulationswerkzeuge**: Kurze Einführung in MATLAB/Simulink oder Python (mit control-Bibliothek) für Simulation von Regelkreisen. Ergänzung: Befehle wie tf() für Transferfunktionen oder rlocus() für Wurzelortskurven. Warum? Ermöglicht Experimente und Validierung deiner Notizen.

Diese Ergänzungen bauen direkt auf deinen Notizen auf und machen sie runder – z. B. von der Theorie zur Anwendung. Wenn du dich auf ein Thema konzentrieren möchtest (z. B. PID-Tuning mit Beispielen), lass es mich wissen, ich kann das vertiefen!

---

### PID-Tuning: Erklärung und Beispiele

Vielen Dank für deine Rückmeldung! PID-Tuning ist ein zentraler Teil der Regelungstechnik, da es darum geht, die Parameter eines PID-Reglers (Proportionalanteil \(K_p\), Integralzeit \(T_i\) und Differenzialzeit \(T_d\)) so anzupassen, dass das System stabil, schnell und genau reagiert. Ein PID-Regler hat die Form:

\[
u(t) = K_p \left( e(t) + \frac{1}{T_i} \int e(t) \, dt + T_d \frac{de(t)}{dt} \right)
\]

wo \(u(t)\) der Stellwert und \(e(t)\) der Regelabweichung ist. Tuning-Methoden helfen, diese Parameter empirisch oder heuristisch zu bestimmen.

Ich konzentriere mich hier auf die gängigste Methode: **Ziegler-Nichols (ZN)**, da sie einfach und weit verbreitet ist. Sie gibt aggressive Einstellungen für eine "Quarter-Wave-Decay"-Antwort (das System schwingt mit abnehmender Amplitude um 1/4 pro Periode). Ich erkläre die Closed-Loop-Methode (Ultimate-Gain-Methode) detailliert, da sie in deinen Notizen implizit vorkommt (z. B. bei Schwingen beheben), und gebe ein numerisches Beispiel. Am Ende ergänze ich kurz die Open-Loop-Methode und andere Ansätze.

#### Ziegler-Nichols Closed-Loop-Methode (Ultimate-Gain-Methode)
Diese Methode basiert auf dem Schwingen des Systems unter rein proportionaler Regelung. Sie eignet sich für Systeme, die oszillieren können, und zielt auf gute Störunterdrückung ab, kann aber Überschwingen verursachen.

**Schritte:**
1. Setze Integral- und Differenzialanteil auf Null (\(T_i = \infty\) oder sehr groß, \(T_d = 0\)) – nur P-Regler.
2. Erhöhe \(K_p\) schrittweise, bis das System stabile, konstante Oszillationen zeigt (Grenzstabilität). Notiere den kritischen Gain \(K_u\) (ultimate gain) und die Oszillationsperiode \(P_u\) (ultimate period).
3. Berechne die PID-Parameter mit der folgenden Tabelle (klassische ZN-Regeln):

| Reglertyp | \(K_p\)     | \(T_i\)       | \(T_d\)       |
|-----------|-------------|---------------|---------------|
| P         | \(0.5 K_u\) | -             | -             |
| PI        | \(0.45 K_u\)| \(P_u / 1.2\) | -             |
| PID       | \(0.6 K_u\) | \(P_u / 2\)   | \(P_u / 8\)   |

**Hinweise:** Diese Einstellungen sind aggressiv und führen zu Überschwingen (ca. 25%). Für weniger Overshoot gibt es Varianten (z. B. "no overshoot": niedrigere \(K_p\)). Nicht für alle Systeme geeignet, z. B. wenn Oszillationen gefährlich sind.

**Numerisches Beispiel (aus einem chemischen Prozess):**  
Angenommen, du hast ein System (z. B. eine Temperaturregelung in einem Reaktor), und durch Experimente (oder Simulation) findest du \(K_u = 4.33\) und \(P_u = 6.28\) Minuten (Periode der Oszillation).  

- Für **PI-Regler**:  
  \(K_p = 0.45 \times 4.33 \approx 1.95\)  
  \(T_i = 6.28 / 1.2 \approx 5.23\) Minuten  
  \(T_d = 0\)  

- Für **PID-Regler**:  
  \(K_p = 0.6 \times 4.33 \approx 2.60\)  
  \(T_i = 6.28 / 2 = 3.14\) Minuten  
  \(T_d = 6.28 / 8 = 0.785\) Minuten  

**Systemantwort-Beschreibung:** Vor Tuning (nur P mit \(K_u\)) oszilliert das System konstant. Nach PID-Tuning zeigt die Step-Antwort (Sollwertsprung) ein schnelles Ansteigen mit Überschwingen (ca. 25% decay pro Zyklus), stabilisiert sich aber schnell. In einer Simulation (z. B. mit MATLAB) würde die Kurve oszillierend abklingen – ideal für dynamische Anwendungen wie Motorsteuerung, aber nicht für präzise Prozesse ohne Overshoot.

#### Ziegler-Nichols Open-Loop-Methode (Reaction-Curve-Methode)
Diese Methode verwendet eine Step-Antwort im offenen Regelkreis und eignet sich für Systeme mit Totzeit (z. B. Transportprozesse).  

**Schritte:**  
1. Führe einen Step-Eingang durch und zeichne die Reaktionskurve (Ausgangsantwort).  
2. Bestimme aus der Kurve: Prozessgain \(K\) (stationärer Gain), Totzeit \(L\), Zeitkonstante \(\tau\).  
3. Berechne Parameter mit dieser Tabelle: (aus Standardquellen, da dein Notiz-Fokus auf klassisch ist):  

| Reglertyp | \(K_p\)          | \(T_i\) | \(T_d\) |
|-----------|------------------|---------|---------|
| P         | \(\tau / (K L)\) | -       | -       |
| PI        | \(0.9 \tau / (K L)\) | \(3.33 L\) | -    |
| PID       | \(1.2 \tau / (K L)\) | \(2 L\) | \(0.5 L\) |

**Numerisches Beispiel:**  
Angenommen ein PT1-System mit Totzeit: Step-Antwort zeigt \(K = 1\), \(L = 1\) Sekunde, \(\tau = 5\) Sekunden.  

- Für **PID-Regler**:  
  \(K_p = 1.2 \times 5 / (1 \times 1) = 6\)  
  \(T_i = 2 \times 1 = 2\) Sekunden  
  \(T_d = 0.5 \times 1 = 0.5\) Sekunden  

Die Antwort würde eine verzögerte, abklingende Kurve zeigen, mit besserer Störunterdrückung als bei Closed-Loop.

#### Andere Tuning-Methoden (kurz, als Ergänzung)
- **Chien-Hrones-Reswick (CHR)**: Ähnlich ZN, aber mit Varianten für 0% oder 20% Overshoot. Besser für robuste Anwendungen (z. B. Klasse 3 in deinen Notizen). Beispiel: Für Setpoint-Folge ohne Overshoot, \(K_p = 0.3 \tau / (K L)\), etc.  
- **Manuelles Tuning:** Starte mit kleinem \(K_p\), erhöhe bis leichte Oszillation, dann \(T_d\) für Dämpfung, \(T_i\) für Genauigkeit. Praktisch für Feinabstimmung.  
- **Software-basiert:** In Tools wie MATLAB/Simulink oder Python (control-Bibliothek) simulieren und optimieren. Beispiel: Für dein PT2-Glied aus Notizen, simuliere Step-Response und passe Parameter an, bis Anstiegszeit < 2s und Overshoot < 10%.

Falls du ein spezifisches System (z. B. aus deinen Notizen) simulieren möchtest oder Code-Beispiele in Python brauchst, sag Bescheid – ich kann das vertiefen!


---

```python
import numpy as np
import matplotlib.pyplot as plt
from control import TransferFunction, feedback, step_response

# Beispiel: PID-Tuning für ein PT1-System (einfache Verzögerung 1. Ordnung)
# Plant: G(s) = 1 / (s + 1)  # Zeitkonstante τ=1
plant = TransferFunction([1], [1, 1])

# Ziegler-Nichols Parameter (angenommen Ku=8, Pu=π für dieses System; in Praxis messen)
Ku = 8  # Beispielwert für kritischen Gain
Pu = np.pi  # Beispiel für Oszillationsperiode

# PID-Parameter nach ZN für PID-Regler
Kp = 0.6 * Ku
Ti = Pu / 2
Td = Pu / 8

# PID-Transferfunktion: Kp (1 + 1/(Ti s) + Td s)
# In control: PID = Kp * (1 + 1/(Ti s) + Td s)
num_pid = [Kp * Td * Ti, Kp * Ti, Kp]  # Kp Td Ti s^2 + Kp Ti s + Kp
den_pid = [Ti, 0]  # Ti s (für I-Term) + D-Term oben
pid = TransferFunction(num_pid, den_pid)

# Geschlossener Regelkreis: Feedback-System
closed_loop = feedback(pid * plant)

# Simulation der Sprungantwort
t = np.linspace(0, 10, 1000)  # Zeitvektor
t_out, y_out = step_response(closed_loop, T=t)

# Plot der Antwort
plt.figure()
plt.plot(t_out, y_out, label='PID-geregelt')
plt.plot(t, np.ones_like(t), 'r--', label='Sollwert')
plt.xlabel('Zeit [s]')
plt.ylabel('Ausgang')
plt.title('Sprungantwort eines PT1-Systems mit PID-Regler (ZN-Tuning)')
plt.legend()
plt.grid(True)
plt.show()
```

### Erklärung
Dieser Code simuliert ein einfaches PT1-System mit einem PID-Regler, getunt nach Ziegler-Nichols Closed-Loop-Methode. 
- **Plant**: Ein PT1-Glied (aus deinen Notizen), G(s) = 1/(s+1).
- **Tuning**: Verwendet Beispielwerte für Ku und Pu (in der Praxis aus Experimenten ableiten).
- **Ausgabe**: Plottet die Step-Response – das System sollte schnell ansteigen, etwas überschwingen und stabilisieren.
- **Ausführen**: Kopiere den Code in Python (mit installierten Paketen: numpy, matplotlib, python-control). Der Plot zeigt die Regelgüte.

Falls du ein anderes System (z.B. PT2) oder spezifische Parameter simulieren möchtest, gib mehr Details!
