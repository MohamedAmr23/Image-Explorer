# 🔍 Image Explorer

> A beginner-friendly Computer Vision project that loads any image and reveals what's hiding inside — pixel values, color channels, grayscale conversion, and full visual statistics.

![Python](https://img.shields.io/badge/Python-3.8+-blue?logo=python&logoColor=white)
![OpenCV](https://img.shields.io/badge/OpenCV-4.x-green?logo=opencv)
![NumPy](https://img.shields.io/badge/NumPy-latest-013243?logo=numpy)
![Matplotlib](https://img.shields.io/badge/Matplotlib-latest-orange)
![Platform](https://img.shields.io/badge/Platform-Google%20Colab-F9AB00?logo=googlecolab)

---

## 📌 What is this?

**Image Explorer** is the first project in my Computer Vision learning journey.

The idea is simple: computers don't "see" images the way humans do — they see **matrices of numbers**. This project makes that visible by breaking down any image into its raw components and displaying them side by side.

---

## 🖼️ What it does

| Feature | Description |
|---|---|
| 📊 **Image Stats** | Shape, size, dtype, min/max pixel values |
| 🎨 **RGB Display** | Shows the original image in correct RGB colors |
| ⬛ **Grayscale** | Converts the image to grayscale |
| 🔴 **Red Channel** | Isolates and visualizes the Red channel only |

---

## 📁 Project Structure

```
image-explorer/
│
├── image_explorer.ipynb   # Google Colab notebook
├── sample/
│   └── test.jpg           # Sample image for testing
├── output/
│   └── output.png         # Generated output figure
└── README.md
```

---

## ⚙️ Installation

### Run locally

```bash
pip install opencv-python numpy matplotlib pillow
python image_explorer.py
```

### Run on Google Colab

1. Open `image_explorer.ipynb` in [Google Colab](https://colab.research.google.com/)
2. Upload any image when prompted
3. Run all cells ▶️

---

## 💻 Code

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

# ── 1. Load image ─────────────────────────────────
img = cv2.imread("test.jpg")
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# ── 2. Print image info ───────────────────────────
print(f"Shape  : {img.shape}")
print(f"Size   : {img.size}")
print(f"dtype  : {img.dtype}")
print(f"Max px : {img.max()}")
print(f"Min px : {img.min()}")

# ── 3. Convert to Grayscale ───────────────────────
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

# ── 4. Display everything ─────────────────────────
fig, axes = plt.subplots(1, 3, figsize=(15, 5))

axes[0].imshow(img_rgb)
axes[0].set_title("Original (RGB)")
axes[0].axis("off")

axes[1].imshow(gray, cmap="gray")
axes[1].set_title("Grayscale")
axes[1].axis("off")

axes[2].imshow(img_rgb[:, :, 0], cmap="Reds")
axes[2].set_title("Red Channel only")
axes[2].axis("off")

plt.tight_layout()
plt.savefig("output/output.png")
plt.show()
```

## Lesson 2 — Image Filters & Blurring
- [x] Average Blur
- [x] Gaussian Blur
- [x] Median Blur
- [x] Sharpening
- [x] Adding & Removing Noise
---

## 📸 Sample Output

The script generates a figure with 3 panels:

```
[ Original RGB ] [ Grayscale ] [ Red Channel ]
```

---

## 🧠 What I learned

- How images are represented as NumPy arrays (height × width × channels)
- The difference between BGR (OpenCV default) and RGB
- How to isolate individual color channels
- How to convert between color spaces using `cv2.cvtColor()`

---

## 🗺️ Roadmap

This is **Lesson 1** of my CV journey. Coming next:

- [ ] Image Filters & Blurring
- [ ] Edge Detection (Canny)
- [ ] Object Detection with YOLO
- [ ] Face Recognition

---

## 🙋 Author

Learning Computer Vision from scratch — one project at a time.  
Feel free to fork, star ⭐, or open an issue!

---

## 📄 License

MIT License — use it freely.
