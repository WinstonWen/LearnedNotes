##  python笔记
### pip
```
使用清华源加速
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple name
```

### 多进程
	from multiprocessing import Pool
	
	def run(id):
		pass
	
	if __name__=="__main__":
		pool = Pool(processes = 4)
		for id in id_list:
	    	pool.apply_async(run, args=(id, ))
		pool.close()
		pool.join()
### 日期
	指定日期：
	yesterday = datetime.date.today() + datetime.timedelta(-2)          
	yesterday = yesterday.strftime("%Y%m%d")
	输出样式：20191111
	字符串转化为日期
	20191208025959 -> 2019-12-08 
	获取起止日期间的列表：
	import datetime
	start='2016-06-01'
	end='2017-01-01'
	 
	datestart=datetime.datetime.strptime(start,'%Y-%m-%d')
	dateend=datetime.datetime.strptime(end,'%Y-%m-%d')
	 
	while datestart<dateend:
		datestart+=datetime.timedelta(days=1)
		print datestart.strftime('%Y-%m-%d')

### MySQL操作
	connection = pymysql.connect(host='localhost',
	                         port=3306,
	                         user='root',
	                         password='root',
	                         db='demo',
	                         charset='utf8')
	cursor = connection.cursor()
	# 执行语句
	effect_row = cursor.execute(sql)
	# 获取单条数据
	cursor.fetchone()
	
	# 获取前N条数据
	cursor.fetchmany(3)
	
	# 获取所有数据
	cursor.fetchall()
	# 开始事务
	connection.begin()
	# 提交修改
	connection.commit()
	# 错误回滚
	connection.rollback()