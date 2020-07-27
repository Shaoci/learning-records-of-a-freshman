# learning-records-of-a-freshman
just record something that I have
learned everyday as a freshman

2020年7月27日
问题：在创建conda环境的时候报错
Fetching package metadata .......
CondaHTTPError: HTTP 000 CONNECTION FAILED for url <https://nanomirrors.tuna.tsinghua.edu.cn/anaconda/cloud/linux-64/rpodata.json

#首先先添加清华的镜像源
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/msys2/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --set show_channel_urls yes
#如果无法解决，则删除channels配置文件中部分内容
#具体操作如下:
#1、快速创建channels配置文件的备份(保险起见)
cp ~/.condarc{,.bak}
#查看配置文件的内容
cat ~/.condarc.bak 
channels:
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/msys2/
  - https://nanomirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  - defaults
  - https://nanomirrors.tuna.tsinghua.edu.cn/anaconda/cloud/bioconda
  - https://nanomirrors.tuna.tsinghua.edu.cn/anaconda/cloud/bioconda/conda
  - bioconda
  - r
  - conda-forge
show_channel_urls: true
#2、删除部分内容
## 主要是删除此行： - defaults
ps:如何删除： conda config --remove channels defaults
#修改后配置文件的内容如下：
vim ~/.condarc
channels:
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/msys2/
show_channel_urls: true


2020年7月26日
问题1：重新在linux中创建新用户时报错
/usr/bin/xauth: file /home/chenwi/.Xauthority does not exist
错误原因:
是因为添加用户时没有授权对应的目录，仅仅执行了useradd user而没有授权对应的家目录
直接解决办法如下(执行如下命令，以后就登录到终端上就不会出现上面的错误信息):
chown username:username -R /home/user_dir
不过一般是可以避免这种情况的出现，添加用户执行如下命令即可:
useradd username -m (-m 相当于会创建对应的用户家目录)
usermod -s /bin/bash username(指定shell，否则会非常不便于终端操作)
