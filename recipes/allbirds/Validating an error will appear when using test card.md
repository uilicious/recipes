# Validating an error will appear when using test card

This test case should validate that an error will appear when using a test card when purchasing an item

## Test Steps

This are the steps to perform to validate the test case:

1. Navigate to the page
2. Choose an item to purchase
3. Proceed to checkout page
4. Fill in personal details
5. Fill in card details
6. Validate that error "Card was declined" will appear

## Test Script

This is the test script to automate testing using the UI-licious test framework:
```javascript
//Navigate to site
I.goTo("https://www.allbirds.com/")

//Choose country to ship
I.click("US")

//Choose what to buy
I.click("Men")
I.click("Shoes")
I.hoverOn("Men's Tree Runners")
I.click("9")
I.wait(10)
I.click("Proceed To Checkout")

//Fill in needed information
I.fill("Email", "johnkent@inboxkitten.com")
I.fill("First Name", "John")
I.fill("Last Name", "Kent")
I.fill("Address", "Sample Address")
I.fill("City", "Sample City")
I.select("State", "Alaska")
I.fill("ZIP code", "99950")
I.click("Continue To Shipping")
I.wait(5)
I.select("Faster Shipping")
I.click("Continue To Payment")
I.wait(5)

//Choose payment method and fill in card information
I.click("Credit Card")
UI.context("iframe[title='Field container for: Card number']", ()=>{
	I.fill("Card Number", "4242 4242 4242 4242")
})
UI.context("iframe[title='Field container for: Name on card']", ()=>{
	I.fill("Name on card", "John Kent")
})
UI.context("iframe[title='Field container for: Expiration date (MM / YY)']", ()=>{
	I.fill("Expiration date (MM / YY)", "12/27")
})
UI.context("iframe[title='Field container for: Security code']", ()=>{
	I.fill("Security Code", "123")
})
I.click("Pay Now")

//Check for errors
I.wait(10)
I.see("Card was declined")
```