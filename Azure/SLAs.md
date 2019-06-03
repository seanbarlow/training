# SLAs

## Performance Targets

An SLA defines performance targets for an Azure product or service. The performance targets that an SLA defines are specific to each Azure product and service. For example, performance targets for some Azure services are expressed as uptime guarantees or connectivity rates.

## Uptime and Connectivity Guarantees

A typical SLA specifies performance-target commitments that range from 99.9 percent ("three nines") to 99.999 percent ("five nines"), for each corresponding Azure product or service. These targets can apply to such performance criteria as uptime or response times for services.

| SLA %  | Downtime per week | Downtime per month | Downtime per year |
| ------ | ----------------- | ------------------ | ----------------- |
| 99     | 1.68 hours        | 7.2 hours          | 3.65 days         |
| 99.9   | 10.1 minutes      | 43.2 minutes       | 8.76 hours        |
| 99.95  | 5 minutes         | 21.6 minutes       | 4.38 hours        |
| 99.99  | 1.01 minutes      | 4.32 minutes       | 52.56 minutes     |
| 99.999 | 6 seconds         | 25.9 seconds       | 5.26 minutes      |

## Composing SLAs

When combining SLAs across different service offerings, the resultant SLA is a called a Composite SLA. The resulting composite SLA can provide higher or lower uptime values, depending on your application architecture.

## Calculating downtime

Consider an App Service web app that writes to Azure SQL Database. These Azure services currently have the following SLAs:

Image representing Web app and its SLA uptime value of 99.95 percent and a SQL database and its SLA value of 99.99 percent.

In this example, if either service fails the whole application will fail. In general, the individual probability values for each service are independent. However, the composite SLA value for this application is:

99.95 percent × 99.99 percent = 99.94 percent

This means the combined probability of failure is higher than the individual SLA values. This isn't surprising, because an application that relies on multiple services has more potential failure points.

Conversely, you can improve the composite SLA by creating independent fallback paths. For example, if SQL Database is unavailable, you can put transactions into a queue for processing at a later time.

Image representing Web app and its SLA uptime value of 99.95% and SQL database and its SLA value of 99.99%.

With this design, the application is still available even if it can't connect to the database. However, it fails if both the database and the queue fail simultaneously.

If the expected percentage of time for a simultaneous failure is 0.0001 × 0.001, the composite SLA for this combined path of a database or queue would be:

1.0 − (0.0001 × 0.001) = 99.99999 percent

Therefore, if we add the queue to our web app, the total composite SLA is:

99.95 percent × 99.99999 percent = ~99.95 percent

Notice we've improved our SLA behavior. However, there are trade-offs to using this approach: the application logic is more complicated, you are paying more to add the queue support, and there may be data-consistency issues you'll have to deal with due to retry behavior.

## Application SLA
You can use SLAs to evaluate how your Azure solutions meet business requirements and the needs of your clients and users. By creating your own SLAs, you can set performance targets to suit your specific Azure application. This approach is known as an Application SLA.

## App Requirements

Building an efficient and reliable Azure solution requires knowing your workload requirements. You can then select Azure products and services, and provision resources according to those requirements. It's important to understand the Azure SLAs that define performance targets for the Azure products and services within your solution. This understanding will help you create achievable Application SLAs.

In a distributed system, failures will happen. Hardware can fail. The network can have transient failures. It's rare for an entire service or region to experience a disruption, but even this must be planned for.

## Resiliency
Resiliency is the ability of a system to recover from failures and continue to function. It's not about avoiding failures,but responding to failures in a way that avoids downtime or data loss. The goal of resiliency is to return the application to a fully functioning state following a failure. High availability and disaster recovery are two crucial components of resiliency.

When designing your architecture you need to design for resiliency, and you should perform a Failure Mode Analysis (FMA). The goal of an FMA is to identify possible points of failure and to define how the application will respond to those failures.

## Cost and complexity vs. high availability

Availability refers to the time that a system is functional and working. Maximizing availability requires implementing measures to prevent possible service failures. However, devising preventative measures can be difficult and expensive, and often results in complex solutions.

As your solution grows in complexity, you will have more services depending on each other. Therefore, you might overlook possible failure points in your solution if you have several interdependent services.

The risk of potential downtime is cumulative across various SLA levels, which means that complex solutions can face greater availability challenges. Therefore, how critical high-availability is to your requirements will determine how you handle the addition of complexity and cost to your application SLAs.

## Considerations for defining application SLAs

1. If your application SLA defines four 9's (99.99%) performance targets, recovering from failures by manual intervention may not be enough to fulfill your SLA. Your Azure solution must be self-diagnosing and self-healing instead.
2. It is difficult to respond to failures quickly enough to meet SLA performance targets above four 9's.
3. Carefully consider the time window against which your application SLA performance targets are measured. The smaller the time window, the tighter the tolerances. If you define your application SLA as hourly or daily uptime, you need to understand these tighter tolerances might not allow for achievable performance targets.
