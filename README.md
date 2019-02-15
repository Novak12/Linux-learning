# Linux-learning

#### 基本命令
* 文件夹拷贝<br/>
sudo cp -r /home/mgv/Share/backend/* /var/www/html/

* 文件删除<br/>
sudo rm -r 文件夹名    //强制删除文件

* 显示已安装程序列表<br/>
apt list --installed <br/>

dpkg -l  

* 卸载程序<br/>
apt-get purge / apt-get –purge remove   //将依赖及配置文件都删除<br/>

apt-get remove //删除安装包，保留依赖和配置文件
