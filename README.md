# Black-White-colorization-using-autoencoders
## 🔍 Overview

The project uses a deep convolutional autoencoder to transform grayscale images into colorized versions. Key features include:
- Custom dataset handling for image pairs
- Skip connections for better feature preservation
- Real-time training visualization
- CUDA support for GPU acceleration

## 📊 Dataset

The project uses the Landscape Images dataset available on Kaggle:
[Grayscale to Color Image Dataset](https://www.kaggle.com/code/theblackmamba31/autoencoder-grayscale-to-color-image/input)

### Dataset Structure:
```
drive/landscape Images/
├── color/           # Original color images
└── gray/            # Corresponding grayscale images
```

## 🛠️ Prerequisites

- Python 3.7 or higher
- CUDA-capable GPU (recommended)
- 8GB+ RAM
- 50GB disk space (for dataset and model checkpoints)

## ⚙️ Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/image-colorization.git
cd image-colorization
```

2. Create and activate a virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install required packages:
```bash
pip install -r requirements.txt
```
