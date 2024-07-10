# Accept cookie banner prompt

This test case validates that a cookie banner can be properly accepted

## Test Steps

These are the steps to perform to validate the test case:

1. Navigate to Modkat's website
2. Validate if cookie banner is appearing
3. Click on "Accept"
4. Validate if cookie banner has been dismissed/ not appearing

## Test Script

This test automation script validates the test case using the UI-licious Test Framework:

```javascript
//Navigate to website
I.goTo("https://modkat.com/")

//Validate if cookie banner is appearing
I.see("We value your privacy")

//Accept cookie banner
I.click("Accept")

//Wait for page to load
I.wait(5)

//Validate if cookie banner has beendisissed/ not appearing
I.dontSee("We Value your privacy")
```