# Apple Leaves

The plant pathology is an important problem of research interest. The plant
pathology challenge focuses on training a model to classify foliar
diseases of apples given the photos of the apple leaves. In this task, data
insufficiency and data imbalance should be addressed. To tackle with the
above issues, we implement a series of data augmentation operations
including illumination, contrast adjustment, flipping, rotation, cropping and
blurring to enrich the dataset. We use ResNet as the model framework and
use 5-fold cross validation to train the model. Experiment results show that
the proposed methods can achieve good results.

## Introduction
Plant pathology is critical due to its impact on crop health and economic loss. Early detection and diagnosis are essential to prevent outbreaks and reduce costs. Traditional human-based detection is accurate but inefficient and costly. With advancements in AI and computer vision, deep learning models have been developed to automate plant disease detection from images, increasing efficiency and reducing costs. The Plant Pathology Challenge requires classifying apple leaf diseases into four categories: healthy, rust, scab, and multiple diseases. This challenge involves handling imbalanced data and varied image conditions.

## Methodology

### Data Augmentation
Data augmentation is crucial to address data insufficiency and imbalance. We used the Python library Albumentations for transformations, including:
- Random illumination enhancement
- Random contrast enhancement
- Up-and-down flipping
- Left-right flipping
- Random rotation
- Cropping
- Blurring

### Model - ResNet18
We used the ResNet18 architecture, which includes residual connections to prevent gradient vanishing and enhance model robustness. The model was fine-tuned for our specific task, replacing the final layer with a four-class output layer. Cross-entropy loss and Adam optimizer were used for training.

### Cross-Validation
Stratified k-fold cross-validation (k=5) was applied to ensure balanced class distribution in each fold, improving model performance on imbalanced data.

## Experiments

### Experiment Settings
- Augmented training set
- Input image size: 512x521
- Pre-trained ResNet18 model from torchvision
- Cross-entropy loss
- Adam optimizer with a learning rate of 5e-5
- Training for 10 epochs with a batch size of 32
- Random seed: 42
- Scheduler: Linear warmup for 2 epochs, followed by linear decay
- Evaluation metric: Macro average of ROC AUC

### Results
Using stratified k-fold cross-validation, the model achieved a final score of 96.97%. Detailed results for each fold are shown in the table below:

| Fold | Valid Score |
|------|-------------|
| 1    | 96.35%      |
| 2    | 95.46%      |
| 3    | 97.21%      |
| 4    | 97.84%      |
| 5    | 97.94%      |
