# Django 在21云盒子上快速起步项目

这是一个示例 [Django](https://www.djangoproject.com/) 应用, 目录结构采用了 [cookiecutter-django](https://github.com/pydanny/cookiecutter-django)的配置 和很好和PostgreSQL.

实例应用已经部置在 https://django-starter.21yunbox.com

# 在21云盒子部署上线的的步驟

## 第一步，创建数据库
   1. 在21云盒子选择适合你的方案，创建一个数据库
   2. 粘一下 `数据库URL`

## 第二步，创建服务器
   1. 授权GitHub获取你的项目代码库，[tobyglei/django-quick-start](https://github.com/tobyglei/django-quick-start) ，创建一个你的服务器
   2. 填写你的自定义域名和服务类型。域名将在url上体现，服务类型目前21云盒子暂时只支持 `Python 3.7+`
   3. 创建一个 `./build.sh` 脚本，并将你所需要的构建步骤添加到build腳本，同时添加你所需要的资源到你的代码库。以下是一个可供参考的[build.sh](https://github.com/tobyglei/django-quick-start/blob/master/build.sh)
   4. 填写Start Command：`gunicorn config.wsgi:application -w 4`
   5. 添加环境变量
   
| Key 	| Value |
|:--:	|:-:	|
| DATABASE_URL | 从你创建的21云数据库中复制粘贴过來 |
| DJANGO_ALLOWED_HOSTS | `xxx.21yunbox.com`, `xxx` 是你的项目域名 |
| DJANGO_SECRET_KEY | 在terminal生成一组随机字符: `echo $(base64 /dev/urandom \| tr -dc 'A-HJ-NP-Za-km-z2-9' \| head -c32)/` |
| DJANGO_SETTINGS_MODULE | `config.settings.production` |
   6. 启动服务器。

## 第三步，完成上线！
    1. 你的专属url已经生成，点击就可以看到啦！
    2. 如果你的项目更新了代码，点击`部署`即可随时更新同步。
