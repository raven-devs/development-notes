# Sync vs Async Communication

## Sync Communication

Services communicate with each other using direct requests.

Pros: Conceptually easy to understand!
Cons: Introduces a dependency between services.
Cons: If any inter-service request fails, the overall request fails.
Cons: The entire request is only as fast as the slowest request.
Cons: Can easily introduce webs of requests.

## Async Communication

Services communicate with each other using events.

Pros: It has zero dependencies on other services.
Pros: It is extremely fast.
Cons: Data duplication.
Cons: Harder to understand.
