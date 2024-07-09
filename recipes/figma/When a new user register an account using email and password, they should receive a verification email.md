# When a user registers an account using email and password, they should receive a verification email

This test case validates that when a user registers an account using email and password, they should see a message to check their inbox for a verification email.

## Test Steps

These are the steps to perform to validate the test case:

1. Navigate to Figma's website
2. Click "Get started for free"
3. Fill in a valid email
4. Fill in a strong password
5. Click "Create account"
6. Validate that "Check your inbox" is shown on screen

## Test Script

This test automation script validates the test case using the UI-licious Test Framework:
```javascript
I.goTo("https://www.figma.com/")
I.click("Get started for free")

// Use I.see to wait for and validate that the iframe appears
I.see("//iframe[@title='Auth']")

// Use UI.context to switch into the iframe
UI.context("//iframe[@title='Auth']", ()=>{
	// Fill in the required forms
	I.fill("Email", "<email>")
	I.fill("Password", "<password>")
	I.click("Create account")
	I.see("Check your inbox")
})
```
