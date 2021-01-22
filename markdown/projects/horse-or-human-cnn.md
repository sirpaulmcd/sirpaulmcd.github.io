---
layout: default
title: Horse or Human CNN
permalink: /projects/horse-or-human-cnn/
parent: Projects
# grand_parent: Blog
has_children: false
nav_order: 4
nav_exclude: false
has_toc: false
---

# Horse-Or-Human-CNN
A convolutional neural network constructed to differentiate between pictures of horses and humans. Try it out with your own pictures!
The project repo can be found [here](https://github.com/sirpaulmcd/Horse-Or-Human-CNN).

<p align="center">
    <img src="/assets/images/horse-or-human-cnn/horse-or-human-preview.png" alt="horse-or-human-preview.png">
</p>

## How to use
If you're looking to classify your own images using this model:
1. Paste your images of horses and humans into the `images` folder.
2. Add the file names to `Image_Names.xlsx`.
3. Run `Model_Predictions.ipynb`.

If you are looking to improve this model:
1. Download the below dataset and place it in the root directory of this project.
**Note:** For whatever reason, the dataset includes a duplicate `horse-or-human` folder. Make sure you delete it so that the model is not trained using duplicates.
1. Running `Model_Training.ipynb` will save the newly created model/weights in the root directory as `NewModel.hdf5` and `NewModel.json` respectively. 
2. `Model_Testing.ipynb` can be used to validate any newly created models.

## Dataset
The [Horses or Humans Dataset](https://www.kaggle.com/sanikamal/horses-or-humans-dataset) was used to train the CNN. It contains 1283 images of computer generated horses and humans that have already been split into training and validation sets.
- Training set: 1027 images of horses and humans with various nature backgrounds.
- Validation set: 256 images of horses and humans with white backgrounds.

## Training
A 90%-10% training-validation split was used on the training dataset. The training set underwent feature scaling and augmentations. Augmentations were used on the training data in order to increase variance in the images and prevent the model from overfitting.
These augmentations included zooming, shearing, and flipping the training images.
The testing dataset only underwent feature scaling. 
Using this method, batches of 32 images of 64x64 size were created to train the model. 
The image sizes were reduced in order to improve training time.

## Results
After some hyperparameter tuning, my training and testing accuracy ended up being 91.2% and 86.7% respectively. 

## Discussion
The model turned out fairly accurate. 
However, it definitely has room for improvement. 
The difference between the training and testing accuracies indicates that the model is overfit. 
In `Model_Predictions.ipynb`, 6 randomly selected images from the dataset were classified. 
The model predicted 5/6 (or 83%) correctly.
The image that was incorrectly classified is shown below:

<p align="center">
    <img src="/assets/images/horse-or-human-cnn/failed-prediction.png" alt="failed-prediction.png">
</p>
Upon closer investigation, it can be seen that this horse has its body directly facing the camera. 
As a result, its legs align such that it appears almost bipedal. 
After seeing this special case, it is easy to understand why this simple CNN would wrongly classify this image.


## Conclusion
This was my first attempt at creating a convolutional neural network.
It was fun but I'd definitely change some things moving forward. 
​
Neural networks tend to work best with a large amount of training data.
However, the dataset used to train the CNN only consisted of 1027 images so a convolutional neural network was likely not the best approach to this problem.
The most obvious way to improve this model would be to expand the dataset as much as possible. 
A better solution may also be found through `transfer learning` because it is another common machine learning approach to classifying image data.