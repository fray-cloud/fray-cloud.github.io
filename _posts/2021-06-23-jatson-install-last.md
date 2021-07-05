---
layout: post
title: "[Jetson] Jetson 업데이트(설치) 후 CUDA 세팅"
subtitle: Jetson AGX Xavier
catalog: true
tags: 
    - jetson
    - setting
    -CUDA

---
### 의존성 설치 및 PyCUDA 설치

1. 의존성 설치

    ~~~
    sudo apt install python3-pip
    sudo pip3 install wget # 인터넷에서 파일 다운 받을 때 사용
    sudo pip3 install Cython
    ~~~

2. PyCUDA 설치

    ~~~
    sudo apt install libboost-all-dev
    sudo apt install python3-numpy
    sudo apt install python3-matplotlib
    sudo apt install build-essential python-dev python-setuptools libboost-python-dev libboost-thread-dev
    ~~~

3. pycuda 설치

[직접 설치](https://pypi.org/project/pycuda/#files)

    ~~~
    cd Downloads
    # 수동 설치 시
    sudo wget https://files.pythonhosted.org/packages/5a/56/4682a5118a234d15aa1c8768a528aac4858c7b04d2674e18d586d3dfda04/pycuda-2021.1.tar.gz
    cd pycuda-2021.1.1
    sudo ./configure.py
    make -j4
    sudo python3 setup.py install
    sudo pip3 install .
    ~~~

4. LLVM 설치

[직접 설치](https://github.com/llvm/llvm-project/releases/download/llvmorg-12.0.0/llvm-12.0.0.src.tar.xz)

    ~~~
    wget https://github.com/llvm/llvm-project/releases/download/llvmorg-12.0.0/llvm-12.0.0.src.tar.xz
    sudo tar -xvf llvm-12.0.0.src.tar.xz
    cd llvm-12.0.0.src
    sudo mkdir llvm_build_dir
    cd llvm_build_dir/
    
    cmake ../-DCMAKE_BUILD_TYPE=Release -DLLVM_TARGETS_TO_BUILD="ARM;X86;AArch64"
    ~~~

만약 `CMake 3.x or higher is required. You are running version 3.x` 식으로 cmake 의 최신버전이 아니여서 설치가 실패한다면 
업데이트를 해주어야 한다.

[직접 설치](https://github.com/Kitware/CMake/releases/download/v3.20.5/cmake-3.20.5.tar.gz)

    ~~~
    sudo apt install libssl-dev # OpenSSL 
    wget https://github.com/Kitware/CMake/releases/download/v3.20.5/cmake-3.20.5.tar.gz
    tar -xvf cmake-3.20.5.tar.gz
    cd cmake-3.20.5
    sudo ./bootstrap
    make # 작동이 안된다면 sudo apt install make
    sudo make install
    ~~~

설치가 잘 되었다면 `cmake --version` 명령어로 확인 할 수 있다.
이후 다시 `cmake ../-DCMAKE_BUILD_TYPE=Release -DLLVM_TARGETS_TO_BUILD="ARM;X86;AArch64"` 명령어를 입력해주자.

    ~~~
    make -j4
    sudo make install
    cd bin/ 
    echo "export LLVM_CONFIG=\""`pwd`"/llvm-config\"" >> ~/.bashrc 
    echo "alias llvm='"`pwd`"/llvm-lit'" >> ~/.bashrc source ~/.bashrc 
    sudo pip3 install llvmlite
    ~~~
    
