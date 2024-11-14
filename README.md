# summit.graphql 2024

My notes from the Apollo GraphQL Virtual Summit 2024

## Keynote : The Value of your API Platform, Today and Tomorrow

- apollo is trying to bring graphql into the architecture, not replace other service types (REST, SOAP, etc...)
- use graphql to coordinate how your other APIs are called
- @connectors - new feature in apollo platform offerings
- Apollo Language Server - schema validation/intellisense for GraphQL Schema and Queries
- "Entity Caching" - DOW Jones saw 20-25% decrease in response time, 8-10x reduction in load on underlying services
- "Demand Control" - can limit sub-graph calls based on costs. Tools exist to observe and monitor the query costs
- "Query Planner" - rewrite from JS to Rust (cool). 10x improvement of query plan time. 5.5x less CPU consumption

![Securing Queries AI can call](./images/AI-Query-Control.png)

## Keynote : Exploring Apollo's new Products, a deep dive

- graphql can be an abstraction between UI and API, which helps integrations for NEW fragments of the graph, or seamless deployments
- the conversion journey has challenges, but the overall benefits outweigh the cost of those challenges.
- @router and @connector have transforms built right in.
- @router - reduces the SDLC steps required
  ![SDLC Steps Reduction](./images/Endpoint-Creation-Steps-Reduction.png)

## What's new in Apollo Client

When you're ready, definitely check out our Swift & Apollo courses on Odyssey!
https://www.apollographql.com/tutorials/apollo-ios-swift-part1

- Apollo Client is actually 3 different clients, TS, Swift and Kotlin
- TTL example - https://gist.github.com/bignimbus/ccb1010183447689ac7bc25df022481a
- OSS
- GraphQL Testing Library
- has browser DevTools extensions for debugging
  - has cache explorer (like ReactQuery!!)
- Has IDE extensions

## Turning your graph into a developer platform

Introducing GraphOS!!

![GraphOS Benefits](./images/GraphOS-benefits.png)

- Automate => Measure => Adapt
- Allows for schema versioning with PRs and included Checks (PR Validation)
- Allows for custom checks
- No server required to have a graphql endpoint

## Introducing a native query planner in Apollo Router

- comparison in Expedia - https://github.com/samuelAndalon/query-planner-service-comparison
- 10x reduction in response times
- 2.2 - 5.5x reduction in CPU usage
- can see MASSIVE reduction in RAM usage (2.049 GB => 0.49 MB)
- ![Query Planner Parts - Before Update](./images/Query-Planner-parts.png)
- biggest reason for conversion from JS to Rust is transformation of data between the router (Rust) and the JS Query Planner
- 2nd reason in memory usage and detecting memory used between the two processes

## Fake it 'til You Build it : Navigating GraphQL Mocking Solutions

- allows builders and consumers to collaborate and test experiments together
- allows consumers to validate the contract by mocking data for all + edge case tests

## OneGraph : Indeed as a Platform

how a proof of concept and an API First mandate transformed our culture and led to OneGraph, which provides access to over **200 subgraphs** and serves **120B requests** per month

| Subgraphs | Requests/Month |
| --------- | -------------- |
| 200       | 120 Billion    |

- in the last 6 years have converted from mixed ecosystem to supergraph
- step one was to add graph to each side of their API platform(s)/BFF
- Easily incorporated another client application
- built a lot of validation into build pipelines, etc.
- brought in Apollo engineers to train in-house engineers in the migration to the graph way

<img alt="Indeed Api Platform Then vs Now : Then" src="./images/Indeed_ApiPlatformThen.png" width="40%" />
<img alt="Indeed Api Platform Then vs Now : Now" src="./images/Indeed_ApiPlatformNow.png"  width="40%" />

<hr />
                          Indeed API Numbers Today
<img alt="Indeed Api Platform: Current Numbers" src="./images/Indeed_NumbersNow.png"  width="75%" />
<hr />

## Apollo Language Server: The subgraph DX

- IDE Extensions for building the graph
- very detailed, uses intellisense style comments from the code to provide hints, etc.
- built-in to Apollo products
- aids learning federation due to auto-completion hints!!

## Securing your GraphQL APIs with Apollo: Best practices for authentication and authorization

- built-in to GraphOS
- WIZ has integrated with GraphOS
  - built custom RBAC
  - uses JWT for authorization
  - uses external service for AuthN
  - multi-layer security (Zero-Trust) (AuthN/Federation/Microservice AuthN&AuthZ/Data Security (RLS))
  - prevent DOS attacks by handling query-depth limits https://www.apollographql.com/docs/graphos/routing/security/demand-control
  - schema validation - allow tests to check that sensitive data is redacted as expected, etc.
  - persisted queries and whitelisting allow you to secure the API even more.
  - Apollo took specs from custom directives created by Wiz and they became the standard for future versions, be sure to communicate with your vendor!

## How American Airlines is self-servicing auth with @policy directive, OPA, Backstage and GitHub

main challenge to `@requireScopes`

1. Lack of Reliable Authorization (Authentication is fine, but FGA with only scopes, is meh)
1. Security Concerns
1. Compliance Friction
1. Reduced Developer Velocity

using the `@policy` directive

- allows custom authorization policies, via the co-processor

- HotChocolate Federation Example/Course
  https://www.apollographql.com/tutorials/federation-hotchocolate/01-intro-federation

- How to feed the authorization co-processor
  https://www.apollographql.com/docs/graphos/routing/customization/coprocessor#coprocessor-request-format
