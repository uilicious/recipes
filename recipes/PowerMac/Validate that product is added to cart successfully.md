# Validate that product is added to cart successfully

This test case validates that when a user searches for an item and adds it to the cart, the item name should appear in the Cart.

## Test Steps

These are the steps to perform to validate the test case:

1. Navigate to Powermac's website
2. Click "Search"
3. Fill in "iPhone 15"
4. Press "Enter"
5. Click on the product
6. Click "Add to Cart"
7. Validate if the Item has been successfully added to cart

## Test Script

This test automation script validates the test case using the UI-licious Test Framework:
```javascript
// 🌐 Lets load up the website
I.goTo("https://powermaccenter.com/")
I.fill("Search", "iPhone 15 Pro Max 1TB Black Titanium")
I.pressEnter()
I.click("iPhone 15 Pro Max 1TB Black Titanium")
I.wait(3)
// to validate availability of stocks
I.click("Add to Cart")

UI.context("#cart-notification", ()=>{
	I.see("Item added to your cart")
	I.see("iPhone 15 Pro Max 1TB Black Titanium")
})
```
