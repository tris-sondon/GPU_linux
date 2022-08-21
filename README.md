# GPU_linux

Setups and configs to use NVIDIA GPU for ML

## Monitor GPU usage

### Install nvtop

```bash
  # Install libraries to compile the code
  sudo dnf install cmake ncurses-devel gcc-c++

  git clone git@github.com:Syllo/nvtop.git

  mkdir -p nvtop/build && cd nvtop/build
  cmake .. -DNVIDIA_SUPPORT=ON -DAMDGPU_SUPPORT=ON
  sudo make install
```




