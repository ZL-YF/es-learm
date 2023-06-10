# ElasticSearch客户端操作

上述部分为理论部分，实际开发中，主要有三种方式可以作为es服务的客户端：

- 使用elasticsearch-head插件
- 使用elasticsearch提供的Restful接口直接访问
- 使用elasticsearch提供的API进行访问

## RESTful风格的介绍

### 介绍

-  RESTful是一种架构的规范与约束、原则，符合这种规范的架构就是RESTful架构
- 先看REST是什么意思，英文Representational state transfer表述性状态转移，其实就是对资源的标书性状态转移，即通过HTTP动词来实现资源的状态扭转
- 资源是REST系统的核心概念。所有的设计都是以资源为中心
- elasticsearch使用RESTful风格api来设计的

### 方法

| action | 描述                     |
| ------ | ------------------------ |
| HEAD   | 只获取某个资源的头部信息 |
| GET    | 获取资源                 |
| POST   | 创建或更新资源           |
| PUT    | 创建或更新资源           |
| DELETE | 删除资源                 |

```
GET /user:列出所有的⽤户
POST /user:新建⼀个⽤户
PUT /user:更新某个指定⽤户的信息
DELETE /user/ID:删除指定⽤户
```

我们需要使用http请求，介绍两款工具：postman和curl工具。

1.**postman**

![image-20230610155918098](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230610155918098.png)



2.**curl工具**

获取elasticcsearch状态

```
curl -X GET "http://localhost:9200"
```

新建一个文档

```
curl -X PUT "localhost:9200/xdclass/_doc/1" -H 'Content-Type:
application/json' -d' {
"user" : "louis",
"message" : "louis is good"
}
```

删除一个文档

```
curl -X DELETE "localhost:9200/xdclass/_doc/1"
```