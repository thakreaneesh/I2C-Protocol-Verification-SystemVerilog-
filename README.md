# I2C Protocol Verification (SystemVerilog)

## Overview
This project implements and verifies a basic **I2C (Inter-Integrated Circuit)** protocol using SystemVerilog.  
It includes:

- **I2C Master** (generates START/STOP, address, R/W, and data)
- **I2C Slave** (responds to master and stores/returns data)
- **UVM-style Verification Environment** (Generator, Driver, Monitor, Scoreboard)

The goal is to verify correct communication between Master and Slave using a **self-checking testbench**.

---

## Features

### Master
- Generates **START** and **STOP** conditions  
- Sends **7-bit address + R/W bit**  
- Supports **read and write** cycles  
- Handles **ACK/NACK** responses  
- Shifts data **MSB first**  
- Drives **SCL** and **SDA**

### Slave
- Detects START condition  
- Performs 7-bit address match  
- Generates **ACK/NACK**  
- Receives or transmits data bytes  
- Stores received data in internal memory  
- Releases SDA when not driving

---

## Testbench Environment
- **Generator:** Creates randomized I2C transactions (address, read/write, data)  
- **Driver:** Drives SDA/SCL signals using the I2C interface  
- **Monitor:** Observes bus activity and reconstructs transactions  
- **Scoreboard:** Compares expected data with received data  
- Uses **mailboxes/events** for synchronization between components  

---

## Simulation Flow

### 1. Reset Phase
Driver applies reset and initializes all DUT signals.

### 2. Transaction Generation
Generator creates random:
- Addresses  
- Read/Write operations  
- Data bytes  

### 3. Communication
Master performs:  
START → Address → R/W → Data → STOP  
Slave responds with ACK/NACK and returns data in read mode.

### 4. Monitoring & Checking
- Monitor captures bus signals  
- Scoreboard checks:
  - Address correctness  
  - Read/Write behavior  
  - Data accuracy  

### 5. Result
Console prints:

