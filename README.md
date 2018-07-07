## Fraud-detection-with-keras

The dataset "Credit Card Fraud Detection" was provided by Kaggle https://www.kaggle.com/mlg-ulb/creditcardfraud. The input is the bank transaction data and the output is a fraud ('1') and a non-fraud transaction ('0'). In total in the dataset there are only 492 frauds out of 284,807 transactions.

### fraud_prediction.py

Fraud transaction is an example of a highly unbalanced dataset, which lead to the case when the model says that there are no frauds at all, i.e. all of the outputs are 0's. As frauds account for only 0,172% of all transactions, the model will show 'good' performance, which is usually determined by loss.
</br>To solve this problem,the amount of the frauds for training was artificially increased so that they would have bigger influence on the model. The amount of the rest transactions was limited to 60,000. For testing there was chosen part of about 20,000 transactions, which later will be separately checked.
</br>
</br>The last 5 epochs of the training:
```
Epoch 15/20
 - 3s - loss: 0.0021 - acc: 0.9951
Epoch 16/20
 - 3s - loss: 0.0020 - acc: 0.9954
Epoch 17/20
 - 3s - loss: 0.0027 - acc: 0.9937
Epoch 18/20
 - 3s - loss: 0.0023 - acc: 0.9947
Epoch 19/20
 - 3s - loss: 0.0027 - acc: 0.9937
Epoch 20/20
 - 3s - loss: 0.0017 - acc: 0.9961
```

</br>Although the values for loss and accuracy show the good result, the actual task to detect the fraud transactions may not be succeeded. To check that there were obtained the predictions for the part of the dataset which was not trained. The predictions are given in a form of list with the probabilities of '1' to happen.
</br>Even a very small probability may be an evidence of a fraud. So by the method of trial there was found a number (0,0001) for a comparison such as if the prediction exceeds it, there would be as many true positives and as fewer false positives as possible.
</br>
</br>The result of the predictions:
```
84.69% of detected frauds
0.38% of false positives, i.e 75 out of 19606 transactions wrongly detected as frauds
```
