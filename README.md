# Java Backend Portfolio

## About
This repository is a consolidation of all monthly sprint project assignments I completed over nine months as a student at BloomTech.

A high level description of each project is outlined below with links to the project's GitHub repository.

The specific assignments for each project can be found in the sub-repository's README or DESIGN_DOC

There is also one sprint project left off this list because it focused more on the frontend. [The project repository can be found here](https://github.com/grauulzz/celtics-engine-frontend-team-project)

---

> ## [Advertising Predicate Evaluator](https://github.com/grauulzz/advertising-predicate-evaluator)
> Description: 
>
> Designed backend architecture that can select an ad for a given user profile based off which targeting group the user belongs to. [Generating the advertisement](https://github.com/grauulzz/advertising-predicate-evaluator/blob/f91d927fd28b98daf0a15633fac92b733453eabb/src/com/amazon/ata/advertising/service/businesslogic/AdvertisementSelectionLogic.java#L80-L97) is accomplished by evaluating a list of user targeting predicates against a group of targetable users and then [sorting the results by click-through rate](https://github.com/grauulzz/advertising-predicate-evaluator/blob/f91d927fd28b98daf0a15633fac92b733453eabb/src/com/amazon/ata/advertising/service/businesslogic/AdvertisementSelectionLogic.java#L45-L51). All the data required to execute this correctly can end up being very large. With this in mind, the service was designed to be scalable and performant, with the ability to [process the predicates in parallel](https://github.com/grauulzz/advertising-predicate-evaluator/blob/f91d927fd28b98daf0a15633fac92b733453eabb/src/com/amazon/ata/advertising/service/targeting/TargetingEvaluator.java#L24-L35). If necessary, the service can wait for [response data to finish processing](https://github.com/grauulzz/advertising-predicate-evaluator/blob/f91d927fd28b98daf0a15633fac92b733453eabb/src/com/amazon/ata/advertising/service/activity/GenerateAdActivity.java#L44-L56) elsewhere before returning a generated ad. This functionality was implemented with Java CompletableFuture objects.
>
> - Gained experience handling big data concurrently
> - Implemented asynchronous handling of request and response objects
> - [Composed future object chaining](https://github.com/grauulzz/advertising-predicate-evaluator/blob/f91d927fd28b98daf0a15633fac92b733453eabb/src/com/amazon/ata/advertising/service/future/FutureUtils.java#L49-L56)
> - Worked with dependency injection at a large scale with Google Dagger
> - Ensured proper communications between multiple data access objects
> - Handled optional values in a relational database 
> - Optimized network I/O performance with concurrent processing 
> - Effectively passed functionality throughout the application using functional programming techniques 
> - Designed a nifty [console logger](https://github.com/grauulzz/advertising-predicate-evaluator/blob/f91d927fd28b98daf0a15633fac92b733453eabb/src/com/amazon/ata/advertising/service/future/FutureUtils.java#L64) to keep track of various future objects stages and execution times
> - Followed thread safety best practices 

---

> ## [Kindle Publishing Service](https://github.com/grauulzz/kindle-publishing-service) 
> Description:
>
> Implemented logic for a service that can publish a book to a Kindle account. The service accounts for both an Author account, and a User account. Integrated with DyanmoDB, the service is designed to be scalable, with ability to process a [queue of publishing requests](https://github.com/grauulzz/kindle-publishing-service/blob/3e738c21bc4b11d13e42cc527f0e67632a500c28/src/com/amazon/ata/kindlepublishingservice/publishing/BookPublishingManager.java#L8-L44)
>
> - Assembled [DynamoDB queries from incoming request objects](https://github.com/grauulzz/kindle-publishing-service/blob/3e738c21bc4b11d13e42cc527f0e67632a500c28/src/com/amazon/ata/kindlepublishingservice/activity/SubmitBookForPublishingActivity.java#L53-L82)
> - Distributed HTTP requests with an Application Load Balancer using AWS EC2
> - Integrated and configured Docker with AWS EC2  
> - Setup the service to run the Docker container for each instance needed by the Load Balancer
> - Routed HTTP requests using RESTful best practices
> - Implemented [Spring RESTful controllers](https://github.com/grauulzz/kindle-publishing-service/blob/3e738c21bc4b11d13e42cc527f0e67632a500c28/src/com/amazon/ata/kindlepublishingservice/controllers/Controller.java#L32) to convert the payload of incomming requests into an internal data structure 
> - Integrated I/O [performance monitoring with Micrometer and Prometheus](https://github.com/grauulzz/kindle-publishing-service/blob/3e738c21bc4b11d13e42cc527f0e67632a500c28/src/com/amazon/ata/kindlepublishingservice/controllers/Controller.java#L36-L47)
> - Preserved order of incomming [HTTP request processing](https://github.com/grauulzz/kindle-publishing-service/blob/3e738c21bc4b11d13e42cc527f0e67632a500c28/src/com/amazon/ata/kindlepublishingservice/publishing/BookPublishTask.java#L47-L93) by implementing a Queue combind with Java CompletableFuture objects 
>

---

> ## [Music Playlist API](https://github.com/grauulzz/music-playlist-api) 
> Description:
>
> Created an API with GET, POST, DELETE, and UPDATE functionality. The Application also integrates with AWS DynamoDB for storage of user's data. 
>
> - Gained experience programming a RESTful API from scratch
> - Provided DynamoDB utilities for CRUD operations with [AWS lambda functions](https://github.com/grauulzz/music-playlist-api/blob/e8946e03ee26a985dad6701fc6fd37c397d55ccd/src/com/amazon/ata/music/playlist/service/lambda/AddSongToPlaylistActivityProvider.java#L13-L38) and dependecy injection
> - Setup table structure and data model for DynamoDB 
> - Worked with unordered hash indexes in DynamoDB with range and hash primary key attributes
> - Implemented [dependecy injection](https://github.com/grauulzz/music-playlist-api/blob/e8946e03ee26a985dad6701fc6fd37c397d55ccd/src/com/amazon/ata/music/playlist/service/dependency/DaoModule.java#L18) on a project from scratch
> - Designed a song order Enum capable of defining [Comparator sorting functionality](https://github.com/grauulzz/music-playlist-api/blob/e8946e03ee26a985dad6701fc6fd37c397d55ccd/src/com/amazon/ata/music/playlist/service/models/SongOrder.java#L13-L61) from arguments passed in
> - Configured AWS APIGateway endpoints for playlist retrieval and creation
> - Wrote unit tests which required mocking the database
> - Designed custom Exception classes for [handling invalid CRUD operations data](https://github.com/grauulzz/music-playlist-api/blob/e8946e03ee26a985dad6701fc6fd37c397d55ccd/src/com/amazon/ata/music/playlist/service/exceptions/PlaylistNotFoundException.java#L6-L45) and invalid [DynamoDB data input](https://github.com/grauulzz/music-playlist-api/blob/e8946e03ee26a985dad6701fc6fd37c397d55ccd/src/com/amazon/ata/music/playlist/service/exceptions/AlbumTrackNotFoundException.java#L7-L46)
>

---

> ## [Sustainable Shipping Service](https://github.com/grauulzz/sustainable-shipping-service)
> Description:
>
> Implemented a service that can calculate the cost of a shipment based on the weight of the shipment and the material used for packaging the shipment. The finished project [provides modular shipment recommendations](https://github.com/grauulzz/sustainable-shipping-service/blob/cc9adacbd7672a257207156ab86d3110af9b6ae5/src/com/amazon/ata/service/ShipmentService.java#L47-L79) to a shipment fulfillment center.
>
> - Gained experience [implementing essential data structures](https://github.com/grauulzz/sustainable-shipping-service/blob/cc9adacbd7672a257207156ab86d3110af9b6ae5/src/com/amazon/ata/dao/PackagingDAO.java#L28-L78) 
> - Worked with hash table buckets and object hashing to efficiently store and retrieve data
> - Implemented hash functions and hash table collision resolution
> - Created an [Interface for shipment cost calculations](https://github.com/grauulzz/sustainable-shipping-service/blob/cc9adacbd7672a257207156ab86d3110af9b6ae5/src/com/amazon/ata/cost/CarbonCostStrategy.java#L12-L35) that provides calculations of the cost of different materials
> - Structured Java class [Inheritance and hierarchy](https://github.com/grauulzz/sustainable-shipping-service/blob/cc9adacbd7672a257207156ab86d3110af9b6ae5/src/com/amazon/ata/types/Box.java#L7-L78) 
> - Learned how to preserve an object's internal state while exposing only what's necessary
> - Created custom Exception classes for specific error conditions
> - Used interface and abstract class design patterns to properly structure java classes  
>

---

> ## [Promise Fulfillment Client](https://github.com/grauulzz/promise-fulfillment-client)
> Description:
>
> Implemented a service that can fulfill orders for a customer and communicate it through a "promise" back to the client (in this case the client was a call center command line interface). This was one of the first projects in the course and was a great opportunity to learn about how a backend can maintain a high level of abstraction between servers and clients.
> - Worked extensively with java Collections and iterating over them
> - Handled communications between data access objects and business logic classes 
> - Followed best practice [Builder design patterns](https://github.com/grauulzz/promise-fulfillment-client/blob/40cd7f79509b4a6a2a74fa0a83039d5f09038efa/src/com/amazon/ata/deliveringonourpromise/deliverypromiseservice/DeliveryPromiseServiceClient.java#L31-L48)
> - Implemented [Comparator Interface](https://github.com/grauulzz/promise-fulfillment-client/blob/40cd7f79509b4a6a2a74fa0a83039d5f09038efa/src/com/amazon/ata/deliveringonourpromise/comparators/PromiseAsinComparator.java#L11-L22) to sort order objects by comparable traits
> - Learned conceptual use of mutability/immutability of collections and objects
>

---

> ## [Text Adventure (Java Fundamentals)](https://github.com/grauulzz/java-fundamentals-text-adventure) 
> Description:
>
> Implemented a text adventure game that allows the user to explore a world in text format. The game is designed to be played in a terminal window. The user can move around the world and interact with items, places, and creatures. This was the first project of the course, and was a lot of fun.
>
> - Learned Java fundamentals and object-oriented design principles 
>
