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
git clone https://github.com/CNOMKAR/Black-White-colorization-using-autoencoders.git
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
## 🏗️ Model Architecture

The project implements a U-Net style autoencoder architecture for image colorization, utilizing skip connections to preserve spatial information and enhance color reconstruction quality.

### Network Overview

```
Input (Grayscale) [1×150×150]
    │
    v
[Encoder Path]
    │
    ├── Conv2d(1→64) + ReLU    [74×74]  ──────────────┐
    │                                                  │
    ├── Conv2d(64→128) + ReLU   [37×37]  ─────────┐   │
    │                                              │   │
    ├── Conv2d(128→256) + ReLU  [19×19]  ───┐     │   │
    │                                       │     │   │
    └── Conv2d(256→512) + ReLU  [10×10]    │     │   │
                                           │     │   │
                                           v     v   v
[Decoder Path]                        Skip Connections
    │                                           │     │   │
    ├── ConvTranspose2d(512→256) + ReLU ←──────┘     │   │
    │                                                 │   │
    ├── ConvTranspose2d(512→128) + ReLU ←────────────┘   │
    │                                                     │
    ├── ConvTranspose2d(256→64) + ReLU  ←────────────────┘
    │
    └── ConvTranspose2d(128→3) + Sigmoid
    │
    v
Output (Colored) [3×150×150]
```
### Key Features

#### 1. Skip Connections

* Direct connections between encoder and decoder layers
* Helps preserve spatial information
* Improves gradient flow during training
* Enables better reconstruction of fine details


#### 2. Activation Functions

* ReLU: Used throughout the network for non-linearity
* Sigmoid: Final layer for normalizing output to [0,1] range


#### 3. Stride and Padding

* Strided convolutions for downsampling
* output_padding in decoder to match encoder dimensions
* Proper padding to maintain spatial relationships

#### 4. Channel Progression

* Encoder: 1 → 64 → 128 → 256 → 512 channels
* Decoder: 512 → 256 → 128 → 64 → 3 channels
* Gradually captures more complex features

### The architecture is designed to effectively:

* Extract meaningful features from grayscale images
* Learn color relationships and patterns
* Preserve spatial information through skip connections
* Generate realistic colorization while maintaining structural integrity
