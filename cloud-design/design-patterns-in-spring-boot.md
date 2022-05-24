# Design Patterns for microservices

> High Level discussion with **problem**, **solution**, **requirements** for solutions

### Service discovery
#### Problem

How can clients find microservices and their instances?

Microservices instances are typically assigned dynamically allocated IP addresses when they start up, for example, when running in containers. This makes it difficult for a client to make a request to a microservice that, for example, exposes a REST API over HTTP.

#### Solution


Add a new component – a service discovery service – to the system landscape, which keeps track of currently available microservices and the IP addresses of its instances.

#### Solution requirements

- Automatically register/unregister microservices and their instances as they come and go.
- The client must be able to make a request to a logical endpoint for the microservice. The request will be routed to one of the microservices available instances.
- Requests to a microservice must be load-balanced over the available instances.
- We must be able to detect instances that are not currently healthy; that is, requests will not be routed to them.

**Implementation notes:** As we will see, this design pattern can be implemented using two different strategies:

- Client-side routing: The client uses a library that communicates with the service discovery service to find out the proper instances to send the requests to.
- Server-side routing: The infrastructure of the service discovery service also exposes a reverse proxy that all requests are sent to. The reverse proxy forwards the requests to a proper microservice instance on behalf of the client.



### Edge server
### Reactive microservices
### Central configuration
### Centralized log analysis
### Distributed tracing
### Circuit Breaker
### Control loop
### Centralized monitoring and alarms
