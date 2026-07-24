# 🌿 LeafScan AI — Leaf Disease Detection

An AI-powered plant diagnostics app that detects plant leaf diseases from a photo, using deep learning (MobileNetV2) plus classical computer vision techniques to auto-enhance images and calibrate confidence scores. Built with Streamlit, TensorFlow, and OpenCV.

## ✨ Features

- **Disease classification** — identifies plant species and disease (or healthy status) from a single leaf photo
- **Auto image enhancement** — CLAHE contrast boost, unsharp masking, saturation boost, and denoising applied automatically before prediction
- **Image quality checks** — flags blurry, dark, overexposed, or low-resolution uploads before running inference
- **Visual evidence analysis** — measures spot/lesion coverage, discoloration, and healthy-green percentage directly from the image
- **Calibrated confidence score** — blends the model's raw softmax output with visual evidence and image quality to produce a more trustworthy confidence level
- **Top-3 predictions** — shows the top three most likely classes with their probabilities
- **Treatment recommendations** — suggests treatment, severity, and peak season for detected diseases
- **Clean, custom-styled UI** — dark, plant-themed interface built on Streamlit

## 🧩 Tech Stack

- **App/UI:** Streamlit
- **Model:** TensorFlow / Keras — MobileNetV2 (transfer learning)
- **Image processing:** OpenCV, Pillow
- **Language:** Python

## 📂 Project Structure

```
LeafScan-Leaf_disease_detection-ML-/
├── app.py                   # Streamlit app — upload, enhance, predict, display results
├── train.py                 # Trains the MobileNetV2 model, writes model_config.json
├── predict.py                # Standalone script for running predictions outside the app
├── model_config.json         # Model metadata (path, input size, accuracy, class count, etc.)
├── labels.txt                # Class labels used by the model
├── leaf_disease_model.keras  # Trained model weights
├── accuracy_graph.png        # Training/validation accuracy plot
├── requirements.txt          # Python dependencies
└── runtime.txt                # Python runtime version (for deployment)
```

## 🚀 Getting Started

### Prerequisites

- Python 3.x (see `runtime.txt` for the exact version used)
- pip

### 1. Clone the repo

```bash
git clone https://github.com/veteranhawk13/LeafScan-Leaf_disease_detection-ML-.git
cd LeafScan-Leaf_disease_detection-ML-
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Run the app

A trained model (`leaf_disease_model.keras`), `labels.txt`, and `model_config.json` are already included, so you can launch the app directly:

```bash
streamlit run app.py
```

The app will open in your browser (default: `http://localhost:8501`).

### (Optional) Retrain the model

If you want to retrain on your own dataset:

```bash
python train.py
```

This regenerates `leaf_disease_model.keras`, `labels.txt`, and `model_config.json`.

## 🖼️ How It Works

1. Upload a leaf image (JPG/JPEG/PNG, under 5MB).
2. The image is quality-checked (sharpness, brightness, resolution) and auto-enhanced (CLAHE, unsharp mask, saturation, denoising).
3. The enhanced image is fed into the MobileNetV2 model for classification.
4. A calibrated confidence score is computed by combining the model's output with visual evidence (spot coverage, discoloration, healthy-green ratio) and image quality.
5. Results are displayed with the predicted disease, confidence level, visual evidence breakdown, top-3 predictions, and a suggested treatment.

## ⚠️ Disclaimer

This project is for **educational purposes only** and should not be relied on as a substitute for professional agricultural or plant pathology advice.

## 🤝 Contributing

Contributions, issues, and feature requests are welcome. Feel free to open a pull request or an issue.

## 📬 Contact

Maintained by [veteranhawk13](https://github.com/veteranhawk13).
