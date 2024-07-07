# Search for a product that exists and validate that the catalogue has results

This test case validates that when a user searches for a product that exists, the search results pages shows relevant products.

## Test Steps

These are the steps to perform to validate the test case:

1. Navigate to Nomatic's website
2. Click "Search"
3. Fill in "Camera Bag" in the search box
4. Validate that relavant products are shown

```javascript
//Navigate to website
I.goTo("https://modkat.com/")

//close the newsletter
I.click("Close")

//Search for an item
I.fill("Search", "Modkat XL")
I.pressEnter()
I.wait(5)

//Validate that a relevant product is shown
I.see("Modkat XL Litter Box")
```