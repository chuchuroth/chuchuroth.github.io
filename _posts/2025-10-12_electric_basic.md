---
layout: post
title:  "electric_basic"
date:   2025-10-12
categories: jekyll update
---


This response draws together all the knowledgeable information, know-how, and industry practices detailed across the provided video transcripts.

---

### I. Foundational Concepts of Electricity and Atomic Structure

*   **The Big Four Properties:** The entire industry and the operation of anything electrical or electronic are driven by four critical properties: **voltage, current, resistance, and power**.
*   **Matter and Charge:** Matter is anything that occupies space and has weight. The basic building block of matter is the **element**.
    *   **Atom Structure:** Protons (positively charged) and neutrons (neutrally charged) reside in the nucleus. Electrons (negatively charged) orbit the nucleus. Electronics is primarily the study of the behavior of the electron.
    *   **Ions:** Energy applied to neutral matter (equal protons and electrons) can knock electrons off the valence shell (ionization). Removing electrons creates a positive ion; gaining them creates a negative ion. Separated ions and electrons seek to return to a neutral state, and this movement is harnessed as electricity.
*   **Current (I):** The flow or movement of electrons from negative to positive atoms.
    *   **Units:** The **Coulomb (C)** is the unit of charge, equal to $6.24 \times 10^{18}$ electrons. The **Ampere (A)** is the unit of current, defined as 1 Coulomb per second ($I = Q/T$).
    *   **Speed:** Current travels through a conductor virtually instantaneously, near the speed of light (186,000 miles per second).
*   **Voltage (V or E):** The force or pressure that moves electrons in a circuit. The source of electrical potential.
    *   **Voltage Rise/Drop (KVL):** The voltage supplied by the source (Rise) must equal the voltage consumed by the loads (Drop); the algebraic sum of voltages in a closed loop is zero.
*   **Resistance (R):** The opposition to electron flow, measured in Ohms ($\Omega$). Every material has resistance, except for superconductors.
*   **Power (P):** The rate at which work is done. Power is the product of current and voltage ($P = I \times V$). Power is **always additive** in any circuit configuration. Measured in Watts (W), while utility companies charge in kilowatt hours (kWh).
*   **Proportionality:** Current flow is directly proportional to voltage and inversely proportional to resistance.

### II. Materials and Conduction Know-How

*   **Conductors:** Have three or fewer valence electrons. Silver is the best conductor. Copper is most common. Gold is used for plating contacts to prevent corrosion (oxidation).
*   **Insulators:** Have five or more valence electrons. Micah is the best natural insulator. Pure water is an insulator, but impurities make it conductive.
*   **Semiconductors:** Have exactly four valence electrons. Key materials are Silicon, Germanium, and Carbon. Silicon is most commonly used in solid-state devices.
    *   **Temperature Effect:** Semiconductor resistance decreases as temperature increases (negative temperature coefficient). Heat dissipation is critical; dust buildup must be cleaned.
*   **Superconductors:** Materials (like certain Ceramics) that exhibit zero resistance at cryogenic temperatures.

### III. DC Circuit Analysis and Design

*   **Circuit Requirements:** A functional circuit must have a **voltage source**, a **load**, and a **conductor**. Optional but common components include a controlling device (switch) and a protective device (fuse).
*   **Series Circuits:** Known as a **voltage divider**. Current is constant throughout. Resistance is calculated by simply adding individual resistances ($R_T = R_1 + R_2 + R_3...$).
*   **Parallel Circuits:** Known as a **current divider**. Voltage is constant across all branches. Total resistance is calculated using the reciprocal formula (or product over sum for two resistors: $R_T = (R_1 \times R_2) / (R_1 + R_2)$). The total resistance is always less than the value of the smallest resistor.
*   **Troubleshooting Strategy:** Always refer back to the basic circuit parts (Source, Load, Conductor, Control, Protective Device). If KVL fails (Voltage Rise $\neq$ Voltage Drop), the missing voltage drop indicates the location of the fault.
*   **Loaded Voltage Divider Design:** When designing a series circuit to provide fixed voltage output points (loaded voltage divider), the **bleeder current** (current through the first resistor) should be $1/10^{th}$ of the total load current to maintain circuit stability.

### IV. Generating and Harnessing Electrical Energy

*   **Six Methods of Generation:** Electricity can be produced by friction, magnetism (most common), chemicals, light, heat, and pressure.
*   **Magnetism and Generators:** Electromagnetic induction (turning a conductor through a magnetic field) is the primary method.
    *   **AC Generator:** Uses **slip rings** to collect the full $360^\circ$ cycle, producing a sinusoidal waveform.
    *   **DC Generator:** Uses a **commutator** to collect only the positive $180^\circ$ alternation, producing pulsating DC.
*   **Batteries (Chemical Cells):** Lead-acid batteries (secondary/rechargeable) are widely used for automotive, solar, and essential backup power systems (e.g., telephone lines, control centers).
*   **Electromagnetic Applications:**
    *   **Relay:** An electromagnetic switch used to electrically isolate two circuits and allow a low-power circuit to control a high-power circuit (e.g., pilot control lighting at airports).
    *   **Solenoid:** A coil that pulls a plunger to perform mechanical work (e.g., pinball flippers, door chimes).

### V. AC Theory and Reactive Components

*   **AC Fundamentals:** AC power alternates (shakes back and forth) at a specific frequency (e.g., $60 \text{ Hz}$ in North America).
    *   **Sinusoidal Waveform (Sine Wave):** Can be analyzed mathematically using the trigonometric sine function ($V_{inst} = V_{peak} \times \sin(\theta)$).
    *   **Effective Value (RMS):** The Root Mean Square value is the DC equivalent value that produces the same heat/effect in a resistive load. $V_{RMS} = V_{Peak} \times 0.707$. Unless otherwise specified, AC voltage values are assumed to be RMS.
*   **Inductors (L):** Devices that oppose a change in current flow by storing energy in a **magnetic field** (electromagnetic).
    *   **Lenz's Law:** The induced voltage (CEMF) opposes the applied voltage.
    *   **Phase Shift (ELI):** In a purely inductive circuit, Voltage (E) **leads** Current (I) by $\mathbf{90^\circ}$ (ELI).
    *   **Inductive Reactance ($X_L$):** Opposition to AC current, measured in Ohms. $X_L = 2 \pi f L$. $X_L$ is directly proportional to frequency (f).
*   **Capacitors (C):** Devices that store electrical energy in an **electrostatic field**. They give the appearance of current flowing through an insulator as they charge and discharge.
    *   **Phase Shift (ICE):** In a purely capacitive circuit, Current (I) **leads** Voltage (V) by $\mathbf{90^\circ}$ (ICE).
    *   **Capacitive Reactance ($X_C$):** Opposition to AC current, measured in Ohms. $X_C = 1 / (2 \pi f C)$. $X_C$ is inversely proportional to frequency (f) and capacitance (C).
*   **Impedance (Z):** The total opposition to AC current, combining both resistance (R) and reactance ($X_L$ or $X_C$).
*   **Resonance:** Occurs when $X_L = X_C$, causing them to cancel out (due to $180^\circ$ phase difference), leaving only resistance (R) in the circuit.
*   **Filter Circuits (RL/RC):** Used to discriminate (attenuate) specific frequencies.
    *   **Low Pass Filter:** Passes low frequencies; output is taken across the parallel capacitor (RC) or parallel resistor (RL).
    *   **High Pass Filter:** Passes high frequencies; output is taken across the parallel resistor (RC) or parallel inductor (RL).

### VI. Transformers

*   **Function:** Transfers AC energy using electromagnetic induction. Provides electrical isolation.
*   **Ratings:** Rated in **Volt Amperes (VA)**.
*   **Step Up/Down:** Determined by the turns ratio (secondary turns / primary turns). Power companies step up voltage for transmission (to minimize current and use smaller conductors) and step it down for distribution.
*   **Applications:** Essential for electrical **isolation** (safety and fault protection), voltage conversion, and **impedance matching** (critical for maximum power transfer).

### VII. Semiconductor Devices and Applications

*   **PN Junction Diodes:** A solid-state check valve allowing current to flow only one way.
    *   **Forward Bias:** Allows current flow when external voltage exceeds the barrier voltage (approx. $0.7 \text{ V}$ for Silicon).
    *   **Reverse Bias:** Blocks current flow by expanding the depletion region. Can be destroyed by excessive reverse voltage.
*   **Transistors (BJTs/FETs):** Used primarily as a high-speed **switch** or an **amplifier** (a small voltage change at the input controls a large current change at the output).
*   **Thyristors (SCRs/TRIACs):** High-power semiconductor switches. TRIACs are bi-directional and used for AC control (up to $25 \text{ A}$). SCRs are uni-directional and handle much higher currents (up to $1400 \text{ A}$).
*   **Amplifier Configurations:**
    *   **Common Emitter:** Most common; provides **$180^\circ$ phase inversion**.
    *   **Common Collector:** Used for impedance matching.
*   **Operational Amplifiers (Op Amps):** High gain DC amplifiers (up to 1 million times input). Used in closed-loop configurations with feedback for stability.

### VIII. Digital and Computer Architecture

*   **Binary and Hexadecimal:** Digital systems rely on binary (base 2, 0 or 1). Hexadecimal (base 16) is commonly used in computing to efficiently utilize 4-bit combinations.
*   **Memory:** Built from flip-flops. RAM is volatile (temporary storage); ROM is non-volatile (permanent storage/firmware). EEPROM (Electrically Erasable PROM) allows for convenient, in-system firmware updates.
*   **Microcomputers:** Consist of five basic functional blocks: **Control, ALU (Arithmetic Logic Unit), Memory, Input, and Output**. The ALU performs all math and logic operations.

### IX. Industry Practices and Test Equipment Know-How

*   **Study and Professional Practice:** Success requires following a disciplined study protocol (reading, reviewing, doing problems). Long-term success is measured by the application of knowledge in industry. Emphasized topics in lecture are likely to appear in industry.
*   **Engineering Notation:** Essential for handling extreme numbers (powers of $10^{\pm 3}, 10^{\pm 6}, 10^{\pm 9}, \text{etc.}$) common in electronics.
*   **Multimeter Use (Know-How):** DMMs are typically used for field service, while analog meters are for bench work. Always inspect leads for damage. To measure current, the meter must be connected in **series** (breaking the circuit). To measure voltage, the meter must be connected in **parallel**.
*   **AC Measurement Limits:** DMMs are generally only accurate for AC voltage and current up to approximately $1,000 \text{ Hz}$. Above this, use an **oscilloscope**.
*   **Oscilloscope Use (Know-How):** Provides a visual display of the signal waveform. Key to stability is proper **triggering** (e.g., automatic internal triggering). Use a specific checklist for control settings (X, Y, Z axes, Trigger). Set intensity low to prevent burning the screen.
*   **Transistor/Diode Testing:** Use an analog ohm meter for forward/reverse resistance ratios. A DMM's diode test feature displays the barrier voltage. Thermal failure is common; use freeze spray to diagnose heat-related component faults.
*   **ESD Protection:** MOSFETs are highly sensitive to Electrostatic Discharge (ESD). Technicians must use proper grounding protocols (wrist/heel straps, grounded iron).

---
---
---
下面按**类别**列举一些**常用的电子元器件**，适合电子基础学习、电路设计和维修参考：

---

## 一、被动元器件

### 1. 电阻器

* 固定电阻
* 可变电阻（电位器）
* 热敏电阻（NTC / PTC）
* 光敏电阻
* 精密电阻
* 功率电阻

### 2. 电容器

* 陶瓷电容
* 电解电容（铝电解、钽电解）
* 薄膜电容（聚酯、聚丙烯）
* 可变电容
* 安规电容（X2、Y2）

### 3. 电感器

* 绕线电感
* 功率电感
* 共模电感
* 磁珠

---

## 二、半导体器件

### 4. 二极管

* 整流二极管
* 稳压二极管（齐纳二极管）
* 肖特基二极管
* 发光二极管（LED）
* 光电二极管

### 5. 晶体管

* 双极型晶体管（BJT：NPN、PNP）
* 场效应管（MOSFET：NMOS、PMOS）
* 结型场效应管（JFET）

---

## 三、集成电路（IC）

### 6. 模拟 IC

* 运算放大器（如 LM358、OPA 系列）
* 比较器
* 稳压芯片（7805、LM317、LDO）

### 7. 数字 IC

* 逻辑门电路（74HC 系列）
* 计数器、移位寄存器
* 存储器（EEPROM、Flash、RAM）

### 8. 微控制器 / 处理器

* 单片机（51、STM32、AVR、PIC）
* SoC 芯片

---

## 四、机电与接口器件

### 9. 继电器与开关

* 电磁继电器
* 固态继电器
* 按键开关
* 拨动开关
* 旋转开关

### 10. 连接与接口

* 排针 / 排母
* USB 接口
* HDMI / RJ45 接口
* 接线端子
* 插座

---

## 五、传感与显示器件

### 11. 传感器

* 温度传感器（DS18B20、NTC）
* 湿度传感器
* 光敏传感器
* 压力传感器
* 霍尔传感器

### 12. 显示与指示

* 数码管
* LCD 显示屏
* OLED 显示屏
* 指示灯

---

## 六、电源与保护器件

### 13. 电源相关

* 变压器
* 开关电源模块
* DC-DC 模块

### 14. 保护器件

* 保险丝
* TVS 二极管
* 压敏电阻
* 防反接二极管

---

如果你愿意，我也可以：

* 📘 按**入门学习清单**推荐元器件
* 🔧 按**电路功能**分类（电源、放大、驱动等）
* 🧪 提供**常见元器件识别图和选型建议**

你可以告诉我你的使用场景（学习 / 项目 / 维修）。
