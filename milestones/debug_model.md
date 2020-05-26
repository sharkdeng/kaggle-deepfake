# Fine-tuning the network


## (1) Check after each work
This will give you confidence and narrow debug area

- ### check if augmentation is correct

print the image after agumentation <br>
For example, I used this fake code one time
```
from albumentations import Normalize
data = data/255.
data = Normalized()(data)
```
When I printed the augmentated image, it is all black because values are all < 0. <br>
Whem I printed the mean and std, I found this is wrong since the data should center around the mean I assigned. <br>
I suspected that I should use the mean and std of my dataset. I did, but the image is still black and the mean and std are still wrong. <br>
Then I found the description of Normalize in albumentations website says that the image would be divided by 255 and then normalized by mean and std<br>
This means I don't need to divide by 255 myself. <br>
So the correct code should be
```
from albumentations import Normalize
data = Normalized()(data)
```
I am not sure if this applies too in torchvision.transforms.


- ### check dataset output is correct
- ### check dataloader output is correct
- ### check model output is correct
- ### check loss is correct

The batch loss is very large, say 130.  <br>
I printed the preds and y and I found the preds are very large. <br>
I transited to cpu mode to debug, so the mode get reinitiated and the first loss is 0.7(normal). But the second batch loss is 130 again. <br>
I found weight update is too large that I should reduce the lr. <br>
After I adjust from lr from 0.1 to 0.001, the batch loss gets normal! I found there are some batch losses are bigger than 1 <br>
So I keep reducing the lr from 0.001 to 0.0001, the batch loss would keep under 1<br>

- ### check gradient descent is correct

- ### check model reinit

When model get reinit or resume from checkpoint, make sure both optimizer and scheduler get updated too. <br>
I encountered this error and I found the loss will fluctuate.<br>

## (2) Start from small batch data
small data can get faster feedback about training correctness and model performance. 

## (3) Batch monitor


