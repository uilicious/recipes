# Validate that product is added to cart successfully

This test case validates that when a user searches for an item and adds it to the cart, the item name should appear in the Cart.

## Test Steps

These are the steps to perform to validate the test case:

1. Navigate to Allbirds's website
2. Choose country to ship to
3. Click on "Men"
4. Click on "Shoes"
5. Hover on an item to expand menu
6. Click on a size
7. Validate if the Item has been successfully added to cart

## Test Script

This test automation script validates the test case using the UI-licious Test Framework:
```javascript
//Navigate to site
I.goTo("https://www.allbirds.com/")

//Choose country to ship
I.click("US")

//Click on the menu to proceed to the shoe page
I.click("Men")
I.click("Shoes")

//Hover on an item 
I.hoverOn("Men's Tree Runners")

//Choose a size
I.click("9")

//Wait for page to load
I.wait(10)

//Use Iframe to limit uilicious to the cart sidebar and validate that the product is added
UI.context("#drawer-body", ()=>{
	I.see("Men's Tree Runners")
})
```