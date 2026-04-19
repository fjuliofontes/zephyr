.. _atsamd21_rs485_ext:

ATSAMD21 RS485 Extension Interface
###################################

Overview
********

The RS485 Extension Interface is a compact ARM board designed for industrial
I/O acquisition and actuation over Modbus RTU / RS485. It features:

- 12V/24V power input with reverse-polarity protection and supercapacitor backup
- Single RS485 channel (ST1480ABDR, true fail-safe) for Modbus RTU
- 2-bit resistor-ladder address selection (up to 25 node combinations)
- 3 differential 4–20 mA current inputs
- 2 voltage inputs with selectable ranges: 0–10 V, 0–5 V, 0–3.3 V
- 2 opto-isolated digital inputs (PLC 0–24 V / free-voltage contact)
- 2 latched bistable relay outputs (5 V coil, G5RL-K1A-E-DC5)
- 1 I2C interface (3.3 V, J5 header)

Hardware
********

- ATSAMD21G18A-M ARM Cortex-M0+ at 48 MHz (48-pin QFN)
- 256 KiB flash, 32 KiB SRAM
- One status LED (PB22)

Pin Mapping
===========

+------------+----------+--------------------------------------------------+
| Signal     | MCU Pin  | Description                                      |
+============+==========+==================================================+
| DBG_TX     | PB08     | SERCOM4 PAD0 — debug / console UART TX           |
+------------+----------+--------------------------------------------------+
| DBG_RX     | PB09     | SERCOM4 PAD1 — debug / console UART RX           |
+------------+----------+--------------------------------------------------+
| RS485_TX   | PA22     | SERCOM5 PAD0 — Modbus RTU UART TX                |
+------------+----------+--------------------------------------------------+
| RS485_RX   | PA23     | SERCOM5 PAD1 — Modbus RTU UART RX                |
+------------+----------+--------------------------------------------------+
| RS485_EN   | PA10     | ST1480ABDR DE/RE direction control               |
+------------+----------+--------------------------------------------------+
| RS485_PWR  | PA18     | RS485 transceiver power enable                   |
+------------+----------+--------------------------------------------------+
| SDA        | PA12     | SERCOM2 PAD0 — I2C data                          |
+------------+----------+--------------------------------------------------+
| SCL        | PA13     | SERCOM2 PAD1 — I2C clock                         |
+------------+----------+--------------------------------------------------+
| RELAY_RST1 | PA14     | Relay 1 reset coil drive (K1)                    |
+------------+----------+--------------------------------------------------+
| RELAY_SET1 | PA15     | Relay 1 set coil drive (K1)                      |
+------------+----------+--------------------------------------------------+
| RELAY_RST2 | PA16     | Relay 2 reset coil drive (K2)                    |
+------------+----------+--------------------------------------------------+
| RELAY_SET2 | PA17     | Relay 2 set coil drive (K2)                      |
+------------+----------+--------------------------------------------------+
| OPTO1      | PA19     | Opto-isolated digital input 1                    |
+------------+----------+--------------------------------------------------+
| OPTO2      | PA20     | Opto-isolated digital input 2                    |
+------------+----------+--------------------------------------------------+
| AN_ENABLE  | PA08     | Analog front-end power enable                    |
+------------+----------+--------------------------------------------------+
| EXT_SENSE  | PA21     | External power presence sense                    |
+------------+----------+--------------------------------------------------+
| STATUS     | PB22     | Status LED                                       |
+------------+----------+--------------------------------------------------+
| ucAN_V1    | PA04     | ADC AIN[4] — voltage input 1                     |
+------------+----------+--------------------------------------------------+
| ucAN_V2    | PA05     | ADC AIN[5] — voltage input 2                     |
+------------+----------+--------------------------------------------------+
| ucAN_I1    | PA06     | ADC AIN[6] — current input 1 (4–20 mA)           |
+------------+----------+--------------------------------------------------+
| ucAN_I2    | PA07     | ADC AIN[7] — current input 2 (4–20 mA)           |
+------------+----------+--------------------------------------------------+
| ucAN_I3    | PB02     | ADC AIN[10] — current input 3 (4–20 mA)          |
+------------+----------+--------------------------------------------------+
| SLAVE_SEL0 | PA00     | ADC AIN[0] — address ladder bit 0                |
+------------+----------+--------------------------------------------------+
| SLAVE_SEL1 | PA01     | ADC AIN[1] — address ladder bit 1                |
+------------+----------+--------------------------------------------------+

Supported Features
==================

+-----------+------------+------------------------------------------+
| Interface | Controller | Driver/Component                         |
+===========+============+==========================================+
| ADC       | on-chip    | Analog inputs (current + voltage)        |
+-----------+------------+------------------------------------------+
| DMA       | on-chip    | Direct memory access                     |
+-----------+------------+------------------------------------------+
| Flash     | on-chip    | LittleFS storage partition               |
+-----------+------------+------------------------------------------+
| GPIO      | on-chip    | Relays, opto inputs, control signals     |
+-----------+------------+------------------------------------------+
| HWINFO    | on-chip    | Hardware info                            |
+-----------+------------+------------------------------------------+
| I2C       | on-chip    | External sensor interface (J5)           |
+-----------+------------+------------------------------------------+
| NVIC      | on-chip    | Nested vector interrupt controller       |
+-----------+------------+------------------------------------------+
| SYSTICK   | on-chip    | System tick                              |
+-----------+------------+------------------------------------------+
| USART     | on-chip    | Debug UART + RS485 Modbus RTU            |
+-----------+------------+------------------------------------------+
| WDT       | on-chip    | Watchdog timer                           |
+-----------+------------+------------------------------------------+
