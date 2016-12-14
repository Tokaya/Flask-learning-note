# Flask Web开发笔记
需要理解的python概念：包、模块、函数、修饰器、面向对象编程、异常处理、知道如何从栈跟踪中分析问题
Flask主要有两个依赖：
1、路由、调试和web服务器网关接口（Web Server Gateway Interface，WSGI）子系统由Werkzeug提供
2、模版系统由jinja2提供
## 第一章 安装
检查虚拟环境是否安装，配置环境，命令行：
```
                        virtualenv --version
                        git clone https://github.com/miguelgrinberg/flasky.git
                        $ cd flasky
                        $ git checkout 1a
                        $ virtualenv venv
激活虚拟环境             $  venv\Scripts\activate
回到全局 Python 解释器中：$ deactivate
                        $ pip install flask
检查是否正确安装flask    (venv) $ python >>> import flask >>>
```
## 第二章 程序基本机构
路由函数
动态路由
```python
@app.route('/user/<name>')
def user(name):
    return '<h1>Hello, %s!</h1>' % name
    #<name>  其中为动态路由
```
路由使用定义类型：
```python
/user/<int:id>  
```
Flask 支持在路由中使用 int、float 和 path 类型。

2.5.1 程序上下文 **需关注**
2.5.2 请求调度 app.url_map 查看路由映射
2.5.3 请求钩子
```
before_first_request• ：注册一个函数，在处理第一个请求之前运行。
before_request• ：注册一个函数，在每次请求之前运行。
after_request• ：注册一个函数，如果没有未处理的异常抛出，在每次请求之后运行。
teardown_request• ：注册一个函数，即使有未处理的异常抛出，也在每次请求之后。
```
2.5.4 响应 **之后再看**
2.6 Flask-Script(manager)

## 第三章 Jinja2模板
3.1.1 render_template(第一个参数为模版的文件名，第二个为关键字参数)
3.1.2 Jinja2 能识别所有类型的变量，甚至是一些复杂的类型，例如列表、字典和对象。在模板 中使用变量的一些示例如下：
```HTML
<p>A value from a dictionary: {{ mydict['key'] }}.</p>
<p>A value from a list: {{ mylist[3] }}.</p>
<p>A value from a list, with a variable index: {{ mylist[myintvar] }}.</p>
<p>A value from an object's method: {{ myobj.somemethod() }}.</p>
```
```python
Jinja2过滤器：
    safe 渲染值时不转义
    capitalize 把值的首字母转换成大写，其他字母转换成小写
    lower 把值转换成小写形式
    upper 把值转换成大写形式
    title 把值中每个单词的首字母都转换成大写
    trim 把值的首尾空格去掉
    striptags 渲染之前把值中所有的
    HTML 标签都删掉
    完整过滤器列表 http://jinja.pocoo.org/docs/templates/#builtin-filters
```
3.1.3 控制结构
* base模版

3.2 Flask-Bootstrap **可再阅读**
3.3 错误页面 404/500
