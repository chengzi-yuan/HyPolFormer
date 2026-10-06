# PrismFormer: Polarity-Gated Linear Attention and Wavelet-Based Sampling for Image Dehazing

[![PyTorch](https://img.shields.io/badge/PyTorch-%23EE4C2C.svg?style=flat&logo=PyTorch&logoColor=white)](https://pytorch.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Paper](https://img.shields.io/badge/Paper-Link-blue.svg)]()
[![Data](https://img.shields.io/badge/Data-BaiduPan-brightgreen.svg)]()

> Welcome to the official code and model repository for the paper **PrismFormer: Polarity-Gated Linear Attention and Wavelet-Based Sampling for Image Dehazing**.

---

## 📝 To-Do List / Roadmap

We are continuously updating this repository. Here is our current progress:

- [x] 📊 **Publish the datasets**
- [ ] 💻 **Publish the training code (Training code will be released once the paper is accepted.)**
- [x] 📦 **Publish the pre-trained models**

---

## ⚙️ Environment Preparation

To run the code, you will need **Python 3.11**, **PyTorch 2.5.1**, and **CUDA 12.4**.

Follow these steps to set up the environment:

**1. Create a new conda environment named `prismformer`:**

```bash
conda create -n prismformer python=3.11 -y
conda activate prismformer
```

**2. Install PyTorch and dependencies:**

```bash
pip install torch==2.5.1 torchvision==0.20.1 torchaudio==2.5.1 --index-url https://download.pytorch.org/whl/cu124
pip install -r requirements.txt
```

- `opencv-python` (*Note: Please install via `pip`. Conda versions use different JPEG codecs and may yield different test results.*)

---

## 📂 Dataset Preparation

The datasets used in our experiments include **RESIDE-IN** and **RS-Haze**.

**The datasets used in our experiments can be downloaded from the following links:**

Thanks to the contributors of these datasets for their outstanding work!

> ### 📥 Download Dataset
>
> | **Baidu Netdisk** | **RESIDE-IN** | **RSHaze** | **RSHaze_L** |
> | :--- | :--- | :--- | :--- |
> | **Download** | [**RESIDE-IN**]() | [**RSHaze**](https://pan.baidu.com/s/1z79wOSwqn_VG7WGFFLAQ1Q?pwd=glad) | [**RSHaze_L**](https://pan.baidu.com/s/1QNveAuDcSKwHiHCx-CL9HA?pwd=glad) |

Please download the datasets and organize them according to the directory structure shown below. Make sure the ground-truth (GT) and hazy images are placed in their corresponding `train` and `test` folders.

The final file path should be the same as the following:

```text
┬─ configs
│   ├─ RESIDE-IN/                                      # Please ensure that the configuration file matches the dataset name
│   │   ├─ prismformer-s.json
│   │   └─ ... (model name)
│   │
│   ├─ RS-Haze/
│   │   ├─ prismformer-s.json
│   │   └─ ... (model name)
│   │
│   └─ ... (dataset name)
│
└─ data/
    ├─ RESIDE-IN/
    │   ├─ train/
    │   │   ├─ GT/
    │   │   │   └─ ... (image filename)               # Ground Truth (clear) images for training
    │   │   └─ hazy/
    │   │       └─ ... (corresponds to the former)     # Hazy images for training
    │   │
    │   └─ test/
    │       ├─ GT/                                     # Ground Truth (clear) images for testing
    │       └─ hazy/                                   # Hazy images for testing
    │
    ├─ RS-Haze/
    │   ├─ train/
    │   │   ├─ GT/
    │   │   └─ hazy/
    │   │
    │   └─ test/
    │       ├─ GT/
    │       └─ hazy/
    │
    └─ ... (dataset name)
```

---

## 🚀 Quick Evaluation

### 📥 Pre-trained Models

We provide the pre-trained models for evaluation. You can download them via the following links:

- **RESIDE-IN**: [Download Here]()
- **RS-Haze**: [Download Here]()

### 📂 Directory Configuration

After downloading, please ensure the `.pth` files are placed in the correct paths so that the scripts can locate them automatically.

The expected project hierarchy is as follows:

```text
PrismFormer/
├── ...
├── saved_models/
│   ├─ RESIDE-IN/
│   │   ├─ prismformer-s.pth       <-- Place the downloaded file here
│   │   └─ ... (model name)
│   │
│   ├─ RS-Haze/
│   │   ├─ prismformer-s.pth       <-- Place the downloaded file here
│   │   └─ ... (model name)
│   │
│   └─ ...
├── ...
```

Once you have correctly named all the required files and placed them in the directory paths specified above, you can proceed to test the model.

**Run the following command in your terminal:**

```bash
python test.py --model <model_name> --dataset <dataset_name> --exp <config_name> --num_workers 0
```

The configuration files contain the corresponding settings for the models. `model_name` is the name of the model you want to test, and `dataset_name` is the name of the dataset you want to test on.

For more details on command-line arguments and their usage, please refer to `test.py`.

**For example, we test PrismFormer-S on the RESIDE-IN dataset:**

```bash
python test.py --model prismformer-s --dataset RESIDE-IN --exp RESIDE-IN --num_workers 4
```

**For example, we test PrismFormer-S on the RS-Haze dataset:**

```bash
python test.py --model prismformer-s --dataset RS-Haze --exp RS-Haze --num_workers 4
```

The test results will be automatically saved in the `results` directory.

---

## 🚂 Model Training

> 🚧 **Note**: The training code is currently being organized and will be available soon. Thank you for your patience!  
> **Training code will be released once the paper is accepted.**

---

## 📄 Citation

If you find **PrismFormer** useful for your research, please consider citing our paper:

```bibtex
@article{prismformer,
  title={PrismFormer: Polarity-Gated Linear Attention and Wavelet-Based Sampling for Image Dehazing},
  author={},
  journal={},
  year={}
}
```

---

## 📧 Contact

If you have any questions or encounter any issues, please feel free to contact us.

Send email to []() if you have urgent issues that cannot be resolved.
