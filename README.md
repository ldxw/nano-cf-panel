# nano-panel

## 简介

​        基于django的一个简易并持续开发中的CloudFlare API面板(本面板需要配合Partner key使用，即将集成账号直接登陆方式)，目前实现了部分免费的API功能包括部分统计功能，持续集成中.....

​        面板有两种语言选择，中文和英文，请在登陆页面在左上角浮标上提前设置，cookies会记录这一设置，直至过期和登出。注意：此面板只是短暂记录你的账号信息（邮箱，API key）用于API 的调用，同cookies生存时间相同。

​        由于作者的时间和前端知识有限，前端会可能有点简陋。但更欢迎指出更多的bug和需求，作者一心向学

demo（一个长期存在的展示）： [cf.github.ci](http://cf.github.ci )
## 必要环境

为了方便安装可以使用pip

simplejson
uwsgi
CloudFlare
django-cors-headers

## 如何使用

### 一、Docker

正在研究中...........

```
examples
```

### 二、uwsgi+django

以ubuntu为示例：

安装python3

```
sudo apt install python3
```

为了配置环境方便，安装pip3

```
apt install python3-pip
```
依此安装必要环境

```
pip3 install -r requestment.txt
```
进入项目根目录，目录结构如下：
```
│  .gitattributes
│  LICENSE
│  list.txt
│  manage.py
│  README.md
│  
├─.idea
│  │
│  │  
│  └─codeStyles
│          
├─domain_manage
│  │
│  ├─tamplatetages
│  │      
│  └─__pycache__
│          
├─mysite
│  │  
│  └─__pycache__
│          
├─static
│  │      
│  ├─fonts
│  ├─img
│  │      
│  ├─jquery
│  │      
│  ├─js
│  │              
│  └─webfonts
│          
└─templates
```

配置panel.ini文件（简单示例）：

```
[uwsgi]
http = 0.0.0.0:80 #端口
chdir = PATH/nano-cf-panel #项目根目录
wsgi-file=mysite/wsgi.py  #wsgi配置文件
processes = 1#(后端缓存方式，进程暂时为1进程）
threads = 2
static-map=/static=static  #静态资源路径“static-map=/static”为配置变量
```

设置CloudFlare Partner host_key (/mysite/settings.py):

```
################################################################
#CF_partner api key: host_key='xxxxxxxxxxxxxxxxxxxxxxxxxxxx'
host_key=''
################################################################
```

尝试通过uwsgi启动项目：

```
uwsgi --ini panel.ini
```

使用浏览器访问

### 三、nginx+uwsgi+django前后端分离

正在测试中......


## 捐赠

如果你对本项目有兴趣，并关注后续的更多改进，可以通过以下方式给予更多的动力

<img src="https://i.loli.net/2020/03/03/7I9blUWr6PiXVA8.png" alt="X8QSZ`R4~G{(Y42`M64%FXC.png" style="zoom: 40%;" />

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

