
- [Tests](#tests)
    - [Common tests](#common-tests)
      - [The status code of the response should be 200](#the-status-code-of-the-response-should-be-200)
      - [The response time should be below 1 second](#the-response-time-should-be-below-1-second)
    - [1 | Get categories](#1--get-categories)
      - [The response time should be below 1 second](#the-response-time-should-be-below-1-second-1)
      - [Each main category should have the properties title and url and they have the datatype "string"](#each-main-category-should-have-the-properties-title-and-url-and-they-have-the-datatype-string)
    - [2 | Get productlist within categories](#2--get-productlist-within-categories)
      - [There should be at least one product in a main category](#there-should-be-at-least-one-product-in-a-main-category)
      - [There should be at least one sub category in each main category](#there-should-be-at-least-one-sub-category-in-each-main-category)
    - [3 | Test name-asc](#3--test-name-asc)
      - [First product of each main category should start with either A, B, +, T, 2, 8, 1 or 4](#first-product-of-each-main-category-should-start-with-either-a-b--t-2-8-1-or-4)
    - [4 | Test name-desc](#4--test-name-desc)
      - [First product of each main category should start with either Ö, Ä, Å, V, T or Z](#first-product-of-each-main-category-should-start-with-either-ö-ä-å-v-t-or-z)
    - [5 | Test pastej price-asc](#5--test-pastej-price-asc)
      - [Product prices should be sorted in ascending order (version 1)](#product-prices-should-be-sorted-in-ascending-order-version-1)
      - [Product prices should be sorted in ascending order (version 2)](#product-prices-should-be-sorted-in-ascending-order-version-2)
    - [6 | Test pastej price-desc](#6--test-pastej-price-desc)
      - [Product prices should be sorted in descending order (version 1)](#product-prices-should-be-sorted-in-descending-order-version-1)
      - [Product prices should be sorted in descending order (version 2)](#product-prices-should-be-sorted-in-descending-order-version-2)
    - [7 | Test pastej compareprice-asc](#7--test-pastej-compareprice-asc)
      - [Product comparePrices should be sorted in ascending order](#product-compareprices-should-be-sorted-in-ascending-order)
    - [8 | Test pastej compareprice-desc](#8--test-pastej-compareprice-desc)
      - [Product comparePrices should be sorted in descending order](#product-compareprices-should-be-sorted-in-descending-order)
    - [9 | Pagination test](#9--pagination-test)
      - [Pagination Test](#pagination-test)
# Tests
TODO - Tester för alla möjliga sätt att sortera produkterna på
TODO - Tester för ?
TODO - Sno thomas kod för att kunna köra "postman" tester i VSC istället
### Common tests
#### The status code of the response should be 200
#### The response time should be below 1 second
### 1 | Get categories
#### The response time should be below 1 second
#### Each main category should have the properties title and url and they have the datatype "string"
Tests that there's at least 10 main categories, that the status is OK with a passable response time.

### 2 | Get productlist within categories
#### There should be at least one product in a main category
#### There should be at least one sub category in each main category
Tests that there's at least one product within in each main category with setNextRequest, that the status is OK with a passable response time.

### 3 | Test name-asc
#### First product of each main category should start with either A, B, +, T, 2, 8, 1 or 4
Tests that the first product from each main category is sorted from A-Z with special characters and numbers taking priority over letters and that the status is OK with a passable response time.

### 4 | Test name-desc
#### First product of each main category should start with either Ö, Ä, Å, V, T or Z

### 5 | Test pastej price-asc
#### Product prices should be sorted in ascending order (version 1)
#### Product prices should be sorted in ascending order (version 2)


### 6 | Test pastej price-desc
#### Product prices should be sorted in descending order (version 1)
#### Product prices should be sorted in descending order (version 2)

### 7 | Test pastej compareprice-asc
#### Product comparePrices should be sorted in ascending order


### 8 | Test pastej compareprice-desc
#### Product comparePrices should be sorted in descending order

### 9 | Pagination test
#### Pagination Test



