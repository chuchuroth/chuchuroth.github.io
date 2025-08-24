
# chatgpt
Sehr gut – deine 9 Themen decken die ganze Kette von Grundlagen bis zu High-Level-Anwendungen ab. Für die **Gestaltung des Praktikums "Rechnergestützte Verfahren der Mess- und Regelungstechnik"** solltest du pro Versuch jeweils drei Aspekte ausarbeiten:

* **Lernziel** (Welche Kompetenz wird vermittelt?)
* **Laborablauf** (Schritte, Methoden, Zeitrahmen)
* **Prototyp des Versuchsstands** (Welche Geräte, Sensoren/Aktoren, Software sind nötig?)

Ich ergänze dir die Details zu deinen 9 Punkten, mit Fokus auf Ablauf & Aufbau der Versuchsstände:

---

### 1. Digitaltechnik

* **Lernziel:** Grundlagen der digitalen Signalrepräsentation, Abtastung, Quantisierung, Codierung.
* **Laborablauf:**

  * Einfache Messungen mit A/D- und D/A-Wandlern (z.B. Sinussignal einlesen und rekonstruieren).
  * Fehleranalyse bei Unterabtastung und Quantisierung.
  * Einführung in Logikanalysator und FPGA-Boards für einfache Logikschaltungen.
* **Versuchsstand:** Funktionsgenerator, A/D-D/A-Modul (z.B. NI-DAQ oder Arduino mit Shield), PC mit MATLAB/Simulink oder LabVIEW, FPGA-Board (z.B. Xilinx Basys3).

---

### 2. Digitales Speicheroszilloskop und digitaler Spektrum-Analysator

* **Lernziel:** Signalvisualisierung, Frequenzanalyse, FFT-Anwendung.
* **Laborablauf:**

  * Signale aufnehmen (Rechteck, Rauschen, modulierte Signale).
  * Analyse im Zeit- und Frequenzbereich mit Oszi & Spektrumanalysator.
  * Vergleich: Hardwaremessung vs. MATLAB-FFT.
* **Versuchsstand:** Digitales Speicheroszilloskop (DSO), Spektrumanalysator (USB-Dongle oder Laborgerät), Signalgenerator, MATLAB/Simulink.

---

### 3. Ultraschall-Computertomographie

* **Lernziel:** Prinzip der Bildgebung durch Laufzeitmessung und Rekonstruktion.
* **Laborablauf:**

  * Ultraschallimpulse durch Proben senden, Laufzeiten messen.
  * Daten in MATLAB verarbeiten und 2D-Rekonstruktion erstellen.
  * Vergleich verschiedener Rekonstruktionsalgorithmen.
* **Versuchsstand:** Ultraschallsender/Empfänger (z.B. 40 kHz), Wasserbecken, Probekörper, Mikrocontroller oder NI-DAQ für Datenerfassung, PC mit MATLAB.

---

### 4. Beleuchtung und Bildgewinnung

* **Lernziel:** Einfluss der Beleuchtung auf Bildqualität.
* **Laborablauf:**

  * Aufnahme derselben Szene mit unterschiedlichen Beleuchtungsarten (diffus, direkt, LED, IR).
  * Vergleich von Bildqualität (Kontrast, Signal-Rausch-Verhältnis).
  * Kamera-Kalibrierung (Linsenverzerrung).
* **Versuchsstand:** Standard-Industriekamera (USB3, GigE), verschiedene LED-Lichtquellen, Lichtkammer mit regelbarer Umgebung.

---

### 5. Digitale Bildverarbeitung

* **Lernziel:** Filterung, Kantenextraktion, Merkmalsdetektion.
* **Laborablauf:**

  * Bildvorverarbeitung (Glättung, Medianfilter, Histogrammgleichung).
  * Kantenfilter (Sobel, Canny).
  * Merkmalsextraktion (Konturen, Ecken).
* **Versuchsstand:** PC mit MATLAB Image Processing Toolbox oder Python (OpenCV), Kamerasignal oder Testbilder.

---

### 6. Bildauswertung

* **Lernziel:** Automatische Sichtprüfung.
* **Laborablauf:**

  * Werkstück mit Defekten aufnehmen (Bohrungen, Risse, Oberflächenfehler).
  * Objekterkennung per Segmentierung und Klassifikation.
  * Vergleich: klassische Verfahren vs. ML-Ansatz (z.B. SVM oder CNN).
* **Versuchsstand:** Kamera mit definierter Teststrecke, Musterteile, PC mit MATLAB/Simulink oder Python/OpenCV.

---

### 7. Reglersynthese und Simulation

* **Lernziel:** Klassische Regelung (P, PI, PID) und digitale Umsetzung.
* **Laborablauf:**

  * Simulation eines einfachen Streckensystems in Simulink (z.B. Motor, Heizung).
  * Reglertuning (Ziegler-Nichols, MATLAB Control System Toolbox).
  * Umsetzung auf Hardware (z.B. DC-Motor mit Encoder).
* **Versuchsstand:** PC mit MATLAB/Simulink, Arduino oder dSPACE MicroLabBox, DC-Motor mit Encoder.

---

### 8. Roboter: Sensorik

* **Lernziel:** Erfassung von Zuständen (Position, Kraft, Abstand).
* **Laborablauf:**

  * Einbau verschiedener Sensoren (IR, Ultraschall, Kraftsensor).
  * Kalibrierung und Signalaufbereitung.
  * Datenfusion mehrerer Sensoren.
* **Versuchsstand:** Kleiner mobiler Roboter oder Roboterarm (z.B. Dobot, TurtleBot), Sensorpakete (Lidar, Kamera, Ultraschall).

---

### 9. Roboter: Aktorik und Bahnplanung

* **Lernziel:** Steuerung von Antrieben und Trajektorienplanung.
* **Laborablauf:**

  * Basisübung: Motor ansteuern, Drehzahlregelung.
  * Bahnplanung: Geradeausfahrt, Kreisbahn, Hindernisumfahrung.
  * Vergleich: Open-Loop vs. Closed-Loop.
* **Versuchsstand:** Mobiler Roboter mit Differentialantrieb (z.B. TurtleBot oder LEGO EV3/NXT), PC mit ROS oder MATLAB Robotics Toolbox.

---

👉 Damit hättest du eine klare Linie: **Grundlagen (1–2) → Bildgebung & Signalverarbeitung (3–6) → Regelung (7) → Robotik als Anwendung (8–9).**

Soll ich dir daraus ein **komplettes Ablaufkonzept für das Semesterpraktikum (z.B. 6–8 Termine à 4 Stunden)** strukturieren, inkl. Vorschlag für Reihenfolge und benötigte Hardware/Software-Budgets?

---

# claude
# Praktikumsdesign: Rechnergestützte Verfahren der Mess- und Regelungstechnik

## 1. Digitaltechnik

### Lernziele
- Verstehen von A/D- und D/A-Wandlung
- Abtasttheorem und Aliasing-Effekte
- Quantisierungsrauschen und Auflösung

### Laborablauf (3 Stunden)
**Phase 1: Grundlagen (45 min)**
- Theoretische Einführung in Sampling und Quantisierung
- MATLAB-Simulation verschiedener Abtastraten
- Demonstration von Aliasing-Effekten

**Phase 2: Praktische Messungen (90 min)**
- A/D-Wandlung analoger Signale verschiedener Frequenzen
- Vergleich verschiedener Abtastraten (fs < 2f, fs = 2f, fs >> 2f)
- Analyse des Quantisierungsrauschens bei verschiedenen Bit-Auflösungen

**Phase 3: Auswertung (45 min)**
- FFT-Analyse der digitalisierten Signale
- Bewertung der Signalqualität (SNR, THD)

### Versuchsstand-Prototyp
**Hardware:**
- NI myDAQ oder Arduino mit ADC/DAC
- Funktionsgenerator (1 Hz - 20 kHz)
- Tiefpassfilter (Anti-Aliasing)
- PC mit MATLAB/LabVIEW

**Software:**
- MATLAB-Scripts für Signalanalyse
- Grafische Darstellung von Zeit- und Frequenzbereich
- Parameter-Interface für Abtastrate und Auflösung

---

## 2. Digitales Speicheroszilloskop und digitaler Spektrum-Analysator

### Lernziele
- Funktionsweise digitaler Messgeräte
- FFT-basierte Spektralanalyse
- Trigger-Konzepte und Messfehler

### Laborablauf (3 Stunden)
**Phase 1: Oszilloskop-Grundlagen (60 min)**
- Konfiguration von Trigger, Zeitbasis und Kopplung
- Messung von Amplitude, Frequenz und Phase
- Cursor-Messungen und automatische Messungen

**Phase 2: Spektralanalyse (90 min)**
- FFT-Funktion des Oszilloskops vs. dedizierter Spektrum-Analysator
- Fensterfunktionen und deren Einfluss
- Messung von Harmonischen und Störsignalen

**Phase 3: Vergleichsmessungen (30 min)**
- Analog- vs. Digital-Oszilloskop
- Vor- und Nachteile verschiedener Ansätze

### Versuchsstand-Prototyp
**Hardware:**
- Digitales Speicheroszilloskop (z.B. Rigol DS1054Z)
- Spektrum-Analysator oder PC-basierte Lösung
- Signal-Generator mit verschiedenen Signalformen
- Störsignal-Generator

**Messaufgaben:**
- AM/FM-modulierte Signale
- Rechteck- und Dreieckssignale
- Rauschbehaftete Signale

---

## 3. Ultraschall-Computertomographie

### Lernziele
- Grundlagen der Ultraschall-Bildgebung
- Back-Projection-Algorithmus
- Signallaufzeiten und Dämpfung

### Laborablauf (4 Stunden)
**Phase 1: Ultraschall-Grundlagen (60 min)**
- Schallgeschwindigkeit in verschiedenen Medien
- Reflexion und Transmission
- Transducer-Charakteristik

**Phase 2: Tomographie-Aufbau (120 min)**
- Mechanischer Scanner mit Schrittmotoren
- Mehrere Ultraschall-Sensoren in verschiedenen Winkeln
- Durchschallung von Testobjekten (Kunststoffzylinder, Hohlräume)

**Phase 3: Rekonstruktion (60 min)**
- Datenerfassung und Vorverarbeitung
- Back-Projection-Algorithmus in MATLAB
- 2D-Bildrekonstruktion und Visualisierung

### Versuchsstand-Prototyp
**Hardware:**
- Ultraschall-Transducer (40 kHz)
- Rotations-/Translationseinheit mit Schrittmotoren
- Wasserbad oder Gel-Kopplung
- Verstärker und Filterelektronik
- Testobjekte verschiedener Geometrien

**Software:**
- MATLAB-basierte Rekonstruktionssoftware
- Motorsteuerung über Arduino/Raspberry Pi
- Echtzeit-Datenvisualisierung

---

## 4. Beleuchtung und Bildgewinnung

### Lernziele
- Beleuchtungstechniken für die Bildverarbeitung
- Kamera-Parameter und Kalibrierung
- Bildqualität und Störeinflüsse

### Laborablauf (3 Stunden)
**Phase 1: Beleuchtungskonzepte (60 min)**
- Durchlicht, Auflicht, Streulicht
- LED-Arrays vs. diffuse Beleuchtung
- Einfluss von Beleuchtungswinkel und -intensität

**Phase 2: Kamera-Setup (90 min)**
- Objektiv-Auswahl und Fokussierung
- Belichtungszeit, Blende, ISO-Einstellungen
- Kamera-Kalibrierung mit Schachbrettmuster

**Phase 3: Bildqualitätsbewertung (30 min)**
- Histogramm-Analyse
- Kontrast- und Schärfemessungen
- Rauschcharakteristik

### Versuchsstand-Prototyp
**Hardware:**
- Industriekamera (z.B. Basler acA1300)
- Variable LED-Beleuchtung (Ring-, Backlight-, Darkfield)
- Mechanische Verstelleinrichtung
- Testtargets (Siemensstern, Schachbrett)

**Software:**
- OpenCV/MATLAB für Bildanalyse
- Kamera-Software für Live-Vorschau
- Beleuchtungssteuerung

---

## 5. Digitale Bildverarbeitung

### Lernziele
- Grundoperationen der Bildverarbeitung
- Filter und Morphologie
- Fourier-Transformation in der Bildverarbeitung

### Laborablauf (4 Stunden)
**Phase 1: Punktoperationen (60 min)**
- Histogramm-Stretching und -Equalization
- Gamma-Korrektur
- Arithmetische Operationen

**Phase 2: Lokale Operationen (90 min)**
- Glättungsfilter (Gauß, Median)
- Kantendetektions-Filter (Sobel, Canny)
- Morphologische Operationen

**Phase 3: Globale Operationen (90 min)**
- 2D-FFT und Frequenzbereich-Filterung
- Geometrische Transformationen
- Template Matching

### Versuchsstand-Prototyp
**Hardware:**
- Standard-PC mit Bildverarbeitungs-Software
- Kamera aus Versuch 4
- Verschiedene Testobjekte

**Software:**
- MATLAB Image Processing Toolbox
- OpenCV-basierte GUI
- Interaktive Parameter-Einstellung
- Vorher/Nachher-Vergleich in Echtzeit

---

## 6. Bildauswertung

### Lernziele
- Feature-Extraktion und -Beschreibung
- Objekterkennung und -klassifikation
- Messtechnische Auswertung

### Laborablauf (4 Stunden)
**Phase 1: Feature-Extraktion (90 min)**
- Blob-Analyse (Fläche, Umfang, Schwerpunkt)
- Kontur-Analyse und -Approximation
- Textur-Features (LBP, GLCM)

**Phase 2: Objekterkennung (90 min)**
- Template Matching
- SIFT/SURF-Features
- Maschinelles Lernen (SVM, Neural Networks)

**Phase 3: Metrische Auswertung (60 min)**
- Kalibrierung Pixel → mm
- Abstandsmessungen
- Winkelmessungen

### Versuchsstand-Prototyp
**Hardware:**
- Kamera-Setup aus vorherigen Versuchen
- Präzisions-Messobjekte (Kugeln, Bleche)
- Referenz-Maßstab

**Software:**
- MATLAB/OpenCV-basierte Analysetools
- Statistik-Tools für Messgenauigkeit
- Automated Optical Inspection (AOI) Demo

---

## 7. Reglersynthese und Simulation

### Lernziele
- Digitale Regelungsalgorithmen
- PID-Regler-Entwurf und -Optimierung
- Simulation vs. Realität

### Laborablauf (4 Stunden)
**Phase 1: Systemidentifikation (60 min)**
- Sprungantwort-Messung
- Frequenzgang-Messung
- Parameterschätzung

**Phase 2: Regler-Entwurf (120 min)**
- PID-Parameter-Optimierung
- Erweiterte Regelungsverfahren (IMC, MPC)
- Simulink-Modellierung

**Phase 3: Implementierung (60 min)**
- Real-Time-Implementation auf Hardware
- Performance-Vergleich Simulation vs. Realität
- Robustheitstests

### Versuchsstand-Prototyp
**Hardware:**
- DC-Motor mit Encoder
- Temperatur-Regelstrecke
- Real-Time-Hardware (Raspberry Pi, Arduino, oder dSPACE)
- Verschiedene Sensoren (Temperatur, Position, Geschwindigkeit)

**Software:**
- MATLAB/Simulink mit Real-Time-Toolbox
- Automatische Code-Generierung
- Monitoring und Datenlogging

---

## 8. Roboter: Sensorik

### Lernziele
- Roboter-Sensorik und Sensor-Fusion
- Lokalisierung und Mapping
- Kalibrierung von Sensorsystemen

### Laborablauf (4 Stunden)
**Phase 1: Einzelsensoren (90 min)**
- Ultraschall, Infrarot, Kamera
- Charakterisierung und Kalibrierung
- Messgenauigkeit und -bereiche

**Phase 2: Sensor-Fusion (90 min)**
- Kalman-Filter für Positions-/Geschwindigkeitsschätzung
- IMU + Encoder Integration
- Probabilistische Sensorfusion

**Phase 3: SLAM-Grundlagen (60 min)**
- Simultaneous Localization and Mapping
- Grid-Maps und Feature-Maps
- Particle Filter

### Versuchsstand-Prototyp
**Hardware:**
- Mobile Roboter-Plattform (TurtleBot, Khepera)
- Sensorsuite: Lidar, Kamera, IMU, Encoder
- Structured Environment mit Landmarks
- Ground-Truth-System (Motion Capture oder Positionierraster)

**Software:**
- ROS (Robot Operating System)
- SLAM-Toolbox (gmapping, cartographer)
- Visualisierung mit RViz

---

## 9. Roboter: Aktorik und Bahnplanung

### Lernziele
- Kinematik und Dynamik von Robotern
- Trajektorien-Planung und -Optimierung
- Motion Control

### Laborablauf (4 Stunden)
**Phase 1: Kinematik (60 min)**
- Forward/Inverse Kinematics
- Jacobi-Matrix und Singularitäten
- Workspace-Analyse

**Phase 2: Bahnplanung (120 min)**
- Point-to-Point-Bewegungen
- Spline-basierte Trajektorien
- Kollisionsvermeidung

**Phase 3: Regelung (60 min)**
- Gelenkraum- vs. Arbeitsraum-Regelung
- Feedforward + Feedback Control
- Compliance Control

### Versuchsstand-Prototyp
**Hardware:**
- 6-DOF Industrie-Roboterarm (z.B. UR5, KUKA iiwa)
- Kraftmoment-Sensor
- Greifer-System
- Obstacles für Bahnplanung

**Software:**
- ROS MoveIt! für Motion Planning
- MATLAB Robotics Toolbox
- Real-time Visualization
- Safety Monitoring

---

## Übergreifende Aspekte

### Labororganisation
- **Dauer:** Je Versuch 3-4 Stunden
- **Gruppengröße:** 2-3 Studierende
- **Rotation:** 3 Wochen pro Versuch
- **Dokumentation:** Digitales Laborbuch mit MATLAB/Python-Code

### Gemeinsame Infrastruktur
- **Hardware:** Modulares System mit austauschbaren Komponenten
- **Software:** Einheitliche MATLAB/Python-Umgebung
- **Datenmanagement:** Zentraler Server für Versuchsdaten
- **Safety:** Notaus-Systeme bei allen motorischen Versuchen

### Assessment
- **Pre-Lab:** Theoretische Vorbereitung (20%)
- **Durchführung:** Praktische Arbeit und Teamwork (40%)
- **Post-Lab:** Auswertung und Bericht (40%)
- **Bonus:** Innovative Lösungsansätze und Erweiterungen

---

# grok

### Schlüsselaspekte für das Praktikumsdesign
- **Modularer Aufbau**: Die 9 Ideen können sequentiell strukturiert werden, beginnend mit Grundlagen der Digitaltechnik und fortschreitend zu komplexen Anwendungen wie Robotik, um einen logischen Lernpfad zu schaffen. Dies fördert praxisnahe Kenntnisse in rechnergestützter Mess- und Regelungstechnik.
- **Fokus auf Praxis und Software**: MATLAB/Simulink als zentrale Tools einsetzen, ergänzt durch Hardware-Prototypen, um Simulation und reale Umsetzung zu verbinden. Es scheint sinnvoll, Gruppenarbeit zu integrieren, um Flexibilität zu gewährleisten.
- **Sicherheit und Machbarkeit**: Prototypen sollten kostengünstig und skalierbar sein, mit Fokus auf offene Plattformen wie Arduino für Robotik oder Standard-Laborausrüstung für Bildverarbeitung, um Zugänglichkeit zu gewährleisten.
- **Bewertung und Erweiterung**: Jeder Versuch könnte mit Vor- und Nachbereitung enden, inklusive Berichten; kontroverse Aspekte wie Genauigkeit in Ultraschall-CT sollten betont werden, um kritische Reflexion zu fördern.

#### Überblick über die Struktur
Das Praktikum könnte in 9 Module unterteilt werden, jeweils 2-4 Stunden dauernd, mit einer Einführung in MATLAB/Simulink. Priorisiere hands-on-Aktivitäten: Studenten beginnen mit Simulationen, gehen zu Hardware-Tests über und analysieren Ergebnisse. Integriere Sicherheitschecks, z.B. bei Robotik, und optionale Erweiterungen für fortgeschrittene Gruppen.

#### Empfohlene Ressourcen
Nutze offene Bibliotheken wie Image Processing Toolbox in MATLAB für Bildverarbeitung oder Control System Toolbox für Regelung. Hardware-Prototypen basieren auf gängigen Komponenten: Digitale Oszilloskope (z.B. Rigol DS1054Z), Kameras für Bildgewinnung und LEGO Mindstorms oder Arduino-Roboter-Kits für Robotik. Kosten pro Stand: ca. 200-500 €, skalierbar für 5-10 Gruppen.

#### Potenzielle Herausforderungen
Es könnte zu Ungenauigkeiten in realen Messungen kommen, z.B. durch Rauschen in Signalen; hege daher Ergebnisse ab, indem du betont, dass Simulationen idealisieren und reale Tests variieren. Für kontroverse Themen wie Bildauswertung in Automatisierung diskutiere ethische Aspekte empathisch, ohne Partei zu ergreifen.

---

### Detailliertes Design des Praktikums "Rechnergestützte Verfahren der Mess- und Regelungstechnik"

Dieser umfassende Entwurf baut auf den 9 Ideen auf und integriert bewährte Praktiken aus ähnlichen Laborprogrammen an Universitäten wie dem KIT (Karlsruher Institut für Technologie) oder der University of Maryland. Der Fokus liegt auf der Erstellung detaillierter Laborabläufe – schrittweise Anleitungen für Studenten – und Prototypen der Versuchsstände, die kostengünstig, flexibel und praxisorientiert sind. Jeder Versuch ist so gestaltet, dass er aufbauend wirkt: Von grundlegenden digitalen Prinzipien über Signalverarbeitung und Bildtechniken bis hin zu Regelung und Robotik-Anwendungen. Die Gesamtdauer beträgt ca. 9-12 Sitzungen à 3-4 Stunden, mit MATLAB/Simulink als Kernsoftware für Simulation und Echtzeit-Implementierung. Hardware-Prototypen nutzen Standardkomponenten, um Kosten unter 1000 € pro Stand zu halten, und ermöglichen Gruppenarbeit (2-4 Studenten pro Stand).

#### Allgemeine Rahmenbedingungen für das Praktikum
Vor jedem Versuch: Eine 15-minütige Einführung in Theorie und Sicherheitsregeln (z.B. Umgang mit Elektrik, Lasern oder Robotern). Nachbereitung: Analyse der Daten in einem Bericht, inklusive Vergleich von Simulation und Realität. Tools: MATLAB R2023a mit Toolboxes (Signal Processing, Image Processing, Control System), Simulink für Regelkreise. Prototypen sind modular, z.B. mit Breadboards für schnelle Anpassungen. Für digitale Umsetzung: Schnittstellen wie NI DAQmx oder Arduino für Echtzeit-Datenakquise. Ziel: Vermittlung von Kenntnissen in automatischer Sichtprüfung, Bildverarbeitung und Regelung, wie in der Praktikumsbeschreibung erwähnt.

#### 1. Digitaltechnik
**Laborablauf**: 
1. Einführung in digitale Signale: Studenten generieren Sinus- und Rechtecksignale in MATLAB und visualisieren sie (stem-Funktion).
2. Quantisierung und Sampling: Implementieren der Sampling-Theorem-Verifikation durch Aliasing-Demonstration.
3. Hardware-Test: Verbinden eines Signalgenerators mit einem Arduino, messen und plotten der digitalisierten Signale.
4. Analyse: Berechnen von Fehlern durch Quantisierung und Diskussion von Rauscheffekten.
Dauer: 3 Stunden. Erweiterung: Implementierung eines einfachen Digitalfilters.

**Prototyp des Versuchsstands**: Ein Breadboard mit Arduino Uno (ca. 20 €), ADC-Wandler, Signalgenerator (z.B. Funktionsgenerator aus dem Labor) und Laptop mit MATLAB-Arduino-Support-Package. Kosten: 50 €. Skalierbar für 10 Stände durch Reuse von Komponenten.

#### 2. Digitales Speicheroszilloskop und digitaler Spektrum-Analysator
**Laborablauf**:
1. Setup: Kalibrieren eines digitalen Oszilloskops in Simulink zur Erfassung von Signalen.
2. Messung: Erfassen von Zeitdomänen-Signalen (z.B. Sinus mit Rauschen) und Umwandlung in Frequenzdomäne via FFT in MATLAB.
3. Analyse: Vergleichen von Spektren vor/nach Filterung; Identifizieren von Harmonischen.
4. Praktische Anwendung: Messen realer Signale (z.B. Audio) und Export der Daten für Bericht.
Dauer: 4 Stunden. Fokus: Präzise Messung, mit Diskussion über Auflösung und Bandbreite.

**Prototyp des Versuchsstands**: Digitales Oszilloskop (z.B. PicoScope 2000-Serie, ca. 150 €) integriert mit MATLAB-Instrument Control Toolbox; Spektrum-Analysator-Software in Simulink. Ergänzt durch Mikrofon/Sensor für reale Signale. Kosten: 200 € pro Stand.

#### 3. Ultraschall-Computertomographie
**Laborablauf**:
1. Theorie: Erklären von Tomographie-Prinzipien in MATLAB (Simulation von Wellenausbreitung).
2. Datenakquise: Positionieren von Ultraschall-Transducern um ein Phantom-Objekt, Erfassen von Signalen.
3. Rekonstruktion: Implementieren eines Backprojection-Algorithmus in MATLAB zur Bildgenerierung.
4. Evaluation: Vergleichen mit Referenzbildern; Diskussion von Artefakten und Auflösung.
Dauer: 4 Stunden. Erweiterung: In-vivo-Simulation für medizinische Anwendungen, mit Betonung auf potenziellen Ungenauigkeiten durch Gewebevariationen.

**Prototyp des Versuchsstands**: Ringförmiges Setup mit 8-16 Ultraschall-Transducern (z.B. Piezo-Sensoren, ca. 100 €), Arduino für Steuerung und Wassergefülltes Phantom (aus 3D-Druck). MATLAB-Skript für Rekonstruktion. Kosten: 300 €, basierend auf offenen Designs aus Forschungsprototypen.

#### 4. Beleuchtung und Bildgewinnung
**Laborablauf**:
1. Setup: Kalibrieren von Beleuchtung (LED-Arrays) und Kamera in MATLAB.
2. Akquise: Aufnehmen von Bildern unter variierender Beleuchtung (z.B. diffus vs. direkt).
3. Verarbeitung: Anpassen von Helligkeit/Kontrast via Histogram-Analyse.
4. Analyse: Bewerten der Bildqualität und Auswirkungen auf nachfolgende Verarbeitung.
Dauer: 3 Stunden. Fokus: Optimale Bedingungen für Sichtprüfung.

**Prototyp des Versuchsstands**: USB-Kamera (z.B. Raspberry Pi Cam, 30 €), verstellbare LED-Beleuchtung (Ringlicht, 50 €) und Stativ. MATLAB Image Acquisition Toolbox. Kosten: 100 €.

#### 5. Digitale Bildverarbeitung
**Laborablauf**:
1. Grundoperationen: Laden von Bildern in MATLAB, Anwenden von Graustufen-Konvertierung und Negativ-Transformation.
2. Filterung: Implementieren von Glättungs- und Schärfungsfiltern (z.B. Gaussian, Sobel).
3. Transformationen: FFT für Frequenzdomäne-Analyse und Rauschunterdrückung.
4. Evaluation: Vergleichen von Original und verarbeitetem Bild; Metriken wie PSNR berechnen.
Dauer: 4 Stunden. Erweiterung: Echtzeit-Verarbeitung mit Webcam.

**Prototyp des Versuchsstands**: Laptop mit MATLAB Image Processing Toolbox, ergänzt durch Testobjekte (z.B. Schablonen). Keine zusätzliche Hardware nötig, Kosten: 0 € (nutzt bestehende Lab-Rechner).

#### 6. Bildauswertung
**Laborablauf**:
1. Segmentierung: Anwenden von Thresholding und Edge-Detection auf akquirierten Bildern.
2. Feature-Extraktion: Berechnen von Konturen, Flächen und Formfaktoren in MATLAB.
3. Klassifikation: Einfache Mustererkennung (z.B. Objekterkennung via Template-Matching).
4. Bericht: Diskussion von Genauigkeit und Anwendungen in Qualitätskontrolle.
Dauer: 3 Stunden. Fokus: Automatische Sichtprüfung, mit empathischer Betrachtung von Fehlklassifikationen in realen Szenarien.

**Prototyp des Versuchsstands**: Erweiterung des Bildgewinnungs-Stands mit MATLAB-Skripten für Analyse. Kosten: 50 € für zusätzliche Testmuster.

#### 7. Reglersynthese und Simulation
**Laborablauf**:
1. Modellierung: Erstellen eines Regelkreises in Simulink (z.B. PID-Regler für ein Masse-Feder-System).
2. Synthese: Tunen von Parametern via Root-Locus oder Bode-Plot in MATLAB.
3. Simulation: Testen von Stabilität und Antwort auf Störungen.
4. Validierung: Vergleichen mit realen Daten (z.B. aus Oszilloskop-Messungen).
Dauer: 4 Stunden. Erweiterung: Hardware-in-the-Loop mit Arduino.

**Prototyp des Versuchsstands**: Simulink-Modell mit Control System Toolbox; physisches Modell wie ein DC-Motor (ca. 50 €) für Echtzeit-Tests. Kosten: 100 €.

#### 8. Roboter: Sensorik
**Laborablauf**:
1. Sensor-Integration: Kalibrieren von Sensoren (z.B. Ultraschall, IR) in MATLAB.
2. Datenakquise: Messen von Umgebungsdaten (z.B. Abstand, Licht) in Echtzeit.
3. Verarbeitung: Filtern und Fusionieren von Sensordaten.
4. Analyse: Bewerten von Sensor-Genauigkeit und Rausch.
Dauer: 3 Stunden. Fokus: Multisensorik für Robotik.

**Prototyp des Versuchsstands**: Arduino-basiertes Roboter-Chassis (z.B. mit HC-SR04 Ultraschall, 20 €) und MATLAB-Support. Kosten: 80 €.

#### 9. Roboter: Aktorik und Bahnplanung
**Laborablauf**:
1. Aktor-Steuerung: Programmieren von Motoren und Servos in Simulink.
2. Bahnplanung: Implementieren eines Pfadfinders (z.B. A*-Algorithmus) in MATLAB.
3. Integration: Kombinieren mit Sensorik für geschlossenen Regelkreis (z.B. Hindernisvermeidung).
4. Test: Ausführen und Optimieren der Bahn; Diskussion von Energieeffizienz.
Dauer: 4 Stunden. Abschluss: Demo eines autonomen Roboters.

**Prototyp des Versuchsstands**: Erweiterung des Sensorik-Stands mit DC-Motoren und Rädern (z.B. LEGO Mindstorms EV3, 200 €). Simulink für Echtzeit-Steuerung. Kosten: 250 €.

#### Übersichtstabelle der Experimente
| Experiment | Dauer (Stunden) | Schlüsselkomponenten | Fokus | Erwartete Lernziele |
|------------|-----------------|----------------------|-------|---------------------|
| 1. Digitaltechnik | 3 | Arduino, MATLAB | Sampling & Quantisierung | Grundlagen digitaler Signale verstehen |
| 2. Speicheroszilloskop & Spektrum-Analysator | 4 | PicoScope, Simulink | Frequenzanalyse | Signale in Zeit- und Frequenzdomäne messen |
| 3. Ultraschall-CT | 4 | Transducer-Ring, MATLAB | Tomographie-Rekonstruktion | Medizinische Bildgebung simulieren |
| 4. Beleuchtung & Bildgewinnung | 3 | USB-Kamera, LED | Akquise-Optimierung | Bildqualität beeinflussen |
| 5. Digitale Bildverarbeitung | 4 | MATLAB Toolbox | Filter & Transformationen | Bilder verbessern |
| 6. Bildauswertung | 3 | MATLAB Skripte | Segmentierung | Objekte erkennen |
| 7. Reglersynthese & Simulation | 4 | Simulink, DC-Motor | PID-Tuning | Regelkreise entwerfen |
| 8. Roboter: Sensorik | 3 | Arduino-Sensoren | Datenfusion | Umwelt wahrnehmen |
| 9. Roboter: Aktorik & Bahnplanung | 4 | Mindstorms, Simulink | Pfadsteuerung | Autonome Navigation |

#### Erweiterte Überlegungen und Best Practices
Basierend auf etablierten Programmen sollte das Praktikum flexibel sein: Optionale Module für tiefergehende Themen, z.B. KI in Bildauswertung. Kostenoptimierung durch Shared Hardware (z.B. ein zentrales Oszilloskop). Sicherheitsaspekte: Risikoanalysen für Robotik (z.B. Kollisionsschutz). Evaluation: Pre-Post-Tests und Feedback-Runden. Für kontroverse Themen wie Datenschutz in Bildverarbeitung: Diskutiere ausgewogen, z.B. Vorteile für Industrie vs. Privatsphäre-Risiken. Insgesamt fördert dies einen Wandel in der Messtechnik, wie in der Einleitung beschrieben, durch Integration von DSP, Bildverarbeitung und Regelung.

**Key Citations:**
-  Lab "Computer-Aided Methods in Measurement and Control Engineering" - https://www.mrt.kit.edu/english/lehre_WS_rvmrt.php
-  Computer-Aided Methods in Measurement and Control Engineering Internship Announcement - https://www.mrt.kit.edu/download/RVMRT-Praktikumsankuendigung.pdf
-  Sensors and actuators lab experiments - https://www.tek.com/en/courseware/sensors-and-actuators-lab-experiments
-  Sensors and Actuators Laboratory - https://robotics.umd.edu/facilities/sensors-and-actuators-laboratory
-  Ultrasound Computed Tomography (USCT) - https://anastasio.bioengineering.illinois.edu/research/ultrasound-computed-tomography-usct/
-  3D ultrasound computer tomography: Hardware setup, reconstruction methods and first clinical results - https://www.researchgate.net/publication/318738167_3D_ultrasound_computer_tomography_Hardware_setup_reconstruction_methods_and_first_clinical_results
-  Control Systems - MATLAB & Simulink - https://www.mathworks.com/help/overview/control-systems.html
-  Control System Design with Simulink - https://www.mathworks.com/learn/training/control-system-design-with-simulink.html
-  Digital Image Processing Lab Manual - https://bmsce.ac.in/Content/ML/DIP_Manual.pdf
-  15EI403J- IMAGE PROCESSING LAB MANUAL - https://webstor.srmist.edu.in/web_assets/srm_mainsite/files/2018/15EI403J-image-processing%20lab-manual.pdf
