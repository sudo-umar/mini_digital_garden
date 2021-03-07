Link to [[Chart sheet of ML]]
This stage can be divided into further stages:
## Feature selection and feature engineering
through visualization and covaraince matrix.
## Resampling
Upsampling(Upsampling with repetitions, Upsampling with SMOTE)

Downsampling

## Scaling
If different features are on different scales.
- max min normalization([-1,1],[0,1])
- Mean normalization
- Standardization(Z-Score normalization)
	It is probably the most important one related to ML as we havr to deal with e,g. audio signals, pixel values and the data can have multiple dimesnions. This method makes each feature value to have  ==zero-mean and unit variance==.(used in SVM, logistic regression, adn ANN).
	
## Data Splits:
Into training, validation and testing sets. We shouldn't touch the test set before the final evaluation. We train our model on training set and fine tune our hyper-parameters on validation set.
