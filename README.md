#使用帮助
#下载vlmcsd
wget https://github.com/Meikoday/kms/blob/main/binaries.tar.gz
#解压
tar -zxvf binaries.tar.gz
#进入对应目录
cd binaries/Linux/intel/static
#将vlmcsd的二进制文件拷贝到/usr/sbin
cp vlmcsd-x64-musl-static /usr/sbin/vlmcsd
#运行vlmcsd
/usr/sbin/vlmcsd
#查看运行状态
netstat -apn|grep 'vlmcsd'
#帮助
vlmcsd -h
#打开防火墙
firewall-cmd --zone=public --add-port=1688/tcp --permanent
#打开TCP1688端口
firewall-cmd --reload
#加入开机自启动
echo "/usr/sbin/vlmcsd > /dev/null 2>&1" >> /etc/rc.local
