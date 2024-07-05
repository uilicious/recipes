# Validate error when invalid phone number is inputted

This test case should validate that an error will appear when using a test card when purchasing an item

## Test Steps

This are the steps to perform to validate the test case:

1. Navigate to the page
2. Choose an item to purchase
3. Proceed to checkout page
4. Fill in personal details
5. Fill in card details
6. Validate that error "Enter a valid phone number" will appear

## Test Script

This is the test script to automate testing using the UI-licious test framework:
```javascript
//Navigate to site
I.goTo("https://www.tentree.ca/")
I.click("United States")
I.wait(10)
UI.context("iframe[title='Sign Up via Text for Offers']", ()=>{
	I.click("#closeIconSvg")
})
I.wait(5)


//Choose something to buy and checkout
I.hoverOn("Women")
I.click("New Arrivals")

UI.context("iframe[title='Sign Up via Text for Offers']", ()=>{
	I.click("#closeIconSvg")
})
I.click("United States")

I.wait(10)
I.scrollDown(500)
I.click("TreeBlend Sleeveless Smocked Dress", 0, -50)
I.wait(10)
I.click("M")
I.click("Add To Bag")
I.click("Checkout")

//Fill in needed details
I.fill("Email", "samanthasmith@inboxkitten.com")
I.fill("First Name", "Samantha")
I.fill("Last Name", "Smith")
I.fill("Address", "Sample Address")
I.fill("City", "Sample City")
I.select("State", "Alaska")
I.fill("Postal Code", "99540")
I.fill("Phone", "7882933073")

//Choose payment method and fill in card information
I.click("Credit Card")
UI.context("iframe[title='Field container for: Card number']", ()=>{
	I.fill("Card Number", "4242 4242 4242 4242")
})
UI.context("iframe[title='Field container for: Name on card']", ()=>{
	I.fill("Name on card", "Samantha Smith")
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
I.see("Enter a valid phone number")
```