# FPGA-to-FPGA UART Communication using VHDL

This project implements UART communication between two Digilent Nexys A7 FPGA boards using VHDL.

The idea is simple: one FPGA sends an 8-bit value through UART, and the second FPGA receives the value and displays it on its 8-digit 7-segment display.

I developed the UART transmitter and receiver from scratch without using a Vivado UART IP core.

## What I worked on

- UART transmitter and receiver in VHDL
- 8N1 UART communication
- 115200 baud rate
- 16x oversampling on the receiver
- Button/switch based data transmission
- Binary to BCD conversion
- 8-digit 7-segment display
- Simulation and verification using GHDL

## How it works

The first FPGA is the transmitter.

An 8-bit value is selected using the switches on the board. When the transmission is triggered, the value is sent through a single UART signal.

The second FPGA receives the UART data, stores the received byte, converts the value from binary to decimal using a double-dabble algorithm, and displays the result on the 8-digit 7-segment display.

```text
          FPGA 1                              FPGA 2
       (Transmitter)                         (Receiver)

    Switches / Button
           |
           v
      UART TX
           |
           | UART
           |---------------------------->
                                         UART RX
                                            |
                                            v
                                      Data Storage
                                            |
                                            v
                                      Binary -> BCD
                                            |
                                            v
                                      7-Segment Display
