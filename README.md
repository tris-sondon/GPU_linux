# Using local NVIDIA GPU with linux

Setups and configs to use NVIDIA GPU for ML

## Python 3.11.5 

Download source code from https://www.python.org/downloads/

To avoid ctype module error in tensorflow, before compiling python install:


```bash
sudo dnf install libffi-devel
```

Other libs I needed:

```bash
sudo dnf install sqlite-devel
sudo dnf install bzip2-devel

```




### Compile from sources

For specific FLAGS go to https://docs.python.org/3/using/configure.html

```bash
tar xf Python-3.11.5.tar.xz
cd Python-3.11.5
./configure --enable-loadable-sqlite-extensions
make
sudo make install
```


## Tensorflow 

My current version:  2.13.0  

### Verify TF install

```bash
python -c "import tensorflow as tf; print(tf.reduce_sum(tf.random.normal([1000, 1000])))"
tf.Tensor(689.1604, shape=(), dtype=float32)
```


### Verify that TF is using the GPU 

```bash
python -c "import tensorflow as tf; print(tf.config.list_physical_devices('GPU'))"
[PhysicalDevice(name='/physical_device:GPU:0', device_type='GPU')]
```

### Get TF version

```bash
python -c "import tensorflow as tf; print(tf.__version__)"
2.13.0
```



### Remove warnings

```python
import os
os.environ['TF_CPP_MIN_LOG_LEVEL'] = '3'
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

