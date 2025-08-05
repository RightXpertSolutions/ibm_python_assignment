# Stock Data Extraction and Visualization Project

## Overview

This project demonstrates how to extract and visualize stock data using Python libraries. It focuses on two major stocks: Tesla (TSLA) and GameStop (GME), extracting both historical stock prices and revenue data to create comprehensive visualizations.

## Table of Contents

1. [Features](#features)
2. [Requirements](#requirements)
3. [Installation](#installation)
4. [Project Structure](#project-structure)
5. [Usage](#usage)
6. [Data Sources](#data-sources)
7. [Functions Overview](#functions-overview)
8. [Visualizations](#visualizations)
9. [Notes](#notes)

## Features

- **Stock Price Extraction**: Uses yfinance library to fetch historical stock data
- **Revenue Data Scraping**: Web scraping to extract quarterly revenue information
- **Data Visualization**: Interactive plots showing stock prices and revenue trends
- **Dual Analysis**: Comprehensive analysis of both Tesla and GameStop stocks
- **Time Series Analysis**: Historical data spanning multiple years

## Requirements

```
yfinance>=0.2.65
pandas>=2.2.2
requests>=2.32.3
beautifulsoup4>=4.13.4
plotly>=6.2.0
numpy>=2.0.2
```

## Installation

1. Clone or download the notebook
2. Install required packages:
```bash
pip install yfinance pandas requests beautifulsoup4 plotly numpy
```

## Project Structure

The notebook is organized into the following sections:

### 1. Setup and Imports
- Library installations and imports
- Configuration for plotting environment

### 2. Define Graphing Function
- `make_graph()` function for creating dual-panel visualizations
- Handles both stock price and revenue data plotting

### 3. Question 1: Tesla Stock Data Extraction
- Extract Tesla (TSLA) historical stock data using yfinance
- Data cleaning and preparation

### 4. Question 2: Tesla Revenue Data Extraction
- Web scraping Tesla revenue data from specified URL
- HTML parsing and data extraction using BeautifulSoup

### 5. Question 3: GameStop Stock Data Extraction
- Extract GameStop (GME) historical stock data using yfinance
- Similar process to Tesla data extraction

### 6. Question 4: GameStop Revenue Data Extraction
- Web scraping GameStop revenue data
- Data cleaning and formatting

### 7. Question 5: Tesla Stock Visualization
- Generate comprehensive Tesla stock and revenue graph

### 8. Question 6: GameStop Stock Visualization
- Generate comprehensive GameStop stock and revenue graph

## Usage

### Basic Usage

1. **Extract Stock Data**:
```python
import yfinance as yf

# Create ticker object
tesla = yf.Ticker("TSLA")
tesla_data = tesla.history(period="max")
tesla_data.reset_index(inplace=True)
```

2. **Extract Revenue Data**:
```python
import requests
from bs4 import BeautifulSoup
import pandas as pd

url = "https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-PY0220EN-SkillsNetwork/labs/project/revenue.htm"
html_data = requests.get(url).text
soup = BeautifulSoup(html_data, "html5lib")

# Extract data from HTML tables
# Process and clean the data
```

3. **Create Visualizations**:
```python
make_graph(tesla_data, tesla_revenue, 'Tesla Stock Data')
```

### Running the Complete Analysis

Simply run all cells in the notebook sequentially. The notebook will:
1. Install required packages
2. Extract all necessary data
3. Generate interactive visualizations for both companies

## Data Sources

### Stock Price Data
- **Source**: Yahoo Finance (via yfinance library)
- **Coverage**: Maximum available historical data
- **Frequency**: Daily stock prices
- **Data Points**: Open, High, Low, Close, Volume, Dividends, Stock Splits

### Revenue Data
- **Tesla**: Custom data source via web scraping
- **GameStop**: Custom data source via web scraping
- **Coverage**: Quarterly revenue figures
- **Format**: Date and Revenue (in millions USD)

## Functions Overview

### `make_graph(stock_data, revenue_data, stock)`

Creates a dual-panel interactive visualization with:
- **Top Panel**: Historical share price over time
- **Bottom Panel**: Historical revenue over time

**Parameters**:
- `stock_data`: DataFrame with Date and Close columns
- `revenue_data`: DataFrame with Date and Revenue columns
- `stock`: String name for the stock (used in title)

**Features**:
- Interactive plotly charts
- Filtered data (stock data ≤ 2021-06-14, revenue data ≤ 2021-04-30)
- Shared x-axis for time correlation
- Professional styling with rangeslider

## Visualizations

The project generates two main visualizations:

### Tesla Stock Analysis
- Stock price trends from 2010 onwards
- Quarterly revenue progression
- Clear visualization of Tesla's growth trajectory

### GameStop Stock Analysis
- Historical price movements including the 2021 surge
- Revenue trends over time
- Comparative analysis capabilities

Both visualizations feature:
- Interactive zoom and pan capabilities
- Hover tooltips with detailed information
- Professional styling suitable for presentations
- Time-synchronized dual panels

## Notes

### Data Limitations
- Stock data filtered to June 14, 2021
- Revenue data filtered to April 30, 2021
- Some data cleaning required for revenue figures

### Technical Considerations
- Requires internet connection for data extraction
- Web scraping may be affected by website changes
- yfinance data subject to Yahoo Finance availability

### Customization Options
- Easy to extend to other stocks by changing ticker symbols
- Revenue data sources can be modified
- Visualization styling can be customized through the `make_graph` function

## Troubleshooting

**Common Issues**:
1. **Import Errors**: Ensure all required packages are installed
2. **Data Extraction Failures**: Check internet connection and data source availability
3. **Empty DataFrames**: Verify ticker symbols and URL accessibility
4. **Plotting Issues**: Ensure plotly is properly configured for your environment

**Solutions**:
- Update packages to latest versions
- Check data source URLs for changes
- Verify ticker symbols are correct
- Restart kernel if experiencing import issues

## License

This project is for educational purposes. Please respect the terms of service of data providers (Yahoo Finance, web scraping sources) when using this code.

## Estimated Completion Time

**30 minutes** for complete execution and analysis.
