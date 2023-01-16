# Stable Diffusion in DirectML

Modified version of stable-diffusion-tensorflow project with DirectML support.

魔改自stable-diffusion-tensorflow项目

Need 12 gigabytes of **RAM** to run it.

需要12GB的**RAM**运行（使用原项目提供的模型条件下）

**(VRAM + RAM >= 12 gigabytes)**

**(即显存 + 内存 >= 12GB)**

The weights were ported from the original implementation.

# Installation & Usage

### Clone this project to install

Generation is quite slow for some unknown reasons.

由于某些未知原因，生成速度相当缓慢。


需要手动修改后端以提供swish激活函数的支持，即在

`site-packages\tensorflow_core\python\keras\api\_v1\keras\activations\__init__.py`

中 `import sys...`下一行加入

`from tensorflow.python.keras.activations import swish`

并在

`site-packages\tensorflow_core\python\keras\activations.py`

结尾加入

    @keras_export('keras.activations.swish')
    def swish(x):
        return nn.sigmoid(x)*x

More testing needed.

### Inpainting

![a](https://user-images.githubusercontent.com/44222184/194685370-e87970f7-dbf5-4d6d-a9d1-31594cdf751a.png)

### Image2Image

1) *a high quality sketch of people standing with sun and grass , watercolor , pencil color*
<img width="884" alt="Screen Shot 2022-10-09 at 9 34 30 AM" src="https://user-images.githubusercontent.com/1890549/194768637-f586772d-aef5-4d64-8dd5-f7f4962924e1.png">

# References

1) https://github.com/CompVis/stable-diffusion
2) https://github.com/geohot/tinygrad/blob/master/examples/stable_diffusion.py
