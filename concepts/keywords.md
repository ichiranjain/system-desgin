# Keywords
---
Table of Contents
---
1. [Stateful vs Stateless](#stateful-vs-stateless)
2. [Load Balancer vs Reverse Proxy](#load-balancer-vs-reverse-proxy)
3. 

### Stateful vs Stateless
##### Stateful
```
Stateful is where the server stores the state of the user who is using a service.

User A --->X Server 1 -
                        -
                          -
User B ---> Server 2  - - - - DB 
                          -
                        -
User C ---> Server 3  -

In this case, 
- if User A will store the state in Server 1.
- while checking out some products from the website the server 1 goes down.
- Now Load balance will redirect to other servers but the state will be lost. (User 1 will have to add products to cart again)


Disadvantages:

- Availibility issues. (cannot connect to other server as state is lost.) (also traffic increases)
- Scalability is a concern. (state has to bbe replicated.
```

##### Serverless:
``` 
state is not maintained in server. We can maintain in  shared location, cache or db.

            __________
User A ---> |         |       __________
            |         |       |         |
            |         |       |         |
User B ---> |Load     |------>| Web Tier|--------> Shared Storage (NoSql DB - scale horizontally)
            |Balancer |       |         |
            |         |       |_________|\
User C ---> |_________|                   \
                                           \
                            		   Cache (Memcache, Redis)


Cloud Context:

When choosing service, 
- stateful or service
- If for eg. install DB (in VM) it require persistence. So Stateful as you will need information of DB to be store in local drive.
- Microservices are designed mostly stateless. Examples: Kubernetes, Cloud functions like Azure. So accroding to traffic the service will scale out or scale in. 

Always ask question regarding how we want to maintain the state?

```


