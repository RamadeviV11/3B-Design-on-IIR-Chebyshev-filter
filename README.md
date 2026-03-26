# IIR-FILTER-DESIGN

# EXP 3 B: DESIGN OF LOW PASS CHEBYSHEV IIR FILTER USING BILINEAR TRANSFORMATION

# AIM: 

# To a design of low pass Chebyshev IIR filter using Bilinear Transformation.

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
```
clc ; 
close ; 
wp=input('Enter the pass band frequency (Radians )= ' ); 
ws=input('Enter the stop band frequency (Radians )= ' ); 
alphap=input( ' Enter the pass band attenuation (dB)=' ); 
alphas=input( ' Enter the stop band attenuation(dB)=' ); 
T=input('Enter the Value of sampling Time='); 
//Pre warping- Bilinear Transformation 
omegap=(2/T)*tan(wp/2); 
disp(omegap,'omegap='); 
omegas=(2/T)*tan(ws/2); 
disp(omegas,'omegas='); 
//Order of the filter 
N=acosh(sqrt(((10^(0.1*alphas))-1)/((10^(0.1*alphap))-1)))/(acosh(omegas/omegap));  
disp(N,'N='); 
N=ceil(N); 
disp(N,'Round off value of N='); 
//Cut off frequency 
omegac=omegap/(((10^(0.1*alphap)) -1)^(1/(2* N))); 
disp(omegac,'omegac='); 
Epsilon = sqrt ((10^(0.1*alphap))-1); 
disp(Epsilon,'Epsilon='); 
[pols ,gn] = zpch1(N, Epsilon,omegap ); 
disp(gn,'Gain'); 
disp(pols,'Poles'); 
hs=poly(gn,'s','coeff')/real(poly(pols,'s'));  
disp(hs,'Analog Low pass Chebyshev Filter Transfer function'); 
z=poly(0,'z');//Defining variable z
Hz=horner(hs,(2/ T)*((z -1)/(z+1)))// Bilinear Transformation 
disp(Hz,'Digital LPF Transfer function H(Z)='); 
HW=frmag(Hz,512); // Frequency response 
w=0:%pi/511:%pi ; 
plot(w/%pi,abs(HW)); 
xlabel(' Normalized Digital Frequency w'); 
ylabel('Magnitude '); 
title(' Frequency Response of Chebyshev IIR LPF');
```

# CALCULATION:

![WhatsApp Image 2026-03-26 at 6 57 31 PM](https://github.com/user-attachments/assets/95793d0c-2df9-45fe-aa11-18bb24e41c9b)
![WhatsApp Image 2026-03-26 at 6 57 31 PM (1)](https://github.com/user-attachments/assets/cc74f66d-7dd6-4eaa-9440-45ff6b1ef214)


# OUTPUT: 

![WhatsApp Image 2026-03-26 at 6 57 30 PM](https://github.com/user-attachments/assets/856031a0-c848-4c7f-bb27-aacdddd1d36e)



# RESULT: 
Thus design of Chebyshev Low pass IIR filter waveforms were plotted and output was
verified.
