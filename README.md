# I2C Protocol Verification (SystemVerilog)

**Author:** Aneesh Rekhalal Thakre  
**Platform:** SystemVerilog, Vivado / ModelSim / VCS / XSIM compatible  
**Summary:**  
This repository contains an RTL implementation of an I2C Master–Slave pair and a class-based verification environment (Generator, Driver, Monitor, Scoreboard) using constrained-random tests to validate START/STOP handling, address phase, read/write cycles, and ACK/NACK signaling.

---

## Table of Contents

- [Project Overview](#project-overview)  
- [Features](#features)  
- [Repository Structure](#repository-structure)  
- [Design Details](#design-details)  
- [Verification Environment](#verification-environment)  
- [How to Run Simulations](#how-to-run-simulations)  
- [Waveform & Coverage](#waveform--coverage)  
- [Example Testcases](#example-testcases)  
- [Contributing](#contributing)  
- [License](#license)

---

## Project Overview

This project implements:
- An RTL I2C Master and I2C Slave written in SystemVerilog using FSMs.
- A class-based verification environment containing:
  - **Generator**: creates constrained-random transactions (start, address, read/write, stop, ACK/NACK patterns).
  - **Driver**: drives the DUT via an interface (SCL, SDA).
  - **Monitor**: observes bus activity and converts it into transaction objects for checking.
  - **Scoreboard**: memory-backed checker that tracks expected data and verifies read/write correctness.

The goal is to validate timing, protocol behavior, and corner cases using functional coverage and assertions.

---

## Features

- Master/Slave RTL (SystemVerilog FSM-based)
- Interface abstraction for SDA & SCL (bidirectional SDA handling)
- Constrained-random transaction generation
- Memory-backed scoreboard for end-to-end data validation
- Assertion-based checks for START/STOP, ACK/NACK, and bus arbitration
- Testbench scripts for ModelSim/XSIM/VCS
- Waveform-friendly signal naming for easy debugging

---

## Repository Structure

