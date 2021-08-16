# ServicePlatForm
Django Rest Framework + Vue 服务报修平台

## 部署

### 下载项目到/user/local/目录下

```shell
cd /usr/local/
git clone http://github.com/fredyuanlu/ServicePlatForm.git
```

### 安装运行环境

```shell
bash /user/local/ITPlatForm/install.sh
```

### 安装运行包

> 如果安装提示报错，可以尝试多次运行

```shell
/usr/python39/bin/python3.9 -m pip install --upgrade pip -i https://pypi.doubanio.com/simple/
```

```shell
/usr/python39/bin/python3.9 -m pip install -r /usr/local/ITPlatForm/requirements.txt -i https://pypi.doubanio.com/simple/
```

### 配置数据库

> 编辑 **/usr/local/ITPlatForm/ITPlatForm/config.ini** 文件，输入数据库的基本信息（数据库需要先创建database）

```shell
vi /usr/local/ITPlatForm/ITPlatForm/config.ini

[mysql]
host = 192.168.0.1
database = DBName
username = DBAdmin
password = DBPwd
port = 3999
```

### 创建数据库

```shell
/usr/python39/bin/python3.9 /usr/local/ITPlatForm/manage.py makemigrations
/usr/python39/bin/python3.9 /usr/local/ITPlatForm/manage.py migrate
```

### 创建初始管理员账号

```shell
/usr/python39/bin/python3.9 /usr/local/ITPlatForm/manage.py createsuperuser

用户名: admin
电子邮件地址: 
Password: 
Password (again): 
```

### 运行项目

> 默认为8080端口，可以自行更改

```shell
/usr/python39/bin/uwsgi --http-socket 0.0.0.0:8080 --chdir /usr/local/ITPlatForm/ --plugin /usr/python39/bin/python3.9 --wsgi-file /usr/local/ITPlatForm/ITPlatForm/wsgi.py --master --static-map /static=/usr/local/ITPlatForm/static/ --static-map /static=/usr/local/ITPlatForm/dist/static/ --processes 8 --threads 8 --static-gzip-dir=/usr/local/ITPlatForm/dist/
```


