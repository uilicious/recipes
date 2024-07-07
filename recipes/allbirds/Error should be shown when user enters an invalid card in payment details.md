# Error should be shown when user enters an invalid card in payment details

This test case should validate that an error is shown when the user enters an invalid card for payment during checkout.

## Test Steps

This are the steps to perform to validate the test case:

1. Navigate to website
2. Add a product to cart
3. Proceed to checkout page
4. Fill in shipping information with valid information
5. Fill in card details with invalid card
6. Validate that error "Card was declined" will appear

## Test Script

This is the test script to automate testing using the UI-licious test framework:
```javascript
//Navigate to site
I.goTo("https://www.allbirds.com/")

//Choose country to ship
I.click("US")

//Click on the menu to proceed to the shoe page
I.click("Men")
I.click("Shoes")

//Hover on an item 
I.hoverOn("Men's Tree Runners")

//Choose a size
I.click("9")

//Wait for page to load
I.wait(10)

//Proceed to checkout
I.click("Proceed To Checkout")

//Fill in shipping information
I.fill("Email", <email>)
I.fill("First Name", <First Name>)
I.fill("Last Name", <Last Name>)
I.fill("Address", <Address>)
I.fill("City", <City>)
I.select("State", <State>)
I.fill("ZIP code", <Zip Code>)

//Proceed to Shipping option
I.click("Continue To Shipping")
I.wait(5)

//Choose a shipping option
I.select("Faster Shipping")

//Proceed to payment
I.click("Continue To Payment")
I.wait(5)

//Choose payment method 
I.click("Credit Card")

//Fill in card details with invalid card
UI.context("iframe[title='Field container for: Card number']", ()=>{
	I.fill("Card Number", <Card Number>)
})
UI.context("iframe[title='Field container for: Name on card']", ()=>{
	I.fill("Name on card", <Name>)
})
UI.context("iframe[title='Field container for: Expiration date (MM / YY)']", ()=>{
	I.fill("Expiration date (MM / YY)", <Expiration Date>)
})
UI.context("iframe[title='Field container for: Security code']", ()=>{
	I.fill("Security Code", <CVV Code>)
})
I.click("Pay Now")
I.wait(10)

//Check for errors
I.see("Card was declined")
```
