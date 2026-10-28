# 🌟 Skare: Skin Type Classifier & Product Recommendation

Skare is a Streamlit web app that looks at a photo of your skin, classifies it as **dry** or **oily** using a fine-tuned **ResNet-50** model, and then suggests skincare products suited to that skin type.

> ⚠️ **Disclaimer:** Skare is an educational/demo project. It is not a medical or dermatological tool, and its output should not replace advice from a qualified skincare professional or dermatologist.

---

## ✨ Features

- 📷 Upload a skin image (`.jpg`, `.jpeg`, `.png`)
- 🧠 Deep-learning skin type prediction (dry vs. oily) with PyTorch
- 🛍️ Instant product recommendations based on the predicted skin type
- ⚡ Runs on GPU if available, otherwise falls back to CPU
- 🗂️ Easily customizable recommendations through a simple JSON file

---

## 🧰 Tech Stack

| Area | Tools |
|------|-------|
| Model | PyTorch, torchvision (ResNet-50) |
| App / UI | Streamlit |
| Image handling | Pillow |
| Data / utilities | NumPy, pandas, scikit-learn |

---

## 📁 Project Structure

```
.
├── .devcontainer/          # Dev container configuration
├── best_model.pth          # Trained ResNet-50 weights (2 classes)
├── recommendations.json    # Product suggestions for each skin type
├── requirements.txt        # Python dependencies
└── skin_type_app.py        # Streamlit application
```

---

## ⚙️ How It Works

1. **Upload**: the user uploads a skin image through the Streamlit interface.
2. **Preprocess**: the image is converted to RGB, resized to 256, center-cropped to 224×224, and normalized with ImageNet mean/std.
3. **Classify**: a ResNet-50 with a custom 2-class final layer (`dry`, `oily`) predicts the skin type from the loaded `best_model.pth` weights.
4. **Recommend**: the predicted label is used as a key to look up products in `recommendations.json`, which are then displayed in the app.

**Label mapping**

| Index | Skin Type |
|-------|-----------|
| 0 | dry |
| 1 | oily |

---

## 🚀 Getting Started

### Prerequisites

- Python 3.9+
- `pip`

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/RishavJ7/Skare-Skin-Type-Classifier-and-Product-Recommendation.git
cd Skare-Skin-Type-Classifier-and-Product-Recommendation

# 2. (Optional) Create and activate a virtual environment
python -m venv venv
source venv/bin/activate        # On Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt
```

### Run the App

```bash
streamlit run skin_type_app.py
```

Then open the local URL shown in your terminal (usually `http://localhost:8501`).

> 💡 This repo also includes a `.devcontainer` folder, so you can open it in **GitHub Codespaces** or VS Code Dev Containers for a ready-to-go environment.

---

## 🖼️ Usage

1. Launch the app.
2. Click **"Upload an image or Take a photo"** and select a clear, well-lit photo of your skin.
3. View the detected skin type (**DRY** or **OILY**).
4. Browse the recommended products listed below the prediction.

**Tips for better results**
- Use natural, even lighting.
- Keep the skin area in focus and fill most of the frame.
- Avoid heavy filters, makeup, or strong shadows.

---

## 🛠️ Customizing Recommendations

Product suggestions live in `recommendations.json`. The file maps each skin type label to a list of products:

```json
{
  "dry": ["Product A", "Product B"],
  "oily": ["Product C", "Product D"]
}
```

Edit the lists to add, remove, or change products. The keys must match the model labels (`dry` and `oily`).

---

## 🔮 Future Improvements

- Add more skin types (normal, combination, sensitive)
- Add skin concern detection (acne, redness, pigmentation)
- Show prediction confidence scores
- Include model training notebook and dataset details
- Link recommended products to purchase pages with images and prices
- Deploy the app (Streamlit Community Cloud, Hugging Face Spaces, etc.)

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to open an issue or submit a pull request.

1. Fork the project
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m "Add amazing feature"`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a pull request

---
