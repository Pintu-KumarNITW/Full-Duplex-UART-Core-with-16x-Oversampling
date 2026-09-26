# Full-Duplex UART Core with 16x Oversampling

A modular, full-duplex UART (Universal Asynchronous Receiver-Transmitter) controller designed and verified in Verilog HDL, supporting configurable baud rates, parity modes, and robust frame-level error detection.

## Overview

This project implements a synthesizable UART core capable of simultaneous transmit (Tx) and receive (Rx) operation. It was designed with a focus on signal integrity at the physical layer — using 16x oversampling to reliably capture the midpoint of each received bit, even in the presence of clock or timing drift between transmitter and receiver.

## Features

- **Full-duplex operation** — independent Tx and Rx datapaths, each governed by its own finite state machine (FSM)
- **16x oversampling** — a 50 MHz clock-divider baud rate generator samples each bit 16 times and votes on the midpoint sample for reliable bit recovery
- **Configurable parity** — Even, Odd, or None, selectable at runtime/compile-time
- **Frame error detection** — flags stop-bit violations and malformed frames
- **PISO/SIPO shift registers** — Parallel-In-Serial-Out (Tx) and Serial-In-Parallel-Out (Rx) for efficient bit-level shifting
- **Parameterizable baud rate** — clock divider values adjustable for different baud rates without redesigning the core

## Architecture
