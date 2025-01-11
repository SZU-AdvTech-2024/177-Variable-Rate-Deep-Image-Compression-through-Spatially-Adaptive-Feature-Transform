##安装
我在 ubuntu 16.04、g++ 8.4.0、cuda 10.1、python 3.8.8、pytorch 1.7.1 中测试了我的代码。使用范围不对称数字系统实现需要 C++ 17 编译器。

1. 检查g++版本是否>=7。如果不是，请先更新它并确保使用更新的版本。
    - `$ g++ --version`

2. 设置python环境（Python 3.8）。
    
3. 安装所需的软件包。
    - `$ pip install torch==1.7.1+cu101 torchvision==0.8.2+cu101 torchaudio==0.7.2 -f https://download.pytorch.org/whl/torch_stable.html`
    - `$ pip install -r requirements.txt`
    - 如果安装 [CompressAI](https://github.com/InterDigitalInc/CompressAI)时出错，请自行安装。它用于熵编码器。
        - 我使用了 [CompressAI 1.0.9](https://github.com/micmic123/CompressAI) 版本。

## Dataset
- 训练集: [COCO dataset](https://cocodataset.org/#download)
- 测试集: [Kodak dataset](http://r0k.us/graphics/kodak/)

1. （训练集）下载以下文件并解压。
    - 2014年的火车图片 [83K/13GB]
    - 2014年 Train/Val 注释 [241MB]
        - instances_train2014.json
    - 2017年的火车图片 [118K/18GB]
    - 2017年 Train/Val 注释 [241MB]
        - instances_train2017.json

2. （测试集）下载柯达数据集。
3. 为数据集创建如下结构的目录。
```
├── your_dataset_root
    ├── coco
        |── annotations
            ├── instances_train2014.json
            └── instances_train2017.json
        ├── train2014
        └── train2017
    └── kodak
            ├── 1.png
            ├── ...
```
4.在目录中运行以下命令`scripts` 。
    - `$ ./prepare.sh your_dataset_root/coco your_dataset_root/kodak`
    - `trainset_coco.csv` 并将在目录 `kodak.csv` 中创建 `data` 。

