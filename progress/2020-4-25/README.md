1) test diverse models (undone)
- Xception
- Inception
- Efficient
- Meso
- C3D
- LSTM
- Unet

2) re-made the 400 public test label (done)

validate with LB submission files to check their order and hist.

| LB score | 290 score | hist |
|:--:|:--:|:--:|
| 0.29477 | 0.05889474638117082 | ![](lb_0.png) | 
| 0.29529 | 0.0716567031551443 |  ![](lb_1.png) | 
| 0.32224 | 0.14586953903160402 | ![](lb_2.png) | 
| 0.35116 | 0.07629036680407163 |  ![](lb_3.png) | 
| 0.38 | 0.1833915999778282  |  ![](lb_4.png) | 
| 0.45962 | 0.25416006786950274 |  ![](lb_5.png) | 
| 0.52242 | 0.283754022969272 |  ![](lb_6.png) | 
| 0.53019 | 0.33495555210575245 |  ![](lb_7.png) | 
| 0.56179 | 0.28050708671199465 | ![](lb_8.png) | 

3) resume training based on 0.45 weight + cv5 (done)

4) clean previous trained(useless) weights on Kaggle

Kaggle competition process

- EDA
- transfer learning model to make the baseline
- training (upload weights, training files)
- cleaning (useless weights and training files)
- 

| Picture | 290 test score | 4000 test score |
|:--:|:--:|:--:|
| ![](pic_cv5.png) | 0.2390419641580054 | - |
| ![](pic_0.png) | 0.28207076301299144 | - |
| ![](pic_1.png) | 0.24293407978474904 | - |
| ![](pic_2.png) | 0.21624501530341708 | - |
| ![](pic_3.png) | 0.2628455866760407 | - |
| ![](pic_4.png) | 0.28207076301299144 | - |



# Conclusion:
- Generally, cv is better than single, but has 1 exception.
- The relationship between 290 test and LB is 0.2+, namely the 290 test is useful




