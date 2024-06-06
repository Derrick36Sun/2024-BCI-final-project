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

## Usage

### Pip Installs

```python
!pip install mne
!pip install asrpy
```
### Instructions

1. The code is recommended to run in [Google Colab](https://colab.google/)
3. Download the EEG dataset from here: Grasp-and-Lift EEG Detection Data.
4. Put the dataset and .ipynb files into the same folder.
5. Change `FILE_PATH` to the relative path of the downloaded EEG dataset in Google Drive.

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

| EEG (32 channels, 1 dataset) | Bandpass filter | ASR | Brain | Muscle | Eye | Heart | Line | Channel noise | Other | 
|-------------------------------|----------------|-----|-------|--------|-----|-------|------|---------------|-------|
| Raw                           |                |     |    0  |    0   |   1 |   0   |   0  |      0       |    31   | 
| Filtered                      | ✓              |    |    0  |    0   |  1 |    0  |    0 |       0        |    31   |   
| ASR                           | ✓              | ✓   |   9   |    1   |  1  |   0   |  0  |        0       |   21  |  

# README.md

## Introduction
The primary aim of our final project is to design and implement an EEG data processing pipeline tailored for motor Brain-Computer Interface (BCI) applications. The Brain-Computer Interface (BCI) system and the WAY-EEG-GAL dataset are designed to investigate the neural dynamics of motor control during grasp and lift tasks. We utilize the dataset in neurorehabilitation, assistive technology, and scientific research, providing a valuable resource for studying the neural mechanisms of motor control and sensory-motor integration.

## Model Framework

<img src="https://github.com/Derrick36Sun/2024-BCI-final-project/assets/68135531/f35fd36a-900e-4c73-8291-08a69db5c1b8" width="700"/>

### Raw

<img src="https://github.com/Derrick36Sun/2024-BCI-final-project/assets/68135531/91a7723f-1fe9-41be-9149-12c16d02e0f1" width="700"/>

### Filtered

<img src="https://github.com/Derrick36Sun/2024-BCI-final-project/assets/68135531/8fe551a6-3b51-43d0-ba1a-b4e0abff9323" width="700"/>

### Raw Independent Component Analysis

<img src="https://github.com/Derrick36Sun/2024-BCI-final-project/assets/68135531/11b51fdc-5f77-411e-8e17-afcd6164a5c1" width="700"/><br>
<img src="https://github.com/Derrick36Sun/2024-BCI-final-project/assets/68135531/e65b67fb-af2f-48e2-a6fb-64b5f747f9ed" width="700"/>

### Filtered Independent Component Analysis

<img src="https://github.com/Derrick36Sun/2024-BCI-final-project/assets/68135531/16ff1c27-89bf-4e32-be7e-2c9a12b797fb" width="700"/><br>
<img src="https://github.com/Derrick36Sun/2024-BCI-final-project/assets/68135531/fa4ffc2e-5aeb-4a29-a6b2-b7cdb47e636b" width="700"/><br>
<img src="https://github.com/Derrick36Sun/2024-BCI-final-project/assets/68135531/6e9e56e2-5b89-4718-b315-a0bf58c7a5f1" width="700"/>

### Filtered ASR Independent Component Analysis

<img src="https://github.com/Derrick36Sun/2024-BCI-final-project/assets/68135531/f0c81691-f1cb-44aa-82d9-a7c5fadb824c" width="700"/><br>
<img src="https://github.com/Derrick36Sun/2024-BCI-final-project/assets/68135531/7ab83108-6572-41fc-b4fb-0f149abf1b8b" width="700"/><br>
<img src="https://github.com/Derrick36Sun/2024-BCI-final-project/assets/68135531/d257852f-e7f1-4f8e-9034-347f5dfcdb46" width="700"/>

### Autoreject Before (Top) vs. After (Bottom)
<img src="https://github.com/Derrick36Sun/2024-BCI-final-project/assets/68135531/4b3de60c-862b-4c3c-b80c-7bf03fe2379e" width="700"/><br>
<img src="https://github.com/Derrick36Sun/2024-BCI-final-project/assets/68135531/3a02a9e8-2b10-4bd2-9dd0-0452638c60c4" width="700"/>

## Validation
To evaluate the trained classifier, we use cross-validation on the dataset to assess its performance in accurately classifying motor imagery tasks. We also analyze classification metrics such as accuracy, precision, recall, and F1-score to quantify the classifier's effectiveness.

## Usage
Describe the usage of their BCI model's code. Explain the required environment and dependencies needed to run the code. Describe any configurable options or parameters within the code. Provide instructions on how to execute the code.

## Results
Comparison of preprocessing methods on classifier performance:

| Preprocessing Method      | SVM   | KNN   |
|---------------------------|-------|-------|
| Raw                       | X     | X     |
| Filtered                  | 44.37%| 43.71%|
| Filtered + ICA*           | 54.97%| 46.36%|
| Filtered + ICA + ASR*     | 40.40%| 42.38%|
| Filtered + Auto-Reject    | 36.43%| 33.33%|


### Confusion matrix

<img src="https://github.com/Derrick36Sun/2024-BCI-final-project/assets/68135531/c7334489-f5c1-4160-896b-6b90aabe55e2" width="700"/>


## References

1. Luciw, M., Jarocka, E., & Edin, B. (2014). Multi-channel EEG recordings during 3,936 grasp and lift trials with varying weight and friction. Scientific Data, 1, 140047. https://doi.org/10.1038/sdata.2014.47

1. Liao, L. D., Chen, C. Y., Wang, I. J., et al. (2012). Gaming control using a wearable and wireless EEG-based brain-computer interface device with novel dry foam-based sensors. *Journal of NeuroEngineering and Rehabilitation, 9*(1), 5. https://doi.org/10.1186/1743-0003-9-5

2. McFarland, D. J., Daly, J., Boulay, C., & Parvaz, M. (2017). Therapeutic applications of BCI technologies. *Brain-Computer Interfaces, 47*(1-2), 37-52. https://doi.org/10.1080/2326263X.2017.1307625

3. Stokes, M., & James, C. J. (2006). Brain-computer interfacing (BCI) in rehabilitation. *Clinical Neurophysiology, 117*(Supplement 1), 28. https://doi.org/10.1016/j.clinph.2006.07.077

4. Tarafdar, K. K., Pradhan, B. K., Nayak, S. K., Khasnobish, A., Bhattacharyya, S., & Pal, K. (2019). Electroencephalogram-based brain–computer interface systems for controlling rehabilitative devices. *Bioelectronics and Medical Devices.*

5. Vasiljevic, G. A., & Miranda, L. C. (2020). A general model for electroencephalography-controlled brain-computer interface games. In *Computational Science and Its Applications – ICCSA 2020* (pp. 174-189).

6. Foong, R., Ang, K. K., Quek, C., et al. (2020). Assessment of the efficacy of EEG-based MI-BCI with visual feedback and EEG correlates of mental fatigue for upper-limb stroke rehabilitation. *IEEE Transactions on Biomedical Engineering, 67*(3), 786-795. https://doi.org/10.1109/TBME.2019.2921198

7. Quiles, E., Suay, F., Candela, G., Chio, N., Jiménez, M., & Álvarez-Kurogi, L. (2020). Low-cost robotic guide based on a motor imagery brain-computer interface for arm assisted rehabilitation. *International Journal of Environmental Research and Public Health, 17*(3), 699. https://doi.org/10.3390/ijerph17030699

8. Tong, Y., Pendy, J. T., Jr, Li, W. A., et al. (2017). Motor imagery-based rehabilitation: Potential neural correlates and clinical application for functional recovery of motor deficits after stroke. *Aging and Disease, 8*(3), 364-371. https://doi.org/10.14336/AD.2016.1012

9. Gustavsson, M., Kjörk, E. K., Erhardsson, M., & Alt Murphy, M. (2022). Virtual reality gaming in rehabilitation after stroke - user experiences and perceptions. *Disability and Rehabilitation, 44*(22), 6759-6765. https://doi.org/10.1080/09638288.2021.1972351

