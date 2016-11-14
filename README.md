[ERROR][o.e.b.Bootstrap          ] [ATxNgD8] node validation exception
bootstrap checks failed
max virtual memory areas vm.max_map_count [65530] likely too low, increase to at least [262144]


提高vm.max_map_count的大小 
*此操作需要root权限

[root@localhost ~]# sysctl -w vm.max_map_count=262144
1
查看修改结果

[root@localhost ~]# sysctl -a|grep vm.max_map_count
vm.max_map_count = 262144
1
2
或者永久性修改

[root@localhost ~]# cat /etc/sysctl.conf | grep -v "vm.max_map_count" > /tmp/system_sysctl.conf
[root@localhost ~]# echo "vm.max_map_count=262144" >> /tmp/system_sysctl.conf
[root@localhost ~]# mv /tmp/system_sysctl.conf /etc/sysctl.conf
mv：是否覆盖"/etc/sysctl.conf"？ y
[root@localhost ~]# cat /etc/sysctl.conf
# System default settings live in /usr/lib/sysctl.d/00-system.conf.
# To override those settings, enter new settings here, or in an /etc/sysctl.d/<name>.conf file
#
# For more information, see sysctl.conf(5) and sysctl.d(5).
vm.max_map_count=262144
[root@localhost ~]# sysctl -p
vm.max_map_count = 262144

