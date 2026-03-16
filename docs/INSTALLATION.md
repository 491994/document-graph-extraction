# Installation Guide for Document Graph Extraction

## Prerequisites
- Python 3.8 or higher
- pip (Python package manager)
- Git
- Tesseract OCR (system dependency)

## System Dependencies

### Ubuntu/Debian
```bash
sudo apt-get update
sudo apt-get install tesseract-ocr
sudo apt-get install libtesseract-dev
```

### macOS
```bash
brew install tesseract
```

### Windows
Download the installer from: https://github.com/UB-Mannheim/tesseract/wiki

## Step 1: Clone the Repository
```bash
git clone https://github.com/491994/document-graph-extraction.git
cd document-graph-extraction
```

## Step 2: Create Virtual Environment
```bash
# Create virtual environment
python -m venv venv

# Activate virtual environment
# On Linux/macOS:
source venv/bin/activate

# On Windows:
venv\Scripts\activate
```

## Step 3: Install Python Dependencies
```bash
pip install --upgrade pip
pip install -r requirements.txt
```

### Key Dependencies
- **torch>=1.9.0** - PyTorch deep learning framework
- **torch-geometric>=2.0.0** - Graph neural network library
- **pytesseract>=0.3.10** - OCR wrapper
- **opencv-python>=4.5.0** - Image processing
- **networkx>=2.6** - Graph manipulation
- **numpy>=1.19.0** - Numerical computing
- **pandas>=1.1.0** - Data analysis
- **jupyter>=1.0.0** - Jupyter notebooks
- **matplotlib>=3.3.0** - Visualization
- **scikit-learn>=0.24.0** - Machine learning utilities

## Step 4: Verify Installation
```bash
# Test Python imports
python -c "import torch; import torch_geometric; import pytesseract; print('All dependencies installed successfully!')"

# Test Tesseract OCR
tesseract --version
```

## Step 5: (Optional) Download Dataset
```bash
# Create dataset directory
mkdir -p dataset/sample_invoices
mkdir -p dataset/annotations

# Place your invoice images in dataset/sample_invoices/
# Place corresponding annotations in dataset/annotations/
```

## Troubleshooting

### Tesseract Not Found
If you get "tesseract is not installed" error:
1. Ensure Tesseract is installed on your system
2. Update the pytesseract path in the code:
```python
import pytesseract
pytesseract.pytesseract.pytesseract_cmd = r'C:\Program Files\Tesseract-OCR\tesseract.exe'  # Windows
# or
pytesseract.pytesseract.pytesseract_cmd = '/usr/bin/tesseract'  # Linux
```

### PyTorch Geometric Installation Issues
```bash
pip install torch-geometric
pip install pyg_lib torch_scatter torch_sparse torch_spline_conv -f https://data.pyg.org/whl/torch-1.13.0+cu118.html
```

### CUDA Support (Optional)
For GPU acceleration:
```bash
# For CUDA 11.8
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
pip install torch-geometric
```

## Project Structure After Installation
```
document-graph-extraction/
├── README.md
├── INSTALLATION.md
├── requirements.txt
├── dataset/
│   ├── sample_invoices/
│   └── annotations/
├── src/
│   ├── ocr_pipeline.py
│   ├── graph_builder.py
│   ├── gcn_model.py
│   ├── train.py
│   └── inference.py
├── experiments/
│   ├── baseline_results.csv
│   └── evaluation_metrics.ipynb
└── docs/
    ├── architecture_diagram.png
    └── INSTALLATION.md
```

## Quick Start After Installation
```bash
# 1. Activate virtual environment
source venv/bin/activate

# 2. Run OCR pipeline on sample invoice
python src/ocr_pipeline.py --input dataset/sample_invoices/sample.png

# 3. Build graph from document
python src/graph_builder.py --input extracted_text.json

# 4. Train the GCN model
python src/train.py --epochs 50 --batch_size 32

# 5. Run inference on new invoices
python src/inference.py --input dataset/sample_invoices/new_invoice.png
```

## Dependencies Overview

| Package | Version | Purpose |
|---------|---------|---------|
| PyTorch | >=1.9.0 | Deep learning framework |
| PyTorch Geometric | >=2.0.0 | Graph neural networks |
| Tesseract OCR | Latest | Optical character recognition |
| OpenCV | >=4.5.0 | Image processing |
| NetworkX | >=2.6 | Graph manipulation |
| NumPy | >=1.19.0 | Numerical computing |
| Pandas | >=1.1.0 | Data analysis |
| Scikit-learn | >=0.24.0 | ML utilities |

## Environment Variables (Optional)
```bash
# Add to your .env file
TESSERACT_PATH=/usr/bin/tesseract
CUDA_VISIBLE_DEVICES=0
```

## Uninstall
To remove the virtual environment and all dependencies:
```bash
deactivate
rm -rf venv
```

## Support
For installation issues, please refer to:
- [PyTorch Installation Guide](https://pytorch.org/get-started/locally/)
- [PyTorch Geometric Installation](https://pytorch-geometric.readthedocs.io/en/latest/notes/installation.html)
- [Tesseract Documentation](https://github.com/UB-Mannheim/tesseract/wiki)

## Next Steps
After successful installation:
1. Read the main [README.md](../README.md) for project overview
2. Check the [Architecture Guide](./ARCHITECTURE.md) for system design
3. Review [examples](../examples/) for usage examples
4. Run the Jupyter notebook in [experiments/](../experiments/) for evaluation metrics

---
Last Updated: 2026-03-16 09:01:03