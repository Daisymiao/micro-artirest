# micro-artirest
最新版源码+说明+视频例子请于老师处获取

强烈建议使用前先学习

https://www.jhipster.tech

中的内容，非应用功能的问题（例如如何配置各个服务，如何使用不同的部署方式等）在这里都能找到答案


每个文件夹均为一个独立服务

本地运行方法：
1. 数据库：MongoDB3.4及以下版本

2. kafka：2.11-1.0.0版本，于根目录下依次运行
    1. bin/zookeeper-server-start.sh config/zookeeper.properties
    2. bin/kafka-server-start.sh config/server.properties

3. 服务启动：于各服务根目录下运行./mvwn（console请直接运行docker-compose up）

务必按照jhipster-registry -> uaa -> 其它服务的顺序启动



服务与端口对应关系：

gateway :8081

Artifact-model: 8082

Processes: 8083

BusinessRule:8084

Service:8085

ThirdService:8086

jhipster-registry:8761

uaa:9999

console/ELK三件套：5601



所有服务正常启动后（正常启动：terminal中可以看到端口号返回，没有跳出），浏览器访问localhost:8081

默认用户名密码请打听,聪明如你甚至不需要打听


1. 如何创建流程？

导航切换到process model页面，new一个


2. 如何创建服务与业务规则？

导航切换，new一个

在需要应用的流程模型中填写需要使用的service class与br class

在流程模型中不写全写准这两栏内容将无法创建一个你想象中可以正常运转的流程实例

务必注意定义时service class/br class的名字将是流程应用时的唯一筛选条件

即，如果你有X个service的service class都叫a，且流程模型绑定了service class a，那么创建流程实例的时候你将只能从这X个service中X选一

br class同理



3. 如何使用human_task?

url请使用http://localhost:8081/服务名/api/artifact名


4. 如何使用invoke_service/定义自动服务/第三方服务的逻辑？

这个有点复杂

url请使用http://domain:port/随便写什么/服务名Y

这里domain:port只要不是localhost:8081都会被识别为第三方服务

然后请在ThirdService/src/main/java/me/daisyliao/thirdservice/service/ThirdServiceService.java 68行开始的if-else中添加逻辑



5. 如何启动流程实例？

从流程模型的第4栏中new一个，点点玩一下就会了


6. 如何看registry内容？

访问localhost:8761

默认用户名密码请打听,聪明如你甚至不需要打听



7. 如何看ELK三件套监控内容？

访问localhost:5601

然后请随意玩耍

怎么配里面的内容请参考你使用的组件的官方文档



8. 如何scale我的服务？

请参考https://www.jhipster.tech/microservices-in-production/

用docker把服务起起来，照着docker的使用方法用就可以了
