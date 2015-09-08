
# MODERN APPS AND MICROSERVICES

## INTRODUCTION

Bob Familiar, Practice Director, Cloud and Services at BlueMetal Architects, Director, Technology Evangelism
Microsoft, Architect Evangelist, Principal Consultant

### 作者简介

Bob Familiar，在咨询公司 BlueMetal Architects 担任实施总监，负责云服务。之前他是微软的明星布道师，在云计算领域有着丰富经验。他毕业于美国东北大学。

Bob Familiar is the Practice Director for the Cloud & Services team at BlueMetal. The Cloud & Services team are practitioners of Lean Engineering, a high velocity product development process that applies Lean methodology, service oriented patterns and practices and cloud platform capabilities for the design and development of modern applications for the enterprise.

Bob Familiar has been in the software industry for 29 years having worked for both ISVs such as Dunn & Bradstreet Software and ON Technology and for Microsoft as a Principal Consultant, Architect Evangelist and Director of Technology Evangelism in the Northeast. Bob holds a Masters in Computer Science from Northeastern and a patent for Object Relational Database and Distributed Computing.

原文链接：http://theundocumentedapi.com/2015/01/05/modern-apps-and-microservices/

---

This post is part one of a two part series that delves into an emerging approach to modern application architecture called Microservices where  applications are composed of autonomous, independently deployed, scaled, and managed services. This approach to service architecture along with the benefits of cloud platforms provides the scalable, resilient, cross platform foundation necessary for Modern Applications. In part one I will provide an overview of Microservices along with the benefits, a logical architecture and deployment scenarios. In part two of the series I will detail the design and implementation of RefM, a Microservice that provides application reference data.

微服务是现代应用架构的新兴方法。应用由自动化的、可独立部署、扩展和管理的服务组成。这一服务架构方式与云平台一起，提供了"现代应用"所必需的可扩展、弹性、跨平台等基础。本文对微服务进行了综述，分析其优点、逻辑架构和部署脚本。


The software development landscape has changed dramatically over the past decade. Disruptive technologies and design approaches have introduced entirely new types of applications and methods for building them. As Mikhail Shir of BlueMetal writes ‘…The Modern Application is user centric. It enables users to interact with information and people anywhere on any device. It scales resiliently and adapts to its environment. It is designed, architected, and developed using modern frameworks, patterns and methodologies. It is beautiful in its user experience as well as its technical implementation…’ In conjunction with these new user experiences is the need to connect to and interact with a variety of online services that provide information and transactions in a scalable, resilient and cross platform way.

在过去的十年里，软件部署的图景已经发生了翻天覆地的变化。颠覆性技术和设计方案采用了全新的应用类型及相应的构建方法。正如 BlueMetal 高级架构师 Mikhail Shir [所写](http://blog.bluemetal.com/?p=8921)：

> 现代应用以用户为中心，让用户与信息和人交换，不论身处何地，使用何种设备。它弹性扩展，自适应环境。它使用现代框架、模型和方法论进行设计、架构和开发。它在用户体验和技术实施方面，同样优雅。

要获得这样的体验，就需要与各种各样的线上服务连接并交互。这些线上服务能够以可扩展、弹性和跨平台的方式提供信息并执行。


The concept of distributed services is not new. Since the early days of object oriented programming, the idea that one could provide ‘objects’ in a distributed network using RPC mechanisms and message queues along with location transparency has been the holy grail of software engineering. CORBA and DCOM were early attempts to provide a language and OS agnostic approach to distributed computing but not without the heavy burden of complexity.

分布式服务并非新生事物。在“面向对象的编程”的早期，人们希望能使用 RPC 机制、消息队列以及位置透明的方式在分布式网络中提供“对象”。这一想法早已成为软件工程的圣杯。诸如 [CORBA](http://en.wikipedia.org/wiki/Common_Object_Request_Broker_Architecture) 和 [DCOM](http://en.wikipedia.org/wiki/Distributed_Component_Object_Model) 这样的早期尝试，提供了一种语言和操作系统的不可知论范型来进行分布式计算，但是在复杂性上饱受其苦。

The Internet revolution brought about the evolution, and in many ways the simplification, of distributed computing with the introduction of Web Service Protocols such as SOAP and REST. There has been much back and forth amongst the proponents of Service Oriented Architecture on which protocol should rule the day. Without rehashing those battles, suffice it to say that REST has become the primary choice today for defining API’s to cloud hosted services. The key to applying REST is to understand that its CRUD style of API design is not focused on the underlying physical store, i.e. the database, but on the resources that are being accessed. As such, it is a good choice for API design and keeps the overall approach simple and straightforward.

互联网革命带来了分布式计算的进化，引入了 [SOAP](http://en.wikipedia.org/wiki/Distributed_Component_Object_Model) 、 [REST](http://en.wikipedia.org/wiki/Representational_state_transfer) 这样的 [网络服务协议](http://en.wikipedia.org/wiki/List_of_web_service_protocols) 。即便是 [面向服务的架构](http://en.wikipedia.org/wiki/Service-oriented_architecture) 的支持者，对于“当今哪种协议占主导”，也有反复争论。抛开这些争论，对于云托管服务， REST 已成为定义 API 的首选。应用 REST 的关键在于，理解 API 设计的 CRUD 类型关注正在访问的资源，而非基础的物理存储（譬如数据库）。因此，对于 API 设计来说，自然是个好选择，也能让整个方法保持简单和直接。

Another important factor that is impacting how we think about distributed computing today is the emergence of commercial cloud platforms such as Amazon’s AWS and Microsoft’s Azure. These platforms provide pay-as-you-go access to compute and storage as well as easy access to a suite of common application services such as SQL and No-SQL databases, in-memory cache and performance analytics as well as lend themselves to automating the development, test, staging and production environments providing the foundation for Continuous Delivery. 

[AWS](http://aws.amazon.com/) 和 [Azure](http://azure.net/) 等商用云平台的兴起，是引发我们对分布式计算进行思考的另一因素。这些平台提供按需付费的计算和存储服务，也提供常用的应用服务套件，包括 SQL 和 No-SQL 数据库、内存缓存、性能分析等，实现部署、测试、staging 和生产环境的自动化，为 [持续交付](http://en.wikipedia.org/wiki/Continuous_delivery) 奠定基础。

themselves to automating the development, test, staging and production environments providing the foundation for Continuous Delivery. 



## EVOLUTION OF METHODOLOGY, PROCESS AND ARCHITECTURE

## 方法论、进程和架构的进化

The early days of PC development leveraged techniques that came from the mainframe world and used a Waterfall methodology to deliver desktop and client/server applications. This process was gated in that a project phase could not start until the previous phase had completed. This approach resulted in long development cycles and if a project was going poorly, as many did, the dreaded death march to release. 


早期个人电脑部署促进了起源于大型机时代的部署技术的发展，使用瀑布模型来交付桌面和客户端/服务器应用。这种方法类似给项目装大门，除非上一阶段完成，否则无法开始新阶段，这也导致了漫长的部署周期。一旦项目进展不顺利，那就会面临可怕的发布压力。

![](http://bobfamiliar.azurewebsites.net/wp-content/uploads/2015/01/clip_image002_thumb.jpg)

As the industry moved to web development, the methodology and process evolved to Agile/Scrum which is a much healthier approach to team structure and project management. This method of developing software has worked very well for the past several years. As the industry moves to the cloud, Agile/Scum is being leveraged as part of a high velocity, continuous product development approach called Lean Engineering.

随着业界使用网页部署，方法论和进程进化到了Agile/Scrum，使得团队结构和项目管理更健全。在过去几年里，这种方法论运行良好。等业界开始迁移到云上， Aglile/Scum 也就进化到高可用性、持续部署，被称为精益工程。


Lean Engineering defines a set of principles that guide the creation and deployment of software products at high velocity with low risk. By leveraging a Lean Engineering approach, the risk of validating new technology, making incremental changes in process, and bringing new products to market can be lowered and a high quality result can be achieved at a faster rate. 

[精益工程](http://theundocumentedapi.com/2014/11/11/lean-engineering-lean-methodology-applied-to-enterprise-it/)（ Lean Engineering ）明确了一系列原则，指导软件产品进行高可用、低风险的开发和部署。通过推动精益工程法，使得验证新技术、进程中的增量改变、以及将新产品推向市场的成本降低，同时也能更快地获得更高的产品质量。

![](http://bobfamiliar.azurewebsites.net/wp-content/uploads/2015/01/clip_image004_thumb.png)

Lean Engineering leverages the Build-Measure-Learn cycle from Lean Startup and applies these methods to enterprise class product development. The goal is to deliver high quality, valuable software in an efficient, fast, and reliable manner through automation and increasing release cycles. Using commercial cloud platforms, you can create a highly automated on-demand process to iterate quickly through the Build-Measure-Feedback loop, incorporate into their Continuous Integration and Deployment Pipeline processes, and leverage built-in analytics tools.

精益工程从精益创业中提炼了“构建－评估－精益（ Build-Measure-Learn ）”的周期理论，并将其应用于企业级产品开发中。通过自动化和逐步增加的发布周期，以高效、快速、可靠的方式，交付高质量、有价值的软件。通过使用商用云平台，你也能够按需创建高度自动化的进程，借助“构建－评估－反馈”实现快速迭代，并纳入持续集成和部署，促进内置的分析工具发展。 

## DEPENDS ON HOW YOU SLICE IT

## 关键在于如何切割

The interesting artifact of this evolution from desktop to web has been the horizontal slicing of application architecture to take advantage of the advancements in the platform. The first horizontal slice was client/server where the application data was placed in a server hosted database such as SQL Server or Oracle, stored procedures were developed that dealt with database CRUD operations and business logic while the client facing portions of the application were delivered as desktop executables.

从桌面向网页的进化过程中，最让人感兴趣的技能莫过于水平切割应用架构，从而利用平台的优势。首次切割是分离客户端和服务器。应用数据被放在服务器上，托管着 SQL Server 或者 Oracle 数据库，储存着涉及数据库 CRUD 操作和业务逻辑的流程。与此同时，客户端面向应用端口，则以桌面可执行文件的形式呈现。

![](http://bobfamiliar.azurewebsites.net/wp-content/uploads/2015/01/clip_image0027_thumb.jpg)

The next slice came with the advent of web based applications targeting browsers. The code that dynamically generated the web pages, provided business logic, and accessed data was moved to a web server. This middle layer communicated with the database which now resided in a third logical tier. This approach has served the industry well, but as cloud platforms mature, this 3-tier architecture is unable to fully realize the power of these cloud platforms.

第二重切割则伴随着针对浏览器的网页应用的兴起。代码不断生成网页，提供业务逻辑，访问位于网页服务器的数据。这一中间层与位于第三层逻辑层的数据库通信。这一方法在业界运行良好，但是随着云平台的成长，这种三级构架不能完全发挥这些云平台的优势。

Cloud platforms provide the ability to instantiate services on demand and scale them in an elastic manner. When 3-Tier applications are hosted in the cloud, the monolithic nature of the architecture limits the ability to take full advantage of elasticity and the ability to scale the entire app. Our goal is to enable dynamic scaling of individual application components (Microservices). This ability is made possible by vertically slicing the application into a suite of Microservices.

云平台按需提供实例服务，并弹性扩展。当三级架构运行于云端，这种庞大的架构不能完全发挥弹性优势，也不能扩展整个应用。我们的目标是让每个应用组件（微服务）能够弹性扩展。而将整个应用纵向切割为一整套微服务，则使得这一切成为可能。

## MICROSERVICES DEFINED

## 定义微服务

Microservices are autonomous, scalable services that provide easy-to-use API’s for a particular business function. Martin Fowler has written on the topic and defines a Microservice as…

微服务是自动化、可扩展的服务，为特定的业务功能提供易于使用的 API 。 [Martin Fowler](http://martinfowler.com/articles/microservices.html) 曾撰文将微服务定义为：

> …an approach to developing a single application as a suite of small services, each running in its own process and communicating with lightweight mechanisms, often an HTTP resource API. These services are built around business capabilities and independently deployable by fully automated deployment machinery…

> ……把单一应用作为一套微小服务而进行开发的方法，每个服务都运行自己的进程，通过轻量级机制通信，通常是一个 HTTP 资源的 API 。这些服务围绕着业务能力构建，能够通过完全自动化的部署机制独立部署。


Determining what constitutes a Microservice is dependent on the nature of the application but in general terms a Microservice is scoped to a particular business domain such as Customer, Product and Order or cross cutting concerns such as Workflow, Rules and Reference Data. As you begin to adopt a Microservices approach to application architecture across the enterprise, the opportunity for reuse will grow. You will discover that new applications can be composed from mostly existing reusable Microservices.

微服务的构成是由应用的性质决定多。一般而言，微服务被划分为不同领域，比如客户、产品和订单，或者根据关注点不同被划分为工作流、规则和参考数据。一旦在企业应用中采用了微服务架构，那复用的机会就会增加。你会发现新应用可以使用已有的可复用的微服务。

In order for a Microservices architecture to be successful, each Microservice must exhibit a set non-negotiable characteristics:

为了让微服务架构成功，每个微服务都必须具有以下不可转让的特点

|特征|描述|
| ------------ | ------------ |
|Autonomous	|A Microservice is a unit of functionality; it provides an API for a set of capabilities oriented around a business domain or common utility|
| Isolated	|A Microservice is a unit of deployment; it can be modified, tested and deployed as a unit without impacting other areas of a solution|
|Elastic	|A Microservice is stateless; it can be horizontally scaled up and down as needed|
|Resilient	|A Microservice is designed for failure; it is fault tolerant and highly available|
|Responsive|	A Microservice responds to requests in a reasonable amount of time|
|Intelligent|	The intelligence in a system is found in the Microservice endpoints not ‘on the wire’
|Message Oriented	|Microservices rely on HTTP or a lightweight message bus to establish a boundary between components; this ensures loose coupling, isolation, location transparency, and provides the means to delegate errors as messages|
|Programmable	|Microservices provide API’s for access by developers and administrators|
|Composable	| Applications are composed from multiple Microservices|
| Automated	|The lifecycle of a Microservice is managed through automation that includes development, build, test, staging, production and distribution|


|特征|描述|
| ------------ | ------------ |
|自治 |每个微服务是一个功能单元，围绕业务模块和通用功能，为每个功能提供 API 接口|
|隔离|每个微服务是一个部署单元，能够作为单元被修改、测试和部署，而不会对方案的其它部分造成影响|
|弹性|微服务无状态，能够根据需要进行水平扩展或收缩|
|适应性	|微服务能够适应失败、容错和高可用|
|响应|微服务能对一定时间内的请求作出响应|
|智能|能够发现系统中的微服务端点“不在线” |
|面向消息	|微服务通过 HTTP 或者轻量级的信息总线回应，建立各组件之间的界限。这确保了松耦合、隔离、位置透明，提供了处理错误信息的方法|
|可组合| 应用由多个微服务构成|
|自动化|微服务的生命周期使用自动化管理，包括部署、构建、测试、staging、生产和分发。|

## WHAT ARE THE BENEFITS OF A MICROSERVICE ARCHITECTURE?

## 微服务架构的优点

There are many benefits to a Microservice Architecture. These benefits are not only technical in nature, but also improve the team culture. Instead of forming separate teams by job function, it is recommended that you create cross functional teams that combine all roles; design, development, QA, IT, program and product management, stakeholder and so on. These cross functional teams own the Microservice Product from start to finish, from concept to deployment. This approach will increase quality through ownership and create a positive working environment for all involved.

微服务架构具有诸多优点。它们不仅与技术有关，同时也能促进团队文化。不同于按照业务功能划分团队，微服务架构推荐创建跨功能的团队，能够联合所有职责，包括设计、开发、 QA 、 IT 、产品和项目管理等。这些跨功能组建的团队拥有同一个微服务架构的产品，从始至终，从概念图到部署。通过强化所有权，不仅提高了产品质量，也创造了一个士气高涨的工作环境。

The benefits of a Microservice Architecture are:

微服务架构的优点如下表：

|优点|描述|
| ------------ | ------------ |
|Evolutionary	|They can be developed alongside existing monolithic applications providing a bridge to a future state|
|Open|	They provide highly decoupled, language agnostic APIs|
|Tool/Language Agnostic	|They are not bound to a single technology and not a one-size-fits-all approach|
|Deployment Flexibility	|Services are deployed independently|
|Scale Flexibility	|On-demand scaling of services leads to better cost control|
|Reusable	|The can be reused and composed with other services|
|Versioned	| New API’s can be released without impacting clients that are using previous API’s|
|Replaceable|	Services can be rewritten and replaced with minimal downstream impact|
|Owned	|Microservices are owned by one team from development through deployment|



|优点|描述|
| ------------ | ------------ |
|进化|它们能够与当前存在的单一巨型应用并行开发，为未来架起桥梁|
|开放|它们提供高度解耦合的，语言模糊的 API 接口|
|工具/语言模糊|它们不与单一技术绑定，不做万能的均码|
|部署的灵活性|每个微服务都独立部署|
|扩展的灵活性|按需扩展服务带来更好的开销控制|
|复用性|它们能被别的服务复用，或成为其中一部分|
|版本更新	|发布新的 API ，同时不影响使用原有 API 的客户端|
|可替换|微服务能够被重写或替代，而影响极小	|
|所有权|从开发到部署，微服务归同一团队所有|

## MICROSERVICE LOGICAL ARCHITECTURE

## 微服务的逻辑架构

While the term ‘micro’ appears in the name of this architecture pattern, a Microservice is not necessarily small. The term micro indicates that the surface area of capability is scoped, bounded to an area of a business domain. Another way to say this is that a Microservice does one thing and it does it well.

尽管微服务架构中包含了“微”字，但是并不意味着小。“微”表示性能的作用范围，与某一业务范围绑定。换言之，微服务只做一件事并将其做好。

The scope of a Microservice goes beyond the public facing API’s. A Microservice serves two masters; it provides a public façade that client applications and other services leverage to access its publically accessible functions, and a private façade that provides the development and administration team configuration, monitoring, batch processing, analytics, and other private concerns. The two facades share the Modes, a common code Framework for accessing stores, invoking REST API’s and serializing objects, and a common in-memory and physical repository. Taken all together these two facades and the common components represent the entire scope of the Microservice domain.

微服务的范围超出了公用 API 。微服务要服务两个层面：公有服务层和私有服务层。微服务为公有服务提供客户端应用和其他应用，进而访问可公开访问的功能；对于私有服务，则提供部署和系统管理员配置、监控、批处理、分析其它私有功能。这两个方面共享同一 Mode ，包括通用的代码框架和通用内存和物理仓库。借助代码框架能够访问存储，唤醒 REST API ，以及串行目标。把这两个层面和所有通用组件拼接起来，就能呈现一个完整的微服务画面。

![](http://bobfamiliar.azurewebsites.net/wp-content/uploads/2015/01/clip_image004_thumb.jpg)

| Component	| Access	| Description |
| ------------ | ------------ | ------------ |
| User Experience |	Public	| Any Client that leverages the public SDK |
|	| Private	| An Administrators Console that leverages both the public and private SDK to provide a user experience for managing the Microservice | 
|SDK	| Public|	SDK used by client applications and services to access the Microservice capabilities|
|	|Private |	SDK used by the Microservices development team and administrators to manage and monitor the Microservice|
|Models	|On-the-Wire|	The message formats that are emitted to and received from client of the Microservice|
|	| In-the-Store	|The message formats as they reside in storage. These formats may be different than what is communicated on the wire and therefore transformation may be applied|
|API	| Public	| The ‘public’ programmable interface provided over a lightweight communication protocol such as HTTP used by client services and applications|
|	| Private	| The ‘private’ programmable interface provided over a lightweight communication protocol such as HTTP used by Microservices development team and administrators|
| Logic |	PublicPrivate|	Rules, validations, calculations that comprise the business logic for a particular Microservice|
|Frameworks	|Common	|Common Frameworks for communication, caching, messaging, storage, logging, security, and other cross cutting concerns|
|Store	|Persistence|	Relational, Non-Relational, In-Memory and/or Message Q stores, used for model persistence and loosely coupled messaging|
|Automation	|Deployment	|Leveraging process and tools for continuous deployment across development, build, test, tagging and production to provide high-velocity, high-quality release cycles|


| 组件	| 权限	| 描述 |
| ------------ | ------------ | ------------ |
| 用户体验 |	公开| 任何影响公有 SDK 的客户端 |
|	| 私有	|管理员控制台，同时影响公有和私有 SDK ，提供管理微服务的用户体验 | 
|SDK	| 公开|	SDK 被用于客户端应用和服务，获得微服务性能|
|	|私有|	微服务开发团队和管理员使用 SDK 管理和监控微服务|
|模型|线上|微服务客户端上发送和接收的信息格式|
|	| 存储器	|存储信息的格式。这些格式与通信时的不同，因而需要转换|
|API| 公开| “公共”的可编程界面，提供了 HPPT 这样但轻量级的通信协议，应用于客户端服务和应用|
|	| 私有|“私有”的可编程界面，为微服务开发团队和管理员提供 HPPT 这样的轻量级通信协议 |
| 逻辑 |	PublicPrivate|构成特定的微服务业务逻辑所需的规则、验证、计算等|
|框架|通用|通信、缓存、消息、存储、日志、安全和其它横切关注点的通用框架|
|存储|留存|相关、非相关、In-Memory 和/或 Message Q 存储，用于模型的持续性和松耦合通知|
|Automation自动化|Deployment部署	|影响持续部署中的进程和工具，持续部署贯穿开发、构建、测试、打标签和生产，提供高可用、高质量的发布周期|

## MICROSERVICE DEPLOYMENT SCENARIOS

A benefit of Microservices is that they provide the flexibility to scale individual components based on performance profiles exhibited at runtime. They can also be composed to deliver just the right set of functionality for new user experiences that target current and emerging form factors. 

clip_image006 

Today’s cloud platforms such as AWS and Azure provide Virtual Machine based mechanisms for deploying Microservices. Each cloud platform vendor will provide various tools; API’s and patterns for defining virtual machine configurations. For sake of this discussion, we will use Microsoft Azure as the cloud platform and assume our Microservices were developed using ASP.NET Web API. The Microservices will be deployed in the same manner one would deploy a web site.

Azure provides the ability to define Resource Groups and deploy web sites (Microservices) into these Resource Groups. All the web sites in a resource group will share the resources assigned that Resource Group. Azure then lets you define Web Hosting Plans. Each Web Hosting Plan is associated with a Resource Group and defines the size of the virtual machines, the metric that will be used for elasticity, the number of instances currently running, and the maximum number to scale to when the scale metric has triggered the need for a new instance.

clip_image008

Using this model, we could choose to configure our Microservices as follows:

- Reference Data and Customer Microservices deployed to the Resource Group A using Web Hosting Plan A therefore running on the same VM instance
- Order Microservice are deployed to Resource Group B using Web Hosting Plan B which defines a minimum 4 VM farm

clip_image010

Another way we could go is to deploy each Microservice independently. Each Microservice is deployed into its own Resource Group each with their own Web Hosting Plan, sized appropriately for the amount of load expected and scaled according to the metric defined in the Web Hosting Plan.

clip_image012

The key point here is that cloud platforms provide great flexibility in how each Microservice is deployed and scaled. Designing load testing scenarios that emulate real world usage of the overall system will inform your initial deployment configurations. Leveraging real-time monitoring and analytics over time will provide the necessary data to tweak the deployment configurations for optimal efficiency.

There is an emerging product called Docker that provides an even more granular approach to deploying Microservices. Docker is an open-source project that provides the ability to easily create lightweight, portable, self-sufficient containers for any application. The same container that a developer builds and tests on a laptop can run at scale, in production, on VMs, bare metal, OpenStack clusters and public clouds. This feature is available today in Azure and AWS with support for Linux based applications. Windows Container support is coming in early 2015. Using a container approach, one could deploy multiple Microservice containers to individual VM’s to maximize utilization of each VM, helping to provide very flexible cost containment.

clip_image014

## SUMMARY

Modern Applications are designed, architected, and developed using modern frameworks, patterns, practices and methodologies. They are beautiful in their user experience, are built on a foundation of scalable, resilient services. Microservice Architecture is an approach to delivering highly scalable, cross platform RESTful API’s that can be developed, deployed and scaled independently of one another to provide the Modern Application product team the greatest amount of flexibility and control.

BlueMetal recommends Lean Engineering, Responsive Design, and Microservice Architecture along with Cloud Platforms to deliver Modern Applications at high velocity. If you are interested in learning more about Microservices and how they can be applied to your next development project, please contact me at bobf@bluemetal.com or reach out to the Sales Directors in your area.
