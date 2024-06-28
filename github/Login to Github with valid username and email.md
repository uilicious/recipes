# Login to Github with valid username and email

This test case should validate that a user should be able to login to github with a valid username and email, and see the "Dashboard".

## Test Steps

This are the steps to perform to validate the test case:

1. Navigate to the login page
2. Fill in username field with a valid username
3. Fill in password field with a valid password
4. Click the Sign in button
5. Validate that "Dashboard" is displayed on the page

## Test Script

This is the test script to automate testing using the UI-licious test framework:
```javascript
I.goTo("https://github.com/login")
I.fill("Username or email", "<username>")
I.fill("Password","<password>")
I.click("Sign in")
I.see("Dashboard")
```
