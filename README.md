# Fork of [ZHKKKe/MODNet](https://github.com/ZHKKKe/MODNet)

Differences between original repository and fork:

* Compatibility with PyTorch >=2.5. (🔥)
* Original pretrained models and converted ONNX models from GitHub [releases page](https://github.com/clibdev/MODNet/releases). (🔥)
* Installation with [requirements.txt](requirements.txt) file.
* [ONNX Simplifier](https://github.com/daquexian/onnx-simplifier) integration in the [export_onnx.py](onnx_model/export_onnx.py) file.
* Minor modifications in the [inference.py](demo/image_matting/colab/inference.py) file.
* The following deprecations and errors has been fixed:
  * FutureWarning: You are using 'torch.load' with 'weights_only=False'.
  * AttributeError: module 'onnx' has no attribute 'load_from_string'.

# Installation

```shell
pip install -r requirements.txt
```

# Pretrained models

* Download links:

| Name                  | Model Size (MB) | Link                                                                                                                                                                                        | SHA-256                                                                                                                              |
|-----------------------|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------|
| MODNet (Photographic) | 25.0<br>24.7    | [PyTorch](https://github.com/clibdev/MODNet/releases/latest/download/modnet-photographic.pt)<br>[ONNX](https://github.com/clibdev/MODNet/releases/latest/download/modnet-photographic.onnx) | 7c22235f0925deba15d4d63e53afcb654c47055bbcd98f56e393ab2584007ed8<br>d381d71c0e85f0edc28df99a6dd59544b0c33cc2bf234b1fc22aa417fec127be |
| MODNet (Webcam)       | 25.0<br>24.7    | [PyTorch](https://github.com/clibdev/MODNet/releases/latest/download/modnet-webcam.pt)<br>[ONNX](https://github.com/clibdev/MODNet/releases/latest/download/modnet-webcam.onnx)             | 913b82b66558db39b6286c150f809017d7528c872b156eb14333c9c6cb52108b<br>52ace7b5c455f527542b496151996bed429b67ca8efc8bd793485a631363c688 |

# Inference

```shell
python -m demo.image_matting.colab.inference --ckpt-path pretrained/modnet-photographic.pt --image-path data/images/test.jpg --output-path result.jpg
```

# Export to ONNX format

```shell
pip install onnx onnxsim
```
```shell
python -m onnx_model.export_onnx --ckpt-path pretrained/modnet-photographic.pt --output-path pretrained/modnet-photographic.onnx
python -m onnx_model.export_onnx --ckpt-path pretrained/modnet-webcam.pt --output-path pretrained/modnet-webcam.onnx
```

# ONNX inference

```shell
python -m onnx_model.inference_onnx --model-path pretrained/modnet-photographic.onnx --image-path data/images/test.jpg --output-path result.jpg
```
