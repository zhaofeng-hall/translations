# The geek shall inherit the earth: The age of developer-defined infrastructure

http://venturebeat.com/2015/04/01/the-geek-shall-inherit-the-earth-the-age-of-developer-defined-infrastructure/

# 极客接管世界：DDI 的时代

If “software is eating the world,” then the meal will be prepared by developers.

如果说“软件正在吞食世界”，那奉上这场盛宴的，必然是开发者无疑。

Over the past several years, there have been articles about the primacy of software engineers. This reality is supported by the fact that technical majors are making more money coming out of college than their classmates and the average salary for a developer has risen dramatically over the past few years. In fact, developers will soon become some of the highest paid employees in a company — and I mean every company, not just in Silicon Valley.

在过去数年中，关于软件工程师地位的文章层出不穷。这些文章列举了以下事实：技术专业的毕业生比他们的同学赚得更多，开发者的平均薪水大幅增长。在我看来，开发者将成为各种公司薪酬最高的人，而不仅仅局限在硅谷的公司。

We are entering the age of developer-defined infrastructure (DDI). Historically, developers had limited say in many application technologies. During the 1990s, we effectively lived in a bilateral world of Microsoft .NET vs Java, and we pretty much defaulted to using Oracle as a database. In the past several years, we have seen a renaissance in developer technologies and application infrastructure from a proliferation of languages and frameworks (Go, Scala, Python, Swift) as well as data infrastructure (Hadoop, Mongo, Kafka, etc.). With the power of open source, developers can now choose the language, runtime, and database that make sense. However, developers are not only making application infrastructure decisions. They are also making underlying cloud infrastructure decisions. They are determining not only where will their applications run (private or public clouds) but how storage, networking, compute, and security should be managed. This is the age of DDI, and the IT landscape will never look the same again.

我们正在进入 DDI （ developer-defined infrastructure ，开发者定义软件基础设施） 的时代。历史上，开发者在许多应用技术中鲜有发声。在 20 世纪 90 年代，我们经历 Microsoft .NET vs Java 的战争，不情愿地使用 Oracle 作为数据库。在过去几年间，我们看到了开发技术和应用基础设施的复兴，语言和框架（如 Go 、 Scala 、Python 、 Swift ）和数据技术设施（如 Hadoop 、 Mongo 、 Kafka 等）层出不限。由于开源的力量，开发者们现在可以选择语言、运行时和数据库。然而，开发者们不仅仅决定软件的基础设施，他们还需要决定更云基础设施。他们不仅决定自己的应用跑在哪里（私有云还是公有云），还要决定如何存储、网络、计算和管理。这是 DDI 的时代，这样的 IT 盛景也不会再现。

The roles of developer and system administrators were separate and defined: developers made decisions about developer tools like source code management and issue tracking (Git, Jira), and system administrators (server admins, storage admins, network admins) managed production and infrastructure standards. However, with the move to clouds like Amazon Web Services (AWS) have given developers choice in what infrastructure services they can use.

开发者和系统管理员的角色被分别定义：开发者对于开发工具做决定，而系统管理员则管理铲平和基础设施标准。开发工具包括源码管理和问题追踪，如 Git 和 Jira ；系统管理包括服务器管理、存储管理、网络管理等。然而，随着向 AWS 等云服务迁移，开发者们有权选择使用何种软件基础设施。

How did we get here? Let’s take a quick look at the evolution of the data center.

这一切又是从何而来？让我们简要回顾一下数据中心的进化：

## The three ages of the data center

### Physical-defined infrastructure (~1985 to 1999)

### 物理机定义基础设施

During the rise of the client/server era, corporations were moving from mainframes to mini-computers to a powerful server computers coupled with personal computers. This was the age when hardware design and hardware vendors drove IT strategy. Engineers debated CPU architectures (RISC vs CISC), Power vs X86 vs SPARC and the strategic vendors of this generation were companies like Sun Microsystems, IBM, and HP.

在客户端/服务器兴起的年代，公司将他们的中央处理器转移到小型计算机，继而转变为一台服务器搭配数台个人电脑。这个时代硬件为王，硬件厂商驱动 TI 战略。工程师们为 CPU 架构（ RISC vs CISC ）、Power vs X86 vs SPARC 争论不休，而 Sun Microsystems 、 IBM 和 HP 则成为这个年代的战略厂商。

### Software-defined infrastructure (~2000 to 2014)

### 软件定义基础设施

In physical defined infrastructure, software was usually paired with hardware. In the early 2000s, we saw the Intel X86 architecture win out in the CPU layer, allowing servers and systems to standardize. Once you have hardware standards, the software ecosystem grew up around these servers started to decouple the logical from the physical. Operating systems like Windows and Linux became the layer to which software interacted with hardware. Eventually, VMware pioneered the idea of software virtualization, which enabled IT administrators to render virtual computers, disks, and networks all in software. Riding the power of Moore’s Law, VMware turned physical defined infrastructure into software-defined infrastructure. You can trace the evolution from physical to virtual just by looking at how profit margins flowed from system vendors like Sun to the winers of the software-defined infrastructure age like VMware, Microsoft, Red Hat, and Intel as the de facto CPU standard. VMware moved from virtualized compute to storage (vSAN) and then networking (NSX).

在物理机定义基础设施的时代，软件需要迎合硬件。在 21 世纪初，我们看到 Inter X86 在 CPU 层面的全面胜利，带来了服务器和系统的标准化。一旦硬件标准化，软件生态系统就围绕着这些服务器发展，断开了与物理机的逻辑耦合。操作系统（ Windows 和 Linux ）成为软件与硬件的交互层。最终， VMware 提出了软件虚拟化的概念，使得 IT 管理员能够以软件的方式来管理虚拟机、磁盘和网络。基于摩尔定律， VMware 将物理机定义软件基础设施推进到软件定义基础设施。通过一窥利润从系统厂商（譬如 Sun ）流向到软件定义基础设施年代的霸主们（譬如 VMware 、微软、红帽，和 CPU 的标准制订者英特尔），我们也可以回溯从物理机到虚拟化的进化。

If VMware pioneered the idea of software-defined infrastructure, the web-scale giants like Google and Facebook perfected it. Living by the adage “software will eventually work, hardware will eventually fail,” they saw the value of using commodity hardware and software to make unreliable hardware reliable.

如果说 VMare 只是软件定义基础设施概念的先行者，那网络巨头 Google 和 Facebook 则将其完善。他们看到了使用商业硬件和软件的价值，将不稳定的硬件变得可靠稳定，鲜活地证明了“软件终将胜利，硬件必然失败”的格言。

The impact of this software-defined data center can be seen by the fate of some of the leaders of the physical defined infrastructure age: Dell went private, IBM sold its x86 server line to Lenovo, and HP is undergoing an identity crisis right now.

从物理机定义基础设施年代的霸主们的命运中，我们可以看到软件定义数据中心的概念的影响：戴尔私有化、 IBM 将其 X86 服务器线出售给了联想， HP 正经历着痛苦的身份危机。


### Developer-defined infrastructure (2015 to ????)

### 开发者定义基础设施

Welcome to the age of DDI, where developers are making decisions on how, what, and where their applications should run. DDI is the natural evolution of software defined infrastructure. The power of turning hardware into software is partly the separation of logical from physical into software, but mainly the fact that once you have hardware represented in software, you can treat hardware like any other piece of code. You can move it, you can program it, you can write programs for it. For example, on AWS, everything has an application programming interface (API) and can be programmed: storage, compute, networking, security, etc. Today, developers need to think like IT and operations, and IT administrators must enable developers to make these infrastructure choices and not constrain them. With this rise of devops and cloud, developers are looking for technologies to build, run, and manage their applications that support DDI: If VMware was the platform for the last 15 years, then companies, like Docker, could be the platform for the next 15. In particular, Docker supports:

欢迎来到 DDI 时代！开发者们正在决定他们的应用将如何在哪里运行。 DDI 是软件定义基础设施的自然进化结果。从硬件向软件转变，部分是由于从物理机到软件的逻辑分离，更主要的原因在于，一旦硬件可以通过软件展示，那么你就可以将硬件与其它代码一视同仁。你可以移动或者编码，也可以为它编写程序。例如，AWS 上，存储、计算、网络和安全都有 API 且可被编程。如今，开发者需要像 IT 和运营人员那样思考，而 IT 管理员则要给开发者选择基础设施的权利，并且不给予限制。随着开发运维一体化和云的兴起，开发者们寻求支持 DDI 的技术，去建构、运行和管理他们的应用。如果 VMware 是过去 15 年的平台，那 Docker 这样的公司则是未来 15 年的平台。具体而言，Docker 将支持：


- Programmability and portability: Infrastructure should be treated like any other bit of software. No longer tied to a physical location, Docker containers can easily be moved anywhere, from a laptop in a coffee shop to a cloud. Even more importantly, DDI like Docker can be programmed through its own API.

- 可编程与可移植性：基础设施应当与软件的其它部分一视同仁。 Docker 容器能够轻松迁移，无论是咖啡馆里的笔记本电脑还是云，不受物理位置束缚。更重要的是像 Docker 这样但 DDI 能够通过自带 API 编程。


- Consolidation: This is the attribute of Docker that wins over most of the IT and system admins. Just like virtualization replaced physical infrastructure by turning 10 physical servers into 10 virtualized servers on a single machine, Docker can further increase the consolidation ratio of server workloads while improving speed and performance.

- 一致性：这是 Docker 的贡献，也因此赢得了 IT 和系统管理员。通过把 10 台物理服务器转变为一台机器上的 10 台虚拟服务器，虚拟化取代了物理机基础设施。Docker 大幅提升服务器工作负载的一致性，同时提高速度和性能。


- Move to microservices: Companies, like Twitter, Google, and Facebook have adopted microservices to build their next generation of applications. Microservices are easier to scale, update, and develop by a larger engineering team.

- 迈向微服务：Twitter 、 Google 、 Facebook 这样但公司已经使用微服务来构建他们的下一代应用。工程师团队通过使用微服务，能够轻松实现扩展、更新和开发。



## The geek shall inherit the earth

## 极客接管世界

What are the implications for vendors, developers, and IT professionals in the DDI era? Software vendors that don’t understand or embrace developers will fail to be relevant. Incumbents that sell to IT administrators like virtualization, storage, network, or security admins will need to understand how to sell to developers. IT professionals need to think about how to enable developer choice and not restrict it. Finally, developers need to expand what the definition of an application is. Code isn’t just a program, or an app on a smart phone, code becomes everything from metal to management, to the final pixel.

DDI 时代对于厂商、开发者和 IT 专家意味着什么？不能理解和拥抱开发者的软件厂商将会失败。原本面向 IT 系统管理（如虚拟化、存储、网络、安全管理）的销售代表需要学习如何与开发者打交道。IT 专家们需要思考如何给开发者授权而不是约束。最后，开发者需要扩展应用的定义。代码不仅仅只是一段程序、或者智能手机上的一个应用，代码无处不在，从metal到管理，到成品的每一像素。

Jerry Chen is a partner at Greylock Partners. He sits on the board of Docker. Previously he was vice president of cloud and application services at VMware.

Jerry Chen 是 Greylock Partners 合作人， Docker 董事会成员。他曾在 VMware 担任副总裁，负责云和应用服务。
