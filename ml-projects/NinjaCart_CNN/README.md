# Ninjacart Vegetable Image Classification

A computer vision project that classifies images into four categories: **Potato**, **Onion**, **Tomato**, and **Indian Market (Noise)** using Convolutional Neural Networks and transfer learning.

This project was developed as part of a business case study based on a real-world use case from Ninjacart, India's largest fresh produce supply chain company. The objective is to automate vegetable identification to improve sorting accuracy and reduce manual inspection during warehouse operations.

---

## Problem Statement

Ninjacart handles large volumes of fresh produce every day. Manual identification of vegetables is time-consuming, prone to human error, and difficult to scale.

The objective of this project is to develop an image classification model capable of distinguishing between:

- Potato
- Onion
- Tomato
- Indian Market (Noise)

The final model should generalize well to unseen images and accurately classify vegetables captured under varying lighting conditions, backgrounds, viewpoints, and image resolutions.

---

## Dataset

The dataset contains images collected from Google and is organized into separate training and testing directories.

### Training Set

| Class | Images |
|--------|-------:|
| Potato | 898 |
| Onion | 849 |
| Tomato | 789 |
| Indian Market | 599 |

Total training images: **3,135**

### Test Set

| Class | Images |
|--------|-------:|
| Potato | 81 |
| Onion | 83 |
| Tomato | 106 |
| Indian Market | 81 |

Total testing images: **351**

---

## Project Workflow

1. Dataset loading and exploration
2. Exploratory Data Analysis
3. Image preprocessing
4. Data augmentation
5. Train and validation split
6. CNN implementation from scratch
7. Transfer learning using MobileNetV2
8. Model evaluation
9. Confusion matrix and classification report
10. Performance comparison and business insights

---

## Exploratory Data Analysis

The dataset was analyzed to understand:

- Class distribution
- Image dimensions
- Pixel value ranges
- Image channels
- Sample images from each category

Key observations:

- Images have varying resolutions and aspect ratios.
- Images are RGB with pixel values in the range 0 to 255.
- The dataset is reasonably balanced across all four classes.
- Indian Market images contain significantly more background clutter than the vegetable classes.

---

## Data Preprocessing

The following preprocessing steps were applied before model training:

- Resize all images to 224 × 224 pixels
- Normalize pixel values to the range [0, 1]
- Create an 80:20 train-validation split
- Build TensorFlow data pipelines
- Prefetch batches for efficient training

---

## Data Augmentation

To improve generalization, the following augmentation techniques were applied during training:

- Random horizontal flip
- Random rotation

These transformations expose the model to different viewpoints without changing the semantic meaning of the images.

---

## Models

### Baseline CNN

A custom Convolutional Neural Network was implemented consisting of:

- Convolution layers
- Max Pooling layers
- Fully connected layers
- Softmax output layer

The baseline model served as a performance benchmark.

### Transfer Learning

The final production model uses **MobileNetV2** pretrained on ImageNet.

Transfer learning provides a strong feature extractor, allowing high classification performance despite the relatively small dataset.

The classifier head consists of:

- Global Average Pooling
- Dense layer
- Dropout
- Softmax classifier

---

## Training Strategy

Training included the following techniques:

- Adam optimizer
- Sparse Categorical Crossentropy loss
- EarlyStopping
- ReduceLROnPlateau
- ModelCheckpoint
- TensorBoard logging

---

## Results

| Model | Test Accuracy |
|--------|--------------:|
| Baseline CNN | 78.9% |
| MobileNetV2 | **93.7%** |

The transfer learning model improved test accuracy by approximately **15 percentage points** over the CNN trained from scratch.

---

## Evaluation

The final model was evaluated using:

- Test Accuracy
- Confusion Matrix
- Classification Report
- Precision
- Recall
- F1 Score

### Final Performance

| Metric | Score |
|--------|------:|
| Accuracy | 93.7% |
| Macro F1 Score | 0.93 |
| Weighted F1 Score | 0.94 |

The confusion matrix shows that most predictions lie along the diagonal, indicating strong classification performance across all four classes.

Most classification errors occurred between **potato** and **onion**, which share similar visual characteristics.

---

## Business Impact

This project demonstrates how transfer learning can improve automation within fresh produce supply chains.

Potential applications include:

- Automated vegetable sorting
- Warehouse quality inspection
- Inventory verification
- Packaging automation
- Reduction of manual inspection effort

Accurate image classification can reduce sorting errors, improve operational efficiency, and enable faster processing of fresh produce.

---

## Repository Structure

```
├── notebook.ipynb
├── README.md
├── requirements.txt
├── images/
└── models/
```

---

## Technologies Used

- Python
- TensorFlow
- Keras
- NumPy
- Pandas
- Matplotlib
- Seaborn
- scikit-learn
- Google Colab

---

## Future Improvements

- Evaluate additional pretrained architectures such as EfficientNet and ResNet50.
- Expand the dataset with real warehouse images.
- Perform hyperparameter optimization.
- Deploy the model using TensorFlow Serving or FastAPI.
- Convert the model to TensorFlow Lite for edge deployment.

---

## Key Takeaways

- Transfer learning significantly outperformed training a CNN from scratch.
- MobileNetV2 achieved strong generalization on unseen test data.
- The final model achieved 93.7% test accuracy while maintaining stable validation performance.
- Transfer learning is an effective solution for image classification tasks with limited labeled data.

---

## License

This repository is intended for educational and portfolio purposes.
