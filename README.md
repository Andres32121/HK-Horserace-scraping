# Horse Record Scraping on HKJC

This project automates the scraping of horse racing records from the Hong Kong Jockey Club (HKJC) website. The script extracts race dates, race result links, and detailed horse, jockey, and trainer records, saving the data for further analysis.

## Features

- **Scrapes race dates** from the HKJC Local Results page and updates local storage.
- **Extracts race result links** for each race on new dates.
- **Categorizes URLs** by horse, jockey, and trainer.
- **Downloads and updates horse records**, storing them in a CSV file.
- **Handles incremental updates** by checking for and saving only new data.

## Project Structure

- `HorseRecord_Scraping.ipynb`: Main Jupyter Notebook containing all scraping and data processing logic.
- `date_list.txt`: Stores all race dates previously scraped.
- `link.txt`: Stores all unique race result links.
- `horseRecord.csv`: Stores detailed horse records.

## Requirements

- Python 3.x
- Google Chrome browser
- ChromeDriver (compatible with your Chrome version)
- Required Python packages:
  - `selenium`
  - `pandas`
  - `numpy`
  - `re`

Install dependencies with:
```
pip install selenium pandas numpy
```

## Usage

1. **Set up ChromeDriver**  
   Download and place the ChromeDriver executable in your system PATH.

2. **Run the Notebook**  
   Open `HorseRecord_Scraping.ipynb` in Jupyter Notebook and execute each cell in order.

3. **Data Output**  
   - New race dates are saved to `date_list.txt`.
   - Race result links are saved to `link.txt`.
   - Horse records are saved and updated in `horseRecord.csv`.

## Code Overview

### 1. Get Dates from HKJC

- Opens the HKJC Local Results page.
- Extracts all available race dates.
- Updates `date_list.txt` with new dates only.

### 2. Get Links from Race Records

- For each new date, iterates over possible races (1-12).
- Extracts links to race results.
- Saves all unique links to `link.txt`.

### 3. Group URLs by Entity

- Uses regular expressions to categorize links:
  - Horse
  - Jockey
  - Trainer

### 4. Get Horse Records

- Visits each horse's record page.
- Extracts and parses race record tables.
- Appends or updates records in `horseRecord.csv`.

## Notes

- The script uses Selenium WebDriver for browser automation. Ensure Chrome and ChromeDriver are installed and compatible.
- The notebook is designed for incremental updates: it checks for existing data and only scrapes new content.
- Error handling is included to skip over missing data or inaccessible pages.


## Disclaimer

This project is for educational and research purposes. Please respect the terms of use of the HKJC website and avoid excessive scraping that may violate their policies.
