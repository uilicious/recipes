# Validate that quantity of product is correct after adding to cart

This test case validates that when a user searches for an item and adds it to the cart, the item name should appear on the cart and the quantity is correct.

## Test Steps

These are the steps to perform to validate the test case:

1. Navigate to Blizzard's website
2. Click "Search"
3. Fill in "Starcraft"
4. Click on an item
5. Click Add to Cart
6. Validate if the Item has been successfully added to cart
7. Validate if the item has the correct quantity added to the cart

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

UI.context("#dropdown-cart", ()=>{
	//Initialization of values
	var expected_quantity = "1"
	var actual_quantity = I.getValue("#item-quantity")
	TEST.assert(expected_quantity === actual_quantity, `Expected quantity is ${expected_quantity}, got ${actual_quantity}`)
})
```
