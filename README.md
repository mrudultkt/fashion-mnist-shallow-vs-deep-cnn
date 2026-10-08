# Fashion-MNIST CNN Comparative Study: Shallow CNN vs Deep CNN

A deep learning project that classifies Fashion-MNIST clothing images using Convolutional Neural Networks (CNNs). It builds a Shallow CNN and a Deep CNN, trains them under identical settings, and compares their accuracy, generalization, training time and error patterns.

## Project Overview

The objective is to understand how CNN depth affects performance on an image classification task. Both models are trained on the same data with the same optimizer, loss, epochs, batch size and validation split, so the comparison stays fair.

The study answers four questions:

- Does a deeper CNN perform meaningfully better than a shallow one?
- Which model generalizes better to unseen images?
- Which clothing classes are easiest and hardest to classify?
- Does extra depth reduce confusion between visually similar classes?

## Dataset

**Fashion-MNIST** contains 70,000 grayscale images (28 × 28 pixels) across 10 clothing and footwear classes.

| Split | Images |
|---|---|
| Training | 60,000 |
| Test | 10,000 |

**Classes:** T-shirt/top, Trouser, Pullover, Dress, Coat, Sandal, Shirt, Sneaker, Bag, Ankle boot

The dataset is loaded directly through `tensorflow.keras.datasets`, so no manual download is needed.

## Technologies Used

- Python
- Jupyter Notebook
- TensorFlow / Keras
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn

## Workflow

1. Load and explore the dataset, with one sample image per class
2. Normalize pixel values from 0–255 to 0–1
3. Reshape images to `(28, 28, 1)` for `Conv2D` input
4. Build, train and evaluate a Shallow CNN
5. Build, train and evaluate a Deep CNN
6. Compare both models on accuracy, parameters, overfitting and training time
7. Analyze predictions and confusion matrices
8. Write the final conclusion

## Model Architectures

**Shallow CNN**

```
Conv2D(32, 3x3, relu) -> Conv2D(64, 3x3, relu) -> MaxPooling2D(2x2)
-> Flatten -> Dense(128, relu) -> Dense(10, softmax)
```

**Deep CNN**

```
Conv2D(32) -> Conv2D(64) -> MaxPooling2D
-> Conv2D(128) -> MaxPooling2D
-> Conv2D(256) -> MaxPooling2D
-> Flatten -> Dense(128, relu) -> Dense(10, softmax)
```

All convolutional layers use 3 × 3 filters, `padding="same"` and ReLU activation.

## Training Setup

| Setting | Value |
|---|---|
| Optimizer | Adam |
| Loss | `sparse_categorical_crossentropy` |
| Metric | Accuracy |
| Epochs | 10 |
| Batch size | 64 |
| Validation split | 20% of the training data |

## Results

| Metric | Shallow CNN | Deep CNN |
|---|---:|---:|
| Convolutional layers | 2 | 4 |
| Total parameters | 1,625,866 | 684,170 |
| Training accuracy | 99.24% | 98.08% |
| Validation accuracy (final epoch) | 92.38% | 92.26% |
| **Test accuracy** | **92.35%** | 91.77% |
| Test loss | 0.3921 | 0.3254 |
| Correct test predictions | 9,235 | 9,177 |
| Overfitting observed | Yes | Yes |
| Approx. training time | ~5 min | ~10 min |

## Key Findings

- The Shallow CNN performed better overall, with 92.35% test accuracy against 91.77% for the Deep CNN.
- The Deep CNN took about twice as long to train and did not improve test performance, so the extra depth was not justified here.
- The Deep CNN has fewer parameters despite having more layers, because its three pooling layers shrink the feature maps to 3 × 3 before the Flatten and Dense layers.
- Both models showed overfitting. Training loss kept falling while validation loss rose in later epochs.
- The easiest classes were Sandal, Bag, Trouser and Sneaker, which have distinctive shapes.
- The most confused classes were T-shirt/top and Shirt. The Deep CNN did not reduce this confusion: combined T-shirt/top and Shirt errors rose from 168 (Shallow) to 194 (Deep).

## Final Conclusion

The Shallow CNN is the recommended model for this experiment. It achieved slightly higher test accuracy while needing about half the training time. Increasing CNN depth does not always improve performance, so model architecture, computational cost and generalization should all be considered together.

## Repository Structure

```
├── ipynb file
└── README.md
```

## How to Run

1. **Clone the repository**
```bash
   git clone https://github.com/mrudultkt/fashion-mnist-shallow-vs-deep-cnn
   cd fashion-mnist-shallow-vs-deep-cnn
```

2. **Install the required dependencies**
```bash
   pip install tensorflow numpy matplotlib seaborn scikit-learn jupyter
```

3. **Launch Jupyter Notebook**
```bash
   jupyter notebook
```

4. **Open the notebook**

   Open the ipynb file from the Jupyter interface.

5. **Run all cells**

   Use **Cell → Run All**, or run the cells from top to bottom.

**Notes:**
- An internet connection is needed the first time you run it, because Keras downloads Fashion-MNIST automatically.
- On a CPU, training takes roughly 5 minutes for the Shallow CNN and 10 minutes for the Deep CNN. Times vary by machine.

## Notes

Both models use identical preprocessing, training settings and validation split, so differences in performance come from the architecture alone. Test accuracy is the primary metric for comparing generalization.