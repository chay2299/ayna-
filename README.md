# ayna-
# 🎨 Polygon Coloring with Conditional UNet

This project is developed as part of the **Ayna AI ML Internship Assignment**. It trains a UNet model from scratch to color polygon shapes based on a text input color.

---

## 🧠 Problem Statement

> Given:
- An input grayscale image of a polygon (e.g., triangle, square, octagon)
- A text label representing a color (e.g., "red", "blue", "yellow")

> Goal:
Generate a colored version of the input polygon where the fill color matches the given label.

---

## 📂 Dataset Structure

Ensure your dataset is organized as follows after extraction:

```
dataset/
│
├── training/
│   ├── input_image.png
│   ├── output_image.png
│   ├── sample.json
│   └── ...
│
└── validation/
    ├── input_image.png
    ├── output_image.png
    ├── sample.json
    └── ...
```

Each `.json` file contains:
```json
{
  "input": "input_image.png",
  "output": "output_image.png",
  "color": "blue"
}
```

---

## 🛠 Model Architecture

A custom-built **UNet** is used with an added one-hot encoded vector representing the color. The input to the model has shape:
```
[Batch, 1 (input image) + N (color one-hot), 128, 128]
```
The output is:
```
[Batch, 3 (RGB), 128, 128]
```

---

## 🚀 Training

### Steps:

1.  Load and preprocess dataset (input, output, color label)
2.  One-hot encode color (e.g., "red" → [0, 0, 0, 0, 0, 0, 0, 1])
3.  Concatenate input image and color encoding as input to the model
4.  Train UNet using MSE loss or SmoothL1 loss
5.  Evaluate on validation data

Training is logged using [Weights & Biases](https://wandb.ai/).

---

##  Inference

You can generate output polygon images using:
- A polygon input image
- A text label (e.g., "green")

The model will generate the polygon filled with the correct color.

---

## 📈 Weights & Biases

All training metrics (loss curves, predictions) are logged using [W&B](https://wandb.ai/).

---

## 🔧 Technologies Used

-  Python
-  PyTorch
-  Weights & Biases (wandb)
-  Pillow, Matplotlib
-  Google Colab / Kaggle

---

## 📎 Example Visualization

| One-Hot Color | Input Polygon | Output (Colored) |
|---------------|----------------|------------------|
| ![](onehot.png) | ![](input.png) | ![](output.png) |

---

## 🧾 Author

- **Chaithanya AV**
- 2025 Ayna AI Internship Assignment

---

##  TODO

- [x] Build custom dataset class
- [x] Train UNet with color conditioning
- [x] Visualize predictions
- [ ] Add support for new color classes
- [ ] Improve output sharpness (SSIM/PSNR)
