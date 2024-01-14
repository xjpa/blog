---
layout: default
title: Understanding Distributed Systems
---

## Understanding Distributed Systems

<img src="https://m.media-amazon.com/images/I/71rlI0H7QsL._SY522_.jpg" height="300">

This is a good book. I read this as I wanted an easier read to the extremely dense book, Designing Data Intensive Applications (DDIA). But after reading this book, I didnt find the time sunk to have been worth my time. It was extremely basic. The reason I still find it a good book, is that it's well written for an audience that's just looking for a shallow covering of distributed system concepts, like perhaps a freshman student.

But for someone with a bit of experience with the web, sticking to books like Designing Data Intensive Applications (DDIA) or Web Scalability for Startup Engineers wouldve been a far better use of one's time.

Also, I do see some benefits of reading this book as a way to like "skim" the field ahead.

## Notes

My notes also include things that arent from the book, as my process is basically

1. Read Book

2. Highlight

3. Research them on the net

4. Summarize (as notes)

As the book is pretty short, I had to add a few more details from research to my notes here

<center><h1>Introduction</h1></center>

- DISTRIBUTED SYSTEMS: a group of nodes (process, machine) that cooperate by exchanging messages over communication links to achieve some task

- WHY - AVAILABILITY: because some apps require high availability, need to be resilient to single-node failures. Ex. dropbox replicates your data across nodes so none will be lost when 1 node has failed

- WHY - THROUGHPUT: some workloads cant be tackled by a single node. Ex. Google receives lots of RPS (requests per second)

- WHY - PERF: some apps have performance requirements that are unattainable with a single node due to limitations in processing power, memory, and bandwidth. Ex. Netflix can stream high-resolution movies seamlessly to your TV partly because it uses distributed systems. Geographically distributed, enabling them to deliver content from a data center close to the user, reducing latency and improving streaming quality. This approach also allows for load balancing and fault tolerance, ensuring a consistent and high-quality viewing experience even during times of high demand.

5 Challenges in Building Distributed Systems

#1 COMMUNICATION

- CHALLENGE: In a distributed system, components often need to communicate over a network, which is less reliable and slower than local communication. Handling latency, managing network failures, and ensuring efficient data transfer are significant issues.

- SOLUTION: Techniques like message queuing, efficient serialization protocols, and robust error handling can help mitigate communication challenges.

#2 COORDINATION

- CHALLENGE: Ensuring that different parts of the system are working together in a coherent and synchronized manner is difficult, especially in the presence of network delays and failures.

- SOLUTION: Implementing distributed algorithms for consensus (like Paxos or Raft), using coordination services like Apache ZooKeeper, and designing systems with eventual consistency in mind can aid in effective coordination.

#3 SCALABILITY

- CHALLENGE: As the system grows, it must handle more users, data, and transactions without a drop in performance. Scaling a distributed system can be complex, involving both hardware and software challenges.

- SOLUTION: Employing load balancing, horizontal scaling (adding more nodes), efficient data partitioning, and stateless design can improve scalability.

#4 RESILIENCY

- CHALLENGE: Building systems that can handle and recover from failures (be it hardware, software, or network-related) is essential. Resilient systems should continue to operate effectively in the face of such failures.

- SOLUTION: Implementing redundancy, failover mechanisms, reliable cross-service communication, and regular testing of failure scenarios (like chaos engineering) can enhance system resilience.

#5 MAINTAINABILITY

- CHALLENGE: As distributed systems are complex and involve many interdependent components, making changes, diagnosing issues, and understanding system behavior can be challenging.

- SOLUTION: Adopting good design practices, such as modular architecture, clear interfaces, and comprehensive monitoring and logging, can significantly improve maintainability. Regular code reviews and documentation also play a vital role.

<center><h1>I. Communication</h1></center>
<center><h1>II. Coordination</h1></center>

- TWO GENERALS PROBLEM: [wikipedia](https://en.wikipedia.org/wiki/Two_Generals%27_Problem)

<center><h1>III. Scalability</h1></center>

- LOAD: performance of a system is about how it can handle load (system resources like CPU, memory, bandwidth)

- PERFORMANCE: in the book, is measured by throughput and response time

- THROUGHPUT: number of requests per second (RPS) by the app

- RESPONSE TIME: the time between sending a request to the app and receiving a response.
<center><h1>IV. Resiliency</h1></center>

- RESILIENT: about doing the job even when failures happen. At scale, many components can fail like nodes crashing, network links severed, data corruption, security vulnerabilities, human errors, environmental factors like natural disasters affecting physical infra, dependency failures like 3rd party APIs failing, poorly optimized queries/algorithms, service orchestration challenges like with microservices or service discovery

- Availability Nines

| Availability         | Downtime Per Day |
| -------------------- | ---------------- |
| 90% (One Nine)       | 2.40 hours       |
| 99% (Two Nines)      | 14.40 minutes    |
| 99.9% (Three Nines)  | 1.44 minutes     |
| 99.99% (Four Nines)  | 8.64 seconds     |
| 99.999% (Five Nines) | 864 milliseconds |

90% Availability ("One Nine"): Downtime Per Day: 2.4 hours

This level of availability is generally considered low for most services.

99% Availability ("Two Nines"): Downtime Per Day: 14.4 minutes

This is a basic level of reliability for many business applications.

99.9% Availability ("Three Nines"): Downtime Per Day: 1.44 minutes

Often considered a good balance between cost and reliability for many services.

99.99% Availability ("Four Nines"): Downtime Per Day: 8.64 seconds

This is a higher standard of reliability, common in critical business operations.

99.999% Availability ("Five Nines"): Downtime Per Day: 864 milliseconds

This is considered near-perfect availability, often sought after in mission-critical systems where downtime is extremely costly.

- P99 vs Availability Nines: Note that the Nines are different to percentile metrics like P99 as P99 is a measurement of how systems perform under load, in particular response times and for measuring perf of tail end users. Availability Nines are for the uptime. P99 is more for the scalability challenge. Although it is quite relevant to resiliency as it might reflect the system under stress/failure conditions, which is why i brought it up here (as well as I sometimes mix the two up)

<center><h1>V. Maintanability</h1></center>

<a href="/bookshelf">⬅️ back to bookshelf</a>
