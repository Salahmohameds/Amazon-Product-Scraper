# Amazon-Product-Scraper

![Python](https://img.shields.io/badge/Python-3.x-blue)
![Selenium](https://img.shields.io/badge/Selenium-3.141.0-green)
![BeautifulSoup](https://img.shields.io/badge/BeautifulSoup-4.9.3-yellow)

## Overview

This project is a powerful tool for automating the extraction of detailed product information from Amazon. Utilizing Python, Selenium, and BeautifulSoup, this scraper navigates through Amazon product pages and extracts data such as prices, promotions, reviews, and more, saving everything neatly into a CSV file.

## Features

- **Automated Browsing:** Navigate through Amazon product listings using Selenium in headless mode.
- **Comprehensive Data Extraction:** Capture detailed product information including:
  - Product Name
  - Price
  - Promotions
  - Ratings
  - Reviews
  - ASIN, and more.
- **Multi-page Scraping:** Automatically navigate through all available product pages, ensuring no data is missed.
- **CSV Export:** Save the extracted data in a structured CSV format for easy analysis.

## Installation

1. **Clone the Repository:**

    ```bash
    git clone https://github.com/yourusername/amazon-product-scraper.git
    cd amazon-product-scraper
    ```

2. **Install the Required Packages:**

    Make sure you have Python 3.x installed. Then, install the required packages using pip:

    ```bash
    pip install -r requirements.txt
    ```

    **Packages Include:**
    - `selenium`
    - `beautifulsoup4`
    - `pandas`

3. **Setup ChromeDriver:**

    Download ChromeDriver that matches your Chrome browser version and place it in your system's PATH, or specify the path directly in your script.

    ```python
    chromedriver_path = "C:\\path\\to\\chromedriver.exe"
    ```

## Usage

1. **Configure the Script:**

    Customize the script parameters such as the starting URL, file name for the CSV output, and any specific product attributes you want to scrape.

2. **Run the Scraper:**

    ```bash
    python amazon_scraper.py
    ```

3. **Output:**

    The script will output a CSV file containing all the scraped data, structured and ready for analysis.

## Code Walkthrough

Here’s a brief explanation of the key parts of the code:

- **Initialization:** Set up Selenium with Chrome in headless mode for efficient scraping.
  
    ```python
    options = webdriver.ChromeOptions()
    options.add_argument('headless')
    driver = webdriver.Chrome(executable_path=chromedriver_path, options=options)
    ```

- **Scraping Logic:** Navigate through each page, extract the desired product details, and handle pagination.
  
    ```python
    while True:
        # Extract data from the current page
        # Check if there's a 'Next' page, if not, break
        next_button = driver.find_element_by_class_name('a-last')
        if 'disabled' in next_button.get_attribute('class'):
            break
        next_button.click()
    ```

- **Data Storage:** Use Pandas to structure the data and save it as a CSV file.

    ```python
    df = pd.DataFrame(data_list, columns=['Product Name', 'Price', 'Rating', 'Review Count', 'ASIN'])
    df.to_csv('amazon_products.csv', index=False)
    ```

## Future Improvements

- **Error Handling:** Enhance error handling for cases like CAPTCHA, page timeouts, and network issues.
- **Proxy Integration:** Add proxy support to bypass Amazon's scraping prevention mechanisms.
- **Parallel Scraping:** Implement parallel processing to speed up the scraping process for large datasets.

## Contributing

If you’d like to contribute to this project, feel free to fork the repository and submit a pull request. Any improvements, bug fixes, or new features are welcome!

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- **Selenium:** For providing a robust web automation tool.
- **BeautifulSoup:** For making HTML parsing straightforward.
- **Pandas:** For handling data manipulation with ease.
