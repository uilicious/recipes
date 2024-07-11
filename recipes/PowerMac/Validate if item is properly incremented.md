# Validate that quantity of product is correct

This test case validates that when a user searches for an item and adds it to the cart, the item should be properly incremented after it has been added to cart.

## Test Steps

These are the steps to perform to validate the test case:

1. Navigate to Powermac's website
2. Click "Search"
3. Fill in "iPhone 15"
4. Press "Enter"
5. Click on the product
6. Click "Add to Cart"
7. Validate if the Item has been successfully added to cart
8. Click "View my cart"
9. Validate if user is redirected to correct page
10. Validate if number of product in cart is correct
11. Click on "Plus" icon
12. Do another validation if number of item is correct after increment

## Test Script

This test automation script validates the test case using the UI-licious Test Framework:
```javascript
// 🌐 Lets load up the website
I.goTo("https://powermaccenter.com/")
I.fill("Search", "iPhone 15 Pro Max 1TB Blue Titanium")
I.pressEnter()
I.click("iPhone 15 Pro Max 1TB Blue Titanium")
I.wait(3)
// to validate availability of stocks
I.click("Add to Cart")

//Use UI.context to specifically cart drawer and validate if item is added
UI.context("#cart-notification", ()=>{
	I.see("Item added to your cart")
	I.see("iPhone 15 Pro Max")
})

//Procced to cart page
UI.context("#cart-notification", ()=>{
	I.click("View My Cart")
})

//Validate if redirected to correct page
I.amAt("https://powermaccenter.com/cart")

//Validate if number of product is correct
var expected_quantity = "1"
var actual_quantity = I.getValue(".quantity__input")
TEST.assert(expected_quantity === actual_quantity, `Expected quantity is ${expected_quantity}, got ${actual_quantity}`)

//Click on "Plus" icon
I.click(`//*[@name="plus"]`)

//Validate if number of product is correct
var expected_quantity = "2"
var actual_quantity = I.getValue(".quantity__input")
TEST.assert(expected_quantity === actual_quantity, `Expected quantity is ${expected_quantity}, got ${actual_quantity}`)
```