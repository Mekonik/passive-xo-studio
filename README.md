# passive-xo-studio
Automated passive crossover designer &amp; tournament optimizer for DIY loudspeakers. Features FRD/ZMA import, datasheet graph image scanner, VituixCAD G(f) export, and BOM generator.


# 🎛️ Passive XO Studio Pro

**Passive XO Studio Pro** is a zero-dependency, browser-based passive crossover design suite and automated topology tournament optimizer for DIY loudspeaker builders and audio engineers. 

It bridges the gap between raw acoustic measurements (**.FRD** / **.ZMA** from REW or manufacturer datasheets) and a finished, ready-to-solder passive crossover—evaluating thousands (or millions) of mixed circuit topologies in seconds.

🔗 **[Live Web App Demo (GitHub Pages)](mekonik.github.io/passive-xo-studio/index.html)**
---

## ✨ Key Features

### 🟢 Dual Workflow: Easy Mode Wizard & Pro Studio
* **Easy Mode (Wizard):** A streamlined 3-step guided setup. Select your speaker configuration (1-, 2-, or 3-way), load your `.frd` and `.zma` files (or test with built-in demo drivers), set your maximum allowed component count (`1` to `14` or `Max`), and immediately get the **Top 5 ready-to-build crossover proposals**.
* **Pro Studio (VituixCAD-style Workbench):** Full manual and semi-automated control over every filter branch, target alignment, driver array configuration, acoustic Z-offset, and individual component value.

### ⚡ 3-Stage Tournament & "Unlimited" Live Optimizer
* **Stage 1 – Acoustic X-Ray:** Automatically scans raw driver curves in `< 1 ms` to detect cone breakup peaks ($f_{\text{breakup}}$) and tweeter fundamental impedance resonances ($f_s$).
* **Stage 2 – Analytical Physics Locking:** Pre-calculates exact resonant values for elliptic notches, shunt LCR traps, and impedance-compensating Zobel networks instead of relying on blind brute-force guessing.
* **Stage 3 – Smoothness, Stopband & Smart Pruning:** Optimizes for a smooth on-axis/off-axis response (penalizing 1st and 2nd derivative ripples and high-frequency stopband leakage) and automatically prunes redundant parts that contribute `< 0.15 dB` improvement.
* **♾️ Unlimited Live Crunch:** Let the optimizer run continuously in the background while watching the Top 5 leaderboard and frequency response update in real time until you click **Stop & Use Best**.

### 🧩 Unrestricted, Mixed Circuit Topologies
Unlike basic textbook calculators, the optimizer freely mixes and matches topologies across branches:
* **0th-Order to 4th-Order Ladders:** Including **0th-order woofer filters** (no series inductor—using only a shunt LCR or RC Zobel network to ground for zero DC series loss).
* **Pre- & Post-Filter Attenuation:** Series resistors ($R_{\text{in}}$) and full **L-Pads ($R_1 + R_3$)** placed either *before* or *after* the high-pass filter.
* **Elliptic Breakup Filters ($C_{\text{ell}} \parallel L_1$):** Places a small bypass capacitor in parallel across the woofer's series coil to create a surgical notch at the cone breakup frequency.
* **Q-Damped Shunt Coils ($R_q + L_1$), Parallel RLC Contour Tanks ($C \parallel L \parallel R$), Shunt LCR Traps & RC Zobel Networks.**
* **Free / Staggered Target Alignment:** Optimize strictly for the flattest, smoothest acoustic sum or lock to textbook **LR2**, **LR4**, **BW2**, or **BW3** acoustic targets.

### 📷 Built-In Datasheet Graph Image Scanner (with Hilbert Phase)
* Don't have `.frd` or `.zma` files? Upload a screenshot (`.png` / `.jpg`) of any manufacturer datasheet graph.
* Features **2-point axis calibration**, **bi-directional path tracking** (even when off-axis curves overlap at low frequencies), **freehand mouse correction**, and a **Bode-Hilbert transform** that reconstructs true minimum-phase response directly from the scanned magnitude curve.

### 🛠️ Practical Engineering Tools
* **Driver Arrays:** Simulate single drivers, $2\times$ Series ($Z \times 2$), $2\times$ Parallel ($Z / 2, +6\text{ dB}$), $3\times$ Series/Parallel, and $4\times$ `2S2P` arrays with C-C spacing lobing.
* ** Diagnostic Advisor:** Warns about driver sensitivity mismatches, high-frequency roll-off, or midrange frequency gaps (e.g., suggesting when to switch from 2-way to 3-way).
* **Analysis Overlays:** Toggle **Without Filter (Before/After)**, **Reverse Null**, **Acoustic Phase & Group Delay (ms)**, **$\pm 5\%$ Monte Carlo Tolerance Band**, and **Golden Reference A**.
* **VituixCAD $G(f)$ Export:** Export the exact complex electrical transfer function (`.frd`) of each branch for VituixCAD or active DSP prototyping (CamillaDSP / REW / MiniDSP).
* **Auto-Rated BOM & 90° PCB Layout Guide:** Generates a complete Bill of Materials in Euro (`€`) with automatic thermal power ratings (`10W` / `20W` / `25W`), E12/E24 snapping, generic search strings, and an orthogonal $90^\circ$ coil placement guide to prevent magnetic crosstalk.

---

## 🚀 Quick Start

Because the entire application is self-contained in a single HTML file with zero external dependencies, no installation or build step is required:

1. Download **`index.html`** (or `passive_xo_generator.html`).
2. Double-click to open it in any modern web browser (Chrome, Edge, Firefox, Safari).
3. Choose **🟢 Easy Mode (Wizard)** for a guided 3-step setup, or use **🔧 Pro Studio** for full manual control.

---

## 🧮 Mathematical Engine

* **2-Port ABCD Chain Matrices:** Every series and shunt building block is modeled as a complex $2 \times 2$ transmission matrix $\begin{bmatrix} A & B \\ C & D \end{bmatrix}$ loaded by the driver's complex impedance curve $Z_{\text{load}}(f)$, capturing real-world voltage divider interaction between the crossover and the reactive voice coil load.
* **Realistic Inductor $R_{\text{dc}}$ Scaling:** Automatically estimates DC resistance as a function of inductance ($\text{mH}$) and wire gauge, or allows fixed manual $\text{m}\Omega$ entry.

---

## 📄 License

This project is licensed under the **MIT License** – free to use, modify, and distribute for personal, educational, and commercial loudspeaker projects.
