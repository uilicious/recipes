# Login to Github with invalid username and password

This test case should validate that a user shouldn't be able to login with invalid username and password

## Test Steps

This are the steps to perform to validate the test case:

1. Navigate to the login page
2. Fill in username field with a invalid username
3. Fill in password field with a invalid password
4. Click the Sign in button
5. Validate that the error message "Incorrect username or password" appears

## Test Script

This is the test script to automate testing using the UI-licious test framework:
```javascript
I.goTo("https://github.com/login")
I.fill("Username or email", "<invalid username>")
I.fill("Password","<invalid password>")
I.click("Sign in")
I.see("Incorrect username or password")
```
