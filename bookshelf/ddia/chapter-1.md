---
layout: default
title: Designing Data Intensive Applications
---

## Designing Data Intensive Applications (DDIA) Chapter 1 Notes

---

The book is too compact to write notes of. The book reads like a cliff notes page itself. Thus I will take a different approach here in that my book notes will just contain questions I use to review the book and explore the topics mentioned deeper.

<h1>Questions to Ask</h1>

- What is the primary distinction between data-intensive and compute-intensive applications?

- Can you provide examples of scenarios where databases, caches, search indexes, stream processing, and batch processing are required in an application?

- Describe the significance of asynchronous message handling in data-intensive applications. How might this be advantageous?

- How does batch processing differ from stream processing in the context of data-intensive applications? Provide examples of scenarios where each might be useful.

- What are some potential challenges or trade-offs that developers might encounter when striving to build reliable, scalable, and maintainable data systems?

- How does the concept of an application programming interface (API) play a role in hiding implementation details and providing a seamless experience for clients?

- Define the characteristics of a good API for a data service. How might a well-designed API contribute to the overall success of a data-intensive application?

- Review the tricky questions mentioned when designing a data system or service. What are some examples of these questions, and why are they important to address?

- Reflect on the significance of ensuring data correctness and completeness, especially in situations where internal issues may arise. What strategies might be employed to achieve this goal?

- How do cache speeds up read operations?

- Scalability. What common challenges arise as a system grows in data volume, traffic, or complexity?

- Fault-tolerant vs resilient systems. Their key difference and how does the concept of fault anticipation tie into these terms?

- Fault vs Failure. A fault refers to a single component deviating from its specification, while a failure occurs when the entire system no longer provides the required service.

- Netflix Chaos Monkey and how it deliberately triggers faults to ensure fault tolerance mechanisms are tested

- How does the Netflix Chaos Monkey work in practice? How does it introduces faults into the system?

- Are there any potential drawbacks or challenges associated with using Chaos Monkey or similar fault injection techniques?

- MTTF. In the context of hardware, what is meant by "mean time to failure" (MTTF)? How is MTTF used to estimate the reliability of hardware components?

- Redundancy on hardware. Redundancy involves adding backup components to hardware systems to reduce the impact of failures. Techniques like RAID, dual power supplies, and hot-swappable components are employed to achieve redundancy. Look into the details of these

<a href="/bookshelf/ddia">⬅️ back to DDIA</a>
