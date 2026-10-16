# Ladder Logic Documentation

## 1. Overview

This document describes the ladder logic implemented for the Multi-Conveyor Automation System using PLC Fiddle.

The system coordinates three conveyors — Conveyor A, Conveyor B, and Conveyor C — using start/stop controls, product sensors, and transfer conditions.

## 2. System Start and Stop

### Start Logic
The system uses a Start contact and a normally closed Stop contact to control the `System_Run` state.

- Activating Start while Stop is inactive enables the system.
- The Stop condition is used to stop the system and reset the conveyor outputs.

### Reset Logic
The Reset input clears selected system states, including `System_Run` and `Product_At_C`.

## 3. Conveyor Sequence

### Conveyor A
When `Sensor_A` and `System_Run` are active, Conveyor A runs.

When `Sensor_B` and `System_Run` become active, Conveyor A is reset and the transfer condition `Transfer_AB` is initiated.

### Conveyor B
The `Transfer_AB` condition enables Conveyor B.

When `Sensor_C` and `System_Run` become active, Conveyor B is reset and the transfer condition `Transfer_BC` is initiated.

### Conveyor C
The `Transfer_BC` condition enables Conveyor C.

When `Exit_Sensor` and `System_Run` become active, Conveyor C is reset and `Product_At_C` is cleared.

## 4. Main Control Variables

| Variable | Function |
|---|---|
| `Start` | Starts the system |
| `Stop` | Stops conveyor operation |
| `Reset` | Resets selected system states |
| `Sensor_A` | Detects a product at stage A |
| `Sensor_B` | Detects a product at stage B |
| `Sensor_C` | Detects a product at stage C |
| `Exit_Sensor` | Detects a product at the exit |
| `System_Run` | Indicates that the system is enabled |
| `Conveyor_A` | Controls Conveyor A |
| `Conveyor_B` | Controls Conveyor B |
| `Conveyor_C` | Controls Conveyor C |
| `Transfer_AB` | Transfer condition between A and B |
| `Transfer_BC` | Transfer condition between B and C |
| `Product_At_C` | Product-state variable associated with stage C |

## 5. Simulation and Verification

The ladder logic was tested in PLC Fiddle. The system was observed to behave as intended during simulation, including start/stop control, conveyor transitions, and exit detection.

**Simulation:** https://tinyurl.com/drhtc4bz

## 6. Scope and Limitations

This project demonstrates PLC ladder-logic concepts in a simulated environment. It does not represent a commissioned industrial installation. Real-world deployment would require suitable hardware, electrical protection, safety circuits, and testing.

## 7. Possible Improvements

- Add fault detection and alarm handling.
- Introduce timers for controlled transfer delays.
- Add product-count tracking.
- Implement jam detection and recovery logic.
- Extend the design with a documented input/output map.
