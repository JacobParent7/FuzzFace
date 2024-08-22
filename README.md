# Fuzz Face Guitar Pedal

## The Fuzz Face Circuit
![image](https://github.com/user-attachments/assets/d238433e-f945-4119-aca1-6a3b554279a7)

## BJT Germanium Transistors
  - Germanium transistors have lower forward voltage ~4V and lower gain
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
  - ![image](https://github.com/user-attachments/assets/b606f459-f566-4f92-a2d4-28c41c535434)
  - Second transistor is emitter degenerated. This is a form of local negative feedback. 
  - Emitter voltage is tapped and fed to base of first transistor, reducing the base voltage of transistor 1.
  - The effect of the local feedback and feedback network are controlled by a single potentiometer labelled "fuzz"
