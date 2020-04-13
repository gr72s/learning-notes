核心配置文件: superset/config.py
1.  数据库配置文件：`SQLALCHEMY_DATABASE_URI = 'postgresql://root:password@localhost/myapp'`
2.  启用swagger：`FAB_API_SWAGGER_UI = True`。默认路径为：/swaggerview/v1
3.  Druid查询时区：`DRUID_TZ = tz.gettz('Asia/Shanghai')`
4.  数据压缩：`ENABLE_FLASK_COMPRESS = True`