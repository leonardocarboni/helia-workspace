---
triggers:
  - browse
  - web
  - internet
  - search online
  - check website
---

# Web Browsing & Chromium Usage

You are running in a sandbox environment with a Chromium-loaded image. You have access to the internet.

## When to use this skill
Use this when the user asks to verify information online, look up documentation, or interact with web applications.

## Guidelines

### 1. Tool Selection
* **Primary:** Use the native `browse` tool if available for simple page visits and reading.
* **Advanced:** If complex interaction (clicking, filling forms) or JavaScript rendering is required, use Python with **Selenium** or **Playwright**. Chromium is pre-installed.

### 2. Navigation Best Practices
* **Verification:** Always check the current URL and page title after navigating to ensure you are where you expect to be.
* **Rate Limiting:** Do not flood websites with requests. Add `time.sleep()` in loops when using Python scripts.
* **403/404 Handling:** If you encounter a block, try accessing the Google Cache version or the Internet Archive (Wayback Machine).

### 3. Headless Usage (Python)
If writing a script, always run the browser in **headless mode**.
```python
from selenium import webdriver
options = webdriver.ChromeOptions()
options.add_argument('--headless')
options.add_argument('--no-sandbox')
driver = webdriver.Chrome(options=options)

```

### 4. Safety

* Do not log into personal accounts unless explicitly instructed and credentials are provided safely.
* Do not download executables (.exe, .dmg) unless explicitly asked.
