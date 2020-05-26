|id | Training Data | Split | Model | training loss | val loss | test loss | 290 score |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|1 | 16074(real)+16074(fake) | train(60%), val(20%), test(20%) | Xception | 0.2777 | 0.4296 | 0.4330 | |
|2 | 16074(real)+16074(fake) | train(80%), val(20%), test(20%) (I kept previous val) | Xception | 0.2924 | 0.2909 | 0.4227 | |
|3 | 16074(real)+16074(fake) | train(80%), test(20%) | Xception | 0.2731 | - | 0.5049 |  |


Common parameters: <br>
epoch: 20