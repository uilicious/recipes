# Validate that product is removed from the cart

This test case validates that when a user adds a prodcuct to the cart then remove, the item name should be removed from the cart.

## Test Steps

These are the steps to perform to validate the test case:

1. Navigate to Tentree's website
2. Click "Search"
3. Fill in "Jumper" in the search box
4. Choose an item
5. Choose a size
6. Click Add to Cart
7. Validate if the Item has been successfully added to cart
8. Click on the "Decrement" icon
9. Validate if the item has been successfully removed to cart and the message "Your cart is empty" is appearing

## Test Script

This test automation script validates the test case using the UI-licious Test Framework:
```javascript
// Navigate to site
I.goTo("https://www.tentree.ca/")

// Select region
I.click("United States")
I.wait(5)

// Dismiss promo banner
UI.context("iframe[title='Sign Up via Text for Offers']", ()=>{
	// Click the close icon
	I.click("#closeIconSvg")
})
I.wait(5)

//Click on search bar
UI.context("#menu-button", ()=>{
	I.click("#desktop-searchbar")
})

//Fill in search bar
I.fill("Search", "Jumper")
I.wait(5)

//Validate that relevant item exists
I.see("Highline Mock Neck Sweater")

//Choose an item
I.click("Highline Mock Neck Sweater",0 ,-50)

// Dismiss promo banner
UI.context("iframe[title='Sign Up via Text for Offers']", ()=>{
	// Click the close icon
	I.click("#closeIconSvg")
})

// Select region
I.click("United States")
I.wait(5)

//Choose size
I.click("XXL")

//Add to cart
I.click("Add to bag")

//Use iframe and verify if product is added to cart
UI.context(".rebuy-cart__flyout", ()=>{
	I.see("Highline Mock Neck Sweater")
})

UI.context(".rebuy-cart__flyout", ()=>{
	I.click("Trash Icon")
})

UI.context(".rebuy-cart__flyout", ()=>{
	I.see("Your cart is empty")
})
```