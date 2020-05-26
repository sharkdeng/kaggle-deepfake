Today's Work

Change model to EfficientNet-B4 since Kaggle top scorers claim that they are using this, but encountered a problem: the training loss is fluctuating around 0.6-0.7. 

This problem solved. 

| Loss Proble | Solution | 
|:--:|:--:|
| loss is increasing | add `optimizer.zero_grad()` | 
| loss is fluctruacting | test the model learning ability in 100 images, then to 1000 images | 
| memory overload | add `gc.collect() /  torch.cuda.clean_cache() /  del x, y_ture, y_pred, loss `|

Reason for fluctruacting loss:
- layers in model not freeze
- model initiated, but optimizer not initiated accordingly.

I compare EFficientNet, Xception, and ResnetXT on 1000 images. All of them have learning ability(training loss is decreasing). So I copy the EffcientNet model to my dfdc training code, but the loss still flucturates. And I found:
lr = 0.01, fluctuate <br>
lr = 0.001, decrease very slowly <br>
lr = 0.005, decrease more slowly <br>
lr = 0.0001, decrease faster <br>

So lr decrease, the training loss would decrease more. Weird.

