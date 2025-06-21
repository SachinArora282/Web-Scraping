from bs4 import BeautifulSoup
import requests
import pandas as pd
url = "https://en.wikipedia.org/wiki/List_of_largest_companies_by_revenue"
page = requests.get(url)
soup = BeautifulSoup(page.text, 'html')
print(soup)
soup.find('table')
soup.find_all('table')[0]
soup.find('table', class_= 'wikitable sortable plainrowheaders')
table = soup.find('table', class_='wikitable sortable sticky-header-multi sort-under')
table.find_all('th')
world_titles
world_table_titles = [title.text.strip() for title in world_titles[1:7]]
world_table_titles
import pandas as pd
df = pd.DataFrame(columns = world_table_titles)
df
column_data = table.find_all('tr')
column_data
data_rows = table.find_all('tr')

# Iterate over the data rows, skipping the header rows
for row in data_rows[2:]:
    # Find all td and th elements in the row
    row_elements = row.find_all(['td', 'th'])
    # Extract the text from each element, stripping whitespace
    individual_row_data = [element.text.strip() for element in row_elements]

    # Select the correct columns for the DataFrame, skipping the Rank and last two columns
        if len(individual_row_data) < 9 and '$' in individual_row_data[2]:
      data_elements = row.find_all('td')
        if len(data_elements) >= 5: # Ensure there are enough td elements for core data
            name = data_elements[0].text.strip()
              if len(data_elements) == 7: # Normal row structure
                 industry = data_elements[1].text.strip()
                 revenue = data_elements[2].text.strip()
                 profit = data_elements[3].text.strip()
                 employees = data_elements[4].text.strip()
                 headquarters = data_elements[5].text.strip()
        elif len(data_elements) == 6: # Industry merged with previous row
                industry = '' # Or carry over from the previous row if implemented
                name = data_elements[0].text.strip()
                revenue = data_elements[1].text.strip()
                profit = data_elements[2].text.strip()
                employees = data_elements[3].text.strip()
                headquarters = data_elements[4].text.strip()
            else:
                 # Handle other potential variations or skip the row
                 continue # Skip rows with unexpected structure
row_data = [name, industry, revenue, profit, employees, headquarters]
            print(row_data)
            lenght = len(df)
            df.loc[lenght] = row_data

display(df)
