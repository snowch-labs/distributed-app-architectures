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

### Project 1 - Catalog MVP

- The catalog may have hundreds of thousands of items
- An item may belong to multiple categories
- A category must have one parent category (except the ROOT category)
- Items may be managed via a REST API using CRUD (a backend UI isn't required at this stage)
- Catalog CRUD operations must be available in browse/search within 30 seconds
- Users must be able to search the catalog from the latest stable chrome and firefox web browsers
- Catalog search must support free text searching on item name, description and category
- The catalog must support 500 search operations per second with a latency of 500ms or lower for 99.9% of requests
- The catalog must have an availability of 99.95% or greater
- The solution should be able to scale horizontally initially starting at a low cost with the cost increase approximately equal to the capacity increase (e.g. 2x capacity = 2x cost, 3x capacity = 3x cost, ...)
- The solution should be able to scale up/down dynamically based on the workload

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
