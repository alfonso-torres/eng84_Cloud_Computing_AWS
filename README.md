# Cloud Computing - AWS

### What is Cloud Computing

Cloud computing is a term used to describe the use of hardware and software delivered via network (usually the Internet). So is a paradigm that allows computing services to be offered through a network, which is usually the internet. Simply put, cloud computing is the delivery of computing services – including servers, storage, databases, networking, software, analytics and intelligence – over the Internet (“the cloud”) supported by four amazing pillars ease of use, flexibility, robustness, cost (AWS, scaling on demand.).

- __Benefits:__

It offers faster innovation, flexbile resources and economies of scale. Typically, you only pay for cloud services you use, helping you lower your operating costs(you don't have to spend huge amounts of money on purchasing and maintaing equipment.), run your infrastructure more efficientely and scale as your business need change (If your business demands increase, you can easily increase your cloud capacity without having to invest in physical infrastructure (Scalability).). Also cloud offers many advanced security features that guarantee that data is securely stored and handled.

1. Cost: Cloud computing eliminates the capital expense of buying hardware and software and setting up and running on-site data centres.
2. Reliability: Cloud computing makes data backup, disaster recovery and business continuity easier and less expensive because data can be mirrored at multiple redundant sites on the cloud provider’s network.
3. Security: Many cloud providers offer a broad set of policies, technologies and controls that strengthen your security posture overall, helping to protect your data, apps and infrastructure from potential threats.

- __Best use cases(Type of cloud services)/who is using it in the industry:__ 

1. Software as a Service (SaaS):

For the reason that companies grow and gather more data, they want to organize and maintain the data. So, SaaS solutions are centrally hosted in the cloud and can be accessed from anywhere, any time. It helps lines of business to more efficiently do their jobs.

2. Infrastructure as a Servive (IaaS):

There is a lot that goes into building and maintaining infrastructure. There's the hardware costs, the cost of the space, the electricity to power it, and the overhead to build and maintain it. Building out a data center can easily cost a company millions of dollars. So this allows companies to avoid costly infrastructure investments and easily access their data via the cloud, from a cloud provider on a pay-as-you-go basis.

3. Test and Development:

The flexibility of the cloud allows for environments to be built up, tested and torn down quickly. There is no need to wait months for the provisioning of a new environment.

4. Platform as a service (PaaS):

Platform as a service refers to cloud computing services that supply an on-demand environment for developing, testing, delivering and managing software applications. PaaS is designed to make it easier for developers to quickly create web or mobile apps, without worrying about setting up or managing the underlying infrastructure of servers.

5. Store, back up and recover data:

Protect your data more cost-efficiently – and at massive scale – by transferring your data over the Internet to an offsite cloud storage system that’s accessible from any location and any device.

Organizations of every type, size, and industry are using the cloud for a wide variety of use cases, such as data backup, disaster recovery, email, virtual desktops, software development and testing, big data analytics, and customer-facing web applications. For example AWS, Microsoft Azure, Google Cloud Platform.

### What is AWS

Amazon Web Services (AWS) is an extension of amazon providing on-demand cloud computing platforms and APIs to individuals, companies, and governments on a metered pay-as-you-go basis, supported by four amazing pillars ease of use, flexibility, robustness, cost.

- __3 advantages of AWS/who is using AWS in the industry:__

1. Easy to use: quickly and securely to host your applications.

2. Flexible: With AWS, you receive a virtual environment that lets you load the software and services your application requires. AWS enables you to select the operating system, programming language, web application platform, database, and other services you need

3. Cost-Effective: You pay only for the compute power, storage, and other resources you use, with no long-term contracts or up-front commitments.

__Industry who are using it:__

- Netflix
- Twitch
- LinkedIn
- Facebook
- BBC
- etc

### Types of Cloud Computing

Not all clouds are the same and not one type of cloud computing is right for everyone. Several different models, types and services have evolved to help offer the right solution for your needs.

There are three different ways to deploy cloud services: on a public cloud, private cloud or hybrid cloud.

![CLOUD](./Cloud_Infrastructure.png)

- __Public Cloud:__

Public clouds are owned and operated by third-party cloud service providers, who deliver their computing resources such as servers and storage over the Internet. Some public cloud examples include those offered by Amazon, Microsoft, or Google. With a public cloud, all hardware, software and other supporting infrastructure are owned and managed by the cloud provider. You access these services and manage your account using a web browser.

- __Private Cloud/On premises:__

A private cloud refers to cloud computing resources used exclusively by a single business or organisation. A private cloud can be physically located on the company’s on-site data centre. Some companies also pay third-party service providers to host their private cloud. A private cloud is one in which the services and infrastructure are maintained on a private network. Is more used for banks, goverments

- __Hybrid Cloud:__

Hybrid clouds combine public and private clouds, bound together by technology that allows data and applications to be shared between them. By allowing data and applications to move between private and public clouds, a hybrid cloud gives your business greater flexibility, more deployment options and helps optimise your existing infrastructure, security and compliance. Sensitive data is saved in private cloud and publicly available information goes on the public cloud, so Hybrid Cloud shared security responsibility.

### Cloud Scaling and types

- __Scale Out/Vertical__:

Scaling out a microservices application can be as simple as spinning up a new container running a webserver app and adding it to the load balancer pool. When scaling out the idea is that it is possible to add identical services to a system to increase performance. (Add new server)

- __Scale Up/Horizontal__:

The target is to increase the resources supporting your application to reach or maintain adequate performance. In a hardware-centric world, this might mean adding a larger hard drive to a computer for increased storage capacity. (make a bigger server)

![SCALING](./scaling.png)


### AWS - Set Up - Two-Tier Architecture - EC2

![AWS_Scheme](./AWS.png)

- __App server set up:__

1. Spinning up an EC2 instance (we use the Ireland DZ) - make sure it's Ubuntu 16.04.
2. Choose free tier for t2.micro when selecting instance type
3. Naming conventions for AWS Servers (Sparta Global only): `Eng84_jose_app`
4. Security group acts as a firewall that controls the traffic for your instance (server) on the machine. Security group works on the instance level as a firewall for your machine. Setting up strict firewalls with minimal port access. So create a security group named `eng84_jose_app_sg` with the following details: SSH, TCP, 22, IP. SSH works on Port 22.
5. DO NOT push any keys or relevant information to Git-hub.

Inside the machine run:
- `sudo apt-get update -y` and `sudo apt-get upgrade -y`
- `sudo apt-get install nginx` to install Nginx
- `sudo systemctl status nginx` to check if it was installed

6. Add http port 80 in your instance inside the security group.
7. Let's check in the browser with the public IP if nginx service is working.
8. To run the app we need to copy the app from our local machine to the server: `scp -i [pem file] [file/folder] ubuntu@[ip]:[path]`
9. Install all the dependencies, run the app and check if it is listening in the browser.

deploy instance = vagrant up

- __Two-Tier Architecture:__

The difference is that when we configure our virtualization environment with vagrant, we use the monolith architecture, it means, everything in the same place, with no backup. All the code and the different parts of it are built together. 

Now what we have is 2-Tier Architecture. A two-tier architecture is a software architecture in which a presentation layer or interface runs on a client, and a data layer or data structure gets stored on a server. Separating these two components into different locations represents a two-tier architecture, as opposed to a single-tier architecture. Two tier architecture provides added security to the DBMS(A database management system) as it is not exposed to the end-user directly. It also provides direct and faster communication.

Wherewith our scenario is the following:

- 2 different machines on the same cloud, eg:
- Ubuntu 16.04 app EC2 with Nodejs and Nginx - Public IP
- Ubuntu 16.04 for Mongo DB - No public IP, only accessible from the app machine.

- __EC2:__

Elastic Compute Cloud (EC2) provides scalable computing capacity in the Amazon Web Services (AWS) Cloud. Using Amazon EC2 eliminates your need to invest in hardware up front, so you can develop and deploy applications faster. You can use Amazon EC2 to launch as many or as few virtual servers as you need, configure security and networking, and manage storage. Amazon EC2 enables you to scale up or down to handle changes in requirements or spikes in popularity, reducing your need to forecast traffic.

EC2 provides the following features:

1. Infrastructure running in the cloud.
2. Very flexible and scalable.
3. Virtual computing environments, known as instances.
4. Secure login information for your instances using key pairs (AWS stores the public key, and you store the private key in a secure place)
5. A firewall that enables you to specify the protocols, ports, and source IP ranges that can reach your instances using security groups.
6. Various configurations of CPU, memory, storage, and networking capacity for your instances, known as instance types.
7. Static IPv4 addresses for dynamic cloud computing, known as Elastic IP addresses.
8. Virtual networks you can create that are logically isolated from the rest of the AWS Cloud, and that you can optionally connect to your own network, known as virtual private clouds (VPCs).
9. Preconfigured templates for your instances, known as Amazon Machine Images (AMIs), that package the bits you need for your server (including the operating system and additional software)

- __VPC:__

Virtual Private Cloud (VPC) is a service that lets you launch AWS resources in a logically isolated virtual network that you define. You have complete control over your virtual networking environment, including selection of your own IP address range, creation of subnets, and configuration of route tables and network gateways. You can use both IPv4 and IPv6 for most resources in your virtual private cloud, helping to ensure secure and easy access to resources and applications.

VPC makes it easy to customize your VPC's network configuration. You can create a public-facing subnet for your web servers that have access to the internet. It also lets you place your backend systems, such as databases or application servers, in a private-facing subnet with no internet access. Amazon VPC lets you to use multiple layers of security, including security groups and network access control lists.

Benefits:

- Secure and monitored network connections.
- Simple set-up and use.
- Customizable virtual network.

Use cases:

- Host a simple, public-facing website: VPC with a Single Public Subnet Only.

- __Security Group:__

A firewall that enables you to specify the protocols, ports, and source IP ranges that can reach your instances using security groups.

A security group acts as a virtual firewall for your EC2 instances to control incoming and outgoing traffic. Inbound rules control the incoming traffic to your instance, and outbound rules control the outgoing traffic from your instance. When you launch an instance, you can specify one or more security groups. You can add rules to each security group that allow traffic to or from its associated instances. You can modify the rules for a security group at any time.

When EC2 decides whether to allow traffic to reach an instance, it evaluates all of the rules from all of the security groups that are associated with the instance.

When you launch an instance in a VPC, you must specify a security group that's created for that VPC.

Wherewith it is our responsibility to control who has access to our instances!!!

- __Route tables/IP Table:__

A route table contains a set of rules, called routes, that are used to determine where network traffic from your subnet or gateway is directed.

Your VPC has an implicit router, and you use route tables to control where network traffic is directed. Each subnet in your VPC must be associated with a route table, which controls the routing for the subnet (subnet route table). You can explicitly associate a subnet with a particular route table. Otherwise, the subnet is implicitly associated with the main route table. A subnet can only be associated with one route table at a time, but you can associate multiple subnets with the same subnet route table.

Each route in a table specifies a destination and a target. For example, the destination for the route is 0.0.0.0/0, which represents all IPv4 addresses. The target is the internet gateway that's attached to your VPC.

We define which are the gateways to our cloud.

- __AMI:__

An Amazon Machine Image (AMI) provides the information required to launch an instance. You must specify an AMI when you launch an instance. You can launch multiple instances from a single AMI when you need multiple instances with the same configuration. You can use different AMIs to launch instances when you need instances with different configurations.

After you create and register an AMI, you can use it to launch new instances.

Basically, is like create a snapshot of a VM instance, with all the configuration that we have installed it that so far, for use later or recover an instance if it has been deleted.
