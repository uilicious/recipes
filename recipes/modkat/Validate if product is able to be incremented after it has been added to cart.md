# Validate that product is properly incremented after it has been added to cart

This test case validates that when a user searches for an item and adds it to the cart, the item should be properly incremented after it has been added to cart.

## Test Steps

These are the steps to perform to validate the test case:

1. Navigate to Modkat's website
2. Fill in Search bar with "Modkat XL"
3. Click on an item
4. Click Add to Cart
5. Validate if the Item has been successfully added to cart
6. Validate the number of item in the cart
7. Click on the plus button
8. Do another validation to check if the item is properly incremented

## Test Script

This test automation script validates the test case using the UI-licious Test Framework:
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

//Click on an available item
I.click("Modkat XL Litter Box")

//Add it to cart
I.click("Add to cart")

//Use iframe to limit UIlicious and validate if product is added to cart
UI.context(".cart_items", ()=>{
	I.see("Modkat XL Litter box")
})

//Use iframe to limit UIlicious and validate if number of product is correct
UI.context(".cart_items", ()=>{
	var expected_quantity = "1"
	var actual_quantity = I.getValue(".quantity")
	TEST.assert(expected_quantity === actual_quantity, `Expected quantity is ${expected_quantity}, got ${actual_quantity}`)
})

//Click on incremet button
UI.context(".cart_items", ()=>{
	I.click(".icon-plus")
})

//Use iframe to limit UIlicious and validate number of products after increment
UI.context(".cart_items", ()=>{
	var expected_quantity = "2"
	var actual_quantity = I.getValue(".quantity")
	TEST.assert(expected_quantity === actual_quantity, `Expected quantity is ${expected_quantity}, got ${actual_quantity}`)
})
```