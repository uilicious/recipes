# Validate that product is properly incremented after it has been added to cart

This test case validates that when a user searches for an item and adds it to the cart, the item should be properly incremented after it has been added to cart.

## Test Steps

These are the steps to perform to validate the test case:

1. Navigate to Nomatic's website
2. Click "Search"
3. Fill in "Camera Bag"
4. Click on the name of the camera bag
5. Click Add to Cart
6. Validate if the Item has been successfully added to cart
7. Validate the number of item in the cart
8. Click on the plus button
9. Do another validation to check if the item is properly incremented

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

//Use Iframe to limit uilicious to cart and validate that quantity is correct
UI.context("#dropdown-cart", ()=>{
	//Initialization of values
	var expected_quantity = "1"
	var actual_quantity = I.getValue("#item-quantity")
	TEST.assert(expected_quantity === actual_quantity, `Expected quantity is ${expected_quantity}, got ${actual_quantity}`)
})

//Use Iframe to limit uilicious to cart and click on the plus icon
UI.context("#dropdown-cart", ()=>{
	I.click(".qty-btn.qtyplus")
})

//Use Iframe to limit uilicious to cart and do another check if the quantity is properly incremented
UI.context("#dropdown-cart", ()=>{
	//Initialization of values
	var expected_quantity = "2"
	var actual_quantity = I.getValue("#item-quantity")
	TEST.assert(expected_quantity === actual_quantity, `Expected quantity is ${expected_quantity}, got ${actual_quantity}`)
})
```