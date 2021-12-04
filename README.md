# Academic-Norms-and-Ethics
A paper reading note
# Temporal ensembling for semi-supervised learning，2017
## The core idea: use consistency regularity to extract valid signals from unlabeled data.
The consistency regularity expresses the designer’s a priori to the model that the network should be flat in the vicinity of the input data. Even if the input data changes slightly, the output of the model can remain basically unchanged. (Play a similar role, add noise, data enhancement, dropout, prevent model overfitting, learn more robust features)
## model1
![image](https://user-images.githubusercontent.com/94347374/144703679-aa1ac421-7375-4317-9f4d-285cc2330fb5.png)

First, for each sample participating in training, two forward operations are performed in the training phase. The forward operation here includes a random enhancement transformation and a forward operation of the model. Since the enhancement transformation is random, and the model uses Dropout, these two factors will cause the two forward calculation results to be different, as shown in the figure two zi.
Second, the loss function consists of two parts, as shown in the figure below. The first term consists of cross entropy and is only used to evaluate the error of labeled data. The second term consists of the mean square error (MSE) of the results of the two forward calculations and is used to evaluate all the data (including both labeled data and unlabeled data). Among them, the second term contains a time-varying coefficient, which is used to gradually release the error signal of this term. The second item here is used to achieve consistency regularity.  
![image](https://user-images.githubusercontent.com/94347374/144703931-256c6073-9061-479a-88f9-9e4f97f91056.png)  
## Temporal ensembling Model
For Temporal ensembling Model, its overall framework is similar to Π Model. The same idea is adopted in obtaining information of unlabeled data. The only difference is:
In the unsupervised term of the objective function, Π Model is the mean square error of the two forward calculation results. In the temporal ensembling model, the average of the current model prediction results and the historical prediction results is used to calculate the mean square error.
![image](https://user-images.githubusercontent.com/94347374/144703967-c9d7a141-3782-4012-b87e-ac4e505f6424.png)  
Advantages: exchange space for time, in the case of the same epoch, the total number of forward calculations is reduced by half, so the training speed is faster;  
            Averaging through historical predictions helps smooth the noise in a single prediction.

