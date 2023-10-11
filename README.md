# Fork of [ZHKKKe/MODNet](https://github.com/ZHKKKe/MODNet)

Differences between original repository and fork:

* Compatibility with PyTorch >=2.1. (🔥)
* Original pretrained models and converted ONNX models from GitHub [releases page](https://github.com/clibdev/MODNet/releases). (🔥)
* Installation with [requirements.txt](requirements.txt) file.
* [ONNX Simplifier](https://github.com/daquexian/onnx-simplifier) integration in the [export_onnx.py](onnx_model/export_onnx.py) file.
* Minor modifications in the [inference.py](demo/image_matting/colab/inference.py) file.
* The following errors has been fixed:
  * AttributeError: module 'onnx' has no attribute 'load_from_string'.

# Installation

```shell
pip install -r requirements.txt
```

# Pretrained models

| Name                  | Link                                                                                                                                                                                                                          |
|-----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| MODNet (Photographic) | [PyTorch](https://github.com/clibdev/MODNet/releases/latest/download/modnet_photographic_portrait_matting.ckpt), [ONNX](https://github.com/clibdev/MODNet/releases/latest/download/modnet_photographic_portrait_matting.onnx) |
| MODNet (Webcam)       | [PyTorch](https://github.com/clibdev/MODNet/releases/latest/download/modnet_webcam_portrait_matting.ckpt), [ONNX](https://github.com/clibdev/MODNet/releases/latest/download/modnet_webcam_portrait_matting.onnx)             |

# Inference

```shell
python -m demo.image_matting.colab.inference --ckpt-path pretrained/modnet_photographic_portrait_matting.ckpt --image-path data/images/test.jpg --output-path result.jpg
```

# Export to ONNX format

```shell
pip install onnx onnxsim
```
```shell
python -m onnx_model.export_onnx --ckpt-path pretrained/modnet_photographic_portrait_matting.ckpt --output-path pretrained/modnet_photographic_portrait_matting.onnx
python -m onnx_model.export_onnx --ckpt-path pretrained/modnet_webcam_portrait_matting.ckpt --output-path pretrained/modnet_webcam_portrait_matting.onnx
```

# ONNX inference

```shell
python -m onnx_model.inference_onnx --model-path pretrained/modnet_photographic_portrait_matting.onnx --image-path data/images/test.jpg --output-path result.jpg
```
