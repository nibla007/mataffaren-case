# Tests

## Common tests

### The status code of the response should be 200

Tests if the current request had a response with status-code 200, which is the globally accepted status-code for OK("pm.response.to.have.status(200"))

### The response time should be below 1 second

Tests the response time of the API and makes sure it's below 1000ms("pm.expect(pm.response.responseTime).to.be.below(1000)")

## 1 | Get categories

### The response time should be below 1 second  Each main category should have the properties title and url and they have the datatype "string"

Tests that each main category have certain properties(title, url), and that the datatype is "string".

## 2 | Get productlist within categories

### There should be at least one product in a main category

Tests that there's at least one product in each main category to make sure that it isn't empty.

### There should be at least one sub category in each main category

Tests that there's at least one sub category for each main category.

## 3 | Test name-asc

### First product of each main category should start with either A, B, +, T, 2, 8, 1 or 4

Tests that the first product in each main category starts with one of the above letters to make sure that the alphabetical sorting system works. If it fails, it means that they've added a new product that starts with either a symbol, number or that the first product starts with an unexpected letter.

## 4 | Test name-desc

### First product of each main category should start with either Ö, Ä, Å, V, T or Z

Tests that the first product in each main category starts with one of the above letters to make sure that the alphabetical sorting system works. If it fails, it means that they've added a new product that takes priority over either Ä, Å, V, T or Z.

## 5 | Test pastej price-asc

### Product prices should be sorted in ascending order (version 1)

Tests that the first product's price(a)(index 0) is less than or equal to the second product's price(b)(index 1) and it compares it this way on all products in the sub category Pastej och paté to ensure that there're no <span style="color:red">anomalies</span>.
```
0, a: 9.9 is less than or equal to b: 11.9 
 
1, a: 11.9 is less than or equal to b: 11.9 
 
2, a: 11.9 is less than or equal to b: 14.5 
 
3, a: 14.5 is less than or equal to b: 13.5 -> Test fails here because 14.5 is not less than or equal to 13.5
```

### Product prices should be sorted in ascending order (version 2)

- Checks if the current product is on a campaign
- If the current product and the next product are on campaign, continue to the next iteration
- If the next product is on campaign but the current one is not, fail the test
- If the prices are not in ascending order, fail the test
- Asserts that the prices are sorted in ascending order

## 6 | Test pastej price-desc

### Product prices should be sorted in descending order (version 1)

Tests that the first product's price(a)(index 0) is greater than or equal to the second product's price(a)(index 1), and it compares it this way on all products in the sub category Pastej och paté to ensure that there're no <span style="color:red">anomalies</span>.

```
11, a: 14.5 is greater than or equal to b: 14.5 
 
12, a: 14.5 is greater than or equal to b: 14.5 
 
13, a: 14.5 is greater than or equal to b: 13.5 
 
14, a: 13.5 is greater than or equal to b: 14.5 -> Test fails here because 13.5 is not greater than 14.5
```

### Product prices should be sorted in descending order (version 2)

## 7 | Test pastej compareprice-asc

### Product comparePrices should be sorted in ascending order

Tests that the first product's compare price(a)(index 0) is less than or equal to the second product's price(b)(index 1) and it compares it this way on all products in the sub category Pastej och paté to ensure that there're no <span style="color:red">anomalies</span>.
```
0, a: 24.9 is less than or equal to b: 28.9 
 
1, a: 28.9 is less than or equal to b: 16.9  ->  Test fails here because 28.9 is not less than or equal to 16.9
```

## 8 | Test pastej compareprice-desc

### Product comparePrices should be sorted in descending order

Tests that the second product's compare price(b) is less than or equal to the first product's price(a) and loops through the whole product list of the sub category Pastej och paté in this way to ensure that there're no <span style="color:red">anomalies</span>.
```
0, a: 229 is greater than or equal to b: 238 -> Test fails here because 229 is not greater than or equal to 238
```

## 9 | Pagination test

### Test if pagination is implemented and working as intended

Checks if pagination and it's properties exists and tests their values.
