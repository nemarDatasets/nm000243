[![DOI](https://img.shields.io/badge/DOI-10.82901%2Fnemar.nm000243-blue)](https://doi.org/10.82901/nemar.nm000243)

# BNCI 2016-002 Emergency Braking during Simulated Driving dataset

BNCI 2016-002 Emergency Braking during Simulated Driving dataset.

## Dataset Overview

- **Code**: BNCI2016-002
- **Paradigm**: p300
- **DOI**: 10.1088/1741-2560/8/5/056001
- **Subjects**: 15
- **Sessions per subject**: 1
- **Events**: Target=1, NonTarget=2
- **Trial interval**: [-0.5, 1.0] s
- **File format**: .mat
- **Data preprocessed**: True
- **Contributing labs**: Machine Learning Group, Berlin Institute of Technology, Bernstein Focus Neurotechnology, Berlin, Neurophysics Group, Charité University Medicine Berlin, Intelligent Data Analysis Group, Fraunhofer Institute FIRST

## Acquisition

- **Sampling rate**: 200.0 Hz
- **Number of channels**: 59
- **Channel types**: eeg=59, emg=1, eog=2, misc=7
- **Channel names**: AF3, AF4, C1, C2, C3, C4, C5, C6, CP1, CP2, CP3, CP4, CP5, CP6, CPz, Cz, EMGf, EOGh, EOGv, F1, F2, F3, F4, F5, F6, F7, F8, FC1, FC2, FC3, FC4, FC5, FC6, FCz, FT7, FT8, Fp1, Fp2, Fz, O1, O2, Oz, P1, P10, P2, P3, P4, P5, P6, P7, P8, P9, PO3, PO4, PO7, PO8, POz, Pz, T7, T8, TP7, TP8, brake, dist_to_lead, gas, lead_brake, lead_gas, wheel_X, wheel_Y
- **Montage**: extended 10-20
- **Hardware**: BrainAmp
- **Software**: TORCS
- **Reference**: nose
- **Sensor type**: Ag/AgCl
- **Line frequency**: 50.0 Hz
- **Online filters**: {'highpass_hz': 0.1, 'lowpass_hz': 250}
- **Impedance threshold**: {'eeg': 20, 'emg': 50} kOhm
- **Cap manufacturer**: Easycap
- **Cap model**: Easycap
- **Auxiliary channels**: EOG (2 ch, vertical, horizontal), EMG (1 ch), technical_markers

## Participants

- **Number of subjects**: 15
- **Health status**: healthy
- **Age**: mean=30.6, std=5.4
- **Gender distribution**: male=14, female=4
- **Handedness**: right-handed
- **BCI experience**: naive
- **Species**: human

## Experimental Protocol

- **Paradigm**: p300
- **Task type**: driving_simulation
- **Number of classes**: 2
- **Class labels**: Target, NonTarget
- **Trial duration**: 3.0 s
- **Study design**: Participants drove a virtual racing car using steering wheel and gas/brake pedals, tightly following a computer-controlled lead vehicle at 100 km/h. The lead vehicle occasionally decelerated abruptly (20-40s inter-stimulus-interval) to 60-80 km/h, requiring immediate emergency braking. Three blocks of 45 min each with 10-15 min rest between blocks.
- **Feedback type**: visual (colored circle indicating distance: green <20m, yellow otherwise; brakelight flashing)
- **Stimulus type**: emergency_braking_scenario
- **Stimulus modalities**: visual, multisensory
- **Primary modality**: visual
- **Synchronicity**: asynchronous
- **Mode**: online
- **Training/test split**: True
- **Instructions**: Drive a virtual racing car using steering wheel and gas/brake pedals, tightly follow the lead vehicle within 20m at 100 km/h. Perform immediate emergency braking when the lead vehicle decelerates abruptly to avoid a crash.
- **Stimulus presentation**: isi_range=20-40 seconds, deceleration_range=60-80 km/h, brakelight=flashing, oncoming_traffic=present, sharp_curves=present

## HED Event Annotations

Schema: HED 8.4.0 | Browse: https://www.hedtags.org/hed-schema-browser

```
  Target
    ├─ Sensory-event
    ├─ Experimental-stimulus
    ├─ Visual-presentation
    └─ Target

  NonTarget
    ├─ Sensory-event
    ├─ Experimental-stimulus
    ├─ Visual-presentation
    └─ Non-target

```
## Paradigm-Specific Parameters

- **Detected paradigm**: p300

## Data Structure

- **Trials**: ~99 emergency braking events per subject (test set)
- **Blocks per session**: 3
- **Block duration**: 2700.0 s
- **Trials context**: Emergency braking events with 20-40s inter-stimulus-interval, total ~225 events across 3 blocks per subject

## Preprocessing

- **Data state**: preprocessed
- **Preprocessing applied**: True
- **Steps**: lowpass filtering, bandpass filtering, notch filtering, rectification, downsampling/upsampling, baseline correction, synchronization
- **Highpass filter**: 0.1 Hz
- **Lowpass filter**: 45.0 Hz
- **Bandpass filter**: [15.0, 90.0]
- **Notch filter**: 50.0 Hz
- **Filter type**: Chebychev type II (EEG lowpass), Elliptic (EMG bandpass), digital (notch)
- **Filter order**: tenth-order (EEG), sixth-order (EMG), second-order (notch)
- **Re-reference**: nose
- **Downsampled to**: 200.0 Hz
- **Epoch window**: [-0.3, 1.2]
- **Notes**: EEG lowpass filtered at 45 Hz (causal). EMG bandpass filtered 15-90 Hz with 50 Hz notch and rectified. All signals synchronized and resampled to 200 Hz. Baseline correction using first 100 ms.

## Signal Processing

- **Classifiers**: RLDA, Regularized Linear Discriminant Analysis, Shrinkage LDA
- **Feature extraction**: Event-Related Potentials, Spatio-temporal features, Bi-serial correlation, Area Under Curve
- **Spatial filters**: Artifact rejection based on spectral power

## Cross-Validation

- **Method**: sequential temporal split
- **Evaluation type**: temporal_validation

## Performance (Original Study)

- **Auc**: 0.5
- **Braking Time Reduction Ms**: 130
- **Braking Distance Reduction M**: 3.66

## BCI Application

- **Applications**: driving_assistance, emergency_braking_detection, neuroergonomics
- **Environment**: laboratory
- **Online feedback**: True

## Tags

- **Pathology**: Healthy
- **Modality**: Visual, Multisensory
- **Type**: Driving, Neuroergonomics

## Documentation

- **Description**: Emergency braking detection during simulated driving using EEG and EMG to predict driver's braking intention before behavioral response.
- **DOI**: 10.1088/1741-2560/8/5/056001
- **Associated paper DOI**: 10.1088/1741-2560/8/5/056001
- **License**: CC-BY-NC-ND-4.0
- **Investigators**: Stefan Haufe, Matthias S Treder, Manfred F Gugler, Max Sagebaum, Gabriel Curio, Benjamin Blankertz
- **Senior author**: Benjamin Blankertz
- **Contact**: stefan.haufe@tu-berlin.de
- **Institution**: Berlin Institute of Technology
- **Department**: Machine Learning Group, Department of Computer Science
- **Address**: Franklinstraße 28/29, D-10587 Berlin, Germany
- **Country**: Germany
- **Repository**: BNCI Horizon
- **Publication year**: 2011
- **Funding**: DFG grant; BMBF grant; Bernstein Focus Neurotechnology, Berlin
- **Ethics approval**: IRB of Charité University Medicine, Berlin; Declaration of Helsinki; Written informed consent from all participants
- **Keywords**: emergency braking, driving simulation, EEG, EMG, brain-computer interface, neuroergonomics, event-related potentials, machine learning, driver assistance

## References

Haufe, S., Treder, M. S., Gugler, M. F., Sagebaum, M., Curio, G., & Blankertz, B. (2011). EEG potentials predict upcoming emergency brakings during simulated driving. Journal of Neural Engineering, 8(5), 056001. https://doi.org/10.1088/1741-2560/8/5/056001

Notes

.. versionadded:: 1.3.0

This dataset is valuable for research on:

- Predictive braking assistance systems - Neuroergonomics and driving safety - Real-time detection of emergency intentions - Multimodal biosignal integration (EEG + EMG + vehicle dynamics)

The paradigm represents a unique blend of ERP (event-related potential) analysis with ecological validity in a naturalistic driving context.

**Data Availability**: Currently 15 of 18 subjects are available. Files are hosted at the BBCI (Berlin Brain-Computer Interface) archive.

License: Creative Commons Attribution Non-Commercial No Derivatives (CC BY-NC-ND 4.0)
Appelhoff, S., Sanderson, M., Brooks, T., Vliet, M., Quentin, R., Holdgraf, C., Chaumon, M., Mikulan, E., Tavabi, K., Hochenberger, R., Welke, D., Brunner, C., Rockhill, A., Larson, E., Gramfort, A. and Jas, M. (2019). MNE-BIDS: Organizing electrophysiological data into the BIDS format and facilitating their analysis. Journal of Open Source Software 4: (1896). https://doi.org/10.21105/joss.01896

Pernet, C. R., Appelhoff, S., Gorgolewski, K. J., Flandin, G., Phillips, C., Delorme, A., Oostenveld, R. (2019). EEG-BIDS, an extension to the brain imaging data structure for electroencephalography. Scientific Data, 6, 103. https://doi.org/10.1038/s41597-019-0104-8

---
Generated by MOABB 1.5.0 (Mother of All BCI Benchmarks)
https://github.com/NeuroTechX/moabb
