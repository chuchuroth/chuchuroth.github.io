---
layout: post
title:  "Stromlaufplan"
date:   2025-08-06
categories: jekyll update
---


Natürlich! Hier ist eine **Schritt-für-Schritt-Anleitung zur Analyse eines Stromlaufplans (Schaltplans)** sowie ein **Beispiel** eines typischen Stromlaufplans aus dem Bereich Automatisierung/Steuerungstechnik.

---

## ✅ **Was ist ein Stromlaufplan?**

Ein Stromlaufplan (auch: **Schaltplan**) ist eine technische Zeichnung, die den elektrischen Aufbau einer Schaltung zeigt – also wie **Komponenten elektrisch miteinander verbunden** sind (z. B. Sensoren, Schütze, Taster, Motoren, SPS, etc.).

---

## 🔍 **Schritt-für-Schritt Anleitung zur Analyse eines Stromlaufplans**

---

### **1. Legende & Symbolverständnis**
1. 图例与符号理解  
* Schau dir die **Legende** an: Dort sind alle Symbole erklärt (z. B. Schützspule, Öffner, Schließer, Taster, Motor, Sicherung).
查看图例：所有符号在这里都有解释（比如接触器线圈、常开/常闭触点、按钮、电机、保险丝）。  
* Vergewissere dich, dass du die **Normsymbole nach DIN EN 60617** (ehem. DIN 40700) verstehst.
确认你理解根据DIN EN 60617（原DIN 40700）标准的规范符号。

---

### **2. Hauptspannung & Steuerstromkreis identifizieren**
2. 主电源与控制回路识别 
* **Hauptstromkreis** (z. B. 400V 3\~): Enthält Leistungsteile wie Sicherungen, Schütze, Motoren.
主回路（如400V三相）：包含功率元件，如保险、接触器、电机等。  
* **Steuerstromkreis** (z. B. 24VDC oder 230VAC): Enthält Taster, Relais, SPS-Eingänge/Ausgänge.
控制回路（如24VDC或230VAC）：包含按钮、继电器、PLC输入/输出等。

---

### **3. Energiezuführung & Schutzgeräte finden**
3. 查找电源引入点和保护装置 
* Starte beim **Einspeisepunkt**: Netzanschluss, Hauptschalter, Sicherungen.
从进线点开始：接线电源、主开关、保险丝。 
* Achte auf **Schutzgeräte**: Leitungsschutzschalter, FI-Schalter, Motorschutzschalter.
注意保护装置：断路器、漏电保护、马达保护器等。

---

### **4. Verbraucher lokalisieren**
4. 定位负载  
* Erkenne alle Endverbraucher: z. B. Motoren, Magnetventile, Lampen, Hupen, etc.
识别所有终端负载：如电机、电磁阀、灯、蜂鸣器等。  
* Prüfe, wie sie angesteuert werden (direkt, über Schütze, über SPS-Ausgänge).
检查它们是如何被控制的（直接、通过接触器或PLC输出）。

---

### **5. Steuergeräte & Logik analysieren**
5. 分析控制装置与逻辑 
* Schaue, welche **Schaltlogik** verwendet wird: z. B. Start/Stop-Schaltung mit Selbsthaltung.
查看使用了什么控制逻辑：如带自锁的启动/停止回路。  
* Prüfe, ob **Relais, Schütze oder SPS** zur Steuerung genutzt werden.
检查控制方式是继电器、接触器还是PLC。

---

### **6. Sicherheitseinrichtungen erkennen**
6. 识别安全装置  
* **NOT-AUS, Türschalter, Lichtschranken** etc. sind meist als Öffner dargestellt.
急停、门开关、光电开关等多数以常闭符号表示。  
* Prüfe, ob sie **sicherheitsgerichtet** verdrahtet sind (z. B. in Reihe).
检查它们是否安全接线（如串联）。

---

### **7. SPS-Einbindung prüfen**
7. 检查PLC接入方式  
* Erkenne Eingänge (z. B. Sensoren, Taster) und Ausgänge (z. B. Schütze, Relais).
识别输入（如传感器、按钮）和输出（如接触器、继电器）。 
* Beachte Adressierung wie **I0.0 / Q0.0** (Siemens) oder **%I0.0 / %Q0.0** (IEC-Notation).
注意地址标识，如I0.0 / Q0.0（西门子）或%I0.0 / %Q0.0（IEC标记）。

---

### **8. Drahtnummern & Querverweise lesen**
8. 阅读导线编号与跳线  
* Prüfe **Querverweise**, wenn Stromlaufplan über mehrere Seiten geht.
如果电路图跨多页，需查阅跳线编号。  
* **Drahtnummern** helfen bei Verdrahtung und Fehlersuche.
导线编号有助于接线和故障排查。

---

### **9. Klemmleisten und externe Anschlüsse**
9. 端子排和外部接线  
* Prüfe, welche Signale an **Klemmen** nach außen geführt werden (Sensorleitungen, Motoranschlüsse etc.).
检查从端子排引出的信号（如传感器线、电机接线等）。  
* Unterscheide zwischen interner Verdrahtung und **Feldverkabelung**.
区分内部接线和现场布线。

---

## 📘 **Beispiel: Vereinfachter Stromlaufplan einer Start-Stopp-Motorsteuerung**

```
-------------------------- Hauptstromkreis --------------------------
L1 ──┬────[F1]──────[K1]──────(M)─────┐
     │                              │
    (N)                            PE
     │
-------------------------- Steuerstromkreis -------------------------
L ───[F2]───┬───[S1] Start ─────┬────[K1 Spule]─────── N
            │                   │
            └───[S0] Stop───────┘
                          ↓
                  Selbsthaltung über K1 (Schließer)
```

### **Legende:**

* **F1 / F2** = Sicherung
* **S0** = Not-Aus / Stop (Öffner)
* **S1** = Start-Taster (Schließer)
* **K1** = Schütz (mit Hilfskontakt zur Selbsthaltung)
* **M** = Motor

### **Analyse:**

* Beim Drücken von **S1** zieht **K1** an → Motor startet.
* Selbsthaltung hält K1, auch wenn S1 losgelassen wird.
* Drücken von **S0** unterbricht Steuerstrom → Motor stoppt.

---

## 🧰 Typische Fehlerquellen & Diagnosetipps

| Fehler                    | Ursache                             | Testmethode                 | Lösung                    |
| ------------------------- | ----------------------------------- | --------------------------- | ------------------------- |
| Schütz zieht nicht an     | Keine Spannung an Spule             | Spannung messen an K1-A1/A2 | Taster defekt, Drahtbruch |
| Motor läuft nicht         | Schütz schaltet nicht durch         | Schützkontakte prüfen       | Schütz ersetzen           |
| SPS reagiert nicht        | Falsche Verdrahtung, Adresse falsch | SPS-Monitor prüfen          | Verdrahtung korrigieren   |
| NOT-AUS deaktiviert alles | Öffner geöffnet                     | Durchgang messen            | Schalter überprüfen       |

---

## 📂 Möchtest du einen echten Stromlaufplan als Datei (PDF, AutoCAD oder Bild)?

Ich kann dir ein Beispiel **zeichnen und zuschicken** oder dir helfen, einen eigenen Plan zu erstellen. Sag mir einfach:

* Für welche Anwendung (z. B. Förderband, Pumpe, Roboter)?
* Welche Spannung (230V/400V)?
* Mit oder ohne SPS?

Dann erstelle ich dir ein echtes Planbeispiel!


---

Absolutely. Let's break this into **three parts**:

---

## ✅ PART 1: Example – Electric Circuit Design for a Control Panel (Small Factory)

### ⚙️ **Application Overview:**

Let’s assume the control panel is for a **small bottling line** in a food production facility. It includes:

* Conveyor motors (3-phase)
* Bottle filling machine
* Bottle capping machine
* Sensors (photoelectric, level)
* Emergency stop circuit
* HMI and PLC-based control (Siemens S7-1200)
* Basic VFD for speed control
* 24VDC control logic

---

### 🗂️ **Main Components in the Panel:**

* **Main Circuit Breaker** (3P MCCB 63A)
* **Contactor + Overload Relays** (for each motor)
* **VFD** (for main conveyor motor)
* **24VDC Power Supply** (for PLC, sensors, relays)
* **PLC** – Siemens S7-1200 + Digital I/O modules
* **HMI** – 7” touchscreen
* **Mains-to-Control Transformer** (if needed)
* **Terminal Blocks, Relays, Push Buttons, Selector Switches, Indicator Lamps**
* **Emergency Stop Mushroom Buttons**
* **Circuit Breakers (MCBs)** – for segmented protection

---

### 🖉 **Basic Wiring Overview (Simplified Diagram Description):**

#### ➤ **Power Circuit:**

```
3-Phase Supply (L1, L2, L3) ──> MCCB ──> Contactor ──> Overload ──> Motor
                                   └──> VFD ──> Motor
```

#### ➤ **Control Circuit:**

```
24VDC Power Supply ──> PLC Digital Inputs/Outputs ──> Relays ──> Contactor Coils
                         └──> Sensors, HMI, Indicator Lights
                         └──> E-Stop Circuit ──> Safety Relay ──> Enable Control Loop
```

#### ➤ **Emergency Stop Circuit (Safety Loop):**

```
E-Stop Buttons (NC) ──> Safety Relay ──> Contactor Enable
```

*All components are grounded properly, and shielded cables used for analog/sensor signals.*

---

## ⚠️ PART 2: Common Electrical & Control Failures (from real field experience)

### 1. **Contactor Coil Not Energizing**

* **Cause:** Blown fuse, loose control wire, coil burnout, or PLC output not functioning.
* **How to Test:**

  * Measure 24VDC at the coil terminals.
  * Check continuity of coil.
  * Test PLC output using force/test mode.
* **Fix:** Replace coil/fuse, fix wiring, or use spare PLC output.

---

### 2. **Motor Not Starting / Tripping**

* **Cause:** Overload relay tripped, phase loss, or incorrect VFD parameters.
* **How to Test:**

  * Check overload status.
  * Measure phase voltage.
  * Check VFD fault code.
* **Fix:** Reset overload, fix power supply issue, correct VFD config (e.g., acceleration time, torque limits).

---

### 3. **PLC Not Powering On**

* **Cause:** 24V power supply failure, short circuit in field devices.
* **How to Test:**

  * Measure 24VDC at the power supply.
  * Disconnect field loads and check again.
* **Fix:** Replace shorted device, check PSU loading.

---

### 4. **Sensor Not Detecting / False Signals**

* **Cause:** Dirty lens, incorrect alignment, or electrical noise.
* **How to Test:**

  * Clean sensor, realign, check with handheld tester.
  * Use scope to observe signal integrity.
* **Fix:** Replace sensor, add shielding or filter capacitor.

---

### 5. **PLC I/O Failure**

* **Cause:** Overvoltage, reverse polarity, short circuit.
* **How to Test:**

  * Use test mode to toggle I/O.
  * Measure current draw.
* **Fix:** Replace damaged module, add fuse/diode protection.

---

## 🧪 PART 3: How to Test & Diagnose

| Test                           | Purpose                              | Tool Needed                |
| ------------------------------ | ------------------------------------ | -------------------------- |
| **Multimeter Test**            | Voltage, continuity, coil resistance | Digital Multimeter         |
| **Insulation Resistance Test** | Detect wire degradation              | Megger (Insulation Tester) |
| **Current Measurement**        | Check motor current, overload        | Clamp Meter                |
| **PLC Diagnostic Mode**        | Check I/O and faults                 | TIA Portal / RSLogix       |
| **Visual Inspection**          | Loose wires, burnt components        | Flashlight, hand tools     |
| **Thermal Camera (optional)**  | Detect overheating                   | Thermal imaging camera     |

---

If you'd like, I can also create a **proper schematic diagram** (PDF or image) of the electric circuit using tools like AutoCAD or EPLAN-style layout. Just let me know the specifics or upload your reference design.

Would you like to see a drawn version of this control panel wiring?


---

Certainly! Here's a **short introduction** to each of the listed electrical documents commonly used in industrial settings, followed by **additional documents** that are also standard in professional practice.

---

## 📘 **Introduction to Common Electrical Documents in Industrial Settings**

1. ### **Single Line Diagrams (SLDs)**

   * **Purpose:** Provide a simplified overview of the power distribution system using **single lines to represent all three phases**.
   * **Usage:** Used by engineers and electricians to understand the **flow of power** from incoming supply through switchgear, transformers, panels, and major loads.

2. ### **Wiring Diagrams**

   * **Purpose:** Show **physical connections** and wire routes between components.
   * **Usage:** Helpful for **installation and troubleshooting**, showing terminal numbers, wire colors, and actual wiring paths.

3. ### **Schematic Diagrams**

   * **Purpose:** Represent the **logical function** and interaction of electrical components.
   * **Usage:** Focused on **function rather than layout**, used for designing and understanding control systems.

4. ### **Ladder Diagrams**

   * **Purpose:** Show control logic using **relay-ladder logic**, commonly used in PLC programming.
   * **Usage:** Widely used by control engineers to design **sequential control logic** and debug systems in automation.

5. ### **Floor Plans**

   * **Purpose:** Show the **physical location** of electrical equipment (e.g., panels, machines) within the building.
   * **Usage:** Useful for electricians, planners, and maintenance staff for installation planning and space allocation.

6. ### **Site Plans**

   * **Purpose:** Present a **broad overview** of the facility, including outdoor infrastructure, cable trenches, substations, and utility access.
   * **Usage:** Used during construction and utility planning for **site-wide coordination** of services.

---

## 🧾 **Other Common Industry-Used Documents**

1. ### **Panel Layout Drawings**

   * Show internal layout of control cabinets, including DIN rail components, terminal blocks, wiring ducts, and spacing.

2. ### **Cable Schedules**

   * Lists all cables with details such as type, size, route, and terminations.

3. ### **Loop Diagrams**

   * Used primarily in process industries, show the signal path from instrument to control system and back.

4. ### **Bill of Materials (BOM)**

   * Lists all electrical components used in a project with quantities, part numbers, and specs.

5. ### **Load Schedules / Load Lists**

   * Provide detailed information on connected electrical loads, used for sizing breakers, panels, and transformers.

6. ### **I/O Lists**

   * Show PLC input/output channel assignments and signal sources/destinations.

7. ### **Functional Design Specifications (FDS)**

   * Describe the control philosophy, sequence of operations, and functional behavior of automated systems.

8. ### **Test & Commissioning Protocols**

   * Procedures and checklists used during electrical system startup and verification.

9. ### **Risk Assessments & Safety Compliance Reports**

   * Especially for high-risk systems or when safety standards (e.g. IEC 60204, ISO 13849) are applied.

---

## ✅ Summary

While your list covers the **core electrical drawing types**, industrial projects often require additional documents for **installation**, **commissioning**, **compliance**, and **maintenance**. These collectively ensure that systems are **safe, functional, and maintainable** across the entire equipment lifecycle.

Let me know if you want templates or examples of any specific document!




