# System Design Key Components

We can Function and Non Functional Requirement

## Functional Requirement:

The following requirements define the core features and behavioral expectations of the system.

### 1.The "Who" (Actors & Permissions)
Before you build a feature, you need to know who is using it.

1. **How many types of users are there?:** In Uber, there are Riders and Drivers. In an E-commerce site, there are Buyers, Sellers, and Admins.
2. **Do we Need Authorization & Authentication**: (Can anyone see this data, or do they need to log in?)


### 2. The "What" (Core Actions)
Focus on the CRUD operations (Create, Read, Update, Delete).

1. **Creation**: How is the data created? Is it user-generated (like a tweet) or system-generated (like a log)?
2. **Retrieval**: How do users find this information? Is it via a search bar, a feed/timeline, or a direct link?
3. **Modification**: Can users edit or delete their content after it's posted? If so, do we need to keep a history (versioning)?


### 3. The "Input/Output" (Data & Format)
1. **What does the data look like?:** Is it simple text, high-resolution images, or streaming video?
2. **Are there any size limits?** Can a user upload a 10GB file, or is the limit 20MB?


### 4. The "Edge Cases" (System Rules)
1. **"What happens when things go wrong?"** If a user tries to book a hotel room that just got taken, do we show an error or a suggestion for another room?
2. **"Are there social features?"** (Do we need likes, comments, or sharing?)
3. **"Is there a notification component?"** (Do we need to send Emails, SMS, or Push Notifications when an event happens?)

## Non-Functional Requirement:
### 1. Scale & Traffic
   1. **DAU/MAU:** Daily Active User/ Monthly Active User
   2. **Peak vs Average Load:** How many request we get in peak time and how many request we get in average time (At time of Black Friday sale)
   3. **Read Write Ratio:** System will be rad more than write, or it will be written more than read (Read Heavy we can have Cache and write heavy we can have message queue)
### 2. Performance
   1. **Latency:** How much time it takes to process a request, or how much time it takes for the system to respond to a request.
   2. **Throughput:** How many request the system can process in a given time frame, or how many request the system can handle per second.
### 3. Availability vs Consistency
   1. **Availability:** System is up and running, or we can have some downtime for maintenance.
   2. **Consistency:** All user see the same data at the same time, or we can have eventual consistency
### 4. Data Retention & Durability:
1. **Data Retention:** How long do we need to keep the data? 
2. **Durability:** if the Data fails it is acceptable to lose the few second data or not