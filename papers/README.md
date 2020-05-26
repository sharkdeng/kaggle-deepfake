# Overview
This list shows all papers I have read. I would describe them by levels, filename, summary, keywords, and critics. 
- **Level** has *relevant*, *not relevant*, *not sure*, accompanied by a number which indicates the significance of the paper in my opinion. ranging from 0 to 5. 0 means not important(didn't do experiments), 5 means very important.
- **Filename** is for quick access the paper.
- **Summary** is an except from original abstract of the paper.

# Methods
1. In Ictu Oculi: Exposing AI Created Fake Videos by Detecting Eye Blinking
- **Level**: Relevant (0)
- **Filename**: p-wifs2018.pdf 
- **Summary**: Our method is based on detection of eye blinking in the videos, which is a physio-logical signal that is not well presented in the synthesized fake videos. Our method is evaluated over benchmarks of eye-blinking detection datasets and shows promising per- formance on detecting videos generated with DNN based software DeepFake.
- **Keywords**: fake video detection, eye blinking
- **Critics**:
Not done experiments on this.



2. Extracting camera-based fingerprints for video forensics
- **Level**: Relevant (1)
- **Filename**: p-Verdoliva_Extracting_camera-based_fingerprints_for_video_forensics_CVPRW_2019_paper.pdf
- **Summary**:
- **Keywords**: fingerprint, video forensics
- **Critics**:



3. Exposing DeepFake Videos By Detecting Face Warping Artifacts 
- **Level**: Relevant (0)
- **Filename**: p-Li_Exposing_DeepFake_Videos_By_Detecting_Face_Warping_Artifacts_CVPRW_2019_paper.pdf
- **Summary**:
- **Keywords**:
- **Critics**:


# Face Detector
Regarding finding a good face detector, after observing the deepfake dataset, I found these aspects. 
- small face (BlazeFace cannot detect some samll face)
- side face (head  back). front face
- dark illumination
- error rate(BlazeFace would be too positive)

2. DSFD: Dual Shot Face Detector
- **Level**: Relevant (0)
- **Filename**: p-Li_DSFD_Dual_Shot_Face_Detector_CVPR_2019_paper.pdf
- **Summary**:
- **Keywords**: face detector
- **Critics**:
Although the paper image show it can detect small faces, but whether it works sill needs to be confirmed in experiments on the dataset, because I know another face detector also says it can detect small face but the real effect is not very good.

2. 
- **Filename**:
- **Summary**:
- **Keywords**:
- **Critics**:




# Dataset
2. The Deepfake Detection Challenge (DFDC) Preview Dataset
- **Level**: Relevant (5)
- **Filename**: p-DFDC.pdf
- **Summary**:
- **Keywords**:
- **Critics**:
This paper gives important information about the competiton dataset. For example, It introduces that the 2/3 test videos are augmentated by 3 methods and present 3 baseline models: 1) Tampernet (6CNN + 1FC), 2) Xception (full frame), 3) Xception (face)

# Audio
2. 
- **filename**: p-Detection-Of-Alterations-In-Audio-Files-Using-Spectrograph-Analysis.pdf
- **summary**:
- **keywords**: fake audio detection
- **critics**:

# Other
2. Shampoo: Preconditioned Stochastic Tensor Optimization
- **filename**: p-1802.09568.pdf
- **summary**:
- **keywords**:
- **critics**:
I was wondering whether I should change optimizer from Adam to Shampoo, which says is better than Adam. But to proves this new opitimizer works, I need experiment evidence, and it takes time to find the code of Shampoo and how to custimize a optimizer. I just keep it.

2. 
- **filename**:
- **summary**:
- **keywords**:
- **critics**:


