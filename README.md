# 🛡️ Handwritten Digit Classifier — MNIST (Deep Neural Network)

A production-style Deep Neural Network built with TensorFlow/Keras that classifies handwritten digits (0–9) from the MNIST dataset, achieving **98.44% test accuracy**. This project was completed as Module 13 of the Ostad AI/ML Engineering Program (Batch 6).

---

## ❇️ Project Overview

I built and trained a fully-connected Deep Neural Network (DNN) to solve the classic MNIST handwritten digit classification problem — a foundational computer vision task that demonstrates my understanding of neural network design, regularization, and training optimization. Rather than a minimal baseline model, I engineered a deeper architecture with Batch Normalization and Dropout to improve generalization, and used adaptive training callbacks to make the training process efficient and stable.

## 🎯 Key Highlights

- **Test Accuracy:** 98.44% | **Test Loss:** 0.0546
- **Architecture:** 3 hidden layers (512 → 256 → 128 units) with Batch Normalization + ReLU + Dropout
- **Training Optimization:** EarlyStopping and ReduceLROnPlateau callbacks for stable convergence
- **Full Evaluation Suite:** Confusion matrix, per-class classification report, and visual prediction inspection

## 🧠 Model Architecture

```
Input (784 = 28×28 flattened image)
   │
   ├── Dense(512) → BatchNormalization → ReLU → Dropout(0.3)
   │
   ├── Dense(256) → BatchNormalization → ReLU → Dropout(0.3)
   │
   ├── Dense(128) → BatchNormalization → ReLU → Dropout(0.2)
   │
   └── Dense(10, activation="softmax")   ← Output layer (digit probabilities)
```

**Why this design?**
- **Batch Normalization** after every hidden layer stabilizes and speeds up training by normalizing layer activations.
- **Dropout** (0.2–0.3) randomly deactivates neurons during training to reduce overfitting.
- **Progressively shrinking layer sizes** (512 → 256 → 128) let the network learn coarse-to-fine feature representations before the final classification layer.

## 🛠️ Tech Stack

| Category | Tools |
|---|---|
| Language | Python 3 |
| Deep Learning | TensorFlow, Keras |
| Data Handling | NumPy |
| Visualization | Matplotlib, Seaborn |
| Evaluation | Scikit-learn (confusion matrix, classification report) |
| Environment | Jupyter Notebook / Google Colab |

## 📊 Results

| Metric | Value |
|---|---|
| Dataset | MNIST (60,000 train / 10,000 test images) |
| Epochs Trained | 20 (with EarlyStopping) |
| Optimizer | Adam |
| Loss Function | Categorical Crossentropy |
| **Final Test Accuracy** | **98.44%** |
| **Final Test Loss** | **0.0546** |

The model was evaluated using a full confusion matrix and a per-digit classification report (precision, recall, F1-score) to verify that performance was consistently strong across all 10 digit classes — not just on average.

## 📂 Project Structure

```
mnist-digit-classifier-dnn/
│
├── Module_13_MNIST_Digit_Classifier.ipynb   # Main notebook (end-to-end pipeline)
├── confusion_matrix.png                     # Saved confusion matrix visualization
├── training_history.png                     # Accuracy/loss curves
├── sample_predictions.png                   # Sample correct/incorrect predictions
└── README.md
```

## ⚙️ How I Built It — Pipeline Steps

1. **Load Data** — Loaded the MNIST dataset directly via `keras.datasets.mnist`.
2. **Preprocess** — Normalized pixel values from [0, 255] → [0, 1], flattened 28×28 images into 784-dimensional vectors, and one-hot encoded the labels.
3. **Build Model** — Designed a 3-hidden-layer DNN with Batch Normalization and Dropout.
4. **Compile** — Used the Adam optimizer with categorical crossentropy loss.
5. **Train** — Trained for up to 20 epochs with `EarlyStopping` and `ReduceLROnPlateau` callbacks and a 15% validation split.
6. **Evaluate** — Measured final test accuracy/loss and generated a confusion matrix + classification report.
7. **Visualize** — Plotted training curves and inspected sample predictions to sanity-check model behavior.

## 🚀 How to Run

```bash
# Clone the repository
git clone https://github.com/farjanaferdausi-cs50ai/mnist-digit-classifier-dnn.git
cd mnist-digit-classifier-dnn

# Install dependencies
pip install tensorflow numpy matplotlib seaborn scikit-learn

# Run the notebook
jupyter notebook Module_13_MNIST_Digit_Classifier.ipynb
```

## 💡 Key Learnings

- How Batch Normalization and Dropout work together to stabilize training and reduce overfitting in fully-connected networks.
- How adaptive callbacks (`EarlyStopping`, `ReduceLROnPlateau`) make training more efficient by avoiding wasted epochs and adjusting the learning rate dynamically.
- How to move beyond a single accuracy number and validate a classifier properly using a confusion matrix and per-class metrics.

## 🔮 Future Improvements

- Replace the flattened DNN with a Convolutional Neural Network (CNN) to better capture spatial patterns in the images.
- Add data augmentation (rotation, shift, zoom) to further improve robustness.
- Deploy the trained model behind a simple API (FastAPI) with a web front end for live digit-drawing predictions.

---

## 🖊️ Author

**Farjana Ferdausi**
AI/ML Engineering & Data Science, Fellow — Google Cloud Gen AI Academy APAC Edition (Cohort 3)
Agentic AI · RAG · Gemini · ADK · BigQuery MCP · Cloud Run
Former HR Professional (14+ years) at Radisson Blu Dhaka Water Garden, Bangladesh

- LinkedIn: [linkedin.com/in/farjana-ferdausi](https://www.linkedin.com/in/farjana-ferdausi/)
- Medium: [@farjana.rafi1983](https://medium.com/@farjana.rafi1983)
- GitHub: [farjanaferdausi-cs50ai](https://github.com/farjanaferdausi-cs50ai)
