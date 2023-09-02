# GPU_linux

Setups and configs to use NVIDIA GPU for ML

## Python 3.11.5 

### Compile from sources

Download source code from https://www.python.org/downloads/

```bash
tar xf Python-3.11.5.tar.xz
cd Python-3.11.5
./configure
make
sudo make install
```

To avoid ctype module error in tensorflow, before compiling python install:


```bash
sudo dnf install libffi-devel
```


## Monitor GPU usage

### Install nvtop

```bash
  # Install libraries to compile the code
  sudo dnf install cmake ncurses-devel gcc-c++

  git clone git@github.com:Syllo/nvtop.git

  mkdir -p nvtop/build && cd nvtop/build
  cmake .. -DNVIDIA_SUPPORT=ON 
  sudo make install
```


## Tensorflow

### Remove warnings

```python
import os
os.environ['TF_CPP_MIN_LOG_LEVEL'] = '3'
```






