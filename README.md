# Experiment-03
Question : Design and Analyze the Differential Amplifier for the following specs, Vdd=2.2V, P<=2.2mW, Vicm=1.2V, Vocm=1.25V, Vp=0.4V. Perform DC analysis, Transient Analysis, Frequency Response and extract the parameters.


# Theory
Introductory studies of active circuits often focus extensively on standard single-ended amplifier configurations, such as common-source, common-gate, and emitter-follower. While these configurations are valuable for understanding transistor operation, small-signal analysis, and amplifier characteristics, their practical applications are somewhat limited. In modern analog IC design, differential amplifiers are far more prevalent.

Differential amplifiers amplify the difference between two input signals rather than a single input, which offers several advantages:

They inherently reject noise and interference that appear in both input signals, improving signal integrity.
Common-mode signals, such as DC offsets present in both inputs, are suppressed, allowing amplification to focus solely on the desired signal. This is particularly beneficial in IC design, as it eliminates the need for bulky DC-blocking capacitors.
The subtraction performed by a differential pair makes it well-suited for integration into negative-feedback amplifiers, which significantly enhance amplifier performance.
One might expect these advantages to come with major drawbacks, but IC fabrication largely mitigates any concerns. Two potential issues are:

A higher component count, which is insignificant in IC design due to the minimal cost of adding extra transistors.
The necessity for matched components, which is effectively managed through modern IC fabrication techniques that ensure consistent component characteristics.

![image](https://github.com/user-attachments/assets/6d16d84f-d1c0-4c50-9ac9-926032796c73)

In a real-world application, the current-source symbol would be replaced by a circuit that generates a constant current. (For more details, refer to The Basic MOSFET Constant-Current Source.) However, to keep our introductory analysis straightforward, we will use an ideal current source in our simulations instead of a practical constant-current circuit.

In an actual IC implementation, the resistors would be replaced by a current mirror acting as an “active load.” However, to better understand the core functionality of the differential pair, we will begin with the resistor-based version.

The differential pair relies on balance for optimal performance. This requires that the MOSFETs and resistors be properly matched—both FETs should have identical channel dimensions, and the resistors should be equal, meaning R1 must be the same as R2. The chosen resistance value for these resistors is referred to as RD (drain resistance).

DC Analysis
Let's analyze the biasing conditions of the circuit when both input terminals are grounded.
The sum of the two drain currents ID1 and ID2 must equal IBIAS. We also know that the two drain currents are equal because, in this idealized analysis, both halves of the circuit are identical. Thus,

![image](https://github.com/user-attachments/assets/be4ca8c0-4c6f-4538-b7e2-a83980404c7b)

Let’s assume for the moment that the transistors are in saturation. The equation for saturation-mode drain current is the following:

![image](https://github.com/user-attachments/assets/dcf38da9-d33d-40e4-b8e1-6d62392d991b)

A MOSFET amplifier needs to remain in the saturation portion of its transfer characteristic, because the gain is higher and more stable in the saturation region compared to the triode region. To ensure saturation, the drain voltage must always be higher than the gate voltage minus the threshold voltage:

 ![image](https://github.com/user-attachments/assets/c53baa74-f4ea-43b8-a288-a90856871a64)

Differential Gain
If the voltage at the gate of Q1 is higher than the voltage at the gate of Q2, VGS1 must also be higher than VGS2, because both transistors have the same potential at the source terminal. A higher gate-to-source voltage means more drain current, but the sum of the drain currents remains the same—thus, ID1 increases and ID2 decreases, and this causes a corresponding decrease in Vout1 and a corresponding increase in Vout2.
The formula for theoretical differential gain is:

![image](https://github.com/user-attachments/assets/edd37ecc-0913-4904-8868-381e7a2c39a5)


# Solution

Let P=2.2mW
Iss = P/V = 2.2m/2.2 = 1mA
Rd = Vdd - Vocm / Id1.........(1)
Id1 = Id2 = Iss/2
Therefore,  Id1 = 0.5mA
Subs Id1 in Rd
Rd = 2.2 - 1.25 / 0.5m = 1.9kohm
Rss = Vd/Iss = 0.4/1m = 400ohm
Qpoint : (Vds, Id)Vgs 
Vds = Vd - Vs = 1.25 - 0.4 = 0.85V
Therefore, (0.85V, 0.5m)1.2V 

# Procedure
Step 1 : DC Analysis, Design Rd, Rss
Analysis
1. Increase Vicm to 1V and observe Vocm, Vp. Identify the results.
2. Calculate maximum input swing and output swing.
3. Calculate Gain using small signal model.
   
Step 2 : Transient Analysis
Apply Vinp-pmax and verify the output, Calculate gain if the output is linear.

Step 3 : AC Analysis
Find 3-dB band width.

# Circuit 1

DC Analysis

  DC analysis examines how a circuit behaves with direct current (constant voltage) applied. It helps determine values like current and voltage in a steady-state 
  condition, where everything is stable and not changing over time.

  Procedure for Performing DC Analysis:
  Select the dc output print(DC op pnt) in the Edit Simulation Command and Run the Simulation.
  The Figure below shows the Values obtained from the DC Analysis :

  ![Screenshot 2025-02-25 130229](https://github.com/user-attachments/assets/ba9496c1-126e-404e-9abc-e2af3cf64ba7)

Transient Analysis:

   Transient analysis shows how a circuit responds over time to changes, like when a signal is applied or turned off. It helps us understand how voltages and currents 
   change before the circuit stabilizes.

   Procedure for Performing Transient Analysis:
   Select the Transient Analysis in the Edit Simulation Command,  Give the stop time as 5ms and Run the Simulation.

   ![Screenshot 2025-02-28 074734](https://github.com/user-attachments/assets/8fb2a4f9-fa42-49ab-bc31-e44ac611687a)

   ![Screenshot 2025-02-28 074758](https://github.com/user-attachments/assets/7c5fc05c-a33b-451f-8c38-3d5f828de0c6)

   ![Screenshot 2025-02-28 074510](https://github.com/user-attachments/assets/f2d37632-c160-49f4-9857-f76c65e88b4b)


   The Graph below shows the Transient Response of the Given Design;

   ![Screenshot 2025-02-25 132729](https://github.com/user-attachments/assets/59570532-4651-4f35-95b4-918f61aa4d57)

  V2 is a sine wave that starts at 1.2V, has a peak-to-peak variation of 50mV, and oscillates at a frequency of 1kHz.

  AC Analysis:

   AC analysis looks at how a circuit behaves when alternating current (AC) signals are applied. It helps measure how the circuit responds to different frequencies, 
   including changes in voltage, current, gain, and phase shift.

  The Graph below shows the AC Analysis of the Given Design;

  ![Screenshot 2025-03-03 222318](https://github.com/user-attachments/assets/f9899166-7be2-4fc7-856d-23b5b85ec0ee)

  



   

















