# Fuzz Face Guitar Pedal

## The Fuzz Face Circuit
![image](https://github.com/user-attachments/assets/d238433e-f945-4119-aca1-6a3b554279a7)

## BJT Germanium Transistors
  - Germanium transistors have lower forward voltage ~0.2V and lower gain
  - This causes failed gain, also known as distortion to guitarists, to occur earlier
  - Audibly, this gives the distortion a warmer and subjectively pleasent tone

### Why are germanium transistors so hard to find?
  - No loneger manufactured in bulk
  - high leakage current
  - inconsistent gain value

## Circuit Overview
 - 2 stage amplifier
 - Feeds output emitter to input base to implement negative feedack for stability
 
### Feedback
   ![image](https://github.com/user-attachments/assets/b606f459-f566-4f92-a2d4-28c41c535434)
  - Second transistor is emitter degenerated. This is a form of local negative feedback. 
  - Emitter voltage is tapped and fed to base of first transistor, reducing the base voltage of transistor 1.
  - The effect of the local feedback and feedback network are controlled by a single potentiometer labelled "fuzz"

### Circuit Bias
  ![image](https://github.com/user-attachments/assets/c5c1313c-ff0c-41a1-90c7-1636e652557d)
  - This bias is simulated at fuzz pot midpoint 500 Ohm

### Input Stage
  ![image](https://github.com/user-attachments/assets/d455799c-f736-41f4-b0e1-5e6ecb20e7bf)
  C1 is a AC coupling capacitor, responsible for blocking any DC signal at the input. 33k resistor sets gain, bias points, and max collector current according to PNP BJT Ebers Moll Equation

### Transconductance
  - We analyze BJT transistors as transconductance amplifiers (voltage controlled current source), unlike Op-Amps (VCVS)
  - To get a sense of input impedance, we observe the inverse effect of transconductance, also called resistance
  - The impedance is represented by this emitter resistance multiplied by Beta, more life hfe in your datasheet
  - BJTs do not really have a resistance like a linear part (resistor, capacitor, inductor), but it helps to think of their input impedance this way
  ![image](https://github.com/user-attachments/assets/268068b2-e6bd-476e-987c-7f64c7e46e20)
  - In this calculation, ignore the feedback (although this does have a significant effects bringing 8k to around 5k)
  - This is EXTREMELY low for a guitar pedal which should typically have 1M input impedance at the least
  ![image](https://github.com/user-attachments/assets/bf0e167d-76f8-4395-b858-7390cda14771)
  - This input impedance will represent R2 in the voltage divider equation with whatever input (typically 1k) it recieves
  - This causes significant signal attenuation 



