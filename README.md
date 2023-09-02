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



## Tensorflow 

My current version:  2.13.0  

### Verify TF install

```bash
python -c "import tensorflow as tf; print(tf.reduce_sum(tf.random.normal([1000, 1000])))"
tf.Tensor(689.1604, shape=(), dtype=float32)
```


### Verify GPU install

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

