# fescar-example（分布式事务中间件Fescar）

**FESCAR: Fast & Easy Commit And Rollback**

`fescar git:https://github.com/alibaba/fescar`

`参考:https://github.com/alibaba/fescar/wiki/Quick-Start`

## 下载fescar-server 运行。
`fescar-server-0.1.1.tar.gz`

## 安装mySql
`mysql官网最新版本:8.0.13`

## DDL
<pre>
CREATE TABLE `undo_log` (
   `id` bigint(20) NOT NULL AUTO_INCREMENT,
   `branch_id` bigint(20) NOT NULL,
   `xid` varchar(100) NOT NULL,
   `rollback_info` longblob NOT NULL,
   `log_status` int(11) NOT NULL,
   `log_created` datetime NOT NULL,
   `log_modified` datetime NOT NULL,
   `ext` varchar(100) DEFAULT NULL,
   PRIMARY KEY (`id`),
   KEY `idx_unionkey` (`xid`,`branch_id`)
 ) ENGINE=InnoDB AUTO_INCREMENT=159 DEFAULT CHARSET=utf8
</pre>

<pre>
DROP TABLE IF EXISTS `storage_tbl`;
  CREATE TABLE `storage_tbl` (
    `id` int(11) NOT NULL AUTO_INCREMENT,
    `commodity_code` varchar(255) DEFAULT NULL,
    `count` int(11) DEFAULT 0,
    PRIMARY KEY (`id`),
    UNIQUE KEY (`commodity_code`)
  ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
  
  
  DROP TABLE IF EXISTS `order_tbl`;
  CREATE TABLE `order_tbl` (
    `id` int(11) NOT NULL AUTO_INCREMENT,
    `user_id` varchar(255) DEFAULT NULL,
    `commodity_code` varchar(255) DEFAULT NULL,
    `count` int(11) DEFAULT 0,
    `money` int(11) DEFAULT 0,
    PRIMARY KEY (`id`)
  ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
  
  
  DROP TABLE IF EXISTS `account_tbl`;
  CREATE TABLE `account_tbl` (
    `id` int(11) NOT NULL AUTO_INCREMENT,
    `user_id` varchar(255) DEFAULT NULL,
    `money` int(11) DEFAULT 0,
    PRIMARY KEY (`id`)
  ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
</pre>

# 注意
`修改classpath下application.conf中的localRgroup.grouplist ip`
