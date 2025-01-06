# Circuitry Blowout Fuse Design

## Preface:
This document addresses a suggested safe design for a safety blowout fuse that _couples_ the turntable module circuitry with the linear accelerator module circuitry for extra safety measures that act as **anti-failure mechanisms** as a redundancy in case of failure of the microswitches and the software critical section measures.

## A brief about the suggested design of the fuse module:
The design involves connecting **4 hardware components** together, and **the relations** between them could be attained using **wiring diagrams** and **digital logic**:
* The VT-100 Controller unit computer.
* The Turntable Controller Module.
* The Linear Accelerator Controller Module.
* The Blowable Fuse Module (the central part of this design).

> [!NOTE]
>
> * The **Fuse Module** must provide the explicit ability to change a blown fuse with a new one. The blown fuse may cut the power off the linear accelerator circuitry and fires an error interrupt signal to the VT-100 interface to indicate a FATAL ERROR; as the device is down for "Unsafe" operations and need immediate maintenance.
> * The relations between modules involves 2 types of relations:
>   1) **TTL or transistor-transistor-logic relation**: a binary tuple, typically between the turntable controller module and the VT-100 unit, and back from the VT-100 to the Fuse Module (i.e., $$R_{TTL} = [(Table, VT_{100}), (VT_{100}, Fuse)]$$).
>   2) **High-dc relation:** a triple tuple, typically lies between the Fuse Module, the power source, and the Linear Accelerator Module, and synthesized by a high-performance MOSFET (i.e., $$R_{HV-DC} = [(Fuse, Power, Accelerator)]$$).
> * The design could be further enforced by stimulating software-hardware component the "Emergency Shutdown Interrupt Service", when the treatment is proceeded with an indeterminated turntable position, instead of introducing a new software component.
> * The incorporation of the fuse or circuit breaker modules as an anti-failure measure for the turntable module are an actual electrical hack, and will entail intentionally passing a current rating above the selected fuse module via a MOSFET switch circuit. However, this type of design will require additional modular safety against the high current that is introduced intentionally into this connection, current limiting devices or current dividers (e.g., Resistors in parallel) are usually a good solution so far, but the general complexity increases.
> * There are several other ways to introduce this safety circuit typically via connecting the VT-100 commander to the turntable module via an NAND digital logic circuitry that gets triggered to shut off the circuit when both inputs are HIGH. If the turntable module requires non-TTL voltage power source; then an additional High-Voltage relay is required to complete the wiring between the digital circuit and the module power circuitry.

> [!CAUTION]
> 
> Using the fuse-based anti-failure circuit design has its unrevealed downsides which is the complexity of adding further protection mechanisms against
> high-current which is an intentional design in this case, as this entails a high-voltage protection logic.
>
> There are better alternatives though, the introduction of digital control via simple NAND, Multiplexers, and Decoder modules could be much simpler and safer.

## Suggested designs for the _Anti-failure Module_:

Suggested designs using digital logic (automata model) for the **Anti-failure Turntable Shutdown Module**:

### Automata Model for the Anti-failure Module:

### Digital Logic Protection Modules:
| NAND Anti-failure Turntable Module | Multiplexer-based Anti-failure Module | Decoder-based Anti-failure Module |
|------------------------------------|---------------------------------------|-----------------------------------|
| <img src="https://github.com/Electrostat-Lab/Therac-25/blob/therac-25-design/device-engineering/assets/Screenshot%20from%202025-01-06%2002-48-47.png"/> | | | 
| The preceding circuit represents a TTL voltage anti-failure module circuit design for the Turntable module, the basic components are:<br/> 1) A NAND package **74AHC1G00**.<br/> 2) A SPST Reed Relay (Single-pole-single-throw).<br/> 3) A 1N4001 diode for a transient suppressor protection circuit.<br/> The circuit takes commands from the **VT-100** digital logic CMOS encoder that if commanded as `11` will shutdown the turntable immediately (typically within nanoseconds delay time -- reed relay switching time).  | | |

### High-Voltage Logic Protection Modules:
| Fuse-based Anti-failure Module | Thermal Circuit breaker Anti-failure Module | 
|--------------------------------|---------------------------------------------|
| | |

## Useful formulas for different components used: 
| BJTs | FETs (Field Effect Transistors) | MOSFETs (Metal Oxide Semi-conductor Field Effect Transistors) | MSFETs (Metal Semi-conductor Field Effect Transistors) |
|-----------|-----------|---------|------|
|    |   |  | |
|    |    |  | |

| Reed Relays | Zener Diodes | Inductance and Inductive Reaction |
|-------------|--------------|-------|
|  |  | |

### References:

