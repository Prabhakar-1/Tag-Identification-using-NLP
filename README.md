# Tag Identification Using NLP

## Overview

This project demonstrates how to identify and count the frequency of words from a specific webpage using Natural Language Processing (NLP) techniques. The project utilizes Python libraries such as `BeautifulSoup` for web scraping and `nltk` for text processing.

## Features

- Scrapes the content from a specified webpage (e.g., Wikipedia page).
- Tokenizes the text into individual words.
- Removes stopwords (common words that do not add significant meaning).
- Counts the frequency of remaining words.
- Visualizes the top 30 words by frequency.

## Requirements

Before running the project, make sure you have the following Python packages installed:

- `beautifulsoup4`
- `html5lib`
- `nltk`
  
You can install these packages using pip:

```bash
pip install beautifulsoup4 html5lib nltk
```

## Getting Started

1. **Clone the repository** (if applicable) or create a new Python file.
2. **Import the required libraries** and download necessary NLTK data:

```python
import urllib.request  # Handling URL
from bs4 import BeautifulSoup  # Handling or parsing HTML files
import nltk  # NLP toolkit

nltk.download('stopwords')  # Download stopwords list
from nltk.corpus import stopwords
```

3. **Fetch and parse the webpage**:

```python
# Get the info from website
response = urllib.request.urlopen('https://en.wikipedia.org/wiki/apple')
html = response.read()

soup = BeautifulSoup(html, 'html5lib')
text = soup.get_text(strip=True)
```

4. **Tokenize the text and remove stopwords**:

```python
tokens = [t for t in text.split()]
sr = stopwords.words('english')
clean_tokens = tokens[:]  # Create a copy of tokens

for token in tokens:
    if token in stopwords.words('english'):
        clean_tokens.remove(token)
```

5. **Count word frequencies**:

```python
freq = nltk.FreqDist(clean_tokens)

for key, val in freq.items():
    print(str(key) + ':' + str(val))
```

6. **Visualize the top 30 words**:

```python
freq.plot(30, cumulative=False)
```

## Usage

Simply run the Python script to scrape the webpage and see the output of word frequencies printed in the console and visualized in a plot.

## Output

The program will output the frequency of each word and a plot displaying the top 30 most frequent words.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- [BeautifulSoup Documentation](https://www.crummy.com/software/BeautifulSoup/bs4/doc/)
- [NLTK Documentation](https://www.nltk.org/)
- [Wikipedia](https://en.wikipedia.org)

---

Feel free to modify any sections or add additional details specific to your project!
