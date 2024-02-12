---
title: Event Driven Architecture
enableToc: true
tags:
  - Pub/Sub
---
# Event Driven Architecture (EDA)
## What is EDA
An event is a change in state, like a change in inventory volume for an e-commerce store when something has been purchased. Event driven architecture uses events to trigger and communicate between services in distributed systems.

Event driven systems typically consist of three main components. 
**Event Producer**
- Detects and creates the event then forwards it to the Event Broker
**Event Broker**
- The event broker is responsible for transferring these events to the correct Event Subscribers
- Event subscribers can consist of different services so some services will not need to consume every event.
**Event Consumers**
- Event subscribers receive the event and perform some action in response

The Producer and Consumers are decoupled. The producer does not need to know anything about the Consumers or how many there are. More consumers can subscribe to the events and if consumer services go down it will not affect the events being published. This is also known as the Publisher Subscriber Model (Pub/Sub). 

## When to use EDA
 EDA is useful when a lot of services need to response to an event. The event broker can fanout the event to the consumers to process events in parallel. 
 
 A popular example is when a user purchases something off an e-commerce platform. The purchase event will trigger actions such as
 - Payment processing service processes the transaction and checks that the sale is successful
 - Database needs to update inventory value to account for sale 
 - Attach order invoice to customer account purchase history
Perhaps email receipts were not implemented yet but an email service can be developed independently and listen for a customer purchase event to create this feature. 

Other examples include
- Social media posting
	- Notify followers whenever new content is posted
- Logistics, Resource Monitoring and alerts
	- Postage tracking
		- Event every time a package arrives in a new location
	- Food delivery tracker
		- Food being made, food waiting for pickup, on the way, arrived etc.
-  IoT devices
	-  Data ingestion and analytics
		- Collect data from a variety of sensors and trigger events
	- Smart Home Automations

Popular event queues used are
- Apache [[notes/Kafka|Kafka]]
- Amazon Simple Queue System (SQS)

# Resources
- [What is an Event-Driven Architecture - AWS](https://aws.amazon.com/event-driven-architecture/#:~:text=An%20event%2Ddriven%20architecture%20uses,on%20an%20e%2Dcommerce%20website.)
- [Event Driven Architecture - altexsoft](https://www.altexsoft.com/blog/event-driven-architecture-pub-sub/)
- [Pub-Sub Messaging - geekculture](https://medium.com/geekculture/system-design-basics-pub-sub-messaging-88dfd98e67b7)
- [Complete Guide to Event Driven Architecture - seetharamugn](https://medium.com/@seetharamugn/the-complete-guide-to-event-driven-architecture-b25226594227)
