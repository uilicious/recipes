# Error should be shown when user enters an invalid phone number in shipping details

This test case should validate that an error is shown when the user fills an invalid phone number for shipping information during checkout.

## Test Steps

This are the steps to perform to validate the test case:

1. Navigate to website
2. Add a product to cart
3. Proceed to checkout page
4. Fill in shipping information with valid address but invalid phone number
5. Fill in credit credit information
6. Validate that error "Enter a valid phone number" will appear

## Test Script

This is the test script to automate testing using the UI-licious test framework:

```javascript
// Navigate to site
I.goTo("https://www.tentree.ca/")

// Select region
I.click("United States")
I.wait(10)

// Dismiss promo banner
UI.context("iframe[title='Sign Up via Text for Offers']", ()=>{
	// Click the close icon
	I.click("#closeIconSvg")
})
I.wait(5)

// Hover to view expanded menu for "Women" category
I.hoverOn("Women")

// Click to select "New Arrivals" from "Women" category menu
I.click("New Arrivals")

// Dismiss promo banner
UI.context("iframe[title='Sign Up via Text for Offers']", ()=>{
	// Click the close icon
	I.click("#closeIconSvg")
})
I.click("United States")
I.wait(10)

I.scrollDown(500)

// Use an offset to click on the product thumbnail, 50px above the product title
I.click("TreeBlend Sleeveless Smocked Dress", 0, -50)

// Wait for product page to load
I.wait(10)

// Select size
I.click("M")

// Add to cart
I.click("Add To Bag")

// Go to check
I.click("Checkout")

// Fill in shipping information with valid email and name
I.fill("Email", "samanthasmith@inboxkitten.com")
I.fill("First Name", "Samantha")
I.fill("Last Name", "Smith")

// Fill in shipping information with valid US address
I.fill("Address", "Sample Address")
I.fill("City", "Sample City")
I.select("State", "Alaska")
I.fill("Postal Code", "99540")

// Fill in shipping information with INVALID US phone number
I.fill("Phone", "7882933073")

// Select credit card payment method
I.click("Credit Card")

// Fill in valid credit card number
UI.context("iframe[title='Field container for: Card number']", ()=>{
	I.fill("Card Number", "4242 4242 4242 4242")
})

// Fill in valid name on card
UI.context("iframe[title='Field container for: Name on card']", ()=>{
	I.fill("Name on card", "Samantha Smith")
})

// Fill in valid expiry credit card name and year
UI.context("iframe[title='Field container for: Expiration date (MM / YY)']", ()=>{
	I.fill("Expiration date (MM / YY)", "12/27")
})

// Fill in valid CVC code for credit card
UI.context("iframe[title='Field container for: Security code']", ()=>{
	I.fill("Security Code", "123")
})

// Submit checkout form
I.click("Pay Now")
I.wait(10)

// Validate error message is shown for invalid phone number
I.see("Enter a valid phone number")
```
