# Zero-Latency-Audio-Hub        *UNFINISHED*
A relatively cheap DAC/Amp and microphone input hub. Made to outperform everything in its price bracket at the expense of many hours of labour.
Key features:
  Mixed-Signal Architecture: Analog signal path for 0ms latency monitoring.
  CDC Implementation: SystemVerilog Async FIFO for reliable USB to I2S clock domain crossing.
  Noise Performance: Custom +-12V ultra low noise power supply (Measured -110dB noise floor)

Block diagram: 
<img width="2816" height="1536" alt="Top Level System Block Diagram" src="https://github.com/user-attachments/assets/3e4cb24e-7af7-4d65-bbaa-6e4fbd708c83" />
Figure 1: Top level system block diagram

<img width="2816" height="1536" alt="FPGA Internal Logic (RTL) Diagram" src="https://github.com/user-attachments/assets/5ee2e7ce-d5c5-4584-bc40-4f2e1b570051" />
Figure 2: FPGA Internal Logic (RTL) Diagram

<img width="2816" height="1536" alt="Analog Signal Path   Power Diagram" src="https://github.com/user-attachments/assets/0320b246-f5f4-4da4-89ac-8c90127b230d" />
Figure 3: Analog Signal Path & Power Diagram

List of materials:
| Section      | Component          | Part Number (subject to change)                       | Key Feature / Why This?                                                                                                                                 |
| ------------ | ------------------ | ----------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| DIGITAL CORE | FPGA               | Lattice iCE40UP5K (QFN) or Gowin GW1N-UV9             | Low cost, easy to solder QFN package. Sufficient logic for FIFO & I2S. Open-source toolchain friendly (yosys/nextpnr).                                  |
|              | USB Bridge         | XMOS XU208 (Module) or standard header for "Combo384" | Offloads complex USB UAC2 enumeration. Provides standard I2S output. Using a proven module reduces risk.                                                |
|              | Audio Clock (MCLK) | NDK NZ2520SD (24.576 MHz)                             | Critical. Low phase noise crystal oscillator. The time reference for the DAC, defining audio precision.                                                 |
|              | FPGA Config Flash  | Winbond W25Q32                                        | Standard SPI Flash for storing the FPGA bitstream.                                                                                                      |
| ANALOG AUDIO | DAC Chip           | Texas Instruments PCM5102A                            | 32-bit/384kHz. "Hardware Mode" requires no microcontroller configuration. Integrated line driver simplifies the BOM.                                    |
|              | Mic Preamp         | THAT Corp 1510                                        | Professional studio-grade IC. Ultra-low noise (-127dBu EIN). Far superior to generic op-amp preamps.                                                    |
|              | Op-Amps (Mix/Gain) | Texas Instruments OPA1612                             | Ultralow noise (1.1nV/√Hz), ultra-low distortion. Used in high end audiophile gear.                                                                     |
|              | Headphone Buffer   | Texas Instruments LME49600                            | High-current (250mA) output buffer. Placed in the OPA1612 feedback loop to drive low-impedance headphones (like DT 770 Pro X) with near zero impedance. |
|              | Volume Control     | Microchip MCP41HV51-103                               | High-Voltage Digital Potentiometer. Must handle the ±12V analog signal swing without clipping.                                                          |
| POWER        | Split-Rail DC-DC   | Texas Instruments TPS65131                            | Converts single 5V USB input into positive (+15V) and negative (-15V) rails for the analog section.                                                     |
|              | LDO (+12V Analog)  | Texas Instruments TPS7A49                             | Ultra-low noise, high PSRR linear regulator to clean up the switching noise from the DC-DC converter.                                                   |
|              | LDO (-12V Analog)  | Texas Instruments TPS7A30                             | Negative counterpart to the TPS7A49.                                                                                                                    |
|              | LDO (Digital 3.3V) | Generic AMS1117-3.3 or similar                        | Standard regulator for FPGA I/O and digital logic.                                                                                                      |
| CONNECTORS   | Mic Input          | Neutrik NC3FAH2                                       | Quality PCB mount XLR connector.                                                                                                                        |
|              | Headphone Out      | Neutrik NRJ6HF-1                                      | Quality PCB mount 1/4" (6.35mm) TRS jack with metal nose for grounding.                                                                                 |
|              | USB Port           | Generic USB Type-C receptacle                         | 16-pin for easier hand soldering than 24-pin.                                                                                                           |
