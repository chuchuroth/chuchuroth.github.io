---
layout: post
title:  "Regelungstechnik1&2_Prüfungsaufgaben"
date:   2025-08-27
categories: jekyll update
---



---
Die Modellbildung in folgenden Schritten:
1. Beschreibung des Modellierungsziels
2. Auswahl der Modellannahmen.
3. Beschreibung der Regelstrecke.
4. Aufstellung des Blockschaltbildes.
5. Aufstellung der Modellgleichungen.
6. Modellvalidierung.

---
Aufstellung einer Differentialgleichung:
1. Zerlegen das System in Komponenten.
2. Schreiben die physikalischen Gesetze auf, die das Verhalten der Komponenten beschreiben.
3. Schreiben die Beziehungen auf, die zwischen den Komponenten bestehen
4. Fassen die Gleichungen zu einer Differentialgleichung zusammen.

---
Aufstellung eines Zustandsraummodells：
1 Systemzerlegung: Zerlegen das System in Komponenten.
2 Komponentenmodelle: Schreiben die physikalischen Gesetze auf, die das Verhalten der Komponenten beschreiben.
3 Kopplungsbeziehungen: Schreiben die Beziehungen auf, die zwischen den Komponenten bestehen.
4 Modellumformung: Fassen die Gleichungen zu einem Zustandsraummodell zusammen.



---
Das wissenschaftliche Fundament der klassischen und modernen Regelungstheorie besteht darin, durch geeignete Rückkopplungsstrategien Systeme stabil und leistungsfähig zu machen. Die klassische Regelungstheorie basiert auf Übertragungsfunktionen und analysiert überwiegend Ein-zu-Ein-Ausgangssysteme (SISO) im Zeit- und Frequenzbereich. Ihre zentralen Werkzeuge sind Bode-Diagramme, Nyquist-Kurven und Wurzelortskurven, mit denen Stabilität und Dynamik auf anschauliche Weise untersucht werden können. Sie repräsentiert damit einen frequenzbasierten, input-output-orientierten Ansatz.

Die moderne Regelungstheorie hingegen verwendet die Zustandsraumdarstellung, um Mehrgrößensysteme (MIMO) auf einer höheren Abstraktionsebene zu modellieren. Sie legt den Schwerpunkt auf Konzepte wie Steuerbarkeit und Beobachtbarkeit und nutzt fortgeschrittene Methoden wie Optimale und Robuste Regelung, um komplexen Leistungsanforderungen gerecht zu werden.

Zusammenfassend lässt sich sagen: Während die klassische Regelungstheorie eher eine präzise Feinabstimmung einzelner Systeme erlaubt, zielt die moderne Regelung auf eine umfassende, systemübergreifende und modellbasierte Steuerung komplexer dynamischer Prozesse.

---


Diese drei Darstellungsformen sind wichtige grafische Werkzeuge der klassischen Regelungstheorie zur Analyse und zum Entwurf von Regelsystemen. Sie gehören alle in den Bereich der Frequenzganganalyse. Sie werden benutzt um das Verhalten eines Systems bei unterschiedlichen Eingangssignalen anschaulich zu verstehen und seine Stabilität zu beurteilen.

Bode-Diagramm (Bode Plot)
Ein Bode-Diagramm besteht aus zwei Teilgrafiken: dem Betragsdiagramm und dem Phasendiagramm.
Betragsdiagramm (Magnitude Plot): Zeigt die Verstärkung des Systems bei sinusförmigen Eingangssignalen verschiedener Frequenzen (also das Verhältnis von Ausgangs- zu Eingangsamplitude). Die Ordinate wird üblicherweise in Dezibel (dB) angegeben, die Abszisse ist die logarithmische Frequenzachse.
Phasendiagramm (Phase Plot): Zeigt die Phasenverzögerung oder Phasenverschiebung des Ausgangssignals in Abhängigkeit von der Eingangsfrequenz.
Funktion: Das Bode-Diagramm ermöglicht eine schnelle Beurteilung von Stabilität und Dynamik. Anhand von Betrag- und Phasenkurve lassen sich Amplituden- und Phasenreserve bestimmen. Sind beide Reserven positiv, gilt das System als stabil.

Nyquist-Diagramm (Nyquist Plot)
Das Nyquist-Diagramm stellt den Frequenzgang eines Systems (Betrag und Phase) in der komplexen Ebene dar.
Jeder Punkt der Kurve entspricht der Frequenzantwort bei einer bestimmten Frequenz:
Der Abstand des Punktes vom Ursprung stellt den Betrag dar,
Der Winkel zur positiven reellen Achse entspricht der Phase.
Variiert die Frequenz von null bis unendlich, so ergibt sich eine geschlossene Kurve.
Funktion: Das Nyquist-Diagramm dient in erster Linie zur Stabilitätsanalyse. Grundlage ist das Nyquist-Stabilitätskriterium, bei dem untersucht wird, ob und wie die Kurve den Punkt (-1, 0) in der komplexen Ebene umschließt. Dieses Verfahren ist besonders hilfreich für Systeme mit Verzögerungszeiten oder komplexeren Eigenschaften.

Wurzelortskurve (Root Locus)
Die Wurzelortskurve unterscheidet sich von den beiden vorherigen Darstellungen, da sie im s- oder Laplace-Ebene (komplexen Ebene) erzeugt wird.
In diesem s-Plane werden die Eigenwerte (Pole) des Systems dargestellt. Die Stabilität eines Systems hängt allein von der Lage dieser Pole ab: Nur wenn alle Pole in der linken Halbebene liegen, ist das System stabil.
Die Wurzelortskurve zeigt die Bewegung der geschlossenen Pole, wenn ein Systemparameter (meist der offene Verstärkungsfaktor K) von 0 bis ∞ variiert.
Funktion:
Stabilitätsanalyse: Lässt sich erkennen, ob Pole in die rechte s-Halbebene wandern.
Optimierung: Durch die Wahl eines geeigneten Verstärkungsfaktors K können die geschlossenen Pole gezielt positioniert werden, um gewünschte Dämpfung und Dynamik des Systems einzustellen.

---

Ordnen Sie folgende Begriffe den Modellierungs-, Analyse- und Entwurfsverfahren der Regelungstechnik zu und erläutern Sie ihre Bedeutung:
Anstiegszeit, Bandbreite, Eigenvorgang, Empfindlichkeitsfunktion, Folgeregelung,
Gleichgewichtszustand, kanonische Zustandsvariablen, Knickpunktabstand, Kreisverstärkung, Linearität, Nulldynamik, Resonanzfrequenz, statisches Verhalten,
stationäres Verhalten, Stabilitätsgrenze, Übergangsmatrix.

---
hier sind die Begriffe den jeweiligen Phasen der Regelungstechnik zugeordnet und ihre Bedeutung erläutert.

### 1. Modellierungsverfahren

Diese Phase befasst sich mit der mathematischen Beschreibung eines Systems.

* **Linearität:** Ein System ist linear, wenn das Superpositionsprinzip gilt. Das bedeutet, dass die Summe der Reaktionen auf einzelne Eingaben der Reaktion auf die Summe der Eingaben entspricht. Lineare Modelle sind für die Analyse und den Entwurf wesentlich einfacher.
* **Gleichgewichtszustand:** Ein Zustand, in dem ein System ohne äußere Einflüsse verharrt. In der Regelungstechnik sind Gleichgewichtszustände oft die gewünschten Sollwerte.
* **kanonische Zustandsvariablen:** Eine spezielle Wahl von Zustandsvariablen, die die Systembeschreibung in der **Zustandsraumdarstellung** vereinfacht. Sie dienen dazu, die Steuerbarkeit und Beobachtbarkeit eines Systems zu analysieren.
* **Übergangsmatrix:** Eine Matrix, die die zeitliche Entwicklung des Zustands eines linearen Systems beschreibt. Sie verknüpft den Zustand zu einem Zeitpunkt t_0 mit dem Zustand zu einem späteren Zeitpunkt t.

***

### 2. Analyseverfahren

In dieser Phase werden die Eigenschaften eines bereits modellierten Systems untersucht.

* **Eigenvorgang:** Die natürliche, freie Bewegung eines Systems, wenn keine äußere Anregung vorliegt. Er wird durch die Eigenwerte der Systemmatrix bestimmt und beeinflusst die Stabilität und das Einschwingverhalten des Systems.
* **statisches Verhalten:** Beschreibt das Systemverhalten im **stationären Zustand**, wenn alle dynamischen Ausgleichsvorgänge abgeklungen sind. Wichtige Kenngröße ist der Verstärkungsfaktor im eingeschwungenen Zustand.
* **stationäres Verhalten:** Der Zustand eines Systems nach dem Abklingen des **Einschwingvorgangs**. Ein stabiles System erreicht typischerweise einen neuen stationären Zustand nach einer Eingangsänderung.
* **Resonanzfrequenz:** Die Frequenz, bei der die Amplitude der Systemantwort ihr Maximum erreicht. Bei dieser Frequenz kann es zu unerwünscht hohen Schwingungen kommen.
* **Nulldynamik:** Das Verhalten eines nichtlinearen Systems, wenn der Ausgang auf null gezwungen wird. Sie ist wichtig für die Stabilitätseigenschaften in der nichtlinearen Regelung.
* **Stabilitätsgrenze:** Die Grenze, bei der ein System von einem stabilen in einen instabilen Zustand übergeht. Im Frequenzbereich wird diese oft durch die **Knickpunkte** im Bode-Diagramm oder den Schnittpunkt mit dem Einheitskreis im Nyquist-Diagramm bestimmt.

***

### 3. Entwurfsverfahren

Diese Phase befasst sich mit der Entwicklung von Regelstrategien und der Auslegung von Reglern.

* **Folgeregelung:** Eine Regelungsart, bei der der Regler so ausgelegt wird, dass der Systemausgang einem sich ändernden Sollwert folgt. Dies ist die häufigste Form der Regelungstechnik (z.B. in Servomotoren).
* **Anstiegszeit:** Ein Maß für die Geschwindigkeit des Einschwingvorgangs. Sie gibt die Zeit an, die der Systemausgang benötigt, um von 10% auf 90% seines Endwerts zu steigen. Eine kurze Anstiegszeit bedeutet eine schnelle Reaktion.
* **Bandbreite:** Die Frequenz, bis zu der ein System auf Eingangssignale ohne wesentliche Dämpfung reagieren kann. Eine größere Bandbreite bedeutet, dass das System auf schnellere Änderungen reagieren kann.
* **Empfindlichkeitsfunktion:** Eine mathematische Funktion, die beschreibt, wie empfindlich die Regelgröße auf Störungen und Parameteränderungen im System reagiert. Ziel des Regelkreisentwurfs ist oft, diese Funktion zu minimieren.
* **Kreisverstärkung:** Das Produkt aus den Verstärkungen der einzelnen Komponenten im offenen Regelkreis. Sie ist entscheidend für die **Stabilität** des geschlossenen Regelkreises und wird oft im Bode-Diagramm oder Nyquist-Diagramm analysiert.
* **Knickpunktabstand:** Im Bode-Diagramm sind dies die Frequenzen, an denen sich die Steigung der asymptotischen Approximationen ändert. Sie sind direkt mit den Pol- und Nullstellen des Systems verknüpft und wichtig für die grafische Analyse.

---

Welche Bedeutung haben Nullstellen, Pole, Eigenwerte, relativer Grad, Zeitkonstanten
und Grenzfrequenz für das Systemverhalten? Wie berechnet man diese Größen aus den
Zeitbereichs- und Frequenzbereichsmodellen linearer Systeme? Ordnen Sie diese Eigenschaften dem E/A-Verhalten bzw. der Eigenbewegung des Systems zu. Wie beeinflussen
diese Eigenschaften das Übergangsverhalten bzw. das stationäre Verhalten?

---

Für das Systemverhalten linearer Systeme spielen verschiedene mathematische Größen eine entscheidende Rolle. Im Folgenden werden ihre Bedeutung, Berechnung und ihr Einfluss auf das Systemverhalten erläutert und den Systemkategorien zugeordnet.

***

### 1. Bedeutung und Berechnung

<img width="567" height="612" alt="image" src="https://github.com/user-attachments/assets/f5ddb5cc-bccb-4650-8412-2a1af2d82557" />


***

### 2. Zuordnung zu E/A-Verhalten und Eigenbewegung

* **E/A-Verhalten (Eingabe-Ausgabe-Verhalten)**:
    * **Nullstellen**
    * **relativer Grad**
    * **Grenzfrequenz**
* **Eigenbewegung (Freie Bewegung)**:
    * **Pole** (entsprechen den Eigenwerten)
    * **Eigenwerte**
    * **Zeitkonstanten**

***

### 3. Einfluss auf das Übergangs- und stationäre Verhalten

* **Übergangsverhalten (Einschwingvorgang)**:
    * **Pole** und **Eigenwerte** bestimmen die Dynamik und die Stabilität des Übergangsverhaltens. Ein Pol im linken Halbebene führt zu einem stabilen, abklingenden Verhalten. Ein Pol im rechten Halbebene führt zu einem instabilen, aufschwingenden Verhalten. Pole nahe der imaginären Achse führen zu langsamen Einschwingvorgängen. Konjugiert komplexe Pole erzeugen gedämpfte Schwingungen. 
    * **Nullstellen** beeinflussen die Form der Übergangsfunktion, können Überschwingen oder Unterschwingen verursachen und das Systemverhalten je nach ihrer Lage im s-Ebene verändern.
    * **Zeitkonstanten** beeinflussen die Geschwindigkeit des Übergangsvorgangs. Eine kleinere Zeitkonstante führt zu einem schnelleren Einschwingen.

* **Stationäres Verhalten (eingeschwungener Zustand)**:
    * Das stationäre Verhalten wird primär durch die Anzahl der Pole im Ursprung (<img width="39" height="18" alt="image" src="https://github.com/user-attachments/assets/5460cea5-b334-4aa6-acb5-615060aaea57" />
) der Übertragungsfunktion bestimmt. Ein Pol bei <img width="39" height="18" alt="image" src="https://github.com/user-attachments/assets/33dd8c5a-239b-462b-99d8-d0475e1b4aae" />
 bedeutet einen Systemtyp 1, der einen stationären Fehler bei einer Rampenfunktion korrigieren kann. Pole bei <img width="39" height="18" alt="image" src="https://github.com/user-attachments/assets/d4fc8602-344a-4767-b923-8bafdbd70256" />
 beeinflussen die Art des stationären Fehlers.
    * **Grenzfrequenz** ist ein Maß für die Frequenzbereichsleistung. Eine höhere Grenzfrequenz bedeutet, dass das System auf schnellere Eingangssignale reagieren kann, was sich auch auf das stationäre Verhalten bei periodischen Signalen auswirkt.
 

---

In der Regelungstechnik werden sowohl Modelle für das Zeitverhalten dynamischer Systeme als auch Frequenzbereichsbeschreibungen eingesetzt. Einige von ihnen erfassen nur das E/A-Verhalten.
1. Stellen Sie diese Modelle einschließlich der Voraussetzungen zusammen, unter denen diese Modelle verwendet werden können.
2. Kennzeichnen Sie, durch welche Transformationen bzw. unter welchen zusätzlichen Annahmen Sie von einer Modellform zu einer anderen kommen können.

---


### 1. Modelle für das Zeitverhalten und den Frequenzbereich

In der Regelungstechnik werden dynamische Systeme hauptsächlich durch zwei Arten von Modellen beschrieben: Zeitbereichsmodelle und Frequenzbereichsmodelle.

#### Zeitbereichsmodelle
Diese Modelle beschreiben das Systemverhalten in Abhängigkeit von der Zeit (t). Sie sind besonders nützlich, um die **interne Dynamik** und den **Zustand** des Systems zu analysieren.

* **Zustandsraumdarstellung:**
    * **Beschreibung:** Ein System wird durch einen Satz von Differentialgleichungen erster Ordnung beschrieben. Diese Gleichungen beziehen den **Zustandsvektor** (x) auf die Eingangsgröße (u) und beschreiben, wie sich der Zustand des Systems über die Zeit ändert. Die Ausgabe (y) ist eine Funktion des Zustandsvektors und der Eingangsgröße. Die allgemeine Form ist <img width="418" height="32" alt="image" src="https://github.com/user-attachments/assets/c15c0327-f1f4-4066-afd5-e0300aa20390" />
.
    * **Voraussetzungen:** Anwendbar auf **lineare, zeitinvariante (LTI)** und **nichtlineare** Systeme, sowie **Mehrgrößensysteme (MIMO)**. Es ist ein internes Modell, das die gesamte Systemdynamik erfasst, nicht nur das E/A-Verhalten.

* **Differentialgleichungen:**
    * **Beschreibung:** Eine einzelne Differentialgleichung (oder ein System von Differentialgleichungen) beschreibt die Beziehung zwischen der Eingangsgröße und der Ausgangsgröße. Diese Form ist typischerweise für **Eingrößensysteme (SISO)** geeignet.
    * **Voraussetzungen:** Das System muss **linear** und **zeittinvariant** sein.

#### Frequenzbereichsmodelle
Diese Modelle beschreiben das Systemverhalten in Abhängigkeit von der Frequenz (<img width="27" height="24" alt="image" src="https://github.com/user-attachments/assets/9f3a1d3c-1fa4-4e14-b849-0afe88535d48" />
oder der komplexen Frequenz s). Sie erfassen ausschließlich das **Eingabe-Ausgabe-Verhalten** des Systems.

* **Übertragungsfunktion:**
    * **Beschreibung:** Das Verhältnis der Laplace-Transformierten der Ausgangsgröße Y(s) zur Laplace-Transformierten der Eingangsgröße U(s) bei null Anfangsbedingungen, <img width="104" height="40" alt="image" src="https://github.com/user-attachments/assets/f4f26b3a-fee4-4993-9e18-3e4539ce5f9e" />
 Die Übertragungsfunktion ist ein rationaler Bruch von Polynomen in s.
    * **Voraussetzungen:** Das System muss **linear** und **zeittinvariant (LTI)** sein. Dieses Modell erfasst nur das äußere E/A-Verhalten und ignoriert die interne Dynamik, die nicht steuerbar oder nicht beobachtbar ist.

* **Frequenzgang:**
    * **Beschreibung:** Der Frequenzgang ist die Übertragungsfunktion mit s = <img width="27" height="24" alt="image" src="https://github.com/user-attachments/assets/2b3c2332-8530-41fb-8359-f987cf7e0055" />
, also <img width="132" height="37" alt="image" src="https://github.com/user-attachments/assets/07cfb656-ec37-4441-a598-b3eee76fb4be" />
. Er beschreibt, wie das System auf sinusförmige Eingangssignale reagiert, und gibt die Verstärkung und Phasenverschiebung in Abhängigkeit von der Frequenz an. Er kann grafisch durch **Bode-Diagramme** oder **Nyquist-Diagramme** dargestellt werden.
    * **Voraussetzungen:** Das System muss **linear** und **zeittinvariant (LTI)** sein. Es wird angenommen, dass der stationäre Zustand erreicht ist.

***

### 2. Transformationen und Annahmen

Der Wechsel zwischen den Modellformen ist durch verschiedene Transformationen möglich.

#### Von Zeitbereich zu Frequenzbereich

* **Laplace-Transformation:** Dies ist die wichtigste Transformation, um von einer linearen Differentialgleichung im Zeitbereich zu einer algebraischen Gleichung im Frequenzbereich (der Übertragungsfunktion) zu gelangen.
    * **Annahme:** Die Laplace-Transformation erfordert, dass alle **Anfangsbedingungen null** sind. 

* **Laplace-Transformation der Zustandsraumdarstellung:**
    * **Voraussetzung:** Die Zustandsraumdarstellung gilt nur für LTI-Systeme.
    * **Transformation:** Die Gleichungen <img width="344" height="26" alt="image" src="https://github.com/user-attachments/assets/92734da6-ba99-4dbb-afbc-5cd4cd572027" /> <img width="55" height="24" alt="image" src="https://github.com/user-attachments/assets/95896e0a-843e-46f9-8ec2-7db0bff10a2f" />
 werden laplace-transformiert. Mit null Anfangsbedingungen ergibt sich <img width="462" height="29" alt="image" src="https://github.com/user-attachments/assets/98a096bf-84d2-4353-85e7-0ee7e56e910f" />
. Durch algebraische Umformung erhält man die Übertragungsfunktion <img width="255" height="27" alt="image" src="https://github.com/user-attachments/assets/f75bec30-d70c-4be4-a2da-a9696d9bf252" />

    * **Zusätzliche Annahme:** Diese Transformation erfasst nur das **E/A-Verhalten** des Systems. Jede intern nicht steuerbare oder nicht beobachtbare Dynamik wird in der Übertragungsfunktion nicht sichtbar sein.

#### Von Frequenzbereich zu Zeitbereich

* **Inverse Laplace-Transformation:** Um von einer Übertragungsfunktion zu einer Differentialgleichung zurückzukehren, verwendet man die inverse Laplace-Transformation. Dies ist die mathematisch exakte Methode.

* **Realisiereung der Zustandsraumdarstellung:** Aus einer gegebenen Übertragungsfunktion kann eine äquivalente Zustandsraumdarstellung erstellt werden.
    * **Annahme:** Es gibt **unendlich viele** Zustandsraumdarstellungen für eine gegebene Übertragungsfunktion. Daher muss man sich für eine "kanonische" Form entscheiden (z.B. Steuerbarkeits- oder Beobachtbarkeits-Normalform).

#### Zusätzliche Annahmen und Vereinfachungen

* **Lineare und zeitinvariante (LTI) Annahme:** Fast alle Frequenzbereichsmodelle (Übertragungsfunktion, Frequenzgang) sind auf LTI-Systeme beschränkt. Nichtlineare und zeitinvariante Systeme können oft lokal um einen Arbeitspunkt linearisiert werden, um diese Methoden anwenden zu können.
* **Stationäre Annahme:** Der Frequenzgang G(<img width="27" height="24" alt="image" src="https://github.com/user-attachments/assets/fa057dfa-abc5-4a38-bb65-dcef5247233a" />
) beschreibt das Verhalten des Systems im stationären Zustand, nachdem alle transienten Effekte abgeklungen sind.

---

1. Wie können Übertragungsglieder klassifiziert werden? Geben Sie für alle Klassen technische Beispiele an.
2. Wie lauten Zustandsraummodell und Übertragungsfunktion dieser Übertragungsglieder in ihrer einfachsten Form?
3. Welche Eigenschaften besitzen diese Übertragungsglieder? Zeichnen Sie qualitativ die Übergangsfunktion, die Gewichtsfunktion, das PN-Bild, die Ortskurve und das Bodediagramm der wichtigsten Übertragungsglieder auf.
4. Kennzeichnen Sie in den Diagrammen, wo Sie wichtige Kenngrößen wie statische Verstärkung, Summenzeitkonstante, Dämpfung usw. ablesen können bzw. wie Sie Aussagen über die Sprungfähigkeit, Minimalphasigkeit und Stabilität erhalten.
5. Welches Übergangsverhalten und welches stationäre Verhalten haben diese Übertragungsglieder?

---

### 1. Klassifizierung von Übertragungsgliedern

Übertragungsglieder können nach ihrem dynamischen Verhalten in verschiedene Klassen eingeteilt werden. Die wichtigsten sind:
* **P-Glied (Proportionalglied):** Die Ausgangsgröße ist proportional zur Eingangsgröße. Es gibt keine Dynamik. Beispiele: Potentiometer, Verstärker ohne Filter.
* **I-Glied (Integrationsglied):** Die Ausgangsgröße ist das Integral der Eingangsgröße. Die Ausgangsgröße steigt oder fällt konstant, solange die Eingangsgröße konstant ungleich Null ist. Beispiele: Motor ohne Last, Füllstand eines Tanks bei konstantem Zufluss.
* **D-Glied (Differenzialglied):** Die Ausgangsgröße ist proportional zur Änderungsrate der Eingangsgröße. Es reagiert auf Änderungen, nicht auf konstante Werte. Beispiele: Tachogenerator, induktive Sensoren.
* **PT1-Glied (Proportional-Verzögerungsglied 1. Ordnung):** Die Ausgangsgröße verzögert sich proportional zur Eingangsgröße mit einer Zeitkonstante. Beispiele: Thermometer, RC-Glied, die meisten physikalischen Prozesse.
* **PT2-Glied (Proportional-Verzögerungsglied 2. Ordnung):** Das System weist ein verzögertes und oft schwingendes Verhalten auf. Beispiele: Feder-Masse-Dämpfer-System, LCR-Schwingkreis.
* **PD-Glied (Proportional-Differenzialglied):** Eine Kombination aus proportionalem und differenzierendem Verhalten. Es reagiert schnell auf Änderungen und behält das proportionale Signal bei.
* **T-Glied (Totzeitglied):** Die Ausgangsgröße ist eine verzögerte Kopie der Eingangsgröße. Die Verzögerung ist konstant. Beispiele: Transportband, chemische Reaktionen mit Transportzeit.

***

### 2. Zustandsraummodell und Übertragungsfunktion

<img width="700" height="352" alt="image" src="https://github.com/user-attachments/assets/893f3e85-6c34-4fcc-a21d-f7350c8f7ce9" />

***

### 3. Eigenschaften und qualitative Diagramme

<img width="684" height="289" alt="image" src="https://github.com/user-attachments/assets/1bc00fd3-b028-44cc-ae08-0fbf95699419" />

<img width="666" height="314" alt="image" src="https://github.com/user-attachments/assets/b873ab7e-d999-414c-857b-8083ffd37da1" />

<img width="708" height="312" alt="image" src="https://github.com/user-attachments/assets/0c1a0358-7d59-4ed7-bb7a-ee0561ddc75f" />

<img width="709" height="284" alt="image" src="https://github.com/user-attachments/assets/fcae7f6d-2d0a-4e6a-b631-ebb9a8bb6b36" />

<img width="681" height="255" alt="image" src="https://github.com/user-attachments/assets/622090ef-1aca-4955-be50-b21d72d80b6d" />


***

### 4. Kennzeichnung wichtiger Kenngrößen in den Diagrammen

* **Statische Verstärkung (K):** Kann aus der **Übergangsfunktion** als Endwert abgelesen werden. Im **Bodediagramm** der Amplitudengang bei <img width="61" height="22" alt="image" src="https://github.com/user-attachments/assets/6c50caab-b6c1-43d7-8302-203b14ac9c20" />
. In der **Ortskurve** ist es der Anfangspunkt der Kurve auf der reellen Achse.
* **Summenzeitkonstante (T):** Bei PT1-Gliedern die Zeit, die der Ausgang benötigt, um 63.2% des Endwerts zu erreichen. Im **Bodediagramm** ist 1/T die Frequenz des Knickpunktes.
* <img width="122" height="33" alt="image" src="https://github.com/user-attachments/assets/f9cd515e-f82f-4fe9-b16a-c5c94a8ba794" />
 Bei PT2-Gliedern kann die Dämpfung aus dem Überschwingen der **Übergangsfunktion** abgeleitet werden. In der **Ortskurve** und im **Bodediagramm** manifestiert sich eine geringe Dämpfung als eine Resonanzüberhöhung.
* **Sprungfähigkeit:** Eine endliche Sprungantwort impliziert eine **Übertragungsfunktion** ohne Nullstellen bei <img width="64" height="22" alt="image" src="https://github.com/user-attachments/assets/3627bedf-5e44-4a8f-a522-8b1a0953582c" />
(d.h. der Zählergrad ist kleiner oder gleich dem Nennergrad).
* **Minimalphasigkeit:** Ein System ist **minimalphasig**, wenn alle Pole und Nullstellen in der linken Halbebene liegen. Dies kann direkt aus dem **PN-Bild** oder dem **Phasengang** des Bodediagramms abgelesen werden. Bei minimalphasigen Systemen ist die Phase bei hohen Frequenzen negativ.
* **Stabilität:** Ein System ist stabil, wenn alle Pole einen negativen Realteil haben. Dies kann im **PN-Bild** direkt abgelesen werden (alle Pole in der linken Halbebene).

***

### 5. Übergangsverhalten und stationäres Verhalten

* **P-Glied:** Sofortiges Übergangsverhalten (keine Dynamik). Das stationäre Verhalten ist die Multiplikation des Eingangssignals mit dem Proportionalitätsfaktor K_p.
* **I-Glied:** Unendliches Übergangsverhalten. Die Ausgangsgröße steigt oder fällt konstant, bis das stationäre Gleichgewicht erreicht ist. Das stationäre Verhalten ist die Integration des Eingangssignals.
* **PT1-Glied:** exponentielles Übergangsverhalten. Das stationäre Verhalten ist der Endwert des Ausgangssignals nach einer exponentiellen Annäherung.
* **PT2-Glied:** kann schwingendes oder aperiodisches Übergangsverhalten aufweisen, abhängig von der Dämpfung. Das stationäre Verhalten ist der Endwert des Ausgangssignals nach einem schwingenden oder aperiodischen Einschwingvorgang.
* **T-Glied:** Keine Dynamik im eigentlichen Sinne, das Übergangsverhalten ist eine reine Zeitverschiebung. Das stationäre Verhalten ist identisch mit dem Eingangssignal, nur zeitlich verzögert.

---

1. Welche Stabilitätsdefinitionen kennen Sie? Welcher Zusammenhang besteht zwischen diesen Eigenschaften?
2. Mit welchen Modellen können Sie diese Eigenschaften untersuchen?
3. Mit welchen Kriterien können Sie diese Stabilitätseigenschaften für die Regelstrecke bzw. für den Regelkreis überprüfen?

---

### 1. Stabilitätsdefinitionen und ihr Zusammenhang

In der Regelungstechnik gibt es verschiedene Stabilitätsdefinitionen, die das Verhalten eines Systems nach einer Störung beschreiben. Die wichtigsten sind:

* **Asymptotische Stabilität:** Ein System ist asymptotisch stabil, wenn es nach einer anfänglichen Störung nicht nur in seinen Ausgangszustand zurückkehrt, sondern sich auch auf diesen zubewegt und sich schließlich **im stationären Zustand** befindet.
* **Stabilität nach Ljapunow (interne Stabilität):** Ein System ist stabil nach Ljapunow, wenn für jede anfängliche Störung die Reaktion des Systems beschränkt bleibt. Es wird dabei nicht gefordert, dass das System in den Ausgangszustand zurückkehrt. Es bleibt lediglich in einer begrenzten Region um diesen herum. Die Ljapunow-Stabilität wird oft als **BIBO-Stabilität (Bounded-Input Bounded-Output)** bezeichnet.

Der Zusammenhang zwischen diesen Definitionen ist hierarchisch: **Asymptotische Stabilität impliziert Stabilität nach Ljapunow.** Das heißt, ein System, das sich auf seinen Gleichgewichtszustand zubewegt, bleibt automatisch in einer begrenzten Region. Die Umkehrung gilt jedoch nicht: Ein System kann stabil nach Ljapunow sein, ohne asymptotisch stabil zu sein (z.B. ein System mit Polen auf der imaginären Achse).

---

### 2. Untersuchung von Stabilitätseigenschaften mit Modellen

Die Stabilität eines Systems kann mit verschiedenen Modellen untersucht werden.

* **Zustandsraumdarstellung:** Mit diesem Modell können Sie die **interne Stabilität** (nach Ljapunow) eines Systems überprüfen. Ein lineares, zeitinvariantes (LTI) System in Zustandsraumdarstellung ist stabil, wenn die Eigenwerte der Systemmatrix (A) einen **negativen Realteil** haben. Liegen alle Eigenwerte auf der imaginären Achse, ist das System nur stabil nach Ljapunow (d.h. begrenzt).

* **Übertragungsfunktion:** Dieses Modell dient der Untersuchung der **BIBO-Stabilität**. Ein System ist BIBO-stabil, wenn alle **Pole** der Übertragungsfunktion einen **negativen Realteil** haben. Diese Pole sind identisch mit den Eigenwerten der Systemmatrix in der Zustandsraumdarstellung. Daher ist die Pole-Nullstellen-Analyse eine direkte Methode zur Beurteilung der Stabilität.

---

### 3. Stabilitätskriterien für Regelstrecke und Regelkreis

Die Stabilität kann für die Regelstrecke (offener Kreis) und den Regelkreis (geschlossener Kreis) mit verschiedenen Kriterien untersucht werden.

* **Für die Regelstrecke (offener Kreis):**
    * **Eigenwert-Analyse:** Wie oben erwähnt, werden die Eigenwerte der Systemmatrix (A) berechnet. Wenn alle einen negativen Realteil haben, ist die Regelstrecke stabil.
    * **Pol-Analyse:** Wenn die Übertragungsfunktion der Regelstrecke gegeben ist, können Sie die Wurzeln des Nennerpolynoms (die Pole) bestimmen. Ein negativer Realteil aller Pole bedeutet Stabilität.

* **Für den Regelkreis (geschlossener Kreis):**
    * **Algebraische Kriterien:**
        * **Hurwitz-Kriterium:** Dieses Kriterium überprüft, ob alle Wurzeln des Nennerpolynoms der geschlossenen Schleife einen negativen Realteil haben. Die Berechnung basiert auf den Koeffizienten des charakteristischen Polynoms.
        * **Routh-Kriterium:** Ähnlich dem Hurwitz-Kriterium. Es stellt eine systematische Methode zur Überprüfung der Koeffizienten eines Polynoms dar. Durch die Erstellung eines Routh-Schemas können Sie die Anzahl der Wurzeln im rechten Halbebene bestimmen, ohne die Wurzeln explizit zu berechnen.

    * **Grafische Kriterien:**
        * **Wurzelortskurve (Root Locus):** Diese Methode zeigt, wie sich die geschlossenen Pole bewegen, wenn die Kreisverstärkung von null bis unendlich variiert wird. Das System ist stabil, solange die Wurzelortskurve nicht in die rechte Hälfte der s-Ebene eindringt. .
        * **Nyquist-Kriterium:** Dieses Kriterium überprüft die Stabilität anhand des Frequenzgangs des **offenen Regelkreises**. Das System ist stabil, wenn die Nyquist-Kurve den kritischen Punkt (-1, j0) nicht umschließt. Es ist eine sehr leistungsfähige Methode, da es auch Aussagen über die relative Stabilität (Phasen- und Amplitudenrand) ermöglicht.
        * **Bode-Kriterium:** Dieses Kriterium basiert auf dem **Bode-Diagramm** des offenen Regelkreises. Ein System ist stabil, wenn der Amplitudengang bei der Phasenverschiebung von -180° kleiner als 1 ist und die Phase bei dem Amplitudengang 1 über -180° liegt.
     
---

Das Verhalten vieler Regelstrecken lässt sich in guter Näherung durch PT2- bzw. PTtT1-Glieder beschreiben. Diese Näherungen haben nicht nur den Vorteil, dass die Modelle eine kleine dynamische Ordnung und wenige festzulegende Parameter besitzen. Die Stabilitätseigenschaften der mit diesen Regelstreckenmodellen entstehenden Regelkreise sind überschaubar.
1. Wird ein P-Regler verwendet, so ist der Regelkreis mit PT2-Strecke für beliebige (positive) Reglerverstärkungen stabil. Für die PTtT1-Strecke gibt es eine obere Schranke kkrit, so dass die Stabilität für k<kkrit gesichert ist. Wie können Sie diese Aussagen anhand des charakteristischen Polynoms des geschlossenen Kreises, anhand des Bodediagramms und der Ortskurve der offenen Kette bzw. mit Hilfe der Wurzelortskurve beweisen?
2. Die angegebenen Aussagen gelten nur, solange man die Regelstrecke tatsächlich als PT2- bzw. PTtT1-Glied auffassen kann. Zeigen Sie, dass die entstehenden Regelkreise robust gegenüber Approximationsfehlern sind, d. h., dass man trotz kleiner Approximationsfehler von der Stabilität des vereinfachten Modells des Regelkreises auf die Stabilität des realen Regelkreises schließen kann. Woran erkennen Sie Grenzen für die Robustheit? Begründen Sie, warum es eine obere Schranke k¯krit für die Reglerverstärkung gibt, so dass der reale Regelkreis für k > k¯krit instabil sein kann.
3. Wie verändern sich alle vorherigen Betrachtungen, wenn an Stelle eines P- ein I-Regler verwendet wird?

---
     
### 1. Nachweis der Stabilitätsaussagen

Hier wird die Stabilität von Regelkreisen mit PT2- bzw. PTtT1-Strecken unter Verwendung eines P-Reglers (Verstärkung K_p) nachgewiesen.

<img width="547" height="465" alt="image" src="https://github.com/user-attachments/assets/9145e419-4b17-4853-93cb-6918eef8f993" />


<img width="553" height="389" alt="image" src="https://github.com/user-attachments/assets/cc10bf7c-f4dc-4e54-a345-d2f6b098f0f7" />


---

### 2. Robustheit gegenüber Approximationsfehlern

Die Stabilität von Regelkreisen ist oft robust gegenüber kleinen Modellierungsfehlern, insbesondere bei PT2- und PTtT1-Approximationen.

* **Robustheitsprinzip:**
    Solange die **Pol- und Nullstellenverteilung** des realen Systems nahe der des vereinfachten Modells liegt, bleibt auch die Stabilität erhalten. Wenn die realen Pole und Nullstellen in der Nähe der Pole und Nullstellen der PT2- oder PTtT1-Modelle liegen, wird die Nyquist-Kurve des realen Systems nur minimal vom idealisierten Modell abweichen. Solange diese Abweichung nicht so groß ist, dass der kritische Punkt (-1, 0) umschlossen wird, bleibt das System stabil.

* **Grenzen der Robustheit:**
    Die Robustheit hat ihre Grenzen, wenn **ungefilterte hochfrequente Dynamik** im realen System existiert. Wenn das reale System zusätzliche Pole bei hohen Frequenzen besitzt, die im PT2- oder PTtT1-Modell nicht berücksichtigt wurden, können diese Pole das System instabil machen.

* **Erklärung für die obere Schranke K_{\text{krit}}:**
    Ein vereinfachtes PT2-Modell kann die hochfrequenten, unmodellierten Dynamiken (z.B. zusätzliche, sehr kleine Zeitkonstanten oder Totzeiten) **nicht erfassen**. Diese unmodellierten Dynamiken fügen zusätzliche Phasenverschiebung hinzu. Während der Phasenverlauf des PT2-Gliedes nie unter -180^\circ geht, kann die **zusätzliche Phasenverschiebung** der realen, unmodellierten Pole die Gesamtphase des Systems unter -180^\circ verschieben. Wenn dann der Betrag der Kreisverstärkung K_p K groß genug ist, kann der kritische Punkt (-1, 0) umschlossen werden, was zur Instabilität führt.
    Die obere Schranke K_{\text{krit}} existiert, weil bei zu hoher Verstärkung die Phasenverschiebung des realen Systems an der Frequenz, an der die Verstärkung 1 ist, die -180^\circ-Grenze überschreitet und damit die Stabilität verloren geht.

---

### 3. Verwendung eines I-Reglers

Die Verwendung eines I-Reglers (Übertragungsfunktion <img width="73" height="26" alt="image" src="https://github.com/user-attachments/assets/415a0e86-1cc9-4a7b-a9fc-b7129a263c4c" />
) verändert die Stabilitätsbetrachtungen grundlegend.

* **Zusätzlicher Pol im Ursprung:**
    Der I-Regler fügt einen **zusätzlichen Pol bei s=0** zur offenen Kette hinzu. Dies verändert die Eigenbewegung und das stationäre Verhalten des Regelkreises.

<img width="536" height="269" alt="image" src="https://github.com/user-attachments/assets/49270e71-0a7c-4362-8a81-d871a487ca5f" />

* **PTtT1-Strecke + I-Regler:**
    * Der I-Regler verschiebt den Phasengang erneut um -90^\circ. Da das PTtT1-Glied bereits eine Phasenverschiebung über -180^\circ aufweist, wird der gesamte Regelkreis mit einem I-Regler noch anfälliger für Instabilität. Eine obere Schranke für die Reglerverstärkung K_i existiert ebenfalls, die sogar noch kleiner ist als die für einen P-Regler, um Stabilität zu gewährleisten.

* **Stationäres Verhalten:**
    Ein entscheidender Vorteil des I-Reglers ist, dass er den **stationären Fehler eliminiert**. Der Regler integriert den Fehler über die Zeit, was dazu führt, dass der Ausgang dem Sollwert folgt, auch wenn eine konstante Störung vorliegt. Dies ist der Hauptgrund für die Verwendung eines I-Reglers in vielen Anwendungen. Im Gegensatz dazu hat ein P-Regler einen konstanten stationären Fehler bei einer sprungförmigen Eingabe.

---

1. Vergleichen Sie die Eigenschaften von Steuerungen in der offenen Wirkungskette und Steuerungen im geschlossenen Wirkungskreis. Wo werden diese Arten der Steuerung in technischen Anwendungen eingesetzt?
2. Wie entwirft man Vorsteuerungen?

---



### 1. Steuerungen: Offene Wirkungskette vs. Geschlossener Wirkungskreis

Steuerungen können grob in zwei Hauptkategorien eingeteilt werden: solche in einer **offenen Wirkungskette (Steuerung)** und solche in einem **geschlossenen Wirkungskreis (Regelung)**. Der entscheidende Unterschied liegt im Vorhandensein einer **Rückkopplung (Feedback)**.

#### Offene Wirkungskette (Steuerung)

* **Eigenschaften:**
    * **Kein Feedback:** Der Ausgang wird nicht gemessen und nicht mit dem Eingang verglichen.
    * **Keine Korrektur von Störungen:** Wenn eine externe Störung auftritt, wird diese vom System nicht erfasst und somit auch nicht korrigiert.
    * **Einfacher Aufbau:** Die Systemstruktur ist simpler und kostengünstiger, da keine Sensoren zur Messung des Ausgangs benötigt werden.
    * **Hohe Empfindlichkeit:** Die Genauigkeit hängt stark von der Präzision der Komponenten und der Kenntnis der Systemdynamik ab.
* **Technische Anwendungen:**
    * **Waschmaschine:** Ein einfaches, zeitgesteuertes Waschprogramm, bei dem die Schleuderdauer nicht von der tatsächlich erreichten Drehzahl abhängt.
    * **Verkehrsampel:** Die Ampelphasen laufen nach einem festen Zeitplan ab, unabhängig von der tatsächlichen Verkehrsdichte.
    * **Kaffeemaschine:** Das Gerät erhitzt das Wasser für eine vordefinierte Zeit, ohne die Wassertemperatur zu messen.

---

#### Geschlossener Wirkungskreis (Regelung)

* **Eigenschaften:**
    * **Mit Feedback:** Der Ausgang wird kontinuierlich gemessen und mit dem gewünschten Sollwert verglichen, um eine Regelabweichung zu bestimmen.
    * **Störgrößenkorrektur:** Das System kann auf äußere Störungen und Modellunsicherheiten reagieren, indem es die Regelabweichung minimiert.
    * **Komplexer Aufbau:** Der Aufbau ist aufwendiger, da Sensoren, ein Regler und eine Regelstrecke erforderlich sind.
    * **Hohe Genauigkeit und Robustheit:** Durch die Feedbackschleife kann eine hohe Genauigkeit und Unempfindlichkeit gegenüber Störungen erreicht werden.
* **Technische Anwendungen:**
    * **Tempomat im Auto:** Misst die tatsächliche Geschwindigkeit des Fahrzeugs und passt die Motorleistung an, um die voreingestellte Geschwindigkeit konstant zu halten.
    * **Thermostat in einer Heizung:** Misst die Raumtemperatur und schaltet die Heizung ein oder aus, um die gewünschte Solltemperatur zu halten.
    * **Robotergreifer:** Misst die Position des Greifers und korrigiert die Bewegung, um ein Objekt präzise zu greifen. .

---

### 2. Entwurf von Vorsteuerungen

**Vorsteuerung** ist eine Methode, die die Vorteile der Steuerung mit den Vorteilen der Regelung kombiniert. Sie ergänzt einen bestehenden Regelkreis, um die dynamischen Eigenschaften des Systems zu verbessern.

**Wie entwirft man eine Vorsteuerung?**

Der Entwurf einer Vorsteuerung basiert auf einem **Modell der Regelstrecke**. Das Ziel ist, die Eingangsgröße des Systems so vorzuformen, dass die Ausgangsgröße dem Sollwert folgt, bevor der Regelkreis überhaupt eingreift.

<img width="544" height="639" alt="image" src="https://github.com/user-attachments/assets/cda7ef25-8bb1-4e25-962b-a3ffa20c8f63" />



---

1. Wie kann man die folgenden Kenngrößen von Regelkreisen berechnen: Führungsübertragungsfunktion, Störübergangsfunktion, bleibende Regelabweichung, Kreisverstärkung, Stabilitätsrand, Pole, Empfindlichkeit?
2. Was besagt das Innere-Modell-Prinzip und wie kann man es für impulsförmige bzw. sprungförmige Störsignale erfüllen?

---


  

### 1. Berechnung von Kenngrößen im Regelkreis

Die Berechnung der Kenngrößen eines Regelkreises hängt von seiner Struktur ab. Hier werden die wichtigsten Kenngrößen basierend auf der offenen Kette G_o(s) = G_R(s) \cdot G_S(s) berechnet, wobei G_R(s) die Übertragungsfunktion des Reglers und G_S(s) die der Regelstrecke ist.

<img width="563" height="696" alt="image" src="https://github.com/user-attachments/assets/2609d56a-c8f1-4c8e-bc90-b9498c6ffed3" />


***

### 2. Das Innere-Modell-Prinzip (Internal Model Principle)

Das **Innere-Modell-Prinzip** besagt, dass ein stabiler Regelkreis eine stationäre Regelabweichung von null für eine bestimmte Eingangsgröße nur dann erreichen kann, wenn die Übertragungsfunktion des **offenen Regelkreises** ein Modell der Eingangsgröße enthält. Einfacher ausgedrückt: Um eine bestimmte Art von Störung oder Sollwertänderung zu eliminieren, muss der Regler eine interne Repräsentation (ein "inneres Modell") dieser Störung besitzen.

* **Erfüllung für impulsförmige Signale:**
    Ein Impuls ist eine sehr kurze Eingabe. Die Laplace-Transformierte eines Impulses ist 1. Um einen Impuls zu eliminieren, muss die offene Kette theoretisch einen **Pol im Unendlichen** haben, was praktisch nicht realisierbar ist. In der Praxis geht es nicht darum, einen Impuls zu eliminieren, sondern vielmehr darum, dessen Auswirkung schnell zu dämpfen.

* **Erfüllung für sprungförmige Signale:**
    Die Laplace-Transformierte einer Sprungfunktion ist 1/s. Um das Innere-Modell-Prinzip zu erfüllen, muss die Übertragungsfunktion des offenen Regelkreises G_o(s) einen **Pol bei s=0** enthalten. Dieser Pol entspricht einem **I-Anteil** im Regler, der den stationären Fehler eliminiert.
   <img width="178" height="28" alt="image" src="https://github.com/user-attachments/assets/dc06938e-6570-4390-ac3c-e95c09d56d82" />

    Das Hinzufügen des I-Anteils sorgt dafür, dass G_o(s) einen Pol bei s=0 hat, wodurch die bleibende Regelabweichung für eine sprungförmige Eingabe oder eine sprungförmige Störung zu null wird.

---
Die Reglerstruktur wird anhand struktureller Eigenschaften der Regelstrecke festgelegt.
Stellen Sie die Regeln für die Wahl der Reglerstruktur zusammen, wenn folgende Forderungen erfüllt werden sollen:
• Der Regelkreis soll stabil bzw. I-stabil sein.
• Der Regelkreis soll die Eigenschaft der Sollwertfolge besitzen.
• Das Messrauschen soll ausreichend unterdrückt werden.
• Der Regelkreis soll robust gegenüber Unsicherheiten des Regelstreckenmodells sein.
• Das Führungsverhalten und das Störverhalten sollen gegebene Dynamikforderungen erfüllen.
Klassifizieren Sie die Regelungsaufgaben in Abhängigkeit davon, welche dieser Forderungen von besonderer Bedeutung sind, und stellen Sie die für die einzelnen Klassen von Regelungsaufgaben zutreffenden Forderungen an die Reglerstruktur zusammen. Welche Beschränkungen ergibt sich für die Wahl der Reglerparameter aufgrund des Gleichgewichtstheorems?

---

Um die Reglerstruktur festzulegen, müssen die geforderten Eigenschaften des Regelkreises berücksichtigt werden. Die Wahl des Reglers ist ein Kompromiss zwischen Stabilität, Nachführgenauigkeit, Rauschunterdrückung und Robustheit.

***

### 1. Regeln für die Wahl der Reglerstruktur

<img width="561" height="671" alt="image" src="https://github.com/user-attachments/assets/8e6f7feb-032b-4a5e-8c46-5278e3effc60" />

***

### 2. Klassifizierung der Regelungsaufgaben und Forderungen an die Reglerstruktur

Je nach den Prioritäten der Anwendung kann man Regelungsaufgaben klassifizieren:

#### Klasse 1: Hohe Genauigkeit im stationären Zustand
* **Problem:** Stabile Regelstrecke mit stationären Störungen oder Sollwertänderungen.
* **Forderung:** Bleibende Regelabweichung soll Null sein.
* **Reglerstruktur:** **I-Regler** oder **PI-Regler** sind zwingend erforderlich, um einen Pol bei s=0 in der offenen Kette zu erzeugen (Innere-Modell-Prinzip). Der P-Anteil sorgt für eine schnellere Reaktion.
* **Beispiel:** Temperaturregelung in einem Ofen.

#### Klasse 2: Hohe Dynamik
* **Problem:** Schnelle und präzise Reaktion auf Sollwertänderungen oder Störungen gefordert, oft mit schwingendem Verhalten.
* **Forderung:** Kurze Anstiegszeit, minimale Überschwingung.
* **Reglerstruktur:** **PID-Regler** ist die beste Wahl. Der **D-Anteil** kann das Systemverhalten beschleunigen und das Überschwingen reduzieren.
* **Beispiel:** Servomotor-Positionsregelung.

#### Klasse 3: Hohe Robustheit
* **Problem:** Das Modell der Regelstrecke ist unsicher, oder es treten unvorhersehbare Störungen auf.
* **Forderung:** Das System muss unter allen Umständen stabil bleiben.
* **Reglerstruktur:** **P-Regler** (bei PT2-Strecken) oder **PI-Regler** (bei PT1-Strecken) mit einer **kleinen Verstärkung** sind oft die beste Wahl. Ein **D-Anteil wird vermieden**, da er hochfrequente Dynamik verstärkt und damit das System bei Modellunsicherheiten anfälliger für Instabilität macht. Ein **I-Anteil** kann bei der I-Stabilität kritisch sein, aber seine stabilisierende Wirkung bei langsamen Dynamiken ist oft wichtiger.
* **Beispiel:** Regelung von Prozessen mit vielen unvorhersehbaren Einflüssen (z.B. in der chemischen Industrie).

***

### 3. Beschränkungen durch das Gleichgewichtstheorem

<img width="556" height="513" alt="image" src="https://github.com/user-attachments/assets/085bab2d-a1f0-4e5e-a2ca-562a9317516f" />

 
---

1. Welche Entwurfsverfahren für einschleifige Regelkreise kennen Sie?
2. Vergleichen Sie die Annahmen, von denen die einzelnen Verfahren ausgehen, und geben Sie an, für welche Anwendungsfälle sich diese Verfahren deshalb besonders gut eignen.
3. Schreiben Sie das Vorgehen beim Entwurf für die einzelnen Verfahren in Form eines Programmablaufplanes auf. Wo treten Iterationsschleifen auf? Wann werden diese Schleifen durchlaufen und welche Veränderungen gegenüber vorhergehenden Entwurfsschritten finden in ihnen statt?
   
---
 
### 1. Entwurfsverfahren für einschleifige Regelkreise

Die wichtigsten Entwurfsverfahren für einschleifige Regelkreise lassen sich in zwei Hauptkategorien unterteilen: **analytische Verfahren** und **grafische Verfahren**.

* **Analytische Verfahren:**
    * **Ziegler-Nichols-Verfahren:** Ein empirisches Einstellverfahren für PID-Regler, das auf dem Sprungantwort-Verhalten der Strecke (offener Kreis) oder dem Verhalten an der Stabilitätsgrenze (geschlossener Kreis) beruht. Es liefert gute erste Schätzungen für die Reglerparameter.
    * **Reglerentwurf mit Pol-Nullstellen-Kompensation:** Nullstellen des Reglers werden so gewählt, dass sie Pole der Strecke kompensieren, um die Dynamik zu vereinfachen.

* **Grafische Verfahren:**
    * **Wurzelortskurven-Verfahren:** Man visualisiert, wie sich die Pole des geschlossenen Kreises bewegen, wenn ein Reglerparameter (meist die Verstärkung) variiert wird.
    * **Frequenzbereichs-Verfahren (Bode/Nyquist):** Die Reglerparameter werden angepasst, um die Frequenzgang-Eigenschaften der offenen Kette zu formen. Ziel ist es, einen ausreichenden Stabilitätsrand und eine gewünschte Dynamik zu erreichen. .

---

### 2. Vergleich der Verfahren und Anwendungsfälle

| Verfahren | Annahmen | Anwendungsfälle |
| :--- | :--- | :--- |
| **Ziegler-Nichols** | Die Strecke hat einen s-förmigen Übergangsverlauf (reines PTn oder PTtTn). Der Regelkreis kann in den schwingenden Zustand gebracht werden. | Ideal für einfache, aperiodische Prozesse in der Industrie (z. B. Temperatur-, Füllstands- oder Durchflussregelungen) bei denen eine moderate Genauigkeit ausreicht. Es ist ein schnelles, praxisnahes Verfahren, das kaum Modellkenntnisse voraussetzt. |
| **Pol-Nullstellen-Kompensation** | Ein genaues lineares Streckenmodell (z. B. in Form einer Übertragungsfunktion) ist bekannt. | Besonders gut geeignet für Systeme, die sich gut modellieren lassen. Es ist ein analytisches, präzises Verfahren, das sich hervorragend für hochdynamische Systeme (z. B. Servomotoren) eignet. |
| **Wurzelortskurven-Verfahren** | Ein lineares Streckenmodell in Form einer Übertragungsfunktion ist bekannt. Der Regler soll einen variablen Parameter (z. B. K_p) haben. | Ideal für den Entwurf von Systemen, bei denen die Platzierung der Pole des geschlossenen Kreises eine genaue Vorgabe ist (z. B. für eine bestimmte Dämpfung oder Eigenfrequenz). Es bietet einen klaren visuellen Einblick in die Stabilitätseigenschaften. |
| **Frequenzbereichs-Verfahren (Bode)** | Ein lineares Streckenmodell ist bekannt. Der Frequenzgang kann experimentell ermittelt werden. | Wird verwendet, wenn eine genaue Kenntnis der Frequenzeigenschaften des Systems entscheidend ist (z. B. in der Luftfahrt oder bei der Audioelektronik). Der Schwerpunkt liegt auf der Erzielung einer hohen Stabilität und Robustheit (durch Einhaltung von Phasen- und Amplitudenrand). |

---

### 3. Vorgehen und Iterationsschleifen

#### **Ziegler-Nichols-Verfahren (Iterationsschleife)**

* **Schritt 1:** Bestimmung der Parameter der Strecke aus der Sprungantwort oder durch Herbeiführen von Dauerschwingungen.
* **Schritt 2:** Berechnung der Reglerparameter (K_p, T_i, T_d) nach den Ziegler-Nichols-Regeln.
* **Schritt 3:** Implementierung der Reglerparameter und Test des Regelkreises.
* **Iterationsschleife (Wenn die Regelgüte nicht ausreicht):**
    * **Wann?** Wenn die Regelgüte (z. B. Überschwingen, Anstiegszeit, stationärer Fehler) nicht den Anforderungen entspricht.
    * **Veränderungen:** Die Reglerparameter werden manuell in kleinen Schritten angepasst (Tuning), z. B. K_p erhöhen, um das System schneller zu machen, oder T_d erhöhen, um die Schwingungen zu dämpfen.

#### **Wurzelortskurven-Verfahren (Iterationsschleife)**

* **Schritt 1:** Zeichnen der Wurzelortskurve der offenen Kette mit dem variablen Parameter (z. B. K_p).
* **Schritt 2:** Auswahl eines gewünschten Pols in der Wurzelortskurve, der die Systemanforderungen (z. B. Dämpfung) erfüllt.
* **Schritt 3:** Ablesen der zugehörigen Reglerverstärkung K_p aus der Wurzelortskurve.
* **Iterationsschleife (Wenn der gewünschte Pol nicht auf der Wurzelortskurve liegt):**
    * **Wann?** Wenn die gewünschte Polposition (z. B. ein schneller, gedämpfter Pol) nicht auf der Kurve liegt.
    * **Veränderungen:** Der Regler wird umgestaltet, indem zusätzliche Pole oder Nullstellen hinzugefügt werden (z. B. durch einen PD- oder PID-Regler). Dies verändert das gesamte Layout der Wurzelortskurve, und die Schritte 1-3 werden wiederholt. .

#### **Frequenzbereichs-Verfahren (Bode-Diagramm) (Iterationsschleife)**

* **Schritt 1:** Zeichnen des Bode-Diagramms der offenen Kette ohne Regler.
* **Schritt 2:** Auswahl einer Reglerstruktur (z. B. PI oder PID).
* **Schritt 3:** Schätzung der Reglerparameter, um die gewünschten Stabilitätsränder zu erreichen (z. B. durch Verschieben des Frequenzgangs im Amplituden- und Phasendiagramm).
* **Iterationsschleife (Wenn die Stabilitätsränder oder die Dynamik nicht den Anforderungen entsprechen):**
    * **Wann?** Wenn der Phasen- oder Amplitudenrand zu klein ist oder wenn die Bandbreite nicht ausreicht.
    * **Veränderungen:** Die Reglerparameter werden angepasst. Zum Beispiel wird der I-Anteil verschoben, um die Phase bei niedrigen Frequenzen anzuheben, oder der D-Anteil hinzugefügt, um die Phase bei höheren Frequenzen zu erhöhen und die Stabilität zu verbessern. Die Schritte 1-3 werden mit den neuen Parametern wiederholt.
 
---

Ein Regelkreis, der aus einer stabilen Regelstrecke und einem PID-Regler besteht, schwingt. Wie müssen Sie die Reglerparameter kP, TI und TD verändern, um dieses Schwingen zu beseitigen? Erläutern Sie Ihr Vorgehen anhand der Wurzelortskurve, am Bodediagramm der offenen Kette und an der Ortskurve der offenen Kette. Wie verändern sich diese Diagramme, wenn Sie den D-Anteil abschalten (TD = 0)?

---
 
Das Schwingen eines Regelkreises mit einem PID-Regler deutet auf **Instabilität** oder **zu geringe Dämpfung** hin. Um dieses Schwingen zu beseitigen, müssen die Reglerparameter so verändert werden, dass das System stabiler wird.

### Vorgehensweise zur Beseitigung des Schwingens

| Parameter | Veränderung | Begründung |
| :--- | :--- | :--- |
| **k_p (Proportionalanteil)** | Verringern | Eine Verringerung von k_p **senkt die Kreisverstärkung**. Dies verkleinert im **Bodediagramm** den Amplitudengang, erhöht den **Amplitudenrand** und verschiebt die **Schnittfrequenz** zu kleineren Werten, wo die Phase noch nicht so stark verzögert ist. Im **Wurzelort** wandern die Pole der geschlossenen Kette von der imaginären Achse in die linke Halbebene. |
| **T_I (Integralzeit)** | Erhöhen | Eine Erhöhung der Integralzeit **verringert den I-Anteil** und damit die Verstärkung bei niedrigen Frequenzen. Dadurch wird der Phasenabfall des I-Gliedes zu höheren Frequenzen verschoben, was zu einem größeren **Phasenrand** führt. In der **Ortskurve** wird der Kurvenverlauf flacher, und der kritische Punkt (-1, 0) wird nicht mehr umschlossen. |
| **T_D (Differenzialzeit)** | Erhöhen | Eine Erhöhung der Differenzialzeit **erhöht den D-Anteil**. Dies fügt im **Bodediagramm** eine Phasenreserve hinzu (der Phasengang wird bei höheren Frequenzen angehoben). Im **Wurzelort** bewegt der D-Anteil die Pole von der imaginären Achse weg und erzeugt eine zusätzliche Nullstelle in der linken Halbebene, die die Pole in die linke Halbebene zieht und die Dämpfung erhöht. . |

---

### Veranschaulichung in den Diagrammen

#### **Wurzelortskurve**
* **Mit D-Anteil:** Die Wurzelortskurve zeigt, wie die Pole der geschlossenen Schleife mit zunehmender Reglerverstärkung (k_p) die imaginäre Achse überschreiten. Um das Schwingen zu beseitigen, muss der **Regler so getuned werden, dass die Pole in die linke Halbebene zurückkehren**. Dies geschieht, indem k_p verringert oder der D-Anteil erhöht wird, was die Pole von der Achse wegbewegt und zu einem stabilen, gedämpften Verhalten führt.

* **D-Anteil abschalten (T_D = 0):** Der D-Anteil fügt dem System eine Nullstelle in der linken Halbebene hinzu. Ohne diese Nullstelle ändert sich der Verlauf der Wurzelortskurve dramatisch. Die Pole des Systems werden sich **stärker in Richtung der rechten Halbebene bewegen** oder die imaginäre Achse bei einer geringeren Verstärkung schneiden.

#### **Bodediagramm der offenen Kette**
* **Mit D-Anteil:** Ein PID-Regler hebt den Phasengang bei den kritischen Frequenzen an, wodurch der **Phasenrand** vergrößert wird. Wenn das System schwingt, ist der Phasenrand null oder negativ. Man muss k_p verringern (senkt den Amplitudengang) oder T_D erhöhen (hebt den Phasengang an), um den Phasenrand wieder positiv zu machen.

* **D-Anteil abschalten (T_D = 0):** Ohne den D-Anteil fehlen die Phasenreserve und der Anstieg im Amplitudengang bei höheren Frequenzen. Die **Phase nähert sich der -180^\circ-Grenze schneller an**, was zu einem geringeren Phasenrand und einer erhöhten Schwingungsneigung führt. Die Reglerverstärkung k_p muss deutlich kleiner gewählt werden, um Stabilität zu gewährleisten.

#### **Ortskurve der offenen Kette**
* **Mit D-Anteil:** Wenn das System schwingt, umschließt die Ortskurve den kritischen Punkt (-1, 0) oder geht direkt durch ihn hindurch. Um das Schwingen zu beseitigen, muss die Ortskurve so verändert werden, dass sie den kritischen Punkt nicht mehr umschließt. Dies geschieht durch eine **Verkleinerung des Radius** der Kurve (Verringerung von k_p) oder durch **Verschiebung der Kurve weg vom kritischen Punkt** (durch Erhöhung von T_D). .

* **D-Anteil abschalten (T_D = 0):** Die Ortskurve eines PI-Reglers (T_D = 0) wird den kritischen Punkt **viel leichter umschließen**. Der D-Anteil bewirkt eine "Rückbiegung" der Ortskurve nach rechts, weg vom kritischen Punkt, was das System stabilisiert. Ohne diesen Effekt ist die Stabilität schwieriger zu erreichen.

---

1. Welche Modelle dynamischer Systeme haben Sie kennengelernt?
2. Welche Eigenschaften treten sowohl bei Eingrößen- als auch bei Mehrgrößensystemen auf? Welche zusätzlichen Eigenschaften haben Mehrgrößensysteme?
3. Welche Systemeigenschaften sind struktureller Art, so dass sie weitgehend unabhängig von den Systemparametern sind und mit graphentheoretischen Mitteln bestimmt werden können?

---
### 1. Modelle dynamischer Systeme

In der Regelungstechnik werden dynamische Systeme hauptsächlich durch folgende Modelle beschrieben:

* **Zeitbereichsmodelle**:
    * **Differentialgleichungen**: Beschreiben die Beziehung zwischen Eingangs- und Ausgangsgröße in Form von Differentialgleichungen. Sie sind besonders für Eingrößensysteme (SISO) geeignet.
    * **Zustandsraumdarstellung**: Beschreibt die interne Dynamik eines Systems durch einen Satz von Differentialgleichungen erster Ordnung für die Zustandsvariablen. Dieses Modell ist universell und sowohl für Eingrößen- als auch für Mehrgrößensysteme (MIMO) anwendbar. 

* **Frequenzbereichsmodelle**:
    * **Übertragungsfunktion**: Das Verhältnis der Laplace-transformierten Ausgangs- zur Eingangsgröße unter der Annahme null Anfangsbedingungen. Es beschreibt das E/A-Verhalten (Eingabe-Ausgabe) und ist hauptsächlich für lineare, zeitinvariante (LTI) SISO-Systeme relevant.
    * **Frequenzgang**: Die Übertragungsfunktion für s = j\omega. Sie beschreibt das Verhalten des Systems auf sinusförmige Eingangssignale.

***

### 2. Eigenschaften von Ein- und Mehrgrößensystemen

#### Gemeinsame Eigenschaften

* **Stabilität**: Ein System ist stabil, wenn seine Ausgabe für begrenzte Eingaben begrenzt bleibt (BIBO-Stabilität) oder wenn es nach einer Störung in den Gleichgewichtszustand zurückkehrt. Die Stabilität wird durch die Pole der Übertragungsfunktion bzw. die Eigenwerte der Systemmatrix bestimmt.
* **Linearität**: Ein System ist linear, wenn es das Superpositionsprinzip erfüllt. Dies ist eine grundlegende Eigenschaft für die Anwendung der meisten mathematischen Werkzeuge der Regelungstechnik.
* **Ordnung**: Die Ordnung eines Systems wird durch die Anzahl der Zustandsvariablen oder durch den Grad des Nennerpolynoms der Übertragungsfunktion bestimmt. Sie gibt Aufschluss über die Komplexität und die dynamische Speicherfähigkeit des Systems.

#### Zusätzliche Eigenschaften von Mehrgrößensystemen

* **Entkopplung (Decoupling)**: Die Fähigkeit, die verschiedenen Ein- und Ausgänge eines MIMO-Systems so zu steuern, dass die Wirkung eines Eingangs auf einen bestimmten Ausgang minimiert oder vollständig eliminiert wird. Dies ist oft das Hauptziel beim Entwurf von MIMO-Reglern.
* **Wechselwirkung (Interaction)**: In einem Mehrgrößensystem beeinflusst eine Eingangsgröße typischerweise mehrere Ausgangsgrößen, und umgekehrt. Diese unerwünschten Wechselwirkungen machen den Reglerentwurf komplexer.

***

### 3. Strukturelle Systemeigenschaften

Strukturelle Systemeigenschaften sind unabhängig von den genauen Werten der Systemparameter (z.B. Widerständen, Kapazitäten). Sie hängen von der **Topologie** oder der internen Konnektivität des Systems ab und können oft mit graphentheoretischen Mitteln analysiert werden.

* **Strukturelle Steuerbarkeit**: Ein System ist strukturell steuerbar, wenn es möglich ist, alle Zustände durch eine geeignete Wahl der Eingabeverbindungen zu steuern. Die strukturelle Steuerbarkeit hängt von der Anordnung von Nullen und Einsen in den Matrizen A und B der Zustandsraumdarstellung ab.
* **Strukturelle Beobachtbarkeit**: Ein System ist strukturell beobachtbar, wenn es möglich ist, alle internen Zustände durch die Messung der Ausgaben zu rekonstruieren. Die strukturelle Beobachtbarkeit hängt von der Anordnung von Nullen und Einsen in den Matrizen A und C ab.
* **Struktureller Rang**: Der Rang der Matrizen, die die Steuerbarkeit oder Beobachtbarkeit beschreiben. Graphentheoretische Verfahren, wie die Analyse von Graphen auf zyklische Strukturen oder Pfade, können verwendet werden, um festzustellen, ob ein System strukturell steuerbar oder beobachtbar ist.

---

1. Stellen Sie die Beschreibungsformen für kontinuierliche und zeitdiskrete Systeme in Form einer Tabelle gegenüber und kennzeichnen Sie durch Pfeile, welche Modelle Sie direkt ineinander umrechnen können, wenn das zeitdiskrete System aus dem kontinuierlichen durch Abtastung hervorgeht.
2. Wie können die Pole und Nullstellen beider Systemklassen berechnet werden?
3. Wie können Sie die Steuerbarkeit, Beobachtbarkeit und Stabilität überprüfen? Welche Beziehungen gibt es zwischen diesen Eigenschaften des kontinuierlichen Systems und des zeitdiskreten Systems, das aus dem kontinuierlichen System durch Abtastung entsteht?
4. Welche Reglerentwurfsverfahren sind für beide Betrachtungsweisen anwendbar, welche nur für kontinuierliche bzw. nur für zeitdiskrete Systeme?

---

### 1. Vergleich von kontinuierlichen und zeitdiskreten Systemmodellen

| Beschreibungsform | Kontinuierliche Systeme | Zeitdiskrete Systeme |
| :--- | :--- | :--- |
| **Zeitbereichsmodelle** | Differentialgleichungen <img width="238" height="37" alt="image" src="https://github.com/user-attachments/assets/e2f330fd-ebab-499b-97d8-340ff48c1d37" />
 | Differenzengleichungen x[k+1]=A_dx[k]+B_du[k] y[k]=C_dx[k]+D_du[k] |
| **Frequenzbereichsmodelle** | Übertragungsfunktion G(s) | Impulsübertragungsfunktion G(z) |

<img width="460" height="391" alt="image" src="https://github.com/user-attachments/assets/84c7283f-9f9e-4c89-a84d-7a8302a27c3c" />


***

### 2. Berechnung von Polen und Nullstellen

* **Kontinuierliche Systeme:**
    * **Pole:** Die Pole von G(s) sind die Wurzeln des Nennerpolynoms. Sie sind auch die **Eigenwerte** der Systemmatrix A in der Zustandsraumdarstellung.
    * **Nullstellen:** Die Nullstellen von G(s) sind die Wurzeln des Zählerpolynoms.

* **Zeitdiskrete Systeme:**
    * **Pole:** Die Pole von G(z) sind die Wurzeln des Nennerpolynoms. Sie sind auch die Eigenwerte der diskreten Systemmatrix A_d.
    * **Nullstellen:** Die Nullstellen von G(z) sind die Wurzeln des Zählerpolynoms.

***

### 3. Steuerbarkeit, Beobachtbarkeit und Stabilität

#### Überprüfung
* **Kontinuierlich:**
    * **Steuerbarkeit:** Überprüfen Sie den Rang der Steuerbarkeitsmatrix <img width="235" height="33" alt="image" src="https://github.com/user-attachments/assets/dc1971da-18be-4fb1-96b7-f1daaabd7030" />
 Der Rang muss gleich der Systemordnung n sein.
    * **Beobachtbarkeit:** Überprüfen Sie den Rang der Beobachtbarkeitsmatrix <img width="323" height="30" alt="image" src="https://github.com/user-attachments/assets/b108672c-9f65-4fe7-9b19-e4fee741259e" />
 Der Rang muss ebenfalls n sein.
    * **Stabilität:** Ein System ist stabil, wenn alle **Eigenwerte von A einen negativen Realteil** haben. .

* **Zeitdiskret:**
    * **Steuerbarkeit & Beobachtbarkeit:** Die gleichen Rangbedingungen gelten für die diskreten Matrizen A_d und B_d bzw. A_d und C_d.
    * **Stabilität:** Ein System ist stabil, wenn alle **Eigenwerte von A_d innerhalb des Einheitskreises** in der z-Ebene liegen <img width="64" height="25" alt="image" src="https://github.com/user-attachments/assets/27d01c2b-9b30-4c55-b247-a4d9ac2c03de" />
. .

#### Beziehungen bei Abtastung
* **Steuerbarkeit & Beobachtbarkeit:**
    * Wenn das kontinuierliche System steuerbar ist, ist auch das abgetastete System steuerbar, wenn der **Abtastzeitraum T_a kurz genug** ist. Die Abtastfrequenz muss mehr als doppelt so hoch sein wie die höchste Eigenfrequenz des Systems. Bei Pole-Nullstellen-Kompensationen, die bei Abtastung zu Pol-Nullstellen-Anordnungen am gleichen Ort führen, kann die diskrete Steuerbarkeit verloren gehen.
    * Gleiches gilt für die Beobachtbarkeit. Ein beobachtbares kontinuierliches System führt zu einem beobachtbaren diskreten System.
* **Stabilität:**
    * Ein **stabiles kontinuierliches System** mit Eigenwerten in der linken s-Halbebene führt immer zu einem **stabilen zeitdiskreten System**, da die Eigenwerte durch z_i = e^{s_i T_a} in den Einheitskreis transformiert werden.
    * Die Umkehrung gilt nicht: Ein zeitdiskretes System kann stabil sein, auch wenn das ursprüngliche kontinuierliche System instabil war, wenn die Abtastung zu langsam ist (Aliasing-Effekt).

***

### 4. Reglerentwurfsverfahren

* **Beide anwendbar:**
    * **Ziegler-Nichols-Verfahren:** Sowohl die Frequenz- als auch die Zeitbereichsversion sind anwendbar.
    * **Wurzelortskurven-Verfahren:** Anwendbar, aber die Stabilitätsbedingungen sind unterschiedlich (linke Halbebene vs. Einheitskreis).
    * **Zustandsraummethoden:** Der Entwurf von Zustandsreglern oder Beobachtern ist in beiden Bereichen möglich.

* **Nur für kontinuierliche Systeme:**
    * **Ortskurvenverfahren (Nyquist-Kriterium):** Kann nur für kontinuierliche Systeme verwendet werden.
    * **Bode-Diagramm:** Obwohl es ein diskretes Äquivalent gibt, sind die klassischen Entwurfsmethoden (z.B. Phasen- und Amplitudenrand) intuitiver für kontinuierliche Systeme.

* **Nur für zeitdiskrete Systeme:**
    * **z-Ebene-Methoden:** Direkte z-Transformation und die z-Ebene-Polplatzierung.
    * **Deadbeat-Algorithmus:** Ein Regler, der die Systemantwort in einer minimalen Anzahl von Schritten auf den Sollwert bringt, was nur in der diskreten Domäne möglich ist.
 
---
1. Erläutern Sie die Definitionen der Zustandsstabilität, der E/A-Stabilität und der inneren
Stabilität von Regelkreisen.
2. Wie hängen diese Stabilitätseigenschaften zusammen? (Hinweis: Stellen Sie Bedingungen zusammen, unter denen mit einer der angegebenen Stabilitätseigenschaften gleichzeitig eine andere dieser Eigenschaften nachgewiesen
ist.)
3. Wie kann die Stabilität von Regelkreisen geprüft werden? (Hinweis: Stellen Sie die für die einzelnen Modellformen anwendbaren Bedingungen zusammen. Kennzeichnen Sie, welche der Bedingungen notwendig, welche hinreichend bzw. welche notwendig und hinreichend für die Stabilität sind.)
4. Was versteht man unter Integrität? Wie kann man diese Eigenschaft nachweisen?

---

### 1. Definitionen der Stabilitätsarten

* **Zustandsstabilität (Ljapunow-Stabilität):** Ein System ist zustandsstabil, wenn für jeden beliebigen Anfangszustand die nachfolgenden Zustände beschränkt bleiben. Das bedeutet, das System schwingt nicht unendlich auf. Es kann aber sein, dass das System nicht zu seinem Gleichgewichtszustand zurückkehrt.
* **E/A-Stabilität (BIBO-Stabilität):** Ein System ist E/A-stabil, wenn für jede beschränkte Eingabe (u(t)) die Ausgabe (y(t)) ebenfalls beschränkt bleibt. 
* **Innere Stabilität (Asymptotische Stabilität):** Ein System ist intern stabil, wenn es zustandsstabil ist und zusätzlich nach einer Störung in seinen Gleichgewichtszustand zurückkehrt. Bei LTI-Systemen kehrt es zu seinem ursprünglichen Zustand zurück. Dies ist die stärkste Form der Stabilität.

---

### 2. Zusammenhänge zwischen den Stabilitätseigenschaften

Der Zusammenhang zwischen diesen Stabilitätsdefinitionen ist hierarchisch:

* **Innere Stabilität impliziert Zustandsstabilität.** Wenn ein System in seinen Gleichgewichtszustand zurückkehrt, bleiben seine Zustände notwendigerweise beschränkt.
* **Innere Stabilität impliziert E/A-Stabilität.** Wenn ein System seine Zustände wieder auf einen Gleichgewichtspunkt zurückführt, bleibt die Ausgabe für jede beschränkte Eingabe ebenfalls beschränkt.
* **Unter bestimmten Bedingungen gilt auch die Umkehrung:**
    * Für **vollständig steuerbare und vollständig beobachtbare LTI-Systeme** sind alle drei Stabilitätsdefinitionen äquivalent. Das bedeutet, wenn eine dieser Eigenschaften nachgewiesen ist, sind die anderen beiden ebenfalls erfüllt.
    * Wenn ein System nur **E/A-stabil** ist, bedeutet das nicht zwangsläufig, dass es auch intern stabil ist. Ein Beispiel ist ein System mit einem Pol und einer Nullstelle am selben Ort im rechten Halbebene. Dieses System ist E/A-stabil, aber intern instabil, da ein ungesteuerter, ungedämpfter Eigenvorgang existiert.

---

### 3. Überprüfung der Stabilität

Die Stabilität kann je nach Modellform mit verschiedenen Kriterien überprüft werden:

| Modellform | Kriterium | Bedingung |
| :--- | :--- | :--- |
| **Zustandsraum** | Eigenwert-Kriterium | Alle Eigenwerte von A müssen einen **negativen Realteil** haben. |
| | | (Notwendig und hinreichend für asymptotische Stabilität) |
| **Übertragungsfunktion** | Pol-Kriterium | Alle Pole von G(s) müssen in der **linken Halbebene** liegen. |
| | | (Notwendig und hinreichend für BIBO-Stabilität) |
| **Charakteristisches Polynom** | Hurwitz-Kriterium | Alle Hauptunterdeterminanten der Hurwitz-Matrix müssen **positiv** sein. |
| | Routh-Kriterium | Alle Elemente der ersten Spalte des Routh-Schemas müssen **positiv** sein. |
| | | (Beide sind notwendig und hinreichend für die Stabilität des Polynoms) |
| **Frequenzbereich** | Nyquist-Kriterium | Die Ortskurve des offenen Kreises darf den kritischen Punkt **(-1, j0) nicht umschließen**. |
| | | (Notwendig und hinreichend für die Stabilität des geschlossenen Regelkreises) |
| | Bode-Kriterium | Der Amplitudenrand muss >1 sein und der Phasenrand muss >0 sein. |
| | | (Hinreichend für Stabilität, aber nicht notwendig) |

---

### 4. Integrität

* **Definition:** Die Integrität eines Regelkreises bezeichnet seine Fähigkeit, auch beim Ausfall eines Teilsystems (z.B. eines Sensors) **stabil zu bleiben**. Es ist eine Eigenschaft der **Robustheit** gegenüber Ausfällen. Ein Regelkreis, der nach einem Sensorausfall instabil wird, hat keine Integrität.
* **Nachweis:**
    * **Verfahren:** Der Nachweis erfolgt durch die Analyse der Stabilität des Regelkreises unter der Annahme, dass ein oder mehrere seiner Bestandteile (z.B. ein Feedback-Pfad) ausgefallen sind.
    * **Mathematisch:** Man muss die Übertragungsfunktion des Regelkreises für alle möglichen Ausfallszenarien aufstellen und dann die Stabilität dieser neuen, vereinfachten Systeme überprüfen. Beispielsweise kann man die Übertragungsfunktion des Reglers G_R(s) durch 0 ersetzen, um den Ausfall zu simulieren, und dann die Stabilität des restlichen Regelkreises prüfen. Wenn das System in allen relevanten Ausfallszenarien stabil bleibt, hat es eine gute Integrität.
 
---
Gegeben ist eine instabile Regelstrecke. Beantworten Sie die folgenden Fragen zur Existenz und zum Entwurf einer linearen Regelung, mit der der geschlossene Kreis stabil ist.

1. Welche Eigenschaften muss die Regelstrecke besitzen, damit ein Regler gefunden werden kann, für den der geschlossene Regelkreis stabil ist? Sind diese Forderungen für kontinuierliche Regler bzw. Abtastregler unterschiedlich?
2. Unter welchen Bedingungen kann das Stabilisierungsproblem durch eine proportionale Rückführung gelöst werden?
3. Unter welchen Bedingungen sind dynamische Regler notwendig? Welche Struktur haben diese dynamischen Regler und wie findet man geeignete dynamische Elemente dieser Regler?
4. Wie geht man vor, um stabilisierende Regler zu entwerfen?
5. Unter welcher Bedingung ist die Stabilität des entstehenden Regelkreises robust gegenüber Modellunbestimmtheiten?

---
 
Eine instabile Regelstrecke kann durch einen geeigneten linearen Regler stabilisiert werden, wenn bestimmte Bedingungen erfüllt sind.

***

### 1. Erforderliche Eigenschaften der Regelstrecke

Damit eine instabile Regelstrecke stabilisiert werden kann, muss sie **steuerbar** sein. Das bedeutet, dass alle instabilen Pole der Strecke durch eine geeignete Eingabe beeinflusst und in die linke Halbebene verschoben werden können.

* **Kontinuierliche und Abtastregler**: Die Forderung nach Steuerbarkeit gilt sowohl für kontinuierliche als auch für abgetastete Systeme. Für ein zeitdiskretes System, das durch Abtastung eines kontinuierlichen Systems entsteht, ist die Steuerbarkeit gewährleistet, wenn das kontinuierliche System steuerbar ist und die Abtastzeit T_a kurz genug ist, sodass keine Pole des ursprünglichen Systems (insbesondere konjugiert komplexe Paare) Aliasing verursachen.

***

### 2. Stabilisierung durch proportionale Rückführung

Eine proportionale Rückführung (P-Regler) kann eine instabile Regelstrecke nur unter bestimmten Bedingungen stabilisieren.

* **Bedingungen**: Das Stabilisierungsproblem kann durch eine proportionale Rückführung gelöst werden, wenn das **Wurzelortskurven-Verfahren** zeigt, dass die Wurzeln des geschlossenen Kreises für einen positiven Verstärkungsfaktor k_p in die linke Halbebene wandern. Dies ist der Fall, wenn die Wurzelortskurve, die von den instabilen Polen ausgeht, die imaginäre Achse schneidet und in die linke Halbebene eintritt. Ein einfacher, stabiler Pol kann einen instabilen Pol in die linke Halbebene ziehen. Ein einzelner, reeller, instabiler Pol kann durch eine proportionale Rückführung stabilisiert werden, solange der Wurzelort zu einem stabilen Ort führt.

***

### 3. Notwendigkeit und Struktur dynamischer Regler

Dynamische Regler sind notwendig, wenn eine proportionale Rückführung allein nicht ausreicht, um die Stabilität zu gewährleisten.

* **Bedingungen**:
    * Wenn die Wurzelortskurve von den instabilen Polen ausgeht und die imaginäre Achse nie in die linke Halbebene schneidet.
    * Wenn ein Paar von konjugiert komplexen instabilen Polen vorliegt, die eine zusätzliche Dämpfung erfordern.
    * Wenn eine Totzeit vorliegt, die zusätzliche Phasenverzögerung in den Regelkreis einbringt.
* **Struktur**: Die einfachste Form eines dynamischen Reglers ist ein **Phasen-Voreil-Regler** (lead compensator). Dieser Regler hat die Struktur eines PD-Reglers mit einem zusätzlichen Pol zur Rauschunterdrückung. Die Übertragungsfunktion hat die Form G_R(s) = K \frac{s + a}{s + b} mit a < b.
* **geeignete dynamische Elemente**: Die Nullstelle (s = -a) und der Pol (s = -b) des dynamischen Reglers werden so platziert, dass sie die **Wurzelortskurve in die linke Halbebene "biegen"**. Die Nullstelle wird in der Nähe der instabilen Pole platziert, um sie anzuziehen, während der Pol weiter entfernt platziert wird, um die Phasenerhöhung zu maximieren. Das **Bode-Diagramm** ist hierbei hilfreich, da der Phasen-Voreil-Regler bei den kritischen Frequenzen eine positive Phasenerhöhung hinzufügt und so den Phasenrand vergrößert.

***

### 4. Entwurf von stabilisierenden Reglern

Der Entwurf stabilisierender Regler ist ein iterativer Prozess, der folgende Schritte umfasst:

1.  **Systemanalyse**: Analysieren Sie die Stabilität der offenen Strecke. Bestimmen Sie die Pole, Nullstellen und den relativen Grad. Identifizieren Sie alle instabilen Pole.
2.  **Reglerwahl**: Wählen Sie eine geeignete Reglerstruktur (z.B. P, PD, PID, oder einen Phasen-Voreil-Regler).
3.  **Parameteranpassung**:
    * **Wurzelortskurve**: Passen Sie die Reglerparameter (z.g. k_p) an, um die Pole des geschlossenen Kreises in die linke Halbebene zu verschieben. Bei dynamischen Reglern platzieren Sie Pole und Nullstellen so, dass der Wurzelort die gewünschten Regionen durchläuft.
    * **Frequenzbereich**: Gestalten Sie den Frequenzgang der offenen Kette so, dass er einen ausreichenden **Phasen- und Amplitudenrand** aufweist. Dies geschieht durch Hinzufügen von Phasenreserve (mit einem D-Anteil oder einem Phasen-Voreil-Regler).
4.  **Verifikation**: Überprüfen Sie die Stabilität des entworfenen Systems mit den gewählten Parametern (z.B. durch das Routh-Kriterium). .
5.  **Optimierung**: Wenn die Systemantwort nicht den Anforderungen entspricht (z.B. zu langsam oder zu viel Überschwingen), passen Sie die Parameter an und wiederholen Sie den Prozess.

***

### 5. Robuste Stabilität

Die Stabilität eines Regelkreises ist robust gegenüber Modellunsicherheiten, wenn der Regler so entworfen wurde, dass er mit Variationen der tatsächlichen Systemparameter umgehen kann.

* **Bedingung**: Robuste Stabilität wird erreicht, wenn die **Empfindlichkeitsfunktion** S(s) = \frac{1}{1+G_o(s)} bei den Frequenzen, an denen Modellunsicherheiten auftreten, möglichst klein ist.
* **Nachweis**:
    * **Frequenzbereich**: Ein großer **Phasenrand** (z.B. > 45^\circ) und ein hoher **Amplitudenrand** (z.B. > 6 dB) im **Bode-Diagramm** sind Indikatoren für robuste Stabilität.
    * **In der Wurzelortskurve**: Die Wurzeln des geschlossenen Kreises sollten eine ausreichende Distanz von der imaginären Achse haben, um auch bei kleinen Änderungen der Pole nicht in die rechte Halbebene zu wandern. Dies wird durch die sogenannte **relative Stabilität** bestimmt.
 
---
1. Warum haben Zustandsrückführungen eine so große Bedeutung in der Regelungstechnik, obwohl sie i. Allg. technisch nicht realisierbar sind?
2. Wie können Zustandsrückführungen entworfen werden?
3. Wie können Zustandsrückführungen realisiert werden?
4. Welche Probleme entstehen, wenn man von einer Zustandsrückführung auf eine Ausgangsrückführung übergeht?
5. Unter welchen Bedingungen besitzt der Regelkreis mit Zustandsrückführung die Eigenschaft der Sollwertfolge?

---
 
### 1. Warum Zustandsrückführungen so wichtig sind

Zustandsrückführungen haben eine große Bedeutung in der Regelungstechnik, obwohl sie technisch selten direkt umsetzbar sind, weil sie ein **ideales theoretisches Konzept** darstellen. Sie ermöglichen es, die **Pole des geschlossenen Regelkreises an jede beliebige Position** in der stabilen linken Halbebene zu verschieben (sogenannte "Polplatzierung"), vorausgesetzt, das System ist **vollständig steuerbar**. Dies ist der Hauptgrund für ihre theoretische Relevanz: Sie zeigen, was unter idealen Bedingungen möglich ist, und dienen als Grundlage für den Entwurf von praktischen Reglern.

---

### 2. Entwurf von Zustandsrückführungen

Der Entwurf einer Zustandsrückführung basiert auf der **Zustandsraumdarstellung** des Systems:
<img width="152" height="32" alt="image" src="https://github.com/user-attachments/assets/8710f745-4b88-4d19-bfb9-ff4cbc0c4d76" />

y(t) = Cx(t) + Du(t)Das Rückführungsgesetz lautetu(t) = -Kx(t) + r(t) wobei K der Rückführvektor der Verstärkungen und r(t) der Sollwert ist.

<img width="538" height="246" alt="image" src="https://github.com/user-attachments/assets/5edd269e-d7f2-4d49-860b-c7b32ecdc5a4" />


---

### 3. Realisierung von Zustandsrückführungen

Zustandsrückführungen sind in der Praxis nur selten direkt realisierbar, da oft nicht alle Zustandsvariablen messbar sind. Die Lösung dafür ist der Einsatz eines **Zustandsbeobachters (State Observer)**.

* **Prinzip:** Ein Zustandsbeobachter ist ein dynamisches System, das die internen Zustandsvariablen des realen Systems auf der Grundlage der messbaren Eingangs- und Ausgangsgrößen **schätzt**. Der Beobachter hat die gleiche mathematische Struktur wie das Originalsystem.
* **Realisierung:** Die geschätzten Zustände \hat{x}(t) aus dem Beobachter werden anstelle der realen Zustände für die Rückführung verwendet. Das Rückführungsgesetz lautet dann <img width="167" height="38" alt="image" src="https://github.com/user-attachments/assets/c1baad35-67af-41a1-acf1-67a5b6503fdb" />

* **Separierungsprinzip:** Die Theorie besagt, dass der Entwurf des Reglers (Polplatzierung der Zustände) und der Entwurf des Beobachters (Polplatzierung der Fehler) **unabhängig voneinander** durchgeführt werden können. Das bedeutet, man entwirft zuerst den idealen Zustandsrückführungsregler und dann den Beobachter, der die geschätzten Zustände bereitstellt.

---

### 4. Probleme bei der Umstellung von Zustands- auf Ausgangsrückführung

Wenn man von der idealen Zustandsrückführung auf eine realisierbare Ausgangsrückführung (mit einem Zustandsbeobachter) übergeht, können folgende Probleme auftreten:

* **Verzögerungen und Ungenauigkeiten:** Der Beobachter benötigt Zeit, um sich an die realen Zustände anzunähern. Dies kann zu Verzögerungen und Ungenauigkeiten in der Rückführung führen.
* **Empfindlichkeit gegenüber Störungen:** Beobachter sind empfindlich gegenüber Messrauschen und Modellunsicherheiten. Ein ungenauer Beobachter kann dazu führen, dass die geschätzten Zustände von den tatsächlichen abweichen, was die Stabilität des Systems beeinträchtigt.
* **Erhöhte Systemordnung:** Der Zustandsbeobachter fügt dem System zusätzliche Dynamik hinzu, was die Systemordnung verdoppelt. . Dies kann den Entwurf komplizierter machen und zu unerwarteten Eigenbewegungen führen.

---

### 5. Sollwertfolge mit Zustandsrückführung

Ein Regelkreis mit reiner Zustandsrückführung hat im Allgemeinen **nicht** die Eigenschaft der Sollwertfolge, das heißt, es verbleibt ein **stationärer Fehler**.

* **Bedingung für Sollwertfolge:** Die Sollwertfolge kann nur erreicht werden, wenn die Übertragungsfunktion des geschlossenen Regelkreises bei **s \to 0 den Wert 1** annimmt. In einer reinen Zustandsrückführung kann dies nur erreicht werden, indem die Zustandsrückführung durch eine **Integratorrückkopplung** oder eine **Vorsteuerung** ergänzt wird.
* **Realistisches Szenario:** In der Praxis wird eine Zustandsrückführung oft durch eine **Regler-Struktur mit einem Integralanteil** erweitert, die den stationären Fehler eliminiert. Der I-Anteil sorgt dafür, dass die offene Kette einen Pol bei s=0 hat, was nach dem **Inneren-Modell-Prinzip** für die Sollwertfolge bei sprungförmigen Eingaben notwendig ist.

---
1. Stellen Sie die Entwurfsprinzipien für Ein- und Mehrgrößenregler in Form einer Übersicht zusammen. Kennzeichnen Sie, unter welchen Bedingungen die einzelnen Prinzipien anwendbar sind und für welche Entwurfsaufgaben sie besonders gut geeignet sind. Wie müssen die Entwurfsforderungen formuliert werden? Welche Art von Reglergesetzen entsteht?
2. Bewerten Sie anhand Ihrer Tabelle den Aufwand für den Entwurf der Regler und für deren Realisierung. Welche Verfahren sind praktikabel, wenn die Entwurfsforderung relativ schwach sind, welche, wenn es auf die Einhaltung exakter und bezüglich der Regelkreisdynamik sehr strenger Forderungen ankommt?
3. Welche Vor- und welche Nachteile haben die Entwurfsverfahren untereinander, wenn man die Art und Weise betrachtet, in der die Güteforderungen formuliert werden müssen, um mit den einzelnen Entwurfsverfahren berücksichtigt zu werden?
4. Unter welchen Bedingungen kann der Entwurf eines Mehrgrößenreglers auf den Entwurf mehrerer Eingrößenregler zurückgeführt werden?
5. Was ist eine dezentrale Regelung? Unter welchen Bedingungen muss sie verwendet werden? Wie kann man sie entwerfen?

---

### 1. Entwurfsprinzipien für Ein- und Mehrgrößenregler

| Entwurfsprinzip | Anwendbarkeit | Geeignet für | Entwurfsforderungen | Reglergesetze |
| :--- | :--- | :--- | :--- | :--- |
| **Klassisch (PID)** | SISO-Systeme, lineare LTI-Strecken, Prozesse mit geringer Ordnung und Totzeit. | Schneller und einfacher Entwurf, robuste Regelung. | Qualitative Vorgaben zu Stabilität und Dynamik (z.B. Phasen- und Amplitudenrand, Überschwingen, Anstiegszeit). | Empirisch (Ziegler-Nichols) oder durch Tuning optimierte PID-Regler. |
| **Polplatzierung** | LTI-Systeme, steuerbare Systeme, Zustandsraummodell notwendig. | Präzise Vorgabe der Dynamik (Eigenfrequenz, Dämpfung). | Quantitativ: Vorgabe der Polpositionen des geschlossenen Kreises. | Lineare Zustandsrückführung (u=-Kx). |
| **Optimal (LQR/LQG)** | LTI-Systeme, Zustandsraummodell notwendig. | Optimales Verhalten bezüglich eines Kostenfunktionsals (z.B. Minimierung von Energieverbrauch und Regelabweichung). | Quantitativ: Wahl der Gewichtungsmatrizen Q und R in einem quadratischen Kostenfunktional. | Lineare Zustandsrückführung, gegeben durch die Lösung einer Riccati-Gleichung. |
| **Robust (H_\infty)** | LTI-Systeme, Zustandsraum- oder Frequenzbereichsmodell. | Systeme mit Unsicherheiten und Störungen, garantiert Stabilität in Worst-Case-Szenarien. | Quantitativ: Obere Schranke für die Empfindlichkeit (z.B. ||S(s)||_\infty < \gamma). | Regler, die die Norm des Übertragungsfunktionals minimieren. |
| **Entkopplung** | MIMO-Systeme mit interagierenden Kanälen. | Entwurf von MIMO-Systemen als Satz von SISO-Systemen. | Entkopplung der Kanäle. | Vorfilter und/oder Rückkopplungsregler. |

***

### 2. Aufwand und Eignung der Verfahren

* **Klassisch (PID):**
    * **Entwurfsaufwand:** Gering. Basiert oft auf einfachen Regeln oder manuellem Tuning.
    * **Realisierungsaufwand:** Sehr gering. PID-Regler sind in der Praxis universell einsetzbar und in Standard-SPS oder Mikrocontrollern implementiert.
    * **Anwendung:** Praktikabel für schwache Anforderungen und wenn kein komplexes Modell der Regelstrecke vorliegt.

* **Polplatzierung/Optimal (LQR/LQG):**
    * **Entwurfsaufwand:** Hoch. Erfordert ein genaues Zustandsraummodell und komplexe Berechnungen.
    * **Realisierungsaufwand:** Mittel bis hoch. Erfordert die Messung oder Schätzung aller Zustandsvariablen (z.B. durch einen Beobachter).
    * **Anwendung:** Für sehr strenge Dynamikanforderungen (Polplatzierung) oder für Systemoptimierung (LQR) in hochpräzisen Anwendungen (z.B. Luft- und Raumfahrt).

* **Robust <img width="49" height="14" alt="image" src="https://github.com/user-attachments/assets/e9351ae3-6ff3-45d0-804f-f91bbd89c714" />**
    * **Entwurfsaufwand:** Sehr hoch. Mathematisch anspruchsvoll und erfordert spezielle Software.
    * **Realisierungsaufwand:** Hoch. Die Regler können eine hohe Ordnung haben, was komplex in der Implementierung ist.
    * **Anwendung:** Wenn die Robustheit im Vordergrund steht und die Modellunsicherheiten groß sind (z.B. in der Robotik oder bei Prozessleitsystemen).

***

### 3. Vor- und Nachteile bei der Formulierung von Güteforderungen

* **Klassisch (Bode/Nyquist):**
    * **Vorteil:** Die Güteforderungen (z.B. Stabilitätsrand) können intuitiv und direkt im Bode-Diagramm formuliert und überprüft werden.
    * **Nachteil:** Qualitative Natur. Die Verbindung zwischen Frequenzbereichsvorgaben und zeitlicher Antwort ist nicht immer direkt ersichtlich.

* **Polplatzierung:**
    * **Vorteil:** Güteforderungen wie Anstiegszeit und Dämpfung können direkt in die Polpositionen übersetzt werden.
    * **Nachteil:** Es gibt keine direkte Möglichkeit, Robustheit gegenüber Unsicherheiten zu berücksichtigen. Ein großer Abstand zur imaginären Achse kann die Empfindlichkeit erhöhen.

* **Optimal/Robust:**
    * **Vorteil:** Güteforderungen (z.B. Energieverbrauch vs. Regelabweichung) können direkt in einen mathematischen Optimierungs- oder Minimierungsprozess überführt werden.
    * **Nachteil:** Die Wahl der Gewichtungsmatrizen (Q, R) in LQR oder des \gamma-Werts in H_\infty kann schwierig und nicht-intuitiv sein.

***

### 4. Entwurf von MIMO-Systemen durch SISO-Regler

Ein Mehrgrößenregler kann auf den Entwurf mehrerer Eingrößenregler zurückgeführt werden, wenn das System **statisch oder dynamisch entkoppelt** werden kann.

* **Entkopplung:** Das Ziel ist, die Eingangs- und Ausgangskanäle so zu transformieren, dass jede Eingangsgröße nur eine einzige Ausgangsgröße beeinflusst.
    * **Voraussetzung:** Die **Entkopplungsmatrix** des Systems muss invertierbar sein.
    * **Vorgehen:** Ein **Vorfilter** oder ein **Rückkopplungsregler** wird entworfen, der die Wechselwirkungen zwischen den Kanälen aufhebt. Sobald das System entkoppelt ist, kann jeder entkoppelte Kanal mit einem separaten SISO-Regler (z.B. einem PID-Regler) geregelt werden.

***

### 5. Dezentrale Regelung

* **Definition:** Eine dezentrale Regelung liegt vor, wenn ein Mehrgrößensystem durch eine Reihe von unabhängigen **SISO-Reglern** geregelt wird, wobei jeder Regler nur eine einzelne Eingangsgröße und eine einzelne Ausgangsgröße verwendet. .
* **Bedingungen:** Dezentrale Regelung muss verwendet werden, wenn die **Wechselwirkungen zwischen den Kanälen gering** sind. Wenn die Wechselwirkungen zu stark sind, kann der dezentrale Regler das System instabil machen.
* **Entwurf:**
    1.  **Paarung der Kanäle:** Wählen Sie die Eingangs- und Ausgangsgrößen, die am stärksten miteinander interagieren.
    2.  **Einzelregler-Entwurf:** Entwerfen Sie für jedes gekoppelte Paar einen separaten SISO-Regler (z.B. einen PID-Regler) unter der Annahme, dass die anderen Kanäle geschlossen sind.
    3.  **Stabilitätsprüfung:** Überprüfen Sie die Stabilität des gesamten dezentral geregelten Systems. Oft wird dafür das **Relativ-Gain-Array (RGA)** als Hilfsmittel verwendet.
 
 ---

1. Welche prinzipiellen Unterschiede bestehen zwischen einer kontinuierlichen und einer zeitdiskreten Regelung?
2. Bringt die Abtastung Vereinfachungen oder zusätzliche Schwierigkeiten für den Entwurf und die Realisierung einer Regelung?
3. Welche Gesichtspunkte sind für die Wahl der Abtastzeit maßgebend?
4. Wann kann eine kontinuierliche Regelung ohne Probleme als zeitdiskrete Regelung eingesetzt werden?

---

### 1. Prinzipielle Unterschiede zwischen kontinuierlicher und zeitdiskreter Regelung

Der grundlegende Unterschied zwischen kontinuierlicher und zeitdiskreter Regelung liegt in der Art und Weise, wie die Signale verarbeitet werden.

* **Kontinuierliche Regelung:** Alle Signale sind kontinuierlich in der Zeit. Die Regelung erfolgt zu jedem Zeitpunkt. Sie wird durch Differentialgleichungen im Zeitbereich und durch die Laplace-Transformation im Frequenzbereich beschrieben. .
* **Zeitdiskrete Regelung:** Die Signale werden nur zu bestimmten Zeitpunkten, den **Abtastzeitpunkten**, erfasst und verarbeitet. Zwischen diesen Zeitpunkten bleiben die Signale konstant. Die Regelung wird durch Differenzengleichungen im Zeitbereich und durch die **z-Transformation** im Frequenzbereich beschrieben. Die Umsetzung erfolgt häufig in digitalen Systemen wie Mikrocontrollern oder Computern.

---

### 2. Vereinfachungen und zusätzliche Schwierigkeiten durch die Abtastung

Die Abtastung bringt sowohl Vor- als auch Nachteile mit sich:

* **Vereinfachungen:**
    * **Flexibilität:** Digitale Regler können einfach durch Softwareänderungen angepasst werden, ohne die Hardware zu modifizieren.
    * **Kosteneffizienz:** Digitale Systeme sind oft kostengünstiger als analoge.
    * **Komplexität:** Es können komplexere Regelungsalgorithmen implementiert werden, die in der analogen Domäne nur schwer oder gar nicht realisierbar wären.

* **Zusätzliche Schwierigkeiten:**
    * **Abtasteffekte:** Die Abtastung kann zu Informationsverlust und sogenannten **Aliasing-Effekten** führen, bei denen hochfrequente Signale als niederfrequente Signale interpretiert werden. .
    * **Abtastzeit:** Die Wahl der richtigen Abtastzeit ist kritisch und kann das Systemverhalten stark beeinflussen.
    * **Zusätzliche Totzeit:** Die Rechenzeit des Reglers fügt dem Regelkreis eine zusätzliche Totzeit hinzu, die die Stabilität beeinträchtigen kann.
    * **Modellierung:** Die Modelle von zeitdiskreten Systemen sind in der Regel komplexer, da sie die Abtastung mitberücksichtigen müssen.

---

### 3. Gesichtspunkte für die Wahl der Abtastzeit

Die Wahl der Abtastzeit (T_a) ist ein zentraler Kompromiss im Entwurf und wird von folgenden Gesichtspunkten bestimmt:

* **Abtasttheorem nach Shannon-Nyquist:** Die **Abtastfrequenz** (f_s = 1/T_a) muss mindestens **doppelt so hoch** sein wie die höchste im Eingangssignal enthaltene Frequenz (f_{max}). Eine noch höhere Abtastfrequenz (z.B. das 5- bis 10-fache) wird empfohlen, um Aliasing und Informationsverlust zu vermeiden.
* **Systemdynamik:** Die Abtastzeit sollte deutlich kürzer sein als die **kleinste relevante Zeitkonstante** des Systems. Eine zu lange Abtastzeit kann dazu führen, dass wichtige dynamische Informationen zwischen den Abtastzeitpunkten verloren gehen, was die Reglergüte beeinträchtigt.
* **Regler- und Systemverzögerung:** Die Rechenzeit des Reglers und die Totzeit im Regelkreis müssen berücksichtigt werden, da sie die Stabilität negativ beeinflussen können. Eine kürzere Abtastzeit kann diese Totzeit reduzieren.
* **Kosten und Rechenleistung:** Eine zu kurze Abtastzeit erfordert eine höhere Rechenleistung und schnellere Prozessoren, was die Kosten und den Energieverbrauch erhöht.

---

### 4. Einsatz einer kontinuierlichen Regelung als zeitdiskrete Regelung

Eine kontinuierliche Regelung kann nur dann ohne größere Probleme als zeitdiskrete Regelung eingesetzt werden, wenn folgende Bedingungen erfüllt sind:

* **Kurze Abtastzeit:** Die Abtastzeit muss **sehr viel kleiner** sein als die kleinste signifikante Zeitkonstante des Systems (Faustregel: 1/10 oder kleiner).
* **Ausreichende Rechenleistung:** Der Digitalregler muss in der Lage sein, die notwendigen Berechnungen innerhalb der Abtastzeit durchzuführen.
* **Analoge Komponenten:** Die Systemkomponenten, die die eigentliche Regelung ausführen (z.B. Motor, Ventil), müssen in der Lage sein, dem digitalen Signal zu folgen.
* **Fehlen von Totzeit und Totzeitapproximation:** Das System hat keine oder eine vernachlässigbar kleine Totzeit. Die digitale Regelung darf keine zusätzliche, signifikante Totzeit einführen.

Unter diesen Bedingungen kann das zeitdiskrete System das kontinuierliche System sehr gut annähern, und die klassischen Entwurfsmethoden für kontinuierliche Systeme können mit relativ geringen Anpassungen verwendet werden.
