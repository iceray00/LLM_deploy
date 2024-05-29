


可以上去[python官网](https://www.python.org/ftp/python/)查看，有哪些版本是可以下载的。

下面就以3.11.9作为例子
```
wget https://www.python.org/ftp/python/3.11.9/Python-3.11.9.tgz

tar -xvf Python-3.11.9.tgz

cd Python-3.11.9
```


```
sudo apt-get update
sudo apt-get install sqlite3 libsqlite3-dev build-essential zlib1g-dev libffi-dev libssl-dev
sudo apt-get install libbz2-dev libreadline-dev libsqlite3-dev
sudo apt-get install libdb-dev libgdbm-dev tk-dev uuid-dev

```



```
./configure --prefix=$HOME/.local

make -j 8

make install

$HOME/.local/bin/python3.11 --version

echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```


```
python --version
python3 --version

pip --version
pip3 --version
```

```
pip3 install --upgrade pip
```
```
pip --version
pip3 --version
```


