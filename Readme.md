Kaggle's Talking Adtracking Fraud Detection in clicks traffic for mobile app ads.

Description:  https://www.kaggle.com/c/talkingdata-adtracking-fraud-detection


The objective of this project is to experiment neural nets on large datasets (60M to 180M rows), initially with a simple 3 layer neural net using sparse one-hot-encoding sparce matrix, and training on AWS deep learning ami.  I chose to leave the features as they were mostly provided because I wanted to feed the same features to LSTM/GRU models later, and in theory, they should be able to learn sequences.

Tracking the scores:

    *I used AWS g3.4xl GPU to train 60M rows, the apprx row num for one day, and acheived roc score of 96.9.
    
    *The original notebook was run locally with 32G ram over 30M rows, and acheived a roc score of .965.

    *5M rows was used in Kaggle kernal env't and roc is reduced to .956.
    
    Result:  The roc will probably increase another percent to .98+ if trained on the full 180M rows, which is possible using AWS ami.  The training took about 20 min per epoch.
    To speed it up, one can increase the training batch size.  And only 5 epochs was sufficient 
    before there was no more improvement in the value loss.
    

Sources:  Some of the snipplets, such as for graphing,
    were taken from the web, and other kaggle kernels.
  
What I also experimented:
    * Imported to sqlite db - Some unwanted data conversion coming back from db.
    * Used Embedding for categories -  I tried this but encountered some errors in compiling the model.
    
Issues To resolve:  
    *One-hot encoding for categories needs to include both data from
    train and test dataset. Could Include 'Other' category bucket in training.  Any
    unseen codes in test data will go in this category.  
    One would also need to 'refresh' the training model occasionnally
    to include new test codes.


    




