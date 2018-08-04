### Introduction

This lab walks through incrementally building a distributed application architecture as a series of projects.  

The goal of the lab are to provide the student with experience:

 - designing distributed application architectures
 - implementing distributed application architectures using IBM Cloud technologies

A fictional startup is used for the examples, "E-MART" who are aiming to be the next big online retailer.


### Project 1 - Catalog MVP

- The catalog may have hundreds of thousands of items
- An item may belong to multiple categories
- A category must have one parent category (except the ROOT category)
- Items may be managed via a REST API using CRUD (a backend UI isn't required at this stage)
- Catalog CRUD operations must be available in browse/search within 30 seconds
- Users must be able to browse the catalog from the latest stable chrome and firefox web browsers
- Users must be able to search the catalog from the latest stable chrome and firefox web browsers
- Catalog search must support free text searching on item name, description and category
- The catalog must support 500 seach operations per second with a latency of 500ms or lower for 99.9% of requests
- The catalog must have an availability of 99.95% or greater
- The solution should be able to scale horizontally initially starting at a low cost with the cost increase approximately equal to the capacity increase (e.g. 2x capacity = 2x cost, 3x capacity = 3x cost, ...)
