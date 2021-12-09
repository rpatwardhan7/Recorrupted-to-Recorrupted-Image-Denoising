# Recorrupted-to-Recorrupted-Image-Denoising
There are multiple datasets needed in order to run the code
To get the BSD 400 Dataset to generate training data for the DnCNN, use https://github.com/cszn/DnCNN

To get the PolyU dataset, use https://github.com/csjunxu/PolyU-Real-World-Noisy-Images-Dataset

To get the CBSD68 Dataset, use https://github.com/CBSD68-dataset

For AWGN Removal in 4.1 and 4.3, there are a few parameters that require attention in order to run the code properly. In the AWGN Dataset Generation section, the parameter NOISE_LEVEL refers to the amount of noise being added to the clean images from the BSD 400 dataset. The default we have set it to is 50.
In the Recorruption section, the parameter ALPHA is the hyperparameter used by the paper in recorruption and ranges from [0.0, 1.0]. This parameter is used in generating D^T and D^{-1} and influences the creation of y_hat and y_tilde. The Model Training section has hyperparameters that were used, as suggested by the paper, when training with the DnCNN model. The epochs, batch size, gamma (which is used to decrease learning rate after a certain number of epochs) and learning rate can be tuned up or down for better output image results. In the Generate Model Input section, the parameter T refers to the number of recorruptions needed for a test image that is passed through the model. The paper hypothesized passing T random recorruptions, passing all of them through the model and taking the average. The ablation study shows that doing T random recorruptions was better than passing an image only once through the model. Tuning the parameters ALPHA, T and NOISE_LEVEL will yield all the results in the ablation study in Experiment 4.3 as well.

For Experiment 4.2, which uses the PolyU dataset, the Recorruption section has a parameter called pch_size, which is passed into the function noise_estimate. This parameter determines the size of patches that are created on an input image for each channel which is important in estimating the noise level. This patch size can be tuned up or down to try different output results for different noise levels, but we chose to do 32 because it was the most computationally efficient and produced the best results. The Model Training section again has hyperparameters, as suggested by the paper, that were used when training the PolyU dataset in the DnCNN. These parameters were tuned based on computational power and output results. The number of epochs, gamma, learning rate and batch size can be tuned up or down for better results.

