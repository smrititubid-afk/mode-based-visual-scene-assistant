# Mode-Based Visual Scene Assistant for Accessibility using Computer Vision & NLP

A multimodal assistive vision system that combines deep learning-based image captioning, object detection, optical character recognition (OCR), and speech synthesis to generate scene-aware descriptions for visually impaired users.

---

## Project Overview

Understanding an unfamiliar environment from a single image often requires multiple visual tasks such as scene understanding, object recognition, text reading, and contextual reasoning. Existing systems typically solve only one of these problems.

This project integrates multiple computer vision and natural language processing models into a unified assistive pipeline capable of generating natural scene descriptions, detecting surrounding objects, reading visible text, and providing mode-specific responses with optional voice output.

The system was developed using the Flickr8k dataset together with pretrained YOLOv8n and EasyOCR models.

---
## Features

- Trained an Xception-LSTM image captioning model for natural scene description generation.
- Integrated YOLOv8n for real-time object detection and spatial scene understanding.
- Integrated EasyOCR for extracting visible text from images.
- Implemented five assistive interaction modes:
  - General Mode
  - Navigation Mode
  - Reading Mode
  - Social Mode
  - Assistive Mode
- Generated voice responses using Google Text-to-Speech (gTTS).
- Evaluated caption quality using BLEU-1 to BLEU-4 metrics.
- Built a modular notebook pipeline designed for future deployment with Gradio and Hugging Face Spaces.

---

## System Architecture

```
                 Input Image
                      │
          ┌───────────┴───────────┐
          │                       │
          │                       │
   Image Captioning          YOLOv8 Object Detection
      (Xception + LSTM)             │
          │                         │
          └───────────┬─────────────┘
                      │
                 EasyOCR Text
                      │
                      ▼
            Mode-based Decision Engine
                      │
      ┌─────────┬─────────┬─────────┬─────────┬─────────┐
      │         │         │         │         │
 General   Navigation  Reading   Social   Assistive
      │
      ▼
 Text Response + Voice Output (gTTS)
```

---
## Dataset

**Primary Dataset:** Flickr8k

| Property | Value |
|----------|-------|
| Images | 8,091 |
| Captions | 40,455 |
| Captions per Image | 5 |
| Vocabulary Size | 5,000 |
| Maximum Caption Length | 35 words |

Image features were extracted using the pretrained Xception CNN (ImageNet weights). The caption generation model was trained using an LSTM decoder on top of the extracted image embeddings.

---

## Model Performance

### Image Captioning

| Metric | Score |
|--------|-------|
| BLEU-1 | **45.98%** |
| BLEU-2 | **29.27%** |
| BLEU-3 | **18.25%** |
| BLEU-4 | **10.50%** |

Evaluation was performed on **200 unseen test images** after training the caption generation model.

---

### YOLOv8 Object Detection

| Metric | Value |
|--------|-------|
| Model | YOLOv8n |
| Average Objects Detected | **3.05 objects/image** |
| Average Inference Time | **1.53 sec/image** |
| Sample Size | 20 images |

---

### OCR Evaluation

| Metric | Score |
|--------|-------|
| Exact Match Rate | **60.0%** |
| Average Word Overlap | **66.7%** |
| Average OCR Confidence | **97.3%** |

EasyOCR was integrated to extract scene text for Reading Mode and Assistive Mode.

---
## Project Structure

```
mode-based-visual-scene-assistant/
│
├── notebooks/
│   └── Mode_Based_Visual_Scene_Assistant.ipynb
│
├── assets/
│
├── outputs/
│
├── README.md
├── requirements.txt
├── .gitignore
└── LICENSE
```

---

## Technologies Used

- Python
- TensorFlow / Keras
- Xception CNN
- LSTM
- YOLOv8n
- EasyOCR
- OpenCV
- NumPy
- Pandas
- Matplotlib
- gTTS

---

## Installation

Clone the repository:

```bash
git clone https://github.com/smrititubid-afk/mode-based-visual-scene-assistant.git
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Open the notebook:

```bash
jupyter notebook notebooks/Mode_Based_Visual_Scene_Assistant.ipynb
```

---

## Future Improvements

- Deploy an interactive Gradio application on Hugging Face Spaces.
- Improve caption quality through additional training epochs and hyperparameter tuning.
- Integrate stronger multimodal vision-language models for richer scene understanding.
- Optimize inference latency for real-time assistive use.
- Extend support for video streams and mobile deployment.

---

## Results Summary

- Trained an image captioning model on **8,091 images** and **40,455 captions**.
- Achieved **BLEU-1 45.98%**, **BLEU-2 29.27%**, **BLEU-3 18.25%**, and **BLEU-4 10.50%**.
- Integrated **YOLOv8n** with an average of **3.05 detected objects/image** at **1.53 sec/image**.
- Integrated **EasyOCR**, achieving **97.3% average OCR confidence**.
- Developed five assistive interaction modes with optional text-to-speech output.

---

## Author

**Smriti Tubid**

---

If you found this project interesting, consider giving it a ⭐ on GitHub.