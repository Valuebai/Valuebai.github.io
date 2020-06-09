---
layout:     post					# 使用的布局（不需要改）
title:      python+mysql数据库连接池		# 标题
subtitle:   填写副标题    			#副标题
date:       2020-6-9
author:     Valuebai
header-img: img/back-gunicorn.jpg 	#这篇文章标题背景图片
catalog: true
tags:
    - python
---

- 创建db_pool.py文件
- DBUtils.PooledDB部分加进来
- 方式1或者2虽然选一种

## DBUtils.PooledDB部分

```
from DBUtils.PooledDB import PooledDB
import pymysql

POOL = PooledDB(
    creator=pymysql,  # 使用链接数据库的模块
    maxconnections=6,  # 连接池允许的最大连接数，0和None表示不限制连接数
    mincached=2,  # 初始化时，链接池中至少创建的空闲的链接，0表示不创建
    maxcached=5,  # 链接池中最多闲置的链接，0和None不限制
    maxshared=3,
    # 链接池中最多共享的链接数量，0和None表示全部共享。PS: 无用，因为pymysql和MySQLdb等模块的 threadsafety都为1，所有值无论设置为多少，
    # _maxcached永远为0，所以永远是所有链接都共享。
    blocking=True,  # 连接池中如果没有可用连接后，是否阻塞等待。True，等待；False，不等待然后报错
    maxusage=None,  # 一个链接最多被重复使用的次数，None表示无限制
    setsession=[],  # 开始会话前执行的命令列表。如：["set datestyle to ...", "set time zone ..."]
    ping=0,
    # ping MySQL服务端，检查是否服务可用。# 如：0 = None = never, 1 = default = whenever it is requested,
    # 2 = when a cursor iscreated, 4 = when a query is executed, 7 = always
    host='127.0.0.1',
    port=3306,
    user='root',
    password='123456',
    database='matrix',
    charset='utf8',
    autocommit='True'
)
```

## 实现方式1，实例化调用 MySQLHelper().insert
```
class MySQLHelper(object):
    """
    实现方式1，实例化调用 MySQLHelper().insert
    """

    def __init__(self):
        self.conn = POOL.connection()
        self.cursor = self.conn.cursor(pymysql.cursors.DictCursor)

    def closed_db(self):
        """
        关闭数据库cursor连接
        """
        self.cursor.close()
        self.conn.close()

    def fetch_one(self, sql, args=None):
        """
        查询获取一条数据
        """
        res_one = None
        try:
            self.cursor.execute(sql, args)
            res_one = self.cursor.fetchone()
        except Exception as e:
            print("查询一条数据报错:{}".format(e))
        finally:
            self.closed_db()
        return res_one

    def fetch_all(self, sql, args=None):
        """
        查询获取全部数据
        """
        res_all = None
        try:
            self.cursor.execute(sql, args)
            res_all = self.cursor.fetchall()
        except Exception as e:
            print("MySQL查询多条数据报错:{}".format(e))
        finally:
            self.closed_db()
        return res_all

    def execute(self, sql, args=None):
        """
        执行sql
        """
        try:
            self.cursor.execute(sql, args)
        except BaseException as e:
            print("MySQL执行语句报错:{}".format(e))
        finally:
            self.closed_db()

    def insert(self, sql, args=None):
        """
        插入一条数据
        """
        try:
            self.cursor.execute(sql, args)
            self.conn.commit()
            _id = self.cursor.lastrowid
            # 防止表中没有id返回0
            if _id == 0:
                return True
            return _id
        except Exception as e:
            print("MySQL插入数据报错:{}".format(e))
            self.conn.rollback()
        finally:
            self.closed_db()

    def delete(self, sql, args=None):
        """
        删除数据
        """
        try:
            self.cursor.execute(sql, args)
            self.conn.commit()
        except Exception as e:
            print("MySQL删除数据报错:{}".format(e))
            self.conn.rollback()
        finally:
            self.closed_db()

    def update(self, sql, args=None):
        """
        更新数据
        """
        try:
            self.cursor.execute(sql, args)
            self.conn.commit()
        except Exception as e:
            print("MySQL删除数据报错:{}".format(e))
            self.conn.rollback()
        finally:
            self.closed_db()
```

## 实现方式2，直接当函数调用调用

```

class MySQLHelper(object):
    """
    # 实现方式2，直接MySQLHelper.fetch_one调用
    """

    @staticmethod
    def fetch_one(sql, args=None):
        """
        查询获取一条数据
        """
        res_one = None
        try:
            conn = POOL.connection()
            cursor = conn.cursor(pymysql.cursors.DictCursor)
            cursor.execute(sql, args)
            res_one = cursor.fetchone()
        except Exception as e:
            print("查询一条数据报错:", e)
        finally:
            cursor.close()
            conn.close()
        return res_one

    @staticmethod
    def fetch_all(sql, args=None):
        """
        查询获取全部数据
        """
        res_all = None
        try:
            conn = POOL.connection()
            cursor = conn.cursor(pymysql.cursors.DictCursor)
            cursor.execute(sql, args)
            res_all = cursor.fetchall()
        except Exception as e:
            print("MySQL查询多条数据报错:", e)
        finally:
            cursor.close()
            conn.close()
        return res_all

    def execute(self, sql, args):
        """
        执行传入的sql
        """
        try:
            conn = POOL.connection()
            cursor = conn.cursor(pymysql.cursors.DictCursor)
            cursor.execute(sql, args)
        except BaseException as e:
            print("MySQL执行语句报错:", e)
        finally:
            cursor.close()
            conn.close()
```



【环境】win10_x64 + python3.6.5


【Me】https://github.com/Valuebai/


【参考】
1、出处：地址