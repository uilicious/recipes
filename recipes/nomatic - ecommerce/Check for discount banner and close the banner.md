# Check for discount banner and close the banner

This test case validates that when a discount banner appears it can be closed

## Test Steps

These are the steps to perform to validate the test case:

1. Navigate to Nomatic's website
2. Click "Best Sellers"
3. Wait for the Discount banner to appear
4. Close discount banner

## Test Script

This test automation script validates the test case using the UI-licious Test Framework:
```javascript
// Open the website
I.goTo("https://www.nomatic.com/collections/all-backpacks-bags")

// Click "Shop your country" to be redirected to subsite based on detected IP address
I.click("Shop your country")

// Navigate to Best Sellers Page through Menu Bar
I.click("Best Sellers")

// Check if the Discount Banner appears
if(I.see("Sign up for special offers and updates")){
        // Close the discount banner
		I.click("close")
	}else{
        // Print a message if the Discount Banner did not appear
		TEST.log.info("No Special Offer Popup Appeared")
	}
```
