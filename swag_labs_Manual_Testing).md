# SWAG LABS - TEST CASE DOCUMENT

**Application Under Test:** Swag Labs (https://www.saucedemo.com/)  
**Test Type:** Manual Functional Testing  
**Date:** January 6, 2026  
**Prepared By:** QA Team  
**Version:** 1.0

---

## TEST CASE SUMMARY

| **Category** | **Total Test Cases** |
|--------------|---------------------|
| Login Functionality | 7 |
| Product Listing & Sorting | 5 |
| Product Details | 3 |
| Shopping Cart | 6 |
| Checkout Process | 6 |
| UI/UX & Navigation | 4 |
| **TOTAL** | **31** |


## 1. LOGIN FUNCTIONALITY

### TC-001: Verify Login with Valid Standard User Credentials
**Priority:** High  
**Preconditions:** Application is accessible  
**Test Data:**  
- Username: standard_user  
- Password: secret_sauce

**Test Steps:**
1. Navigate to https://www.saucedemo.com/
2. Enter "standard_user" in the Username field
3. Enter "secret_sauce" in the Password field
4. Click on the "Login" button

**Expected Result:**
- User should be successfully logged in
- User should be redirected to the Products page
- Product inventory should be visible


### TC-002: Verify Login with Invalid Username
**Priority:** High  
**Preconditions:** Application is accessible  
**Test Data:**  
- Username: invalid_user  
- Password: secret_sauce

**Test Steps:**
1. Navigate to https://www.saucedemo.com/
2. Enter "invalid_user" in the Username field
3. Enter "secret_sauce" in the Password field
4. Click on the "Login" button

**Expected Result:**
- Login should fail
- Error message "Epic sadface: Username and password do not match any user in this service" should be displayed
- User should remain on the login page


### TC-003: Verify Login with Invalid Password
**Priority:** High  
**Preconditions:** Application is accessible  
**Test Data:**  
- Username: standard_user  
- Password: wrong_password

**Test Steps:**
1. Navigate to https://www.saucedemo.com/
2. Enter "standard_user" in the Username field
3. Enter "wrong_password" in the Password field
4. Click on the "Login" button

**Expected Result:**
- Login should fail
- Error message "Epic sadface: Username and password do not match any user in this service" should be displayed
- User should remain on the login page


### TC-004: Verify Login with Empty Credentials
**Priority:** High  
**Preconditions:** Application is accessible  
**Test Data:** None

**Test Steps:**
1. Navigate to https://www.saucedemo.com/
2. Leave Username field empty
3. Leave Password field empty
4. Click on the "Login" button

**Expected Result:**
- Login should fail
- Error message "Epic sadface: Username is required" should be displayed
- User should remain on the login page


### TC-005: Verify Login with Locked Out User
**Priority:** High  
**Preconditions:** Application is accessible  
**Test Data:**  
- Username: locked_out_user  
- Password: secret_sauce

**Test Steps:**
1. Navigate to https://www.saucedemo.com/
2. Enter "locked_out_user" in the Username field
3. Enter "secret_sauce" in the Password field
4. Click on the "Login" button

**Expected Result:**
- Login should fail
- Error message "Epic sadface: Sorry, this user has been locked out." should be displayed
- User should remain on the login page


### TC-006: Verify Error Message Close Button
**Priority:** Medium  
**Preconditions:** Error message is displayed after failed login  
**Test Data:**  
- Username: invalid_user  
- Password: secret_sauce

**Test Steps:**
1. Navigate to https://www.saucedemo.com/
2. Enter invalid credentials
3. Click on the "Login" button (error message appears)
4. Click on the "X" button on the error message

**Expected Result:**
- Error message should be closed/hidden
- Error styling on input fields should be removed
- User should be able to re-enter credentials


### TC-007: Verify Logout Functionality
**Priority:** High  
**Preconditions:** User is logged in  
**Test Data:** Standard user login

**Test Steps:**
1. Login with valid credentials
2. Click on the hamburger menu icon (top left)
3. Click on "Logout" from the menu

**Expected Result:**
- User should be logged out successfully
- User should be redirected to the login page
- Session should be cleared


## 2. PRODUCT LISTING & SORTING

### TC-008: Verify All Products are Displayed
**Priority:** High  
**Preconditions:** User is logged in as standard_user  
**Test Data:** N/A

**Test Steps:**
1. Login with valid standard_user credentials
2. Observe the products page

**Expected Result:**
- All 6 products should be displayed
- Each product should have: image, name, description, price, and "Add to cart" button
- Products should be displayed in grid format


### TC-009: Verify Sort by Name (A to Z)
**Priority:** Medium  
**Preconditions:** User is logged in and on Products page  
**Test Data:** N/A

**Test Steps:**
1. Login with valid credentials
2. Click on the sort dropdown
3. Select "Name (A to Z)"
4. Observe the product order

**Expected Result:**
- Products should be sorted alphabetically from A to Z
- First product should start with letter closest to A
- Sort order should be maintained


### TC-010: Verify Sort by Name (Z to A)
**Priority:** Medium  
**Preconditions:** User is logged in and on Products page  
**Test Data:** N/A

**Test Steps:**
1. Login with valid credentials
2. Click on the sort dropdown
3. Select "Name (Z to A)"
4. Observe the product order

**Expected Result:**
- Products should be sorted alphabetically from Z to A
- First product should start with letter closest to Z
- Sort order should be reversed

---

### TC-011: Verify Sort by Price (Low to High)
**Priority:** Medium  
**Preconditions:** User is logged in and on Products page  
**Test Data:** N/A

**Test Steps:**
1. Login with valid credentials
2. Click on the sort dropdown
3. Select "Price (low to high)"
4. Observe the product order and prices

**Expected Result:**
- Products should be sorted by price in ascending order
- Lowest priced item should appear first
- Highest priced item should appear last

---

### TC-012: Verify Sort by Price (High to Low)
**Priority:** Medium  
**Preconditions:** User is logged in and on Products page  
**Test Data:** N/A

**Test Steps:**
1. Login with valid credentials
2. Click on the sort dropdown
3. Select "Price (high to low)"
4. Observe the product order and prices

**Expected Result:**
- Products should be sorted by price in descending order
- Highest priced item should appear first
- Lowest priced item should appear last

---

## 3. PRODUCT DETAILS

### TC-013: Verify Product Image Click Navigation
**Priority:** Medium  
**Preconditions:** User is logged in and on Products page  
**Test Data:** Any product

**Test Steps:**
1. Login with valid credentials
2. Click on any product image
3. Observe the navigation

**Expected Result:**
- User should be navigated to product detail page
- Product details should be displayed (image, name, description, price)
- "Add to cart" and "Back to products" buttons should be visible

---

### TC-014: Verify Product Name Click Navigation
**Priority:** Medium  
**Preconditions:** User is logged in and on Products page  
**Test Data:** Any product

**Test Steps:**
1. Login with valid credentials
2. Click on any product name (title)
3. Observe the navigation

**Expected Result:**
- User should be navigated to product detail page
- Product details should match the selected product
- All product information should be displayed correctly

---

### TC-015: Verify Back to Products Button
**Priority:** Medium  
**Preconditions:** User is on product detail page  
**Test Data:** Any product

**Test Steps:**
1. Login with valid credentials
2. Navigate to any product detail page
3. Click on "Back to products" button
4. Observe the navigation

**Expected Result:**
- User should be navigated back to Products listing page
- All products should be visible
- Previous scroll position should ideally be maintained

---

## 4. SHOPPING CART

### TC-016: Verify Add to Cart from Products Page
**Priority:** High  
**Preconditions:** User is logged in and on Products page  
**Test Data:** Any product

**Test Steps:**
1. Login with valid credentials
2. Note the cart badge count (should be empty or show a number)
3. Click "Add to cart" button on any product
4. Observe the button text and cart badge

**Expected Result:**
- Button text should change from "Add to cart" to "Remove"
- Cart badge should increment by 1
- Product should be added to cart

---

### TC-017: Verify Remove from Cart on Products Page
**Priority:** High  
**Preconditions:** At least one item is added to cart  
**Test Data:** Any product already in cart

**Test Steps:**
1. Login and add a product to cart
2. Note the cart badge count
3. Click "Remove" button on the product
4. Observe the button text and cart badge

**Expected Result:**
- Button text should change from "Remove" to "Add to cart"
- Cart badge should decrement by 1
- Product should be removed from cart

---

### TC-018: Verify Cart Badge Counter
**Priority:** Medium  
**Preconditions:** User is logged in  
**Test Data:** Multiple products

**Test Steps:**
1. Login with valid credentials
2. Add 3 different products to cart
3. Observe the cart badge after each addition
4. Remove 1 product
5. Observe the cart badge

**Expected Result:**
- Cart badge should show "3" after adding 3 products
- Cart badge should show "2" after removing 1 product
- Count should be accurate at all times

---

### TC-019: Verify Shopping Cart Page Access
**Priority:** High  
**Preconditions:** User is logged in  
**Test Data:** At least one product in cart

**Test Steps:**
1. Login and add at least one product to cart
2. Click on the shopping cart icon
3. Observe the cart page

**Expected Result:**
- User should be navigated to cart page
- All added products should be listed
- Each product should show: quantity, name, description, price
- "Continue Shopping" and "Checkout" buttons should be visible

---

### TC-020: Verify Continue Shopping Button
**Priority:** Medium  
**Preconditions:** User is on shopping cart page  
**Test Data:** N/A

**Test Steps:**
1. Login and navigate to cart page
2. Click "Continue Shopping" button
3. Observe the navigation

**Expected Result:**
- User should be navigated back to Products page
- Cart contents should be preserved
- All products should be displayed

---

### TC-021: Verify Remove Product from Cart Page
**Priority:** High  
**Preconditions:** At least one product is in cart  
**Test Data:** Any product in cart

**Test Steps:**
1. Login and add products to cart
2. Navigate to cart page
3. Click "Remove" button on any product
4. Observe the cart contents and badge

**Expected Result:**
- Product should be removed from cart immediately
- Cart badge should decrement
- If cart becomes empty, appropriate message or empty state should be shown

---

## 5. CHECKOUT PROCESS

### TC-022: Verify Checkout Button Navigation
**Priority:** High  
**Preconditions:** At least one product is in cart  
**Test Data:** Any product

**Test Steps:**
1. Login and add product to cart
2. Navigate to cart page
3. Click "Checkout" button
4. Observe the navigation

**Expected Result:**
- User should be navigated to Checkout: Your Information page
- Form fields should be displayed: First Name, Last Name, Postal Code
- "Cancel" and "Continue" buttons should be visible

---

### TC-023: Verify Checkout with Valid Information
**Priority:** High  
**Preconditions:** User is on Checkout Information page  
**Test Data:**  
- First Name: John  
- Last Name: Doe  
- Postal Code: 12345

**Test Steps:**
1. Proceed to checkout page
2. Enter "John" in First Name field
3. Enter "Doe" in Last Name field
4. Enter "12345" in Postal Code field
5. Click "Continue" button

**Expected Result:**
- User should be navigated to Checkout: Overview page
- Cart items should be listed with prices
- Payment and shipping information should be displayed
- Total price calculation should be correct (Item total + Tax)
- "Finish" button should be visible

---

### TC-024: Verify Checkout with Empty Fields
**Priority:** High  
**Preconditions:** User is on Checkout Information page  
**Test Data:** None

**Test Steps:**
1. Proceed to checkout page
2. Leave all fields empty
3. Click "Continue" button

**Expected Result:**
- Error message "Error: First Name is required" should be displayed
- User should remain on the same page
- Fields should be highlighted with error styling

---

### TC-025: Verify Checkout Cancel Button
**Priority:** Medium  
**Preconditions:** User is on Checkout Information page  
**Test Data:** N/A

**Test Steps:**
1. Proceed to checkout page
2. Click "Cancel" button
3. Observe the navigation

**Expected Result:**
- User should be navigated back to Cart page
- Cart contents should be preserved
- No data should be submitted

---

### TC-026: Verify Order Completion
**Priority:** Critical  
**Preconditions:** User has completed checkout information and is on Overview page  
**Test Data:** Complete checkout flow

**Test Steps:**
1. Add products to cart
2. Complete checkout information form
3. Review order on Overview page
4. Click "Finish" button
5. Observe the confirmation page

**Expected Result:**
- User should be navigated to "Checkout: Complete!" page
- Success message should be displayed: "Thank you for your order!"
- Confirmation icon/image should be visible
- "Back Home" button should be displayed
- Cart should be empty (badge should not show any count)

---

### TC-027: Verify Back Home Button After Order
**Priority:** Medium  
**Preconditions:** User has completed an order  
**Test Data:** N/A

**Test Steps:**
1. Complete an order successfully
2. Click "Back Home" button on confirmation page
3. Observe the navigation

**Expected Result:**
- User should be navigated back to Products page
- Cart should be empty
- All products should be available for new purchase

---

## 6. UI/UX & NAVIGATION

### TC-028: Verify Hamburger Menu Functionality
**Priority:** Medium  
**Preconditions:** User is logged in  
**Test Data:** N/A

**Test Steps:**
1. Login with valid credentials
2. Click on hamburger menu icon (top left)
3. Observe the menu
4. Click on the "X" to close menu

**Expected Result:**
- Menu should slide in from left
- All menu items should be visible: All Items, About, Logout, Reset App State
- Menu should close when "X" is clicked
- Menu should overlay the page content

---

### TC-029: Verify About Link in Menu
**Priority:** Low  
**Preconditions:** User is logged in  
**Test Data:** N/A

**Test Steps:**
1. Login with valid credentials
2. Open hamburger menu
3. Click on "About" link
4. Observe the navigation

**Expected Result:**
- User should be redirected to Sauce Labs website (https://saucelabs.com/)
- Link should open in same or new tab depending on implementation
- Session should be maintained if user returns

---

### TC-030: Verify Reset App State
**Priority:** Medium  
**Preconditions:** User has items in cart  
**Test Data:** Products in cart

**Test Steps:**
1. Login and add multiple products to cart
2. Open hamburger menu
3. Click "Reset App State"
4. Observe the cart and product states

**Expected Result:**
- Cart should be cleared
- Cart badge should disappear
- All "Remove" buttons should revert to "Add to cart"
- Application should return to initial state

---

### TC-031: Verify Footer Links and Copyright
**Priority:** Low  
**Preconditions:** User is on any page of the application  
**Test Data:** N/A

**Test Steps:**
1. Login with valid credentials
2. Scroll to the bottom of the page
3. Observe footer content
4. Click on social media icons (Twitter, Facebook, LinkedIn)

**Expected Result:**
- Footer should be visible on all pages
- Copyright information should be displayed
- Social media icons should be clickable
- Social media links should open respective platforms
- Layout should be consistent across all pages

---

## TEST ENVIRONMENT

- **Browser:** Chrome (Latest), Firefox (Latest), Safari (Latest), Edge (Latest)
- **Operating System:** Windows 10/11, macOS, Linux
- **Screen Resolution:** 1920x1080, 1366x768, Mobile responsive
- **Network:** Broadband Internet Connection

---

## TEST DATA CREDENTIALS

| Username | Password | User Type |
|----------|----------|-----------|
| standard_user | secret_sauce | Standard User |
| locked_out_user | secret_sauce | Locked Out User |
| problem_user | secret_sauce | Problem User |
| performance_glitch_user | secret_sauce | Performance Glitch User |
| error_user | secret_sauce | Error User |
| visual_user | secret_sauce | Visual User |

---

## NOTES

1. All test cases should be executed in a clean browser session (clear cache and cookies)
2. Screenshots should be captured for failed test cases
3. Any UI inconsistencies or performance issues should be documented
4. Test execution should cover different user types to identify specific user issues
5. Responsive testing should be performed on mobile and tablet devices

---

**Document Status:** Approved  
**Next Review Date:** February 6, 2026  
**Approver:** QA Manager
