<a name="br1"></a> 

**E-learning Applicaꢀon**

**(Post & comment & reation Microservice)**


<a name="br2"></a> 

**Introducꢀon:**

The E-learning applicaꢀon serves as a tool that aids teaching organizaꢀons by

facilitaꢀng teacher-student communicaꢀon and providing easy access to

educaꢀonal materials for students. The system was developed using Microservice

architecture, which ensures the independence of all system components.

The applicaꢀon is built using Spring Boot, RabbitMQ, and MongoDB, and is

containerized using Docker for easy deployment. The project is developed using

agile project management techniques and is divided into several phases, including

planning and requirements gathering, microservices design and implementaꢀon,

API gateway implementaꢀon, RabbitMQ integraꢀon, MongoDB database design

and implementaꢀon, and unit tesꢀng. In this report, this document comprises the

secꢀon containing Posts & Comments services that students and teachers use for

asking quesꢀons or sharing materials.

The following diagram shows the systems, applicaꢀons, and users that are

considered in the scenario with minimum technical details.

*Figure 1 Business architecture (Level 0)*



<a name="br3"></a> 

**Microservices Architecture:**

The E-learning applicaꢀon project is built using a microservices architecture,

which allows for greater scalability and robustness of the applicaꢀon. The

microservices architecture consists of several independent services that

communicate with each other through APIs or message broker. The Post and

Comment microservices are two of the main microservices in the applicaꢀon,

responsible for creaꢀng, retrieving, updaꢀng, and deleꢀng posts and comments,

respecꢀvely.

The following diagram goes into the detailed features and funcꢀons of each

component in the business architecture.

*Figure 2 Technical architecture (Level 1)*

**System Components**

**1. Post Microservice:**

The Post microservice is responsible for managing posts in the applicaꢀon. It

consists of several components, including a controller, enꢀꢀes, conﬁguraꢀon, and

repositories. The controller is responsible for handling HTTP requests related to

posts, such as creaꢀng, retrieving, updaꢀng, sharing, and deleꢀng posts. The

enꢀꢀes represent the data models used in the microservice, including the Post



<a name="br4"></a> 

and User classes. The conﬁguraꢀon deﬁnes the conﬁguraꢀon seꢁngs for the

microservice, such as the database connecꢀon and the message queue seꢁngs.

The repositories are responsible for accessing and manipulaꢀng Post enꢀꢀes in

the database.

Furthermore, the Post microservice establishes communicaꢀon with reacꢀon

services to fetch reacꢀons associated with the post and with comment services to

retrieve all comments related to the post. This communicaꢀon is achieved by

uꢀlizing a message broker known as RabbitMQ.

**Service Acꢀons:**

• Create a new post for course discussions.

• Edit and delete your own posts.

• View all posts related to a speciﬁc course.

• Receive noꢀﬁcaꢀons when your post is edited or deleted.

• Add, edit, and delete comments on posts.

• Receive noꢀﬁcaꢀons when a new comment is added to your post or a post

you commented on.

**2. Comment Microservice:**

The Comment microservice is responsible for managing comments in the

applicaꢀon. It consists of several components, including a controller, enꢀꢀes,

conﬁguraꢀon, and repositories. The controller is responsible for handling HTTP

requests related to comments, such as creaꢀng, retrieving, updaꢀng, and deleꢀng

comments. The enꢀꢀes represent the data models used in the microservice,

including the Comment and User classes. The conﬁguraꢀon deﬁnes the

conﬁguraꢀon seꢁngs for the microservice, such as the database connecꢀon and

the message queue seꢁngs. The repositories are responsible for accessing and

manipulaꢀng Comment enꢀꢀes in the database.



<a name="br5"></a> 

**Service Acꢀons:**

• Create a new comment on a speciﬁc post.

• View all comments for a parꢀcular post.

• View a speciﬁc comment by its ID.

• Update the content of a comment.

• Delete a comment.

• Retrieve the number of likes, loves, and angry counts for a comment.

**3. Reacꢀon Microservice:**

The Reacꢀon microservice is a component of your overall system architecture that

is responsible for handling reacꢀons or senꢀments associated with posts and

comments. It allows users to express their emoꢀons or opinions towards speciﬁc

content, such as liking, loving, or expressing other reacꢀons. The purpose of the

Reacꢀon microservice is to manage the various types of reacꢀons that users can

have on posts and comments and keep track of the counts for each reacꢀon type.

It provides an API that allows other microservices or components to interact with

it to retrieve reacꢀon counts, update reacꢀons, or retrieve the overall senꢀment

associated with posts or comments.

**Service Acꢀons:**

• Managing Reacꢀon Types: The microservice deﬁnes the various types of

reacꢀons that users can express, such as likes, loves, angry, or any other

custom reacꢀons. It maintains a list of available reacꢀon types.

• Storing Reacꢀons: The microservice stores the reacꢀons made by users for

speciﬁc posts or comments. It tracks the type of reacꢀon, and the

associated post or comment ID.

• Counꢀng Reacꢀons: The microservice calculates and maintains the counts

for each reacꢀon type associated with posts or comments. It keeps track of

the number of likes, loves, angry, etc., for each post or comment.

• Get count of total reacꢀons (likes, loves, angry,...., etc) on speciﬁc post or

comment.



<a name="br6"></a> 

**4. API Gateway:**

The E-learning applicaꢀon uꢀlizes the API Gateway as its primary access point,

handling the task of direcꢀng client requests to the relevant microservices. To

achieve this, the API Gateway uses Eureka server, which oﬀers rouꢀng, ﬁltering,

and load balancing capabiliꢀes for microservices.

**5. RabbitMQ Integraꢀon:**

The E-learning applicaꢀon uꢀlizes RabbitMQ for message exchange among

microservices, enabling reliable and orderly communicaꢀon between them.

RabbitMQ plays a crucial role in managing the delivery of messages between

microservices. In our system it is used to noꢀfy post service that a comment adds

to and give him post id which increases the number of comments in post and

make it very easy to get all comments related to this post.

**6. MongoDB Database:**

The E-learning applicaꢀon uses MongoDB as its NoSQL database to store and

retrieve applicaꢀon data. MongoDB is a document-oriented database that

provides high scalability and performance for applicaꢀons with large amounts of

data. The database schema is designed to opꢀmize the performance of the

applicaꢀon, with each microservice having its own collecꢀon in the database.

**7. Unit Test:**

Unit Tesꢀng is an essenꢀal pracꢀce to ensure the quality and reliability of

individual microservices. Unit tests are designed to verify the correctness of a

speciﬁc unit or component of code in isolaꢀon, without considering its

dependencies on other services or components. In this architecture, we can

discover individual unit tests integrated in the service that assess all the

funcꢀonaliꢀes of the microservice and prove the dependence of each

microservice.



<a name="br7"></a> 

**8. Containerizaꢀon:**

Docker is employed to containerize the applicaꢀon, enabling easier deployment

and management. By uꢀlizing Docker, the applicaꢀon and its dependencies are

encapsulated within self-contained containers. These containers can be executed

on any plaꢂorm that supports Docker, streamlining the deployment process. The

applicaꢀon is parꢀꢀoned into mulꢀple Docker containers, with each microservice

and the API Gateway having its dedicated container.

**Class Diagram:**

The class diagram for the Post and Comment microservices is shown below:

The diagram shows the relaꢀonships between the diﬀerent classes in the

microservices, including the Comment, User, Post and reacts classes.



<a name="br8"></a> 

**Deployment Architecture (Level 2):**

Deployment architecture which provides the details of how the actual deployment

looks like in a data center or a cloud infrastructure:

*Figure 3 Deployment architecture (Level 2)*

**Conclusion:**

The E-learning applicaꢀon project is designed and implemented using a

microservices architecture, which oﬀers several advantages like scalability,

robustness, and ﬂexibility. The architecture comprises several independent

services, with the Post and Comment microservices being the main components

responsible for managing posts and comments, respecꢀvely. Each microservice is

carefully designed with various components, including controllers, enꢀꢀes,

conﬁguraꢀon, and repositories, to handle speciﬁc funcꢀonaliꢀes eﬃciently. The

Post microservice allows users to create, edit, delete, and view posts related to

course discussions, while the Comment microservice enables users to interact

with comments on posts, including adding, updaꢀng, and deleꢀng comments.

To manage communicaꢀon between microservices, the applicaꢀon employs

RabbitMQ, a message broker that facilitates reliable and orderly message

exchange. The API Gateway acts as the primary access point, direcꢀng client

requests to the relevant microservices using Eureka server for rouꢀng, ﬁltering,

and load balancing. The applicaꢀon uses MongoDB as its NoSQL database,



<a name="br9"></a> 

ensuring high scalability and performance, with each microservice having its

collecꢀon.

Unit tesꢀng is implemented to maintain the quality and reliability of individual

microservices, ensuring they funcꢀon correctly in isolaꢀon. Moreover, the

applicaꢀon leverages Docker for containerizaꢀon, simplifying deployment and

management. Docker containers encapsulate the applicaꢀon and its

dependencies, making it portable and easily deployable on any plaꢂorm

supporꢀng Docker. Each microservice and the API Gateway are divided into

separate Docker containers, facilitaꢀng a streamlined and eﬃcient deployment

process.

Overall, the microservices architecture, in conjuncꢀon with the use of RabbitMQ,

MongoDB, unit tesꢀng, and Docker containerizaꢀon, contributes to the overall

success of the E-learning applicaꢀon by providing a scalable, reliable, and easily

deployable plaꢂorm for online learning.

