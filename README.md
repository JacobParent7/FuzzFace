# Fuzz Face Guitar Pedal
This is a project I made and documented using the electrosmash website. For a more in depth explanation of the circuit, visit https://www.electrosmash.com/fuzz-face.

## The Fuzz Face Circuit
![image](https://github.com/user-attachments/assets/d238433e-f945-4119-aca1-6a3b554279a7)

## BJT Germanium Transistors
  - Germanium transistors have lower forward voltage ~0.2V and lower gain
  - This causes failed gain, also known as distortion to guitarists, to occur earlier
  - Audibly, this gives the distortion a warmer and subjectively pleasent tone

### Why are germanium transistors so hard to find?
  - No longer manufactured in bulk
  - High leakage current
  - Inconsistent gain value

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
  - C1 is a AC coupling capacitor, responsible for blocking any DC signal at the input.
  - 33k resistor sets gain, bias points, and max collector current according to PNP BJT Ebers Moll Equation

#### Input Impedance
  - We analyze BJT transistors as transconductance amplifiers (voltage controlled current source), unlike Op-Amps (VCVS)
  - To get a sense of input impedance, we observe the inverse effect of transconductance, also called resistance
  - The impedance is represented by this emitter resistance multiplied by Beta, more life hfe in your datasheet
  - BJTs do not really have a resistance like a linear part (resistor, capacitor, inductor), but it helps to think of their input impedance this way
   ![image](https://github.com/user-attachments/assets/268068b2-e6bd-476e-987c-7f64c7e46e20)
  - In this calculation, ignore the feedback (although this does have a significant effects bringing 8k to around 5k)
  - This is EXTREMELY low for a guitar pedal which should typically have 1M input impedance at the least
   ![image](https://github.com/user-attachments/assets/bf0e167d-76f8-4395-b858-7390cda14771)
  - This input impedance will represent R2 in the voltage divider equation with whatever input (1k from pedal, 5k from pickup) it receives
  - This causes significant signal attenuation

#### Input Voltage Gain 
  - Common emitter gain is shown below
  ![image](https://github.com/user-attachments/assets/34e725c4-2b71-4b19-b588-6d3d5c1e7ed0)
  ![image](https://github.com/user-attachments/assets/21d882cf-9e28-48d0-a87b-5072f318f92d)
  - Ie is DC emitter current
  - Vt is thermal voltage, we always approximate at 25mV as engineers
  - Overall, this should give 49 dB of gain, but feedback cuts this to 18 dB realistically
#### Input Filter
  - The DC blocking cap and input impedance of the transistor form a high pass filter
    ![image](https://github.com/user-attachments/assets/b00d0149-7a75-4d87-bbb9-ac87b36d919b)
  - This has a cutoff of 14 Hz

### Output Stage

#### Output Impedance
  - Rvol / 470, giving a max of ~500 Ohm output impedance
  - THis changes when considering the feedback, giving an actual value of 15k Ohm
  - Typically, this is considered too high
  - 
#### Output Filter
  - Output cap blocks DC but also creates a high pass with Rvol
  - Highest cutoff is 31Hz

#### Total Voltage Gain
  - Second stage is more stable due to emitter degeneration
  ![image](https://github.com/user-attachments/assets/575c86f8-300e-41e8-bfbd-13f45a2fd156)
  - With first stage in mind, the second stage only has around 1dB of gain to add.
  - However, the output is taken at the divider, making the real gain -5.5 dB
  - This is similar to the input signal amplitude. By design, we don't want to overdrive the level of the following FX modules

## Sound Signature

### Asymetrical Clipping
  - Most pedals bias at the halfway point (+-4.5V depending on NPN or PNP) of their voltage rails to get max range
  - FF biases at -1.6V
  - Positive voltage swin is much larger than negative voltage swing

### Frequency Response
  - The pedal has 2 high pass filters that shape the response that were mentioned above
    ![image](https://github.com/user-attachments/assets/6843abd3-28cf-4513-981b-7fe54237cbff)







