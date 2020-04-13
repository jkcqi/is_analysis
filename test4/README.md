# 实验4 图书管理系统顺序图绘制

学号|班级|姓名
:-------:|:-------:|:-------:|
201710414226|2017软件工程2班|张开轩|

### 1.借书用例
####1.1 源码
```puml
@startuml
actor 管理员
participant "借书界面" as A
participant "操作验证" as B
participant "检查用户" as C
database 数据库 as D
participant "返回信息" as E
activate A
管理员 -> A :1.登录
管理员 -> A :2.检查借书卡
管理员 -> A :3.显示用户信息
A -> B :4.借书
activate C
B -> C :5.检查用户
C -> D :6.有权限借书
C -[#0000FF]> B :无权限借书
B -[#0000FF]> A :借书失败
activate D
D -> E :7.数据库操作完成
activate E
E -> A :借书成功
@enduml
```

####1.2 用例图

![](./img/借书.png)

###2.还书用例
####2.1 源码
```puml
@startuml
actor 读者
actor 管理员
participant "还书界面" as A
participant "操作验证" as B
participant "还书扫描" as C
participant "确认操作" as D
database 数据库 as E
participant "返回信息" as F
读者 -> 管理员 :1.图书交付
activate A
管理员 -> A :2.登录
A -> B:3.还书操作
activate C
B -> C :4.扫描数据条形码
C -> D :5.确认还书
activate D
D -> E :6.还书正确
activate E
E -> F :7.数据库更新
F -> A :8.返回还书成功
@enduml
```

####2.2 用例图
![](./img/还书.png)

###3.查询用例
####3.1 源码
```puml
@startuml
autonumber
actor 访客

opt
    读者 -> 管理系统:登陆
end


访客 -> 馆藏资源品种:选择资源品种
访客 -> 资源项: 输入资源名称、出版社等
访客 -> 资源信息: 浏览相关信息（馆藏数量、可借数量等）
@enduml
```

####3.2 用例图
![](./img/查询.png)

###4.预定用例
####4.1 源码
```puml
@startuml
autonumber
actor 图书管理员

读者 -> 资源项:读取资源信息
资源项 -> 馆藏资源品种: 取资源的品种
loop
    读者 -> 预约记录:新增预约
    图书管理员->读者:取预约者信息
    资源项 -> 馆藏资源品种: 减少可预约数量
    图书管理员->预约记录:登记预约时间
end

@enduml
```

####4.2 用例图
![](./img/预定.png)

###4.总结
通过本次实验， 加深了用puml代码画图的技能力，学到了顺序图，对象交互模式，消息在对象交互中的作用，以及顺序图与活动图（通常叫流程图）的区别。 


