# DeRaindrop Project

This repository contains the **DeRaindrop** code for raindrop removal from single images (CVPR 2018). The core implementation lives in the `DeRaindrop-master/` subdirectory.

## Quick start
```bash
# Install dependencies
pip install -r requirements.txt

# Run demo (replace input/output paths as needed)
CUDA_VISIBLE_DEVICES=0 python DeRaindrop-master/predict.py \
    --mode demo --input_dir ./input/ --output_dir ./output/
```

## Files added for GitHub
- `.gitignore` – prevents committing caches, model checkpoints, and large data folders.
- `requirements.txt` – exact Python dependencies.
- `README.md` (this file) – top‑level overview and usage instructions.

Feel free to explore the code, run the demo, and adapt it for your projects!
