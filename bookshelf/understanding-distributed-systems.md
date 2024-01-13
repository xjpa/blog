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

Note that my notes also include things that arent from the book, as my process is basically

1. Read Book

2. Highlight

3. Research them on the net

4. Summarize (as notes)

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
<center><h1>III. Scalability</h1></center>
<center><h1>IV. Resiliency</h1></center>
<center><h1>V. Maintanability</h1></center>

<a href="/bookshelf">⬅️ back to bookshelf</a>
