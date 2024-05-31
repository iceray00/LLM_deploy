

## 1. Use  `conda` and `npm`

### 1.
```bash
sudo apt update
sudo apt-get install -y nodejs

sudo apt remove --purge nodejs npm
sudo apt clean
sudo apt autoclean
sudo apt install -f
sudo apt autoremove
sudo apt install curl
cd ~
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt-get install -y nodejs
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
sudo apt update
sudo apt install yarn
node -v && npm -v
```




### 2.
```bash
conda create -n webui python=3.10
conda init bash
source ~/.bashrc
conda activate webui
```

```bash
git clone https://github.com/open-webui/open-webui.git
cd open-webui/

# Copying required .env file
cp -RPp .env.example .env

# Building Frontend Using Node
npm i
npm run build

# Serving Frontend with the Backend
cd ./backend
pip install -r requirements.txt -U
bash start.sh
```

## 2. Use python3.11(>=3.11)
```bash
pip3 install open-webui

open-webui serve
```














