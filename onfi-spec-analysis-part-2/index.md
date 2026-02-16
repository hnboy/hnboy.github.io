# ONFI Spec Analysis Part 2: Data Interface Evolution & ODT


# ONFI Spec Analysis Part 2: Data Interface Evolution & ODT

Following our architecture overview in Part 1, we now dive into the physical data interfaces that enable the high-speed performance of modern NAND flash.

## 1. Evolution of the Interface
ONFI has evolved significantly to keep up with throughput demands:
- **SDR (Single Data Rate)**: The classic asynchronous interface. Simple but limited in frequency.
- **NV-DDR**: Introduced source-synchronous clocking using the DQS strobe.
- **NV-DDR2/3**: Added features like differential signaling and lower voltage swings (1.2V/1.8V) to reach speeds beyond 400MT/s.

## 2. On-Die Termination (ODT)
As frequencies increase, signal reflections become a major bottleneck. ONFI 4.x and 5.x specifications rely heavily on **ODT**.
- ODT allows the NAND device to terminate the signal line internally with a specific resistance (e.g., 50Ω, 75Ω).
- This significantly improves signal integrity (SI) by reducing eye-diagram jitter.

## 3. Training and Calibration
High-speed modes aren't just plug-and-play. The controller must perform:
- **ZQ Calibration**: Adjusts the output driver impedance.
- **Read/Write Training**: Aligns the DQS strobe with the data eye for reliable sampling.

---
*In Part 3, we will look at ONFI 5.x specific enhancements for enterprise-grade performance.*

