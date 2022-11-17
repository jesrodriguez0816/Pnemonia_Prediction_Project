Jessica Rodriguez
Flatiron School
Github repository: 

# Phase 4: Pneumonia Prediction Project

## Overview

The goal of this project was to build a machine learning model to classify a dataset for chest x-ray images, screening them for pneumonia.
To achieve this goal, I built a **convolutional neural network** to **classify images as either pneumonia or non-pnemonia**.
The Paul Mooney dataset was used, found on Kaggle [here:] (https://www.kaggle.com/datasets/paultimothymooney/chest-xray-pneumonia). It contains 5,683 images separated into two categories: "Pneumonia" and "Normal".

## Preprocessing and Metric Determination

The images in the Mooney dataset have the three layers of a colored photograph, although they appear to be in grayscale. In order to preprocess the images, I used Keras' ImageDataGenerator to rescale the images' pixels (to a scale of 0 to 1), and resized the images to 224 x 224 px.
![](Image 10-25-22 at 1.57 PM.jpg)
![](Image 10-25-22 at 1.57 PM (1).jpg)

In classifying these images, both false positives and false negatives seem to have a cost. Reducing the rate of false positives would reduce the amount of unneccesary perscriptions for patients who do not have pneumonia. However, if the rate of false negatives is neglected, that would mean the rate of untreated pneumonia patients would increase.

It is assumed that each X-ray image in this dataset will be looked over by human eyes-in addition to being trained on the machine-learning model. Therefore, the overall accuracy of the model should be high to make this process the most efficient for the technician or doctor reviewing the x-ray.

## Feature Importances

The python LIME package (Local Interpretable Model-agnostic Explanations) was used to depict the features (edges) in the image that the model found most important in making its prediction.
![alt text](Image 11-15-22 at 9.43 AM.jpg)

## Final Model
In diagnosing pneumonia, the best practice is to reduce the number of False Negatives.

5 models were trained and evaluated for accuracy. The final model has less false negatives and less false positives than most of the other models, with an accuracy score of 75%.


## Model Conclusion and Reccomendation
The model is imperfect; further tuning could be done to improve its accuracy score.

However,  it can still be a useful tool for efficiency.

Recommendations:

* Each image should be reviewed by human eyes (tech and/or doctor) in addition to being trained on the model.
* Each image should be saved as 224 x 224 px before being trained on the model
* High-intensity pixel from the diaphragm may be adding noise to the model. The tech should crop out the diaphragm on each image to improve accuracy.


## Follow-Up Work...What's Next?
To further improve this model, I would:

* Explore methods to remove the diaphragm from each image to remove “noise” and improve accuracy
* Retrain the model using smaller images (ex: 32 x 32 px) see if image features are more accurately highlighted
* Research other methods to tune CNNs
