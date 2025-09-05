# AG News Topic Classifier 📋

This project implements a news topic classification model using the **BERT** transformer model to classify news headlines into four categories: **World** 🌍, **Sports** ⚽, **Business** 💼, and **Sci/Tech** 🧪. The model is trained on the **AG News dataset** and includes a user-friendly **Gradio interface** for interactive predictions.

## Table of Contents
- [Overview](#overview) ℹ️
- [Dataset](#dataset) 📊
- [Model](#model) 🤖
- [Training](#training) 🚀
- [Evaluation](#evaluation) 📈
- [Usage](#usage) 🖱️
- [Requirements](#requirements) 🛠️
- [Results](#results) 🏆
- [How to Run](#how-to-run) ▶️
- [License](#license) 📜

## Overview
This project fine-tunes a **BERT** model (`bert-base-uncased`) to classify news headlines from the AG News dataset into one of four categories. After training, the model is integrated into a **Gradio interface** for easy interaction, allowing users to input a news headline and receive a predicted topic.

## Dataset
The **AG News dataset** is used, which contains news articles categorized into:
- **World** 🌍
- **Sports** ⚽
- **Business** 💼
- **Sci/Tech** 🧪

The dataset is loaded using the `datasets` library from Hugging Face and consists of training and test splits.

## Model
- **Model**: `BertForSequenceClassification` from Hugging Face, based on `bert-base-uncased`.
- **Tokenizer**: `BertTokenizerFast` for preprocessing text.
- **Number of Labels**: 4 (one for each category).
- The model is fine-tuned to classify headlines based on their content.

## Training
The model is trained with the following configuration:
- **Epochs**: 1
- **Batch Size**: 16 (training), 64 (evaluation)
- **Warmup Steps**: 500
- **Weight Decay**: 0.01
- **Logging**: Every 10 steps
- **Output Directory**: `./results`
- **Logging Directory**: `./logs`

The training process uses the `Trainer` API from Hugging Face, with a data collator for dynamic padding.

## Evaluation
The model is evaluated on the test split of the AG News dataset. Metrics include:
- **Accuracy**: 94.58% ✅
- **F1 Score**: 94.57% (weighted average) 📊
- **Evaluation Loss**: 0.1694
- **Runtime**: ~53 seconds
- **Samples per Second**: 142.62

The evaluation uses a custom `compute_metrics` function to calculate accuracy and F1 score.

## Usage
1. **Train the Model**: Run the provided script to fine-tune the BERT model.
2. **Save the Model**: The fine-tuned model and tokenizer are saved to the `./results` directory.
3. **Interactive Interface**: Use the Gradio interface to input a news headline and get the predicted topic (World, Sports, Business, or Sci/Tech).
4. **Example**:
   - Input: "New AI breakthrough in neural networks"
   - Output: Sci/Tech 🧪

## Requirements
Install the required packages using:
```bash
pip install transformers datasets accelerate gradio torch scikit-learn numpy
```

## Results
The model achieves:
- **Training Loss**: 0.2448 (average over 7500 steps) 📉
- **Accuracy**: 94.58% ✅
- **F1 Score**: 94.57% 📊
- **Total Training Time**: ~46 minutes ⏱️
- **Total FLOPs**: 7.89e15

The training loss decreases steadily, as shown in the logs, indicating effective learning.

## How to Run
1. **Clone the Repository**:
   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```
2. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```
3. **Run the Script**:
   ```bash
   python ag_news_classifier.py
   ```
4. **Launch the Gradio Interface**:
   After training, the Gradio interface will launch automatically, or you can manually run the prediction function with a saved model.

## App Demo
![App Demo](app.demo.png)

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details. 📜
