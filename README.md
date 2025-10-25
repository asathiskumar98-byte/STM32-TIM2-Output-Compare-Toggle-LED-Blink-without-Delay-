# STM32 TIM2 Output Compare Toggle (LED Blink without Delay)

This project demonstrates how to use **Timer 2 (TIM2)** on the **STM32F446RE Nucleo Board** to toggle a pin output using **Output Compare (OC) Mode** — no software delay loops, just pure hardware timing.

---

## ⚙️ Overview
The timer is configured in **Output Compare Toggle Mode**, meaning:
- Each time the timer reaches the compare value (CCR1), the corresponding pin toggles automatically.
- The toggling happens **independently of the CPU**, achieving precise timing without blocking code.

---

## 🧩 Hardware Setup

| Pin  | Function | Description |
|------|-----------|-------------|
| PA5  | TIM2 Channel 1 | Onboard LED (Active HIGH) |

---

## 🧱 Configuration Details

| Parameter | Value |
|------------|--------|
| **Timer** | TIM2 |
| **Mode** | Output Compare Toggle |
| **Channel** | CH1 |
| **Prescaler** | 15999 |
| **Period (ARR)** | 1000 |
| **Pulse (CCR1)** | 1000 |
| **Clock Source** | Internal |
| **APB1 Clock** | 16 MHz (HSI) |
| **Toggle Frequency** | 0.5 Hz (1 toggle per second) |

---

## 🧰 Tools Used
- **STM32CubeIDE 1.x**
- **STM32CubeMX**
- **HAL (Hardware Abstraction Layer)**
- **Nucleo-F446RE Board**

---

## 🚀 How It Works
1. **TIM2** counts from 0 to 1000 (ARR value).  
2. When the counter matches **CCR1 (1000)**, the **OC toggle mode** flips the output on PA5.  
3. The LED blinks automatically — **no interrupts or polling loops** required.  
4. The main loop remains empty (`while(1)`), showing the timer handles toggling in hardware.

---

## 🪄 How to Run
1. Open this folder in **STM32CubeIDE**.  
2. Build the project.  
3. Flash the code to your **Nucleo-F446RE**.  
4. Watch the onboard LED (PA5) toggle every second.

---

## 💡 Why It Matters
This project teaches:
- Non-blocking timing with hardware timers  
- Hardware-based waveform generation  
- Real-time embedded system design principles  

This method is ideal for **PWM generation**, **frequency output**, or **precise signal toggling**.

---

## 📸 Example Output
- LED toggles automatically at a fixed rate.
- `main()` runs empty while hardware does the timing.

---

## 🧩 Educational Upgrade
To explore further:
- Add **TIM interrupt** and blink pattern logic.
- Generate custom frequencies by adjusting `Prescaler` and `Period`.
- Drive external circuits (e.g., buzzer or PWM-controlled motor).
