# Analog_communication_FDM
# Aim:

To study and implement Frequency Division Multiplexing (FDM) and Demultiplexing using SCILAB by combining six different message signals into a single composite signal for transmission and then recovering each message signal at the receiver through demodulation and filtering.

# Apparatus Required:

Computer system with SCILAB software installed.

# Theory:
Frequency Division Multiplexing (FDM) is a technique in which multiple message signals are transmitted simultaneously over a single communication channel by assigning each signal a unique carrier frequency. Each message is modulated with its respective carrier so that their frequency bands do not overlap. These modulated signals are then combined to form a single multiplexed signal for transmission. At the receiver end, the signal is demultiplexed by using the same carrier frequencies for demodulation, followed by low-pass filtering to recover the original baseband signals. FDM is widely used in radio broadcasting, cable television, and satellite communication systems where efficient bandwidth utilization is essential.

# Algorithm:
1.Start the program and initialize the sampling frequency fs and time vector t. 

2.Generate six message signals of different frequencies (150 Hz to 900 Hz) using sine functions.

3.Assign six distinct carrier frequencies (3 kHz to 13 kHz) to each message signal to avoid overlap. 

4.Modulate each message signal by multiplying it with its corresponding carrier (Amplitude Modulation).

5.Add all modulated signals to obtain the combined FDM signal representing multiple channels. 

6.Plot all six message signals and the multiplexed signal for observation. 

7.Demodulate each signal by multiplying the FDM signal with its corresponding carrier frequency. 

8.Apply a low-pass filter to extract the original baseband signals (recovering the messages). 
9.Plot the demodulated signals to verify successful recovery. 10.End the program after confirming proper multiplexing and demultiplexing operation.

# Code:
```asm
clc;
clear;
close;

fs = 20000;
t = 0:1/fs:0.02;

fm = [75,150,225,300,375,400];
m = [];

for i = 1:6
    m(i, :) = sin(2*%pi*fm(i)*t);
end

fc = [2000, 3000, 4000, 5000, 6000, 7000];

fdm = zeros(1, length(t));
for i = 1:6
    c = cos(2*%pi*fc(i)*t);
    s = m(i, :) .* c;
    fdm = fdm + s;
end

scf(1);
clf;
for i = 1:6
    subplot(6,1,i);
    plot(t, m(i, :));

end

scf(2);
clf;
plot(t, fdm);

demod = [];
for i = 1:6
    c = cos(2*%pi*fc(i)*t);
    x = fdm .* c;
    h = ones(1,100)/100;
    y = conv(x, h, 'same');
    demod(i, :) = y;
end

scf(3);
clf;
for i = 1:6
    subplot(6,1,i);
    plot(t, demod(i, :));
end

disp("FDM and Demultiplexing completed successfully!");
```

# Output

<img width="756" height="624" alt="image" src="https://github.com/user-attachments/assets/52f5af6b-acc1-4d4e-9652-a5ed21023c1e" />

<img width="760" height="626" alt="image" src="https://github.com/user-attachments/assets/c7c85329-78f1-43e0-abbb-4fd245e4f280" />

<img width="765" height="622" alt="image" src="https://github.com/user-attachments/assets/d98c0287-03d8-4588-afbd-b8baec9a169c" />


# Calculation

![WhatsApp Image 2025-11-28 at 08 11 27_1341fb41](https://github.com/user-attachments/assets/b2bc0824-2b84-43cb-b38c-a170ff8720da)

![WhatsApp Image 2025-11-28 at 08 11 27_217a0b63](https://github.com/user-attachments/assets/9beeceb9-c62e-49ca-9259-6805481ac5c0)


# Result 

Six different message signals were generated and modulated using FDM. All modulated signals were added to form a multiplexed FDM signal. Each message was successfully recovered using coherent demodulation followed by low-pass filtering. The plots confirmed accurate multiplexing and demultiplexing.

