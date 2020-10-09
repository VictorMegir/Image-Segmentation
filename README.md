# Image Segmentation
This repository contains the code of my diploma thesis.<br> I use the DeepLabV3+ neural network to extract deep features and i use a Gaussian Mixture Model to perform image segmentation.

### DeepLabv3+
I used the DeepLabv3+ neural network with the xception architecture and pretrained weights on the PASCAL VOC 2012 semantic segmentation dataset.
The original repo can be found here: https://github.com/tensorflow/models/tree/master/research/deeplab
To use this neural network with the Keras framework i used the implementation from this GitHub repo: https://github.com/bonlime/keras-deeplab-v3-plus

### Feature Extraction
I extracted the features from the last convolutional layer of the neural network for a set of color images that i resized to 512x512.

### Dimensionality Reduction
To avoid the curse of dimensionality i reduced the extracted features using Principal Component Analysis (PCA). I used the scikit learn implementation of PCA with n=8 
principal components and derived with 8 feature images for each input image.<br>
![Image](https://github.com/VictorMegir/Feature-Extraction-and-Image-Segmentation/blob/master/screenshots/Principal%20Components%20of%20features.png)

### Image Segmentation
To perform image segmentation i used a Gaussian Mixture Model with the principal component features. I used the Gaussian Mixture Model implementation from scikit learn for
different numbers of clusters. After fitting the Gaussian Mixture Model with a few images i used it to perform segmentation on new images.<br>
![Image](https://github.com/VictorMegir/Feature-Extraction-and-Image-Segmentation/blob/master/screenshots/Segementation%20Example.png)

### Filters
To improve the result of the segmentation i used max, min, and meadian filters as well as morphological tranformations such as opening on the segmented iamges.

### Video
To test the results i applied the process on a video, using Gaussian Mixture Models with different numbers of clusters.

### DeepLab vs GMM
To validate the results i compare the results of my system with DeepLab's segmentation.<br>
In addition, i calculated the Intersection over Union (IoU) of the results using annotated images as ground truth. The annotated images were provided by user https://github.com/sfikas
