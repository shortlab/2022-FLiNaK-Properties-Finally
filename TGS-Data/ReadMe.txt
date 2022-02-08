Each folder contains raw signal vs time files for both the long and short timescale TGS signals.
Each folder contains a summary file of the fitted results for thermal diffusivity (Thermal.txt) and sound speed (Acoustic.txt) as a function of temperature
Naming convention for raw signal files is as follows:
C2 = Short timescale acosutic signals
C3 = Long timescale thermal signals
T_#, # is the uncorrected temperature in degC (i.e actual temperture is stated temp + 3 +/- 5.5 degC)
ND_#, # is the OD of the ND filter used on the reference probe light
GS_#, is the grating spacing in um for a 8 cm lens. a 15 cm lens is used so the appropriate conversion is require
S indicates singals that are taken as the sample is heating up
SD indicages signals that are taken as the sample is cooling down

### Grating Spacing Conversion in Python ###		
d1 = float((filename.split('_'))[5])*1e-6 # 8 cm gratting spacing (m)
wavelength = 532E-9 # Pump Wavlength (m)
theta1 = np.arcsin(wavelength/(2*d1)) # 8cm Intersection angle (radians)
s = np.tan(theta1)*(0.08) # half of the distance between the two beams at the lens
theta2 = np.arctan(s/0.15) # 15cm Intersection angle (radians)
d2 = wavelength/(2*np.sin(theta2)) # 15cm gratting spacing (m)
