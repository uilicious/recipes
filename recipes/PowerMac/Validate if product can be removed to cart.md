# Validate that quantity of product is correct

This test case validates that when a user removes an item from the cart, it is properly removed.

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
10. Click on "Remove"
11. Do a validation if item is removed

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

I.click("Remove")

I.see("Your cart is empty")
```