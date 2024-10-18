# KuCoin ETL Pipeline

This project implements a robust ETL (Extract, Transform, Load) pipeline designed to process and analyze KuCoin cryptocurrency data in real-time. Built with Python, it integrates essential technologies like Flask, CCXT, APScheduler, AWS S3, and Pandas, providing a seamless workflow from data extraction to cloud storage.

## Key Features

### 1. **Real-time Data Extraction**
- Utilizes the powerful `CCXT` library to fetch OHLCV (Open, High, Low, Close, Volume) data for multiple cryptocurrency pairs from KuCoin.

### 2. **Automated Data Processing**
- Computes various indicators, such as:
  - 24-hour percentage change
  - Rolling maximum prices
  - All-Time High (ATH) relative changes

### 3. **Efficient Multi-threading**
- Leverages Python's `concurrent.futures.ThreadPoolExecutor` for concurrent processing of multiple tokens, enhancing performance and speed.

### 4. **Scheduled Data Processing**
- Employs `APScheduler` for automating periodic execution of data extraction and transformation, ensuring up-to-date information.

### 5. **AWS S3 Integration**
- Automatically uploads processed output data to an AWS S3 bucket for easy access and storage.

## Technologies Used

- **Flask**: Web framework used to create an API endpoint for running the scanner.
- **CCXT**: A cryptocurrency trading library to fetch data from the KuCoin exchange.
- **APScheduler**: A scheduling library to automate task execution at specified intervals.
- **AWS S3**: For storing and retrieving processed files.
- **Pandas**: For data manipulation and transformation.
- **ThreadPoolExecutor**: For concurrent processing of large datasets to improve performance.

## How It Works

### Data Flow

#### 1. **Data Extraction**
- Fetches ticker and OHLCV data for multiple cryptocurrency pairs traded on KuCoin.
- Filters out leveraged tokens (e.g., 3S, 2L) to focus on main trading pairs.

#### 2. **Data Transformation**
- Computes key metrics like price changes, 24-hour high/low, weekly and monthly highs, and volumes.
- Calculates changes relative to All-Time High (ATH) and other timeframes (24h, 7d, 30d).

#### 3. **Parallel Processing**
- Cryptocurrencies are processed concurrently in multiple threads to enhance speed and efficiency.

#### 4. **Output & Storage**
- Data is merged with additional metadata and uploaded to AWS S3 for storage.
- CSV reports are generated and stored locally before being uploaded.

## Endpoint

### `/BOT1`
- Runs the cryptocurrency scanner and triggers the data processing pipeline.
- Schedules jobs every 400 seconds using `APScheduler` and uploads the results to S3.

## Screenshots

### 1. Flask Instance Running
![Flask Instance Running](<files/python code.png>)

### 2. Homepage
![Homepage](<files/Homepage.png>)
*Displays the message: "Welcome to KuCoin ETL Pipeline."*

### 3. S3 Bucket Upload
![S3 Bucket Upload](<files/s3bucket.png>)
*Shows the uploaded file in the S3 bucket.*

### 4. BOT1 Page Output
![BOT1 Page Output](<files/botpage_output.png>)
*Displays the results from the BOT1 page.*

### 5. CSV Transformed and Uploaded file Output
*A glimpse of output and transformed data file is stored in "data.csv"*


