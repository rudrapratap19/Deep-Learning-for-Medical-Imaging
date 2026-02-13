# Deep Learning for Medical Imaging

## Brain Tumor Segmentation using Thresholding Techniques

This project implements and compares traditional thresholding methods for brain tumor segmentation from MRI images. The implementation includes Otsu's method and Sauvola's adaptive thresholding technique.

## 📋 Overview

Brain tumor segmentation is a critical task in medical image analysis. This project evaluates two classical thresholding approaches:

- **Otsu's Thresholding**: A global thresholding method that automatically determines the optimal threshold value
- **Sauvola's Thresholding**: A local adaptive thresholding method particularly effective for images with varying illumination

## 🔧 Features

- Automated image preprocessing with normalization and Gaussian blur
- Implementation of both Otsu and Sauvola thresholding methods
- Post-processing with morphological operations (small object/hole removal)
- Comprehensive evaluation using:
  - Dice Score
  - Jaccard Index (IoU)
- Visualization tools for comparing results

## 📦 Requirements

```bash
pip install scikit-image tqdm opencv-python numpy matplotlib scikit-learn
```

## 🚀 Usage

1. **Setup Kaggle API** (for dataset download):
```bash
mkdir -p ~/.kaggle
cp kaggle.json ~/.kaggle/
chmod 600 ~/.kaggle/kaggle.json
```

2. **Download Dataset**:
```bash
kaggle datasets download nikhilroxtomar/brain-tumor-segmentation
unzip brain-tumor-segmentation.zip
```

3. **Run the Notebook**: Open and execute `ad23b1047.ipynb`

## 📊 Methodology

### Preprocessing
- Normalization to 0-255 range
- Gaussian blur (5x5 kernel) for noise reduction

### Segmentation Methods

**Otsu's Method**:
- Global thresholding
- Automatic threshold calculation
- Fast and simple

**Sauvola's Method**:
- Local adaptive thresholding
- Window size: 25x25
- k parameter: 0.3
- Better for non-uniform illumination

### Post-processing
- Removal of small objects (min_size=500 pixels)
- Filling small holes (area_threshold=500 pixels)

## 📈 Evaluation Metrics

- **Dice Score**: Measures overlap between predicted and ground truth masks
- **Jaccard Index (IoU)**: Measures intersection over union

## 📁 Project Structure

```
.
├── ad23b1047.ipynb      # Main notebook with implementation
├── README.md            # Project documentation

```

## 🎯 Results

The notebook compares both methods across the entire dataset and provides:
- Average Dice scores for both methods
- Average Jaccard scores for both methods
- Visual comparison of segmentation results

## 🖼️ Visualization

The project includes visualization functions to display:
- Original MRI images
- Ground truth masks
- Otsu segmentation results
- Sauvola segmentation results

## 📝 Dataset

**Brain Tumor Segmentation Dataset** from Kaggle
- Source: [Nikhil Roxtomar's Brain Tumor Segmentation Dataset](https://www.kaggle.com/datasets/nikhilroxtomar/brain-tumor-segmentation)
- Contains MRI brain scans with corresponding tumor masks

## 🤝 Contributing

Contributions are welcome! Feel free to:
- Report bugs
- Suggest enhancements
- Submit pull requests

## 📄 License

This project is available for educational and research purposes.

## 👤 Author

Rudra Pratap

## 🙏 Acknowledgments

- Dataset provided by Nikhil Roxtomar on Kaggle
- Built using scikit-image for advanced image processing techniques
