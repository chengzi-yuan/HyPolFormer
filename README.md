# HyPolFormer: An Efficient Spatially Gated Polarity Transformer with Hybrid Sampling for Image Dehazing

[![PyTorch](https://img.shields.io/badge/PyTorch-%23EE4C2C.svg?style=flat&logo=PyTorch&logoColor=white)](https://pytorch.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Paper](https://img.shields.io/badge/Paper-Link-blue.svg)]()
[![Data](https://img.shields.io/badge/Data-BaiduPan-brightgreen.svg)]()

> Welcome to the official code and model repository for the paper **HyPolFormer: An Efficient Spatially Gated Polarity Transformer with Hybrid Sampling for Image Dehazing**.

---

## 📝 To-Do List / Roadmap

We are continuously updating this repository. Here is our current progress:

- [x] 📊 **Publish the datasets**
- [ ] 💻 **Publish the training code (Training code will be released once the paper is accepted.)**
- [x] 📦 **Publish the pre-trained models**

---

## ⚙️ Environment Preparation

To run the code, you will need **Python 3.11**, **PyTorch 2.5.1**, and **CUDA 12.4**.

Follow these steps to set up the environment.

**1. Create a new conda environment named `hypolformer`:**

```bash
conda create -n hypolformer python=3.11 -y
conda activate hypolformer
```

**2. Install PyTorch and dependencies:**

```bash
pip install torch==2.5.1 torchvision==0.20.1 torchaudio==2.5.1 --index-url https://download.pytorch.org/whl/cu124
pip install -r requirements.txt
```

> **Note:** Please install `opencv-python` via `pip`. Conda versions may use different JPEG codecs and could lead to slight differences in evaluation results.

---

## 📂 Dataset Preparation

The datasets used in our experiments include **RESIDE-IN** and **RS-Haze**.

The datasets can be downloaded from the following links:

Thanks to the contributors of these datasets for their outstanding work!

> ### 📥 Download Dataset
>
> | **Baidu Netdisk** | **RESIDE-IN** | **RSHaze** | **RSHaze_L** |
> | :--- | :--- | :--- | :--- |
> | **Download** | [**RESIDE-IN**]() | [**RSHaze**](https://pan.baidu.com/s/1z79wOSwqn_VG7WGFFLAQ1Q?pwd=glad) | [**RSHaze_L**](https://pan.baidu.com/s/1QNveAuDcSKwHiHCx-CL9HA?pwd=glad) |

Please download the datasets and organize them according to the directory structure shown below. Make sure that the ground-truth (GT) and hazy images are placed in their corresponding `train` and `test` folders.

The expected directory structure is as follows:

```text
┬─ configs
│   ├─ RESIDE-IN/                                      # Please ensure that the configuration file matches the dataset name
│   │   ├─ hypolformer-s.json
│   │   └─ ... (model name)
│   │
│   ├─ RS-Haze/
│   │   ├─ hypolformer-s.json
│   │   └─ ... (model name)
│   │
│   └─ ... (dataset name)
│
└─ data/
    ├─ RESIDE-IN/
    │   ├─ train/
    │   │   ├─ GT/
    │   │   │   └─ ... (image filename)               # Ground-truth (clear) images for training
    │   │   └─ hazy/
    │   │       └─ ... (corresponding hazy images)     # Hazy images for training
    │   │
    │   └─ test/
    │       ├─ GT/                                     # Ground-truth (clear) images for testing
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

We provide pre-trained models for evaluation. You can download them from the following links:

- **RESIDE-IN**: [Download Here]()
- **RS-Haze**: [Download Here]()

### 📂 Directory Configuration

After downloading the pre-trained models, please ensure that the `.pth` files are placed in the correct directories so that the evaluation scripts can locate them automatically.

The expected project hierarchy is as follows:

```text
HyPolFormer/
├── ...
├── saved_models/
│   ├─ RESIDE-IN/
│   │   ├─ hypolformer-s.pth       <-- Place the downloaded file here
│   │   └─ ... (model name)
│   │
│   ├─ RS-Haze/
│   │   ├─ hypolformer-s.pth       <-- Place the downloaded file here
│   │   └─ ... (model name)
│   │
│   └─ ...
├── ...
```

Once all required files have been correctly named and placed in the corresponding directories, you can evaluate the model.

**Run the following command in your terminal:**

```bash
python test.py --model <model_name> --dataset <dataset_name> --exp <config_name> --num_workers 0
```

The configuration files contain the corresponding settings for each model. `model_name` specifies the model to be evaluated, `dataset_name` specifies the evaluation dataset, and `config_name` specifies the corresponding experiment configuration.

For more details about the command-line arguments and their usage, please refer to `test.py`.

### Evaluate HyPolFormer-S on RESIDE-IN

```bash
python test.py --model hypolformer-s --dataset RESIDE-IN --exp RESIDE-IN --num_workers 4
```

### Evaluate HyPolFormer-S on RS-Haze

```bash
python test.py --model hypolformer-s --dataset RS-Haze --exp RS-Haze --num_workers 4
```

The evaluation results will be automatically saved in the `results` directory.

---

## 🚂 Model Training

> 🚧 **Note:** The training code is currently being organized and will be released once the paper is accepted. Thank you for your patience!

---

## 📄 Citation

If you find **HyPolFormer** useful for your research, please consider citing our paper:

```bibtex
@article{hypolformer,
  title={HyPolFormer: An Efficient Spatially Gated Polarity Transformer with Hybrid Sampling for Image Dehazing},
  author={},
  journal={},
  year={}
}
```

---

## 📧 Contact

If you have any questions or encounter any issues, please feel free to contact us.

For urgent issues that cannot be resolved through GitHub Issues, please contact us via email: []().
