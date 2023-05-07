# Covid CT image classification

This repository contains code for a COVID-19 CT image classifier. The purpose of this classifier is to take in CT images of lungs and classify them as either positive or negative for COVID-19.

[Related paper](https://arxiv.org/pdf/2003.13865.pdf)
## Dataset

The dataset used in this project is the COVID-19 CT scan dataset, which can be found at [this link](https://github.com/UCSD-AI4H/COVID-CT). This dataset contains CT scan images of lungs from both COVID-19 positive and negative patients.
## Data Preprocessing

**Loading the dataset**: The CT scan dataset is loaded using the load_dataset function from the utils module. The function takes the path to the dataset directory and the desired image size as input, and returns a tuple containing the training and validation sets.

**Data augmentation**: Data augmentation is performed on the training set using the ImageDataGenerator class from Keras. This is done to increase the size of the training set and improve the generalization of the model. The augmentation techniques used include random rotation, horizontal and vertical shift, zoom, and flipping.

**Preprocessing the images**: The images are preprocessed using the preprocess_input function from the keras.applications module. This function applies normalization to the pixel values of the images, making them suitable for the VGG16 model.

**Splitting the dataset**: The dataset is split into training and validation sets using the train_test_split function from the sklearn.model_selection module. The function takes the preprocessed images and their corresponding labels as input, and returns the training and validation sets.

**Creating generators**: The training and validation sets are converted into data generators using the ImageDataGenerator.flow method. This allows us to load and preprocess the images on-the-fly, which is more memory-efficient than loading all the images into memory at once.

**Balancing the dataset**: The training set is balanced using the class_weight parameter in the fit_generator method. This is done to address the class imbalance problem in the dataset, as there are more negative images than positive ones.

**Normalization**: Normalization is performed on the pixel values of the images by dividing them by 255. This is done to scale the pixel values between 0 and 1, which helps the model to converge faster during training.
## Model & Classifier

### Model
The model used in this project is a convolutional neural network (CNN). The CNN is trained on the preprocessed CT scan images and learns to classify them as either COVID-19 positive or negative.

### Classifier
Once the CNN is trained, it can be used to classify new CT scan images. To use the classifier, simply call the classify_image function, passing in the file path of the image you want to classify. The function will return either "Positive" or "Negative", indicating whether the image is positive or negative for COVID-19.
## Result

Validation at Epoch 20 , Accuracy: 0.78325 , sensitivity: 0.74489 specificity: 0.819047619047619 , roc_score: 0.86171

