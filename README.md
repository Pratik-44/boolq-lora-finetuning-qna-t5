# BoolQ Question Answering Fine-Tuning using T5 and LoRA

**Fine-tuning T5-Base with LoRA on the BoolQ dataset for yes/no question answering, achieving 81.55% accuracy with parameter-efficient training.**

## Overview

This project fine-tunes Google's **T5-Base** model on the **BoolQ (Boolean Questions)** dataset using **LoRA (Low-Rank Adaptation)**, a parameter-efficient fine-tuning technique.

The objective is to answer **yes/no questions** given a supporting passage while significantly reducing the number of trainable parameters compared to full model fine-tuning.

The project includes:

* Data preprocessing and tokenization
* LoRA-based parameter-efficient fine-tuning
* Baseline vs fine-tuned model comparison
* Hyperparameter experimentation
* Error analysis and confusion matrix evaluation
* Sample prediction generation

---

## Dataset

**Dataset:** BoolQ (Boolean Questions)

BoolQ is a question-answering dataset consisting of:

* Natural language yes/no questions
* Associated passages
* Binary answers (Yes/No)

### Example

**Question**

> Is the sky blue?

**Passage**

> The sky appears blue due to Rayleigh scattering of sunlight in Earth's atmosphere.

**Answer**

> Yes

---

## Model Architecture

### Base Model

* T5-Base

### Fine-Tuning Method

* LoRA (Low-Rank Adaptation)

### LoRA Configuration

| Parameter | Value |
| --------- | ----- |
| Rank (r)  | 8     |
| Alpha     | 32    |
| Dropout   | 0.1   |

### Advantages of LoRA

* Reduced trainable parameters
* Lower memory requirements
* Faster training
* Comparable performance to full fine-tuning

---

## Training Configuration

| Parameter                   | Value                     |
| --------------------------- | ------------------------- |
| Epochs                      | 3                         |
| Learning Rate               | 3e-4                      |
| Batch Size                  | 4                         |
| Gradient Accumulation Steps | 4                         |
| Effective Batch Size        | 16                        |
| Sequence Length             | 384                       |
| Framework                   | Hugging Face Transformers |
| Platform                    | Google Colab              |

---

## Results

### Baseline Model (Vanilla T5)

| Metric   | Value  |
| -------- | ------ |
| Accuracy | 37.75% |
| F1 Score | 0.00   |

### Fine-Tuned Model (T5 + LoRA)

| Metric    | Value  |
| --------- | ------ |
| Accuracy  | 81.55% |
| Precision | 0.81   |
| Recall    | 0.82   |
| F1 Score  | 0.81   |

### Improvement

| Metric        | Value                    |
| ------------- | ------------------------ |
| Accuracy Gain | +43.80 percentage points |

The fine-tuned model substantially outperformed the baseline model, demonstrating the effectiveness of parameter-efficient fine-tuning using LoRA.

---

## Hyperparameter Experiments

### Sequence Length Study

| Sequence Length | Training Loss |
| --------------- | ------------- |
| 256             | 1.152         |
| 384             | 1.135         |
| 512             | 1.136         |

**Best:** 384

---

### Learning Rate Study

| Learning Rate | Training Loss |
| ------------- | ------------- |
| 1e-4          | 0.567         |
| 3e-4          | 0.406         |
| 5e-4          | 0.370         |

**Best observed training loss in the 1-epoch experiment:** 5e-4

---

### Batch Size Study

| Batch Size | Training Loss |
| ---------- | ------------- |
| 4          | 0.406         |
| 8          | 0.473         |

**Best:** 4

---

## Evaluation Techniques

The model was evaluated using:

* Accuracy
* Precision
* Recall
* F1 Score
* Confusion Matrix
* Error Analysis
* Sample Predictions

---

## Technologies Used

* Python
* PyTorch
* Hugging Face Transformers
* PEFT (LoRA)
* Datasets
* Scikit-learn
* NumPy
* Pandas
* Matplotlib
* Google Colab

---

## Repository Structure

```text
boolq-lora-finetuning-qna-t5/
│
├── README.md
├── requirements.txt
└── T5_BoolQ_Project.ipynb
```

---

## How to Run

1. Clone the repository

```bash
git clone https://github.com/<your-username>/boolq-lora-finetuning-qna-t5.git
cd boolq-lora-finetuning-qna-t5
```

2. Install dependencies

```bash
pip install -r requirements.txt
```

3. Open the notebook

```bash
jupyter notebook
```

or upload the notebook to Google Colab.

---

## Future Improvements

* Evaluate larger T5 variants
* Experiment with QLoRA
* Compare against BERT-style classifiers
* Deploy as an API
* Extend evaluation to additional QA benchmarks

---

## Author

**Pratik Bora**

Project developed as part of an NLP and Parameter-Efficient Fine-Tuning study using T5 and LoRA.
