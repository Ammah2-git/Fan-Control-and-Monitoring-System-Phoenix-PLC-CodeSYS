# 🌀 DC Brushless Fan Control & Monitoring System (Phoenix PLC + CodeSYS)

This project implements a real-time **fan control and anomaly detection system** using a **DC brushless fan**, **Phoenix Contact PLC**, and **CodeSYS** programming. The system provides **PWM-based fan speed control**, **tachometer-based feedback**, and **ramping logic**, complete with a WebVisu HMI interface for visualization and control.

---

## 📦 Features

✅ PWM fan speed control (0–100%)  
✅ Speed ramping to target speed  
✅ Real-time RPM feedback using tachometer signal  
✅ WebVisu-based HMI with user input fields  
✅ Configurable ramp time and setpoints  
✅ Expandable for anomaly detection (future scope)

---

## 🔧 Hardware Specifications

### 🌀 Fan: `09225VE-24L-CU-02` (NMB Technologies)

| Parameter           | Value                  |
|---------------------|------------------------|
| Voltage Range       | 14.0 – 27.6 VDC        |
| Rated Voltage       | 24 VDC                 |
| Max Current         | 0.19 A                 |
| Speed (Nominal)     | 3700 RPM               |
| Max Airflow         | 63.6 CFM               |
| Bearing Type        | Ball Bearing           |
| Tachometer Output   | 2 pulses per revolution |
| PWM Input           | TTL-level control via brown wire |

📄 [Fan Datasheet](https://www.nmbtc.com/pdf/dcfans/09225VE-24L.pdf)

---

## 🛠️ System Architecture

```
[ HMI (WebVisu) ]
       ⇅
[ CodeSYS Ladder Logic ]
       ⇅
[ Phoenix PLC ]
   ↙       ↘
[ PWM Out ]   [ Tacho In ]
    ↓             ↑
[ DC Fan ]     [ RPM Feedback ]
```

---

## 💡 How It Works

1. **PWM Speed Control**  
   - The user sets a PWM duty cycle (0–100%) via HMI.  
   - PLC sends corresponding signal to the fan through PWM output.

2. **Speed Ramping**  
   - Timer-based logic ramps the fan smoothly to the desired speed over a configurable period.

3. **RPM Monitoring**  
   - Tacho signal (open collector) sends pulses to a digital input.  
   - RPM is calculated in real-time using pulse counting and shown on HMI.

4. **Optional: Anomaly Detection**  
   - Simulated fan faults (e.g., imbalance via blade cuts or added weight) can be detected using RPM irregularities.

---

## 🎛️ HMI Interface (WebVisu)

| Control        | Address  | Description                        |
|----------------|----------|------------------------------------|
| Start Button   | `%IX0.0` | Activates PWM and ramping logic    |
| Target PWM (%) | `%MW0`   | User-defined speed (0–100%)        |
| Ramp Time (ms) | `%MW1`   | Time between increments            |
| Current PWM    | `%MW2`   | System-calculated ramped value     |
| RPM Display    | `%MW3`   | Live feedback from tachometer      |

---

## 📁 Project Structure

```
Fan-Control-and-Monitoring-System/
├── PLC_Project/              # CodeSYS project files
│   └── LadderLogic.project
├── HMI_Design/               # WebVisu HMI screenshots and layout
│   └── hmi-layout.png
├── docs/
│   └── Fan-Datasheet.pdf
├── README.md
└── LICENSE
```

---

## 🔍 Use Case Example

This system is suitable for:  
- 🌡️ Thermal management in control panels  
- 📦 Embedded system cooling  
- 🏭 Industrial automation environments  
- 🔧 Educational labs for control systems  

---

## 🚀 Getting Started

### ✅ Requirements
- Phoenix PLC (with PWM support)
- CodeSYS software (with WebVisu runtime)
- DC Brushless Fan with PWM + Tacho
- Optional: Tacho-compatible digital input or high-speed counter

### 🔌 Wiring

| Wire Color | Function       |
|------------|----------------|
| Red        | +24V VDC       |
| Black      | GND            |
| Brown      | PWM input      |
| White      | Tacho output   |

---
## 🌟 Acknowledgements

- Phoenix Contact & CodeSYS documentation  
- NMB Technologies for the fan datasheet  
- Community references on PWM + tacho integration  

---

