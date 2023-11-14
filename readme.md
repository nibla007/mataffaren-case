# Link to google sheet

https://docs.google.com/spreadsheets/d/1yetO0htd2ClwuVOloOxpFSdSyfv_v4kKqOoJteeBpjw/edit?usp=sharing

# Willys GitHub Green

We added this collection to make sure that Github actions passes and is working as intended.

# Willys Standard Tests

This is the main collection for all tests that we explain below in the readme.

# Tests

## Common tests

### The status code of the response should be 200

Tests if the current request had a response with status-code 200, which is the globally accepted status-code for OK("pm.response.to.have.status(200")).

### The response time should be below 1 second

Tests the response time of the API and makes sure it's below 1000ms("pm.expect(pm.response.responseTime).to.be.below(1000)").

## 1 | Get categories

### Each main category should have the properties title and url and they have the datatype "string"

Tests that each main category have certain properties(title, url), and that the datatype is "string".

## 2 | Get productlist within categories

### There should be at least one product in a main category

Tests that there's at least one product in each main category to make sure that it isn't empty.

### There should be at least one sub category in each main category - length check

Tests that there's at least one sub category for each main category.
Expects the length of each main category's children array(The sub categories in each main category) to be greater than 0.
Test fails if it's 0.

### There should be at least one sub category in each main category - not empty check

Tests that there are sub categories in each main category.
Loops through every main category and checks if it's not empty.
Fails on "lotter" because it has no sub categories meaning that the array is empty.

### Check if the last main category "lotter" is empty and is length 0

Tests if the last main category has no sub categories by checking if it's length is less than 1 and checking if the sub category is empty.

## 3 | Test name-asc

### First product of each main category should start with either A, B, +, T, 2, 8, 1 or 4

Tests that the first product in each main category starts with one of the above letters to make sure that the alphabetical sorting system works. If it fails, it means that they've added a new product that starts with either a symbol, number or that the first product starts with an unexpected letter.

## 4 | Test name-desc

### First product of each main category should start with either Ö, Ä, Å, V, T or Z

Tests that the first product in each main category starts with one of the above letters to make sure that the alphabetical sorting system works. If it fails, it means that they've added a new product that takes priority over either Ä, Å, V, T or Z.

## 5 | Test price-asc

### Product prices should be sorted in ascending order (version 1)

Tests that the first product's price(a) is less than or equal to the second product's price(b) and it compares it this way on all products in a sub category to ensure that there are no <span style="color:red">anomalies</span>.
```
0, a: 9.9 is less than or equal to b: 11.9 
 
1, a: 11.9 is less than or equal to b: 11.9 
 
2, a: 11.9 is less than or equal to b: 14.5 
 
3, a: 14.5 is less than or equal to b: 13.5 -> Test fails here because 14.5 is not less than or equal to 13.5
```

### Product prices should be sorted in ascending order (version 2)

- Checks if the current product is on a campaign
- If the current product and the next product are on campaign, continue to the next iteration
- If the first product's priceValue is greater than the second product's priceValue, fail the test
- If the prices are not sorted in ascending order, fail the test

## 6 | Test price-desc

### Product prices should be sorted in descending order (version 1)

Tests that the first product's price(a) is greater than or equal to the second product's price(b), and it compares it this way on all products in a sub category to ensure that there are no <span style="color:red">anomalies</span>.

```
11, a: 14.5 is greater than or equal to b: 14.5 
 
12, a: 14.5 is greater than or equal to b: 14.5 
 
13, a: 14.5 is greater than or equal to b: 13.5 
 
14, a: 13.5 is greater than or equal to b: 14.5 -> Test fails here because 13.5 is not greater than 14.5
```

### Product prices should be sorted in descending order (version 2)

- Checks if the current product is on a campaign
- If the current product and the next product are on campaign, continue to the next iteration
- If the first product's priceValue is less than the second product's priceValue, fail the test
- If the prices are not sorted in descending order, fail the test

## 7 | Test compareprice-asc

sort=comparePrice-asc does not visually change to display a products "comparePrice" but still sorts the products by "comparePrice". It always shows the "price" of a product.

### Product comparePrices should be sorted in ascending order

Tests that the first product's compare price(a) is less than or equal to the second product's price(b) and it compares it this way on all products in a sub category to ensure that there're no <span style="color:red">anomalies</span>.
```
0, a: 24.9 is less than or equal to b: 28.9 
 
1, a: 28.9 is less than or equal to b: 16.9  ->  Test fails here because 28.9 is not less than or equal to 16.9
```

## 8 | Test compareprice-desc

sort=comparePrice-desc does not visually change to display a products "comparePrice" but still sorts the products by "comparePrice". It always shows the "price" of a product.

### Product comparePrices should be sorted in descending order

Tests that the first product's compare price(a) is greater than or equal to the second product's price(b) and it compares it this way on all products in a sub category to ensure that there're no <span style="color:red">anomalies</span>.
```
0, a: 229 is greater than or equal to b: 238 -> Test fails here because 229 is not greater than or equal to 238
```

## 9 | Pagination test

### Pagination is implemented and working

Checks if pagination and its properties exists and checks if their values are realistic.

