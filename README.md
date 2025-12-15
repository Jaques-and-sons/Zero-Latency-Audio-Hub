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
