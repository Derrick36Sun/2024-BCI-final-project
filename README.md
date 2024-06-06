# 2024-BCI-final-project
## Data Description
1. Overview:<br>
This dataset, WAY-EEG-GAL (Wearable interfaces for hAnd function recoverY, a European project), contains multi-channel EEG recordings collected during an experimental study focusing on the neural dynamics of motor control during grasp and lift tasks. 
3. Experimental Design/Paradigm:<br>
The experiment employed a within-subjects design where 12 participants performed a total of 3,936 grasp and lift trials (328 trials per participant). Each trial involved reaching for a small object, grasping it using the index finger and thumb, lifting it a few centimeters, holding it stably for a couple of seconds, and then replacing and releasing the object. The beginning of the reach and the lowering of the object were cued by an LED, but the pace of the task was otherwise determined by the participant.The trials varied in terms of object weight (light, medium, heavy) and surface friction (high, medium, low).
4. Procedure for Collecting Data:<br>
Participants were seated comfortably and instructed to follow the cues provided by the LED. EEG, EMG, and various kinematic and force data were recorded during the trials. The procedure involved:
* Reaching for the object upon the LED cue.
* Grasping and lifting the object.
* Holding the object stably.
* Lowering and releasing the object upon the LED cue.
4. Hardware and Software Used:
* EEG Hardware: The EEG data were collected using a BrainAmp EEG signal amplifier and an EEG cap. The BrainAmp amplifier sampled at 5 kHz and band-pass filtered each channel from 0.016 to 1,000 Hz. The amplifier software VisionRecorder digitized and filtered the raw EEG data and passed it to BCI2000 for data storage. The amplifier software set a target sampling rate of 500 Hz, utilizing an adapted low-pass filter to prevent aliasing.
* EMG and Other Signals: All other signals were sampled using SC/ZOOM, developed at the Department of Integrative Medical Biology, Umeå University. The EMG signals were sampled at 4 kHz, and all other signals at 500 Hz.
* Kinetic and Kinematic Sensors: These sensors recorded the positions of the arm, thumb, index finger, and the object, as well as the forces applied by the precision grip. Additional recorded states included the object's contact surface (sandpaper, suede, silk), weight (165 g, 330 g, 660 g), the LED indicating trial start and end, and the LED indicating to the researcher to change contact surfaces.
5. Data Size: <br>
The dataset comprises recordings from 12 participants, with each participant performing 328 trials. The total dataset includes data from all channels and sensors recorded during the trials.
6. Number of Channels:<br>
* EEG: 32 channels.
* EMG: 5 channels.
Additional Sensors: Position and force sensors for the arm, thumb, index finger, and object.
7. Sampling Rate:<br>
* EEG: 500 Hz (processed from an initial 5 kHz sampling rate).
* EMG: 4 kHz.
* Other Signals: 500 Hz.
8. Data Source and Ownership:<br>
* Website: https://www.kaggle.com/c/grasp-and-lift-eeg-detection/data
* Owner: The study was conducted at Umeå University.
* Source: Participants were recruited through an advertisement at Umeå University, promising 100 SEK per hour for at least two hours of participation. The selection criteria included right-handed individuals only. A total of 12 participants (8 females, aged 19-35) were selected. All participants signed a consent form in accordance with the Declaration of Helsinki, and the experimental procedures were approved by the Ethical Committee at Umeå University. Participants were informed that the aim of the study was to investigate how the brain and muscles are coordinated when handling an object.
