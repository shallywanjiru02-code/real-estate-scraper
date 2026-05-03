\# Real Estate Scraper



Scraping real estate data from \*\*realtor.ca\*\* (Ottawa, Canada) using their hidden API.



\## Project Overview



This scraper extracts property data including:

\- Address

\- Price

\- Bedrooms \& Bathrooms

\- Sales agent information (name, area code, phone number)



\## Tech Stack



\- \*\*Python\*\* with requests library

\- \*\*Pandas\*\* for data manipulation

\- \*\*PostgreSQL\*\* for database storage

\- \*\*Excel\*\* for output files



\## Step-by-Step Process



\### Part 1: Initial Setup \& Single Page

1\. Import libraries (`requests`, `pandas`)

2\. Get request from hidden API

3\. Create JSON object from response

4\. Extract keys: `Results`, `Paging`, `ErrorCode`

5\. Target specific data points:

&#x20;  - Address: `result\['Property']\['Address']\['AddressText']`

&#x20;  - Bedrooms: `result\['Building']\['Bedrooms']`

&#x20;  - Bathrooms: `result\['Building']\['BathroomTotal']`

&#x20;  - Agent: `result\['Individual']\[0]\['Name']`

&#x20;  - Phone: `result\['Individual']\[0]\['Phones']\[0]`



\### Part 2: Data Extraction \& DataFrame

\- Loop through 12 results per page

\- Use try/except blocks for missing data

\- Create pandas DataFrame with all fields



\### Part 3: Multiple Pages

\- Loop through pages 1-50

\- Modify `'current page'` parameter dynamically

\- Export to Excel: `realtor\_multiple\_pages.xlsx`

\- Push to PostgreSQL database



\## Setup Instructions



\### 1. Create virtual environment

```bash

python -m venv .venv

.venv\\Scripts\\activate

