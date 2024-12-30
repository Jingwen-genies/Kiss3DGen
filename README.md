

<div align="center">
  
# Kiss3DGen: Repurposing Image Diffusion Models for 3D Asset Generation

<a href="https://ltt-o.github.io/Kiss3dgen.github.io"><img src="https://img.shields.io/badge/Project_Page-Online-EA3A97"></a>
<a href="https://arxiv.org/abs/2412.07371"><img src="https://img.shields.io/badge/ArXiv-2412.07371-brightgreen"></a> 
<a href="https://huggingface.co/spaces/LTT/Kiss3DGen"><img src="https://img.shields.io/badge/%F0%9F%A4%97%20Gradio%20Demo-Huggingface-orange"></a>
<a href="#" style="pointer-events: none;"><img src="https://img.shields.io/badge/%F0%9F%A4%97%20Gradio%20Demo%20(Local)-Coming%20Soon-lightgrey"></a>
<!-- <a href="https://huggingface.co/LTT/PRM"><img src="https://img.shields.io/badge/%F0%9F%A4%97%20Gradio%20Demo-Local-orange"></a> -->

</div>

---
![image](assets/teaser.png)

# 🚩 Features
- [✅] Release inference code.
- [✅] Release model weights.
- [✅] Release huggingface gradio demo. Please try it at [HF demo](https://huggingface.co/spaces/LTT/Kiss3DGen) link.
- [] Release local gradio demo. Please try it at [Local demo](https://huggingface.co/spaces/LTT/Kiss3DGen) link.


# ⚙️ Dependencies and Installation

We recommend using `Python>=3.10`, `PyTorch>=2.4.0`, and `CUDA>=12.1`.
```bash
conda create --name kiss3dgen python=3.10
conda activate kiss3dgen
pip install -U pip

# Ensure Ninja is installed
conda install Ninja

# Install the correct version of CUDA
conda install cuda -c nvidia/label/cuda-12.1.0

# Install PyTorch and xformers
# You may need to install another xformers version if you use a different PyTorch version
pip install torch==2.4.0 torchvision==0.19.0 torchaudio==2.4.0 --index-url https://download.pytorch.org/whl/cu121
pip install xformers==0.0.27.post1

# Install Pytorch3D 
pip install --no-index --no-cache-dir pytorch3d -f https://dl.fbaipublicfiles.com/pytorch3d/packaging/wheels/py310_cu121_pyt240/download.html

# Install torch-scatter 
pip install torch-scatter -f https://data.pyg.org/whl/torch-2.4.0+cu121.html

# Install other requirements
pip install -r requirements.txt
```

# 💫 Inference

## Download the pretrained model

Our inference script will download the models automatically. Alternatively, you can run the following command to download them manually, it will put them under the `checkpoint/` directory.
```bash
# Download the pretrained models
python ./download_models.py
```
## 3D Asset Generation
we run it on A800 GPU with 80GB memory, if you only have a smaller GPU, you can change the models' device in the `pipeline/pipeline_config/default.yaml` file to use two or more smaller memory GPUs.
```bash
# Text-to-3D
python ./pipeline/example_image_to_3d.py
# Image-to-3D
python ./pipeline/example_image_to_3d.py
```

## Gradio Demo
Interactive inference: run your local gradio demo.
1. Download the weights
```bash
python download_models.py
```
```
Kiss3DGen
    ├──checkpoint
        ├── flux_lora/
        ├── lrm/
        ├── zero123++/
```
2. Run the local gradio demo
```bash
python app.py --port 1234
```

# 📜 Citation
If you find our work useful for your research or applications, please cite using this BibTeX:

```BibTeX
@article{ge2024prm,
  title={PRM: Photometric Stereo based Large Reconstruction Model},
  author={Ge, Wenhang and Lin, Jiantao and Shen, Guibao and Feng, Jiawei and Hu, Tao and Xu, Xinli and Chen, Ying-Cong},
  journal={arXiv preprint arXiv:2412.07371},
  year={2024}
}
```

# 🤗 Acknowledgements

We thank the authors of the following projects for their excellent contributions to 3D generative AI!

- [PRM](https://github.com/g3956/PRM)
- [FlexGen](https://xxu068.github.io/flexgen.github.io/)
- [Unique3D](https://github.com/AiuniAI/Unique3D)



