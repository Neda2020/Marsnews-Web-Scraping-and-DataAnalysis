# Marsnews-Web-Scraping-and-DataAnalysis--Ch11
Mars news site Web-Scraping and data analysis via both automated browsing with Splinter and HTML parsing  with Beautiful Soup.
# Mars Data Web Scraping and Analysis Project
## Overview
This project consists of two major parts:
1. Scraping titles and preview text from Mars news articles.
2. Scraping and analyzing Mars weather data, focusing on atmospheric pressure and temperature patterns.
The primary goal of this project is to showcase web-scraping and data analysis skills using Splinter and BeautifulSoup for data extraction, Pandas for data manipulation, and Matplotlib for data visualization.

# Part 1: Mars News Scraping
## Objective
The goal of Part 1 was to scrape the titles and preview text of Mars news articles from a webpage using automated browsing and HTML parsing.

## Methodology
# Automated Browsing:
I used the Splinter library to navigate to the Mars News website.
# HTML Parsing:
BeautifulSoup was utilized to extract and parse text elements such as titles and preview text of news articles.
# Data Storage:
Each title and preview text was stored in a dictionary, and all dictionaries were appended to a list for easy access and potential storage.
# Data Output:
The final result was printed in a structured format and optionally saved in a JSON file for sharing.
Code Highlights

## Copy Highlights
#Example of extracting and storing news article
titles = soup.find_all('div', class_='content_title')
paragraphs = soup.find_all('div', class_='article_teaser_body')
news_articles = []
for title, paragraph in zip(titles, paragraphs):
    news_articles.append({'title': title.text.strip(), 'preview': paragraph.text.strip()})
print(news_articles)

# Outcomes
This part demonstrated the use of web-scraping techniques to extract relevant data from a webpage. The extracted data can be used for further analysis, providing insights into Mars-related missions and research.

## Part 2: Mars Weather Data Scraping and Analysis
# Objective
In Part 2, we scraped and analyzed Mars weather data, focusing on patterns in atmospheric pressure and minimum temperature across Martian months. The data was scraped from a table on a Mars temperature webpage.
#### Minimum Temperature
Mars experiences extreme cold, with temperatures varying between -90°C and -60°C. The coldest month is month 3, while the warmest occurs in month 8. Despite the harsh conditions, the temperature follows a predictable pattern.

#### Atmospheric Pressure
Mars' thin atmosphere exhibits seasonal fluctuations, with pressure reaching its peak in month 9 and dipping in month 6. These variations highlight the planet’s challenging environment, making human survival and stable water presence difficult.

#### Year Length
The data reveals that Mars' minimum temperature varies cyclically between approximately -90°C and -60°C, corresponding to seasonal changes. This recurring pattern indicates that a complete Martian year is approximately 671 sols in length.

# Methodology
## Automated Browsing and Scraping: 
Splinter and BeautifulSoup were used to extract the table data from the webpage.
## Data Cleaning and Manipulation: 
Data was organized into a Pandas DataFrame with appropriate column headings and data types.
## Data Analysis:
.Counted the number of unique Martian months.
.Determined the total number of Martian sols (days) represented in the dataset.
.Calculated and visualized the average minimum temperature and average atmospheric pressure for each Martian month.
.Identified the coldest and hottest months as well as the months with the highest and lowest atmospheric pressure.

## Code Highlights
# Scraping Table Data
#Extracting table data into a DataFrame
table = soup.find('table', class_='table')
headers = [header.text.strip() for header in table.find_all('th')]
rows = table.find_all('tr')
data = [[col.text.strip() for col in row.find_all('td')] for row in rows[1:]]
df = pd.DataFrame(data, columns=headers)

## Data Analysis Example
# .Average Minimum Temperature by Month
python:
avg_min_temp = df.groupby('month')['min_temp'].mean()
avg_min_temp.plot(kind='bar', title='Average Minimum Temperature by Month on Mars')
plt.xlabel('Month')
plt.ylabel('Average Minimum Temperature (°C)')
plt.show()

# Saving Data to CSV
python
df.to_csv('mars_weather_data.csv', index=False)

## Outcomes
# Martian Months:
Identified 12 distinct Martian months.
# Temperature Patterns:
Determined and visualized the coldest and hottest months based on average minimum temperatures.
![Average Minimum Temperature by Month on Mars sorted](https://github.com/user-attachments/assets/aa03ac64-0db7-4899-8fcb-6495d990f327)
![Average Minimum Temperature by Month on Mars](https://github.com/user-attachments/assets/c46d9a2f-c5ed-49fb-b905-797365615082)
![Minimum Temperature over Time](https://github.com/user-attachments/assets/8e58fa84-ed04-49a2-81a3-d97cce47773e)

# Pressure Analysis: 
Visualized atmospheric pressure patterns, identifying months with the highest and lowest pressure values.
![Average Atmospheric Pressure by Month on Mars](https://github.com/user-attachments/assets/defce38a-d4f6-4b37-82a6-94b883d9bcbc)
![daAverage Atmospheric Pressure by Month on Mars (Sorted)](https://github.com/user-attachments/assets/2a373ac1-b206-494d-a701-41d2128c3789)

## Key Takeaways
# .Web Scraping:
Leveraged Splinter and BeautifulSoup for data extraction.
# .Data Analysis:
Used Pandas for data manipulation and Matplotlib for visualization.
# .Insights:
The project offered insights into Martian weather patterns, including temperature and pressure variations across Martian months.

## Project Structure
Mars_Web_Scraping_Project/
├── README.md
├── part_1_mars_news.ipynb
├── part_2_mars_weather.ipynb
├── mars_weather_data.csv
└── images/
    └── temperature_plot.png
.README.md: Project documentation
.part_1_mars_news.ipynb: Jupyter Notebook for Mars news scraping
.part_2_mars_weather.ipynb: Jupyter Notebook for Mars weather data scraping and analysis
.mars_weather_data.csv: CSV file containing the scraped weather data
.images/: Folder containing images/graphs generated during the analysis
