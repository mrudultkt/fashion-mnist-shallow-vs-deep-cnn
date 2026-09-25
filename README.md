# Fashion-MNIST: Shallow CNN vs Deep CNN

A comparative study of a shallow CNN and a deep CNN on the Fashion-MNIST dataset — covering data preprocessing, model architecture design, training, evaluation, and error analysis.

## 📌 Overview

This project trains two convolutional neural networks of differing depth on the same dataset and training setup, then compares them on accuracy, parameter count, training time, and generalization behavior.

| | Shallow CNN | Deep CNN |
|---|---|---|
| Conv layers | 1 | 6 |
| Pooling layers | 1 | 3 |
| Regularization | None | Batch Normalization + Dropout |
| Dense layers | 1 (64 units) | 1 (256 units) |

## 📂 Dataset

[Fashion-MNIST](https://github.com/zalandoresearch/fashion-mnist) — 70,000 grayscale 28×28 images across 10 clothing categories (T-shirt/top, Trouser, Pullover, Dress, Coat, Sandal, Shirt, Sneaker, Bag, Ankle boot). Loaded directly via `tensorflow.keras.datasets.fashion_mnist`.

## 🗂 Repository Structure
├── Fashion_MNIST_Shallow_vs_Deep_CNN.ipynb # Main notebook — all experiments
├── Comparative_Report_Fashion_MNIST.md # Short written report
└── README.md

## 🧪 What's in the Notebook

1. **Data loading & exploration** — shapes, class distribution, sample images, normalization, reshaping
2. **Shallow CNN** — build, train, evaluate, plot accuracy/loss curves
3. **Deep CNN** — build, train, evaluate, plot accuracy/loss curves
4. **Comparison table** — parameters, accuracy, training time, overfitting check
5. **Error analysis** — correct/incorrect predictions, confusion matrices
6. **Final conclusion** — recommendation and key takeaways

## ▶️ How to Run

1. Open the notebook in [Google Colab](https://colab.research.google.com/) (recommended — enable GPU via `Runtime → Change runtime type → GPU`) or run locally with Jupyter.
2. Install dependencies if running locally:
```bash
   pip install tensorflow numpy matplotlib seaborn scikit-learn pandas
```
3. Run all cells top to bottom.

## 🛠 Tech Stack

- Python
- TensorFlow / Keras
- NumPy, Pandas
- Matplotlib, Seaborn
- scikit-learn (confusion matrix)

## 📊 Results

See the comparison table and confusion matrices in the notebook, and the summary in `Comparative_Report_Fashion_MNIST.md`.

## 📄 License

This project was completed as part of a coursework assignment.