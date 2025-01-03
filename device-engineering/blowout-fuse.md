# Circuitry Blowout Fuse Design

## Preface:
This document addresses a suggested safe design for a safety blowout fuse that _couples_ the turntable module circuitry with the linear accelerator module circuitry for extra safety measures that act as **anti-failure mechanisms** as a redundancy in case of failure of the microswitches and the software critical section measures.

## A brief about the suggested design of the fuse module:
The design involves connecting **4 hardware components** together, and the relations between them could be attained using wires and digital logic:
* The VT-100 Controller unit computer.
* The Turntable Controller Module.
* The Linear Accelerator Controller Module.
* The Blowable Fuse Module (the central part of this design).

> [!NOTE]
>
> * The **Fuse Module** must provide the explicit ability to change a blown fuse with a new one. The blown fuse may cut the power off the linear accelerator circuitry and fires an error interrupt signal to the VT-100 interface to indicate a FATAL ERROR; as the device is down for "Unsafe" operations and need immediate maintenance.
> * The relations between modules involves 2 types of relations:
>   1) **TTL or transistor-transistor-logic relation**: a binary tuple, typically between the turntable controller module and the VT-100 unit, and back from the VT-100 to the Fuse Module (i.e., $$R_{TTL} = [(Table, VT-100), (VT-100, Fuse)]$$).
>   2) **High-dc relation:** a triple tuple, typically lies between the Fuse Module, the power source, and the Linear Accelerator Module, and synthesized by a high-performance MOSFET (i.e., $$R_{HV-DC} = [(Fuse, Power, Accelerator)]$$).