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

## Device Engineering: Hardware components

The following is an overview of the Therac-25 facility involved in this study of interest:

![Screenshot from 2025-01-02 22-55-48](https://github.com/user-attachments/assets/b75d729b-4a08-4912-92b6-0b05146ac12d)

> [!NOTE]
> * Components of the **Therac-25 Unit** itself are the most to blame, specifically the turntable part and the VT-100 computer control contains the most components to blame and are required to reverse engineer them to understand the accident causation model.
> * The device unit generally runs in 3 operating modes with generally 2 therapeutic modes (i.e., Dual Therapeutic Mode Device), and 1 non-therapeutic mode: **Field Light Non-therapeutic Mode**, **X-ray Therapeutic Mode**, and **Electron beam Therapeutic Mode**.
> * The device unit is settled up and controlled via a VT-100 terminal device, and setup to a specific mode involves a particular **deterministic automata** that transforms the state of the device by initiating the following:
>     1) A turntable rotation from a calibrated position to the right position to align the target component (i.e., X-ray module or electron scan module) to the linear accelerator gun.
>     2) Applying the treatment parameters (e.g., electron beam energy - rotation angles - filter component parameters)

> [!CAUTION]
> In Therac-25 uint, unlike the predecessors of its series, since the software is the **only determinant** of the turntable position. Hence, the _turntable state_ must **_critically_** force the device to enter a locked state mode preventing other interrupt services, including the setup serivice itself, from disrupting the operation of the turntable component setup; because in the case of no critical section handling, execution of another _turntable setup routine_ will eventually lead the VT-100 to send another turntable command, which presumably starts first with a calibration preprocessor, then a turntable rotation processor; this could be hazardous when the turntable is already in **a rotation session** which is a hardware-only state (as the microswitches are removed); as the computer assumes the angle from the previously entered mode; thus the net result of this mess would likely be an undetermined position of the turntable that most like lies in the interval between the previous mode and the new commanded mode, which could result in unprotected direct electron beam radition (i.e., direct linear accelerator radiation).
>
> Hints: Several Maneuvers should be addressed in these issues including:
> 1) **Critical-safety Automatas**: design some critical tasks as **"Locked Auto States"**; that typically involves sofware-to-hardware interfacing that takes place without the conventional hardware-safety feedback measures (e.g., the turntable microswitches or the interlocks).
> 2) **Anti-failure Automatas**:
>       1) _Hardware fuse circuits_: that blowout the turntable circuitry with an error message and error report on VT-100, if the treatment is started with the electron linear accelerator exposed directly to the patient without a turntable target.
>       2) _Turntable Surface Ground Wiring_: wiring the turntable with a specific way to the ground may drain the hitting electron beam to the GND if the linear accelerator is fired in an exposed state (?).
> 4) **Emergency Shutdown Automatas**: could be executed as a last resort when the previously described anti-failure mechanisms fail. 

### Hardware Modules and Components:
1) Turntable Module.
    1) Mirror for field light Mode (Field Light Module).
    2) Electron Mode Scan Magnet (Electron Beam Module).
    3) X-ray Target Flattener and primary definer (X-ray Module).
    4) Plunger (Turntable Module).
    5) Microswitches (REMOVED).   
6) Power Module.
7) VT-100 Module.
8) Emergency Shutdown Module.
9) Intercom Module.
10) Door control Module.
11) Printer Module.

### Software Modules and Processors:
1) Processors (via an RTOS Scheduler):
    1) Linear Accelerator Processor (**Faulty Interaction**).
    2) Input Mode Processor (**Faulty Interaction**).
    3) Dosimeter input processor.
    4) Upset and Recovery processor.
    5) Timer processor.
    6) Turntable position/controls processor (**Faulty Interaction**).
    7) Printer processor.
2) Interrupt Services:
    1) Emergency Interrupt service (**Faulty Interaction**).
    2) Upset detection service. (?)
    3) Upset recovery service. (?)
    4) Timer Interrupt service.
    5) Turntable position interrupt service. (**Faulty Interaction**).

