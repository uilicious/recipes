# Error should be shown when user enters an invalid card in payment details

This test case should validate that an error is shown when the user enters an invalid card for payment during checkout.

## Test Steps

This are the steps to perform to validate the test case:

1. Navigate to modkat's website
2. Add a product to cart
3. Proceed to checkout page
4. Fill in shipping information with valid information
5. Fill in card details with invalid card
6. Validate that error "Card was declined" will appear

## Test Script

This is the test script to automate testing using the UI-licious test framework:
```javascript
//Navigate to website
I.goTo("https://modkat.com/")

//close the newsletter
I.click("Close")

//Search for an item
I.fill("Search", "Modkat XL")
I.pressEnter()
I.wait(5)

//Choose an item
I.click("Modkat XL Litter Box")

//Choose a color
I.click("Gray")

//Add to cart
I.click("Add To Cart")

//Proceed to checkout
I.click("Checkout")

//Fill in shipping details
I.fill("Email", <Email>)
I.fill("First Name", <First Name>)
I.fill("Last Name", <Last Name>)
I.fill("Address", <Address>)
I.fill("City", <City>)
I.select("State", <State>)
I.fill("ZIP code", <Zip Code>)

//Choose shipping option
I.click("Standard Shipping")

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
	I.fill("Security Code", <Security Code>)
})
I.click("Pay Now")
I.wait(10)

//Check for errors
I.see("Card was declined")
```
