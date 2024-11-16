---
layout: post
title: "Microservices are great....until they aren't"
categories: tech
date: "2024-07-21T00:00:00.000Z"
description: "A quick look at my experience with microservices architecture."
---

<img src="/assets/indra-projects-a_ldJ0EzbLI-unsplash.jpg" alt="A microscope" />

## Before we start...

Despite the tone of what you are about to read I am actually mostly pro micro service architecture. Currently our industry seems to be stuck in the mindset that every piece of logic should be split up into a serparate microservice. Not only does this contradict my 'Do what works' mindset, it can create a lot of overhead and cause issues for projects that would be be better suited for a monolithic codebase.

[Better articles](https://renegadeotter.com/2023/09/10/death-by-a-thousand-microservices.html) have been written by smarter people than I on the pitfalls of micro services architecture. This article is meant to share my experience working in a culture of microservice first api strategy.

Through a combination of Googling and asking Github Copilot, I have come up with this list of benefits to microservices architecture:

1. **Scalability**
2. **Flexibility**
3. **Modularity**
4. **Fault Isolation**
5. **Team Autonomy**
6. **Easier Maintenance**

## The supposed benefits of microservices

A breakdown of the highly touted benefits of microservices architecture and why they have never been actually benefits to me

Microservices architecture offers several benefits:

### Scalability

**The idea** - Microservices allow for independent scaling of different components of an application. Each microservice can be scaled individually based on its specific needs, resulting in better resource utilization and improved performance.

**My experience** - I have literally never done this. I know this is probably a large benefit for many companies with heavy or inconsistent traffic, but in my experience scaling config is copy pasted from one app the other and never touched after launch. The reality is that for a lot of apps traffic is predictable and a sensible scaling config can be reused with no need to adjust. Also, I find that it is rare that specific functionality needs to scale independantly. If it truly does

### Flexibility

**The idea** - Microservices enable flexibility in technology choices. Each microservice can be developed using different programming languages, frameworks, and databases, based on the specific requirements of that service. This allows teams to choose the best tools for each component, resulting in increased productivity and innovation.

**My experience** -

### Modularity

**The idea** - Microservices promote modularity by breaking down an application into smaller, loosely coupled services. Each microservice focuses on a specific business capability, making it easier to understand, develop, test, and maintain. Changes or updates to one microservice do not impact the entire application, reducing the risk of unintended consequences.

**My experience** -

### Fault Isolation

**The idea** - In a microservices architecture, if one microservice fails or experiences issues, it does not affect the entire system. Other microservices can continue to function independently, ensuring high availability and fault tolerance.

**My experience** -

### Team Autonomy

**The idea** - Microservices enable teams to work independently on different microservices. Each team can have its own development, deployment, and release cycles, allowing for faster iteration and innovation. This also promotes ownership and accountability within each team.

**My experience** -

### Easier Maintenance

**The idea** - With smaller and more focused microservices, it becomes easier to understand, debug, and maintain the system. Changes or updates to one microservice have minimal impact on other services, reducing the risk of introducing regressions or breaking changes.

**My experience** - I have often found the opposite to be true. Sure you have spread out the logic, but each microservice requires boilerplate and dependencies which are often duplcated in. For example, axios is a common JavaScript package used for making HTTP requests. If axios gets a patch to fix a vulnerabilty you now have to apply that patch in each service. If you have split your monolith into 5 microservices you now have 5 times the work to apply that patch.

Debugging can be more difficult when you have to follow transactions as they flow through multiple microservices, and observability is more difficult to configure. Observability also suffers from the same problem as package upgrades. You have to configure APM (New Relic for example) and synthetics for each service, again multiplying the work required.

Furthermore, it is trivial to split the logic up in your app code and still keep in one service. A good file structure is important for any codebase.

## Conclusion

What do I think is the best approach. Keep it simple. Do what works.
