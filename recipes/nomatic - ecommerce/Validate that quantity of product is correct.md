# Validate that quantity of product is correct after adding to cart

This test case validates that when a user searches for an item and adds it to the cart, the item name should appear on the cart and the quantity is correct.

## Test Steps

These are the steps to perform to validate the test case:

1. Navigate to Nomatic's website
2. Click "Search"
3. Fill in "Camera Bag"
4. Click on the name of the camera bag
5. Click Add to Cart
6. Validate if the Item has been successfully added to cart
7. Validate if the item has the correct quantity added to the cart

## Test Script

This test automation script validates the test case using the UI-licious Test Framework:
```javascript
I.goTo("https://www.nomatic.com/collections/all-backpacks-bags")
I.click("Shop your country")

// Fill in search
I.click("icon-search")
I.fill("Search", "Camera Bag")
I.pressEnter() // Press "Enter" to submit search

// Check that product appearts in search reasult
I.see("Mckinnon Camera Pack 25L")

// View product and add to cart
I.click("Mckinnon Camera Pack 25L")
I.click("Add to Cart")

// Use UI.context to specifically target the Shopping Cart UI for validation of added item
UI.context("#CartDrawer", ()=>{
	I.see("Mckinnon Camera Pack 25L")	
})

//Use UI.context to specifically target the shopping cart UI for validation of item quantity
UI.context("#CartDrawer", ()=>{
	//Initialization of values
	var expected_quantity = "1"
	var actual_quantity = I.getValue(".js-qty__num")
	TEST.assert(expected_quantity === actual_quantity, `Expected quantity is ${expected_quantity}, got ${actual_quantity}`)
})
```
