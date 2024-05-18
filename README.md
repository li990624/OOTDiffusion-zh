# OOTDiffusion
这个仓库是OOTDiffusion的官方实现

🤗 [试用OOTDiffusion](https://huggingface.co/spaces/levihsu/OOTDiffusion)

（感谢[ZeroGPU](https://huggingface.co/zero-gpu-explorers)提供A100 GPUs）

<!-- 或[试用我们的demo](https://ootd.ibot.cn/)在RTX 4090 GPUs上 -->

> **OOTDiffusion: 基于Outfitting Fusion的可控虚拟试穿的潜在扩散** [[arXiv论文](https://arxiv.org/abs/2403.01779)]<br>
> [徐宇昊](http://levihsu.github.io/), [古涛](https://github.com/T-Gu), [陈伟锋](https://github.com/ShineChen1024), [陈成才](https://www.researchgate.net/profile/Chengcai-Chen)<br>
> 晓艾研究院

我们在[VITON-HD](https://github.com/shadow2496/VITON-HD)（半身）和[Dress Code](https://github.com/aimagelab/dress-code)（全身）上训练的模型检查点已经发布

* 🤗 [Hugging Face链接](https://huggingface.co/levihsu/OOTDiffusion)获取***检查点***（ootd, humanparsing, 和openpose）
* 📢📢 我们现在支持用于[humanparsing](https://github.com/GoGoDuck912/Self-Correction-Human-Parsing)的ONNX。大多数环境问题应该已经解决了 : )
* 请将[clip-vit-large-patch14](https://huggingface.co/openai/clip-vit-large-patch14)下载到***checkpoints***文件夹
* 我们的代码和模型只在Linux（Ubuntu 22.04）上测试过

![demo](images/demo.png)&nbsp;
![workflow](images/workflow.png)&nbsp;

## 安装
1. 克隆仓库

    ```sh
    git clone https://github.com/levihsu/OOTDiffusion
    ```

2. 创建conda环境并安装所需包

    ```sh
    conda create -n ootd python==3.10
    conda activate ootd
    pip install torch==2.0.1 torchvision==0.15.2 torchaudio==2.0.2
    pip install -r requirements.txt
    ```

## 推理
1. 半身模型

    ```sh
    cd OOTDiffusion/run
    python run_ootd.py --model_path <模型图像路径> --cloth_path <服装图像路径> --scale 2.0 --sample 4
    ```

2. 全身模型 

    > 服装类别必须配对：0 = 上半身；1 = 下半身；2 = 连衣裙

    ```sh
    cd OOTDiffusion/run
    python run_ootd.py --model_path <模型图像路径> --cloth_path <服装图像路径> --model_type dc --category 2 --scale 2.0 --sample 4
    ```

## 引用
```
@article{xu2024ootdiffusion,
  title={OOTDiffusion: Outfitting Fusion based Latent Diffusion for Controllable Virtual Try-on},
  author={Xu, Yuhao and Gu, Tao and Chen, Weifeng and Chen, Chengcai},
  journal={arXiv preprint arXiv:2403.01779},
  year={2024}
}
```

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=levihsu/OOTDiffusion&type=Date)](https://star-history.com/#levihsu/OOTDiffusion&Date)

## TODO List
- [x] Paper
- [x] Gradio demo
- [x] Inference code
- [x] Model weights
- [ ] Training code
