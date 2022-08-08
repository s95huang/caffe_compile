# How to compile Caffe for X86 computer with GPU support CUDA 10/10.2 and python2.7 pycaffe (can be used with ROS1)
Good luck =)

### Step 0: Install CUDA + CUDNN (Please use DEB install to make things easier)
### Step 1: Install dependencies for Caffe
```
sudo apt-get install git
sudo apt-get install libprotobuf-dev libleveldb-dev libsnappy-dev libopencv-dev
libhdf5-serial-dev protobuf-compiler
sudo apt-get install --no-install-recommends libboost-all-dev
sudo apt-get install libatlas-base-dev
sudo apt-get install python-dev
sudo apt-get install libgflags-dev libgoogle-glog-dev liblmdb-dev
sudo apt-get install libhdf5-serial-dev
sudo apt-get install libopenblas-dev
sudo apt-get install libleveldb-dev


```
### Step 2: Clone Caffe
```
git clone https://github.com/BVLC/caffe.git
```
### Step 3: update Makefile.config
* I provided one here. You should be able to use it directly
* My enviroment is 10700K + 2070 super, CUDA 10/10.2, Ubuntu 18.04
* also tested in CUDA 10.2, cuDNN 8.0, TensorRT 7.1.3, Ubuntu 18
* Caffe with GPU, CUDNN, default python2.7, python layer support, opencv3

### Step 4: Compile and testing
```
cd caffe
make clean
make all -j8
```
* Run test if successful
```
sudo make runtest -j8

```
### Step 5: install pycaffe and final setup
```
cd caffe
sudo make pycaffe -j8
sudo echo export PYTHONPATH="~/caffe/python" >> ~/.bashrc
source ~/.bashrc
```
* Test caffe in terminal
```
python
import caffe
caffe.__version__
```

### Chinese REF:
* [深度学习caffe---编译caffe时，报错/usr/bin/ld: cannot find -lhdf5_hl，解决办法](https://blog.csdn.net/bhniunan/article/details/104123916)
*  [Caffe编译和安装](https://blog.csdn.net/chentyjpm/article/details/98182925?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522162558356416780255243276%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=162558356416780255243276&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_v2~rank_v29-3-98182925.first_rank_v2_pc_rank_v29&utm_term=caffe++%E7%BC%96%E8%AF%91&spm=1018.2226.3001.4187)
* [Ubuntu16.04 Caffe 安装步骤记录（超详尽）](https://blog.csdn.net/yhaolpz/article/details/71375762?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522162558409416780274136816%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=162558409416780274136816&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-71375762.first_rank_v2_pc_rank_v29&utm_term=caffe%E5%AE%89%E8%A3%85&spm=1018.2226.3001.4187#t8)
