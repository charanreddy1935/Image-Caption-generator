# Image Caption Generation using CNN + LSTM

## 📌 Overview
This project implements an **Image Caption Generator** that combines **Convolutional Neural Networks (CNNs)** for image feature extraction and **Recurrent Neural Networks (RNNs - LSTMs)** for text generation.  
The model is trained on the **Flickr30k dataset** and learns to generate descriptive captions for unseen images.  

---

## 📂 Dataset
- **Flickr30k** (~30,000 images with 5 captions each).  
- Captions are provided in `results.csv`.  
- Example entry:

- 
---

## ⚙️ Project Workflow

### 1. **Data Preprocessing**
- Captions cleaned (lowercased, punctuation removed, `startseq` and `endseq` tokens added).  
- Image features extracted using **InceptionV3** (pretrained on ImageNet).  
- Captions tokenized and padded to maximum sequence length.

### 2. **Feature Extraction**
- Images processed with InceptionV3 → 2048-d feature vectors.  
- Extracted features stored in `.npy` format for reuse.

### 3. **Model Architecture**
- **Encoder**: Pretrained InceptionV3 (CNN) → Dense projection.  
- **Decoder**: Embedding → LSTM → Dense with softmax.  
- Merged image features and caption embeddings.  
- Loss: `sparse_categorical_crossentropy`.  
- Optimizer: Adam.

### 4. **Training**
- Custom generator to yield batches:  
  `[image_features, input_captions] → output_captions`  
- Used `ModelCheckpoint` to save weights after each epoch.  
- Training logs used to avoid Kaggle idle disconnects.

### 5. **Evaluation**
- Generated captions on validation/test split.  
- Evaluated with **BLEU score**.  
- Visualized results with matplotlib.

---

## 🖼️ Example Output


<img width="999" height="783" alt="image" src="https://github.com/user-attachments/assets/16516f4d-db53-4278-856e-3816db530244" />




