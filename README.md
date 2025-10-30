**Web Scraper with Selenium & Async HTTP Requests
**
This Python script is a robust web scraping tool designed to extract detailed information from a list of websites. It combines asynchronous HTTP requests with Selenium-based browser automation for dynamic content, enabling the extraction of both static and dynamic data. It also features checkpointing to resume progress without duplicating work.

Key Features

Input/Output Handling

Reads a CSV file (INPUT_CSV) containing a list of website URLs.

Outputs results to OUTPUT_CSV.

Supports temporary CSV saving for progress (TEMP_OUTPUT_CSV).

Website Status Checking

Quickly determines if a website is accessible (Proper) or broken (Broken) using HTTP requests.

Social Media Detection

Detects links to Instagram, Facebook, Twitter, Pinterest, and LinkedIn.

Uses regex patterns to handle common variations and redirects.

Indicates overall social media presence.

Email and Phone Extraction

Extracts valid email addresses from website content.

Extracts US phone numbers with multiple validation steps:

Checks formatting.

Filters out fake or sequential numbers.

Ensures context relevance (e.g., "contact" or "phone").

Street Address Extraction

Detects likely US street addresses, including suite and city/state/ZIP formatting.

Dynamic Content Scraping

Uses Selenium WebDriver pool (SeleniumPool) to scrape JavaScript-rendered pages.

Detects integrated videos (YouTube, Vimeo, Wistia, etc.).

Checks for D2C (Direct-to-Consumer) and e-commerce features using keyword matching.

Checkpointing

Saves progress in checkpoints/scraping_progress.json.

Resumes from the last checkpoint to avoid reprocessing already scraped URLs.

Concurrency

Uses asyncio and semaphores to handle multiple URLs in parallel (MAX_WORKERS).

Efficiently handles up to 15 concurrent tasks (configurable).

Logging

Logs progress and errors using Python's logging module.

Prints a summary of results at the end:

Working/broken websites

Social media presence

Video integrations

D2C/e-commerce detection

Emails, phone numbers, and addresses found

Resiliency

Handles Selenium driver creation with retries.

Uses fallback mechanisms for ChromeDriver mismatches.

Gracefully handles HTTP timeouts and scraping errors.

