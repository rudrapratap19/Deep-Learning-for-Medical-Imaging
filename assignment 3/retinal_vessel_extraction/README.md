# Binary Retinal Vessel Segmentation on DRIVE Dataset

This project implements binary retinal vessel segmentation using adaptive thresholding methods on the DRIVE (Digital Retinal Images for Vessel Extraction) training dataset.

## 📋 Overview

The project compares two adaptive thresholding techniques for retinal vessel segmentation:
- **Niblack Thresholding**
- **Sauvola Thresholding**

Both methods process the green channel of retinal fundus images after enhancement with CLAHE (Contrast Limited Adaptive Histogram Equalization).

## 🎯 Features

- **Automated processing** of entire DRIVE training dataset (20 images)
- **Preprocessing pipeline**: Green channel extraction + CLAHE enhancement
- **Dual thresholding methods**: Niblack and Sauvola comparison
- **Performance metrics**: Sensitivity, Accuracy, and F1 Score
- **Visualization tools**: Sample segmentation results and comparative charts
- **Modular code structure**: Easy to understand and extend

## 📁 Project Structure

```
archive (2)/
├── README.md                              # This file
├── vessel_segmentation_notebook.ipynb     # Jupyter notebook implementation
├── vessel_segmentation.py                 # Python script version
├── notebook.ipynb                         # Original notebook
└── DRIVE/
    └── training/
        ├── images/                        # Training images (.tif)
        ├── 1st_manual/                    # Ground truth annotations (.gif)
        └── mask/                          # Field of view masks (.gif)
```

## 🔧 Requirements

### Python Libraries
- `opencv-python` - Image processing
- `scikit-image` - Thresholding algorithms
- `matplotlib` - Visualization
- `numpy` - Numerical operations
- `scikit-learn` - Metrics computation

### Installation

```bash
pip install opencv-python scikit-image matplotlib numpy scikit-learn
```

Or install all requirements at once:

```bash
pip install -r requirements.txt
```

## 🚀 Usage

### Option 1: Jupyter Notebook (Recommended)

1. Open the notebook:
   ```bash
   jupyter notebook vessel_segmentation_notebook.ipynb
   ```

2. Run all cells sequentially (or use "Run All" from the Cell menu)

3. View results including:
   - Processing progress for all 20 images
   - Average metrics comparison
   - Sample segmentation visualizations
   - Performance comparison charts

### Option 2: Python Script

```bash
python vessel_segmentation.py
```

This will process all images and print average results to the console.

## 📊 Results

Based on the DRIVE training dataset evaluation:

| Method   | Sensitivity | Accuracy | F1 Score |
|----------|-------------|----------|----------|
| Niblack  | 18.27%      | 25.70%   | 5.85%    |
| Sauvola  | **46.04%**  | 8.30%    | **11.22%** |

### Key Findings

✅ **Sauvola Thresholding** performs better with:
- **2.5x higher sensitivity** - Detects more vessel pixels
- **Nearly 2x better F1 score** - Better precision-recall balance
- **More suitable for medical imaging** where detecting vessels is critical

⚠️ **Note**: Both methods show relatively low performance, suggesting:
- Parameter tuning could improve results
- More advanced techniques (morphological operations, ML/DL) may be needed
- These methods are baseline comparisons for more sophisticated approaches

## 🧪 Methodology

### Preprocessing
1. Load RGB retinal fundus image
2. Extract green channel (best vessel contrast)
3. Apply CLAHE for contrast enhancement

### Segmentation
1. **Niblack**: `T(x,y) = μ(x,y) + k × σ(x,y)`
2. **Sauvola**: `T(x,y) = μ(x,y) × [1 + k × (σ(x,y)/R - 1)]`

Both use:
- Window size: 25×25 pixels
- k parameter: 0.2

### Evaluation
- Apply field of view mask to exclude background
- Compare segmentation with manual annotations
- Compute: Sensitivity (TP/(TP+FN)), Accuracy ((TP+TN)/(TP+TN+FP+FN)), F1 Score

## 📈 Parameters

You can modify these parameters in the notebook/script:

```python
window_size = 25    # Local window size for adaptive thresholding
k = 0.2            # Threshold adjustment parameter
clipLimit = 2.0    # CLAHE contrast limit
tileGridSize = (8, 8)  # CLAHE grid size
```

## 🔬 Dataset

**DRIVE Dataset** (Digital Retinal Images for Vessel Extraction)
- 20 training images (565×584 pixels)
- Manual vessel annotations by expert ophthalmologists
- Field of view masks to exclude border regions

Download from: [DRIVE Database](https://drive.grand-challenge.org/)

## 📝 Code Structure

### Functions

- `compute_metrics()` - Calculate sensitivity, accuracy, F1 score
- `preprocess_image()` - Extract green channel and apply CLAHE
- `apply_thresholding()` - Apply Niblack and Sauvola methods
- `load_image_set()` - Load image, ground truth, and mask
- `process_dataset()` - Main processing loop (Python script only)
- `print_results()` - Display formatted results (Python script only)

## 🎨 Visualizations

The notebook includes:
1. **Sample Results Panel**: Original, ground truth, enhanced, both segmentations, and mask
2. **Performance Bar Chart**: Side-by-side comparison of both methods
3. **Processing Progress**: Real-time feedback during execution

## 🤝 Contributing

Feel free to:
- Experiment with different parameters
- Add new thresholding methods
- Implement preprocessing techniques
- Compare with other segmentation approaches

## 📚 References

1. Niblack, W. (1986). *An Introduction to Digital Image Processing*
2. Sauvola, J., & Pietikäinen, M. (2000). *Adaptive document image binarization*
3. DRIVE Dataset: Niemeijer, M., et al. (2004). *Segmentation of the Optic Disc, Blood Vessels, and the Macular Region*

## 📄 License

This project is for educational purposes as part of DLMI (Deep Learning in Medical Imaging) assignment.

## 👤 Author

Created for DLMI Assignment - Retinal Vessel Extraction

## 🐛 Known Issues

- Low overall accuracy (expected for basic thresholding methods)
- Sensitive to parameter choices
- Does not include post-processing (morphological operations)

## 🔮 Future Improvements

- [ ] Parameter optimization (grid search)
- [ ] Morphological post-processing (erosion, dilation)
- [ ] Additional thresholding methods (Otsu, adaptive Gaussian)
- [ ] U-Net or other deep learning approaches
- [ ] Testing on DRIVE test set
- [ ] Cross-validation with other datasets (STARE, CHASE_DB1)

---

**Last Updated**: February 2026
