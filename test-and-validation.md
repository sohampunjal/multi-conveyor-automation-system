# Test and Validation Report

## 1. Objective

To verify the operation of the Multi-Conveyor Automation System simulated using PLC Fiddle, including system control, conveyor transitions, and exit detection.

## 2. Test Environment

- **Platform:** PLC Fiddle
- **Control method:** Ladder logic
- **System under test:** Three-stage conveyor automation simulation
- **Validation method:** Manual simulation testing

## 3. Test Cases

| Test ID | Test Scenario | Expected Behavior | Status |
|---|---|---|---|
| T01 | Activate Start while Stop is inactive | System_Run becomes active | Passed |
| T02 | Activate Sensor_A while the system is running | Conveyor A operates | Passed |
| T03 | Activate Sensor_B while the system is running | Conveyor A stops and the A-to-B transfer condition is initiated | Passed |
| T04 | Activate Sensor_C while the system is running | Conveyor B stops and the B-to-C transfer condition is initiated | Passed |
| T05 | Activate Exit_Sensor while the system is running | Conveyor C stops and Product_At_C is cleared | Passed |
| T06 | Activate Stop | Conveyor outputs and the system run state are reset | Passed |
| T07 | Activate Reset | Selected system states are reset | Passed |

## 4. Validation Summary

The system was tested in PLC Fiddle, and its overall simulated behavior was reported to be correct.

The test cases document the expected behavior of the main control functions. Individual cases should be considered independently verified only when each has been tested and observed.

## 5. Limitations

- Testing was performed in simulation rather than on physical conveyor hardware.
- No measured throughput, response-time, or reliability data is reported.
- Sensor failures, conveyor jams, and power-loss recovery have not been documented as tested.
- The simulation does not establish that the design meets industrial safety requirements.

## 6. Future Testing

- Test repeated product transfers.
- Verify behavior when sensors activate unexpectedly or remain active.
- Test restart behavior after Stop and Reset.
- Add fault-injection scenarios and recovery tests.
- Measure transfer timing if timing functionality is implemented.

## 7. Simulation

[Open the Multi-Conveyor Automation System](https://tinyurl.com/drhtc4bz)
