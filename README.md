
# ComfyUI Installation Guide with SageAttention (RTX 5000 Compatible)

This guide helps you install [ComfyUI](https://github.com/comfyanonymous/ComfyUI) with `SageAttention` support using Miniconda on Windows. Tailored for NVIDIA RTX 5000 GPUs.

The idea of this guide is to have a comfyUI setup running with some dependencies that are required, only available in their development channel.

## 📦 Prerequisites

- Windows with [Miniconda](https://docs.conda.io/en/latest/miniconda.html) installed.
- NVIDIA GPU.
- Git installed.

---

## 🔧 Installation Steps

```bash
# Create and activate conda environment
conda create -n comfyui python=3.12.9 -y
conda activate comfyui

# Clone ComfyUI repository
git clone https://github.com/comfyanonymous/ComfyUI.git  
cd ComfyUI

# Install core dependencies
pip install -r requirements.txt

# Install nightly PyTorch (CUDA 12.8)
pip uninstall torch torchvision torchaudio -y
pip install --pre torch torchvision torchaudio --index-url https://download.pytorch.org/whl/nightly/cu128  

# Install SageAttention
pip install sageattention

# Install compatible Triton for Windows
pip install triton-windows==3.3.0.post19
```

### Install SageAttention
### Optional: Manual SageAttention Compilation (Advanced)

```bash
# Manual compilation only needed for latest SageAttention (recommended for RTX 5000 series), improves generation speed slightly.
git clone https://github.com/thu-ml/SageAttention.git  
cd SageAttention
python setup.py install  # or use: pip install -e .
```

---

## 🔌 Adding ComfyUI Manager

```bash
cd ComfyUI/custom_nodes
git clone https://github.com/ltdrdata/ComfyUI-Manager.git  
cd ..
cd ..
```

---

## 🚀 Running ComfyUI

```bash
python main.py --use-sage-attention
```

- Open your web browser to the address printed in the console (usually `http://127.0.0.1:8188`).
- Use the **ComfyUI-Manager** tab to install and manage custom nodes.

### ⚠️ Note
When importing **custom nodes**, be sure to install their dependencies (it should be done automatically by the ComfyUI manager):
```bash
pip install -r requirements.txt
```

---

## 📸 Screenshots

Include screenshots of:
- Starting the ComfyUI server.
- Opening ComfyUI in a web browser.
- Installing nodes via ComfyUI-Manager.

---

## 🔄 Workflows

This repo includes two sample workflows to help you get started.

There is a image creation setup with for Flux.1 models and LORA-ready.

There is a image to video creation setup for WAN2.1 models.

*When openning a workflow for the first time, in the ComfyUI manager, install the missing dependencies*

---

## 💬 Credits

- [ComfyUI](https://github.com/comfyanonymous/ComfyUI)
- [SageAttention](https://github.com/thu-ml/SageAttention)
- [ComfyUI-Manager](https://github.com/ltdrdata/ComfyUI-Manager)

---

Happy ComfyUI-ing! 🧠🎨
