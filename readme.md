
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
    - [test](#test)
# Tests
TODO - Tester för alla möjliga sätt att sortera produkterna på
TODO - Tester för ?
TODO - Sno thomas kod för att kunna köra "postman" tester i VSC istället
## Common tests
### The status code of the response should be 200
Tests the status of the API we're sending a request to and makes sure that it's working by expecting it to have a status of 200, which is the globally accepted status-code for OK("pm.response.to.have.status(200"))
### The response time should be below 1 second
Tests the response time of the API and makes sure it's below 1000ms("pm.expect(pm.response.responseTime).to.be.below(1000)")
## 1 | Get categories
### The response time should be below 1 second
### Each main category should have the properties title and url and they have the datatype "string"
Tests that each main category have certain properties(title, url), and that the datatype is "string".

## 2 | Get productlist within categories
### There should be at least one product in a main category
Tests that there's at least one product in each main category to make sure that it isn't empty.
### There should be at least one sub category in each main category
Tests that there's at least one sub category for each main category.

## 3 | Test name-asc
### First product of each main category should start with either A, B, +, T, 2, 8, 1 or 4
Tests that the first product of each main category starts with one of the above letters to make sure that the alphabetical sorting system works. If it fails, it means that they've added a new product that starts with either a symbol, number or that the first product starts with an unexpected letter.

## 4 | Test name-desc
### First product of each main category should start with either Ö, Ä, Å, V, T or Z
Tests that the first product of each main category starts with one of the above letters to make sure that the alphabetical sorting system works. If it fails, it means that they've added a new product that takes priority over either Ä, Å, V, T or Z.

## 5 | Test pastej price-asc
### Product prices should be sorted in ascending order (version 1)
Tests that the first product's price(a) is less than or equal to the second product's price(b) and loops through the whole product list of the sub category Pastej och paté in this way to ensure that there're no <span style="color:red">anomalies</span>.
```
1. a = 9.9, b = 11.9
 
2: a = 11.9, b = 11.9
 
3: a = 11.9, b = 14.5
 
4: a = 14.5, b = 13.5 (Where the test fails, because a is expected to be less than or equal to b)
```
### Product prices should be sorted in ascending order (version 2)


## 6 | Test pastej price-desc
### Product prices should be sorted in descending order (version 1)
Tests that the second product's price(b) is less than or equal to the first product's price(a) and loops through the whole product list of the sub category Pastej och paté in this way to ensure that there're no <span style="color:red">anomalies</span>.

```
10: a = 15.9, b = 14.5
 
11: a = 14.5, b = 14.5
 
12: a = 14.5, b = 14.5
 
13: a = 14.5, b = 14.5
 
14: a = 14.5, b = 13.5

15: a = 13.5, b = 14.5 (Where the test fails, because b is expected to be less than or equal to a)
```

### Product prices should be sorted in descending order (version 2)

## 7 | Test pastej compareprice-asc
### Product comparePrices should be sorted in ascending order
Tests that the first product's compare price(a) is less than or equal to the second product's price(b) and loops through the whole product list of the sub category Pastej och paté in this way to ensure that there're no <span style="color:red">anomalies</span>.
```
a: 49.5, is less than or equal to b: 49.8 
 
a: 49.8, is less than or equal to b: 53.8 
 
a: 53.8, is less than or equal to b: 54 
 
a: 54, is less than or equal to b: 59.5 
 
a: 59.5, is less than or equal to b: 59.5 
```

## 8 | Test pastej compareprice-desc
### Product comparePrices should be sorted in descending order
Tests that the second product's compare price(b) is less than or equal to the first product's price(a) and loops through the whole product list of the sub category Pastej och paté in this way to ensure that there're no <span style="color:red">anomalies</span>.
```
b: 172.67 is less than or equal to, a: 172.67 
 
b: 99.47 is less than or equal to, a: 172.67 
 
b: 97.5 is less than or equal to, a: 99.47 
 
b: 96.67 is less than or equal to, a: 97.5 
 
b: 84.5 is less than or equal to, a: 96.67 
```

## 9 | Pagination test
### Test if pagination is implemented and working as intended
Checks if pagination and it's properties exists and tests their values.
