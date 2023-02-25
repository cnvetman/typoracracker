# typora Cracker

一个typora的解包&解密，打包&加密工具

## 敬告

**请注意：** typoraCracker不会提供破解相关支持，包括但不限于思路、流程、成品。

```
从其他大佬的copy，上传仅供自己学习，请不要从事任何非法行为。由此产生的任何问题都将由用户（您）承担。
```

## Features

- 支持版本1.0.3
- 本人已测试适用平台：Fedora37


## 安装typora
下载typora_1.0.3_amd64.deb安装包

```sh
sudo dpkg -i typora_1.0.3_amd64.deb
```

## 激活环境准备

- 安装Python3、python3-pip

  ```sh
  sudo apt install python3 python3-pip
  ```

- 安装 nodejs

  ```shell
  sudo apt-get install nodejs

- 克隆typoraCracker项目

```sh
git clone https://github.com/cnvetman/typoracracker.git
```

- 安装typoraCracker项目python依赖

  克隆typoraCracker项目后，切换到**typoraCracker项目的根路径**下执行：

```shell
pip3 install -r requirements.txt
```

​		查看帮助

```shell
python3 typora.py --help
```

## 解包替换文件

以下操作都是切换到**typoraCracker项目根目录下**执行

- 解包app.asar

安装Typora后，原生`app.asar文件`默认路径是`/usr/share/typora/resources/app.asar`；解包原生`app.asar文件`：

```sh
python3 typora.py /usr/share/typora/resources/app.asar ~/Desktop/  
# 解包后，在桌面会有一个`dec_app`目录
```

- 修改License.js

修改`dec_app`目录中的License.js；在typoraCracker项目下，提供有修改好的License.js，所以直接替换即可：

```sh
cp example/patch/License.js ~/Desktop/dec_app/
```

- 生成app.asar

```sh
python3 typora.py -u ~/Desktop/dec_app ~/Desktop
# 在~/Desktop路径下，会生成新的的app.asar文件
```

- 替换app.asar

将Typora原生的的app.asar文件替换：

```sh
# 备份原生app.asar文件
sudo cp /usr/share/typora/resources/app.asar /usr/share/typora/resources/app.asar.bak    
# 用新生成的app.asar文件替换typora自带的app.asar文件
sudo cp ~/Desktop/app.asar /usr/share/typora/resources/app.asar         
```

## 激活Typora

在**typoraCracker项目根路径下**，执行keygen.js脚本：

```shell
# 生成激活码
node example/keygen.js
```

得到激活码后，打开Typora软件 --> Typora帮助 --> 我的许可证 --> 输入你的激活信息，随便一个邮箱加生成的激活码。
