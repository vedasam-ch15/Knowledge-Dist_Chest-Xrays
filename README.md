# Knowledge-Dist_Chest-Xrays
Following is the repository of the design credits project "**Knowledge Distillation of Chest Xrays**".
* Student-Teacher model has been implemented on the [Pneumonia Chest X-Rays Dataset](https://www.kaggle.com/datasets/paultimothymooney/chest-xray-pneumonia)
* To start with, implentation of Student-Teacher model has been applied on the **CIFAR-10** dataset without any pretrained model to understand the behavious of a Student model which is being trained from a Teacher model. [Colab Link](https://github.com/vedasam-ch15/Knowledge-Dist_Chest-Xrays/blob/main/Knowledge_dist_CIFAR10.ipynb)
* Then, the imeplentation on the Chest X-rays has been done in the [notebook](https://github.com/vedasam-ch15/Knowledge-Dist_Chest-Xrays/blob/main/Knowledge_dist_ChestXrays.ipynb)
* The results, analysis and conclusions have been jotted in the [report](https://github.com/vedasam-ch15/Knowledge-Dist_Chest-Xrays/blob/main/DC_Final_Report.pdf)
* Final presentation of the project during evaluation: [PPT](https://github.com/vedasam-ch15/Knowledge-Dist_Chest-Xrays/blob/main/Project%20Summary.pdf)

**<u>IMPLEMENTATION OF STUDENT-TEACHER MODEL ON PNEUMONIA CHEST X-RAY DATASET:**
* Model Details:<br>
  The layers in the TeacherModel are:
    * DenseNet121: pre-trained convolutional layers with pretrained = False <br>
    * Dropout: with probability 0.5 to avoid overfitting<br>
    * Conv2d: with 512 filters of size 3x3 and padding of 1<br>
    * ReLU: Rectified Linear Unit activation function<br>
    * MaxPool2d: with kernel size of 7x7 and stride of 1<br>
    * Linear: fully connected layer with 512 input features and 64 output features<br>
    * Linear: fully connected layer with 64 input features and 2 output features<br>
    <br>
    
  The layers in the StudentModel are:<br>
    * mobilenet: A MobileNetV2 feature extractor with no weights pretrained.<br>
    * adaptive_pool: An adaptive average pooling layer that reduces the spatial dimensions of the features to a size of (1, 1).<br>
    * fc1: A fully connected layer with 1280 input features and 512 output features.<br>
    * fc2: A fully connected layer with 512 input features and 2 output features (assuming it is a binary classification problem).<br>
    * ReLU activation function is applied after fc1 layer.<br>
  
* To the original models, **Lr regularization done , Dropout layer added, Weight decay added, Data Augumentation were done for proper fitting**
* Comparision between Student and Teacher:<br>
  - For accuracies:<br>
  ![ST_ACC](https://github.com/vedasam-ch15/Knowledge-Dist_Chest-Xrays/assets/106541321/417941e7-ce1b-4d64-83f4-1238379bae08)

  - For losses:<br>
  ![ST_LOSSES](https://github.com/vedasam-ch15/Knowledge-Dist_Chest-Xrays/assets/106541321/871b3240-4aac-4c86-add0-29f236036e40)

* Comparision between only Student and Student trained from Teacher:<br>
  - For accuracies:<br>
  ![S_ACC](https://github.com/vedasam-ch15/Knowledge-Dist_Chest-Xrays/assets/106541321/bf25461f-0fa7-421f-8709-6ae4ff7f5306)

  - For losses:<br>
  ![S_LOSSES](https://github.com/vedasam-ch15/Knowledge-Dist_Chest-Xrays/assets/106541321/907756d4-354c-4d5c-a107-f5e63f4e29a5)
  
 * **Conclusion:** Student performs better when trained with teacher than when performed alone
 * Other results have been shown in the [report](https://github.com/vedasam-ch15/Knowledge-Dist_Chest-Xrays/blob/main/DC_Final_Report.pdf)

  
 

