# Register a new account with valid Email Address and Password

This test case validates that when a user registers an account with valid email address and password, they should be automatically logged in and no longer see the "Create Account" option.

## Test Steps

These are the steps to perform to validate the test case:

1. Navigate to Agoda's website
2. Click "Create account"
3. Fill in "First name"
4. Fill in "Last name"
5. Fill in "Email"
6. Fill in "Password"
7. Fill in "Confirm Password"
8. Select "I agree to receive updates and promotions about Agoda and its affiliates or business partners via various channels, including Whatsapp. Opt out anytime. Read more in the Privacy Policy."
9. Click "Sign up"

## Test Script

This test automation script validates the test case using the UI-licious Test Framework:
```javascript
I.goTo("https://www.agoda.com/login")
// Click "Create account"
I.click("Create account")

// Use UI.context to switch into the iframe
UI.context("iframe[title='Universal login']",()=>{
    // Fill in "First name"
    I.fill("First name", "<first name>")
    // Fill in "Last name"
    I.fill("Last name", "<last name>")
    // Fill in "Email"
    I.fill("Email", "<email>")
    // Fill in "Password"
    I.fill("Password", "<password>")
    // Fill in "Confirm Password"
    I.fill("Confirm Password", "<password>")
    // Select "I agree to receive updates and promotions about Agoda and its affiliates or business partners via various channels, including Whatsapp. Opt out anytime. Read more in the Privacy Policy."
    I.select("I agree to receive updates and promotions about Agoda and its affiliates or business partners via various channels, including Whatsapp. Opt out anytime. Read more in the Privacy Policy.")
    // Click "Sign up"
    I.click("Sign up")
})
```