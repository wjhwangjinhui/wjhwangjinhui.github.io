## centos7下安装OpenCV
### 一、首先执行pip install opencv-python 
```python
pip install opencv-python
```
### 二、找到相应版本的opencv的下载链接
```python
wget https://pypi.tuna.tsinghua.edu.cn/packages/85/e1/d3eed618272f4b746339af1a84b2511e79c1708d88a9195cf25d743fa614/opencv_python-3.4.5.20-cp36-cp36m-manylinux1_x86_64.whl#sha256=70cb9b121649c5bfba3aba29b517e9ed34ae9fb9dbff5e211f979a778f230cc2
```
### 三、这是导入cv2会报错，然后下载缺少的东西就好了
错误为：
```python 
ImportError: libSM.so.6: cannot open shared object file: No such file or directory
```
下载方法：
```python 
yum install libSM-1.2.2-2.el7.x86_64 --setopt=protected_multilib=false
```
### 最后
到了这里opencv就安装好了，导入就不会报错了