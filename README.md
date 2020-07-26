# learning-records-of-a-freshman
just record something that I have learned everyday as a freshman
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
