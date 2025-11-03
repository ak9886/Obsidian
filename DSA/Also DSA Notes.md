---
updated_at: 2025-11-03T20:58:10.726+05:30
edited_seconds: 120
---
#DSA 


# **UNIT 4 — Measuring Instruments and Transducers**

---

## **1. Transducers**

### **1.1 Definition**

A **transducer** converts a non-electrical quantity (temperature, pressure, displacement, light, etc.) into an **electrical signal**.  
This allows physical phenomena to be measured, processed, and displayed.

### **1.2 Basic Principle**

Every transducer depends on a **sensing element** that reacts to the measured quantity and a **transduction element** that converts that reaction into a usable signal.

```
Physical Quantity  →  Sensor Element  →  Electrical Output
```

### **1.3 Block Representation**

```
Input Quantity → Sensing Element → Transduction Element → Output Signal
```

### **1.4 Types of Transducers**

|Category|Examples|Output|
|---|---|---|
|Active (self-generating)|Thermocouple, Piezoelectric sensor|Electrical energy without external supply|
|Passive|LVDT, Strain gauge, RTD|Needs external power source|

### **1.5 Performance Parameters**

- **Sensitivity:** ΔOutput / ΔInput
    
- **Linearity:** deviation of actual output from ideal straight line
    
- **Range & Span:** min–max measurable values
    
- **Hysteresis:** difference in output for same input when measured from increasing and decreasing directions
    
- **Dynamic Response:** how fast the transducer reacts to change
    

### **1.6 Example (C code – LVDT simulation)**

```c
#include <stdio.h>
int main() {
    float displacement, sensitivity = 0.5; // V/mm
    printf("Enter displacement (mm): ");
    scanf("%f", &displacement);
    printf("LVDT Output Voltage = %.2f V\n", displacement * sensitivity);
    return 0;
}
```

---

## **2. Sensors**

### **2.1 Definition**

A **sensor** is the front-end device that **detects** a physical change and converts it into an observable signal (electrical, optical, etc.).  
Every transducer contains at least one sensor.

### **2.2 Classification**

1. **Active Sensors:** Generate their own voltage or current.  
    _Examples:_ Thermocouple, Piezoelectric sensor.
    
2. **Passive Sensors:** Require external excitation.  
    _Examples:_ RTD, LDR, Potentiometer.
    

### **2.3 Common Sensors**

|Sensor|Measured Quantity|Working Principle|
|---|---|---|
|**RTD**|Temperature|Resistance increases with temperature|
|**Thermistor**|Temperature|Non-linear resistance vs temperature|
|**LDR**|Light intensity|Resistance decreases with light|
|**Piezoelectric**|Pressure/vibration|Generates charge when stressed|
|**Capacitive sensor**|Displacement|Capacitance varies with distance|

### **2.4 Example (C++ – Thermistor model)**

```cpp
#include <iostream>
#include <cmath>
using namespace std;

int main() {
    double R0 = 10000; // resistance at 25°C
    double T0 = 298.15; // Kelvin
    double B = 3950;    // material constant
    double T;           // temperature in °C

    cout << "Enter temperature (°C): ";
    cin >> T;
    double Tk = T + 273.15;
    double Rt = R0 * exp(B * (1/Tk - 1/T0));

    cout << "Thermistor resistance = " << Rt << " ohms\n";
    return 0;
}
```

---

## **3. Classification of Measuring Instruments**

### **3.1 Based on Principle of Operation**

- **Indicating instruments:** show instantaneous values (e.g., ammeter, voltmeter).
    
- **Recording instruments:** record readings over time (e.g., ECG recorder).
    
- **Integrating instruments:** measure total quantity over time (e.g., energy meter).
    

### **3.2 Based on Energy Source**

- **Self-operated (active):** use the measured quantity’s energy.
    
- **Power-operated (passive):** need external supply.
    

### **3.3 Analog vs Digital**

|Feature|Analog|Digital|
|---|---|---|
|Output|Continuous|Discrete|
|Accuracy|Moderate|High|
|Readability|Pointer scale|Numeric|
|Example|Analog voltmeter|Digital multimeter|

### **3.4 Essential Components**

1. **Deflecting system:** produces torque proportional to measurand.
    
2. **Controlling system:** restores pointer to zero.
    
3. **Damping system:** prevents oscillations.
    

### **3.5 Example Formula**

For PMMC instrument:

```
Deflecting torque Td ∝ I
Controlling torque Tc ∝ θ
At equilibrium → Td = Tc → I ∝ θ
```

---

## **4. Measurement Systems**

### **4.1 Definition**

A **measurement system** converts a physical variable into an interpretable quantity through multiple stages:  
**Sensor → Signal Conditioning → Processing → Display.**

### **4.2 Functional Elements**

|Stage|Function|Example|
|---|---|---|
|Primary sensing element|detects the quantity|Diaphragm in pressure sensor|
|Transduction element|converts to electrical signal|Strain gauge|
|Signal conditioning|amplifies/filter|Op-amp|
|Data presentation|display/output|Digital display, storage|

### **4.3 Static Characteristics**

|Characteristic|Description|
|---|---|
|Accuracy|Closeness to true value|
|Precision|Repeatability|
|Resolution|Smallest measurable change|
|Drift|Gradual deviation over time|

### **4.4 Dynamic Characteristics**

- **Fidelity:** output follows input without distortion.
    
- **Speed of response:** time to reach steady value.
    
- **Dynamic error:** difference during transient state.
    

### **4.5 C Example – Simple Measurement Calculation**

```c
#include <stdio.h>
int main() {
    float actual = 100.0, measured;
    printf("Enter measured value: ");
    scanf("%f", &measured);
    float error = (measured - actual) / actual * 100;
    printf("Percentage error = %.2f%%\n", error);
    return 0;
}
```

---

## **5. Signal Conditioning and Data Acquisition Systems**

### **5.1 Signal Conditioning**

Signal conditioning improves the sensor’s raw signal to a usable form for display or processing.

#### **Operations:**

1. **Amplification** – increases weak sensor signals (e.g., op-amp amplifiers).
    
2. **Filtering** – removes noise (low-pass, high-pass).
    
3. **Modulation/Demodulation** – converts signals for transmission.
    
4. **Linearization** – compensates for sensor non-linearity.
    
5. **Analog-to-Digital Conversion (ADC)** – required for digital processing.
    

### **5.2 Data Acquisition System (DAQ)**

A **DAQ** system collects and processes data from multiple sensors.

#### **Basic Components**

1. **Transducer/Sensor** – converts physical variable to electrical signal.
    
2. **Signal Conditioner** – amplifies and filters.
    
3. **Multiplexer (MUX)** – selects one signal at a time.
    
4. **ADC** – converts analog signal to digital.
    
5. **Processor/Computer** – stores, analyzes, and displays.
    

```
Sensor → Conditioner → MUX → ADC → Processor → Display
```

### **5.3 Example (C code – Basic Sampling)**

```c
#include <stdio.h>
#include <math.h>

int main() {
    float signal[10];
    for (int i = 0; i < 10; i++)
        signal[i] = sin(i * 0.5);  // simulated sensor data

    printf("Sampled Data:\n");
    for (int i = 0; i < 10; i++)
        printf("Sample %d: %.3f\n", i, signal[i]);

    return 0;
}
```

### **5.4 Example (C++ – ADC Quantization Simulation)**

```cpp
#include <iostream>
#include <cmath>
using namespace std;

int main() {
    int bits = 8;
    float Vref = 5.0;
    float Vin;
    cout << "Enter analog voltage (0–5 V): ";
    cin >> Vin;

    int digital = (int)((Vin / Vref) * ((1 << bits) - 1));
    cout << "Digital output code = " << digital << endl;
    cout << "Quantized voltage = " << (digital * Vref / ((1 << bits) - 1)) << " V\n";
    return 0;
}
```

---

## **Summary of Unit 4**

- **Transducers**: devices converting physical to electrical signals.
    
- **Sensors**: primary detecting elements.
    
- **Measuring Instruments**: classified by function and energy type.
    
- **Measurement Systems**: process chain from sensing to display.
    
- **Signal Conditioning & DAQ**: interface between analog sensors and digital processors.
    

---
# **UNIT 5 — EARTHING, SINGLE LINE DIAGRAMS & ELECTRIC VEHICLES**

---

## **1. EARTHING SYSTEMS**

### **1.1 Definition**

**Earthing** (or grounding) is the process of connecting the non-current carrying parts of electrical equipment or the neutral of the supply system to the earth — to maintain the same potential as the ground and to ensure **safety of personnel and equipment**.

### **1.2 Purpose**

- Protects human beings from electric shock.
    
- Provides a path for fault currents to flow safely to earth.
    
- Stabilizes voltage under transient conditions.
    
- Protects equipment against lightning and static discharges.
    

### **1.3 Basic Principle**

When an insulation failure occurs, fault current flows through the earthing conductor instead of through a person.  
The earth electrode provides **low resistance** so that sufficient current flows to trip protective devices (e.g., fuse, MCB).

```
Fault → Equipment Frame → Earthing Conductor → Earth Electrode → Ground
```

### **1.4 Types of Earthing**

|Type|Description|Application|
|---|---|---|
|**Plate Earthing**|Galvanized iron or copper plate buried vertically in earth.|Substations, industries|
|**Pipe Earthing**|GI pipe with holes for moisture retention.|Domestic systems|
|**Rod Earthing**|Copper rod driven into ground.|Temporary setups|
|**Strip/Conductor Earthing**|GI or copper strip laid in trenches.|Large installations|

### **1.5 Earthing Resistance (R)**

Resistance between the electrode and the general mass of earth depends on:

- Material and size of electrode
    
- Soil resistivity (ρ)
    
- Depth of burial (L)
    

For a rod electrode:

```
R = (ρ / (2πL)) * [ln(4L/d) - 1]
```

Where:  
ρ = soil resistivity (Ω·m), L = length, d = diameter.

### **1.6 C Example – Calculate Earthing Resistance**

```c
#include <stdio.h>
#include <math.h>

int main() {
    float rho, L, d;
    printf("Enter soil resistivity (ohm-m): ");
    scanf("%f", &rho);
    printf("Enter length (m) and diameter (m) of electrode: ");
    scanf("%f %f", &L, &d);

    float R = (rho / (2 * M_PI * L)) * (log(4 * L / d) - 1);
    printf("Earthing resistance = %.3f ohms\n", R);
    return 0;
}
```

---

## **2. SINGLE LINE DIAGRAMS (SLD)**

### **2.1 Definition**

A **Single Line Diagram (SLD)** is a simplified symbolic representation of a power system where **each three-phase connection** is shown using a **single line**.

It provides a clear overview of how power flows from generation to load.

### **2.2 Components Shown in SLD**

1. **Generators** – represented by circles or ellipses.
    
2. **Transformers** – shown by two interlinked coils.
    
3. **Transmission lines** – single straight lines.
    
4. **Circuit breakers & fuses** – protect system.
    
5. **Loads** – represented by rectangles.
    
6. **Busbars** – junctions connecting several lines.
    

```
Generator → Transformer → Busbar → Feeder → Load
```

### **2.3 Purpose of SLD**

- Simplifies complex 3-phase systems.
    
- Helps in fault analysis and load flow studies.
    
- Useful for maintenance planning and troubleshooting.
    

### **2.4 Example (Conceptual Description)**

```
[GEN]──[CB]──[TR]──[BUS]──┬──[Feeder 1 → Load 1]
                           ├──[Feeder 2 → Load 2]
                           └──[Feeder 3 → Motor Bank]
```

### **2.5 Example (C++ Simulation for Load Current Calculation)**

```cpp
#include <iostream>
using namespace std;

int main() {
    float P, V, pf; // Power (kW), Voltage (V), Power factor
    cout << "Enter power (kW): ";
    cin >> P;
    cout << "Enter voltage (V): ";
    cin >> V;
    cout << "Enter power factor (0-1): ";
    cin >> pf;

    float I = (P * 1000) / (1.732 * V * pf);
    cout << "Line current = " << I << " A\n";
    return 0;
}
```

---

## **3. TYPES OF ELECTRIC VEHICLES (EVs)**

### **3.1 Classification**

|Type|Description|Example|
|---|---|---|
|**Battery Electric Vehicle (BEV)**|Fully powered by batteries and electric motor.|Tesla Model 3, Tata Nexon EV|
|**Hybrid Electric Vehicle (HEV)**|Combines IC engine + electric motor (no plug-in).|Toyota Prius|
|**Plug-in Hybrid Electric Vehicle (PHEV)**|Like HEV but battery can be charged externally.|Hyundai Ioniq PHEV|
|**Fuel Cell Electric Vehicle (FCEV)**|Uses hydrogen fuel cells to produce electricity.|Toyota Mirai|

### **3.2 Basic Components of an EV**

1. **Battery Pack** – stores DC energy.
    
2. **Inverter** – converts DC to AC for the motor.
    
3. **Electric Motor** – traction drive (BLDC, PMSM).
    
4. **Controller** – manages speed and torque.
    
5. **On-board Charger** – converts AC from grid to DC.
    
6. **Regenerative Braking System** – converts kinetic energy back to electrical energy.
    

### **3.3 EV Power Flow**

```
Battery → Inverter → Motor → Wheels
          ↑               ↓
   Regenerative Braking ← Vehicle Motion
```

### **3.4 Battery Management System (BMS)**

BMS ensures battery safety and efficiency:

- Monitors voltage, current, temperature
    
- Prevents overcharging/discharging
    
- Balances cell voltages
    
- Communicates with vehicle controller
    

### **3.5 Example (C++ – Battery State of Charge Simulation)**

```cpp
#include <iostream>
using namespace std;

int main() {
    float capacity = 50.0; // kWh
    float soc = 80.0;      // %
    float discharge = 5.0; // kWh consumed per trip

    cout << "Initial SOC = " << soc << "%\n";
    soc = soc - (discharge / capacity) * 100;
    if (soc < 0) soc = 0;

    cout << "Remaining SOC after trip = " << soc << "%\n";
    return 0;
}
```

### **3.6 Motor Types Used in EVs**

|Motor Type|Characteristics|Applications|
|---|---|---|
|**DC Motor**|Simple control, low cost|Older EVs|
|**BLDC Motor**|High efficiency, low maintenance|Two-wheelers, cars|
|**Induction Motor**|Rugged, low cost|Tesla Model S|
|**PMSM**|High torque density, efficient|Premium EVs|

---

## **4. CHARGING SYSTEMS**

### **4.1 Types of Charging**

|Type|Voltage|Charging Time|Example|
|---|---|---|---|
|**Level 1 (AC)**|120 V|8–12 hrs|Home socket|
|**Level 2 (AC)**|240 V|4–6 hrs|Wall charger|
|**Level 3 (DC Fast Charging)**|400–800 V|<1 hr|Public stations|

### **4.2 Charger Topology**

- **On-board Charger:** limited power, compact.
    
- **Off-board Charger:** higher power, used for fast DC charging.
    

### **4.3 C Example – Estimate Charging Time**

```c
#include <stdio.h>

int main() {
    float battery_kWh, charger_kW;
    printf("Enter battery capacity (kWh): ");
    scanf("%f", &battery_kWh);
    printf("Enter charger power (kW): ");
    scanf("%f", &charger_kW);

    float time = battery_kWh / charger_kW;
    printf("Approximate charging time = %.2f hours\n", time);
    return 0;
}
```

---

## **5. ELECTRIC VEHICLE DRIVES**

### **5.1 Definition**

An **electric drive** controls the speed, torque, and direction of an electric motor based on driver inputs.

### **5.2 Main Components**

- **Power Converter (Inverter/Chopper)**
    
- **Electric Motor (BLDC, PMSM, Induction)**
    
- **Control Circuit (microcontroller)**
    
- **Feedback Sensors (speed, position)**
    

### **5.3 Types of Drives**

1. **DC Drives:**  
    Use DC motors controlled by choppers.  
    Speed ∝ Armature voltage.
    
2. **AC Drives:**  
    Use inverters for variable frequency control.  
    Speed ∝ Supply frequency.
    

### **5.4 Example (C++ – PWM Control Logic)**

```cpp
#include <iostream>
using namespace std;

int main() {
    float speed_percent;
    cout << "Enter desired motor speed (0-100%): ";
    cin >> speed_percent;

    float duty_cycle = speed_percent;
    cout << "PWM Duty Cycle set to: " << duty_cycle << "%\n";
    cout << "Motor speed adjusted accordingly.\n";
    return 0;
}
```

---

## **6. ADVANTAGES AND LIMITATIONS OF EVs**

### **Advantages**

- Zero tailpipe emissions
    
- Higher energy efficiency (≈90%)
    
- Low running and maintenance cost
    
- Quiet operation
    
- Regenerative braking improves range
    

### **Limitations**

- High initial cost
    
- Limited driving range
    
- Long charging time
    
- Battery degradation over time
    
- Charging infrastructure constraints
    

---

## **7. FUTURE TRENDS**

- **Wireless (Inductive) Charging**
    
- **Battery Swapping Stations**
    
- **Vehicle-to-Grid (V2G) Integration**
    
- **Solar-powered Charging Systems**
    
- **Solid-state Batteries**
    

---

## **Summary of Unit 5**

- **Earthing** ensures safety and stability by grounding non-current carrying parts.
    
- **Single Line Diagrams** simplify power system representation.
    
- **Electric Vehicles** use electric drives, BMS, and advanced charging systems.
    
- **EV Drives and Chargers** enable efficient motion control and fast energy replenishment.
    
