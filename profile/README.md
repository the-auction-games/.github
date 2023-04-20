# Introduction
The Auction Games is an online application that utilizes microservice architecture. It offers a highly scalable and effective platform for listing, bidding, or purchasing auctions. Altogether, this project is comprised of a front-end web application with 4 back-end REST APIs. I took on this project to gain hands-on experience with microservices and container orchestration.  
Here is the microservice breakdown:  
-	Account Microservice (API for account registration and validation)
-	Auction Microservice (API for auction logic such as bidding)
-	Activity Microservice (API for logging and displaying application activity)
-	Session Microservice (API for tracking active user sessions)
-	Front-End Microservice (Angular application utilizing previously mentioned APIs)

# Functional Requirements
Below is a list of all the functional requirements of the project:
-	Account Registration
-	Account Sign In / Sign Out
-	Auction Creation
-	Auction Modification
-	Auction Deletion
-	Auction Bidding
-	Auction Purchasing
-	Auction Marketplace (Search, Sort, Filter)
-	Activity Creation
-	Activity Retrieval (Global, Personal)
-	Client Session Creation
-	Client Session Validation
-	Client Session Timeout

# Non-Functional Requirements
Below is a list of the non-functional requirements:
-	Daily Backups (at midnight) to Drop Box

# Tools and Technologies
Here are all of the tools and technologies used in The Auction Games:
-	Java
-	Spring Boot (Full-stack Framework for Java Applications)
-	JavaScript / TypeScript
-	Express (Back-end web application framework for Node)
-	Angular (Front-end web application framework for JavaScript)
-	HTML / CSS
-	Rust
-	Rocket (Rust Framework for creating APIs)
-	MongoDB (Auction Database)
-	PostgreSQL (Account & Activity Database)
-	Redis (Session Cache)
-	Dapr (Service Invocation and State Storage Management)
-	Zipkin (Transaction Tracing)
-	Docker (Containerization)
-	Kubernetes (Container Orchestration)
-	AWS EKS (Amazon’s Elastic Kubernetes Service)  

I had little to no experience in most of these tools and technologies. For example, I used Rust and the Rocket framework to get hands-on experience with the Rust programming language. Additionally, I utilized Dapr, Zipkin, Docker, and Kubernetes to gain experience in microservice development.

# Technical Approach
From a technical standpoint, the overarching application was split into its key components: the user interface, accounts, auctions, activity, and sessions. Each back-end API was assigned a database for storing their corresponding data. Additionally, every microservice is assigned a Dapr sidecar for service invocation and state storage management. This application was deployed to Amazon’s Elastic Kubernetes Service for public access.  

Here is an architecture design for AWS EKS:  

![alt text](https://github.com/the-auction-games/.github/blob/main/profile/EKS%20Architecture.png)

As seen in the diagram, all connections flow from the client to an AWS load balancer and then to the ingress controller. This controller then routes the client’s request to the corresponding web application, backend API, or the tracing application known as Zipkin. Altogether, this creates a seamless and scalable experience for the client.

# Risks and Challenges
Before starting development, I ran into a few risks with the project. Before work I had no prior experience or knowledge with Rust, Dapr, Zipkin, Docker, Kubernetes or AWS. However, with consistent research and multiple proof-of-concepts, I was able to successfully create a working Kubernetes cluster with all of these features. Each proof-of-concept I developed was responsible for proving each feature or component in the overall application was applicable to the task I originally assumed it was capable of accomplishing.

# Issues
The Session API presently has one issue: users can trick it into thinking they are other accounts, gaining access to anyone’s account if they know some of the account’s public information. The next iteration of the Session API will resolve this issue with the help of the Account API. The Account API will utilize the Session API and provide a valid session token after successful account authentication. This will prevent anyone from gaining session tokens without the account’s credentials.

# Deployment
Click on the ‘Repositories’ tab to view deployment options with Docker and Kubernetes.
-	docker-compose (Deploy with docker compose locally)
-	kubernetes (Deploy onto local Kubernetes cluster)
-	kubernetes-aws (Deploy to Amazon’s EKS platform)
