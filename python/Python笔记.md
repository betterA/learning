### 什么是WSGI

1.PEP3333

2.web框架交互规范

3.解决web server CGI FastCGI 等乱象

### Django VS Flask VS Tornado

Django: 大而全，有ORM admin 等插件，有统一的代码逻辑和目录层级

Flask:灵活 三方插件也比较多 也有ORM admin 之类的东西，但是没有统一项目的模板（可以使用flask-cookiecutter进行生成）

Tornado ：异步

### 什么是MVC

出现意义：解耦

Model：模型 负责对象和数据库的交互ORM

View: 负责与用户的交互展示

Controller: 接收请求参数调用模型和视图完成请求

ORM 代码少效率高，更安全



### WEB 安全

1. **SQL 注入**  没有对输入进行过滤，直接动态拼接SQL

   防范： 永远不要相信用户的任何输入

   对输入参数做好检查；过滤和转义特殊字符

   不要直接拼接SQL,使用ORM 可以降低SQL 注入的风险

   数据库层：做好权限管理配置；不要明文存储敏感信息  

2.  **XSS 跨站脚本攻击**     插入未经转换的js 代码，其他用户也会访问他  比如**评论**

   黑客获取cookie, 盗取敏感数据

3. **CSRF 跨站请求伪造**

   首先用户C**浏览并登录了受信任站点A**；

   登录信息验证通过以后，站点A会在返回给浏览器的信息中带上已登录的**cookie**，cookie信息会在浏览器端保存一定时间（根据服务端设置而定）；

   完成这一步以后，用户在没有登出（清除站点A的cookie）站点A的情况下，访问**恶意站点B**；

   这时恶意站点 **B的某个页面向站点A发起请求，而这个请求会带上浏览器端所保存的站点A的cookie**；

   站点A根据请求所带的cookie，判断此请求为用户C所发送的。

   危害： 数据泄露  或者数据安全

   **防御**：

   1. 尽量使用POST 限制使用GET, GET 接口可以构造img 标签等
   2. 将cookie设置为HttpOnly 
   3. 添加token
   4. 通过Referer 识别



### 什么是前后端分离？有什么优点？

后端只负责提供数据接口，不再渲染模板，前端获取数据并呈现

1. 前后端解耦，接口复用（前端和客户端公用接口），减少开发量
2. 前后端同步开发，提升工作效率。
3. 更利于调试mock 、 测试和运维部署



### 什么是RESTful

表现层状态转移

**一种软件架构的风格， 就是用URL定位资源，用HTTP METHOD 描述操作。**

Rosources 资源 

Representation 表现层 

State Transfer 状态转化  使用GET POST PUT DELETE  http 动词来操作资源，实现资源状态的改变