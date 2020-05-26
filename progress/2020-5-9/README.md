# How to debug the network

### Loss fluctuates

- 1) if **model reset**, check if these three things all get reset.
```
model.load\_state\_dict() 
optimizer.load\_state\_dict()
scheduler = torch.lr_scheduler.ReduceLROnPlateau(optimizer)
```

It sometimes happens to me that I only reset the model but forgot to reset the optimizer, so both the train\_loss and val\_loss fluctuates.


- 2) Feed small dataset

Previous few weeks(OMG!!), I was struggling that EfficientNet (Kagglers said this network is better) just has fluctuate val_loss, then I found, if feed only a small amount of data the network, it is learning very well, the val\_loss can go down to 0.007. But once I feed a new batch of data, the val\_loss would be 1.2 or 2.2, not good. I was freezing feature layers and unfroze last layers. It turns out the network is too small, and I should unfreeze all layers!

So **feed a small amount of data at first to prove whether the model has learning ability. If it does, but didn't learn in large amount data, this proves the learning network is too small.**


- 3) Check if **data augmentation** is added. 


- 4) Check code grammar

For example, if forget to add **self.df** in customized dataset



### Combat overfitting
1) dropout
2) L2 regularization
3) 