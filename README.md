# photometry

A simple labview .vi for fibre photometry acquisition. Allows creation of modulated led excitation, collection of resultant fluorescence emission, and online demodulation of the signal. Files are saved both as raw data and as downsampled demdulated signal. an be easily combined with TTL inputs to sync to behvaiour.

The .VI has three parts:

1. Generates and sends two sine wave modulatory signals to drive two thorlabs led drivers (210 Hz and 500 Hz by default). This allows separation of autofluorescence and excitation fluorescence from the same sensor.

2. Acquires the resulting emission fluorescence signal from up to 4 separate photosensors and saves the raw data.

3. Performs standard quadrature demodulation of each channel of fluorescence signal at the frequencies sent to the led drivers, displays the resultant demodulation on screen, and saves the demodulated signal.

All setup is standard using NIDAQmx in LabView, and acquisition and modulation channels are assigned using the standard DAQ assistant as specified here:

http://www.ni.com/tutorial/2744/en/


Versions and dependencies:

All experiments were run on a standard machine running Windows 10;
Function of the code was also tested on windows 7;
Data input and output was achieved via an NI USB-6341 National Instruments board.

Software used:
Labview v15 
NI-DAQmx 16.1

Two subVIs (included in zip file): 
Convert Digital Waveform to analog waveforms (SubVI).vi
decimate.vi


Installation guide:

There is no installation apart from standard LabView and NIDAQmx installations, the code is a simply a combination of standard pre-existing functions in LabView.
Open ‘photometry_bellot_2020.VI’ in LabView, set acquisition channels as standard in DAQ assistant that correspond to led modulators and fluorescence sensors.

Instructions for use / demo:

To run, fluorescence excitation driven by led output is measured via standard optics (described in methods). For example, a 473 nm led driven at 210 Hz will excite GCaMP6f, and result in an emission fluorescence signal modulated at 210 Hz at the sensor. This is acquired through the NI board and DAQ assistant. Both the raw data and demodulated data at 210Hz are then displayed in real time in the GUI.

Demodulated and raw data are saved as .tdms files, with names specified in the text boxes at the bottom left of the screen.

Small adjustments to the amplitude and offset of each output (to control led brightness) can be made with the input boxes at the bottom right of the screen.

We have also added functionality to add digital TTL-based timestamps to the same data files, but this functionality was not used in this study.

Finally, we have not included demo data, as this is an acquisition system.


