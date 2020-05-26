This filder is for me to record daily experiments. If you want result, you can go to [milestone](https://gitlab.cecs.anu.edu.au/u6849956/deepfake/edit/master/milestones) folder.


# 2020-3

**Adjustments**
Adjust frames\_per\_vid parameters in inference code

**LB Score**

**Support Information**

| frames\_per\_vid | LB Score |  frames\_per\_vid | LB Score | 
|:--:|:--:|:--:|:--:|
| 17 | 0.52862 | 17 | 0.46788 |
| 32 | 0.52242 | 25 | 0.46776 |
| 48 | 0.53222 | 35 | 0.46643 |
| 64 | 0.55951 | 36 | 0.46484 |

**Conclusion**
32 is the best





# 2020-3-19

**Adjustments**
Add Ben's preprocessing (1st in 2015 APTOS competition) to make normalized image more sharpen.

**LB Score**
Bad

**Support Information**

**Conclusion**
Should reduce the difference among training, validation, and test datasets.
Test datasets are blurred while training datasets are sharpend. 
1) Sharpen test datasets also
2) Or blur the trainig dataset.





# 2020-3-20
**Adjustments**
1) Clean the small face dataset <br>
2) Reduce ResnetXT final layers to only 1 layer<br>
3) Bright the dark image<br>
4) Change preprocess pipeline<br>
5) Cross Validation 5 folds<br>

**LB Score**

**Support Information** <br>
Use facenet_pytorch to validate faces extracted by BlazeFace. <br>
Found facenet_pytorch cannot recognize 1) side face, 2) blurred face, 3) dark face(dark lighting or dark skin)k 4) exposed face


|    |BCE | LogLoss | Accuracy |
|:--:|:--:|:--:|:--:|
Training | ![Training BCE](imgs/2020-3-20-train_bce.png) | ![Training LogLoss](imgs/2020-3-20-train_logloss.png) | ![Training Accuracy](imgs/2020-3-20-train_accuracy.png)
Val | ![Val BCE](imgs/2020-3-20-val_bce.png) | ![Val LogLoss](imgs/2020-3-20-val_logloss.png) | ![Val Accuracy](imgs/2020-3-20-val_accuracy.png)

**Conclusion**





# 2020-3-21

**Adjustments**
1) Run on original inference kernel, just replace weights, there is preds distribution which proves the model works, but the distribution is not good.<br>
2) Add TTA, to see distribution can be more even, to prove TTA is working.<br>
3) Check my inference code, why the predictions are same <br>
possible reasons:
a) not updated

**LB Score**

**Support Information**<br>

|Distribution Original | Distribution TTA |
|:--:|:--:|
![](imgs/2020-3-21-distribution-original.png) | ![](imgs/020-3-21-distribution-tta.png) 

**Conclusion**
Too much changes. 



# 2020-3-22
**Adjustments**

1) model: ResnetXT (fc=Linear)
2) only change datasets to see if cleaning noise is working

**LB Score**

0.61762

**Support Information**<br>

|  No.  | Data | Training BCE | Training val loss | Distribution | LB Score|
|:--:|:--:|:--:|:--:|:--:|:--:|
| 1 | 150X150 faces | ![](imgs/1-1.png) | ![](imgs/1-2.png) | ![](imgs/1-3.png) | 1.3 | 
| 2 | 99430 faces | ![](imgs/2-1.png) | ![](imgs/2-2.png) | ![](imgs/2-3.png) | 0.72875 | 
| 3 | 98494 faces (cleaned) | ![](imgs/3-1.png) | ![](imgs/3-2.png) | ![](imgs/3-3.png) | 0.61762 | 

**Conclusion**

My self-made dataset is working <br>
Noise cleaning(remove non-face images) is working <br>


# 2020-3-22
**Adjustments**

1) model: ResnetXT (fc=Linear)
2) save the best model

**LB Score**

0.56445

**Support Information**<br>

|  No.  | Data | Training BCE | Training val loss | Distribution | LB Score|
|:--:|:--:|:--:|:--:|:--:|:--:|
| 1 | save the best model | ![](imgs/4-1.png) | ![](imgs/4-2.png) | ![](imgs/4-3.png) | 0.56445 | 

**Conclusion**

*Save the best model* is working


# 2020-3-23
**Adjustments**

1) model: ResnetXT (fc=Linear)
2) change *frames_per_vid* in inference code from 17 to 32

**LB Score**


**Support Information**<br>

|  No.  | frames\_per\_vid | LB Score|
|:--:|:--:|:--:|
| 1 | 17 | 0.56445 | 
| 1 | 32 | 0.56179

**Conclusion**

32 


# 2020-3-24
**Adjustments**

brighten the image in inference code 

**LB Score**
0.9

**Support Information**<br>

![](imgs/5-3.png)

**Conclusion**

not working


# 2020-3-24
**Adjustments**

add more data in training (previously sample part images)

**LB Score**
0.59683

**Support Information**<br>

| Training bce | Eval bce | Distribution | LB Score | 
|:--:|:--:|:--:|:--:|
|![](imgs/6-1.png) | ![](imgs/6-2.png) | ![](imgs/6-3.png) | 0.59683|

**Conclusion**

I doubt this result, I just add a little more data, no reason for LB to change so much. <br>
I am gonna find 0.522 training code and see how much data it used.


# 2020-3-24
**Adjustments**

cross validation 5 folds in training <br>
(with more data)

**LB Score**
0.7

**Support Information**<br>

| Training bce | Eval bce | Distribution | LB Score |
|:--:|:--:|:--:|:--:|
|![](imgs/7-1.png) | ![](imgs/7-2.png) | ![](imgs/7-3.png) | 0.70037 | 

**Conclusion**

For the 400 avaiable test videos, fake is far more than real. This gives hint of LB score. <br>
If the difference between fake and real is close, no need to submit.(save submission limits)

# 2020-3-25
**Adjustments**

rerun the previous 0.522 training and inference<br>
to see if can replicate the result

**LB Score**


**Support Information**<br>

| Training bce | Eval bce | Distribution | LB Score |
|:--:|:--:|:--:|:--:|
|![](imgs/8-1.png) | ![](imgs/8-2.png) | ![](imgs/8-3.png) |  | 

**Conclusion**

# 2020-3-29
**Adjustments**

lr schedule on val set <br>
more data by train (85%) and val (15%) split <br>
post processing (clip to 0.1-0.9 and change 0.5 to 0.481)

**LB Score**
0.45

**Support Information**<br>

| Eval bce | Distribution | LB Score |
|:--:|:--:|:--:|
| can down to 0.27 | ![](imgs/9-3.png) | 0.45962 | 

**Conclusion**
The relationship between local training and LB score is: <br>
local val_loss score + 0.2 or so = LB score <br>
Also, prediction distribution can give hints of LB score <br>
Good predictions should have clear 2 columns and less middle values


# 2020-3-30
**Adjustments**

cross validation 10 folds

**LB Score**
0.47

**Support Information**<br>


**Conclusion**
This training helps find ideal train and val split, it can reduces val_loss on local training.  <br>
Fold 3 can down to 0.26, but LB score is not improved accordingly. <br>
And, the training price of CV 10 folds is really big <br>



# 2020-3-31
**Adjustments**

model selection <br>
- Resnetxt50
- Resnet50
- Xception

select 2 bests to do ensemble
0.53 * m1 + 0.481 * m2


**LB Score**


**Support Information**<br>

| Model | Training bce | Eval bce | Distribution | LB Score |
|:--:|:--:|:--:|:--:|:--:|
|:--:|:--:|:--:|:--:|:--:|
|:--:|:--:|:--:|:--:|:--:|


**Conclusion**
I will select m1 () and m2 ()



# 2020-3-31
**Adjustments**

fine-tune ensemble efficient E1 and E2
E1 * m1 + E2 * m2

**LB Score**


**Support Information**<br>



**Conclusion**
The E1 () and E2 ()

# 2020-4-22
**Adjustments**

set up local benchmarks

1) self-made dfdc(dfdc)<br>
2) deepfake-timit(timit)<br>
3) face-forensices(ff) <br>

**LB Score**


**Support Information**

| kernel | dataset | extra info | prediction distribution | score |
|:--:|:--:|:--:|:--:|:--:|
| me\_latest\_0.45 | dfdc | without post-processing | ![](imgs/me_dfdc_without_pp.png) | 2.123 | 
| me\_latest\_0.45 | dfdc | with post-processing | ![](imgs/me_dfdc_with_pp.png) |  1.574 |
| 0.46 | dfdc | without post-processing(1)| ![](imgs/0.46_dfdc_without_pp.png) | 1.1215821480623365 |
| 0.46 | dfdc | with post-processing(1)|  ![](imgs/0.46_dfdc_with_pp.png) | 1.015481719764217 |
| me\_latest\_0.45 | dfdc | with post-processing(2) |  |  |
| 0.46 | dfdc | with post-processing(2)| |  |


| me\_latest\_0.45 | timit | without post-processing(1) | |  | 
| me\_latest\_0.45 | timit | with post-processing(1) | | |
| 0.46 | timit | without post-processing(1)| | |
| 0.46 | timit | with post-processing(1)| | |
| me\_latest\_0.45 | ff | without post-processing(1) | | | 
| me\_latest\_0.45 | ff | with post-processing(1) | | |
| 0.46 | ff | without post-processing(1)| | |
| 0.46 | ff | with post-processing(1)| | |


**Conclusion**

several undeteced reasons:
1) the manipulated trace is far from face  
2) manipulated effects orrur in last few frames  
3) multiple characters 
4) only very few manipulated frames 

