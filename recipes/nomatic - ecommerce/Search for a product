# Search for a product that exists and validate that the catalogue has results

This test case validates that when a user searches for a product that exists, the search results pages shows relevant products.

## Test Steps

These are the steps to perform to validate the test case:

1. Navigate to Nomatic's website
2. Click "Search"
3. Fill in "Camera Bag" in the search box
4. Validate that relavant products are shown

## Test Script

This test automation script validates the test case using the UI-licious Test Framework:
```javascript
// Open the website
I.goTo("https://www.nomatic.com/collections/all-backpacks-bags")

// Click "Shop your country" to be redirected to subsite based on detected IP address
I.click("Shop your country")

// Fill in search
I.click(".icon-search"); // Click on the "Magnifying glass" icon using CSS selector
I.fill("Search", "Camera Bag");
I.pressEnter(); // Press enter to submit search

// Validate that a relavent product is shown
I.see("Mckinnon Camera Pack 25L")
```
