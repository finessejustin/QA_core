# 24-Hour Selenium Python Bootcamp: Beginner to Hero

## 🎯 Course Overview
This intensive bootcamp takes you from zero to hero in web automation with Selenium and Python. Each hour includes theory, practical examples, and real-world projects.

---

## 📚 **HOURS 1-4: FOUNDATIONS**

### **Hour 1: Environment Setup & First Steps**

#### What You'll Learn
- Install Python, Selenium, and ChromeDriver
- Understand browser automation basics
- Write your first Selenium script

#### Practical Setup
```python
# Install required packages
# Run in terminal: pip install selenium

from selenium import webdriver
from selenium.webdriver.common.by import By
import time

# Initialize browser
driver = webdriver.Chrome()

# Navigate to a website
driver.get("https://www.python.org")

# Print page title
print(f"Page title: {driver.title}")

# Take screenshot
driver.save_screenshot("python_homepage.png")

# Wait 3 seconds to see the page
time.sleep(3)

# Close browser
driver.quit()
```

#### Real-World Exercise
**Project: Website Status Checker**
```python
from selenium import webdriver
import time

def check_website_status(url):
    """Check if a website loads successfully"""
    driver = webdriver.Chrome()
    try:
        driver.get(url)
        if driver.title:
            print(f"✓ {url} is UP - Title: {driver.title}")
            return True
        else:
            print(f"✗ {url} is DOWN")
            return False
    except Exception as e:
        print(f"✗ Error accessing {url}: {e}")
        return False
    finally:
        driver.quit()

# Test multiple websites
websites = [
    "https://www.google.com",
    "https://www.github.com",
    "https://www.stackoverflow.com"
]

for site in websites:
    check_website_status(site)
    time.sleep(2)
```

---

### **Hour 2: Locating Elements**

#### What You'll Learn
- 8 ways to find elements on a webpage
- When to use each locator strategy
- Best practices for element selection

#### Locator Strategies
```python
from selenium import webdriver
from selenium.webdriver.common.by import By

driver = webdriver.Chrome()
driver.get("https://www.example.com")

# 1. By ID (most reliable)
element = driver.find_element(By.ID, "username")

# 2. By NAME
element = driver.find_element(By.NAME, "email")

# 3. By CLASS_NAME
element = driver.find_element(By.CLASS_NAME, "btn-primary")

# 4. By TAG_NAME
element = driver.find_element(By.TAG_NAME, "h1")

# 5. By LINK_TEXT (exact match)
element = driver.find_element(By.LINK_TEXT, "Click Here")

# 6. By PARTIAL_LINK_TEXT
element = driver.find_element(By.PARTIAL_LINK_TEXT, "Click")

# 7. By CSS_SELECTOR (very powerful)
element = driver.find_element(By.CSS_SELECTOR, "div.container > input[type='text']")

# 8. By XPATH (most flexible)
element = driver.find_element(By.XPATH, "//input[@id='username']")

driver.quit()
```

#### Real-World Exercise
**Project: Google Search Automation**
```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
import time

def google_search(query):
    """Perform a Google search and print top 5 results"""
    driver = webdriver.Chrome()
    driver.get("https://www.google.com")
    
    # Accept cookies if present
    try:
        accept_button = driver.find_element(By.XPATH, "//button[contains(text(), 'Accept') or contains(text(), 'I agree')]")
        accept_button.click()
        time.sleep(1)
    except:
        pass
    
    # Find search box and enter query
    search_box = driver.find_element(By.NAME, "q")
    search_box.send_keys(query)
    search_box.send_keys(Keys.RETURN)
    
    # Wait for results to load
    time.sleep(2)
    
    # Get search results
    results = driver.find_elements(By.CSS_SELECTOR, "h3")
    
    print(f"\nTop 5 results for '{query}':")
    for i, result in enumerate(results[:5], 1):
        print(f"{i}. {result.text}")
    
    driver.quit()

# Test the function
google_search("Python Selenium tutorial")
```

---

### **Hour 3: Interacting with Elements**

#### What You'll Learn
- Click buttons and links
- Fill out forms
- Select dropdown options
- Handle checkboxes and radio buttons

#### Interaction Methods
```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.select import Select
import time

driver = webdriver.Chrome()
driver.get("https://www.example-form.com")

# Click a button
button = driver.find_element(By.ID, "submit-btn")
button.click()

# Type into text field
text_field = driver.find_element(By.NAME, "username")
text_field.send_keys("john_doe")

# Clear a field
text_field.clear()
text_field.send_keys("jane_doe")

# Select from dropdown
dropdown = Select(driver.find_element(By.ID, "country"))
dropdown.select_by_visible_text("United States")
# or
dropdown.select_by_value("us")
# or
dropdown.select_by_index(1)

# Handle checkbox
checkbox = driver.find_element(By.ID, "agree-terms")
if not checkbox.is_selected():
    checkbox.click()

# Handle radio button
radio = driver.find_element(By.CSS_SELECTOR, "input[value='male']")
radio.click()

driver.quit()
```

#### Real-World Exercise
**Project: Login Automation**
```python
from selenium import webdriver
from selenium.webdriver.common.by import By
import time

def login_to_website(url, username, password):
    """Automate login to a website"""
    driver = webdriver.Chrome()
    driver.get(url)
    driver.maximize_window()
    
    try:
        # Find and fill username
        username_field = driver.find_element(By.ID, "username")
        username_field.clear()
        username_field.send_keys(username)
        
        # Find and fill password
        password_field = driver.find_element(By.ID, "password")
        password_field.clear()
        password_field.send_keys(password)
        
        # Click login button
        login_button = driver.find_element(By.CSS_SELECTOR, "button[type='submit']")
        login_button.click()
        
        time.sleep(3)
        
        # Check if login was successful
        if "dashboard" in driver.current_url or "welcome" in driver.current_url.lower():
            print("✓ Login successful!")
        else:
            print("✗ Login may have failed")
        
        # Take screenshot
        driver.save_screenshot("after_login.png")
        
    except Exception as e:
        print(f"Error during login: {e}")
    finally:
        time.sleep(2)
        driver.quit()

# Example usage (replace with actual website)
# login_to_website("https://example.com/login", "testuser", "testpass123")
```

---

### **Hour 4: Waits and Synchronization**

#### What You'll Learn
- Implicit vs Explicit waits
- Expected Conditions
- Handling dynamic content

#### Wait Strategies
```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
import time

driver = webdriver.Chrome()

# 1. IMPLICIT WAIT (applies to all elements)
driver.implicitly_wait(10)  # Wait up to 10 seconds for elements

# 2. EXPLICIT WAIT (for specific conditions)
driver.get("https://www.example.com")

# Wait for element to be clickable
wait = WebDriverWait(driver, 10)
element = wait.until(EC.element_to_be_clickable((By.ID, "submit-btn")))
element.click()

# Wait for element to be visible
element = wait.until(EC.visibility_of_element_located((By.CLASS_NAME, "alert")))

# Wait for element to be present
element = wait.until(EC.presence_of_element_located((By.XPATH, "//div[@id='result']")))

# Wait for title to contain text
wait.until(EC.title_contains("Dashboard"))

# Wait for URL to change
wait.until(EC.url_contains("success"))

# 3. HARD WAIT (use sparingly)
time.sleep(2)  # Pause for 2 seconds

driver.quit()
```

#### Real-World Exercise
**Project: Wait for AJAX Content**
```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

def scrape_dynamic_content(url):
    """Scrape content that loads via AJAX"""
    driver = webdriver.Chrome()
    driver.get(url)
    
    # Wait for dynamic content to load
    wait = WebDriverWait(driver, 15)
    
    try:
        # Wait for loading spinner to disappear
        wait.until(EC.invisibility_of_element_located((By.CLASS_NAME, "loading-spinner")))
        
        # Wait for content to appear
        content = wait.until(EC.presence_of_element_located((By.ID, "dynamic-content")))
        
        print("Content loaded:")
        print(content.text)
        
        # Wait for additional elements
        items = wait.until(EC.presence_of_all_elements_located((By.CLASS_NAME, "item")))
        print(f"\nFound {len(items)} items")
        
        for i, item in enumerate(items[:5], 1):
            print(f"{i}. {item.text}")
            
    except Exception as e:
        print(f"Error: {e}")
    finally:
        driver.quit()

# Example usage
# scrape_dynamic_content("https://example.com/ajax-content")
```

---

## 📚 **HOURS 5-8: INTERMEDIATE SKILLS**

### **Hour 5: Handling Multiple Windows & Frames**

#### What You'll Learn
- Switch between windows/tabs
- Work with iframes
- Handle popup windows

#### Window Handling
```python
from selenium import webdriver
from selenium.webdriver.common.by import By
import time

driver = webdriver.Chrome()
driver.get("https://www.example.com")

# Get current window handle
main_window = driver.current_window_handle
print(f"Main window: {main_window}")

# Click link that opens new tab
link = driver.find_element(By.LINK_TEXT, "Open in New Tab")
link.click()

time.sleep(2)

# Get all window handles
all_windows = driver.window_handles
print(f"Total windows: {len(all_windows)}")

# Switch to new window
for window in all_windows:
    if window != main_window:
        driver.switch_to.window(window)
        print(f"Switched to: {driver.title}")
        break

# Do something in new window
print(driver.current_url)

# Close current window
driver.close()

# Switch back to main window
driver.switch_to.window(main_window)

driver.quit()
```

#### Frame Handling
```python
from selenium import webdriver
from selenium.webdriver.common.by import By

driver = webdriver.Chrome()
driver.get("https://www.example-with-frames.com")

# Switch to frame by name
driver.switch_to.frame("frameName")

# Switch to frame by index
driver.switch_to.frame(0)

# Switch to frame by WebElement
frame_element = driver.find_element(By.ID, "myframe")
driver.switch_to.frame(frame_element)

# Interact with elements inside frame
element = driver.find_element(By.ID, "button-in-frame")
element.click()

# Switch back to main content
driver.switch_to.default_content()

driver.quit()
```

#### Real-World Exercise
**Project: Multi-Tab Price Comparison**
```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
import time

def compare_prices(product_name):
    """Compare prices across multiple e-commerce sites"""
    driver = webdriver.Chrome()
    driver.maximize_window()
    
    websites = [
        "https://www.amazon.com",
        "https://www.ebay.com",
        "https://www.walmart.com"
    ]
    
    prices = {}
    
    for site in websites:
        try:
            # Open new tab
            driver.execute_script(f"window.open('{site}', '_blank');")
            time.sleep(2)
            
            # Switch to new tab
            driver.switch_to.window(driver.window_handles[-1])
            
            # Search for product
            wait = WebDriverWait(driver, 10)
            search_box = wait.until(EC.presence_of_element_located((By.NAME, "q")))
            search_box.send_keys(product_name)
            search_box.submit()
            
            time.sleep(3)
            
            # Extract price (simplified - actual selectors vary)
            try:
                price_element = driver.find_element(By.CSS_SELECTOR, ".price, .a-price-whole, .price-current")
                prices[site] = price_element.text
                print(f"{site}: {price_element.text}")
            except:
                prices[site] = "Price not found"
                print(f"{site}: Price not found")
            
        except Exception as e:
            print(f"Error on {site}: {e}")
            prices[site] = "Error"
    
    driver.quit()
    return prices

# Example usage
# compare_prices("wireless mouse")
```

---

### **Hour 6: JavaScript Execution & Advanced Interactions**

#### What You'll Learn
- Execute JavaScript in the browser
- Scroll pages
- Handle hidden elements
- Take full-page screenshots

#### JavaScript Execution
```python
from selenium import webdriver
from selenium.webdriver.common.by import By
import time

driver = webdriver.Chrome()
driver.get("https://www.example.com")

# Execute simple JavaScript
driver.execute_script("alert('Hello from Selenium!');")
time.sleep(2)
driver.switch_to.alert.accept()

# Scroll to bottom of page
driver.execute_script("window.scrollTo(0, document.body.scrollHeight);")

# Scroll to specific element
element = driver.find_element(By.ID, "footer")
driver.execute_script("arguments[0].scrollIntoView();", element)

# Click hidden element using JS
hidden_button = driver.find_element(By.ID, "hidden-btn")
driver.execute_script("arguments[0].click();", hidden_button)

# Change element properties
driver.execute_script("arguments[0].style.border='3px solid red'", element)

# Get return value from JS
page_height = driver.execute_script("return document.body.scrollHeight;")
print(f"Page height: {page_height}px")

# Get element attributes
element_value = driver.execute_script("return arguments[0].getAttribute('value');", element)

driver.quit()
```

#### Real-World Exercise
**Project: Infinite Scroll Instagram-like Feed**
```python
from selenium import webdriver
from selenium.webdriver.common.by import By
import time

def scrape_infinite_scroll(url, scroll_pause_time=2, max_scrolls=10):
    """Scrape content from infinite scroll page"""
    driver = webdriver.Chrome()
    driver.get(url)
    driver.maximize_window()
    
    # Get initial scroll height
    last_height = driver.execute_script("return document.body.scrollHeight")
    
    items_scraped = set()
    scrolls = 0
    
    while scrolls < max_scrolls:
        # Scroll down to bottom
        driver.execute_script("window.scrollTo(0, document.body.scrollHeight);")
        
        # Wait for new content to load
        time.sleep(scroll_pause_time)
        
        # Scrape items currently visible
        items = driver.find_elements(By.CLASS_NAME, "post-item")
        for item in items:
            item_id = item.get_attribute("data-id")
            if item_id and item_id not in items_scraped:
                items_scraped.add(item_id)
                print(f"Scraped item: {item.text[:50]}...")
        
        # Calculate new scroll height
        new_height = driver.execute_script("return document.body.scrollHeight")
        
        # Check if we've reached the bottom
        if new_height == last_height:
            print("Reached bottom of page")
            break
        
        last_height = new_height
        scrolls += 1
    
    print(f"\nTotal items scraped: {len(items_scraped)}")
    driver.quit()
    return items_scraped

# Example usage
# scrape_infinite_scroll("https://example.com/feed")
```

---

### **Hour 7: File Upload & Download**

#### What You'll Learn
- Upload files using Selenium
- Handle file downloads
- Manage download directories

#### File Upload
```python
from selenium import webdriver
from selenium.webdriver.common.by import By
import os
import time

driver = webdriver.Chrome()
driver.get("https://www.example.com/upload")

# Method 1: Direct file path
file_input = driver.find_element(By.CSS_SELECTOR, "input[type='file']")
file_path = os.path.abspath("test_file.pdf")
file_input.send_keys(file_path)

# Submit the form
submit_button = driver.find_element(By.ID, "upload-btn")
submit_button.click()

time.sleep(3)

# Verify upload success
success_message = driver.find_element(By.CLASS_NAME, "success-msg")
print(success_message.text)

driver.quit()
```

#### File Download
```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.chrome.options import Options
import time
import os

# Set download directory
download_dir = os.path.abspath("downloads")
os.makedirs(download_dir, exist_ok=True)

# Configure Chrome options
chrome_options = Options()
prefs = {
    "download.default_directory": download_dir,
    "download.prompt_for_download": False,
    "download.directory_upgrade": True,
    "safebrowsing.enabled": True
}
chrome_options.add_experimental_option("prefs", prefs)

driver = webdriver.Chrome(options=chrome_options)
driver.get("https://www.example.com/downloads")

# Click download link
download_link = driver.find_element(By.LINK_TEXT, "Download Report")
download_link.click()

# Wait for download to complete
time.sleep(5)

# Verify file was downloaded
files = os.listdir(download_dir)
print(f"Downloaded files: {files}")

driver.quit()
```

#### Real-World Exercise
**Project: Automated Report Downloader**
```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
from selenium.webdriver.chrome.options import Options
import time
import os
from datetime import datetime

def download_monthly_reports(url, username, password, download_folder="reports"):
    """Login and download all monthly reports"""
    
    # Setup download directory
    download_dir = os.path.abspath(download_folder)
    os.makedirs(download_dir, exist_ok=True)
    
    # Configure browser
    chrome_options = Options()
    prefs = {
        "download.default_directory": download_dir,
        "download.prompt_for_download": False,
    }
    chrome_options.add_experimental_option("prefs", prefs)
    
    driver = webdriver.Chrome(options=chrome_options)
    driver.get(url)
    
    try:
        # Login
        wait = WebDriverWait(driver, 10)
        username_field = wait.until(EC.presence_of_element_located((By.ID, "username")))
        username_field.send_keys(username)
        
        password_field = driver.find_element(By.ID, "password")
        password_field.send_keys(password)
        
        login_button = driver.find_element(By.CSS_SELECTOR, "button[type='submit']")
        login_button.click()
        
        # Navigate to reports page
        wait.until(EC.url_contains("dashboard"))
        reports_link = wait.until(EC.element_to_be_clickable((By.LINK_TEXT, "Reports")))
        reports_link.click()
        
        # Find all download links
        download_links = wait.until(EC.presence_of_all_elements_located((By.CLASS_NAME, "download-report")))
        
        print(f"Found {len(download_links)} reports to download")
        
        # Download each report
        for i, link in enumerate(download_links, 1):
            report_name = link.get_attribute("data-report-name")
            print(f"Downloading {i}/{len(download_links)}: {report_name}")
            link.click()
            time.sleep(3)  # Wait for download
        
        print(f"\n✓ All reports downloaded to: {download_dir}")
        
        # List downloaded files
        files = os.listdir(download_dir)
        print(f"Downloaded {len(files)} files:")
        for file in files:
            print(f"  - {file}")
            
    except Exception as e:
        print(f"Error: {e}")
    finally:
        driver.quit()

# Example usage
# download_monthly_reports("https://example.com/login", "user@example.com", "password123")
```

---

### **Hour 8: Taking Screenshots & Visual Testing**

#### What You'll Learn
- Capture screenshots
- Take full-page screenshots
- Element-specific screenshots
- Visual regression testing basics

#### Screenshot Techniques
```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from datetime import datetime
import os

driver = webdriver.Chrome()
driver.maximize_window()
driver.get("https://www.example.com")

# Create screenshots directory
os.makedirs("screenshots", exist_ok=True)

# 1. Full page screenshot
driver.save_screenshot("screenshots/full_page.png")

# 2. Screenshot with timestamp
timestamp = datetime.now().strftime("%Y%m%d_%H%M%S")
driver.save_screenshot(f"screenshots/page_{timestamp}.png")

# 3. Element screenshot
element = driver.find_element(By.ID, "main-content")
element.screenshot("screenshots/element.png")

# 4. Screenshot in different viewport sizes
sizes = [(1920, 1080), (1366, 768), (375, 667)]
for width, height in sizes:
    driver.set_window_size(width, height)
    driver.save_screenshot(f"screenshots/viewport_{width}x{height}.png")

driver.quit()
```

#### Real-World Exercise
**Project: Automated Visual Testing for Website**
```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from datetime import datetime
import os
import time

class VisualTester:
    def __init__(self, base_url):
        self.base_url = base_url
        self.driver = webdriver.Chrome()
        self.driver.maximize_window()
        self.screenshot_dir = f"visual_tests_{datetime.now().strftime('%Y%m%d_%H%M%S')}"
        os.makedirs(self.screenshot_dir, exist_ok=True)
        
    def test_page(self, path, page_name):
        """Test a specific page and capture screenshots"""
        url = f"{self.base_url}{path}"
        print(f"\nTesting: {page_name}")
        print(f"URL: {url}")
        
        try:
            self.driver.get(url)
            time.sleep(2)
            
            # Desktop view
            self.driver.set_window_size(1920, 1080)
            self.driver.save_screenshot(f"{self.screenshot_dir}/{page_name}_desktop.png")
            print("✓ Desktop screenshot captured")
            
            # Tablet view
            self.driver.set_window_size(768, 1024)
            self.driver.save_screenshot(f"{self.screenshot_dir}/{page_name}_tablet.png")
            print("✓ Tablet screenshot captured")
            
            # Mobile view
            self.driver.set_window_size(375, 667)
            self.driver.save_screenshot(f"{self.screenshot_dir}/{page_name}_mobile.png")
            print("✓ Mobile screenshot captured")
            
            # Check for broken images
            images = self.driver.find_elements(By.TAG_NAME, "img")
            broken_images = []
            for img in images:
                if self.driver.execute_script("return arguments[0].complete && arguments[0].naturalHeight === 0", img):
                    broken_images.append(img.get_attribute("src"))
            
            if broken_images:
                print(f"⚠ Found {len(broken_images)} broken images")
                for img_url in broken_images:
                    print(f"  - {img_url}")
            else:
                print("✓ No broken images found")
                
        except Exception as e:
            print(f"✗ Error testing {page_name}: {e}")
    
    def run_visual_tests(self):
        """Run tests on multiple pages"""
        pages = [
            ("/", "homepage"),
            ("/about", "about"),
            ("/products", "products"),
            ("/contact", "contact")
        ]
        
        print(f"Starting visual tests for {self.base_url}")
        print(f"Screenshots will be saved to: {self.screenshot_dir}")
        
        for path, name in pages:
            self.test_page(path, name)
        
        print(f"\n✓ Visual testing complete!")
        print(f"Results saved in: {self.screenshot_dir}")
        
    def close(self):
        self.driver.quit()

# Example usage
# tester = VisualTester("https://www.example.com")
# tester.run_visual_tests()
# tester.close()
```

---

## 📚 **HOURS 9-12: ADVANCED TECHNIQUES**

### **Hour 9: Handling Alerts, Popups & Modals**

#### What You'll Learn
- Handle JavaScript alerts
- Accept/dismiss confirmation dialogs
- Work with modal windows
- Handle browser notifications

#### Alert Handling
```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
import time

driver = webdriver.Chrome()
driver.get("https://www.example.com")

# Trigger alert
button = driver.find_element(By.ID, "alert-btn")
button.click()

# Wait for alert to appear
wait = WebDriverWait(driver, 10)
wait.until(EC.alert_is_present())

# Switch to alert
alert = driver.switch_to.alert

# Get alert text
print(f"Alert text: {alert.text}")

# Accept alert (click OK)
alert.accept()

# For confirmation dialogs
# Click button that triggers confirm
confirm_button = driver.find_element(By.ID, "confirm-btn")
confirm_button.click()

# Wait and get alert
wait.until(EC.alert_is_present())
alert = driver.switch_to.alert

# Dismiss (click Cancel)
alert.dismiss()

# For prompt dialogs
prompt_button = driver.find_element(By.ID, "prompt-btn")
prompt_button.click()

wait.until(EC.alert_is_present())
alert = driver.switch_to.alert

# Send text to prompt
alert.send_keys("Hello, Selenium!")
alert.accept()

driver.quit()
```

#### Real-World Exercise
**Project: Form Submission with Validation Alerts**
```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
import time

def fill_form_with_validation(url, form_data):
    """Fill form and handle validation alerts"""
    driver = webdriver.Chrome()
    driver.get(url)
    wait = WebDriverWait(driver, 10)
    
    try:
        # Fill form fields
        for field_id, value in form_data.items():
            field = wait.until(EC.presence_of_element_located((By.ID, field_id)))
            field.clear()
            field.send_keys(value)
            print(f"✓ Filled {field_id}: {value}")
        
        # Submit form
        submit_button = driver.find_element(By.ID, "submit")
        submit_button.click()
        
        # Handle potential validation alert
        try:
            wait.until(EC.alert_is_present(), timeout=3)
            alert = driver.switch_to.alert
            alert_message = alert.text
            print(f"\n⚠ Validation Alert: {alert_message}")
            alert.accept()
            
            # Fix the issue and resubmit
            print("Attempting to fix and resubmit...")
            # Add fixing logic here
            
        except:
            print("\n✓ No validation errors")
        
        # Check for success message
        try:
            success_msg = wait.until(EC.presence_of_element_located((By.CLASS_NAME, "success")))
            print(f"✓ Success: {success_msg.text}")
        except:
            print("✗ Submission may have failed")
        
        time.sleep(2)
        
    except Exception as e:
        print(f"Error: {e}")
    finally:
        driver.quit()

# Example usage
form_data = {
    "name": "John Doe",
    "email": "john@example.com",
    "phone": "1234567890",
    "message": "Test message"
}

# fill_form_with_validation("https://example.com/contact", form_data)
```

---

### **Hour 10: Browser Configuration & Options**

#### What You'll Learn
- Run browsers in headless mode
- Disable images for faster scraping
- Set custom user agents
- Handle browser profiles

#### Chrome Options
```python
from selenium import webdriver
from selenium.webdriver.chrome.options import Options
from selenium.webdriver.common.by import By

# Create options object
chrome_options = Options()

# 1. Headless mode (no GUI)
chrome_options.add_argument("--headless")

# 2. Disable GPU (for headless)
chrome_options.add_argument