# OpenCV-work-demonstrating-one-hidden-layer-perceptron-NN-trained-with-HSV-intensity-values-as-featur
OpenCV work demonstrating one hidden layer perceptron NN trained with HSV intensity values as feature vector for segmenting water pixels from non-water pixel in underwater images



The following work using OpenCV (4.2) library uses multi-layer (three) perceptron neural network for train and prediction of water pixels in underwater images while considering Hue, Saturation and Value(Gray) intensity values as the feature vector. This work also provides the effect of incrementing its #neurons under thousand neurons. Note that, it may not keep on working for more than a thousand neurons.
TrainData:
It holds the training data that must be CV_32FC1 type and its dimension is nSamples * nFeatures
TrainLabels:
It holds the labels for each sample that must be CV_32FC1 type and its dimension is nSamples * 1
TestData:
It holds test data and must be CV_32FC1 type 
TestLabels:
It holds the correct labels for test data and it is also used in accuracy measuring


The first part of the code deals with red channel compensation of the image which improves the bluish color bias of the image. For red channel compensation, equation 8 of paper "Color Correction Based on CFA and Enhancement Based on Retinex With Dense Pixels for Underwater Images" have been used. The red channel compensated image is stored in image2 in the code. 


Pure blue water samples are loaded as two training image samples (two .png files). These pure water samples are named sample (1).png and sample (2).png. They are labeled +1.0 in the training label vector.


Non water samples are chosen within another input image using this rectangle window (1, 400, 640, 320). They are labeled 0.0 in the non-water training label vector.

This work measures accuracy values at the end of each iteration and then increments the #neurons for the next iteration. The accuracy is measured by dividing sum of confusion matrix main diagonal elements to sum of all confusion matrix elements.

Parameters in ANN_MLP:

-	Sigmoid activation function
-	300 iteration
-	1e-4 as max error
-	Variable number of neurons in the hidden layer (50 to 1000)
-	The feature vector has three columns holding R-G-B intensities respectively (e.g. mx3).

Image Data Base:

The input image is an underwater image from this dataset:
  ( https://li-chongyi.github.io/proj_benchmark.html ). 

Conclusion:

In brief, the code's purpose is to demonstrate the performance of Hue, Saturation and Value (Gray) intensity values in segmenting water pixel regions from non-water regions using one hidden layer perceptron ANN with under a thousand neurons. 
Since our results may be inaccurate in case of different systems, the plot of accuracy vs #neurons is not guaranteed to be %100 accurate.
In this case, we insist on replicating the process by yourself. The execution time is in order of hours.
