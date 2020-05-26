# 2020-5-14

**Adjustments**
model: EffcientNet <br>
only open the last layer  <br>
use 100 training images and 10 val images(small data) to observe its learning process

used tensorboard to monitor the weight, gradient, and losses(training and val), but it doesn't feel explanable for now.Leave it later.
**LB Score**

**Support Information**
In previous training, I encountered a problem, training loss and val loss are going down to 0.04, but the test loss is high. 

|parameters| training loss|val loss| possible reason |
|:--:|:--:|:--:|:--:|
|training: 10 <br> val: 10 <br> layers: last 2|<img src="10-1.png" width="400"/>|<img src="10-2.png" width="400"/>|training data is not enough <br><img src="c-11.png" width="200"/><img src="c-1.png" width="200"/>|
|training: 100 <br> val: 10 <br> layers: last 2|<img src="100-1.png" width="400"/>|<img src="100-2.png" width="400"/>|need to unfreeze more layers? <br><img src="c-22.png" width="200"/><img src="c-2.png" width="200"/>|
|training: 100 <br> val: 10 <br> layers: last 4|<img src="100-3.png" width="400"/>|<img src="100-4.png" width="400"/>||




**Conclusion**
- when training images change from 10 to 100, the val loss was going down in the first 3 epochs but going up again.  <br>
possible reason: the training doesn't cover val <br>
use clustering to find features distributions.


