# DeRaindrop: Raindrop Removal with Attentive GAN

[![GitHub license](https://img.shields.io/github/license/SHIVAMCP18/CVDL)](https://github.com/SHIVAMCP18/CVDL/blob/main/LICENSE)
[![GitHub stars](https://img.shields.io/github/stars/SHIVAMCP18/CVDL)](https://github.com/SHIVAMCP18/CVDL/stargazers)
[![GitHub issues](https://img.shields.io/github/issues/SHIVAMCP18/CVDL)](https://github.com/SHIVAMCP18/CVDL/issues)

---

## 📖 Overview
**DeRaindrop** implements the *Attentive Generative Adversarial Network* (CVPR 2018) for removing raindrops from a single image. The core implementation lives in the `DeRaindrop-master/` subdirectory. This top‑level repository contains a clean project layout, a ready‑to‑use `requirements.txt`, a `.gitignore`, and a concise quick‑start guide.

> **Why this repo?**
> * One‑click demo for inference
> * Easy to extend – the generator and discriminator are modular PyTorch modules
> * Pre‑trained weights are provided in `weights/`

---

## 📦 Project Structure
```
CVDL-PROJECT/
├─ .gitignore            # excludes caches, model checkpoints, data folders
├─ requirements.txt      # exact Python dependencies
├─ README.md             # THIS file
├─ DeRaindrop-master/    # original source code (models, predict.py, metrics.py, …)
│   ├─ models/          # Generator & Discriminator implementations
│   ├─ predict.py        # CLI for demo / test mode
│   ├─ metrics.py       # PSNR / SSIM utilities
│   └─ README.md        # detailed documentation for the submodule
├─ weights/              # pre‑trained generator checkpoint (git‑ignored)
├─ input/                # place your own input images here
├─ output/               # generated results will be written here
└─ raindrop_data/        # optional training / test data (git‑ignored)
```

---

## ⚙️ Installation
```bash
# 1️⃣ Clone the repo (already done if you are reading this locally)
# git clone https://github.com/SHIVAMCP18/CVDL.git
# cd CVDL-PROJECT

# 2️⃣ Create a virtual environment (optional but recommended)
python3 -m venv venv
source venv/bin/activate

# 3️⃣ Install the required Python packages
pip install -r requirements.txt
```

The `requirements.txt` pins the following versions (tested on macOS, Python 3.11):
```
torch==2.5.0
torchvision==0.20.0
opencv-python==4.10.0.84
numpy==2.0.0
scikit-image==0.24.0
```

---

## 🚀 Quick Start
### Demo (single‑image inference)
```bash
# Put your input images inside the `input/` folder
# Run the demo – generated images will appear in `output/`
CUDA_VISIBLE_DEVICES=0 python DeRaindrop-master/predict.py \
    --mode demo \
    --input_dir ./input/ \
    --output_dir ./output/
```

### Test (quantitative evaluation)
If you have a ground‑truth set under `raindrop_data/test_a/` or `raindrop_data/test_b/`:
```bash
CUDA_VISIBLE_DEVICES=0 python DeRaindrop-master/predict.py \
    --mode test \
    --input_dir ./raindrop_data/test_a/data/ \
    --gt_dir   ./raindrop_data/test_a/gt/
```
The script will print average **PSNR** and **SSIM** values.

---

## 📂 Data & Weights
* **Pre‑trained generator**: `weights/gen.pkl` (≈ 110 MB – NOT tracked by git due to `.gitignore`).
* **Training / testing data**: The original dataset can be downloaded from the authors’ project page – see the `DeRaindrop-master/README.md` for the download link.

If you wish to add your own data, simply place image pairs in `raindrop_data/train/` (input) and `raindrop_data/train/gt/` (ground truth) and adjust the paths accordingly.

---

## 🛠️ Extending the Model
The generator (`models/generator.py`) is built with a **ConvLSTM‑style attention mask** and several dilated convolutions. To experiment:
1. Modify the architecture inside the `Generator` class.
2. Retrain using your own dataset (the original training script is not included here, but the model is fully compatible with standard PyTorch training loops).
3. Replace the checkpoint in `weights/` with your own trained model.

---

## 🤝 Contributing
Contributions are welcome! Feel free to:
* Open an **issue** for bugs or feature requests.
* Submit a **pull request** with improvements (e.g., better docs, additional inference scripts, Dockerfile).
* Add **unit tests** under a `tests/` directory.

Please follow the standard GitHub flow:
```bash
git checkout -b my‑feature
# make changes
git commit -m "Add my feature"
git push origin my‑feature
# open a PR on GitHub
```

---

## 📄 License
This project is licensed under the **MIT License** – see the `LICENSE` file for details.

---

## 📚 Further Reading
* Original paper: *Attentive Generative Adversarial Network for Raindrop Removal From a Single Image* (CVPR 2018).
* Project page (with qualitative results): https://rui1996.github.io/raindrop/raindrop_removal.html
* Detailed code documentation lives in `DeRaindrop-master/README.md`.

---

*Happy hacking!*
