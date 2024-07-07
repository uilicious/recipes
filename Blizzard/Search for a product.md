# Search for a product that exists and validate that the catalogue has results

This test case validates that when a user searches for a product that exists, the search results pages shows relevant products.

## Test Steps

These are the steps to perform to validate the test case:

1. Navigate to Nomatic's website
2. Click "Search"
3. Fill in "Camera Bag" in the search box
4. Validate that relavant products are shown

## Test Script

This test automation script validates the test case using the UI-licious Test Framework:
```javascript
//Navigate to website
I.goTo("https://uk.gear.blizzard.com/")

//Wait for page to load
I.wait(5)

//Close promo dialog
UI.context(".needsclick", ()=>{
	I.click("Close")
})

//Search for an item
I.fill("Search", "StarCraft")
I.pressEnter()

//Wait for page to load
I.wait(5)

//Validate that a relevant item appears
I.see("StarCraft Black Flatbill Snapback Hat")
```