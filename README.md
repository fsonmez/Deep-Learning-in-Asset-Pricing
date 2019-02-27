# Deep-Learning-in-Asset-Pricing
https://arxiv.org/abs/1805.01104

# Example Data Description
1975 - 2017 monthly data (516 months)

* "realMKT.txt": a 516*4 matrix of Fama & French factors. The columns are Mkt.RF, SMB, HML and MOM.

* "realstock_return.txt": a 516*1000 matrix of stock returns, which contains monthly excess returns of 1000 stocks.

* "realZ_sample.txt": a 516*2000 matrix of stock charcteristics. The columns are size of stock 1, book to market ratio of stock 1, size of stock 2, book to market ratio of stock 2 ...

* "realportfolio_return.txt": a 516*49 matrix of 49 Industry portfolio returns. 

# Usage of "dl_alpha" function

## Input 

* "data": a dictionary of all kinds of data. The keys are 
  - "characteristics"
  - "stock_return"
  - "target_return" (i.e. portoflio return)
  - "factor" (i.e. benchmark factors)

* "layer_size": a list of hidden layer size where the last element is the number of deep factors to be constructed. 

* "para": a dictionary of all training parameters. The keys are
  - "split": the way to split data into training set and test set. See "data_split" function.
  - "train_ratio": the proportion of training set if "split" is "future", between 0 and 1.
  - "batch_size": batch size for training. For example, 32.
  - "train_algo": optimization method. For example, tf.train.AdamOptimizer.
  - "learning_rate": parameter for "train_algo".
  - "activation": activation function when constructing deep characteristics. For example, tf.nn.tanh.
  - "value_index": index of stock value. For example, if value is the first characteristics, then value_index=0
  - "ens": the number of ensambles.
  - "epoch": the number of epochs for training.
  
## Output

* "factor": deep factors in training periods

* "factor_oos": deep factors in test periods

* "alpha_path": the rmse values of alpha (defined in Section 2.1 in paper) during training.  

* "loss_path": the rmse values of alpha (defined in Section 2.1 in paper) during training.  
  
