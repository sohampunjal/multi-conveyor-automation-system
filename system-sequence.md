# System Sequence Diagram

## Overview

This diagram represents the intended control sequence of the three-stage conveyor system implemented in PLC Fiddle.

## Control Flow

```mermaid
flowchart TD
    A([System Start]) --> B{Start requested<br/>and Stop inactive?}
    B -- No --> B
    B -- Yes --> C[Enable System_Run]
    C --> D{Sensor_A active?}
    D -- Yes --> E[Run Conveyor A]
    E --> F{Sensor_B active?}
    F -- Yes --> G[Stop Conveyor A<br/>Initiate Transfer_AB]
    G --> H[Run Conveyor B]
    H --> I{Sensor_C active?}
    I -- Yes --> J[Stop Conveyor B<br/>Initiate Transfer_BC]
    J --> K[Run Conveyor C]
    K --> L{Exit_Sensor active?}
    L -- Yes --> M[Stop Conveyor C<br/>Clear Product_At_C]
    M --> N([Product Transfer Complete])
```

## Sequence Explanation

1. **System activation:** Start and Stop conditions determine whether the system can run.
2. **Stage A:** Sensor A and `System_Run` control Conveyor A.
3. **Transfer A to B:** Sensor B initiates the transition from Conveyor A to Conveyor B.
4. **Transfer B to C:** Sensor C initiates the transition from Conveyor B to Conveyor C.
5. **Exit stage:** Exit sensor detection stops Conveyor C and clears the associated product-state variable.

## Notes

- This is a conceptual representation of the implemented ladder logic, not a timing diagram.
- The diagram omits detailed reset behavior and individual PLC scan cycles for clarity.
- Refer to [Ladder Logic Documentation](ladder-logic.md) for the rung-level explanation.
- Refer to [Input/Output Mapping](io-mapping.md) for the variable descriptions.
