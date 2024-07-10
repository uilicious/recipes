# Search for a product that exists and validate that the catalogue has results

This test case validates that when a user searches for a product that exists, the search results pages shows relevant products.

## Test Steps

These are the steps to perform to validate the test case:

1. Navigate to Tentree's website
2. Click "Search"
3. Fill in "Jumper" in the search box
4. Validate that relavant products are shown

## Test Script

This test automation script validates the test case using the UI-licious Test Framework:
```javascript
// Navigate to site
I.goTo("https://www.tentree.ca/")

// Select region
I.click("United States")
I.wait(5)

// Dismiss promo banner
UI.context("iframe[title='Sign Up via Text for Offers']", ()=>{
	// Click the close icon
	I.click("#closeIconSvg")
})
I.wait(5)

//Click on search bar
UI.context("#menu-button", ()=>{
	I.click("#desktop-searchbar")
})

//Fill in search bar
I.fill("Search", "Jumper")
I.wait(5)

//Validate that relevant item exists
I.see("Highline Mock Neck Sweater")
```
