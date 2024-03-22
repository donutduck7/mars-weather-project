# module-11-challenge

Module 12 Challenge: Scrape Titles and Preview Text from Mars News
This project involves scraping titles and preview text from the Mars news website using Splinter and BeautifulSoup. The scraped data is then stored in Python data structures for further analysis.

Steps:
Visit the Website: Use automated browsing to visit the Mars news site and inspect the page to identify elements to scrape.

Scrape the Website: Create a Beautiful Soup object and extract text elements from the website.

Store the Results: Extract the titles and preview text of the news articles, store them in Python dictionaries, and then in a list.
Code Snippets:
# Import Splinter and BeautifulSoup
from splinter import Browser
from bs4 import BeautifulSoup as soup

# Visit the Mars news site
url = 'https://static.bc-edx.com/data/web/mars_news/index.html'
browser = Browser('chrome')
browser.visit(url)
html = browser.html

# Create a Beautiful Soup object
soup = soup(html, 'html.parser')

# Extract all the text elements
all_text = soup.find_all(class_='list_text')

# Create an empty list to store the dictionaries
summary_list = []

# Loop through the text elements
for text in all_text:
    # Extract the title and preview text from the elements
    title = text.find(class_='content_title').text
    preview = text.find(class_='article_teaser_body').text

    # Store each title and preview pair in a dictionary
    summary_dict = {'title': title, 'preview': preview}

    # Add the dictionary to the list
    summary_list.append(summary_dict)

# Print the list to confirm success
print(summary_list)

browser.quit()

