# GENERATION-AND-DETECTION-OF-AM_1
## AIM:
To generate and detect the amplitude modulation and demodulation u s i n g S C I L A B and to calculate modulation index of AM.

## EQUIPMENTS REQUIRED

•	Computer with i3 Processor

•	SCI LAB

## THEORY:
Modulation can be defined as the process by which the characteristics of carrier wave are varied in accordance with the modulating wave (signal). Modulation is performed in a transmitter by a circuit called a modulator.

Need for modulation is as follows:

•	Avoid mixing of signals

•	Reduction in antenna height

•	long distance communication

•	Multiplexing

•	Improve the quality of reception

•	Ease of radiation.

Amplitude Modulation is the process of changing the amplitude of a relatively high frequency carrier signal in proportion with the instantaneous value of the modulating signal. The output waveform contains all the frequencies that make up the AM signal and is used to transport the information through the system. Therefore the shape of the modulated wave is called the AM envelope. With no modulating signal the output waveform is simply the carrier signal. Coefficient of modulation is a term used to describe the amount of amplitude change present in an AM waveform. There are three degrees of modulation available based on value of modulation index.

1)	Under modulation :	m<1, Em < Ec
	
2)	Critical modulation: m-1, Em = Ec
  
3)	Over modulation:	m>1, Em > Ec

Note: Keep all the switch faults in off position

## ALGORITHM
1.	Define Parameters
   
    First, define the parameters for your signals:
    
    •	Carrier frequency (fc)
    
    •	Modulating signal frequency (fm)
    
    •	Sampling frequency (Fs)
    
    •	Duration of the signal (T)

2.	Create a time vector based on the sampling frequency and duration.
 
3.	Create Modulating Signal:Define the modulating signal (message signal).

4.	Create Carrier Signal:Define the carrier signal.

5.	Perform Amplitude Modulation:Multiply the carrier signal by the modulating signal plus 1 (to ensure the modulation depth).

6.	Plot the Signals:Visualize the modulating, carrier, and modulated signals.

7.	Demodulate the AM Signal:To demodulate, you can use envelope detection. One way is to rectify the signal and then apply a low-pass filter.

8.	Plot the Demodulated Signal:Visualize the demodulated signal.

9.	Compare Signals:Compare the original modulating signal with the demodulated signal.

 ## PROCEDURE
•	Refer Algorithms and write code for the experiment.

•	Open SCILAB in System

•	Type your code in New Editor

•	Save the file

•	Execute the code

•	If any Error, correct it in code and execute again

•	Verify the generated waveform using Tabulation and Model Waveform

## MODEL GRAPH:
<img width="600" height="800" alt="image" src="https://github.com/user-attachments/assets/7bc77926-9c2a-42c6-994b-6c67433b11d2" />

## PROGRAM:
// =================================================================
// REVISED SCILAB CODE FOR AM GENERATION AND DETECTION
// Corrected for common SCILAB errors and using simpler demodulation
// =================================================================

// 1. Define Parameters
fc = 1000;    // Carrier frequency (1000 Hz)
fm = 100;     // Modulating signal frequency (100 Hz)
Fs = 10 * fc; // Sampling frequency
Ac = 5;       // Carrier signal amplitude
Am = 3;       // Modulating signal amplitude
T = 0.05;     // Duration of the signal
ma = Am / Ac; // Theoretical Modulation Index (0.6)

disp("Theoretical Modulation Index (ma) = " + string(ma));

// 2. Create a time vector
t = 0:1/Fs:T;
N = length(t); // Number of samples

// 3. Create Modulating Signal
m_t = Am * sin(2 * %pi * fm * t);

// 4. Create Carrier Signal
c_t = Ac * sin(2 * %pi * fc * t);

// 5. Perform Amplitude Modulation
// **CRITICAL:** Use .* for element-wise multiplication
s_t = Ac * (1 + ma * sin(2 * %pi * fm * t)) .* sin(2 * %pi * fc * t);

// 6. Plot the Signals
figure(1);
clf(); 

subplot(3, 1, 1);
plot(t, m_t);
title("1. Modulating Signal (Message)");
xgrid();

subplot(3, 1, 2);
plot(t, c_t);
title("2. Carrier Signal");
xgrid();

subplot(3, 1, 3);
plot(t, s_t);
title("3. Amplitude Modulated Signal (AM)");
xgrid();

// -----------------------------------------------------------------
// CALCULATION OF PRACTICAL MODULATION INDEX
// -----------------------------------------------------------------
Emax_practical = max(s_t); 
Emin_practical = min(s_t);
// For the positive envelope: Emax = max(s_t), and Emin = min(s_t) when m_t is negative.
// Since the envelope never crosses zero (ma < 1), we use the theoretical envelope points.
E_max_env = Ac * (1 + ma); // Theoretical peak of envelope
E_min_env = Ac * (1 - ma); // Theoretical minimum of envelope

ma_practical = (E_max_env - E_min_env) / (E_max_env + E_min_env);

disp("Practical Modulation Index (ma_practical) = " + string(ma_practical));


// -----------------------------------------------------------------
// 7. Demodulate the AM Signal (Envelope Detection using Moving Average)
// -----------------------------------------------------------------

// Step 1: Rectification (Half-wave, only keep positive values)
rectified_s_t = max(0, s_t);

// Step 2: Low-Pass Filtering (Using a Moving Average Filter as LPF approximation)
// The window size (M) must be > 1/fc and < 1/fm. Let's use

 
## TABULATION:
![WhatsApp Image 2025-11-19 at 19 31 14_590b1da2](https://github.com/user-attachments/assets/90fd5ab5-b5c0-4c0f-a8dc-85bba26b8191)


## CALCULATION:
![WhatsApp Image 2025-11-19 at 19 32 01_09ace973](https://github.com/user-attachments/assets/55bf5210-c084-4bb1-bb5b-a32c934c99d6)



## OUTPUT:
![WhatsApp Image 2025-11-19 at 19 31 31_6a86efe8](https://github.com/user-attachments/assets/92d7ea1c-a1a2-40a7-9d36-5b0b92f09bfa)

## RESULT:
Thus the amplitude modulation and demodulation is experimentally donev and the output is verified

