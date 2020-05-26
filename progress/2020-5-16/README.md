# Adjustment  
- (E1) MyDataset +  MyCode
- (E2) Kaggle-real-fake-faces + MyCode
- (E3) MyDataset + 4th Code
- (E4) 4th Dataset +  4th Code


# Score
At first, I was using lr 0.1 and about 1500 training images, I found the train  oss is large, say 130. <br>
I reduced the lr to 0.01,then the train loss goes down, but some losses are still bigger than 1<br>
I reduced the lr to 0.0001, then the train loss goes down and no loss is bigger than 1 <br>

I increased dataset from 1500 images to 32000 images (my 98 dataset), the val and test losses go down to 0.2 <br>
I increased dataset from 32000 images to 430000 images (my 420 dataset) <br>

|epoch|train|val|test|info|
|:--:|:--:|:--:|:--:|:--:|
|1|(0.17552084200945847, 0.9265213582151698)|(0.12402318205056487, 0.9496973079262357)|(0.11608333078523476, 0.953125)|420 dataset|

Test score

|video numbers | score|info|
|:--:|:--:|:--:|
|100|0.6967682501512578|290 test videos|
|290|0.6760700691440398|290 test videos|

I suspect my label may have problem, I am gonna test on last 10 folders (in the 16th paper) (done) <br>
My label is good.

I suspect something wrong in my predict code, I am gonna extract faces of my test videos and predict them <br>

# Support

# Conclusion


1) how to adjust lr
2) how to adjust dataset size
