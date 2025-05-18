# E-BMAS: A Mixture of AI Detectors

Large Language Models (LLMs) are gearing up to surpass human creativity. The veracity of the statement needs careful consideration. This paper addresses machine-generated content across several scenarios, including document-level binary and multiclass classification, sentence-level segmentation to differentiate between human and machine-generated text, and a survey of adversarial attacks aimed at reducing the detectability of machine-generated content.
We introduce a new work called BMAS English: an English language dataset for Binary classification of human and machine text, for Multiclass-classification, which not only identifies machine-generated text but can also try to determine its generator, and Adversarial attack addressing where it is a common act for the mitigation of detection, and Sentence-level segmentation, for predicting the boundaries between human and machine-generated text. We believe that this paper will address previous work done in machine-generated text detection (MGTD) in a more meaningful way.

<div align="center">
  <img src="Images/EMLP.drawio.png" alt="Overview of All Experiments" width="600"/>
</div>



## Dataset Statistics
The dataset used in this work can be downloaded from the following [Google Drive link](https://drive.google.com/drive/folders/1tWqFkJJHfs2uFGU3O1_BoHo3QebKVbYx)


| LLM ↓ Domain → | Reddit             | News               | Wikipedia          | Arxiv              | Q&A                |
|-----------------|--------------------|--------------------|--------------------|--------------------|--------------------|
| **Human** | 10,000 (*(5+1))   | 10,000 (*(5+1))   | 10,000 (*(5+1))   | 10,000 (*(5+1))   | 10,000 (*(5+1))   |
| **Deepseek** | 2,000 (*(5+1))    | 2,000 (*(5+1))    | 2,000 (*(5+1))    | 2,000 (*(5+1))    | 2,000 (*(5+1))    |
| **OpenAI** | 2,000 (*(5+1))    | 2,000 (*(5+1))    | 2,000 (*(5+1))    | 2,000 (*(5+1))    | 2,000 (*(5+1))    |
| **Anthropic** | 2,000 (*(5+1))    | 2,000 (*(5+1))    | 2,000 (*(5+1))    | 2,000 (*(5+1))    | 2,000 (*(5+1))    |
| **Llama** | 2,000 (*(5+1))    | 2,000 (*(5+1))    | 2,000 (*(5+1))    | 2,000 (*(5+1))    | 2,000 (*(5+1))    |

<br>

**Note:** The 2,000 and 10,000 represent the original non-adversarial texts, and the numbers in brackets represent 5 adversarially attacked texts and 1 original non-adversarial text. Non-Adversarial Data Size = 80,000 and Adversarial Data Size = 480,000.

---

| LLM ↓ Source → | XSUM  | SciGen | ELI5  | YELP  | SQuAD | CMV   | Wikipedia | Reddit |
|-----------------|-------|--------|-------|-------|-------|-------|-----------|--------|
| **Deepseek** | 2,000 | 2,000  | 2,000 | 1,046 | 954   | 466   | 1,046     | 488    |
| **OpenAI** | 2,000 | 2,000  | 2,000 | 1,046 | 988   | 492   | 1,012     | 496    |
| **Anthropic** | 2,000 | 2,000  | 2,000 | 1,004 | 996   | 514   | 1,004     | 482    |
| **Llama** | 2,000 | 2,000  | 2,000 | 980   | 1,020 | 520   | 980       | 500    |

---

| Model           | Reddit | News | Wikipedia | ArXiv | Q&A   |
|-----------------|--------|------|-----------|-------|-------|
| **OpenAI(HM)** | 2k     | 2k   | 2k        | 2k    | 2k    |
| **DeepSeek(HM)**| 2k     | 2k   | 2k        | 2k    | 2k    |
| **OpenAI(MH)** | 2k     | 2k   | 2k        | 2k    | 2k    |
| **DeepSeek(MH)**| 957    | 1998 | -         | 2k    | 2k    |
| **GPT-4.1(Mix)**| 986    | 1k   | 981       | 998   | 971   |
| **GPT-4.1(Mix)**| 987    | 1k   | 984       | 998   | 970   |


## AI Text Detection Methods and Models

**1. Binary Classification:**

* **Machine Learning:**
    * LR (Logistic Regression)
    * RF (Random Forest)
    * XGB (XGBoost)
    * LDA (Linear Discriminant Analysis)
    * SVM (Support Vector Machine)
    * Feature Extraction: TF-IDF, Word2Vec, GloVe
* **Neural Networks:**
    * CNN (Convolutional Neural Network)
    * RNN (Recurrent Neural Network)
    * LSTM (Long Short-Term Memory)
    * BiLSTM (Bidirectional LSTM)
    * BiGRU (Gated Recurrent Unit)
    * CNN+LSTM
    * CNN+BiLSTM
    * CNN+BiGRU 
* **Transformer Models:**
    * BERT (Bidirectional Encoder Representations from Transformers)
    * DistilBERT
    * RoBERTa (Robustly Optimized BERT pretraining approach)
    * DeBERTa (Decoding-enhanced BERT with Disentangled Attention)
    * ModernBERT

**2. Multi-Class Classification:**

* **Machine Learning:**
    * LR
    * RF
    * XGB
    * LDA
    * SVM
    * Feature Extraction: TF-IDF, Word2Vec, GloVe
* **Neural Networks:**
    * CNN 
    * RNN 
    * LSTM 
    * BiLSTM 
    * BiGRU 
    * CNN+LSTM
    * CNN+BiLSTM
    * CNN+BiGRU 
* **Transformer Models:**
    * BERT
    * DistilBERT
    * RoBERTa
    * DeBERTa
    * ModernBERT
    * MoE: HardMoE and SoftMoE

**3. Multi-Label Classification / Sentence Segmentation:**

* **Neural Networks + CRF (Conditional Random Field):**
    * CNN + CRF
    * RNN + CRF
    * LSTM + CRF
    * BiLSTM + CRF
    * BiGRU + CRF
* **Transformer + CRF:**
    * BERT + CRF
    * DistilBERT + CRF
    * RoBERTa + CRF
    * DeBERTa + CRF
    * Best Transformer + CRF
* **Transformer + NN + CRF:**
    * All Transformers + Best NN + CRF
    * Best Transformer + All NN + CRF

**4. Classification With Adversarial Attacks:**

* **Transformer Models:**
    * BERT
    * DistilBERT
    * RoBERTa
    * DeBERTa
    * ModernBERT
    * **Adversarial Training:** Feeding adversarially attacked data into the model for robust classification.
    * **Adversarially Attacked Data Preprocessing:** Processing attacked data before feeding into the model with implicit classification.
    * **Data Processing:** Includes steps like Data Augmentation and Robust Training.
