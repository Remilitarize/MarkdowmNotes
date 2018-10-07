[toc]

## BASIC TERMS AND CONCEPTS

**Information security** is a complex ensemble of techniques, technologies, regulations, and behaviors that collaboratively protect the integrity of and access to computer systems and data.
**信息安全** 是技术、科技、规章和行为的复杂组合，它们联合起来保护计算机系统和数据的完整性和对之的访问。
**IT security measures** aim to defend against threats and interference that arise from both *malicious intent* and *unintentional user error*.
**IT 安全措施** 旨在防御由于 *恶意的企图* 和 *无心的用户错误* 造成的威胁和干扰。

### Confidentiality 保密性

**Confidentiality** is the charactgeristic of something begin made accessible only to **authorized parties**.
**保密性** 是指事物只有 **被授权方** 才能访问的特性。
Within cloud environments, confidentiality primarily pertains th restricting access to data in *transit* and *storage*.
在云环境中，保密性主要是关于对 *传输* 和 *存储* 的数据进行访问限制的。

![保密性](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/baomixing.PNG)

### Integrity 完整性

**Integrity** is the characteristic of **not having been altered by an unauthorized party**.
**完整性** 是指 **未被未授权方篡改** 的特性。
An important issue that concerns data integrity in the cloud is whether a cloud consumer can be guaranteed that the data it transmits to a cloud service **matches** the data received by that cloud service.
关系到云中数据完整性的一个重要问题是能否向云用户保证传送到云服务的数据与云服务接收到的数据 **完全一致**。
Intergrity can extend to how data is stored, processed, and retrieved by cloud services and cloud-based IT resources.
完整性可以扩展至云服务和基于云的 IT 资源如何存储、处理和检索数据。

![完整性](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/wanzhengxing.PNG)

### Authenticity 真实性

**Authenticity** is the characteristic of something having been provided by an **authorized source**.
**真实性** 是指事物是由 **经过授权的源** 提供的这一特性。
This concept encompasses **non-repudiation**, which is the inability of a party to deny or challenge the authentication of an interaction.
这个概念包括 **不可否认性**，也就是一方面不能否认或质疑一次交互的真实性。

### Availability 可用性

**Availability** is the characteristic of being accessible and usable during a specified time period.
**可用性** 是在特定的时间段内可以访问和可以使用的特性。
In typical cloud environments, the availability of cloud services can be a responsibility that is shared by the cloud provider and the cloud carrier.
在典型的云环境中，云服务的可用性可能是云提供者和云运营商共同的责任。
The availability of a cloud-based solution that extends to cloud service consumers is further shared by the cloud consumer.
当基于云的解决方案扩展到云服务用户时，可用性也会是云用户的责任。

### Threat 威胁

A **threat** is a potential security violation that can challenge defenses in an attempt to breach privacy and/or cause harm.
**威胁** 是潜在的安全性违反，可能试图破坏隐私并/或导致危害，以此挑战防护。
Both manually and automatically instigated threats are designed to exploit known weaknesses, also referred to as *vulnerabilities*.
由手动或自动策动的威胁被设计用来利用已知的弱点，这些弱点也称为 *漏洞*。
A threat that is carried out results in an *attack*.
威胁实时的结果就是 *攻击*。

### Vulnerability 漏洞

A **vulnerability** is a weakness that can be exploited either because it is protected by insufficient security controls, or because existing security controls are overcome by an attack.
**漏洞** 是一种可能被利用的弱点，可能是因为安全控制保护不够，也可能是因为攻击击败了现有的安全控制。
IT resource vulnerabilities can have a range of causes, including configuration deficiencies, security policy weaknesses, user errors, hardware or firmware flaws, software bugs, and poor security architecture.
造成 IT 资源漏洞的原因有很多，包括配置缺陷、安全策略弱点、用户错误、硬件或固件缺陷、软件漏洞和安全架构薄弱。

### Risk 风险

**Risk** is the possibility of loss or harm arising from performing an activity.
**风险** 是指执行一个行为带来损失或危害的可能性。
Risk is typically measured according to its *threat level* and *the number of possible or known vulnerabilities*.
风险一般是由它的 *威胁等级* 和 *可能或已知的漏洞数量* 来衡量的。

### Security Controls 安全控制

**Security controls** are countermeasures used to *prevent or respond* to security threats and to *reduce or avoid* risk.
**安全控制** 是用来 *预防或响应* 安全威胁以及 *降低或避免* 风险的对策。
Details on how to use security countermeasures are typically outlined in the security policy.
如何使用安全对策的细节通常是在安全策略中设定的。

### Security Mechanisms 安全机制

*Countermeasures* are typically described in terms of **security mechanisms**, which are components comprising a defensive framework that protects IT resources, information, and service.
*对策* 通常是以 **安全机制** 的形式来描述的，安全机制是构成保护 IT 资源、信息和服务的防御框架的组成部分。

### Security Policies 安全策略

A **security policy** establishes a set of security rules and regulations.
**安全策略** 建立了一套安全规则和规章。
Often, security policies will further define how these rules and regulations are implemented and enforced.
通常，安全策略会进一步定义该如何实现和加强这些规则和规章。

## THREAT AGENTS 威胁作用者

A **threat agent** is an entity that poses a threat because it is capable of carrying out an attack.
**威胁作用者** 是引发威胁的实体，因为它能够实施攻击。
Cloud security threats can originate either **internally** or **externally**, from **humans** or **software programs**.
云安全威胁可能来自 **内部** 也可以来自 **外部**，可能来自于 **人** 也可能来自于 **软件程序**。

![威胁作用者](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/weixiezuoyongzhe.PNG)

### Anonymous Attacker 匿名攻击者

An **anonymous attacker** is a non-trusted cloud service consumer without permissions in the cloud.
**匿名攻击者** 是云中没有权限的、不被信任的云服务用户。
It typically exists as an *extermal software program* that launches network-level attacks through public networks.
它通常是一个 *外部软件程序*，通过公网发动网络攻击。

Anonymous attackers often resort to committing acts like *bypassing* user accouts or *stealing* user credentials, while using methods that either ensure anonymity or require substantial resources for prosecution.
匿名攻击者往往诉诸 *绕过* 用户账号或 *窃取* 用户证书的手段，同时使用能保证匿名性或需要大量资源才能被检举的方法。

![匿名攻击者](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/niminggongjizhe.PNG)

> 图符为红色圆角方框加红色闪电符号。

### Malicious Service Agent 恶意服务作用者

A **malicious service agent** is able to **intercept and forward** the network traffic that flows within a cloud.
**恶意服务作用者** 能 **截取并转发** 云内的网络流量。
It typically exists as a *service agent (or a program pretending to be a service agent) with compromised or malicious logic*.
它通常是 *带有被损害的或恶意逻辑的服务代理（或伪装成服务代理的程序）*。
It may also exist as an *external program* able to remotely intercept and potentially corrupt message contents.
也有可能是能够远程截取并破坏消息内容的 *外部程序*。

![恶意服务作用者](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/eyifuwuzuoyongzhe.PNG)

> 恶意服务作用者的图符为蓝色长条加红色闪电。

### Trusted Attacker 授信的攻击者

A **trusted attacker** shares IT resources in the same cloud environment as the cloud consumer and attempts to exploit legitimate credentials to target cloud providers and the cloud tenants with whom they share IT resources.
**授信的攻击者** 与同一云环境中的云用户共享 IT 资源，试图利用合法的证书来把云提供者以及与他们共享 IT 资源的云租户作为攻击目标。
Unlike anonymous attackers (which are non-trusted), trusted attackers usually launch their attacks from within a cloud's trust boundaries by *abusing* legitimate credentials or *via* the appropriation of sensitive and confidential information.
不同于匿名攻击者（它们是非授信的），授信的攻击者通常通过 *滥用* 合法的证书或通过 *挪用* 敏感和保密的信息，在云的信任边界内部发动攻击。

![授信的攻击者](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/shouxindegongjizhe.PNG)

> 授信的攻击者的图符由蓝色圆角方框加红色闪电组成。

### Malicious Insider 恶意的内部人员

**Malicious insiders** are human threat agents acting on behalf of or in relation to the cloud provider.
**恶意的内部人员** 是人为的危险作用者，他们的行为代表云提供者或者与之有关。

![恶意的内部人员](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/eyideneiburenyuan.PNG)

> 恶意的内部人员用以表示发起自总作战的攻击的记号，人形符号是可选的。

## CLOUD SECURITY THREATS 云安全威胁

### Traffic Eavesdropping 流量窃听

**Traffic eavesdropping** occurs when data being transferred to or within a cloud (usually from the cloud consumer to the cloud provider) is passively intercepted by a malicious service agent for illegitimate information gathering purposes.
**流量窃听** 是指当数据在传输到云中或在云内部传输时（通常是从云用户到云提供者）被恶意的服务作用者被动地截获。

![流量窃听](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/liuliangqieting.PNG)

### Malicious Intermediary 恶意媒介

The **malicious intermediary** threat arises when messages are intercepted and altered by a malicious service agent, thereby potentially compromising the message's confidentiality and/or intergrity.
**恶意媒介** 威胁是指消息被恶意服务作用者截获并且被篡改，因此可能会破坏消息的保密性和完整性。

![恶意媒介](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/eyimeijie.PNG)

### Denial of Service 拒绝服务

The objective of the **denial of service(DoS)** attack is to overload IT resources to the point where they cannot function properly.
**拒绝服务（DoS）** 攻击的目标是使 IT 资源过载至无法正确运行。
This form of attack is commonly launched in one of the following ways:
这种形式的供给通常是以以下方式之一发起的：

- The workload on cloud services is artificially increased with *imitation messages or repeated communication requests*.
  云服务上的负载由于 *伪造的消息或重复的通信请求* 不正常地增加。
- The network is overloaded with traffic to reduce its responsiveness and cripple its performance.
  网络流量过载，降低了响应性，性能下降。
- Multiple cloud service requests are sent, each of which is designed to consume excessive memory and processing resources.
  发出多个云服务请求，每个请求都设计成消耗过量的内存和处理资源。

![拒绝服务](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/jujuefuwu.PNG)

### Insufficient Authorization 授权不足

The **insufficient authorization** attack occurs when access is granted to an attacker erroneously or too broadly, resulting in the attacker getting access to IT resources that are normally protected.
**授权不足** 攻击是指错误地授予了攻击者访问权限或是权限太宽泛，导致攻击者能够访问到本应该受到保护的 IT 资源。

![授权不足](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/shouquanbuzu.PNG)

A variation of this attack, known as **weak authentication**, can result when weak passwords or shared accounts are used to protect IT resources.
这种攻击的一种变种称为 **弱认证**，如果用弱密码或共享账户来保护 IT 资源，就可能导致这种攻击。

![弱认证](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/ruorenzheng.PNG)

### Virtualization Attack 虚拟化攻击

A **virtualization attack** exploits vulnerabilities in the virtualization platform to jeopardize its confidentiality, integrity, and/or availability.
**虚拟化攻击** 利用的是虚拟化平台中的漏洞来危害虚拟化平台的保密性、完整性和可用性。

![虚拟化攻击](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/xunihuagongji.PNG)

### Overlapping Trust Boundaries 信任边界重叠

If physical IT resources within a cloud are shared by different cloud service consumers, these cloud service consumers have **overlapping** trust boundaries.
如果云中的物理 IT 资源是由不同的云服务用户共享的，那么这些云服务用户的信任边界是 **重叠** 的。
Malicious cloud service consumers can target shared IT resources with the intention of compromising cloud consumers or other IT resources that share the same trust boundary.
恶意的云服务用户可以把目标设定为共享的 IT 资源，意图损害其他共享同样信任边界的云服务用户或 IT 资源。
The consequence is that some or all of the other cloud service consumers cloud be impacted by the attack and/or the attacker cloud use virtual IT resources against others that happen to also share the same trust boundary.
结果是某些或者所有其他的云服务用户都受到攻击的影响，或者攻击者可能使用虚拟 IT 资源来供给其他共享同样信任边界的用户。

![信任边界重叠](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/xinrenbianjiechongdie.PNG)

## ADDITIONAL CONSIDERATIONS 其他考量

### Flawed Implementations 有缺陷的实现

The substandard design, implementation, or configuration of cloud service deployments can have undesirable consequences, beyond runtime exceptioins and failures.
云服务部署不合规范的设计、实现或配置会有不利的后果，而不仅仅是运行时的异常和失效。

![有缺陷的实现](http://oxnec2zdn.bkt.clouddn.com/CloudComputing/youquexiandeshixian.PNG)

### Security Policy Disparity 安全策略不一致

When a cloud consumer places IT resources with a public cloud provider, it may need to accept that its traditional information security approach may not be identical or even similar to that of the cloud provider.
当云用户把 IT 资源放到公有云提供者那里时，就需要接受云提供者提供的信息安全方法与传动的方法可能会不完全相同，甚至不相似。
This incompatibility needs to be assessed to ensure that any data or other IT assets being relocated to a public cloud are adequately protected.
需要评估这种不兼容性，保证对被放置到公有云的数据或其他 IT 资产的保护是足够的。

Furthermore, with some public clouds, additional third parties, such as security brokers and certificate authorities, may introduce their own distinct set of security policies and practices, further complicating amy attempts to standardize the protection of cloud consumer assets.
此外，在有些公有云中，其他的第三方（例如安全代理和证书授权方）可能会引入他们自己不同的安全策略和措施，使得任何对云用户资产保护进行标准化的试图都进一步复杂化。

### Contracts 合约

Cloud consumers need to carefully examine contracts and SLAs put forth by cloud providers to ensure that security policles, and other relevant guarantees, are satisfactory when it comes to asset security.
云用户需要很小心地检查云提供者提出的合约和 SLA，确保设计资产安全的安全策略和其他相关的保障令人满意。

Another aspect to contractual obligations is where the lines are drawn between cloud consumer and cloud providers assets.
有关合约责任的另一点是云用户和云提供者资产之间的界限在哪里。

Sometimes the best solution is to look for a different cloud provider with more compatible contractual terms.
有时最好的解决方案就是找另外一家提供更兼容合约条款的云提供者。

### Risk Management 风险管理

When assessing the potential impacts and challenges pertaining to cloud adoption, cloud consumers are encouraged to perform a formal risk assessment as part of a risk management strategy.
在评估与采用云相关的可能的影响和挑战时，云用户被鼓励进行一个正式的风险评估，作为风险管理策略的一部分。

The main activities are generally defined as *risk assessment*, *risk treatment*, and *risk control*.
主要的工作通常是 *风险评估*、*风险处理* 和 *风险控制*。

- *Risk Assessment 风险评估*
    - In the risk assessment stage, the cloud environment is analyzed to identify potential vulnerabilities and shortcomings that threats can exploit.
      在风险评估阶段，要分析云环境，识别出威胁可能会利用的潜在的漏洞和缺陷。
    - The cloud provider can be asked to produce statistics and other information about past attacks (successful and unsuccessful) carried out in its cloud.
      云提供者可能会被要求提供过去在它的云中发生过的（成功和不成功的）供给。
    - The identified risks are *quantified and qualified* according to the probability of occurrence and the degree of impact in relation to how the cloud consumer plans to utilize cloud-based IT resources.
      根据发生的概率和对云用户计划使用基于云的 IT 资源的影响的程度，对识别出来的风险进行 *定量和定性*。
- *Risk Treatment 风险处理*
    - Mitigation policies and plans are designed during the risk treatment stage with the intent of successfully treating the risks that were discovered during risk assessment.
      在风险处理阶段设计的风险减轻策略和计划意在成功地处理在风险评估阶段发现的风险。
    - Some risk can be *eliminated*, others can be *mitigated*, while others can be dealt with via outsourcing or even incorporated into the insurance and/or operating loss budgets.
      有些风险可以 *消除*，有些可以 *减轻*， 还有一些可以通过外包或者甚至加入保险或运营损失预算中。
- *Risk Control 风险控制*
    - The risk control stage is related to risk monitoring, a *three-step process* that is comprised of surveying related events, reviewing these events to determine the effectiveness of previous assessments and treatments, and identifying any policy adjustment needs.
      风险控制阶段是与风险监控相关的，含有一个 *三阶段处理过程*，包括调查相关的事件，审阅这些时间来决定前期评估和处理的有效性，确认是否需要进行策略调整。
