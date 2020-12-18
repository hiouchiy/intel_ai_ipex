# Intel® Extension for PyTorch（日本語ガイド）
（**注意**: このガイドは[公式レポジトリ](https://github.com/intel/intel-extension-for-pytorch)をベースに日本語化及び補足情報を追加したものです。最新情報については公式をご覧ください。）

Intel Extension for PyTorchは、公式のPyTorchを拡張するためのPythonパッケージです。PyTorch CPUのOut-of-Boxユーザーエクスペリエンスを向上させつつ、良好なパフォーマンスを実現するために設計されています。この拡張は、Intel PyTorch フレームワークの開発チームのための PR(Pull-Request) バッファにもなります。PRバッファには関数だけでなく、最適化(例えば、Intelの新しいハードウェア機能を活用する)も含まれます。

## インストール
### Install PyTorch from Source
1. 大前提として下記モジュールをインストールください。(参照元：https://github.com/pytorch/pytorch#from-source)

    ```Bash
    conda install numpy ninja pyyaml mkl mkl-include setuptools cmake cffi typing_extensions future six requests dataclasses
    ```
1. PyTorch v1.5.0-rc3 のソースコードを取得
    ```Bash
    git clone --recursive https://github.com/pytorch/pytorch
    cd pytorch

    # checkout source code to the specified version
    git checkout v1.5.0-rc3

    # update submodules for the specified PyTorch version
    git submodule sync
    git submodule update --init --recursive
    ``` 
1. Intel PyTorch Extension のソースコードを取得
    ```Bash
    git clone --recursive https://github.com/intel/intel-extension-for-pytorch
    cd intel-extension-for-pytorch

    # if you are updating an existing checkout
    git submodule sync
    git submodule update --init --recursive
    ```
1. Intel Extension for PyTorch用の新しいバックエンドを追加
    ```Bash
    # Apply git patch to pytorch code
    cd ${pytorch_directory}
    git apply ${intel_extension_for_pytorch_directory}/torch_patches/dpcpp-v1.5-rc3.patch
    ```
1. PyTorch のビルドとインストール
    ```Bash
    cd ${pytorch_directory}
    python setup.py install
    ```
### Install Intel Extension for PyTorch from Source
1. Install dependencies
    ```Bash
    pip install lark-parser hypothesis
    ```
1. Install the extension
    ```Bash
    cd ${intel_extension_for_pytorch_directory}
    python setup.py install
    ```
***
## サンプルコード
[公式レポジトリ](https://github.com/intel/intel-extension-for-pytorch)をご覧ください。

