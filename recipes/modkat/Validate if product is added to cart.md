# Validate that product is added to cart successfully

This test case validates that when a user searches for an item and adds it to the cart, the item name should appear in the Cart.

## Test Steps

These are the steps to perform to validate the test case:

1. Navigate to Modkat's website
2. Fill in Search bar with "Modkat XL"
3. Click on an item
4. Click Add to Cart
5. Validate if the Item has been successfully added to cart

## Test Script

This test automation script validates the test case using the UI-licious Test Framework:
```javascript
//Navigate to website
I.goTo("https://modkat.com/")

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
```