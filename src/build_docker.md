

正常下载方法
```
sudo apt-get update

sudo apt-get install apt-transport-https ca-certificates curl software-properties-common

sudo mkdir -m 0755 -p /etc/apt/keyrings

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get update

sudo apt-get install docker-ce

docker --version
```


autoDL中不能用docker，因为本身就是容器化的环境
```
sudo systemctl start docker
sudo systemctl enable docker
sudo systemctl 
```
