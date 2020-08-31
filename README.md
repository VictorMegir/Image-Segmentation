# Feature Extraction and Image Segmentation
Using the DeepLabv3+ neural network

### DeepLabv3+
I used the DeepLabv3+ neural network with the xception architecture and pretrained weights on the PASCAL VOC 2012 semantic segmentation dataset.
The original repo can be found here: https://github.com/tensorflow/models/tree/master/research/deeplab
To use this neural network with the Keras framework i used the implementation from this GitHub repo: https://github.com/bonlime/keras-deeplab-v3-plus

### Feature Extraction
I extracted the features from the last convolutional layer of the neural network for a set of color images that i resized to 512x512.

### Dimensionality Reduction
To avoid the curse of dimensionality i reduced the extracted features using Principal Component Analysis (PCA). I used the scikit learn implementation of PCA with n=8 
principal components and derived with 8 feature images for each input image.

### Image Segmentation
To perform image segmentation i used a Gaussian Mixture Model with the principal component features. I used the Gaussian Mixture Model implementation from scikit learn for
different numbers of clusters. After fitting the Gaussian Mixture Model with a few images i used it to perform segmentation on new images.
![Image](https://github.com/VictorMegir/Feature-Extraction-and-Image-Segmentation/blob/master/screenshots/Segementation%20Example.png)

### Filters
To improve the result of the segmentation i used max, min, and meadian filters on the segmented iamges.
