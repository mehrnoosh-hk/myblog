---
title: "Smart Endpoints and Dumb Pipes Principle"
date: 2023-03-20T14:16:44+03:30
type: "post"
tags: ["Microservices"]
---

In a microservices architecture, it is essential to design communication methods between microservices. Contrary to a monolithic design where all components live within the same process and can communicate directly, microservices may be distributed across a cluster of servers. There are two basic ways of communicating between microservices: **Synchronous** and **Asynchronous**



**Synchronous or Request/Response:** 
---
In this method, a service directly invokes another one by sending a request and waiting for a response. For example, when a user updates their address in the profile, the user service sends a PUT request to the billing service so that the billing address updates accordingly.

**Asynchronous or Publish/Subscribe:** 
---
Also known as **event-based** architecture, in this method, a service implicitly invokes another service by publishing an event that the other service is watching for. For example, when a customer makes a payment, the payment microservice publishes an event, and the shipping service that is watching for that event starts the shipment process. 

The problem occurs when we try to solve complex communication requirements by building a complex message bus for routing messages between services. This means the bus is configured or scripted to handle different communication scenarios between services. 

But the best way to handle asynchronous communication is to let the endpoints that produce and consume messages be smart, but the pipe between them to be dumb. In other words, let logic be centralized in the services and refrain from complex messaging services. 

One of the main benefits of the microservices architecture is the ability to develop and deploy each service without conflicting with other parts of the system. Building smart endpoints and dumb pipes helps to reach this goal by encapsulating the logic of consumption of incoming requests and publishing outgoing events inside the service. 

This principle also helps when we need our system to scale up. Another service can join the dumb pipeline and start consuming and publishing messages immediately.