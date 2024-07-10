# Search for a product that exists and validate that the catalogue has results

This test case validates that when a user searches for a product that exists, the search results pages shows relevant products.

## Test Steps

These are the steps to perform to validate the test case:

1. Navigate to allbird's website
2. Click "Search"
3. Fill in "Shoes" in the search box
4. Validate that relavant products are shown

## Test Script

This test automation script validates the test case using the UI-licious Test Framework:
```javascript
//Navigate to website
I.goTo("https://www.allbirds.com/")

//Choose shipping country
I.click("US")

//Wait for page to load
I.wait(5)

//Search for an item
I.click("Search")
I.fill("Search", "Shoes")

//Check for relevant item
I.see("Men's Tree Runners")
```