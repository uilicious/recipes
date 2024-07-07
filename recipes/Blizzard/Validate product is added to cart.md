# Validate that product is added to cart successfully

This test case validates that when a user searches for an item and adds it to the cart, the item name should appear in the Cart.

## Test Steps

These are the steps to perform to validate the test case:

1. Navigate to Nomatic's website
2. Click "Search"
3. Fill in "Camera Bag"
4. Click on the name of the camera bag
5. Click Add to Cart
6. Validate if the Item has been successfully added to cart

## Test Script

This test automation script validates the test case using the UI-licious Test Framework:
```javascript
//Navigate to website
I.goTo("https://uk.gear.blizzard.com/")

//Wait for page to load
I.wait(5)

//Close promo dialog
UI.context(".needsclick", ()=>{
	I.click("Close")
})

//Search for an item
I.fill("Search", "StarCraft")
I.pressEnter()

//Wait for page to load
I.wait(5)

//Choose an item
I.click("StarCraft Black Flatbill Snapback Hat")

//Add to cart
I.click("Add to cart")

//Use Iframe to limit uilicious to the cart sidebar and validate that the product is added
UI.context("#dropdown-cart", ()=>{
	I.see("StarCraft Black Flatbill Snapback Hat")
})
```
