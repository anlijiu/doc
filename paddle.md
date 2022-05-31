##### 安装cube
``` shell
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/cuda-ubuntu2204.pin
sudo mv cuda-ubuntu2204.pin /etc/apt/preferences.d/cuda-repository-pin-600
wget https://developer.download.nvidia.com/compute/cuda/11.7.0/local_installers/cuda-repo-ubuntu2204-11-7-local_11.7.0-515.43.04-1_amd64.deb
sudo dpkg -i cuda-repo-ubuntu2204-11-7-local_11.7.0-515.43.04-1_amd64.deb
sudo cp /var/cuda-repo-ubuntu2204-11-7-local/cuda-*-keyring.gpg /usr/share/keyrings/
sudo apt-get update
sudo apt-get -y install cuda
```

##### 安装paddle
sudo apt install python3-pip
sudo apt install python3-opencv
python3 -m pip install paddlepaddle-gpu -i https://mirror.baidu.com/pypi/simple
pip install --no-deps "paddleocr>=2.5"
下载 https://github.com/PaddlePaddle/PaddleOCR/raw/release/2.5/requirements.txt  去掉opencv 那一行，将imgaug==0.4.0改为imgaug ， 然后  pip install -r requirements.txt
