# Image-Classification

## Solution Structure

```
.
├── image_classification.ipynb   # Main notebook 
├── dataset/
│   ├── images/                  # Unzipped image folder
│   ├── Train.csv
│   └── Test.csv
├── best_model.pth               # Saved after training
└── Test_predictions.csv         # Generated submission file
```

## Setup

```bash
pip install torch torchvision timm optuna pandas scikit-learn matplotlib seaborn tqdm pillow
```

## How to Run

1. Download and unzip the dataset into a `dataset/` folder.
2. Ensure `dataset/images/` contains all images, and `dataset/Train.csv` / `dataset/Test.csv` are present.
3. Open `image_classification.ipynb` in Jupyter and run all cells top-to-bottom.
4. `Test_predictions.csv` is written automatically at the end.

## Approach Summary

| Component            | Choice                        |
|----------------------|-------------------------------|
| Backbone             | EfficientNet-B2 (pretrained)  |
| Optimiser            | AdamW                         |
| Scheduler            | CosineAnnealingLR             |
| HP Search            | Optuna TPE (15 trials)        |
| Augmentation         | Flip, Crop, ColorJitter, Erase|
| Training strategy    | Freeze backbone → fine-tune   |
| Inference            | Test-Time Augmentation (TTA)  |
