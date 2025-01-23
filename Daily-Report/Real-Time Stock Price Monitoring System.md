# Real-Time Stock Price Monitoring System

**Author:** Sourabh Narnaulia
**Date:** 13 Dec 2025
Title: Real-Time Stock Price Monitoring System
Epic Name: KAFKA
Git link: https://github.com/srbhcodes/RealTimeStockMonitor

## Scope of Project

The objective of this project is to create a real-time stock price monitoring system that:

- Fetches live stock data from an external API (Alpha Vantage).
- Streams the stock price data to a Kafka topic.
- Consumes the data and stores it in an SQLite database for further analysis.
- Enables real-time monitoring of stock price movements for selected companies.

## Technologies Used

- **Python**: Core programming language for implementing producers and consumers.
- **Kafka**: Messaging system for real-time data streaming.
- **Alpha Vantage API**: For fetching live stock prices.
- **SQLite**: Database to store stock prices.
- **Libraries**:
    - `kafka-python` for Kafka integration.
    - `requests` for API calls.
    - `json` for handling data serialization.

## Steps

1. Set up the development environment and install required libraries.
2. Create a Kafka producer to fetch and send stock prices to a Kafka topic.
3. Fetch live stock data from Alpha Vantage API in the producer script.
4. Create a Kafka consumer to receive and process stock price messages.
5. Store the consumed data into an SQLite database.
6. Implement error handling and logging to manage API and Kafka failures.
7. Test the system end-to-end for different stock symbols.
8. Troubleshoot and resolve issues encountered during development.

## Project Outcome

- A functional system that fetches live stock prices for selected companies and streams them to a Kafka topic.
- The system successfully stores the real-time stock price data into an SQLite database for further use.
- Real-time monitoring of stock price movements achieved through seamless producer-consumer communication.

## Issues Faced

1. **Kafka Configuration Errors:**
    
    - Misconfigured Kafka server leading to connection issues.
    - Solution: Verified `bootstrap_servers` and ensured Kafka was running.
2. **API Key Rate Limits:**
    
    - Alpha Vantage free tier limits API calls to 5 requests per minute.
    - Solution: Implemented delays between API calls and added robust error handling.
3. **Random Stock Selection Issue:**
    
    - Producer script fetching data only for one stock symbol.
    - Solution: Enhanced error handling and switched to sequential stock fetching for consistent data.
4. **NameError:**
    
    - Missing import of the `random` library in the producer script.
    - Solution: Added the necessary import.
5. **Data Parsing Errors:**
    
    - JSON response from API occasionally missing keys.
    - Solution: Added `try-except` blocks to handle missing data gracefully.
6. **Consumer Script Errors:**
    
    - SQLite database table not found during initial execution.
    - Solution: Ensured table creation code was executed before consuming messages.
7. **Git Authentication Issues:**
    
    - Faced issues pushing code to GitHub after August 2021's deprecation of password authentication.
    - Solution: Switched to personal access tokens for secure authentication.

---

### Screenshots:

![[Pasted image 20250107213830.png]]