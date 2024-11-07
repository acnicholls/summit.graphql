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

![Securing Queries AI can call](./images/AI-Query-Control.png.png)

## Keynote : Exploring Apollo's new Products, a deep dive

- graphql can be an abstraction between UI and API, which helps integrations for NEW fragments of the graph, or seamless deployments
- the conversion journey has challenges, but the overall benefits outweigh the cost of those challenges.
- @router and @connector have transforms built right in.
- @router - reduces the SDLC steps required
  ![SDLC Steps Reduction](./images/Endpoint-Creation-Steps-Reduction.png)

## What's new in Apollo Client

When you're ready, definitely check out our Swift & Apollo courses on Odyssey! https://www.apollographql.com/tutorials/apollo-ios-swift-part1

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
