---
title: "Serverless"
enableToc: true
---
## What is Serverless
Serverless computing is a method of providing backend services on an "as used" basis. 
Rather than allocating an entire machine or allocating resources for a server, serverless computing only allocates the necessary resources when called for. 

As developers usually reserve fixed amounts of server space to be prepared for spikes in traffic there is often wasted server resources that is being paid for and not utilised. Therefore using a serverless approach results in cost saving as when the app is not being used then no computing resources are being used. 

Serverless applications can also save time for developers as they do not need to manage capacity planning, configurations, maintenance, fault tolerance or scaling. Note that serverless applications are unable to persist data in memory and therefore need to store results in storage. 

Serverless providers often offer Function as a Service platforms (FaaS) which often charge by compute time. 

One of the drawbacks for serverless applications are cold starts. The concept of serverless involves not allocating resources when they're not needed and therefore when a function has not been called in a while the provider will shut down the function to save resources. The next call for that function will require the provider to start a server and begin hosting that function again which adds significant latency.


#### Serverless Products
- Cloudflare Workers
- AWS Lambda