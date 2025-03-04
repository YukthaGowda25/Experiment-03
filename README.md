b# Experiment-03
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

![image](https://github.com/user-attachments/assets/51a058e5-8e16-41ea-a4f4-262eeb3a8bd4)


DC Analysis

  DC analysis examines how a circuit behaves with direct current (constant voltage) applied. It helps determine values like current and voltage in a steady-state 
  condition, where everything is stable and not changing over time. It shows the operating point transistors, including voltages at different nodes and the currents flowing through them. This is crucial because proper biasing ensures that the amplifier operates in the correct region (saturation for MOSFETs) and provides the expected gain and performance.

  Procedure for Performing DC Analysis:
  1. Assign values for length and width of mosfet to ensure that the required amount of current is flowing in each branch. Considering Length = 180n and Width = 6.41246u, which is optimal for the working of FET.

![image](https://github.com/user-attachments/assets/3260b840-20b4-4d17-8376-14d9bb67e1d7)

  2. Select the dc output point(DC op pnt) in the Edit Simulation Command and Run the Simulation.
  The Figure below shows the Values obtained from the DC Analysis :

  ![Screenshot 2025-02-25 130229](https://github.com/user-attachments/assets/ba9496c1-126e-404e-9abc-e2af3cf64ba7)

 From the above picture, we can see that the current(Idd) obtained is 0.5mA satisfying the values of Vocm and Vp with the design specifiactions.
 In order to cross verify, we calculate the power using the formula, P=V*I where P<=2.2x1m=2.2mW. This satisfies the given condition that the power rating should be 2.2mW or below.

Transient Analysis:

   Transient analysis shows how the circuit responds to time-varying input signals. It helps us observe the amplifier’s behavior, such as signal amplification, settling time, and transient distortions. This analysis is useful for checking how the circuit handles real-world signals and verifying if it provides the expected output without delays or unwanted oscillations.

   Procedure for Performing Transient Analysis:
   1. In order to perform transient analysis, we give sine input with 1.2V offset voltage, 50m amplitude and 1kHz frequency to both the gate voltage source and observe the changes.

   ![Screenshot 2025-02-28 074734](https://github.com/user-attachments/assets/8fb2a4f9-fa42-49ab-bc31-e44ac611687a)

   ![Screenshot 2025-02-28 074758](https://github.com/user-attachments/assets/7c5fc05c-a33b-451f-8c38-3d5f828de0c6)

   2. Select the Transient Analysis in the Edit Simulation Command,  Give the stop time as 5ms and Run the Simulation. Observe the graph between Vocm (output) and the input gate voltage to analyse the circuit. 

   ![Screenshot 2025-02-28 074510](https://github.com/user-attachments/assets/f2d37632-c160-49f4-9857-f76c65e88b4b)


   The Graph below shows the Transient Response of the Given Design;

   ![Screenshot 2025-02-25 132729](https://github.com/user-attachments/assets/59570532-4651-4f35-95b4-918f61aa4d57)

  Here, the green sine wave indicates the input signal and the blue sine wave indicates the output signal and the amplifier circuit is producing output with 180 degree phase shift with respect to the input.
  Calculating the gain of the circuit with the equation, Av = Vout / Vin where Vout = 1.4493 - 1.051 = 0.3983 and Vin = 1.2496 - 1.1503 = 0.0993, after substituting the values in the equation, we get 
  Av = Vout / Vin

  Av = 0.3983 / 0.0993 = 4.012
  The dB conversion of the gain is dB = 20 log Av
                              
  Therefore, dB = 20 log (4.012) = 12.067dB.
  This is verified by AC analysis.

  AC Analysis:

   AC analysis helps determine the circuit’s frequency response. It shows how the gain, phase shift, and bandwidth change with different input frequencies. This is useful for understanding how well the amplifier performs in real applications, ensuring it provides stable gain and operates effectively within the desired frequency range. This is done to verify the gain calculated during the transient analysis. Here, the same sinusoidal signal is supplied to the gate terminals with the small signal ac analysis amplitude 1 and then simulate.

  The Graph below shows the AC Analysis of the Given Design;

  ![Screenshot 2025-03-03 222318](https://github.com/user-attachments/assets/f9899166-7be2-4fc7-856d-23b5b85ec0ee)

  From the above picture, theoretical values of gain Av is approximate to the practical value which is around 175 degree, which helps in understanding the working and the output of the circuit.

  # Circuit 2

  Here, we replace resistor Rss with a current source with 1mA to analyse the circuit.

  In a MOS differential amplifier, the resistor is replaced with a current source to improve gain and performance. A current source provides a high output resistance, which increases the gain of the amplifier. It also ensures a more stable and constant current flow, making the circuit more efficient and less sensitive to variations in power supply or transistor parameters.
   A current source also helps in rejecting common-mode signals more effectively, improving the amplifier's differential performance. It also helps maintain a constant current flow, reducing distortion and improving signal quality.

   ![Screenshot 2025-03-03 225120](https://github.com/user-attachments/assets/7826cc7f-aba2-473a-bd70-a76cec7d37af)

  DC Analysis

  ![Screenshot 2025-03-03 225230](https://github.com/user-attachments/assets/61089776-337a-4f53-a17d-c6aa91f3242b)

  Here, there is no much change in the DC output, since it is only a resistor which is been replaced with the current source. The overall stability is increased keeping the current and voltage across Vp constant.

  Transient Analysis

  ![Screenshot 2025-03-03 225322](https://github.com/user-attachments/assets/102ccb86-37e7-475d-b415-d840714f4ea8)

Keeping DC offset = 1.2V, Amplitude = 50m and Frequency = 1kHz, after simulation there is 180 degree phase shift with the input. The gain is calculated using the formula  Av = Vout / Vin where Vout = 1.4493 - 1.051 = 0.3983 and Vin = 1.2496 - 1.1503 = 0.0993, after substituting the values in the equation, we get 
  Av = Vout / Vin

  Av = 0.3983 / 0.0993 = 4.012
  The dB conversion of the gain is dB = 20 log Av
                              
  Therefore, dB = 20 log (4.012) = 12.067dB.
  This is verified by AC analysis.

  AC Analysis 

  ![Screenshot 2025-03-03 225458](https://github.com/user-attachments/assets/d7d2f31c-f8b6-4741-9e34-2a9ea22ec691)

  ![Screenshot 2025-03-03 225514](https://github.com/user-attachments/assets/e71811c8-03f3-4c74-8d7f-d8880daf7bb3)

  Here, the same sinusoidal signal is supplied to the gate terminals with the small signal ac analysis amplitude 1 and then simulate. Comparing this with the previous circuit which consisted resistor Rss, we can see that there is negligible amount of variation in gain.

# Ciruit 3
Here, we replace resistor Rss with a N-Channel MOSFET to analyse the circuit.
  
  In a MOS differential amplifier, the resistor is replaced with a MOSFET (acting as a current source) to improve performance. A MOSFET provides a high output resistance, which increases gain. It also ensures a stable and constant current, improving biasing and making the circuit less sensitive to power supply variations. Additionally, using a MOSFET saves space in IC design and enhances common-mode rejection, making the amplifier more efficient. This is done to prove that the MOSFET acts as "constant current source".

  ![Screenshot 2025-03-03 224901](https://github.com/user-attachments/assets/3cf5b844-32af-45ec-b207-ef2443438f82)


DC Analysis 

Procedure for Performing DC Analysis:
  1. Assign values for length and width of mosfet to ensure that the required amount of current is flowing in each branch. Considering Length = 180n and Width = 6.89912u, which is optimal for the working of FET.
 2. Select the dc output point(DC op pnt) in the Edit Simulation Command and Run the Simulation.
  The Figure below shows the Values obtained from the DC Analysis :

 ![Screenshot 2025-03-03 224406](https://github.com/user-attachments/assets/74833609-3d94-4eb3-85e6-51979de71266)

 Transient Analysis 

 ![Screenshot 2025-03-03 225322](https://github.com/user-attachments/assets/fab81074-725c-4967-8033-4beb29b1798c)

![Screenshot 2025-03-03 225351](https://github.com/user-attachments/assets/76741f57-6b87-4c94-aa28-dddc8b1a48ee)

AC Analysis 

![Screenshot 2025-03-03 224706](https://github.com/user-attachments/assets/d104a29b-45e9-4827-afec-b3ef79543412)

![Screenshot 2025-03-03 224732](https://github.com/user-attachments/assets/8cd01ab7-c482-4815-8f7d-d574edfe0987)





