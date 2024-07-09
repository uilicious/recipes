# Search for a product and validate that the result only displays the specific product

This test case should validate that the item added to cart has been successfully added to cart

## Test Steps

These are the steps to perform to validate the test case:

1. Navigate to Nomatic's website
2. Click "Search"
3. Fill in "iPhone 15 Pro Max 1TB Black Titanium" in the search box
4. Validate that relavant products are shown

## Test Script

This test automation script validates the test case using the UI-licious Test Framework:
```javascript
// 🌐 Lets load up the website
I.goTo("https://powermaccenter.com/")
// Search for the item/product
I.fill("Search", "iPhone 15 Pro Max 1TB Black Titanium")
// press "Enter" to proceed with the search
I.pressEnter()
// Wait 3 seconds to ensure that the page has loaded
I.wait(3)
// Validate that the catalogue has relevant results
I.dontSee("iPhone 14 Pro Max")
```