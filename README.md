# Java Backend Portfolio

## About
This repository is a consolidation of all monthly sprint project assignments I completed over nine months as a student at BloomTech.

A high level description of each project is outlined below with links to the project's GitHub repository.

The specific assignments for each project can be found in the sub-repository's README or DESIGN_DOC

There is also one sprint project left off this list because it focused more on the frontend. [The project repository can be found here](https://github.com/Celtics-Engine/Celtics-Frontend)

---

> ## [Advertising Predicate Evaluator](https://github.com/grauulzz/advertising-predicate-evaluator)
> Description: 
>
> Designed backend architecture that can select an ad for a given user profile based off which targeting group the user belongs to. This was accomplished by evaluating a list of user targeting predicates against a group of targetable users and then [sorting the results by click-through rate](https://github.com/grauulzz/advertising-predicate-evaluator/blob/f91d927fd28b98daf0a15633fac92b733453eabb/src/com/amazon/ata/advertising/service/businesslogic/AdvertisementSelectionLogic.java#L45). All the data required to execute this correctly can end up being very large. With this in mind, the service was designed to be scalable and performant, with the ability to [process the predicates in parallel](https://github.com/grauulzz/advertising-predicate-evaluator/blob/f91d927fd28b98daf0a15633fac92b733453eabb/src/com/amazon/ata/advertising/service/targeting/TargetingEvaluator.java#L24). If necessary, the service can wait for [response data to finish processing](https://github.com/grauulzz/advertising-predicate-evaluator/blob/f91d927fd28b98daf0a15633fac92b733453eabb/src/com/amazon/ata/advertising/service/activity/GenerateAdActivity.java#L44) elsewhere before returning a generated ad. This functionality was implemented with Java CompletableFuture objects.
>
> - Gained experience handling big data concurrently
> - Implemented asynchronous handling of request and response objects
> - [Composed future object chaining](https://github.com/grauulzz/advertising-predicate-evaluator/blob/f91d927fd28b98daf0a15633fac92b733453eabb/src/com/amazon/ata/advertising/service/future/FutureUtils.java#L49)
> - Worked with dependency injection at a large scale with Google Dagger
> - Ensured proper communications between multiple data access objects
> - Assembled complex database queries from incoming request objects
> - Handled optional values in a relational database 
> - Optimized network I/O performance with concurrent processing 
> - Effectively passed functionality throughout the application using functional programming techniques 
> - Designed a nifty [console logger]([https://github.com/grauulzz/advertising-predicate-evaluator/blob/f91d927fd28b98daf0a15633fac92b733453eabb/src/com/amazon/ata/advertising/service/future/FutureMonitor.java#L20](https://github.com/grauulzz/advertising-predicate-evaluator/blob/f91d927fd28b98daf0a15633fac92b733453eabb/src/com/amazon/ata/advertising/service/future/FutureUtils.java#L64)) to keep track of various future objects stages and execution times
> - Followed thread safety best practices 

---

> ## [Kindle Publishing Service](https://github.com/grauulzz/kindle-publishing-service) 
> Description:
>
> Implemented logic for a service that can publish a book to a Kindle account. The service accounts for both an Author account, and a User account. While using the database effectively, the service is able to handle multiple concurrent requests using a mix of load balancing and Java CompletableFuture Objects.
> 
> - Distributed HTTP requests with an Application Load Balancer using AWS EC2
> - Integrated Docker with AWS EC2 and configured the service to run a container for each instance needed by the load balancer
> - Routed incoming requests to the Load Balancer using AWS API Gateway
> - Implemented web layer using Spring MVC
> - Integrated redirection and forwarding of API calls with Spring MVC controllers 
> - Scraped HTTP endpoint metrics with Micrometer and Prometheus
> - Setup I/O performance monitoring with Micrometer and Prometheus 
> - Handled concurrent HTTP requests using Java CompletableFuture Objects, Stacks, and Queues
>

---

> ## [Music Playlist Api](https://github.com/grauulzz/music-playlist-api) 
> Description:
>
> Created an API with GET, POST, DELETE, and UPDATE functionality. The Application also integrates with AWS DynamoDB for storage of user's data. 
>
> - Gained experience programming a RESTful API from scratch
> - Provided DynamoDB utilities for CRUD operations with AWS lambda functions
> - Setup table structure and data model for DynamoDB 
> - Worked extensively with DynamoDB range and hash key attributes
> - Configured endpoints for playlist retrieval and creation
> - Wrote unit tests which required mocking the database
>

---

> ## [Sustainable Shipping Service](https://github.com/grauulzz/sustainable-shipping-service)
> Description:
>
> Implemented a service that can calculate the cost of a shipment based on the weight of the shipment and the material used for packaging the shipment. The finished product provides modular shipment recommendations to the shipping fulfillment center.
>
> - Gained experience implementing essential data structures
> - Worked with hash table buckets and object hashing to efficiently store and retrieve data
> - Implemented hash functions and hash table collision resolution
> - Created data structures for shipment cost calculations that could implement common functionality in a modular way (calculations of different materials)
> - Structured Java class Inheritance and hierarchy 
> - Learned how to preserve an object's internal state while exposing only what's necessary
> - Created custom Exception classes for specific error conditions
> - Used interface and abstract class design patterns to properly structure java classes  
>

---

> ## [Promise Fulfillment Client](https://github.com/grauulzz/promise-fulfillment-client)
> Description:
>
> Implemented a service that can fulfill orders for a customer and communicate it through a "promise" back to the client (in this case the client was a call center CLI). This was one of the first projects in the course, and was a great opportunity to learn about how a backend can maintain a high level of abstraction between servers and clients.
> - Worked extensively with java Collections and iterating over them
> - Handled communications between data access objects and business logic classes 
> - Followed best practice Builder design patterns
> - Implemented Comparator and Comparable Interfaces to sort order objects by comparable traits
> - Learned when a collection should be mutable or immutable
>

---

> ## [Text Adventure (Java Fundamentals)](https://github.com/grauulzz/java-fundamentals-text-adventure) 
> Description:
>
> Implemented a text adventure game that allows the user to explore a world in text format. The game is designed to be played in a terminal window. The user can move around the world and interact with items, places, and creatures. This was the first project of the course, and was a lot of fun.
>
> - Learned Java fundamentals and object-oriented design principles 
>
