# easy-cloud简称EasyCloud
## 前言
### 宗旨：EasyCloud,EasyCode

###    说明

- 享受各种开源组件带来的便利和惠泽。怀着无比感恩之心为开源尽一份微薄之力。
- dqEasyCloud以spring-boot和spring-cloud为基础，同时定义一套微服务的相关规范，尽可能的降低企业维护成本。
- 如您觉得该项目对您有用，欢迎点击右上方的Star按钮，给予支持！！欢迎大家一起参与开发
- 由于我们经验见识有限，尽管殚精竭虑依旧有很多不足之处，非常期待接受您的意见和建议。欢迎大家加入easy-cloud开源项目组。

###     使用申明
- 为方便开发者初步使用、项目提供了可直接运行的资源环境
- 本开源项目所有可运行的资源包括但不限于(数据库资源、缓存资源、消息队列资源等等)，只可以用做测试之用。切勿进行压力测试
- 若要进行压力测试，请替换为自己的数据资源

## 项目基础架构
###  请求流程解析

- 前端请求->dns负载->nginx反向代理集群->zuul网关集群->聚合服务层->原子服务层->数据层访问层。


### 项目架构图

![系统架构图](系统架构设计.png)

###  项目模块解析

- EasyCloud推荐封装自己的工具类，业务逻辑类尽可能降低与第三方接口的依赖，从而方便统一管理及维护。

- EasyCloud相关工具类都以Ec作为前缀开头:目的是为了防止和第三方的工具类同名冲突。

- EasyCloud原子服务层使用了模块化思想进行封装，分为工具模块和业务逻辑模块。

- EasyCloud工具模块：

  ​	提供公共的服务，并且不依赖于任何业务逻辑模块。


- EasyCloud业务逻辑模块：

  1. Controlle层为该原子服务层提供给聚合服务层调用的接口，不编写而任何业务逻辑代码。

  2. 聚合业务逻辑模块：类名以Logic为结尾，将原子逻辑模块进行组装后，暴露接口给Controller调用。

  3. 原子业务逻辑模块(以下简称原子逻辑模块，举例User模块)：

     - service：服务层，类名以Service为结尾(UserService)，处理原子业务逻辑。


     - repository：数据访问层，类名以Repository结尾(UserRepository)，提供访问数据库的相关操作。


     - entity：持久化对象，类名以Entity结尾(UserEntity)，继承DqBaseEntity。不建议在持久化对象进行数据处理，持久化对象不应该包含任何与数据库无关的属性和方法。


     - vo：视图对象，类名以VO结尾(UserVO)，用作对外的vo对象。也称作视图对象。可以通过继承持久化对象拥有持久化对象的相关属性。


     - dto：数据传输对象，类名以DTO结尾(UserDTO)，用作数据传输的对象。


     -  bo：业务逻辑对象，类名以BO结尾(UserVO)，封装相关业务逻辑，保证其对象的高内聚


     - query：查询条件对象，类名以Query结尾(UserQuery)，封装相关查询条件的对象


     - constant：常量类，类名以Constant结尾(UserConstant)。


     - utils：工具类，类名以Utils结尾(UserUtils)。


## 开发步骤
###     集成微服务基本组件


###     项目实战(用户关注电影功能)

## 持续开发中
