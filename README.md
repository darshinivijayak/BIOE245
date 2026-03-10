# BIOE245
Homework 2 

Task #2
1. What learning rates are used in the training? 
The initial learning rate used in this model seems to be 0.001, which then after 50 epochs it becomes 0.0001 and after 75 epochs it becomes 0.00001.

2. What is the train/val/test split of the dataset (provide sample counts)?
The train/val/test split of the dataset are 89,996 samples for training, 10,004 samples for validation and 7,180 samples for testing.

3. What are the dimensions of the model input per batch?
The dimensions of the model input per batch for a (128, 3, 28, 28).

4. What is the dimension of the model output during training? What does it represent?
The dimension of the model output is (128,9). This represents the 9 different tissue classes in the PathMNIST.

5. What type of task is this? What loss function is used?
This is a multi-class classification task, using a cross entropy loss function.

6. How many files are generated after training? Where are they located and what do they contain?
There seems to be three files generated after the training, a best_model.pth file, a pathmnist_log.txt and Tensorboard_results. There were also three csv files generated. They are located in PathMNIST_ResNet18 folder we had created before training, under the pathmnist subfolder within that folder.


Task #3
1. Where are the training statistics stored? Demonstrate how to visualize them.
The training statistics are stored in the Tensorboard_results file. In order to visualize them we can do the following:
tensorboard --logdir /Users/dvijayakumar/Downloads/PathMNIST_ResNet18/pathmnist/260214_024337/Tensorboard_Results

2. How many curves are displayed? What do they represent and how are they calculated?
I see 10 curves displayed. I see curves for the following
- Test accuracy 
- Test AUC 
- Test loss
- Training accuracy 
- Training AUC
- Training Loss
- Training Loss Logs
- Validation accuracy 
- Validation AUC
- Validation Loss
Accuracy is calculated as the number of correct predictions/total samples. Loss is computed using the cross-entropy loss function, and AUC is calculated using the predicted probabilities across the dataset in order to predict the model's ability to rank positive examples higher than negative ones. 

3. How does the learning rate schedule correlate with the behavior of the curves?
When the learning rate is high, the curves fluctuate and loss seems to oscillate. When the learning rate drops, the loss curve slope becomes smaller and the fluctuations in the curves reduce. 

4. What observations can you make about the curve trends? Are they monotonically increasing, decreasing, or fluctuating? Explain why.
For the accuracy curves, the accuracy in the initial epochs (up to about 50) seem to be very random, and then after 50 epochs it seems to stabilize in an overall upward trend. For the loss curves, for the testing loss curve the trend seems to be overall random but for the validation and traning curves, the curve trend overall seems to be decreasing as more epochs are done. For the AUC curves, they seems to have an overall upward trend as the number of epochs completed increases. All the curves seem to be fluctuating, because for each mini-batch completed there are different effects per epoch. 

Task #4
1. Is AUC used in this training script? If so, is it applied directly for binary classification, or are there adaptations for multi-class classification?
AUC is used in the training curve and is computed for the training, validation and test sets. for multi-class classification the training script adapts AUC computation by applying a one-vs-rest strategy in order to treat each class as positive compared to all others. Then the per-class AUCs are averaged to produce one singular final AUC score. 

2. What curve does "AUC" refer to? Plot this curve for the saved model evaluated on the test set.
In this case it is the ROC curve that the AUC refers to.
<img width="700" height="600" alt="image" src="https://github.com/user-attachments/assets/ee4ce505-e6f9-4efc-98af-0383d53f1395" />


3. From the test set, find examples for 5 classes of your choice:
   - One example where the model correctly predicts the class
   Class 0: <img width="389" height="409" alt="image" src="https://github.com/user-attachments/assets/6408d693-8ee8-4b4a-90e7-76176f7691c5" />

   Class 1: <img width="389" height="409" alt="image" src="https://github.com/user-attachments/assets/6041a824-3ae0-4de4-8353-1f956bebc63e" />

   Class 2: <img width="389" height="409" alt="image" src="https://github.com/user-attachments/assets/42a97760-f3e3-465c-89eb-b410c2667a46" />

   Class 5: <img width="389" height="409" alt="class5_correct" src="https://github.com/user-attachments/assets/8f55b9c5-917b-4d5b-a9ec-c8ecfdfb0164" />

   Class 7: <img width="389" height="409" alt="class7_correct" src="https://github.com/user-attachments/assets/c5b92eff-4fca-427e-bf6d-01cb5f881fd1" />


   - One example where the model incorrectly predicts the class
   Class 0: <img width="389" height="409" alt="class0_incorrect" src="https://github.com/user-attachments/assets/bfd8fdf6-c45b-48b4-8f88-d3d8f2cbf3ba" />

   Class 1: <img width="389" height="409" alt="class1_incorrect" src="https://github.com/user-attachments/assets/dfab2230-51fc-4bc4-bb9a-2a906ed73780" />

   Class 2: <img width="389" height="409" alt="class2_incorrect" src="https://github.com/user-attachments/assets/5da8327f-13dc-4c71-9e3a-b989721094f5" />

   Class 3: <img width="389" height="409" alt="class3_incorrect" src="https://github.com/user-attachments/assets/803b7d78-20ad-4cef-8df9-7b15a56bc7ce" />

   Class 4: <img width="389" height="409" alt="class4_incorrect" src="https://github.com/user-attachments/assets/f49bc51b-71a5-410b-b5d4-f9a72934caf2" />


   Include the images in your report (total: 10 images).
