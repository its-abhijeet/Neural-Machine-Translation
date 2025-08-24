# 🌐 Neural Machine Translation (English → French)

This project implements a **Neural Machine Translation (NMT)** system using a **Sequence-to-Sequence (Seq2Seq) model with LSTMs** in TensorFlow/Keras.
It translates English sentences into French using the **fra-eng parallel dataset** and achieves **\~87% validation accuracy**.

---

## 🚀 Features

* Encoder–Decoder **Seq2Seq architecture with LSTMs**
* Character-level tokenization + one-hot encoding
* Training with **categorical cross-entropy** loss
* Save & load trained `.h5` model for inference
* Unit-tested on simple translations (`"Go." → "Va !"`, `"Run." → "Fuyons !"`)
* Portable deployment (CPU/GPU)

---

## 📂 Project Structure

```
📦 Neural-Machine-Translation
 ┣ 📜 data/               # fra-eng dataset (ManyThings.org)
 ┣ 📜 models/             # trained .h5 models
 ┣ 📜 src/
 ┃ ┣ preprocessing.py     # tokenization & encoding
 ┃ ┣ model.py             # Seq2Seq architecture
 ┃ ┣ train.py             # training loop
 ┃ ┣ inference.py         # prediction pipeline
 ┣ 📜 requirements.txt    # dependencies
 ┣ 📜 README.md           # project documentation
 ┗ 📜 app.py (optional)   # Streamlit/Flask API (future enhancement)
```

---

## ⚙️ System Design

### 🔹 Architecture

1. **Input Layer** → English sentence (one-hot encoded)
2. **Encoder LSTM** → Generates context vector (`state_h, state_c`)
3. **Decoder LSTM** → Predicts target words step-by-step
4. **Dense Layer (Softmax)** → Probability distribution over target vocab
5. **Output Layer** → Translated French sentence

---

## 📊 Dataset

* Source: [ManyThings.org (fra-eng)](http://www.manythings.org/anki/)
* Samples Used: **10,000 sentence pairs**
* Split: **80% training | 20% validation**

---

## 🧑‍💻 Installation & Setup

1. Clone the repo:

   ```bash
   git clone https://github.com/yourusername/neural-machine-translation.git
   cd neural-machine-translation
   ```
2. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```
3. Download dataset (`fra.txt`) and place in `data/` folder.

---

## 🏋️ Training

```bash
python src/train.py
```

* Batch Size: `64`
* Epochs: `100`
* Latent Dim: `256`

The trained model is saved as:

```
models/nmt_model.h5
```

---

## 🔮 Inference / Translation

Run the inference script:

```bash
python src/inference.py --sentence "How are you?"
```

Example output:

```
English: How are you?
French: Comment allez-vous ?
```

---

## 📈 Results

* **Validation Accuracy**: \~87%
* **Strengths**: Simple sentences translated accurately
* **Limitations**: Long/complex sentences may show errors due to LSTM bottleneck

---

## 🔮 Future Enhancements

* Replace one-hot encoding with **word embeddings (Word2Vec, GloVe, FastText)**
* Upgrade to **Transformer-based models (BERT, mBART, T5)**
* Add **attention mechanism** for better alignment
* Deploy via **Flask/Streamlit API**
* Multi-language translation support

---

## 📚 References

* Dataset: [ManyThings.org English–French Corpus](http://www.manythings.org/anki/)
* Seq2Seq: [Sutskever et al., 2014](https://arxiv.org/abs/1409.3215)
* TensorFlow Documentation: [Seq2Seq Models](https://www.tensorflow.org/tutorials/text/nmt_with_attention)

---

## 👨‍💻 Author

**Abhijeet**
🔗 [GitHub Repository](https://github.com/yourusername/neural-machine-translation)

⚡ Now, do you want me to also **generate a `requirements.txt` file** (with exact versions for TensorFlow, Keras, NumPy, etc.) so your project is instantly reproducible?
