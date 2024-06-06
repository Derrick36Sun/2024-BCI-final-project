# WAY-EEG-GAL Dataset Description and Quality Evaluation

## Data Description

### Overview
This dataset, WAY-EEG-GAL (Wearable interfaces for hAnd function recoverY, a European project), contains multi-channel EEG recordings collected during an experimental study focusing on the neural dynamics of motor control during grasp and lift tasks.

### Experimental Design/Paradigm
- **Design:** Within-subjects
- **Participants:** 12
- **Total Trials:** 3,936 (328 trials per participant)
- **Task:** Grasp and lift
  - Reach for a small object
  - Grasp using index finger and thumb
  - Lift a few centimeters
  - Hold stably for a couple of seconds
  - Replace and release the object
- **Cues:** Beginning of reach and lowering of the object cued by an LED; task pace determined by the participant
- **Variations:** Object weight (light, medium, heavy) and surface friction (high, medium, low)

### Procedure for Collecting Data
- **Participants:** Seated comfortably
- **Instructions:** Follow LED cues
- **Data Recorded:**
  - **EEG, EMG, Kinematic and Force Data**
  - **Procedure:**
    - Reaching for the object upon the LED cue
    - Grasping and lifting the object
    - Holding the object stably
    - Lowering and releasing the object upon the LED cue

### Hardware and Software Used
- **EEG Hardware:** BrainAmp EEG signal amplifier and EEG cap
  - **Sampling Rate:** 5 kHz (initial), 500 Hz (processed)
  - **Band-Pass Filter:** 0.016 to 1,000 Hz
  - **Software:** VisionRecorder and BCI2000
- **EMG and Other Signals:**
  - **Software:** SC/ZOOM
  - **Sampling Rate:** 4 kHz (EMG), 500 Hz (others)
- **Kinetic and Kinematic Sensors:** Recorded positions of the arm, thumb, index finger, and the object, and forces applied by the precision grip
- **Additional States Recorded:** Object's contact surface (sandpaper, suede, silk), weight (165 g, 330 g, 660 g), LED indications for trial start/end and researcher to change contact surfaces

### Data Size
- **Participants:** 12
- **Trials per Participant:** 328
- **Total Dataset:** Includes data from all channels and sensors recorded during the trials

### Number of Channels
- **EEG:** 32 channels
- **EMG:** 5 channels
- **Additional Sensors:** Position and force sensors for the arm, thumb, index finger, and object

### Sampling Rate
- **EEG:** 500 Hz (processed from an initial 5 kHz sampling rate)
- **EMG:** 4 kHz
- **Other Signals:** 500 Hz

### Data Source and Ownership
- **Website:** [Kaggle](https://www.kaggle.com/c/grasp-and-lift-eeg-detection/data)
- **Owner:** Umeå University
- **Source:** Participants recruited through an advertisement at Umeå University, compensated 100 SEK per hour for at least two hours of participation
- **Selection Criteria:** Right-handed individuals, 12 participants (8 females, aged 19-35)
- **Ethics:** Informed consent obtained, study approved by the Ethical Committee at Umeå University

## Quality Evaluation

### Surveying and Analyzing Existing Literature

1. **Established Protocols:**
   - The experimental design involving grasp and lift tasks is well-documented in motor control and neurophysiological studies.
   - Similar protocols have been used to investigate motor planning and execution, supporting the reliability of this study's design (e.g., Johansson & Westling, 1984).

2. **Multimodal Sensory Activity:**
   - The correct completion of the grasp and lift (GAL) task depends on multimodal sensory activity correlated with specific events such as object contact, lift-off, and replacement.
   - This aligns with the Discrete Event Sensory Control (DESC) policy, where feedforward control routines operate between sensed discrete events (Johansson & Flanagan, 2009).

3. **EEG Methodology:**
   - The use of a 32-channel EEG system to capture neural dynamics is standard in neuroscience research.
   - Literature supports the reliability of BrainAmp EEG signal amplifiers in high-resolution EEG studies (e.g., Debener et al., 2005).

4. **Signal Processing:**
   - The data preprocessing steps, including cross-correlation synchronization and mean removal from EMG signals, align with best practices in EEG data handling (e.g., Makeig et al., 2004).

### Analyzing the Hidden Independent Components within EEG Using ICA with ICLabel

| EEG (32 channels, 1 dataset) | Bandpass filter | ASR | Brain | Muscle | Eye | Heart | Line | Channel noise | Other | Raw |
|-------------------------------|----------------|-----|-------|--------|-----|-------|------|---------------|-------|-----|
| 0                             | 0              | 1   | 0     | 0      | 0   | 31    |     |               |       |     |
| Filtered                      | ✓              | 0   | 0     | 1      | 0   | 0     |     |               |       |     |
| ASR                           | ✓              | ✓   | 9     | 1      | 1   | 0     | 0   |               | 21    |     |
