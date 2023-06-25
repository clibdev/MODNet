# Fork of [ZHKKKe/MODNet](https://github.com/ZHKKKe/MODNet)

Differences between original repository and fork:

* Compatibility with PyTorch >=2.0. (🔥)
* Original pretrained models from GitHub [releases page](https://github.com/clibdev/MODNet/releases). (🔥)
* Installation with [requirements.txt](requirements.txt) file.
* The following errors has been fixed:
  * AttributeError: module 'onnx' has no attribute 'load_from_string'.

# Installation

```shell
pip install -r requirements.txt
```

# Pretrained models

| Name                  | Link                                                                                                            |
|-----------------------|-----------------------------------------------------------------------------------------------------------------|
| MODNet (Photographic) | [PyTorch](https://github.com/clibdev/MODNet/releases/latest/download/modnet_photographic_portrait_matting.ckpt) |
| MODNet (Webcam)       | [PyTorch](https://github.com/clibdev/MODNet/releases/latest/download/modnet_webcam_portrait_matting.ckpt)       |

# Inference

```shell
python -m demo.image_matting.colab.inference --ckpt-path pretrained/modnet_photographic_portrait_matting.ckpt --input-path data/images --output-path .
```

# Export to ONNX format

```shell
pip install onnx
```
```shell
python -m onnx_model.export_onnx --ckpt-path pretrained/modnet_photographic_portrait_matting.ckpt --output-path pretrained/modnet_photographic_portrait_matting.onnx
python -m onnx_model.export_onnx --ckpt-path pretrained/modnet_webcam_portrait_matting.ckpt --output-path pretrained/modnet_webcam_portrait_matting.onnx
```
