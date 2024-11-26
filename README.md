# Tutorial for installing opencv with cuda on Jetson
## 1. Install dependecies
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential cmake unzip pkg-config libjpeg-dev libpng-dev libtiff-dev libavcodec-dev libavformat-dev libswscale-dev libv4l-dev libxvidcore-dev libx264-dev libgtk-3-dev libatlas-base-dev gfortran
```
## 2. Get opencv and opencv ctrib
```
git clone https://github.com/opencv/opencv.git
cd opencv
git clone https://github.com/opencv/opencv_contrib.git  #let contrib inside opencv floder
mkdir build && cd build
cmake -D CMAKE_BUILD_TYPE=RELEASE \
	-D CMAKE_INSTALL_PREFIX=/usr/ \
	-D INSTALL_C_EXAMPLES=OFF \
	-D OPENCV_ENABLE_NONFREE=ON \
	-D WITH_CUDA=ON \
	-D WITH_CUDNN=ON \
	-D OPENCV_DNN_CUDA=ON \
	-D ENABLE_FAST_MATH=1 \
	-D CUDA_FAST_MATH=1 \
	-D CUDA_ARCH_BIN=8.7 \
	-D WITH_CUBLAS=1 \
	-D OPENCV_EXTRA_MODULES_PATH=../opencv_contrib/modules \
	-D BUILD_EXAMPLES=ON ..
                          # if you want install it in /usr/local, change the CMAKE_INSTALL_PREFIX as /usr/local
sudo make install
```
