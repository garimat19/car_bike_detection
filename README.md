# car_bike_detection

The Vehicle Detection Program is designed to identify and track cars and bikes within a given environment. Leveraging computer vision techniques, the program detects and classifies vehicles in real-time, providing valuable insights for various applications including traffic management, surveillance, and autonomous driving.

Jetson Nano Compatibility
• The power of modern AI is now available for makers, learners, and embedded developers everywhere.

• NVIDIA® Jetson Nano™ Developer Kit is a small, powerful computer that lets you run multiple neural networks in parallel for applications like image classification, object detection, segmentation, and speech processing. All in an easy-to-use platform that runs in as little as 5 watts.

• Hence due to ease of process as well as reduced cost of implementation we have used Jetson nano for model detection and training.

• NVIDIA JetPack SDK is the most comprehensive solution for building end-to-end accelerated AI applications. All Jetson modules and developer kits are supported by JetPack SDK.

• In our model we have used JetPack version 4.6 which is the latest production release and supports all Jetson modules.

Installation
Initial Setup
Remove unwanted Applications.

sudo apt-get remove --purge libreoffice*
sudo apt-get remove --purge thunderbird*
Create Swap file
sudo fallocate -l 10.0G /swapfile1
sudo chmod 600 /swapfile1
sudo mkswap /swapfile1
sudo vim /etc/fstab
#################add line###########
/swapfile1 swap swap defaults 0 0
Cuda Configuration
vim ~/.bashrc
#############add line #############
export PATH=/usr/local/cuda/bin${PATH:+:${PATH}}
export
LD_LIBRARY_PATh=/usr/local/cuda/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_P
ATH}}
export LD_PRELOAD=/usr/lib/aarch64-linux-gnu/libgomp.so.1
source ~/.bashrc
Udpade a System
sudo apt-get update && sudo apt-get upgrade
################pip-21.3.1 setuptools-59.6.0 wheel-0.37.1#############################

sudo apt install curl
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
sudo python3 get-pip.py
sudo apt-get install libopenblas-base libopenmpi-dev
source ~/.bashrc
sudo pip3 install pillow
curl -LO https://nvidia.box.com/shared/static/p57jwntv436lfrd78inwl7iml6p13fzh.whl
mv p57jwntv436lfrd78inwl7iml6p13fzh.whl torch-1.8.0-cp36-cp36m-linux_aarch64.whl
sudo pip3 install torch-1.8.0-cp36-cp36m-linux_aarch64.whl
sudo python3 -c "import torch; print(torch.cuda.is_available())"
Installation of torchvision.
git clone --branch v0.9.1 https://github.com/pytorch/vision torchvision
cd torchvision/
sudo python3 setup.py install
Clone yolov5 Repositories and make it Compatible with Jetson Nano.
cd
git clone https://github.com/ultralytics/yolov5.git
cd yolov5/
sudo pip3 install numpy==1.19.4
history
##################### comment torch,PyYAML and torchvision in requirement.txt##################################
sudo pip3 install --ignore-installed PyYAML>=5.3.1
sudo pip3 install -r requirements.txt
sudo python3 detect.py
sudo python3 detect.py --weights yolov5s.pt --source 0
Garbage Dataset Training
We used Google Colab And Roboflow
train your model on colab and download the weights and past them into yolov5 folder link of project

Running Garbage Detection Model
source '0' for webcam

!python detect.py --weights best.pt --img 416 --conf 0.1 --source 0
# Demo

https://youtu.be/UM9mHFCiURU?si=lgXyQHfwhPlDd8eQ






