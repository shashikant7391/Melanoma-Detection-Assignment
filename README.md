# Multiclass classification model using a custom convolutional neural network to detect Melanoma
> The model analyzes a dataset of 2357 images of malignant and benign oncological diseases, builds a model using CNN for melanoma detection.


## Problem Statement
>To build a CNN based model which can accurately detect melanoma. Melanoma is a type of cancer that can be deadly if not detected early. It accounts for 75% of skin cancer deaths. A solution which can evaluate images and alert the dermatologists about the presence of melanoma has the potential to reduce a lot of manual effort needed in diagnosis.


### Dataset 
The dataset consists of 2357 images of 9 diseases, which were formed from the International Skin Imaging Collaboration (ISIC). All images were sorted according to the classification taken with ISIC.
The data set contains the following diseases:
- Actinic keratosis
- Basal cell carcinoma
- Dermatofibroma
- Melanoma
- Nevus
- Pigmented benign keratosis
- Seborrheic keratosis
- Squamous cell carcinoma
- Vascular lesion

### Steps Performed

1. Data Reading/Data Understanding → Defining the path for train and test images 
2. Dataset Creation→ Create train & validation dataset from the train directory with a batch size of 32. Also, make sure you resize your images to 180*180.
3. Dataset visualisation → Create a code to visualize one instance of all the nine classes present in the dataset classes 
4. Model Building & training:
    - Create a CNN model, which can accurately detect 9 classes present in the dataset. While building the model, rescale images to normalize pixel values between (0,1)..
    - Use adam optimiser for model training
    - Train the model for ~20 epochs
	- The output of this model is overfitting.
5. Choose an appropriate data augmentation strategy to resolve overfitting
6. Model Building & training on the augmented data :
    - Use the model -1
	- Add Augmentation layer with the model -1
	- Add a dropout layer to handle the overfitting
	- Train the model for ~20 epochs
    - This resolve the overfitting. However, model -2 resulted underfitting
7. Class distribution: 
    - Validate the class distribution. It is imbalanced.
    - Add a class balance to handle the class imbalance to over come with the underfitting.	
8. Handling class imbalances: Rectify class imbalances present in the training dataset with Augmentor library.
9. Model Building & training on the rectified class imbalance data :
    - Use model 2 using the new test data which is created using the Augmentor
    - Train the model for 30 epochs
    - Now the model underfitting is also resolved and the accuracy is 85% on Training data and 82% on Validation data.

### Python Packages:
- Seaborn
- Matplotlib
- Numpy
- Tensorflow
- Pandas

## Conclusions

- Model 1: Basic Model
  - Model Training has good accuracy - Training accuracy 81% but Validation Accuracy is low of 53%.
  - Model is Overfitting.

- Model 2: Model 1 with Dropout Layer and Data Augmentation
  - Dropout Layers are added
  - Data Augmentation layer is added
  - Accuracy of the model is reduced as compared to model 1 - Training Accuracy 56% and Validation Accuracy 51%
  - Model is Underfitting.

- Model 3: Model 1 with Dropout Layer, Data Augmentation and a Class balanced Dataset
  - To fix the class imbalance issue, Dataset Added using Augmentor (500 images added per class)
  - The accuracy of the model is improved. So we can consider this base CNN model with droput, data augmentation and class imbalance fix - as our final model.
  - Final Accuracy of the model is - Training Accuracy 56% and Validation Accuracy 51%


