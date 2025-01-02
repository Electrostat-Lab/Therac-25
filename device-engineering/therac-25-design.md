# Therac-25 Design

The design of the device had been ported essentially from the previous models, Therac-6 and Therac-20, with the exception that _Therac-25_ unit has an electron linear accelerator that can deliver a maximum power of up-to **25 MeV (Million Electronvolt)**; that is attributed to the use of a **double pass** technology that folds the physical space required to accelerate the electrons using **Magnetrons** rather than **Kylstrons** as a source of energy which gave it a much economical value.

> [!NOTE]
>
> * The suffix (N) written as **6, 20 and 25** denotes the maximum capabilities of the linear accelerator powering the device.
> * Unlike the electron beam therapeutic mode (EBT Mode), the x-ray therapeutic mode requires a high-energy high-voltage electron beam radiation;
> due to the fact that the x-ray mode uses photons emitted from a charged **tungsten** target as a result of colloiding with a high-energy high-current electron beam.

## Outline:
* **Electrical Engineering:** Electrons Linear Accelerators (Electron Guns).
* **Electrical Engineering:** Microswitches mode of operations.
* **Device Engineering:** Microswitches wiring in the Therac series.
* **Device Engineering:** Hardware components.
* **Device Engineering:** Hardware-Software components co-design.
* **Device Reverse Engineering:** Suggested design to the **Turntable Position/Control Processor** software component based on the accident causation analysis provided by [Nancy Leveson](https://en.wikipedia.org/wiki/Nancy_Leveson).
