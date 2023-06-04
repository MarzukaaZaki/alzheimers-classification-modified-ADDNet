# Alzheimer's Disease Classification using ADD-Net
This repository contains a Jupyter Notebook presenting a modified version of the ADD-Net architecture for Alzheimer's disease classification. 


# Table of Contents
- [Paper](#paper)
- [Dataset](#dataset)
- [Modifications Made to the Original ADD-Net](#modifications-made-to-the-original-add-net)
- [Tools Used](#tools-used)


# Paper
The ADD-Net architecture is based on the research outlined in thea following paper:

[Add-Net: An Effective Deep Learning Model for Early Detection of Alzheimer's Disease in MRI Scans](https://ieeexplore.ieee.org/document/987a7809)


# Dataset
To reproduce the results and evaluate the performance of the modified ADD-Net architecture, the publicly available Kaggle dataset used in the paper has been utilized. The dataset contains MRI scans of people suffering from Alzheimer's disease grouped into 4 classes: Mild Demented, Very Mild Demented, Moderate Demented and Non Demented. Link to the dataset:

[Alzheimer's 4-Class Dataset](https://www.kaggle.com/datasets/shahidzikria/alz-dataset)



# Modifications Made to the Original ADD-Net

## Exploring Different Techniques to Solve Class Imbalance
To solve class imbalance, so far I have used the techniques: SMOTEENN, SMOTETomek, BorderlineSMOTE, ADASYN and observed differences in their results.   

## Adding Another Path to the Model
- The original ADD-Net used filters of size 5x5 in its convolution blocks. Filters of this size are useful for extracting local features, but not the global ones. So in this modified version of the architecture, filters of size 12 x 12 are used along with that of size 5 x 5. 
- To do so, another path parallel to the convolution blocks is created. 
- This path has the same set of convolution layers except the filter size, which is 12x12. There are 4 convolution blocks, that is followed by a dropout layer similar to the ADD-Net. After the flatten layer, the output from the two branches is merged and fed to the flatten layer and thereafter, the fully connected layers.

Here is a visualization with input shapes of the modified ADD-Net:

![shared_input_layer](https://ibb.co/JFgMdFY)


## Evaluating Performance
Accuracy of the original ADD-Net is 98.6%.
### Modified ADD-Net with SMOTE
| Performance Metric | Obtained Result |
| -------------- | -------------- | 
| Accuracy | 98.48%|
| AUC | 99.82% |
| F1-Score| 98.53% |
| Precision| 98.63% |
| Recall| 98.43% |


### Modified ADD-Net with ADASYN
| Performance Metric | Obtained Result |
| -------------- | -------------- | 
| Accuracy | 99.4%|
| AUC | 99.84% |
| F1-Score| 98.73% |
| Precision| 98.82% |
| Recall| 98.67% |

### Modified ADD-Net with SMOTEENN
| Performance Metric | Obtained Result |
| -------------- | -------------- | 
| Accuracy | 99.5%|
| AUC | 99.93% |
| F1-Score| 99.48% |
| Precision| 98.50% |
| Recall| 99.4% |

### Modified ADD-Net with BorderlineSMOTE
| Performance Metric | Obtained Result |
| -------------- | -------------- | 
| Accuracy | 98.0%|


# Tools Used

## Language
- [Python](https://www.python.org/)

## Libraries and APIs
- [Tensorflow](https://www.tensorflow.org/)
- [Keras API](https://keras.io/)




