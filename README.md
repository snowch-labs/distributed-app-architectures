### Introduction

This lab walks through incrementally building a distributed application architecture as a series of projects.  

The goal of the lab are to provide the student with experience:

 - designing distributed application architectures
 - implementing distributed application architectures using IBM Cloud technologies

A fictional startup is used for the examples, "E-MART" who are aiming to be the next big online retailer.

### Overall architecture constraints

- The solution must be built using microservices approach
- The solution must be built on IBM Cloud
- The solution must be built using IBM Cloud Continuous Delivery
- The solution must be open source
- The solution must have an availability of 99.95% or greater
- The solution should be implemented with [principles of chaos](http://principlesofchaos.org)
- Quality is of paramount importance:
   - Metrics should be recorded for all user requests and the request response code
   - KPIs charts should be available for all metrics to monitor how quality is changing over time
   

### Project 1 - Catalog MVP

- The catalog will have a global customer base
- The catalog may have hundreds of thousands of items
- An item may belong to multiple categories
- A category must have one parent category (except the ROOT category)
- Items may be managed via a REST API using CRUD (a backend UI isn't required at this stage)
- Catalog CRUD operations must be available in browse/search within 30 seconds
- Users must be able to search the catalog from the latest stable chrome and firefox web browsers
- The catalog must support 500 search operations per second with a latency of 400ms or lower for 99.9% of requests
- The catalog must have an availability of 99.95% or greater
- The solution should be able to scale horizontally initially starting at a low cost with the cost increase approximately equal to the capacity increase (e.g. 2x capacity = 2x cost, 3x capacity = 3x cost, ...)
- The solution should be able to scale up/down dynamically based on the workload
- The catalog will serve a region (e.g. US, UK, ...)
- Each region is an independent business unit

**Nice to have functionality**

- Catalog search could support full text searching on item name, description and category
- The full text search could support ([fuzzy matching](https://en.wikipedia.org/wiki/Approximate_string_matching))

**Some considerations**

- IP Latency could be important: http://www.verizonenterprise.com/about/network/latency/
- Will you use a single domain name, or is per country ok?  (E.g. amazon.com [US], amazon.co.uk [UK], ...)
- Adding full text (and fuzzy) search later may require a re-architecture

## Project 1B - B2B Catalog

- A subset of items will be offered to b2b customers only
- B2B customers must be authenticated to view the items


## Project 2 - Shopping Cart MVP

- Users must be able to add/remove items to shopping cart
- When users attempt to checkout they will be required to login
- If users don't have an account at checkout, they can signup for a new account  
- When checking out, the server will verify that each item in the cart is fresh
  - if the item is not fresh, a message will be displayed to the user with the change
- TODO: NFRs

## Project 3 - Analytics Foundations MVP

- Each of the following events will be recorded:
  - catalog search
  - add item to shopping cart
  - remove item from shopping cart
  - checkout shopping cart
  - login to account
  - register for account
- Anonymous catalog search events will be linked to a user account at checkout
- Performance of shopping cart is paramount, analytics must not be performed on datastore created in Project 2
- A collaborative filtering style machine learning model will be created 
- Batch (e.g. nightly training) of the model will be sufficient for the MVP

## Project 4 - Predictive Analytis MVP

- The model built in Project 3 will be used to make recommendations to users on the search pagef
- The recommendation must be created in 50ms or less
- More requirements coming soon

## Project 5 - Business Intelligence MVP

- Business users should be able to run exploratory queries against tens of terabytes of shopping data (checkouts, product, customers)
- More requirements coming soon
