# mysql monitor web
比较全面的MySQL实时监控</br>

# 安装环境：</br>
1.基于python2.7.11开发的</br>
2.安装MySQL数据库</br>
3.如果要监控OS，需要设置ssh免密码登录</br>
4.安装依赖包，执行./install.sh脚本</br>
5.在setting.py设置MySQL_Host相关账户信息</br>
``` python
MySQL_Host = host_info.HoseInfo(host="192.168.11.128", port=3306, user="yangcg", password="yangcaogui", remark="Monitor")
```
6.导入sql/table.sql的SQL脚本</br>
7.添加MySQL数据库用户</br>
``` mysql
insert into host_infos (host, port, user, password, remark) values
("192.168.11.129", 3306, "yangcg", "yangcaogui", "Master"), ("192.168.11.130", 3306, "yangcg", "yangcaogui", "Slave");
```
8.添加系统登录账号</br>
``` mysql
insert into mysql_web.mysql_web_user_info (user_name, user_password)values("yangcaogui", md5("123456"));
```
9.启动python mysql_web.py runserver</br>
10.如果要监控慢查询还要进行几步配置</br>

# 支持的功能:</br>
1.mysql tps qps table_cache handler监控</br>
2.支持对innodb各种status进行监控</br>
3.支持对show engine innodb status分析</br>
4.支持对复制进行监控</br>
5.支持对表空间进行分析</br>
7.支持对os基本监控</br>
8.支持收集慢查询监控</br>
9.支持对thread进行完整分析</br>
10.支持实时的图表显示</br>
11.支持对数据库用户账号的查询</br>
12.支持登录验证，未登录不允许查看其它任何界面</br>
13.支持半同步复制的实时监控</br>

# 完成的脚本:
1.binlog_bk.py - 实现使用mysqlbinlog对binlog日志进行备份</br>
2.binlog_sync.py - 实现对binlog进行分析，可以把数据同步到另一个实例中</br>
3.binlog_util.py - 基于mysql-replication的binlog分析，可生成回滚SQL，实现误操作的闪回</br>
4.binlog_util_new.py - 实现对binlog文件的分析，可生成回滚SQL</br>
5.bk_xtrabackup.py - 实现对xtrabackup的备份封装，可以增量和全备</br>
6.bk_recovery_xtrbackup - 实现对xtrabackup的备份恢复，是基于bk_xtrabackup.py实现的备份恢复，可以远程和本地恢复</br>
7.collect_mysql_status_log.sh - 实现对mysql指定时间段的日志收集，有助于排除问题</br>
8.mysql_auto_install.py - 实现mysql的远程自动安装</br>
9.mysql_replication_repair - 实现对slave出现1032和1062错误的自动恢复功能</br>
10.mysql_slow_log.sh - 基于pt工具的慢查询收集脚本，需要和mysql_web一起使用</br>


# 界面展示:</br>
![image](https://github.com/ycg/mysql_web/blob/master/static/img/111.png)
![image](https://github.com/ycg/mysql_web/blob/master/static/img/112.png)
![image](https://github.com/ycg/mysql_web/blob/master/static/img/113.png)
![image](https://github.com/ycg/mysql_web/blob/master/static/img/114.png)
![image](https://github.com/ycg/mysql_web/blob/master/static/img/115.png)
![image](https://github.com/ycg/mysql_web/blob/master/static/img/116.png)
![image](https://github.com/ycg/mysql_web/blob/master/static/img/117.png)
![image](https://github.com/ycg/mysql_web/blob/master/static/img/118.png)
![image](https://github.com/ycg/mysql_web/blob/master/static/img/119.png)
![image](https://github.com/ycg/mysql_web/blob/master/static/img/120.png)
![image](https://github.com/ycg/mysql_web/blob/master/static/img/121.png)
![image](https://github.com/ycg/mysql_web/blob/master/static/img/123.png)
![image](https://github.com/ycg/mysql_web/blob/master/static/img/124.png)
