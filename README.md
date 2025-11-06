# EXP 3 : IIR-BUTTERWORTH-FITER-DESIGN

## AIM: 

 To design an IIR Butterworth filter  using SCILAB. 

## APPARATUS REQUIRED: 
PC installed with SCILAB. 

## PROGRAM (LPF): 
```
clc;
clear;

// Sampling frequency
Fs = 5000;           // Hz

// Cutoff frequency
fc = 1500;           // Hz (changed)
Wn = 2 * fc / Fs;    // Normalized (0 to 1)

// Butterworth LPF (order 2) — new coefficients
b = [0.2452  0.4904  0.2452];   // Numerator
a = [1.0000  -0.8683  0.2569];  // Denominator

// Frequency response (N = 512 points)
N = 512;
[H, f_norm] = frmag(b, a, N);

// Convert normalized freq to Hz
f = f_norm * Fs;

// Plot magnitude response in dB
clf();
plot(f, 20 * log10(H + %eps));
xlabel("Frequency (Hz)");
ylabel("Magnitude (dB)");
title("Butterworth Low Pass Filter (Order 2) — fc = 1500 Hz");
xgrid();
```


## PROGRAM (HPF): 
```
clc;
clear;

// Sampling frequency in Hz
Fs = 8000;

// Cutoff frequency in Hz
fc = 2000;

// Precomputed 2nd order Butterworth HPF coefficients
// These coefficients correspond to a 2nd order Butterworth HPF with cutoff ~ 2000 Hz
b = [0.6389 -1.2777 0.6389];    // Numerator
a = [1.0000 -0.5095 0.1825];    // Denominator

// Number of frequency points for response
N = 512;

// Calculate frequency response magnitude and normalized frequency vector
[H, f_norm] = frmag(b, a, N);

// Convert normalized frequency (0 to 0.5) to Hz (0 to Fs/2)
f = f_norm * Fs;

// Plot magnitude response in dB
clf();
plot(f, 20 * log10(H), 'LineWidth', 2);
xlabel("Frequency (Hz)");
ylabel("Magnitude (dB)");
title("Butterworth High Pass Filter (Order 2) Frequency Response");
xgrid();

// Optional: draw vertical line at cutoff frequency (fc)
xset("color", 2); // red color
plot([fc fc], [-80 5], '--');
xset("color", 1); // reset to black
```


## OUTPUT (LPF) : 

<img width="1918" height="1074" alt="image" src="https://github.com/user-attachments/assets/bed835ba-4d0f-4516-a9d4-7e9bd79073ce" />


## OUTPUT (HPF) : 

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/3d2acaa3-2f89-4d7d-b3ff-331c3703dad0" />


## RESULT: 

 A 2nd-order IIR Butterworth low-pass filter was designed with cutoff frequency 1500 Hz and sampling frequency 5000 Hz. The frequency response shows flat passband and sharp attenuation in the stopband.


