# Input/Output Mapping

## 1. Overview

This document lists the logical inputs, outputs, and internal control variables used in the Multi-Conveyor Automation System simulation developed in PLC Fiddle.

**Note:** These are logical simulation variables, not verified physical PLC addresses.

## 2. Inputs

| Input Variable | Type | Function |
|---|---|---|
| `Start` | Boolean | Requests system startup |
| `Stop` | Boolean | Activates the stop condition |
| `Reset` | Boolean | Resets selected system states |
| `Sensor_A` | Boolean | Simulates product detection at stage A |
| `Sensor_B` | Boolean | Simulates product detection at stage B |
| `Sensor_C` | Boolean | Simulates product detection at stage C |
| `Exit_Sensor` | Boolean | Simulates product detection at the exit |

## 3. Outputs

| Output Variable | Type | Function |
|---|---|---|
| `Conveyor_A` | Boolean | Represents the operating state of Conveyor A |
| `Conveyor_B` | Boolean | Represents the operating state of Conveyor B |
| `Conveyor_C` | Boolean | Represents the operating state of Conveyor C |

## 4. Internal Control Variables

| Variable | Type | Function |
|---|---|---|
| `System_Run` | Boolean | Represents the system's run state |
| `Transfer_AB` | Boolean | Represents the transfer condition between A and B |
| `Transfer_BC` | Boolean | Represents the transfer condition between B and C |
| `Product_At_C` | Boolean | Represents a product-state condition associated with stage C |

## 5. Control Sequence

1. The Start input enables the system when the Stop condition is inactive.
2. Sensor A and the system run state control Conveyor A.
3. Detection at Sensor B initiates the transition from Conveyor A toward Conveyor B.
4. Detection at Sensor C initiates the transition from Conveyor B toward Conveyor C.
5. The exit sensor stops Conveyor C and clears the associated product-state variable.
6. Stop and Reset provide system-stop and state-reset functions, respectively.

## 6. Implementation Notes

- All variables are represented as Boolean values in PLC Fiddle.
- Physical input/output addresses have not been assigned in this simulation documentation.
- Actual hardware implementation would require address allocation, electrical interface design, and appropriate safety measures.

## 7. Simulation

[Open the Multi-Conveyor Automation System simulation](https://tinyurl.com/drhtc4bz)
