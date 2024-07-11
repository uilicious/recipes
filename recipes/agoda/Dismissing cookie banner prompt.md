# Dismissing cookie banner prompt

This test case validates that a cookie banner can be properly dismissed

## Test Steps

These are the steps to perform to validate the test case:

1. Navigate to Agoda's website
2. Validate if cookie banner is appearing
3. Click on "Dismiss"
4. Validate if cookie banner has been dismissed

## Test Script

This test automation script validates the test case using the UI-licious Test Framework:

```javascript
//Naviate to page
I.goTo("https://www.agoda.com/")

//Validate if cookie banner is appearing
I.see("Manage Cookie Preference")

//Click "Dismiss" to dismiss cookie banner
I.click("Dismiss")

//Validate if cookie banner is dismissed
I.dontSee("Manage Cookie Preference")
```
