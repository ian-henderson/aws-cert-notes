# 03 - Beginner's Guide to EC2

## Introducing EC2 (Elastic Compute Cloud)

Secure, resizable compute capacity in the cloud.

Like a virtual machine, only hosted in AWS instead of your own data center.

It's designed to make web-scale cloud computing easier for developers.

The capacity you want when you need it.

You are in complete control of your own instances.

### Why Is It So Cool?

#### Game Changer

AWS led a big change in the industry by introducing EC2.

#### Pay Only For What You Use

EC2 changed the economics of computing.

#### No Wasted Capacity

Select the capacity that you need right now. Grow and shrink when you need.

#### On Premises Infrastructure (the old way)

Requires:

- Estimating capacity
- Long-term investment (3-5 years)

## EC2 Instance Pricing Options

### [Pricing Calculator](https://calculator.aws/#/)

### On Demand

Pay by the hour or the second, depending on the type of instance you run.

- Flexible
  - Low cost and flexibility of Amazon EC2 without any up-front payment or long-term commitment.

- Short-Term
  - Applications with short-term, spiky, or unpredictable workloads that cannot be interrupted.

- Testing The Waters
  - Applications being developed or tested on Amazon EC2 for the first time.

### Reserved

Reserved capacity for one or three years. Up to 72% discount on the hourly charge. Regional.

- Predictable Usage
  - Applications with steady state or predictable usage.

- Specific Capacity Requirements
  - Applications that require reserved capacity.

- Pay Up-Front
  - You can make up-front payments to reduce their total computing cost even further.

- Standard Reserved Instances
  - Up to 72% off on-demand price.

- Convertable Reserved Instances
  - Up to 54% off on-demand price. Has the option to change to a different Reserved Instance type of equal or greater value.

- Scheduled Reserved Instances
  - Launch within the time window you define. Match your capacity reservation to a predictable recurring schedule that only requires a fraction of a day, week, or month.

### Spot

Purchase unused capacity at a discount of up to 90%. Prices fluctuate with supply and demand.

#### When to use Spot instances

- Applications that have flexible start and end times.
- Applications that are only feasable at very low compute prices.
- Users with an urgent need for large amounts of additional computing capacity.

### Dedicated Hosts

A physical EC2 server dedicated for your use. The most expensive option.

- Compliance
  - Regulatory requirements that may not support multi-tenant virtualization.

- Licensing
  - Great for licensing which does not support multi-tenancy or cloud deployments.

- On-Demand
  - Can be purchased on-demand (hourly).

- Reserved
  - Can be purchased as a reservation for up to 70% off the on-demand price.

### Savings Plans

- Save up to 72%
  - All AWS Compute usage regardless of instance type or Region.

- Commit To One or Three Years
  - Commit to use a specific amount of compute power (measured in $/hour) for a one-year or three-year period.

- Super Flexible
  - Not only EC2, also includes serverless technologies like Lambda and Fargate.

## Exploring EC2 Instance Types

[EC2 Instance Types](https://aws.amazon.com/ec2/instance-types/)

### General Purpose

General purpose instances provide a balance of compute, memory and networking resources, and can be used for a variety of diverse workloads. These instances are ideal for applications that use these resources in equal proportions such as web servers and code repositories.

### Compute Optimized

Compute Optimized instances are ideal for compute bound applications that benefit from high performance processors. Instances belonging to this category are well suited for batch processing workloads, media transcoding, high performance web servers, high performance computing (HPC), scientific modeling, dedicated gaming servers and ad server engines, machine learning inference and other compute intensive applications.

### Memory Optimized

Memory optimized instances are designed to deliver fast performance for workloads that process large data sets in memory.

### Accelerated Computing

Accelerated computing instances use hardware accelerators, or co-processors, to perform functions, such as floating point number calculations, graphics processing, or data pattern matching, more efficiently than is possible in software running on CPUs.

### Storage Optimized

Storage optimized instances are designed for workloads that require high, sequential read and write access to very large data sets on local storage. They are optimized to deliver tens of thousands of low-latency, random I/O operations per second (IOPS) to applications.

## [Elastic Block Store (EBS) Volumes](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volumes.html)

Storage volumes that you can attach to your EC2 instances.

- Use them the same way you'd use any system disk
- Create a filesystem
- Run a database
- Run an operating system
- Store data
- Install applications

### Mission Critical

- Production Workloads
  - Designed for mission critical workloads.

- Highly Available
  - Automatically replicated within a single Availability Zone to protect against hardware failures.

- Scalable
  - Dynamically increase capacity and change the type volume with no downtime or performance impact to you live systems.

### [EBS Volume Types](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volume-types.html)

#### General Purpose SSD (gp2)

- 3 IOPS per GiB, up to a maximum of 16,000 IOPS per volume.
- gp2 volumes smaller than 1 TB can burst up to 3,000 IOPS.
- Good for boot volumes or development and test applications which are not latency sensitive.

#### General Purpose SSD (gp3)

- The latest generation.
- Baseline of 3,000 IOPS for any volume size (1 GB - 16 TB).
- Delivers up to 16,000 IOPS.
- 20% cheaper than gp2!
- Like gp2, they are good for boot volumes or development and test applications which are not latency sensitive.

#### Provisioned IOPS SSD (io1)

- The high performance option, and the most expensive.
- Up to 64,000 IOPS per volume. 50 IOPS per GiB.
- Use if you need more than 16,000 IOPS.
- Designed for I/O intensive applications, large databases, and latency-sensitive workloads.

#### Provisioned IOPS SSD (io2)

- Latest generation; higher durability and more IOPS.
- io2 is the same price as io1.
- 500 IOPS per GiB, up to 64,000 IOPS.
- 99.999% durability instead of up to 99.9%.
- I/O intensive apps, large databases, and latency-sensitive workloads. Applications which need high levels of durability.

#### Provisioned IOPS SSD io2 Block Express

- Storage Area Network (SAN) in the cloud. Highest performance, sub-millisecond latency.
- Uses EBS Block Express architecture.
- 4x throughput, IOPS, and capacity of regular io2 volumes.
- Up to 64 TB, 256,000 IOPS per volume.
- 99.999% durability.
- Great for the largest, most critical, high-performance applications like SAP HANA, Oracle, Microsoft SQL Server, and IBM DB2.

#### Throughput Optimized HDD (st1)

- Low-cost HDD volume.
- Baseline throughput of 40 MB/s per TB.
- Ability to burst up to 250 MB/s per TB.
- Maximum thoughput of 500 MB/s per volume.
- Frequently-accessed, throughput-intensive workloads.
- Big Data, data warehouses, ETL, and log processing.
- A cost-effective way to store mountains of data.
- Cannot be a boot volume.

#### Cold HDD (sc1)

- Lowest cost option.
- Baseline throughput of 12 MB/s per TB.
- Ability to burst up to 80 MB/s per TB.
- Max throughput of 250 MB/s per volume.
- A good choice for colder data, requiring fewer scans per day.
- Good for applications that need the lowest cost and performance is not a factor.
- Cannot be a boot volume.

### IOPS vs Throughput

#### IOPS

- Measures the number of read and write operations per second.
- Important metric for quick transactions, low latency apps, transactional workloads.
- The ability to action reads and writes very quickly.
- Choose Provisioned IOPS SSD (io1 or io2).

#### Throughput

- Measures the number of bits read or written per second (MB/s).
- Important metric for large datasets, large I/O sizes, complex queries.
- The ability to deal with large datasets.
- Choose Throughput Optimized HDD (st1).

### Exam Tips

#### EBS: SSD Volumes

Highly available and scalable storage volumes you can attach to an EC2 instance.

- gp2: General Purpose SSD
  - Suitable for boot disks and general applications.
  - 3 IOPS per GiB.
  - Up to 16,000 IOPS per volume.
  - Up to 99.9% durability.

- gp3: Latest Generation General Purpose SSD
  - Suitable for boot disks and general applications.
  - Baseline of 3,000 IOPS for all volumes.
  - Up to 16,000 IOPS per volume.
  - Up to 99.9% durability.
  - 20% cheaper than gp2!

- io1: Provisioned IOPS SSD
  - Suitable for OLTP and latency-sensitive applications.
  - 50 IOPS/GiB.
  - Up to 64,000 IOPS per volume.
  - High performance and most expensive.
  - Up to 99.9% durability.

- io2: Latest Generation Provisioned IOPS SSD
  - Suitable for OLTP and latency-sensitive applications.
  - 500 IOPS/GiB.
  - Up to 64,000 IOPS per volume.
  - Up to 99.999% durability.

- io2: Block Express: Provisioned IOPS SSD
  - For the largest, most critical, high-performance applications: SAP HANA, Oracle, Microsoft SQL Server, and IBM DB2.
  - Up to 64 TB, 256,000 IOPS per volume.
  - 99.999% durability.
  - SAN in the cloud!

#### EBS: HDD Volumes

- st1: Throughput Optimized HDD
  - Suitable for big data, data warehouse, ETL.
  - Max throughput is 500 MB/s per voluem.
  - Cannot be a boot volume.
  - Up to 99.9% durability.

- sc1: Cold HDD
  - Max throughput of 250 MB/s per volume.
  - Less-frequently-accessed data.
  - Cannot be a boot volume.
  - Lowest cost.
  - Up to 99.9% durability.

## Elastic Load Balancer

A load balancer distributes network traffic across a group of servers.

### 7 Layer (OSI) Model

#### What is it?

A conceptual framework which describes the functions of a network.

Beginning with the application layer, which directly serves the end user, down to the physical layer.

- Layer 7: Application
  - What the end user sees, HTTP, web browsers.
- Layer 6: Presentation
  - Data is in a usable format. Encryption, SSH.
- Layer 5: Session
  - Maintains connections and sessions.
- Layer 4: Transport
  - Transmits data using TCP and UDP.
- Layer 3: Network
  - Logically routes packets, based on IP address.
- Layer 2: Data Link
  - Physically transmits data based on MAC addresses.
- Layer 1: Physical
  - Transmits bits and bytes over physical devices.

### Elastic Load Balancer Types

#### Application Load Balancer

- Used for load balancing HTTP/HTTPS traffic.
- Operates at Layer 7 and is application-aware.
- They support advanced request routing to specific web servers based on the HTTP header.

#### Network Load Balancer

- High performance.
- Used for load balancing TCP traffic where extreme performance is required.
- Operates at Layer 4 (Transport Layer).
- Capable of handling millions of requests per second while maintaining ultra-low latencies.
- Most expesive option.

#### Classic Load Balancer (Legacy)

- Legacy
  - Legacy option, but may appear on exam
- HTTP/HTTPS
  - Support Layer 7-specific features, such as X-Forwarded-For headers and sticky sessions.
- TCP
  - Supports Layer 4 load balancing for applications that rely purely on the TCP protocol.

#### Gateway Load Balancer

Allows you to load balance workloads for third-party virtual appliances running in AWS, such as:

- Virtual appliances purchased using the AWS Marketplace
- Virtual firewalls from companies like Fortinet, Palo Alto, Juniper, Cisco
- IDS/IPS systems from companies like CheckPoint, Trend Micro, etc.

### X-Forwarded-For Header

Identifies the originating IP address of a client connecting through a load balancer.

### Common Load Balancer Errors

#### Error 504: Gateway Timeout

The target failed to respond; Check your application.

- The Elastic Load Balancer could not establish a connection to the target, e.g. the web server, database, or Lambda function.
- Your application is having issues.
- Identify where the application is failing and fix the problem.
